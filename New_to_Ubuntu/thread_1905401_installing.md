---
title: "installing"
date: 2012-01-06
forum: New to Ubuntu
---

### Post by Oinkzter on 2012-01-06
Hello everyone, i need help with installing ubuntu 11.10.
When its done installing it says:

'WindowsBackend' object has no attribute 'iso_path'

Se venligst logfil: (on danish)
c:\users\mark\appdata\local\temp\wubi-11.10-rev241.log
for more information

please help me, any suggestions???

---

### Post by lisati on 2012-01-06
This looks like a "Wubi" installation. The log file mentioned in the error message can be found in your "%temp%" folder.

Which version of Ubuntu were you trying to install?

---

### Post by Oinkzter on 2012-01-06
> **lisati said:**
> This looks like a "Wubi" installation. The log file mentioned in the error message can be found in your "%temp%" folder.

Which version of Ubuntu were you trying to install?

ubuntu 11.10 32 bit

---

### Post by Oinkzter on 2012-01-06
i looked in the folder:

```
01-07 00:21 INFO   root: === wubi 11.10 rev241 ===
01-07 00:21 DEBUG  root: Logfile is c:\users\mark\appdata\local\temp\wubi-11.10-rev241.log
01-07 00:21 DEBUG  root: sys.argv = ['main.pyo', '--exefile="G:\\wubi.exe"']
01-07 00:21 DEBUG  CommonBackend: data_dir=C:\Users\Mark\AppData\Local\Temp\pylD1CF.tmp\data
01-07 00:21 DEBUG  WindowsBackend: 7z=C:\Users\Mark\AppData\Local\Temp\pylD1CF.tmp\bin\7z.exe
01-07 00:21 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
01-07 00:21 DEBUG  CommonBackend: Fetching basic info...
01-07 00:21 DEBUG  CommonBackend: original_exe=G:\wubi.exe
01-07 00:21 DEBUG  CommonBackend: platform=win32
01-07 00:21 DEBUG  CommonBackend: osname=nt
01-07 00:21 DEBUG  CommonBackend: language=da_DK
01-07 00:21 DEBUG  CommonBackend: encoding=cp1252
01-07 00:21 DEBUG  WindowsBackend: arch=amd64
01-07 00:21 DEBUG  CommonBackend: Parsing isolist=C:\Users\Mark\AppData\Local\Temp\pylD1CF.tmp\data\isolist.ini
01-07 00:21 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
01-07 00:21 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
01-07 00:21 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
01-07 00:21 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
01-07 00:21 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
01-07 00:21 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
01-07 00:21 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
01-07 00:21 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
01-07 00:21 DEBUG  WindowsBackend: Fetching host info...
01-07 00:21 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
01-07 00:21 DEBUG  WindowsBackend: windows version=vista
01-07 00:21 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium
01-07 00:21 DEBUG  WindowsBackend: windows_sp=None
01-07 00:21 DEBUG  WindowsBackend: windows_build=7601
01-07 00:21 DEBUG  WindowsBackend: gmt=1
01-07 00:21 DEBUG  WindowsBackend: country=DK
01-07 00:21 DEBUG  WindowsBackend: timezone=Europe/Copenhagen
01-07 00:21 DEBUG  WindowsBackend: windows_username=Mark
01-07 00:21 DEBUG  WindowsBackend: user_full_name=Mark
01-07 00:21 DEBUG  WindowsBackend: user_directory=C:\Users\Mark
01-07 00:21 DEBUG  WindowsBackend: windows_language_code=1030
01-07 00:21 DEBUG  WindowsBackend: windows_language=Danish
01-07 00:21 DEBUG  WindowsBackend: processor_name=Intel(R) Pentium(R) Dual  CPU  T3200  @ 2.00GHz
01-07 00:21 DEBUG  WindowsBackend: bootloader=vista
01-07 00:21 DEBUG  WindowsBackend: system_drive=Drive(C: hd 35471.5898438 mb free ntfs)
01-07 00:21 DEBUG  WindowsBackend: drive=Drive(C: hd 35471.5898438 mb free ntfs)
01-07 00:21 DEBUG  WindowsBackend: drive=Drive(D: hd 50882.6796875 mb free ntfs)
01-07 00:21 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free udf)
01-07 00:21 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free )
01-07 00:21 DEBUG  WindowsBackend: drive=Drive(G: removable 1217.96875 mb free fat)
01-07 00:21 DEBUG  WindowsBackend: uninstaller_path=None
01-07 00:21 DEBUG  WindowsBackend: previous_target_dir=None
01-07 00:21 DEBUG  WindowsBackend: previous_distro_name=None
01-07 00:21 DEBUG  WindowsBackend: keyboard_id=67503110
01-07 00:21 DEBUG  WindowsBackend: keyboard_layout=dk
01-07 00:21 DEBUG  WindowsBackend: keyboard_variant=
01-07 00:21 DEBUG  CommonBackend: python locale=('da_DK', 'cp1252')
01-07 00:21 DEBUG  CommonBackend: locale=da_DK.UTF-8
01-07 00:21 DEBUG  WindowsBackend: total_memory_mb=3839.20703125
01-07 00:21 DEBUG  CommonBackend: Searching ISOs on USB devices
01-07 00:21 DEBUG  CommonBackend: Searching for local CDs
01-07 00:21 DEBUG  Distro:   checking whether C:\Users\Mark\AppData\Local\Temp\pylD1CF.tmp is a valid Ubuntu CD
01-07 00:21 DEBUG  Distro:     does not contain C:\Users\Mark\AppData\Local\Temp\pylD1CF.tmp\casper\filesystem.squashfs
01-07 00:21 DEBUG  Distro:   checking whether C:\Users\Mark\AppData\Local\Temp\pylD1CF.tmp is a valid Ubuntu CD
01-07 00:21 DEBUG  Distro:     does not contain C:\Users\Mark\AppData\Local\Temp\pylD1CF.tmp\casper\filesystem.squashfs
01-07 00:21 DEBUG  Distro:   checking whether C:\Users\Mark\AppData\Local\Temp\pylD1CF.tmp is a valid Kubuntu CD
01-07 00:21 DEBUG  Distro:     does not contain C:\Users\Mark\AppData\Local\Temp\pylD1CF.tmp\casper\filesystem.squashfs
01-07 00:21 DEBUG  Distro:   checking whether C:\Users\Mark\AppData\Local\Temp\pylD1CF.tmp is a valid Kubuntu CD
01-07 00:21 DEBUG  Distro:     does not contain C:\Users\Mark\AppData\Local\Temp\pylD1CF.tmp\casper\filesystem.squashfs
01-07 00:21 DEBUG  Distro:   checking whether C:\Users\Mark\AppData\Local\Temp\pylD1CF.tmp is a valid Xubuntu CD
01-07 00:21 DEBUG  Distro:     does not contain C:\Users\Mark\AppData\Local\Temp\pylD1CF.tmp\casper\filesystem.squashfs
01-07 00:21 DEBUG  Distro:   checking whether C:\Users\Mark\AppData\Local\Temp\pylD1CF.tmp is a valid Xubuntu CD
01-07 00:21 DEBUG  Distro:     does not contain C:\Users\Mark\AppData\Local\Temp\pylD1CF.tmp\casper\filesystem.squashfs
01-07 00:21 DEBUG  Distro:   checking whether C:\Users\Mark\AppData\Local\Temp\pylD1CF.tmp is a valid Mythbuntu CD
01-07 00:21 DEBUG  Distro:     does not contain C:\Users\Mark\AppData\Local\Temp\pylD1CF.tmp\casper\filesystem.squashfs
01-07 00:21 DEBUG  Distro:   checking whether C:\Users\Mark\AppData\Local\Temp\pylD1CF.tmp is a valid Mythbuntu CD
01-07 00:21 DEBUG  Distro:     does not contain C:\Users\Mark\AppData\Local\Temp\pylD1CF.tmp\casper\filesystem.squashfs
01-07 00:21 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
01-07 00:21 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-07 00:21 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
01-07 00:21 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-07 00:21 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
01-07 00:21 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-07 00:21 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
01-07 00:21 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-07 00:21 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
01-07 00:21 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-07 00:21 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
01-07 00:21 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-07 00:21 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
01-07 00:21 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-07 00:21 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
01-07 00:21 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-07 00:21 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
01-07 00:21 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
01-07 00:21 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
01-07 00:21 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
01-07 00:21 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
01-07 00:21 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
01-07 00:21 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
01-07 00:21 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
01-07 00:21 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
01-07 00:21 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
01-07 00:21 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
01-07 00:21 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
01-07 00:21 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
01-07 00:21 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
01-07 00:21 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
01-07 00:21 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
01-07 00:21 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
01-07 00:21 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
01-07 00:21 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
01-07 00:21 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
01-07 00:21 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
01-07 00:21 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
01-07 00:21 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
01-07 00:21 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
01-07 00:21 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
01-07 00:21 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
01-07 00:21 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
01-07 00:21 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
01-07 00:21 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
01-07 00:21 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
01-07 00:21 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
01-07 00:21 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
01-07 00:21 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
01-07 00:21 DEBUG  Distro:   parsing info from str=Ubuntu 11.10 "Oneiric Ocelot" - Release i386 (20111012)
01-07 00:21 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '11.10', 'build': '20111012', 'codename': 'Oneiric Ocelot', 'arch': 'i386'}
01-07 00:21 INFO   Distro: Found a valid CD for Ubuntu: G:\
01-07 00:21 INFO   root: Running the CD menu...
01-07 00:21 DEBUG  WindowsFrontend: __init__...
01-07 00:21 DEBUG  WindowsFrontend: on_init...
01-07 00:21 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Mark\AppData\Local\Temp\pylD1CF.tmp\translations, languages=['da_DK', 'da']
01-07 00:21 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Mark\AppData\Local\Temp\pylD1CF.tmp\translations, languages=['da_DK', 'da']
01-07 00:22 INFO   root: CD menu finished
01-07 00:22 INFO   root: Running the installer...
01-07 00:22 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Mark\AppData\Local\Temp\pylD1CF.tmp\translations, languages=['da_DK', 'da']
01-07 00:22 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Mark\AppData\Local\Temp\pylD1CF.tmp\translations, languages=['da_DK', 'da']
01-07 00:22 DEBUG  WinuiInstallationPage: target_drive=D:, installation_size=18000MB, distro_name=Ubuntu, language=da_DK, locale=da_DK.UTF-8, username=oinkzter
01-07 00:22 INFO   root: Received settings
01-07 00:22 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Mark\AppData\Local\Temp\pylD1CF.tmp\translations, languages=['da_DK', 'da']
01-07 00:22 DEBUG  TaskList: # Running tasklist...
01-07 00:22 DEBUG  TaskList: ## Running select_target_dir...
01-07 00:22 INFO   WindowsBackend: Installing into D:\ubuntu
01-07 00:22 DEBUG  TaskList: ## Finished select_target_dir
01-07 00:22 DEBUG  TaskList: ## Running create_dir_structure...
01-07 00:22 DEBUG  CommonBackend: Creating dir D:\ubuntu
01-07 00:22 DEBUG  CommonBackend: Creating dir D:\ubuntu\disks
01-07 00:22 DEBUG  CommonBackend: Creating dir D:\ubuntu\install
01-07 00:22 DEBUG  CommonBackend: Creating dir D:\ubuntu\install\boot
01-07 00:22 DEBUG  CommonBackend: Creating dir D:\ubuntu\disks\boot
01-07 00:22 DEBUG  CommonBackend: Creating dir D:\ubuntu\disks\boot\grub
01-07 00:22 DEBUG  CommonBackend: Creating dir D:\ubuntu\install\boot\grub
01-07 00:22 DEBUG  TaskList: ## Finished create_dir_structure
01-07 00:22 DEBUG  TaskList: ## Running uncompress_target_dir...
01-07 00:22 DEBUG  TaskList: ## Finished uncompress_target_dir
01-07 00:22 DEBUG  TaskList: ## Running create_uninstaller...
01-07 00:22 DEBUG  WindowsBackend: Copying uninstaller G:\wubi.exe -> D:\ubuntu\uninstall-wubi.exe
01-07 00:22 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString D:\ubuntu\uninstall-wubi.exe
01-07 00:22 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir D:\ubuntu
01-07 00:22 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
01-07 00:22 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon D:\ubuntu\Ubuntu.ico
01-07 00:22 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 11.10-rev241
01-07 00:22 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
01-07 00:22 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com]("http://www.ubuntu.com/")
01-07 00:22 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
01-07 00:22 DEBUG  TaskList: ## Finished create_uninstaller
01-07 00:22 DEBUG  TaskList: ## Running copy_installation_files...
01-07 00:22 DEBUG  WindowsBackend: Copying C:\Users\Mark\AppData\Local\Temp\pylD1CF.tmp\data\custom-installation -> D:\ubuntu\install\custom-installation
01-07 00:22 DEBUG  WindowsBackend: Copying C:\Users\Mark\AppData\Local\Temp\pylD1CF.tmp\winboot -> D:\ubuntu\winboot
01-07 00:22 DEBUG  WindowsBackend: Copying C:\Users\Mark\AppData\Local\Temp\pylD1CF.tmp\data\images\Ubuntu.ico -> D:\ubuntu\Ubuntu.ico
01-07 00:22 DEBUG  TaskList: ## Finished copy_installation_files
01-07 00:22 DEBUG  TaskList: ## Running get_iso...
01-07 00:22 DEBUG  TaskList: New task copy_file
01-07 00:22 DEBUG  TaskList: ### Running copy_file...
01-07 00:27 DEBUG  TaskList: ### Finished copy_file
01-07 00:27 DEBUG  TaskList: New task check_iso
01-07 00:27 DEBUG  TaskList: ### Running check_iso...
01-07 00:27 DEBUG  CommonBackend: Checking D:\ubuntu\install\installation.iso
01-07 00:27 DEBUG  Distro:   checking Ubuntu ISO D:\ubuntu\install\installation.iso
01-07 00:27 DEBUG  Distro:     wrong size: 2012155904 > 900000000
01-07 00:27 DEBUG  TaskList: ### Finished check_iso
01-07 00:27 ERROR  TaskList: 'WindowsBackend' object has no attribute 'iso_path'
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 579, in get_iso
  File "\lib\wubi\backends\common\backend.py", line 565, in use_iso
AttributeError: 'WindowsBackend' object has no attribute 'iso_path'
01-07 00:27 DEBUG  TaskList: # Cancelling tasklist
01-07 00:27 DEBUG  TaskList: # Finished tasklist
01-07 00:27 ERROR  root: 'WindowsBackend' object has no attribute 'iso_path'
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 58, in run
  File "\lib\wubi\application.py", line 130, in select_task
  File "\lib\wubi\application.py", line 205, in run_cd_menu
  File "\lib\wubi\application.py", line 120, in select_task
  File "\lib\wubi\application.py", line 158, in run_installer
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 579, in get_iso
  File "\lib\wubi\backends\common\backend.py", line 565, in use_iso
AttributeError: 'WindowsBackend' object has no attribute 'iso_path'
01-07 00:30 INFO   root: === wubi 11.10 rev241 ===
01-07 00:30 DEBUG  root: Logfile is c:\users\mark\appdata\local\temp\wubi-11.10-rev241.log
01-07 00:30 DEBUG  root: sys.argv = ['main.pyo', '--exefile="G:\\wubi.exe"']
01-07 00:30 DEBUG  CommonBackend: data_dir=C:\Users\Mark\AppData\Local\Temp\pyl5791.tmp\data
01-07 00:30 DEBUG  WindowsBackend: 7z=C:\Users\Mark\AppData\Local\Temp\pyl5791.tmp\bin\7z.exe
01-07 00:30 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
01-07 00:30 DEBUG  CommonBackend: Fetching basic info...
01-07 00:30 DEBUG  CommonBackend: original_exe=G:\wubi.exe
01-07 00:30 DEBUG  CommonBackend: platform=win32
01-07 00:30 DEBUG  CommonBackend: osname=nt
01-07 00:30 DEBUG  CommonBackend: language=da_DK
01-07 00:30 DEBUG  CommonBackend: encoding=cp1252
01-07 00:30 DEBUG  WindowsBackend: arch=amd64
01-07 00:30 DEBUG  CommonBackend: Parsing isolist=C:\Users\Mark\AppData\Local\Temp\pyl5791.tmp\data\isolist.ini
01-07 00:30 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
01-07 00:30 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
01-07 00:30 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
01-07 00:30 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
01-07 00:30 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
01-07 00:30 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
01-07 00:30 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
01-07 00:30 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
01-07 00:30 DEBUG  WindowsBackend: Fetching host info...
01-07 00:30 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
01-07 00:30 DEBUG  WindowsBackend: windows version=vista
01-07 00:30 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium
01-07 00:30 DEBUG  WindowsBackend: windows_sp=None
01-07 00:30 DEBUG  WindowsBackend: windows_build=7601
01-07 00:30 DEBUG  WindowsBackend: gmt=1
01-07 00:30 DEBUG  WindowsBackend: country=DK
01-07 00:30 DEBUG  WindowsBackend: timezone=Europe/Copenhagen
01-07 00:30 DEBUG  WindowsBackend: windows_username=Mark
01-07 00:30 DEBUG  WindowsBackend: user_full_name=Mark
01-07 00:30 DEBUG  WindowsBackend: user_directory=C:\Users\Mark
01-07 00:30 DEBUG  WindowsBackend: windows_language_code=1030
01-07 00:30 DEBUG  WindowsBackend: windows_language=Danish
01-07 00:30 DEBUG  WindowsBackend: processor_name=Intel(R) Pentium(R) Dual  CPU  T3200  @ 2.00GHz
01-07 00:30 DEBUG  WindowsBackend: bootloader=vista
01-07 00:30 DEBUG  WindowsBackend: system_drive=Drive(C: hd 35469.1328125 mb free ntfs)
01-07 00:30 DEBUG  WindowsBackend: drive=Drive(C: hd 35469.1328125 mb free ntfs)
01-07 00:30 DEBUG  WindowsBackend: drive=Drive(D: hd 48961.1484375 mb free ntfs)
01-07 00:30 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free udf)
01-07 00:30 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free )
01-07 00:30 DEBUG  WindowsBackend: drive=Drive(G: removable 1217.96875 mb free fat)
01-07 00:30 DEBUG  WindowsBackend: uninstaller_path=D:\ubuntu\uninstall-wubi.exe
01-07 00:30 DEBUG  WindowsBackend: previous_target_dir=D:\ubuntu
01-07 00:30 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
01-07 00:30 DEBUG  WindowsBackend: keyboard_id=67503110
01-07 00:30 DEBUG  WindowsBackend: keyboard_layout=dk
01-07 00:30 DEBUG  WindowsBackend: keyboard_variant=
01-07 00:30 DEBUG  CommonBackend: python locale=('da_DK', 'cp1252')
01-07 00:30 DEBUG  CommonBackend: locale=da_DK.UTF-8
01-07 00:30 DEBUG  WindowsBackend: total_memory_mb=3839.20703125
01-07 00:30 DEBUG  CommonBackend: Searching ISOs on USB devices
01-07 00:30 DEBUG  CommonBackend: Searching for local CDs
01-07 00:30 DEBUG  Distro:   checking whether C:\Users\Mark\AppData\Local\Temp\pyl5791.tmp is a valid Ubuntu CD
01-07 00:30 DEBUG  Distro:     does not contain C:\Users\Mark\AppData\Local\Temp\pyl5791.tmp\casper\filesystem.squashfs
01-07 00:30 DEBUG  Distro:   checking whether C:\Users\Mark\AppData\Local\Temp\pyl5791.tmp is a valid Ubuntu CD
01-07 00:30 DEBUG  Distro:     does not contain C:\Users\Mark\AppData\Local\Temp\pyl5791.tmp\casper\filesystem.squashfs
01-07 00:30 DEBUG  Distro:   checking whether C:\Users\Mark\AppData\Local\Temp\pyl5791.tmp is a valid Kubuntu CD
01-07 00:30 DEBUG  Distro:     does not contain C:\Users\Mark\AppData\Local\Temp\pyl5791.tmp\casper\filesystem.squashfs
01-07 00:30 DEBUG  Distro:   checking whether C:\Users\Mark\AppData\Local\Temp\pyl5791.tmp is a valid Kubuntu CD
01-07 00:30 DEBUG  Distro:     does not contain C:\Users\Mark\AppData\Local\Temp\pyl5791.tmp\casper\filesystem.squashfs
01-07 00:30 DEBUG  Distro:   checking whether C:\Users\Mark\AppData\Local\Temp\pyl5791.tmp is a valid Xubuntu CD
01-07 00:30 DEBUG  Distro:     does not contain C:\Users\Mark\AppData\Local\Temp\pyl5791.tmp\casper\filesystem.squashfs
01-07 00:30 DEBUG  Distro:   checking whether C:\Users\Mark\AppData\Local\Temp\pyl5791.tmp is a valid Xubuntu CD
01-07 00:30 DEBUG  Distro:     does not contain C:\Users\Mark\AppData\Local\Temp\pyl5791.tmp\casper\filesystem.squashfs
01-07 00:30 DEBUG  Distro:   checking whether C:\Users\Mark\AppData\Local\Temp\pyl5791.tmp is a valid Mythbuntu CD
01-07 00:30 DEBUG  Distro:     does not contain C:\Users\Mark\AppData\Local\Temp\pyl5791.tmp\casper\filesystem.squashfs
01-07 00:30 DEBUG  Distro:   checking whether C:\Users\Mark\AppData\Local\Temp\pyl5791.tmp is a valid Mythbuntu CD
01-07 00:30 DEBUG  Distro:     does not contain C:\Users\Mark\AppData\Local\Temp\pyl5791.tmp\casper\filesystem.squashfs
01-07 00:30 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
01-07 00:30 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-07 00:30 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
01-07 00:30 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-07 00:30 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
01-07 00:30 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-07 00:30 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
01-07 00:30 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-07 00:30 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
01-07 00:30 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-07 00:30 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
01-07 00:30 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-07 00:30 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
01-07 00:30 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-07 00:30 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
01-07 00:30 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-07 00:30 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
01-07 00:30 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
01-07 00:30 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
01-07 00:30 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
01-07 00:30 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
01-07 00:30 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
01-07 00:30 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
01-07 00:30 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
01-07 00:30 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
01-07 00:30 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
01-07 00:30 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
01-07 00:30 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
01-07 00:30 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
01-07 00:30 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
01-07 00:30 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
01-07 00:30 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
01-07 00:30 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
01-07 00:30 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
01-07 00:30 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
01-07 00:30 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
01-07 00:30 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
01-07 00:30 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
01-07 00:30 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
01-07 00:30 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
01-07 00:30 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
01-07 00:30 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
01-07 00:30 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
01-07 00:30 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
01-07 00:30 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
01-07 00:30 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
01-07 00:30 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
01-07 00:30 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
01-07 00:30 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
01-07 00:30 DEBUG  Distro:   parsing info from str=Ubuntu 11.10 "Oneiric Ocelot" - Release i386 (20111012)
01-07 00:30 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '11.10', 'build': '20111012', 'codename': 'Oneiric Ocelot', 'arch': 'i386'}
01-07 00:30 INFO   Distro: Found a valid CD for Ubuntu: G:\
01-07 00:30 INFO   root: Running the CD menu...
01-07 00:30 DEBUG  WindowsFrontend: __init__...
01-07 00:30 DEBUG  WindowsFrontend: on_init...
01-07 00:30 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Mark\AppData\Local\Temp\pyl5791.tmp\translations, languages=['da_DK', 'da']
01-07 00:30 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Mark\AppData\Local\Temp\pyl5791.tmp\translations, languages=['da_DK', 'da']
01-07 00:31 INFO   root: CD menu finished
01-07 00:31 INFO   root: Rebooting
01-07 00:31 DEBUG  TaskList: # Running tasklist...
01-07 00:31 DEBUG  TaskList: ## Running reboot...
01-07 00:31 DEBUG  TaskList: ## Finished reboot
01-07 00:31 DEBUG  TaskList: # Finished tasklist
01-07 00:31 DEBUG  root: application.quit
01-07 00:31 DEBUG  WindowsFrontend: frontend.quit
01-07 00:31 DEBUG  WindowsFrontend: frontend.on_quit
01-07 00:31 DEBUG  root: application.on_quit
01-07 00:31 INFO   root: sys.exit
01-07 00:36 INFO   root: === wubi 11.10 rev241 ===
01-07 00:36 DEBUG  root: Logfile is c:\users\mark\appdata\local\temp\wubi-11.10-rev241.log
01-07 00:36 DEBUG  root: sys.argv = ['main.pyo', '--exefile="G:\\wubi.exe"']
01-07 00:36 DEBUG  CommonBackend: data_dir=C:\Users\Mark\AppData\Local\Temp\pyl8F63.tmp\data
01-07 00:36 DEBUG  WindowsBackend: 7z=C:\Users\Mark\AppData\Local\Temp\pyl8F63.tmp\bin\7z.exe
01-07 00:36 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
01-07 00:36 DEBUG  CommonBackend: Fetching basic info...
01-07 00:36 DEBUG  CommonBackend: original_exe=G:\wubi.exe
01-07 00:36 DEBUG  CommonBackend: platform=win32
01-07 00:36 DEBUG  CommonBackend: osname=nt
01-07 00:36 DEBUG  CommonBackend: language=da_DK
01-07 00:36 DEBUG  CommonBackend: encoding=cp1252
01-07 00:36 DEBUG  WindowsBackend: arch=amd64
01-07 00:36 DEBUG  CommonBackend: Parsing isolist=C:\Users\Mark\AppData\Local\Temp\pyl8F63.tmp\data\isolist.ini
01-07 00:36 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
01-07 00:36 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
01-07 00:36 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
01-07 00:36 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
01-07 00:36 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
01-07 00:36 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
01-07 00:36 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
01-07 00:36 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
01-07 00:36 DEBUG  WindowsBackend: Fetching host info...
01-07 00:36 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
01-07 00:36 DEBUG  WindowsBackend: windows version=vista
01-07 00:36 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium
01-07 00:36 DEBUG  WindowsBackend: windows_sp=None
01-07 00:36 DEBUG  WindowsBackend: windows_build=7601
01-07 00:36 DEBUG  WindowsBackend: gmt=1
01-07 00:36 DEBUG  WindowsBackend: country=DK
01-07 00:36 DEBUG  WindowsBackend: timezone=Europe/Copenhagen
01-07 00:36 DEBUG  WindowsBackend: windows_username=Mark
01-07 00:36 DEBUG  WindowsBackend: user_full_name=Mark
01-07 00:36 DEBUG  WindowsBackend: user_directory=C:\Users\Mark
01-07 00:36 DEBUG  WindowsBackend: windows_language_code=1030
01-07 00:36 DEBUG  WindowsBackend: windows_language=Danish
01-07 00:36 DEBUG  WindowsBackend: processor_name=Intel(R) Pentium(R) Dual  CPU  T3200  @ 2.00GHz
01-07 00:36 DEBUG  WindowsBackend: bootloader=vista
01-07 00:36 DEBUG  WindowsBackend: system_drive=Drive(C: hd 35249.7421875 mb free ntfs)
01-07 00:36 DEBUG  WindowsBackend: drive=Drive(C: hd 35249.7382813 mb free ntfs)
01-07 00:36 DEBUG  WindowsBackend: drive=Drive(D: hd 48961.1484375 mb free ntfs)
01-07 00:36 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free udf)
01-07 00:36 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free )
01-07 00:36 DEBUG  WindowsBackend: drive=Drive(G: removable 1217.96875 mb free fat)
01-07 00:36 DEBUG  WindowsBackend: uninstaller_path=D:\ubuntu\uninstall-wubi.exe
01-07 00:36 DEBUG  WindowsBackend: previous_target_dir=D:\ubuntu
01-07 00:36 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
01-07 00:36 DEBUG  WindowsBackend: keyboard_id=67503110
01-07 00:36 DEBUG  WindowsBackend: keyboard_layout=dk
01-07 00:36 DEBUG  WindowsBackend: keyboard_variant=
01-07 00:36 DEBUG  CommonBackend: python locale=('da_DK', 'cp1252')
01-07 00:36 DEBUG  CommonBackend: locale=da_DK.UTF-8
01-07 00:36 DEBUG  WindowsBackend: total_memory_mb=3839.20703125
01-07 00:36 DEBUG  CommonBackend: Searching ISOs on USB devices
01-07 00:36 DEBUG  CommonBackend: Searching for local CDs
01-07 00:36 DEBUG  Distro:   checking whether C:\Users\Mark\AppData\Local\Temp\pyl8F63.tmp is a valid Ubuntu CD
01-07 00:36 DEBUG  Distro:     does not contain C:\Users\Mark\AppData\Local\Temp\pyl8F63.tmp\casper\filesystem.squashfs
01-07 00:36 DEBUG  Distro:   checking whether C:\Users\Mark\AppData\Local\Temp\pyl8F63.tmp is a valid Ubuntu CD
01-07 00:36 DEBUG  Distro:     does not contain C:\Users\Mark\AppData\Local\Temp\pyl8F63.tmp\casper\filesystem.squashfs
01-07 00:36 DEBUG  Distro:   checking whether C:\Users\Mark\AppData\Local\Temp\pyl8F63.tmp is a valid Kubuntu CD
01-07 00:36 DEBUG  Distro:     does not contain C:\Users\Mark\AppData\Local\Temp\pyl8F63.tmp\casper\filesystem.squashfs
01-07 00:36 DEBUG  Distro:   checking whether C:\Users\Mark\AppData\Local\Temp\pyl8F63.tmp is a valid Kubuntu CD
01-07 00:36 DEBUG  Distro:     does not contain C:\Users\Mark\AppData\Local\Temp\pyl8F63.tmp\casper\filesystem.squashfs
01-07 00:36 DEBUG  Distro:   checking whether C:\Users\Mark\AppData\Local\Temp\pyl8F63.tmp is a valid Xubuntu CD
01-07 00:36 DEBUG  Distro:     does not contain C:\Users\Mark\AppData\Local\Temp\pyl8F63.tmp\casper\filesystem.squashfs
01-07 00:36 DEBUG  Distro:   checking whether C:\Users\Mark\AppData\Local\Temp\pyl8F63.tmp is a valid Xubuntu CD
01-07 00:36 DEBUG  Distro:     does not contain C:\Users\Mark\AppData\Local\Temp\pyl8F63.tmp\casper\filesystem.squashfs
01-07 00:36 DEBUG  Distro:   checking whether C:\Users\Mark\AppData\Local\Temp\pyl8F63.tmp is a valid Mythbuntu CD
01-07 00:36 DEBUG  Distro:     does not contain C:\Users\Mark\AppData\Local\Temp\pyl8F63.tmp\casper\filesystem.squashfs
01-07 00:36 DEBUG  Distro:   checking whether C:\Users\Mark\AppData\Local\Temp\pyl8F63.tmp is a valid Mythbuntu CD
01-07 00:36 DEBUG  Distro:     does not contain C:\Users\Mark\AppData\Local\Temp\pyl8F63.tmp\casper\filesystem.squashfs
01-07 00:36 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
01-07 00:36 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-07 00:36 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
01-07 00:36 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-07 00:36 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
01-07 00:36 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-07 00:36 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
01-07 00:36 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-07 00:36 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
01-07 00:36 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-07 00:36 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
01-07 00:36 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-07 00:36 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
01-07 00:36 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-07 00:36 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
01-07 00:36 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-07 00:36 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
01-07 00:36 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
01-07 00:36 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
01-07 00:36 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
01-07 00:36 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
01-07 00:36 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
01-07 00:36 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
01-07 00:36 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
01-07 00:36 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
01-07 00:36 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
01-07 00:36 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
01-07 00:36 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
01-07 00:36 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
01-07 00:36 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
01-07 00:36 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
01-07 00:36 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
01-07 00:36 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
01-07 00:36 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
01-07 00:36 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
01-07 00:36 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
01-07 00:36 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
01-07 00:36 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
01-07 00:36 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
01-07 00:36 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
01-07 00:36 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
01-07 00:36 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
01-07 00:36 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
01-07 00:36 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
01-07 00:36 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
01-07 00:36 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
01-07 00:36 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
01-07 00:36 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
01-07 00:36 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
01-07 00:36 DEBUG  Distro:   parsing info from str=Ubuntu 11.10 "Oneiric Ocelot" - Release i386 (20111012)
01-07 00:36 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '11.10', 'build': '20111012', 'codename': 'Oneiric Ocelot', 'arch': 'i386'}
01-07 00:36 INFO   Distro: Found a valid CD for Ubuntu: G:\
01-07 00:36 INFO   root: Running the CD menu...
01-07 00:36 DEBUG  WindowsFrontend: __init__...
01-07 00:36 DEBUG  WindowsFrontend: on_init...
01-07 00:36 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Mark\AppData\Local\Temp\pyl8F63.tmp\translations, languages=['da_DK', 'da']
01-07 00:36 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Mark\AppData\Local\Temp\pyl8F63.tmp\translations, languages=['da_DK', 'da']
01-07 00:36 INFO   root: CD menu finished
01-07 00:36 INFO   root: Running the installer...
01-07 00:36 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Mark\AppData\Local\Temp\pyl8F63.tmp\translations, languages=['da_DK', 'da']
01-07 00:36 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Mark\AppData\Local\Temp\pyl8F63.tmp\translations, languages=['da_DK', 'da']
01-07 00:36 DEBUG  WinuiInstallationPage: target_drive=D:, installation_size=30000MB, distro_name=Ubuntu, language=da_DK, locale=da_DK.UTF-8, username=mark
01-07 00:36 INFO   root: Received settings
01-07 00:36 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Mark\AppData\Local\Temp\pyl8F63.tmp\translations, languages=['da_DK', 'da']
01-07 00:36 DEBUG  TaskList: # Running tasklist...
01-07 00:36 DEBUG  TaskList: ## Running select_target_dir...
01-07 00:36 INFO   WindowsBackend: Installing into D:\ubuntu
01-07 00:36 DEBUG  TaskList: ## Finished select_target_dir
01-07 00:36 DEBUG  TaskList: ## Running create_dir_structure...
01-07 00:36 DEBUG  CommonBackend: Creating dir D:\ubuntu
01-07 00:36 DEBUG  CommonBackend: Creating dir D:\ubuntu\disks
01-07 00:36 DEBUG  CommonBackend: Creating dir D:\ubuntu\install
01-07 00:36 DEBUG  CommonBackend: Creating dir D:\ubuntu\install\boot
01-07 00:36 DEBUG  CommonBackend: Creating dir D:\ubuntu\disks\boot
01-07 00:36 DEBUG  CommonBackend: Creating dir D:\ubuntu\disks\boot\grub
01-07 00:36 DEBUG  CommonBackend: Creating dir D:\ubuntu\install\boot\grub
01-07 00:36 DEBUG  TaskList: ## Finished create_dir_structure
01-07 00:36 DEBUG  TaskList: ## Running uncompress_target_dir...
01-07 00:36 DEBUG  TaskList: ## Finished uncompress_target_dir
01-07 00:36 DEBUG  TaskList: ## Running create_uninstaller...
01-07 00:36 DEBUG  WindowsBackend: Copying uninstaller G:\wubi.exe -> D:\ubuntu\uninstall-wubi.exe
01-07 00:36 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString D:\ubuntu\uninstall-wubi.exe
01-07 00:36 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir D:\ubuntu
01-07 00:36 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
01-07 00:36 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon D:\ubuntu\Ubuntu.ico
01-07 00:36 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 11.10-rev241
01-07 00:36 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
01-07 00:36 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com]("http://www.ubuntu.com/")
01-07 00:36 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
01-07 00:36 DEBUG  TaskList: ## Finished create_uninstaller
01-07 00:36 DEBUG  TaskList: ## Running copy_installation_files...
01-07 00:36 DEBUG  WindowsBackend: Copying C:\Users\Mark\AppData\Local\Temp\pyl8F63.tmp\data\custom-installation -> D:\ubuntu\install\custom-installation
01-07 00:36 DEBUG  WindowsBackend: Copying C:\Users\Mark\AppData\Local\Temp\pyl8F63.tmp\winboot -> D:\ubuntu\winboot
01-07 00:36 DEBUG  WindowsBackend: Copying C:\Users\Mark\AppData\Local\Temp\pyl8F63.tmp\data\images\Ubuntu.ico -> D:\ubuntu\Ubuntu.ico
01-07 00:36 DEBUG  TaskList: ## Finished copy_installation_files
01-07 00:36 DEBUG  TaskList: ## Running get_iso...
01-07 00:36 DEBUG  TaskList: New task copy_file
01-07 00:36 DEBUG  TaskList: ### Running copy_file...
01-07 00:42 DEBUG  TaskList: ### Finished copy_file
01-07 00:42 DEBUG  TaskList: New task check_iso
01-07 00:42 DEBUG  TaskList: ### Running check_iso...
01-07 00:42 DEBUG  CommonBackend: Checking D:\ubuntu\install\installation.iso
01-07 00:42 DEBUG  Distro:   checking Ubuntu ISO D:\ubuntu\install\installation.iso
01-07 00:42 DEBUG  Distro:     wrong size: 2012155904 > 900000000
01-07 00:42 DEBUG  TaskList: ### Finished check_iso
01-07 00:42 ERROR  TaskList: 'WindowsBackend' object has no attribute 'iso_path'
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 579, in get_iso
  File "\lib\wubi\backends\common\backend.py", line 565, in use_iso
AttributeError: 'WindowsBackend' object has no attribute 'iso_path'
01-07 00:42 DEBUG  TaskList: # Cancelling tasklist
01-07 00:42 DEBUG  TaskList: # Finished tasklist
01-07 00:42 ERROR  root: 'WindowsBackend' object has no attribute 'iso_path'
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 58, in run
  File "\lib\wubi\application.py", line 130, in select_task
  File "\lib\wubi\application.py", line 205, in run_cd_menu
  File "\lib\wubi\application.py", line 120, in select_task
  File "\lib\wubi\application.py", line 158, in run_installer
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 579, in get_iso
  File "\lib\wubi\backends\common\backend.py", line 565, in use_iso
AttributeError: 'WindowsBackend' object has no attribute 'iso_path'
01-07 00:49 INFO   root: === wubi 11.10 rev241 ===
01-07 00:49 DEBUG  root: Logfile is c:\users\mark\appdata\local\temp\wubi-11.10-rev241.log
01-07 00:49 DEBUG  root: sys.argv = ['main.pyo', '--exefile="D:\\ubuntu\\uninstall-wubi.exe"']
01-07 00:49 DEBUG  CommonBackend: data_dir=C:\Users\Mark\AppData\Local\Temp\pyl2EFB.tmp\data
01-07 00:49 DEBUG  WindowsBackend: 7z=C:\Users\Mark\AppData\Local\Temp\pyl2EFB.tmp\bin\7z.exe
01-07 00:49 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
01-07 00:49 DEBUG  CommonBackend: Fetching basic info...
01-07 00:49 DEBUG  CommonBackend: original_exe=D:\ubuntu\uninstall-wubi.exe
01-07 00:49 DEBUG  CommonBackend: platform=win32
01-07 00:49 DEBUG  CommonBackend: osname=nt
01-07 00:49 DEBUG  CommonBackend: language=da_DK
01-07 00:49 DEBUG  CommonBackend: encoding=cp1252
01-07 00:49 DEBUG  WindowsBackend: arch=amd64
01-07 00:49 DEBUG  CommonBackend: Parsing isolist=C:\Users\Mark\AppData\Local\Temp\pyl2EFB.tmp\data\isolist.ini
01-07 00:49 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
01-07 00:49 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
01-07 00:49 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
01-07 00:49 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
01-07 00:49 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
01-07 00:49 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
01-07 00:49 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
01-07 00:49 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
01-07 00:49 DEBUG  WindowsBackend: Fetching host info...
01-07 00:49 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
01-07 00:49 DEBUG  WindowsBackend: windows version=vista
01-07 00:49 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium
01-07 00:49 DEBUG  WindowsBackend: windows_sp=None
01-07 00:49 DEBUG  WindowsBackend: windows_build=7601
01-07 00:49 DEBUG  WindowsBackend: gmt=1
01-07 00:49 DEBUG  WindowsBackend: country=DK
01-07 00:49 DEBUG  WindowsBackend: timezone=Europe/Copenhagen
01-07 00:49 DEBUG  WindowsBackend: windows_username=Mark
01-07 00:49 DEBUG  WindowsBackend: user_full_name=Mark
01-07 00:49 DEBUG  WindowsBackend: user_directory=C:\Users\Mark
01-07 00:49 DEBUG  WindowsBackend: windows_language_code=1030
01-07 00:49 DEBUG  WindowsBackend: windows_language=Danish
01-07 00:49 DEBUG  WindowsBackend: processor_name=Intel(R) Pentium(R) Dual  CPU  T3200  @ 2.00GHz
01-07 00:49 DEBUG  WindowsBackend: bootloader=vista
01-07 00:49 DEBUG  WindowsBackend: system_drive=Drive(C: hd 35249.0976563 mb free ntfs)
01-07 00:49 DEBUG  WindowsBackend: drive=Drive(C: hd 35249.0976563 mb free ntfs)
01-07 00:49 DEBUG  WindowsBackend: drive=Drive(D: hd 47039.6171875 mb free ntfs)
01-07 00:49 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free udf)
01-07 00:49 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free )
01-07 00:49 DEBUG  WindowsBackend: drive=Drive(G: removable 1217.96875 mb free fat)
01-07 00:49 DEBUG  WindowsBackend: uninstaller_path=D:\ubuntu\uninstall-wubi.exe
01-07 00:49 DEBUG  WindowsBackend: previous_target_dir=D:\ubuntu
01-07 00:49 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
01-07 00:49 DEBUG  WindowsBackend: keyboard_id=67503110
01-07 00:49 DEBUG  WindowsBackend: keyboard_layout=dk
01-07 00:49 DEBUG  WindowsBackend: keyboard_variant=
01-07 00:49 DEBUG  CommonBackend: python locale=('da_DK', 'cp1252')
01-07 00:49 DEBUG  CommonBackend: locale=da_DK.UTF-8
01-07 00:49 DEBUG  WindowsBackend: total_memory_mb=3839.20703125
01-07 00:49 DEBUG  CommonBackend: Searching ISOs on USB devices
01-07 00:49 DEBUG  CommonBackend: Searching for local CDs
01-07 00:49 DEBUG  Distro:   checking whether C:\Users\Mark\AppData\Local\Temp\pyl2EFB.tmp is a valid Ubuntu CD
01-07 00:49 DEBUG  Distro:     does not contain C:\Users\Mark\AppData\Local\Temp\pyl2EFB.tmp\casper\filesystem.squashfs
01-07 00:49 DEBUG  Distro:   checking whether C:\Users\Mark\AppData\Local\Temp\pyl2EFB.tmp is a valid Ubuntu CD
01-07 00:49 DEBUG  Distro:     does not contain C:\Users\Mark\AppData\Local\Temp\pyl2EFB.tmp\casper\filesystem.squashfs
01-07 00:49 DEBUG  Distro:   checking whether C:\Users\Mark\AppData\Local\Temp\pyl2EFB.tmp is a valid Kubuntu CD
01-07 00:49 DEBUG  Distro:     does not contain C:\Users\Mark\AppData\Local\Temp\pyl2EFB.tmp\casper\filesystem.squashfs
01-07 00:49 DEBUG  Distro:   checking whether C:\Users\Mark\AppData\Local\Temp\pyl2EFB.tmp is a valid Kubuntu CD
01-07 00:49 DEBUG  Distro:     does not contain C:\Users\Mark\AppData\Local\Temp\pyl2EFB.tmp\casper\filesystem.squashfs
01-07 00:49 DEBUG  Distro:   checking whether C:\Users\Mark\AppData\Local\Temp\pyl2EFB.tmp is a valid Xubuntu CD
01-07 00:49 DEBUG  Distro:     does not contain C:\Users\Mark\AppData\Local\Temp\pyl2EFB.tmp\casper\filesystem.squashfs
01-07 00:49 DEBUG  Distro:   checking whether C:\Users\Mark\AppData\Local\Temp\pyl2EFB.tmp is a valid Xubuntu CD
01-07 00:49 DEBUG  Distro:     does not contain C:\Users\Mark\AppData\Local\Temp\pyl2EFB.tmp\casper\filesystem.squashfs
01-07 00:49 DEBUG  Distro:   checking whether C:\Users\Mark\AppData\Local\Temp\pyl2EFB.tmp is a valid Mythbuntu CD
01-07 00:49 DEBUG  Distro:     does not contain C:\Users\Mark\AppData\Local\Temp\pyl2EFB.tmp\casper\filesystem.squashfs
01-07 00:49 DEBUG  Distro:   checking whether C:\Users\Mark\AppData\Local\Temp\pyl2EFB.tmp is a valid Mythbuntu CD
01-07 00:49 DEBUG  Distro:     does not contain C:\Users\Mark\AppData\Local\Temp\pyl2EFB.tmp\casper\filesystem.squashfs
01-07 00:49 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
01-07 00:49 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-07 00:49 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
01-07 00:49 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-07 00:49 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
01-07 00:49 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-07 00:49 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
01-07 00:49 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-07 00:49 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
01-07 00:49 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-07 00:49 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
01-07 00:49 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-07 00:49 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
01-07 00:49 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-07 00:49 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
01-07 00:49 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-07 00:49 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
01-07 00:49 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
01-07 00:49 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
01-07 00:49 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
01-07 00:49 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
01-07 00:49 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
01-07 00:49 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
01-07 00:49 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
01-07 00:49 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
01-07 00:49 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
01-07 00:49 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
01-07 00:49 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
01-07 00:49 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
01-07 00:49 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
01-07 00:49 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
01-07 00:49 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
01-07 00:49 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
01-07 00:49 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
01-07 00:49 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
01-07 00:49 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
01-07 00:49 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
01-07 00:49 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
01-07 00:49 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
01-07 00:49 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
01-07 00:49 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
01-07 00:49 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
01-07 00:49 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
01-07 00:49 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
01-07 00:49 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
01-07 00:49 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
01-07 00:49 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
01-07 00:49 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
01-07 00:49 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
01-07 00:49 DEBUG  Distro:   parsing info from str=Ubuntu 11.10 "Oneiric Ocelot" - Release i386 (20111012)
01-07 00:49 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '11.10', 'build': '20111012', 'codename': 'Oneiric Ocelot', 'arch': 'i386'}
01-07 00:49 INFO   Distro: Found a valid CD for Ubuntu: G:\
01-07 00:49 INFO   root: Running the uninstaller...
01-07 00:49 INFO   CommonBackend: This is the uninstaller running
01-07 00:49 DEBUG  WindowsFrontend: __init__...
01-07 00:49 DEBUG  WindowsFrontend: on_init...
01-07 00:49 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Mark\AppData\Local\Temp\pyl2EFB.tmp\translations, languages=['da_DK', 'da']
01-07 00:50 INFO   root: Received settings
01-07 00:50 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Mark\AppData\Local\Temp\pyl2EFB.tmp\translations, languages=['da_DK', 'da']
01-07 00:50 DEBUG  TaskList: # Running tasklist...
01-07 00:50 DEBUG  TaskList: ## Running Fjern indgang fra opstartsindlæser...
01-07 00:50 DEBUG  WindowsBackend: Could not find bcd id
01-07 00:50 DEBUG  WindowsBackend: undo_bootini C:
01-07 00:50 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 35249.0976563 mb free ntfs)
01-07 00:50 DEBUG  WindowsBackend: undo_bootini D:
01-07 00:50 DEBUG  WindowsBackend: undo_configsys Drive(D: hd 47039.6171875 mb free ntfs)
01-07 00:50 DEBUG  WindowsBackend: undo_bootini G:
01-07 00:50 DEBUG  WindowsBackend: undo_configsys Drive(G: removable 1217.96875 mb free fat)
01-07 00:50 DEBUG  TaskList: ## Finished Fjern indgang fra opstartsindlæser
01-07 00:50 DEBUG  TaskList: ## Running Fjern destinationsmappe...
01-07 00:50 DEBUG  CommonBackend: Deleting D:\ubuntu
01-07 00:50 DEBUG  TaskList: ## Finished Fjern destinationsmappe
01-07 00:50 DEBUG  TaskList: ## Running Fjern registreringsnøglen...
01-07 00:50 DEBUG  TaskList: ## Finished Fjern registreringsnøglen
01-07 00:50 DEBUG  TaskList: # Finished tasklist
01-07 00:50 INFO   root: Almost finished uninstalling
01-07 00:50 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Mark\AppData\Local\Temp\pyl2EFB.tmp\translations, languages=['da_DK', 'da']
01-07 00:50 INFO   root: Finished uninstallation
01-07 00:50 DEBUG  root: application.quit
01-07 00:50 DEBUG  WindowsFrontend: frontend.quit
01-07 00:50 DEBUG  WindowsFrontend: frontend.on_quit
01-07 00:50 DEBUG  root: application.on_quit
01-07 00:50 INFO   root: sys.exit
01-07 01:09 INFO   root: === wubi 11.10 rev241 ===
01-07 01:09 DEBUG  root: Logfile is c:\users\mark\appdata\local\temp\wubi-11.10-rev241.log
01-07 01:09 DEBUG  root: sys.argv = ['main.pyo', '--exefile="G:\\wubi.exe"']
01-07 01:09 DEBUG  CommonBackend: data_dir=C:\Users\Mark\AppData\Local\Temp\pyl3D4E.tmp\data
01-07 01:09 DEBUG  WindowsBackend: 7z=C:\Users\Mark\AppData\Local\Temp\pyl3D4E.tmp\bin\7z.exe
01-07 01:09 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
01-07 01:09 DEBUG  CommonBackend: Fetching basic info...
01-07 01:09 DEBUG  CommonBackend: original_exe=G:\wubi.exe
01-07 01:09 DEBUG  CommonBackend: platform=win32
01-07 01:09 DEBUG  CommonBackend: osname=nt
01-07 01:09 DEBUG  CommonBackend: language=da_DK
01-07 01:09 DEBUG  CommonBackend: encoding=cp1252
01-07 01:09 DEBUG  WindowsBackend: arch=amd64
01-07 01:09 DEBUG  CommonBackend: Parsing isolist=C:\Users\Mark\AppData\Local\Temp\pyl3D4E.tmp\data\isolist.ini
01-07 01:09 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
01-07 01:09 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
01-07 01:09 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
01-07 01:09 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
01-07 01:09 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
01-07 01:09 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
01-07 01:09 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
01-07 01:09 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
01-07 01:09 DEBUG  WindowsBackend: Fetching host info...
01-07 01:09 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
01-07 01:09 DEBUG  WindowsBackend: windows version=vista
01-07 01:09 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium
01-07 01:09 DEBUG  WindowsBackend: windows_sp=None
01-07 01:09 DEBUG  WindowsBackend: windows_build=7601
01-07 01:09 DEBUG  WindowsBackend: gmt=1
01-07 01:09 DEBUG  WindowsBackend: country=DK
01-07 01:09 DEBUG  WindowsBackend: timezone=Europe/Copenhagen
01-07 01:09 DEBUG  WindowsBackend: windows_username=Mark
01-07 01:09 DEBUG  WindowsBackend: user_full_name=Mark
01-07 01:09 DEBUG  WindowsBackend: user_directory=C:\Users\Mark
01-07 01:09 DEBUG  WindowsBackend: windows_language_code=1030
01-07 01:09 DEBUG  WindowsBackend: windows_language=Danish
01-07 01:09 DEBUG  WindowsBackend: processor_name=Intel(R) Pentium(R) Dual  CPU  T3200  @ 2.00GHz
01-07 01:09 DEBUG  WindowsBackend: bootloader=vista
01-07 01:09 DEBUG  WindowsBackend: system_drive=Drive(C: hd 35257.984375 mb free ntfs)
01-07 01:09 DEBUG  WindowsBackend: drive=Drive(C: hd 35257.984375 mb free ntfs)
01-07 01:09 DEBUG  WindowsBackend: drive=Drive(D: hd 48961.1484375 mb free ntfs)
01-07 01:09 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free udf)
01-07 01:09 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free )
01-07 01:09 DEBUG  WindowsBackend: drive=Drive(G: removable 1217.96875 mb free fat)
01-07 01:09 DEBUG  WindowsBackend: uninstaller_path=None
01-07 01:09 DEBUG  WindowsBackend: previous_target_dir=None
01-07 01:09 DEBUG  WindowsBackend: previous_distro_name=None
01-07 01:09 DEBUG  WindowsBackend: keyboard_id=67503110
01-07 01:09 DEBUG  WindowsBackend: keyboard_layout=dk
01-07 01:09 DEBUG  WindowsBackend: keyboard_variant=
01-07 01:09 DEBUG  CommonBackend: python locale=('da_DK', 'cp1252')
01-07 01:09 DEBUG  CommonBackend: locale=da_DK.UTF-8
01-07 01:09 DEBUG  WindowsBackend: total_memory_mb=3839.20703125
01-07 01:09 DEBUG  CommonBackend: Searching ISOs on USB devices
01-07 01:09 DEBUG  CommonBackend: Searching for local CDs
01-07 01:09 DEBUG  Distro:   checking whether C:\Users\Mark\AppData\Local\Temp\pyl3D4E.tmp is a valid Ubuntu CD
01-07 01:09 DEBUG  Distro:     does not contain C:\Users\Mark\AppData\Local\Temp\pyl3D4E.tmp\casper\filesystem.squashfs
01-07 01:09 DEBUG  Distro:   checking whether C:\Users\Mark\AppData\Local\Temp\pyl3D4E.tmp is a valid Ubuntu CD
01-07 01:09 DEBUG  Distro:     does not contain C:\Users\Mark\AppData\Local\Temp\pyl3D4E.tmp\casper\filesystem.squashfs
01-07 01:09 DEBUG  Distro:   checking whether C:\Users\Mark\AppData\Local\Temp\pyl3D4E.tmp is a valid Kubuntu CD
01-07 01:09 DEBUG  Distro:     does not contain C:\Users\Mark\AppData\Local\Temp\pyl3D4E.tmp\casper\filesystem.squashfs
01-07 01:09 DEBUG  Distro:   checking whether C:\Users\Mark\AppData\Local\Temp\pyl3D4E.tmp is a valid Kubuntu CD
01-07 01:09 DEBUG  Distro:     does not contain C:\Users\Mark\AppData\Local\Temp\pyl3D4E.tmp\casper\filesystem.squashfs
01-07 01:09 DEBUG  Distro:   checking whether C:\Users\Mark\AppData\Local\Temp\pyl3D4E.tmp is a valid Xubuntu CD
01-07 01:09 DEBUG  Distro:     does not contain C:\Users\Mark\AppData\Local\Temp\pyl3D4E.tmp\casper\filesystem.squashfs
01-07 01:09 DEBUG  Distro:   checking whether C:\Users\Mark\AppData\Local\Temp\pyl3D4E.tmp is a valid Xubuntu CD
01-07 01:09 DEBUG  Distro:     does not contain C:\Users\Mark\AppData\Local\Temp\pyl3D4E.tmp\casper\filesystem.squashfs
01-07 01:09 DEBUG  Distro:   checking whether C:\Users\Mark\AppData\Local\Temp\pyl3D4E.tmp is a valid Mythbuntu CD
01-07 01:09 DEBUG  Distro:     does not contain C:\Users\Mark\AppData\Local\Temp\pyl3D4E.tmp\casper\filesystem.squashfs
01-07 01:09 DEBUG  Distro:   checking whether C:\Users\Mark\AppData\Local\Temp\pyl3D4E.tmp is a valid Mythbuntu CD
01-07 01:09 DEBUG  Distro:     does not contain C:\Users\Mark\AppData\Local\Temp\pyl3D4E.tmp\casper\filesystem.squashfs
01-07 01:09 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
01-07 01:09 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-07 01:09 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
01-07 01:09 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-07 01:09 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
01-07 01:09 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-07 01:09 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
01-07 01:09 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-07 01:09 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
01-07 01:09 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-07 01:09 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
01-07 01:09 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-07 01:09 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
01-07 01:09 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-07 01:09 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
01-07 01:09 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-07 01:09 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
01-07 01:09 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
01-07 01:09 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
01-07 01:09 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
01-07 01:09 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
01-07 01:09 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
01-07 01:09 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
01-07 01:09 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
01-07 01:09 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
01-07 01:09 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
01-07 01:09 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
01-07 01:09 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
01-07 01:09 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
01-07 01:09 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
01-07 01:09 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
01-07 01:09 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
01-07 01:09 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
01-07 01:09 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
01-07 01:09 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
01-07 01:09 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
01-07 01:09 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
01-07 01:09 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
01-07 01:09 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
01-07 01:09 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
01-07 01:09 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
01-07 01:09 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
01-07 01:09 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
01-07 01:09 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
01-07 01:09 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
01-07 01:09 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
01-07 01:09 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
01-07 01:09 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
01-07 01:09 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
01-07 01:09 DEBUG  Distro:   parsing info from str=Ubuntu 11.10 "Oneiric Ocelot" - Release i386 (20111012)
01-07 01:09 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '11.10', 'build': '20111012', 'codename': 'Oneiric Ocelot', 'arch': 'i386'}
01-07 01:09 INFO   Distro: Found a valid CD for Ubuntu: G:\
01-07 01:09 INFO   root: Running the CD menu...
01-07 01:09 DEBUG  WindowsFrontend: __init__...
01-07 01:09 DEBUG  WindowsFrontend: on_init...
01-07 01:09 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Mark\AppData\Local\Temp\pyl3D4E.tmp\translations, languages=['da_DK', 'da']
01-07 01:09 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Mark\AppData\Local\Temp\pyl3D4E.tmp\translations, languages=['da_DK', 'da']
01-07 01:09 INFO   root: CD menu finished
01-07 01:09 INFO   root: Running the installer...
01-07 01:09 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Mark\AppData\Local\Temp\pyl3D4E.tmp\translations, languages=['da_DK', 'da']
01-07 01:09 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Mark\AppData\Local\Temp\pyl3D4E.tmp\translations, languages=['da_DK', 'da']
01-07 01:09 DEBUG  WinuiInstallationPage: target_drive=D:, installation_size=18000MB, distro_name=Ubuntu, language=da_DK, locale=da_DK.UTF-8, username=mark
01-07 01:09 INFO   root: Received settings
01-07 01:09 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Mark\AppData\Local\Temp\pyl3D4E.tmp\translations, languages=['da_DK', 'da']
01-07 01:09 DEBUG  TaskList: # Running tasklist...
01-07 01:09 DEBUG  TaskList: ## Running select_target_dir...
01-07 01:09 INFO   WindowsBackend: Installing into D:\ubuntu
01-07 01:09 DEBUG  TaskList: ## Finished select_target_dir
01-07 01:09 DEBUG  TaskList: ## Running create_dir_structure...
01-07 01:09 DEBUG  CommonBackend: Creating dir D:\ubuntu
01-07 01:09 DEBUG  CommonBackend: Creating dir D:\ubuntu\disks
01-07 01:09 DEBUG  CommonBackend: Creating dir D:\ubuntu\install
01-07 01:09 DEBUG  CommonBackend: Creating dir D:\ubuntu\install\boot
01-07 01:09 DEBUG  CommonBackend: Creating dir D:\ubuntu\disks\boot
01-07 01:09 DEBUG  CommonBackend: Creating dir D:\ubuntu\disks\boot\grub
01-07 01:09 DEBUG  CommonBackend: Creating dir D:\ubuntu\install\boot\grub
01-07 01:09 DEBUG  TaskList: ## Finished create_dir_structure
01-07 01:09 DEBUG  TaskList: ## Running uncompress_target_dir...
01-07 01:09 DEBUG  TaskList: ## Finished uncompress_target_dir
01-07 01:09 DEBUG  TaskList: ## Running create_uninstaller...
01-07 01:09 DEBUG  WindowsBackend: Copying uninstaller G:\wubi.exe -> D:\ubuntu\uninstall-wubi.exe
01-07 01:09 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString D:\ubuntu\uninstall-wubi.exe
01-07 01:09 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir D:\ubuntu
01-07 01:09 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
01-07 01:09 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon D:\ubuntu\Ubuntu.ico
01-07 01:09 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 11.10-rev241
01-07 01:09 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
01-07 01:09 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com]("http://www.ubuntu.com/")
01-07 01:09 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
01-07 01:09 DEBUG  TaskList: ## Finished create_uninstaller
01-07 01:09 DEBUG  TaskList: ## Running copy_installation_files...
01-07 01:09 DEBUG  WindowsBackend: Copying C:\Users\Mark\AppData\Local\Temp\pyl3D4E.tmp\data\custom-installation -> D:\ubuntu\install\custom-installation
01-07 01:09 DEBUG  WindowsBackend: Copying C:\Users\Mark\AppData\Local\Temp\pyl3D4E.tmp\winboot -> D:\ubuntu\winboot
01-07 01:09 DEBUG  WindowsBackend: Copying C:\Users\Mark\AppData\Local\Temp\pyl3D4E.tmp\data\images\Ubuntu.ico -> D:\ubuntu\Ubuntu.ico
01-07 01:09 DEBUG  TaskList: ## Finished copy_installation_files
01-07 01:09 DEBUG  TaskList: ## Running get_iso...
01-07 01:09 DEBUG  TaskList: New task copy_file
01-07 01:09 DEBUG  TaskList: ### Running copy_file...
01-07 01:15 DEBUG  TaskList: ### Finished copy_file
01-07 01:15 DEBUG  TaskList: New task check_iso
01-07 01:15 DEBUG  TaskList: ### Running check_iso...
01-07 01:15 DEBUG  CommonBackend: Checking D:\ubuntu\install\installation.iso
01-07 01:15 DEBUG  Distro:   checking Ubuntu ISO D:\ubuntu\install\installation.iso
01-07 01:15 DEBUG  Distro:     wrong size: 2012155904 > 900000000
01-07 01:15 DEBUG  TaskList: ### Finished check_iso
01-07 01:15 ERROR  TaskList: 'WindowsBackend' object has no attribute 'iso_path'
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 579, in get_iso
  File "\lib\wubi\backends\common\backend.py", line 565, in use_iso
AttributeError: 'WindowsBackend' object has no attribute 'iso_path'
01-07 01:15 DEBUG  TaskList: # Cancelling tasklist
01-07 01:15 DEBUG  TaskList: # Finished tasklist
01-07 01:15 ERROR  root: 'WindowsBackend' object has no attribute 'iso_path'
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 58, in run
  File "\lib\wubi\application.py", line 130, in select_task
  File "\lib\wubi\application.py", line 205, in run_cd_menu
  File "\lib\wubi\application.py", line 120, in select_task
  File "\lib\wubi\application.py", line 158, in run_installer
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 579, in get_iso
  File "\lib\wubi\backends\common\backend.py", line 565, in use_iso
AttributeError: 'WindowsBackend' object has no attribute 'iso_path'
```

