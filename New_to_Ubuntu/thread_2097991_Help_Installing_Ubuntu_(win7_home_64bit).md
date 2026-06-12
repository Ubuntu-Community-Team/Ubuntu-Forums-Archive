---
title: "Help Installing Ubuntu (win7 home 64bit)"
date: 2012-12-25
forum: New to Ubuntu
---

### Post by angrywabbit on 2012-12-25
Hello all!

I am currently trying to use Ubuntu, firstly i tried to create a bootable usb stick, and it will not allow me to boot from it. It just goes to a dos like prompt?

Secondly i tried partitioning win7. I used wubi, and i get an extraction error code 2, and then it quits.

Any advise?

I'm using an alienware m11x r2 64bit if thats any help

Thankyou.

---

### Post by angrywabbit on 2012-12-25
After trying to setup the usb stick it generates this log if that helps...

```
12-25 11:11 INFO   root: === wubi 12.10 rev273 ===
12-25 11:11 DEBUG  root: Logfile is c:\users\wabbit\appdata\local\temp\wubi-12.10-rev273.log
12-25 11:11 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\Users\\Wabbit\\Downloads\\wubi.exe"']
12-25 11:11 DEBUG  CommonBackend: data_dir=C:\Users\Wabbit\AppData\Local\Temp\pyl3033.tmp\data
12-25 11:11 DEBUG  WindowsBackend: 7z=C:\Users\Wabbit\AppData\Local\Temp\pyl3033.tmp\bin\7z.exe
12-25 11:11 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
12-25 11:11 DEBUG  CommonBackend: Fetching basic info...
12-25 11:11 DEBUG  CommonBackend: original_exe=C:\Users\Wabbit\Downloads\wubi.exe
12-25 11:11 DEBUG  CommonBackend: platform=win32
12-25 11:11 DEBUG  CommonBackend: osname=nt
12-25 11:11 DEBUG  CommonBackend: language=en_GB
12-25 11:11 DEBUG  CommonBackend: encoding=cp1252
12-25 11:11 DEBUG  WindowsBackend: arch=amd64
12-25 11:11 DEBUG  CommonBackend: Parsing isolist=C:\Users\Wabbit\AppData\Local\Temp\pyl3033.tmp\data\isolist.ini
12-25 11:11 DEBUG  CommonBackend:   Adding distro Edubuntu-i386
12-25 11:11 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
12-25 11:11 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
12-25 11:11 DEBUG  CommonBackend:   Adding distro Edubuntu-amd64
12-25 11:11 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
12-25 11:11 DEBUG  CommonBackend:   Adding distro Lubuntu-i386
12-25 11:11 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
12-25 11:11 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
12-25 11:11 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
12-25 11:11 DEBUG  CommonBackend:   Adding distro Lubuntu-amd64
12-25 11:11 DEBUG  WindowsBackend: Fetching host info...
12-25 11:11 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
12-25 11:11 DEBUG  WindowsBackend: windows version=vista
12-25 11:11 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium
12-25 11:11 DEBUG  WindowsBackend: windows_sp=None
12-25 11:11 DEBUG  WindowsBackend: windows_build=7601
12-25 11:11 DEBUG  WindowsBackend: gmt=0
12-25 11:11 DEBUG  WindowsBackend: country=GB
12-25 11:11 DEBUG  WindowsBackend: timezone=Europe/London
12-25 11:11 DEBUG  WindowsBackend: windows_username=Wabbit
12-25 11:11 DEBUG  WindowsBackend: user_full_name=Wabbit
12-25 11:11 DEBUG  WindowsBackend: user_directory=C:\Users\Wabbit
12-25 11:11 DEBUG  WindowsBackend: windows_language_code=1033
12-25 11:11 DEBUG  WindowsBackend: windows_language=English
12-25 11:11 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM) i7 CPU       U 640  @ 1.20GHz
12-25 11:11 DEBUG  WindowsBackend: bootloader=vista
12-25 11:11 DEBUG  WindowsBackend: system_drive=Drive(C: hd 189302.109375 mb free ntfs)
12-25 11:11 DEBUG  WindowsBackend: drive=Drive(C: hd 189302.109375 mb free ntfs)
12-25 11:11 DEBUG  WindowsBackend: drive=Drive(D: cd 0.0 mb free )
12-25 11:11 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free cdfs)
12-25 11:11 DEBUG  WindowsBackend: drive=Drive(F: removable 1145.50585938 mb free fat32)
12-25 11:11 DEBUG  WindowsBackend: uninstaller_path=None
12-25 11:11 DEBUG  WindowsBackend: previous_target_dir=None
12-25 11:11 DEBUG  WindowsBackend: previous_distro_name=None
12-25 11:11 DEBUG  WindowsBackend: keyboard_id=134809609
12-25 11:11 DEBUG  WindowsBackend: keyboard_layout=gb
12-25 11:11 DEBUG  WindowsBackend: keyboard_variant=
12-25 11:11 DEBUG  CommonBackend: python locale=('en_GB', 'cp1252')
12-25 11:11 DEBUG  CommonBackend: locale=en_GB.UTF-8
12-25 11:11 DEBUG  WindowsBackend: total_memory_mb=3893.859375
12-25 11:11 DEBUG  CommonBackend: Searching ISOs on USB devices
12-25 11:11 DEBUG  CommonBackend: Searching for local CDs
12-25 11:11 DEBUG  Distro:   checking whether C:\Users\Wabbit\AppData\Local\Temp\pyl3033.tmp is a valid Ubuntu CD
12-25 11:11 DEBUG  Distro:     does not contain C:\Users\Wabbit\AppData\Local\Temp\pyl3033.tmp\casper\filesystem.squashfs
12-25 11:11 DEBUG  Distro:   checking whether C:\Users\Wabbit\AppData\Local\Temp\pyl3033.tmp is a valid Ubuntu CD
12-25 11:11 DEBUG  Distro:     does not contain C:\Users\Wabbit\AppData\Local\Temp\pyl3033.tmp\casper\filesystem.squashfs
12-25 11:11 DEBUG  Distro:   checking whether C:\Users\Wabbit\AppData\Local\Temp\pyl3033.tmp is a valid Kubuntu CD
12-25 11:11 DEBUG  Distro:     does not contain C:\Users\Wabbit\AppData\Local\Temp\pyl3033.tmp\casper\filesystem.squashfs
12-25 11:11 DEBUG  Distro:   checking whether C:\Users\Wabbit\AppData\Local\Temp\pyl3033.tmp is a valid Kubuntu CD
12-25 11:11 DEBUG  Distro:     does not contain C:\Users\Wabbit\AppData\Local\Temp\pyl3033.tmp\casper\filesystem.squashfs
12-25 11:11 DEBUG  Distro:   checking whether C:\Users\Wabbit\AppData\Local\Temp\pyl3033.tmp is a valid Mythbuntu CD
12-25 11:11 DEBUG  Distro:     does not contain C:\Users\Wabbit\AppData\Local\Temp\pyl3033.tmp\casper\filesystem.squashfs
12-25 11:11 DEBUG  Distro:   checking whether C:\Users\Wabbit\AppData\Local\Temp\pyl3033.tmp is a valid Mythbuntu CD
12-25 11:11 DEBUG  Distro:     does not contain C:\Users\Wabbit\AppData\Local\Temp\pyl3033.tmp\casper\filesystem.squashfs
12-25 11:11 DEBUG  Distro:   checking whether C:\Users\Wabbit\AppData\Local\Temp\pyl3033.tmp is a valid Edubuntu CD
12-25 11:11 DEBUG  Distro:     does not contain C:\Users\Wabbit\AppData\Local\Temp\pyl3033.tmp\casper\filesystem.squashfs
12-25 11:11 DEBUG  Distro:   checking whether C:\Users\Wabbit\AppData\Local\Temp\pyl3033.tmp is a valid Edubuntu CD
12-25 11:11 DEBUG  Distro:     does not contain C:\Users\Wabbit\AppData\Local\Temp\pyl3033.tmp\casper\filesystem.squashfs
12-25 11:11 DEBUG  Distro:   checking whether C:\Users\Wabbit\AppData\Local\Temp\pyl3033.tmp is a valid Lubuntu CD
12-25 11:11 DEBUG  Distro:     does not contain C:\Users\Wabbit\AppData\Local\Temp\pyl3033.tmp\casper\filesystem.squashfs
12-25 11:11 DEBUG  Distro:   checking whether C:\Users\Wabbit\AppData\Local\Temp\pyl3033.tmp is a valid Lubuntu CD
12-25 11:11 DEBUG  Distro:     does not contain C:\Users\Wabbit\AppData\Local\Temp\pyl3033.tmp\casper\filesystem.squashfs
12-25 11:11 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
12-25 11:11 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-25 11:11 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
12-25 11:11 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-25 11:11 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
12-25 11:11 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-25 11:11 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
12-25 11:11 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-25 11:11 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
12-25 11:11 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-25 11:11 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
12-25 11:11 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-25 11:11 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
12-25 11:11 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-25 11:11 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
12-25 11:11 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-25 11:11 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
12-25 11:11 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-25 11:11 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
12-25 11:11 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-25 11:11 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
12-25 11:11 DEBUG  Distro:   parsing info from str=ÖË‹Fo)qµgÜ…aXÆ|ÀÛ_ÈÚôô÷¡+ôÏ¯®=ÉÂ½3ëŒgîõôûñŒÿ íþ=Rœ!)B
12-25 11:11 ERROR  Distro: 'NoneType' object has no attribute 'group'
12-25 11:11 DEBUG  Distro: could not get info None
12-25 11:11 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
12-25 11:11 DEBUG  Distro: could not get info None
12-25 11:11 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
12-25 11:11 DEBUG  Distro: could not get info None
12-25 11:11 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
12-25 11:11 DEBUG  Distro: could not get info None
12-25 11:11 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
12-25 11:11 DEBUG  Distro: could not get info None
12-25 11:11 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
12-25 11:11 DEBUG  Distro: could not get info None
12-25 11:11 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
12-25 11:11 DEBUG  Distro: could not get info None
12-25 11:11 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
12-25 11:11 DEBUG  Distro: could not get info None
12-25 11:11 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
12-25 11:11 DEBUG  Distro: could not get info None
12-25 11:11 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
12-25 11:11 DEBUG  Distro: could not get info None
12-25 11:11 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
12-25 11:11 DEBUG  Distro:   parsing info from str=ÖË‹Fo)qµgÜ…aXÆ|ÀÛ_ÈÚôô÷¡+ôÏ¯®=ÉÂ½3ëŒgîõôûñŒÿ íþ=Rœ!)B
12-25 11:11 ERROR  Distro: 'NoneType' object has no attribute 'group'
12-25 11:11 DEBUG  Distro: could not get info None
12-25 11:11 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
12-25 11:11 DEBUG  Distro: could not get info None
12-25 11:11 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
12-25 11:11 DEBUG  Distro: could not get info None
12-25 11:11 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
12-25 11:11 DEBUG  Distro: could not get info None
12-25 11:11 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
12-25 11:11 DEBUG  Distro: could not get info None
12-25 11:11 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
12-25 11:11 DEBUG  Distro: could not get info None
12-25 11:11 DEBUG  Distro:   checking whether F:\ is a valid Edubuntu CD
12-25 11:11 DEBUG  Distro: could not get info None
12-25 11:11 DEBUG  Distro:   checking whether F:\ is a valid Edubuntu CD
12-25 11:11 DEBUG  Distro: could not get info None
12-25 11:11 DEBUG  Distro:   checking whether F:\ is a valid Lubuntu CD
12-25 11:11 DEBUG  Distro: could not get info None
12-25 11:11 DEBUG  Distro:   checking whether F:\ is a valid Lubuntu CD
12-25 11:11 DEBUG  Distro: could not get info None
12-25 11:11 INFO   root: Running the installer...
12-25 11:11 DEBUG  WindowsFrontend: __init__...
12-25 11:11 DEBUG  WindowsFrontend: on_init...
12-25 11:11 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Wabbit\AppData\Local\Temp\pyl3033.tmp\translations, languages=['en_GB', 'en']
12-25 11:11 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Wabbit\AppData\Local\Temp\pyl3033.tmp\translations, languages=['en_GB', 'en']
12-25 11:12 DEBUG  WinuiInstallationPage: target_drive=C:, installation_size=18000MB, distro_name=Ubuntu, language=en_GB, locale=en_GB.UTF-8, username=wabbitlinux
12-25 11:12 INFO   root: Received settings
12-25 11:12 DEBUG  CommonBackend: Searching for local CD
12-25 11:12 DEBUG  Distro:   checking whether C:\Users\Wabbit\AppData\Local\Temp\pyl3033.tmp is a valid Ubuntu CD
12-25 11:12 DEBUG  Distro:     does not contain C:\Users\Wabbit\AppData\Local\Temp\pyl3033.tmp\casper\filesystem.squashfs
12-25 11:12 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
12-25 11:12 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-25 11:12 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
12-25 11:12 DEBUG  Distro: could not get info None
12-25 11:12 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
12-25 11:12 DEBUG  Distro: could not get info None
12-25 11:12 DEBUG  CommonBackend: Searching for local ISO
12-25 11:12 DEBUG  Distro:   checking Ubuntu ISO C:\Users\Wabbit\Downloads\ubuntu-11.10-desktop-i386.iso
12-25 11:12 DEBUG  WindowsBackend:   extracting .disk\info from C:\Users\Wabbit\Downloads\ubuntu-11.10-desktop-i386.iso
12-25 11:12 DEBUG  Distro:   parsing info from str=LTˆ#!° óÇ-Ä.T=€x÷Ò‡]†‘G¹…]îóŸ[‡·=“)ÍèêÍ‡º†ÛÆ
12-25 11:12 ERROR  Distro: 'NoneType' object has no attribute 'group'
12-25 11:12 DEBUG  Distro: could not get info None
12-25 11:12 DEBUG  Distro:   checking Ubuntu ISO C:\Users\Wabbit\Downloads\ubuntu-12.10-desktop-amd64.iso
12-25 11:12 DEBUG  WindowsBackend:   extracting .disk\info from C:\Users\Wabbit\Downloads\ubuntu-12.10-desktop-amd64.iso
12-25 11:12 DEBUG  Distro:   parsing info from str=ÖË‹Fo)qµgÜ…aXÆ|ÀÛ_ÈÚôô÷¡+ôÏ¯®=ÉÂ½3ëŒgîõôûñŒÿ íþ=Rœ!)B
12-25 11:12 ERROR  Distro: 'NoneType' object has no attribute 'group'
12-25 11:12 DEBUG  Distro: could not get info None
12-25 11:12 DEBUG  Distro:   checking Ubuntu ISO C:\Users\Wabbit\Downloads\ubuntu-12.10-desktop-i386.iso
12-25 11:12 DEBUG  WindowsBackend:   extracting .disk\info from C:\Users\Wabbit\Downloads\ubuntu-12.10-desktop-i386.iso
12-25 11:12 DEBUG  Distro:   parsing info from str=~^-e–3~˜Ãä²Ë9Îâ³’¨áCÕ÷å×g¿ú¹¥?ü_Žï®:íà&ºAìMÂn(ë-…X}ò
12-25 11:12 ERROR  Distro: 'NoneType' object has no attribute 'group'
12-25 11:12 DEBUG  Distro: could not get info None
12-25 11:12 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Wabbit\AppData\Local\Temp\pyl3033.tmp\translations, languages=['en_GB', 'en']
12-25 11:12 DEBUG  TaskList: # Running tasklist...
12-25 11:12 DEBUG  TaskList: ## Running select_target_dir...
12-25 11:12 INFO   WindowsBackend: Installing into C:\ubuntu
12-25 11:12 DEBUG  TaskList: ## Finished select_target_dir
12-25 11:12 DEBUG  TaskList: ## Running create_dir_structure...
12-25 11:12 DEBUG  CommonBackend: Creating dir C:\ubuntu
12-25 11:12 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks
12-25 11:12 DEBUG  CommonBackend: Creating dir C:\ubuntu\install
12-25 11:12 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot
12-25 11:12 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot
12-25 11:12 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot\grub
12-25 11:12 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot\grub
12-25 11:12 DEBUG  TaskList: ## Finished create_dir_structure
12-25 11:12 DEBUG  TaskList: ## Running create_uninstaller...
12-25 11:12 DEBUG  WindowsBackend: Copying uninstaller C:\Users\Wabbit\Downloads\wubi.exe -> C:\ubuntu\uninstall-wubi.exe
12-25 11:12 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString C:\ubuntu\uninstall-wubi.exe
12-25 11:12 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir C:\ubuntu
12-25 11:12 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
12-25 11:12 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon C:\ubuntu\Ubuntu.ico
12-25 11:12 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 12.10-rev273
12-25 11:12 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
12-25 11:12 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com](http://www.ubuntu.com)
12-25 11:12 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
12-25 11:12 DEBUG  TaskList: ## Finished create_uninstaller
12-25 11:12 DEBUG  TaskList: ## Running create_preseed_diskimage...
12-25 11:12 DEBUG  TaskList: ## Finished create_preseed_diskimage
12-25 11:12 DEBUG  TaskList: ## Running get_diskimage...
12-25 11:12 DEBUG  TaskList: New task download
12-25 11:12 DEBUG  TaskList: ### Running download...
12-25 11:12 DEBUG  downloader: downloading [http://releases.ubuntu.com/12.10/ubuntu-12.10-wubi-amd64.tar.xz](http://releases.ubuntu.com/12.10/ubuntu-12.10-wubi-amd64.tar.xz) > C:\ubuntu\disks\ubuntu-12.10-wubi-amd64.tar.xz
12-25 11:12 DEBUG  downloader: Download start filename=C:\ubuntu\disks\ubuntu-12.10-wubi-amd64.tar.xz, url=http://releases.ubuntu.com/12.10/ubuntu-12.10-wubi-amd64.tar.xz, basename=ubuntu-12.10-wubi-amd64.tar.xz, length=562061340, text=None
12-25 11:16 DEBUG  downloader: download finished (read 562059880 bytes)
12-25 11:16 DEBUG  TaskList: ### Finished download
12-25 11:16 DEBUG  TaskList: ## Finished get_diskimage
12-25 11:16 DEBUG  TaskList: ## Running extract_diskimage...
12-25 11:16 ERROR  TaskList: Extraction failed with code: 2
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 450, in extract_diskimage
Exception: Extraction failed with code: 2
12-25 11:16 DEBUG  TaskList: # Cancelling tasklist
12-25 11:16 DEBUG  TaskList: # Finished tasklist
12-25 11:16 ERROR  root: Extraction failed with code: 2
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 58, in run
  File "\lib\wubi\application.py", line 132, in select_task
  File "\lib\wubi\application.py", line 158, in run_installer
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 450, in extract_diskimage
Exception: Extraction failed with code: 2
12-25 11:22 INFO   root: === wubi 12.10 rev273 ===
12-25 11:22 DEBUG  root: Logfile is c:\users\wabbit\appdata\local\temp\wubi-12.10-rev273.log
12-25 11:22 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\Users\\Wabbit\\Downloads\\wubi.exe"']
12-25 11:22 DEBUG  CommonBackend: data_dir=C:\Users\Wabbit\AppData\Local\Temp\pyl61BE.tmp\data
12-25 11:22 DEBUG  WindowsBackend: 7z=C:\Users\Wabbit\AppData\Local\Temp\pyl61BE.tmp\bin\7z.exe
12-25 11:22 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
12-25 11:22 DEBUG  CommonBackend: Fetching basic info...
12-25 11:22 DEBUG  CommonBackend: original_exe=C:\Users\Wabbit\Downloads\wubi.exe
12-25 11:22 DEBUG  CommonBackend: platform=win32
12-25 11:22 DEBUG  CommonBackend: osname=nt
12-25 11:22 DEBUG  CommonBackend: language=en_GB
12-25 11:22 DEBUG  CommonBackend: encoding=cp1252
12-25 11:22 DEBUG  WindowsBackend: arch=amd64
12-25 11:22 DEBUG  CommonBackend: Parsing isolist=C:\Users\Wabbit\AppData\Local\Temp\pyl61BE.tmp\data\isolist.ini
12-25 11:22 DEBUG  CommonBackend:   Adding distro Edubuntu-i386
12-25 11:22 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
12-25 11:22 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
12-25 11:22 DEBUG  CommonBackend:   Adding distro Edubuntu-amd64
12-25 11:22 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
12-25 11:22 DEBUG  CommonBackend:   Adding distro Lubuntu-i386
12-25 11:22 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
12-25 11:22 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
12-25 11:22 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
12-25 11:22 DEBUG  CommonBackend:   Adding distro Lubuntu-amd64
12-25 11:22 DEBUG  WindowsBackend: Fetching host info...
12-25 11:22 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
12-25 11:22 DEBUG  WindowsBackend: windows version=vista
12-25 11:22 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium
12-25 11:22 DEBUG  WindowsBackend: windows_sp=None
12-25 11:22 DEBUG  WindowsBackend: windows_build=7601
12-25 11:22 DEBUG  WindowsBackend: gmt=0
12-25 11:22 DEBUG  WindowsBackend: country=GB
12-25 11:22 DEBUG  WindowsBackend: timezone=Europe/London
12-25 11:22 DEBUG  WindowsBackend: windows_username=Wabbit
12-25 11:22 DEBUG  WindowsBackend: user_full_name=Wabbit
12-25 11:22 DEBUG  WindowsBackend: user_directory=C:\Users\Wabbit
12-25 11:22 DEBUG  WindowsBackend: windows_language_code=1033
12-25 11:22 DEBUG  WindowsBackend: windows_language=English
12-25 11:22 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM) i7 CPU       U 640  @ 1.20GHz
12-25 11:22 DEBUG  WindowsBackend: bootloader=vista
12-25 11:22 DEBUG  WindowsBackend: system_drive=Drive(C: hd 187512.789063 mb free ntfs)
12-25 11:22 DEBUG  WindowsBackend: drive=Drive(C: hd 187512.789063 mb free ntfs)
12-25 11:22 DEBUG  WindowsBackend: drive=Drive(D: cd 0.0 mb free )
12-25 11:22 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free cdfs)
12-25 11:22 DEBUG  WindowsBackend: drive=Drive(F: removable 1145.50585938 mb free fat32)
12-25 11:22 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
12-25 11:22 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
12-25 11:22 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
12-25 11:22 DEBUG  WindowsBackend: keyboard_id=134809609
12-25 11:22 DEBUG  WindowsBackend: keyboard_layout=gb
12-25 11:22 DEBUG  WindowsBackend: keyboard_variant=
12-25 11:22 DEBUG  CommonBackend: python locale=('en_GB', 'cp1252')
12-25 11:22 DEBUG  CommonBackend: locale=en_GB.UTF-8
12-25 11:22 DEBUG  WindowsBackend: total_memory_mb=3893.859375
12-25 11:22 DEBUG  CommonBackend: Searching ISOs on USB devices
12-25 11:22 DEBUG  CommonBackend: Searching for local CDs
12-25 11:22 DEBUG  Distro:   checking whether C:\Users\Wabbit\AppData\Local\Temp\pyl61BE.tmp is a valid Ubuntu CD
12-25 11:22 DEBUG  Distro:     does not contain C:\Users\Wabbit\AppData\Local\Temp\pyl61BE.tmp\casper\filesystem.squashfs
12-25 11:22 DEBUG  Distro:   checking whether C:\Users\Wabbit\AppData\Local\Temp\pyl61BE.tmp is a valid Ubuntu CD
12-25 11:22 DEBUG  Distro:     does not contain C:\Users\Wabbit\AppData\Local\Temp\pyl61BE.tmp\casper\filesystem.squashfs
12-25 11:22 DEBUG  Distro:   checking whether C:\Users\Wabbit\AppData\Local\Temp\pyl61BE.tmp is a valid Kubuntu CD
12-25 11:22 DEBUG  Distro:     does not contain C:\Users\Wabbit\AppData\Local\Temp\pyl61BE.tmp\casper\filesystem.squashfs
12-25 11:22 DEBUG  Distro:   checking whether C:\Users\Wabbit\AppData\Local\Temp\pyl61BE.tmp is a valid Kubuntu CD
12-25 11:22 DEBUG  Distro:     does not contain C:\Users\Wabbit\AppData\Local\Temp\pyl61BE.tmp\casper\filesystem.squashfs
12-25 11:22 DEBUG  Distro:   checking whether C:\Users\Wabbit\AppData\Local\Temp\pyl61BE.tmp is a valid Mythbuntu CD
12-25 11:22 DEBUG  Distro:     does not contain C:\Users\Wabbit\AppData\Local\Temp\pyl61BE.tmp\casper\filesystem.squashfs
12-25 11:22 DEBUG  Distro:   checking whether C:\Users\Wabbit\AppData\Local\Temp\pyl61BE.tmp is a valid Mythbuntu CD
12-25 11:22 DEBUG  Distro:     does not contain C:\Users\Wabbit\AppData\Local\Temp\pyl61BE.tmp\casper\filesystem.squashfs
12-25 11:22 DEBUG  Distro:   checking whether C:\Users\Wabbit\AppData\Local\Temp\pyl61BE.tmp is a valid Edubuntu CD
12-25 11:22 DEBUG  Distro:     does not contain C:\Users\Wabbit\AppData\Local\Temp\pyl61BE.tmp\casper\filesystem.squashfs
12-25 11:22 DEBUG  Distro:   checking whether C:\Users\Wabbit\AppData\Local\Temp\pyl61BE.tmp is a valid Edubuntu CD
12-25 11:22 DEBUG  Distro:     does not contain C:\Users\Wabbit\AppData\Local\Temp\pyl61BE.tmp\casper\filesystem.squashfs
12-25 11:22 DEBUG  Distro:   checking whether C:\Users\Wabbit\AppData\Local\Temp\pyl61BE.tmp is a valid Lubuntu CD
12-25 11:22 DEBUG  Distro:     does not contain C:\Users\Wabbit\AppData\Local\Temp\pyl61BE.tmp\casper\filesystem.squashfs
12-25 11:22 DEBUG  Distro:   checking whether C:\Users\Wabbit\AppData\Local\Temp\pyl61BE.tmp is a valid Lubuntu CD
12-25 11:22 DEBUG  Distro:     does not contain C:\Users\Wabbit\AppData\Local\Temp\pyl61BE.tmp\casper\filesystem.squashfs
12-25 11:22 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
12-25 11:22 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-25 11:22 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
12-25 11:22 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-25 11:22 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
12-25 11:22 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-25 11:22 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
12-25 11:22 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-25 11:22 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
12-25 11:22 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-25 11:22 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
12-25 11:22 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-25 11:22 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
12-25 11:22 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-25 11:22 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
12-25 11:22 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-25 11:22 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
12-25 11:22 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-25 11:22 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
12-25 11:22 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-25 11:22 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
12-25 11:22 DEBUG  Distro:   parsing info from str=ÖË‹Fo)qµgÜ…aXÆ|ÀÛ_ÈÚôô÷¡+ôÏ¯®=ÉÂ½3ëŒgîõôûñŒÿ íþ=Rœ!)B
12-25 11:22 ERROR  Distro: 'NoneType' object has no attribute 'group'
12-25 11:22 DEBUG  Distro: could not get info None
12-25 11:22 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
12-25 11:22 DEBUG  Distro: could not get info None
12-25 11:22 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
12-25 11:22 DEBUG  Distro: could not get info None
12-25 11:22 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
12-25 11:22 DEBUG  Distro: could not get info None
12-25 11:22 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
12-25 11:22 DEBUG  Distro: could not get info None
12-25 11:22 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
12-25 11:22 DEBUG  Distro: could not get info None
12-25 11:22 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
12-25 11:22 DEBUG  Distro: could not get info None
12-25 11:22 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
12-25 11:22 DEBUG  Distro: could not get info None
12-25 11:22 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
12-25 11:22 DEBUG  Distro: could not get info None
12-25 11:22 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
12-25 11:22 DEBUG  Distro: could not get info None
12-25 11:22 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
12-25 11:22 DEBUG  Distro:   parsing info from str=ÖË‹Fo)qµgÜ…aXÆ|ÀÛ_ÈÚôô÷¡+ôÏ¯®=ÉÂ½3ëŒgîõôûñŒÿ íþ=Rœ!)B
12-25 11:22 ERROR  Distro: 'NoneType' object has no attribute 'group'
12-25 11:22 DEBUG  Distro: could not get info None
12-25 11:22 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
12-25 11:22 DEBUG  Distro: could not get info None
12-25 11:22 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
12-25 11:22 DEBUG  Distro: could not get info None
12-25 11:22 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
12-25 11:22 DEBUG  Distro: could not get info None
12-25 11:22 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
12-25 11:22 DEBUG  Distro: could not get info None
12-25 11:22 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
12-25 11:22 DEBUG  Distro: could not get info None
12-25 11:22 DEBUG  Distro:   checking whether F:\ is a valid Edubuntu CD
12-25 11:22 DEBUG  Distro: could not get info None
12-25 11:22 DEBUG  Distro:   checking whether F:\ is a valid Edubuntu CD
12-25 11:22 DEBUG  Distro: could not get info None
12-25 11:22 DEBUG  Distro:   checking whether F:\ is a valid Lubuntu CD
12-25 11:22 DEBUG  Distro: could not get info None
12-25 11:22 DEBUG  Distro:   checking whether F:\ is a valid Lubuntu CD
12-25 11:22 DEBUG  Distro: could not get info None
12-25 11:22 INFO   root: Already installed, running the uninstaller...
12-25 11:22 INFO   root: Running the uninstaller...
12-25 11:22 INFO   CommonBackend: This is the uninstaller running
12-25 11:22 DEBUG  WindowsFrontend: __init__...
12-25 11:22 DEBUG  WindowsFrontend: on_init...
12-25 11:22 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Wabbit\AppData\Local\Temp\pyl61BE.tmp\translations, languages=['en_GB', 'en']
12-25 11:22 INFO   WindowsFrontend: Operation cancelled
12-25 11:22 DEBUG  WindowsFrontend: frontend.quit
12-25 11:22 DEBUG  WindowsFrontend: frontend.on_quit
12-25 11:22 DEBUG  root: application.on_quit
12-25 11:22 INFO   root: sys.exit
12-25 11:23 INFO   root: === wubi 12.10 rev273 ===
12-25 11:23 DEBUG  root: Logfile is c:\users\wabbit\appdata\local\temp\wubi-12.10-rev273.log
12-25 11:23 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\Users\\Wabbit\\Downloads\\wubi.exe"']
12-25 11:23 DEBUG  CommonBackend: data_dir=C:\Users\Wabbit\AppData\Local\Temp\pyl65B4.tmp\data
12-25 11:23 DEBUG  WindowsBackend: 7z=C:\Users\Wabbit\AppData\Local\Temp\pyl65B4.tmp\bin\7z.exe
12-25 11:23 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
12-25 11:23 DEBUG  CommonBackend: Fetching basic info...
12-25 11:23 DEBUG  CommonBackend: original_exe=C:\Users\Wabbit\Downloads\wubi.exe
12-25 11:23 DEBUG  CommonBackend: platform=win32
12-25 11:23 DEBUG  CommonBackend: osname=nt
12-25 11:23 DEBUG  CommonBackend: language=en_GB
12-25 11:23 DEBUG  CommonBackend: encoding=cp1252
12-25 11:23 DEBUG  WindowsBackend: arch=amd64
12-25 11:23 DEBUG  CommonBackend: Parsing isolist=C:\Users\Wabbit\AppData\Local\Temp\pyl65B4.tmp\data\isolist.ini
12-25 11:23 DEBUG  CommonBackend:   Adding distro Edubuntu-i386
12-25 11:23 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
12-25 11:23 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
12-25 11:23 DEBUG  CommonBackend:   Adding distro Edubuntu-amd64
12-25 11:23 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
12-25 11:23 DEBUG  CommonBackend:   Adding distro Lubuntu-i386
12-25 11:23 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
12-25 11:23 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
12-25 11:23 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
12-25 11:23 DEBUG  CommonBackend:   Adding distro Lubuntu-amd64
12-25 11:23 DEBUG  WindowsBackend: Fetching host info...
12-25 11:23 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
12-25 11:23 DEBUG  WindowsBackend: windows version=vista
12-25 11:23 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium
12-25 11:23 DEBUG  WindowsBackend: windows_sp=None
12-25 11:23 DEBUG  WindowsBackend: windows_build=7601
12-25 11:23 DEBUG  WindowsBackend: gmt=0
12-25 11:23 DEBUG  WindowsBackend: country=GB
12-25 11:23 DEBUG  WindowsBackend: timezone=Europe/London
12-25 11:23 DEBUG  WindowsBackend: windows_username=Wabbit
12-25 11:23 DEBUG  WindowsBackend: user_full_name=Wabbit
12-25 11:23 DEBUG  WindowsBackend: user_directory=C:\Users\Wabbit
12-25 11:23 DEBUG  WindowsBackend: windows_language_code=1033
12-25 11:23 DEBUG  WindowsBackend: windows_language=English
12-25 11:23 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM) i7 CPU       U 640  @ 1.20GHz
12-25 11:23 DEBUG  WindowsBackend: bootloader=vista
12-25 11:23 DEBUG  WindowsBackend: system_drive=Drive(C: hd 187520.0625 mb free ntfs)
12-25 11:23 DEBUG  WindowsBackend: drive=Drive(C: hd 187520.0625 mb free ntfs)
12-25 11:23 DEBUG  WindowsBackend: drive=Drive(D: cd 0.0 mb free )
12-25 11:23 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free cdfs)
12-25 11:23 DEBUG  WindowsBackend: drive=Drive(F: removable 1145.50585938 mb free fat32)
12-25 11:23 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
12-25 11:23 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
12-25 11:23 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
12-25 11:23 DEBUG  WindowsBackend: keyboard_id=134809609
12-25 11:23 DEBUG  WindowsBackend: keyboard_layout=gb
12-25 11:23 DEBUG  WindowsBackend: keyboard_variant=
12-25 11:23 DEBUG  CommonBackend: python locale=('en_GB', 'cp1252')
12-25 11:23 DEBUG  CommonBackend: locale=en_GB.UTF-8
12-25 11:23 DEBUG  WindowsBackend: total_memory_mb=3893.859375
12-25 11:23 DEBUG  CommonBackend: Searching ISOs on USB devices
12-25 11:23 DEBUG  CommonBackend: Searching for local CDs
12-25 11:23 DEBUG  Distro:   checking whether C:\Users\Wabbit\AppData\Local\Temp\pyl65B4.tmp is a valid Ubuntu CD
12-25 11:23 DEBUG  Distro:     does not contain C:\Users\Wabbit\AppData\Local\Temp\pyl65B4.tmp\casper\filesystem.squashfs
12-25 11:23 DEBUG  Distro:   checking whether C:\Users\Wabbit\AppData\Local\Temp\pyl65B4.tmp is a valid Ubuntu CD
12-25 11:23 DEBUG  Distro:     does not contain C:\Users\Wabbit\AppData\Local\Temp\pyl65B4.tmp\casper\filesystem.squashfs
12-25 11:23 DEBUG  Distro:   checking whether C:\Users\Wabbit\AppData\Local\Temp\pyl65B4.tmp is a valid Kubuntu CD
12-25 11:23 DEBUG  Distro:     does not contain C:\Users\Wabbit\AppData\Local\Temp\pyl65B4.tmp\casper\filesystem.squashfs
12-25 11:23 DEBUG  Distro:   checking whether C:\Users\Wabbit\AppData\Local\Temp\pyl65B4.tmp is a valid Kubuntu CD
12-25 11:23 DEBUG  Distro:     does not contain C:\Users\Wabbit\AppData\Local\Temp\pyl65B4.tmp\casper\filesystem.squashfs
12-25 11:23 DEBUG  Distro:   checking whether C:\Users\Wabbit\AppData\Local\Temp\pyl65B4.tmp is a valid Mythbuntu CD
12-25 11:23 DEBUG  Distro:     does not contain C:\Users\Wabbit\AppData\Local\Temp\pyl65B4.tmp\casper\filesystem.squashfs
12-25 11:23 DEBUG  Distro:   checking whether C:\Users\Wabbit\AppData\Local\Temp\pyl65B4.tmp is a valid Mythbuntu CD
12-25 11:23 DEBUG  Distro:     does not contain C:\Users\Wabbit\AppData\Local\Temp\pyl65B4.tmp\casper\filesystem.squashfs
12-25 11:23 DEBUG  Distro:   checking whether C:\Users\Wabbit\AppData\Local\Temp\pyl65B4.tmp is a valid Edubuntu CD
12-25 11:23 DEBUG  Distro:     does not contain C:\Users\Wabbit\AppData\Local\Temp\pyl65B4.tmp\casper\filesystem.squashfs
12-25 11:23 DEBUG  Distro:   checking whether C:\Users\Wabbit\AppData\Local\Temp\pyl65B4.tmp is a valid Edubuntu CD
12-25 11:23 DEBUG  Distro:     does not contain C:\Users\Wabbit\AppData\Local\Temp\pyl65B4.tmp\casper\filesystem.squashfs
12-25 11:23 DEBUG  Distro:   checking whether C:\Users\Wabbit\AppData\Local\Temp\pyl65B4.tmp is a valid Lubuntu CD
12-25 11:23 DEBUG  Distro:     does not contain C:\Users\Wabbit\AppData\Local\Temp\pyl65B4.tmp\casper\filesystem.squashfs
12-25 11:23 DEBUG  Distro:   checking whether C:\Users\Wabbit\AppData\Local\Temp\pyl65B4.tmp is a valid Lubuntu CD
12-25 11:23 DEBUG  Distro:     does not contain C:\Users\Wabbit\AppData\Local\Temp\pyl65B4.tmp\casper\filesystem.squashfs
12-25 11:23 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
12-25 11:23 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-25 11:23 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
12-25 11:23 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-25 11:23 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
12-25 11:23 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-25 11:23 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
12-25 11:23 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-25 11:23 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
12-25 11:23 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-25 11:23 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
12-25 11:23 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-25 11:23 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
12-25 11:23 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-25 11:23 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
12-25 11:23 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-25 11:23 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
12-25 11:23 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-25 11:23 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
12-25 11:23 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-25 11:23 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
12-25 11:23 DEBUG  Distro:   parsing info from str=ÖË‹Fo)qµgÜ…aXÆ|ÀÛ_ÈÚôô÷¡+ôÏ¯®=ÉÂ½3ëŒgîõôûñŒÿ íþ=Rœ!)B
12-25 11:23 ERROR  Distro: 'NoneType' object has no attribute 'group'
12-25 11:23 DEBUG  Distro: could not get info None
12-25 11:23 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
12-25 11:23 DEBUG  Distro: could not get info None
12-25 11:23 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
12-25 11:23 DEBUG  Distro: could not get info None
12-25 11:23 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
12-25 11:23 DEBUG  Distro: could not get info None
12-25 11:23 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
12-25 11:23 DEBUG  Distro: could not get info None
12-25 11:23 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
12-25 11:23 DEBUG  Distro: could not get info None
12-25 11:23 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
12-25 11:23 DEBUG  Distro: could not get info None
12-25 11:23 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
12-25 11:23 DEBUG  Distro: could not get info None
12-25 11:23 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
12-25 11:23 DEBUG  Distro: could not get info None
12-25 11:23 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
12-25 11:23 DEBUG  Distro: could not get info None
12-25 11:23 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
12-25 11:23 DEBUG  Distro:   parsing info from str=ÖË‹Fo)qµgÜ…aXÆ|ÀÛ_ÈÚôô÷¡+ôÏ¯®=ÉÂ½3ëŒgîõôûñŒÿ íþ=Rœ!)B
12-25 11:23 ERROR  Distro: 'NoneType' object has no attribute 'group'
12-25 11:23 DEBUG  Distro: could not get info None
12-25 11:23 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
12-25 11:23 DEBUG  Distro: could not get info None
12-25 11:23 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
12-25 11:23 DEBUG  Distro: could not get info None
12-25 11:23 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
12-25 11:23 DEBUG  Distro: could not get info None
12-25 11:23 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
12-25 11:23 DEBUG  Distro: could not get info None
12-25 11:23 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
12-25 11:23 DEBUG  Distro: could not get info None
12-25 11:23 DEBUG  Distro:   checking whether F:\ is a valid Edubuntu CD
12-25 11:23 DEBUG  Distro: could not get info None
12-25 11:23 DEBUG  Distro:   checking whether F:\ is a valid Edubuntu CD
12-25 11:23 DEBUG  Distro: could not get info None
12-25 11:23 DEBUG  Distro:   checking whether F:\ is a valid Lubuntu CD
12-25 11:23 DEBUG  Distro: could not get info None
12-25 11:23 DEBUG  Distro:   checking whether F:\ is a valid Lubuntu CD
12-25 11:23 DEBUG  Distro: could not get info None
12-25 11:23 INFO   root: Already installed, running the uninstaller...
12-25 11:23 INFO   root: Running the uninstaller...
12-25 11:23 INFO   CommonBackend: This is the uninstaller running
12-25 11:23 DEBUG  WindowsFrontend: __init__...
12-25 11:23 DEBUG  WindowsFrontend: on_init...
12-25 11:23 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Wabbit\AppData\Local\Temp\pyl65B4.tmp\translations, languages=['en_GB', 'en']
12-25 11:23 INFO   root: Received settings
12-25 11:23 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Wabbit\AppData\Local\Temp\pyl65B4.tmp\translations, languages=['en_GB', 'en']
12-25 11:23 DEBUG  TaskList: # Running tasklist...
12-25 11:23 DEBUG  TaskList: ## Running Remove bootloader entry....
12-25 11:23 DEBUG  WindowsBackend: Could not find bcd id
12-25 11:23 DEBUG  WindowsBackend: undo_bootini C:
12-25 11:23 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 187520.0625 mb free ntfs)
12-25 11:23 DEBUG  WindowsBackend: undo_bootini F:
12-25 11:23 DEBUG  WindowsBackend: undo_configsys Drive(F: removable 1145.50585938 mb free fat32)
12-25 11:23 DEBUG  TaskList: ## Finished Remove bootloader entry.
12-25 11:23 DEBUG  TaskList: ## Running Remove target dir....
12-25 11:23 DEBUG  CommonBackend: Deleting C:\ubuntu
12-25 11:23 DEBUG  TaskList: ## Finished Remove target dir.
12-25 11:23 DEBUG  TaskList: ## Running Remove registry key....
12-25 11:23 DEBUG  TaskList: ## Finished Remove registry key.
12-25 11:23 DEBUG  TaskList: # Finished tasklist
12-25 11:23 INFO   root: Almost finished uninstalling
12-25 11:23 INFO   root: Finished uninstallation
12-25 11:23 DEBUG  CommonBackend: Fetching basic info...
12-25 11:23 DEBUG  CommonBackend: original_exe=C:\Users\Wabbit\Downloads\wubi.exe
12-25 11:23 DEBUG  CommonBackend: platform=win32
12-25 11:23 DEBUG  CommonBackend: osname=nt
12-25 11:23 DEBUG  WindowsBackend: arch=amd64
12-25 11:23 DEBUG  CommonBackend: Parsing isolist=C:\Users\Wabbit\AppData\Local\Temp\pyl65B4.tmp\data\isolist.ini
12-25 11:23 DEBUG  CommonBackend:   Adding distro Edubuntu-i386
12-25 11:23 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
12-25 11:23 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
12-25 11:23 DEBUG  CommonBackend:   Adding distro Edubuntu-amd64
12-25 11:23 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
12-25 11:23 DEBUG  CommonBackend:   Adding distro Lubuntu-i386
12-25 11:23 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
12-25 11:23 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
12-25 11:23 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
12-25 11:23 DEBUG  CommonBackend:   Adding distro Lubuntu-amd64
12-25 11:23 DEBUG  WindowsBackend: Fetching host info...
12-25 11:23 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
12-25 11:23 DEBUG  WindowsBackend: windows version=vista
12-25 11:23 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium
12-25 11:23 DEBUG  WindowsBackend: windows_sp=None
12-25 11:23 DEBUG  WindowsBackend: windows_build=7601
12-25 11:23 DEBUG  WindowsBackend: gmt=0
12-25 11:23 DEBUG  WindowsBackend: country=GB
12-25 11:23 DEBUG  WindowsBackend: timezone=Europe/London
12-25 11:23 DEBUG  WindowsBackend: windows_username=Wabbit
12-25 11:23 DEBUG  WindowsBackend: user_full_name=Wabbit
12-25 11:23 DEBUG  WindowsBackend: user_directory=C:\Users\Wabbit
12-25 11:23 DEBUG  WindowsBackend: windows_language_code=1033
12-25 11:23 DEBUG  WindowsBackend: windows_language=English
12-25 11:23 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM) i7 CPU       U 640  @ 1.20GHz
12-25 11:23 DEBUG  WindowsBackend: bootloader=vista
12-25 11:23 DEBUG  WindowsBackend: system_drive=Drive(C: hd 189075.261719 mb free ntfs)
12-25 11:23 DEBUG  WindowsBackend: drive=Drive(C: hd 189075.261719 mb free ntfs)
12-25 11:23 DEBUG  WindowsBackend: drive=Drive(D: cd 0.0 mb free )
12-25 11:23 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free cdfs)
12-25 11:23 DEBUG  WindowsBackend: drive=Drive(F: removable 1145.50585938 mb free fat32)
12-25 11:23 DEBUG  WindowsBackend: uninstaller_path=None
12-25 11:23 DEBUG  WindowsBackend: previous_target_dir=None
12-25 11:23 DEBUG  WindowsBackend: previous_distro_name=None
12-25 11:23 DEBUG  WindowsBackend: keyboard_id=134809609
12-25 11:23 DEBUG  WindowsBackend: keyboard_layout=gb
12-25 11:23 DEBUG  WindowsBackend: keyboard_variant=
12-25 11:23 DEBUG  WindowsBackend: total_memory_mb=3893.859375
12-25 11:23 DEBUG  CommonBackend: Searching ISOs on USB devices
12-25 11:23 DEBUG  CommonBackend: Searching for local CDs
12-25 11:23 DEBUG  Distro:   checking whether C:\Users\Wabbit\AppData\Local\Temp\pyl65B4.tmp is a valid Ubuntu CD
12-25 11:23 DEBUG  Distro:     does not contain C:\Users\Wabbit\AppData\Local\Temp\pyl65B4.tmp\casper\filesystem.squashfs
12-25 11:23 DEBUG  Distro:   checking whether C:\Users\Wabbit\AppData\Local\Temp\pyl65B4.tmp is a valid Ubuntu CD
12-25 11:23 DEBUG  Distro:     does not contain C:\Users\Wabbit\AppData\Local\Temp\pyl65B4.tmp\casper\filesystem.squashfs
12-25 11:23 DEBUG  Distro:   checking whether C:\Users\Wabbit\AppData\Local\Temp\pyl65B4.tmp is a valid Kubuntu CD
12-25 11:23 DEBUG  Distro:     does not contain C:\Users\Wabbit\AppData\Local\Temp\pyl65B4.tmp\casper\filesystem.squashfs
12-25 11:23 DEBUG  Distro:   checking whether C:\Users\Wabbit\AppData\Local\Temp\pyl65B4.tmp is a valid Kubuntu CD
12-25 11:23 DEBUG  Distro:     does not contain C:\Users\Wabbit\AppData\Local\Temp\pyl65B4.tmp\casper\filesystem.squashfs
12-25 11:23 DEBUG  Distro:   checking whether C:\Users\Wabbit\AppData\Local\Temp\pyl65B4.tmp is a valid Mythbuntu CD
12-25 11:23 DEBUG  Distro:     does not contain C:\Users\Wabbit\AppData\Local\Temp\pyl65B4.tmp\casper\filesystem.squashfs
12-25 11:23 DEBUG  Distro:   checking whether C:\Users\Wabbit\AppData\Local\Temp\pyl65B4.tmp is a valid Mythbuntu CD
12-25 11:23 DEBUG  Distro:     does not contain C:\Users\Wabbit\AppData\Local\Temp\pyl65B4.tmp\casper\filesystem.squashfs
12-25 11:23 DEBUG  Distro:   checking whether C:\Users\Wabbit\AppData\Local\Temp\pyl65B4.tmp is a valid Edubuntu CD
12-25 11:23 DEBUG  Distro:     does not contain C:\Users\Wabbit\AppData\Local\Temp\pyl65B4.tmp\casper\filesystem.squashfs
12-25 11:23 DEBUG  Distro:   checking whether C:\Users\Wabbit\AppData\Local\Temp\pyl65B4.tmp is a valid Edubuntu CD
12-25 11:23 DEBUG  Distro:     does not contain C:\Users\Wabbit\AppData\Local\Temp\pyl65B4.tmp\casper\filesystem.squashfs
12-25 11:23 DEBUG  Distro:   checking whether C:\Users\Wabbit\AppData\Local\Temp\pyl65B4.tmp is a valid Lubuntu CD
12-25 11:23 DEBUG  Distro:     does not contain C:\Users\Wabbit\AppData\Local\Temp\pyl65B4.tmp\casper\filesystem.squashfs
12-25 11:23 DEBUG  Distro:   checking whether C:\Users\Wabbit\AppData\Local\Temp\pyl65B4.tmp is a valid Lubuntu CD
12-25 11:23 DEBUG  Distro:     does not contain C:\Users\Wabbit\AppData\Local\Temp\pyl65B4.tmp\casper\filesystem.squashfs
12-25 11:23 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
12-25 11:23 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-25 11:23 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
12-25 11:23 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-25 11:23 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
12-25 11:23 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-25 11:23 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
12-25 11:23 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-25 11:23 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
12-25 11:23 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-25 11:23 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
12-25 11:23 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-25 11:23 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
12-25 11:23 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-25 11:23 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
12-25 11:23 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-25 11:23 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
12-25 11:23 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-25 11:23 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
12-25 11:23 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-25 11:23 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
12-25 11:23 DEBUG  Distro: could not get info None
12-25 11:23 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
12-25 11:23 DEBUG  Distro: could not get info None
12-25 11:23 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
12-25 11:23 DEBUG  Distro: could not get info None
12-25 11:23 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
12-25 11:23 DEBUG  Distro: could not get info None
12-25 11:23 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
12-25 11:23 DEBUG  Distro: could not get info None
12-25 11:23 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
12-25 11:23 DEBUG  Distro: could not get info None
12-25 11:23 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
12-25 11:23 DEBUG  Distro: could not get info None
12-25 11:23 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
12-25 11:23 DEBUG  Distro: could not get info None
12-25 11:23 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
12-25 11:23 DEBUG  Distro: could not get info None
12-25 11:23 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
12-25 11:23 DEBUG  Distro: could not get info None
12-25 11:23 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
12-25 11:23 DEBUG  Distro: could not get info None
12-25 11:23 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
12-25 11:23 DEBUG  Distro: could not get info None
12-25 11:23 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
12-25 11:23 DEBUG  Distro: could not get info None
12-25 11:23 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
12-25 11:23 DEBUG  Distro: could not get info None
12-25 11:23 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
12-25 11:23 DEBUG  Distro: could not get info None
12-25 11:23 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
12-25 11:23 DEBUG  Distro: could not get info None
12-25 11:23 DEBUG  Distro:   checking whether F:\ is a valid Edubuntu CD
12-25 11:23 DEBUG  Distro: could not get info None
12-25 11:23 DEBUG  Distro:   checking whether F:\ is a valid Edubuntu CD
12-25 11:23 DEBUG  Distro: could not get info None
12-25 11:23 DEBUG  Distro:   checking whether F:\ is a valid Lubuntu CD
12-25 11:23 DEBUG  Distro: could not get info None
12-25 11:23 DEBUG  Distro:   checking whether F:\ is a valid Lubuntu CD
12-25 11:23 DEBUG  Distro: could not get info None
12-25 11:23 INFO   root: Running the installer...
12-25 11:23 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Wabbit\AppData\Local\Temp\pyl65B4.tmp\translations, languages=['en_GB', 'en']
12-25 11:23 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Wabbit\AppData\Local\Temp\pyl65B4.tmp\translations, languages=['en_GB', 'en']
12-25 11:23 DEBUG  WinuiInstallationPage: target_drive=C:, installation_size=5000MB, distro_name=Ubuntu, language=en_GB, locale=en_GB.UTF-8, username=wabbit
12-25 11:23 INFO   root: Received settings
12-25 11:23 DEBUG  CommonBackend: Searching for local CD
12-25 11:23 DEBUG  Distro:   checking whether C:\Users\Wabbit\AppData\Local\Temp\pyl65B4.tmp is a valid Ubuntu CD
12-25 11:23 DEBUG  Distro:     does not contain C:\Users\Wabbit\AppData\Local\Temp\pyl65B4.tmp\casper\filesystem.squashfs
12-25 11:23 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
12-25 11:23 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-25 11:23 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
12-25 11:23 DEBUG  Distro: could not get info None
12-25 11:23 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
12-25 11:23 DEBUG  Distro: could not get info None
12-25 11:23 DEBUG  CommonBackend: Searching for local ISO
12-25 11:23 DEBUG  Distro:   checking Ubuntu ISO C:\Users\Wabbit\Downloads\ubuntu-11.10-desktop-i386.iso
12-25 11:23 DEBUG  WindowsBackend:   extracting .disk\info from C:\Users\Wabbit\Downloads\ubuntu-11.10-desktop-i386.iso
12-25 11:23 DEBUG  Distro:   parsing info from str=LTˆ#!° óÇ-Ä.T=€x÷Ò‡]†‘G¹…]îóŸ[‡·=“)ÍèêÍ‡º†ÛÆ
12-25 11:23 ERROR  Distro: 'NoneType' object has no attribute 'group'
12-25 11:23 DEBUG  Distro: could not get info None
12-25 11:23 DEBUG  Distro:   checking Ubuntu ISO C:\Users\Wabbit\Downloads\ubuntu-12.10-desktop-amd64.iso
12-25 11:23 DEBUG  WindowsBackend:   extracting .disk\info from C:\Users\Wabbit\Downloads\ubuntu-12.10-desktop-amd64.iso
12-25 11:23 DEBUG  Distro:   parsing info from str=ÖË‹Fo)qµgÜ…aXÆ|ÀÛ_ÈÚôô÷¡+ôÏ¯®=ÉÂ½3ëŒgîõôûñŒÿ íþ=Rœ!)B
12-25 11:23 ERROR  Distro: 'NoneType' object has no attribute 'group'
12-25 11:23 DEBUG  Distro: could not get info None
12-25 11:23 DEBUG  Distro:   checking Ubuntu ISO C:\Users\Wabbit\Downloads\ubuntu-12.10-desktop-i386.iso
12-25 11:23 DEBUG  WindowsBackend:   extracting .disk\info from C:\Users\Wabbit\Downloads\ubuntu-12.10-desktop-i386.iso
12-25 11:23 DEBUG  Distro:   parsing info from str=~^-e–3~˜Ãä²Ë9Îâ³’¨áCÕ÷å×g¿ú¹¥?ü_Žï®:íà&ºAìMÂn(ë-…X}ò
12-25 11:23 ERROR  Distro: 'NoneType' object has no attribute 'group'
12-25 11:23 DEBUG  Distro: could not get info None
12-25 11:23 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Wabbit\AppData\Local\Temp\pyl65B4.tmp\translations, languages=['en_GB', 'en']
12-25 11:23 DEBUG  TaskList: # Running tasklist...
12-25 11:23 DEBUG  TaskList: ## Running select_target_dir...
12-25 11:23 INFO   WindowsBackend: Installing into C:\ubuntu
12-25 11:23 DEBUG  TaskList: ## Finished select_target_dir
12-25 11:23 DEBUG  TaskList: ## Running create_dir_structure...
12-25 11:23 DEBUG  CommonBackend: Creating dir C:\ubuntu
12-25 11:23 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks
12-25 11:23 DEBUG  CommonBackend: Creating dir C:\ubuntu\install
12-25 11:23 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot
12-25 11:23 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot
12-25 11:23 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot\grub
12-25 11:23 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot\grub
12-25 11:23 DEBUG  TaskList: ## Finished create_dir_structure
12-25 11:23 DEBUG  TaskList: ## Running create_uninstaller...
12-25 11:23 DEBUG  WindowsBackend: Copying uninstaller C:\Users\Wabbit\Downloads\wubi.exe -> C:\ubuntu\uninstall-wubi.exe
12-25 11:23 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString C:\ubuntu\uninstall-wubi.exe
12-25 11:23 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir C:\ubuntu
12-25 11:23 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
12-25 11:23 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon C:\ubuntu\Ubuntu.ico
12-25 11:23 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 12.10-rev273
12-25 11:23 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
12-25 11:23 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com](http://www.ubuntu.com)
12-25 11:23 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
12-25 11:23 DEBUG  TaskList: ## Finished create_uninstaller
12-25 11:23 DEBUG  TaskList: ## Running create_preseed_diskimage...
12-25 11:23 DEBUG  TaskList: ## Finished create_preseed_diskimage
12-25 11:23 DEBUG  TaskList: ## Running get_diskimage...
12-25 11:23 DEBUG  TaskList: New task download
12-25 11:23 DEBUG  TaskList: ### Running download...
12-25 11:23 DEBUG  downloader: downloading [http://releases.ubuntu.com/12.10/ubuntu-12.10-wubi-amd64.tar.xz](http://releases.ubuntu.com/12.10/ubuntu-12.10-wubi-amd64.tar.xz) > C:\ubuntu\disks\ubuntu-12.10-wubi-amd64.tar.xz
12-25 11:23 DEBUG  downloader: Download start filename=C:\ubuntu\disks\ubuntu-12.10-wubi-amd64.tar.xz, url=http://releases.ubuntu.com/12.10/ubuntu-12.10-wubi-amd64.tar.xz, basename=ubuntu-12.10-wubi-amd64.tar.xz, length=562061340, text=None
12-25 11:28 DEBUG  downloader: download finished (read 562048200 bytes)
12-25 11:28 DEBUG  TaskList: ### Finished download
12-25 11:28 DEBUG  TaskList: ## Finished get_diskimage
12-25 11:28 DEBUG  TaskList: ## Running extract_diskimage...
12-25 11:28 ERROR  TaskList: Extraction failed with code: 2
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 450, in extract_diskimage
Exception: Extraction failed with code: 2
12-25 11:28 DEBUG  TaskList: # Cancelling tasklist
12-25 11:28 DEBUG  TaskList: # Finished tasklist
12-25 11:28 ERROR  root: Extraction failed with code: 2
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 58, in run
  File "\lib\wubi\application.py", line 132, in select_task
  File "\lib\wubi\application.py", line 158, in run_installer
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 450, in extract_diskimage
Exception: Extraction failed with code: 2
12-25 11:46 INFO   root: === wubi 12.10 rev273 ===
12-25 11:46 DEBUG  root: Logfile is c:\users\wabbit\appdata\local\temp\wubi-12.10-rev273.log
12-25 11:46 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\Users\\Wabbit\\Downloads\\wubi.exe"']
12-25 11:46 DEBUG  CommonBackend: data_dir=C:\Users\Wabbit\AppData\Local\Temp\pylB65.tmp\data
12-25 11:46 DEBUG  WindowsBackend: 7z=C:\Users\Wabbit\AppData\Local\Temp\pylB65.tmp\bin\7z.exe
12-25 11:46 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
12-25 11:46 DEBUG  CommonBackend: Fetching basic info...
12-25 11:46 DEBUG  CommonBackend: original_exe=C:\Users\Wabbit\Downloads\wubi.exe
12-25 11:46 DEBUG  CommonBackend: platform=win32
12-25 11:46 DEBUG  CommonBackend: osname=nt
12-25 11:46 DEBUG  CommonBackend: language=en_GB
12-25 11:46 DEBUG  CommonBackend: encoding=cp1252
12-25 11:46 DEBUG  WindowsBackend: arch=amd64
12-25 11:46 DEBUG  CommonBackend: Parsing isolist=C:\Users\Wabbit\AppData\Local\Temp\pylB65.tmp\data\isolist.ini
12-25 11:46 DEBUG  CommonBackend:   Adding distro Edubuntu-i386
12-25 11:46 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
12-25 11:46 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
12-25 11:46 DEBUG  CommonBackend:   Adding distro Edubuntu-amd64
12-25 11:46 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
12-25 11:46 DEBUG  CommonBackend:   Adding distro Lubuntu-i386
12-25 11:46 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
12-25 11:46 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
12-25 11:46 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
12-25 11:46 DEBUG  CommonBackend:   Adding distro Lubuntu-amd64
12-25 11:46 DEBUG  WindowsBackend: Fetching host info...
12-25 11:46 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
12-25 11:46 DEBUG  WindowsBackend: windows version=vista
12-25 11:46 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium
12-25 11:46 DEBUG  WindowsBackend: windows_sp=None
12-25 11:46 DEBUG  WindowsBackend: windows_build=7601
12-25 11:46 DEBUG  WindowsBackend: gmt=0
12-25 11:46 DEBUG  WindowsBackend: country=GB
12-25 11:46 DEBUG  WindowsBackend: timezone=Europe/London
12-25 11:46 DEBUG  WindowsBackend: windows_username=Wabbit
12-25 11:46 DEBUG  WindowsBackend: user_full_name=Wabbit
12-25 11:46 DEBUG  WindowsBackend: user_directory=C:\Users\Wabbit
12-25 11:46 DEBUG  WindowsBackend: windows_language_code=1033
12-25 11:46 DEBUG  WindowsBackend: windows_language=English
12-25 11:46 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM) i7 CPU       U 640  @ 1.20GHz
12-25 11:46 DEBUG  WindowsBackend: bootloader=vista
12-25 11:46 DEBUG  WindowsBackend: system_drive=Drive(C: hd 188280.628906 mb free ntfs)
12-25 11:46 DEBUG  WindowsBackend: drive=Drive(C: hd 188280.628906 mb free ntfs)
12-25 11:46 DEBUG  WindowsBackend: drive=Drive(D: cd 0.0 mb free )
12-25 11:46 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free cdfs)
12-25 11:46 DEBUG  WindowsBackend: drive=Drive(F: removable 1914.78125 mb free fat)
12-25 11:46 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
12-25 11:46 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
12-25 11:46 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
12-25 11:46 DEBUG  WindowsBackend: keyboard_id=134809609
12-25 11:46 DEBUG  WindowsBackend: keyboard_layout=gb
12-25 11:46 DEBUG  WindowsBackend: keyboard_variant=
12-25 11:46 DEBUG  CommonBackend: python locale=('en_GB', 'cp1252')
12-25 11:46 DEBUG  CommonBackend: locale=en_GB.UTF-8
12-25 11:46 DEBUG  WindowsBackend: total_memory_mb=3893.859375
12-25 11:46 DEBUG  CommonBackend: Searching ISOs on USB devices
12-25 11:46 DEBUG  CommonBackend: Searching for local CDs
12-25 11:46 DEBUG  Distro:   checking whether C:\Users\Wabbit\AppData\Local\Temp\pylB65.tmp is a valid Ubuntu CD
12-25 11:46 DEBUG  Distro:     does not contain C:\Users\Wabbit\AppData\Local\Temp\pylB65.tmp\casper\filesystem.squashfs
12-25 11:46 DEBUG  Distro:   checking whether C:\Users\Wabbit\AppData\Local\Temp\pylB65.tmp is a valid Ubuntu CD
12-25 11:46 DEBUG  Distro:     does not contain C:\Users\Wabbit\AppData\Local\Temp\pylB65.tmp\casper\filesystem.squashfs
12-25 11:46 DEBUG  Distro:   checking whether C:\Users\Wabbit\AppData\Local\Temp\pylB65.tmp is a valid Kubuntu CD
12-25 11:46 DEBUG  Distro:     does not contain C:\Users\Wabbit\AppData\Local\Temp\pylB65.tmp\casper\filesystem.squashfs
12-25 11:46 DEBUG  Distro:   checking whether C:\Users\Wabbit\AppData\Local\Temp\pylB65.tmp is a valid Kubuntu CD
12-25 11:46 DEBUG  Distro:     does not contain C:\Users\Wabbit\AppData\Local\Temp\pylB65.tmp\casper\filesystem.squashfs
12-25 11:46 DEBUG  Distro:   checking whether C:\Users\Wabbit\AppData\Local\Temp\pylB65.tmp is a valid Mythbuntu CD
12-25 11:46 DEBUG  Distro:     does not contain C:\Users\Wabbit\AppData\Local\Temp\pylB65.tmp\casper\filesystem.squashfs
12-25 11:46 DEBUG  Distro:   checking whether C:\Users\Wabbit\AppData\Local\Temp\pylB65.tmp is a valid Mythbuntu CD
12-25 11:46 DEBUG  Distro:     does not contain C:\Users\Wabbit\AppData\Local\Temp\pylB65.tmp\casper\filesystem.squashfs
12-25 11:46 DEBUG  Distro:   checking whether C:\Users\Wabbit\AppData\Local\Temp\pylB65.tmp is a valid Edubuntu CD
12-25 11:46 DEBUG  Distro:     does not contain C:\Users\Wabbit\AppData\Local\Temp\pylB65.tmp\casper\filesystem.squashfs
12-25 11:46 DEBUG  Distro:   checking whether C:\Users\Wabbit\AppData\Local\Temp\pylB65.tmp is a valid Edubuntu CD
12-25 11:46 DEBUG  Distro:     does not contain C:\Users\Wabbit\AppData\Local\Temp\pylB65.tmp\casper\filesystem.squashfs
12-25 11:46 DEBUG  Distro:   checking whether C:\Users\Wabbit\AppData\Local\Temp\pylB65.tmp is a valid Lubuntu CD
12-25 11:46 DEBUG  Distro:     does not contain C:\Users\Wabbit\AppData\Local\Temp\pylB65.tmp\casper\filesystem.squashfs
12-25 11:46 DEBUG  Distro:   checking whether C:\Users\Wabbit\AppData\Local\Temp\pylB65.tmp is a valid Lubuntu CD
12-25 11:46 DEBUG  Distro:     does not contain C:\Users\Wabbit\AppData\Local\Temp\pylB65.tmp\casper\filesystem.squashfs
12-25 11:46 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
12-25 11:46 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-25 11:46 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
12-25 11:46 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-25 11:46 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
12-25 11:46 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-25 11:46 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
12-25 11:46 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-25 11:46 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
12-25 11:46 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-25 11:46 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
12-25 11:46 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-25 11:46 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
12-25 11:46 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-25 11:46 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
12-25 11:46 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-25 11:46 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
12-25 11:46 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-25 11:46 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
12-25 11:46 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-25 11:46 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
12-25 11:46 DEBUG  Distro:   parsing info from str=ÖË‹Fo)qµgÜ…aXÆ|ÀÛ_ÈÚôô÷¡+ôÏ¯®=ÉÂ½3ëŒgîõôûñŒÿ íþ=Rœ!)B
12-25 11:46 ERROR  Distro: 'NoneType' object has no attribute 'group'
12-25 11:46 DEBUG  Distro: could not get info None
12-25 11:46 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
12-25 11:46 DEBUG  Distro: could not get info None
12-25 11:46 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
12-25 11:46 DEBUG  Distro: could not get info None
12-25 11:46 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
12-25 11:46 DEBUG  Distro: could not get info None
12-25 11:46 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
12-25 11:46 DEBUG  Distro: could not get info None
12-25 11:46 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
12-25 11:46 DEBUG  Distro: could not get info None
12-25 11:46 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
12-25 11:46 DEBUG  Distro: could not get info None
12-25 11:46 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
12-25 11:46 DEBUG  Distro: could not get info None
12-25 11:46 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
12-25 11:46 DEBUG  Distro: could not get info None
12-25 11:46 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
12-25 11:46 DEBUG  Distro: could not get info None
12-25 11:46 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
12-25 11:46 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-25 11:46 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
12-25 11:46 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-25 11:46 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
12-25 11:46 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-25 11:46 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
12-25 11:46 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-25 11:46 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
12-25 11:46 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-25 11:46 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
12-25 11:46 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-25 11:46 DEBUG  Distro:   checking whether F:\ is a valid Edubuntu CD
12-25 11:46 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-25 11:46 DEBUG  Distro:   checking whether F:\ is a valid Edubuntu CD
12-25 11:46 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-25 11:46 DEBUG  Distro:   checking whether F:\ is a valid Lubuntu CD
12-25 11:46 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-25 11:46 DEBUG  Distro:   checking whether F:\ is a valid Lubuntu CD
12-25 11:46 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-25 11:46 INFO   root: Already installed, running the uninstaller...
12-25 11:46 INFO   root: Running the uninstaller...
12-25 11:46 INFO   CommonBackend: This is the uninstaller running
12-25 11:46 DEBUG  WindowsFrontend: __init__...
12-25 11:46 DEBUG  WindowsFrontend: on_init...
12-25 11:46 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Wabbit\AppData\Local\Temp\pylB65.tmp\translations, languages=['en_GB', 'en']
12-25 11:46 INFO   root: Received settings
12-25 11:46 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Wabbit\AppData\Local\Temp\pylB65.tmp\translations, languages=['en_GB', 'en']
12-25 11:46 DEBUG  TaskList: # Running tasklist...
12-25 11:46 DEBUG  TaskList: ## Running Remove bootloader entry....
12-25 11:46 DEBUG  WindowsBackend: Could not find bcd id
12-25 11:46 DEBUG  WindowsBackend: undo_bootini C:
12-25 11:46 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 188280.628906 mb free ntfs)
12-25 11:46 DEBUG  WindowsBackend: undo_bootini F:
12-25 11:46 DEBUG  WindowsBackend: undo_configsys Drive(F: removable 1914.78125 mb free fat)
12-25 11:46 DEBUG  TaskList: ## Finished Remove bootloader entry.
12-25 11:46 DEBUG  TaskList: ## Running Remove target dir....
12-25 11:46 DEBUG  CommonBackend: Deleting C:\ubuntu
12-25 11:46 DEBUG  TaskList: ## Finished Remove target dir.
12-25 11:46 DEBUG  TaskList: ## Running Remove registry key....
12-25 11:46 DEBUG  TaskList: ## Finished Remove registry key.
12-25 11:46 DEBUG  TaskList: # Finished tasklist
12-25 11:46 INFO   root: Almost finished uninstalling
12-25 11:46 INFO   root: Finished uninstallation
12-25 11:46 DEBUG  CommonBackend: Fetching basic info...
12-25 11:46 DEBUG  CommonBackend: original_exe=C:\Users\Wabbit\Downloads\wubi.exe
12-25 11:46 DEBUG  CommonBackend: platform=win32
12-25 11:46 DEBUG  CommonBackend: osname=nt
12-25 11:46 DEBUG  WindowsBackend: arch=amd64
12-25 11:46 DEBUG  CommonBackend: Parsing isolist=C:\Users\Wabbit\AppData\Local\Temp\pylB65.tmp\data\isolist.ini
12-25 11:46 DEBUG  CommonBackend:   Adding distro Edubuntu-i386
12-25 11:46 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
12-25 11:46 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
12-25 11:46 DEBUG  CommonBackend:   Adding distro Edubuntu-amd64
12-25 11:46 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
12-25 11:46 DEBUG  CommonBackend:   Adding distro Lubuntu-i386
12-25 11:46 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
12-25 11:46 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
12-25 11:46 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
12-25 11:46 DEBUG  CommonBackend:   Adding distro Lubuntu-amd64
12-25 11:46 DEBUG  WindowsBackend: Fetching host info...
12-25 11:46 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
12-25 11:46 DEBUG  WindowsBackend: windows version=vista
12-25 11:46 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium
12-25 11:46 DEBUG  WindowsBackend: windows_sp=None
12-25 11:46 DEBUG  WindowsBackend: windows_build=7601
12-25 11:46 DEBUG  WindowsBackend: gmt=0
12-25 11:46 DEBUG  WindowsBackend: country=GB
12-25 11:46 DEBUG  WindowsBackend: timezone=Europe/London
12-25 11:46 DEBUG  WindowsBackend: windows_username=Wabbit
12-25 11:46 DEBUG  WindowsBackend: user_full_name=Wabbit
12-25 11:46 DEBUG  WindowsBackend: user_directory=C:\Users\Wabbit
12-25 11:46 DEBUG  WindowsBackend: windows_language_code=1033
12-25 11:46 DEBUG  WindowsBackend: windows_language=English
12-25 11:46 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM) i7 CPU       U 640  @ 1.20GHz
12-25 11:46 DEBUG  WindowsBackend: bootloader=vista
12-25 11:46 DEBUG  WindowsBackend: system_drive=Drive(C: hd 188935.578125 mb free ntfs)
12-25 11:46 DEBUG  WindowsBackend: drive=Drive(C: hd 188935.578125 mb free ntfs)
12-25 11:46 DEBUG  WindowsBackend: drive=Drive(D: cd 0.0 mb free )
12-25 11:46 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free cdfs)
12-25 11:46 DEBUG  WindowsBackend: drive=Drive(F: removable 1914.78125 mb free fat)
12-25 11:46 DEBUG  WindowsBackend: uninstaller_path=None
12-25 11:46 DEBUG  WindowsBackend: previous_target_dir=None
12-25 11:46 DEBUG  WindowsBackend: previous_distro_name=None
12-25 11:46 DEBUG  WindowsBackend: keyboard_id=134809609
12-25 11:46 DEBUG  WindowsBackend: keyboard_layout=gb
12-25 11:46 DEBUG  WindowsBackend: keyboard_variant=
12-25 11:46 DEBUG  WindowsBackend: total_memory_mb=3893.859375
12-25 11:46 DEBUG  CommonBackend: Searching ISOs on USB devices
12-25 11:46 DEBUG  CommonBackend: Searching for local CDs
12-25 11:46 DEBUG  Distro:   checking whether C:\Users\Wabbit\AppData\Local\Temp\pylB65.tmp is a valid Ubuntu CD
12-25 11:46 DEBUG  Distro:     does not contain C:\Users\Wabbit\AppData\Local\Temp\pylB65.tmp\casper\filesystem.squashfs
12-25 11:46 DEBUG  Distro:   checking whether C:\Users\Wabbit\AppData\Local\Temp\pylB65.tmp is a valid Ubuntu CD
12-25 11:46 DEBUG  Distro:     does not contain C:\Users\Wabbit\AppData\Local\Temp\pylB65.tmp\casper\filesystem.squashfs
12-25 11:46 DEBUG  Distro:   checking whether C:\Users\Wabbit\AppData\Local\Temp\pylB65.tmp is a valid Kubuntu CD
12-25 11:46 DEBUG  Distro:     does not contain C:\Users\Wabbit\AppData\Local\Temp\pylB65.tmp\casper\filesystem.squashfs
12-25 11:46 DEBUG  Distro:   checking whether C:\Users\Wabbit\AppData\Local\Temp\pylB65.tmp is a valid Kubuntu CD
12-25 11:46 DEBUG  Distro:     does not contain C:\Users\Wabbit\AppData\Local\Temp\pylB65.tmp\casper\filesystem.squashfs
12-25 11:46 DEBUG  Distro:   checking whether C:\Users\Wabbit\AppData\Local\Temp\pylB65.tmp is a valid Mythbuntu CD
12-25 11:46 DEBUG  Distro:     does not contain C:\Users\Wabbit\AppData\Local\Temp\pylB65.tmp\casper\filesystem.squashfs
12-25 11:46 DEBUG  Distro:   checking whether C:\Users\Wabbit\AppData\Local\Temp\pylB65.tmp is a valid Mythbuntu CD
12-25 11:46 DEBUG  Distro:     does not contain C:\Users\Wabbit\AppData\Local\Temp\pylB65.tmp\casper\filesystem.squashfs
12-25 11:46 DEBUG  Distro:   checking whether C:\Users\Wabbit\AppData\Local\Temp\pylB65.tmp is a valid Edubuntu CD
12-25 11:46 DEBUG  Distro:     does not contain C:\Users\Wabbit\AppData\Local\Temp\pylB65.tmp\casper\filesystem.squashfs
12-25 11:46 DEBUG  Distro:   checking whether C:\Users\Wabbit\AppData\Local\Temp\pylB65.tmp is a valid Edubuntu CD
12-25 11:46 DEBUG  Distro:     does not contain C:\Users\Wabbit\AppData\Local\Temp\pylB65.tmp\casper\filesystem.squashfs
12-25 11:46 DEBUG  Distro:   checking whether C:\Users\Wabbit\AppData\Local\Temp\pylB65.tmp is a valid Lubuntu CD
12-25 11:46 DEBUG  Distro:     does not contain C:\Users\Wabbit\AppData\Local\Temp\pylB65.tmp\casper\filesystem.squashfs
12-25 11:46 DEBUG  Distro:   checking whether C:\Users\Wabbit\AppData\Local\Temp\pylB65.tmp is a valid Lubuntu CD
12-25 11:46 DEBUG  Distro:     does not contain C:\Users\Wabbit\AppData\Local\Temp\pylB65.tmp\casper\filesystem.squashfs
12-25 11:46 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
12-25 11:46 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-25 11:46 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
12-25 11:46 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-25 11:46 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
12-25 11:46 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-25 11:46 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
12-25 11:46 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-25 11:46 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
12-25 11:46 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-25 11:46 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
12-25 11:46 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-25 11:46 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
12-25 11:46 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-25 11:46 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
12-25 11:46 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-25 11:46 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
12-25 11:46 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-25 11:46 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
12-25 11:46 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-25 11:46 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
12-25 11:46 DEBUG  Distro: could not get info None
12-25 11:46 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
12-25 11:46 DEBUG  Distro: could not get info None
12-25 11:46 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
12-25 11:46 DEBUG  Distro: could not get info None
12-25 11:46 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
12-25 11:46 DEBUG  Distro: could not get info None
12-25 11:46 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
12-25 11:46 DEBUG  Distro: could not get info None
12-25 11:46 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
12-25 11:46 DEBUG  Distro: could not get info None
12-25 11:46 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
12-25 11:46 DEBUG  Distro: could not get info None
12-25 11:46 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
12-25 11:46 DEBUG  Distro: could not get info None
12-25 11:46 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
12-25 11:46 DEBUG  Distro: could not get info None
12-25 11:46 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
12-25 11:46 DEBUG  Distro: could not get info None
12-25 11:46 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
12-25 11:46 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-25 11:46 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
12-25 11:46 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-25 11:46 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
12-25 11:46 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-25 11:46 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
12-25 11:46 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-25 11:46 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
12-25 11:46 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-25 11:46 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
12-25 11:46 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-25 11:46 DEBUG  Distro:   checking whether F:\ is a valid Edubuntu CD
12-25 11:46 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-25 11:46 DEBUG  Distro:   checking whether F:\ is a valid Edubuntu CD
12-25 11:46 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-25 11:46 DEBUG  Distro:   checking whether F:\ is a valid Lubuntu CD
12-25 11:46 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-25 11:46 DEBUG  Distro:   checking whether F:\ is a valid Lubuntu CD
12-25 11:46 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-25 11:46 INFO   root: Running the installer...
12-25 11:46 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Wabbit\AppData\Local\Temp\pylB65.tmp\translations, languages=['en_GB', 'en']
12-25 11:46 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Wabbit\AppData\Local\Temp\pylB65.tmp\translations, languages=['en_GB', 'en']
12-25 11:47 INFO   WindowsFrontend: Operation cancelled
12-25 11:47 DEBUG  WindowsFrontend: frontend.quit
12-25 11:47 DEBUG  WindowsFrontend: frontend.on_quit
12-25 11:47 DEBUG  root: application.on_quit
12-25 11:47 INFO   root: sys.exit
12-25 11:48 INFO   root: === wubi 12.10 rev273 ===
12-25 11:48 DEBUG  root: Logfile is c:\users\wabbit\appdata\local\temp\wubi-12.10-rev273.log
12-25 11:48 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\Users\\Wabbit\\Desktop\\wubi.exe"']
12-25 11:48 DEBUG  CommonBackend: data_dir=C:\Users\Wabbit\AppData\Local\Temp\pyl5753.tmp\data
12-25 11:48 DEBUG  WindowsBackend: 7z=C:\Users\Wabbit\AppData\Local\Temp\pyl5753.tmp\bin\7z.exe
12-25 11:48 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
12-25 11:48 DEBUG  CommonBackend: Fetching basic info...
12-25 11:48 DEBUG  CommonBackend: original_exe=C:\Users\Wabbit\Desktop\wubi.exe
12-25 11:48 DEBUG  CommonBackend: platform=win32
12-25 11:48 DEBUG  CommonBackend: osname=nt
12-25 11:48 DEBUG  CommonBackend: language=en_GB
12-25 11:48 DEBUG  CommonBackend: encoding=cp1252
12-25 11:48 DEBUG  WindowsBackend: arch=amd64
12-25 11:48 DEBUG  CommonBackend: Parsing isolist=C:\Users\Wabbit\AppData\Local\Temp\pyl5753.tmp\data\isolist.ini
12-25 11:48 DEBUG  CommonBackend:   Adding distro Edubuntu-i386
12-25 11:48 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
12-25 11:48 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
12-25 11:48 DEBUG  CommonBackend:   Adding distro Edubuntu-amd64
12-25 11:48 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
12-25 11:48 DEBUG  CommonBackend:   Adding distro Lubuntu-i386
12-25 11:48 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
12-25 11:48 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
12-25 11:48 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
12-25 11:48 DEBUG  CommonBackend:   Adding distro Lubuntu-amd64
12-25 11:48 DEBUG  WindowsBackend: Fetching host info...
12-25 11:48 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
12-25 11:48 DEBUG  WindowsBackend: windows version=vista
12-25 11:48 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium
12-25 11:48 DEBUG  WindowsBackend: windows_sp=None
12-25 11:48 DEBUG  WindowsBackend: windows_build=7601
12-25 11:48 DEBUG  WindowsBackend: gmt=0
12-25 11:48 DEBUG  WindowsBackend: country=GB
12-25 11:48 DEBUG  WindowsBackend: timezone=Europe/London
12-25 11:48 DEBUG  WindowsBackend: windows_username=Wabbit
12-25 11:48 DEBUG  WindowsBackend: user_full_name=Wabbit
12-25 11:48 DEBUG  WindowsBackend: user_directory=C:\Users\Wabbit
12-25 11:48 DEBUG  WindowsBackend: windows_language_code=1033
12-25 11:48 DEBUG  WindowsBackend: windows_language=English
12-25 11:48 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM) i7 CPU       U 640  @ 1.20GHz
12-25 11:48 DEBUG  WindowsBackend: bootloader=vista
12-25 11:48 DEBUG  WindowsBackend: system_drive=Drive(C: hd 188935.046875 mb free ntfs)
12-25 11:48 DEBUG  WindowsBackend: drive=Drive(C: hd 188935.046875 mb free ntfs)
12-25 11:48 DEBUG  WindowsBackend: drive=Drive(D: cd 0.0 mb free )
12-25 11:48 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free )
12-25 11:48 DEBUG  WindowsBackend: drive=Drive(F: removable 1914.78125 mb free fat)
12-25 11:48 DEBUG  WindowsBackend: uninstaller_path=None
12-25 11:48 DEBUG  WindowsBackend: previous_target_dir=None
12-25 11:48 DEBUG  WindowsBackend: previous_distro_name=None
12-25 11:48 DEBUG  WindowsBackend: keyboard_id=134809609
12-25 11:48 DEBUG  WindowsBackend: keyboard_layout=gb
12-25 11:48 DEBUG  WindowsBackend: keyboard_variant=
12-25 11:48 DEBUG  CommonBackend: python locale=('en_GB', 'cp1252')
12-25 11:48 DEBUG  CommonBackend: locale=en_GB.UTF-8
12-25 11:48 DEBUG  WindowsBackend: total_memory_mb=3893.859375
12-25 11:48 DEBUG  CommonBackend: Searching ISOs on USB devices
12-25 11:48 DEBUG  CommonBackend: Searching for local CDs
12-25 11:48 DEBUG  Distro:   checking whether C:\Users\Wabbit\AppData\Local\Temp\pyl5753.tmp is a valid Ubuntu CD
12-25 11:48 DEBUG  Distro:     does not contain C:\Users\Wabbit\AppData\Local\Temp\pyl5753.tmp\casper\filesystem.squashfs
12-25 11:48 DEBUG  Distro:   checking whether C:\Users\Wabbit\AppData\Local\Temp\pyl5753.tmp is a valid Ubuntu CD
12-25 11:48 DEBUG  Distro:     does not contain C:\Users\Wabbit\AppData\Local\Temp\pyl5753.tmp\casper\filesystem.squashfs
12-25 11:48 DEBUG  Distro:   checking whether C:\Users\Wabbit\AppData\Local\Temp\pyl5753.tmp is a valid Kubuntu CD
12-25 11:48 DEBUG  Distro:     does not contain C:\Users\Wabbit\AppData\Local\Temp\pyl5753.tmp\casper\filesystem.squashfs
12-25 11:48 DEBUG  Distro:   checking whether C:\Users\Wabbit\AppData\Local\Temp\pyl5753.tmp is a valid Kubuntu CD
12-25 11:48 DEBUG  Distro:     does not contain C:\Users\Wabbit\AppData\Local\Temp\pyl5753.tmp\casper\filesystem.squashfs
12-25 11:48 DEBUG  Distro:   checking whether C:\Users\Wabbit\AppData\Local\Temp\pyl5753.tmp is a valid Mythbuntu CD
12-25 11:48 DEBUG  Distro:     does not contain C:\Users\Wabbit\AppData\Local\Temp\pyl5753.tmp\casper\filesystem.squashfs
12-25 11:48 DEBUG  Distro:   checking whether C:\Users\Wabbit\AppData\Local\Temp\pyl5753.tmp is a valid Mythbuntu CD
12-25 11:48 DEBUG  Distro:     does not contain C:\Users\Wabbit\AppData\Local\Temp\pyl5753.tmp\casper\filesystem.squashfs
12-25 11:48 DEBUG  Distro:   checking whether C:\Users\Wabbit\AppData\Local\Temp\pyl5753.tmp is a valid Edubuntu CD
12-25 11:48 DEBUG  Distro:     does not contain C:\Users\Wabbit\AppData\Local\Temp\pyl5753.tmp\casper\filesystem.squashfs
12-25 11:48 DEBUG  Distro:   checking whether C:\Users\Wabbit\AppData\Local\Temp\pyl5753.tmp is a valid Edubuntu CD
12-25 11:48 DEBUG  Distro:     does not contain C:\Users\Wabbit\AppData\Local\Temp\pyl5753.tmp\casper\filesystem.squashfs
12-25 11:48 DEBUG  Distro:   checking whether C:\Users\Wabbit\AppData\Local\Temp\pyl5753.tmp is a valid Lubuntu CD
12-25 11:48 DEBUG  Distro:     does not contain C:\Users\Wabbit\AppData\Local\Temp\pyl5753.tmp\casper\filesystem.squashfs
12-25 11:48 DEBUG  Distro:   checking whether C:\Users\Wabbit\AppData\Local\Temp\pyl5753.tmp is a valid Lubuntu CD
12-25 11:48 DEBUG  Distro:     does not contain C:\Users\Wabbit\AppData\Local\Temp\pyl5753.tmp\casper\filesystem.squashfs
12-25 11:48 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
12-25 11:48 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-25 11:48 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
12-25 11:48 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-25 11:48 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
12-25 11:48 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-25 11:48 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
12-25 11:48 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-25 11:48 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
12-25 11:48 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-25 11:48 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
12-25 11:48 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-25 11:48 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
12-25 11:48 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-25 11:48 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
12-25 11:48 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-25 11:48 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
12-25 11:48 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-25 11:48 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
12-25 11:48 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-25 11:48 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
12-25 11:48 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-25 11:48 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
12-25 11:48 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-25 11:48 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
12-25 11:48 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-25 11:48 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
12-25 11:48 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-25 11:48 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
12-25 11:48 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-25 11:48 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
12-25 11:48 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-25 11:48 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
12-25 11:48 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-25 11:48 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
12-25 11:48 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-25 11:48 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
12-25 11:48 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-25 11:48 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
12-25 11:48 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-25 11:48 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
12-25 11:48 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-25 11:48 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
12-25 11:48 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-25 11:48 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
12-25 11:48 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-25 11:48 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
12-25 11:48 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-25 11:48 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
12-25 11:48 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-25 11:48 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
12-25 11:48 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-25 11:48 DEBUG  Distro:   checking whether F:\ is a valid Edubuntu CD
12-25 11:48 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-25 11:48 DEBUG  Distro:   checking whether F:\ is a valid Edubuntu CD
12-25 11:48 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-25 11:48 DEBUG  Distro:   checking whether F:\ is a valid Lubuntu CD
12-25 11:48 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-25 11:48 DEBUG  Distro:   checking whether F:\ is a valid Lubuntu CD
12-25 11:48 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-25 11:48 INFO   root: Running the installer...
12-25 11:48 DEBUG  WindowsFrontend: __init__...
12-25 11:48 DEBUG  WindowsFrontend: on_init...
12-25 11:48 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Wabbit\AppData\Local\Temp\pyl5753.tmp\translations, languages=['en_GB', 'en']
12-25 11:48 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Wabbit\AppData\Local\Temp\pyl5753.tmp\translations, languages=['en_GB', 'en']
12-25 11:48 DEBUG  WinuiInstallationPage: target_drive=C:, installation_size=5000MB, distro_name=Ubuntu, language=en_GB, locale=en_GB.UTF-8, username=wabbit
12-25 11:48 INFO   root: Received settings
12-25 11:48 DEBUG  CommonBackend: Searching for local CD
12-25 11:48 DEBUG  Distro:   checking whether C:\Users\Wabbit\AppData\Local\Temp\pyl5753.tmp is a valid Ubuntu CD
12-25 11:48 DEBUG  Distro:     does not contain C:\Users\Wabbit\AppData\Local\Temp\pyl5753.tmp\casper\filesystem.squashfs
12-25 11:48 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
12-25 11:48 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-25 11:48 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
12-25 11:48 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-25 11:48 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
12-25 11:48 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-25 11:48 DEBUG  CommonBackend: Searching for local ISO
12-25 11:48 DEBUG  Distro:   checking Ubuntu ISO C:\Users\Wabbit\Desktop\ubuntu-12.10-desktop-amd64.iso
12-25 11:48 DEBUG  WindowsBackend:   extracting .disk\info from C:\Users\Wabbit\Desktop\ubuntu-12.10-desktop-amd64.iso
12-25 11:48 DEBUG  Distro:   parsing info from str=ÖË‹Fo)qµgÜ…aXÆ|ÀÛ_ÈÚôô÷¡+ôÏ¯®=ÉÂ½3ëŒgîõôûñŒÿ íþ=Rœ!)B
12-25 11:48 ERROR  Distro: 'NoneType' object has no attribute 'group'
12-25 11:48 DEBUG  Distro: could not get info None
12-25 11:48 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Wabbit\AppData\Local\Temp\pyl5753.tmp\translations, languages=['en_GB', 'en']
12-25 11:48 DEBUG  TaskList: # Running tasklist...
12-25 11:48 DEBUG  TaskList: ## Running select_target_dir...
12-25 11:48 INFO   WindowsBackend: Installing into C:\ubuntu
12-25 11:48 DEBUG  TaskList: ## Finished select_target_dir
12-25 11:48 DEBUG  TaskList: ## Running create_dir_structure...
12-25 11:48 DEBUG  CommonBackend: Creating dir C:\ubuntu
12-25 11:48 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks
12-25 11:48 DEBUG  CommonBackend: Creating dir C:\ubuntu\install
12-25 11:48 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot
12-25 11:48 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot
12-25 11:48 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot\grub
12-25 11:48 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot\grub
12-25 11:48 DEBUG  TaskList: ## Finished create_dir_structure
12-25 11:48 DEBUG  TaskList: ## Running create_uninstaller...
12-25 11:48 DEBUG  WindowsBackend: Copying uninstaller C:\Users\Wabbit\Desktop\wubi.exe -> C:\ubuntu\uninstall-wubi.exe
12-25 11:48 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString C:\ubuntu\uninstall-wubi.exe
12-25 11:48 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir C:\ubuntu
12-25 11:48 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
12-25 11:48 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon C:\ubuntu\Ubuntu.ico
12-25 11:48 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 12.10-rev273
12-25 11:48 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
12-25 11:48 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com](http://www.ubuntu.com)
12-25 11:48 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
12-25 11:48 DEBUG  TaskList: ## Finished create_uninstaller
12-25 11:48 DEBUG  TaskList: ## Running create_preseed_diskimage...
12-25 11:48 DEBUG  TaskList: ## Finished create_preseed_diskimage
12-25 11:48 DEBUG  TaskList: ## Running get_diskimage...
12-25 11:48 DEBUG  TaskList: New task download
12-25 11:48 DEBUG  TaskList: ### Running download...
12-25 11:48 DEBUG  downloader: downloading [http://releases.ubuntu.com/12.10/ubuntu-12.10-wubi-amd64.tar.xz](http://releases.ubuntu.com/12.10/ubuntu-12.10-wubi-amd64.tar.xz) > C:\ubuntu\disks\ubuntu-12.10-wubi-amd64.tar.xz
12-25 11:48 DEBUG  downloader: Download start filename=C:\ubuntu\disks\ubuntu-12.10-wubi-amd64.tar.xz, url=http://releases.ubuntu.com/12.10/ubuntu-12.10-wubi-amd64.tar.xz, basename=ubuntu-12.10-wubi-amd64.tar.xz, length=562061340, text=None
12-25 11:52 DEBUG  downloader: download finished (read 562056960 bytes)
12-25 11:52 DEBUG  TaskList: ### Finished download
12-25 11:52 DEBUG  TaskList: ## Finished get_diskimage
12-25 11:52 DEBUG  TaskList: ## Running extract_diskimage...
12-25 11:53 ERROR  TaskList: Extraction failed with code: 2
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 450, in extract_diskimage
Exception: Extraction failed with code: 2
12-25 11:53 DEBUG  TaskList: # Cancelling tasklist
12-25 11:53 DEBUG  TaskList: # Finished tasklist
12-25 11:53 ERROR  root: Extraction failed with code: 2
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 58, in run
  File "\lib\wubi\application.py", line 132, in select_task
  File "\lib\wubi\application.py", line 158, in run_installer
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 450, in extract_diskimage
Exception: Extraction failed with code: 2
```

