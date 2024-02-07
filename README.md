# Add "Windows Terminal Here" to Right-Click Context Menu (Windows 10)

This guide provides step-by-step instructions on how to add an option to open Windows Terminal at any folder location in Windows 10's right-click context menu.

## Prerequisites

- Windows 10 operating system
- Windows Terminal installed on your system
- Downloaded this repository

## Instructions

1. **Install Windows Terminal**:
   - Ensure that Windows Terminal is installed on your system. If not, download and install it from the [Microsoft Store](https://www.microsoft.com/en-us/p/windows-terminal/9n0dx20hk701).

2. **Download This Repository**:
   - Download this repository to your local machine. You can clone it or download it as a ZIP file.

3. **Edit `.reg` File**:
   - Navigate to the downloaded repository folder.
   - Open the `wt.reg` file in a text editor.
   - Replace `"YOUR_USERNAME"` with your actual username in the file.

   ```reg
    Windows Registry Editor Version 5.00

    [HKEY_CLASSES_ROOT\Directory\Background\shell\wt]
    @="Windows terminal here"
    "Icon"="C:\\Users\\YOUR_USERNAME\\AppData\\Local\\terminal\\terminal.ico"

    [HKEY_CLASSES_ROOT\Directory\Background\shell\wt\command]
    @="C:\\Users\\YOUR_USERNAME\\AppData\\Local\\Microsoft\\WindowsApps\\wt.exe"
   ```

4. **Create folder for icon:**

    ```cmd
    mkdir %USERPROFILE%\AppData\Local\terminal
    ```

5. **Download the Icon**:
   - Download the Windows Terminal icon from [here](terminal.ico).
   - Place the downloaded icon in the Windows Terminal installation folder. The default installation folder is usually `C:\\Users\\YOUR_USERNAME\\AppData\\Local\\terminal\\`.
   - Copy terminal icon to the required folder
    ```cmd
    cp terminal.ico %USERPROFILE%\AppData\Local\terminal
    ```

6. **Run `.reg` File**:
   - Double-click the modified `.reg` file (`wt.reg`) to run it.
   - Confirm the prompts to add the changes to the Windows registry.



7. **Edit Terminal Settings**:
   - Locate the `settings.json` file in the Windows Terminal installation folder.
   - Open the `settings.json` file in a text editor.
   - Find the `profiles` section and add `"startingDirectory": "."` to the relevant profile(s). This ensures that Windows Terminal opens in the right directory.
   ```json
    {
        "guid": "{61c54bbd-c2c6-5271-96e7-009a87ff44bf}",
        "name": "Windows PowerShell",
        "commandline": "powershell.exe",
        "startingDirectory": ".",
        "hidden": false
    },
    {
        "guid": "{0caa0dad-35be-5f56-a8ff-afceeeaa6101}",
        "name": "cmd",
        "commandline": "cmd.exe",
        "startingDirectory": ".",
        "hidden": false
    }                                                                                           
   ```

## Usage

Once the changes are applied, follow these steps to use the added functionality:

1. **Navigate to Folder**:
   - Open File Explorer and navigate to the folder where you want to open Windows Terminal.

2. **Right-Click**:
   - Right-click on an empty space within the folder or on the folder itself.

3. **Select "Windows Terminal Here"**:
   - In the context menu, you should see an option labeled "Windows Terminal Here". Click on it.

4. **Windows Terminal Opens**:
   - Windows Terminal will open, starting in the directory where you right-clicked.

## Notes

- Ensure the path to Windows Terminal (`WindowsTerminal.exe`) in the `.reg` file matches the installation path on your system.
- Modifying the registry can have unintended consequences if not done correctly. Proceed with caution and follow the instructions carefully.
- Always back up your registry before making any changes.
- Replace `"YOUR_USERNAME"` in the `.reg` file with your actual username before running it.
- Download the Windows Terminal icon and place it in the installation folder as instructed.
- Edit the `settings.json` file to ensure Windows Terminal opens in the right directory.
