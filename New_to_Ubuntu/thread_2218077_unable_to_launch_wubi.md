---
title: "unable to launch wubi"
date: 2014-04-19
forum: New to Ubuntu
---

### Post by yippie2 on 2014-04-19
im totally a newbie for linux,i wish to learn from the linux enviroment,but right now i am not able to install wubi,can anyone help me?thanks

the log file

[https://drive.google.com/file/d/0B0POPnLAWaGgaHlBRG9seUR0SWs/edit?usp=sharing](https://drive.google.com/file/d/0B0POPnLAWaGgaHlBRG9seUR0SWs/edit?usp=sharing)

---

### Post by yippie2 on 2014-04-19
the log file

```
04-19 15:29 INFO   root: === wubi 14.04 rev286 ===
04-19 15:29 DEBUG  root: Logfile is c:\users\kok\appdata\local\temp\wubi-14.04-rev286.log
04-19 15:29 DEBUG  root: sys.argv = ['main.pyo', '--exefile="F:\\wubi.exe"']
04-19 15:29 DEBUG  CommonBackend: data_dir=C:\Users\kok\AppData\Local\Temp\pyl52FD.tmp\data
04-19 15:29 DEBUG  WindowsBackend: 7z=C:\Users\kok\AppData\Local\Temp\pyl52FD.tmp\bin\7z.exe
04-19 15:29 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
04-19 15:29 DEBUG  CommonBackend: Fetching basic info...
04-19 15:29 DEBUG  CommonBackend: original_exe=F:\wubi.exe
04-19 15:29 DEBUG  CommonBackend: platform=win32
04-19 15:29 DEBUG  CommonBackend: osname=nt
04-19 15:29 DEBUG  CommonBackend: language=en_MY
04-19 15:29 DEBUG  CommonBackend: encoding=cp950
04-19 15:29 DEBUG  WindowsBackend: arch=amd64
04-19 15:29 DEBUG  CommonBackend: Parsing isolist=C:\Users\kok\AppData\Local\Temp\pyl52FD.tmp\data\isolist.ini
04-19 15:29 DEBUG  CommonBackend:   Adding distro Edubuntu-i386
04-19 15:29 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
04-19 15:29 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
04-19 15:29 DEBUG  CommonBackend:   Adding distro Edubuntu-amd64
04-19 15:29 DEBUG  CommonBackend:   Adding distro Ubuntu Studio-amd64
04-19 15:29 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
04-19 15:29 DEBUG  CommonBackend:   Adding distro Lubuntu-i386
04-19 15:29 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
04-19 15:29 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
04-19 15:29 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
04-19 15:29 DEBUG  CommonBackend:   Adding distro Ubuntu Studio-i386
04-19 15:29 DEBUG  CommonBackend:   Adding distro Lubuntu-amd64
04-19 15:29 DEBUG  WindowsBackend: Fetching host info...
04-19 15:29 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
04-19 15:29 DEBUG  WindowsBackend: windows version=vista
04-19 15:29 DEBUG  WindowsBackend: windows_version2=Windows 8.1 Single Language
04-19 15:29 DEBUG  WindowsBackend: windows_sp=None
04-19 15:29 DEBUG  WindowsBackend: windows_build=9600
04-19 15:29 DEBUG  WindowsBackend: gmt=8
04-19 15:29 DEBUG  WindowsBackend: country=MY
04-19 15:29 DEBUG  WindowsBackend: timezone=Asia/Kuala_Lumpur
04-19 15:29 DEBUG  WindowsBackend: windows_username=yippie
04-19 15:29 DEBUG  WindowsBackend: user_full_name=yippie
04-19 15:29 DEBUG  WindowsBackend: user_directory=C:\Users\kok
04-19 15:29 DEBUG  WindowsBackend: windows_language_code=1033
04-19 15:29 DEBUG  WindowsBackend: windows_language=English
04-19 15:29 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM) i7-3632QM CPU @ 2.20GHz
04-19 15:29 DEBUG  WindowsBackend: bootloader=vista
04-19 15:29 DEBUG  WindowsBackend: system_drive=Drive(C: hd 806922.835938 mb free ntfs)
04-19 15:29 DEBUG  WindowsBackend: drive=Drive(C: hd 806922.835938 mb free ntfs)
04-19 15:29 DEBUG  WindowsBackend: drive=Drive(D: hd 2981.01953125 mb free ntfs)
04-19 15:29 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free )
04-19 15:29 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free cdfs)
04-19 15:29 DEBUG  WindowsBackend: uninstaller_path=None
04-19 15:29 DEBUG  WindowsBackend: previous_target_dir=None
04-19 15:29 DEBUG  WindowsBackend: previous_distro_name=None
04-19 15:29 DEBUG  WindowsBackend: keyboard_id=67716105
04-19 15:29 DEBUG  WindowsBackend: keyboard_layout=us
04-19 15:29 DEBUG  WindowsBackend: keyboard_variant=
04-19 15:29 DEBUG  CommonBackend: python locale=('en_MY', 'cp950')
04-19 15:29 DEBUG  CommonBackend: locale=en_US.UTF-8
04-19 15:29 DEBUG  WindowsBackend: total_memory_mb=3985.2734375
04-19 15:29 DEBUG  CommonBackend: Searching ISOs on USB devices
04-19 15:29 DEBUG  CommonBackend: Searching for local CDs
04-19 15:29 DEBUG  Distro:   checking whether C:\Users\kok\AppData\Local\Temp\pyl52FD.tmp is a valid Ubuntu CD
04-19 15:29 DEBUG  Distro:     does not contain C:\Users\kok\AppData\Local\Temp\pyl52FD.tmp\casper\filesystem.squashfs
04-19 15:29 DEBUG  Distro:   checking whether C:\Users\kok\AppData\Local\Temp\pyl52FD.tmp is a valid Ubuntu CD
04-19 15:29 DEBUG  Distro:     does not contain C:\Users\kok\AppData\Local\Temp\pyl52FD.tmp\casper\filesystem.squashfs
04-19 15:29 DEBUG  Distro:   checking whether C:\Users\kok\AppData\Local\Temp\pyl52FD.tmp is a valid Kubuntu CD
04-19 15:29 DEBUG  Distro:     does not contain C:\Users\kok\AppData\Local\Temp\pyl52FD.tmp\casper\filesystem.squashfs
04-19 15:29 DEBUG  Distro:   checking whether C:\Users\kok\AppData\Local\Temp\pyl52FD.tmp is a valid Kubuntu CD
04-19 15:29 DEBUG  Distro:     does not contain C:\Users\kok\AppData\Local\Temp\pyl52FD.tmp\casper\filesystem.squashfs
04-19 15:29 DEBUG  Distro:   checking whether C:\Users\kok\AppData\Local\Temp\pyl52FD.tmp is a valid Mythbuntu CD
04-19 15:29 DEBUG  Distro:     does not contain C:\Users\kok\AppData\Local\Temp\pyl52FD.tmp\casper\filesystem.squashfs
04-19 15:29 DEBUG  Distro:   checking whether C:\Users\kok\AppData\Local\Temp\pyl52FD.tmp is a valid Mythbuntu CD
04-19 15:29 DEBUG  Distro:     does not contain C:\Users\kok\AppData\Local\Temp\pyl52FD.tmp\casper\filesystem.squashfs
04-19 15:29 DEBUG  Distro:   checking whether C:\Users\kok\AppData\Local\Temp\pyl52FD.tmp is a valid Edubuntu CD
04-19 15:29 DEBUG  Distro:     does not contain C:\Users\kok\AppData\Local\Temp\pyl52FD.tmp\casper\filesystem.squashfs
04-19 15:29 DEBUG  Distro:   checking whether C:\Users\kok\AppData\Local\Temp\pyl52FD.tmp is a valid Edubuntu CD
04-19 15:29 DEBUG  Distro:     does not contain C:\Users\kok\AppData\Local\Temp\pyl52FD.tmp\casper\filesystem.squashfs
04-19 15:29 DEBUG  Distro:   checking whether C:\Users\kok\AppData\Local\Temp\pyl52FD.tmp is a valid Lubuntu CD
04-19 15:29 DEBUG  Distro:     does not contain C:\Users\kok\AppData\Local\Temp\pyl52FD.tmp\casper\filesystem.squashfs
04-19 15:29 DEBUG  Distro:   checking whether C:\Users\kok\AppData\Local\Temp\pyl52FD.tmp is a valid Lubuntu CD
04-19 15:29 DEBUG  Distro:     does not contain C:\Users\kok\AppData\Local\Temp\pyl52FD.tmp\casper\filesystem.squashfs
04-19 15:29 DEBUG  Distro:   checking whether C:\Users\kok\AppData\Local\Temp\pyl52FD.tmp is a valid Ubuntu Studio CD
04-19 15:29 DEBUG  Distro:     does not contain C:\Users\kok\AppData\Local\Temp\pyl52FD.tmp\casper\filesystem.squashfs
04-19 15:29 DEBUG  Distro:   checking whether C:\Users\kok\AppData\Local\Temp\pyl52FD.tmp is a valid Ubuntu Studio CD
04-19 15:29 DEBUG  Distro:     does not contain C:\Users\kok\AppData\Local\Temp\pyl52FD.tmp\casper\filesystem.squashfs
04-19 15:29 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
04-19 15:29 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-19 15:29 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
04-19 15:29 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-19 15:29 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
04-19 15:29 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-19 15:29 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
04-19 15:29 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-19 15:29 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
04-19 15:29 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-19 15:29 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
04-19 15:29 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-19 15:29 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
04-19 15:29 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-19 15:29 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
04-19 15:29 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-19 15:29 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
04-19 15:29 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-19 15:29 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
04-19 15:29 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-19 15:29 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Studio CD
04-19 15:29 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-19 15:29 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Studio CD
04-19 15:29 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-19 15:29 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
04-19 15:29 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-19 15:29 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
04-19 15:29 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-19 15:29 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
04-19 15:29 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-19 15:29 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
04-19 15:29 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-19 15:29 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
04-19 15:29 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-19 15:29 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
04-19 15:29 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-19 15:29 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
04-19 15:29 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-19 15:29 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
04-19 15:29 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-19 15:29 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
04-19 15:29 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-19 15:29 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
04-19 15:29 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-19 15:29 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Studio CD
04-19 15:29 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-19 15:29 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Studio CD
04-19 15:29 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-19 15:29 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
04-19 15:29 DEBUG  Distro:   parsing info from str=Ubuntu 14.04 LTS "Trusty Tahr" - Release amd64 (20140417)
04-19 15:29 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '14.04', 'build': '20140417', 'codename': 'Trusty Tahr', 'arch': 'amd64'}
04-19 15:29 INFO   Distro: Found a valid CD for Ubuntu: F:\
04-19 15:29 INFO   root: Running the CD menu...
04-19 15:29 DEBUG  WindowsFrontend: __init__...
04-19 15:29 DEBUG  WindowsFrontend: on_init...
04-19 15:29 INFO   WinuiPage: appname=wubi, localedir=C:\Users\kok\AppData\Local\Temp\pyl52FD.tmp\translations, languages=['en_US', 'en']
04-19 15:29 INFO   WinuiPage: appname=wubi, localedir=C:\Users\kok\AppData\Local\Temp\pyl52FD.tmp\translations, languages=['en_US', 'en']
04-19 15:29 DEBUG  root: application.quit
04-19 15:29 DEBUG  WindowsFrontend: frontend.quit
04-19 15:29 DEBUG  WindowsFrontend: frontend.on_quit
04-19 15:29 DEBUG  root: application.on_quit
04-19 15:29 INFO   root: sys.exit
04-19 15:30 INFO   root: === wubi 14.04 rev286 ===
04-19 15:30 DEBUG  root: Logfile is c:\users\kok\appdata\local\temp\wubi-14.04-rev286.log
04-19 15:30 DEBUG  root: sys.argv = ['main.pyo', '--exefile="F:\\wubi.exe"']
04-19 15:30 DEBUG  CommonBackend: data_dir=C:\Users\kok\AppData\Local\Temp\pylF2F6.tmp\data
04-19 15:30 DEBUG  WindowsBackend: 7z=C:\Users\kok\AppData\Local\Temp\pylF2F6.tmp\bin\7z.exe
04-19 15:30 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
04-19 15:30 DEBUG  CommonBackend: Fetching basic info...
04-19 15:30 DEBUG  CommonBackend: original_exe=F:\wubi.exe
04-19 15:30 DEBUG  CommonBackend: platform=win32
04-19 15:30 DEBUG  CommonBackend: osname=nt
04-19 15:30 DEBUG  CommonBackend: language=en_MY
04-19 15:30 DEBUG  CommonBackend: encoding=cp950
04-19 15:30 DEBUG  WindowsBackend: arch=amd64
04-19 15:30 DEBUG  CommonBackend: Parsing isolist=C:\Users\kok\AppData\Local\Temp\pylF2F6.tmp\data\isolist.ini
04-19 15:30 DEBUG  CommonBackend:   Adding distro Edubuntu-i386
04-19 15:30 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
04-19 15:30 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
04-19 15:30 DEBUG  CommonBackend:   Adding distro Edubuntu-amd64
04-19 15:30 DEBUG  CommonBackend:   Adding distro Ubuntu Studio-amd64
04-19 15:30 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
04-19 15:30 DEBUG  CommonBackend:   Adding distro Lubuntu-i386
04-19 15:30 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
04-19 15:30 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
04-19 15:30 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
04-19 15:30 DEBUG  CommonBackend:   Adding distro Ubuntu Studio-i386
04-19 15:30 DEBUG  CommonBackend:   Adding distro Lubuntu-amd64
04-19 15:30 DEBUG  WindowsBackend: Fetching host info...
04-19 15:30 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
04-19 15:30 DEBUG  WindowsBackend: windows version=vista
04-19 15:30 DEBUG  WindowsBackend: windows_version2=Windows 8.1 Single Language
04-19 15:30 DEBUG  WindowsBackend: windows_sp=None
04-19 15:30 DEBUG  WindowsBackend: windows_build=9600
04-19 15:30 DEBUG  WindowsBackend: gmt=8
04-19 15:30 DEBUG  WindowsBackend: country=MY
04-19 15:30 DEBUG  WindowsBackend: timezone=Asia/Kuala_Lumpur
04-19 15:30 DEBUG  WindowsBackend: windows_username=yippie
04-19 15:30 DEBUG  WindowsBackend: user_full_name=yippie
04-19 15:30 DEBUG  WindowsBackend: user_directory=C:\Users\kok
04-19 15:30 DEBUG  WindowsBackend: windows_language_code=1033
04-19 15:30 DEBUG  WindowsBackend: windows_language=English
04-19 15:30 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM) i7-3632QM CPU @ 2.20GHz
04-19 15:30 DEBUG  WindowsBackend: bootloader=vista
04-19 15:30 DEBUG  WindowsBackend: system_drive=Drive(C: hd 806922.363281 mb free ntfs)
04-19 15:30 DEBUG  WindowsBackend: drive=Drive(C: hd 806922.363281 mb free ntfs)
04-19 15:30 DEBUG  WindowsBackend: drive=Drive(D: hd 2981.01953125 mb free ntfs)
04-19 15:30 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free )
04-19 15:30 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free cdfs)
04-19 15:30 DEBUG  WindowsBackend: uninstaller_path=None
04-19 15:30 DEBUG  WindowsBackend: previous_target_dir=None
04-19 15:30 DEBUG  WindowsBackend: previous_distro_name=None
04-19 15:30 DEBUG  WindowsBackend: keyboard_id=67716105
04-19 15:30 DEBUG  WindowsBackend: keyboard_layout=us
04-19 15:30 DEBUG  WindowsBackend: keyboard_variant=
04-19 15:30 DEBUG  CommonBackend: python locale=('en_MY', 'cp950')
04-19 15:30 DEBUG  CommonBackend: locale=en_US.UTF-8
04-19 15:30 DEBUG  WindowsBackend: total_memory_mb=3985.2734375
04-19 15:30 DEBUG  CommonBackend: Searching ISOs on USB devices
04-19 15:30 DEBUG  CommonBackend: Searching for local CDs
04-19 15:30 DEBUG  Distro:   checking whether C:\Users\kok\AppData\Local\Temp\pylF2F6.tmp is a valid Ubuntu CD
04-19 15:30 DEBUG  Distro:     does not contain C:\Users\kok\AppData\Local\Temp\pylF2F6.tmp\casper\filesystem.squashfs
04-19 15:30 DEBUG  Distro:   checking whether C:\Users\kok\AppData\Local\Temp\pylF2F6.tmp is a valid Ubuntu CD
04-19 15:30 DEBUG  Distro:     does not contain C:\Users\kok\AppData\Local\Temp\pylF2F6.tmp\casper\filesystem.squashfs
04-19 15:30 DEBUG  Distro:   checking whether C:\Users\kok\AppData\Local\Temp\pylF2F6.tmp is a valid Kubuntu CD
04-19 15:30 DEBUG  Distro:     does not contain C:\Users\kok\AppData\Local\Temp\pylF2F6.tmp\casper\filesystem.squashfs
04-19 15:30 DEBUG  Distro:   checking whether C:\Users\kok\AppData\Local\Temp\pylF2F6.tmp is a valid Kubuntu CD
04-19 15:30 DEBUG  Distro:     does not contain C:\Users\kok\AppData\Local\Temp\pylF2F6.tmp\casper\filesystem.squashfs
04-19 15:30 DEBUG  Distro:   checking whether C:\Users\kok\AppData\Local\Temp\pylF2F6.tmp is a valid Mythbuntu CD
04-19 15:30 DEBUG  Distro:     does not contain C:\Users\kok\AppData\Local\Temp\pylF2F6.tmp\casper\filesystem.squashfs
04-19 15:30 DEBUG  Distro:   checking whether C:\Users\kok\AppData\Local\Temp\pylF2F6.tmp is a valid Mythbuntu CD
04-19 15:30 DEBUG  Distro:     does not contain C:\Users\kok\AppData\Local\Temp\pylF2F6.tmp\casper\filesystem.squashfs
04-19 15:30 DEBUG  Distro:   checking whether C:\Users\kok\AppData\Local\Temp\pylF2F6.tmp is a valid Edubuntu CD
04-19 15:30 DEBUG  Distro:     does not contain C:\Users\kok\AppData\Local\Temp\pylF2F6.tmp\casper\filesystem.squashfs
04-19 15:30 DEBUG  Distro:   checking whether C:\Users\kok\AppData\Local\Temp\pylF2F6.tmp is a valid Edubuntu CD
04-19 15:30 DEBUG  Distro:     does not contain C:\Users\kok\AppData\Local\Temp\pylF2F6.tmp\casper\filesystem.squashfs
04-19 15:30 DEBUG  Distro:   checking whether C:\Users\kok\AppData\Local\Temp\pylF2F6.tmp is a valid Lubuntu CD
04-19 15:30 DEBUG  Distro:     does not contain C:\Users\kok\AppData\Local\Temp\pylF2F6.tmp\casper\filesystem.squashfs
04-19 15:30 DEBUG  Distro:   checking whether C:\Users\kok\AppData\Local\Temp\pylF2F6.tmp is a valid Lubuntu CD
04-19 15:30 DEBUG  Distro:     does not contain C:\Users\kok\AppData\Local\Temp\pylF2F6.tmp\casper\filesystem.squashfs
04-19 15:30 DEBUG  Distro:   checking whether C:\Users\kok\AppData\Local\Temp\pylF2F6.tmp is a valid Ubuntu Studio CD
04-19 15:30 DEBUG  Distro:     does not contain C:\Users\kok\AppData\Local\Temp\pylF2F6.tmp\casper\filesystem.squashfs
04-19 15:30 DEBUG  Distro:   checking whether C:\Users\kok\AppData\Local\Temp\pylF2F6.tmp is a valid Ubuntu Studio CD
04-19 15:30 DEBUG  Distro:     does not contain C:\Users\kok\AppData\Local\Temp\pylF2F6.tmp\casper\filesystem.squashfs
04-19 15:30 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
04-19 15:30 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-19 15:30 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
04-19 15:30 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-19 15:30 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
04-19 15:30 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-19 15:30 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
04-19 15:30 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-19 15:30 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
04-19 15:30 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-19 15:30 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
04-19 15:30 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-19 15:30 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
04-19 15:30 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-19 15:30 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
04-19 15:30 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-19 15:30 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
04-19 15:30 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-19 15:30 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
04-19 15:30 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-19 15:30 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Studio CD
04-19 15:30 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-19 15:30 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Studio CD
04-19 15:30 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-19 15:30 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
04-19 15:30 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-19 15:30 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
04-19 15:30 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-19 15:30 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
04-19 15:30 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-19 15:30 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
04-19 15:30 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-19 15:30 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
04-19 15:30 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-19 15:30 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
04-19 15:30 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-19 15:30 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
04-19 15:30 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-19 15:30 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
04-19 15:30 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-19 15:30 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
04-19 15:30 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-19 15:30 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
04-19 15:30 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-19 15:30 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Studio CD
04-19 15:30 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-19 15:30 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Studio CD
04-19 15:30 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-19 15:30 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
04-19 15:30 DEBUG  Distro:   parsing info from str=Ubuntu 14.04 LTS "Trusty Tahr" - Release amd64 (20140417)
04-19 15:30 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '14.04', 'build': '20140417', 'codename': 'Trusty Tahr', 'arch': 'amd64'}
04-19 15:30 INFO   Distro: Found a valid CD for Ubuntu: F:\
04-19 15:30 INFO   root: Running the CD menu...
04-19 15:30 DEBUG  WindowsFrontend: __init__...
04-19 15:30 DEBUG  WindowsFrontend: on_init...
04-19 15:30 INFO   WinuiPage: appname=wubi, localedir=C:\Users\kok\AppData\Local\Temp\pylF2F6.tmp\translations, languages=['en_US', 'en']
04-19 15:30 INFO   WinuiPage: appname=wubi, localedir=C:\Users\kok\AppData\Local\Temp\pylF2F6.tmp\translations, languages=['en_US', 'en']
04-19 15:30 INFO   root: CD menu finished
04-19 15:30 INFO   root: Rebooting
04-19 15:30 DEBUG  TaskList: # Running tasklist...
04-19 15:30 DEBUG  TaskList: ## Running reboot...
04-19 15:30 DEBUG  TaskList: ## Finished reboot
04-19 15:30 DEBUG  TaskList: # Finished tasklist
04-19 15:30 DEBUG  root: application.quit
04-19 15:30 DEBUG  WindowsFrontend: frontend.quit
04-19 15:30 DEBUG  WindowsFrontend: frontend.on_quit
04-19 15:30 DEBUG  root: application.on_quit
04-19 15:30 INFO   root: sys.exit
04-19 15:33 INFO   root: === wubi 14.04 rev286 ===
04-19 15:33 DEBUG  root: Logfile is c:\users\kok\appdata\local\temp\wubi-14.04-rev286.log
04-19 15:33 DEBUG  root: sys.argv = ['main.pyo', '--exefile="F:\\wubi.exe"']
04-19 15:33 DEBUG  CommonBackend: data_dir=C:\Users\kok\AppData\Local\Temp\pylF2D7.tmp\data
04-19 15:33 DEBUG  WindowsBackend: 7z=C:\Users\kok\AppData\Local\Temp\pylF2D7.tmp\bin\7z.exe
04-19 15:33 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
04-19 15:33 DEBUG  CommonBackend: Fetching basic info...
04-19 15:33 DEBUG  CommonBackend: original_exe=F:\wubi.exe
04-19 15:33 DEBUG  CommonBackend: platform=win32
04-19 15:33 DEBUG  CommonBackend: osname=nt
04-19 15:33 DEBUG  CommonBackend: language=en_MY
04-19 15:33 DEBUG  CommonBackend: encoding=cp950
04-19 15:33 DEBUG  WindowsBackend: arch=amd64
04-19 15:33 DEBUG  CommonBackend: Parsing isolist=C:\Users\kok\AppData\Local\Temp\pylF2D7.tmp\data\isolist.ini
04-19 15:33 DEBUG  CommonBackend:   Adding distro Edubuntu-i386
04-19 15:33 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
04-19 15:33 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
04-19 15:33 DEBUG  CommonBackend:   Adding distro Edubuntu-amd64
04-19 15:33 DEBUG  CommonBackend:   Adding distro Ubuntu Studio-amd64
04-19 15:33 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
04-19 15:33 DEBUG  CommonBackend:   Adding distro Lubuntu-i386
04-19 15:33 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
04-19 15:33 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
04-19 15:33 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
04-19 15:33 DEBUG  CommonBackend:   Adding distro Ubuntu Studio-i386
04-19 15:33 DEBUG  CommonBackend:   Adding distro Lubuntu-amd64
04-19 15:33 DEBUG  WindowsBackend: Fetching host info...
04-19 15:33 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
04-19 15:33 DEBUG  WindowsBackend: windows version=vista
04-19 15:33 DEBUG  WindowsBackend: windows_version2=Windows 8.1 Single Language
04-19 15:33 DEBUG  WindowsBackend: windows_sp=None
04-19 15:33 DEBUG  WindowsBackend: windows_build=9600
04-19 15:33 DEBUG  WindowsBackend: gmt=8
04-19 15:33 DEBUG  WindowsBackend: country=MY
04-19 15:33 DEBUG  WindowsBackend: timezone=Asia/Kuala_Lumpur
04-19 15:33 DEBUG  WindowsBackend: windows_username=yippie
04-19 15:33 DEBUG  WindowsBackend: user_full_name=yippie
04-19 15:33 DEBUG  WindowsBackend: user_directory=C:\Users\kok
04-19 15:33 DEBUG  WindowsBackend: windows_language_code=1033
04-19 15:33 DEBUG  WindowsBackend: windows_language=English
04-19 15:33 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM) i7-3632QM CPU @ 2.20GHz
04-19 15:33 DEBUG  WindowsBackend: bootloader=vista
04-19 15:33 DEBUG  WindowsBackend: system_drive=Drive(C: hd 807194.371094 mb free ntfs)
04-19 15:33 DEBUG  WindowsBackend: drive=Drive(C: hd 807194.371094 mb free ntfs)
04-19 15:33 DEBUG  WindowsBackend: drive=Drive(D: hd 2981.01953125 mb free ntfs)
04-19 15:33 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free )
04-19 15:33 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free cdfs)
04-19 15:33 DEBUG  WindowsBackend: uninstaller_path=None
04-19 15:33 DEBUG  WindowsBackend: previous_target_dir=None
04-19 15:33 DEBUG  WindowsBackend: previous_distro_name=None
04-19 15:33 DEBUG  WindowsBackend: keyboard_id=67716105
04-19 15:33 DEBUG  WindowsBackend: keyboard_layout=us
04-19 15:33 DEBUG  WindowsBackend: keyboard_variant=
04-19 15:33 DEBUG  CommonBackend: python locale=('en_MY', 'cp950')
04-19 15:33 DEBUG  CommonBackend: locale=en_US.UTF-8
04-19 15:33 DEBUG  WindowsBackend: total_memory_mb=3985.2734375
04-19 15:33 DEBUG  CommonBackend: Searching ISOs on USB devices
04-19 15:33 DEBUG  CommonBackend: Searching for local CDs
04-19 15:33 DEBUG  Distro:   checking whether C:\Users\kok\AppData\Local\Temp\pylF2D7.tmp is a valid Ubuntu CD
04-19 15:33 DEBUG  Distro:     does not contain C:\Users\kok\AppData\Local\Temp\pylF2D7.tmp\casper\filesystem.squashfs
04-19 15:33 DEBUG  Distro:   checking whether C:\Users\kok\AppData\Local\Temp\pylF2D7.tmp is a valid Ubuntu CD
04-19 15:33 DEBUG  Distro:     does not contain C:\Users\kok\AppData\Local\Temp\pylF2D7.tmp\casper\filesystem.squashfs
04-19 15:33 DEBUG  Distro:   checking whether C:\Users\kok\AppData\Local\Temp\pylF2D7.tmp is a valid Kubuntu CD
04-19 15:33 DEBUG  Distro:     does not contain C:\Users\kok\AppData\Local\Temp\pylF2D7.tmp\casper\filesystem.squashfs
04-19 15:33 DEBUG  Distro:   checking whether C:\Users\kok\AppData\Local\Temp\pylF2D7.tmp is a valid Kubuntu CD
04-19 15:33 DEBUG  Distro:     does not contain C:\Users\kok\AppData\Local\Temp\pylF2D7.tmp\casper\filesystem.squashfs
04-19 15:33 DEBUG  Distro:   checking whether C:\Users\kok\AppData\Local\Temp\pylF2D7.tmp is a valid Mythbuntu CD
04-19 15:33 DEBUG  Distro:     does not contain C:\Users\kok\AppData\Local\Temp\pylF2D7.tmp\casper\filesystem.squashfs
04-19 15:33 DEBUG  Distro:   checking whether C:\Users\kok\AppData\Local\Temp\pylF2D7.tmp is a valid Mythbuntu CD
04-19 15:33 DEBUG  Distro:     does not contain C:\Users\kok\AppData\Local\Temp\pylF2D7.tmp\casper\filesystem.squashfs
04-19 15:33 DEBUG  Distro:   checking whether C:\Users\kok\AppData\Local\Temp\pylF2D7.tmp is a valid Edubuntu CD
04-19 15:33 DEBUG  Distro:     does not contain C:\Users\kok\AppData\Local\Temp\pylF2D7.tmp\casper\filesystem.squashfs
04-19 15:33 DEBUG  Distro:   checking whether C:\Users\kok\AppData\Local\Temp\pylF2D7.tmp is a valid Edubuntu CD
04-19 15:33 DEBUG  Distro:     does not contain C:\Users\kok\AppData\Local\Temp\pylF2D7.tmp\casper\filesystem.squashfs
04-19 15:33 DEBUG  Distro:   checking whether C:\Users\kok\AppData\Local\Temp\pylF2D7.tmp is a valid Lubuntu CD
04-19 15:33 DEBUG  Distro:     does not contain C:\Users\kok\AppData\Local\Temp\pylF2D7.tmp\casper\filesystem.squashfs
04-19 15:33 DEBUG  Distro:   checking whether C:\Users\kok\AppData\Local\Temp\pylF2D7.tmp is a valid Lubuntu CD
04-19 15:33 DEBUG  Distro:     does not contain C:\Users\kok\AppData\Local\Temp\pylF2D7.tmp\casper\filesystem.squashfs
04-19 15:33 DEBUG  Distro:   checking whether C:\Users\kok\AppData\Local\Temp\pylF2D7.tmp is a valid Ubuntu Studio CD
04-19 15:33 DEBUG  Distro:     does not contain C:\Users\kok\AppData\Local\Temp\pylF2D7.tmp\casper\filesystem.squashfs
04-19 15:33 DEBUG  Distro:   checking whether C:\Users\kok\AppData\Local\Temp\pylF2D7.tmp is a valid Ubuntu Studio CD
04-19 15:33 DEBUG  Distro:     does not contain C:\Users\kok\AppData\Local\Temp\pylF2D7.tmp\casper\filesystem.squashfs
04-19 15:33 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
04-19 15:33 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-19 15:33 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
04-19 15:33 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-19 15:33 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
04-19 15:33 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-19 15:33 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
04-19 15:33 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-19 15:33 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
04-19 15:33 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-19 15:33 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
04-19 15:33 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-19 15:33 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
04-19 15:33 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-19 15:33 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
04-19 15:33 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-19 15:33 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
04-19 15:33 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-19 15:33 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
04-19 15:33 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-19 15:33 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Studio CD
04-19 15:33 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-19 15:33 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Studio CD
04-19 15:33 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-19 15:33 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
04-19 15:33 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-19 15:33 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
04-19 15:33 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-19 15:33 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
04-19 15:33 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-19 15:33 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
04-19 15:33 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-19 15:33 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
04-19 15:33 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-19 15:33 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
04-19 15:33 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-19 15:33 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
04-19 15:33 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-19 15:33 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
04-19 15:33 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-19 15:33 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
04-19 15:33 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-19 15:33 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
04-19 15:33 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-19 15:33 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Studio CD
04-19 15:33 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-19 15:33 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Studio CD
04-19 15:33 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-19 15:33 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
04-19 15:33 DEBUG  Distro:   parsing info from str=Ubuntu 14.04 LTS "Trusty Tahr" - Release amd64 (20140417)
04-19 15:33 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '14.04', 'build': '20140417', 'codename': 'Trusty Tahr', 'arch': 'amd64'}
04-19 15:33 INFO   Distro: Found a valid CD for Ubuntu: F:\
04-19 15:33 INFO   root: Running the CD menu...
04-19 15:33 DEBUG  WindowsFrontend: __init__...
04-19 15:33 DEBUG  WindowsFrontend: on_init...
04-19 15:33 INFO   WinuiPage: appname=wubi, localedir=C:\Users\kok\AppData\Local\Temp\pylF2D7.tmp\translations, languages=['en_US', 'en']
04-19 15:33 INFO   WinuiPage: appname=wubi, localedir=C:\Users\kok\AppData\Local\Temp\pylF2D7.tmp\translations, languages=['en_US', 'en']
04-19 15:34 INFO   root: CD menu finished
04-19 15:34 INFO   root: Running the CD boot helper...
04-19 15:34 INFO   WinuiPage: appname=wubi, localedir=C:\Users\kok\AppData\Local\Temp\pylF2D7.tmp\translations, languages=['en_US', 'en']
04-19 15:34 INFO   WinuiPage: appname=wubi, localedir=C:\Users\kok\AppData\Local\Temp\pylF2D7.tmp\translations, languages=['en_US', 'en']
04-19 15:34 INFO   root: CD boot helper confirmed
04-19 15:34 INFO   WinuiPage: appname=wubi, localedir=C:\Users\kok\AppData\Local\Temp\pylF2D7.tmp\translations, languages=['en_US', 'en']
04-19 15:34 DEBUG  TaskList: # Running tasklist...
04-19 15:34 DEBUG  TaskList: ## Running select_target_dir...
04-19 15:34 INFO   WindowsBackend: Installing into C:\ubuntu
04-19 15:34 DEBUG  TaskList: ## Finished select_target_dir
04-19 15:34 DEBUG  TaskList: ## Running create_dir_structure...
04-19 15:34 DEBUG  CommonBackend: Creating dir C:\ubuntu
04-19 15:34 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks
04-19 15:34 DEBUG  CommonBackend: Creating dir C:\ubuntu\install
04-19 15:34 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot
04-19 15:34 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot
04-19 15:34 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot\grub
04-19 15:34 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot\grub
04-19 15:34 DEBUG  TaskList: ## Finished create_dir_structure
04-19 15:34 DEBUG  TaskList: ## Running uncompress_target_dir...
04-19 15:34 DEBUG  TaskList: ## Finished uncompress_target_dir
04-19 15:34 DEBUG  TaskList: ## Running create_uninstaller...
04-19 15:34 DEBUG  WindowsBackend: Copying uninstaller F:\wubi.exe -> C:\ubuntu\uninstall-wubi.exe
04-19 15:34 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString C:\ubuntu\uninstall-wubi.exe
04-19 15:34 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir C:\ubuntu
04-19 15:34 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
04-19 15:34 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon C:\ubuntu\Ubuntu.ico
04-19 15:34 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 14.04-rev286
04-19 15:34 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
04-19 15:34 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com](http://www.ubuntu.com)
04-19 15:34 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
04-19 15:34 DEBUG  TaskList: ## Finished create_uninstaller
04-19 15:34 DEBUG  TaskList: ## Running copy_installation_files...
04-19 15:34 DEBUG  WindowsBackend: Copying C:\Users\kok\AppData\Local\Temp\pylF2D7.tmp\data\custom-installation -> C:\ubuntu\install\custom-installation
04-19 15:34 DEBUG  WindowsBackend: Copying C:\Users\kok\AppData\Local\Temp\pylF2D7.tmp\winboot -> C:\ubuntu\winboot
04-19 15:34 DEBUG  WindowsBackend: Copying C:\Users\kok\AppData\Local\Temp\pylF2D7.tmp\data\images\Ubuntu.ico -> C:\ubuntu\Ubuntu.ico
04-19 15:34 DEBUG  TaskList: ## Finished copy_installation_files
04-19 15:34 DEBUG  TaskList: ## Running use_cd...
04-19 15:34 DEBUG  TaskList: New task copy_file
04-19 15:34 DEBUG  TaskList: ### Running copy_file...
04-19 15:35 DEBUG  TaskList: ### Finished copy_file
04-19 15:35 DEBUG  TaskList: New task check_iso
04-19 15:35 DEBUG  TaskList: ### Running check_iso...
04-19 15:35 DEBUG  CommonBackend: Checking C:\ubuntu\install\installation.iso
04-19 15:35 DEBUG  Distro:   checking Ubuntu ISO C:\ubuntu\install\installation.iso
04-19 15:35 DEBUG  WindowsBackend:   extracting .disk\info from C:\ubuntu\install\installation.iso
04-19 15:35 DEBUG  Distro:   parsing info from str=Ubuntu 14.04 LTS "Trusty Tahr" - Release amd64 (20140417)
04-19 15:35 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '14.04', 'build': '20140417', 'codename': 'Trusty Tahr', 'arch': 'amd64'}
04-19 15:35 INFO   Distro: Found a valid iso for Ubuntu: C:\ubuntu\install\installation.iso
04-19 15:35 DEBUG  TaskList: New task get_metalink
04-19 15:35 DEBUG  TaskList: #### Running get_metalink...
04-19 15:35 DEBUG  downloader: downloading [http://releases.ubuntu.com/14.04/ubuntu-14.04-desktop-amd64.metalink](http://releases.ubuntu.com/14.04/ubuntu-14.04-desktop-amd64.metalink) > C:\ubuntu\install
04-19 15:35 DEBUG  downloader: Download start filename=C:\ubuntu\install\ubuntu-14.04-desktop-amd64.metalink, url=http://releases.ubuntu.com/14.04/ubuntu-14.04-desktop-amd64.metalink, basename=ubuntu-14.04-desktop-amd64.metalink, length=41450, text=None
04-19 15:35 DEBUG  downloader: download finished (read 41450 bytes)
04-19 15:35 DEBUG  downloader: downloading [http://releases.ubuntu.com/14.04/MD5SUMS-metalink](http://releases.ubuntu.com/14.04/MD5SUMS-metalink) > C:\ubuntu\install
04-19 15:35 DEBUG  downloader: Download start filename=C:\ubuntu\install\MD5SUMS-metalink, url=http://releases.ubuntu.com/14.04/MD5SUMS-metalink, basename=MD5SUMS-metalink, length=276, text=None
04-19 15:35 DEBUG  downloader: download finished (read 276 bytes)
04-19 15:35 DEBUG  downloader: downloading [http://releases.ubuntu.com/14.04/MD5SUMS-metalink.gpg](http://releases.ubuntu.com/14.04/MD5SUMS-metalink.gpg) > C:\ubuntu\install
04-19 15:35 DEBUG  downloader: Download start filename=C:\ubuntu\install\MD5SUMS-metalink.gpg, url=http://releases.ubuntu.com/14.04/MD5SUMS-metalink.gpg, basename=MD5SUMS-metalink.gpg, length=198, text=None
04-19 15:35 DEBUG  downloader: download finished (read 198 bytes)
04-19 15:35 INFO   saplog: Verified a signature from ID:'46181433FBB75451'.
04-19 15:35 INFO   saplog: Checking block bindings..
04-19 15:35 INFO   saplog: Key verified successfully.
04-19 15:35 DEBUG  CommonBackend: metalink md5sums:
c7522c09a4beadfd0969c8338249f126 *ubuntu-14.04-desktop-amd64.metalink
96c7de9d1c56ddf7c0f43888ab9af575 *ubuntu-14.04-desktop-i386.metalink
ac3206dd1eb05205e193767314683520 *ubuntu-14.04-server-amd64.metalink
d1c27a6e4c3dfc5d9f5ef75e46d78ca6 *ubuntu-14.04-server-i386.metalink


04-19 15:35 ERROR  CommonBackend: The md5 of the metalink does match
04-19 15:35 ERROR  CommonBackend: Cannot authenticate the metalink file, it might be corrupt
None
04-19 15:35 DEBUG  TaskList: #### Finished get_metalink
04-19 15:35 DEBUG  TaskList: New task get_file_md5
04-19 15:35 DEBUG  TaskList: #### Running get_file_md5...
04-19 15:35 DEBUG  TaskList: #### Finished get_file_md5
04-19 15:35 DEBUG  TaskList: ### Finished check_iso
04-19 15:35 DEBUG  TaskList: ## Finished use_cd
04-19 15:35 DEBUG  TaskList: ## Running extract_kernel...
04-19 15:35 DEBUG  CommonBackend: Copying files from CD F:\
04-19 15:35 DEBUG  CommonBackend: Checking kernel, initrd and md5sums
04-19 15:35 DEBUG  CommonBackend:   checking C:\ubuntu\install\boot\vmlinuz.efi
04-19 15:35 DEBUG  CommonBackend:   C:\ubuntu\install\boot\vmlinuz.efi md5 = 3830553e4d2e1e040238a4317911d8ed == 3830553e4d2e1e040238a4317911d8ed
04-19 15:35 DEBUG  CommonBackend:   checking C:\ubuntu\install\boot\initrd.lz
04-19 15:35 DEBUG  CommonBackend:   C:\ubuntu\install\boot\initrd.lz md5 = add08a9be2fd6cb462f82a5b01810bb8 == add08a9be2fd6cb462f82a5b01810bb8
04-19 15:35 DEBUG  TaskList: ## Finished extract_kernel
04-19 15:35 DEBUG  TaskList: ## Running create_preseed_cdboot...
04-19 15:35 DEBUG  TaskList: ## Finished create_preseed_cdboot
04-19 15:35 DEBUG  TaskList: ## Running modify_bootloader...
04-19 15:35 DEBUG  TaskList: New task modify_bcd
04-19 15:35 DEBUG  TaskList: ### Running modify_bcd...
04-19 15:35 DEBUG  WindowsBackend: modify_bcd Drive(C: hd 807194.371094 mb free ntfs)
04-19 15:35 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi VistaBootDrive {db2adfeb-a92b-11e3-8141-ed22acc76131}
04-19 15:35 DEBUG  TaskList: ### Finished modify_bcd
04-19 15:35 DEBUG  TaskList: New task modify_bcd
04-19 15:35 DEBUG  TaskList: ### Running modify_bcd...
04-19 15:35 DEBUG  WindowsBackend: modify_bcd Drive(D: hd 2981.01953125 mb free ntfs)
04-19 15:35 DEBUG  WindowsBackend: BCD has already been modified
04-19 15:35 DEBUG  TaskList: ### Finished modify_bcd
04-19 15:35 DEBUG  TaskList: ## Finished modify_bootloader
04-19 15:35 DEBUG  TaskList: ## Running modify_grub_configuration...
04-19 15:35 DEBUG  TaskList: ## Finished modify_grub_configuration
04-19 15:35 DEBUG  TaskList: ## Running uncompress_files...
04-19 15:35 DEBUG  WindowsBackend: compact C:\ubuntu\install\boot /U /A /F
04-19 15:35 DEBUG  WindowsBackend: compact C:\ubuntu\install\boot\*.* /U /A /F
04-19 15:35 DEBUG  TaskList: ## Finished uncompress_files
04-19 15:35 DEBUG  TaskList: ## Running eject_cd...
04-19 15:35 DEBUG  TaskList: ## Finished eject_cd
04-19 15:35 DEBUG  TaskList: # Finished tasklist
04-19 15:35 INFO   root: Almost finished installing
04-19 15:35 INFO   WinuiPage: appname=wubi, localedir=C:\Users\kok\AppData\Local\Temp\pylF2D7.tmp\translations, languages=['en_US', 'en']
04-19 15:35 INFO   root: Finished installation
04-19 15:35 INFO   root: Rebooting
04-19 15:35 DEBUG  TaskList: # Running tasklist...
04-19 15:35 DEBUG  TaskList: ## Running reboot...
04-19 15:35 DEBUG  TaskList: ## Finished reboot
04-19 15:35 DEBUG  TaskList: # Finished tasklist
04-19 15:35 DEBUG  root: application.quit
04-19 15:35 DEBUG  WindowsFrontend: frontend.quit
04-19 15:35 DEBUG  WindowsFrontend: frontend.on_quit
04-19 15:35 DEBUG  root: application.on_quit
04-19 15:35 INFO   root: sys.exit
04-19 16:04 INFO   root: === wubi 14.04 rev286 ===
04-19 16:04 DEBUG  root: Logfile is c:\users\kok\appdata\local\temp\wubi-14.04-rev286.log
04-19 16:04 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\ubuntu\\uninstall-wubi.exe"']
04-19 16:04 DEBUG  CommonBackend: data_dir=C:\Users\kok\AppData\Local\Temp\pyl6F20.tmp\data
04-19 16:04 DEBUG  WindowsBackend: 7z=C:\Users\kok\AppData\Local\Temp\pyl6F20.tmp\bin\7z.exe
04-19 16:04 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
04-19 16:04 DEBUG  CommonBackend: Fetching basic info...
04-19 16:04 DEBUG  CommonBackend: original_exe=C:\ubuntu\uninstall-wubi.exe
04-19 16:04 DEBUG  CommonBackend: platform=win32
04-19 16:04 DEBUG  CommonBackend: osname=nt
04-19 16:04 DEBUG  CommonBackend: language=en_MY
04-19 16:04 DEBUG  CommonBackend: encoding=cp950
04-19 16:04 DEBUG  WindowsBackend: arch=amd64
04-19 16:04 DEBUG  CommonBackend: Parsing isolist=C:\Users\kok\AppData\Local\Temp\pyl6F20.tmp\data\isolist.ini
04-19 16:04 DEBUG  CommonBackend:   Adding distro Edubuntu-i386
04-19 16:04 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
04-19 16:04 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
04-19 16:04 DEBUG  CommonBackend:   Adding distro Edubuntu-amd64
04-19 16:04 DEBUG  CommonBackend:   Adding distro Ubuntu Studio-amd64
04-19 16:04 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
04-19 16:04 DEBUG  CommonBackend:   Adding distro Lubuntu-i386
04-19 16:04 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
04-19 16:04 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
04-19 16:04 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
04-19 16:04 DEBUG  CommonBackend:   Adding distro Ubuntu Studio-i386
04-19 16:04 DEBUG  CommonBackend:   Adding distro Lubuntu-amd64
04-19 16:04 DEBUG  WindowsBackend: Fetching host info...
04-19 16:04 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
04-19 16:04 DEBUG  WindowsBackend: windows version=vista
04-19 16:04 DEBUG  WindowsBackend: windows_version2=Windows 8.1 Single Language
04-19 16:04 DEBUG  WindowsBackend: windows_sp=None
04-19 16:04 DEBUG  WindowsBackend: windows_build=9600
04-19 16:04 DEBUG  WindowsBackend: gmt=8
04-19 16:04 DEBUG  WindowsBackend: country=MY
04-19 16:04 DEBUG  WindowsBackend: timezone=Asia/Kuala_Lumpur
04-19 16:04 DEBUG  WindowsBackend: windows_username=yippie
04-19 16:04 DEBUG  WindowsBackend: user_full_name=yippie
04-19 16:04 DEBUG  WindowsBackend: user_directory=C:\Users\kok
04-19 16:04 DEBUG  WindowsBackend: windows_language_code=1033
04-19 16:04 DEBUG  WindowsBackend: windows_language=English
04-19 16:04 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM) i7-3632QM CPU @ 2.20GHz
04-19 16:04 DEBUG  WindowsBackend: bootloader=vista
04-19 16:04 DEBUG  WindowsBackend: system_drive=Drive(C: hd 805978.5625 mb free ntfs)
04-19 16:04 DEBUG  WindowsBackend: drive=Drive(C: hd 805978.5625 mb free ntfs)
04-19 16:04 DEBUG  WindowsBackend: drive=Drive(D: hd 2981.01953125 mb free ntfs)
04-19 16:04 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free )
04-19 16:04 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
04-19 16:04 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
04-19 16:04 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
04-19 16:04 DEBUG  WindowsBackend: keyboard_id=67716105
04-19 16:04 DEBUG  WindowsBackend: keyboard_layout=us
04-19 16:04 DEBUG  WindowsBackend: keyboard_variant=
04-19 16:04 DEBUG  CommonBackend: python locale=('en_MY', 'cp950')
04-19 16:04 DEBUG  CommonBackend: locale=en_US.UTF-8
04-19 16:04 DEBUG  WindowsBackend: total_memory_mb=3985.2734375
04-19 16:04 DEBUG  CommonBackend: Searching ISOs on USB devices
04-19 16:04 DEBUG  CommonBackend: Searching for local CDs
04-19 16:04 DEBUG  Distro:   checking whether C:\Users\kok\AppData\Local\Temp\pyl6F20.tmp is a valid Ubuntu CD
04-19 16:04 DEBUG  Distro:     does not contain C:\Users\kok\AppData\Local\Temp\pyl6F20.tmp\casper\filesystem.squashfs
04-19 16:04 DEBUG  Distro:   checking whether C:\Users\kok\AppData\Local\Temp\pyl6F20.tmp is a valid Ubuntu CD
04-19 16:04 DEBUG  Distro:     does not contain C:\Users\kok\AppData\Local\Temp\pyl6F20.tmp\casper\filesystem.squashfs
04-19 16:04 DEBUG  Distro:   checking whether C:\Users\kok\AppData\Local\Temp\pyl6F20.tmp is a valid Kubuntu CD
04-19 16:04 DEBUG  Distro:     does not contain C:\Users\kok\AppData\Local\Temp\pyl6F20.tmp\casper\filesystem.squashfs
04-19 16:04 DEBUG  Distro:   checking whether C:\Users\kok\AppData\Local\Temp\pyl6F20.tmp is a valid Kubuntu CD
04-19 16:04 DEBUG  Distro:     does not contain C:\Users\kok\AppData\Local\Temp\pyl6F20.tmp\casper\filesystem.squashfs
04-19 16:04 DEBUG  Distro:   checking whether C:\Users\kok\AppData\Local\Temp\pyl6F20.tmp is a valid Mythbuntu CD
04-19 16:04 DEBUG  Distro:     does not contain C:\Users\kok\AppData\Local\Temp\pyl6F20.tmp\casper\filesystem.squashfs
04-19 16:04 DEBUG  Distro:   checking whether C:\Users\kok\AppData\Local\Temp\pyl6F20.tmp is a valid Mythbuntu CD
04-19 16:04 DEBUG  Distro:     does not contain C:\Users\kok\AppData\Local\Temp\pyl6F20.tmp\casper\filesystem.squashfs
04-19 16:04 DEBUG  Distro:   checking whether C:\Users\kok\AppData\Local\Temp\pyl6F20.tmp is a valid Edubuntu CD
04-19 16:04 DEBUG  Distro:     does not contain C:\Users\kok\AppData\Local\Temp\pyl6F20.tmp\casper\filesystem.squashfs
04-19 16:04 DEBUG  Distro:   checking whether C:\Users\kok\AppData\Local\Temp\pyl6F20.tmp is a valid Edubuntu CD
04-19 16:04 DEBUG  Distro:     does not contain C:\Users\kok\AppData\Local\Temp\pyl6F20.tmp\casper\filesystem.squashfs
04-19 16:04 DEBUG  Distro:   checking whether C:\Users\kok\AppData\Local\Temp\pyl6F20.tmp is a valid Lubuntu CD
04-19 16:04 DEBUG  Distro:     does not contain C:\Users\kok\AppData\Local\Temp\pyl6F20.tmp\casper\filesystem.squashfs
04-19 16:04 DEBUG  Distro:   checking whether C:\Users\kok\AppData\Local\Temp\pyl6F20.tmp is a valid Lubuntu CD
04-19 16:04 DEBUG  Distro:     does not contain C:\Users\kok\AppData\Local\Temp\pyl6F20.tmp\casper\filesystem.squashfs
04-19 16:04 DEBUG  Distro:   checking whether C:\Users\kok\AppData\Local\Temp\pyl6F20.tmp is a valid Ubuntu Studio CD
04-19 16:04 DEBUG  Distro:     does not contain C:\Users\kok\AppData\Local\Temp\pyl6F20.tmp\casper\filesystem.squashfs
04-19 16:04 DEBUG  Distro:   checking whether C:\Users\kok\AppData\Local\Temp\pyl6F20.tmp is a valid Ubuntu Studio CD
04-19 16:04 DEBUG  Distro:     does not contain C:\Users\kok\AppData\Local\Temp\pyl6F20.tmp\casper\filesystem.squashfs
04-19 16:04 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
04-19 16:04 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-19 16:04 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
04-19 16:04 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-19 16:04 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
04-19 16:04 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-19 16:04 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
04-19 16:04 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-19 16:04 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
04-19 16:04 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-19 16:04 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
04-19 16:04 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-19 16:04 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
04-19 16:04 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-19 16:04 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
04-19 16:04 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-19 16:04 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
04-19 16:04 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-19 16:04 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
04-19 16:04 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-19 16:04 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Studio CD
04-19 16:04 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-19 16:04 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Studio CD
04-19 16:04 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-19 16:04 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
04-19 16:04 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-19 16:04 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
04-19 16:04 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-19 16:04 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
04-19 16:04 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-19 16:04 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
04-19 16:04 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-19 16:04 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
04-19 16:04 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-19 16:04 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
04-19 16:04 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-19 16:04 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
04-19 16:04 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-19 16:04 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
04-19 16:04 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-19 16:04 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
04-19 16:04 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-19 16:04 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
04-19 16:04 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-19 16:04 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Studio CD
04-19 16:04 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-19 16:04 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Studio CD
04-19 16:04 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-19 16:04 INFO   root: Running the uninstaller...
04-19 16:04 INFO   CommonBackend: This is the uninstaller running
04-19 16:04 DEBUG  WindowsFrontend: __init__...
04-19 16:04 DEBUG  WindowsFrontend: on_init...
04-19 16:04 INFO   WinuiPage: appname=wubi, localedir=C:\Users\kok\AppData\Local\Temp\pyl6F20.tmp\translations, languages=['en_US', 'en']
04-19 16:04 INFO   root: Received settings
04-19 16:04 INFO   WinuiPage: appname=wubi, localedir=C:\Users\kok\AppData\Local\Temp\pyl6F20.tmp\translations, languages=['en_US', 'en']
04-19 16:04 DEBUG  TaskList: # Running tasklist...
04-19 16:04 DEBUG  TaskList: ## Running Remove bootloader entry...
04-19 16:04 DEBUG  WindowsBackend: Removing bcd entry {db2adfeb-a92b-11e3-8141-ed22acc76131}
04-19 16:04 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi VistaBootDrive 
04-19 16:04 DEBUG  WindowsBackend: undo_bootini C:
04-19 16:04 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 805978.5625 mb free ntfs)
04-19 16:04 DEBUG  WindowsBackend: undo_bootini D:
04-19 16:04 DEBUG  WindowsBackend: undo_configsys Drive(D: hd 2981.01953125 mb free ntfs)
04-19 16:04 DEBUG  TaskList: ## Finished Remove bootloader entry
04-19 16:04 DEBUG  TaskList: ## Running Remove target dir...
04-19 16:04 DEBUG  CommonBackend: Deleting C:\ubuntu
04-19 16:04 DEBUG  TaskList: ## Finished Remove target dir
04-19 16:04 DEBUG  TaskList: ## Running Remove registry key...
04-19 16:04 DEBUG  TaskList: ## Finished Remove registry key
04-19 16:04 DEBUG  TaskList: # Finished tasklist
04-19 16:04 INFO   root: Almost finished uninstalling
04-19 16:04 INFO   WinuiPage: appname=wubi, localedir=C:\Users\kok\AppData\Local\Temp\pyl6F20.tmp\translations, languages=['en_US', 'en']
04-19 16:04 INFO   root: Finished uninstallation
04-19 16:04 DEBUG  root: application.quit
04-19 16:04 DEBUG  WindowsFrontend: frontend.quit
04-19 16:04 DEBUG  WindowsFrontend: frontend.on_quit
04-19 16:04 DEBUG  root: application.on_quit
04-19 16:04 INFO   root: sys.exit
04-19 23:47 INFO   root: === wubi 14.04 rev286 ===
04-19 23:47 DEBUG  root: Logfile is c:\users\kok\appdata\local\temp\wubi-14.04-rev286.log
04-19 23:47 DEBUG  root: sys.argv = ['main.pyo', '--exefile="F:\\wubi.exe"']
04-19 23:47 DEBUG  CommonBackend: data_dir=C:\Users\kok\AppData\Local\Temp\pyl61B4.tmp\data
04-19 23:47 DEBUG  WindowsBackend: 7z=C:\Users\kok\AppData\Local\Temp\pyl61B4.tmp\bin\7z.exe
04-19 23:47 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
04-19 23:47 DEBUG  CommonBackend: Fetching basic info...
04-19 23:47 DEBUG  CommonBackend: original_exe=F:\wubi.exe
04-19 23:47 DEBUG  CommonBackend: platform=win32
04-19 23:47 DEBUG  CommonBackend: osname=nt
04-19 23:47 DEBUG  CommonBackend: language=en_MY
04-19 23:47 DEBUG  CommonBackend: encoding=cp950
04-19 23:47 DEBUG  WindowsBackend: arch=amd64
04-19 23:47 DEBUG  CommonBackend: Parsing isolist=C:\Users\kok\AppData\Local\Temp\pyl61B4.tmp\data\isolist.ini
04-19 23:47 DEBUG  CommonBackend:   Adding distro Edubuntu-i386
04-19 23:47 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
04-19 23:47 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
04-19 23:47 DEBUG  CommonBackend:   Adding distro Edubuntu-amd64
04-19 23:47 DEBUG  CommonBackend:   Adding distro Ubuntu Studio-amd64
04-19 23:47 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
04-19 23:47 DEBUG  CommonBackend:   Adding distro Lubuntu-i386
04-19 23:47 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
04-19 23:47 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
04-19 23:47 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
04-19 23:47 DEBUG  CommonBackend:   Adding distro Ubuntu Studio-i386
04-19 23:47 DEBUG  CommonBackend:   Adding distro Lubuntu-amd64
04-19 23:47 DEBUG  WindowsBackend: Fetching host info...
04-19 23:47 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
04-19 23:47 DEBUG  WindowsBackend: windows version=vista
04-19 23:47 DEBUG  WindowsBackend: windows_version2=Windows 8.1 Single Language
04-19 23:47 DEBUG  WindowsBackend: windows_sp=None
04-19 23:47 DEBUG  WindowsBackend: windows_build=9600
04-19 23:47 DEBUG  WindowsBackend: gmt=8
04-19 23:47 DEBUG  WindowsBackend: country=MY
04-19 23:47 DEBUG  WindowsBackend: timezone=Asia/Kuala_Lumpur
04-19 23:47 DEBUG  WindowsBackend: windows_username=yippie
04-19 23:47 DEBUG  WindowsBackend: user_full_name=yippie
04-19 23:47 DEBUG  WindowsBackend: user_directory=C:\Users\kok
04-19 23:47 DEBUG  WindowsBackend: windows_language_code=1033
04-19 23:47 DEBUG  WindowsBackend: windows_language=English
04-19 23:47 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM) i7-3632QM CPU @ 2.20GHz
04-19 23:47 DEBUG  WindowsBackend: bootloader=vista
04-19 23:47 DEBUG  WindowsBackend: system_drive=Drive(C: hd 806950.003906 mb free ntfs)
04-19 23:47 DEBUG  WindowsBackend: drive=Drive(C: hd 806950.003906 mb free ntfs)
04-19 23:47 DEBUG  WindowsBackend: drive=Drive(D: hd 2981.01953125 mb free ntfs)
04-19 23:47 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free )
04-19 23:47 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free cdfs)
04-19 23:47 DEBUG  WindowsBackend: uninstaller_path=None
04-19 23:47 DEBUG  WindowsBackend: previous_target_dir=None
04-19 23:47 DEBUG  WindowsBackend: previous_distro_name=None
04-19 23:47 DEBUG  WindowsBackend: keyboard_id=134481924
04-19 23:47 DEBUG  WindowsBackend: keyboard_layout=us
04-19 23:47 DEBUG  WindowsBackend: keyboard_variant=
04-19 23:47 DEBUG  CommonBackend: python locale=('en_MY', 'cp950')
04-19 23:47 DEBUG  CommonBackend: locale=en_US.UTF-8
04-19 23:47 DEBUG  WindowsBackend: total_memory_mb=3985.2734375
04-19 23:47 DEBUG  CommonBackend: Searching ISOs on USB devices
04-19 23:47 DEBUG  CommonBackend: Searching for local CDs
04-19 23:47 DEBUG  Distro:   checking whether C:\Users\kok\AppData\Local\Temp\pyl61B4.tmp is a valid Ubuntu CD
04-19 23:47 DEBUG  Distro:     does not contain C:\Users\kok\AppData\Local\Temp\pyl61B4.tmp\casper\filesystem.squashfs
04-19 23:47 DEBUG  Distro:   checking whether C:\Users\kok\AppData\Local\Temp\pyl61B4.tmp is a valid Ubuntu CD
04-19 23:47 DEBUG  Distro:     does not contain C:\Users\kok\AppData\Local\Temp\pyl61B4.tmp\casper\filesystem.squashfs
04-19 23:47 DEBUG  Distro:   checking whether C:\Users\kok\AppData\Local\Temp\pyl61B4.tmp is a valid Kubuntu CD
04-19 23:47 DEBUG  Distro:     does not contain C:\Users\kok\AppData\Local\Temp\pyl61B4.tmp\casper\filesystem.squashfs
04-19 23:47 DEBUG  Distro:   checking whether C:\Users\kok\AppData\Local\Temp\pyl61B4.tmp is a valid Kubuntu CD
04-19 23:47 DEBUG  Distro:     does not contain C:\Users\kok\AppData\Local\Temp\pyl61B4.tmp\casper\filesystem.squashfs
04-19 23:47 DEBUG  Distro:   checking whether C:\Users\kok\AppData\Local\Temp\pyl61B4.tmp is a valid Mythbuntu CD
04-19 23:47 DEBUG  Distro:     does not contain C:\Users\kok\AppData\Local\Temp\pyl61B4.tmp\casper\filesystem.squashfs
04-19 23:47 DEBUG  Distro:   checking whether C:\Users\kok\AppData\Local\Temp\pyl61B4.tmp is a valid Mythbuntu CD
04-19 23:47 DEBUG  Distro:     does not contain C:\Users\kok\AppData\Local\Temp\pyl61B4.tmp\casper\filesystem.squashfs
04-19 23:47 DEBUG  Distro:   checking whether C:\Users\kok\AppData\Local\Temp\pyl61B4.tmp is a valid Edubuntu CD
04-19 23:47 DEBUG  Distro:     does not contain C:\Users\kok\AppData\Local\Temp\pyl61B4.tmp\casper\filesystem.squashfs
04-19 23:47 DEBUG  Distro:   checking whether C:\Users\kok\AppData\Local\Temp\pyl61B4.tmp is a valid Edubuntu CD
04-19 23:47 DEBUG  Distro:     does not contain C:\Users\kok\AppData\Local\Temp\pyl61B4.tmp\casper\filesystem.squashfs
04-19 23:47 DEBUG  Distro:   checking whether C:\Users\kok\AppData\Local\Temp\pyl61B4.tmp is a valid Lubuntu CD
04-19 23:47 DEBUG  Distro:     does not contain C:\Users\kok\AppData\Local\Temp\pyl61B4.tmp\casper\filesystem.squashfs
04-19 23:47 DEBUG  Distro:   checking whether C:\Users\kok\AppData\Local\Temp\pyl61B4.tmp is a valid Lubuntu CD
04-19 23:47 DEBUG  Distro:     does not contain C:\Users\kok\AppData\Local\Temp\pyl61B4.tmp\casper\filesystem.squashfs
04-19 23:47 DEBUG  Distro:   checking whether C:\Users\kok\AppData\Local\Temp\pyl61B4.tmp is a valid Ubuntu Studio CD
04-19 23:47 DEBUG  Distro:     does not contain C:\Users\kok\AppData\Local\Temp\pyl61B4.tmp\casper\filesystem.squashfs
04-19 23:47 DEBUG  Distro:   checking whether C:\Users\kok\AppData\Local\Temp\pyl61B4.tmp is a valid Ubuntu Studio CD
04-19 23:47 DEBUG  Distro:     does not contain C:\Users\kok\AppData\Local\Temp\pyl61B4.tmp\casper\filesystem.squashfs
04-19 23:47 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
04-19 23:47 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-19 23:47 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
04-19 23:47 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-19 23:47 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
04-19 23:47 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-19 23:47 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
04-19 23:47 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-19 23:47 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
04-19 23:47 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-19 23:47 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
04-19 23:47 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-19 23:47 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
04-19 23:47 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-19 23:47 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
04-19 23:47 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-19 23:47 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
04-19 23:47 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-19 23:47 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
04-19 23:47 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-19 23:47 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Studio CD
04-19 23:47 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-19 23:47 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Studio CD
04-19 23:47 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-19 23:47 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
04-19 23:47 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-19 23:47 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
04-19 23:47 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-19 23:47 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
04-19 23:47 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-19 23:47 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
04-19 23:47 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-19 23:47 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
04-19 23:47 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-19 23:47 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
04-19 23:47 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-19 23:47 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
04-19 23:47 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-19 23:47 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
04-19 23:47 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-19 23:47 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
04-19 23:47 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-19 23:47 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
04-19 23:47 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-19 23:47 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Studio CD
04-19 23:47 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-19 23:47 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Studio CD
04-19 23:47 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-19 23:47 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
04-19 23:47 DEBUG  Distro:   parsing info from str=Ubuntu 14.04 LTS "Trusty Tahr" - Release amd64 (20140417)
04-19 23:47 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '14.04', 'build': '20140417', 'codename': 'Trusty Tahr', 'arch': 'amd64'}
04-19 23:47 INFO   Distro: Found a valid CD for Ubuntu: F:\
04-19 23:47 INFO   root: Running the CD menu...
04-19 23:47 DEBUG  WindowsFrontend: __init__...
04-19 23:47 DEBUG  WindowsFrontend: on_init...
04-19 23:47 INFO   WinuiPage: appname=wubi, localedir=C:\Users\kok\AppData\Local\Temp\pyl61B4.tmp\translations, languages=['en_US', 'en']
04-19 23:47 INFO   WinuiPage: appname=wubi, localedir=C:\Users\kok\AppData\Local\Temp\pyl61B4.tmp\translations, languages=['en_US', 'en']
04-19 23:48 INFO   WindowsFrontend: Operation cancelled
04-19 23:48 DEBUG  WindowsFrontend: frontend.quit
04-19 23:48 DEBUG  WindowsFrontend: frontend.on_quit
04-19 23:48 DEBUG  root: application.on_quit
04-19 23:48 INFO   root: sys.exit
04-20 00:16 INFO   root: === wubi 14.04 rev286 ===
04-20 00:16 DEBUG  root: Logfile is c:\users\kok\appdata\local\temp\wubi-14.04-rev286.log
04-20 00:16 DEBUG  root: sys.argv = ['main.pyo', '--exefile="F:\\wubi.exe"']
04-20 00:16 DEBUG  CommonBackend: data_dir=C:\Users\kok\AppData\Local\Temp\pyl9430.tmp\data
04-20 00:16 DEBUG  WindowsBackend: 7z=C:\Users\kok\AppData\Local\Temp\pyl9430.tmp\bin\7z.exe
04-20 00:16 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
04-20 00:16 DEBUG  CommonBackend: Fetching basic info...
04-20 00:16 DEBUG  CommonBackend: original_exe=F:\wubi.exe
04-20 00:16 DEBUG  CommonBackend: platform=win32
04-20 00:16 DEBUG  CommonBackend: osname=nt
04-20 00:16 DEBUG  CommonBackend: language=en_MY
04-20 00:16 DEBUG  CommonBackend: encoding=cp950
04-20 00:16 DEBUG  WindowsBackend: arch=amd64
04-20 00:16 DEBUG  CommonBackend: Parsing isolist=C:\Users\kok\AppData\Local\Temp\pyl9430.tmp\data\isolist.ini
04-20 00:16 DEBUG  CommonBackend:   Adding distro Edubuntu-i386
04-20 00:16 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
04-20 00:16 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
04-20 00:16 DEBUG  CommonBackend:   Adding distro Edubuntu-amd64
04-20 00:16 DEBUG  CommonBackend:   Adding distro Ubuntu Studio-amd64
04-20 00:16 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
04-20 00:16 DEBUG  CommonBackend:   Adding distro Lubuntu-i386
04-20 00:16 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
04-20 00:16 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
04-20 00:16 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
04-20 00:16 DEBUG  CommonBackend:   Adding distro Ubuntu Studio-i386
04-20 00:16 DEBUG  CommonBackend:   Adding distro Lubuntu-amd64
04-20 00:16 DEBUG  WindowsBackend: Fetching host info...
04-20 00:16 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
04-20 00:16 DEBUG  WindowsBackend: windows version=vista
04-20 00:16 DEBUG  WindowsBackend: windows_version2=Windows 8.1 Single Language
04-20 00:16 DEBUG  WindowsBackend: windows_sp=None
04-20 00:16 DEBUG  WindowsBackend: windows_build=9600
04-20 00:16 DEBUG  WindowsBackend: gmt=8
04-20 00:16 DEBUG  WindowsBackend: country=MY
04-20 00:16 DEBUG  WindowsBackend: timezone=Asia/Kuala_Lumpur
04-20 00:16 DEBUG  WindowsBackend: windows_username=yippie
04-20 00:16 DEBUG  WindowsBackend: user_full_name=yippie
04-20 00:16 DEBUG  WindowsBackend: user_directory=C:\Users\kok
04-20 00:16 DEBUG  WindowsBackend: windows_language_code=1033
04-20 00:16 DEBUG  WindowsBackend: windows_language=English
04-20 00:16 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM) i7-3632QM CPU @ 2.20GHz
04-20 00:16 DEBUG  WindowsBackend: bootloader=vista
04-20 00:16 DEBUG  WindowsBackend: system_drive=Drive(C: hd 806945.148438 mb free ntfs)
04-20 00:16 DEBUG  WindowsBackend: drive=Drive(C: hd 806945.148438 mb free ntfs)
04-20 00:16 DEBUG  WindowsBackend: drive=Drive(D: hd 2981.01953125 mb free ntfs)
04-20 00:16 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free )
04-20 00:16 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free cdfs)
04-20 00:16 DEBUG  WindowsBackend: drive=Drive(G: removable 931.5625 mb free fat)
04-20 00:16 DEBUG  WindowsBackend: uninstaller_path=None
04-20 00:16 DEBUG  WindowsBackend: previous_target_dir=None
04-20 00:16 DEBUG  WindowsBackend: previous_distro_name=None
04-20 00:16 DEBUG  WindowsBackend: keyboard_id=134481924
04-20 00:16 DEBUG  WindowsBackend: keyboard_layout=us
04-20 00:16 DEBUG  WindowsBackend: keyboard_variant=
04-20 00:16 DEBUG  CommonBackend: python locale=('en_MY', 'cp950')
04-20 00:16 DEBUG  CommonBackend: locale=en_US.UTF-8
04-20 00:16 DEBUG  WindowsBackend: total_memory_mb=3985.2734375
04-20 00:16 DEBUG  CommonBackend: Searching ISOs on USB devices
04-20 00:16 DEBUG  CommonBackend: Searching for local CDs
04-20 00:16 DEBUG  Distro:   checking whether C:\Users\kok\AppData\Local\Temp\pyl9430.tmp is a valid Ubuntu CD
04-20 00:16 DEBUG  Distro:     does not contain C:\Users\kok\AppData\Local\Temp\pyl9430.tmp\casper\filesystem.squashfs
04-20 00:16 DEBUG  Distro:   checking whether C:\Users\kok\AppData\Local\Temp\pyl9430.tmp is a valid Ubuntu CD
04-20 00:16 DEBUG  Distro:     does not contain C:\Users\kok\AppData\Local\Temp\pyl9430.tmp\casper\filesystem.squashfs
04-20 00:16 DEBUG  Distro:   checking whether C:\Users\kok\AppData\Local\Temp\pyl9430.tmp is a valid Kubuntu CD
04-20 00:16 DEBUG  Distro:     does not contain C:\Users\kok\AppData\Local\Temp\pyl9430.tmp\casper\filesystem.squashfs
04-20 00:16 DEBUG  Distro:   checking whether C:\Users\kok\AppData\Local\Temp\pyl9430.tmp is a valid Kubuntu CD
04-20 00:16 DEBUG  Distro:     does not contain C:\Users\kok\AppData\Local\Temp\pyl9430.tmp\casper\filesystem.squashfs
04-20 00:16 DEBUG  Distro:   checking whether C:\Users\kok\AppData\Local\Temp\pyl9430.tmp is a valid Mythbuntu CD
04-20 00:16 DEBUG  Distro:     does not contain C:\Users\kok\AppData\Local\Temp\pyl9430.tmp\casper\filesystem.squashfs
04-20 00:16 DEBUG  Distro:   checking whether C:\Users\kok\AppData\Local\Temp\pyl9430.tmp is a valid Mythbuntu CD
04-20 00:16 DEBUG  Distro:     does not contain C:\Users\kok\AppData\Local\Temp\pyl9430.tmp\casper\filesystem.squashfs
04-20 00:16 DEBUG  Distro:   checking whether C:\Users\kok\AppData\Local\Temp\pyl9430.tmp is a valid Edubuntu CD
04-20 00:16 DEBUG  Distro:     does not contain C:\Users\kok\AppData\Local\Temp\pyl9430.tmp\casper\filesystem.squashfs
04-20 00:16 DEBUG  Distro:   checking whether C:\Users\kok\AppData\Local\Temp\pyl9430.tmp is a valid Edubuntu CD
04-20 00:16 DEBUG  Distro:     does not contain C:\Users\kok\AppData\Local\Temp\pyl9430.tmp\casper\filesystem.squashfs
04-20 00:16 DEBUG  Distro:   checking whether C:\Users\kok\AppData\Local\Temp\pyl9430.tmp is a valid Lubuntu CD
04-20 00:16 DEBUG  Distro:     does not contain C:\Users\kok\AppData\Local\Temp\pyl9430.tmp\casper\filesystem.squashfs
04-20 00:16 DEBUG  Distro:   checking whether C:\Users\kok\AppData\Local\Temp\pyl9430.tmp is a valid Lubuntu CD
04-20 00:16 DEBUG  Distro:     does not contain C:\Users\kok\AppData\Local\Temp\pyl9430.tmp\casper\filesystem.squashfs
04-20 00:16 DEBUG  Distro:   checking whether C:\Users\kok\AppData\Local\Temp\pyl9430.tmp is a valid Ubuntu Studio CD
04-20 00:16 DEBUG  Distro:     does not contain C:\Users\kok\AppData\Local\Temp\pyl9430.tmp\casper\filesystem.squashfs
04-20 00:16 DEBUG  Distro:   checking whether C:\Users\kok\AppData\Local\Temp\pyl9430.tmp is a valid Ubuntu Studio CD
04-20 00:16 DEBUG  Distro:     does not contain C:\Users\kok\AppData\Local\Temp\pyl9430.tmp\casper\filesystem.squashfs
04-20 00:16 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
04-20 00:16 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-20 00:16 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
04-20 00:16 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-20 00:16 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
04-20 00:16 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-20 00:16 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
04-20 00:16 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-20 00:16 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
04-20 00:16 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-20 00:16 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
04-20 00:16 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-20 00:16 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
04-20 00:16 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-20 00:16 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
04-20 00:16 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-20 00:16 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
04-20 00:16 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-20 00:16 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
04-20 00:16 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-20 00:16 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Studio CD
04-20 00:16 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-20 00:16 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Studio CD
04-20 00:16 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-20 00:16 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
04-20 00:16 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-20 00:16 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
04-20 00:16 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-20 00:16 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
04-20 00:16 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-20 00:16 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
04-20 00:16 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-20 00:16 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
04-20 00:16 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-20 00:16 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
04-20 00:16 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-20 00:16 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
04-20 00:16 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-20 00:16 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
04-20 00:16 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-20 00:16 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
04-20 00:16 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-20 00:16 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
04-20 00:16 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-20 00:16 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Studio CD
04-20 00:16 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-20 00:16 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Studio CD
04-20 00:16 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-20 00:16 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
04-20 00:16 DEBUG  Distro:   parsing info from str=Ubuntu 14.04 LTS "Trusty Tahr" - Release amd64 (20140417)
04-20 00:16 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '14.04', 'build': '20140417', 'codename': 'Trusty Tahr', 'arch': 'amd64'}
04-20 00:16 INFO   Distro: Found a valid CD for Ubuntu: F:\
04-20 00:16 INFO   root: Running the CD menu...
04-20 00:16 DEBUG  WindowsFrontend: __init__...
04-20 00:16 DEBUG  WindowsFrontend: on_init...
04-20 00:16 INFO   WinuiPage: appname=wubi, localedir=C:\Users\kok\AppData\Local\Temp\pyl9430.tmp\translations, languages=['en_US', 'en']
04-20 00:16 INFO   WinuiPage: appname=wubi, localedir=C:\Users\kok\AppData\Local\Temp\pyl9430.tmp\translations, languages=['en_US', 'en']
04-20 00:16 INFO   root: CD menu finished
04-20 00:16 INFO   root: Rebooting
04-20 00:16 DEBUG  TaskList: # Running tasklist...
04-20 00:16 DEBUG  TaskList: ## Running reboot...
04-20 00:16 DEBUG  TaskList: ## Finished reboot
04-20 00:16 DEBUG  TaskList: # Finished tasklist
04-20 00:16 DEBUG  root: application.quit
04-20 00:16 DEBUG  WindowsFrontend: frontend.quit
04-20 00:16 DEBUG  WindowsFrontend: frontend.on_quit
04-20 00:16 DEBUG  root: application.on_quit
04-20 00:16 INFO   root: sys.exit
04-20 00:18 INFO   root: === wubi 14.04 rev286 ===
04-20 00:18 DEBUG  root: Logfile is c:\users\kok\appdata\local\temp\wubi-14.04-rev286.log
04-20 00:18 DEBUG  root: sys.argv = ['main.pyo', '--exefile="G:\\wubi.exe"']
04-20 00:18 DEBUG  CommonBackend: data_dir=C:\Users\kok\AppData\Local\Temp\pyl585C.tmp\data
04-20 00:18 DEBUG  WindowsBackend: 7z=C:\Users\kok\AppData\Local\Temp\pyl585C.tmp\bin\7z.exe
04-20 00:18 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
04-20 00:18 DEBUG  CommonBackend: Fetching basic info...
04-20 00:18 DEBUG  CommonBackend: original_exe=G:\wubi.exe
04-20 00:18 DEBUG  CommonBackend: platform=win32
04-20 00:18 DEBUG  CommonBackend: osname=nt
04-20 00:18 DEBUG  CommonBackend: language=en_MY
04-20 00:18 DEBUG  CommonBackend: encoding=cp950
04-20 00:18 DEBUG  WindowsBackend: arch=amd64
04-20 00:18 DEBUG  CommonBackend: Parsing isolist=C:\Users\kok\AppData\Local\Temp\pyl585C.tmp\data\isolist.ini
04-20 00:18 DEBUG  CommonBackend:   Adding distro Edubuntu-i386
04-20 00:18 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
04-20 00:18 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
04-20 00:18 DEBUG  CommonBackend:   Adding distro Edubuntu-amd64
04-20 00:18 DEBUG  CommonBackend:   Adding distro Ubuntu Studio-amd64
04-20 00:18 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
04-20 00:18 DEBUG  CommonBackend:   Adding distro Lubuntu-i386
04-20 00:18 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
04-20 00:18 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
04-20 00:18 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
04-20 00:18 DEBUG  CommonBackend:   Adding distro Ubuntu Studio-i386
04-20 00:18 DEBUG  CommonBackend:   Adding distro Lubuntu-amd64
04-20 00:18 DEBUG  WindowsBackend: Fetching host info...
04-20 00:18 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
04-20 00:18 DEBUG  WindowsBackend: windows version=vista
04-20 00:18 DEBUG  WindowsBackend: windows_version2=Windows 8.1 Single Language
04-20 00:18 DEBUG  WindowsBackend: windows_sp=None
04-20 00:18 DEBUG  WindowsBackend: windows_build=9600
04-20 00:18 DEBUG  WindowsBackend: gmt=8
04-20 00:18 DEBUG  WindowsBackend: country=MY
04-20 00:18 DEBUG  WindowsBackend: timezone=Asia/Kuala_Lumpur
04-20 00:18 DEBUG  WindowsBackend: windows_username=yippie
04-20 00:18 DEBUG  WindowsBackend: user_full_name=yippie
04-20 00:18 DEBUG  WindowsBackend: user_directory=C:\Users\kok
04-20 00:18 DEBUG  WindowsBackend: windows_language_code=1033
04-20 00:18 DEBUG  WindowsBackend: windows_language=English
04-20 00:18 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM) i7-3632QM CPU @ 2.20GHz
04-20 00:18 DEBUG  WindowsBackend: bootloader=vista
04-20 00:18 DEBUG  WindowsBackend: system_drive=Drive(C: hd 806972.324219 mb free ntfs)
04-20 00:18 DEBUG  WindowsBackend: drive=Drive(C: hd 806972.324219 mb free ntfs)
04-20 00:18 DEBUG  WindowsBackend: drive=Drive(D: hd 2981.01953125 mb free ntfs)
04-20 00:18 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free )
04-20 00:18 DEBUG  WindowsBackend: drive=Drive(G: removable 931.5625 mb free fat)
04-20 00:18 DEBUG  WindowsBackend: uninstaller_path=None
04-20 00:18 DEBUG  WindowsBackend: previous_target_dir=None
04-20 00:18 DEBUG  WindowsBackend: previous_distro_name=None
04-20 00:18 DEBUG  WindowsBackend: keyboard_id=67716105
04-20 00:18 DEBUG  WindowsBackend: keyboard_layout=us
04-20 00:18 DEBUG  WindowsBackend: keyboard_variant=
04-20 00:18 DEBUG  CommonBackend: python locale=('en_MY', 'cp950')
04-20 00:18 DEBUG  CommonBackend: locale=en_US.UTF-8
04-20 00:18 DEBUG  WindowsBackend: total_memory_mb=3985.2734375
04-20 00:18 DEBUG  CommonBackend: Searching ISOs on USB devices
04-20 00:18 DEBUG  CommonBackend: Searching for local CDs
04-20 00:18 DEBUG  Distro:   checking whether C:\Users\kok\AppData\Local\Temp\pyl585C.tmp is a valid Ubuntu CD
04-20 00:18 DEBUG  Distro:     does not contain C:\Users\kok\AppData\Local\Temp\pyl585C.tmp\casper\filesystem.squashfs
04-20 00:18 DEBUG  Distro:   checking whether C:\Users\kok\AppData\Local\Temp\pyl585C.tmp is a valid Ubuntu CD
04-20 00:18 DEBUG  Distro:     does not contain C:\Users\kok\AppData\Local\Temp\pyl585C.tmp\casper\filesystem.squashfs
04-20 00:18 DEBUG  Distro:   checking whether C:\Users\kok\AppData\Local\Temp\pyl585C.tmp is a valid Kubuntu CD
04-20 00:18 DEBUG  Distro:     does not contain C:\Users\kok\AppData\Local\Temp\pyl585C.tmp\casper\filesystem.squashfs
04-20 00:18 DEBUG  Distro:   checking whether C:\Users\kok\AppData\Local\Temp\pyl585C.tmp is a valid Kubuntu CD
04-20 00:18 DEBUG  Distro:     does not contain C:\Users\kok\AppData\Local\Temp\pyl585C.tmp\casper\filesystem.squashfs
04-20 00:18 DEBUG  Distro:   checking whether C:\Users\kok\AppData\Local\Temp\pyl585C.tmp is a valid Mythbuntu CD
04-20 00:18 DEBUG  Distro:     does not contain C:\Users\kok\AppData\Local\Temp\pyl585C.tmp\casper\filesystem.squashfs
04-20 00:18 DEBUG  Distro:   checking whether C:\Users\kok\AppData\Local\Temp\pyl585C.tmp is a valid Mythbuntu CD
04-20 00:18 DEBUG  Distro:     does not contain C:\Users\kok\AppData\Local\Temp\pyl585C.tmp\casper\filesystem.squashfs
04-20 00:18 DEBUG  Distro:   checking whether C:\Users\kok\AppData\Local\Temp\pyl585C.tmp is a valid Edubuntu CD
04-20 00:18 DEBUG  Distro:     does not contain C:\Users\kok\AppData\Local\Temp\pyl585C.tmp\casper\filesystem.squashfs
04-20 00:18 DEBUG  Distro:   checking whether C:\Users\kok\AppData\Local\Temp\pyl585C.tmp is a valid Edubuntu CD
04-20 00:18 DEBUG  Distro:     does not contain C:\Users\kok\AppData\Local\Temp\pyl585C.tmp\casper\filesystem.squashfs
04-20 00:18 DEBUG  Distro:   checking whether C:\Users\kok\AppData\Local\Temp\pyl585C.tmp is a valid Lubuntu CD
04-20 00:18 DEBUG  Distro:     does not contain C:\Users\kok\AppData\Local\Temp\pyl585C.tmp\casper\filesystem.squashfs
04-20 00:18 DEBUG  Distro:   checking whether C:\Users\kok\AppData\Local\Temp\pyl585C.tmp is a valid Lubuntu CD
04-20 00:18 DEBUG  Distro:     does not contain C:\Users\kok\AppData\Local\Temp\pyl585C.tmp\casper\filesystem.squashfs
04-20 00:18 DEBUG  Distro:   checking whether C:\Users\kok\AppData\Local\Temp\pyl585C.tmp is a valid Ubuntu Studio CD
04-20 00:18 DEBUG  Distro:     does not contain C:\Users\kok\AppData\Local\Temp\pyl585C.tmp\casper\filesystem.squashfs
04-20 00:18 DEBUG  Distro:   checking whether C:\Users\kok\AppData\Local\Temp\pyl585C.tmp is a valid Ubuntu Studio CD
04-20 00:18 DEBUG  Distro:     does not contain C:\Users\kok\AppData\Local\Temp\pyl585C.tmp\casper\filesystem.squashfs
04-20 00:18 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
04-20 00:18 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-20 00:18 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
04-20 00:18 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-20 00:18 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
04-20 00:18 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-20 00:18 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
04-20 00:18 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-20 00:18 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
04-20 00:18 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-20 00:18 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
04-20 00:18 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-20 00:18 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
04-20 00:18 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-20 00:18 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
04-20 00:18 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-20 00:18 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
04-20 00:18 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-20 00:18 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
04-20 00:18 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-20 00:18 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Studio CD
04-20 00:18 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-20 00:18 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Studio CD
04-20 00:18 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-20 00:18 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
04-20 00:18 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-20 00:18 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
04-20 00:18 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-20 00:18 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
04-20 00:18 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-20 00:18 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
04-20 00:18 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-20 00:18 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
04-20 00:18 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-20 00:18 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
04-20 00:18 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-20 00:18 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
04-20 00:18 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-20 00:18 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
04-20 00:18 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-20 00:18 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
04-20 00:18 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-20 00:18 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
04-20 00:18 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-20 00:18 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Studio CD
04-20 00:18 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-20 00:18 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Studio CD
04-20 00:18 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-20 00:18 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
04-20 00:18 DEBUG  Distro:   parsing info from str=Ubuntu 14.04 LTS "Trusty Tahr" - Release amd64 (20140417)
04-20 00:18 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '14.04', 'build': '20140417', 'codename': 'Trusty Tahr', 'arch': 'amd64'}
04-20 00:18 INFO   Distro: Found a valid CD for Ubuntu: G:\
04-20 00:18 INFO   root: Running the CD menu...
04-20 00:18 DEBUG  WindowsFrontend: __init__...
04-20 00:18 DEBUG  WindowsFrontend: on_init...
04-20 00:18 INFO   WinuiPage: appname=wubi, localedir=C:\Users\kok\AppData\Local\Temp\pyl585C.tmp\translations, languages=['en_US', 'en']
04-20 00:18 INFO   WinuiPage: appname=wubi, localedir=C:\Users\kok\AppData\Local\Temp\pyl585C.tmp\translations, languages=['en_US', 'en']
04-20 00:18 INFO   root: CD menu finished
04-20 00:18 INFO   root: Running the CD boot helper...
04-20 00:18 INFO   WinuiPage: appname=wubi, localedir=C:\Users\kok\AppData\Local\Temp\pyl585C.tmp\translations, languages=['en_US', 'en']
04-20 00:18 INFO   WinuiPage: appname=wubi, localedir=C:\Users\kok\AppData\Local\Temp\pyl585C.tmp\translations, languages=['en_US', 'en']
04-20 00:18 INFO   root: CD boot helper confirmed
04-20 00:18 INFO   WinuiPage: appname=wubi, localedir=C:\Users\kok\AppData\Local\Temp\pyl585C.tmp\translations, languages=['en_US', 'en']
04-20 00:18 DEBUG  TaskList: # Running tasklist...
04-20 00:18 DEBUG  TaskList: ## Running select_target_dir...
04-20 00:18 INFO   WindowsBackend: Installing into C:\ubuntu
04-20 00:18 DEBUG  TaskList: ## Finished select_target_dir
04-20 00:18 DEBUG  TaskList: ## Running create_dir_structure...
04-20 00:18 DEBUG  CommonBackend: Creating dir C:\ubuntu
04-20 00:18 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks
04-20 00:18 DEBUG  CommonBackend: Creating dir C:\ubuntu\install
04-20 00:18 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot
04-20 00:18 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot
04-20 00:18 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot\grub
04-20 00:18 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot\grub
04-20 00:18 DEBUG  TaskList: ## Finished create_dir_structure
04-20 00:18 DEBUG  TaskList: ## Running uncompress_target_dir...
04-20 00:18 DEBUG  TaskList: ## Finished uncompress_target_dir
04-20 00:18 DEBUG  TaskList: ## Running create_uninstaller...
04-20 00:18 DEBUG  WindowsBackend: Copying uninstaller G:\wubi.exe -> C:\ubuntu\uninstall-wubi.exe
04-20 00:18 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString C:\ubuntu\uninstall-wubi.exe
04-20 00:18 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir C:\ubuntu
04-20 00:18 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
04-20 00:18 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon C:\ubuntu\Ubuntu.ico
04-20 00:18 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 14.04-rev286
04-20 00:18 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
04-20 00:18 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com](http://www.ubuntu.com)
04-20 00:18 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
04-20 00:18 DEBUG  TaskList: ## Finished create_uninstaller
04-20 00:18 DEBUG  TaskList: ## Running copy_installation_files...
04-20 00:18 DEBUG  WindowsBackend: Copying C:\Users\kok\AppData\Local\Temp\pyl585C.tmp\data\custom-installation -> C:\ubuntu\install\custom-installation
04-20 00:18 DEBUG  WindowsBackend: Copying C:\Users\kok\AppData\Local\Temp\pyl585C.tmp\winboot -> C:\ubuntu\winboot
04-20 00:18 DEBUG  WindowsBackend: Copying C:\Users\kok\AppData\Local\Temp\pyl585C.tmp\data\images\Ubuntu.ico -> C:\ubuntu\Ubuntu.ico
04-20 00:18 DEBUG  TaskList: ## Finished copy_installation_files
04-20 00:18 DEBUG  TaskList: ## Running use_cd...
04-20 00:18 DEBUG  TaskList: New task copy_file
04-20 00:18 DEBUG  TaskList: ### Running copy_file...
04-20 00:20 DEBUG  TaskList: ### Finished copy_file
04-20 00:20 DEBUG  TaskList: New task check_iso
04-20 00:20 DEBUG  TaskList: ### Running check_iso...
04-20 00:20 DEBUG  CommonBackend: Checking C:\ubuntu\install\installation.iso
04-20 00:20 DEBUG  Distro:   checking Ubuntu ISO C:\ubuntu\install\installation.iso
04-20 00:20 DEBUG  WindowsBackend:   extracting .disk\info from C:\ubuntu\install\installation.iso
04-20 00:20 DEBUG  Distro:   parsing info from str=Ubuntu 14.04 LTS "Trusty Tahr" - Release amd64 (20140417)
04-20 00:20 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '14.04', 'build': '20140417', 'codename': 'Trusty Tahr', 'arch': 'amd64'}
04-20 00:20 INFO   Distro: Found a valid iso for Ubuntu: C:\ubuntu\install\installation.iso
04-20 00:20 DEBUG  TaskList: New task get_metalink
04-20 00:20 DEBUG  TaskList: #### Running get_metalink...
04-20 00:20 DEBUG  downloader: downloading [http://releases.ubuntu.com/14.04/ubuntu-14.04-desktop-amd64.metalink](http://releases.ubuntu.com/14.04/ubuntu-14.04-desktop-amd64.metalink) > C:\ubuntu\install
04-20 00:20 DEBUG  downloader: Download start filename=C:\ubuntu\install\ubuntu-14.04-desktop-amd64.metalink, url=http://releases.ubuntu.com/14.04/ubuntu-14.04-desktop-amd64.metalink, basename=ubuntu-14.04-desktop-amd64.metalink, length=41450, text=None
04-20 00:20 DEBUG  downloader: download finished (read 41450 bytes)
04-20 00:20 DEBUG  downloader: downloading [http://releases.ubuntu.com/14.04/MD5SUMS-metalink](http://releases.ubuntu.com/14.04/MD5SUMS-metalink) > C:\ubuntu\install
04-20 00:20 DEBUG  downloader: Download start filename=C:\ubuntu\install\MD5SUMS-metalink, url=http://releases.ubuntu.com/14.04/MD5SUMS-metalink, basename=MD5SUMS-metalink, length=276, text=None
04-20 00:20 DEBUG  downloader: download finished (read 276 bytes)
04-20 00:20 DEBUG  downloader: downloading [http://releases.ubuntu.com/14.04/MD5SUMS-metalink.gpg](http://releases.ubuntu.com/14.04/MD5SUMS-metalink.gpg) > C:\ubuntu\install
04-20 00:20 DEBUG  downloader: Download start filename=C:\ubuntu\install\MD5SUMS-metalink.gpg, url=http://releases.ubuntu.com/14.04/MD5SUMS-metalink.gpg, basename=MD5SUMS-metalink.gpg, length=198, text=None
04-20 00:20 DEBUG  downloader: download finished (read 198 bytes)
04-20 00:20 INFO   saplog: Verified a signature from ID:'46181433FBB75451'.
04-20 00:20 INFO   saplog: Checking block bindings..
04-20 00:20 INFO   saplog: Key verified successfully.
04-20 00:20 DEBUG  CommonBackend: metalink md5sums:
c7522c09a4beadfd0969c8338249f126 *ubuntu-14.04-desktop-amd64.metalink
96c7de9d1c56ddf7c0f43888ab9af575 *ubuntu-14.04-desktop-i386.metalink
ac3206dd1eb05205e193767314683520 *ubuntu-14.04-server-amd64.metalink
d1c27a6e4c3dfc5d9f5ef75e46d78ca6 *ubuntu-14.04-server-i386.metalink


04-20 00:20 ERROR  CommonBackend: The md5 of the metalink does match
04-20 00:20 ERROR  CommonBackend: Cannot authenticate the metalink file, it might be corrupt
None
04-20 00:20 DEBUG  TaskList: #### Finished get_metalink
04-20 00:20 DEBUG  TaskList: New task get_file_md5
04-20 00:20 DEBUG  TaskList: #### Running get_file_md5...
04-20 00:20 DEBUG  TaskList: #### Finished get_file_md5
04-20 00:20 ERROR  CommonBackend: Invalid md5 for ISO C:\ubuntu\install\installation.iso (dccff28314d9ae4ed262cfc6f35e5153 != 6b4ad02cbf6bd7baf34b9ffa2fbe6fb5)
None
04-20 00:20 DEBUG  TaskList: ### Finished check_iso
04-20 00:20 DEBUG  TaskList: ## Finished use_cd
04-20 00:20 DEBUG  TaskList: ## Running extract_kernel...
04-20 00:20 ERROR  TaskList: Could not retrieve the required installation files
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 618, in extract_kernel
Exception: Could not retrieve the required installation files
04-20 00:20 DEBUG  TaskList: # Cancelling tasklist
04-20 00:20 DEBUG  TaskList: # Finished tasklist
04-20 00:20 ERROR  root: Could not retrieve the required installation files
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 58, in run
  File "\lib\wubi\application.py", line 130, in select_task
  File "\lib\wubi\application.py", line 205, in run_cd_menu
  File "\lib\wubi\application.py", line 122, in select_task
  File "\lib\wubi\application.py", line 228, in run_cd_boot
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 618, in extract_kernel
Exception: Could not retrieve the required installation files
04-20 00:21 INFO   root: === wubi 14.04 rev286 ===
04-20 00:21 DEBUG  root: Logfile is c:\users\kok\appdata\local\temp\wubi-14.04-rev286.log
04-20 00:21 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\ubuntu\\uninstall-wubi.exe"']
04-20 00:21 DEBUG  CommonBackend: data_dir=C:\Users\kok\AppData\Local\Temp\pyl3729.tmp\data
04-20 00:21 DEBUG  WindowsBackend: 7z=C:\Users\kok\AppData\Local\Temp\pyl3729.tmp\bin\7z.exe
04-20 00:21 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
04-20 00:21 DEBUG  CommonBackend: Fetching basic info...
04-20 00:21 DEBUG  CommonBackend: original_exe=C:\ubuntu\uninstall-wubi.exe
04-20 00:21 DEBUG  CommonBackend: platform=win32
04-20 00:21 DEBUG  CommonBackend: osname=nt
04-20 00:21 DEBUG  CommonBackend: language=en_MY
04-20 00:21 DEBUG  CommonBackend: encoding=cp950
04-20 00:21 DEBUG  WindowsBackend: arch=amd64
04-20 00:21 DEBUG  CommonBackend: Parsing isolist=C:\Users\kok\AppData\Local\Temp\pyl3729.tmp\data\isolist.ini
04-20 00:21 DEBUG  CommonBackend:   Adding distro Edubuntu-i386
04-20 00:21 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
04-20 00:21 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
04-20 00:21 DEBUG  CommonBackend:   Adding distro Edubuntu-amd64
04-20 00:21 DEBUG  CommonBackend:   Adding distro Ubuntu Studio-amd64
04-20 00:21 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
04-20 00:21 DEBUG  CommonBackend:   Adding distro Lubuntu-i386
04-20 00:21 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
04-20 00:21 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
04-20 00:21 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
04-20 00:21 DEBUG  CommonBackend:   Adding distro Ubuntu Studio-i386
04-20 00:21 DEBUG  CommonBackend:   Adding distro Lubuntu-amd64
04-20 00:21 DEBUG  WindowsBackend: Fetching host info...
04-20 00:21 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
04-20 00:21 DEBUG  WindowsBackend: windows version=vista
04-20 00:21 DEBUG  WindowsBackend: windows_version2=Windows 8.1 Single Language
04-20 00:21 DEBUG  WindowsBackend: windows_sp=None
04-20 00:21 DEBUG  WindowsBackend: windows_build=9600
04-20 00:21 DEBUG  WindowsBackend: gmt=8
04-20 00:21 DEBUG  WindowsBackend: country=MY
04-20 00:21 DEBUG  WindowsBackend: timezone=Asia/Kuala_Lumpur
04-20 00:21 DEBUG  WindowsBackend: windows_username=yippie
04-20 00:21 DEBUG  WindowsBackend: user_full_name=yippie
04-20 00:21 DEBUG  WindowsBackend: user_directory=C:\Users\kok
04-20 00:21 DEBUG  WindowsBackend: windows_language_code=1033
04-20 00:21 DEBUG  WindowsBackend: windows_language=English
04-20 00:21 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM) i7-3632QM CPU @ 2.20GHz
04-20 00:21 DEBUG  WindowsBackend: bootloader=vista
04-20 00:21 DEBUG  WindowsBackend: system_drive=Drive(C: hd 805058.425781 mb free ntfs)
04-20 00:21 DEBUG  WindowsBackend: drive=Drive(C: hd 805058.425781 mb free ntfs)
04-20 00:21 DEBUG  WindowsBackend: drive=Drive(D: hd 2981.01953125 mb free ntfs)
04-20 00:21 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free )
04-20 00:21 DEBUG  WindowsBackend: drive=Drive(G: removable 931.5625 mb free fat)
04-20 00:21 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
04-20 00:21 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
04-20 00:21 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
04-20 00:21 DEBUG  WindowsBackend: keyboard_id=67716105
04-20 00:21 DEBUG  WindowsBackend: keyboard_layout=us
04-20 00:21 DEBUG  WindowsBackend: keyboard_variant=
04-20 00:21 DEBUG  CommonBackend: python locale=('en_MY', 'cp950')
04-20 00:21 DEBUG  CommonBackend: locale=en_US.UTF-8
04-20 00:21 DEBUG  WindowsBackend: total_memory_mb=3985.2734375
04-20 00:21 DEBUG  CommonBackend: Searching ISOs on USB devices
04-20 00:21 DEBUG  CommonBackend: Searching for local CDs
04-20 00:21 DEBUG  Distro:   checking whether C:\Users\kok\AppData\Local\Temp\pyl3729.tmp is a valid Ubuntu CD
04-20 00:21 DEBUG  Distro:     does not contain C:\Users\kok\AppData\Local\Temp\pyl3729.tmp\casper\filesystem.squashfs
04-20 00:21 DEBUG  Distro:   checking whether C:\Users\kok\AppData\Local\Temp\pyl3729.tmp is a valid Ubuntu CD
04-20 00:21 DEBUG  Distro:     does not contain C:\Users\kok\AppData\Local\Temp\pyl3729.tmp\casper\filesystem.squashfs
04-20 00:21 DEBUG  Distro:   checking whether C:\Users\kok\AppData\Local\Temp\pyl3729.tmp is a valid Kubuntu CD
04-20 00:21 DEBUG  Distro:     does not contain C:\Users\kok\AppData\Local\Temp\pyl3729.tmp\casper\filesystem.squashfs
04-20 00:21 DEBUG  Distro:   checking whether C:\Users\kok\AppData\Local\Temp\pyl3729.tmp is a valid Kubuntu CD
04-20 00:21 DEBUG  Distro:     does not contain C:\Users\kok\AppData\Local\Temp\pyl3729.tmp\casper\filesystem.squashfs
04-20 00:21 DEBUG  Distro:   checking whether C:\Users\kok\AppData\Local\Temp\pyl3729.tmp is a valid Mythbuntu CD
04-20 00:21 DEBUG  Distro:     does not contain C:\Users\kok\AppData\Local\Temp\pyl3729.tmp\casper\filesystem.squashfs
04-20 00:21 DEBUG  Distro:   checking whether C:\Users\kok\AppData\Local\Temp\pyl3729.tmp is a valid Mythbuntu CD
04-20 00:21 DEBUG  Distro:     does not contain C:\Users\kok\AppData\Local\Temp\pyl3729.tmp\casper\filesystem.squashfs
04-20 00:21 DEBUG  Distro:   checking whether C:\Users\kok\AppData\Local\Temp\pyl3729.tmp is a valid Edubuntu CD
04-20 00:21 DEBUG  Distro:     does not contain C:\Users\kok\AppData\Local\Temp\pyl3729.tmp\casper\filesystem.squashfs
04-20 00:21 DEBUG  Distro:   checking whether C:\Users\kok\AppData\Local\Temp\pyl3729.tmp is a valid Edubuntu CD
04-20 00:21 DEBUG  Distro:     does not contain C:\Users\kok\AppData\Local\Temp\pyl3729.tmp\casper\filesystem.squashfs
04-20 00:21 DEBUG  Distro:   checking whether C:\Users\kok\AppData\Local\Temp\pyl3729.tmp is a valid Lubuntu CD
04-20 00:21 DEBUG  Distro:     does not contain C:\Users\kok\AppData\Local\Temp\pyl3729.tmp\casper\filesystem.squashfs
04-20 00:21 DEBUG  Distro:   checking whether C:\Users\kok\AppData\Local\Temp\pyl3729.tmp is a valid Lubuntu CD
04-20 00:21 DEBUG  Distro:     does not contain C:\Users\kok\AppData\Local\Temp\pyl3729.tmp\casper\filesystem.squashfs
04-20 00:21 DEBUG  Distro:   checking whether C:\Users\kok\AppData\Local\Temp\pyl3729.tmp is a valid Ubuntu Studio CD
04-20 00:21 DEBUG  Distro:     does not contain C:\Users\kok\AppData\Local\Temp\pyl3729.tmp\casper\filesystem.squashfs
04-20 00:21 DEBUG  Distro:   checking whether C:\Users\kok\AppData\Local\Temp\pyl3729.tmp is a valid Ubuntu Studio CD
04-20 00:21 DEBUG  Distro:     does not contain C:\Users\kok\AppData\Local\Temp\pyl3729.tmp\casper\filesystem.squashfs
04-20 00:21 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
04-20 00:21 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-20 00:21 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
04-20 00:21 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-20 00:21 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
04-20 00:21 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-20 00:21 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
04-20 00:21 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-20 00:21 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
04-20 00:21 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-20 00:21 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
04-20 00:21 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-20 00:21 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
04-20 00:21 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-20 00:21 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
04-20 00:21 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-20 00:21 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
04-20 00:21 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-20 00:21 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
04-20 00:21 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-20 00:21 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Studio CD
04-20 00:21 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-20 00:21 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Studio CD
04-20 00:21 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-20 00:21 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
04-20 00:21 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-20 00:21 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
04-20 00:21 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-20 00:21 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
04-20 00:21 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-20 00:21 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
04-20 00:21 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-20 00:21 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
04-20 00:21 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-20 00:21 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
04-20 00:21 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-20 00:21 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
04-20 00:21 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-20 00:21 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
04-20 00:21 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-20 00:21 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
04-20 00:21 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-20 00:21 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
04-20 00:21 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-20 00:21 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Studio CD
04-20 00:21 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-20 00:21 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Studio CD
04-20 00:21 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-20 00:21 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
04-20 00:21 DEBUG  Distro:   parsing info from str=Ubuntu 14.04 LTS "Trusty Tahr" - Release amd64 (20140417)
04-20 00:21 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '14.04', 'build': '20140417', 'codename': 'Trusty Tahr', 'arch': 'amd64'}
04-20 00:21 INFO   Distro: Found a valid CD for Ubuntu: G:\
04-20 00:21 INFO   root: Running the uninstaller...
04-20 00:21 INFO   CommonBackend: This is the uninstaller running
04-20 00:21 DEBUG  WindowsFrontend: __init__...
04-20 00:21 DEBUG  WindowsFrontend: on_init...
04-20 00:21 INFO   WinuiPage: appname=wubi, localedir=C:\Users\kok\AppData\Local\Temp\pyl3729.tmp\translations, languages=['en_US', 'en']
04-20 00:21 INFO   root: Received settings
04-20 00:21 INFO   WinuiPage: appname=wubi, localedir=C:\Users\kok\AppData\Local\Temp\pyl3729.tmp\translations, languages=['en_US', 'en']
04-20 00:21 DEBUG  TaskList: # Running tasklist...
04-20 00:21 DEBUG  TaskList: ## Running Remove bootloader entry...
04-20 00:21 DEBUG  WindowsBackend: Could not find bcd id
04-20 00:21 DEBUG  WindowsBackend: undo_bootini C:
04-20 00:21 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 805058.425781 mb free ntfs)
04-20 00:21 DEBUG  WindowsBackend: undo_bootini D:
04-20 00:21 DEBUG  WindowsBackend: undo_configsys Drive(D: hd 2981.01953125 mb free ntfs)
04-20 00:21 DEBUG  WindowsBackend: undo_bootini G:
04-20 00:21 DEBUG  WindowsBackend: undo_configsys Drive(G: removable 931.5625 mb free fat)
04-20 00:21 DEBUG  TaskList: ## Finished Remove bootloader entry
04-20 00:21 DEBUG  TaskList: ## Running Remove target dir...
04-20 00:21 DEBUG  CommonBackend: Deleting C:\ubuntu
04-20 00:21 DEBUG  TaskList: ## Finished Remove target dir
04-20 00:21 DEBUG  TaskList: ## Running Remove registry key...
04-20 00:21 DEBUG  TaskList: ## Finished Remove registry key
04-20 00:21 DEBUG  TaskList: # Finished tasklist
04-20 00:21 INFO   root: Almost finished uninstalling
04-20 00:21 INFO   WinuiPage: appname=wubi, localedir=C:\Users\kok\AppData\Local\Temp\pyl3729.tmp\translations, languages=['en_US', 'en']
04-20 00:21 INFO   root: Finished uninstallation
04-20 00:21 DEBUG  root: application.quit
04-20 00:21 DEBUG  WindowsFrontend: frontend.quit
04-20 00:21 DEBUG  WindowsFrontend: frontend.on_quit
04-20 00:21 DEBUG  root: application.on_quit
04-20 00:21 INFO   root: sys.exit
04-20 00:25 INFO   root: === wubi 14.04 rev286 ===
04-20 00:25 DEBUG  root: Logfile is c:\users\kok\appdata\local\temp\wubi-14.04-rev286.log
04-20 00:25 DEBUG  root: sys.argv = ['main.pyo', '--exefile="G:\\wubi.exe"']
04-20 00:25 DEBUG  CommonBackend: data_dir=C:\Users\kok\AppData\Local\Temp\pyl871F.tmp\data
04-20 00:25 DEBUG  WindowsBackend: 7z=C:\Users\kok\AppData\Local\Temp\pyl871F.tmp\bin\7z.exe
04-20 00:25 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
04-20 00:25 DEBUG  CommonBackend: Fetching basic info...
04-20 00:25 DEBUG  CommonBackend: original_exe=G:\wubi.exe
04-20 00:25 DEBUG  CommonBackend: platform=win32
04-20 00:25 DEBUG  CommonBackend: osname=nt
04-20 00:25 DEBUG  CommonBackend: language=en_MY
04-20 00:25 DEBUG  CommonBackend: encoding=cp950
04-20 00:25 DEBUG  WindowsBackend: arch=amd64
04-20 00:25 DEBUG  CommonBackend: Parsing isolist=C:\Users\kok\AppData\Local\Temp\pyl871F.tmp\data\isolist.ini
04-20 00:25 DEBUG  CommonBackend:   Adding distro Edubuntu-i386
04-20 00:25 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
04-20 00:25 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
04-20 00:25 DEBUG  CommonBackend:   Adding distro Edubuntu-amd64
04-20 00:25 DEBUG  CommonBackend:   Adding distro Ubuntu Studio-amd64
04-20 00:25 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
04-20 00:25 DEBUG  CommonBackend:   Adding distro Lubuntu-i386
04-20 00:25 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
04-20 00:25 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
04-20 00:25 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
04-20 00:25 DEBUG  CommonBackend:   Adding distro Ubuntu Studio-i386
04-20 00:25 DEBUG  CommonBackend:   Adding distro Lubuntu-amd64
04-20 00:25 DEBUG  WindowsBackend: Fetching host info...
04-20 00:25 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
04-20 00:25 DEBUG  WindowsBackend: windows version=vista
04-20 00:25 DEBUG  WindowsBackend: windows_version2=Windows 8.1 Single Language
04-20 00:25 DEBUG  WindowsBackend: windows_sp=None
04-20 00:25 DEBUG  WindowsBackend: windows_build=9600
04-20 00:25 DEBUG  WindowsBackend: gmt=8
04-20 00:25 DEBUG  WindowsBackend: country=MY
04-20 00:25 DEBUG  WindowsBackend: timezone=Asia/Kuala_Lumpur
04-20 00:25 DEBUG  WindowsBackend: windows_username=yippie
04-20 00:25 DEBUG  WindowsBackend: user_full_name=yippie
04-20 00:25 DEBUG  WindowsBackend: user_directory=C:\Users\kok
04-20 00:25 DEBUG  WindowsBackend: windows_language_code=1033
04-20 00:25 DEBUG  WindowsBackend: windows_language=English
04-20 00:25 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM) i7-3632QM CPU @ 2.20GHz
04-20 00:25 DEBUG  WindowsBackend: bootloader=vista
04-20 00:25 DEBUG  WindowsBackend: system_drive=Drive(C: hd 806948.277344 mb free ntfs)
04-20 00:25 DEBUG  WindowsBackend: drive=Drive(C: hd 806948.277344 mb free ntfs)
04-20 00:25 DEBUG  WindowsBackend: drive=Drive(D: hd 2981.01953125 mb free ntfs)
04-20 00:25 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free )
04-20 00:25 DEBUG  WindowsBackend: drive=Drive(G: removable 931.5625 mb free fat)
04-20 00:25 DEBUG  WindowsBackend: uninstaller_path=None
04-20 00:25 DEBUG  WindowsBackend: previous_target_dir=None
04-20 00:25 DEBUG  WindowsBackend: previous_distro_name=None
04-20 00:25 DEBUG  WindowsBackend: keyboard_id=67716105
04-20 00:25 DEBUG  WindowsBackend: keyboard_layout=us
04-20 00:25 DEBUG  WindowsBackend: keyboard_variant=
04-20 00:25 DEBUG  CommonBackend: python locale=('en_MY', 'cp950')
04-20 00:25 DEBUG  CommonBackend: locale=en_US.UTF-8
04-20 00:25 DEBUG  WindowsBackend: total_memory_mb=3985.2734375
04-20 00:25 DEBUG  CommonBackend: Searching ISOs on USB devices
04-20 00:25 DEBUG  CommonBackend: Searching for local CDs
04-20 00:25 DEBUG  Distro:   checking whether C:\Users\kok\AppData\Local\Temp\pyl871F.tmp is a valid Ubuntu CD
04-20 00:25 DEBUG  Distro:     does not contain C:\Users\kok\AppData\Local\Temp\pyl871F.tmp\casper\filesystem.squashfs
04-20 00:25 DEBUG  Distro:   checking whether C:\Users\kok\AppData\Local\Temp\pyl871F.tmp is a valid Ubuntu CD
04-20 00:25 DEBUG  Distro:     does not contain C:\Users\kok\AppData\Local\Temp\pyl871F.tmp\casper\filesystem.squashfs
04-20 00:25 DEBUG  Distro:   checking whether C:\Users\kok\AppData\Local\Temp\pyl871F.tmp is a valid Kubuntu CD
04-20 00:25 DEBUG  Distro:     does not contain C:\Users\kok\AppData\Local\Temp\pyl871F.tmp\casper\filesystem.squashfs
04-20 00:25 DEBUG  Distro:   checking whether C:\Users\kok\AppData\Local\Temp\pyl871F.tmp is a valid Kubuntu CD
04-20 00:25 DEBUG  Distro:     does not contain C:\Users\kok\AppData\Local\Temp\pyl871F.tmp\casper\filesystem.squashfs
04-20 00:25 DEBUG  Distro:   checking whether C:\Users\kok\AppData\Local\Temp\pyl871F.tmp is a valid Mythbuntu CD
04-20 00:25 DEBUG  Distro:     does not contain C:\Users\kok\AppData\Local\Temp\pyl871F.tmp\casper\filesystem.squashfs
04-20 00:25 DEBUG  Distro:   checking whether C:\Users\kok\AppData\Local\Temp\pyl871F.tmp is a valid Mythbuntu CD
04-20 00:25 DEBUG  Distro:     does not contain C:\Users\kok\AppData\Local\Temp\pyl871F.tmp\casper\filesystem.squashfs
04-20 00:25 DEBUG  Distro:   checking whether C:\Users\kok\AppData\Local\Temp\pyl871F.tmp is a valid Edubuntu CD
04-20 00:25 DEBUG  Distro:     does not contain C:\Users\kok\AppData\Local\Temp\pyl871F.tmp\casper\filesystem.squashfs
04-20 00:25 DEBUG  Distro:   checking whether C:\Users\kok\AppData\Local\Temp\pyl871F.tmp is a valid Edubuntu CD
04-20 00:25 DEBUG  Distro:     does not contain C:\Users\kok\AppData\Local\Temp\pyl871F.tmp\casper\filesystem.squashfs
04-20 00:25 DEBUG  Distro:   checking whether C:\Users\kok\AppData\Local\Temp\pyl871F.tmp is a valid Lubuntu CD
04-20 00:25 DEBUG  Distro:     does not contain C:\Users\kok\AppData\Local\Temp\pyl871F.tmp\casper\filesystem.squashfs
04-20 00:25 DEBUG  Distro:   checking whether C:\Users\kok\AppData\Local\Temp\pyl871F.tmp is a valid Lubuntu CD
04-20 00:25 DEBUG  Distro:     does not contain C:\Users\kok\AppData\Local\Temp\pyl871F.tmp\casper\filesystem.squashfs
04-20 00:25 DEBUG  Distro:   checking whether C:\Users\kok\AppData\Local\Temp\pyl871F.tmp is a valid Ubuntu Studio CD
04-20 00:25 DEBUG  Distro:     does not contain C:\Users\kok\AppData\Local\Temp\pyl871F.tmp\casper\filesystem.squashfs
04-20 00:25 DEBUG  Distro:   checking whether C:\Users\kok\AppData\Local\Temp\pyl871F.tmp is a valid Ubuntu Studio CD
04-20 00:25 DEBUG  Distro:     does not contain C:\Users\kok\AppData\Local\Temp\pyl871F.tmp\casper\filesystem.squashfs
04-20 00:25 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
04-20 00:25 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-20 00:25 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
04-20 00:25 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-20 00:25 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
04-20 00:25 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-20 00:25 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
04-20 00:25 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-20 00:25 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
04-20 00:25 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-20 00:25 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
04-20 00:25 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-20 00:25 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
04-20 00:25 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-20 00:25 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
04-20 00:25 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-20 00:25 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
04-20 00:25 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-20 00:25 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
04-20 00:25 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-20 00:25 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Studio CD
04-20 00:25 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-20 00:25 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Studio CD
04-20 00:25 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-20 00:25 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
04-20 00:25 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-20 00:25 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
04-20 00:25 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-20 00:25 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
04-20 00:25 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-20 00:25 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
04-20 00:25 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-20 00:25 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
04-20 00:25 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-20 00:25 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
04-20 00:25 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-20 00:25 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
04-20 00:25 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-20 00:25 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
04-20 00:25 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-20 00:25 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
04-20 00:25 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-20 00:25 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
04-20 00:25 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-20 00:25 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Studio CD
04-20 00:25 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-20 00:25 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Studio CD
04-20 00:25 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-20 00:25 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
04-20 00:25 DEBUG  Distro:   parsing info from str=Ubuntu 14.04 LTS "Trusty Tahr" - Release amd64 (20140417)
04-20 00:25 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '14.04', 'build': '20140417', 'codename': 'Trusty Tahr', 'arch': 'amd64'}
04-20 00:25 INFO   Distro: Found a valid CD for Ubuntu: G:\
04-20 00:25 INFO   root: Running the CD menu...
04-20 00:25 DEBUG  WindowsFrontend: __init__...
04-20 00:25 DEBUG  WindowsFrontend: on_init...
04-20 00:25 INFO   WinuiPage: appname=wubi, localedir=C:\Users\kok\AppData\Local\Temp\pyl871F.tmp\translations, languages=['en_US', 'en']
04-20 00:25 INFO   WinuiPage: appname=wubi, localedir=C:\Users\kok\AppData\Local\Temp\pyl871F.tmp\translations, languages=['en_US', 'en']
04-20 00:25 INFO   WindowsFrontend: Operation cancelled
04-20 00:25 DEBUG  WindowsFrontend: frontend.quit
04-20 00:25 DEBUG  WindowsFrontend: frontend.on_quit
04-20 00:25 DEBUG  root: application.on_quit
04-20 00:25 INFO   root: sys.exit
04-20 00:25 INFO   root: === wubi 14.04 rev286 ===
04-20 00:25 DEBUG  root: Logfile is c:\users\kok\appdata\local\temp\wubi-14.04-rev286.log
04-20 00:25 DEBUG  root: sys.argv = ['main.pyo', '--exefile="G:\\wubi.exe"']
04-20 00:25 DEBUG  CommonBackend: data_dir=C:\Users\kok\AppData\Local\Temp\pylFA8A.tmp\data
04-20 00:25 DEBUG  WindowsBackend: 7z=C:\Users\kok\AppData\Local\Temp\pylFA8A.tmp\bin\7z.exe
04-20 00:25 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
04-20 00:25 DEBUG  CommonBackend: Fetching basic info...
04-20 00:25 DEBUG  CommonBackend: original_exe=G:\wubi.exe
04-20 00:25 DEBUG  CommonBackend: platform=win32
04-20 00:25 DEBUG  CommonBackend: osname=nt
04-20 00:25 DEBUG  CommonBackend: language=en_MY
04-20 00:25 DEBUG  CommonBackend: encoding=cp950
04-20 00:25 DEBUG  WindowsBackend: arch=amd64
04-20 00:25 DEBUG  CommonBackend: Parsing isolist=C:\Users\kok\AppData\Local\Temp\pylFA8A.tmp\data\isolist.ini
04-20 00:25 DEBUG  CommonBackend:   Adding distro Edubuntu-i386
04-20 00:25 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
04-20 00:25 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
04-20 00:25 DEBUG  CommonBackend:   Adding distro Edubuntu-amd64
04-20 00:25 DEBUG  CommonBackend:   Adding distro Ubuntu Studio-amd64
04-20 00:25 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
04-20 00:25 DEBUG  CommonBackend:   Adding distro Lubuntu-i386
04-20 00:25 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
04-20 00:25 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
04-20 00:25 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
04-20 00:25 DEBUG  CommonBackend:   Adding distro Ubuntu Studio-i386
04-20 00:25 DEBUG  CommonBackend:   Adding distro Lubuntu-amd64
04-20 00:25 DEBUG  WindowsBackend: Fetching host info...
04-20 00:25 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
04-20 00:25 DEBUG  WindowsBackend: windows version=vista
04-20 00:25 DEBUG  WindowsBackend: windows_version2=Windows 8.1 Single Language
04-20 00:25 DEBUG  WindowsBackend: windows_sp=None
04-20 00:25 DEBUG  WindowsBackend: windows_build=9600
04-20 00:25 DEBUG  WindowsBackend: gmt=8
04-20 00:25 DEBUG  WindowsBackend: country=MY
04-20 00:25 DEBUG  WindowsBackend: timezone=Asia/Kuala_Lumpur
04-20 00:25 DEBUG  WindowsBackend: windows_username=yippie
04-20 00:25 DEBUG  WindowsBackend: user_full_name=yippie
04-20 00:25 DEBUG  WindowsBackend: user_directory=C:\Users\kok
04-20 00:25 DEBUG  WindowsBackend: windows_language_code=1033
04-20 00:25 DEBUG  WindowsBackend: windows_language=English
04-20 00:25 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM) i7-3632QM CPU @ 2.20GHz
04-20 00:25 DEBUG  WindowsBackend: bootloader=vista
04-20 00:25 DEBUG  WindowsBackend: system_drive=Drive(C: hd 806939.5 mb free ntfs)
04-20 00:25 DEBUG  WindowsBackend: drive=Drive(C: hd 806939.5 mb free ntfs)
04-20 00:25 DEBUG  WindowsBackend: drive=Drive(D: hd 2981.01953125 mb free ntfs)
04-20 00:25 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free )
04-20 00:25 DEBUG  WindowsBackend: drive=Drive(G: removable 931.5625 mb free fat)
04-20 00:25 DEBUG  WindowsBackend: uninstaller_path=None
04-20 00:25 DEBUG  WindowsBackend: previous_target_dir=None
04-20 00:25 DEBUG  WindowsBackend: previous_distro_name=None
04-20 00:25 DEBUG  WindowsBackend: keyboard_id=67716105
04-20 00:25 DEBUG  WindowsBackend: keyboard_layout=us
04-20 00:25 DEBUG  WindowsBackend: keyboard_variant=
04-20 00:25 DEBUG  CommonBackend: python locale=('en_MY', 'cp950')
04-20 00:25 DEBUG  CommonBackend: locale=en_US.UTF-8
04-20 00:25 DEBUG  WindowsBackend: total_memory_mb=3985.2734375
04-20 00:25 DEBUG  CommonBackend: Searching ISOs on USB devices
04-20 00:25 DEBUG  CommonBackend: Searching for local CDs
04-20 00:25 DEBUG  Distro:   checking whether C:\Users\kok\AppData\Local\Temp\pylFA8A.tmp is a valid Ubuntu CD
04-20 00:25 DEBUG  Distro:     does not contain C:\Users\kok\AppData\Local\Temp\pylFA8A.tmp\casper\filesystem.squashfs
04-20 00:25 DEBUG  Distro:   checking whether C:\Users\kok\AppData\Local\Temp\pylFA8A.tmp is a valid Ubuntu CD
04-20 00:25 DEBUG  Distro:     does not contain C:\Users\kok\AppData\Local\Temp\pylFA8A.tmp\casper\filesystem.squashfs
04-20 00:25 DEBUG  Distro:   checking whether C:\Users\kok\AppData\Local\Temp\pylFA8A.tmp is a valid Kubuntu CD
04-20 00:25 DEBUG  Distro:     does not contain C:\Users\kok\AppData\Local\Temp\pylFA8A.tmp\casper\filesystem.squashfs
04-20 00:25 DEBUG  Distro:   checking whether C:\Users\kok\AppData\Local\Temp\pylFA8A.tmp is a valid Kubuntu CD
04-20 00:25 DEBUG  Distro:     does not contain C:\Users\kok\AppData\Local\Temp\pylFA8A.tmp\casper\filesystem.squashfs
04-20 00:25 DEBUG  Distro:   checking whether C:\Users\kok\AppData\Local\Temp\pylFA8A.tmp is a valid Mythbuntu CD
04-20 00:25 DEBUG  Distro:     does not contain C:\Users\kok\AppData\Local\Temp\pylFA8A.tmp\casper\filesystem.squashfs
04-20 00:25 DEBUG  Distro:   checking whether C:\Users\kok\AppData\Local\Temp\pylFA8A.tmp is a valid Mythbuntu CD
04-20 00:25 DEBUG  Distro:     does not contain C:\Users\kok\AppData\Local\Temp\pylFA8A.tmp\casper\filesystem.squashfs
04-20 00:25 DEBUG  Distro:   checking whether C:\Users\kok\AppData\Local\Temp\pylFA8A.tmp is a valid Edubuntu CD
04-20 00:25 DEBUG  Distro:     does not contain C:\Users\kok\AppData\Local\Temp\pylFA8A.tmp\casper\filesystem.squashfs
04-20 00:25 DEBUG  Distro:   checking whether C:\Users\kok\AppData\Local\Temp\pylFA8A.tmp is a valid Edubuntu CD
04-20 00:25 DEBUG  Distro:     does not contain C:\Users\kok\AppData\Local\Temp\pylFA8A.tmp\casper\filesystem.squashfs
04-20 00:25 DEBUG  Distro:   checking whether C:\Users\kok\AppData\Local\Temp\pylFA8A.tmp is a valid Lubuntu CD
04-20 00:25 DEBUG  Distro:     does not contain C:\Users\kok\AppData\Local\Temp\pylFA8A.tmp\casper\filesystem.squashfs
04-20 00:25 DEBUG  Distro:   checking whether C:\Users\kok\AppData\Local\Temp\pylFA8A.tmp is a valid Lubuntu CD
04-20 00:25 DEBUG  Distro:     does not contain C:\Users\kok\AppData\Local\Temp\pylFA8A.tmp\casper\filesystem.squashfs
04-20 00:25 DEBUG  Distro:   checking whether C:\Users\kok\AppData\Local\Temp\pylFA8A.tmp is a valid Ubuntu Studio CD
04-20 00:25 DEBUG  Distro:     does not contain C:\Users\kok\AppData\Local\Temp\pylFA8A.tmp\casper\filesystem.squashfs
04-20 00:25 DEBUG  Distro:   checking whether C:\Users\kok\AppData\Local\Temp\pylFA8A.tmp is a valid Ubuntu Studio CD
04-20 00:25 DEBUG  Distro:     does not contain C:\Users\kok\AppData\Local\Temp\pylFA8A.tmp\casper\filesystem.squashfs
04-20 00:25 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
04-20 00:25 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-20 00:25 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
04-20 00:25 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-20 00:25 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
04-20 00:25 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-20 00:25 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
04-20 00:25 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-20 00:25 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
04-20 00:25 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-20 00:25 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
04-20 00:25 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-20 00:25 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
04-20 00:25 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-20 00:25 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
04-20 00:25 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-20 00:25 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
04-20 00:25 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-20 00:25 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
04-20 00:25 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-20 00:25 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Studio CD
04-20 00:25 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-20 00:25 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Studio CD
04-20 00:25 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-20 00:25 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
04-20 00:25 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-20 00:25 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
04-20 00:25 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-20 00:25 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
04-20 00:25 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-20 00:25 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
04-20 00:25 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-20 00:25 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
04-20 00:25 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-20 00:25 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
04-20 00:25 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-20 00:25 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
04-20 00:25 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-20 00:25 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
04-20 00:25 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-20 00:25 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
04-20 00:25 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-20 00:25 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
04-20 00:25 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-20 00:25 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Studio CD
04-20 00:25 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-20 00:25 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Studio CD
04-20 00:25 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-20 00:25 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
04-20 00:25 DEBUG  Distro:   parsing info from str=Ubuntu 14.04 LTS "Trusty Tahr" - Release amd64 (20140417)
04-20 00:25 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '14.04', 'build': '20140417', 'codename': 'Trusty Tahr', 'arch': 'amd64'}
04-20 00:25 INFO   Distro: Found a valid CD for Ubuntu: G:\
04-20 00:25 INFO   root: Running the CD menu...
04-20 00:25 DEBUG  WindowsFrontend: __init__...
04-20 00:25 DEBUG  WindowsFrontend: on_init...
04-20 00:25 INFO   WinuiPage: appname=wubi, localedir=C:\Users\kok\AppData\Local\Temp\pylFA8A.tmp\translations, languages=['en_US', 'en']
04-20 00:25 INFO   WinuiPage: appname=wubi, localedir=C:\Users\kok\AppData\Local\Temp\pylFA8A.tmp\translations, languages=['en_US', 'en']
04-20 00:26 INFO   root: CD menu finished
04-20 00:26 INFO   root: Rebooting
04-20 00:26 DEBUG  TaskList: # Running tasklist...
04-20 00:26 DEBUG  TaskList: ## Running reboot...
04-20 00:26 DEBUG  TaskList: ## Finished reboot
04-20 00:26 DEBUG  TaskList: # Finished tasklist
04-20 00:26 DEBUG  root: application.quit
04-20 00:26 DEBUG  WindowsFrontend: frontend.quit
04-20 00:26 DEBUG  WindowsFrontend: frontend.on_quit
04-20 00:26 DEBUG  root: application.on_quit
04-20 00:26 INFO   root: sys.exit
04-20 00:27 INFO   root: === wubi 14.04 rev286 ===
04-20 00:27 DEBUG  root: Logfile is c:\users\kok\appdata\local\temp\wubi-14.04-rev286.log
04-20 00:27 DEBUG  root: sys.argv = ['main.pyo', '--exefile="G:\\wubi.exe"']
04-20 00:27 DEBUG  CommonBackend: data_dir=C:\Users\kok\AppData\Local\Temp\pylEF32.tmp\data
04-20 00:27 DEBUG  WindowsBackend: 7z=C:\Users\kok\AppData\Local\Temp\pylEF32.tmp\bin\7z.exe
04-20 00:27 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
04-20 00:27 DEBUG  CommonBackend: Fetching basic info...
04-20 00:27 DEBUG  CommonBackend: original_exe=G:\wubi.exe
04-20 00:27 DEBUG  CommonBackend: platform=win32
04-20 00:27 DEBUG  CommonBackend: osname=nt
04-20 00:27 DEBUG  CommonBackend: language=en_MY
04-20 00:27 DEBUG  CommonBackend: encoding=cp950
04-20 00:27 DEBUG  WindowsBackend: arch=amd64
04-20 00:27 DEBUG  CommonBackend: Parsing isolist=C:\Users\kok\AppData\Local\Temp\pylEF32.tmp\data\isolist.ini
04-20 00:27 DEBUG  CommonBackend:   Adding distro Edubuntu-i386
04-20 00:27 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
04-20 00:27 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
04-20 00:27 DEBUG  CommonBackend:   Adding distro Edubuntu-amd64
04-20 00:27 DEBUG  CommonBackend:   Adding distro Ubuntu Studio-amd64
04-20 00:27 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
04-20 00:27 DEBUG  CommonBackend:   Adding distro Lubuntu-i386
04-20 00:27 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
04-20 00:27 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
04-20 00:27 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
04-20 00:27 DEBUG  CommonBackend:   Adding distro Ubuntu Studio-i386
04-20 00:27 DEBUG  CommonBackend:   Adding distro Lubuntu-amd64
04-20 00:27 DEBUG  WindowsBackend: Fetching host info...
04-20 00:27 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
04-20 00:27 DEBUG  WindowsBackend: windows version=vista
04-20 00:27 DEBUG  WindowsBackend: windows_version2=Windows 8.1 Single Language
04-20 00:27 DEBUG  WindowsBackend: windows_sp=None
04-20 00:27 DEBUG  WindowsBackend: windows_build=9600
04-20 00:27 DEBUG  WindowsBackend: gmt=8
04-20 00:27 DEBUG  WindowsBackend: country=MY
04-20 00:27 DEBUG  WindowsBackend: timezone=Asia/Kuala_Lumpur
04-20 00:27 DEBUG  WindowsBackend: windows_username=yippie
04-20 00:27 DEBUG  WindowsBackend: user_full_name=yippie
04-20 00:27 DEBUG  WindowsBackend: user_directory=C:\Users\kok
04-20 00:27 DEBUG  WindowsBackend: windows_language_code=1033
04-20 00:27 DEBUG  WindowsBackend: windows_language=English
04-20 00:27 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM) i7-3632QM CPU @ 2.20GHz
04-20 00:27 DEBUG  WindowsBackend: bootloader=vista
04-20 00:27 DEBUG  WindowsBackend: system_drive=Drive(C: hd 806947.976563 mb free ntfs)
04-20 00:27 DEBUG  WindowsBackend: drive=Drive(C: hd 806947.976563 mb free ntfs)
04-20 00:27 DEBUG  WindowsBackend: drive=Drive(D: hd 2981.01953125 mb free ntfs)
04-20 00:27 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free )
04-20 00:27 DEBUG  WindowsBackend: drive=Drive(G: removable 931.5625 mb free fat)
04-20 00:27 DEBUG  WindowsBackend: uninstaller_path=None
04-20 00:27 DEBUG  WindowsBackend: previous_target_dir=None
04-20 00:27 DEBUG  WindowsBackend: previous_distro_name=None
04-20 00:27 DEBUG  WindowsBackend: keyboard_id=67716105
04-20 00:27 DEBUG  WindowsBackend: keyboard_layout=us
04-20 00:27 DEBUG  WindowsBackend: keyboard_variant=
04-20 00:27 DEBUG  CommonBackend: python locale=('en_MY', 'cp950')
04-20 00:27 DEBUG  CommonBackend: locale=en_US.UTF-8
04-20 00:27 DEBUG  WindowsBackend: total_memory_mb=3985.2734375
04-20 00:27 DEBUG  CommonBackend: Searching ISOs on USB devices
04-20 00:27 DEBUG  CommonBackend: Searching for local CDs
04-20 00:27 DEBUG  Distro:   checking whether C:\Users\kok\AppData\Local\Temp\pylEF32.tmp is a valid Ubuntu CD
04-20 00:27 DEBUG  Distro:     does not contain C:\Users\kok\AppData\Local\Temp\pylEF32.tmp\casper\filesystem.squashfs
04-20 00:27 DEBUG  Distro:   checking whether C:\Users\kok\AppData\Local\Temp\pylEF32.tmp is a valid Ubuntu CD
04-20 00:27 DEBUG  Distro:     does not contain C:\Users\kok\AppData\Local\Temp\pylEF32.tmp\casper\filesystem.squashfs
04-20 00:27 DEBUG  Distro:   checking whether C:\Users\kok\AppData\Local\Temp\pylEF32.tmp is a valid Kubuntu CD
04-20 00:27 DEBUG  Distro:     does not contain C:\Users\kok\AppData\Local\Temp\pylEF32.tmp\casper\filesystem.squashfs
04-20 00:27 DEBUG  Distro:   checking whether C:\Users\kok\AppData\Local\Temp\pylEF32.tmp is a valid Kubuntu CD
04-20 00:27 DEBUG  Distro:     does not contain C:\Users\kok\AppData\Local\Temp\pylEF32.tmp\casper\filesystem.squashfs
04-20 00:27 DEBUG  Distro:   checking whether C:\Users\kok\AppData\Local\Temp\pylEF32.tmp is a valid Mythbuntu CD
04-20 00:27 DEBUG  Distro:     does not contain C:\Users\kok\AppData\Local\Temp\pylEF32.tmp\casper\filesystem.squashfs
04-20 00:27 DEBUG  Distro:   checking whether C:\Users\kok\AppData\Local\Temp\pylEF32.tmp is a valid Mythbuntu CD
04-20 00:27 DEBUG  Distro:     does not contain C:\Users\kok\AppData\Local\Temp\pylEF32.tmp\casper\filesystem.squashfs
04-20 00:27 DEBUG  Distro:   checking whether C:\Users\kok\AppData\Local\Temp\pylEF32.tmp is a valid Edubuntu CD
04-20 00:27 DEBUG  Distro:     does not contain C:\Users\kok\AppData\Local\Temp\pylEF32.tmp\casper\filesystem.squashfs
04-20 00:27 DEBUG  Distro:   checking whether C:\Users\kok\AppData\Local\Temp\pylEF32.tmp is a valid Edubuntu CD
04-20 00:27 DEBUG  Distro:     does not contain C:\Users\kok\AppData\Local\Temp\pylEF32.tmp\casper\filesystem.squashfs
04-20 00:27 DEBUG  Distro:   checking whether C:\Users\kok\AppData\Local\Temp\pylEF32.tmp is a valid Lubuntu CD
04-20 00:27 DEBUG  Distro:     does not contain C:\Users\kok\AppData\Local\Temp\pylEF32.tmp\casper\filesystem.squashfs
04-20 00:27 DEBUG  Distro:   checking whether C:\Users\kok\AppData\Local\Temp\pylEF32.tmp is a valid Lubuntu CD
04-20 00:27 DEBUG  Distro:     does not contain C:\Users\kok\AppData\Local\Temp\pylEF32.tmp\casper\filesystem.squashfs
04-20 00:27 DEBUG  Distro:   checking whether C:\Users\kok\AppData\Local\Temp\pylEF32.tmp is a valid Ubuntu Studio CD
04-20 00:27 DEBUG  Distro:     does not contain C:\Users\kok\AppData\Local\Temp\pylEF32.tmp\casper\filesystem.squashfs
04-20 00:27 DEBUG  Distro:   checking whether C:\Users\kok\AppData\Local\Temp\pylEF32.tmp is a valid Ubuntu Studio CD
04-20 00:27 DEBUG  Distro:     does not contain C:\Users\kok\AppData\Local\Temp\pylEF32.tmp\casper\filesystem.squashfs
04-20 00:27 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
04-20 00:27 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-20 00:27 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
04-20 00:27 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-20 00:27 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
04-20 00:27 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-20 00:27 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
04-20 00:27 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-20 00:27 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
04-20 00:27 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-20 00:27 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
04-20 00:27 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-20 00:27 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
04-20 00:27 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-20 00:27 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
04-20 00:27 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-20 00:27 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
04-20 00:27 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-20 00:27 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
04-20 00:27 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-20 00:27 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Studio CD
04-20 00:27 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-20 00:27 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Studio CD
04-20 00:27 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-20 00:27 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
04-20 00:27 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-20 00:27 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
04-20 00:27 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-20 00:27 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
04-20 00:27 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-20 00:27 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
04-20 00:27 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-20 00:27 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
04-20 00:27 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-20 00:27 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
04-20 00:27 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-20 00:27 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
04-20 00:27 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-20 00:27 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
04-20 00:27 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-20 00:27 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
04-20 00:27 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-20 00:27 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
04-20 00:27 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-20 00:27 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Studio CD
04-20 00:27 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-20 00:27 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Studio CD
04-20 00:27 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-20 00:27 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
04-20 00:27 DEBUG  Distro:   parsing info from str=Ubuntu 14.04 LTS "Trusty Tahr" - Release amd64 (20140417)
04-20 00:27 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '14.04', 'build': '20140417', 'codename': 'Trusty Tahr', 'arch': 'amd64'}
04-20 00:27 INFO   Distro: Found a valid CD for Ubuntu: G:\
04-20 00:27 INFO   root: Running the CD menu...
04-20 00:27 DEBUG  WindowsFrontend: __init__...
04-20 00:27 DEBUG  WindowsFrontend: on_init...
04-20 00:27 INFO   WinuiPage: appname=wubi, localedir=C:\Users\kok\AppData\Local\Temp\pylEF32.tmp\translations, languages=['en_US', 'en']
04-20 00:27 INFO   WinuiPage: appname=wubi, localedir=C:\Users\kok\AppData\Local\Temp\pylEF32.tmp\translations, languages=['en_US', 'en']
04-20 00:27 INFO   root: CD menu finished
04-20 00:27 INFO   root: Running the CD boot helper...
04-20 00:27 INFO   WinuiPage: appname=wubi, localedir=C:\Users\kok\AppData\Local\Temp\pylEF32.tmp\translations, languages=['en_US', 'en']
04-20 00:27 INFO   WinuiPage: appname=wubi, localedir=C:\Users\kok\AppData\Local\Temp\pylEF32.tmp\translations, languages=['en_US', 'en']
04-20 00:28 INFO   root: CD boot helper confirmed
04-20 00:28 INFO   WinuiPage: appname=wubi, localedir=C:\Users\kok\AppData\Local\Temp\pylEF32.tmp\translations, languages=['en_US', 'en']
04-20 00:28 DEBUG  TaskList: # Running tasklist...
04-20 00:28 DEBUG  TaskList: ## Running select_target_dir...
04-20 00:28 INFO   WindowsBackend: Installing into C:\ubuntu
04-20 00:28 DEBUG  TaskList: ## Finished select_target_dir
04-20 00:28 DEBUG  TaskList: ## Running create_dir_structure...
04-20 00:28 DEBUG  CommonBackend: Creating dir C:\ubuntu
04-20 00:28 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks
04-20 00:28 DEBUG  CommonBackend: Creating dir C:\ubuntu\install
04-20 00:28 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot
04-20 00:28 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot
04-20 00:28 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot\grub
04-20 00:28 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot\grub
04-20 00:28 DEBUG  TaskList: ## Finished create_dir_structure
04-20 00:28 DEBUG  TaskList: ## Running uncompress_target_dir...
04-20 00:28 DEBUG  TaskList: ## Finished uncompress_target_dir
04-20 00:28 DEBUG  TaskList: ## Running create_uninstaller...
04-20 00:28 DEBUG  WindowsBackend: Copying uninstaller G:\wubi.exe -> C:\ubuntu\uninstall-wubi.exe
04-20 00:28 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString C:\ubuntu\uninstall-wubi.exe
04-20 00:28 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir C:\ubuntu
04-20 00:28 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
04-20 00:28 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon C:\ubuntu\Ubuntu.ico
04-20 00:28 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 14.04-rev286
04-20 00:28 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
04-20 00:28 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com](http://www.ubuntu.com)
04-20 00:28 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
04-20 00:28 DEBUG  TaskList: ## Finished create_uninstaller
04-20 00:28 DEBUG  TaskList: ## Running copy_installation_files...
04-20 00:28 DEBUG  WindowsBackend: Copying C:\Users\kok\AppData\Local\Temp\pylEF32.tmp\data\custom-installation -> C:\ubuntu\install\custom-installation
04-20 00:28 DEBUG  WindowsBackend: Copying C:\Users\kok\AppData\Local\Temp\pylEF32.tmp\winboot -> C:\ubuntu\winboot
04-20 00:28 DEBUG  WindowsBackend: Copying C:\Users\kok\AppData\Local\Temp\pylEF32.tmp\data\images\Ubuntu.ico -> C:\ubuntu\Ubuntu.ico
04-20 00:28 DEBUG  TaskList: ## Finished copy_installation_files
04-20 00:28 DEBUG  TaskList: ## Running use_cd...
04-20 00:28 DEBUG  TaskList: New task copy_file
04-20 00:28 DEBUG  TaskList: ### Running copy_file...
04-20 00:30 DEBUG  TaskList: ### Finished copy_file
04-20 00:30 DEBUG  TaskList: New task check_iso
04-20 00:30 DEBUG  TaskList: ### Running check_iso...
04-20 00:30 DEBUG  CommonBackend: Checking C:\ubuntu\install\installation.iso
04-20 00:30 DEBUG  Distro:   checking Ubuntu ISO C:\ubuntu\install\installation.iso
04-20 00:30 DEBUG  WindowsBackend:   extracting .disk\info from C:\ubuntu\install\installation.iso
04-20 00:30 DEBUG  Distro:   parsing info from str=Ubuntu 14.04 LTS "Trusty Tahr" - Release amd64 (20140417)
04-20 00:30 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '14.04', 'build': '20140417', 'codename': 'Trusty Tahr', 'arch': 'amd64'}
04-20 00:30 INFO   Distro: Found a valid iso for Ubuntu: C:\ubuntu\install\installation.iso
04-20 00:30 DEBUG  TaskList: New task get_metalink
04-20 00:30 DEBUG  TaskList: #### Running get_metalink...
04-20 00:30 DEBUG  downloader: downloading [http://releases.ubuntu.com/14.04/ubuntu-14.04-desktop-amd64.metalink](http://releases.ubuntu.com/14.04/ubuntu-14.04-desktop-amd64.metalink) > C:\ubuntu\install
04-20 00:30 DEBUG  downloader: Download start filename=C:\ubuntu\install\ubuntu-14.04-desktop-amd64.metalink, url=http://releases.ubuntu.com/14.04/ubuntu-14.04-desktop-amd64.metalink, basename=ubuntu-14.04-desktop-amd64.metalink, length=41450, text=None
04-20 00:30 DEBUG  downloader: download finished (read 41450 bytes)
04-20 00:30 DEBUG  downloader: downloading [http://releases.ubuntu.com/14.04/MD5SUMS-metalink](http://releases.ubuntu.com/14.04/MD5SUMS-metalink) > C:\ubuntu\install
04-20 00:30 DEBUG  downloader: Download start filename=C:\ubuntu\install\MD5SUMS-metalink, url=http://releases.ubuntu.com/14.04/MD5SUMS-metalink, basename=MD5SUMS-metalink, length=276, text=None
04-20 00:30 DEBUG  downloader: download finished (read 276 bytes)
04-20 00:30 DEBUG  downloader: downloading [http://releases.ubuntu.com/14.04/MD5SUMS-metalink.gpg](http://releases.ubuntu.com/14.04/MD5SUMS-metalink.gpg) > C:\ubuntu\install
04-20 00:30 DEBUG  downloader: Download start filename=C:\ubuntu\install\MD5SUMS-metalink.gpg, url=http://releases.ubuntu.com/14.04/MD5SUMS-metalink.gpg, basename=MD5SUMS-metalink.gpg, length=198, text=None
04-20 00:30 DEBUG  downloader: download finished (read 198 bytes)
04-20 00:30 INFO   saplog: Verified a signature from ID:'46181433FBB75451'.
04-20 00:30 INFO   saplog: Checking block bindings..
04-20 00:30 INFO   saplog: Key verified successfully.
04-20 00:30 DEBUG  CommonBackend: metalink md5sums:
c7522c09a4beadfd0969c8338249f126 *ubuntu-14.04-desktop-amd64.metalink
96c7de9d1c56ddf7c0f43888ab9af575 *ubuntu-14.04-desktop-i386.metalink
ac3206dd1eb05205e193767314683520 *ubuntu-14.04-server-amd64.metalink
d1c27a6e4c3dfc5d9f5ef75e46d78ca6 *ubuntu-14.04-server-i386.metalink


04-20 00:30 ERROR  CommonBackend: The md5 of the metalink does match
04-20 00:30 ERROR  CommonBackend: Cannot authenticate the metalink file, it might be corrupt
None
04-20 00:30 DEBUG  TaskList: #### Finished get_metalink
04-20 00:30 DEBUG  TaskList: New task get_file_md5
04-20 00:30 DEBUG  TaskList: #### Running get_file_md5...
04-20 00:30 DEBUG  TaskList: #### Finished get_file_md5
04-20 00:30 ERROR  CommonBackend: Invalid md5 for ISO C:\ubuntu\install\installation.iso (dccff28314d9ae4ed262cfc6f35e5153 != 6b4ad02cbf6bd7baf34b9ffa2fbe6fb5)
None
04-20 00:30 DEBUG  TaskList: ### Finished check_iso
04-20 00:30 DEBUG  TaskList: ## Finished use_cd
04-20 00:30 DEBUG  TaskList: ## Running extract_kernel...
04-20 00:30 ERROR  TaskList: Could not retrieve the required installation files
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 618, in extract_kernel
Exception: Could not retrieve the required installation files
04-20 00:30 DEBUG  TaskList: # Cancelling tasklist
04-20 00:30 DEBUG  TaskList: # Finished tasklist
04-20 00:30 ERROR  root: Could not retrieve the required installation files
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 58, in run
  File "\lib\wubi\application.py", line 130, in select_task
  File "\lib\wubi\application.py", line 205, in run_cd_menu
  File "\lib\wubi\application.py", line 122, in select_task
  File "\lib\wubi\application.py", line 228, in run_cd_boot
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 618, in extract_kernel
Exception: Could not retrieve the required installation files 
```

---

### Post by pfeiffep on 2014-04-19
Welcome the Linux and the forum!

ASAIK wubi is no longer supported. If your computer will boot from an USB stick you'll probably be able to try Ubuntu by booting that.

Instructions can be found [online]("https://help.ubuntu.com/community/LiveCD")

---