i've tried formatting the stick to fat32 and fat, and both generate this error

---

### Post by verymadpip on 2012-12-25
Hello there.

Is your iso file good?  Check its md5 sum. (In Windows 7 I use a free application named HashCalc)

When creating bootable USB sticks I use Unetbootin, it's worth a try.
[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

You did 'burn' the image to the USB stick & not simply copy the data over - that doesn't do the job.

---

### Post by Mark Phelps on 2012-12-25
You don't partition using Wubi; that installs INSIDE an existing NTFS partition, creating a virtual filesystem of its own.

---

### Post by oldfred on 2012-12-26
Please use code tags for any longer output. You highlight like a copy & click on # in the edit panel to auto add code tags.

Do you want wubi or a full partitioned install? Wubi is for Windows users who do not want to repartition and have an easy way to uninstall if they do not like it. Intended as a longer term testdrive over just using live install from DVD or flash drive.
       [https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)
[https://help.ubuntu.com/community/Wubi](https://help.ubuntu.com/community/Wubi)

If a full partitioned install use Windows to shrink the Windows partition, but do not create any new partitions.

       Also instructions for CD/DVD or USB
[http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)
Write image or burn image not copy ISO as one large file to CD.
[http://www.ubuntu.com/download/help/burn-a-cd-on-windows](http://www.ubuntu.com/download/help/burn-a-cd-on-windows)
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

Post this from live install terminal once you get it working.
sudo fdisk -lu

---

