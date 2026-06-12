---
title: "An error occurred: no such file in directory 'Q:\\wubildr'"
date: 2012-02-18
forum: New to Ubuntu
---

### Post by benjismith on 2012-02-18
When wubi is finishing the installation it says:
An error occurred: no such file in directory
what should i do?...
here is the log file:

```

02-16 20:38 INFO   root: === wubi 11.10 rev245 ===
02-16 20:38 DEBUG  root: Logfile is c:\users\benji\appdata\local\temp\wubi-11.10-rev245.log
02-16 20:38 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\Users\\Benji\\Downloads\\wubi.exe"']
02-16 20:38 DEBUG  CommonBackend: data_dir=C:\Users\Benji\AppData\Local\Temp\pylB53A.tmp\data
02-16 20:38 DEBUG  WindowsBackend: 7z=C:\Users\Benji\AppData\Local\Temp\pylB53A.tmp\bin\7z.exe
02-16 20:38 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
02-16 20:38 DEBUG  CommonBackend: Fetching basic info...
02-16 20:38 DEBUG  CommonBackend: original_exe=C:\Users\Benji\Downloads\wubi.exe
02-16 20:38 DEBUG  CommonBackend: platform=win32
02-16 20:38 DEBUG  CommonBackend: osname=nt
02-16 20:38 DEBUG  CommonBackend: language=en_US
02-16 20:38 DEBUG  CommonBackend: encoding=cp1252
02-16 20:38 DEBUG  WindowsBackend: arch=amd64
02-16 20:38 DEBUG  CommonBackend: Parsing isolist=C:\Users\Benji\AppData\Local\Temp\pylB53A.tmp\data\isolist.ini
02-16 20:38 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
02-16 20:38 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
02-16 20:38 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
02-16 20:38 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
02-16 20:38 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
02-16 20:38 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
02-16 20:38 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
02-16 20:38 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
02-16 20:38 DEBUG  WindowsBackend: Fetching host info...
02-16 20:38 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
02-16 20:38 DEBUG  WindowsBackend: windows version=vista
02-16 20:38 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium
02-16 20:38 DEBUG  WindowsBackend: windows_sp=None
02-16 20:38 DEBUG  WindowsBackend: windows_build=7601
02-16 20:38 DEBUG  WindowsBackend: gmt=-3
02-16 20:38 DEBUG  WindowsBackend: country=US
02-16 20:38 DEBUG  WindowsBackend: timezone=America/North_Dakota/Center
02-16 20:38 DEBUG  WindowsBackend: windows_username=Benji
02-16 20:38 DEBUG  WindowsBackend: user_full_name=Benji
02-16 20:38 DEBUG  WindowsBackend: user_directory=C:\Users\Benji
02-16 20:38 DEBUG  WindowsBackend: windows_language_code=1033
02-16 20:38 DEBUG  WindowsBackend: windows_language=English
02-16 20:38 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM) i7-2630QM CPU @ 2.00GHz
02-16 20:38 DEBUG  WindowsBackend: bootloader=vista
02-16 20:38 DEBUG  WindowsBackend: system_drive=Drive(C: hd 350974.433594 mb free ntfs)
02-16 20:38 DEBUG  WindowsBackend: drive=Drive(C: hd 350974.433594 mb free ntfs)
02-16 20:38 DEBUG  WindowsBackend: drive=Drive(D: hd 26417.21875 mb free ntfs)
02-16 20:38 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free )
02-16 20:38 DEBUG  WindowsBackend: drive=Drive(Q: hd 0.0 mb free )
02-16 20:38 DEBUG  WindowsBackend: uninstaller_path=None
02-16 20:38 DEBUG  WindowsBackend: previous_target_dir=None
02-16 20:38 DEBUG  WindowsBackend: previous_distro_name=None
02-16 20:38 DEBUG  WindowsBackend: keyboard_id=-268368887
02-16 20:38 DEBUG  WindowsBackend: keyboard_layout=us
02-16 20:38 DEBUG  WindowsBackend: keyboard_variant=
02-16 20:38 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
02-16 20:38 DEBUG  CommonBackend: locale=en_US.UTF-8
02-16 20:38 DEBUG  WindowsBackend: total_memory_mb=4095.99999905
02-16 20:38 DEBUG  CommonBackend: Searching ISOs on USB devices
02-16 20:38 DEBUG  CommonBackend: Searching for local CDs
02-16 20:38 DEBUG  Distro:   checking whether C:\Users\Benji\AppData\Local\Temp\pylB53A.tmp is a valid Ubuntu CD
02-16 20:38 DEBUG  Distro:     does not contain C:\Users\Benji\AppData\Local\Temp\pylB53A.tmp\casper\filesystem.squashfs
02-16 20:38 DEBUG  Distro:   checking whether C:\Users\Benji\AppData\Local\Temp\pylB53A.tmp is a valid Ubuntu CD
02-16 20:38 DEBUG  Distro:     does not contain C:\Users\Benji\AppData\Local\Temp\pylB53A.tmp\casper\filesystem.squashfs
02-16 20:38 DEBUG  Distro:   checking whether C:\Users\Benji\AppData\Local\Temp\pylB53A.tmp is a valid Kubuntu CD
02-16 20:38 DEBUG  Distro:     does not contain C:\Users\Benji\AppData\Local\Temp\pylB53A.tmp\casper\filesystem.squashfs
02-16 20:38 DEBUG  Distro:   checking whether C:\Users\Benji\AppData\Local\Temp\pylB53A.tmp is a valid Kubuntu CD
02-16 20:38 DEBUG  Distro:     does not contain C:\Users\Benji\AppData\Local\Temp\pylB53A.tmp\casper\filesystem.squashfs
02-16 20:38 DEBUG  Distro:   checking whether C:\Users\Benji\AppData\Local\Temp\pylB53A.tmp is a valid Xubuntu CD
02-16 20:38 DEBUG  Distro:     does not contain C:\Users\Benji\AppData\Local\Temp\pylB53A.tmp\casper\filesystem.squashfs
02-16 20:38 DEBUG  Distro:   checking whether C:\Users\Benji\AppData\Local\Temp\pylB53A.tmp is a valid Xubuntu CD
02-16 20:38 DEBUG  Distro:     does not contain C:\Users\Benji\AppData\Local\Temp\pylB53A.tmp\casper\filesystem.squashfs
02-16 20:38 DEBUG  Distro:   checking whether C:\Users\Benji\AppData\Local\Temp\pylB53A.tmp is a valid Mythbuntu CD
02-16 20:38 DEBUG  Distro:     does not contain C:\Users\Benji\AppData\Local\Temp\pylB53A.tmp\casper\filesystem.squashfs
02-16 20:38 DEBUG  Distro:   checking whether C:\Users\Benji\AppData\Local\Temp\pylB53A.tmp is a valid Mythbuntu CD
02-16 20:38 DEBUG  Distro:     does not contain C:\Users\Benji\AppData\Local\Temp\pylB53A.tmp\casper\filesystem.squashfs
02-16 20:38 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
02-16 20:38 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-16 20:38 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
02-16 20:38 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-16 20:38 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
02-16 20:38 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-16 20:38 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
02-16 20:38 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-16 20:38 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
02-16 20:38 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-16 20:38 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
02-16 20:38 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-16 20:38 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
02-16 20:38 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-16 20:38 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
02-16 20:38 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-16 20:38 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
02-16 20:38 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
02-16 20:38 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
02-16 20:38 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
02-16 20:38 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
02-16 20:38 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
02-16 20:38 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
02-16 20:38 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
02-16 20:38 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
02-16 20:38 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
02-16 20:38 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
02-16 20:38 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
02-16 20:38 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
02-16 20:38 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
02-16 20:38 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
02-16 20:38 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
02-16 20:38 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu CD
02-16 20:38 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
02-16 20:38 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu CD
02-16 20:38 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
02-16 20:38 DEBUG  Distro:   checking whether Q:\ is a valid Kubuntu CD
02-16 20:38 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
02-16 20:38 DEBUG  Distro:   checking whether Q:\ is a valid Kubuntu CD
02-16 20:38 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
02-16 20:38 DEBUG  Distro:   checking whether Q:\ is a valid Xubuntu CD
02-16 20:38 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
02-16 20:38 DEBUG  Distro:   checking whether Q:\ is a valid Xubuntu CD
02-16 20:38 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
02-16 20:38 DEBUG  Distro:   checking whether Q:\ is a valid Mythbuntu CD
02-16 20:38 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
02-16 20:38 DEBUG  Distro:   checking whether Q:\ is a valid Mythbuntu CD
02-16 20:38 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
02-16 20:38 INFO   root: Running the installer...
02-16 20:38 DEBUG  WindowsFrontend: __init__...
02-16 20:38 DEBUG  WindowsFrontend: on_init...
02-16 20:38 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Benji\AppData\Local\Temp\pylB53A.tmp\translations, languages=['en_US', 'en']
02-16 20:38 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Benji\AppData\Local\Temp\pylB53A.tmp\translations, languages=['en_US', 'en']
02-16 20:39 DEBUG  WinuiInstallationPage: target_drive=C:, installation_size=30000MB, distro_name=Ubuntu, language=en_US, locale=en_US.UTF-8, username=benji
02-16 20:39 INFO   root: Received settings
02-16 20:39 DEBUG  CommonBackend: Searching for local CD
02-16 20:39 DEBUG  Distro:   checking whether C:\Users\Benji\AppData\Local\Temp\pylB53A.tmp is a valid Ubuntu CD
02-16 20:39 DEBUG  Distro:     does not contain C:\Users\Benji\AppData\Local\Temp\pylB53A.tmp\casper\filesystem.squashfs
02-16 20:39 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
02-16 20:39 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-16 20:39 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
02-16 20:39 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
02-16 20:39 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu CD
02-16 20:39 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
02-16 20:39 DEBUG  CommonBackend: Searching for local ISO
02-16 20:39 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Benji\AppData\Local\Temp\pylB53A.tmp\translations, languages=['en_US', 'en']
02-16 20:39 DEBUG  TaskList: # Running tasklist...
02-16 20:39 DEBUG  TaskList: ## Running select_target_dir...
02-16 20:39 INFO   WindowsBackend: Installing into C:\ubuntu
02-16 20:39 DEBUG  TaskList: ## Finished select_target_dir
02-16 20:39 DEBUG  TaskList: ## Running create_dir_structure...
02-16 20:39 DEBUG  CommonBackend: Creating dir C:\ubuntu
02-16 20:39 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks
02-16 20:39 DEBUG  CommonBackend: Creating dir C:\ubuntu\install
02-16 20:39 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot
02-16 20:39 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot
02-16 20:39 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot\grub
02-16 20:39 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot\grub
02-16 20:39 DEBUG  TaskList: ## Finished create_dir_structure
02-16 20:39 DEBUG  TaskList: ## Running create_uninstaller...
02-16 20:39 DEBUG  WindowsBackend: Copying uninstaller C:\Users\Benji\Downloads\wubi.exe -> C:\ubuntu\uninstall-wubi.exe
02-16 20:39 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString C:\ubuntu\uninstall-wubi.exe
02-16 20:39 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir C:\ubuntu
02-16 20:39 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
02-16 20:39 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon C:\ubuntu\Ubuntu.ico
02-16 20:39 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 11.10-rev245
02-16 20:39 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
02-16 20:39 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com](http://www.ubuntu.com)
02-16 20:39 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
02-16 20:39 DEBUG  TaskList: ## Finished create_uninstaller
02-16 20:39 DEBUG  TaskList: ## Running create_preseed_diskimage...
02-16 20:39 DEBUG  TaskList: ## Finished create_preseed_diskimage
02-16 20:39 DEBUG  TaskList: ## Running get_diskimage...
02-16 20:39 DEBUG  TaskList: New task download
02-16 20:39 DEBUG  TaskList: ### Running download...
02-16 20:39 DEBUG  downloader: downloading [http://releases.ubuntu.com/11.10/ubuntu-11.10-wubi-amd64.tar.xz](http://releases.ubuntu.com/11.10/ubuntu-11.10-wubi-amd64.tar.xz) > C:\ubuntu\disks\ubuntu-11.10-wubi-amd64.tar.xz
02-16 20:39 DEBUG  downloader: Download start filename=C:\ubuntu\disks\ubuntu-11.10-wubi-amd64.tar.xz, url=http://releases.ubuntu.com/11.10/ubuntu-11.10-wubi-amd64.tar.xz, basename=ubuntu-11.10-wubi-amd64.tar.xz, length=507143012, text=None
02-16 20:42 DEBUG  downloader: download finished (read 29167522 bytes)
02-16 20:42 DEBUG  TaskList: ### Finished download
02-16 20:42 DEBUG  TaskList: ## Finished get_diskimage
02-16 20:42 DEBUG  TaskList: ## Running extract_diskimage...
02-16 20:42 ERROR  TaskList: Extraction failed with code: 2
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 448, in extract_diskimage
Exception: Extraction failed with code: 2
02-16 20:42 DEBUG  TaskList: # Cancelling tasklist
02-16 20:42 DEBUG  TaskList: # Finished tasklist
02-16 20:42 ERROR  root: Extraction failed with code: 2
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 58, in run
  File "\lib\wubi\application.py", line 132, in select_task
  File "\lib\wubi\application.py", line 158, in run_installer
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 448, in extract_diskimage
Exception: Extraction failed with code: 2
02-16 20:43 INFO   root: === wubi 11.10 rev245 ===
02-16 20:43 DEBUG  root: Logfile is c:\users\benji\appdata\local\temp\wubi-11.10-rev245.log
02-16 20:43 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\Users\\Benji\\Downloads\\wubi.exe"']
02-16 20:43 DEBUG  CommonBackend: data_dir=C:\Users\Benji\AppData\Local\Temp\pyl8507.tmp\data
02-16 20:43 DEBUG  WindowsBackend: 7z=C:\Users\Benji\AppData\Local\Temp\pyl8507.tmp\bin\7z.exe
02-16 20:43 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
02-16 20:43 DEBUG  CommonBackend: Fetching basic info...
02-16 20:43 DEBUG  CommonBackend: original_exe=C:\Users\Benji\Downloads\wubi.exe
02-16 20:43 DEBUG  CommonBackend: platform=win32
02-16 20:43 DEBUG  CommonBackend: osname=nt
02-16 20:43 DEBUG  CommonBackend: language=en_US
02-16 20:43 DEBUG  CommonBackend: encoding=cp1252
02-16 20:43 DEBUG  WindowsBackend: arch=amd64
02-16 20:43 DEBUG  CommonBackend: Parsing isolist=C:\Users\Benji\AppData\Local\Temp\pyl8507.tmp\data\isolist.ini
02-16 20:43 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
02-16 20:43 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
02-16 20:43 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
02-16 20:43 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
02-16 20:43 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
02-16 20:43 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
02-16 20:43 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
02-16 20:43 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
02-16 20:43 DEBUG  WindowsBackend: Fetching host info...
02-16 20:43 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
02-16 20:43 DEBUG  WindowsBackend: windows version=vista
02-16 20:43 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium
02-16 20:43 DEBUG  WindowsBackend: windows_sp=None
02-16 20:43 DEBUG  WindowsBackend: windows_build=7601
02-16 20:43 DEBUG  WindowsBackend: gmt=-3
02-16 20:43 DEBUG  WindowsBackend: country=US
02-16 20:43 DEBUG  WindowsBackend: timezone=America/North_Dakota/Center
02-16 20:43 DEBUG  WindowsBackend: windows_username=Benji
02-16 20:43 DEBUG  WindowsBackend: user_full_name=Benji
02-16 20:43 DEBUG  WindowsBackend: user_directory=C:\Users\Benji
02-16 20:43 DEBUG  WindowsBackend: windows_language_code=1033
02-16 20:43 DEBUG  WindowsBackend: windows_language=English
02-16 20:43 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM) i7-2630QM CPU @ 2.00GHz
02-16 20:43 DEBUG  WindowsBackend: bootloader=vista
02-16 20:43 DEBUG  WindowsBackend: system_drive=Drive(C: hd 350827.609375 mb free ntfs)
02-16 20:43 DEBUG  WindowsBackend: drive=Drive(C: hd 350827.609375 mb free ntfs)
02-16 20:43 DEBUG  WindowsBackend: drive=Drive(D: hd 26417.21875 mb free ntfs)
02-16 20:43 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free )
02-16 20:43 DEBUG  WindowsBackend: drive=Drive(Q: hd 0.0 mb free )
02-16 20:43 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
02-16 20:43 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
02-16 20:43 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
02-16 20:43 DEBUG  WindowsBackend: keyboard_id=-268368887
02-16 20:43 DEBUG  WindowsBackend: keyboard_layout=us
02-16 20:43 DEBUG  WindowsBackend: keyboard_variant=
02-16 20:43 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
02-16 20:43 DEBUG  CommonBackend: locale=en_US.UTF-8
02-16 20:43 DEBUG  WindowsBackend: total_memory_mb=4095.99999905
02-16 20:43 DEBUG  CommonBackend: Searching ISOs on USB devices
02-16 20:43 DEBUG  CommonBackend: Searching for local CDs
02-16 20:43 DEBUG  Distro:   checking whether C:\Users\Benji\AppData\Local\Temp\pyl8507.tmp is a valid Ubuntu CD
02-16 20:43 DEBUG  Distro:     does not contain C:\Users\Benji\AppData\Local\Temp\pyl8507.tmp\casper\filesystem.squashfs
02-16 20:43 DEBUG  Distro:   checking whether C:\Users\Benji\AppData\Local\Temp\pyl8507.tmp is a valid Ubuntu CD
02-16 20:43 DEBUG  Distro:     does not contain C:\Users\Benji\AppData\Local\Temp\pyl8507.tmp\casper\filesystem.squashfs
02-16 20:43 DEBUG  Distro:   checking whether C:\Users\Benji\AppData\Local\Temp\pyl8507.tmp is a valid Kubuntu CD
02-16 20:43 DEBUG  Distro:     does not contain C:\Users\Benji\AppData\Local\Temp\pyl8507.tmp\casper\filesystem.squashfs
02-16 20:43 DEBUG  Distro:   checking whether C:\Users\Benji\AppData\Local\Temp\pyl8507.tmp is a valid Kubuntu CD
02-16 20:43 DEBUG  Distro:     does not contain C:\Users\Benji\AppData\Local\Temp\pyl8507.tmp\casper\filesystem.squashfs
02-16 20:43 DEBUG  Distro:   checking whether C:\Users\Benji\AppData\Local\Temp\pyl8507.tmp is a valid Xubuntu CD
02-16 20:43 DEBUG  Distro:     does not contain C:\Users\Benji\AppData\Local\Temp\pyl8507.tmp\casper\filesystem.squashfs
02-16 20:43 DEBUG  Distro:   checking whether C:\Users\Benji\AppData\Local\Temp\pyl8507.tmp is a valid Xubuntu CD
02-16 20:43 DEBUG  Distro:     does not contain C:\Users\Benji\AppData\Local\Temp\pyl8507.tmp\casper\filesystem.squashfs
02-16 20:43 DEBUG  Distro:   checking whether C:\Users\Benji\AppData\Local\Temp\pyl8507.tmp is a valid Mythbuntu CD
02-16 20:43 DEBUG  Distro:     does not contain C:\Users\Benji\AppData\Local\Temp\pyl8507.tmp\casper\filesystem.squashfs
02-16 20:43 DEBUG  Distro:   checking whether C:\Users\Benji\AppData\Local\Temp\pyl8507.tmp is a valid Mythbuntu CD
02-16 20:43 DEBUG  Distro:     does not contain C:\Users\Benji\AppData\Local\Temp\pyl8507.tmp\casper\filesystem.squashfs
02-16 20:43 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
02-16 20:43 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-16 20:43 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
02-16 20:43 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-16 20:43 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
02-16 20:43 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-16 20:43 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
02-16 20:43 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-16 20:43 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
02-16 20:43 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-16 20:43 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
02-16 20:43 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-16 20:43 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
02-16 20:43 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-16 20:43 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
02-16 20:43 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-16 20:43 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
02-16 20:43 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
02-16 20:43 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
02-16 20:43 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
02-16 20:43 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
02-16 20:43 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
02-16 20:43 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
02-16 20:43 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
02-16 20:43 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
02-16 20:43 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
02-16 20:43 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
02-16 20:43 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
02-16 20:43 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
02-16 20:43 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
02-16 20:43 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
02-16 20:43 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
02-16 20:43 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu CD
02-16 20:43 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
02-16 20:43 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu CD
02-16 20:43 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
02-16 20:43 DEBUG  Distro:   checking whether Q:\ is a valid Kubuntu CD
02-16 20:43 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
02-16 20:43 DEBUG  Distro:   checking whether Q:\ is a valid Kubuntu CD
02-16 20:43 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
02-16 20:43 DEBUG  Distro:   checking whether Q:\ is a valid Xubuntu CD
02-16 20:43 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
02-16 20:43 DEBUG  Distro:   checking whether Q:\ is a valid Xubuntu CD
02-16 20:43 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
02-16 20:43 DEBUG  Distro:   checking whether Q:\ is a valid Mythbuntu CD
02-16 20:43 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
02-16 20:43 DEBUG  Distro:   checking whether Q:\ is a valid Mythbuntu CD
02-16 20:43 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
02-16 20:43 INFO   root: Already installed, running the uninstaller...
02-16 20:43 INFO   root: Running the uninstaller...
02-16 20:43 INFO   CommonBackend: This is the uninstaller running
02-16 20:43 DEBUG  WindowsFrontend: __init__...
02-16 20:43 DEBUG  WindowsFrontend: on_init...
02-16 20:43 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Benji\AppData\Local\Temp\pyl8507.tmp\translations, languages=['en_US', 'en']
02-16 20:43 INFO   root: Received settings
02-16 20:43 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Benji\AppData\Local\Temp\pyl8507.tmp\translations, languages=['en_US', 'en']
02-16 20:43 DEBUG  TaskList: # Running tasklist...
02-16 20:43 DEBUG  TaskList: ## Running Remove bootloader entry...
02-16 20:43 DEBUG  WindowsBackend: Could not find bcd id
02-16 20:43 DEBUG  WindowsBackend: undo_bootini C:
02-16 20:43 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 350827.609375 mb free ntfs)
02-16 20:43 DEBUG  WindowsBackend: undo_bootini D:
02-16 20:43 DEBUG  WindowsBackend: undo_configsys Drive(D: hd 26417.21875 mb free ntfs)
02-16 20:43 DEBUG  WindowsBackend: undo_bootini Q:
02-16 20:43 DEBUG  WindowsBackend: undo_configsys Drive(Q: hd 0.0 mb free )
02-16 20:43 DEBUG  TaskList: ## Finished Remove bootloader entry
02-16 20:43 DEBUG  TaskList: ## Running Remove target dir...
02-16 20:43 DEBUG  CommonBackend: Deleting C:\ubuntu
02-16 20:43 DEBUG  TaskList: ## Finished Remove target dir
02-16 20:43 DEBUG  TaskList: ## Running Remove registry key...
02-16 20:43 DEBUG  TaskList: ## Finished Remove registry key
02-16 20:43 DEBUG  TaskList: # Finished tasklist
02-16 20:43 INFO   root: Almost finished uninstalling
02-16 20:43 INFO   root: Finished uninstallation
02-16 20:43 DEBUG  CommonBackend: Fetching basic info...
02-16 20:43 DEBUG  CommonBackend: original_exe=C:\Users\Benji\Downloads\wubi.exe
02-16 20:43 DEBUG  CommonBackend: platform=win32
02-16 20:43 DEBUG  CommonBackend: osname=nt
02-16 20:43 DEBUG  WindowsBackend: arch=amd64
02-16 20:43 DEBUG  CommonBackend: Parsing isolist=C:\Users\Benji\AppData\Local\Temp\pyl8507.tmp\data\isolist.ini
02-16 20:43 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
02-16 20:43 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
02-16 20:43 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
02-16 20:43 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
02-16 20:43 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
02-16 20:43 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
02-16 20:43 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
02-16 20:43 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
02-16 20:43 DEBUG  WindowsBackend: Fetching host info...
02-16 20:43 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
02-16 20:43 DEBUG  WindowsBackend: windows version=vista
02-16 20:43 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium
02-16 20:43 DEBUG  WindowsBackend: windows_sp=None
02-16 20:43 DEBUG  WindowsBackend: windows_build=7601
02-16 20:43 DEBUG  WindowsBackend: gmt=-3
02-16 20:43 DEBUG  WindowsBackend: country=US
02-16 20:43 DEBUG  WindowsBackend: timezone=America/North_Dakota/Center
02-16 20:43 DEBUG  WindowsBackend: windows_username=Benji
02-16 20:43 DEBUG  WindowsBackend: user_full_name=Benji
02-16 20:43 DEBUG  WindowsBackend: user_directory=C:\Users\Benji
02-16 20:43 DEBUG  WindowsBackend: windows_language_code=1033
02-16 20:43 DEBUG  WindowsBackend: windows_language=English
02-16 20:43 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM) i7-2630QM CPU @ 2.00GHz
02-16 20:43 DEBUG  WindowsBackend: bootloader=vista
02-16 20:43 DEBUG  WindowsBackend: system_drive=Drive(C: hd 350973.957031 mb free ntfs)
02-16 20:43 DEBUG  WindowsBackend: drive=Drive(C: hd 350973.957031 mb free ntfs)
02-16 20:43 DEBUG  WindowsBackend: drive=Drive(D: hd 26417.21875 mb free ntfs)
02-16 20:43 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free )
02-16 20:43 DEBUG  WindowsBackend: drive=Drive(Q: hd 0.0 mb free )
02-16 20:43 DEBUG  WindowsBackend: uninstaller_path=None
02-16 20:43 DEBUG  WindowsBackend: previous_target_dir=None
02-16 20:43 DEBUG  WindowsBackend: previous_distro_name=None
02-16 20:43 DEBUG  WindowsBackend: keyboard_id=-268368887
02-16 20:43 DEBUG  WindowsBackend: keyboard_layout=us
02-16 20:43 DEBUG  WindowsBackend: keyboard_variant=
02-16 20:43 DEBUG  WindowsBackend: total_memory_mb=4095.99999905
02-16 20:43 DEBUG  CommonBackend: Searching ISOs on USB devices
02-16 20:43 DEBUG  CommonBackend: Searching for local CDs
02-16 20:43 DEBUG  Distro:   checking whether C:\Users\Benji\AppData\Local\Temp\pyl8507.tmp is a valid Ubuntu CD
02-16 20:43 DEBUG  Distro:     does not contain C:\Users\Benji\AppData\Local\Temp\pyl8507.tmp\casper\filesystem.squashfs
02-16 20:43 DEBUG  Distro:   checking whether C:\Users\Benji\AppData\Local\Temp\pyl8507.tmp is a valid Ubuntu CD
02-16 20:43 DEBUG  Distro:     does not contain C:\Users\Benji\AppData\Local\Temp\pyl8507.tmp\casper\filesystem.squashfs
02-16 20:43 DEBUG  Distro:   checking whether C:\Users\Benji\AppData\Local\Temp\pyl8507.tmp is a valid Kubuntu CD
02-16 20:43 DEBUG  Distro:     does not contain C:\Users\Benji\AppData\Local\Temp\pyl8507.tmp\casper\filesystem.squashfs
02-16 20:43 DEBUG  Distro:   checking whether C:\Users\Benji\AppData\Local\Temp\pyl8507.tmp is a valid Kubuntu CD
02-16 20:43 DEBUG  Distro:     does not contain C:\Users\Benji\AppData\Local\Temp\pyl8507.tmp\casper\filesystem.squashfs
02-16 20:43 DEBUG  Distro:   checking whether C:\Users\Benji\AppData\Local\Temp\pyl8507.tmp is a valid Xubuntu CD
02-16 20:43 DEBUG  Distro:     does not contain C:\Users\Benji\AppData\Local\Temp\pyl8507.tmp\casper\filesystem.squashfs
02-16 20:43 DEBUG  Distro:   checking whether C:\Users\Benji\AppData\Local\Temp\pyl8507.tmp is a valid Xubuntu CD
02-16 20:43 DEBUG  Distro:     does not contain C:\Users\Benji\AppData\Local\Temp\pyl8507.tmp\casper\filesystem.squashfs
02-16 20:43 DEBUG  Distro:   checking whether C:\Users\Benji\AppData\Local\Temp\pyl8507.tmp is a valid Mythbuntu CD
02-16 20:43 DEBUG  Distro:     does not contain C:\Users\Benji\AppData\Local\Temp\pyl8507.tmp\casper\filesystem.squashfs
02-16 20:43 DEBUG  Distro:   checking whether C:\Users\Benji\AppData\Local\Temp\pyl8507.tmp is a valid Mythbuntu CD
02-16 20:43 DEBUG  Distro:     does not contain C:\Users\Benji\AppData\Local\Temp\pyl8507.tmp\casper\filesystem.squashfs
02-16 20:43 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
02-16 20:43 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-16 20:43 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
02-16 20:43 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-16 20:43 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
02-16 20:43 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-16 20:43 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
02-16 20:43 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-16 20:43 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
02-16 20:43 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-16 20:43 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
02-16 20:43 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-16 20:43 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
02-16 20:43 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-16 20:43 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
02-16 20:43 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-16 20:43 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
02-16 20:43 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
02-16 20:43 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
02-16 20:43 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
02-16 20:43 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
02-16 20:43 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
02-16 20:43 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
02-16 20:43 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
02-16 20:43 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
02-16 20:43 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
02-16 20:43 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
02-16 20:43 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
02-16 20:43 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
02-16 20:43 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
02-16 20:43 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
02-16 20:43 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
02-16 20:43 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu CD
02-16 20:43 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
02-16 20:43 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu CD
02-16 20:43 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
02-16 20:43 DEBUG  Distro:   checking whether Q:\ is a valid Kubuntu CD
02-16 20:43 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
02-16 20:43 DEBUG  Distro:   checking whether Q:\ is a valid Kubuntu CD
02-16 20:43 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
02-16 20:43 DEBUG  Distro:   checking whether Q:\ is a valid Xubuntu CD
02-16 20:43 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
02-16 20:43 DEBUG  Distro:   checking whether Q:\ is a valid Xubuntu CD
02-16 20:43 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
02-16 20:43 DEBUG  Distro:   checking whether Q:\ is a valid Mythbuntu CD
02-16 20:43 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
02-16 20:43 DEBUG  Distro:   checking whether Q:\ is a valid Mythbuntu CD
02-16 20:43 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
02-16 20:43 INFO   root: Running the installer...
02-16 20:43 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Benji\AppData\Local\Temp\pyl8507.tmp\translations, languages=['en_US', 'en']
02-16 20:43 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Benji\AppData\Local\Temp\pyl8507.tmp\translations, languages=['en_US', 'en']
02-16 20:43 DEBUG  WinuiInstallationPage: target_drive=C:, installation_size=30000MB, distro_name=Ubuntu, language=en_US, locale=en_US.UTF-8, username=benji
02-16 20:43 INFO   root: Received settings
02-16 20:43 DEBUG  CommonBackend: Searching for local CD
02-16 20:43 DEBUG  Distro:   checking whether C:\Users\Benji\AppData\Local\Temp\pyl8507.tmp is a valid Ubuntu CD
02-16 20:43 DEBUG  Distro:     does not contain C:\Users\Benji\AppData\Local\Temp\pyl8507.tmp\casper\filesystem.squashfs
02-16 20:43 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
02-16 20:43 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-16 20:43 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
02-16 20:43 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
02-16 20:43 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu CD
02-16 20:43 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
02-16 20:43 DEBUG  CommonBackend: Searching for local ISO
02-16 20:43 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Benji\AppData\Local\Temp\pyl8507.tmp\translations, languages=['en_US', 'en']
02-16 20:43 DEBUG  TaskList: # Running tasklist...
02-16 20:43 DEBUG  TaskList: ## Running select_target_dir...
02-16 20:43 INFO   WindowsBackend: Installing into C:\ubuntu
02-16 20:43 DEBUG  TaskList: ## Finished select_target_dir
02-16 20:43 DEBUG  TaskList: ## Running create_dir_structure...
02-16 20:43 DEBUG  CommonBackend: Creating dir C:\ubuntu
02-16 20:43 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks
02-16 20:43 DEBUG  CommonBackend: Creating dir C:\ubuntu\install
02-16 20:43 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot
02-16 20:43 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot
02-16 20:43 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot\grub
02-16 20:43 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot\grub
02-16 20:43 DEBUG  TaskList: ## Finished create_dir_structure
02-16 20:43 DEBUG  TaskList: ## Running create_uninstaller...
02-16 20:43 DEBUG  WindowsBackend: Copying uninstaller C:\Users\Benji\Downloads\wubi.exe -> C:\ubuntu\uninstall-wubi.exe
02-16 20:43 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString C:\ubuntu\uninstall-wubi.exe
02-16 20:43 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir C:\ubuntu
02-16 20:43 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
02-16 20:43 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon C:\ubuntu\Ubuntu.ico
02-16 20:43 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 11.10-rev245
02-16 20:43 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
02-16 20:43 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com](http://www.ubuntu.com)
02-16 20:43 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
02-16 20:43 DEBUG  TaskList: ## Finished create_uninstaller
02-16 20:43 DEBUG  TaskList: ## Running create_preseed_diskimage...
02-16 20:43 DEBUG  TaskList: ## Finished create_preseed_diskimage
02-16 20:43 DEBUG  TaskList: ## Running get_diskimage...
02-16 20:43 DEBUG  TaskList: New task download
02-16 20:43 DEBUG  TaskList: ### Running download...
02-16 20:43 DEBUG  downloader: downloading [http://releases.ubuntu.com/11.10/ubuntu-11.10-wubi-amd64.tar.xz](http://releases.ubuntu.com/11.10/ubuntu-11.10-wubi-amd64.tar.xz) > C:\ubuntu\disks\ubuntu-11.10-wubi-amd64.tar.xz
02-16 20:43 DEBUG  downloader: Download start filename=C:\ubuntu\disks\ubuntu-11.10-wubi-amd64.tar.xz, url=http://releases.ubuntu.com/11.10/ubuntu-11.10-wubi-amd64.tar.xz, basename=ubuntu-11.10-wubi-amd64.tar.xz, length=507143012, text=None
02-16 20:48 INFO   WindowsFrontend: Operation cancelled
02-16 20:48 DEBUG  WindowsFrontend: frontend.quit
02-16 20:48 DEBUG  WindowsFrontend: frontend.on_quit
02-16 20:48 DEBUG  WindowsFrontend: stopping remaining background tasks: 'tasklist'
02-16 20:48 DEBUG  TaskList: # Cancelling tasklist
02-16 20:48 DEBUG  WindowsFrontend: Task cancellation timed out, the program will exit anyway
02-16 20:48 DEBUG  root: application.on_quit
02-16 20:48 DEBUG  root: Forceful exit
02-16 20:48 INFO   root: sys.exit
02-16 20:49 INFO   root: === wubi 11.10 rev245 ===
02-16 20:49 DEBUG  root: Logfile is c:\users\benji\appdata\local\temp\wubi-11.10-rev245.log
02-16 20:49 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\Users\\Benji\\Downloads\\wubi.exe"']
02-16 20:49 DEBUG  CommonBackend: data_dir=C:\Users\Benji\AppData\Local\Temp\pyl46CF.tmp\data
02-16 20:49 DEBUG  WindowsBackend: 7z=C:\Users\Benji\AppData\Local\Temp\pyl46CF.tmp\bin\7z.exe
02-16 20:49 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
02-16 20:49 DEBUG  CommonBackend: Fetching basic info...
02-16 20:49 DEBUG  CommonBackend: original_exe=C:\Users\Benji\Downloads\wubi.exe
02-16 20:49 DEBUG  CommonBackend: platform=win32
02-16 20:49 DEBUG  CommonBackend: osname=nt
02-16 20:49 DEBUG  CommonBackend: language=en_US
02-16 20:49 DEBUG  CommonBackend: encoding=cp1252
02-16 20:49 DEBUG  WindowsBackend: arch=amd64
02-16 20:49 DEBUG  CommonBackend: Parsing isolist=C:\Users\Benji\AppData\Local\Temp\pyl46CF.tmp\data\isolist.ini
02-16 20:49 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
02-16 20:49 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
02-16 20:49 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
02-16 20:49 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
02-16 20:49 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
02-16 20:49 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
02-16 20:49 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
02-16 20:49 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
02-16 20:49 DEBUG  WindowsBackend: Fetching host info...
02-16 20:49 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
02-16 20:49 DEBUG  WindowsBackend: windows version=vista
02-16 20:49 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium
02-16 20:49 DEBUG  WindowsBackend: windows_sp=None
02-16 20:49 DEBUG  WindowsBackend: windows_build=7601
02-16 20:49 DEBUG  WindowsBackend: gmt=-3
02-16 20:49 DEBUG  WindowsBackend: country=US
02-16 20:49 DEBUG  WindowsBackend: timezone=America/North_Dakota/Center
02-16 20:49 DEBUG  WindowsBackend: windows_username=Benji
02-16 20:49 DEBUG  WindowsBackend: user_full_name=Benji
02-16 20:49 DEBUG  WindowsBackend: user_directory=C:\Users\Benji
02-16 20:49 DEBUG  WindowsBackend: windows_language_code=1033
02-16 20:49 DEBUG  WindowsBackend: windows_language=English
02-16 20:49 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM) i7-2630QM CPU @ 2.00GHz
02-16 20:49 DEBUG  WindowsBackend: bootloader=vista
02-16 20:49 DEBUG  WindowsBackend: system_drive=Drive(C: hd 350943.496094 mb free ntfs)
02-16 20:49 DEBUG  WindowsBackend: drive=Drive(C: hd 350943.496094 mb free ntfs)
02-16 20:49 DEBUG  WindowsBackend: drive=Drive(D: hd 26417.21875 mb free ntfs)
02-16 20:49 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free )
02-16 20:49 DEBUG  WindowsBackend: drive=Drive(Q: hd 0.0 mb free )
02-16 20:49 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
02-16 20:49 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
02-16 20:49 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
02-16 20:49 DEBUG  WindowsBackend: keyboard_id=-268368887
02-16 20:49 DEBUG  WindowsBackend: keyboard_layout=us
02-16 20:49 DEBUG  WindowsBackend: keyboard_variant=
02-16 20:49 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
02-16 20:49 DEBUG  CommonBackend: locale=en_US.UTF-8
02-16 20:49 DEBUG  WindowsBackend: total_memory_mb=4095.99999905
02-16 20:49 DEBUG  CommonBackend: Searching ISOs on USB devices
02-16 20:49 DEBUG  CommonBackend: Searching for local CDs
02-16 20:49 DEBUG  Distro:   checking whether C:\Users\Benji\AppData\Local\Temp\pyl46CF.tmp is a valid Ubuntu CD
02-16 20:49 DEBUG  Distro:     does not contain C:\Users\Benji\AppData\Local\Temp\pyl46CF.tmp\casper\filesystem.squashfs
02-16 20:49 DEBUG  Distro:   checking whether C:\Users\Benji\AppData\Local\Temp\pyl46CF.tmp is a valid Ubuntu CD
02-16 20:49 DEBUG  Distro:     does not contain C:\Users\Benji\AppData\Local\Temp\pyl46CF.tmp\casper\filesystem.squashfs
02-16 20:49 DEBUG  Distro:   checking whether C:\Users\Benji\AppData\Local\Temp\pyl46CF.tmp is a valid Kubuntu CD
02-16 20:49 DEBUG  Distro:     does not contain C:\Users\Benji\AppData\Local\Temp\pyl46CF.tmp\casper\filesystem.squashfs
02-16 20:49 DEBUG  Distro:   checking whether C:\Users\Benji\AppData\Local\Temp\pyl46CF.tmp is a valid Kubuntu CD
02-16 20:49 DEBUG  Distro:     does not contain C:\Users\Benji\AppData\Local\Temp\pyl46CF.tmp\casper\filesystem.squashfs
02-16 20:49 DEBUG  Distro:   checking whether C:\Users\Benji\AppData\Local\Temp\pyl46CF.tmp is a valid Xubuntu CD
02-16 20:49 DEBUG  Distro:     does not contain C:\Users\Benji\AppData\Local\Temp\pyl46CF.tmp\casper\filesystem.squashfs
02-16 20:49 DEBUG  Distro:   checking whether C:\Users\Benji\AppData\Local\Temp\pyl46CF.tmp is a valid Xubuntu CD
02-16 20:49 DEBUG  Distro:     does not contain C:\Users\Benji\AppData\Local\Temp\pyl46CF.tmp\casper\filesystem.squashfs
02-16 20:49 DEBUG  Distro:   checking whether C:\Users\Benji\AppData\Local\Temp\pyl46CF.tmp is a valid Mythbuntu CD
02-16 20:49 DEBUG  Distro:     does not contain C:\Users\Benji\AppData\Local\Temp\pyl46CF.tmp\casper\filesystem.squashfs
02-16 20:49 DEBUG  Distro:   checking whether C:\Users\Benji\AppData\Local\Temp\pyl46CF.tmp is a valid Mythbuntu CD
02-16 20:49 DEBUG  Distro:     does not contain C:\Users\Benji\AppData\Local\Temp\pyl46CF.tmp\casper\filesystem.squashfs
02-16 20:49 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
02-16 20:49 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-16 20:49 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
02-16 20:49 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-16 20:49 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
02-16 20:49 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-16 20:49 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
02-16 20:49 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-16 20:49 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
02-16 20:49 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-16 20:49 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
02-16 20:49 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-16 20:49 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
02-16 20:49 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-16 20:49 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
02-16 20:49 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-16 20:49 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
02-16 20:49 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
02-16 20:49 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
02-16 20:49 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
02-16 20:49 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
02-16 20:49 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
02-16 20:49 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
02-16 20:49 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
02-16 20:49 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
02-16 20:49 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
02-16 20:49 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
02-16 20:49 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
02-16 20:49 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
02-16 20:49 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
02-16 20:49 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
02-16 20:49 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
02-16 20:49 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu CD
02-16 20:49 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
02-16 20:49 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu CD
02-16 20:49 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
02-16 20:49 DEBUG  Distro:   checking whether Q:\ is a valid Kubuntu CD
02-16 20:49 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
02-16 20:49 DEBUG  Distro:   checking whether Q:\ is a valid Kubuntu CD
02-16 20:49 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
02-16 20:49 DEBUG  Distro:   checking whether Q:\ is a valid Xubuntu CD
02-16 20:49 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
02-16 20:49 DEBUG  Distro:   checking whether Q:\ is a valid Xubuntu CD
02-16 20:49 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
02-16 20:49 DEBUG  Distro:   checking whether Q:\ is a valid Mythbuntu CD
02-16 20:49 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
02-16 20:49 DEBUG  Distro:   checking whether Q:\ is a valid Mythbuntu CD
02-16 20:49 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
02-16 20:49 INFO   root: Already installed, running the uninstaller...
02-16 20:49 INFO   root: Running the uninstaller...
02-16 20:49 INFO   CommonBackend: This is the uninstaller running
02-16 20:49 DEBUG  WindowsFrontend: __init__...
02-16 20:49 DEBUG  WindowsFrontend: on_init...
02-16 20:49 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Benji\AppData\Local\Temp\pyl46CF.tmp\translations, languages=['en_US', 'en']
02-16 20:49 INFO   root: Received settings
02-16 20:49 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Benji\AppData\Local\Temp\pyl46CF.tmp\translations, languages=['en_US', 'en']
02-16 20:49 DEBUG  TaskList: # Running tasklist...
02-16 20:49 DEBUG  TaskList: ## Running Remove bootloader entry...
02-16 20:49 DEBUG  WindowsBackend: Could not find bcd id
02-16 20:49 DEBUG  WindowsBackend: undo_bootini C:
02-16 20:49 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 350943.496094 mb free ntfs)
02-16 20:49 DEBUG  WindowsBackend: undo_bootini D:
02-16 20:49 DEBUG  WindowsBackend: undo_configsys Drive(D: hd 26417.21875 mb free ntfs)
02-16 20:49 DEBUG  WindowsBackend: undo_bootini Q:
02-16 20:49 DEBUG  WindowsBackend: undo_configsys Drive(Q: hd 0.0 mb free )
02-16 20:49 DEBUG  TaskList: ## Finished Remove bootloader entry
02-16 20:49 DEBUG  TaskList: ## Running Remove target dir...
02-16 20:49 DEBUG  CommonBackend: Deleting C:\ubuntu
02-16 20:49 DEBUG  TaskList: ## Finished Remove target dir
02-16 20:49 DEBUG  TaskList: ## Running Remove registry key...
02-16 20:49 DEBUG  TaskList: ## Finished Remove registry key
02-16 20:49 DEBUG  TaskList: # Finished tasklist
02-16 20:49 INFO   root: Almost finished uninstalling
02-16 20:49 INFO   root: Finished uninstallation
02-16 20:49 DEBUG  CommonBackend: Fetching basic info...
02-16 20:49 DEBUG  CommonBackend: original_exe=C:\Users\Benji\Downloads\wubi.exe
02-16 20:49 DEBUG  CommonBackend: platform=win32
02-16 20:49 DEBUG  CommonBackend: osname=nt
02-16 20:49 DEBUG  WindowsBackend: arch=amd64
02-16 20:49 DEBUG  CommonBackend: Parsing isolist=C:\Users\Benji\AppData\Local\Temp\pyl46CF.tmp\data\isolist.ini
02-16 20:49 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
02-16 20:49 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
02-16 20:49 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
02-16 20:49 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
02-16 20:49 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
02-16 20:49 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
02-16 20:49 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
02-16 20:49 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
02-16 20:49 DEBUG  WindowsBackend: Fetching host info...
02-16 20:49 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
02-16 20:49 DEBUG  WindowsBackend: windows version=vista
02-16 20:49 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium
02-16 20:49 DEBUG  WindowsBackend: windows_sp=None
02-16 20:49 DEBUG  WindowsBackend: windows_build=7601
02-16 20:49 DEBUG  WindowsBackend: gmt=-3
02-16 20:49 DEBUG  WindowsBackend: country=US
02-16 20:49 DEBUG  WindowsBackend: timezone=America/North_Dakota/Center
02-16 20:49 DEBUG  WindowsBackend: windows_username=Benji
02-16 20:49 DEBUG  WindowsBackend: user_full_name=Benji
02-16 20:49 DEBUG  WindowsBackend: user_directory=C:\Users\Benji
02-16 20:49 DEBUG  WindowsBackend: windows_language_code=1033
02-16 20:49 DEBUG  WindowsBackend: windows_language=English
02-16 20:49 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM) i7-2630QM CPU @ 2.00GHz
02-16 20:49 DEBUG  WindowsBackend: bootloader=vista
02-16 20:49 DEBUG  WindowsBackend: system_drive=Drive(C: hd 350973.082031 mb free ntfs)
02-16 20:49 DEBUG  WindowsBackend: drive=Drive(C: hd 350973.082031 mb free ntfs)
02-16 20:49 DEBUG  WindowsBackend: drive=Drive(D: hd 26417.21875 mb free ntfs)
02-16 20:49 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free )
02-16 20:49 DEBUG  WindowsBackend: drive=Drive(Q: hd 0.0 mb free )
02-16 20:49 DEBUG  WindowsBackend: uninstaller_path=None
02-16 20:49 DEBUG  WindowsBackend: previous_target_dir=None
02-16 20:49 DEBUG  WindowsBackend: previous_distro_name=None
02-16 20:49 DEBUG  WindowsBackend: keyboard_id=-268368887
02-16 20:49 DEBUG  WindowsBackend: keyboard_layout=us
02-16 20:49 DEBUG  WindowsBackend: keyboard_variant=
02-16 20:49 DEBUG  WindowsBackend: total_memory_mb=4095.99999905
02-16 20:49 DEBUG  CommonBackend: Searching ISOs on USB devices
02-16 20:49 DEBUG  CommonBackend: Searching for local CDs
02-16 20:49 DEBUG  Distro:   checking whether C:\Users\Benji\AppData\Local\Temp\pyl46CF.tmp is a valid Ubuntu CD
02-16 20:49 DEBUG  Distro:     does not contain C:\Users\Benji\AppData\Local\Temp\pyl46CF.tmp\casper\filesystem.squashfs
02-16 20:49 DEBUG  Distro:   checking whether C:\Users\Benji\AppData\Local\Temp\pyl46CF.tmp is a valid Ubuntu CD
02-16 20:49 DEBUG  Distro:     does not contain C:\Users\Benji\AppData\Local\Temp\pyl46CF.tmp\casper\filesystem.squashfs
02-16 20:49 DEBUG  Distro:   checking whether C:\Users\Benji\AppData\Local\Temp\pyl46CF.tmp is a valid Kubuntu CD
02-16 20:49 DEBUG  Distro:     does not contain C:\Users\Benji\AppData\Local\Temp\pyl46CF.tmp\casper\filesystem.squashfs
02-16 20:49 DEBUG  Distro:   checking whether C:\Users\Benji\AppData\Local\Temp\pyl46CF.tmp is a valid Kubuntu CD
02-16 20:49 DEBUG  Distro:     does not contain C:\Users\Benji\AppData\Local\Temp\pyl46CF.tmp\casper\filesystem.squashfs
02-16 20:49 DEBUG  Distro:   checking whether C:\Users\Benji\AppData\Local\Temp\pyl46CF.tmp is a valid Xubuntu CD
02-16 20:49 DEBUG  Distro:     does not contain C:\Users\Benji\AppData\Local\Temp\pyl46CF.tmp\casper\filesystem.squashfs
02-16 20:49 DEBUG  Distro:   checking whether C:\Users\Benji\AppData\Local\Temp\pyl46CF.tmp is a valid Xubuntu CD
02-16 20:49 DEBUG  Distro:     does not contain C:\Users\Benji\AppData\Local\Temp\pyl46CF.tmp\casper\filesystem.squashfs
02-16 20:49 DEBUG  Distro:   checking whether C:\Users\Benji\AppData\Local\Temp\pyl46CF.tmp is a valid Mythbuntu CD
02-16 20:49 DEBUG  Distro:     does not contain C:\Users\Benji\AppData\Local\Temp\pyl46CF.tmp\casper\filesystem.squashfs
02-16 20:49 DEBUG  Distro:   checking whether C:\Users\Benji\AppData\Local\Temp\pyl46CF.tmp is a valid Mythbuntu CD
02-16 20:49 DEBUG  Distro:     does not contain C:\Users\Benji\AppData\Local\Temp\pyl46CF.tmp\casper\filesystem.squashfs
02-16 20:49 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
02-16 20:49 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-16 20:49 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
02-16 20:49 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-16 20:49 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
02-16 20:49 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-16 20:49 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
02-16 20:49 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-16 20:49 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
02-16 20:49 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-16 20:49 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
02-16 20:49 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-16 20:49 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
02-16 20:49 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-16 20:49 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
02-16 20:49 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-16 20:49 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
02-16 20:49 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
02-16 20:49 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
02-16 20:49 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
02-16 20:49 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
02-16 20:49 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
02-16 20:49 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
02-16 20:49 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
02-16 20:49 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
02-16 20:49 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
02-16 20:49 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
02-16 20:49 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
02-16 20:49 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
02-16 20:49 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
02-16 20:49 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
02-16 20:49 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
02-16 20:49 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu CD
02-16 20:49 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
02-16 20:49 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu CD
02-16 20:49 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
02-16 20:49 DEBUG  Distro:   checking whether Q:\ is a valid Kubuntu CD
02-16 20:49 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
02-16 20:49 DEBUG  Distro:   checking whether Q:\ is a valid Kubuntu CD
02-16 20:49 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
02-16 20:49 DEBUG  Distro:   checking whether Q:\ is a valid Xubuntu CD
02-16 20:49 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
02-16 20:49 DEBUG  Distro:   checking whether Q:\ is a valid Xubuntu CD
02-16 20:49 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
02-16 20:49 DEBUG  Distro:   checking whether Q:\ is a valid Mythbuntu CD
02-16 20:49 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
02-16 20:49 DEBUG  Distro:   checking whether Q:\ is a valid Mythbuntu CD
02-16 20:49 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
02-16 20:49 INFO   root: Running the installer...
02-16 20:49 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Benji\AppData\Local\Temp\pyl46CF.tmp\translations, languages=['en_US', 'en']
02-16 20:49 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Benji\AppData\Local\Temp\pyl46CF.tmp\translations, languages=['en_US', 'en']
02-16 20:50 DEBUG  WinuiInstallationPage: target_drive=C:, installation_size=30000MB, distro_name=Ubuntu, language=en_US, locale=en_US.UTF-8, username=benji
02-16 20:50 INFO   root: Received settings
02-16 20:50 DEBUG  CommonBackend: Searching for local CD
02-16 20:50 DEBUG  Distro:   checking whether C:\Users\Benji\AppData\Local\Temp\pyl46CF.tmp is a valid Ubuntu CD
02-16 20:50 DEBUG  Distro:     does not contain C:\Users\Benji\AppData\Local\Temp\pyl46CF.tmp\casper\filesystem.squashfs
02-16 20:50 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
02-16 20:50 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-16 20:50 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
02-16 20:50 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
02-16 20:50 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu CD
02-16 20:50 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
02-16 20:50 DEBUG  CommonBackend: Searching for local ISO
02-16 20:50 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Benji\AppData\Local\Temp\pyl46CF.tmp\translations, languages=['en_US', 'en']
02-16 20:50 DEBUG  TaskList: # Running tasklist...
02-16 20:50 DEBUG  TaskList: ## Running select_target_dir...
02-16 20:50 INFO   WindowsBackend: Installing into C:\ubuntu
02-16 20:50 DEBUG  TaskList: ## Finished select_target_dir
02-16 20:50 DEBUG  TaskList: ## Running create_dir_structure...
02-16 20:50 DEBUG  CommonBackend: Creating dir C:\ubuntu
02-16 20:50 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks
02-16 20:50 DEBUG  CommonBackend: Creating dir C:\ubuntu\install
02-16 20:50 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot
02-16 20:50 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot
02-16 20:50 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot\grub
02-16 20:50 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot\grub
02-16 20:50 DEBUG  TaskList: ## Finished create_dir_structure
02-16 20:50 DEBUG  TaskList: ## Running create_uninstaller...
02-16 20:50 DEBUG  WindowsBackend: Copying uninstaller C:\Users\Benji\Downloads\wubi.exe -> C:\ubuntu\uninstall-wubi.exe
02-16 20:50 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString C:\ubuntu\uninstall-wubi.exe
02-16 20:50 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir C:\ubuntu
02-16 20:50 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
02-16 20:50 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon C:\ubuntu\Ubuntu.ico
02-16 20:50 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 11.10-rev245
02-16 20:50 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
02-16 20:50 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com](http://www.ubuntu.com)
02-16 20:50 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
02-16 20:50 DEBUG  TaskList: ## Finished create_uninstaller
02-16 20:50 DEBUG  TaskList: ## Running create_preseed_diskimage...
02-16 20:50 DEBUG  TaskList: ## Finished create_preseed_diskimage
02-16 20:50 DEBUG  TaskList: ## Running get_diskimage...
02-16 20:50 DEBUG  TaskList: New task download
02-16 20:50 DEBUG  TaskList: ### Running download...
02-16 20:50 DEBUG  downloader: downloading [http://releases.ubuntu.com/11.10/ubuntu-11.10-wubi-amd64.tar.xz](http://releases.ubuntu.com/11.10/ubuntu-11.10-wubi-amd64.tar.xz) > C:\ubuntu\disks\ubuntu-11.10-wubi-amd64.tar.xz
02-16 20:50 DEBUG  downloader: Download start filename=C:\ubuntu\disks\ubuntu-11.10-wubi-amd64.tar.xz, url=http://releases.ubuntu.com/11.10/ubuntu-11.10-wubi-amd64.tar.xz, basename=ubuntu-11.10-wubi-amd64.tar.xz, length=507143012, text=None
02-16 21:20 DEBUG  downloader: download finished (read 302685117 bytes)
02-16 21:20 DEBUG  TaskList: ### Finished download
02-16 21:20 DEBUG  TaskList: ## Finished get_diskimage
02-16 21:20 DEBUG  TaskList: ## Running extract_diskimage...
02-16 21:20 ERROR  TaskList: Extraction failed with code: 2
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 448, in extract_diskimage
Exception: Extraction failed with code: 2
02-16 21:20 DEBUG  TaskList: # Cancelling tasklist
02-16 21:20 DEBUG  TaskList: # Finished tasklist
02-16 21:20 ERROR  root: Extraction failed with code: 2
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 58, in run
  File "\lib\wubi\application.py", line 132, in select_task
  File "\lib\wubi\application.py", line 158, in run_installer
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 448, in extract_diskimage
Exception: Extraction failed with code: 2
02-17 15:43 INFO   root: === wubi 11.10 rev245 ===
02-17 15:43 DEBUG  root: Logfile is c:\users\benji\appdata\local\temp\wubi-11.10-rev245.log
02-17 15:43 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\Users\\Benji\\Downloads\\wubi.exe"']
02-17 15:43 DEBUG  CommonBackend: data_dir=C:\Users\Benji\AppData\Local\Temp\pylD453.tmp\data
02-17 15:43 DEBUG  WindowsBackend: 7z=C:\Users\Benji\AppData\Local\Temp\pylD453.tmp\bin\7z.exe
02-17 15:43 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
02-17 15:43 DEBUG  CommonBackend: Fetching basic info...
02-17 15:43 DEBUG  CommonBackend: original_exe=C:\Users\Benji\Downloads\wubi.exe
02-17 15:43 DEBUG  CommonBackend: platform=win32
02-17 15:43 DEBUG  CommonBackend: osname=nt
02-17 15:43 DEBUG  CommonBackend: language=en_US
02-17 15:43 DEBUG  CommonBackend: encoding=cp1252
02-17 15:43 DEBUG  WindowsBackend: arch=amd64
02-17 15:43 DEBUG  CommonBackend: Parsing isolist=C:\Users\Benji\AppData\Local\Temp\pylD453.tmp\data\isolist.ini
02-17 15:43 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
02-17 15:43 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
02-17 15:43 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
02-17 15:43 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
02-17 15:43 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
02-17 15:43 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
02-17 15:43 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
02-17 15:43 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
02-17 15:43 DEBUG  WindowsBackend: Fetching host info...
02-17 15:43 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
02-17 15:43 DEBUG  WindowsBackend: windows version=vista
02-17 15:43 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium
02-17 15:43 DEBUG  WindowsBackend: windows_sp=None
02-17 15:43 DEBUG  WindowsBackend: windows_build=7601
02-17 15:43 DEBUG  WindowsBackend: gmt=-3
02-17 15:43 DEBUG  WindowsBackend: country=US
02-17 15:43 DEBUG  WindowsBackend: timezone=America/North_Dakota/Center
02-17 15:43 DEBUG  WindowsBackend: windows_username=Benji
02-17 15:43 DEBUG  WindowsBackend: user_full_name=Benji
02-17 15:43 DEBUG  WindowsBackend: user_directory=C:\Users\Benji
02-17 15:43 DEBUG  WindowsBackend: windows_language_code=1033
02-17 15:43 DEBUG  WindowsBackend: windows_language=English
02-17 15:43 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM) i7-2630QM CPU @ 2.00GHz
02-17 15:43 DEBUG  WindowsBackend: bootloader=vista
02-17 15:43 DEBUG  WindowsBackend: system_drive=Drive(C: hd 348700.070313 mb free ntfs)
02-17 15:43 DEBUG  WindowsBackend: drive=Drive(C: hd 348700.070313 mb free ntfs)
02-17 15:43 DEBUG  WindowsBackend: drive=Drive(D: hd 26417.21875 mb free ntfs)
02-17 15:43 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free )
02-17 15:43 DEBUG  WindowsBackend: drive=Drive(Q: hd 0.0 mb free )
02-17 15:43 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
02-17 15:43 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
02-17 15:43 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
02-17 15:43 DEBUG  WindowsBackend: keyboard_id=-268368887
02-17 15:43 DEBUG  WindowsBackend: keyboard_layout=us
02-17 15:43 DEBUG  WindowsBackend: keyboard_variant=
02-17 15:43 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
02-17 15:43 DEBUG  CommonBackend: locale=en_US.UTF-8
02-17 15:43 DEBUG  WindowsBackend: total_memory_mb=4095.99999905
02-17 15:43 DEBUG  CommonBackend: Searching ISOs on USB devices
02-17 15:43 DEBUG  CommonBackend: Searching for local CDs
02-17 15:43 DEBUG  Distro:   checking whether C:\Users\Benji\AppData\Local\Temp\pylD453.tmp is a valid Ubuntu CD
02-17 15:43 DEBUG  Distro:     does not contain C:\Users\Benji\AppData\Local\Temp\pylD453.tmp\casper\filesystem.squashfs
02-17 15:43 DEBUG  Distro:   checking whether C:\Users\Benji\AppData\Local\Temp\pylD453.tmp is a valid Ubuntu CD
02-17 15:43 DEBUG  Distro:     does not contain C:\Users\Benji\AppData\Local\Temp\pylD453.tmp\casper\filesystem.squashfs
02-17 15:43 DEBUG  Distro:   checking whether C:\Users\Benji\AppData\Local\Temp\pylD453.tmp is a valid Kubuntu CD
02-17 15:43 DEBUG  Distro:     does not contain C:\Users\Benji\AppData\Local\Temp\pylD453.tmp\casper\filesystem.squashfs
02-17 15:43 DEBUG  Distro:   checking whether C:\Users\Benji\AppData\Local\Temp\pylD453.tmp is a valid Kubuntu CD
02-17 15:43 DEBUG  Distro:     does not contain C:\Users\Benji\AppData\Local\Temp\pylD453.tmp\casper\filesystem.squashfs
02-17 15:43 DEBUG  Distro:   checking whether C:\Users\Benji\AppData\Local\Temp\pylD453.tmp is a valid Xubuntu CD
02-17 15:43 DEBUG  Distro:     does not contain C:\Users\Benji\AppData\Local\Temp\pylD453.tmp\casper\filesystem.squashfs
02-17 15:43 DEBUG  Distro:   checking whether C:\Users\Benji\AppData\Local\Temp\pylD453.tmp is a valid Xubuntu CD
02-17 15:43 DEBUG  Distro:     does not contain C:\Users\Benji\AppData\Local\Temp\pylD453.tmp\casper\filesystem.squashfs
02-17 15:43 DEBUG  Distro:   checking whether C:\Users\Benji\AppData\Local\Temp\pylD453.tmp is a valid Mythbuntu CD
02-17 15:43 DEBUG  Distro:     does not contain C:\Users\Benji\AppData\Local\Temp\pylD453.tmp\casper\filesystem.squashfs
02-17 15:43 DEBUG  Distro:   checking whether C:\Users\Benji\AppData\Local\Temp\pylD453.tmp is a valid Mythbuntu CD
02-17 15:43 DEBUG  Distro:     does not contain C:\Users\Benji\AppData\Local\Temp\pylD453.tmp\casper\filesystem.squashfs
02-17 15:43 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
02-17 15:43 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-17 15:43 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
02-17 15:43 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-17 15:43 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
02-17 15:43 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-17 15:43 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
02-17 15:43 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-17 15:43 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
02-17 15:43 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-17 15:43 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
02-17 15:43 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-17 15:43 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
02-17 15:43 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-17 15:43 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
02-17 15:43 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-17 15:43 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
02-17 15:43 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
02-17 15:43 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
02-17 15:43 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
02-17 15:43 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
02-17 15:43 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
02-17 15:43 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
02-17 15:43 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
02-17 15:43 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
02-17 15:43 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
02-17 15:43 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
02-17 15:43 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
02-17 15:43 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
02-17 15:43 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
02-17 15:43 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
02-17 15:43 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
02-17 15:43 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu CD
02-17 15:43 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
02-17 15:43 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu CD
02-17 15:43 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
02-17 15:43 DEBUG  Distro:   checking whether Q:\ is a valid Kubuntu CD
02-17 15:43 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
02-17 15:43 DEBUG  Distro:   checking whether Q:\ is a valid Kubuntu CD
02-17 15:43 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
02-17 15:43 DEBUG  Distro:   checking whether Q:\ is a valid Xubuntu CD
02-17 15:43 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
02-17 15:43 DEBUG  Distro:   checking whether Q:\ is a valid Xubuntu CD
02-17 15:43 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
02-17 15:43 DEBUG  Distro:   checking whether Q:\ is a valid Mythbuntu CD
02-17 15:43 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
02-17 15:43 DEBUG  Distro:   checking whether Q:\ is a valid Mythbuntu CD
02-17 15:43 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
02-17 15:43 INFO   root: Already installed, running the uninstaller...
02-17 15:43 INFO   root: Running the uninstaller...
02-17 15:43 INFO   CommonBackend: This is the uninstaller running
02-17 15:43 DEBUG  WindowsFrontend: __init__...
02-17 15:43 DEBUG  WindowsFrontend: on_init...
02-17 15:43 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Benji\AppData\Local\Temp\pylD453.tmp\translations, languages=['en_US', 'en']
02-17 15:43 INFO   root: Received settings
02-17 15:43 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Benji\AppData\Local\Temp\pylD453.tmp\translations, languages=['en_US', 'en']
02-17 15:43 DEBUG  TaskList: # Running tasklist...
02-17 15:43 DEBUG  TaskList: ## Running Remove bootloader entry...
02-17 15:43 DEBUG  WindowsBackend: Could not find bcd id
02-17 15:43 DEBUG  WindowsBackend: undo_bootini C:
02-17 15:43 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 348700.070313 mb free ntfs)
02-17 15:43 DEBUG  WindowsBackend: undo_bootini D:
02-17 15:43 DEBUG  WindowsBackend: undo_configsys Drive(D: hd 26417.21875 mb free ntfs)
02-17 15:43 DEBUG  WindowsBackend: undo_bootini Q:
02-17 15:43 DEBUG  WindowsBackend: undo_configsys Drive(Q: hd 0.0 mb free )
02-17 15:43 DEBUG  TaskList: ## Finished Remove bootloader entry
02-17 15:43 DEBUG  TaskList: ## Running Remove target dir...
02-17 15:43 DEBUG  CommonBackend: Deleting C:\ubuntu
02-17 15:43 DEBUG  TaskList: ## Finished Remove target dir
02-17 15:43 DEBUG  TaskList: ## Running Remove registry key...
02-17 15:43 DEBUG  TaskList: ## Finished Remove registry key
02-17 15:43 DEBUG  TaskList: # Finished tasklist
02-17 15:43 INFO   root: Almost finished uninstalling
02-17 15:43 INFO   root: Finished uninstallation
02-17 15:43 DEBUG  CommonBackend: Fetching basic info...
02-17 15:43 DEBUG  CommonBackend: original_exe=C:\Users\Benji\Downloads\wubi.exe
02-17 15:43 DEBUG  CommonBackend: platform=win32
02-17 15:43 DEBUG  CommonBackend: osname=nt
02-17 15:43 DEBUG  WindowsBackend: arch=amd64
02-17 15:43 DEBUG  CommonBackend: Parsing isolist=C:\Users\Benji\AppData\Local\Temp\pylD453.tmp\data\isolist.ini
02-17 15:43 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
02-17 15:43 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
02-17 15:43 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
02-17 15:43 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
02-17 15:43 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
02-17 15:43 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
02-17 15:43 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
02-17 15:43 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
02-17 15:43 DEBUG  WindowsBackend: Fetching host info...
02-17 15:43 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
02-17 15:43 DEBUG  WindowsBackend: windows version=vista
02-17 15:43 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium
02-17 15:43 DEBUG  WindowsBackend: windows_sp=None
02-17 15:43 DEBUG  WindowsBackend: windows_build=7601
02-17 15:43 DEBUG  WindowsBackend: gmt=-3
02-17 15:43 DEBUG  WindowsBackend: country=US
02-17 15:43 DEBUG  WindowsBackend: timezone=America/North_Dakota/Center
02-17 15:43 DEBUG  WindowsBackend: windows_username=Benji
02-17 15:43 DEBUG  WindowsBackend: user_full_name=Benji
02-17 15:43 DEBUG  WindowsBackend: user_directory=C:\Users\Benji
02-17 15:43 DEBUG  WindowsBackend: windows_language_code=1033
02-17 15:43 DEBUG  WindowsBackend: windows_language=English
02-17 15:43 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM) i7-2630QM CPU @ 2.00GHz
02-17 15:43 DEBUG  WindowsBackend: bootloader=vista
02-17 15:43 DEBUG  WindowsBackend: system_drive=Drive(C: hd 350312.179688 mb free ntfs)
02-17 15:43 DEBUG  WindowsBackend: drive=Drive(C: hd 350312.179688 mb free ntfs)
02-17 15:43 DEBUG  WindowsBackend: drive=Drive(D: hd 26417.21875 mb free ntfs)
02-17 15:43 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free )
02-17 15:43 DEBUG  WindowsBackend: drive=Drive(Q: hd 0.0 mb free )
02-17 15:43 DEBUG  WindowsBackend: uninstaller_path=None
02-17 15:43 DEBUG  WindowsBackend: previous_target_dir=None
02-17 15:43 DEBUG  WindowsBackend: previous_distro_name=None
02-17 15:43 DEBUG  WindowsBackend: keyboard_id=-268368887
02-17 15:43 DEBUG  WindowsBackend: keyboard_layout=us
02-17 15:43 DEBUG  WindowsBackend: keyboard_variant=
02-17 15:43 DEBUG  WindowsBackend: total_memory_mb=4095.99999905
02-17 15:43 DEBUG  CommonBackend: Searching ISOs on USB devices
02-17 15:43 DEBUG  CommonBackend: Searching for local CDs
02-17 15:43 DEBUG  Distro:   checking whether C:\Users\Benji\AppData\Local\Temp\pylD453.tmp is a valid Ubuntu CD
02-17 15:43 DEBUG  Distro:     does not contain C:\Users\Benji\AppData\Local\Temp\pylD453.tmp\casper\filesystem.squashfs
02-17 15:43 DEBUG  Distro:   checking whether C:\Users\Benji\AppData\Local\Temp\pylD453.tmp is a valid Ubuntu CD
02-17 15:43 DEBUG  Distro:     does not contain C:\Users\Benji\AppData\Local\Temp\pylD453.tmp\casper\filesystem.squashfs
02-17 15:43 DEBUG  Distro:   checking whether C:\Users\Benji\AppData\Local\Temp\pylD453.tmp is a valid Kubuntu CD
02-17 15:43 DEBUG  Distro:     does not contain C:\Users\Benji\AppData\Local\Temp\pylD453.tmp\casper\filesystem.squashfs
02-17 15:43 DEBUG  Distro:   checking whether C:\Users\Benji\AppData\Local\Temp\pylD453.tmp is a valid Kubuntu CD
02-17 15:43 DEBUG  Distro:     does not contain C:\Users\Benji\AppData\Local\Temp\pylD453.tmp\casper\filesystem.squashfs
02-17 15:43 DEBUG  Distro:   checking whether C:\Users\Benji\AppData\Local\Temp\pylD453.tmp is a valid Xubuntu CD
02-17 15:43 DEBUG  Distro:     does not contain C:\Users\Benji\AppData\Local\Temp\pylD453.tmp\casper\filesystem.squashfs
02-17 15:43 DEBUG  Distro:   checking whether C:\Users\Benji\AppData\Local\Temp\pylD453.tmp is a valid Xubuntu CD
02-17 15:43 DEBUG  Distro:     does not contain C:\Users\Benji\AppData\Local\Temp\pylD453.tmp\casper\filesystem.squashfs
02-17 15:43 DEBUG  Distro:   checking whether C:\Users\Benji\AppData\Local\Temp\pylD453.tmp is a valid Mythbuntu CD
02-17 15:43 DEBUG  Distro:     does not contain C:\Users\Benji\AppData\Local\Temp\pylD453.tmp\casper\filesystem.squashfs
02-17 15:43 DEBUG  Distro:   checking whether C:\Users\Benji\AppData\Local\Temp\pylD453.tmp is a valid Mythbuntu CD
02-17 15:43 DEBUG  Distro:     does not contain C:\Users\Benji\AppData\Local\Temp\pylD453.tmp\casper\filesystem.squashfs
02-17 15:43 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
02-17 15:43 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-17 15:43 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
02-17 15:43 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-17 15:43 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
02-17 15:43 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-17 15:43 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
02-17 15:43 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-17 15:43 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
02-17 15:43 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-17 15:43 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
02-17 15:43 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-17 15:43 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
02-17 15:43 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-17 15:43 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
02-17 15:43 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-17 15:43 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
02-17 15:43 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
02-17 15:43 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
02-17 15:43 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
02-17 15:43 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
02-17 15:43 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
02-17 15:43 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
02-17 15:43 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
02-17 15:43 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
02-17 15:43 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
02-17 15:43 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
02-17 15:43 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
02-17 15:43 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
02-17 15:43 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
02-17 15:43 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
02-17 15:43 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
02-17 15:43 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu CD
02-17 15:43 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
02-17 15:43 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu CD
02-17 15:43 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
02-17 15:43 DEBUG  Distro:   checking whether Q:\ is a valid Kubuntu CD
02-17 15:43 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
02-17 15:43 DEBUG  Distro:   checking whether Q:\ is a valid Kubuntu CD
02-17 15:43 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
02-17 15:43 DEBUG  Distro:   checking whether Q:\ is a valid Xubuntu CD
02-17 15:43 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
02-17 15:43 DEBUG  Distro:   checking whether Q:\ is a valid Xubuntu CD
02-17 15:43 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
02-17 15:43 DEBUG  Distro:   checking whether Q:\ is a valid Mythbuntu CD
02-17 15:43 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
02-17 15:43 DEBUG  Distro:   checking whether Q:\ is a valid Mythbuntu CD
02-17 15:43 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
02-17 15:43 INFO   root: Running the installer...
02-17 15:43 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Benji\AppData\Local\Temp\pylD453.tmp\translations, languages=['en_US', 'en']
02-17 15:43 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Benji\AppData\Local\Temp\pylD453.tmp\translations, languages=['en_US', 'en']
02-17 15:44 DEBUG  WinuiInstallationPage: target_drive=C:, installation_size=30000MB, distro_name=Ubuntu, language=en_US, locale=en_US.UTF-8, username=benji
02-17 15:44 INFO   root: Received settings
02-17 15:44 DEBUG  CommonBackend: Searching for local CD
02-17 15:44 DEBUG  Distro:   checking whether C:\Users\Benji\AppData\Local\Temp\pylD453.tmp is a valid Ubuntu CD
02-17 15:44 DEBUG  Distro:     does not contain C:\Users\Benji\AppData\Local\Temp\pylD453.tmp\casper\filesystem.squashfs
02-17 15:44 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
02-17 15:44 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-17 15:44 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
02-17 15:44 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
02-17 15:44 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu CD
02-17 15:44 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
02-17 15:44 DEBUG  CommonBackend: Searching for local ISO
02-17 15:44 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Benji\AppData\Local\Temp\pylD453.tmp\translations, languages=['en_US', 'en']
02-17 15:44 DEBUG  TaskList: # Running tasklist...
02-17 15:44 DEBUG  TaskList: ## Running select_target_dir...
02-17 15:44 INFO   WindowsBackend: Installing into C:\ubuntu
02-17 15:44 DEBUG  TaskList: ## Finished select_target_dir
02-17 15:44 DEBUG  TaskList: ## Running create_dir_structure...
02-17 15:44 DEBUG  CommonBackend: Creating dir C:\ubuntu
02-17 15:44 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks
02-17 15:44 DEBUG  CommonBackend: Creating dir C:\ubuntu\install
02-17 15:44 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot
02-17 15:44 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot
02-17 15:44 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot\grub
02-17 15:44 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot\grub
02-17 15:44 DEBUG  TaskList: ## Finished create_dir_structure
02-17 15:44 DEBUG  TaskList: ## Running create_uninstaller...
02-17 15:44 DEBUG  WindowsBackend: Copying uninstaller C:\Users\Benji\Downloads\wubi.exe -> C:\ubuntu\uninstall-wubi.exe
02-17 15:44 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString C:\ubuntu\uninstall-wubi.exe
02-17 15:44 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir C:\ubuntu
02-17 15:44 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
02-17 15:44 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon C:\ubuntu\Ubuntu.ico
02-17 15:44 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 11.10-rev245
02-17 15:44 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
02-17 15:44 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com](http://www.ubuntu.com)
02-17 15:44 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
02-17 15:44 DEBUG  TaskList: ## Finished create_uninstaller
02-17 15:44 DEBUG  TaskList: ## Running create_preseed_diskimage...
02-17 15:44 DEBUG  TaskList: ## Finished create_preseed_diskimage
02-17 15:44 DEBUG  TaskList: ## Running get_diskimage...
02-17 15:44 DEBUG  TaskList: New task download
02-17 15:44 DEBUG  TaskList: ### Running download...
02-17 15:44 DEBUG  downloader: downloading [http://releases.ubuntu.com/11.10/ubuntu-11.10-wubi-amd64.tar.xz](http://releases.ubuntu.com/11.10/ubuntu-11.10-wubi-amd64.tar.xz) > C:\ubuntu\disks\ubuntu-11.10-wubi-amd64.tar.xz
02-17 15:44 DEBUG  downloader: Download start filename=C:\ubuntu\disks\ubuntu-11.10-wubi-amd64.tar.xz, url=http://releases.ubuntu.com/11.10/ubuntu-11.10-wubi-amd64.tar.xz, basename=ubuntu-11.10-wubi-amd64.tar.xz, length=507143012, text=None
02-17 18:23 DEBUG  TaskList: ### Finished download
02-17 18:23 DEBUG  downloader: download finished (read 507143012 bytes)
02-17 18:23 DEBUG  TaskList: ## Finished get_diskimage
02-17 18:23 DEBUG  TaskList: ## Running extract_diskimage...
02-17 18:24 DEBUG  TaskList: ## Finished extract_diskimage
02-17 18:24 DEBUG  TaskList: ## Running choose_disk_sizes...
02-17 18:24 DEBUG  WindowsBackend: total size=30000
  root=29744
  swap=256
  home=0
  usr=0
02-17 18:24 DEBUG  TaskList: ## Finished choose_disk_sizes
02-17 18:24 DEBUG  TaskList: ## Running expand_diskimage...
02-17 18:25 DEBUG  TaskList: ## Finished expand_diskimage
02-17 18:25 DEBUG  TaskList: ## Running create_swap_diskimage...
02-17 18:25 DEBUG  TaskList: ## Finished create_swap_diskimage
02-17 18:25 DEBUG  TaskList: ## Running modify_bootloader...
02-17 18:25 DEBUG  TaskList: New task modify_bcd
02-17 18:25 DEBUG  TaskList: ### Running modify_bcd...
02-17 18:25 DEBUG  WindowsBackend: modify_bcd Drive(C: hd 350312.179688 mb free ntfs)
02-17 18:25 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi VistaBootDrive {8a82e3dd-f4e9-11e0-9887-b870f446aa9c}
02-17 18:25 DEBUG  TaskList: ### Finished modify_bcd
02-17 18:25 DEBUG  TaskList: New task modify_bcd
02-17 18:25 DEBUG  TaskList: ### Running modify_bcd...
02-17 18:25 DEBUG  WindowsBackend: modify_bcd Drive(D: hd 26417.21875 mb free ntfs)
02-17 18:25 DEBUG  WindowsBackend: BCD has already been modified
02-17 18:25 DEBUG  TaskList: ### Finished modify_bcd
02-17 18:25 DEBUG  TaskList: New task modify_bcd
02-17 18:25 DEBUG  TaskList: ### Running modify_bcd...
02-17 18:25 DEBUG  WindowsBackend: modify_bcd Drive(Q: hd 0.0 mb free )
02-17 18:25 DEBUG  WindowsBackend: BCD has already been modified
02-17 18:25 DEBUG  TaskList: ### Finished modify_bcd
02-17 18:25 DEBUG  TaskList: ## Finished modify_bootloader
02-17 18:25 DEBUG  TaskList: ## Running diskimage_bootloader...
02-17 18:25 DEBUG  WindowsBackend: Copying C:\Users\Benji\AppData\Local\Temp\pylD453.tmp\winboot -> C:\ubuntu\winboot
02-17 18:25 ERROR  TaskList: [Errno 13] Permission denied: 'Q:\\wubildr'
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 483, in diskimage_bootloader
  File "\lib\shutil.py", line 39, in copyfile
IOError: [Errno 13] Permission denied: 'Q:\\wubildr'
02-17 18:25 DEBUG  TaskList: # Cancelling tasklist
02-17 18:25 DEBUG  TaskList: # Finished tasklist
02-17 18:25 ERROR  root: [Errno 13] Permission denied: 'Q:\\wubildr'
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 58, in run
  File "\lib\wubi\application.py", line 132, in select_task
  File "\lib\wubi\application.py", line 158, in run_installer
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 483, in diskimage_bootloader
  File "\lib\shutil.py", line 39, in copyfile
IOError: [Errno 13] Permission denied: 'Q:\\wubildr'
02-17 18:40 INFO   root: === wubi 11.10 rev245 ===
02-17 18:40 DEBUG  root: Logfile is c:\users\benji\appdata\local\temp\wubi-11.10-rev245.log
02-17 18:40 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\Users\\Benji\\Downloads\\wubi.exe"']
02-17 18:40 DEBUG  CommonBackend: data_dir=C:\Users\Benji\AppData\Local\Temp\pylEAE2.tmp\data
02-17 18:40 DEBUG  WindowsBackend: 7z=C:\Users\Benji\AppData\Local\Temp\pylEAE2.tmp\bin\7z.exe
02-17 18:40 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
02-17 18:40 DEBUG  CommonBackend: Fetching basic info...
02-17 18:40 DEBUG  CommonBackend: original_exe=C:\Users\Benji\Downloads\wubi.exe
02-17 18:40 DEBUG  CommonBackend: platform=win32
02-17 18:40 DEBUG  CommonBackend: osname=nt
02-17 18:40 DEBUG  CommonBackend: language=en_US
02-17 18:40 DEBUG  CommonBackend: encoding=cp1252
02-17 18:40 DEBUG  WindowsBackend: arch=amd64
02-17 18:40 DEBUG  CommonBackend: Parsing isolist=C:\Users\Benji\AppData\Local\Temp\pylEAE2.tmp\data\isolist.ini
02-17 18:40 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
02-17 18:40 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
02-17 18:40 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
02-17 18:40 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
02-17 18:40 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
02-17 18:40 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
02-17 18:40 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
02-17 18:40 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
02-17 18:40 DEBUG  WindowsBackend: Fetching host info...
02-17 18:40 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
02-17 18:40 DEBUG  WindowsBackend: windows version=vista
02-17 18:40 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium
02-17 18:40 DEBUG  WindowsBackend: windows_sp=None
02-17 18:40 DEBUG  WindowsBackend: windows_build=7601
02-17 18:40 DEBUG  WindowsBackend: gmt=-3
02-17 18:40 DEBUG  WindowsBackend: country=US
02-17 18:40 DEBUG  WindowsBackend: timezone=America/North_Dakota/Center
02-17 18:40 DEBUG  WindowsBackend: windows_username=Benji
02-17 18:40 DEBUG  WindowsBackend: user_full_name=Benji
02-17 18:40 DEBUG  WindowsBackend: user_directory=C:\Users\Benji
02-17 18:40 DEBUG  WindowsBackend: windows_language_code=1033
02-17 18:40 DEBUG  WindowsBackend: windows_language=English
02-17 18:40 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM) i7-2630QM CPU @ 2.00GHz
02-17 18:40 DEBUG  WindowsBackend: bootloader=vista
02-17 18:40 DEBUG  WindowsBackend: system_drive=Drive(C: hd 346203.742188 mb free ntfs)
02-17 18:40 DEBUG  WindowsBackend: drive=Drive(C: hd 346203.742188 mb free ntfs)
02-17 18:40 DEBUG  WindowsBackend: drive=Drive(D: hd 26417.0898438 mb free ntfs)
02-17 18:40 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free )
02-17 18:40 DEBUG  WindowsBackend: drive=Drive(Q: hd 0.0 mb free )
02-17 18:40 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
02-17 18:40 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
02-17 18:40 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
02-17 18:40 DEBUG  WindowsBackend: keyboard_id=-268368887
02-17 18:40 DEBUG  WindowsBackend: keyboard_layout=us
02-17 18:40 DEBUG  WindowsBackend: keyboard_variant=
02-17 18:40 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
02-17 18:40 DEBUG  CommonBackend: locale=en_US.UTF-8
02-17 18:40 DEBUG  WindowsBackend: total_memory_mb=4095.99999905
02-17 18:40 DEBUG  CommonBackend: Searching ISOs on USB devices
02-17 18:40 DEBUG  CommonBackend: Searching for local CDs
02-17 18:40 DEBUG  Distro:   checking whether C:\Users\Benji\AppData\Local\Temp\pylEAE2.tmp is a valid Ubuntu CD
02-17 18:40 DEBUG  Distro:     does not contain C:\Users\Benji\AppData\Local\Temp\pylEAE2.tmp\casper\filesystem.squashfs
02-17 18:40 DEBUG  Distro:   checking whether C:\Users\Benji\AppData\Local\Temp\pylEAE2.tmp is a valid Ubuntu CD
02-17 18:40 DEBUG  Distro:     does not contain C:\Users\Benji\AppData\Local\Temp\pylEAE2.tmp\casper\filesystem.squashfs
02-17 18:40 DEBUG  Distro:   checking whether C:\Users\Benji\AppData\Local\Temp\pylEAE2.tmp is a valid Kubuntu CD
02-17 18:40 DEBUG  Distro:     does not contain C:\Users\Benji\AppData\Local\Temp\pylEAE2.tmp\casper\filesystem.squashfs
02-17 18:40 DEBUG  Distro:   checking whether C:\Users\Benji\AppData\Local\Temp\pylEAE2.tmp is a valid Kubuntu CD
02-17 18:40 DEBUG  Distro:     does not contain C:\Users\Benji\AppData\Local\Temp\pylEAE2.tmp\casper\filesystem.squashfs
02-17 18:40 DEBUG  Distro:   checking whether C:\Users\Benji\AppData\Local\Temp\pylEAE2.tmp is a valid Xubuntu CD
02-17 18:40 DEBUG  Distro:     does not contain C:\Users\Benji\AppData\Local\Temp\pylEAE2.tmp\casper\filesystem.squashfs
02-17 18:40 DEBUG  Distro:   checking whether C:\Users\Benji\AppData\Local\Temp\pylEAE2.tmp is a valid Xubuntu CD
02-17 18:40 DEBUG  Distro:     does not contain C:\Users\Benji\AppData\Local\Temp\pylEAE2.tmp\casper\filesystem.squashfs
02-17 18:40 DEBUG  Distro:   checking whether C:\Users\Benji\AppData\Local\Temp\pylEAE2.tmp is a valid Mythbuntu CD
02-17 18:40 DEBUG  Distro:     does not contain C:\Users\Benji\AppData\Local\Temp\pylEAE2.tmp\casper\filesystem.squashfs
02-17 18:40 DEBUG  Distro:   checking whether C:\Users\Benji\AppData\Local\Temp\pylEAE2.tmp is a valid Mythbuntu CD
02-17 18:40 DEBUG  Distro:     does not contain C:\Users\Benji\AppData\Local\Temp\pylEAE2.tmp\casper\filesystem.squashfs
02-17 18:40 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
02-17 18:40 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-17 18:40 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
02-17 18:40 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-17 18:40 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
02-17 18:40 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-17 18:40 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
02-17 18:40 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-17 18:40 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
02-17 18:40 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-17 18:40 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
02-17 18:40 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-17 18:40 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
02-17 18:40 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-17 18:40 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
02-17 18:40 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-17 18:40 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
02-17 18:40 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
02-17 18:40 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
02-17 18:40 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
02-17 18:40 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
02-17 18:40 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
02-17 18:40 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
02-17 18:40 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
02-17 18:40 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
02-17 18:40 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
02-17 18:40 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
02-17 18:40 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
02-17 18:40 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
02-17 18:40 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
02-17 18:40 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
02-17 18:40 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
02-17 18:40 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu CD
02-17 18:40 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
02-17 18:40 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu CD
02-17 18:40 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
02-17 18:40 DEBUG  Distro:   checking whether Q:\ is a valid Kubuntu CD
02-17 18:40 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
02-17 18:40 DEBUG  Distro:   checking whether Q:\ is a valid Kubuntu CD
02-17 18:40 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
02-17 18:40 DEBUG  Distro:   checking whether Q:\ is a valid Xubuntu CD
02-17 18:40 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
02-17 18:40 DEBUG  Distro:   checking whether Q:\ is a valid Xubuntu CD
02-17 18:40 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
02-17 18:40 DEBUG  Distro:   checking whether Q:\ is a valid Mythbuntu CD
02-17 18:40 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
02-17 18:40 DEBUG  Distro:   checking whether Q:\ is a valid Mythbuntu CD
02-17 18:40 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
02-17 18:40 INFO   root: Already installed, running the uninstaller...
02-17 18:40 INFO   root: Running the uninstaller...
02-17 18:40 INFO   CommonBackend: This is the uninstaller running
02-17 18:40 DEBUG  WindowsFrontend: __init__...
02-17 18:40 DEBUG  WindowsFrontend: on_init...
02-17 18:40 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Benji\AppData\Local\Temp\pylEAE2.tmp\translations, languages=['en_US', 'en']
02-17 18:40 INFO   root: Received settings
02-17 18:40 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Benji\AppData\Local\Temp\pylEAE2.tmp\translations, languages=['en_US', 'en']
02-17 18:40 DEBUG  TaskList: # Running tasklist...
02-17 18:40 DEBUG  TaskList: ## Running Remove bootloader entry...
02-17 18:40 DEBUG  WindowsBackend: Removing bcd entry {8a82e3dd-f4e9-11e0-9887-b870f446aa9c}
02-17 18:40 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi VistaBootDrive 
02-17 18:40 DEBUG  WindowsBackend: undo_bootini C:
02-17 18:40 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 346203.742188 mb free ntfs)
02-17 18:40 DEBUG  WindowsBackend: undo_bootini D:
02-17 18:40 DEBUG  WindowsBackend: undo_configsys Drive(D: hd 26417.0898438 mb free ntfs)
02-17 18:40 DEBUG  WindowsBackend: undo_bootini Q:
02-17 18:40 DEBUG  WindowsBackend: undo_configsys Drive(Q: hd 0.0 mb free )
02-17 18:40 DEBUG  TaskList: ## Finished Remove bootloader entry
02-17 18:40 DEBUG  TaskList: ## Running Remove target dir...
02-17 18:40 DEBUG  CommonBackend: Deleting C:\ubuntu
02-17 18:40 DEBUG  TaskList: ## Finished Remove target dir
02-17 18:40 DEBUG  TaskList: ## Running Remove registry key...
02-17 18:40 DEBUG  TaskList: ## Finished Remove registry key
02-17 18:40 DEBUG  TaskList: # Finished tasklist
02-17 18:40 INFO   root: Almost finished uninstalling
02-17 18:40 INFO   root: Finished uninstallation
02-17 18:40 DEBUG  CommonBackend: Fetching basic info...
02-17 18:40 DEBUG  CommonBackend: original_exe=C:\Users\Benji\Downloads\wubi.exe
02-17 18:40 DEBUG  CommonBackend: platform=win32
02-17 18:40 DEBUG  CommonBackend: osname=nt
02-17 18:40 DEBUG  WindowsBackend: arch=amd64
02-17 18:40 DEBUG  CommonBackend: Parsing isolist=C:\Users\Benji\AppData\Local\Temp\pylEAE2.tmp\data\isolist.ini
02-17 18:40 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
02-17 18:40 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
02-17 18:40 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
02-17 18:40 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
02-17 18:40 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
02-17 18:40 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
02-17 18:40 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
02-17 18:40 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
02-17 18:40 DEBUG  WindowsBackend: Fetching host info...
02-17 18:40 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
02-17 18:40 DEBUG  WindowsBackend: windows version=vista
02-17 18:40 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium
02-17 18:40 DEBUG  WindowsBackend: windows_sp=None
02-17 18:40 DEBUG  WindowsBackend: windows_build=7601
02-17 18:40 DEBUG  WindowsBackend: gmt=-3
02-17 18:40 DEBUG  WindowsBackend: country=US
02-17 18:40 DEBUG  WindowsBackend: timezone=America/North_Dakota/Center
02-17 18:40 DEBUG  WindowsBackend: windows_username=Benji
02-17 18:40 DEBUG  WindowsBackend: user_full_name=Benji
02-17 18:40 DEBUG  WindowsBackend: user_directory=C:\Users\Benji
02-17 18:40 DEBUG  WindowsBackend: windows_language_code=1033
02-17 18:40 DEBUG  WindowsBackend: windows_language=English
02-17 18:40 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM) i7-2630QM CPU @ 2.00GHz
02-17 18:40 DEBUG  WindowsBackend: bootloader=vista
02-17 18:40 DEBUG  WindowsBackend: system_drive=Drive(C: hd 349759.34375 mb free ntfs)
02-17 18:40 DEBUG  WindowsBackend: drive=Drive(C: hd 349759.34375 mb free ntfs)
02-17 18:40 DEBUG  WindowsBackend: drive=Drive(D: hd 26417.21875 mb free ntfs)
02-17 18:40 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free )
02-17 18:40 DEBUG  WindowsBackend: drive=Drive(Q: hd 0.0 mb free )
02-17 18:40 DEBUG  WindowsBackend: uninstaller_path=None
02-17 18:40 DEBUG  WindowsBackend: previous_target_dir=None
02-17 18:40 DEBUG  WindowsBackend: previous_distro_name=None
02-17 18:40 DEBUG  WindowsBackend: keyboard_id=-268368887
02-17 18:40 DEBUG  WindowsBackend: keyboard_layout=us
02-17 18:40 DEBUG  WindowsBackend: keyboard_variant=
02-17 18:40 DEBUG  WindowsBackend: total_memory_mb=4095.99999905
02-17 18:40 DEBUG  CommonBackend: Searching ISOs on USB devices
02-17 18:40 DEBUG  CommonBackend: Searching for local CDs
02-17 18:40 DEBUG  Distro:   checking whether C:\Users\Benji\AppData\Local\Temp\pylEAE2.tmp is a valid Ubuntu CD
02-17 18:40 DEBUG  Distro:     does not contain C:\Users\Benji\AppData\Local\Temp\pylEAE2.tmp\casper\filesystem.squashfs
02-17 18:40 DEBUG  Distro:   checking whether C:\Users\Benji\AppData\Local\Temp\pylEAE2.tmp is a valid Ubuntu CD
02-17 18:40 DEBUG  Distro:     does not contain C:\Users\Benji\AppData\Local\Temp\pylEAE2.tmp\casper\filesystem.squashfs
02-17 18:40 DEBUG  Distro:   checking whether C:\Users\Benji\AppData\Local\Temp\pylEAE2.tmp is a valid Kubuntu CD
02-17 18:40 DEBUG  Distro:     does not contain C:\Users\Benji\AppData\Local\Temp\pylEAE2.tmp\casper\filesystem.squashfs
02-17 18:40 DEBUG  Distro:   checking whether C:\Users\Benji\AppData\Local\Temp\pylEAE2.tmp is a valid Kubuntu CD
02-17 18:40 DEBUG  Distro:     does not contain C:\Users\Benji\AppData\Local\Temp\pylEAE2.tmp\casper\filesystem.squashfs
02-17 18:40 DEBUG  Distro:   checking whether C:\Users\Benji\AppData\Local\Temp\pylEAE2.tmp is a valid Xubuntu CD
02-17 18:40 DEBUG  Distro:     does not contain C:\Users\Benji\AppData\Local\Temp\pylEAE2.tmp\casper\filesystem.squashfs
02-17 18:40 DEBUG  Distro:   checking whether C:\Users\Benji\AppData\Local\Temp\pylEAE2.tmp is a valid Xubuntu CD
02-17 18:40 DEBUG  Distro:     does not contain C:\Users\Benji\AppData\Local\Temp\pylEAE2.tmp\casper\filesystem.squashfs
02-17 18:40 DEBUG  Distro:   checking whether C:\Users\Benji\AppData\Local\Temp\pylEAE2.tmp is a valid Mythbuntu CD
02-17 18:40 DEBUG  Distro:     does not contain C:\Users\Benji\AppData\Local\Temp\pylEAE2.tmp\casper\filesystem.squashfs
02-17 18:40 DEBUG  Distro:   checking whether C:\Users\Benji\AppData\Local\Temp\pylEAE2.tmp is a valid Mythbuntu CD
02-17 18:40 DEBUG  Distro:     does not contain C:\Users\Benji\AppData\Local\Temp\pylEAE2.tmp\casper\filesystem.squashfs
02-17 18:40 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
02-17 18:40 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-17 18:40 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
02-17 18:40 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-17 18:40 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
02-17 18:40 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-17 18:40 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
02-17 18:40 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-17 18:40 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
02-17 18:40 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-17 18:40 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
02-17 18:40 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-17 18:40 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
02-17 18:40 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-17 18:40 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
02-17 18:40 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-17 18:40 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
02-17 18:40 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
02-17 18:40 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
02-17 18:40 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
02-17 18:40 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
02-17 18:40 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
02-17 18:40 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
02-17 18:40 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
02-17 18:40 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
02-17 18:40 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
02-17 18:40 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
02-17 18:40 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
02-17 18:40 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
02-17 18:40 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
02-17 18:40 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
02-17 18:40 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
02-17 18:40 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu CD
02-17 18:40 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
02-17 18:40 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu CD
02-17 18:40 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
02-17 18:40 DEBUG  Distro:   checking whether Q:\ is a valid Kubuntu CD
02-17 18:40 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
02-17 18:40 DEBUG  Distro:   checking whether Q:\ is a valid Kubuntu CD
02-17 18:40 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
02-17 18:40 DEBUG  Distro:   checking whether Q:\ is a valid Xubuntu CD
02-17 18:40 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
02-17 18:40 DEBUG  Distro:   checking whether Q:\ is a valid Xubuntu CD
02-17 18:40 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
02-17 18:40 DEBUG  Distro:   checking whether Q:\ is a valid Mythbuntu CD
02-17 18:40 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
02-17 18:40 DEBUG  Distro:   checking whether Q:\ is a valid Mythbuntu CD
02-17 18:40 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
02-17 18:40 INFO   root: Running the installer...
02-17 18:40 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Benji\AppData\Local\Temp\pylEAE2.tmp\translations, languages=['en_US', 'en']
02-17 18:40 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Benji\AppData\Local\Temp\pylEAE2.tmp\translations, languages=['en_US', 'en']
02-17 18:41 DEBUG  WinuiInstallationPage: target_drive=C:, installation_size=30000MB, distro_name=Ubuntu, language=en_US, locale=en_US.UTF-8, username=benji
02-17 18:41 INFO   root: Received settings
02-17 18:41 DEBUG  CommonBackend: Searching for local CD
02-17 18:41 DEBUG  Distro:   checking whether C:\Users\Benji\AppData\Local\Temp\pylEAE2.tmp is a valid Ubuntu CD
02-17 18:41 DEBUG  Distro:     does not contain C:\Users\Benji\AppData\Local\Temp\pylEAE2.tmp\casper\filesystem.squashfs
02-17 18:41 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
02-17 18:41 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-17 18:41 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
02-17 18:41 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
02-17 18:41 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu CD
02-17 18:41 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
02-17 18:41 DEBUG  CommonBackend: Searching for local ISO
02-17 18:41 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Benji\AppData\Local\Temp\pylEAE2.tmp\translations, languages=['en_US', 'en']
02-17 18:41 DEBUG  TaskList: # Running tasklist...
02-17 18:41 DEBUG  TaskList: ## Running select_target_dir...
02-17 18:41 INFO   WindowsBackend: Installing into C:\ubuntu
02-17 18:41 DEBUG  TaskList: ## Finished select_target_dir
02-17 18:41 DEBUG  TaskList: ## Running create_dir_structure...
02-17 18:41 DEBUG  CommonBackend: Creating dir C:\ubuntu
02-17 18:41 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks
02-17 18:41 DEBUG  CommonBackend: Creating dir C:\ubuntu\install
02-17 18:41 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot
02-17 18:41 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot
02-17 18:41 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot\grub
02-17 18:41 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot\grub
02-17 18:41 DEBUG  TaskList: ## Finished create_dir_structure
02-17 18:41 DEBUG  TaskList: ## Running create_uninstaller...
02-17 18:41 DEBUG  WindowsBackend: Copying uninstaller C:\Users\Benji\Downloads\wubi.exe -> C:\ubuntu\uninstall-wubi.exe
02-17 18:41 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString C:\ubuntu\uninstall-wubi.exe
02-17 18:41 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir C:\ubuntu
02-17 18:41 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
02-17 18:41 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon C:\ubuntu\Ubuntu.ico
02-17 18:41 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 11.10-rev245
02-17 18:41 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
02-17 18:41 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com](http://www.ubuntu.com)
02-17 18:41 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
02-17 18:41 DEBUG  TaskList: ## Finished create_uninstaller
02-17 18:41 DEBUG  TaskList: ## Running create_preseed_diskimage...
02-17 18:41 DEBUG  TaskList: ## Finished create_preseed_diskimage
02-17 18:41 DEBUG  TaskList: ## Running get_diskimage...
02-17 18:41 DEBUG  TaskList: New task download
02-17 18:41 DEBUG  TaskList: ### Running download...
02-17 18:41 DEBUG  downloader: downloading [http://releases.ubuntu.com/11.10/ubuntu-11.10-wubi-amd64.tar.xz](http://releases.ubuntu.com/11.10/ubuntu-11.10-wubi-amd64.tar.xz) > C:\ubuntu\disks\ubuntu-11.10-wubi-amd64.tar.xz
02-17 18:41 DEBUG  downloader: Download start filename=C:\ubuntu\disks\ubuntu-11.10-wubi-amd64.tar.xz, url=http://releases.ubuntu.com/11.10/ubuntu-11.10-wubi-amd64.tar.xz, basename=ubuntu-11.10-wubi-amd64.tar.xz, length=507143012, text=None
02-17 18:45 INFO   WindowsFrontend: Operation cancelled
02-17 18:45 DEBUG  WindowsFrontend: frontend.quit
02-17 18:45 DEBUG  WindowsFrontend: frontend.on_quit
02-17 18:45 DEBUG  WindowsFrontend: stopping remaining background tasks: 'tasklist'
02-17 18:45 DEBUG  TaskList: # Cancelling tasklist
02-17 18:45 DEBUG  downloader: download finished (read 17940480 bytes)
02-17 18:45 DEBUG  TaskList: ### Finished download
02-17 18:45 DEBUG  WindowsFrontend: Task cancellation timed out, the program will exit anyway
02-17 18:45 DEBUG  root: application.on_quit
02-17 18:45 DEBUG  root: Forceful exit
02-17 18:45 INFO   root: sys.exit
02-18 11:31 INFO   root: === wubi 11.10 rev245 ===
02-18 11:31 DEBUG  root: Logfile is c:\users\benji\appdata\local\temp\wubi-11.10-rev245.log
02-18 11:31 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\ubuntu\\uninstall-wubi.exe"']
02-18 11:31 DEBUG  CommonBackend: data_dir=C:\Users\Benji\AppData\Local\Temp\pylA11F.tmp\data
02-18 11:31 DEBUG  WindowsBackend: 7z=C:\Users\Benji\AppData\Local\Temp\pylA11F.tmp\bin\7z.exe
02-18 11:31 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
02-18 11:31 DEBUG  CommonBackend: Fetching basic info...
02-18 11:31 DEBUG  CommonBackend: original_exe=C:\ubuntu\uninstall-wubi.exe
02-18 11:31 DEBUG  CommonBackend: platform=win32
02-18 11:31 DEBUG  CommonBackend: osname=nt
02-18 11:31 DEBUG  CommonBackend: language=en_US
02-18 11:31 DEBUG  CommonBackend: encoding=cp1252
02-18 11:31 DEBUG  WindowsBackend: arch=amd64
02-18 11:31 DEBUG  CommonBackend: Parsing isolist=C:\Users\Benji\AppData\Local\Temp\pylA11F.tmp\data\isolist.ini
02-18 11:31 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
02-18 11:31 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
02-18 11:31 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
02-18 11:31 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
02-18 11:31 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
02-18 11:31 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
02-18 11:31 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
02-18 11:31 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
02-18 11:31 DEBUG  WindowsBackend: Fetching host info...
02-18 11:31 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
02-18 11:31 DEBUG  WindowsBackend: windows version=vista
02-18 11:31 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium
02-18 11:31 DEBUG  WindowsBackend: windows_sp=None
02-18 11:31 DEBUG  WindowsBackend: windows_build=7601
02-18 11:31 DEBUG  WindowsBackend: gmt=-3
02-18 11:31 DEBUG  WindowsBackend: country=US
02-18 11:31 DEBUG  WindowsBackend: timezone=America/North_Dakota/Center
02-18 11:31 DEBUG  WindowsBackend: windows_username=Benji
02-18 11:31 DEBUG  WindowsBackend: user_full_name=Benji
02-18 11:31 DEBUG  WindowsBackend: user_directory=C:\Users\Benji
02-18 11:31 DEBUG  WindowsBackend: windows_language_code=1033
02-18 11:31 DEBUG  WindowsBackend: windows_language=English
02-18 11:31 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM) i7-2630QM CPU @ 2.00GHz
02-18 11:31 DEBUG  WindowsBackend: bootloader=vista
02-18 11:31 DEBUG  WindowsBackend: system_drive=Drive(C: hd 349772.390625 mb free ntfs)
02-18 11:31 DEBUG  WindowsBackend: drive=Drive(C: hd 349772.390625 mb free ntfs)
02-18 11:31 DEBUG  WindowsBackend: drive=Drive(D: hd 26417.21875 mb free ntfs)
02-18 11:31 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free )
02-18 11:31 DEBUG  WindowsBackend: drive=Drive(Q: hd 0.0 mb free )
02-18 11:31 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
02-18 11:31 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
02-18 11:31 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
02-18 11:31 DEBUG  WindowsBackend: keyboard_id=-268368887
02-18 11:31 DEBUG  WindowsBackend: keyboard_layout=us
02-18 11:31 DEBUG  WindowsBackend: keyboard_variant=
02-18 11:31 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
02-18 11:31 DEBUG  CommonBackend: locale=en_US.UTF-8
02-18 11:31 DEBUG  WindowsBackend: total_memory_mb=4095.99999905
02-18 11:31 DEBUG  CommonBackend: Searching ISOs on USB devices
02-18 11:31 DEBUG  CommonBackend: Searching for local CDs
02-18 11:31 DEBUG  Distro:   checking whether C:\Users\Benji\AppData\Local\Temp\pylA11F.tmp is a valid Ubuntu CD
02-18 11:31 DEBUG  Distro:     does not contain C:\Users\Benji\AppData\Local\Temp\pylA11F.tmp\casper\filesystem.squashfs
02-18 11:31 DEBUG  Distro:   checking whether C:\Users\Benji\AppData\Local\Temp\pylA11F.tmp is a valid Ubuntu CD
02-18 11:31 DEBUG  Distro:     does not contain C:\Users\Benji\AppData\Local\Temp\pylA11F.tmp\casper\filesystem.squashfs
02-18 11:31 DEBUG  Distro:   checking whether C:\Users\Benji\AppData\Local\Temp\pylA11F.tmp is a valid Kubuntu CD
02-18 11:31 DEBUG  Distro:     does not contain C:\Users\Benji\AppData\Local\Temp\pylA11F.tmp\casper\filesystem.squashfs
02-18 11:31 DEBUG  Distro:   checking whether C:\Users\Benji\AppData\Local\Temp\pylA11F.tmp is a valid Kubuntu CD
02-18 11:31 DEBUG  Distro:     does not contain C:\Users\Benji\AppData\Local\Temp\pylA11F.tmp\casper\filesystem.squashfs
02-18 11:31 DEBUG  Distro:   checking whether C:\Users\Benji\AppData\Local\Temp\pylA11F.tmp is a valid Xubuntu CD
02-18 11:31 DEBUG  Distro:     does not contain C:\Users\Benji\AppData\Local\Temp\pylA11F.tmp\casper\filesystem.squashfs
02-18 11:31 DEBUG  Distro:   checking whether C:\Users\Benji\AppData\Local\Temp\pylA11F.tmp is a valid Xubuntu CD
02-18 11:31 DEBUG  Distro:     does not contain C:\Users\Benji\AppData\Local\Temp\pylA11F.tmp\casper\filesystem.squashfs
02-18 11:31 DEBUG  Distro:   checking whether C:\Users\Benji\AppData\Local\Temp\pylA11F.tmp is a valid Mythbuntu CD
02-18 11:31 DEBUG  Distro:     does not contain C:\Users\Benji\AppData\Local\Temp\pylA11F.tmp\casper\filesystem.squashfs
02-18 11:31 DEBUG  Distro:   checking whether C:\Users\Benji\AppData\Local\Temp\pylA11F.tmp is a valid Mythbuntu CD
02-18 11:31 DEBUG  Distro:     does not contain C:\Users\Benji\AppData\Local\Temp\pylA11F.tmp\casper\filesystem.squashfs
02-18 11:31 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
02-18 11:31 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-18 11:31 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
02-18 11:31 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-18 11:31 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
02-18 11:31 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-18 11:31 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
02-18 11:31 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-18 11:31 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
02-18 11:31 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-18 11:31 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
02-18 11:31 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-18 11:31 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
02-18 11:31 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-18 11:31 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
02-18 11:31 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-18 11:31 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
02-18 11:31 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
02-18 11:31 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
02-18 11:31 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
02-18 11:31 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
02-18 11:31 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
02-18 11:31 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
02-18 11:31 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
02-18 11:31 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
02-18 11:31 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
02-18 11:31 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
02-18 11:31 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
02-18 11:31 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
02-18 11:31 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
02-18 11:31 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
02-18 11:31 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
02-18 11:31 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu CD
02-18 11:31 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
02-18 11:31 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu CD
02-18 11:31 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
02-18 11:31 DEBUG  Distro:   checking whether Q:\ is a valid Kubuntu CD
02-18 11:31 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
02-18 11:31 DEBUG  Distro:   checking whether Q:\ is a valid Kubuntu CD
02-18 11:31 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
02-18 11:31 DEBUG  Distro:   checking whether Q:\ is a valid Xubuntu CD
02-18 11:31 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
02-18 11:31 DEBUG  Distro:   checking whether Q:\ is a valid Xubuntu CD
02-18 11:31 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
02-18 11:31 DEBUG  Distro:   checking whether Q:\ is a valid Mythbuntu CD
02-18 11:31 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
02-18 11:31 DEBUG  Distro:   checking whether Q:\ is a valid Mythbuntu CD
02-18 11:31 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
02-18 11:31 INFO   root: Running the uninstaller...
02-18 11:31 INFO   CommonBackend: This is the uninstaller running
02-18 11:31 DEBUG  WindowsFrontend: __init__...
02-18 11:31 DEBUG  WindowsFrontend: on_init...
02-18 11:31 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Benji\AppData\Local\Temp\pylA11F.tmp\translations, languages=['en_US', 'en']
02-18 11:31 INFO   root: Received settings
02-18 11:31 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Benji\AppData\Local\Temp\pylA11F.tmp\translations, languages=['en_US', 'en']
02-18 11:31 DEBUG  TaskList: # Running tasklist...
02-18 11:31 DEBUG  TaskList: ## Running Remove bootloader entry...
02-18 11:31 DEBUG  WindowsBackend: Could not find bcd id
02-18 11:31 DEBUG  WindowsBackend: undo_bootini C:
02-18 11:31 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 349772.390625 mb free ntfs)
02-18 11:31 DEBUG  WindowsBackend: undo_bootini D:
02-18 11:31 DEBUG  WindowsBackend: undo_configsys Drive(D: hd 26417.21875 mb free ntfs)
02-18 11:31 DEBUG  WindowsBackend: undo_bootini Q:
02-18 11:31 DEBUG  WindowsBackend: undo_configsys Drive(Q: hd 0.0 mb free )
02-18 11:31 DEBUG  TaskList: ## Finished Remove bootloader entry
02-18 11:31 DEBUG  TaskList: ## Running Remove target dir...
02-18 11:31 DEBUG  CommonBackend: Deleting C:\ubuntu
02-18 11:31 DEBUG  TaskList: ## Finished Remove target dir
02-18 11:31 DEBUG  TaskList: ## Running Remove registry key...
02-18 11:31 DEBUG  TaskList: ## Finished Remove registry key
02-18 11:31 DEBUG  TaskList: # Finished tasklist
02-18 11:31 INFO   root: Almost finished uninstalling
02-18 11:31 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Benji\AppData\Local\Temp\pylA11F.tmp\translations, languages=['en_US', 'en']
02-18 11:31 INFO   root: Finished uninstallation
02-18 11:31 DEBUG  root: application.quit
02-18 11:31 DEBUG  WindowsFrontend: frontend.quit
02-18 11:31 DEBUG  WindowsFrontend: frontend.on_quit
02-18 11:31 DEBUG  root: application.on_quit
02-18 11:31 INFO   root: sys.exit
02-18 11:40 INFO   root: === wubi 11.10 rev245 ===
02-18 11:40 DEBUG  root: Logfile is c:\users\benji\appdata\local\temp\wubi-11.10-rev245.log
02-18 11:40 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\Users\\Benji\\Downloads\\wubi.exe"']
02-18 11:40 DEBUG  CommonBackend: data_dir=C:\Users\Benji\AppData\Local\Temp\pyl7445.tmp\data
02-18 11:40 DEBUG  WindowsBackend: 7z=C:\Users\Benji\AppData\Local\Temp\pyl7445.tmp\bin\7z.exe
02-18 11:40 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
02-18 11:40 DEBUG  CommonBackend: Fetching basic info...
02-18 11:40 DEBUG  CommonBackend: original_exe=C:\Users\Benji\Downloads\wubi.exe
02-18 11:40 DEBUG  CommonBackend: platform=win32
02-18 11:40 DEBUG  CommonBackend: osname=nt
02-18 11:40 DEBUG  CommonBackend: language=en_US
02-18 11:40 DEBUG  CommonBackend: encoding=cp1252
02-18 11:40 DEBUG  WindowsBackend: arch=amd64
02-18 11:40 DEBUG  CommonBackend: Parsing isolist=C:\Users\Benji\AppData\Local\Temp\pyl7445.tmp\data\isolist.ini
02-18 11:40 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
02-18 11:40 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
02-18 11:40 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
02-18 11:40 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
02-18 11:40 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
02-18 11:40 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
02-18 11:40 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
02-18 11:40 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
02-18 11:40 DEBUG  WindowsBackend: Fetching host info...
02-18 11:40 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
02-18 11:40 DEBUG  WindowsBackend: windows version=vista
02-18 11:40 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium
02-18 11:40 DEBUG  WindowsBackend: windows_sp=None
02-18 11:40 DEBUG  WindowsBackend: windows_build=7601
02-18 11:40 DEBUG  WindowsBackend: gmt=-3
02-18 11:40 DEBUG  WindowsBackend: country=US
02-18 11:40 DEBUG  WindowsBackend: timezone=America/North_Dakota/Center
02-18 11:40 DEBUG  WindowsBackend: windows_username=Benji
02-18 11:40 DEBUG  WindowsBackend: user_full_name=Benji
02-18 11:40 DEBUG  WindowsBackend: user_directory=C:\Users\Benji
02-18 11:40 DEBUG  WindowsBackend: windows_language_code=1033
02-18 11:40 DEBUG  WindowsBackend: windows_language=English
02-18 11:40 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM) i7-2630QM CPU @ 2.00GHz
02-18 11:40 DEBUG  WindowsBackend: bootloader=vista
02-18 11:40 DEBUG  WindowsBackend: system_drive=Drive(C: hd 348962.433594 mb free ntfs)
02-18 11:40 DEBUG  WindowsBackend: drive=Drive(C: hd 348962.433594 mb free ntfs)
02-18 11:40 DEBUG  WindowsBackend: drive=Drive(D: hd 26417.21875 mb free ntfs)
02-18 11:40 DEBUG  WindowsBackend: drive=Drive(E: removable 3788.8671875 mb free fat32)
02-18 11:40 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free )
02-18 11:40 DEBUG  WindowsBackend: drive=Drive(Q: hd 0.0 mb free )
02-18 11:40 DEBUG  WindowsBackend: uninstaller_path=None
02-18 11:40 DEBUG  WindowsBackend: previous_target_dir=None
02-18 11:40 DEBUG  WindowsBackend: previous_distro_name=None
02-18 11:40 DEBUG  WindowsBackend: keyboard_id=-268368887
02-18 11:40 DEBUG  WindowsBackend: keyboard_layout=us
02-18 11:40 DEBUG  WindowsBackend: keyboard_variant=
02-18 11:40 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
02-18 11:40 DEBUG  CommonBackend: locale=en_US.UTF-8
02-18 11:40 DEBUG  WindowsBackend: total_memory_mb=4095.99999905
02-18 11:40 DEBUG  CommonBackend: Searching ISOs on USB devices
02-18 11:40 DEBUG  CommonBackend: Searching for local CDs
02-18 11:40 DEBUG  Distro:   checking whether C:\Users\Benji\AppData\Local\Temp\pyl7445.tmp is a valid Ubuntu CD
02-18 11:40 DEBUG  Distro:     does not contain C:\Users\Benji\AppData\Local\Temp\pyl7445.tmp\casper\filesystem.squashfs
02-18 11:40 DEBUG  Distro:   checking whether C:\Users\Benji\AppData\Local\Temp\pyl7445.tmp is a valid Ubuntu CD
02-18 11:40 DEBUG  Distro:     does not contain C:\Users\Benji\AppData\Local\Temp\pyl7445.tmp\casper\filesystem.squashfs
02-18 11:40 DEBUG  Distro:   checking whether C:\Users\Benji\AppData\Local\Temp\pyl7445.tmp is a valid Kubuntu CD
02-18 11:40 DEBUG  Distro:     does not contain C:\Users\Benji\AppData\Local\Temp\pyl7445.tmp\casper\filesystem.squashfs
02-18 11:40 DEBUG  Distro:   checking whether C:\Users\Benji\AppData\Local\Temp\pyl7445.tmp is a valid Kubuntu CD
02-18 11:40 DEBUG  Distro:     does not contain C:\Users\Benji\AppData\Local\Temp\pyl7445.tmp\casper\filesystem.squashfs
02-18 11:40 DEBUG  Distro:   checking whether C:\Users\Benji\AppData\Local\Temp\pyl7445.tmp is a valid Xubuntu CD
02-18 11:40 DEBUG  Distro:     does not contain C:\Users\Benji\AppData\Local\Temp\pyl7445.tmp\casper\filesystem.squashfs
02-18 11:40 DEBUG  Distro:   checking whether C:\Users\Benji\AppData\Local\Temp\pyl7445.tmp is a valid Xubuntu CD
02-18 11:40 DEBUG  Distro:     does not contain C:\Users\Benji\AppData\Local\Temp\pyl7445.tmp\casper\filesystem.squashfs
02-18 11:40 DEBUG  Distro:   checking whether C:\Users\Benji\AppData\Local\Temp\pyl7445.tmp is a valid Mythbuntu CD
02-18 11:40 DEBUG  Distro:     does not contain C:\Users\Benji\AppData\Local\Temp\pyl7445.tmp\casper\filesystem.squashfs
02-18 11:40 DEBUG  Distro:   checking whether C:\Users\Benji\AppData\Local\Temp\pyl7445.tmp is a valid Mythbuntu CD
02-18 11:40 DEBUG  Distro:     does not contain C:\Users\Benji\AppData\Local\Temp\pyl7445.tmp\casper\filesystem.squashfs
02-18 11:40 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
02-18 11:40 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-18 11:40 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
02-18 11:40 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-18 11:40 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
02-18 11:40 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-18 11:40 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
02-18 11:40 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-18 11:40 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
02-18 11:40 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-18 11:40 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
02-18 11:40 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-18 11:40 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
02-18 11:40 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-18 11:40 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
02-18 11:40 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-18 11:40 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
02-18 11:40 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-18 11:40 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
02-18 11:40 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-18 11:40 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
02-18 11:40 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-18 11:40 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
02-18 11:40 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-18 11:40 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
02-18 11:40 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-18 11:40 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
02-18 11:40 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-18 11:40 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
02-18 11:40 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-18 11:40 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
02-18 11:40 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-18 11:40 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
02-18 11:40 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
02-18 11:40 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
02-18 11:40 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
02-18 11:40 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
02-18 11:40 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
02-18 11:40 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
02-18 11:40 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
02-18 11:40 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
02-18 11:40 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
02-18 11:40 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
02-18 11:40 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
02-18 11:40 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
02-18 11:40 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
02-18 11:40 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
02-18 11:40 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
02-18 11:40 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu CD
02-18 11:40 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
02-18 11:40 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu CD
02-18 11:40 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
02-18 11:40 DEBUG  Distro:   checking whether Q:\ is a valid Kubuntu CD
02-18 11:40 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
02-18 11:40 DEBUG  Distro:   checking whether Q:\ is a valid Kubuntu CD
02-18 11:40 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
02-18 11:40 DEBUG  Distro:   checking whether Q:\ is a valid Xubuntu CD
02-18 11:40 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
02-18 11:40 DEBUG  Distro:   checking whether Q:\ is a valid Xubuntu CD
02-18 11:40 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
02-18 11:40 DEBUG  Distro:   checking whether Q:\ is a valid Mythbuntu CD
02-18 11:40 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
02-18 11:40 DEBUG  Distro:   checking whether Q:\ is a valid Mythbuntu CD
02-18 11:40 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
02-18 11:40 INFO   root: Running the installer...
02-18 11:40 DEBUG  WindowsFrontend: __init__...
02-18 11:40 DEBUG  WindowsFrontend: on_init...
02-18 11:40 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Benji\AppData\Local\Temp\pyl7445.tmp\translations, languages=['en_US', 'en']
02-18 11:40 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Benji\AppData\Local\Temp\pyl7445.tmp\translations, languages=['en_US', 'en']
02-18 11:41 INFO   WindowsFrontend: Operation cancelled
02-18 11:41 DEBUG  WindowsFrontend: frontend.quit
02-18 11:41 DEBUG  WindowsFrontend: frontend.on_quit
02-18 11:41 DEBUG  root: application.on_quit
02-18 11:41 INFO   root: sys.exit
02-18 11:41 INFO   root: === wubi 11.10 rev245 ===
02-18 11:41 DEBUG  root: Logfile is c:\users\benji\appdata\local\temp\wubi-11.10-rev245.log
02-18 11:41 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\Users\\Benji\\Downloads\\wubi.exe"']
02-18 11:41 DEBUG  CommonBackend: data_dir=C:\Users\Benji\AppData\Local\Temp\pylB7BA.tmp\data
02-18 11:41 DEBUG  WindowsBackend: 7z=C:\Users\Benji\AppData\Local\Temp\pylB7BA.tmp\bin\7z.exe
02-18 11:41 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
02-18 11:41 DEBUG  CommonBackend: Fetching basic info...
02-18 11:41 DEBUG  CommonBackend: original_exe=C:\Users\Benji\Downloads\wubi.exe
02-18 11:41 DEBUG  CommonBackend: platform=win32
02-18 11:41 DEBUG  CommonBackend: osname=nt
02-18 11:41 DEBUG  CommonBackend: language=en_US
02-18 11:41 DEBUG  CommonBackend: encoding=cp1252
02-18 11:41 DEBUG  WindowsBackend: arch=amd64
02-18 11:41 DEBUG  CommonBackend: Parsing isolist=C:\Users\Benji\AppData\Local\Temp\pylB7BA.tmp\data\isolist.ini
02-18 11:41 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
02-18 11:41 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
02-18 11:41 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
02-18 11:41 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
02-18 11:41 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
02-18 11:41 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
02-18 11:41 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
02-18 11:41 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
02-18 11:41 DEBUG  WindowsBackend: Fetching host info...
02-18 11:41 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
02-18 11:41 DEBUG  WindowsBackend: windows version=vista
02-18 11:41 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium
02-18 11:41 DEBUG  WindowsBackend: windows_sp=None
02-18 11:41 DEBUG  WindowsBackend: windows_build=7601
02-18 11:41 DEBUG  WindowsBackend: gmt=-3
02-18 11:41 DEBUG  WindowsBackend: country=US
02-18 11:41 DEBUG  WindowsBackend: timezone=America/North_Dakota/Center
02-18 11:41 DEBUG  WindowsBackend: windows_username=Benji
02-18 11:41 DEBUG  WindowsBackend: user_full_name=Benji
02-18 11:41 DEBUG  WindowsBackend: user_directory=C:\Users\Benji
02-18 11:41 DEBUG  WindowsBackend: windows_language_code=1033
02-18 11:41 DEBUG  WindowsBackend: windows_language=English
02-18 11:41 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM) i7-2630QM CPU @ 2.00GHz
02-18 11:41 DEBUG  WindowsBackend: bootloader=vista
02-18 11:41 DEBUG  WindowsBackend: system_drive=Drive(C: hd 348962.351563 mb free ntfs)
02-18 11:41 DEBUG  WindowsBackend: drive=Drive(C: hd 348962.351563 mb free ntfs)
02-18 11:41 DEBUG  WindowsBackend: drive=Drive(D: hd 26417.21875 mb free ntfs)
02-18 11:41 DEBUG  WindowsBackend: drive=Drive(E: removable 3788.8671875 mb free fat32)
02-18 11:41 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free )
02-18 11:41 DEBUG  WindowsBackend: drive=Drive(Q: hd 0.0 mb free )
02-18 11:41 DEBUG  WindowsBackend: uninstaller_path=None
02-18 11:41 DEBUG  WindowsBackend: previous_target_dir=None
02-18 11:41 DEBUG  WindowsBackend: previous_distro_name=None
02-18 11:41 DEBUG  WindowsBackend: keyboard_id=-268368887
02-18 11:41 DEBUG  WindowsBackend: keyboard_layout=us
02-18 11:41 DEBUG  WindowsBackend: keyboard_variant=
02-18 11:41 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
02-18 11:41 DEBUG  CommonBackend: locale=en_US.UTF-8
02-18 11:41 DEBUG  WindowsBackend: total_memory_mb=4095.99999905
02-18 11:41 DEBUG  CommonBackend: Searching ISOs on USB devices
02-18 11:41 DEBUG  CommonBackend: Searching for local CDs
02-18 11:41 DEBUG  Distro:   checking whether C:\Users\Benji\AppData\Local\Temp\pylB7BA.tmp is a valid Ubuntu CD
02-18 11:41 DEBUG  Distro:     does not contain C:\Users\Benji\AppData\Local\Temp\pylB7BA.tmp\casper\filesystem.squashfs
02-18 11:41 DEBUG  Distro:   checking whether C:\Users\Benji\AppData\Local\Temp\pylB7BA.tmp is a valid Ubuntu CD
02-18 11:41 DEBUG  Distro:     does not contain C:\Users\Benji\AppData\Local\Temp\pylB7BA.tmp\casper\filesystem.squashfs
02-18 11:41 DEBUG  Distro:   checking whether C:\Users\Benji\AppData\Local\Temp\pylB7BA.tmp is a valid Kubuntu CD
02-18 11:41 DEBUG  Distro:     does not contain C:\Users\Benji\AppData\Local\Temp\pylB7BA.tmp\casper\filesystem.squashfs
02-18 11:41 DEBUG  Distro:   checking whether C:\Users\Benji\AppData\Local\Temp\pylB7BA.tmp is a valid Kubuntu CD
02-18 11:41 DEBUG  Distro:     does not contain C:\Users\Benji\AppData\Local\Temp\pylB7BA.tmp\casper\filesystem.squashfs
02-18 11:41 DEBUG  Distro:   checking whether C:\Users\Benji\AppData\Local\Temp\pylB7BA.tmp is a valid Xubuntu CD
02-18 11:41 DEBUG  Distro:     does not contain C:\Users\Benji\AppData\Local\Temp\pylB7BA.tmp\casper\filesystem.squashfs
02-18 11:41 DEBUG  Distro:   checking whether C:\Users\Benji\AppData\Local\Temp\pylB7BA.tmp is a valid Xubuntu CD
02-18 11:41 DEBUG  Distro:     does not contain C:\Users\Benji\AppData\Local\Temp\pylB7BA.tmp\casper\filesystem.squashfs
02-18 11:41 DEBUG  Distro:   checking whether C:\Users\Benji\AppData\Local\Temp\pylB7BA.tmp is a valid Mythbuntu CD
02-18 11:41 DEBUG  Distro:     does not contain C:\Users\Benji\AppData\Local\Temp\pylB7BA.tmp\casper\filesystem.squashfs
02-18 11:41 DEBUG  Distro:   checking whether C:\Users\Benji\AppData\Local\Temp\pylB7BA.tmp is a valid Mythbuntu CD
02-18 11:41 DEBUG  Distro:     does not contain C:\Users\Benji\AppData\Local\Temp\pylB7BA.tmp\casper\filesystem.squashfs
02-18 11:41 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
02-18 11:41 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-18 11:41 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
02-18 11:41 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-18 11:41 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
02-18 11:41 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-18 11:41 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
02-18 11:41 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-18 11:41 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
02-18 11:41 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-18 11:41 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
02-18 11:41 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-18 11:41 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
02-18 11:41 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-18 11:41 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
02-18 11:41 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-18 11:41 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
02-18 11:41 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-18 11:41 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
02-18 11:41 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-18 11:41 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
02-18 11:41 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-18 11:41 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
02-18 11:41 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-18 11:41 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
02-18 11:41 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-18 11:41 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
02-18 11:41 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-18 11:41 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
02-18 11:41 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-18 11:41 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
02-18 11:41 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-18 11:41 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
02-18 11:41 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
02-18 11:41 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
02-18 11:41 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
02-18 11:41 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
02-18 11:41 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
02-18 11:41 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
02-18 11:41 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
02-18 11:41 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
02-18 11:41 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
02-18 11:41 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
02-18 11:41 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
02-18 11:41 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
02-18 11:41 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
02-18 11:41 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
02-18 11:41 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
02-18 11:41 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu CD
02-18 11:41 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
02-18 11:41 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu CD
02-18 11:41 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
02-18 11:41 DEBUG  Distro:   checking whether Q:\ is a valid Kubuntu CD
02-18 11:41 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
02-18 11:41 DEBUG  Distro:   checking whether Q:\ is a valid Kubuntu CD
02-18 11:41 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
02-18 11:41 DEBUG  Distro:   checking whether Q:\ is a valid Xubuntu CD
02-18 11:41 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
02-18 11:41 DEBUG  Distro:   checking whether Q:\ is a valid Xubuntu CD
02-18 11:41 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
02-18 11:41 DEBUG  Distro:   checking whether Q:\ is a valid Mythbuntu CD
02-18 11:41 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
02-18 11:41 DEBUG  Distro:   checking whether Q:\ is a valid Mythbuntu CD
02-18 11:41 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
02-18 11:41 INFO   root: Running the installer...
02-18 11:41 DEBUG  WindowsFrontend: __init__...
02-18 11:41 DEBUG  WindowsFrontend: on_init...
02-18 11:41 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Benji\AppData\Local\Temp\pylB7BA.tmp\translations, languages=['en_US', 'en']
02-18 11:41 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Benji\AppData\Local\Temp\pylB7BA.tmp\translations, languages=['en_US', 'en']
02-18 11:41 DEBUG  WinuiInstallationPage: target_drive=C:, installation_size=30000MB, distro_name=Ubuntu, language=en_US, locale=en_US.UTF-8, username=benji
02-18 11:41 INFO   root: Received settings
02-18 11:41 DEBUG  CommonBackend: Searching for local CD
02-18 11:41 DEBUG  Distro:   checking whether C:\Users\Benji\AppData\Local\Temp\pylB7BA.tmp is a valid Ubuntu CD
02-18 11:41 DEBUG  Distro:     does not contain C:\Users\Benji\AppData\Local\Temp\pylB7BA.tmp\casper\filesystem.squashfs
02-18 11:41 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
02-18 11:41 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-18 11:41 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
02-18 11:41 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-18 11:41 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
02-18 11:41 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
02-18 11:41 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu CD
02-18 11:41 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
02-18 11:41 DEBUG  CommonBackend: Searching for local ISO
02-18 11:41 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Benji\AppData\Local\Temp\pylB7BA.tmp\translations, languages=['en_US', 'en']
02-18 11:41 DEBUG  TaskList: # Running tasklist...
02-18 11:41 DEBUG  TaskList: ## Running select_target_dir...
02-18 11:41 INFO   WindowsBackend: Installing into C:\ubuntu
02-18 11:41 DEBUG  TaskList: ## Finished select_target_dir
02-18 11:41 DEBUG  TaskList: ## Running create_dir_structure...
02-18 11:41 DEBUG  CommonBackend: Creating dir C:\ubuntu
02-18 11:41 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks
02-18 11:41 DEBUG  CommonBackend: Creating dir C:\ubuntu\install
02-18 11:41 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot
02-18 11:41 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot
02-18 11:41 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot\grub
02-18 11:41 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot\grub
02-18 11:41 DEBUG  TaskList: ## Finished create_dir_structure
02-18 11:41 DEBUG  TaskList: ## Running create_uninstaller...
02-18 11:41 DEBUG  WindowsBackend: Copying uninstaller C:\Users\Benji\Downloads\wubi.exe -> C:\ubuntu\uninstall-wubi.exe
02-18 11:41 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString C:\ubuntu\uninstall-wubi.exe
02-18 11:41 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir C:\ubuntu
02-18 11:41 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
02-18 11:41 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon C:\ubuntu\Ubuntu.ico
02-18 11:41 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 11.10-rev245
02-18 11:41 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
02-18 11:41 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com](http://www.ubuntu.com)
02-18 11:41 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
02-18 11:41 DEBUG  TaskList: ## Finished create_uninstaller
02-18 11:41 DEBUG  TaskList: ## Running create_preseed_diskimage...
02-18 11:41 DEBUG  TaskList: ## Finished create_preseed_diskimage
02-18 11:41 DEBUG  TaskList: ## Running get_diskimage...
02-18 11:41 DEBUG  TaskList: New task download
02-18 11:41 DEBUG  TaskList: ### Running download...
02-18 11:41 DEBUG  downloader: downloading [http://releases.ubuntu.com/11.10/ubuntu-11.10-wubi-amd64.tar.xz](http://releases.ubuntu.com/11.10/ubuntu-11.10-wubi-amd64.tar.xz) > C:\ubuntu\disks\ubuntu-11.10-wubi-amd64.tar.xz
02-18 11:41 DEBUG  downloader: Download start filename=C:\ubuntu\disks\ubuntu-11.10-wubi-amd64.tar.xz, url=http://releases.ubuntu.com/11.10/ubuntu-11.10-wubi-amd64.tar.xz, basename=ubuntu-11.10-wubi-amd64.tar.xz, length=507143012, text=None
02-18 12:10 DEBUG  TaskList: ### Finished download
02-18 12:10 DEBUG  downloader: download finished (read 507143012 bytes)
02-18 12:10 DEBUG  TaskList: ## Finished get_diskimage
02-18 12:10 DEBUG  TaskList: ## Running extract_diskimage...
02-18 12:11 DEBUG  TaskList: ## Finished extract_diskimage
02-18 12:11 DEBUG  TaskList: ## Running choose_disk_sizes...
02-18 12:11 DEBUG  WindowsBackend: total size=30000
  root=29744
  swap=256
  home=0
  usr=0
02-18 12:11 DEBUG  TaskList: ## Finished choose_disk_sizes
02-18 12:11 DEBUG  TaskList: ## Running expand_diskimage...
02-18 12:12 DEBUG  TaskList: ## Finished expand_diskimage
02-18 12:12 DEBUG  TaskList: ## Running create_swap_diskimage...
02-18 12:12 DEBUG  TaskList: ## Finished create_swap_diskimage
02-18 12:12 DEBUG  TaskList: ## Running modify_bootloader...
02-18 12:12 DEBUG  TaskList: New task modify_bcd
02-18 12:12 DEBUG  TaskList: ### Running modify_bcd...
02-18 12:12 DEBUG  WindowsBackend: modify_bcd Drive(C: hd 348962.351563 mb free ntfs)
02-18 12:12 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi VistaBootDrive {8a82e3de-f4e9-11e0-9887-b870f446aa9c}
02-18 12:12 DEBUG  TaskList: ### Finished modify_bcd
02-18 12:12 DEBUG  TaskList: New task modify_bcd
02-18 12:12 DEBUG  TaskList: ### Running modify_bcd...
02-18 12:12 DEBUG  WindowsBackend: modify_bcd Drive(D: hd 26417.21875 mb free ntfs)
02-18 12:12 DEBUG  WindowsBackend: BCD has already been modified
02-18 12:12 DEBUG  TaskList: ### Finished modify_bcd
02-18 12:12 DEBUG  TaskList: New task modify_bcd
02-18 12:12 DEBUG  TaskList: ### Running modify_bcd...
02-18 12:12 DEBUG  WindowsBackend: modify_bcd Drive(E: removable 3788.8671875 mb free fat32)
02-18 12:12 DEBUG  WindowsBackend: BCD has already been modified
02-18 12:12 DEBUG  TaskList: ### Finished modify_bcd
02-18 12:12 DEBUG  TaskList: New task modify_bcd
02-18 12:12 DEBUG  TaskList: ### Running modify_bcd...
02-18 12:12 DEBUG  WindowsBackend: modify_bcd Drive(Q: hd 0.0 mb free )
02-18 12:12 DEBUG  WindowsBackend: BCD has already been modified
02-18 12:12 DEBUG  TaskList: ### Finished modify_bcd
02-18 12:12 DEBUG  TaskList: ## Finished modify_bootloader
02-18 12:12 DEBUG  TaskList: ## Running diskimage_bootloader...
02-18 12:12 DEBUG  WindowsBackend: Copying C:\Users\Benji\AppData\Local\Temp\pylB7BA.tmp\winboot -> C:\ubuntu\winboot
02-18 12:12 ERROR  TaskList: [Errno 2] No such file or directory: 'Q:\\wubildr'
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 483, in diskimage_bootloader
  File "\lib\shutil.py", line 39, in copyfile
IOError: [Errno 2] No such file or directory: 'Q:\\wubildr'
02-18 12:12 DEBUG  TaskList: # Cancelling tasklist
02-18 12:12 DEBUG  TaskList: # Finished tasklist
02-18 12:12 ERROR  root: [Errno 2] No such file or directory: 'Q:\\wubildr'
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 58, in run
  File "\lib\wubi\application.py", line 132, in select_task
  File "\lib\wubi\application.py", line 158, in run_installer
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 483, in diskimage_bootloader
  File "\lib\shutil.py", line 39, in copyfile
IOError: [Errno 2] No such file or directory: 'Q:\\wubildr'
```

