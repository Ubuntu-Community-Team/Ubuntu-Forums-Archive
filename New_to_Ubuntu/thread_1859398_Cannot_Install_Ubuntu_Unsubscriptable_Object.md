---
title: "Cannot Install Ubuntu: Unsubscriptable Object"
date: 2011-10-13
forum: New to Ubuntu
---

### Post by trent_almighty on 2011-10-13
Hey, I'm a very new Ubuntu user and I am not too clued up about everything.  I think I should also mention that I am using Ubuntu because my uni course requires it and so I decided to use wubi to install it on my Windows Vista Machine.

I managed to successfully install and run Ubuntu 11.10 for several days.  However earlier today I my computer died mid update (battery thing) and that caused all sorts of problems where i couldn't get past the GRUB screen.  After scouring the internet and not really finding much accessible help I decided to uninstall Ubuntu from Windows and then reinstall it to see if I could get a fresh start.

The uninstallation worked without a hitch as far as I could tell but when I came to reinstall Ubuntu using WUBI I encountered the following problem during installation:

An error occured:

unsubscriptable object

For more information, please see the log file:

The Log file is rather long so I can't really post it but the first error recorded is:

ERROR  TaskList: [Errno 14] HTTP Error 409: Conflict

and from there on it is just a list of further errors before the log ends.

I'm really unsure about what to do and any help would be greatly appreciated and just hope I haven't made a mess of everything ;)

---

### Post by bcbc on 2011-10-13
Either copy and paste just the last logged execution of wubi, or clear the logfile, rerun and post the contents between [CODE[SIZE="1"] [/SIZE]][/CODE] tags

---