---

### Post by Rubi1200 on 2012-01-07
Try downloading the relevant Desktop ISO and wubi.exe and place both in the same folder before running the executable file.

Let us know if this helps.

---

### Post by Oinkzter on 2012-01-07
> **Rubi1200 said:**
> Try downloading the relevant Desktop ISO and wubi.exe and place both in the same folder before running the executable file.

Let us know if this helps.

i placed it in the %temp% folder and that didn't work

any other suggestions?

---

### Post by Rubi1200 on 2012-01-07
It would be best to place them somewhere like a folder on the Desktop and then run the wubi executable.

Also, do you have admin rights?

---

### Post by Oinkzter on 2012-01-07
okay, it is now installed correct and it ask me to restart my computer.
But now the problem is: 
after it loads the ubuntu brand thing the screen just turns purple and nothing else happens...
what to do?

by the way, thank you for helping me out so far

---

### Post by bcbc on 2012-01-07
First prob was trying to install wubi from a USB. Doesn't work.


Now it's likely a graphics card issue (nvidia?). Try booting with nomodeset and then go to 'additional-drivers' and install a driver to fix. Details here: [http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132) (post #8 is wubi-specific for the first boot)

---

### Post by Oinkzter on 2012-01-08
> **bcbc said:**
> First prob was trying to install wubi from a USB. Doesn't work.


Now it's likely a graphics card issue (nvidia?). Try booting with nomodeset and then go to 'additional-drivers' and install a driver to fix. Details here: [http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132) (post #8 is wubi-specific for the first boot)


i just tried nomodeset and that worked, so i could try ubuntu xD thank you for helping me out.
Ubuntu is awesome

---

### Post by Rubi1200 on 2012-01-08
Glad you got things sorted out in the end.

Please mark this Solved using the Thread Tools near the top of the page.

Enjoy :)

---

