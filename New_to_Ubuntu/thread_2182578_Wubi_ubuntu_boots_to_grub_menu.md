---
title: "Wubi ubuntu boots to grub menu"
date: 2013-10-21
forum: New to Ubuntu
---

### Post by eashenden on 2013-10-21
So I dual booted windows 7 home premium and ubuntu using wubi, originially I came to a choice between windows 7 and ununtu, and when I choose unbuntu it just booted to a purple screen. Then the exact same thing happened except it said file not found press anything to continue, and now finally it just boots straight to the grub menu and I can't seem to figure out how to fix this booting issue.

[COLOR=#000000]Downloaded: wubi 12.04.3 (ubuntu)[/COLOR]
[COLOR=#000000]OS: windows 7 home premium, ubuntu(wubi)[/COLOR]
[COLOR=#000000]processor: Intel Core i5-3317U CPU @ 1.70GHz[/COLOR]
[COLOR=#000000]RAM: 6GB[/COLOR]
[COLOR=#000000]64-bit

below is a picture of what it goes to when I try to boot it up and the log, I didnt realize until now that you can see me and my friend in the picture :D
[/COLOR][IMG]http://i1332.photobucket.com/albums/w615/eashenden/Mobile%20Uploads/20131021_173135_zps4934135a.jpg[/IMG]
```
10-18 20:37 INFO   root: === wubi 12.04.3 rev279 ===
10-18 20:37 DEBUG  root: Logfile is c:\windows\temp\wubi-12.04.3-rev279.log
10-18 20:37 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\Users\\Eric\\Desktop\\ubuntu\\wubi.exe"']
10-18 20:37 DEBUG  CommonBackend: data_dir=C:\Windows\TEMP\pylD5B5.tmp\data
10-18 20:37 DEBUG  WindowsBackend: 7z=C:\Windows\TEMP\pylD5B5.tmp\bin\7z.exe
10-18 20:37 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
10-18 20:37 DEBUG  CommonBackend: Fetching basic info...
10-18 20:37 DEBUG  CommonBackend: original_exe=C:\Users\Eric\Desktop\ubuntu\wubi.exe
10-18 20:37 DEBUG  CommonBackend: platform=win32
10-18 20:37 DEBUG  CommonBackend: osname=nt
10-18 20:37 DEBUG  CommonBackend: language=en_US
10-18 20:37 DEBUG  CommonBackend: encoding=cp1252
10-18 20:37 DEBUG  WindowsBackend: arch=amd64
10-18 20:37 DEBUG  CommonBackend: Parsing isolist=C:\Windows\TEMP\pylD5B5.tmp\data\isolist.ini
10-18 20:37 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
10-18 20:37 DEBUG  CommonBackend:   Adding distro Edubuntu-i386
10-18 20:37 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
10-18 20:37 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
10-18 20:37 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
10-18 20:37 DEBUG  CommonBackend:   Adding distro Edubuntu-amd64
10-18 20:37 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
10-18 20:37 DEBUG  CommonBackend:   Adding distro Lubuntu-i386
10-18 20:37 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
10-18 20:37 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
10-18 20:37 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
10-18 20:37 DEBUG  CommonBackend:   Adding distro Lubuntu-amd64
10-18 20:37 DEBUG  WindowsBackend: Fetching host info...
10-18 20:37 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
10-18 20:37 DEBUG  WindowsBackend: windows version=vista
10-18 20:37 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium
10-18 20:37 DEBUG  WindowsBackend: windows_sp=None
10-18 20:37 DEBUG  WindowsBackend: windows_build=7601
10-18 20:37 DEBUG  WindowsBackend: gmt=-5
10-18 20:37 DEBUG  WindowsBackend: country=US
10-18 20:37 DEBUG  WindowsBackend: timezone=America/New_York
10-18 20:37 DEBUG  WindowsBackend: windows_username=Eric
10-18 20:37 DEBUG  WindowsBackend: user_full_name=Eric
10-18 20:37 DEBUG  WindowsBackend: user_directory=C:\Users\Eric
10-18 20:37 DEBUG  WindowsBackend: windows_language_code=1033
10-18 20:37 DEBUG  WindowsBackend: windows_language=English
10-18 20:37 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM) i5-3317U CPU @ 1.70GHz
10-18 20:37 DEBUG  WindowsBackend: bootloader=vista
10-18 20:37 DEBUG  WindowsBackend: system_drive=Drive(C: hd 375748.375 mb free ntfs)
10-18 20:37 DEBUG  WindowsBackend: drive=Drive(C: hd 375748.375 mb free ntfs)
10-18 20:37 DEBUG  WindowsBackend: drive=Drive(D: cd 0.0 mb free )
10-18 20:37 DEBUG  WindowsBackend: uninstaller_path=None
10-18 20:37 DEBUG  WindowsBackend: previous_target_dir=None
10-18 20:37 DEBUG  WindowsBackend: previous_distro_name=None
10-18 20:37 DEBUG  WindowsBackend: keyboard_id=67699721
10-18 20:37 DEBUG  WindowsBackend: keyboard_layout=us
10-18 20:37 DEBUG  WindowsBackend: keyboard_variant=
10-18 20:37 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
10-18 20:37 DEBUG  CommonBackend: locale=en_US.UTF-8
10-18 20:37 DEBUG  WindowsBackend: total_memory_mb=4095.99999905
10-18 20:37 DEBUG  CommonBackend: Searching ISOs on USB devices
10-18 20:37 DEBUG  CommonBackend: Searching for local CDs
10-18 20:37 DEBUG  Distro:   checking whether C:\Windows\TEMP\pylD5B5.tmp is a valid Ubuntu CD
10-18 20:37 DEBUG  Distro:     does not contain C:\Windows\TEMP\pylD5B5.tmp\casper\filesystem.squashfs
10-18 20:37 DEBUG  Distro:   checking whether C:\Windows\TEMP\pylD5B5.tmp is a valid Ubuntu CD
10-18 20:37 DEBUG  Distro:     does not contain C:\Windows\TEMP\pylD5B5.tmp\casper\filesystem.squashfs
10-18 20:37 DEBUG  Distro:   checking whether C:\Windows\TEMP\pylD5B5.tmp is a valid Kubuntu CD
10-18 20:37 DEBUG  Distro:     does not contain C:\Windows\TEMP\pylD5B5.tmp\casper\filesystem.squashfs
10-18 20:37 DEBUG  Distro:   checking whether C:\Windows\TEMP\pylD5B5.tmp is a valid Kubuntu CD
10-18 20:37 DEBUG  Distro:     does not contain C:\Windows\TEMP\pylD5B5.tmp\casper\filesystem.squashfs
10-18 20:37 DEBUG  Distro:   checking whether C:\Windows\TEMP\pylD5B5.tmp is a valid Xubuntu CD
10-18 20:37 DEBUG  Distro:     does not contain C:\Windows\TEMP\pylD5B5.tmp\casper\filesystem.squashfs
10-18 20:37 DEBUG  Distro:   checking whether C:\Windows\TEMP\pylD5B5.tmp is a valid Xubuntu CD
10-18 20:37 DEBUG  Distro:     does not contain C:\Windows\TEMP\pylD5B5.tmp\casper\filesystem.squashfs
10-18 20:37 DEBUG  Distro:   checking whether C:\Windows\TEMP\pylD5B5.tmp is a valid Mythbuntu CD
10-18 20:37 DEBUG  Distro:     does not contain C:\Windows\TEMP\pylD5B5.tmp\casper\filesystem.squashfs
10-18 20:37 DEBUG  Distro:   checking whether C:\Windows\TEMP\pylD5B5.tmp is a valid Mythbuntu CD
10-18 20:37 DEBUG  Distro:     does not contain C:\Windows\TEMP\pylD5B5.tmp\casper\filesystem.squashfs
10-18 20:37 DEBUG  Distro:   checking whether C:\Windows\TEMP\pylD5B5.tmp is a valid Edubuntu CD
10-18 20:37 DEBUG  Distro:     does not contain C:\Windows\TEMP\pylD5B5.tmp\casper\filesystem.squashfs
10-18 20:37 DEBUG  Distro:   checking whether C:\Windows\TEMP\pylD5B5.tmp is a valid Edubuntu CD
10-18 20:37 DEBUG  Distro:     does not contain C:\Windows\TEMP\pylD5B5.tmp\casper\filesystem.squashfs
10-18 20:37 DEBUG  Distro:   checking whether C:\Windows\TEMP\pylD5B5.tmp is a valid Lubuntu CD
10-18 20:37 DEBUG  Distro:     does not contain C:\Windows\TEMP\pylD5B5.tmp\casper\filesystem.squashfs
10-18 20:37 DEBUG  Distro:   checking whether C:\Windows\TEMP\pylD5B5.tmp is a valid Lubuntu CD
10-18 20:37 DEBUG  Distro:     does not contain C:\Windows\TEMP\pylD5B5.tmp\casper\filesystem.squashfs
10-18 20:37 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
10-18 20:37 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-18 20:37 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
10-18 20:37 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-18 20:37 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
10-18 20:37 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-18 20:37 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
10-18 20:37 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-18 20:37 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
10-18 20:37 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-18 20:37 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
10-18 20:37 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-18 20:37 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
10-18 20:37 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-18 20:37 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
10-18 20:37 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-18 20:37 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
10-18 20:37 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-18 20:37 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
10-18 20:37 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-18 20:37 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
10-18 20:37 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-18 20:37 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
10-18 20:37 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-18 20:37 INFO   root: Running the installer...
10-18 20:37 DEBUG  WindowsFrontend: __init__...
10-18 20:37 DEBUG  WindowsFrontend: on_init...
10-18 20:37 INFO   WinuiPage: appname=wubi, localedir=C:\Windows\TEMP\pylD5B5.tmp\translations, languages=['en_US', 'en']
10-18 20:37 INFO   WinuiPage: appname=wubi, localedir=C:\Windows\TEMP\pylD5B5.tmp\translations, languages=['en_US', 'en']
10-18 20:37 DEBUG  WindowsFrontend: frontend.on_quit
10-18 20:37 DEBUG  root: application.on_quit
10-18 20:37 INFO   root: sys.exit
10-18 20:53 INFO   root: === wubi 12.04.3 rev279 ===
10-18 20:53 DEBUG  root: Logfile is c:\windows\temp\wubi-12.04.3-rev279.log
10-18 20:53 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\Users\\Eric\\Desktop\\ubuntu\\wubi.exe"']
10-18 20:53 DEBUG  CommonBackend: data_dir=C:\Windows\TEMP\pyl1BF8.tmp\data
10-18 20:53 DEBUG  WindowsBackend: 7z=C:\Windows\TEMP\pyl1BF8.tmp\bin\7z.exe
10-18 20:53 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
10-18 20:53 DEBUG  CommonBackend: Fetching basic info...
10-18 20:53 DEBUG  CommonBackend: original_exe=C:\Users\Eric\Desktop\ubuntu\wubi.exe
10-18 20:53 DEBUG  CommonBackend: platform=win32
10-18 20:53 DEBUG  CommonBackend: osname=nt
10-18 20:53 DEBUG  CommonBackend: language=en_US
10-18 20:53 DEBUG  CommonBackend: encoding=cp1252
10-18 20:53 DEBUG  WindowsBackend: arch=amd64
10-18 20:53 DEBUG  CommonBackend: Parsing isolist=C:\Windows\TEMP\pyl1BF8.tmp\data\isolist.ini
10-18 20:53 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
10-18 20:53 DEBUG  CommonBackend:   Adding distro Edubuntu-i386
10-18 20:53 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
10-18 20:53 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
10-18 20:53 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
10-18 20:53 DEBUG  CommonBackend:   Adding distro Edubuntu-amd64
10-18 20:53 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
10-18 20:53 DEBUG  CommonBackend:   Adding distro Lubuntu-i386
10-18 20:53 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
10-18 20:53 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
10-18 20:53 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
10-18 20:53 DEBUG  CommonBackend:   Adding distro Lubuntu-amd64
10-18 20:53 DEBUG  WindowsBackend: Fetching host info...
10-18 20:53 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
10-18 20:53 DEBUG  WindowsBackend: windows version=vista
10-18 20:53 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium
10-18 20:53 DEBUG  WindowsBackend: windows_sp=None
10-18 20:53 DEBUG  WindowsBackend: windows_build=7601
10-18 20:53 DEBUG  WindowsBackend: gmt=-5
10-18 20:53 DEBUG  WindowsBackend: country=US
10-18 20:53 DEBUG  WindowsBackend: timezone=America/New_York
10-18 20:53 DEBUG  WindowsBackend: windows_username=Eric
10-18 20:53 DEBUG  WindowsBackend: user_full_name=Eric
10-18 20:53 DEBUG  WindowsBackend: user_directory=C:\Users\Eric
10-18 20:53 DEBUG  WindowsBackend: windows_language_code=1033
10-18 20:53 DEBUG  WindowsBackend: windows_language=English
10-18 20:53 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM) i5-3317U CPU @ 1.70GHz
10-18 20:53 DEBUG  WindowsBackend: bootloader=vista
10-18 20:53 DEBUG  WindowsBackend: system_drive=Drive(C: hd 380326.304688 mb free ntfs)
10-18 20:53 DEBUG  WindowsBackend: drive=Drive(C: hd 380326.304688 mb free ntfs)
10-18 20:53 DEBUG  WindowsBackend: drive=Drive(D: cd 0.0 mb free )
10-18 20:53 DEBUG  WindowsBackend: uninstaller_path=None
10-18 20:53 DEBUG  WindowsBackend: previous_target_dir=None
10-18 20:53 DEBUG  WindowsBackend: previous_distro_name=None
10-18 20:53 DEBUG  WindowsBackend: keyboard_id=67699721
10-18 20:53 DEBUG  WindowsBackend: keyboard_layout=us
10-18 20:53 DEBUG  WindowsBackend: keyboard_variant=
10-18 20:53 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
10-18 20:53 DEBUG  CommonBackend: locale=en_US.UTF-8
10-18 20:53 DEBUG  WindowsBackend: total_memory_mb=4095.99999905
10-18 20:53 DEBUG  CommonBackend: Searching ISOs on USB devices
10-18 20:53 DEBUG  CommonBackend: Searching for local CDs
10-18 20:53 DEBUG  Distro:   checking whether C:\Windows\TEMP\pyl1BF8.tmp is a valid Ubuntu CD
10-18 20:53 DEBUG  Distro:     does not contain C:\Windows\TEMP\pyl1BF8.tmp\casper\filesystem.squashfs
10-18 20:53 DEBUG  Distro:   checking whether C:\Windows\TEMP\pyl1BF8.tmp is a valid Ubuntu CD
10-18 20:53 DEBUG  Distro:     does not contain C:\Windows\TEMP\pyl1BF8.tmp\casper\filesystem.squashfs
10-18 20:53 DEBUG  Distro:   checking whether C:\Windows\TEMP\pyl1BF8.tmp is a valid Kubuntu CD
10-18 20:53 DEBUG  Distro:     does not contain C:\Windows\TEMP\pyl1BF8.tmp\casper\filesystem.squashfs
10-18 20:53 DEBUG  Distro:   checking whether C:\Windows\TEMP\pyl1BF8.tmp is a valid Kubuntu CD
10-18 20:53 DEBUG  Distro:     does not contain C:\Windows\TEMP\pyl1BF8.tmp\casper\filesystem.squashfs
10-18 20:53 DEBUG  Distro:   checking whether C:\Windows\TEMP\pyl1BF8.tmp is a valid Xubuntu CD
10-18 20:53 DEBUG  Distro:     does not contain C:\Windows\TEMP\pyl1BF8.tmp\casper\filesystem.squashfs
10-18 20:53 DEBUG  Distro:   checking whether C:\Windows\TEMP\pyl1BF8.tmp is a valid Xubuntu CD
10-18 20:53 DEBUG  Distro:     does not contain C:\Windows\TEMP\pyl1BF8.tmp\casper\filesystem.squashfs
10-18 20:53 DEBUG  Distro:   checking whether C:\Windows\TEMP\pyl1BF8.tmp is a valid Mythbuntu CD
10-18 20:53 DEBUG  Distro:     does not contain C:\Windows\TEMP\pyl1BF8.tmp\casper\filesystem.squashfs
10-18 20:53 DEBUG  Distro:   checking whether C:\Windows\TEMP\pyl1BF8.tmp is a valid Mythbuntu CD
10-18 20:53 DEBUG  Distro:     does not contain C:\Windows\TEMP\pyl1BF8.tmp\casper\filesystem.squashfs
10-18 20:53 DEBUG  Distro:   checking whether C:\Windows\TEMP\pyl1BF8.tmp is a valid Edubuntu CD
10-18 20:53 DEBUG  Distro:     does not contain C:\Windows\TEMP\pyl1BF8.tmp\casper\filesystem.squashfs
10-18 20:53 DEBUG  Distro:   checking whether C:\Windows\TEMP\pyl1BF8.tmp is a valid Edubuntu CD
10-18 20:53 DEBUG  Distro:     does not contain C:\Windows\TEMP\pyl1BF8.tmp\casper\filesystem.squashfs
10-18 20:53 DEBUG  Distro:   checking whether C:\Windows\TEMP\pyl1BF8.tmp is a valid Lubuntu CD
10-18 20:53 DEBUG  Distro:     does not contain C:\Windows\TEMP\pyl1BF8.tmp\casper\filesystem.squashfs
10-18 20:53 DEBUG  Distro:   checking whether C:\Windows\TEMP\pyl1BF8.tmp is a valid Lubuntu CD
10-18 20:53 DEBUG  Distro:     does not contain C:\Windows\TEMP\pyl1BF8.tmp\casper\filesystem.squashfs
10-18 20:53 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
10-18 20:53 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-18 20:53 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
10-18 20:53 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-18 20:53 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
10-18 20:53 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-18 20:53 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
10-18 20:53 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-18 20:53 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
10-18 20:53 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-18 20:53 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
10-18 20:53 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-18 20:53 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
10-18 20:53 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-18 20:53 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
10-18 20:53 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-18 20:53 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
10-18 20:53 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-18 20:53 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
10-18 20:53 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-18 20:53 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
10-18 20:53 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-18 20:53 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
10-18 20:53 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-18 20:53 INFO   root: Running the installer...
10-18 20:53 DEBUG  WindowsFrontend: __init__...
10-18 20:53 DEBUG  WindowsFrontend: on_init...
10-18 20:53 INFO   WinuiPage: appname=wubi, localedir=C:\Windows\TEMP\pyl1BF8.tmp\translations, languages=['en_US', 'en']
10-18 20:53 INFO   WinuiPage: appname=wubi, localedir=C:\Windows\TEMP\pyl1BF8.tmp\translations, languages=['en_US', 'en']
10-18 20:53 DEBUG  WinuiInstallationPage: target_drive=C:, installation_size=18000MB, distro_name=Ubuntu, language=en_US, locale=en_US.UTF-8, username=linux
10-18 20:53 INFO   root: Received settings
10-18 20:53 DEBUG  CommonBackend: Searching for local CD
10-18 20:53 DEBUG  Distro:   checking whether C:\Windows\TEMP\pyl1BF8.tmp is a valid Ubuntu CD
10-18 20:53 DEBUG  Distro:     does not contain C:\Windows\TEMP\pyl1BF8.tmp\casper\filesystem.squashfs
10-18 20:53 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
10-18 20:53 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-18 20:53 DEBUG  CommonBackend: Searching for local ISO
10-18 20:53 INFO   WinuiPage: appname=wubi, localedir=C:\Windows\TEMP\pyl1BF8.tmp\translations, languages=['en_US', 'en']
10-18 20:53 DEBUG  TaskList: # Running tasklist...
10-18 20:53 DEBUG  TaskList: ## Running select_target_dir...
10-18 20:53 ERROR  TaskList: Cannot install into C:\ubuntu.
There is another file or directory with this name.
Please remove it before continuing.
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 81, in select_target_dir
Exception: Cannot install into C:\ubuntu.
There is another file or directory with this name.
Please remove it before continuing.
10-18 20:53 DEBUG  TaskList: # Cancelling tasklist
10-18 20:53 DEBUG  TaskList: # Finished tasklist
10-18 20:53 ERROR  root: Cannot install into C:\ubuntu.
There is another file or directory with this name.
Please remove it before continuing.
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 58, in run
  File "\lib\wubi\application.py", line 132, in select_task
  File "\lib\wubi\application.py", line 158, in run_installer
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 81, in select_target_dir
Exception: Cannot install into C:\ubuntu.
There is another file or directory with this name.
Please remove it before continuing.
10-18 20:56 INFO   root: === wubi 12.04.3 rev279 ===
10-18 20:56 DEBUG  root: Logfile is c:\windows\temp\wubi-12.04.3-rev279.log
10-18 20:56 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\Users\\Eric\\Desktop\\ubuntu\\wubi.exe"']
10-18 20:56 DEBUG  CommonBackend: data_dir=C:\Windows\TEMP\pyl2AE6.tmp\data
10-18 20:56 DEBUG  WindowsBackend: 7z=C:\Windows\TEMP\pyl2AE6.tmp\bin\7z.exe
10-18 20:56 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
10-18 20:56 DEBUG  CommonBackend: Fetching basic info...
10-18 20:56 DEBUG  CommonBackend: original_exe=C:\Users\Eric\Desktop\ubuntu\wubi.exe
10-18 20:56 DEBUG  CommonBackend: platform=win32
10-18 20:56 DEBUG  CommonBackend: osname=nt
10-18 20:56 DEBUG  CommonBackend: language=en_US
10-18 20:56 DEBUG  CommonBackend: encoding=cp1252
10-18 20:56 DEBUG  WindowsBackend: arch=amd64
10-18 20:56 DEBUG  CommonBackend: Parsing isolist=C:\Windows\TEMP\pyl2AE6.tmp\data\isolist.ini
10-18 20:56 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
10-18 20:56 DEBUG  CommonBackend:   Adding distro Edubuntu-i386
10-18 20:56 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
10-18 20:56 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
10-18 20:56 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
10-18 20:56 DEBUG  CommonBackend:   Adding distro Edubuntu-amd64
10-18 20:56 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
10-18 20:56 DEBUG  CommonBackend:   Adding distro Lubuntu-i386
10-18 20:56 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
10-18 20:56 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
10-18 20:56 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
10-18 20:56 DEBUG  CommonBackend:   Adding distro Lubuntu-amd64
10-18 20:56 DEBUG  WindowsBackend: Fetching host info...
10-18 20:56 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
10-18 20:56 DEBUG  WindowsBackend: windows version=vista
10-18 20:56 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium
10-18 20:56 DEBUG  WindowsBackend: windows_sp=None
10-18 20:56 DEBUG  WindowsBackend: windows_build=7601
10-18 20:56 DEBUG  WindowsBackend: gmt=-5
10-18 20:56 DEBUG  WindowsBackend: country=US
10-18 20:56 DEBUG  WindowsBackend: timezone=America/New_York
10-18 20:56 DEBUG  WindowsBackend: windows_username=Eric
10-18 20:56 DEBUG  WindowsBackend: user_full_name=Eric
10-18 20:56 DEBUG  WindowsBackend: user_directory=C:\Users\Eric
10-18 20:56 DEBUG  WindowsBackend: windows_language_code=1033
10-18 20:56 DEBUG  WindowsBackend: windows_language=English
10-18 20:56 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM) i5-3317U CPU @ 1.70GHz
10-18 20:56 DEBUG  WindowsBackend: bootloader=vista
10-18 20:56 DEBUG  WindowsBackend: system_drive=Drive(C: hd 380320.042969 mb free ntfs)
10-18 20:56 DEBUG  WindowsBackend: drive=Drive(C: hd 380320.042969 mb free ntfs)
10-18 20:56 DEBUG  WindowsBackend: drive=Drive(D: cd 0.0 mb free )
10-18 20:56 DEBUG  WindowsBackend: uninstaller_path=None
10-18 20:56 DEBUG  WindowsBackend: previous_target_dir=None
10-18 20:56 DEBUG  WindowsBackend: previous_distro_name=None
10-18 20:56 DEBUG  WindowsBackend: keyboard_id=67699721
10-18 20:56 DEBUG  WindowsBackend: keyboard_layout=us
10-18 20:56 DEBUG  WindowsBackend: keyboard_variant=
10-18 20:56 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
10-18 20:56 DEBUG  CommonBackend: locale=en_US.UTF-8
10-18 20:56 DEBUG  WindowsBackend: total_memory_mb=4095.99999905
10-18 20:56 DEBUG  CommonBackend: Searching ISOs on USB devices
10-18 20:56 DEBUG  CommonBackend: Searching for local CDs
10-18 20:56 DEBUG  Distro:   checking whether C:\Windows\TEMP\pyl2AE6.tmp is a valid Ubuntu CD
10-18 20:56 DEBUG  Distro:     does not contain C:\Windows\TEMP\pyl2AE6.tmp\casper\filesystem.squashfs
10-18 20:56 DEBUG  Distro:   checking whether C:\Windows\TEMP\pyl2AE6.tmp is a valid Ubuntu CD
10-18 20:56 DEBUG  Distro:     does not contain C:\Windows\TEMP\pyl2AE6.tmp\casper\filesystem.squashfs
10-18 20:56 DEBUG  Distro:   checking whether C:\Windows\TEMP\pyl2AE6.tmp is a valid Kubuntu CD
10-18 20:56 DEBUG  Distro:     does not contain C:\Windows\TEMP\pyl2AE6.tmp\casper\filesystem.squashfs
10-18 20:56 DEBUG  Distro:   checking whether C:\Windows\TEMP\pyl2AE6.tmp is a valid Kubuntu CD
10-18 20:56 DEBUG  Distro:     does not contain C:\Windows\TEMP\pyl2AE6.tmp\casper\filesystem.squashfs
10-18 20:56 DEBUG  Distro:   checking whether C:\Windows\TEMP\pyl2AE6.tmp is a valid Xubuntu CD
10-18 20:56 DEBUG  Distro:     does not contain C:\Windows\TEMP\pyl2AE6.tmp\casper\filesystem.squashfs
10-18 20:56 DEBUG  Distro:   checking whether C:\Windows\TEMP\pyl2AE6.tmp is a valid Xubuntu CD
10-18 20:56 DEBUG  Distro:     does not contain C:\Windows\TEMP\pyl2AE6.tmp\casper\filesystem.squashfs
10-18 20:56 DEBUG  Distro:   checking whether C:\Windows\TEMP\pyl2AE6.tmp is a valid Mythbuntu CD
10-18 20:56 DEBUG  Distro:     does not contain C:\Windows\TEMP\pyl2AE6.tmp\casper\filesystem.squashfs
10-18 20:56 DEBUG  Distro:   checking whether C:\Windows\TEMP\pyl2AE6.tmp is a valid Mythbuntu CD
10-18 20:56 DEBUG  Distro:     does not contain C:\Windows\TEMP\pyl2AE6.tmp\casper\filesystem.squashfs
10-18 20:56 DEBUG  Distro:   checking whether C:\Windows\TEMP\pyl2AE6.tmp is a valid Edubuntu CD
10-18 20:56 DEBUG  Distro:     does not contain C:\Windows\TEMP\pyl2AE6.tmp\casper\filesystem.squashfs
10-18 20:56 DEBUG  Distro:   checking whether C:\Windows\TEMP\pyl2AE6.tmp is a valid Edubuntu CD
10-18 20:56 DEBUG  Distro:     does not contain C:\Windows\TEMP\pyl2AE6.tmp\casper\filesystem.squashfs
10-18 20:56 DEBUG  Distro:   checking whether C:\Windows\TEMP\pyl2AE6.tmp is a valid Lubuntu CD
10-18 20:56 DEBUG  Distro:     does not contain C:\Windows\TEMP\pyl2AE6.tmp\casper\filesystem.squashfs
10-18 20:56 DEBUG  Distro:   checking whether C:\Windows\TEMP\pyl2AE6.tmp is a valid Lubuntu CD
10-18 20:56 DEBUG  Distro:     does not contain C:\Windows\TEMP\pyl2AE6.tmp\casper\filesystem.squashfs
10-18 20:56 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
10-18 20:56 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-18 20:56 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
10-18 20:56 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-18 20:56 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
10-18 20:56 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-18 20:56 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
10-18 20:56 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-18 20:56 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
10-18 20:56 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-18 20:56 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
10-18 20:56 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-18 20:56 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
10-18 20:56 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-18 20:56 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
10-18 20:56 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-18 20:56 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
10-18 20:56 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-18 20:56 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
10-18 20:56 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-18 20:56 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
10-18 20:56 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-18 20:56 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
10-18 20:56 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-18 20:56 INFO   root: Running the installer...
10-18 20:56 DEBUG  WindowsFrontend: __init__...
10-18 20:56 DEBUG  WindowsFrontend: on_init...
10-18 20:56 INFO   WinuiPage: appname=wubi, localedir=C:\Windows\TEMP\pyl2AE6.tmp\translations, languages=['en_US', 'en']
10-18 20:56 INFO   WinuiPage: appname=wubi, localedir=C:\Windows\TEMP\pyl2AE6.tmp\translations, languages=['en_US', 'en']
10-18 20:56 DEBUG  WinuiInstallationPage: target_drive=C:, installation_size=18000MB, distro_name=Ubuntu, language=en_US, locale=en_US.UTF-8, username=ubuntu_eric
10-18 20:56 INFO   root: Received settings
10-18 20:56 DEBUG  CommonBackend: Searching for local CD
10-18 20:56 DEBUG  Distro:   checking whether C:\Windows\TEMP\pyl2AE6.tmp is a valid Ubuntu CD
10-18 20:56 DEBUG  Distro:     does not contain C:\Windows\TEMP\pyl2AE6.tmp\casper\filesystem.squashfs
10-18 20:56 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
10-18 20:56 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-18 20:56 DEBUG  CommonBackend: Searching for local ISO
10-18 20:56 INFO   WinuiPage: appname=wubi, localedir=C:\Windows\TEMP\pyl2AE6.tmp\translations, languages=['en_US', 'en']
10-18 20:56 DEBUG  TaskList: # Running tasklist...
10-18 20:56 DEBUG  TaskList: ## Running select_target_dir...
10-18 20:56 INFO   WindowsBackend: Installing into C:\ubuntu
10-18 20:56 DEBUG  TaskList: ## Finished select_target_dir
10-18 20:56 DEBUG  TaskList: ## Running create_dir_structure...
10-18 20:56 DEBUG  CommonBackend: Creating dir C:\ubuntu
10-18 20:56 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks
10-18 20:56 DEBUG  CommonBackend: Creating dir C:\ubuntu\install
10-18 20:56 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot
10-18 20:56 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot
10-18 20:56 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot\grub
10-18 20:56 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot\grub
10-18 20:56 DEBUG  TaskList: ## Finished create_dir_structure
10-18 20:56 DEBUG  TaskList: ## Running create_uninstaller...
10-18 20:56 DEBUG  WindowsBackend: Copying uninstaller C:\Users\Eric\Desktop\ubuntu\wubi.exe -> C:\ubuntu\uninstall-wubi.exe
10-18 20:56 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString C:\ubuntu\uninstall-wubi.exe
10-18 20:56 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir C:\ubuntu
10-18 20:56 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
10-18 20:56 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon C:\ubuntu\Ubuntu.ico
10-18 20:56 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 12.04.3-rev279
10-18 20:56 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
10-18 20:56 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com](http://www.ubuntu.com)
10-18 20:56 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
10-18 20:56 DEBUG  TaskList: ## Finished create_uninstaller
10-18 20:56 DEBUG  TaskList: ## Running create_preseed_diskimage...
10-18 20:56 DEBUG  TaskList: ## Finished create_preseed_diskimage
10-18 20:56 DEBUG  TaskList: ## Running get_diskimage...
10-18 20:56 DEBUG  TaskList: New task download
10-18 20:56 DEBUG  TaskList: ### Running download...
10-18 20:56 DEBUG  downloader: downloading [http://releases.ubuntu.com/12.04.3/ubuntu-12.04.3-wubi-amd64.tar.xz](http://releases.ubuntu.com/12.04.3/ubuntu-12.04.3-wubi-amd64.tar.xz) > C:\ubuntu\disks\ubuntu-12.04.3-wubi-amd64.tar.xz
10-18 20:56 DEBUG  downloader: Download start filename=C:\ubuntu\disks\ubuntu-12.04.3-wubi-amd64.tar.xz, url=http://releases.ubuntu.com/12.04.3/ubuntu-12.04.3-wubi-amd64.tar.xz, basename=ubuntu-12.04.3-wubi-amd64.tar.xz, length=545608520, text=None
10-18 21:10 DEBUG  TaskList: ### Finished download
10-18 21:10 DEBUG  downloader: download finished (read 545608520 bytes)
10-18 21:10 DEBUG  TaskList: ## Finished get_diskimage
10-18 21:10 DEBUG  TaskList: ## Running extract_diskimage...
10-18 21:11 DEBUG  TaskList: ## Finished extract_diskimage
10-18 21:11 DEBUG  TaskList: ## Running choose_disk_sizes...
10-18 21:11 DEBUG  WindowsBackend: total size=18000
  root=17744
  swap=256
  home=0
  usr=0
10-18 21:11 DEBUG  TaskList: ## Finished choose_disk_sizes
10-18 21:11 DEBUG  TaskList: ## Running expand_diskimage...
10-18 21:12 DEBUG  TaskList: ## Finished expand_diskimage
10-18 21:12 DEBUG  TaskList: ## Running create_swap_diskimage...
10-18 21:12 DEBUG  TaskList: ## Finished create_swap_diskimage
10-18 21:12 DEBUG  TaskList: ## Running modify_bootloader...
10-18 21:12 DEBUG  TaskList: New task modify_bcd
10-18 21:12 DEBUG  TaskList: ### Running modify_bcd...
10-18 21:12 DEBUG  WindowsBackend: modify_bcd Drive(C: hd 380320.042969 mb free ntfs)
10-18 21:12 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi VistaBootDrive {63287cf2-b105-11e1-a440-efa37d334c7f}
10-18 21:12 DEBUG  TaskList: ### Finished modify_bcd
10-18 21:12 DEBUG  TaskList: ## Finished modify_bootloader
10-18 21:12 DEBUG  TaskList: ## Running diskimage_bootloader...
10-18 21:12 DEBUG  WindowsBackend: Copying C:\Windows\TEMP\pyl2AE6.tmp\winboot -> C:\ubuntu\winboot
10-18 21:12 DEBUG  TaskList: ## Finished diskimage_bootloader
10-18 21:12 DEBUG  TaskList: # Finished tasklist
10-18 21:12 INFO   root: Almost finished installing
10-18 21:12 INFO   WinuiPage: appname=wubi, localedir=C:\Windows\TEMP\pyl2AE6.tmp\translations, languages=['en_US', 'en']
10-18 21:18 INFO   root: Finished installation
10-18 21:18 INFO   root: Rebooting
10-18 21:18 DEBUG  TaskList: # Running tasklist...
10-18 21:18 DEBUG  TaskList: ## Running reboot...
10-18 21:18 DEBUG  TaskList: ## Finished reboot
10-18 21:18 DEBUG  TaskList: # Finished tasklist
10-18 21:18 DEBUG  root: application.quit
10-18 21:18 DEBUG  WindowsFrontend: frontend.quit
10-18 21:18 DEBUG  WindowsFrontend: frontend.on_quit
10-18 21:18 DEBUG  root: application.on_quit
10-18 21:18 INFO   root: sys.exit
```

---

### Post by bcbc on 2013-10-22
You will probably have to reinstall now, likely the wubi virtual disk is corrupted. But based on your "Purple screen" comment you have either an nvidia or radeon graphics card so you should boot with nomodeset: [http://askubuntu.com/questions/162075/my-computer-boots-to-a-black-screen-what-options-do-i-have-to-fix-it](http://askubuntu.com/questions/162075/my-computer-boots-to-a-black-screen-what-options-do-i-have-to-fix-it)

---