---

### Post by philinux on 2012-02-18
I would reboot and see what happens. And post back.

---

### Post by sadaruwan12 on 2012-02-18
> 02-16 20:50 DEBUG  downloader: downloading [http://releases.ubuntu.com/11.10/ubu...i-amd64.tar.xz](http://releases.ubuntu.com/11.10/ubu...i-amd64.tar.xz) > C:\ubuntu\disks\ubuntu-11.10-wubi-amd64.tar.xz
02-16 20:50 DEBUG  downloader: Download start filename=C:\ubuntu\disks\ubuntu-11.10-wubi-amd64.tar.xz, url=http://releases.ubuntu.com/11.10/ubuntu-11.10-wubi-amd64.tar.xz, basename=ubuntu-11.10-wubi-amd64.tar.xz, length=507143012, text=None
02-16 21:20 DEBUG  downloader: download finished (read 302685117 bytes)
02-16 21:20 DEBUG  TaskList: ### Finished download
02-16 21:20 DEBUG  TaskList: ## Finished get_diskimage
02-16 21:20 DEBUG  TaskList: ## Running extract_diskimage...
02-16 21:20 ERROR  TaskList: Extraction failed with code: 2
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 448, in extract_diskimage
Exception: Extraction failed with code: 2
02-16 21:20 DEBUG  TaskList: # Cancelling tasklist
02-16 21:20 DEBUG  TaskList: # Finished tasklist
02-16 21:20 ERROR  root: Extraction failed with code: 2
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 58, in run
  File "\lib\wubi\application.py", line 132, in select_task
  File "\lib\wubi\application.py", line 158, in run_installer
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 448, in extract_diskimage
Exception: Extraction failed with code: 2

I think the cause of the problem is here.

---