### Post by trent_almighty on 2011-10-14
```

10-14 08:32 INFO   root: === wubi 11.10 rev245 ===
10-14 08:32 DEBUG  root: Logfile is c:\users\brian\appdata\local\temp\wubi-11.10-rev245.log
10-14 08:32 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\Users\\Brian\\Desktop\\wubi.exe"']
10-14 08:32 DEBUG  CommonBackend: data_dir=C:\Users\Brian\AppData\Local\Temp\pyl7071.tmp\data
10-14 08:32 DEBUG  WindowsBackend: 7z=C:\Users\Brian\AppData\Local\Temp\pyl7071.tmp\bin\7z.exe
10-14 08:32 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
10-14 08:32 DEBUG  CommonBackend: Fetching basic info...
10-14 08:32 DEBUG  CommonBackend: original_exe=C:\Users\Brian\Desktop\wubi.exe
10-14 08:32 DEBUG  CommonBackend: platform=win32
10-14 08:32 DEBUG  CommonBackend: osname=nt
10-14 08:32 DEBUG  CommonBackend: language=en_GB
10-14 08:32 DEBUG  CommonBackend: encoding=cp1252
10-14 08:32 DEBUG  WindowsBackend: arch=amd64
10-14 08:32 DEBUG  CommonBackend: Parsing isolist=C:\Users\Brian\AppData\Local\Temp\pyl7071.tmp\data\isolist.ini
10-14 08:32 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
10-14 08:32 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
10-14 08:32 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
10-14 08:32 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
10-14 08:32 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
10-14 08:32 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
10-14 08:32 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
10-14 08:32 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
10-14 08:32 DEBUG  WindowsBackend: Fetching host info...
10-14 08:32 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
10-14 08:32 DEBUG  WindowsBackend: windows version=vista
10-14 08:32 DEBUG  WindowsBackend: windows_version2=Windows Vista (TM) Home Premium
10-14 08:32 DEBUG  WindowsBackend: windows_sp=Service Pack 2
10-14 08:32 DEBUG  WindowsBackend: windows_build=6002
10-14 08:32 DEBUG  WindowsBackend: gmt=0
10-14 08:32 DEBUG  WindowsBackend: country=GB
10-14 08:32 DEBUG  WindowsBackend: timezone=Europe/London
10-14 08:32 DEBUG  WindowsBackend: windows_username=Brian
10-14 08:32 DEBUG  WindowsBackend: user_full_name=Brian
10-14 08:32 DEBUG  WindowsBackend: user_directory=C:\Users\Brian
10-14 08:32 DEBUG  WindowsBackend: windows_language_code=1033
10-14 08:32 DEBUG  WindowsBackend: windows_language=English
10-14 08:32 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM)2 Duo CPU     T7250  @ 2.00GHz
10-14 08:32 DEBUG  WindowsBackend: bootloader=vista
10-14 08:32 DEBUG  WindowsBackend: system_drive=Drive(C: hd 59932.9140625 mb free ntfs)
10-14 08:32 DEBUG  WindowsBackend: drive=Drive(C: hd 59932.9140625 mb free ntfs)
10-14 08:32 DEBUG  WindowsBackend: drive=Drive(D: hd 2321.2109375 mb free ntfs)
10-14 08:32 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free cdfs)
10-14 08:32 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
10-14 08:32 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
10-14 08:32 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
10-14 08:32 DEBUG  WindowsBackend: keyboard_id=134809609
10-14 08:32 DEBUG  WindowsBackend: keyboard_layout=gb
10-14 08:32 DEBUG  WindowsBackend: keyboard_variant=
10-14 08:32 DEBUG  CommonBackend: python locale=('en_GB', 'cp1252')
10-14 08:32 DEBUG  CommonBackend: locale=en_GB.UTF-8
10-14 08:32 DEBUG  WindowsBackend: total_memory_mb=2047.99999905
10-14 08:32 DEBUG  CommonBackend: Searching ISOs on USB devices
10-14 08:32 DEBUG  CommonBackend: Searching for local CDs
10-14 08:32 DEBUG  Distro:   checking whether C:\Users\Brian\AppData\Local\Temp\pyl7071.tmp is a valid Ubuntu CD
10-14 08:32 DEBUG  Distro:     does not contain C:\Users\Brian\AppData\Local\Temp\pyl7071.tmp\casper\filesystem.squashfs
10-14 08:32 DEBUG  Distro:   checking whether C:\Users\Brian\AppData\Local\Temp\pyl7071.tmp is a valid Ubuntu CD
10-14 08:32 DEBUG  Distro:     does not contain C:\Users\Brian\AppData\Local\Temp\pyl7071.tmp\casper\filesystem.squashfs
10-14 08:32 DEBUG  Distro:   checking whether C:\Users\Brian\AppData\Local\Temp\pyl7071.tmp is a valid Kubuntu CD
10-14 08:32 DEBUG  Distro:     does not contain C:\Users\Brian\AppData\Local\Temp\pyl7071.tmp\casper\filesystem.squashfs
10-14 08:32 DEBUG  Distro:   checking whether C:\Users\Brian\AppData\Local\Temp\pyl7071.tmp is a valid Kubuntu CD
10-14 08:32 DEBUG  Distro:     does not contain C:\Users\Brian\AppData\Local\Temp\pyl7071.tmp\casper\filesystem.squashfs
10-14 08:32 DEBUG  Distro:   checking whether C:\Users\Brian\AppData\Local\Temp\pyl7071.tmp is a valid Xubuntu CD
10-14 08:32 DEBUG  Distro:     does not contain C:\Users\Brian\AppData\Local\Temp\pyl7071.tmp\casper\filesystem.squashfs
10-14 08:32 DEBUG  Distro:   checking whether C:\Users\Brian\AppData\Local\Temp\pyl7071.tmp is a valid Xubuntu CD
10-14 08:32 DEBUG  Distro:     does not contain C:\Users\Brian\AppData\Local\Temp\pyl7071.tmp\casper\filesystem.squashfs
10-14 08:32 DEBUG  Distro:   checking whether C:\Users\Brian\AppData\Local\Temp\pyl7071.tmp is a valid Mythbuntu CD
10-14 08:32 DEBUG  Distro:     does not contain C:\Users\Brian\AppData\Local\Temp\pyl7071.tmp\casper\filesystem.squashfs
10-14 08:32 DEBUG  Distro:   checking whether C:\Users\Brian\AppData\Local\Temp\pyl7071.tmp is a valid Mythbuntu CD
10-14 08:32 DEBUG  Distro:     does not contain C:\Users\Brian\AppData\Local\Temp\pyl7071.tmp\casper\filesystem.squashfs
10-14 08:32 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
10-14 08:32 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-14 08:32 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
10-14 08:32 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-14 08:32 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
10-14 08:32 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-14 08:32 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
10-14 08:32 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-14 08:32 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
10-14 08:32 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-14 08:32 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
10-14 08:32 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-14 08:32 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
10-14 08:32 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-14 08:32 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
10-14 08:32 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-14 08:32 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
10-14 08:32 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-14 08:32 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
10-14 08:32 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-14 08:32 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
10-14 08:32 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-14 08:32 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
10-14 08:32 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-14 08:32 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
10-14 08:32 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-14 08:32 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
10-14 08:32 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-14 08:32 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
10-14 08:32 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-14 08:32 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
10-14 08:32 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-14 08:32 INFO   root: Already installed, running the uninstaller...
10-14 08:32 INFO   root: Running the uninstaller...
10-14 08:32 INFO   CommonBackend: This is the uninstaller running
10-14 08:32 DEBUG  WindowsFrontend: __init__...
10-14 08:32 DEBUG  WindowsFrontend: on_init...
10-14 08:32 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Brian\AppData\Local\Temp\pyl7071.tmp\translations, languages=['en_GB', 'en']
10-14 08:32 INFO   root: Received settings
10-14 08:32 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Brian\AppData\Local\Temp\pyl7071.tmp\translations, languages=['en_GB', 'en']
10-14 08:32 DEBUG  TaskList: # Running tasklist...
10-14 08:32 DEBUG  TaskList: ## Running Remove bootloader entry....
10-14 08:32 DEBUG  WindowsBackend: Could not find bcd id
10-14 08:32 DEBUG  WindowsBackend: undo_bootini C:
10-14 08:32 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 59932.9140625 mb free ntfs)
10-14 08:32 DEBUG  WindowsBackend: undo_bootini D:
10-14 08:32 DEBUG  WindowsBackend: undo_configsys Drive(D: hd 2321.2109375 mb free ntfs)
10-14 08:32 DEBUG  TaskList: ## Finished Remove bootloader entry.
10-14 08:32 DEBUG  TaskList: ## Running Remove target dir....
10-14 08:32 DEBUG  CommonBackend: Deleting C:\ubuntu
10-14 08:32 DEBUG  TaskList: ## Finished Remove target dir.
10-14 08:32 DEBUG  TaskList: ## Running Remove registry key....
10-14 08:32 DEBUG  TaskList: ## Finished Remove registry key.
10-14 08:32 DEBUG  TaskList: # Finished tasklist
10-14 08:32 INFO   root: Almost finished uninstalling
10-14 08:32 INFO   root: Finished uninstallation
10-14 08:32 DEBUG  CommonBackend: Fetching basic info...
10-14 08:32 DEBUG  CommonBackend: original_exe=C:\Users\Brian\Desktop\wubi.exe
10-14 08:32 DEBUG  CommonBackend: platform=win32
10-14 08:32 DEBUG  CommonBackend: osname=nt
10-14 08:32 DEBUG  WindowsBackend: arch=amd64
10-14 08:32 DEBUG  CommonBackend: Parsing isolist=C:\Users\Brian\AppData\Local\Temp\pyl7071.tmp\data\isolist.ini
10-14 08:32 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
10-14 08:32 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
10-14 08:32 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
10-14 08:32 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
10-14 08:32 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
10-14 08:32 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
10-14 08:32 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
10-14 08:32 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
10-14 08:32 DEBUG  WindowsBackend: Fetching host info...
10-14 08:32 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
10-14 08:32 DEBUG  WindowsBackend: windows version=vista
10-14 08:32 DEBUG  WindowsBackend: windows_version2=Windows Vista (TM) Home Premium
10-14 08:32 DEBUG  WindowsBackend: windows_sp=Service Pack 2
10-14 08:32 DEBUG  WindowsBackend: windows_build=6002
10-14 08:32 DEBUG  WindowsBackend: gmt=0
10-14 08:32 DEBUG  WindowsBackend: country=GB
10-14 08:32 DEBUG  WindowsBackend: timezone=Europe/London
10-14 08:32 DEBUG  WindowsBackend: windows_username=Brian
10-14 08:32 DEBUG  WindowsBackend: user_full_name=Brian
10-14 08:32 DEBUG  WindowsBackend: user_directory=C:\Users\Brian
10-14 08:32 DEBUG  WindowsBackend: windows_language_code=1033
10-14 08:32 DEBUG  WindowsBackend: windows_language=English
10-14 08:32 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM)2 Duo CPU     T7250  @ 2.00GHz
10-14 08:32 DEBUG  WindowsBackend: bootloader=vista
10-14 08:32 DEBUG  WindowsBackend: system_drive=Drive(C: hd 59935.28125 mb free ntfs)
10-14 08:32 DEBUG  WindowsBackend: drive=Drive(C: hd 59935.28125 mb free ntfs)
10-14 08:32 DEBUG  WindowsBackend: drive=Drive(D: hd 2321.2109375 mb free ntfs)
10-14 08:32 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free cdfs)
10-14 08:32 DEBUG  WindowsBackend: uninstaller_path=None
10-14 08:32 DEBUG  WindowsBackend: previous_target_dir=None
10-14 08:32 DEBUG  WindowsBackend: previous_distro_name=None
10-14 08:32 DEBUG  WindowsBackend: keyboard_id=134809609
10-14 08:32 DEBUG  WindowsBackend: keyboard_layout=gb
10-14 08:32 DEBUG  WindowsBackend: keyboard_variant=
10-14 08:32 DEBUG  WindowsBackend: total_memory_mb=2047.99999905
10-14 08:32 DEBUG  CommonBackend: Searching ISOs on USB devices
10-14 08:32 DEBUG  CommonBackend: Searching for local CDs
10-14 08:32 DEBUG  Distro:   checking whether C:\Users\Brian\AppData\Local\Temp\pyl7071.tmp is a valid Ubuntu CD
10-14 08:32 DEBUG  Distro:     does not contain C:\Users\Brian\AppData\Local\Temp\pyl7071.tmp\casper\filesystem.squashfs
10-14 08:32 DEBUG  Distro:   checking whether C:\Users\Brian\AppData\Local\Temp\pyl7071.tmp is a valid Ubuntu CD
10-14 08:32 DEBUG  Distro:     does not contain C:\Users\Brian\AppData\Local\Temp\pyl7071.tmp\casper\filesystem.squashfs
10-14 08:32 DEBUG  Distro:   checking whether C:\Users\Brian\AppData\Local\Temp\pyl7071.tmp is a valid Kubuntu CD
10-14 08:32 DEBUG  Distro:     does not contain C:\Users\Brian\AppData\Local\Temp\pyl7071.tmp\casper\filesystem.squashfs
10-14 08:32 DEBUG  Distro:   checking whether C:\Users\Brian\AppData\Local\Temp\pyl7071.tmp is a valid Kubuntu CD
10-14 08:32 DEBUG  Distro:     does not contain C:\Users\Brian\AppData\Local\Temp\pyl7071.tmp\casper\filesystem.squashfs
10-14 08:32 DEBUG  Distro:   checking whether C:\Users\Brian\AppData\Local\Temp\pyl7071.tmp is a valid Xubuntu CD
10-14 08:32 DEBUG  Distro:     does not contain C:\Users\Brian\AppData\Local\Temp\pyl7071.tmp\casper\filesystem.squashfs
10-14 08:32 DEBUG  Distro:   checking whether C:\Users\Brian\AppData\Local\Temp\pyl7071.tmp is a valid Xubuntu CD
10-14 08:32 DEBUG  Distro:     does not contain C:\Users\Brian\AppData\Local\Temp\pyl7071.tmp\casper\filesystem.squashfs
10-14 08:32 DEBUG  Distro:   checking whether C:\Users\Brian\AppData\Local\Temp\pyl7071.tmp is a valid Mythbuntu CD
10-14 08:32 DEBUG  Distro:     does not contain C:\Users\Brian\AppData\Local\Temp\pyl7071.tmp\casper\filesystem.squashfs
10-14 08:32 DEBUG  Distro:   checking whether C:\Users\Brian\AppData\Local\Temp\pyl7071.tmp is a valid Mythbuntu CD
10-14 08:32 DEBUG  Distro:     does not contain C:\Users\Brian\AppData\Local\Temp\pyl7071.tmp\casper\filesystem.squashfs
10-14 08:32 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
10-14 08:32 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-14 08:32 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
10-14 08:32 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-14 08:32 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
10-14 08:32 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-14 08:32 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
10-14 08:32 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-14 08:32 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
10-14 08:32 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-14 08:32 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
10-14 08:32 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-14 08:32 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
10-14 08:32 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-14 08:32 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
10-14 08:32 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-14 08:32 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
10-14 08:32 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-14 08:32 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
10-14 08:32 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-14 08:32 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
10-14 08:32 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-14 08:32 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
10-14 08:32 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-14 08:32 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
10-14 08:32 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-14 08:32 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
10-14 08:32 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-14 08:32 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
10-14 08:32 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-14 08:32 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
10-14 08:32 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-14 08:32 INFO   root: Running the installer...
10-14 08:32 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Brian\AppData\Local\Temp\pyl7071.tmp\translations, languages=['en_GB', 'en']
10-14 08:32 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Brian\AppData\Local\Temp\pyl7071.tmp\translations, languages=['en_GB', 'en']
10-14 08:32 DEBUG  WinuiInstallationPage: target_drive=C:, installation_size=18000MB, distro_name=Ubuntu, language=en_GB, locale=en_GB.UTF-8, username=brian
10-14 08:32 INFO   root: Received settings
10-14 08:32 DEBUG  CommonBackend: Searching for local CD
10-14 08:32 DEBUG  Distro:   checking whether C:\Users\Brian\AppData\Local\Temp\pyl7071.tmp is a valid Ubuntu CD
10-14 08:32 DEBUG  Distro:     does not contain C:\Users\Brian\AppData\Local\Temp\pyl7071.tmp\casper\filesystem.squashfs
10-14 08:32 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
10-14 08:32 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-14 08:32 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
10-14 08:32 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-14 08:32 DEBUG  CommonBackend: Searching for local ISO
10-14 08:32 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Brian\AppData\Local\Temp\pyl7071.tmp\translations, languages=['en_GB', 'en']
10-14 08:32 DEBUG  TaskList: # Running tasklist...
10-14 08:32 DEBUG  TaskList: ## Running select_target_dir...
10-14 08:32 INFO   WindowsBackend: Installing into C:\ubuntu
10-14 08:32 DEBUG  TaskList: ## Finished select_target_dir
10-14 08:32 DEBUG  TaskList: ## Running create_dir_structure...
10-14 08:32 DEBUG  CommonBackend: Creating dir C:\ubuntu
10-14 08:32 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks
10-14 08:32 DEBUG  CommonBackend: Creating dir C:\ubuntu\install
10-14 08:32 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot
10-14 08:32 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot
10-14 08:32 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot\grub
10-14 08:32 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot\grub
10-14 08:32 DEBUG  TaskList: ## Finished create_dir_structure
10-14 08:32 DEBUG  TaskList: ## Running create_uninstaller...
10-14 08:32 DEBUG  WindowsBackend: Copying uninstaller C:\Users\Brian\Desktop\wubi.exe -> C:\ubuntu\uninstall-wubi.exe
10-14 08:32 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString C:\ubuntu\uninstall-wubi.exe
10-14 08:32 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir C:\ubuntu
10-14 08:32 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
10-14 08:32 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon C:\ubuntu\Ubuntu.ico
10-14 08:32 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 11.10-rev245
10-14 08:32 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
10-14 08:32 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout http://www.ubuntu.com
10-14 08:32 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink http://www.ubuntu.com/support
10-14 08:32 DEBUG  TaskList: ## Finished create_uninstaller
10-14 08:32 DEBUG  TaskList: ## Running create_preseed_diskimage...
10-14 08:32 DEBUG  TaskList: ## Finished create_preseed_diskimage
10-14 08:32 DEBUG  TaskList: ## Running get_diskimage...
10-14 08:32 DEBUG  TaskList: New task download
10-14 08:32 DEBUG  TaskList: ### Running download...
10-14 08:32 DEBUG  downloader: downloading http://releases.ubuntu.com/11.10/ubuntu-11.10-wubi-amd64.tar.xz > C:\ubuntu\disks\ubuntu-11.10-wubi-amd64.tar.xz
10-14 08:34 ERROR  TaskList: [Errno 14] HTTP Error 409: Conflict
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\downloader.py", line 78, in download
  File "\lib\urlgrabber\grabber.py", line 927, in urlgrab
  File "\lib\urlgrabber\grabber.py", line 845, in _retry
  File "\lib\urlgrabber\grabber.py", line 913, in retryfunc
  File "\lib\urlgrabber\grabber.py", line 1001, in __init__
  File "\lib\urlgrabber\grabber.py", line 1072, in _do_open
  File "\lib\urlgrabber\grabber.py", line 1182, in _make_request
URLGrabError: [Errno 14] HTTP Error 409: Conflict
10-14 08:34 ERROR  TaskList: Non fatal error [Errno 14] HTTP Error 409: Conflict in task download
10-14 08:34 DEBUG  TaskList: ### Finished download
10-14 08:34 DEBUG  TaskList: ## Finished get_diskimage
10-14 08:34 DEBUG  TaskList: ## Running extract_diskimage...
10-14 08:34 ERROR  TaskList: unsubscriptable object
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 439, in extract_diskimage
  File "\lib\ntpath.py", line 199, in basename
  File "\lib\ntpath.py", line 163, in split
  File "\lib\ntpath.py", line 118, in splitdrive
TypeError: unsubscriptable object
10-14 08:34 DEBUG  TaskList: # Cancelling tasklist
10-14 08:34 DEBUG  TaskList: # Finished tasklist
10-14 08:34 ERROR  root: unsubscriptable object
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 58, in run
  File "\lib\wubi\application.py", line 132, in select_task
  File "\lib\wubi\application.py", line 158, in run_installer
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 439, in extract_diskimage
  File "\lib\ntpath.py", line 199, in basename
  File "\lib\ntpath.py", line 163, in split
  File "\lib\ntpath.py", line 118, in splitdrive
TypeError: unsubscriptable object


```

