---
title: "What does this error code mean?"
date: 2011-10-09
forum: New to Ubuntu
---

### Post by evanbas on 2011-10-09
Hey everybody, I'm new to Ubuntu and want to Install  Ubuntu 11.04 using Wubi in one of my partition, but every time I try that, this error message always pop up and ubuntu won't install.. Can someone please explain it?


[IMG]http://ubuntuforums.org/attachment.php?attachmentid=203868&stc=1&d=1318151421[/IMG]

---

### Post by raja.genupula on 2011-10-09
Its showing some error log at the bottom of the window , go that location please post that info here .

---

### Post by evanbas on 2011-10-09
> **raja.genupula said:**
> Its showing some error log at the bottom of the window , go that location please post that info here .

Here you go :p

```
09-29 18:26 INFO   root: === wubi 11.04 rev211 ===
09-29 18:26 DEBUG  root: Logfile is c:\users\evan\appdata\local\temp\wubi-11.04-rev211.log
09-29 18:26 DEBUG  root: sys.argv = ['main.pyo', '--exefile="G:\\wubi.exe"']
09-29 18:26 DEBUG  CommonBackend: data_dir=C:\Users\Evan\AppData\Local\Temp\pyl52F0.tmp\data
09-29 18:26 DEBUG  WindowsBackend: 7z=C:\Users\Evan\AppData\Local\Temp\pyl52F0.tmp\bin\7z.exe
09-29 18:26 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
09-29 18:26 DEBUG  CommonBackend: Fetching basic info...
09-29 18:26 DEBUG  CommonBackend: original_exe=G:\wubi.exe
09-29 18:26 DEBUG  CommonBackend: platform=win32
09-29 18:26 DEBUG  CommonBackend: osname=nt
09-29 18:26 DEBUG  CommonBackend: language=id_ID
09-29 18:26 DEBUG  CommonBackend: encoding=cp1252
09-29 18:26 DEBUG  WindowsBackend: arch=amd64
09-29 18:26 DEBUG  CommonBackend: Parsing isolist=C:\Users\Evan\AppData\Local\Temp\pyl52F0.tmp\data\isolist.ini
09-29 18:26 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
09-29 18:26 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
09-29 18:26 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
09-29 18:26 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
09-29 18:26 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
09-29 18:26 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
09-29 18:26 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
09-29 18:26 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
09-29 18:26 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
09-29 18:26 DEBUG  WindowsBackend: Fetching host info...
09-29 18:26 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
09-29 18:26 DEBUG  WindowsBackend: windows version=vista
09-29 18:26 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium
09-29 18:26 DEBUG  WindowsBackend: windows_sp=Service Pack 1
09-29 18:26 DEBUG  WindowsBackend: windows_build=7601
09-29 18:26 DEBUG  WindowsBackend: gmt=7
09-29 18:26 DEBUG  WindowsBackend: country=ID
09-29 18:26 DEBUG  WindowsBackend: timezone=Asia/Jakarta
09-29 18:26 DEBUG  WindowsBackend: windows_username=Evan
09-29 18:26 DEBUG  WindowsBackend: user_full_name=Evan
09-29 18:26 DEBUG  WindowsBackend: user_directory=C:\Users\Evan
09-29 18:26 DEBUG  WindowsBackend: windows_language_code=1057
09-29 18:26 DEBUG  WindowsBackend: windows_language=Indonesian
09-29 18:26 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM) i3 CPU       M 330  @ 2.13GHz
09-29 18:26 DEBUG  WindowsBackend: bootloader=vista
09-29 18:26 DEBUG  WindowsBackend: system_drive=Drive(C: hd 119170.460938 mb free ntfs)
09-29 18:26 DEBUG  WindowsBackend: drive=Drive(C: hd 119170.460938 mb free ntfs)
09-29 18:26 DEBUG  WindowsBackend: drive=Drive(D: hd 2872.41796875 mb free ntfs)
09-29 18:26 DEBUG  WindowsBackend: drive=Drive(E: hd 99.328125 mb free fat32)
09-29 18:26 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free )
09-29 18:26 DEBUG  WindowsBackend: drive=Drive(G: cd 0.0 mb free cdfs)
09-29 18:26 DEBUG  WindowsBackend: drive=Drive(H: hd 76814.8203125 mb free ntfs)
09-29 18:26 DEBUG  WindowsBackend: drive=Drive(I: hd 19989.8984375 mb free ntfs)
09-29 18:26 DEBUG  WindowsBackend: drive=Drive(J: cd 0.0 mb free cdfs)
09-29 18:26 DEBUG  WindowsBackend: drive=Drive(K: removable 710.19921875 mb free fat32)
09-29 18:26 DEBUG  WindowsBackend: uninstaller_path=None
09-29 18:26 DEBUG  WindowsBackend: previous_target_dir=None
09-29 18:26 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
09-29 18:26 DEBUG  WindowsBackend: keyboard_id=67699721
09-29 18:26 DEBUG  WindowsBackend: keyboard_layout=us
09-29 18:26 DEBUG  WindowsBackend: keyboard_variant=
09-29 18:26 DEBUG  CommonBackend: python locale=('id_ID', 'cp1252')
09-29 18:26 DEBUG  CommonBackend: locale=id_ID.UTF-8
09-29 18:26 DEBUG  WindowsBackend: total_memory_mb=1910.83984375
09-29 18:26 DEBUG  CommonBackend: Searching ISOs on USB devices
09-29 18:26 DEBUG  CommonBackend: Searching for local CDs
09-29 18:26 DEBUG  Distro:   checking whether C:\Users\Evan\AppData\Local\Temp\pyl52F0.tmp is a valid Ubuntu CD
09-29 18:26 DEBUG  Distro:     does not contain C:\Users\Evan\AppData\Local\Temp\pyl52F0.tmp\casper\filesystem.squashfs
09-29 18:26 DEBUG  Distro:   checking whether C:\Users\Evan\AppData\Local\Temp\pyl52F0.tmp is a valid Ubuntu CD
09-29 18:26 DEBUG  Distro:     does not contain C:\Users\Evan\AppData\Local\Temp\pyl52F0.tmp\casper\filesystem.squashfs
09-29 18:26 DEBUG  Distro:   checking whether C:\Users\Evan\AppData\Local\Temp\pyl52F0.tmp is a valid Ubuntu Netbook CD
09-29 18:26 DEBUG  Distro:     does not contain C:\Users\Evan\AppData\Local\Temp\pyl52F0.tmp\casper\filesystem.squashfs
09-29 18:26 DEBUG  Distro:   checking whether C:\Users\Evan\AppData\Local\Temp\pyl52F0.tmp is a valid Kubuntu CD
09-29 18:26 DEBUG  Distro:     does not contain C:\Users\Evan\AppData\Local\Temp\pyl52F0.tmp\casper\filesystem.squashfs
09-29 18:26 DEBUG  Distro:   checking whether C:\Users\Evan\AppData\Local\Temp\pyl52F0.tmp is a valid Kubuntu CD
09-29 18:26 DEBUG  Distro:     does not contain C:\Users\Evan\AppData\Local\Temp\pyl52F0.tmp\casper\filesystem.squashfs
09-29 18:26 DEBUG  Distro:   checking whether C:\Users\Evan\AppData\Local\Temp\pyl52F0.tmp is a valid Xubuntu CD
09-29 18:26 DEBUG  Distro:     does not contain C:\Users\Evan\AppData\Local\Temp\pyl52F0.tmp\casper\filesystem.squashfs
09-29 18:26 DEBUG  Distro:   checking whether C:\Users\Evan\AppData\Local\Temp\pyl52F0.tmp is a valid Xubuntu CD
09-29 18:26 DEBUG  Distro:     does not contain C:\Users\Evan\AppData\Local\Temp\pyl52F0.tmp\casper\filesystem.squashfs
09-29 18:26 DEBUG  Distro:   checking whether C:\Users\Evan\AppData\Local\Temp\pyl52F0.tmp is a valid Mythbuntu CD
09-29 18:26 DEBUG  Distro:     does not contain C:\Users\Evan\AppData\Local\Temp\pyl52F0.tmp\casper\filesystem.squashfs
09-29 18:26 DEBUG  Distro:   checking whether C:\Users\Evan\AppData\Local\Temp\pyl52F0.tmp is a valid Mythbuntu CD
09-29 18:26 DEBUG  Distro:     does not contain C:\Users\Evan\AppData\Local\Temp\pyl52F0.tmp\casper\filesystem.squashfs
09-29 18:26 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
09-29 18:26 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-29 18:26 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
09-29 18:26 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-29 18:26 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
09-29 18:26 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-29 18:26 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
09-29 18:26 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-29 18:26 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
09-29 18:26 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-29 18:26 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
09-29 18:26 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-29 18:26 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
09-29 18:26 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-29 18:26 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
09-29 18:26 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-29 18:26 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
09-29 18:26 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-29 18:26 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
09-29 18:26 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-29 18:26 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
09-29 18:26 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-29 18:26 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook CD
09-29 18:26 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-29 18:26 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
09-29 18:26 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-29 18:26 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
09-29 18:26 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-29 18:26 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
09-29 18:26 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-29 18:26 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
09-29 18:26 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-29 18:26 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
09-29 18:26 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-29 18:26 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
09-29 18:26 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-29 18:26 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
09-29 18:26 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-29 18:26 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
09-29 18:26 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-29 18:26 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu Netbook CD
09-29 18:26 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-29 18:26 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
09-29 18:26 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-29 18:26 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
09-29 18:26 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-29 18:26 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
09-29 18:26 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-29 18:26 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
09-29 18:26 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-29 18:26 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
09-29 18:26 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-29 18:26 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
09-29 18:26 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-29 18:26 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
09-29 18:26 DEBUG  Distro:   parsing info from str=Ubuntu 11.04 "Natty Narwhal" - Release i386 (20110427.1)
09-29 18:26 DEBUG  Distro:   parsed info={'name': 'Ubuntu',  'subversion': 'Release', 'version': '11.04', 'build': '20110427.1',  'codename': 'Natty Narwhal', 'arch': 'i386'}
09-29 18:26 INFO   Distro: Found a valid CD for Ubuntu: G:\
09-29 18:26 INFO   root: Running the CD menu...
09-29 18:26 DEBUG  WindowsFrontend: __init__...
09-29 18:26 DEBUG  WindowsFrontend: on_init...
09-29 18:26 INFO   WinuiPage: appname=wubi,  localedir=C:\Users\Evan\AppData\Local\Temp\pyl52F0.tmp\translations,  languages=['id_ID', 'id']
09-29 18:26 INFO   WinuiPage: appname=wubi,  localedir=C:\Users\Evan\AppData\Local\Temp\pyl52F0.tmp\translations,  languages=['id_ID', 'id']
09-29 18:26 INFO   root: CD menu finished
09-29 18:26 INFO   root: Running the installer...
09-29 18:26 INFO   WinuiPage: appname=wubi,  localedir=C:\Users\Evan\AppData\Local\Temp\pyl52F0.tmp\translations,  languages=['id_ID', 'id']
09-29 18:26 INFO   WinuiPage: appname=wubi,  localedir=C:\Users\Evan\AppData\Local\Temp\pyl52F0.tmp\translations,  languages=['id_ID', 'id']
09-29 18:26 DEBUG  WinuiInstallationPage: target_drive=I:,  installation_size=17000MB, distro_name=Ubuntu, language=en_US,  locale=en_US.UTF-8, username=evan
09-29 18:26 INFO   root: Received settings
09-29 18:26 INFO   WinuiPage: appname=wubi,  localedir=C:\Users\Evan\AppData\Local\Temp\pyl52F0.tmp\translations,  languages=['en_US', 'en']
09-29 18:26 DEBUG  TaskList: # Running tasklist...
09-29 18:26 DEBUG  TaskList: ## Running select_target_dir...
09-29 18:26 INFO   WindowsBackend: Installing into I:\ubuntu
09-29 18:26 DEBUG  TaskList: ## Finished select_target_dir
09-29 18:26 DEBUG  TaskList: ## Running create_dir_structure...
09-29 18:26 DEBUG  CommonBackend: Creating dir I:\ubuntu
09-29 18:26 DEBUG  CommonBackend: Creating dir I:\ubuntu\disks
09-29 18:26 DEBUG  CommonBackend: Creating dir I:\ubuntu\install
09-29 18:26 DEBUG  CommonBackend: Creating dir I:\ubuntu\install\boot
09-29 18:26 DEBUG  CommonBackend: Creating dir I:\ubuntu\disks\boot
09-29 18:26 DEBUG  CommonBackend: Creating dir I:\ubuntu\disks\boot\grub
09-29 18:26 DEBUG  CommonBackend: Creating dir I:\ubuntu\install\boot\grub
09-29 18:26 DEBUG  TaskList: ## Finished create_dir_structure
09-29 18:26 DEBUG  TaskList: ## Running uncompress_target_dir...
09-29 18:26 DEBUG  TaskList: ## Finished uncompress_target_dir
09-29 18:26 DEBUG  TaskList: ## Running create_uninstaller...
09-29 18:26 DEBUG  WindowsBackend: Copying uninstaller G:\wubi.exe -> I:\ubuntu\uninstall-wubi.exe
09-29 18:26 DEBUG  registry: Setting registry key -2147483646  Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString  I:\ubuntu\uninstall-wubi.exe
09-29 18:26 DEBUG  registry: Setting registry key -2147483646  Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir  I:\ubuntu
09-29 18:26 DEBUG  registry: Setting registry key -2147483646  Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName  Ubuntu
09-29 18:26 DEBUG  registry: Setting registry key -2147483646  Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon  I:\ubuntu\Ubuntu.ico
09-29 18:26 DEBUG  registry: Setting registry key -2147483646  Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion  11.04-rev211
09-29 18:26 DEBUG  registry: Setting registry key -2147483646  Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher  Ubuntu
09-29 18:26 DEBUG  registry: Setting registry key -2147483646  Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com]("http://www.ubuntu.com/")
09-29 18:26 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
09-29 18:26 DEBUG  TaskList: ## Finished create_uninstaller
09-29 18:26 DEBUG  TaskList: ## Running copy_installation_files...
09-29 18:26 DEBUG  WindowsBackend: Copying  C:\Users\Evan\AppData\Local\Temp\pyl52F0.tmp\data\custom-installation  -> I:\ubuntu\install\custom-installation
09-29 18:26 DEBUG  WindowsBackend: Copying C:\Users\Evan\AppData\Local\Temp\pyl52F0.tmp\winboot -> I:\ubuntu\winboot
09-29 18:26 DEBUG  WindowsBackend: Copying  C:\Users\Evan\AppData\Local\Temp\pyl52F0.tmp\data\images\Ubuntu.ico  -> I:\ubuntu\Ubuntu.ico
09-29 18:26 DEBUG  TaskList: ## Finished copy_installation_files
09-29 18:26 DEBUG  TaskList: ## Running get_iso...
09-29 18:26 DEBUG  TaskList: New task copy_file
09-29 18:26 DEBUG  TaskList: ### Running copy_file...
09-29 18:27 DEBUG  TaskList: ### Finished copy_file
09-29 18:27 DEBUG  TaskList: New task check_iso
09-29 18:27 DEBUG  TaskList: ### Running check_iso...
09-29 18:27 DEBUG  CommonBackend: Checking I:\ubuntu\install\installation.iso
09-29 18:27 DEBUG  Distro:   checking Ubuntu ISO I:\ubuntu\install\installation.iso
09-29 18:27 DEBUG  WindowsBackend:   extracting .disk\info from I:\ubuntu\install\installation.iso
09-29 18:27 DEBUG  Distro:   parsing info from str=Ubuntu 11.04 "Natty Narwhal" - Release i386 (20110427.1)
09-29 18:27 DEBUG  Distro:   parsed info={'name': 'Ubuntu',  'subversion': 'Release', 'version': '11.04', 'build': '20110427.1',  'codename': 'Natty Narwhal', 'arch': 'i386'}
09-29 18:27 INFO   Distro: Found a valid iso for Ubuntu: I:\ubuntu\install\installation.iso
09-29 18:27 DEBUG  CommonBackend: Using distro Ubuntu i386 instead of Ubuntu amd64
09-29 18:27 DEBUG  TaskList: New task get_metalink
09-29 18:27 DEBUG  TaskList: #### Running get_metalink...
09-29 18:27 DEBUG  downloader: downloading [http://releases.ubuntu.com/11.04/ubuntu-11.04-desktop-i386.metalink](http://releases.ubuntu.com/11.04/ubuntu-11.04-desktop-i386.metalink) > I:\ubuntu\install
09-29 18:27 ERROR  CommonBackend: Cannot download metalink file [http://releases.ubuntu.com/11.04/ubuntu-11.04-desktop-i386.metalink](http://releases.ubuntu.com/11.04/ubuntu-11.04-desktop-i386.metalink) err=[Errno 4] IOError: <urlopen error (7, 'getaddrinfo failed')>
09-29 18:27 DEBUG  downloader: downloading [http://cdimage.ubuntu.com/daily-live/current/natty-desktop-i386.metalink](http://cdimage.ubuntu.com/daily-live/current/natty-desktop-i386.metalink) > I:\ubuntu\install
09-29 18:27 ERROR  CommonBackend: Cannot download metalink file2 [http://cdimage.ubuntu.com/daily-live/current/natty-desktop-i386.metalink](http://cdimage.ubuntu.com/daily-live/current/natty-desktop-i386.metalink) err=[Errno 4] IOError: <urlopen error (7, 'getaddrinfo failed')>
09-29 18:27 DEBUG  TaskList: #### Finished get_metalink
09-29 18:27 ERROR  CommonBackend: ERROR: the metalink file is not  available, cannot check the md5 for I:\ubuntu\install\installation.iso,  ignoring
09-29 18:27 DEBUG  TaskList: ### Finished check_iso
09-29 18:27 DEBUG  TaskList: ## Finished get_iso
09-29 18:27 DEBUG  TaskList: ## Running extract_kernel...
09-29 18:27 DEBUG  CommonBackend: Copying files from CD G:\
09-29 18:27 DEBUG  CommonBackend: Checking kernel, initrd and md5sums
09-29 18:27 DEBUG  CommonBackend:   checking I:\ubuntu\install\boot\vmlinuz
09-29 18:27 DEBUG  CommonBackend:   I:\ubuntu\install\boot\vmlinuz md5 =  db0104e80bc7e667344a14af3515de25 == db0104e80bc7e667344a14af3515de25
09-29 18:27 DEBUG  CommonBackend:   checking I:\ubuntu\install\boot\initrd.lz
09-29 18:27 DEBUG  CommonBackend:   I:\ubuntu\install\boot\initrd.lz md5  = 4b776cdafb272064bb70e09ba212e4aa == 4b776cdafb272064bb70e09ba212e4aa
09-29 18:27 DEBUG  TaskList: ## Finished extract_kernel
09-29 18:27 DEBUG  TaskList: ## Running choose_disk_sizes...
09-29 18:27 DEBUG  WindowsBackend: total size=17000
  root=16744
  swap=256
  home=0
  usr=0
09-29 18:27 DEBUG  TaskList: ## Finished choose_disk_sizes
09-29 18:27 DEBUG  TaskList: ## Running create_preseed...
09-29 18:27 DEBUG  TaskList: ## Finished create_preseed
09-29 18:27 DEBUG  TaskList: ## Running modify_bootloader...
09-29 18:27 DEBUG  TaskList: New task modify_bcd
09-29 18:27 DEBUG  TaskList: ### Running modify_bcd...
09-29 18:27 DEBUG  WindowsBackend: modify_bcd Drive(C: hd 119170.460938 mb free ntfs)
09-29 18:27 ERROR  TaskList: Error executing command
>>command=C:\Windows\System32\bcdedit.exe /set {3f2cd356-091c-11df-b381-9c46b9b554f6} device partition=I:
>>retval=1
>>stderr=An error has occurred setting the element data.

The request is not supported.


>>stdout=
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 648, in modify_bcd
  File "\lib\wubi\backends\common\utils.py", line 62, in run_command
Exception: Error executing command
>>command=C:\Windows\System32\bcdedit.exe /set {3f2cd356-091c-11df-b381-9c46b9b554f6} device partition=I:
>>retval=1
>>stderr=An error has occurred setting the element data.

The request is not supported.


>>stdout=
09-29 18:27 DEBUG  TaskList: # Cancelling tasklist
09-29 18:27 DEBUG  TaskList: New task modify_bcd
09-29 18:27 ERROR  root: Error executing command
>>command=C:\Windows\System32\bcdedit.exe /set {3f2cd356-091c-11df-b381-9c46b9b554f6} device partition=I:
>>retval=1
>>stderr=An error has occurred setting the element data.

The request is not supported.


>>stdout=
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 57, in run
  File "\lib\wubi\application.py", line 129, in select_task
  File "\lib\wubi\application.py", line 195, in run_cd_menu
  File "\lib\wubi\application.py", line 119, in select_task
  File "\lib\wubi\application.py", line 157, in run_installer
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 648, in modify_bcd
  File "\lib\wubi\backends\common\utils.py", line 62, in run_command
Exception: Error executing command
>>command=C:\Windows\System32\bcdedit.exe /set {3f2cd356-091c-11df-b381-9c46b9b554f6} device partition=I:
>>retval=1
>>stderr=An error has occurred setting the element data.

The request is not supported.


>>stdout=
09-29 18:27 DEBUG  TaskList: New task modify_bcd
09-29 18:27 DEBUG  TaskList: New task modify_bcd
09-29 18:27 DEBUG  TaskList: New task modify_bcd
09-29 18:27 DEBUG  TaskList: New task modify_bcd
09-29 18:27 DEBUG  TaskList: ## Finished modify_bootloader
09-29 18:27 DEBUG  TaskList: # Finished tasklist
09-29 18:29 INFO   root: === wubi 11.04 rev211 ===
09-29 18:29 DEBUG  root: Logfile is c:\users\evan\appdata\local\temp\wubi-11.04-rev211.log
09-29 18:29 DEBUG  root: sys.argv = ['main.pyo', '--exefile="G:\\wubi.exe"']
09-29 18:29 DEBUG  CommonBackend: data_dir=C:\Users\Evan\AppData\Local\Temp\pyl5CFF.tmp\data
09-29 18:29 DEBUG  WindowsBackend: 7z=C:\Users\Evan\AppData\Local\Temp\pyl5CFF.tmp\bin\7z.exe
09-29 18:29 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
09-29 18:29 DEBUG  CommonBackend: Fetching basic info...
09-29 18:29 DEBUG  CommonBackend: original_exe=G:\wubi.exe
09-29 18:29 DEBUG  CommonBackend: platform=win32
09-29 18:29 DEBUG  CommonBackend: osname=nt
09-29 18:29 DEBUG  CommonBackend: language=id_ID
09-29 18:29 DEBUG  CommonBackend: encoding=cp1252
09-29 18:29 DEBUG  WindowsBackend: arch=amd64
09-29 18:29 DEBUG  CommonBackend: Parsing isolist=C:\Users\Evan\AppData\Local\Temp\pyl5CFF.tmp\data\isolist.ini
09-29 18:29 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
09-29 18:29 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
09-29 18:29 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
09-29 18:29 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
09-29 18:29 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
09-29 18:29 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
09-29 18:29 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
09-29 18:29 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
09-29 18:29 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
09-29 18:29 DEBUG  WindowsBackend: Fetching host info...
09-29 18:29 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
09-29 18:29 DEBUG  WindowsBackend: windows version=vista
09-29 18:29 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium
09-29 18:29 DEBUG  WindowsBackend: windows_sp=Service Pack 1
09-29 18:29 DEBUG  WindowsBackend: windows_build=7601
09-29 18:29 DEBUG  WindowsBackend: gmt=7
09-29 18:29 DEBUG  WindowsBackend: country=ID
09-29 18:29 DEBUG  WindowsBackend: timezone=Asia/Jakarta
09-29 18:29 DEBUG  WindowsBackend: windows_username=Evan
09-29 18:29 DEBUG  WindowsBackend: user_full_name=Evan
09-29 18:29 DEBUG  WindowsBackend: user_directory=C:\Users\Evan
09-29 18:29 DEBUG  WindowsBackend: windows_language_code=1057
09-29 18:29 DEBUG  WindowsBackend: windows_language=Indonesian
09-29 18:29 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM) i3 CPU       M 330  @ 2.13GHz
09-29 18:29 DEBUG  WindowsBackend: bootloader=vista
09-29 18:29 DEBUG  WindowsBackend: system_drive=Drive(C: hd 119457.511719 mb free ntfs)
09-29 18:29 DEBUG  WindowsBackend: drive=Drive(C: hd 119457.511719 mb free ntfs)
09-29 18:29 DEBUG  WindowsBackend: drive=Drive(D: hd 2872.41796875 mb free ntfs)
09-29 18:29 DEBUG  WindowsBackend: drive=Drive(E: hd 99.328125 mb free fat32)
09-29 18:29 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free )
09-29 18:29 DEBUG  WindowsBackend: drive=Drive(G: cd 0.0 mb free cdfs)
09-29 18:29 DEBUG  WindowsBackend: drive=Drive(H: hd 76814.8203125 mb free ntfs)
09-29 18:29 DEBUG  WindowsBackend: drive=Drive(I: hd 19285.8671875 mb free ntfs)
09-29 18:29 DEBUG  WindowsBackend: drive=Drive(J: cd 0.0 mb free cdfs)
09-29 18:29 DEBUG  WindowsBackend: drive=Drive(K: removable 710.19921875 mb free fat32)
09-29 18:29 DEBUG  WindowsBackend: uninstaller_path=I:\ubuntu\uninstall-wubi.exe
09-29 18:29 DEBUG  WindowsBackend: previous_target_dir=I:\ubuntu
09-29 18:29 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
09-29 18:29 DEBUG  WindowsBackend: keyboard_id=67699721
09-29 18:29 DEBUG  WindowsBackend: keyboard_layout=us
09-29 18:29 DEBUG  WindowsBackend: keyboard_variant=
09-29 18:29 DEBUG  CommonBackend: python locale=('id_ID', 'cp1252')
09-29 18:29 DEBUG  CommonBackend: locale=id_ID.UTF-8
09-29 18:29 DEBUG  WindowsBackend: total_memory_mb=1910.83984375
09-29 18:29 DEBUG  CommonBackend: Searching ISOs on USB devices
09-29 18:29 DEBUG  CommonBackend: Searching for local CDs
09-29 18:29 DEBUG  Distro:   checking whether C:\Users\Evan\AppData\Local\Temp\pyl5CFF.tmp is a valid Ubuntu CD
09-29 18:29 DEBUG  Distro:     does not contain C:\Users\Evan\AppData\Local\Temp\pyl5CFF.tmp\casper\filesystem.squashfs
09-29 18:29 DEBUG  Distro:   checking whether C:\Users\Evan\AppData\Local\Temp\pyl5CFF.tmp is a valid Ubuntu CD
09-29 18:29 DEBUG  Distro:     does not contain C:\Users\Evan\AppData\Local\Temp\pyl5CFF.tmp\casper\filesystem.squashfs
09-29 18:29 DEBUG  Distro:   checking whether C:\Users\Evan\AppData\Local\Temp\pyl5CFF.tmp is a valid Ubuntu Netbook CD
09-29 18:29 DEBUG  Distro:     does not contain C:\Users\Evan\AppData\Local\Temp\pyl5CFF.tmp\casper\filesystem.squashfs
09-29 18:29 DEBUG  Distro:   checking whether C:\Users\Evan\AppData\Local\Temp\pyl5CFF.tmp is a valid Kubuntu CD
09-29 18:29 DEBUG  Distro:     does not contain C:\Users\Evan\AppData\Local\Temp\pyl5CFF.tmp\casper\filesystem.squashfs
09-29 18:29 DEBUG  Distro:   checking whether C:\Users\Evan\AppData\Local\Temp\pyl5CFF.tmp is a valid Kubuntu CD
09-29 18:29 DEBUG  Distro:     does not contain C:\Users\Evan\AppData\Local\Temp\pyl5CFF.tmp\casper\filesystem.squashfs
09-29 18:29 DEBUG  Distro:   checking whether C:\Users\Evan\AppData\Local\Temp\pyl5CFF.tmp is a valid Xubuntu CD
09-29 18:29 DEBUG  Distro:     does not contain C:\Users\Evan\AppData\Local\Temp\pyl5CFF.tmp\casper\filesystem.squashfs
09-29 18:29 DEBUG  Distro:   checking whether C:\Users\Evan\AppData\Local\Temp\pyl5CFF.tmp is a valid Xubuntu CD
09-29 18:29 DEBUG  Distro:     does not contain C:\Users\Evan\AppData\Local\Temp\pyl5CFF.tmp\casper\filesystem.squashfs
09-29 18:29 DEBUG  Distro:   checking whether C:\Users\Evan\AppData\Local\Temp\pyl5CFF.tmp is a valid Mythbuntu CD
09-29 18:29 DEBUG  Distro:     does not contain C:\Users\Evan\AppData\Local\Temp\pyl5CFF.tmp\casper\filesystem.squashfs
09-29 18:29 DEBUG  Distro:   checking whether C:\Users\Evan\AppData\Local\Temp\pyl5CFF.tmp is a valid Mythbuntu CD
09-29 18:29 DEBUG  Distro:     does not contain C:\Users\Evan\AppData\Local\Temp\pyl5CFF.tmp\casper\filesystem.squashfs
09-29 18:29 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
09-29 18:29 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-29 18:29 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
09-29 18:29 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-29 18:29 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
09-29 18:29 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-29 18:29 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
09-29 18:29 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-29 18:29 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
09-29 18:29 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-29 18:29 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
09-29 18:29 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-29 18:29 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
09-29 18:29 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-29 18:29 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
09-29 18:29 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-29 18:29 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
09-29 18:29 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-29 18:29 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
09-29 18:29 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-29 18:29 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
09-29 18:29 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-29 18:29 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook CD
09-29 18:29 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-29 18:29 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
09-29 18:29 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-29 18:29 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
09-29 18:29 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-29 18:29 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
09-29 18:29 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-29 18:29 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
09-29 18:29 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-29 18:29 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
09-29 18:29 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-29 18:29 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
09-29 18:29 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-29 18:29 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
09-29 18:29 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-29 18:29 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
09-29 18:29 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-29 18:29 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu Netbook CD
09-29 18:29 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-29 18:29 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
09-29 18:29 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-29 18:29 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
09-29 18:29 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-29 18:29 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
09-29 18:29 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-29 18:29 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
09-29 18:29 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-29 18:29 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
09-29 18:29 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-29 18:29 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
09-29 18:29 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-29 18:29 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
09-29 18:29 DEBUG  Distro:   parsing info from str=Ubuntu 11.04 "Natty Narwhal" - Release i386 (20110427.1)
09-29 18:29 DEBUG  Distro:   parsed info={'name': 'Ubuntu',  'subversion': 'Release', 'version': '11.04', 'build': '20110427.1',  'codename': 'Natty Narwhal', 'arch': 'i386'}
09-29 18:29 INFO   Distro: Found a valid CD for Ubuntu: G:\
09-29 18:29 INFO   root: Running the CD menu...
09-29 18:29 DEBUG  WindowsFrontend: __init__...
09-29 18:29 DEBUG  WindowsFrontend: on_init...
09-29 18:29 INFO   WinuiPage: appname=wubi,  localedir=C:\Users\Evan\AppData\Local\Temp\pyl5CFF.tmp\translations,  languages=['id_ID', 'id']
09-29 18:29 INFO   WinuiPage: appname=wubi,  localedir=C:\Users\Evan\AppData\Local\Temp\pyl5CFF.tmp\translations,  languages=['id_ID', 'id']
09-29 18:29 INFO   root: CD menu finished
09-29 18:29 INFO   root: Already installed, running the uninstaller...
09-29 18:29 INFO   root: Running the uninstaller...
09-29 18:29 INFO   CommonBackend: This is the uninstaller running
09-29 18:29 INFO   WinuiPage: appname=wubi,  localedir=C:\Users\Evan\AppData\Local\Temp\pyl5CFF.tmp\translations,  languages=['id_ID', 'id']
09-29 18:29 INFO   root: Received settings
09-29 18:29 INFO   WinuiPage: appname=wubi,  localedir=C:\Users\Evan\AppData\Local\Temp\pyl5CFF.tmp\translations,  languages=['id_ID', 'id']
09-29 18:29 DEBUG  TaskList: # Running tasklist...
09-29 18:29 DEBUG  TaskList: ## Running Salin ISO...
09-29 18:29 DEBUG  TaskList: ## Finished Salin ISO
09-29 18:29 DEBUG  TaskList: ## Running Hapus entri bootloader...
09-29 18:29 DEBUG  WindowsBackend: Could not find bcd id
09-29 18:29 DEBUG  WindowsBackend: undo_bootini C:
09-29 18:29 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 119457.511719 mb free ntfs)
09-29 18:29 DEBUG  WindowsBackend: undo_bootini D:
09-29 18:29 DEBUG  WindowsBackend: undo_configsys Drive(D: hd 2872.41796875 mb free ntfs)
09-29 18:29 DEBUG  WindowsBackend: undo_bootini E:
09-29 18:29 DEBUG  WindowsBackend: undo_configsys Drive(E: hd 99.328125 mb free fat32)
09-29 18:29 DEBUG  WindowsBackend: undo_bootini H:
09-29 18:29 DEBUG  WindowsBackend: undo_configsys Drive(H: hd 76814.8203125 mb free ntfs)
09-29 18:29 DEBUG  WindowsBackend: undo_bootini I:
09-29 18:29 DEBUG  WindowsBackend: undo_configsys Drive(I: hd 19285.8671875 mb free ntfs)
09-29 18:29 DEBUG  WindowsBackend: undo_bootini K:
09-29 18:29 DEBUG  WindowsBackend: undo_configsys Drive(K: removable 710.19921875 mb free fat32)
09-29 18:29 DEBUG  TaskList: ## Finished Hapus entri bootloader
09-29 18:29 DEBUG  TaskList: ## Running Hapus direktori tujuan...
09-29 18:29 DEBUG  CommonBackend: Deleting I:\ubuntu
09-29 18:29 DEBUG  TaskList: ## Finished Hapus direktori tujuan
09-29 18:29 DEBUG  TaskList: ## Running Hapus kunci registy...
09-29 18:29 DEBUG  TaskList: ## Finished Hapus kunci registy
09-29 18:29 DEBUG  TaskList: # Finished tasklist
09-29 18:29 INFO   root: Almost finished uninstalling
09-29 18:29 INFO   root: Finished uninstallation
09-29 18:29 DEBUG  CommonBackend: Fetching basic info...
09-29 18:29 DEBUG  CommonBackend: original_exe=G:\wubi.exe
09-29 18:29 DEBUG  CommonBackend: platform=win32
09-29 18:29 DEBUG  CommonBackend: osname=nt
09-29 18:29 DEBUG  WindowsBackend: arch=amd64
09-29 18:29 DEBUG  CommonBackend: Parsing isolist=C:\Users\Evan\AppData\Local\Temp\pyl5CFF.tmp\data\isolist.ini
09-29 18:29 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
09-29 18:29 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
09-29 18:29 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
09-29 18:29 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
09-29 18:29 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
09-29 18:29 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
09-29 18:29 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
09-29 18:29 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
09-29 18:29 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
09-29 18:29 DEBUG  WindowsBackend: Fetching host info...
09-29 18:29 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
09-29 18:29 DEBUG  WindowsBackend: windows version=vista
09-29 18:29 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium
09-29 18:29 DEBUG  WindowsBackend: windows_sp=Service Pack 1
09-29 18:29 DEBUG  WindowsBackend: windows_build=7601
09-29 18:29 DEBUG  WindowsBackend: gmt=7
09-29 18:29 DEBUG  WindowsBackend: country=ID
09-29 18:29 DEBUG  WindowsBackend: timezone=Asia/Jakarta
09-29 18:29 DEBUG  WindowsBackend: windows_username=Evan
09-29 18:29 DEBUG  WindowsBackend: user_full_name=Evan
09-29 18:29 DEBUG  WindowsBackend: user_directory=C:\Users\Evan
09-29 18:29 DEBUG  WindowsBackend: windows_language_code=1057
09-29 18:29 DEBUG  WindowsBackend: windows_language=Indonesian
09-29 18:29 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM) i3 CPU       M 330  @ 2.13GHz
09-29 18:29 DEBUG  WindowsBackend: bootloader=vista
09-29 18:29 DEBUG  WindowsBackend: system_drive=Drive(C: hd 119457.554688 mb free ntfs)
09-29 18:29 DEBUG  WindowsBackend: drive=Drive(C: hd 119457.554688 mb free ntfs)
09-29 18:29 DEBUG  WindowsBackend: drive=Drive(D: hd 2872.41796875 mb free ntfs)
09-29 18:29 DEBUG  WindowsBackend: drive=Drive(E: hd 99.328125 mb free fat32)
09-29 18:29 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free )
09-29 18:29 DEBUG  WindowsBackend: drive=Drive(G: cd 0.0 mb free cdfs)
09-29 18:29 DEBUG  WindowsBackend: drive=Drive(H: hd 76814.8203125 mb free ntfs)
09-29 18:29 DEBUG  WindowsBackend: drive=Drive(I: hd 19989.8984375 mb free ntfs)
09-29 18:29 DEBUG  WindowsBackend: drive=Drive(J: cd 0.0 mb free cdfs)
09-29 18:29 DEBUG  WindowsBackend: drive=Drive(K: removable 710.19921875 mb free fat32)
09-29 18:29 DEBUG  WindowsBackend: uninstaller_path=None
09-29 18:29 DEBUG  WindowsBackend: previous_target_dir=None
09-29 18:29 DEBUG  WindowsBackend: previous_distro_name=None
09-29 18:29 DEBUG  WindowsBackend: keyboard_id=67699721
09-29 18:29 DEBUG  WindowsBackend: keyboard_layout=us
09-29 18:29 DEBUG  WindowsBackend: keyboard_variant=
09-29 18:29 DEBUG  WindowsBackend: total_memory_mb=1910.83984375
09-29 18:29 DEBUG  CommonBackend: Searching ISOs on USB devices
09-29 18:29 DEBUG  CommonBackend: Searching for local CDs
09-29 18:29 DEBUG  Distro:   checking whether C:\Users\Evan\AppData\Local\Temp\pyl5CFF.tmp is a valid Ubuntu CD
09-29 18:29 DEBUG  Distro:     does not contain C:\Users\Evan\AppData\Local\Temp\pyl5CFF.tmp\casper\filesystem.squashfs
09-29 18:29 DEBUG  Distro:   checking whether C:\Users\Evan\AppData\Local\Temp\pyl5CFF.tmp is a valid Ubuntu CD
09-29 18:29 DEBUG  Distro:     does not contain C:\Users\Evan\AppData\Local\Temp\pyl5CFF.tmp\casper\filesystem.squashfs
09-29 18:29 DEBUG  Distro:   checking whether C:\Users\Evan\AppData\Local\Temp\pyl5CFF.tmp is a valid Ubuntu Netbook CD
09-29 18:29 DEBUG  Distro:     does not contain C:\Users\Evan\AppData\Local\Temp\pyl5CFF.tmp\casper\filesystem.squashfs
09-29 18:29 DEBUG  Distro:   checking whether C:\Users\Evan\AppData\Local\Temp\pyl5CFF.tmp is a valid Kubuntu CD
09-29 18:29 DEBUG  Distro:     does not contain C:\Users\Evan\AppData\Local\Temp\pyl5CFF.tmp\casper\filesystem.squashfs
09-29 18:29 DEBUG  Distro:   checking whether C:\Users\Evan\AppData\Local\Temp\pyl5CFF.tmp is a valid Kubuntu CD
09-29 18:29 DEBUG  Distro:     does not contain C:\Users\Evan\AppData\Local\Temp\pyl5CFF.tmp\casper\filesystem.squashfs
09-29 18:29 DEBUG  Distro:   checking whether C:\Users\Evan\AppData\Local\Temp\pyl5CFF.tmp is a valid Xubuntu CD
09-29 18:29 DEBUG  Distro:     does not contain C:\Users\Evan\AppData\Local\Temp\pyl5CFF.tmp\casper\filesystem.squashfs
09-29 18:29 DEBUG  Distro:   checking whether C:\Users\Evan\AppData\Local\Temp\pyl5CFF.tmp is a valid Xubuntu CD
09-29 18:29 DEBUG  Distro:     does not contain C:\Users\Evan\AppData\Local\Temp\pyl5CFF.tmp\casper\filesystem.squashfs
09-29 18:29 DEBUG  Distro:   checking whether C:\Users\Evan\AppData\Local\Temp\pyl5CFF.tmp is a valid Mythbuntu CD
09-29 18:29 DEBUG  Distro:     does not contain C:\Users\Evan\AppData\Local\Temp\pyl5CFF.tmp\casper\filesystem.squashfs
09-29 18:29 DEBUG  Distro:   checking whether C:\Users\Evan\AppData\Local\Temp\pyl5CFF.tmp is a valid Mythbuntu CD
09-29 18:29 DEBUG  Distro:     does not contain C:\Users\Evan\AppData\Local\Temp\pyl5CFF.tmp\casper\filesystem.squashfs
09-29 18:29 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
09-29 18:29 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-29 18:29 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
09-29 18:29 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-29 18:29 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
09-29 18:29 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-29 18:29 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
09-29 18:29 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-29 18:29 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
09-29 18:29 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-29 18:29 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
09-29 18:29 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-29 18:29 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
09-29 18:29 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-29 18:29 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
09-29 18:29 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-29 18:29 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
09-29 18:29 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-29 18:29 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
09-29 18:29 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-29 18:29 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
09-29 18:29 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-29 18:29 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook CD
09-29 18:29 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-29 18:29 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
09-29 18:29 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-29 18:29 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
09-29 18:29 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-29 18:29 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
09-29 18:29 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-29 18:29 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
09-29 18:29 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-29 18:29 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
09-29 18:29 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-29 18:29 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
09-29 18:29 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-29 18:29 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
09-29 18:29 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-29 18:29 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
09-29 18:29 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-29 18:29 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu Netbook CD
09-29 18:29 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-29 18:29 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
09-29 18:29 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-29 18:29 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
09-29 18:29 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-29 18:29 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
09-29 18:29 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-29 18:29 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
09-29 18:29 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-29 18:29 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
09-29 18:29 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-29 18:29 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
09-29 18:29 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-29 18:29 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
09-29 18:29 INFO   Distro: Found a valid CD for Ubuntu: G:\
09-29 18:29 INFO   root: Running the installer...
09-29 18:29 INFO   WinuiPage: appname=wubi,  localedir=C:\Users\Evan\AppData\Local\Temp\pyl5CFF.tmp\translations,  languages=['id_ID', 'id']
09-29 18:29 INFO   WinuiPage: appname=wubi,  localedir=C:\Users\Evan\AppData\Local\Temp\pyl5CFF.tmp\translations,  languages=['id_ID', 'id']
09-29 18:29 INFO   WindowsFrontend: Operation cancelled
09-29 18:29 DEBUG  WindowsFrontend: frontend.quit
09-29 18:29 DEBUG  WindowsFrontend: frontend.on_quit
09-29 18:29 DEBUG  root: application.on_quit
09-29 18:29 INFO   root: sys.exit
09-29 18:29 INFO   root: === wubi 11.04 rev211 ===
09-29 18:29 DEBUG  root: Logfile is c:\users\evan\appdata\local\temp\wubi-11.04-rev211.log
09-29 18:29 DEBUG  root: sys.argv = ['main.pyo', '--exefile="G:\\wubi.exe"']
09-29 18:29 DEBUG  CommonBackend: data_dir=C:\Users\Evan\AppData\Local\Temp\pylD70E.tmp\data
09-29 18:29 DEBUG  WindowsBackend: 7z=C:\Users\Evan\AppData\Local\Temp\pylD70E.tmp\bin\7z.exe
09-29 18:29 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
09-29 18:29 DEBUG  CommonBackend: Fetching basic info...
09-29 18:29 DEBUG  CommonBackend: original_exe=G:\wubi.exe
09-29 18:29 DEBUG  CommonBackend: platform=win32
09-29 18:29 DEBUG  CommonBackend: osname=nt
09-29 18:29 DEBUG  CommonBackend: language=id_ID
09-29 18:29 DEBUG  CommonBackend: encoding=cp1252
09-29 18:29 DEBUG  WindowsBackend: arch=amd64
09-29 18:29 DEBUG  CommonBackend: Parsing isolist=C:\Users\Evan\AppData\Local\Temp\pylD70E.tmp\data\isolist.ini
09-29 18:29 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
09-29 18:29 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
09-29 18:29 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
09-29 18:29 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
09-29 18:29 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
09-29 18:29 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
09-29 18:29 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
09-29 18:29 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
09-29 18:29 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
09-29 18:29 DEBUG  WindowsBackend: Fetching host info...
09-29 18:29 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
09-29 18:29 DEBUG  WindowsBackend: windows version=vista
09-29 18:29 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium
09-29 18:29 DEBUG  WindowsBackend: windows_sp=Service Pack 1
09-29 18:29 DEBUG  WindowsBackend: windows_build=7601
09-29 18:29 DEBUG  WindowsBackend: gmt=7
09-29 18:29 DEBUG  WindowsBackend: country=ID
09-29 18:29 DEBUG  WindowsBackend: timezone=Asia/Jakarta
09-29 18:29 DEBUG  WindowsBackend: windows_username=Evan
09-29 18:29 DEBUG  WindowsBackend: user_full_name=Evan
09-29 18:29 DEBUG  WindowsBackend: user_directory=C:\Users\Evan
09-29 18:29 DEBUG  WindowsBackend: windows_language_code=1057
09-29 18:29 DEBUG  WindowsBackend: windows_language=Indonesian
09-29 18:29 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM) i3 CPU       M 330  @ 2.13GHz
09-29 18:29 DEBUG  WindowsBackend: bootloader=vista
09-29 18:29 DEBUG  WindowsBackend: system_drive=Drive(C: hd 119457.023438 mb free ntfs)
09-29 18:29 DEBUG  WindowsBackend: drive=Drive(C: hd 119457.023438 mb free ntfs)
09-29 18:29 DEBUG  WindowsBackend: drive=Drive(D: hd 2872.41796875 mb free ntfs)
09-29 18:29 DEBUG  WindowsBackend: drive=Drive(E: hd 99.328125 mb free fat32)
09-29 18:29 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free )
09-29 18:29 DEBUG  WindowsBackend: drive=Drive(G: cd 0.0 mb free cdfs)
09-29 18:29 DEBUG  WindowsBackend: drive=Drive(H: hd 76814.8203125 mb free ntfs)
09-29 18:29 DEBUG  WindowsBackend: drive=Drive(I: hd 19989.8984375 mb free ntfs)
09-29 18:29 DEBUG  WindowsBackend: drive=Drive(J: cd 0.0 mb free cdfs)
09-29 18:29 DEBUG  WindowsBackend: drive=Drive(K: removable 710.19921875 mb free fat32)
09-29 18:29 DEBUG  WindowsBackend: uninstaller_path=None
09-29 18:29 DEBUG  WindowsBackend: previous_target_dir=None
09-29 18:29 DEBUG  WindowsBackend: previous_distro_name=None
09-29 18:29 DEBUG  WindowsBackend: keyboard_id=67699721
09-29 18:29 DEBUG  WindowsBackend: keyboard_layout=us
09-29 18:29 DEBUG  WindowsBackend: keyboard_variant=
09-29 18:29 DEBUG  CommonBackend: python locale=('id_ID', 'cp1252')
09-29 18:29 DEBUG  CommonBackend: locale=id_ID.UTF-8
09-29 18:29 DEBUG  WindowsBackend: total_memory_mb=1910.83984375
09-29 18:29 DEBUG  CommonBackend: Searching ISOs on USB devices
09-29 18:29 DEBUG  CommonBackend: Searching for local CDs
09-29 18:29 DEBUG  Distro:   checking whether C:\Users\Evan\AppData\Local\Temp\pylD70E.tmp is a valid Ubuntu CD
09-29 18:29 DEBUG  Distro:     does not contain C:\Users\Evan\AppData\Local\Temp\pylD70E.tmp\casper\filesystem.squashfs
09-29 18:29 DEBUG  Distro:   checking whether C:\Users\Evan\AppData\Local\Temp\pylD70E.tmp is a valid Ubuntu CD
09-29 18:29 DEBUG  Distro:     does not contain C:\Users\Evan\AppData\Local\Temp\pylD70E.tmp\casper\filesystem.squashfs
09-29 18:29 DEBUG  Distro:   checking whether C:\Users\Evan\AppData\Local\Temp\pylD70E.tmp is a valid Ubuntu Netbook CD
09-29 18:29 DEBUG  Distro:     does not contain C:\Users\Evan\AppData\Local\Temp\pylD70E.tmp\casper\filesystem.squashfs
09-29 18:29 DEBUG  Distro:   checking whether C:\Users\Evan\AppData\Local\Temp\pylD70E.tmp is a valid Kubuntu CD
09-29 18:29 DEBUG  Distro:     does not contain C:\Users\Evan\AppData\Local\Temp\pylD70E.tmp\casper\filesystem.squashfs
09-29 18:29 DEBUG  Distro:   checking whether C:\Users\Evan\AppData\Local\Temp\pylD70E.tmp is a valid Kubuntu CD
09-29 18:29 DEBUG  Distro:     does not contain C:\Users\Evan\AppData\Local\Temp\pylD70E.tmp\casper\filesystem.squashfs
09-29 18:29 DEBUG  Distro:   checking whether C:\Users\Evan\AppData\Local\Temp\pylD70E.tmp is a valid Xubuntu CD
09-29 18:29 DEBUG  Distro:     does not contain C:\Users\Evan\AppData\Local\Temp\pylD70E.tmp\casper\filesystem.squashfs
09-29 18:29 DEBUG  Distro:   checking whether C:\Users\Evan\AppData\Local\Temp\pylD70E.tmp is a valid Xubuntu CD
09-29 18:29 DEBUG  Distro:     does not contain C:\Users\Evan\AppData\Local\Temp\pylD70E.tmp\casper\filesystem.squashfs
09-29 18:29 DEBUG  Distro:   checking whether C:\Users\Evan\AppData\Local\Temp\pylD70E.tmp is a valid Mythbuntu CD
09-29 18:29 DEBUG  Distro:     does not contain C:\Users\Evan\AppData\Local\Temp\pylD70E.tmp\casper\filesystem.squashfs
09-29 18:29 DEBUG  Distro:   checking whether C:\Users\Evan\AppData\Local\Temp\pylD70E.tmp is a valid Mythbuntu CD
09-29 18:29 DEBUG  Distro:     does not contain C:\Users\Evan\AppData\Local\Temp\pylD70E.tmp\casper\filesystem.squashfs
09-29 18:29 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
09-29 18:29 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-29 18:29 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
09-29 18:29 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-29 18:29 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
09-29 18:29 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-29 18:29 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
09-29 18:29 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-29 18:29 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
09-29 18:29 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-29 18:29 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
09-29 18:29 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-29 18:29 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
09-29 18:29 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-29 18:29 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
09-29 18:29 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-29 18:29 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
09-29 18:29 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-29 18:29 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
09-29 18:29 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-29 18:29 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
09-29 18:29 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-29 18:29 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook CD
09-29 18:29 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-29 18:29 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
09-29 18:29 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-29 18:29 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
09-29 18:29 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-29 18:29 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
09-29 18:29 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-29 18:29 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
09-29 18:29 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-29 18:29 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
09-29 18:29 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-29 18:29 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
09-29 18:29 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-29 18:29 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
09-29 18:29 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-29 18:29 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
09-29 18:29 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-29 18:29 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu Netbook CD
09-29 18:29 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-29 18:29 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
09-29 18:29 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-29 18:29 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
09-29 18:29 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-29 18:29 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
09-29 18:29 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-29 18:29 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
09-29 18:29 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-29 18:29 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
09-29 18:29 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-29 18:29 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
09-29 18:29 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-29 18:29 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
09-29 18:29 DEBUG  Distro:   parsing info from str=Ubuntu 11.04 "Natty Narwhal" - Release i386 (20110427.1)
09-29 18:29 DEBUG  Distro:   parsed info={'name': 'Ubuntu',  'subversion': 'Release', 'version': '11.04', 'build': '20110427.1',  'codename': 'Natty Narwhal', 'arch': 'i386'}
09-29 18:29 INFO   Distro: Found a valid CD for Ubuntu: G:\
09-29 18:29 INFO   root: Running the CD menu...
09-29 18:29 DEBUG  WindowsFrontend: __init__...
09-29 18:29 DEBUG  WindowsFrontend: on_init...
09-29 18:29 INFO   WinuiPage: appname=wubi,  localedir=C:\Users\Evan\AppData\Local\Temp\pylD70E.tmp\translations,  languages=['id_ID', 'id']
09-29 18:29 INFO   WinuiPage: appname=wubi,  localedir=C:\Users\Evan\AppData\Local\Temp\pylD70E.tmp\translations,  languages=['id_ID', 'id']
09-29 18:29 INFO   root: CD menu finished
09-29 18:29 INFO   root: Running the installer...
09-29 18:29 INFO   WinuiPage: appname=wubi,  localedir=C:\Users\Evan\AppData\Local\Temp\pylD70E.tmp\translations,  languages=['id_ID', 'id']
09-29 18:29 INFO   WinuiPage: appname=wubi,  localedir=C:\Users\Evan\AppData\Local\Temp\pylD70E.tmp\translations,  languages=['id_ID', 'id']
09-29 18:30 DEBUG  WinuiInstallationPage: target_drive=I:,  installation_size=17000MB, distro_name=Ubuntu, language=en_US,  locale=en_US.UTF-8, username=evan
09-29 18:30 INFO   root: Received settings
09-29 18:30 INFO   WinuiPage: appname=wubi,  localedir=C:\Users\Evan\AppData\Local\Temp\pylD70E.tmp\translations,  languages=['en_US', 'en']
09-29 18:30 DEBUG  TaskList: # Running tasklist...
09-29 18:30 DEBUG  TaskList: ## Running select_target_dir...
09-29 18:30 INFO   WindowsBackend: Installing into I:\ubuntu
09-29 18:30 DEBUG  TaskList: ## Finished select_target_dir
09-29 18:30 DEBUG  TaskList: ## Running create_dir_structure...
09-29 18:30 DEBUG  CommonBackend: Creating dir I:\ubuntu
09-29 18:30 DEBUG  CommonBackend: Creating dir I:\ubuntu\disks
09-29 18:30 DEBUG  CommonBackend: Creating dir I:\ubuntu\install
09-29 18:30 DEBUG  CommonBackend: Creating dir I:\ubuntu\install\boot
09-29 18:30 DEBUG  CommonBackend: Creating dir I:\ubuntu\disks\boot
09-29 18:30 DEBUG  CommonBackend: Creating dir I:\ubuntu\disks\boot\grub
09-29 18:30 DEBUG  CommonBackend: Creating dir I:\ubuntu\install\boot\grub
09-29 18:30 DEBUG  TaskList: ## Finished create_dir_structure
09-29 18:30 DEBUG  TaskList: ## Running uncompress_target_dir...
09-29 18:30 DEBUG  TaskList: ## Finished uncompress_target_dir
09-29 18:30 DEBUG  TaskList: ## Running create_uninstaller...
09-29 18:30 DEBUG  WindowsBackend: Copying uninstaller G:\wubi.exe -> I:\ubuntu\uninstall-wubi.exe
09-29 18:30 DEBUG  registry: Setting registry key -2147483646  Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString  I:\ubuntu\uninstall-wubi.exe
09-29 18:30 DEBUG  registry: Setting registry key -2147483646  Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir  I:\ubuntu
09-29 18:30 DEBUG  registry: Setting registry key -2147483646  Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName  Ubuntu
09-29 18:30 DEBUG  registry: Setting registry key -2147483646  Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon  I:\ubuntu\Ubuntu.ico
09-29 18:30 DEBUG  registry: Setting registry key -2147483646  Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion  11.04-rev211
09-29 18:30 DEBUG  registry: Setting registry key -2147483646  Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher  Ubuntu
09-29 18:30 DEBUG  registry: Setting registry key -2147483646  Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com]("http://www.ubuntu.com/")
09-29 18:30 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
09-29 18:30 DEBUG  TaskList: ## Finished create_uninstaller
09-29 18:30 DEBUG  TaskList: ## Running copy_installation_files...
09-29 18:30 DEBUG  WindowsBackend: Copying  C:\Users\Evan\AppData\Local\Temp\pylD70E.tmp\data\custom-installation  -> I:\ubuntu\install\custom-installation
09-29 18:30 DEBUG  WindowsBackend: Copying C:\Users\Evan\AppData\Local\Temp\pylD70E.tmp\winboot -> I:\ubuntu\winboot
09-29 18:30 DEBUG  WindowsBackend: Copying  C:\Users\Evan\AppData\Local\Temp\pylD70E.tmp\data\images\Ubuntu.ico  -> I:\ubuntu\Ubuntu.ico
09-29 18:30 DEBUG  TaskList: ## Finished copy_installation_files
09-29 18:30 DEBUG  TaskList: ## Running get_iso...
09-29 18:30 DEBUG  TaskList: New task copy_file
09-29 18:30 DEBUG  TaskList: ### Running copy_file...
09-29 18:30 ERROR  TaskList: [Errno 13] Permission denied
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\utils.py", line 208, in copy_file
IOError: [Errno 13] Permission denied
09-29 18:30 DEBUG  TaskList: # Cancelling tasklist
09-29 18:30 DEBUG  TaskList: New task check_iso
09-29 18:30 ERROR  root: [Errno 13] Permission denied
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 57, in run
  File "\lib\wubi\application.py", line 129, in select_task
  File "\lib\wubi\application.py", line 195, in run_cd_menu
  File "\lib\wubi\application.py", line 119, in select_task
  File "\lib\wubi\application.py", line 157, in run_installer
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\utils.py", line 208, in copy_file
IOError: [Errno 13] Permission denied
09-29 18:30 DEBUG  CommonBackend: Searching for local ISO
09-29 18:30 DEBUG  CommonBackend: Could not find any ISO or CD, downloading one now
09-29 18:30 DEBUG  TaskList: New task get_metalink
09-29 18:30 ERROR  TaskList: Cannot download the metalink and therefore the ISO
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 492, in get_iso
  File "\lib\wubi\backends\common\backend.py", line 330, in download_iso
Exception: Cannot download the metalink and therefore the ISO
09-29 18:30 DEBUG  TaskList: # Cancelling tasklist
09-29 18:30 DEBUG  TaskList: # Finished tasklist
10-09 15:31 INFO   root: === wubi 11.04 rev211 ===
10-09 15:31 DEBUG  root: Logfile is c:\users\evan\appdata\local\temp\wubi-11.04-rev211.log
10-09 15:31 DEBUG  root: sys.argv = ['main.pyo', '--exefile="G:\\wubi.exe"']
10-09 15:31 DEBUG  CommonBackend: data_dir=C:\Users\Evan\AppData\Local\Temp\pylD25B.tmp\data
10-09 15:31 DEBUG  WindowsBackend: 7z=C:\Users\Evan\AppData\Local\Temp\pylD25B.tmp\bin\7z.exe
10-09 15:31 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
10-09 15:31 DEBUG  CommonBackend: Fetching basic info...
10-09 15:31 DEBUG  CommonBackend: original_exe=G:\wubi.exe
10-09 15:31 DEBUG  CommonBackend: platform=win32
10-09 15:31 DEBUG  CommonBackend: osname=nt
10-09 15:31 DEBUG  CommonBackend: language=id_ID
10-09 15:31 DEBUG  CommonBackend: encoding=cp1252
10-09 15:31 DEBUG  WindowsBackend: arch=amd64
10-09 15:31 DEBUG  CommonBackend: Parsing isolist=C:\Users\Evan\AppData\Local\Temp\pylD25B.tmp\data\isolist.ini
10-09 15:31 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
10-09 15:31 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
10-09 15:31 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
10-09 15:31 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
10-09 15:31 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
10-09 15:31 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
10-09 15:31 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
10-09 15:31 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
10-09 15:31 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
10-09 15:31 DEBUG  WindowsBackend: Fetching host info...
10-09 15:31 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
10-09 15:31 DEBUG  WindowsBackend: windows version=vista
10-09 15:31 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium
10-09 15:31 DEBUG  WindowsBackend: windows_sp=Service Pack 1
10-09 15:31 DEBUG  WindowsBackend: windows_build=7601
10-09 15:31 DEBUG  WindowsBackend: gmt=7
10-09 15:31 DEBUG  WindowsBackend: country=ID
10-09 15:31 DEBUG  WindowsBackend: timezone=Asia/Jakarta
10-09 15:31 DEBUG  WindowsBackend: windows_username=Evan
10-09 15:31 DEBUG  WindowsBackend: user_full_name=Evan
10-09 15:31 DEBUG  WindowsBackend: user_directory=C:\Users\Evan
10-09 15:31 DEBUG  WindowsBackend: windows_language_code=1057
10-09 15:31 DEBUG  WindowsBackend: windows_language=Indonesian
10-09 15:31 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM) i3 CPU       M 330  @ 2.13GHz
10-09 15:31 DEBUG  WindowsBackend: bootloader=vista
10-09 15:31 DEBUG  WindowsBackend: system_drive=Drive(C: hd 118691.132813 mb free ntfs)
10-09 15:31 DEBUG  WindowsBackend: drive=Drive(C: hd 118691.132813 mb free ntfs)
10-09 15:31 DEBUG  WindowsBackend: drive=Drive(D: hd 2872.41796875 mb free ntfs)
10-09 15:31 DEBUG  WindowsBackend: drive=Drive(E: hd 99.328125 mb free fat32)
10-09 15:31 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free cdfs)
10-09 15:31 DEBUG  WindowsBackend: drive=Drive(G: cd 0.0 mb free cdfs)
10-09 15:31 DEBUG  WindowsBackend: drive=Drive(H: removable 0.0 mb free )
10-09 15:31 DEBUG  WindowsBackend: drive=Drive(I: hd 19486.2539063 mb free ntfs)
10-09 15:31 DEBUG  WindowsBackend: drive=Drive(J: hd 76814.8203125 mb free ntfs)
10-09 15:31 DEBUG  WindowsBackend: uninstaller_path=I:\ubuntu\uninstall-wubi.exe
10-09 15:31 DEBUG  WindowsBackend: previous_target_dir=I:\ubuntu
10-09 15:31 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
10-09 15:31 DEBUG  WindowsBackend: keyboard_id=67699721
10-09 15:31 DEBUG  WindowsBackend: keyboard_layout=us
10-09 15:31 DEBUG  WindowsBackend: keyboard_variant=
10-09 15:31 DEBUG  CommonBackend: python locale=('id_ID', 'cp1252')
10-09 15:31 DEBUG  CommonBackend: locale=id_ID.UTF-8
10-09 15:31 DEBUG  WindowsBackend: total_memory_mb=1910.83984375
10-09 15:31 DEBUG  CommonBackend: Searching ISOs on USB devices
10-09 15:31 DEBUG  CommonBackend: Searching for local CDs
10-09 15:31 DEBUG  Distro:   checking whether C:\Users\Evan\AppData\Local\Temp\pylD25B.tmp is a valid Ubuntu CD
10-09 15:31 DEBUG  Distro:     does not contain C:\Users\Evan\AppData\Local\Temp\pylD25B.tmp\casper\filesystem.squashfs
10-09 15:31 DEBUG  Distro:   checking whether C:\Users\Evan\AppData\Local\Temp\pylD25B.tmp is a valid Ubuntu CD
10-09 15:31 DEBUG  Distro:     does not contain C:\Users\Evan\AppData\Local\Temp\pylD25B.tmp\casper\filesystem.squashfs
10-09 15:31 DEBUG  Distro:   checking whether C:\Users\Evan\AppData\Local\Temp\pylD25B.tmp is a valid Ubuntu Netbook CD
10-09 15:31 DEBUG  Distro:     does not contain C:\Users\Evan\AppData\Local\Temp\pylD25B.tmp\casper\filesystem.squashfs
10-09 15:31 DEBUG  Distro:   checking whether C:\Users\Evan\AppData\Local\Temp\pylD25B.tmp is a valid Kubuntu CD
10-09 15:31 DEBUG  Distro:     does not contain C:\Users\Evan\AppData\Local\Temp\pylD25B.tmp\casper\filesystem.squashfs
10-09 15:31 DEBUG  Distro:   checking whether C:\Users\Evan\AppData\Local\Temp\pylD25B.tmp is a valid Kubuntu CD
10-09 15:31 DEBUG  Distro:     does not contain C:\Users\Evan\AppData\Local\Temp\pylD25B.tmp\casper\filesystem.squashfs
10-09 15:31 DEBUG  Distro:   checking whether C:\Users\Evan\AppData\Local\Temp\pylD25B.tmp is a valid Xubuntu CD
10-09 15:31 DEBUG  Distro:     does not contain C:\Users\Evan\AppData\Local\Temp\pylD25B.tmp\casper\filesystem.squashfs
10-09 15:31 DEBUG  Distro:   checking whether C:\Users\Evan\AppData\Local\Temp\pylD25B.tmp is a valid Xubuntu CD
10-09 15:31 DEBUG  Distro:     does not contain C:\Users\Evan\AppData\Local\Temp\pylD25B.tmp\casper\filesystem.squashfs
10-09 15:31 DEBUG  Distro:   checking whether C:\Users\Evan\AppData\Local\Temp\pylD25B.tmp is a valid Mythbuntu CD
10-09 15:31 DEBUG  Distro:     does not contain C:\Users\Evan\AppData\Local\Temp\pylD25B.tmp\casper\filesystem.squashfs
10-09 15:31 DEBUG  Distro:   checking whether C:\Users\Evan\AppData\Local\Temp\pylD25B.tmp is a valid Mythbuntu CD
10-09 15:31 DEBUG  Distro:     does not contain C:\Users\Evan\AppData\Local\Temp\pylD25B.tmp\casper\filesystem.squashfs
10-09 15:31 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
10-09 15:31 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-09 15:31 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
10-09 15:31 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-09 15:31 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
10-09 15:31 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-09 15:31 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
10-09 15:31 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-09 15:31 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
10-09 15:31 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-09 15:31 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
10-09 15:31 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-09 15:31 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
10-09 15:31 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-09 15:31 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
10-09 15:31 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-09 15:31 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
10-09 15:31 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-09 15:31 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
10-09 15:31 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-09 15:31 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
10-09 15:31 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-09 15:31 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook CD
10-09 15:31 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-09 15:31 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
10-09 15:31 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-09 15:31 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
10-09 15:31 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-09 15:31 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
10-09 15:31 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-09 15:31 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
10-09 15:31 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-09 15:31 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
10-09 15:31 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-09 15:31 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
10-09 15:31 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-09 15:31 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
10-09 15:31 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-09 15:31 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
10-09 15:31 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-09 15:31 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu Netbook CD
10-09 15:31 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-09 15:31 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
10-09 15:31 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-09 15:31 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
10-09 15:31 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-09 15:31 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
10-09 15:31 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-09 15:31 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
10-09 15:31 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-09 15:31 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
10-09 15:31 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-09 15:31 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
10-09 15:31 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-09 15:31 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
10-09 15:31 DEBUG  Distro:   parsing info from str=Ubuntu 11.04 "Natty Narwhal" - Release i386 (20110427.1)
10-09 15:31 DEBUG  Distro:   parsed info={'name': 'Ubuntu',  'subversion': 'Release', 'version': '11.04', 'build': '20110427.1',  'codename': 'Natty Narwhal', 'arch': 'i386'}
10-09 15:31 INFO   Distro: Found a valid CD for Ubuntu: G:\
10-09 15:31 INFO   root: Running the CD menu...
10-09 15:31 DEBUG  WindowsFrontend: __init__...
10-09 15:31 DEBUG  WindowsFrontend: on_init...
10-09 15:31 INFO   WinuiPage: appname=wubi,  localedir=C:\Users\Evan\AppData\Local\Temp\pylD25B.tmp\translations,  languages=['id_ID', 'id']
10-09 15:31 INFO   WinuiPage: appname=wubi,  localedir=C:\Users\Evan\AppData\Local\Temp\pylD25B.tmp\translations,  languages=['id_ID', 'id']
10-09 15:31 INFO   root: CD menu finished
10-09 15:31 INFO   root: Already installed, running the uninstaller...
10-09 15:31 INFO   root: Running the uninstaller...
10-09 15:31 INFO   CommonBackend: This is the uninstaller running
10-09 15:31 INFO   WinuiPage: appname=wubi,  localedir=C:\Users\Evan\AppData\Local\Temp\pylD25B.tmp\translations,  languages=['id_ID', 'id']
10-09 15:31 INFO   root: Received settings
10-09 15:31 INFO   WinuiPage: appname=wubi,  localedir=C:\Users\Evan\AppData\Local\Temp\pylD25B.tmp\translations,  languages=['id_ID', 'id']
10-09 15:31 DEBUG  TaskList: # Running tasklist...
10-09 15:31 DEBUG  TaskList: ## Running Salin ISO...
10-09 15:31 DEBUG  TaskList: ## Finished Salin ISO
10-09 15:31 DEBUG  TaskList: ## Running Hapus entri bootloader...
10-09 15:31 DEBUG  WindowsBackend: Could not find bcd id
10-09 15:31 DEBUG  WindowsBackend: undo_bootini C:
10-09 15:31 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 118691.132813 mb free ntfs)
10-09 15:31 DEBUG  WindowsBackend: undo_bootini D:
10-09 15:31 DEBUG  WindowsBackend: undo_configsys Drive(D: hd 2872.41796875 mb free ntfs)
10-09 15:31 DEBUG  WindowsBackend: undo_bootini E:
10-09 15:31 DEBUG  WindowsBackend: undo_configsys Drive(E: hd 99.328125 mb free fat32)
10-09 15:31 DEBUG  WindowsBackend: undo_bootini H:
10-09 15:31 DEBUG  WindowsBackend: undo_configsys Drive(H: removable 0.0 mb free )
10-09 15:32 DEBUG  WindowsBackend: undo_bootini I:
10-09 15:32 DEBUG  WindowsBackend: undo_configsys Drive(I: hd 19486.2539063 mb free ntfs)
10-09 15:32 DEBUG  WindowsBackend: undo_bootini J:
10-09 15:32 DEBUG  WindowsBackend: undo_configsys Drive(J: hd 76814.8203125 mb free ntfs)
10-09 15:32 DEBUG  TaskList: ## Finished Hapus entri bootloader
10-09 15:32 DEBUG  TaskList: ## Running Hapus direktori tujuan...
10-09 15:32 DEBUG  CommonBackend: Deleting I:\ubuntu
10-09 15:32 DEBUG  TaskList: ## Finished Hapus direktori tujuan
10-09 15:32 DEBUG  TaskList: ## Running Hapus kunci registy...
10-09 15:32 DEBUG  TaskList: ## Finished Hapus kunci registy
10-09 15:32 DEBUG  TaskList: # Finished tasklist
10-09 15:32 INFO   root: Almost finished uninstalling
10-09 15:32 INFO   root: Finished uninstallation
10-09 15:32 DEBUG  CommonBackend: Fetching basic info...
10-09 15:32 DEBUG  CommonBackend: original_exe=G:\wubi.exe
10-09 15:32 DEBUG  CommonBackend: platform=win32
10-09 15:32 DEBUG  CommonBackend: osname=nt
10-09 15:32 DEBUG  WindowsBackend: arch=amd64
10-09 15:32 DEBUG  CommonBackend: Parsing isolist=C:\Users\Evan\AppData\Local\Temp\pylD25B.tmp\data\isolist.ini
10-09 15:32 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
10-09 15:32 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
10-09 15:32 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
10-09 15:32 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
10-09 15:32 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
10-09 15:32 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
10-09 15:32 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
10-09 15:32 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
10-09 15:32 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
10-09 15:32 DEBUG  WindowsBackend: Fetching host info...
10-09 15:32 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
10-09 15:32 DEBUG  WindowsBackend: windows version=vista
10-09 15:32 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium
10-09 15:32 DEBUG  WindowsBackend: windows_sp=Service Pack 1
10-09 15:32 DEBUG  WindowsBackend: windows_build=7601
10-09 15:32 DEBUG  WindowsBackend: gmt=7
10-09 15:32 DEBUG  WindowsBackend: country=ID
10-09 15:32 DEBUG  WindowsBackend: timezone=Asia/Jakarta
10-09 15:32 DEBUG  WindowsBackend: windows_username=Evan
10-09 15:32 DEBUG  WindowsBackend: user_full_name=Evan
10-09 15:32 DEBUG  WindowsBackend: user_directory=C:\Users\Evan
10-09 15:32 DEBUG  WindowsBackend: windows_language_code=1057
10-09 15:32 DEBUG  WindowsBackend: windows_language=Indonesian
10-09 15:32 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM) i3 CPU       M 330  @ 2.13GHz
10-09 15:32 DEBUG  WindowsBackend: bootloader=vista
10-09 15:32 DEBUG  WindowsBackend: system_drive=Drive(C: hd 118691.144531 mb free ntfs)
10-09 15:32 DEBUG  WindowsBackend: drive=Drive(C: hd 118691.144531 mb free ntfs)
10-09 15:32 DEBUG  WindowsBackend: drive=Drive(D: hd 2872.41796875 mb free ntfs)
10-09 15:32 DEBUG  WindowsBackend: drive=Drive(E: hd 99.328125 mb free fat32)
10-09 15:32 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free cdfs)
10-09 15:32 DEBUG  WindowsBackend: drive=Drive(G: cd 0.0 mb free cdfs)
10-09 15:32 DEBUG  WindowsBackend: drive=Drive(H: removable 0.0 mb free )
10-09 15:32 DEBUG  WindowsBackend: drive=Drive(I: hd 19989.8984375 mb free ntfs)
10-09 15:32 DEBUG  WindowsBackend: drive=Drive(J: hd 76814.8203125 mb free ntfs)
10-09 15:32 DEBUG  WindowsBackend: uninstaller_path=None
10-09 15:32 DEBUG  WindowsBackend: previous_target_dir=None
10-09 15:32 DEBUG  WindowsBackend: previous_distro_name=None
10-09 15:32 DEBUG  WindowsBackend: keyboard_id=67699721
10-09 15:32 DEBUG  WindowsBackend: keyboard_layout=us
10-09 15:32 DEBUG  WindowsBackend: keyboard_variant=
10-09 15:32 DEBUG  WindowsBackend: total_memory_mb=1910.83984375
10-09 15:32 DEBUG  CommonBackend: Searching ISOs on USB devices
10-09 15:32 DEBUG  CommonBackend: Searching for local CDs
10-09 15:32 DEBUG  Distro:   checking whether C:\Users\Evan\AppData\Local\Temp\pylD25B.tmp is a valid Ubuntu CD
10-09 15:32 DEBUG  Distro:     does not contain C:\Users\Evan\AppData\Local\Temp\pylD25B.tmp\casper\filesystem.squashfs
10-09 15:32 DEBUG  Distro:   checking whether C:\Users\Evan\AppData\Local\Temp\pylD25B.tmp is a valid Ubuntu CD
10-09 15:32 DEBUG  Distro:     does not contain C:\Users\Evan\AppData\Local\Temp\pylD25B.tmp\casper\filesystem.squashfs
10-09 15:32 DEBUG  Distro:   checking whether C:\Users\Evan\AppData\Local\Temp\pylD25B.tmp is a valid Ubuntu Netbook CD
10-09 15:32 DEBUG  Distro:     does not contain C:\Users\Evan\AppData\Local\Temp\pylD25B.tmp\casper\filesystem.squashfs
10-09 15:32 DEBUG  Distro:   checking whether C:\Users\Evan\AppData\Local\Temp\pylD25B.tmp is a valid Kubuntu CD
10-09 15:32 DEBUG  Distro:     does not contain C:\Users\Evan\AppData\Local\Temp\pylD25B.tmp\casper\filesystem.squashfs
10-09 15:32 DEBUG  Distro:   checking whether C:\Users\Evan\AppData\Local\Temp\pylD25B.tmp is a valid Kubuntu CD
10-09 15:32 DEBUG  Distro:     does not contain C:\Users\Evan\AppData\Local\Temp\pylD25B.tmp\casper\filesystem.squashfs
10-09 15:32 DEBUG  Distro:   checking whether C:\Users\Evan\AppData\Local\Temp\pylD25B.tmp is a valid Xubuntu CD
10-09 15:32 DEBUG  Distro:     does not contain C:\Users\Evan\AppData\Local\Temp\pylD25B.tmp\casper\filesystem.squashfs
10-09 15:32 DEBUG  Distro:   checking whether C:\Users\Evan\AppData\Local\Temp\pylD25B.tmp is a valid Xubuntu CD
10-09 15:32 DEBUG  Distro:     does not contain C:\Users\Evan\AppData\Local\Temp\pylD25B.tmp\casper\filesystem.squashfs
10-09 15:32 DEBUG  Distro:   checking whether C:\Users\Evan\AppData\Local\Temp\pylD25B.tmp is a valid Mythbuntu CD
10-09 15:32 DEBUG  Distro:     does not contain C:\Users\Evan\AppData\Local\Temp\pylD25B.tmp\casper\filesystem.squashfs
10-09 15:32 DEBUG  Distro:   checking whether C:\Users\Evan\AppData\Local\Temp\pylD25B.tmp is a valid Mythbuntu CD
10-09 15:32 DEBUG  Distro:     does not contain C:\Users\Evan\AppData\Local\Temp\pylD25B.tmp\casper\filesystem.squashfs
10-09 15:32 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
10-09 15:32 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-09 15:32 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
10-09 15:32 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-09 15:32 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
10-09 15:32 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-09 15:32 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
10-09 15:32 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-09 15:32 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
10-09 15:32 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-09 15:32 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
10-09 15:32 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-09 15:32 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
10-09 15:32 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-09 15:32 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
10-09 15:32 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-09 15:32 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
10-09 15:32 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-09 15:32 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
10-09 15:32 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-09 15:32 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
10-09 15:32 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-09 15:32 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook CD
10-09 15:32 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-09 15:32 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
10-09 15:32 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-09 15:32 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
10-09 15:32 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-09 15:32 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
10-09 15:32 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-09 15:32 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
10-09 15:32 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-09 15:32 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
10-09 15:32 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-09 15:32 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
10-09 15:32 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-09 15:32 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
10-09 15:32 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-09 15:32 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
10-09 15:32 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-09 15:32 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu Netbook CD
10-09 15:32 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-09 15:32 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
10-09 15:32 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-09 15:32 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
10-09 15:32 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-09 15:32 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
10-09 15:32 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-09 15:32 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
10-09 15:32 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-09 15:32 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
10-09 15:32 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-09 15:32 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
10-09 15:32 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-09 15:32 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
10-09 15:32 INFO   Distro: Found a valid CD for Ubuntu: G:\
10-09 15:32 INFO   root: Running the installer...
10-09 15:32 INFO   WinuiPage: appname=wubi,  localedir=C:\Users\Evan\AppData\Local\Temp\pylD25B.tmp\translations,  languages=['id_ID', 'id']
10-09 15:32 INFO   WinuiPage: appname=wubi,  localedir=C:\Users\Evan\AppData\Local\Temp\pylD25B.tmp\translations,  languages=['id_ID', 'id']
10-09 15:32 DEBUG  WinuiInstallationPage: target_drive=I:,  installation_size=17000MB, distro_name=Ubuntu, language=en_US,  locale=en_US.UTF-8, username=evan
10-09 15:32 INFO   root: Received settings
10-09 15:32 INFO   WinuiPage: appname=wubi,  localedir=C:\Users\Evan\AppData\Local\Temp\pylD25B.tmp\translations,  languages=['en_US', 'en']
10-09 15:32 DEBUG  TaskList: # Running tasklist...
10-09 15:32 DEBUG  TaskList: ## Running select_target_dir...
10-09 15:32 INFO   WindowsBackend: Installing into I:\ubuntu
10-09 15:32 DEBUG  TaskList: ## Finished select_target_dir
10-09 15:32 DEBUG  TaskList: ## Running create_dir_structure...
10-09 15:32 DEBUG  CommonBackend: Creating dir I:\ubuntu
10-09 15:32 DEBUG  CommonBackend: Creating dir I:\ubuntu\disks
10-09 15:32 DEBUG  CommonBackend: Creating dir I:\ubuntu\install
10-09 15:32 DEBUG  CommonBackend: Creating dir I:\ubuntu\install\boot
10-09 15:32 DEBUG  CommonBackend: Creating dir I:\ubuntu\disks\boot
10-09 15:32 DEBUG  CommonBackend: Creating dir I:\ubuntu\disks\boot\grub
10-09 15:32 DEBUG  CommonBackend: Creating dir I:\ubuntu\install\boot\grub
10-09 15:32 DEBUG  TaskList: ## Finished create_dir_structure
10-09 15:32 DEBUG  TaskList: ## Running uncompress_target_dir...
10-09 15:32 DEBUG  TaskList: ## Finished uncompress_target_dir
10-09 15:32 DEBUG  TaskList: ## Running create_uninstaller...
10-09 15:32 DEBUG  WindowsBackend: Copying uninstaller G:\wubi.exe -> I:\ubuntu\uninstall-wubi.exe
10-09 15:32 DEBUG  registry: Setting registry key -2147483646  Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString  I:\ubuntu\uninstall-wubi.exe
10-09 15:32 DEBUG  registry: Setting registry key -2147483646  Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir  I:\ubuntu
10-09 15:32 DEBUG  registry: Setting registry key -2147483646  Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName  Ubuntu
10-09 15:32 DEBUG  registry: Setting registry key -2147483646  Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon  I:\ubuntu\Ubuntu.ico
10-09 15:32 DEBUG  registry: Setting registry key -2147483646  Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion  11.04-rev211
10-09 15:32 DEBUG  registry: Setting registry key -2147483646  Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher  Ubuntu
10-09 15:32 DEBUG  registry: Setting registry key -2147483646  Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com]("http://www.ubuntu.com/")
10-09 15:32 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
10-09 15:32 DEBUG  TaskList: ## Finished create_uninstaller
10-09 15:32 DEBUG  TaskList: ## Running copy_installation_files...
10-09 15:32 DEBUG  WindowsBackend: Copying  C:\Users\Evan\AppData\Local\Temp\pylD25B.tmp\data\custom-installation  -> I:\ubuntu\install\custom-installation
10-09 15:32 DEBUG  WindowsBackend: Copying C:\Users\Evan\AppData\Local\Temp\pylD25B.tmp\winboot -> I:\ubuntu\winboot
10-09 15:32 DEBUG  WindowsBackend: Copying  C:\Users\Evan\AppData\Local\Temp\pylD25B.tmp\data\images\Ubuntu.ico  -> I:\ubuntu\Ubuntu.ico
10-09 15:32 DEBUG  TaskList: ## Finished copy_installation_files
10-09 15:32 DEBUG  TaskList: ## Running get_iso...
10-09 15:32 DEBUG  TaskList: New task copy_file
10-09 15:32 DEBUG  TaskList: ### Running copy_file...
10-09 15:32 DEBUG  TaskList: ### Finished copy_file
10-09 15:32 DEBUG  TaskList: New task check_iso
10-09 15:32 DEBUG  TaskList: ### Running check_iso...
10-09 15:32 DEBUG  CommonBackend: Checking I:\ubuntu\install\installation.iso
10-09 15:32 DEBUG  Distro:   checking Ubuntu ISO I:\ubuntu\install\installation.iso
10-09 15:32 DEBUG  WindowsBackend:   extracting .disk\info from I:\ubuntu\install\installation.iso
10-09 15:32 DEBUG  Distro:   parsing info from str=Ubuntu 11.04 "Natty Narwhal" - Release i386 (20110427.1)
10-09 15:32 DEBUG  Distro:   parsed info={'name': 'Ubuntu',  'subversion': 'Release', 'version': '11.04', 'build': '20110427.1',  'codename': 'Natty Narwhal', 'arch': 'i386'}
10-09 15:32 INFO   Distro: Found a valid iso for Ubuntu: I:\ubuntu\install\installation.iso
10-09 15:32 DEBUG  CommonBackend: Using distro Ubuntu i386 instead of Ubuntu amd64
10-09 15:32 DEBUG  TaskList: New task get_metalink
10-09 15:32 DEBUG  TaskList: #### Running get_metalink...
10-09 15:32 DEBUG  downloader: downloading [http://releases.ubuntu.com/11.04/ubuntu-11.04-desktop-i386.metalink](http://releases.ubuntu.com/11.04/ubuntu-11.04-desktop-i386.metalink) > I:\ubuntu\install
10-09 15:33 DEBUG  downloader: Download start  filename=I:\ubuntu\install\ubuntu-11.04-desktop-i386.metalink,  url=http://releases.ubuntu.com/11.04/ubuntu-11.04-desktop-i386.metalink,  basename=ubuntu-11.04-desktop-i386.metalink, length=28158, text=None
10-09 15:33 DEBUG  downloader: download finished (read 28158 bytes)
10-09 15:33 DEBUG  downloader: downloading [http://releases.ubuntu.com/11.04/MD5SUMS-metalink](http://releases.ubuntu.com/11.04/MD5SUMS-metalink) > I:\ubuntu\install
10-09 15:33 DEBUG  downloader: Download start  filename=I:\ubuntu\install\MD5SUMS-metalink,  url=http://releases.ubuntu.com/11.04/MD5SUMS-metalink,  basename=MD5SUMS-metalink, length=874, text=None
10-09 15:33 DEBUG  downloader: download finished (read 874 bytes)
10-09 15:33 DEBUG  downloader: downloading [http://releases.ubuntu.com/11.04/MD5SUMS-metalink.gpg](http://releases.ubuntu.com/11.04/MD5SUMS-metalink.gpg) > I:\ubuntu\install
10-09 15:33 DEBUG  downloader: Download start  filename=I:\ubuntu\install\MD5SUMS-metalink.gpg,  url=http://releases.ubuntu.com/11.04/MD5SUMS-metalink.gpg,  basename=MD5SUMS-metalink.gpg, length=198, text=None
10-09 15:33 DEBUG  downloader: download finished (read 198 bytes)
10-09 15:33 INFO   saplog: Verified a signature from ID:'46181433FBB75451'.
10-09 15:33 INFO   saplog: Checking block bindings..
10-09 15:33 INFO   saplog: Key verified successfully.
10-09 15:33 DEBUG  CommonBackend: metalink md5sums:
a941ca07230dd2a812b5abd3aa12f79f  ubuntu-11.04-alternate-amd64.metalink
ec67d129102bbe53715c0a192c6e703b  ubuntu-11.04-alternate-i386.metalink
350c4c0da5823625e5278cc869153e65  ubuntu-11.04-beta2-alternate-amd64.metalink
10eb1df66373fd00cd9be2acfc329bf3  ubuntu-11.04-beta2-alternate-i386.metalink
7b3ef94055a263d7f7f9b1ed6e3c99e2  ubuntu-11.04-beta2-desktop-amd64.metalink
84b89292c5ae40be000a5ee861da257e  ubuntu-11.04-beta2-desktop-i386.metalink
d39c949129feb09da7e349882833f488  ubuntu-11.04-beta2-server-amd64.metalink
b7be563bfb89faaa4c7bd892a1a56aa1  ubuntu-11.04-beta2-server-i386.metalink
42aa52e7eaa441d0b00965d225f4e44f  ubuntu-11.04-desktop-amd64.metalink
8376ce671b922bd1051f16ab2d44d06f  ubuntu-11.04-desktop-i386.metalink
e23ed6d1164876804a7fb9dfb2f8aee1  ubuntu-11.04-server-amd64.metalink
b4b50d20f519fd0d8761e9d998630449  ubuntu-11.04-server-i386.metalink

10-09 15:33 DEBUG  TaskList: #### Finished get_metalink
10-09 15:33 DEBUG  TaskList: New task get_file_md5
10-09 15:33 DEBUG  TaskList: #### Running get_file_md5...
10-09 15:34 DEBUG  TaskList: #### Finished get_file_md5
10-09 15:34 DEBUG  TaskList: ### Finished check_iso
10-09 15:34 DEBUG  TaskList: ## Finished get_iso
10-09 15:34 DEBUG  TaskList: ## Running extract_kernel...
10-09 15:34 DEBUG  CommonBackend: Copying files from CD G:\
10-09 15:34 DEBUG  CommonBackend: Checking kernel, initrd and md5sums
10-09 15:34 DEBUG  CommonBackend:   checking I:\ubuntu\install\boot\vmlinuz
10-09 15:34 DEBUG  CommonBackend:   I:\ubuntu\install\boot\vmlinuz md5 =  db0104e80bc7e667344a14af3515de25 == db0104e80bc7e667344a14af3515de25
10-09 15:34 DEBUG  CommonBackend:   checking I:\ubuntu\install\boot\initrd.lz
10-09 15:34 DEBUG  CommonBackend:   I:\ubuntu\install\boot\initrd.lz md5  = 4b776cdafb272064bb70e09ba212e4aa == 4b776cdafb272064bb70e09ba212e4aa
10-09 15:34 DEBUG  TaskList: ## Finished extract_kernel
10-09 15:34 DEBUG  TaskList: ## Running choose_disk_sizes...
10-09 15:34 DEBUG  WindowsBackend: total size=17000
  root=16744
  swap=256
  home=0
  usr=0
10-09 15:34 DEBUG  TaskList: ## Finished choose_disk_sizes
10-09 15:34 DEBUG  TaskList: ## Running create_preseed...
10-09 15:34 DEBUG  TaskList: ## Finished create_preseed
10-09 15:34 DEBUG  TaskList: ## Running modify_bootloader...
10-09 15:34 DEBUG  TaskList: New task modify_bcd
10-09 15:34 DEBUG  TaskList: ### Running modify_bcd...
10-09 15:34 DEBUG  WindowsBackend: modify_bcd Drive(C: hd 118691.144531 mb free ntfs)
10-09 15:34 ERROR  TaskList: Error executing command
>>command=C:\Windows\System32\bcdedit.exe /set {3f2cd357-091c-11df-b381-9c46b9b554f6} device partition=I:
>>retval=1
>>stderr=An error has occurred setting the element data.

The request is not supported.


>>stdout=
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 648, in modify_bcd
  File "\lib\wubi\backends\common\utils.py", line 62, in run_command
Exception: Error executing command
>>command=C:\Windows\System32\bcdedit.exe /set {3f2cd357-091c-11df-b381-9c46b9b554f6} device partition=I:
>>retval=1
>>stderr=An error has occurred setting the element data.

The request is not supported.


>>stdout=
10-09 15:34 DEBUG  TaskList: # Cancelling tasklist
10-09 15:34 DEBUG  TaskList: New task modify_bcd
10-09 15:34 ERROR  root: Error executing command
>>command=C:\Windows\System32\bcdedit.exe /set {3f2cd357-091c-11df-b381-9c46b9b554f6} device partition=I:
>>retval=1
>>stderr=An error has occurred setting the element data.

The request is not supported.


>>stdout=
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 57, in run
  File "\lib\wubi\application.py", line 129, in select_task
  File "\lib\wubi\application.py", line 195, in run_cd_menu
  File "\lib\wubi\application.py", line 119, in select_task
  File "\lib\wubi\application.py", line 157, in run_installer
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 648, in modify_bcd
  File "\lib\wubi\backends\common\utils.py", line 62, in run_command
Exception: Error executing command
>>command=C:\Windows\System32\bcdedit.exe /set {3f2cd357-091c-11df-b381-9c46b9b554f6} device partition=I:
>>retval=1
>>stderr=An error has occurred setting the element data.

The request is not supported.


>>stdout=
10-09 15:34 DEBUG  TaskList: New task modify_bcd
10-09 15:34 DEBUG  TaskList: New task modify_bcd
10-09 15:34 DEBUG  TaskList: New task modify_bcd
10-09 15:34 DEBUG  TaskList: New task modify_bcd
10-09 15:34 DEBUG  TaskList: ## Finished modify_bootloader
10-09 15:34 DEBUG  TaskList: # Finished tasklist
10-09 15:52 INFO   root: === wubi 11.04 rev211 ===
10-09 15:52 DEBUG  root: Logfile is c:\users\evan\appdata\local\temp\wubi-11.04-rev211.log
10-09 15:52 DEBUG  root: sys.argv = ['main.pyo', '--exefile="G:\\wubi.exe"']
10-09 15:52 DEBUG  CommonBackend: data_dir=C:\Users\Evan\AppData\Local\Temp\pyl2E7F.tmp\data
10-09 15:52 DEBUG  WindowsBackend: 7z=C:\Users\Evan\AppData\Local\Temp\pyl2E7F.tmp\bin\7z.exe
10-09 15:52 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
10-09 15:52 DEBUG  CommonBackend: Fetching basic info...
10-09 15:52 DEBUG  CommonBackend: original_exe=G:\wubi.exe
10-09 15:52 DEBUG  CommonBackend: platform=win32
10-09 15:52 DEBUG  CommonBackend: osname=nt
10-09 15:52 DEBUG  CommonBackend: language=id_ID
10-09 15:52 DEBUG  CommonBackend: encoding=cp1252
10-09 15:52 DEBUG  WindowsBackend: arch=amd64
10-09 15:52 DEBUG  CommonBackend: Parsing isolist=C:\Users\Evan\AppData\Local\Temp\pyl2E7F.tmp\data\isolist.ini
10-09 15:52 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
10-09 15:52 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
10-09 15:52 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
10-09 15:52 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
10-09 15:52 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
10-09 15:52 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
10-09 15:52 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
10-09 15:52 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
10-09 15:52 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
10-09 15:52 DEBUG  WindowsBackend: Fetching host info...
10-09 15:52 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
10-09 15:52 DEBUG  WindowsBackend: windows version=vista
10-09 15:52 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium
10-09 15:52 DEBUG  WindowsBackend: windows_sp=Service Pack 1
10-09 15:52 DEBUG  WindowsBackend: windows_build=7601
10-09 15:52 DEBUG  WindowsBackend: gmt=7
10-09 15:52 DEBUG  WindowsBackend: country=ID
10-09 15:52 DEBUG  WindowsBackend: timezone=Asia/Jakarta
10-09 15:52 DEBUG  WindowsBackend: windows_username=Evan
10-09 15:52 DEBUG  WindowsBackend: user_full_name=Evan
10-09 15:52 DEBUG  WindowsBackend: user_directory=C:\Users\Evan
10-09 15:52 DEBUG  WindowsBackend: windows_language_code=1057
10-09 15:52 DEBUG  WindowsBackend: windows_language=Indonesian
10-09 15:52 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM) i3 CPU       M 330  @ 2.13GHz
10-09 15:52 DEBUG  WindowsBackend: bootloader=vista
10-09 15:52 DEBUG  WindowsBackend: system_drive=Drive(C: hd 118679.804688 mb free ntfs)
10-09 15:52 DEBUG  WindowsBackend: drive=Drive(C: hd 118679.804688 mb free ntfs)
10-09 15:52 DEBUG  WindowsBackend: drive=Drive(D: hd 2872.41796875 mb free ntfs)
10-09 15:52 DEBUG  WindowsBackend: drive=Drive(E: hd 99.328125 mb free fat32)
10-09 15:52 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free cdfs)
10-09 15:52 DEBUG  WindowsBackend: drive=Drive(G: cd 0.0 mb free cdfs)
10-09 15:52 DEBUG  WindowsBackend: drive=Drive(H: removable 0.0 mb free )
10-09 15:52 DEBUG  WindowsBackend: drive=Drive(J: hd 76814.8203125 mb free ntfs)
10-09 15:52 DEBUG  WindowsBackend: uninstaller_path=I:\ubuntu\uninstall-wubi.exe
10-09 15:52 DEBUG  WindowsBackend: previous_target_dir=I:\ubuntu
10-09 15:52 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
10-09 15:52 DEBUG  WindowsBackend: keyboard_id=67699721
10-09 15:52 DEBUG  WindowsBackend: keyboard_layout=us
10-09 15:52 DEBUG  WindowsBackend: keyboard_variant=
10-09 15:52 DEBUG  CommonBackend: python locale=('id_ID', 'cp1252')
10-09 15:52 DEBUG  CommonBackend: locale=id_ID.UTF-8
10-09 15:52 DEBUG  WindowsBackend: total_memory_mb=1910.83984375
10-09 15:52 DEBUG  CommonBackend: Searching ISOs on USB devices
10-09 15:52 DEBUG  CommonBackend: Searching for local CDs
10-09 15:52 DEBUG  Distro:   checking whether C:\Users\Evan\AppData\Local\Temp\pyl2E7F.tmp is a valid Ubuntu CD
10-09 15:52 DEBUG  Distro:     does not contain C:\Users\Evan\AppData\Local\Temp\pyl2E7F.tmp\casper\filesystem.squashfs
10-09 15:52 DEBUG  Distro:   checking whether C:\Users\Evan\AppData\Local\Temp\pyl2E7F.tmp is a valid Ubuntu CD
10-09 15:52 DEBUG  Distro:     does not contain C:\Users\Evan\AppData\Local\Temp\pyl2E7F.tmp\casper\filesystem.squashfs
10-09 15:52 DEBUG  Distro:   checking whether C:\Users\Evan\AppData\Local\Temp\pyl2E7F.tmp is a valid Ubuntu Netbook CD
10-09 15:52 DEBUG  Distro:     does not contain C:\Users\Evan\AppData\Local\Temp\pyl2E7F.tmp\casper\filesystem.squashfs
10-09 15:52 DEBUG  Distro:   checking whether C:\Users\Evan\AppData\Local\Temp\pyl2E7F.tmp is a valid Kubuntu CD
10-09 15:52 DEBUG  Distro:     does not contain C:\Users\Evan\AppData\Local\Temp\pyl2E7F.tmp\casper\filesystem.squashfs
10-09 15:52 DEBUG  Distro:   checking whether C:\Users\Evan\AppData\Local\Temp\pyl2E7F.tmp is a valid Kubuntu CD
10-09 15:52 DEBUG  Distro:     does not contain C:\Users\Evan\AppData\Local\Temp\pyl2E7F.tmp\casper\filesystem.squashfs
10-09 15:52 DEBUG  Distro:   checking whether C:\Users\Evan\AppData\Local\Temp\pyl2E7F.tmp is a valid Xubuntu CD
10-09 15:52 DEBUG  Distro:     does not contain C:\Users\Evan\AppData\Local\Temp\pyl2E7F.tmp\casper\filesystem.squashfs
10-09 15:52 DEBUG  Distro:   checking whether C:\Users\Evan\AppData\Local\Temp\pyl2E7F.tmp is a valid Xubuntu CD
10-09 15:52 DEBUG  Distro:     does not contain C:\Users\Evan\AppData\Local\Temp\pyl2E7F.tmp\casper\filesystem.squashfs
10-09 15:52 DEBUG  Distro:   checking whether C:\Users\Evan\AppData\Local\Temp\pyl2E7F.tmp is a valid Mythbuntu CD
10-09 15:52 DEBUG  Distro:     does not contain C:\Users\Evan\AppData\Local\Temp\pyl2E7F.tmp\casper\filesystem.squashfs
10-09 15:52 DEBUG  Distro:   checking whether C:\Users\Evan\AppData\Local\Temp\pyl2E7F.tmp is a valid Mythbuntu CD
10-09 15:52 DEBUG  Distro:     does not contain C:\Users\Evan\AppData\Local\Temp\pyl2E7F.tmp\casper\filesystem.squashfs
10-09 15:52 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
10-09 15:52 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-09 15:52 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
10-09 15:52 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-09 15:52 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
10-09 15:52 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-09 15:52 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
10-09 15:52 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-09 15:52 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
10-09 15:52 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-09 15:52 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
10-09 15:52 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-09 15:52 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
10-09 15:52 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-09 15:52 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
10-09 15:52 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-09 15:52 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
10-09 15:52 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-09 15:52 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
10-09 15:52 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-09 15:52 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
10-09 15:52 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-09 15:52 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook CD
10-09 15:52 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-09 15:52 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
10-09 15:52 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-09 15:52 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
10-09 15:52 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-09 15:52 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
10-09 15:52 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-09 15:52 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
10-09 15:52 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-09 15:52 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
10-09 15:52 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-09 15:52 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
10-09 15:52 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-09 15:52 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
10-09 15:52 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-09 15:52 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
10-09 15:52 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-09 15:52 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu Netbook CD
10-09 15:52 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-09 15:52 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
10-09 15:52 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-09 15:52 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
10-09 15:52 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-09 15:52 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
10-09 15:52 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-09 15:52 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
10-09 15:52 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-09 15:52 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
10-09 15:52 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-09 15:52 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
10-09 15:52 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-09 15:52 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
10-09 15:52 DEBUG  Distro:   parsing info from str=Ubuntu 11.04 "Natty Narwhal" - Release i386 (20110427.1)
10-09 15:52 DEBUG  Distro:   parsed info={'name': 'Ubuntu',  'subversion': 'Release', 'version': '11.04', 'build': '20110427.1',  'codename': 'Natty Narwhal', 'arch': 'i386'}
10-09 15:52 INFO   Distro: Found a valid CD for Ubuntu: G:\
10-09 15:52 INFO   root: Running the CD menu...
10-09 15:52 DEBUG  WindowsFrontend: __init__...
10-09 15:52 DEBUG  WindowsFrontend: on_init...
10-09 15:52 INFO   WinuiPage: appname=wubi,  localedir=C:\Users\Evan\AppData\Local\Temp\pyl2E7F.tmp\translations,  languages=['id_ID', 'id']
10-09 15:52 INFO   WinuiPage: appname=wubi,  localedir=C:\Users\Evan\AppData\Local\Temp\pyl2E7F.tmp\translations,  languages=['id_ID', 'id']
10-09 15:52 INFO   root: CD menu finished
10-09 15:52 INFO   root: Running the installer...
10-09 15:52 INFO   WinuiPage: appname=wubi,  localedir=C:\Users\Evan\AppData\Local\Temp\pyl2E7F.tmp\translations,  languages=['id_ID', 'id']
10-09 15:52 INFO   WinuiPage: appname=wubi,  localedir=C:\Users\Evan\AppData\Local\Temp\pyl2E7F.tmp\translations,  languages=['id_ID', 'id']
10-09 15:52 INFO   WindowsFrontend: Operation cancelled
10-09 15:52 DEBUG  WindowsFrontend: frontend.quit
10-09 15:52 DEBUG  WindowsFrontend: frontend.on_quit
10-09 15:52 DEBUG  root: application.on_quit
10-09 15:52 INFO   root: sys.exit
10-09 15:57 INFO   root: === wubi 11.04 rev211 ===
10-09 15:57 DEBUG  root: Logfile is c:\users\evan\appdata\local\temp\wubi-11.04-rev211.log
10-09 15:57 DEBUG  root: sys.argv = ['main.pyo', '--exefile="G:\\wubi.exe"']
10-09 15:57 DEBUG  CommonBackend: data_dir=C:\Users\Evan\AppData\Local\Temp\pylE743.tmp\data
10-09 15:57 DEBUG  WindowsBackend: 7z=C:\Users\Evan\AppData\Local\Temp\pylE743.tmp\bin\7z.exe
10-09 15:57 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
10-09 15:57 DEBUG  CommonBackend: Fetching basic info...
10-09 15:57 DEBUG  CommonBackend: original_exe=G:\wubi.exe
10-09 15:57 DEBUG  CommonBackend: platform=win32
10-09 15:57 DEBUG  CommonBackend: osname=nt
10-09 15:57 DEBUG  CommonBackend: language=id_ID
10-09 15:57 DEBUG  CommonBackend: encoding=cp1252
10-09 15:57 DEBUG  WindowsBackend: arch=amd64
10-09 15:57 DEBUG  CommonBackend: Parsing isolist=C:\Users\Evan\AppData\Local\Temp\pylE743.tmp\data\isolist.ini
10-09 15:57 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
10-09 15:57 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
10-09 15:57 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
10-09 15:57 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
10-09 15:57 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
10-09 15:57 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
10-09 15:57 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
10-09 15:57 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
10-09 15:57 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
10-09 15:57 DEBUG  WindowsBackend: Fetching host info...
10-09 15:57 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
10-09 15:57 DEBUG  WindowsBackend: windows version=vista
10-09 15:57 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium
10-09 15:57 DEBUG  WindowsBackend: windows_sp=Service Pack 1
10-09 15:57 DEBUG  WindowsBackend: windows_build=7601
10-09 15:57 DEBUG  WindowsBackend: gmt=7
10-09 15:57 DEBUG  WindowsBackend: country=ID
10-09 15:57 DEBUG  WindowsBackend: timezone=Asia/Jakarta
10-09 15:57 DEBUG  WindowsBackend: windows_username=Evan
10-09 15:57 DEBUG  WindowsBackend: user_full_name=Evan
10-09 15:57 DEBUG  WindowsBackend: user_directory=C:\Users\Evan
10-09 15:57 DEBUG  WindowsBackend: windows_language_code=1057
10-09 15:57 DEBUG  WindowsBackend: windows_language=Indonesian
10-09 15:57 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM) i3 CPU       M 330  @ 2.13GHz
10-09 15:57 DEBUG  WindowsBackend: bootloader=vista
10-09 15:57 DEBUG  WindowsBackend: system_drive=Drive(C: hd 118678.039063 mb free ntfs)
10-09 15:57 DEBUG  WindowsBackend: drive=Drive(C: hd 118678.039063 mb free ntfs)
10-09 15:57 DEBUG  WindowsBackend: drive=Drive(D: hd 2872.41796875 mb free ntfs)
10-09 15:57 DEBUG  WindowsBackend: drive=Drive(E: hd 99.328125 mb free fat32)
10-09 15:57 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free cdfs)
10-09 15:57 DEBUG  WindowsBackend: drive=Drive(G: cd 0.0 mb free cdfs)
10-09 15:57 DEBUG  WindowsBackend: drive=Drive(H: removable 0.0 mb free )
10-09 15:57 DEBUG  WindowsBackend: drive=Drive(I: hd 20070.953125 mb free fat32)
10-09 15:57 DEBUG  WindowsBackend: drive=Drive(J: hd 76814.8203125 mb free ntfs)
10-09 15:57 DEBUG  WindowsBackend: uninstaller_path=I:\ubuntu\uninstall-wubi.exe
10-09 15:57 DEBUG  WindowsBackend: previous_target_dir=I:\ubuntu
10-09 15:57 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
10-09 15:57 DEBUG  WindowsBackend: keyboard_id=67699721
10-09 15:57 DEBUG  WindowsBackend: keyboard_layout=us
10-09 15:57 DEBUG  WindowsBackend: keyboard_variant=
10-09 15:57 DEBUG  CommonBackend: python locale=('id_ID', 'cp1252')
10-09 15:57 DEBUG  CommonBackend: locale=id_ID.UTF-8
10-09 15:57 DEBUG  WindowsBackend: total_memory_mb=1910.83984375
10-09 15:57 DEBUG  CommonBackend: Searching ISOs on USB devices
10-09 15:57 DEBUG  CommonBackend: Searching for local CDs
10-09 15:57 DEBUG  Distro:   checking whether C:\Users\Evan\AppData\Local\Temp\pylE743.tmp is a valid Ubuntu CD
10-09 15:57 DEBUG  Distro:     does not contain C:\Users\Evan\AppData\Local\Temp\pylE743.tmp\casper\filesystem.squashfs
10-09 15:57 DEBUG  Distro:   checking whether C:\Users\Evan\AppData\Local\Temp\pylE743.tmp is a valid Ubuntu CD
10-09 15:57 DEBUG  Distro:     does not contain C:\Users\Evan\AppData\Local\Temp\pylE743.tmp\casper\filesystem.squashfs
10-09 15:57 DEBUG  Distro:   checking whether C:\Users\Evan\AppData\Local\Temp\pylE743.tmp is a valid Ubuntu Netbook CD
10-09 15:57 DEBUG  Distro:     does not contain C:\Users\Evan\AppData\Local\Temp\pylE743.tmp\casper\filesystem.squashfs
10-09 15:57 DEBUG  Distro:   checking whether C:\Users\Evan\AppData\Local\Temp\pylE743.tmp is a valid Kubuntu CD
10-09 15:57 DEBUG  Distro:     does not contain C:\Users\Evan\AppData\Local\Temp\pylE743.tmp\casper\filesystem.squashfs
10-09 15:57 DEBUG  Distro:   checking whether C:\Users\Evan\AppData\Local\Temp\pylE743.tmp is a valid Kubuntu CD
10-09 15:57 DEBUG  Distro:     does not contain C:\Users\Evan\AppData\Local\Temp\pylE743.tmp\casper\filesystem.squashfs
10-09 15:57 DEBUG  Distro:   checking whether C:\Users\Evan\AppData\Local\Temp\pylE743.tmp is a valid Xubuntu CD
10-09 15:57 DEBUG  Distro:     does not contain C:\Users\Evan\AppData\Local\Temp\pylE743.tmp\casper\filesystem.squashfs
10-09 15:57 DEBUG  Distro:   checking whether C:\Users\Evan\AppData\Local\Temp\pylE743.tmp is a valid Xubuntu CD
10-09 15:57 DEBUG  Distro:     does not contain C:\Users\Evan\AppData\Local\Temp\pylE743.tmp\casper\filesystem.squashfs
10-09 15:57 DEBUG  Distro:   checking whether C:\Users\Evan\AppData\Local\Temp\pylE743.tmp is a valid Mythbuntu CD
10-09 15:57 DEBUG  Distro:     does not contain C:\Users\Evan\AppData\Local\Temp\pylE743.tmp\casper\filesystem.squashfs
10-09 15:57 DEBUG  Distro:   checking whether C:\Users\Evan\AppData\Local\Temp\pylE743.tmp is a valid Mythbuntu CD
10-09 15:57 DEBUG  Distro:     does not contain C:\Users\Evan\AppData\Local\Temp\pylE743.tmp\casper\filesystem.squashfs
10-09 15:57 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
10-09 15:57 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-09 15:57 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
10-09 15:57 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-09 15:57 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
10-09 15:57 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-09 15:57 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
10-09 15:57 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-09 15:57 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
10-09 15:57 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-09 15:57 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
10-09 15:57 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-09 15:57 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
10-09 15:57 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-09 15:57 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
10-09 15:57 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-09 15:57 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
10-09 15:57 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-09 15:57 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
10-09 15:57 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-09 15:57 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
10-09 15:57 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-09 15:57 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook CD
10-09 15:57 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-09 15:57 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
10-09 15:57 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-09 15:57 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
10-09 15:57 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-09 15:57 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
10-09 15:57 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-09 15:57 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
10-09 15:57 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-09 15:57 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
10-09 15:57 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-09 15:57 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
10-09 15:57 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-09 15:57 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
10-09 15:57 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-09 15:57 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
10-09 15:57 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-09 15:57 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu Netbook CD
10-09 15:57 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-09 15:57 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
10-09 15:57 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-09 15:57 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
10-09 15:57 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-09 15:57 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
10-09 15:57 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-09 15:57 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
10-09 15:57 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-09 15:57 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
10-09 15:57 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-09 15:57 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
10-09 15:57 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-09 15:57 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
10-09 15:57 DEBUG  Distro:   parsing info from str=Ubuntu 11.04 "Natty Narwhal" - Release i386 (20110427.1)
10-09 15:57 DEBUG  Distro:   parsed info={'name': 'Ubuntu',  'subversion': 'Release', 'version': '11.04', 'build': '20110427.1',  'codename': 'Natty Narwhal', 'arch': 'i386'}
10-09 15:57 INFO   Distro: Found a valid CD for Ubuntu: G:\
10-09 15:57 INFO   root: Running the CD menu...
10-09 15:57 DEBUG  WindowsFrontend: __init__...
10-09 15:57 DEBUG  WindowsFrontend: on_init...
10-09 15:57 INFO   WinuiPage: appname=wubi,  localedir=C:\Users\Evan\AppData\Local\Temp\pylE743.tmp\translations,  languages=['id_ID', 'id']
10-09 15:57 INFO   WinuiPage: appname=wubi,  localedir=C:\Users\Evan\AppData\Local\Temp\pylE743.tmp\translations,  languages=['id_ID', 'id']
10-09 15:57 INFO   root: CD menu finished
10-09 15:57 INFO   root: Running the installer...
10-09 15:57 INFO   WinuiPage: appname=wubi,  localedir=C:\Users\Evan\AppData\Local\Temp\pylE743.tmp\translations,  languages=['id_ID', 'id']
10-09 15:57 INFO   WinuiPage: appname=wubi,  localedir=C:\Users\Evan\AppData\Local\Temp\pylE743.tmp\translations,  languages=['id_ID', 'id']
10-09 15:58 DEBUG  WinuiInstallationPage: target_drive=I:,  installation_size=17000MB, distro_name=Ubuntu, language=en_US,  locale=en_US.UTF-8, username=evan
10-09 15:58 INFO   root: Received settings
10-09 15:58 INFO   WinuiPage: appname=wubi,  localedir=C:\Users\Evan\AppData\Local\Temp\pylE743.tmp\translations,  languages=['en_US', 'en']
10-09 15:58 DEBUG  TaskList: # Running tasklist...
10-09 15:58 DEBUG  TaskList: ## Running select_target_dir...
10-09 15:58 INFO   WindowsBackend: Installing into I:\ubuntu
10-09 15:58 DEBUG  TaskList: ## Finished select_target_dir
10-09 15:58 DEBUG  TaskList: ## Running create_dir_structure...
10-09 15:58 DEBUG  CommonBackend: Creating dir I:\ubuntu
10-09 15:58 DEBUG  CommonBackend: Creating dir I:\ubuntu\disks
10-09 15:58 DEBUG  CommonBackend: Creating dir I:\ubuntu\install
10-09 15:58 DEBUG  CommonBackend: Creating dir I:\ubuntu\install\boot
10-09 15:58 DEBUG  CommonBackend: Creating dir I:\ubuntu\disks\boot
10-09 15:58 DEBUG  CommonBackend: Creating dir I:\ubuntu\disks\boot\grub
10-09 15:58 DEBUG  CommonBackend: Creating dir I:\ubuntu\install\boot\grub
10-09 15:58 DEBUG  TaskList: ## Finished create_dir_structure
10-09 15:58 DEBUG  TaskList: ## Running uncompress_target_dir...
10-09 15:58 DEBUG  TaskList: ## Finished uncompress_target_dir
10-09 15:58 DEBUG  TaskList: ## Running create_uninstaller...
10-09 15:58 DEBUG  WindowsBackend: Copying uninstaller G:\wubi.exe -> I:\ubuntu\uninstall-wubi.exe
10-09 15:58 DEBUG  registry: Setting registry key -2147483646  Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString  I:\ubuntu\uninstall-wubi.exe
10-09 15:58 DEBUG  registry: Setting registry key -2147483646  Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir  I:\ubuntu
10-09 15:58 DEBUG  registry: Setting registry key -2147483646  Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName  Ubuntu
10-09 15:58 DEBUG  registry: Setting registry key -2147483646  Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon  I:\ubuntu\Ubuntu.ico
10-09 15:58 DEBUG  registry: Setting registry key -2147483646  Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion  11.04-rev211
10-09 15:58 DEBUG  registry: Setting registry key -2147483646  Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher  Ubuntu
10-09 15:58 DEBUG  registry: Setting registry key -2147483646  Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com]("http://www.ubuntu.com/")
10-09 15:58 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
10-09 15:58 DEBUG  TaskList: ## Finished create_uninstaller
10-09 15:58 DEBUG  TaskList: ## Running copy_installation_files...
10-09 15:58 DEBUG  WindowsBackend: Copying  C:\Users\Evan\AppData\Local\Temp\pylE743.tmp\data\custom-installation  -> I:\ubuntu\install\custom-installation
10-09 15:58 DEBUG  WindowsBackend: Copying C:\Users\Evan\AppData\Local\Temp\pylE743.tmp\winboot -> I:\ubuntu\winboot
10-09 15:58 DEBUG  WindowsBackend: Copying  C:\Users\Evan\AppData\Local\Temp\pylE743.tmp\data\images\Ubuntu.ico  -> I:\ubuntu\Ubuntu.ico
10-09 15:58 DEBUG  TaskList: ## Finished copy_installation_files
10-09 15:58 DEBUG  TaskList: ## Running get_iso...
10-09 15:58 DEBUG  TaskList: New task copy_file
10-09 15:58 DEBUG  TaskList: ### Running copy_file...
10-09 15:58 DEBUG  TaskList: ### Finished copy_file
10-09 15:58 DEBUG  TaskList: New task check_iso
10-09 15:58 DEBUG  TaskList: ### Running check_iso...
10-09 15:58 DEBUG  CommonBackend: Checking I:\ubuntu\install\installation.iso
10-09 15:58 DEBUG  Distro:   checking Ubuntu ISO I:\ubuntu\install\installation.iso
10-09 15:58 DEBUG  WindowsBackend:   extracting .disk\info from I:\ubuntu\install\installation.iso
10-09 15:58 DEBUG  Distro:   parsing info from str=Ubuntu 11.04 "Natty Narwhal" - Release i386 (20110427.1)
10-09 15:58 DEBUG  Distro:   parsed info={'name': 'Ubuntu',  'subversion': 'Release', 'version': '11.04', 'build': '20110427.1',  'codename': 'Natty Narwhal', 'arch': 'i386'}
10-09 15:58 INFO   Distro: Found a valid iso for Ubuntu: I:\ubuntu\install\installation.iso
10-09 15:58 DEBUG  CommonBackend: Using distro Ubuntu i386 instead of Ubuntu amd64
10-09 15:58 DEBUG  TaskList: New task get_metalink
10-09 15:58 DEBUG  TaskList: #### Running get_metalink...
10-09 15:58 DEBUG  downloader: downloading [http://releases.ubuntu.com/11.04/ubuntu-11.04-desktop-i386.metalink](http://releases.ubuntu.com/11.04/ubuntu-11.04-desktop-i386.metalink) > I:\ubuntu\install
10-09 15:58 DEBUG  downloader: Download start  filename=I:\ubuntu\install\ubuntu-11.04-desktop-i386.metalink,  url=http://releases.ubuntu.com/11.04/ubuntu-11.04-desktop-i386.metalink,  basename=ubuntu-11.04-desktop-i386.metalink, length=28158, text=None
10-09 15:58 DEBUG  downloader: download finished (read 28158 bytes)
10-09 15:58 DEBUG  downloader: downloading [http://releases.ubuntu.com/11.04/MD5SUMS-metalink](http://releases.ubuntu.com/11.04/MD5SUMS-metalink) > I:\ubuntu\install
10-09 15:58 DEBUG  downloader: Download start  filename=I:\ubuntu\install\MD5SUMS-metalink,  url=http://releases.ubuntu.com/11.04/MD5SUMS-metalink,  basename=MD5SUMS-metalink, length=874, text=None
10-09 15:58 DEBUG  downloader: download finished (read 874 bytes)
10-09 15:58 DEBUG  downloader: downloading [http://releases.ubuntu.com/11.04/MD5SUMS-metalink.gpg](http://releases.ubuntu.com/11.04/MD5SUMS-metalink.gpg) > I:\ubuntu\install
10-09 15:59 ERROR  TaskList: [Errno 4] IOError: <urlopen error (10060, 'Operation timed out')>
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 377, in get_metalink
  File "\lib\wubi\backends\common\backend.py", line 242, in check_metalink
  File "\lib\wubi\backends\common\downloader.py", line 78, in download
  File "\lib\urlgrabber\grabber.py", line 927, in urlgrab
  File "\lib\urlgrabber\grabber.py", line 845, in _retry
  File "\lib\urlgrabber\grabber.py", line 913, in retryfunc
  File "\lib\urlgrabber\grabber.py", line 1001, in __init__
  File "\lib\urlgrabber\grabber.py", line 1072, in _do_open
  File "\lib\urlgrabber\grabber.py", line 1188, in _make_request
URLGrabError: [Errno 4] IOError: <urlopen error (10060, 'Operation timed out')>
10-09 15:59 DEBUG  TaskList: # Cancelling tasklist
10-09 15:59 ERROR  CommonBackend: ERROR: the metalink file is not  available, cannot check the md5 for I:\ubuntu\install\installation.iso,  ignoring
10-09 15:59 ERROR  root: [Errno 4] IOError: <urlopen error (10060, 'Operation timed out')>
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 57, in run
  File "\lib\wubi\application.py", line 129, in select_task
  File "\lib\wubi\application.py", line 195, in run_cd_menu
  File "\lib\wubi\application.py", line 119, in select_task
  File "\lib\wubi\application.py", line 157, in run_installer
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 377, in get_metalink
  File "\lib\wubi\backends\common\backend.py", line 242, in check_metalink
  File "\lib\wubi\backends\common\downloader.py", line 78, in download
  File "\lib\urlgrabber\grabber.py", line 927, in urlgrab
  File "\lib\urlgrabber\grabber.py", line 845, in _retry
  File "\lib\urlgrabber\grabber.py", line 913, in retryfunc
  File "\lib\urlgrabber\grabber.py", line 1001, in __init__
  File "\lib\urlgrabber\grabber.py", line 1072, in _do_open
  File "\lib\urlgrabber\grabber.py", line 1188, in _make_request
URLGrabError: [Errno 4] IOError: <urlopen error (10060, 'Operation timed out')>
10-09 15:59 DEBUG  TaskList: ### Finished check_iso
10-09 15:59 DEBUG  TaskList: ## Finished get_iso
10-09 15:59 DEBUG  TaskList: # Finished tasklist
10-09 16:05 INFO   root: === wubi 11.04 rev211 ===
10-09 16:05 DEBUG  root: Logfile is c:\users\evan\appdata\local\temp\wubi-11.04-rev211.log
10-09 16:05 DEBUG  root: sys.argv = ['main.pyo', '--exefile="G:\\wubi.exe"']
10-09 16:05 DEBUG  CommonBackend: data_dir=C:\Users\Evan\AppData\Local\Temp\pyl142C.tmp\data
10-09 16:05 DEBUG  WindowsBackend: 7z=C:\Users\Evan\AppData\Local\Temp\pyl142C.tmp\bin\7z.exe
10-09 16:05 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
10-09 16:05 DEBUG  CommonBackend: Fetching basic info...
10-09 16:05 DEBUG  CommonBackend: original_exe=G:\wubi.exe
10-09 16:05 DEBUG  CommonBackend: platform=win32
10-09 16:05 DEBUG  CommonBackend: osname=nt
10-09 16:05 DEBUG  CommonBackend: language=id_ID
10-09 16:05 DEBUG  CommonBackend: encoding=cp1252
10-09 16:05 DEBUG  WindowsBackend: arch=amd64
10-09 16:05 DEBUG  CommonBackend: Parsing isolist=C:\Users\Evan\AppData\Local\Temp\pyl142C.tmp\data\isolist.ini
10-09 16:05 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
10-09 16:05 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
10-09 16:05 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
10-09 16:05 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
10-09 16:05 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
10-09 16:05 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
10-09 16:05 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
10-09 16:05 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
10-09 16:05 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
10-09 16:05 DEBUG  WindowsBackend: Fetching host info...
10-09 16:05 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
10-09 16:05 DEBUG  WindowsBackend: windows version=vista
10-09 16:05 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium
10-09 16:05 DEBUG  WindowsBackend: windows_sp=Service Pack 1
10-09 16:05 DEBUG  WindowsBackend: windows_build=7601
10-09 16:05 DEBUG  WindowsBackend: gmt=7
10-09 16:05 DEBUG  WindowsBackend: country=ID
10-09 16:05 DEBUG  WindowsBackend: timezone=Asia/Jakarta
10-09 16:05 DEBUG  WindowsBackend: windows_username=Evan
10-09 16:05 DEBUG  WindowsBackend: user_full_name=Evan
10-09 16:05 DEBUG  WindowsBackend: user_directory=C:\Users\Evan
10-09 16:05 DEBUG  WindowsBackend: windows_language_code=1057
10-09 16:05 DEBUG  WindowsBackend: windows_language=Indonesian
10-09 16:05 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM) i3 CPU       M 330  @ 2.13GHz
10-09 16:05 DEBUG  WindowsBackend: bootloader=vista
10-09 16:05 DEBUG  WindowsBackend: system_drive=Drive(C: hd 118677.023438 mb free ntfs)
10-09 16:05 DEBUG  WindowsBackend: drive=Drive(C: hd 118677.023438 mb free ntfs)
10-09 16:05 DEBUG  WindowsBackend: drive=Drive(D: hd 2872.41796875 mb free ntfs)
10-09 16:05 DEBUG  WindowsBackend: drive=Drive(E: hd 99.328125 mb free fat32)
10-09 16:05 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free cdfs)
10-09 16:05 DEBUG  WindowsBackend: drive=Drive(G: cd 0.0 mb free cdfs)
10-09 16:05 DEBUG  WindowsBackend: drive=Drive(H: removable 0.0 mb free )
10-09 16:05 DEBUG  WindowsBackend: drive=Drive(I: hd 19383.671875 mb free fat32)
10-09 16:05 DEBUG  WindowsBackend: drive=Drive(J: hd 76814.8203125 mb free ntfs)
10-09 16:05 DEBUG  WindowsBackend: uninstaller_path=I:\ubuntu\uninstall-wubi.exe
10-09 16:05 DEBUG  WindowsBackend: previous_target_dir=I:\ubuntu
10-09 16:05 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
10-09 16:05 DEBUG  WindowsBackend: keyboard_id=67699721
10-09 16:05 DEBUG  WindowsBackend: keyboard_layout=us
10-09 16:05 DEBUG  WindowsBackend: keyboard_variant=
10-09 16:05 DEBUG  CommonBackend: python locale=('id_ID', 'cp1252')
10-09 16:05 DEBUG  CommonBackend: locale=id_ID.UTF-8
10-09 16:05 DEBUG  WindowsBackend: total_memory_mb=1910.83984375
10-09 16:05 DEBUG  CommonBackend: Searching ISOs on USB devices
10-09 16:05 DEBUG  CommonBackend: Searching for local CDs
10-09 16:05 DEBUG  Distro:   checking whether C:\Users\Evan\AppData\Local\Temp\pyl142C.tmp is a valid Ubuntu CD
10-09 16:05 DEBUG  Distro:     does not contain C:\Users\Evan\AppData\Local\Temp\pyl142C.tmp\casper\filesystem.squashfs
10-09 16:05 DEBUG  Distro:   checking whether C:\Users\Evan\AppData\Local\Temp\pyl142C.tmp is a valid Ubuntu CD
10-09 16:05 DEBUG  Distro:     does not contain C:\Users\Evan\AppData\Local\Temp\pyl142C.tmp\casper\filesystem.squashfs
10-09 16:05 DEBUG  Distro:   checking whether C:\Users\Evan\AppData\Local\Temp\pyl142C.tmp is a valid Ubuntu Netbook CD
10-09 16:05 DEBUG  Distro:     does not contain C:\Users\Evan\AppData\Local\Temp\pyl142C.tmp\casper\filesystem.squashfs
10-09 16:05 DEBUG  Distro:   checking whether C:\Users\Evan\AppData\Local\Temp\pyl142C.tmp is a valid Kubuntu CD
10-09 16:05 DEBUG  Distro:     does not contain C:\Users\Evan\AppData\Local\Temp\pyl142C.tmp\casper\filesystem.squashfs
10-09 16:05 DEBUG  Distro:   checking whether C:\Users\Evan\AppData\Local\Temp\pyl142C.tmp is a valid Kubuntu CD
10-09 16:05 DEBUG  Distro:     does not contain C:\Users\Evan\AppData\Local\Temp\pyl142C.tmp\casper\filesystem.squashfs
10-09 16:05 DEBUG  Distro:   checking whether C:\Users\Evan\AppData\Local\Temp\pyl142C.tmp is a valid Xubuntu CD
10-09 16:05 DEBUG  Distro:     does not contain C:\Users\Evan\AppData\Local\Temp\pyl142C.tmp\casper\filesystem.squashfs
10-09 16:05 DEBUG  Distro:   checking whether C:\Users\Evan\AppData\Local\Temp\pyl142C.tmp is a valid Xubuntu CD
10-09 16:05 DEBUG  Distro:     does not contain C:\Users\Evan\AppData\Local\Temp\pyl142C.tmp\casper\filesystem.squashfs
10-09 16:05 DEBUG  Distro:   checking whether C:\Users\Evan\AppData\Local\Temp\pyl142C.tmp is a valid Mythbuntu CD
10-09 16:05 DEBUG  Distro:     does not contain C:\Users\Evan\AppData\Local\Temp\pyl142C.tmp\casper\filesystem.squashfs
10-09 16:05 DEBUG  Distro:   checking whether C:\Users\Evan\AppData\Local\Temp\pyl142C.tmp is a valid Mythbuntu CD
10-09 16:05 DEBUG  Distro:     does not contain C:\Users\Evan\AppData\Local\Temp\pyl142C.tmp\casper\filesystem.squashfs
10-09 16:05 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
10-09 16:05 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-09 16:05 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
10-09 16:05 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-09 16:05 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
10-09 16:05 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-09 16:05 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
10-09 16:05 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-09 16:05 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
10-09 16:05 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-09 16:05 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
10-09 16:05 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-09 16:05 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
10-09 16:05 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-09 16:05 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
10-09 16:05 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-09 16:05 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
10-09 16:05 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-09 16:05 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
10-09 16:05 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-09 16:05 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
10-09 16:05 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-09 16:05 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook CD
10-09 16:05 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-09 16:05 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
10-09 16:05 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-09 16:05 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
10-09 16:05 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-09 16:05 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
10-09 16:05 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-09 16:05 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
10-09 16:05 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-09 16:05 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
10-09 16:05 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-09 16:05 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
10-09 16:05 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-09 16:05 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
10-09 16:05 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-09 16:05 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
10-09 16:05 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-09 16:05 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu Netbook CD
10-09 16:05 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-09 16:05 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
10-09 16:05 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-09 16:05 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
10-09 16:05 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-09 16:05 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
10-09 16:05 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-09 16:05 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
10-09 16:05 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-09 16:05 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
10-09 16:05 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-09 16:05 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
10-09 16:05 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-09 16:05 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
10-09 16:05 DEBUG  Distro:   parsing info from str=Ubuntu 11.04 "Natty Narwhal" - Release i386 (20110427.1)
10-09 16:05 DEBUG  Distro:   parsed info={'name': 'Ubuntu',  'subversion': 'Release', 'version': '11.04', 'build': '20110427.1',  'codename': 'Natty Narwhal', 'arch': 'i386'}
10-09 16:05 INFO   Distro: Found a valid CD for Ubuntu: G:\
10-09 16:05 INFO   root: Running the CD menu...
10-09 16:05 DEBUG  WindowsFrontend: __init__...
10-09 16:05 DEBUG  WindowsFrontend: on_init...
10-09 16:05 INFO   WinuiPage: appname=wubi,  localedir=C:\Users\Evan\AppData\Local\Temp\pyl142C.tmp\translations,  languages=['id_ID', 'id']
10-09 16:05 INFO   WinuiPage: appname=wubi,  localedir=C:\Users\Evan\AppData\Local\Temp\pyl142C.tmp\translations,  languages=['id_ID', 'id']
10-09 16:05 INFO   root: CD menu finished
10-09 16:05 INFO   root: Already installed, running the uninstaller...
10-09 16:05 INFO   root: Running the uninstaller...
10-09 16:05 INFO   CommonBackend: This is the uninstaller running
10-09 16:05 INFO   WinuiPage: appname=wubi,  localedir=C:\Users\Evan\AppData\Local\Temp\pyl142C.tmp\translations,  languages=['id_ID', 'id']
10-09 16:05 INFO   root: Received settings
10-09 16:05 INFO   WinuiPage: appname=wubi,  localedir=C:\Users\Evan\AppData\Local\Temp\pyl142C.tmp\translations,  languages=['id_ID', 'id']
10-09 16:05 DEBUG  TaskList: # Running tasklist...
10-09 16:05 DEBUG  TaskList: ## Running Salin ISO...
10-09 16:05 DEBUG  TaskList: ## Finished Salin ISO
10-09 16:05 DEBUG  TaskList: ## Running Hapus entri bootloader...
10-09 16:05 DEBUG  WindowsBackend: Could not find bcd id
10-09 16:05 DEBUG  WindowsBackend: undo_bootini C:
10-09 16:05 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 118677.023438 mb free ntfs)
10-09 16:05 DEBUG  WindowsBackend: undo_bootini D:
10-09 16:05 DEBUG  WindowsBackend: undo_configsys Drive(D: hd 2872.41796875 mb free ntfs)
10-09 16:05 DEBUG  WindowsBackend: undo_bootini E:
10-09 16:05 DEBUG  WindowsBackend: undo_configsys Drive(E: hd 99.328125 mb free fat32)
10-09 16:05 DEBUG  WindowsBackend: undo_bootini H:
10-09 16:05 DEBUG  WindowsBackend: undo_configsys Drive(H: removable 0.0 mb free )
10-09 16:05 DEBUG  WindowsBackend: undo_bootini I:
10-09 16:05 DEBUG  WindowsBackend: undo_configsys Drive(I: hd 19383.671875 mb free fat32)
10-09 16:05 DEBUG  WindowsBackend: undo_bootini J:
10-09 16:05 DEBUG  WindowsBackend: undo_configsys Drive(J: hd 76814.8203125 mb free ntfs)
10-09 16:05 DEBUG  TaskList: ## Finished Hapus entri bootloader
10-09 16:05 DEBUG  TaskList: ## Running Hapus direktori tujuan...
10-09 16:05 DEBUG  CommonBackend: Deleting I:\ubuntu
10-09 16:05 DEBUG  TaskList: ## Finished Hapus direktori tujuan
10-09 16:05 DEBUG  TaskList: ## Running Hapus kunci registy...
10-09 16:05 DEBUG  TaskList: ## Finished Hapus kunci registy
10-09 16:05 DEBUG  TaskList: # Finished tasklist
10-09 16:05 INFO   root: Almost finished uninstalling
10-09 16:05 INFO   root: Finished uninstallation
10-09 16:05 DEBUG  CommonBackend: Fetching basic info...
10-09 16:05 DEBUG  CommonBackend: original_exe=G:\wubi.exe
10-09 16:05 DEBUG  CommonBackend: platform=win32
10-09 16:05 DEBUG  CommonBackend: osname=nt
10-09 16:05 DEBUG  WindowsBackend: arch=amd64
10-09 16:05 DEBUG  CommonBackend: Parsing isolist=C:\Users\Evan\AppData\Local\Temp\pyl142C.tmp\data\isolist.ini
10-09 16:05 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
10-09 16:05 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
10-09 16:05 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
10-09 16:05 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
10-09 16:05 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
10-09 16:05 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
10-09 16:05 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
10-09 16:05 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
10-09 16:05 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
10-09 16:05 DEBUG  WindowsBackend: Fetching host info...
10-09 16:05 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
10-09 16:05 DEBUG  WindowsBackend: windows version=vista
10-09 16:05 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium
10-09 16:05 DEBUG  WindowsBackend: windows_sp=Service Pack 1
10-09 16:05 DEBUG  WindowsBackend: windows_build=7601
10-09 16:05 DEBUG  WindowsBackend: gmt=7
10-09 16:05 DEBUG  WindowsBackend: country=ID
10-09 16:05 DEBUG  WindowsBackend: timezone=Asia/Jakarta
10-09 16:05 DEBUG  WindowsBackend: windows_username=Evan
10-09 16:05 DEBUG  WindowsBackend: user_full_name=Evan
10-09 16:05 DEBUG  WindowsBackend: user_directory=C:\Users\Evan
10-09 16:05 DEBUG  WindowsBackend: windows_language_code=1057
10-09 16:05 DEBUG  WindowsBackend: windows_language=Indonesian
10-09 16:05 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM) i3 CPU       M 330  @ 2.13GHz
10-09 16:05 DEBUG  WindowsBackend: bootloader=vista
10-09 16:05 DEBUG  WindowsBackend: system_drive=Drive(C: hd 118677.144531 mb free ntfs)
10-09 16:05 DEBUG  WindowsBackend: drive=Drive(C: hd 118677.144531 mb free ntfs)
10-09 16:05 DEBUG  WindowsBackend: drive=Drive(D: hd 2872.41796875 mb free ntfs)
10-09 16:05 DEBUG  WindowsBackend: drive=Drive(E: hd 99.328125 mb free fat32)
10-09 16:05 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free cdfs)
10-09 16:05 DEBUG  WindowsBackend: drive=Drive(G: cd 0.0 mb free cdfs)
10-09 16:05 DEBUG  WindowsBackend: drive=Drive(H: removable 0.0 mb free )
10-09 16:05 DEBUG  WindowsBackend: drive=Drive(I: hd 20070.953125 mb free fat32)
10-09 16:05 DEBUG  WindowsBackend: drive=Drive(J: hd 76814.8203125 mb free ntfs)
10-09 16:05 DEBUG  WindowsBackend: uninstaller_path=None
10-09 16:05 DEBUG  WindowsBackend: previous_target_dir=None
10-09 16:05 DEBUG  WindowsBackend: previous_distro_name=None
10-09 16:05 DEBUG  WindowsBackend: keyboard_id=67699721
10-09 16:05 DEBUG  WindowsBackend: keyboard_layout=us
10-09 16:05 DEBUG  WindowsBackend: keyboard_variant=
10-09 16:05 DEBUG  WindowsBackend: total_memory_mb=1910.83984375
10-09 16:05 DEBUG  CommonBackend: Searching ISOs on USB devices
10-09 16:05 DEBUG  CommonBackend: Searching for local CDs
10-09 16:05 DEBUG  Distro:   checking whether C:\Users\Evan\AppData\Local\Temp\pyl142C.tmp is a valid Ubuntu CD
10-09 16:05 DEBUG  Distro:     does not contain C:\Users\Evan\AppData\Local\Temp\pyl142C.tmp\casper\filesystem.squashfs
10-09 16:05 DEBUG  Distro:   checking whether C:\Users\Evan\AppData\Local\Temp\pyl142C.tmp is a valid Ubuntu CD
10-09 16:05 DEBUG  Distro:     does not contain C:\Users\Evan\AppData\Local\Temp\pyl142C.tmp\casper\filesystem.squashfs
10-09 16:05 DEBUG  Distro:   checking whether C:\Users\Evan\AppData\Local\Temp\pyl142C.tmp is a valid Ubuntu Netbook CD
10-09 16:05 DEBUG  Distro:     does not contain C:\Users\Evan\AppData\Local\Temp\pyl142C.tmp\casper\filesystem.squashfs
10-09 16:05 DEBUG  Distro:   checking whether C:\Users\Evan\AppData\Local\Temp\pyl142C.tmp is a valid Kubuntu CD
10-09 16:05 DEBUG  Distro:     does not contain C:\Users\Evan\AppData\Local\Temp\pyl142C.tmp\casper\filesystem.squashfs
10-09 16:05 DEBUG  Distro:   checking whether C:\Users\Evan\AppData\Local\Temp\pyl142C.tmp is a valid Kubuntu CD
10-09 16:05 DEBUG  Distro:     does not contain C:\Users\Evan\AppData\Local\Temp\pyl142C.tmp\casper\filesystem.squashfs
10-09 16:05 DEBUG  Distro:   checking whether C:\Users\Evan\AppData\Local\Temp\pyl142C.tmp is a valid Xubuntu CD
10-09 16:05 DEBUG  Distro:     does not contain C:\Users\Evan\AppData\Local\Temp\pyl142C.tmp\casper\filesystem.squashfs
10-09 16:05 DEBUG  Distro:   checking whether C:\Users\Evan\AppData\Local\Temp\pyl142C.tmp is a valid Xubuntu CD
10-09 16:05 DEBUG  Distro:     does not contain C:\Users\Evan\AppData\Local\Temp\pyl142C.tmp\casper\filesystem.squashfs
10-09 16:05 DEBUG  Distro:   checking whether C:\Users\Evan\AppData\Local\Temp\pyl142C.tmp is a valid Mythbuntu CD
10-09 16:05 DEBUG  Distro:     does not contain C:\Users\Evan\AppData\Local\Temp\pyl142C.tmp\casper\filesystem.squashfs
10-09 16:05 DEBUG  Distro:   checking whether C:\Users\Evan\AppData\Local\Temp\pyl142C.tmp is a valid Mythbuntu CD
10-09 16:05 DEBUG  Distro:     does not contain C:\Users\Evan\AppData\Local\Temp\pyl142C.tmp\casper\filesystem.squashfs
10-09 16:05 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
10-09 16:05 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-09 16:05 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
10-09 16:05 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-09 16:05 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
10-09 16:05 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-09 16:05 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
10-09 16:05 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-09 16:05 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
10-09 16:05 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-09 16:05 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
10-09 16:05 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-09 16:05 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
10-09 16:05 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-09 16:05 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
10-09 16:05 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-09 16:05 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
10-09 16:05 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-09 16:05 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
10-09 16:05 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-09 16:05 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
10-09 16:05 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-09 16:05 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook CD
10-09 16:05 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-09 16:05 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
10-09 16:05 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-09 16:05 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
10-09 16:05 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-09 16:05 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
10-09 16:05 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-09 16:05 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
10-09 16:05 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-09 16:05 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
10-09 16:05 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-09 16:05 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
10-09 16:05 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-09 16:05 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
10-09 16:05 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-09 16:05 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
10-09 16:05 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-09 16:05 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu Netbook CD
10-09 16:05 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-09 16:05 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
10-09 16:05 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-09 16:05 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
10-09 16:05 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-09 16:05 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
10-09 16:05 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-09 16:05 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
10-09 16:05 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-09 16:05 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
10-09 16:05 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-09 16:05 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
10-09 16:05 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-09 16:05 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
10-09 16:05 INFO   Distro: Found a valid CD for Ubuntu: G:\
10-09 16:05 INFO   root: Running the installer...
10-09 16:05 INFO   WinuiPage: appname=wubi,  localedir=C:\Users\Evan\AppData\Local\Temp\pyl142C.tmp\translations,  languages=['id_ID', 'id']
10-09 16:05 INFO   WinuiPage: appname=wubi,  localedir=C:\Users\Evan\AppData\Local\Temp\pyl142C.tmp\translations,  languages=['id_ID', 'id']
10-09 16:06 DEBUG  WinuiInstallationPage: target_drive=I:,  installation_size=17000MB, distro_name=Ubuntu, language=en_US,  locale=en_US.UTF-8, username=evan
10-09 16:06 INFO   root: Received settings
10-09 16:06 INFO   WinuiPage: appname=wubi,  localedir=C:\Users\Evan\AppData\Local\Temp\pyl142C.tmp\translations,  languages=['en_US', 'en']
10-09 16:06 DEBUG  TaskList: # Running tasklist...
10-09 16:06 DEBUG  TaskList: ## Running select_target_dir...
10-09 16:06 INFO   WindowsBackend: Installing into I:\ubuntu
10-09 16:06 DEBUG  TaskList: ## Finished select_target_dir
10-09 16:06 DEBUG  TaskList: ## Running create_dir_structure...
10-09 16:06 DEBUG  CommonBackend: Creating dir I:\ubuntu
10-09 16:06 DEBUG  CommonBackend: Creating dir I:\ubuntu\disks
10-09 16:06 DEBUG  CommonBackend: Creating dir I:\ubuntu\install
10-09 16:06 DEBUG  CommonBackend: Creating dir I:\ubuntu\install\boot
10-09 16:06 DEBUG  CommonBackend: Creating dir I:\ubuntu\disks\boot
10-09 16:06 DEBUG  CommonBackend: Creating dir I:\ubuntu\disks\boot\grub
10-09 16:06 DEBUG  CommonBackend: Creating dir I:\ubuntu\install\boot\grub
10-09 16:06 DEBUG  TaskList: ## Finished create_dir_structure
10-09 16:06 DEBUG  TaskList: ## Running uncompress_target_dir...
10-09 16:06 DEBUG  TaskList: ## Finished uncompress_target_dir
10-09 16:06 DEBUG  TaskList: ## Running create_uninstaller...
10-09 16:06 DEBUG  WindowsBackend: Copying uninstaller G:\wubi.exe -> I:\ubuntu\uninstall-wubi.exe
10-09 16:06 DEBUG  registry: Setting registry key -2147483646  Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString  I:\ubuntu\uninstall-wubi.exe
10-09 16:06 DEBUG  registry: Setting registry key -2147483646  Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir  I:\ubuntu
10-09 16:06 DEBUG  registry: Setting registry key -2147483646  Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName  Ubuntu
10-09 16:06 DEBUG  registry: Setting registry key -2147483646  Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon  I:\ubuntu\Ubuntu.ico
10-09 16:06 DEBUG  registry: Setting registry key -2147483646  Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion  11.04-rev211
10-09 16:06 DEBUG  registry: Setting registry key -2147483646  Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher  Ubuntu
10-09 16:06 DEBUG  registry: Setting registry key -2147483646  Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com]("http://www.ubuntu.com/")
10-09 16:06 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
10-09 16:06 DEBUG  TaskList: ## Finished create_uninstaller
10-09 16:06 DEBUG  TaskList: ## Running copy_installation_files...
10-09 16:06 DEBUG  WindowsBackend: Copying  C:\Users\Evan\AppData\Local\Temp\pyl142C.tmp\data\custom-installation  -> I:\ubuntu\install\custom-installation
10-09 16:06 DEBUG  WindowsBackend: Copying C:\Users\Evan\AppData\Local\Temp\pyl142C.tmp\winboot -> I:\ubuntu\winboot
10-09 16:06 DEBUG  WindowsBackend: Copying  C:\Users\Evan\AppData\Local\Temp\pyl142C.tmp\data\images\Ubuntu.ico  -> I:\ubuntu\Ubuntu.ico
10-09 16:06 DEBUG  TaskList: ## Finished copy_installation_files
10-09 16:06 DEBUG  TaskList: ## Running get_iso...
10-09 16:06 DEBUG  TaskList: New task copy_file
10-09 16:06 DEBUG  TaskList: ### Running copy_file...
10-09 16:06 DEBUG  TaskList: ### Finished copy_file
10-09 16:06 DEBUG  TaskList: New task check_iso
10-09 16:06 DEBUG  TaskList: ### Running check_iso...
10-09 16:06 DEBUG  CommonBackend: Checking I:\ubuntu\install\installation.iso
10-09 16:06 DEBUG  Distro:   checking Ubuntu ISO I:\ubuntu\install\installation.iso
10-09 16:06 DEBUG  WindowsBackend:   extracting .disk\info from I:\ubuntu\install\installation.iso
10-09 16:06 DEBUG  Distro:   parsing info from str=Ubuntu 11.04 "Natty Narwhal" - Release i386 (20110427.1)
10-09 16:06 DEBUG  Distro:   parsed info={'name': 'Ubuntu',  'subversion': 'Release', 'version': '11.04', 'build': '20110427.1',  'codename': 'Natty Narwhal', 'arch': 'i386'}
10-09 16:06 INFO   Distro: Found a valid iso for Ubuntu: I:\ubuntu\install\installation.iso
10-09 16:06 DEBUG  CommonBackend: Using distro Ubuntu i386 instead of Ubuntu amd64
10-09 16:06 DEBUG  TaskList: New task get_metalink
10-09 16:06 DEBUG  TaskList: #### Running get_metalink...
10-09 16:06 DEBUG  downloader: downloading [http://releases.ubuntu.com/11.04/ubuntu-11.04-desktop-i386.metalink](http://releases.ubuntu.com/11.04/ubuntu-11.04-desktop-i386.metalink) > I:\ubuntu\install
10-09 16:06 DEBUG  downloader: Download start  filename=I:\ubuntu\install\ubuntu-11.04-desktop-i386.metalink,  url=http://releases.ubuntu.com/11.04/ubuntu-11.04-desktop-i386.metalink,  basename=ubuntu-11.04-desktop-i386.metalink, length=28158, text=None
10-09 16:06 DEBUG  downloader: download finished (read 28158 bytes)
10-09 16:06 DEBUG  downloader: downloading [http://releases.ubuntu.com/11.04/MD5SUMS-metalink](http://releases.ubuntu.com/11.04/MD5SUMS-metalink) > I:\ubuntu\install
10-09 16:06 DEBUG  downloader: Download start  filename=I:\ubuntu\install\MD5SUMS-metalink,  url=http://releases.ubuntu.com/11.04/MD5SUMS-metalink,  basename=MD5SUMS-metalink, length=874, text=None
10-09 16:06 DEBUG  downloader: download finished (read 874 bytes)
10-09 16:06 DEBUG  downloader: downloading [http://releases.ubuntu.com/11.04/MD5SUMS-metalink.gpg](http://releases.ubuntu.com/11.04/MD5SUMS-metalink.gpg) > I:\ubuntu\install
10-09 16:06 DEBUG  downloader: Download start  filename=I:\ubuntu\install\MD5SUMS-metalink.gpg,  url=http://releases.ubuntu.com/11.04/MD5SUMS-metalink.gpg,  basename=MD5SUMS-metalink.gpg, length=198, text=None
10-09 16:06 DEBUG  downloader: download finished (read 198 bytes)
10-09 16:06 INFO   saplog: Verified a signature from ID:'46181433FBB75451'.
10-09 16:06 INFO   saplog: Checking block bindings..
10-09 16:06 INFO   saplog: Key verified successfully.
10-09 16:06 DEBUG  CommonBackend: metalink md5sums:
a941ca07230dd2a812b5abd3aa12f79f  ubuntu-11.04-alternate-amd64.metalink
ec67d129102bbe53715c0a192c6e703b  ubuntu-11.04-alternate-i386.metalink
350c4c0da5823625e5278cc869153e65  ubuntu-11.04-beta2-alternate-amd64.metalink
10eb1df66373fd00cd9be2acfc329bf3  ubuntu-11.04-beta2-alternate-i386.metalink
7b3ef94055a263d7f7f9b1ed6e3c99e2  ubuntu-11.04-beta2-desktop-amd64.metalink
84b89292c5ae40be000a5ee861da257e  ubuntu-11.04-beta2-desktop-i386.metalink
d39c949129feb09da7e349882833f488  ubuntu-11.04-beta2-server-amd64.metalink
b7be563bfb89faaa4c7bd892a1a56aa1  ubuntu-11.04-beta2-server-i386.metalink
42aa52e7eaa441d0b00965d225f4e44f  ubuntu-11.04-desktop-amd64.metalink
8376ce671b922bd1051f16ab2d44d06f  ubuntu-11.04-desktop-i386.metalink
e23ed6d1164876804a7fb9dfb2f8aee1  ubuntu-11.04-server-amd64.metalink
b4b50d20f519fd0d8761e9d998630449  ubuntu-11.04-server-i386.metalink

10-09 16:06 DEBUG  TaskList: #### Finished get_metalink
10-09 16:06 DEBUG  TaskList: New task get_file_md5
10-09 16:06 DEBUG  TaskList: #### Running get_file_md5...
10-09 16:06 DEBUG  TaskList: #### Finished get_file_md5
10-09 16:06 DEBUG  TaskList: ### Finished check_iso
10-09 16:06 DEBUG  TaskList: ## Finished get_iso
10-09 16:06 DEBUG  TaskList: ## Running extract_kernel...
10-09 16:06 DEBUG  CommonBackend: Copying files from CD G:\
10-09 16:06 DEBUG  CommonBackend: Checking kernel, initrd and md5sums
10-09 16:06 DEBUG  CommonBackend:   checking I:\ubuntu\install\boot\vmlinuz
10-09 16:06 DEBUG  CommonBackend:   I:\ubuntu\install\boot\vmlinuz md5 =  db0104e80bc7e667344a14af3515de25 == db0104e80bc7e667344a14af3515de25
10-09 16:06 DEBUG  CommonBackend:   checking I:\ubuntu\install\boot\initrd.lz
10-09 16:06 DEBUG  CommonBackend:   I:\ubuntu\install\boot\initrd.lz md5  = 4b776cdafb272064bb70e09ba212e4aa == 4b776cdafb272064bb70e09ba212e4aa
10-09 16:06 DEBUG  TaskList: ## Finished extract_kernel
10-09 16:06 DEBUG  TaskList: ## Running choose_disk_sizes...
10-09 16:06 DEBUG  WindowsBackend: total size=17000
  root=4000
  swap=256
  home=4000
  usr=4000
10-09 16:06 DEBUG  TaskList: ## Finished choose_disk_sizes
10-09 16:06 DEBUG  TaskList: ## Running create_preseed...
10-09 16:06 DEBUG  TaskList: ## Finished create_preseed
10-09 16:06 DEBUG  TaskList: ## Running modify_bootloader...
10-09 16:06 DEBUG  TaskList: New task modify_bcd
10-09 16:06 DEBUG  TaskList: ### Running modify_bcd...
10-09 16:06 DEBUG  WindowsBackend: modify_bcd Drive(C: hd 118677.144531 mb free ntfs)
10-09 16:06 ERROR  TaskList: Error executing command
>>command=C:\Windows\System32\bcdedit.exe /set {3f2cd358-091c-11df-b381-9c46b9b554f6} device partition=I:
>>retval=1
>>stderr=An error has occurred setting the element data.

The request is not supported.


>>stdout=
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 648, in modify_bcd
  File "\lib\wubi\backends\common\utils.py", line 62, in run_command
Exception: Error executing command
>>command=C:\Windows\System32\bcdedit.exe /set {3f2cd358-091c-11df-b381-9c46b9b554f6} device partition=I:
>>retval=1
>>stderr=An error has occurred setting the element data.

The request is not supported.


>>stdout=
10-09 16:06 DEBUG  TaskList: # Cancelling tasklist
10-09 16:06 DEBUG  TaskList: New task modify_bcd
10-09 16:06 ERROR  root: Error executing command
>>command=C:\Windows\System32\bcdedit.exe /set {3f2cd358-091c-11df-b381-9c46b9b554f6} device partition=I:
>>retval=1
>>stderr=An error has occurred setting the element data.

The request is not supported.


>>stdout=
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 57, in run
  File "\lib\wubi\application.py", line 129, in select_task
  File "\lib\wubi\application.py", line 195, in run_cd_menu
  File "\lib\wubi\application.py", line 119, in select_task
  File "\lib\wubi\application.py", line 157, in run_installer
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 648, in modify_bcd
  File "\lib\wubi\backends\common\utils.py", line 62, in run_command
Exception: Error executing command
>>command=C:\Windows\System32\bcdedit.exe /set {3f2cd358-091c-11df-b381-9c46b9b554f6} device partition=I:
>>retval=1
>>stderr=An error has occurred setting the element data.

The request is not supported.


>>stdout=
10-09 16:06 DEBUG  TaskList: New task modify_bcd
10-09 16:06 DEBUG  TaskList: New task modify_bcd
10-09 16:06 DEBUG  TaskList: New task modify_bcd
10-09 16:06 DEBUG  TaskList: New task modify_bcd
10-09 16:06 DEBUG  TaskList: ## Finished modify_bootloader
10-09 16:06 DEBUG  TaskList: # Finished tasklist
```

---

### Post by raja.genupula on 2011-10-09
have you tried to install with different cd ? check that cd for any errors.

---

