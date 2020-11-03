https://github.com/microsoft/terminal/issues/1060

I solved the issue now, it could be closed. Thanks a lot to all who involved into this discussion.

Step 0:

Test if two constants below works well which will be used in following other steps.

echo %USERPROFILE%

echo %LOCALAPPDATA%
If everything works well here, then these two constants can be used directly in other below steps.

Or please perform following replacements in below steps:

%USERPROFILE% → C:\Users\[userName]
%LOCALAPPDATA% → C:\Users\[userName]\AppData\Local

Here [userName] represents your user name，for instance, mine is Bruce.

Step 1:
Run below stuff in CMD:

mkdir "%USERPROFILE%\AppData\Local\terminal"
image

Step 2:
Copy the windows terminal icon to the folder %USERPROFILE%\AppData\Local\terminal, the icon can be obtained in https://github.com/yanglr/WindowsDevTools/tree/master/awosomeTerminal/icons whose file name is wt_32.ico.

Step 3:
Save follwing content as wt.reg, then run as administrator.

Windows Registry Editor Version 5.00

[HKEY_CLASSES_ROOT\Directory\Background\shell\wt]
@="Windows terminal here"
"Icon"="%USERPROFILE%\\AppData\\Local\\terminal\\wt_32.ico"

[HKEY_CLASSES_ROOT\Directory\Background\shell\wt\command]
@="%LOCALAPPDATA%\\Microsoft\\WindowsApps\\wt.exe"
To be noted, if the exe obtained after building code by yourself is wtd.exe, you need to change the above wt.exe to wtd.exe in the above registry.

Step 4:
Test





#### change resolution in option -> settings
{
    "$schema": "https://aka.ms/terminal-profiles-schema",

    "defaultProfile": "{61c54bbd-c2c6-5271-96e7-009a87ff44bf}",

    // You can add more global application settings here.
    // To learn more about global settings, visit https://aka.ms/terminal-global-settings

    // If enabled, selections are automatically copied to your clipboard.
    "copyOnSelect": false,

    // If enabled, formatted data is also copied to your clipboard
    "copyFormatting": false,
    "initialCols" : 100,
    "initialRows" : 25,

....