---

### Post by dschulten on 2011-10-14
It seems this happens during download errors, at least in my case. For some reason, it appears that wubi cannot resolve the host.

```

10-14 10:55 DEBUG  downloader: downloading http://releases.ubuntu.com/11.10/ubuntu-11.10-wubi-amd64.tar.xz > C:\ubuntu\disks\ubuntu-11.10-wubi-amd64.tar.xz
10-14 10:55 ERROR  TaskList: [Errno 4] IOError: <urlopen error (7, 'getaddrinfo failed')>
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\downloader.py", line 78, in download
  File "\lib\urlgrabber\grabber.py", line 927, in urlgrab
  File "\lib\urlgrabber\grabber.py", line 845, in _retry
  File "\lib\urlgrabber\grabber.py", line 913, in retryfunc
  File "\lib\urlgrabber\grabber.py", line 1001, in __init__
  File "\lib\urlgrabber\grabber.py", line 1072, in _do_open
  File "\lib\urlgrabber\grabber.py", line 1188, in _make_request
URLGrabError: [Errno 4] IOError: <urlopen error (7, 'getaddrinfo failed')>
10-14 10:55 ERROR  TaskList: Non fatal error [Errno 4] IOError: <urlopen error (7, 'getaddrinfo failed')> in task download
10-14 10:55 DEBUG  TaskList: ### Finished download
10-14 10:55 DEBUG  TaskList: ## Finished get_diskimage
10-14 10:55 DEBUG  TaskList: ## Running extract_diskimage...
10-14 10:55 ERROR  TaskList: unsubscriptable object
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 439, in extract_diskimage
  File "\lib\ntpath.py", line 199, in basename
  File "\lib\ntpath.py", line 163, in split
  File "\lib\ntpath.py", line 118, in splitdrive
TypeError: unsubscriptable object
10-14 10:55 DEBUG  TaskList: # Cancelling tasklist
10-14 10:55 DEBUG  TaskList: # Finished tasklist
10-14 10:55 ERROR  root: unsubscriptable object
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 58, in run
  File "\lib\wubi\application.py", line 132, in select_task
  File "\lib\wubi\application.py", line 158, in run_installer
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 439, in extract_diskimage
  File "\lib\ntpath.py", line 199, in basename
  File "\lib\ntpath.py", line 163, in split
  File "\lib\ntpath.py", line 118, in splitdrive
TypeError: unsubscriptable object


```

---

### Post by bcbc on 2011-10-14
Trent_almighty, thanks for the log file. It's a bit strange - the http response doesn't say much other than the 409 - conflict, and this doesn't make much sense.
The 409 code (as documented [here]("http://www.w3.org/Protocols/rfc2616/rfc2616-sec10.html")) indicates:
> 10.4.10 409 Conflict

The request could not be completed due to a conflict with the current state of the resource. This code is only allowed in situations where it is expected that the user might be able to resolve the conflict and resubmit the request. The response body SHOULD include enough

information for the user to recognize the source of the conflict. Ideally, the response entity would include enough information for the user or user agent to fix the problem; however, that might not be possible and is not required.

Conflicts are most likely to occur in response to a PUT request. For example, if versioning were being used and the entity being PUT included changes to a resource which conflict with those made by an earlier (third-party) request, the server might use the 409 response to indicate that it can't complete the request. In this case, the response entity would likely contain a list of the differences between the two versions in a format defined by the response Content-Type.

Since there is no PUT request involved, and the resource seems to work fine (based on my testing) - I'm a bit puzzled. Have you had this issue repeatedly at different times over a long period or just one time? My theory is that perhaps Canonical were trying to update the image while you were downloading it, or maybe it's related to heavy web traffic.

Try again and if the same problem occurs, I'd recommend filing a [bug ]("https://bugs.launchpad.net/wubi/+filebug")and attach the logfile.
Thanks

PS might be a good idea to file a bug even if you find it works now since it's not a graceful exit and no clear idea of what the problem is.

---

### Post by bcbc on 2011-10-14
dschulten,

based on your log (resource not found) it does seem to imply that the resource might have been replaced. That could explain the 409 (if it was removed during download).
Actually the timestamp on the image file is 12-Oct-2011 18:42 so this doesn't seem to be the case. 

It's therefore more likely to be heavy server load causing these issues.

---

### Post by mikechant on 2011-10-14
I was getting weird errors last night just trying to download the routine updates for Ubuntu 10.4; I assumed it was due to server overload, retried a few times and it worked OK.

---

### Post by agribby on 2011-10-15
I think that the problem is with Windows firewall. I had the same problem with the same log and when I turned off my firewall it worked fine.

---

### Post by trent_almighty on 2011-10-17
Thanks for all the help, but it's still having a problem.  Looks like I'll have to go a different route then haha!

---

