---
title: "Help Installing Ubuntu 11.10."
date: 2012-02-18
forum: New to Ubuntu
---

### Post by Jamieyates14 on 2012-02-18
When I've downloaded and extracted Ubuntu 11.10, I get the error shown in the picture below.
[IMG]http://img59.imageshack.us/img59/3126/ubuntuerror.png[/IMG]
Also if it's any use I have a Sony VAIO VPCEB4L1E.

---

### Post by Jamieyates14 on 2012-02-18
Actually, I think I may have posted this in the wrong place...

---

### Post by nothingspecial on 2012-02-18
*Thread moved to **Absolute Beginner Talk**.*

---

### Post by Jamieyates14 on 2012-02-18
> **nothingspecial said:**
> *Thread moved to **Absolute Beginner Talk**.*
Thanks :)

---

### Post by sadaruwan12 on 2012-02-18
Did you tried to install this after disabling your virus guard.

---

### Post by Jamieyates14 on 2012-02-18
> **sadaruwan12 said:**
> Did you tried to install this after disabling your virus guard.

Why? Would it stop Ubuntu installing or something?

---

### Post by sadaruwan12 on 2012-02-18
No but just in case any way can you do a small thing can you post the full wubi.log file here so wee can get a idea what went wrong.

You can see the file path in the error message.

---

### Post by Jamieyates14 on 2012-02-18
> **sadaruwan12 said:**
> No but just in case any way can you do a small thing can you post the full wubi.log file here so wee can get a idea what went wrong.

You can see the file path in the error message.

Do you have any idea where that might be? I can't seem to find it. The only file I found to do with Ubuntu and mentions errors is called ''wubi-11.10-rev245. Is that it or not?

EDIT:I read the picture again, think I found it. [IMG]http://img62.imageshack.us/img62/3619/ubuntuerrorlog1.png[/IMG]
Oh and I tried turning off my anti-virus, still had this error.

---

### Post by sadaruwan12 on 2012-02-18
This is the correct file but don't use a picture copy the full text and paste it here alos when your doing that use ```

``` tags to get it wrapped.

That way we can track it from the beginning.

---

### Post by Jamieyates14 on 2012-02-18
> **sadaruwan12 said:**
> This is the correct file but don't use a picture copy the full text and paste it here alos when your doing that use ```

``` tags to get it wrapped.

That way we can track it from the beginning.

Ohhh, okay. It's gonna have to be in two halves, first here and second in another message.
First half:
02-18 13:41 INFO   root: === wubi 11.10 rev245 ===
02-18 13:41 DEBUG  root: Logfile is c:\users\jamie's\appdata\local\temp\wubi-11.10-rev245.log
02-18 13:41 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\Users\\Jamie\'s\\Downloads\\wubi (1).exe"']
02-18 13:41 DEBUG  CommonBackend: data_dir=C:\Users\Jamie's\AppData\Local\Temp\pyl4C0F.tmp\data
02-18 13:41 DEBUG  WindowsBackend: 7z=C:\Users\Jamie's\AppData\Local\Temp\pyl4C0F.tmp\bin\7z.exe
02-18 13:41 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
02-18 13:41 DEBUG  CommonBackend: Fetching basic info...
02-18 13:41 DEBUG  CommonBackend: original_exe=C:\Users\Jamie's\Downloads\wubi (1).exe
02-18 13:41 DEBUG  CommonBackend: platform=win32
02-18 13:41 DEBUG  CommonBackend: osname=nt
02-18 13:41 DEBUG  CommonBackend: language=en_GB
02-18 13:41 DEBUG  CommonBackend: encoding=cp1252
02-18 13:41 DEBUG  WindowsBackend: arch=amd64
02-18 13:41 DEBUG  CommonBackend: Parsing isolist=C:\Users\Jamie's\AppData\Local\Temp\pyl4C0F.tmp\data\isolist.ini
02-18 13:41 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
02-18 13:41 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
02-18 13:41 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
02-18 13:41 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
02-18 13:41 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
02-18 13:41 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
02-18 13:41 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
02-18 13:41 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
02-18 13:41 DEBUG  WindowsBackend: Fetching host info...
02-18 13:41 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
02-18 13:41 DEBUG  WindowsBackend: windows version=vista
02-18 13:41 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium
02-18 13:41 DEBUG  WindowsBackend: windows_sp=None
02-18 13:41 DEBUG  WindowsBackend: windows_build=7600
02-18 13:41 DEBUG  WindowsBackend: gmt=0
02-18 13:41 DEBUG  WindowsBackend: country=GB
02-18 13:41 DEBUG  WindowsBackend: timezone=Europe/London
02-18 13:41 DEBUG  WindowsBackend: windows_username=Jamie's
02-18 13:41 DEBUG  WindowsBackend: user_full_name=Jamie's
02-18 13:41 DEBUG  WindowsBackend: user_directory=C:\Users\Jamie's
02-18 13:41 DEBUG  WindowsBackend: windows_language_code=1033
02-18 13:41 DEBUG  WindowsBackend: windows_language=English
02-18 13:41 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM) i3 CPU       M 380  @ 2.53GHz
02-18 13:41 DEBUG  WindowsBackend: bootloader=vista
02-18 13:41 DEBUG  WindowsBackend: system_drive=Drive(C: hd 281490.484375 mb free ntfs)
02-18 13:41 DEBUG  WindowsBackend: drive=Drive(C: hd 281490.484375 mb free ntfs)
02-18 13:41 DEBUG  WindowsBackend: drive=Drive(D: cd 0.0 mb free cdfs)
02-18 13:41 DEBUG  WindowsBackend: uninstaller_path=None
02-18 13:41 DEBUG  WindowsBackend: previous_target_dir=None
02-18 13:41 DEBUG  WindowsBackend: previous_distro_name=None
02-18 13:41 DEBUG  WindowsBackend: keyboard_id=134809609
02-18 13:41 DEBUG  WindowsBackend: keyboard_layout=gb
02-18 13:41 DEBUG  WindowsBackend: keyboard_variant=
02-18 13:41 DEBUG  CommonBackend: python locale=('en_GB', 'cp1252')
02-18 13:41 DEBUG  CommonBackend: locale=en_GB.UTF-8
02-18 13:41 DEBUG  WindowsBackend: total_memory_mb=3758.09765625
02-18 13:41 DEBUG  CommonBackend: Searching ISOs on USB devices
02-18 13:41 DEBUG  CommonBackend: Searching for local CDs
02-18 13:41 DEBUG  Distro:   checking whether C:\Users\Jamie's\AppData\Local\Temp\pyl4C0F.tmp is a valid Ubuntu CD
02-18 13:41 DEBUG  Distro:     does not contain C:\Users\Jamie's\AppData\Local\Temp\pyl4C0F.tmp\casper\filesystem.squashfs
02-18 13:41 DEBUG  Distro:   checking whether C:\Users\Jamie's\AppData\Local\Temp\pyl4C0F.tmp is a valid Ubuntu CD
02-18 13:41 DEBUG  Distro:     does not contain C:\Users\Jamie's\AppData\Local\Temp\pyl4C0F.tmp\casper\filesystem.squashfs
02-18 13:41 DEBUG  Distro:   checking whether C:\Users\Jamie's\AppData\Local\Temp\pyl4C0F.tmp is a valid Kubuntu CD
02-18 13:41 DEBUG  Distro:     does not contain C:\Users\Jamie's\AppData\Local\Temp\pyl4C0F.tmp\casper\filesystem.squashfs
02-18 13:41 DEBUG  Distro:   checking whether C:\Users\Jamie's\AppData\Local\Temp\pyl4C0F.tmp is a valid Kubuntu CD
02-18 13:41 DEBUG  Distro:     does not contain C:\Users\Jamie's\AppData\Local\Temp\pyl4C0F.tmp\casper\filesystem.squashfs
02-18 13:41 DEBUG  Distro:   checking whether C:\Users\Jamie's\AppData\Local\Temp\pyl4C0F.tmp is a valid Xubuntu CD
02-18 13:41 DEBUG  Distro:     does not contain C:\Users\Jamie's\AppData\Local\Temp\pyl4C0F.tmp\casper\filesystem.squashfs
02-18 13:41 DEBUG  Distro:   checking whether C:\Users\Jamie's\AppData\Local\Temp\pyl4C0F.tmp is a valid Xubuntu CD
02-18 13:41 DEBUG  Distro:     does not contain C:\Users\Jamie's\AppData\Local\Temp\pyl4C0F.tmp\casper\filesystem.squashfs
02-18 13:41 DEBUG  Distro:   checking whether C:\Users\Jamie's\AppData\Local\Temp\pyl4C0F.tmp is a valid Mythbuntu CD
02-18 13:41 DEBUG  Distro:     does not contain C:\Users\Jamie's\AppData\Local\Temp\pyl4C0F.tmp\casper\filesystem.squashfs
02-18 13:41 DEBUG  Distro:   checking whether C:\Users\Jamie's\AppData\Local\Temp\pyl4C0F.tmp is a valid Mythbuntu CD
02-18 13:41 DEBUG  Distro:     does not contain C:\Users\Jamie's\AppData\Local\Temp\pyl4C0F.tmp\casper\filesystem.squashfs
02-18 13:41 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
02-18 13:41 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-18 13:41 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
02-18 13:41 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-18 13:41 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
02-18 13:41 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-18 13:41 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
02-18 13:41 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-18 13:41 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
02-18 13:41 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-18 13:41 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
02-18 13:41 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-18 13:41 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
02-18 13:41 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-18 13:41 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
02-18 13:41 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-18 13:41 INFO   root: Running the installer...
02-18 13:41 DEBUG  WindowsFrontend: __init__...
02-18 13:41 DEBUG  WindowsFrontend: on_init...
02-18 13:41 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Jamie's\AppData\Local\Temp\pyl4C0F.tmp\translations, languages=['en_GB', 'en']
02-18 13:41 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Jamie's\AppData\Local\Temp\pyl4C0F.tmp\translations, languages=['en_GB', 'en']
02-18 13:42 DEBUG  WinuiInstallationPage: target_drive=C:, installation_size=20000MB, distro_name=Ubuntu, language=en_GB, locale=en_GB.UTF-8, username=jamie-ubuntu
02-18 13:42 INFO   root: Received settings
02-18 13:42 DEBUG  CommonBackend: Searching for local CD
02-18 13:42 DEBUG  Distro:   checking whether C:\Users\Jamie's\AppData\Local\Temp\pyl4C0F.tmp is a valid Ubuntu CD
02-18 13:42 DEBUG  Distro:     does not contain C:\Users\Jamie's\AppData\Local\Temp\pyl4C0F.tmp\casper\filesystem.squashfs
02-18 13:42 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
02-18 13:42 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-18 13:42 DEBUG  CommonBackend: Searching for local ISO
02-18 13:42 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Jamie's\AppData\Local\Temp\pyl4C0F.tmp\translations, languages=['en_GB', 'en']
02-18 13:42 DEBUG  TaskList: # Running tasklist...
02-18 13:42 DEBUG  TaskList: ## Running select_target_dir...
02-18 13:42 INFO   WindowsBackend: Installing into C:\ubuntu
02-18 13:42 DEBUG  TaskList: ## Finished select_target_dir
02-18 13:42 DEBUG  TaskList: ## Running create_dir_structure...
02-18 13:42 DEBUG  CommonBackend: Creating dir C:\ubuntu
02-18 13:42 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks
02-18 13:42 DEBUG  CommonBackend: Creating dir C:\ubuntu\install
02-18 13:42 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot
02-18 13:42 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot
02-18 13:42 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot\grub
02-18 13:42 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot\grub
02-18 13:42 DEBUG  TaskList: ## Finished create_dir_structure
02-18 13:42 DEBUG  TaskList: ## Running create_uninstaller...
02-18 13:42 DEBUG  WindowsBackend: Copying uninstaller C:\Users\Jamie's\Downloads\wubi (1).exe -> C:\ubuntu\uninstall-wubi.exe
02-18 13:42 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString C:\ubuntu\uninstall-wubi.exe
02-18 13:42 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir C:\ubuntu
02-18 13:42 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
02-18 13:42 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon C:\ubuntu\Ubuntu.ico
02-18 13:42 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 11.10-rev245
02-18 13:42 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
02-18 13:42 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com](http://www.ubuntu.com)
02-18 13:42 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
02-18 13:42 DEBUG  TaskList: ## Finished create_uninstaller
02-18 13:42 DEBUG  TaskList: ## Running create_preseed_diskimage...
02-18 13:42 DEBUG  TaskList: ## Finished create_preseed_diskimage
02-18 13:42 DEBUG  TaskList: ## Running get_diskimage...
02-18 13:42 DEBUG  TaskList: New task download
02-18 13:42 DEBUG  TaskList: ### Running download...
02-18 13:42 DEBUG  downloader: downloading [http://releases.ubuntu.com/11.10/ubuntu-11.10-wubi-amd64.tar.xz](http://releases.ubuntu.com/11.10/ubuntu-11.10-wubi-amd64.tar.xz) > C:\ubuntu\disks\ubuntu-11.10-wubi-amd64.tar.xz
02-18 13:42 DEBUG  downloader: Download start filename=C:\ubuntu\disks\ubuntu-11.10-wubi-amd64.tar.xz, url=http://releases.ubuntu.com/11.10/ubuntu-11.10-wubi-amd64.tar.xz, basename=ubuntu-11.10-wubi-amd64.tar.xz, length=507143012, text=None
02-18 13:47 DEBUG  TaskList: ### Finished download
02-18 13:47 DEBUG  downloader: download finished (read 507143012 bytes)
02-18 13:47 DEBUG  TaskList: ## Finished get_diskimage
02-18 13:47 DEBUG  TaskList: ## Running extract_diskimage...
02-18 13:51 DEBUG  TaskList: ## Finished extract_diskimage
02-18 13:51 DEBUG  TaskList: ## Running choose_disk_sizes...
02-18 13:51 DEBUG  WindowsBackend: total size=20000
  root=19744
  swap=256
  home=0
  usr=0
02-18 13:51 DEBUG  TaskList: ## Finished choose_disk_sizes
02-18 13:51 DEBUG  TaskList: ## Running expand_diskimage...
02-18 13:51 ERROR  TaskList: Error executing command
>>command=C:\Users\Jamie's\AppData\Local\Temp\pyl4C0F.tmp\bin\resize2fs.exe -f C:\ubuntu\disks\root.disk 19744M
>>retval=1
>>stderr=
>>stdout=resize2fs 1.40.6 (09-Feb-2008)
Usage: /cygdrive/c/Users/Jamies/AppData/Local/Temp/pyl4C0F.tmp/bin/resize2fs.exe -f C:/ubuntu/disks/root.disk 19744M [-d debug_flags] [-f] [-F] [-p] device [new_size]

Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 461, in expand_diskimage
  File "\lib\wubi\backends\common\utils.py", line 66, in run_command
Exception: Error executing command
>>command=C:\Users\Jamie's\AppData\Local\Temp\pyl4C0F.tmp\bin\resize2fs.exe -f C:\ubuntu\disks\root.disk 19744M
>>retval=1
>>stderr=
>>stdout=resize2fs 1.40.6 (09-Feb-2008)
Usage: /cygdrive/c/Users/Jamies/AppData/Local/Temp/pyl4C0F.tmp/bin/resize2fs.exe -f C:/ubuntu/disks/root.disk 19744M [-d debug_flags] [-f] [-F] [-p] device [new_size]


02-18 13:51 DEBUG  TaskList: # Cancelling tasklist
02-18 13:51 ERROR  root: Error executing command
>>command=C:\Users\Jamie's\AppData\Local\Temp\pyl4C0F.tmp\bin\resize2fs.exe -f C:\ubuntu\disks\root.disk 19744M
>>retval=1
>>stderr=
>>stdout=resize2fs 1.40.6 (09-Feb-2008)
Usage: /cygdrive/c/Users/Jamies/AppData/Local/Temp/pyl4C0F.tmp/bin/resize2fs.exe -f C:/ubuntu/disks/root.disk 19744M [-d debug_flags] [-f] [-F] [-p] device [new_size]

Traceback (most recent call last):
  File "\lib\wubi\application.py", line 58, in run
  File "\lib\wubi\application.py", line 132, in select_task
  File "\lib\wubi\application.py", line 158, in run_installer
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 461, in expand_diskimage
  File "\lib\wubi\backends\common\utils.py", line 66, in run_command
Exception: Error executing command
>>command=C:\Users\Jamie's\AppData\Local\Temp\pyl4C0F.tmp\bin\resize2fs.exe -f C:\ubuntu\disks\root.disk 19744M
>>retval=1
>>stderr=
>>stdout=resize2fs 1.40.6 (09-Feb-2008)
Usage: /cygdrive/c/Users/Jamies/AppData/Local/Temp/pyl4C0F.tmp/bin/resize2fs.exe -f C:/ubuntu/disks/root.disk 19744M [-d debug_flags] [-f] [-F] [-p] device [new_size]


02-18 13:51 DEBUG  TaskList: # Finished tasklist
02-18 14:02 INFO   root: === wubi 11.10 rev245 ===
02-18 14:02 DEBUG  root: Logfile is c:\users\jamie's\appdata\local\temp\wubi-11.10-rev245.log
02-18 14:02 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\ubuntu\\uninstall-wubi.exe"']
02-18 14:02 DEBUG  CommonBackend: data_dir=C:\Users\Jamie's\AppData\Local\Temp\pylD683.tmp\data
02-18 14:02 DEBUG  WindowsBackend: 7z=C:\Users\Jamie's\AppData\Local\Temp\pylD683.tmp\bin\7z.exe
02-18 14:02 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
02-18 14:02 DEBUG  CommonBackend: Fetching basic info...
02-18 14:02 DEBUG  CommonBackend: original_exe=C:\ubuntu\uninstall-wubi.exe
02-18 14:02 DEBUG  CommonBackend: platform=win32
02-18 14:02 DEBUG  CommonBackend: osname=nt
02-18 14:02 DEBUG  CommonBackend: language=en_GB
02-18 14:02 DEBUG  CommonBackend: encoding=cp1252
02-18 14:02 DEBUG  WindowsBackend: arch=amd64
02-18 14:02 DEBUG  CommonBackend: Parsing isolist=C:\Users\Jamie's\AppData\Local\Temp\pylD683.tmp\data\isolist.ini
02-18 14:02 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
02-18 14:02 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
02-18 14:02 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
02-18 14:02 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
02-18 14:02 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
02-18 14:02 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
02-18 14:02 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
02-18 14:02 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
02-18 14:02 DEBUG  WindowsBackend: Fetching host info...
02-18 14:02 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
02-18 14:02 DEBUG  WindowsBackend: windows version=vista
02-18 14:02 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium
02-18 14:02 DEBUG  WindowsBackend: windows_sp=None
02-18 14:02 DEBUG  WindowsBackend: windows_build=7600
02-18 14:02 DEBUG  WindowsBackend: gmt=0
02-18 14:02 DEBUG  WindowsBackend: country=GB
02-18 14:02 DEBUG  WindowsBackend: timezone=Europe/London
02-18 14:02 DEBUG  WindowsBackend: windows_username=Jamie's
02-18 14:02 DEBUG  WindowsBackend: user_full_name=Jamie's
02-18 14:02 DEBUG  WindowsBackend: user_directory=C:\Users\Jamie's
02-18 14:02 DEBUG  WindowsBackend: windows_language_code=1033
02-18 14:02 DEBUG  WindowsBackend: windows_language=English
02-18 14:02 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM) i3 CPU       M 380  @ 2.53GHz
02-18 14:02 DEBUG  WindowsBackend: bootloader=vista
02-18 14:02 DEBUG  WindowsBackend: system_drive=Drive(C: hd 279248.007813 mb free ntfs)
02-18 14:02 DEBUG  WindowsBackend: drive=Drive(C: hd 279248.007813 mb free ntfs)
02-18 14:02 DEBUG  WindowsBackend: drive=Drive(D: cd 0.0 mb free cdfs)
02-18 14:02 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
02-18 14:02 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
02-18 14:02 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
02-18 14:02 DEBUG  WindowsBackend: keyboard_id=134809609
02-18 14:02 DEBUG  WindowsBackend: keyboard_layout=gb
02-18 14:02 DEBUG  WindowsBackend: keyboard_variant=
02-18 14:02 DEBUG  CommonBackend: python locale=('en_GB', 'cp1252')
02-18 14:02 DEBUG  CommonBackend: locale=en_GB.UTF-8
02-18 14:02 DEBUG  WindowsBackend: total_memory_mb=3758.09765625
02-18 14:02 DEBUG  CommonBackend: Searching ISOs on USB devices
02-18 14:02 DEBUG  CommonBackend: Searching for local CDs
02-18 14:02 DEBUG  Distro:   checking whether C:\Users\Jamie's\AppData\Local\Temp\pylD683.tmp is a valid Ubuntu CD
02-18 14:02 DEBUG  Distro:     does not contain C:\Users\Jamie's\AppData\Local\Temp\pylD683.tmp\casper\filesystem.squashfs
02-18 14:02 DEBUG  Distro:   checking whether C:\Users\Jamie's\AppData\Local\Temp\pylD683.tmp is a valid Ubuntu CD
02-18 14:02 DEBUG  Distro:     does not contain C:\Users\Jamie's\AppData\Local\Temp\pylD683.tmp\casper\filesystem.squashfs
02-18 14:02 DEBUG  Distro:   checking whether C:\Users\Jamie's\AppData\Local\Temp\pylD683.tmp is a valid Kubuntu CD
02-18 14:02 DEBUG  Distro:     does not contain C:\Users\Jamie's\AppData\Local\Temp\pylD683.tmp\casper\filesystem.squashfs
02-18 14:02 DEBUG  Distro:   checking whether C:\Users\Jamie's\AppData\Local\Temp\pylD683.tmp is a valid Kubuntu CD
02-18 14:02 DEBUG  Distro:     does not contain C:\Users\Jamie's\AppData\Local\Temp\pylD683.tmp\casper\filesystem.squashfs
02-18 14:02 DEBUG  Distro:   checking whether C:\Users\Jamie's\AppData\Local\Temp\pylD683.tmp is a valid Xubuntu CD
02-18 14:02 DEBUG  Distro:     does not contain C:\Users\Jamie's\AppData\Local\Temp\pylD683.tmp\casper\filesystem.squashfs
02-18 14:02 DEBUG  Distro:   checking whether C:\Users\Jamie's\AppData\Local\Temp\pylD683.tmp is a valid Xubuntu CD
02-18 14:02 DEBUG  Distro:     does not contain C:\Users\Jamie's\AppData\Local\Temp\pylD683.tmp\casper\filesystem.squashfs
02-18 14:02 DEBUG  Distro:   checking whether C:\Users\Jamie's\AppData\Local\Temp\pylD683.tmp is a valid Mythbuntu CD
02-18 14:02 DEBUG  Distro:     does not contain C:\Users\Jamie's\AppData\Local\Temp\pylD683.tmp\casper\filesystem.squashfs
02-18 14:02 DEBUG  Distro:   checking whether C:\Users\Jamie's\AppData\Local\Temp\pylD683.tmp is a valid Mythbuntu CD
02-18 14:02 DEBUG  Distro:     does not contain C:\Users\Jamie's\AppData\Local\Temp\pylD683.tmp\casper\filesystem.squashfs
02-18 14:02 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
02-18 14:02 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-18 14:02 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
02-18 14:02 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-18 14:02 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
02-18 14:02 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-18 14:02 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
02-18 14:02 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-18 14:02 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
02-18 14:02 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-18 14:02 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
02-18 14:02 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-18 14:02 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
02-18 14:02 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-18 14:02 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
02-18 14:02 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-18 14:02 INFO   root: Running the uninstaller...
02-18 14:02 INFO   CommonBackend: This is the uninstaller running
02-18 14:02 DEBUG  WindowsFrontend: __init__...
02-18 14:02 DEBUG  WindowsFrontend: on_init...
02-18 14:02 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Jamie's\AppData\Local\Temp\pylD683.tmp\translations, languages=['en_GB', 'en']
02-18 14:02 INFO   WindowsFrontend: Operation cancelled
02-18 14:02 DEBUG  WindowsFrontend: frontend.quit
02-18 14:02 DEBUG  WindowsFrontend: frontend.on_quit
02-18 14:02 DEBUG  root: application.on_quit
02-18 14:02 INFO   root: sys.exit
02-18 14:02 INFO   root: === wubi 11.10 rev245 ===
02-18 14:02 DEBUG  root: Logfile is c:\users\jamie's\appdata\local\temp\wubi-11.10-rev245.log
02-18 14:02 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\ubuntu\\uninstall-wubi.exe"']
02-18 14:02 DEBUG  CommonBackend: data_dir=C:\Users\Jamie's\AppData\Local\Temp\pylE9C5.tmp\data
02-18 14:02 DEBUG  WindowsBackend: 7z=C:\Users\Jamie's\AppData\Local\Temp\pylE9C5.tmp\bin\7z.exe
02-18 14:02 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
02-18 14:02 DEBUG  CommonBackend: Fetching basic info...
02-18 14:02 DEBUG  CommonBackend: original_exe=C:\ubuntu\uninstall-wubi.exe
02-18 14:02 DEBUG  CommonBackend: platform=win32
02-18 14:02 DEBUG  CommonBackend: osname=nt
02-18 14:02 DEBUG  CommonBackend: language=en_GB
02-18 14:02 DEBUG  CommonBackend: encoding=cp1252
02-18 14:02 DEBUG  WindowsBackend: arch=amd64
02-18 14:02 DEBUG  CommonBackend: Parsing isolist=C:\Users\Jamie's\AppData\Local\Temp\pylE9C5.tmp\data\isolist.ini
02-18 14:02 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
02-18 14:02 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
02-18 14:02 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
02-18 14:02 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
02-18 14:02 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
02-18 14:02 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
02-18 14:02 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
02-18 14:02 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
02-18 14:02 DEBUG  WindowsBackend: Fetching host info...
02-18 14:02 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
02-18 14:02 DEBUG  WindowsBackend: windows version=vista
02-18 14:02 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium
02-18 14:02 DEBUG  WindowsBackend: windows_sp=None
02-18 14:02 DEBUG  WindowsBackend: windows_build=7600
02-18 14:02 DEBUG  WindowsBackend: gmt=0
02-18 14:02 DEBUG  WindowsBackend: country=GB
02-18 14:02 DEBUG  WindowsBackend: timezone=Europe/London
02-18 14:02 DEBUG  WindowsBackend: windows_username=Jamie's
02-18 14:02 DEBUG  WindowsBackend: user_full_name=Jamie's
02-18 14:02 DEBUG  WindowsBackend: user_directory=C:\Users\Jamie's
02-18 14:02 DEBUG  WindowsBackend: windows_language_code=1033
02-18 14:02 DEBUG  WindowsBackend: windows_language=English
02-18 14:02 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM) i3 CPU       M 380  @ 2.53GHz
02-18 14:02 DEBUG  WindowsBackend: bootloader=vista
02-18 14:02 DEBUG  WindowsBackend: system_drive=Drive(C: hd 279247.957031 mb free ntfs)
02-18 14:02 DEBUG  WindowsBackend: drive=Drive(C: hd 279247.957031 mb free ntfs)
02-18 14:02 DEBUG  WindowsBackend: drive=Drive(D: cd 0.0 mb free cdfs)
02-18 14:02 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
02-18 14:02 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
02-18 14:02 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
02-18 14:02 DEBUG  WindowsBackend: keyboard_id=134809609
02-18 14:02 DEBUG  WindowsBackend: keyboard_layout=gb
02-18 14:02 DEBUG  WindowsBackend: keyboard_variant=
02-18 14:02 DEBUG  CommonBackend: python locale=('en_GB', 'cp1252')
02-18 14:02 DEBUG  CommonBackend: locale=en_GB.UTF-8
02-18 14:02 DEBUG  WindowsBackend: total_memory_mb=3758.09765625
02-18 14:02 DEBUG  CommonBackend: Searching ISOs on USB devices
02-18 14:02 DEBUG  CommonBackend: Searching for local CDs
02-18 14:02 DEBUG  Distro:   checking whether C:\Users\Jamie's\AppData\Local\Temp\pylE9C5.tmp is a valid Ubuntu CD
02-18 14:02 DEBUG  Distro:     does not contain C:\Users\Jamie's\AppData\Local\Temp\pylE9C5.tmp\casper\filesystem.squashfs
02-18 14:02 DEBUG  Distro:   checking whether C:\Users\Jamie's\AppData\Local\Temp\pylE9C5.tmp is a valid Ubuntu CD
02-18 14:02 DEBUG  Distro:     does not contain C:\Users\Jamie's\AppData\Local\Temp\pylE9C5.tmp\casper\filesystem.squashfs
02-18 14:02 DEBUG  Distro:   checking whether C:\Users\Jamie's\AppData\Local\Temp\pylE9C5.tmp is a valid Kubuntu CD
02-18 14:02 DEBUG  Distro:     does not contain C:\Users\Jamie's\AppData\Local\Temp\pylE9C5.tmp\casper\filesystem.squashfs
02-18 14:02 DEBUG  Distro:   checking whether C:\Users\Jamie's\AppData\Local\Temp\pylE9C5.tmp is a valid Kubuntu CD
02-18 14:02 DEBUG  Distro:     does not contain C:\Users\Jamie's\AppData\Local\Temp\pylE9C5.tmp\casper\filesystem.squashfs
02-18 14:02 DEBUG  Distro:   checking whether C:\Users\Jamie's\AppData\Local\Temp\pylE9C5.tmp is a valid Xubuntu CD
02-18 14:02 DEBUG  Distro:     does not contain C:\Users\Jamie's\AppData\Local\Temp\pylE9C5.tmp\casper\filesystem.squashfs
02-18 14:02 DEBUG  Distro:   checking whether C:\Users\Jamie's\AppData\Local\Temp\pylE9C5.tmp is a valid Xubuntu CD
02-18 14:02 DEBUG  Distro:     does not contain C:\Users\Jamie's\AppData\Local\Temp\pylE9C5.tmp\casper\filesystem.squashfs
02-18 14:02 DEBUG  Distro:   checking whether C:\Users\Jamie's\AppData\Local\Temp\pylE9C5.tmp is a valid Mythbuntu CD
02-18 14:02 DEBUG  Distro:     does not contain C:\Users\Jamie's\AppData\Local\Temp\pylE9C5.tmp\casper\filesystem.squashfs
02-18 14:02 DEBUG  Distro:   checking whether C:\Users\Jamie's\AppData\Local\Temp\pylE9C5.tmp is a valid Mythbuntu CD
02-18 14:02 DEBUG  Distro:     does not contain C:\Users\Jamie's\AppData\Local\Temp\pylE9C5.tmp\casper\filesystem.squashfs
02-18 14:02 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
02-18 14:02 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-18 14:02 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
02-18 14:02 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-18 14:02 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
02-18 14:02 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-18 14:02 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
02-18 14:02 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-18 14:02 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
02-18 14:02 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-18 14:02 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
02-18 14:02 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-18 14:02 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
02-18 14:02 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-18 14:02 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
02-18 14:02 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-18 14:02 INFO   root: Running the uninstaller...
02-18 14:02 INFO   CommonBackend: This is the uninstaller running
02-18 14:02 DEBUG  WindowsFrontend: __init__...
02-18 14:02 DEBUG  WindowsFrontend: on_init...
02-18 14:02 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Jamie's\AppData\Local\Temp\pylE9C5.tmp\translations, languages=['en_GB', 'en']
02-18 14:02 INFO   root: Received settings
02-18 14:02 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Jamie's\AppData\Local\Temp\pylE9C5.tmp\translations, languages=['en_GB', 'en']
02-18 14:02 DEBUG  TaskList: # Running tasklist...
02-18 14:02 DEBUG  TaskList: ## Running Remove bootloader entry....
02-18 14:02 DEBUG  WindowsBackend: Could not find bcd id
02-18 14:02 DEBUG  WindowsBackend: undo_bootini C:
02-18 14:02 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 279247.957031 mb free ntfs)
02-18 14:02 DEBUG  TaskList: ## Finished Remove bootloader entry.
02-18 14:02 DEBUG  TaskList: ## Running Remove target dir....
02-18 14:02 DEBUG  CommonBackend: Deleting C:\ubuntu
02-18 14:02 DEBUG  TaskList: ## Finished Remove target dir.
02-18 14:02 DEBUG  TaskList: ## Running Remove registry key....
02-18 14:02 DEBUG  TaskList: ## Finished Remove registry key.
02-18 14:02 DEBUG  TaskList: # Finished tasklist
02-18 14:02 INFO   root: Almost finished uninstalling
02-18 14:02 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Jamie's\AppData\Local\Temp\pylE9C5.tmp\translations, languages=['en_GB', 'en']
02-18 14:02 INFO   root: Finished uninstallation
02-18 14:02 DEBUG  root: application.quit
02-18 14:02 DEBUG  WindowsFrontend: frontend.quit
02-18 14:02 DEBUG  WindowsFrontend: frontend.on_quit
02-18 14:02 DEBUG  root: application.on_quit
02-18 14:02 INFO   root: sys.exit
02-18 14:03 INFO   root: === wubi 11.10 rev245 ===
02-18 14:03 DEBUG  root: Logfile is c:\users\jamie's\appdata\local\temp\wubi-11.10-rev245.log
02-18 14:03 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\Users\\Jamie\'s\\Downloads\\wubi (1).exe"']
02-18 14:03 DEBUG  CommonBackend: data_dir=C:\Users\Jamie's\AppData\Local\Temp\pylE800.tmp\data
02-18 14:03 DEBUG  WindowsBackend: 7z=C:\Users\Jamie's\AppData\Local\Temp\pylE800.tmp\bin\7z.exe
02-18 14:03 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
02-18 14:03 DEBUG  CommonBackend: Fetching basic info...
02-18 14:03 DEBUG  CommonBackend: original_exe=C:\Users\Jamie's\Downloads\wubi (1).exe
02-18 14:03 DEBUG  CommonBackend: platform=win32
02-18 14:03 DEBUG  CommonBackend: osname=nt
02-18 14:03 DEBUG  CommonBackend: language=en_GB
02-18 14:03 DEBUG  CommonBackend: encoding=cp1252
02-18 14:03 DEBUG  WindowsBackend: arch=amd64
02-18 14:03 DEBUG  CommonBackend: Parsing isolist=C:\Users\Jamie's\AppData\Local\Temp\pylE800.tmp\data\isolist.ini
02-18 14:03 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
02-18 14:03 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
02-18 14:03 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
02-18 14:03 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
02-18 14:03 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
02-18 14:03 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
02-18 14:03 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
02-18 14:03 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
02-18 14:03 DEBUG  WindowsBackend: Fetching host info...
02-18 14:03 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
02-18 14:03 DEBUG  WindowsBackend: windows version=vista
02-18 14:03 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium
02-18 14:03 DEBUG  WindowsBackend: windows_sp=None
02-18 14:03 DEBUG  WindowsBackend: windows_build=7600
02-18 14:03 DEBUG  WindowsBackend: gmt=0
02-18 14:03 DEBUG  WindowsBackend: country=GB
02-18 14:03 DEBUG  WindowsBackend: timezone=Europe/London
02-18 14:03 DEBUG  WindowsBackend: windows_username=Jamie's
02-18 14:03 DEBUG  WindowsBackend: user_full_name=Jamie's
02-18 14:03 DEBUG  WindowsBackend: user_directory=C:\Users\Jamie's
02-18 14:03 DEBUG  WindowsBackend: windows_language_code=1033
02-18 14:03 DEBUG  WindowsBackend: windows_language=English
02-18 14:03 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM) i3 CPU       M 380  @ 2.53GHz
02-18 14:03 DEBUG  WindowsBackend: bootloader=vista
02-18 14:03 DEBUG  WindowsBackend: system_drive=Drive(C: hd 281470.660156 mb free ntfs)
02-18 14:03 DEBUG  WindowsBackend: drive=Drive(C: hd 281470.660156 mb free ntfs)
02-18 14:03 DEBUG  WindowsBackend: drive=Drive(D: cd 0.0 mb free cdfs)
02-18 14:03 DEBUG  WindowsBackend: uninstaller_path=None
02-18 14:03 DEBUG  WindowsBackend: previous_target_dir=None
02-18 14:03 DEBUG  WindowsBackend: previous_distro_name=None
02-18 14:03 DEBUG  WindowsBackend: keyboard_id=134809609
02-18 14:03 DEBUG  WindowsBackend: keyboard_layout=gb
02-18 14:03 DEBUG  WindowsBackend: keyboard_variant=
02-18 14:03 DEBUG  CommonBackend: python locale=('en_GB', 'cp1252')
02-18 14:03 DEBUG  CommonBackend: locale=en_GB.UTF-8
02-18 14:03 DEBUG  WindowsBackend: total_memory_mb=3758.09765625
02-18 14:03 DEBUG  CommonBackend: Searching ISOs on USB devices
02-18 14:03 DEBUG  CommonBackend: Searching for local CDs
02-18 14:03 DEBUG  Distro:   checking whether C:\Users\Jamie's\AppData\Local\Temp\pylE800.tmp is a valid Ubuntu CD
02-18 14:03 DEBUG  Distro:     does not contain C:\Users\Jamie's\AppData\Local\Temp\pylE800.tmp\casper\filesystem.squashfs
02-18 14:03 DEBUG  Distro:   checking whether C:\Users\Jamie's\AppData\Local\Temp\pylE800.tmp is a valid Ubuntu CD
02-18 14:03 DEBUG  Distro:     does not contain C:\Users\Jamie's\AppData\Local\Temp\pylE800.tmp\casper\filesystem.squashfs
02-18 14:03 DEBUG  Distro:   checking whether C:\Users\Jamie's\AppData\Local\Temp\pylE800.tmp is a valid Kubuntu CD
02-18 14:03 DEBUG  Distro:     does not contain C:\Users\Jamie's\AppData\Local\Temp\pylE800.tmp\casper\filesystem.squashfs
02-18 14:03 DEBUG  Distro:   checking whether C:\Users\Jamie's\AppData\Local\Temp\pylE800.tmp is a valid Kubuntu CD
02-18 14:03 DEBUG  Distro:     does not contain C:\Users\Jamie's\AppData\Local\Temp\pylE800.tmp\casper\filesystem.squashfs
02-18 14:03 DEBUG  Distro:   checking whether C:\Users\Jamie's\AppData\Local\Temp\pylE800.tmp is a valid Xubuntu CD
02-18 14:03 DEBUG  Distro:     does not contain C:\Users\Jamie's\AppData\Local\Temp\pylE800.tmp\casper\filesystem.squashfs
02-18 14:03 DEBUG  Distro:   checking whether C:\Users\Jamie's\AppData\Local\Temp\pylE800.tmp is a valid Xubuntu CD
02-18 14:03 DEBUG  Distro:     does not contain C:\Users\Jamie's\AppData\Local\Temp\pylE800.tmp\casper\filesystem.squashfs
02-18 14:03 DEBUG  Distro:   checking whether C:\Users\Jamie's\AppData\Local\Temp\pylE800.tmp is a valid Mythbuntu CD
02-18 14:03 DEBUG  Distro:     does not contain C:\Users\Jamie's\AppData\Local\Temp\pylE800.tmp\casper\filesystem.squashfs
02-18 14:03 DEBUG  Distro:   checking whether C:\Users\Jamie's\AppData\Local\Temp\pylE800.tmp is a valid Mythbuntu CD
02-18 14:03 DEBUG  Distro:     does not contain C:\Users\Jamie's\AppData\Local\Temp\pylE800.tmp\casper\filesystem.squashfs
02-18 14:03 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
02-18 14:03 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-18 14:03 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
02-18 14:03 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-18 14:03 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
02-18 14:03 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-18 14:03 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
02-18 14:03 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-18 14:03 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
02-18 14:03 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-18 14:03 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
02-18 14:03 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-18 14:03 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
02-18 14:03 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-18 14:03 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
02-18 14:03 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-18 14:03 INFO   root: Running the installer...
02-18 14:03 DEBUG  WindowsFrontend: __init__...
02-18 14:03 DEBUG  WindowsFrontend: on_init...
02-18 14:03 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Jamie's\AppData\Local\Temp\pylE800.tmp\translations, languages=['en_GB', 'en']
02-18 14:03 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Jamie's\AppData\Local\Temp\pylE800.tmp\translations, languages=['en_GB', 'en']
02-18 14:03 DEBUG  WinuiInstallationPage: target_drive=C:, installation_size=18000MB, distro_name=Ubuntu, language=en_GB, locale=en_GB.UTF-8, username=jamie
02-18 14:03 INFO   root: Received settings
02-18 14:03 DEBUG  CommonBackend: Searching for local CD
02-18 14:03 DEBUG  Distro:   checking whether C:\Users\Jamie's\AppData\Local\Temp\pylE800.tmp is a valid Ubuntu CD
02-18 14:03 DEBUG  Distro:     does not contain C:\Users\Jamie's\AppData\Local\Temp\pylE800.tmp\casper\filesystem.squashfs
02-18 14:03 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
02-18 14:03 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-18 14:03 DEBUG  CommonBackend: Searching for local ISO
02-18 14:03 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Jamie's\AppData\Local\Temp\pylE800.tmp\translations, languages=['en_GB', 'en']
02-18 14:03 DEBUG  TaskList: # Running tasklist...
02-18 14:03 DEBUG  TaskList: ## Running select_target_dir...
02-18 14:03 INFO   WindowsBackend: Installing into C:\ubuntu
02-18 14:03 DEBUG  TaskList: ## Finished select_target_dir
02-18 14:03 DEBUG  TaskList: ## Running create_dir_structure...
02-18 14:03 DEBUG  CommonBackend: Creating dir C:\ubuntu
02-18 14:03 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks
02-18 14:03 DEBUG  CommonBackend: Creating dir C:\ubuntu\install
02-18 14:03 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot
02-18 14:03 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot
02-18 14:03 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot\grub
02-18 14:03 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot\grub
02-18 14:03 DEBUG  TaskList: ## Finished create_dir_structure
02-18 14:03 DEBUG  TaskList: ## Running create_uninstaller...
02-18 14:03 DEBUG  WindowsBackend: Copying uninstaller C:\Users\Jamie's\Downloads\wubi (1).exe -> C:\ubuntu\uninstall-wubi.exe
02-18 14:03 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString C:\ubuntu\uninstall-wubi.exe
02-18 14:03 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir C:\ubuntu
02-18 14:03 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
02-18 14:03 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon C:\ubuntu\Ubuntu.ico
02-18 14:03 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 11.10-rev245
02-18 14:03 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
02-18 14:03 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com](http://www.ubuntu.com)
02-18 14:03 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
02-18 14:03 DEBUG  TaskList: ## Finished create_uninstaller
02-18 14:03 DEBUG  TaskList: ## Running create_preseed_diskimage...
02-18 14:03 DEBUG  TaskList: ## Finished create_preseed_diskimage
02-18 14:03 DEBUG  TaskList: ## Running get_diskimage...
02-18 14:03 DEBUG  TaskList: New task download
02-18 14:03 DEBUG  TaskList: ### Running download...
02-18 14:03 DEBUG  downloader: downloading [http://releases.ubuntu.com/11.10/ubuntu-11.10-wubi-amd64.tar.xz](http://releases.ubuntu.com/11.10/ubuntu-11.10-wubi-amd64.tar.xz) > C:\ubuntu\disks\ubuntu-11.10-wubi-amd64.tar.xz
02-18 14:03 DEBUG  downloader: Download start filename=C:\ubuntu\disks\ubuntu-11.10-wubi-amd64.tar.xz, url=http://releases.ubuntu.com/11.10/ubuntu-11.10-wubi-amd64.tar.xz, basename=ubuntu-11.10-wubi-amd64.tar.xz, length=507143012, text=None
02-18 14:10 DEBUG  TaskList: ### Finished download
02-18 14:10 DEBUG  downloader: download finished (read 507143012 bytes)
02-18 14:10 DEBUG  TaskList: ## Finished get_diskimage
02-18 14:10 DEBUG  TaskList: ## Running extract_diskimage...
02-18 14:12 DEBUG  TaskList: ## Finished extract_diskimage
02-18 14:12 DEBUG  TaskList: ## Running choose_disk_sizes...
02-18 14:12 DEBUG  WindowsBackend: total size=18000
  root=17744
  swap=256
  home=0
  usr=0
02-18 14:12 DEBUG  TaskList: ## Finished choose_disk_sizes
02-18 14:12 DEBUG  TaskList: ## Running expand_diskimage...
02-18 14:12 ERROR  TaskList: Error executing command
>>command=C:\Users\Jamie's\AppData\Local\Temp\pylE800.tmp\bin\resize2fs.exe -f C:\ubuntu\disks\root.disk 17744M
>>retval=1
>>stderr=
>>stdout=resize2fs 1.40.6 (09-Feb-2008)
Usage: /cygdrive/c/Users/Jamies/AppData/Local/Temp/pylE800.tmp/bin/resize2fs.exe -f C:/ubuntu/disks/root.disk 17744M [-d debug_flags] [-f] [-F] [-p] device [new_size]

Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 461, in expand_diskimage
  File "\lib\wubi\backends\common\utils.py", line 66, in run_command
Exception: Error executing command
>>command=C:\Users\Jamie's\AppData\Local\Temp\pylE800.tmp\bin\resize2fs.exe -f C:\ubuntu\disks\root.disk 17744M
>>retval=1
>>stderr=
>>stdout=resize2fs 1.40.6 (09-Feb-2008)
Usage: /cygdrive/c/Users/Jamies/AppData/Local/Temp/pylE800.tmp/bin/resize2fs.exe -f C:/ubuntu/disks/root.disk 17744M [-d debug_flags] [-f] [-F] [-p] device [new_size]


02-18 14:12 DEBUG  TaskList: # Cancelling tasklist
02-18 14:12 DEBUG  TaskList: # Finished tasklist
02-18 14:12 ERROR  root: Error executing command
>>command=C:\Users\Jamie's\AppData\Local\Temp\pylE800.tmp\bin\resize2fs.exe -f C:\ubuntu\disks\root.disk 17744M
>>retval=1
>>stderr=
>>stdout=resize2fs 1.40.6 (09-Feb-2008)
Usage: /cygdrive/c/Users/Jamies/AppData/Local/Temp/pylE800.tmp/bin/resize2fs.exe -f C:/ubuntu/disks/root.disk 17744M [-d debug_flags] [-f] [-F] [-p] device [new_size]

Traceback (most recent call last):
  File "\lib\wubi\application.py", line 58, in run
  File "\lib\wubi\application.py", line 132, in select_task
  File "\lib\wubi\application.py", line 158, in run_installer
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 461, in expand_diskimage
  File "\lib\wubi\backends\common\utils.py", line 66, in run_command
Exception: Error executing command
>>command=C:\Users\Jamie's\AppData\Local\Temp\pylE800.tmp\bin\resize2fs.exe -f C:\ubuntu\disks\root.disk 17744M
>>retval=1
>>stderr=
>>stdout=resize2fs 1.40.6 (09-Feb-2008)
Usage: /cygdrive/c/Users/Jamies/AppData/Local/Temp/pylE800.tmp/bin/resize2fs.exe -f C:/ubuntu/disks/root.disk 17744M [-d debug_flags] [-f] [-F] [-p] device [new_size]

---

### Post by Jamieyates14 on 2012-02-18
Second Half:

02-18 14:12 INFO   root: === wubi 11.10 rev245 ===
02-18 14:12 DEBUG  root: Logfile is c:\users\jamie's\appdata\local\temp\wubi-11.10-rev245.log
02-18 14:12 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\Users\\Jamie\'s\\Downloads\\wubi (1).exe"']
02-18 14:12 DEBUG  CommonBackend: data_dir=C:\Users\Jamie's\AppData\Local\Temp\pyl33CF.tmp\data
02-18 14:12 DEBUG  WindowsBackend: 7z=C:\Users\Jamie's\AppData\Local\Temp\pyl33CF.tmp\bin\7z.exe
02-18 14:12 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
02-18 14:12 DEBUG  CommonBackend: Fetching basic info...
02-18 14:12 DEBUG  CommonBackend: original_exe=C:\Users\Jamie's\Downloads\wubi (1).exe
02-18 14:12 DEBUG  CommonBackend: platform=win32
02-18 14:12 DEBUG  CommonBackend: osname=nt
02-18 14:12 DEBUG  CommonBackend: language=en_GB
02-18 14:12 DEBUG  CommonBackend: encoding=cp1252
02-18 14:12 DEBUG  WindowsBackend: arch=amd64
02-18 14:12 DEBUG  CommonBackend: Parsing isolist=C:\Users\Jamie's\AppData\Local\Temp\pyl33CF.tmp\data\isolist.ini
02-18 14:12 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
02-18 14:12 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
02-18 14:12 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
02-18 14:12 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
02-18 14:12 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
02-18 14:12 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
02-18 14:12 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
02-18 14:12 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
02-18 14:12 DEBUG  WindowsBackend: Fetching host info...
02-18 14:12 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
02-18 14:12 DEBUG  WindowsBackend: windows version=vista
02-18 14:12 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium
02-18 14:12 DEBUG  WindowsBackend: windows_sp=None
02-18 14:12 DEBUG  WindowsBackend: windows_build=7600
02-18 14:12 DEBUG  WindowsBackend: gmt=0
02-18 14:12 DEBUG  WindowsBackend: country=GB
02-18 14:12 DEBUG  WindowsBackend: timezone=Europe/London
02-18 14:12 DEBUG  WindowsBackend: windows_username=Jamie's
02-18 14:12 DEBUG  WindowsBackend: user_full_name=Jamie's
02-18 14:12 DEBUG  WindowsBackend: user_directory=C:\Users\Jamie's
02-18 14:12 DEBUG  WindowsBackend: windows_language_code=1033
02-18 14:12 DEBUG  WindowsBackend: windows_language=English
02-18 14:12 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM) i3 CPU       M 380  @ 2.53GHz
02-18 14:12 DEBUG  WindowsBackend: bootloader=vista
02-18 14:12 DEBUG  WindowsBackend: system_drive=Drive(C: hd 279242.988281 mb free ntfs)
02-18 14:12 DEBUG  WindowsBackend: drive=Drive(C: hd 279242.988281 mb free ntfs)
02-18 14:12 DEBUG  WindowsBackend: drive=Drive(D: cd 0.0 mb free cdfs)
02-18 14:12 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
02-18 14:12 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
02-18 14:12 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
02-18 14:12 DEBUG  WindowsBackend: keyboard_id=134809609
02-18 14:12 DEBUG  WindowsBackend: keyboard_layout=gb
02-18 14:12 DEBUG  WindowsBackend: keyboard_variant=
02-18 14:12 DEBUG  CommonBackend: python locale=('en_GB', 'cp1252')
02-18 14:12 DEBUG  CommonBackend: locale=en_GB.UTF-8
02-18 14:12 DEBUG  WindowsBackend: total_memory_mb=3758.09765625
02-18 14:12 DEBUG  CommonBackend: Searching ISOs on USB devices
02-18 14:12 DEBUG  CommonBackend: Searching for local CDs
02-18 14:12 DEBUG  Distro:   checking whether C:\Users\Jamie's\AppData\Local\Temp\pyl33CF.tmp is a valid Ubuntu CD
02-18 14:12 DEBUG  Distro:     does not contain C:\Users\Jamie's\AppData\Local\Temp\pyl33CF.tmp\casper\filesystem.squashfs
02-18 14:12 DEBUG  Distro:   checking whether C:\Users\Jamie's\AppData\Local\Temp\pyl33CF.tmp is a valid Ubuntu CD
02-18 14:12 DEBUG  Distro:     does not contain C:\Users\Jamie's\AppData\Local\Temp\pyl33CF.tmp\casper\filesystem.squashfs
02-18 14:12 DEBUG  Distro:   checking whether C:\Users\Jamie's\AppData\Local\Temp\pyl33CF.tmp is a valid Kubuntu CD
02-18 14:12 DEBUG  Distro:     does not contain C:\Users\Jamie's\AppData\Local\Temp\pyl33CF.tmp\casper\filesystem.squashfs
02-18 14:12 DEBUG  Distro:   checking whether C:\Users\Jamie's\AppData\Local\Temp\pyl33CF.tmp is a valid Kubuntu CD
02-18 14:12 DEBUG  Distro:     does not contain C:\Users\Jamie's\AppData\Local\Temp\pyl33CF.tmp\casper\filesystem.squashfs
02-18 14:12 DEBUG  Distro:   checking whether C:\Users\Jamie's\AppData\Local\Temp\pyl33CF.tmp is a valid Xubuntu CD
02-18 14:12 DEBUG  Distro:     does not contain C:\Users\Jamie's\AppData\Local\Temp\pyl33CF.tmp\casper\filesystem.squashfs
02-18 14:12 DEBUG  Distro:   checking whether C:\Users\Jamie's\AppData\Local\Temp\pyl33CF.tmp is a valid Xubuntu CD
02-18 14:12 DEBUG  Distro:     does not contain C:\Users\Jamie's\AppData\Local\Temp\pyl33CF.tmp\casper\filesystem.squashfs
02-18 14:12 DEBUG  Distro:   checking whether C:\Users\Jamie's\AppData\Local\Temp\pyl33CF.tmp is a valid Mythbuntu CD
02-18 14:12 DEBUG  Distro:     does not contain C:\Users\Jamie's\AppData\Local\Temp\pyl33CF.tmp\casper\filesystem.squashfs
02-18 14:12 DEBUG  Distro:   checking whether C:\Users\Jamie's\AppData\Local\Temp\pyl33CF.tmp is a valid Mythbuntu CD
02-18 14:12 DEBUG  Distro:     does not contain C:\Users\Jamie's\AppData\Local\Temp\pyl33CF.tmp\casper\filesystem.squashfs
02-18 14:12 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
02-18 14:12 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-18 14:12 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
02-18 14:12 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-18 14:12 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
02-18 14:12 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-18 14:12 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
02-18 14:12 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-18 14:12 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
02-18 14:12 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-18 14:12 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
02-18 14:12 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-18 14:12 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
02-18 14:12 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-18 14:12 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
02-18 14:12 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-18 14:12 INFO   root: Already installed, running the uninstaller...
02-18 14:12 INFO   root: Running the uninstaller...
02-18 14:12 INFO   CommonBackend: This is the uninstaller running
02-18 14:12 DEBUG  WindowsFrontend: __init__...
02-18 14:12 DEBUG  WindowsFrontend: on_init...
02-18 14:12 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Jamie's\AppData\Local\Temp\pyl33CF.tmp\translations, languages=['en_GB', 'en']
02-18 14:12 INFO   root: Received settings
02-18 14:12 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Jamie's\AppData\Local\Temp\pyl33CF.tmp\translations, languages=['en_GB', 'en']
02-18 14:12 DEBUG  TaskList: # Running tasklist...
02-18 14:12 DEBUG  TaskList: ## Running Remove bootloader entry....
02-18 14:12 DEBUG  WindowsBackend: Could not find bcd id
02-18 14:12 DEBUG  WindowsBackend: undo_bootini C:
02-18 14:12 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 279242.988281 mb free ntfs)
02-18 14:12 DEBUG  TaskList: ## Finished Remove bootloader entry.
02-18 14:12 DEBUG  TaskList: ## Running Remove target dir....
02-18 14:12 DEBUG  CommonBackend: Deleting C:\ubuntu
02-18 14:12 DEBUG  TaskList: ## Finished Remove target dir.
02-18 14:12 DEBUG  TaskList: ## Running Remove registry key....
02-18 14:12 DEBUG  TaskList: ## Finished Remove registry key.
02-18 14:12 DEBUG  TaskList: # Finished tasklist
02-18 14:12 INFO   root: Almost finished uninstalling
02-18 14:12 INFO   root: Finished uninstallation
02-18 14:12 DEBUG  CommonBackend: Fetching basic info...
02-18 14:12 DEBUG  CommonBackend: original_exe=C:\Users\Jamie's\Downloads\wubi (1).exe
02-18 14:12 DEBUG  CommonBackend: platform=win32
02-18 14:12 DEBUG  CommonBackend: osname=nt
02-18 14:12 DEBUG  WindowsBackend: arch=amd64
02-18 14:12 DEBUG  CommonBackend: Parsing isolist=C:\Users\Jamie's\AppData\Local\Temp\pyl33CF.tmp\data\isolist.ini
02-18 14:12 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
02-18 14:12 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
02-18 14:12 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
02-18 14:12 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
02-18 14:12 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
02-18 14:12 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
02-18 14:12 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
02-18 14:12 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
02-18 14:12 DEBUG  WindowsBackend: Fetching host info...
02-18 14:12 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
02-18 14:12 DEBUG  WindowsBackend: windows version=vista
02-18 14:12 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium
02-18 14:12 DEBUG  WindowsBackend: windows_sp=None
02-18 14:12 DEBUG  WindowsBackend: windows_build=7600
02-18 14:12 DEBUG  WindowsBackend: gmt=0
02-18 14:12 DEBUG  WindowsBackend: country=GB
02-18 14:12 DEBUG  WindowsBackend: timezone=Europe/London
02-18 14:12 DEBUG  WindowsBackend: windows_username=Jamie's
02-18 14:12 DEBUG  WindowsBackend: user_full_name=Jamie's
02-18 14:12 DEBUG  WindowsBackend: user_directory=C:\Users\Jamie's
02-18 14:12 DEBUG  WindowsBackend: windows_language_code=1033
02-18 14:12 DEBUG  WindowsBackend: windows_language=English
02-18 14:12 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM) i3 CPU       M 380  @ 2.53GHz
02-18 14:12 DEBUG  WindowsBackend: bootloader=vista
02-18 14:12 DEBUG  WindowsBackend: system_drive=Drive(C: hd 281466.183594 mb free ntfs)
02-18 14:12 DEBUG  WindowsBackend: drive=Drive(C: hd 281466.183594 mb free ntfs)
02-18 14:12 DEBUG  WindowsBackend: drive=Drive(D: cd 0.0 mb free cdfs)
02-18 14:12 DEBUG  WindowsBackend: uninstaller_path=None
02-18 14:12 DEBUG  WindowsBackend: previous_target_dir=None
02-18 14:12 DEBUG  WindowsBackend: previous_distro_name=None
02-18 14:12 DEBUG  WindowsBackend: keyboard_id=134809609
02-18 14:12 DEBUG  WindowsBackend: keyboard_layout=gb
02-18 14:12 DEBUG  WindowsBackend: keyboard_variant=
02-18 14:12 DEBUG  WindowsBackend: total_memory_mb=3758.09765625
02-18 14:12 DEBUG  CommonBackend: Searching ISOs on USB devices
02-18 14:12 DEBUG  CommonBackend: Searching for local CDs
02-18 14:12 DEBUG  Distro:   checking whether C:\Users\Jamie's\AppData\Local\Temp\pyl33CF.tmp is a valid Ubuntu CD
02-18 14:12 DEBUG  Distro:     does not contain C:\Users\Jamie's\AppData\Local\Temp\pyl33CF.tmp\casper\filesystem.squashfs
02-18 14:12 DEBUG  Distro:   checking whether C:\Users\Jamie's\AppData\Local\Temp\pyl33CF.tmp is a valid Ubuntu CD
02-18 14:12 DEBUG  Distro:     does not contain C:\Users\Jamie's\AppData\Local\Temp\pyl33CF.tmp\casper\filesystem.squashfs
02-18 14:12 DEBUG  Distro:   checking whether C:\Users\Jamie's\AppData\Local\Temp\pyl33CF.tmp is a valid Kubuntu CD
02-18 14:12 DEBUG  Distro:     does not contain C:\Users\Jamie's\AppData\Local\Temp\pyl33CF.tmp\casper\filesystem.squashfs
02-18 14:12 DEBUG  Distro:   checking whether C:\Users\Jamie's\AppData\Local\Temp\pyl33CF.tmp is a valid Kubuntu CD
02-18 14:12 DEBUG  Distro:     does not contain C:\Users\Jamie's\AppData\Local\Temp\pyl33CF.tmp\casper\filesystem.squashfs
02-18 14:12 DEBUG  Distro:   checking whether C:\Users\Jamie's\AppData\Local\Temp\pyl33CF.tmp is a valid Xubuntu CD
02-18 14:12 DEBUG  Distro:     does not contain C:\Users\Jamie's\AppData\Local\Temp\pyl33CF.tmp\casper\filesystem.squashfs
02-18 14:12 DEBUG  Distro:   checking whether C:\Users\Jamie's\AppData\Local\Temp\pyl33CF.tmp is a valid Xubuntu CD
02-18 14:12 DEBUG  Distro:     does not contain C:\Users\Jamie's\AppData\Local\Temp\pyl33CF.tmp\casper\filesystem.squashfs
02-18 14:12 DEBUG  Distro:   checking whether C:\Users\Jamie's\AppData\Local\Temp\pyl33CF.tmp is a valid Mythbuntu CD
02-18 14:12 DEBUG  Distro:     does not contain C:\Users\Jamie's\AppData\Local\Temp\pyl33CF.tmp\casper\filesystem.squashfs
02-18 14:12 DEBUG  Distro:   checking whether C:\Users\Jamie's\AppData\Local\Temp\pyl33CF.tmp is a valid Mythbuntu CD
02-18 14:12 DEBUG  Distro:     does not contain C:\Users\Jamie's\AppData\Local\Temp\pyl33CF.tmp\casper\filesystem.squashfs
02-18 14:12 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
02-18 14:12 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-18 14:12 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
02-18 14:12 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-18 14:12 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
02-18 14:12 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-18 14:12 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
02-18 14:12 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-18 14:12 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
02-18 14:12 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-18 14:12 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
02-18 14:12 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-18 14:12 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
02-18 14:12 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-18 14:12 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
02-18 14:12 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-18 14:12 INFO   root: Running the installer...
02-18 14:12 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Jamie's\AppData\Local\Temp\pyl33CF.tmp\translations, languages=['en_GB', 'en']
02-18 14:12 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Jamie's\AppData\Local\Temp\pyl33CF.tmp\translations, languages=['en_GB', 'en']
02-18 14:12 DEBUG  WinuiInstallationPage: target_drive=C:, installation_size=18000MB, distro_name=Ubuntu, language=en_GB, locale=en_GB.UTF-8, username=jamie
02-18 14:12 INFO   root: Received settings
02-18 14:12 DEBUG  CommonBackend: Searching for local CD
02-18 14:12 DEBUG  Distro:   checking whether C:\Users\Jamie's\AppData\Local\Temp\pyl33CF.tmp is a valid Ubuntu CD
02-18 14:12 DEBUG  Distro:     does not contain C:\Users\Jamie's\AppData\Local\Temp\pyl33CF.tmp\casper\filesystem.squashfs
02-18 14:12 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
02-18 14:12 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-18 14:12 DEBUG  CommonBackend: Searching for local ISO
02-18 14:12 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Jamie's\AppData\Local\Temp\pyl33CF.tmp\translations, languages=['en_GB', 'en']
02-18 14:12 DEBUG  TaskList: # Running tasklist...
02-18 14:12 DEBUG  TaskList: ## Running select_target_dir...
02-18 14:12 INFO   WindowsBackend: Installing into C:\ubuntu
02-18 14:12 DEBUG  TaskList: ## Finished select_target_dir
02-18 14:12 DEBUG  TaskList: ## Running create_dir_structure...
02-18 14:12 DEBUG  CommonBackend: Creating dir C:\ubuntu
02-18 14:12 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks
02-18 14:12 DEBUG  CommonBackend: Creating dir C:\ubuntu\install
02-18 14:12 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot
02-18 14:12 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot
02-18 14:12 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot\grub
02-18 14:12 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot\grub
02-18 14:12 DEBUG  TaskList: ## Finished create_dir_structure
02-18 14:12 DEBUG  TaskList: ## Running create_uninstaller...
02-18 14:12 DEBUG  WindowsBackend: Copying uninstaller C:\Users\Jamie's\Downloads\wubi (1).exe -> C:\ubuntu\uninstall-wubi.exe
02-18 14:12 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString C:\ubuntu\uninstall-wubi.exe
02-18 14:12 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir C:\ubuntu
02-18 14:12 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
02-18 14:12 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon C:\ubuntu\Ubuntu.ico
02-18 14:12 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 11.10-rev245
02-18 14:12 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
02-18 14:12 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com](http://www.ubuntu.com)
02-18 14:12 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
02-18 14:12 DEBUG  TaskList: ## Finished create_uninstaller
02-18 14:12 DEBUG  TaskList: ## Running create_preseed_diskimage...
02-18 14:12 DEBUG  TaskList: ## Finished create_preseed_diskimage
02-18 14:12 DEBUG  TaskList: ## Running get_diskimage...
02-18 14:12 DEBUG  TaskList: New task download
02-18 14:12 DEBUG  TaskList: ### Running download...
02-18 14:12 DEBUG  downloader: downloading [http://releases.ubuntu.com/11.10/ubuntu-11.10-wubi-amd64.tar.xz](http://releases.ubuntu.com/11.10/ubuntu-11.10-wubi-amd64.tar.xz) > C:\ubuntu\disks\ubuntu-11.10-wubi-amd64.tar.xz
02-18 14:12 DEBUG  downloader: Download start filename=C:\ubuntu\disks\ubuntu-11.10-wubi-amd64.tar.xz, url=http://releases.ubuntu.com/11.10/ubuntu-11.10-wubi-amd64.tar.xz, basename=ubuntu-11.10-wubi-amd64.tar.xz, length=507143012, text=None
02-18 14:16 DEBUG  TaskList: ### Finished download
02-18 14:16 DEBUG  downloader: download finished (read 507143012 bytes)
02-18 14:16 DEBUG  TaskList: ## Finished get_diskimage
02-18 14:16 DEBUG  TaskList: ## Running extract_diskimage...
02-18 14:18 DEBUG  TaskList: ## Finished extract_diskimage
02-18 14:18 DEBUG  TaskList: ## Running choose_disk_sizes...
02-18 14:18 DEBUG  WindowsBackend: total size=18000
  root=17744
  swap=256
  home=0
  usr=0
02-18 14:18 DEBUG  TaskList: ## Finished choose_disk_sizes
02-18 14:18 DEBUG  TaskList: ## Running expand_diskimage...
02-18 14:18 ERROR  TaskList: Error executing command
>>command=C:\Users\Jamie's\AppData\Local\Temp\pyl33CF.tmp\bin\resize2fs.exe -f C:\ubuntu\disks\root.disk 17744M
>>retval=1
>>stderr=
>>stdout=resize2fs 1.40.6 (09-Feb-2008)
Usage: /cygdrive/c/Users/Jamies/AppData/Local/Temp/pyl33CF.tmp/bin/resize2fs.exe -f C:/ubuntu/disks/root.disk 17744M [-d debug_flags] [-f] [-F] [-p] device [new_size]

Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 461, in expand_diskimage
  File "\lib\wubi\backends\common\utils.py", line 66, in run_command
Exception: Error executing command
>>command=C:\Users\Jamie's\AppData\Local\Temp\pyl33CF.tmp\bin\resize2fs.exe -f C:\ubuntu\disks\root.disk 17744M
>>retval=1
>>stderr=
>>stdout=resize2fs 1.40.6 (09-Feb-2008)
Usage: /cygdrive/c/Users/Jamies/AppData/Local/Temp/pyl33CF.tmp/bin/resize2fs.exe -f C:/ubuntu/disks/root.disk 17744M [-d debug_flags] [-f] [-F] [-p] device [new_size]


02-18 14:18 DEBUG  TaskList: # Cancelling tasklist
02-18 14:18 ERROR  root: Error executing command
>>command=C:\Users\Jamie's\AppData\Local\Temp\pyl33CF.tmp\bin\resize2fs.exe -f C:\ubuntu\disks\root.disk 17744M
>>retval=1
>>stderr=
>>stdout=resize2fs 1.40.6 (09-Feb-2008)
Usage: /cygdrive/c/Users/Jamies/AppData/Local/Temp/pyl33CF.tmp/bin/resize2fs.exe -f C:/ubuntu/disks/root.disk 17744M [-d debug_flags] [-f] [-F] [-p] device [new_size]

Traceback (most recent call last):
  File "\lib\wubi\application.py", line 58, in run
  File "\lib\wubi\application.py", line 132, in select_task
  File "\lib\wubi\application.py", line 158, in run_installer
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 461, in expand_diskimage
  File "\lib\wubi\backends\common\utils.py", line 66, in run_command
Exception: Error executing command
>>command=C:\Users\Jamie's\AppData\Local\Temp\pyl33CF.tmp\bin\resize2fs.exe -f C:\ubuntu\disks\root.disk 17744M
>>retval=1
>>stderr=
>>stdout=resize2fs 1.40.6 (09-Feb-2008)
Usage: /cygdrive/c/Users/Jamies/AppData/Local/Temp/pyl33CF.tmp/bin/resize2fs.exe -f C:/ubuntu/disks/root.disk 17744M [-d debug_flags] [-f] [-F] [-p] device [new_size]


02-18 14:18 DEBUG  TaskList: # Finished tasklist
02-18 16:28 INFO   root: === wubi 11.10 rev245 ===
02-18 16:28 DEBUG  root: Logfile is c:\users\jamie's\appdata\local\temp\wubi-11.10-rev245.log
02-18 16:28 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\ubuntu\\uninstall-wubi.exe"', '--uninstall']
02-18 16:28 DEBUG  CommonBackend: data_dir=C:\Users\Jamie's\AppData\Local\Temp\pyl37A8.tmp\data
02-18 16:28 DEBUG  WindowsBackend: 7z=C:\Users\Jamie's\AppData\Local\Temp\pyl37A8.tmp\bin\7z.exe
02-18 16:28 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
02-18 16:28 DEBUG  CommonBackend: Fetching basic info...
02-18 16:28 DEBUG  CommonBackend: original_exe=C:\ubuntu\uninstall-wubi.exe
02-18 16:28 DEBUG  CommonBackend: platform=win32
02-18 16:28 DEBUG  CommonBackend: osname=nt
02-18 16:28 DEBUG  CommonBackend: language=en_GB
02-18 16:28 DEBUG  CommonBackend: encoding=cp1252
02-18 16:28 DEBUG  WindowsBackend: arch=amd64
02-18 16:28 DEBUG  CommonBackend: Parsing isolist=C:\Users\Jamie's\AppData\Local\Temp\pyl37A8.tmp\data\isolist.ini
02-18 16:28 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
02-18 16:28 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
02-18 16:28 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
02-18 16:28 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
02-18 16:28 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
02-18 16:28 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
02-18 16:28 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
02-18 16:28 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
02-18 16:28 DEBUG  WindowsBackend: Fetching host info...
02-18 16:28 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
02-18 16:28 DEBUG  WindowsBackend: windows version=vista
02-18 16:28 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium
02-18 16:28 DEBUG  WindowsBackend: windows_sp=None
02-18 16:28 DEBUG  WindowsBackend: windows_build=7600
02-18 16:28 DEBUG  WindowsBackend: gmt=0
02-18 16:28 DEBUG  WindowsBackend: country=GB
02-18 16:28 DEBUG  WindowsBackend: timezone=Europe/London
02-18 16:28 DEBUG  WindowsBackend: windows_username=Jamie's
02-18 16:28 DEBUG  WindowsBackend: user_full_name=Jamie's
02-18 16:28 DEBUG  WindowsBackend: user_directory=C:\Users\Jamie's
02-18 16:28 DEBUG  WindowsBackend: windows_language_code=1033
02-18 16:28 DEBUG  WindowsBackend: windows_language=English
02-18 16:28 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM) i3 CPU       M 380  @ 2.53GHz
02-18 16:28 DEBUG  WindowsBackend: bootloader=vista
02-18 16:28 DEBUG  WindowsBackend: system_drive=Drive(C: hd 271781.914063 mb free ntfs)
02-18 16:28 DEBUG  WindowsBackend: drive=Drive(C: hd 271781.914063 mb free ntfs)
02-18 16:28 DEBUG  WindowsBackend: drive=Drive(D: cd 0.0 mb free cdfs)
02-18 16:28 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
02-18 16:28 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
02-18 16:28 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
02-18 16:28 DEBUG  WindowsBackend: keyboard_id=134809609
02-18 16:28 DEBUG  WindowsBackend: keyboard_layout=gb
02-18 16:28 DEBUG  WindowsBackend: keyboard_variant=
02-18 16:28 DEBUG  CommonBackend: python locale=('en_GB', 'cp1252')
02-18 16:28 DEBUG  CommonBackend: locale=en_GB.UTF-8
02-18 16:28 DEBUG  WindowsBackend: total_memory_mb=3758.09765625
02-18 16:28 DEBUG  CommonBackend: Searching ISOs on USB devices
02-18 16:28 DEBUG  CommonBackend: Searching for local CDs
02-18 16:28 DEBUG  Distro:   checking whether C:\Users\Jamie's\AppData\Local\Temp\pyl37A8.tmp is a valid Ubuntu CD
02-18 16:28 DEBUG  Distro:     does not contain C:\Users\Jamie's\AppData\Local\Temp\pyl37A8.tmp\casper\filesystem.squashfs
02-18 16:28 DEBUG  Distro:   checking whether C:\Users\Jamie's\AppData\Local\Temp\pyl37A8.tmp is a valid Ubuntu CD
02-18 16:28 DEBUG  Distro:     does not contain C:\Users\Jamie's\AppData\Local\Temp\pyl37A8.tmp\casper\filesystem.squashfs
02-18 16:28 DEBUG  Distro:   checking whether C:\Users\Jamie's\AppData\Local\Temp\pyl37A8.tmp is a valid Kubuntu CD
02-18 16:28 DEBUG  Distro:     does not contain C:\Users\Jamie's\AppData\Local\Temp\pyl37A8.tmp\casper\filesystem.squashfs
02-18 16:28 DEBUG  Distro:   checking whether C:\Users\Jamie's\AppData\Local\Temp\pyl37A8.tmp is a valid Kubuntu CD
02-18 16:28 DEBUG  Distro:     does not contain C:\Users\Jamie's\AppData\Local\Temp\pyl37A8.tmp\casper\filesystem.squashfs
02-18 16:28 DEBUG  Distro:   checking whether C:\Users\Jamie's\AppData\Local\Temp\pyl37A8.tmp is a valid Xubuntu CD
02-18 16:28 DEBUG  Distro:     does not contain C:\Users\Jamie's\AppData\Local\Temp\pyl37A8.tmp\casper\filesystem.squashfs
02-18 16:28 DEBUG  Distro:   checking whether C:\Users\Jamie's\AppData\Local\Temp\pyl37A8.tmp is a valid Xubuntu CD
02-18 16:28 DEBUG  Distro:     does not contain C:\Users\Jamie's\AppData\Local\Temp\pyl37A8.tmp\casper\filesystem.squashfs
02-18 16:28 DEBUG  Distro:   checking whether C:\Users\Jamie's\AppData\Local\Temp\pyl37A8.tmp is a valid Mythbuntu CD
02-18 16:28 DEBUG  Distro:     does not contain C:\Users\Jamie's\AppData\Local\Temp\pyl37A8.tmp\casper\filesystem.squashfs
02-18 16:28 DEBUG  Distro:   checking whether C:\Users\Jamie's\AppData\Local\Temp\pyl37A8.tmp is a valid Mythbuntu CD
02-18 16:28 DEBUG  Distro:     does not contain C:\Users\Jamie's\AppData\Local\Temp\pyl37A8.tmp\casper\filesystem.squashfs
02-18 16:28 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
02-18 16:28 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-18 16:28 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
02-18 16:28 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-18 16:28 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
02-18 16:28 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-18 16:28 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
02-18 16:28 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-18 16:28 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
02-18 16:28 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-18 16:28 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
02-18 16:28 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-18 16:28 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
02-18 16:28 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-18 16:28 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
02-18 16:28 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-18 16:28 INFO   root: Running the uninstaller...
02-18 16:28 INFO   CommonBackend: This is the uninstaller running
02-18 16:28 DEBUG  WindowsFrontend: __init__...
02-18 16:28 DEBUG  WindowsFrontend: on_init...
02-18 16:28 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Jamie's\AppData\Local\Temp\pyl37A8.tmp\translations, languages=['en_GB', 'en']
02-18 16:28 INFO   root: === wubi 11.10 rev245 ===
02-18 16:28 DEBUG  root: Logfile is c:\users\jamie's\appdata\local\temp\wubi-11.10-rev245.log
02-18 16:28 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\ubuntu\\uninstall-wubi.exe"', '--uninstall']
02-18 16:28 DEBUG  CommonBackend: data_dir=C:\Users\Jamie's\AppData\Local\Temp\pylA9CB.tmp\data
02-18 16:28 DEBUG  WindowsBackend: 7z=C:\Users\Jamie's\AppData\Local\Temp\pylA9CB.tmp\bin\7z.exe
02-18 16:28 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
02-18 16:28 DEBUG  CommonBackend: Fetching basic info...
02-18 16:28 DEBUG  CommonBackend: original_exe=C:\ubuntu\uninstall-wubi.exe
02-18 16:28 DEBUG  CommonBackend: platform=win32
02-18 16:28 DEBUG  CommonBackend: osname=nt
02-18 16:28 DEBUG  CommonBackend: language=en_GB
02-18 16:28 DEBUG  CommonBackend: encoding=cp1252
02-18 16:28 DEBUG  WindowsBackend: arch=amd64
02-18 16:28 DEBUG  CommonBackend: Parsing isolist=C:\Users\Jamie's\AppData\Local\Temp\pylA9CB.tmp\data\isolist.ini
02-18 16:28 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
02-18 16:28 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
02-18 16:28 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
02-18 16:28 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
02-18 16:28 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
02-18 16:28 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
02-18 16:28 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
02-18 16:28 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
02-18 16:28 DEBUG  WindowsBackend: Fetching host info...
02-18 16:28 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
02-18 16:28 DEBUG  WindowsBackend: windows version=vista
02-18 16:28 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium
02-18 16:28 DEBUG  WindowsBackend: windows_sp=None
02-18 16:28 DEBUG  WindowsBackend: windows_build=7600
02-18 16:28 DEBUG  WindowsBackend: gmt=0
02-18 16:28 DEBUG  WindowsBackend: country=GB
02-18 16:28 DEBUG  WindowsBackend: timezone=Europe/London
02-18 16:28 DEBUG  WindowsBackend: windows_username=Jamie's
02-18 16:28 DEBUG  WindowsBackend: user_full_name=Jamie's
02-18 16:28 DEBUG  WindowsBackend: user_directory=C:\Users\Jamie's
02-18 16:28 DEBUG  WindowsBackend: windows_language_code=1033
02-18 16:28 DEBUG  WindowsBackend: windows_language=English
02-18 16:28 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM) i3 CPU       M 380  @ 2.53GHz
02-18 16:28 DEBUG  WindowsBackend: bootloader=vista
02-18 16:28 DEBUG  WindowsBackend: system_drive=Drive(C: hd 271777.390625 mb free ntfs)
02-18 16:28 DEBUG  WindowsBackend: drive=Drive(C: hd 271777.390625 mb free ntfs)
02-18 16:28 DEBUG  WindowsBackend: drive=Drive(D: cd 0.0 mb free cdfs)
02-18 16:28 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
02-18 16:28 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
02-18 16:28 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
02-18 16:28 DEBUG  WindowsBackend: keyboard_id=134809609
02-18 16:28 DEBUG  WindowsBackend: keyboard_layout=gb
02-18 16:28 DEBUG  WindowsBackend: keyboard_variant=
02-18 16:28 DEBUG  CommonBackend: python locale=('en_GB', 'cp1252')
02-18 16:28 DEBUG  CommonBackend: locale=en_GB.UTF-8
02-18 16:28 DEBUG  WindowsBackend: total_memory_mb=3758.09765625
02-18 16:28 DEBUG  CommonBackend: Searching ISOs on USB devices
02-18 16:28 DEBUG  CommonBackend: Searching for local CDs
02-18 16:28 DEBUG  Distro:   checking whether C:\Users\Jamie's\AppData\Local\Temp\pylA9CB.tmp is a valid Ubuntu CD
02-18 16:28 DEBUG  Distro:     does not contain C:\Users\Jamie's\AppData\Local\Temp\pylA9CB.tmp\casper\filesystem.squashfs
02-18 16:28 DEBUG  Distro:   checking whether C:\Users\Jamie's\AppData\Local\Temp\pylA9CB.tmp is a valid Ubuntu CD
02-18 16:28 DEBUG  Distro:     does not contain C:\Users\Jamie's\AppData\Local\Temp\pylA9CB.tmp\casper\filesystem.squashfs
02-18 16:28 DEBUG  Distro:   checking whether C:\Users\Jamie's\AppData\Local\Temp\pylA9CB.tmp is a valid Kubuntu CD
02-18 16:28 DEBUG  Distro:     does not contain C:\Users\Jamie's\AppData\Local\Temp\pylA9CB.tmp\casper\filesystem.squashfs
02-18 16:28 DEBUG  Distro:   checking whether C:\Users\Jamie's\AppData\Local\Temp\pylA9CB.tmp is a valid Kubuntu CD
02-18 16:28 DEBUG  Distro:     does not contain C:\Users\Jamie's\AppData\Local\Temp\pylA9CB.tmp\casper\filesystem.squashfs
02-18 16:28 DEBUG  Distro:   checking whether C:\Users\Jamie's\AppData\Local\Temp\pylA9CB.tmp is a valid Xubuntu CD
02-18 16:28 DEBUG  Distro:     does not contain C:\Users\Jamie's\AppData\Local\Temp\pylA9CB.tmp\casper\filesystem.squashfs
02-18 16:28 DEBUG  Distro:   checking whether C:\Users\Jamie's\AppData\Local\Temp\pylA9CB.tmp is a valid Xubuntu CD
02-18 16:28 DEBUG  Distro:     does not contain C:\Users\Jamie's\AppData\Local\Temp\pylA9CB.tmp\casper\filesystem.squashfs
02-18 16:28 DEBUG  Distro:   checking whether C:\Users\Jamie's\AppData\Local\Temp\pylA9CB.tmp is a valid Mythbuntu CD
02-18 16:28 DEBUG  Distro:     does not contain C:\Users\Jamie's\AppData\Local\Temp\pylA9CB.tmp\casper\filesystem.squashfs
02-18 16:28 DEBUG  Distro:   checking whether C:\Users\Jamie's\AppData\Local\Temp\pylA9CB.tmp is a valid Mythbuntu CD
02-18 16:28 DEBUG  Distro:     does not contain C:\Users\Jamie's\AppData\Local\Temp\pylA9CB.tmp\casper\filesystem.squashfs
02-18 16:28 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
02-18 16:28 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-18 16:28 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
02-18 16:28 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-18 16:28 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
02-18 16:28 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-18 16:28 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
02-18 16:28 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-18 16:28 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
02-18 16:28 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-18 16:28 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
02-18 16:28 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-18 16:28 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
02-18 16:28 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-18 16:28 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
02-18 16:28 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-18 16:28 INFO   root: Running the uninstaller...
02-18 16:28 INFO   CommonBackend: This is the uninstaller running
02-18 16:28 DEBUG  WindowsFrontend: __init__...
02-18 16:28 DEBUG  WindowsFrontend: on_init...
02-18 16:28 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Jamie's\AppData\Local\Temp\pylA9CB.tmp\translations, languages=['en_GB', 'en']
02-18 16:28 INFO   WindowsFrontend: Operation cancelled
02-18 16:28 DEBUG  WindowsFrontend: frontend.quit
02-18 16:28 DEBUG  WindowsFrontend: frontend.on_quit
02-18 16:28 DEBUG  root: application.on_quit
02-18 16:28 INFO   root: sys.exit
02-18 16:28 INFO   WindowsFrontend: Operation cancelled
02-18 16:28 DEBUG  WindowsFrontend: frontend.quit
02-18 16:28 DEBUG  WindowsFrontend: frontend.on_quit
02-18 16:28 DEBUG  root: application.on_quit
02-18 16:28 INFO   root: sys.exit
02-18 16:29 INFO   root: === wubi 11.10 rev245 ===
02-18 16:29 DEBUG  root: Logfile is c:\users\jamie's\appdata\local\temp\wubi-11.10-rev245.log
02-18 16:29 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\ubuntu\\uninstall-wubi.exe"', '--uninstall']
02-18 16:29 DEBUG  CommonBackend: data_dir=C:\Users\Jamie's\AppData\Local\Temp\pyl247.tmp\data
02-18 16:29 DEBUG  WindowsBackend: 7z=C:\Users\Jamie's\AppData\Local\Temp\pyl247.tmp\bin\7z.exe
02-18 16:29 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
02-18 16:29 DEBUG  CommonBackend: Fetching basic info...
02-18 16:29 DEBUG  CommonBackend: original_exe=C:\ubuntu\uninstall-wubi.exe
02-18 16:29 DEBUG  CommonBackend: platform=win32
02-18 16:29 DEBUG  CommonBackend: osname=nt
02-18 16:29 DEBUG  CommonBackend: language=en_GB
02-18 16:29 DEBUG  CommonBackend: encoding=cp1252
02-18 16:29 DEBUG  WindowsBackend: arch=amd64
02-18 16:29 DEBUG  CommonBackend: Parsing isolist=C:\Users\Jamie's\AppData\Local\Temp\pyl247.tmp\data\isolist.ini
02-18 16:29 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
02-18 16:29 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
02-18 16:29 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
02-18 16:29 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
02-18 16:29 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
02-18 16:29 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
02-18 16:29 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
02-18 16:29 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
02-18 16:29 DEBUG  WindowsBackend: Fetching host info...
02-18 16:29 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
02-18 16:29 DEBUG  WindowsBackend: windows version=vista
02-18 16:29 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium
02-18 16:29 DEBUG  WindowsBackend: windows_sp=None
02-18 16:29 DEBUG  WindowsBackend: windows_build=7600
02-18 16:29 DEBUG  WindowsBackend: gmt=0
02-18 16:29 DEBUG  WindowsBackend: country=GB
02-18 16:29 DEBUG  WindowsBackend: timezone=Europe/London
02-18 16:29 DEBUG  WindowsBackend: windows_username=Jamie's
02-18 16:29 DEBUG  WindowsBackend: user_full_name=Jamie's
02-18 16:29 DEBUG  WindowsBackend: user_directory=C:\Users\Jamie's
02-18 16:29 DEBUG  WindowsBackend: windows_language_code=1033
02-18 16:29 DEBUG  WindowsBackend: windows_language=English
02-18 16:29 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM) i3 CPU       M 380  @ 2.53GHz
02-18 16:29 DEBUG  WindowsBackend: bootloader=vista
02-18 16:29 DEBUG  WindowsBackend: system_drive=Drive(C: hd 271616.066406 mb free ntfs)
02-18 16:29 DEBUG  WindowsBackend: drive=Drive(C: hd 271616.066406 mb free ntfs)
02-18 16:29 DEBUG  WindowsBackend: drive=Drive(D: cd 0.0 mb free cdfs)
02-18 16:29 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
02-18 16:29 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
02-18 16:29 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
02-18 16:29 DEBUG  WindowsBackend: keyboard_id=134809609
02-18 16:29 DEBUG  WindowsBackend: keyboard_layout=gb
02-18 16:29 DEBUG  WindowsBackend: keyboard_variant=
02-18 16:29 DEBUG  CommonBackend: python locale=('en_GB', 'cp1252')
02-18 16:29 DEBUG  CommonBackend: locale=en_GB.UTF-8
02-18 16:29 DEBUG  WindowsBackend: total_memory_mb=3758.09765625
02-18 16:29 DEBUG  CommonBackend: Searching ISOs on USB devices
02-18 16:29 DEBUG  CommonBackend: Searching for local CDs
02-18 16:29 DEBUG  Distro:   checking whether C:\Users\Jamie's\AppData\Local\Temp\pyl247.tmp is a valid Ubuntu CD
02-18 16:29 DEBUG  Distro:     does not contain C:\Users\Jamie's\AppData\Local\Temp\pyl247.tmp\casper\filesystem.squashfs
02-18 16:29 DEBUG  Distro:   checking whether C:\Users\Jamie's\AppData\Local\Temp\pyl247.tmp is a valid Ubuntu CD
02-18 16:29 DEBUG  Distro:     does not contain C:\Users\Jamie's\AppData\Local\Temp\pyl247.tmp\casper\filesystem.squashfs
02-18 16:29 DEBUG  Distro:   checking whether C:\Users\Jamie's\AppData\Local\Temp\pyl247.tmp is a valid Kubuntu CD
02-18 16:29 DEBUG  Distro:     does not contain C:\Users\Jamie's\AppData\Local\Temp\pyl247.tmp\casper\filesystem.squashfs
02-18 16:29 DEBUG  Distro:   checking whether C:\Users\Jamie's\AppData\Local\Temp\pyl247.tmp is a valid Kubuntu CD
02-18 16:29 DEBUG  Distro:     does not contain C:\Users\Jamie's\AppData\Local\Temp\pyl247.tmp\casper\filesystem.squashfs
02-18 16:29 DEBUG  Distro:   checking whether C:\Users\Jamie's\AppData\Local\Temp\pyl247.tmp is a valid Xubuntu CD
02-18 16:29 DEBUG  Distro:     does not contain C:\Users\Jamie's\AppData\Local\Temp\pyl247.tmp\casper\filesystem.squashfs
02-18 16:29 DEBUG  Distro:   checking whether C:\Users\Jamie's\AppData\Local\Temp\pyl247.tmp is a valid Xubuntu CD
02-18 16:29 DEBUG  Distro:     does not contain C:\Users\Jamie's\AppData\Local\Temp\pyl247.tmp\casper\filesystem.squashfs
02-18 16:29 DEBUG  Distro:   checking whether C:\Users\Jamie's\AppData\Local\Temp\pyl247.tmp is a valid Mythbuntu CD
02-18 16:29 DEBUG  Distro:     does not contain C:\Users\Jamie's\AppData\Local\Temp\pyl247.tmp\casper\filesystem.squashfs
02-18 16:29 DEBUG  Distro:   checking whether C:\Users\Jamie's\AppData\Local\Temp\pyl247.tmp is a valid Mythbuntu CD
02-18 16:29 DEBUG  Distro:     does not contain C:\Users\Jamie's\AppData\Local\Temp\pyl247.tmp\casper\filesystem.squashfs
02-18 16:29 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
02-18 16:29 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-18 16:29 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
02-18 16:29 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-18 16:29 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
02-18 16:29 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-18 16:29 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
02-18 16:29 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-18 16:29 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
02-18 16:29 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-18 16:29 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
02-18 16:29 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-18 16:29 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
02-18 16:29 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-18 16:29 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
02-18 16:29 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-18 16:29 INFO   root: Running the uninstaller...
02-18 16:29 INFO   CommonBackend: This is the uninstaller running
02-18 16:29 DEBUG  WindowsFrontend: __init__...
02-18 16:29 DEBUG  WindowsFrontend: on_init...
02-18 16:29 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Jamie's\AppData\Local\Temp\pyl247.tmp\translations, languages=['en_GB', 'en']
02-18 16:29 INFO   root: Received settings
02-18 16:29 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Jamie's\AppData\Local\Temp\pyl247.tmp\translations, languages=['en_GB', 'en']
02-18 16:29 DEBUG  TaskList: # Running tasklist...
02-18 16:29 DEBUG  TaskList: ## Running Remove bootloader entry....
02-18 16:29 DEBUG  WindowsBackend: Could not find bcd id
02-18 16:29 DEBUG  WindowsBackend: undo_bootini C:
02-18 16:29 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 271616.066406 mb free ntfs)
02-18 16:29 DEBUG  TaskList: ## Finished Remove bootloader entry.
02-18 16:29 DEBUG  TaskList: ## Running Remove target dir....
02-18 16:29 DEBUG  CommonBackend: Deleting C:\ubuntu
02-18 16:29 DEBUG  TaskList: ## Finished Remove target dir.
02-18 16:29 DEBUG  TaskList: ## Running Remove registry key....
02-18 16:29 DEBUG  TaskList: ## Finished Remove registry key.
02-18 16:29 DEBUG  TaskList: # Finished tasklist
02-18 16:29 INFO   root: Almost finished uninstalling
02-18 16:29 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Jamie's\AppData\Local\Temp\pyl247.tmp\translations, languages=['en_GB', 'en']
02-18 16:29 INFO   root: Finished uninstallation
02-18 16:29 DEBUG  root: application.quit
02-18 16:29 DEBUG  WindowsFrontend: frontend.quit
02-18 16:29 DEBUG  WindowsFrontend: frontend.on_quit
02-18 16:29 DEBUG  root: application.on_quit
02-18 16:29 INFO   root: sys.exit
End of text.

---

### Post by sadaruwan12 on 2012-02-18
Thx can you tell me the size of your C:\ partition and how much of it is free.

And the full size of your hard disk as well.

---

### Post by Jamieyates14 on 2012-02-18
> **sadaruwan12 said:**
> Thx can you tell me the size of your C:\ partition and how much of it is free.

And the full size of your hard disk as well.

The hard drive is 500gb, and partition for Ubuntu is 60gb. And It's like 205gb unused.

---

### Post by sadaruwan12 on 2012-02-18
This is the part where your getting the ERROR from.

> 02-18 14:18 DEBUG TaskList: ## Finished choose_disk_sizes
02-18 14:18 DEBUG TaskList: ## Running expand_diskimage...
02-18 14:18 ERROR TaskList: Error executing command
>>command=C:\Users\Jamie's\AppData\Local\Temp\pyl3 3CF.tmp\bin\resize2fs.exe -f C:\ubuntu\disks\root.disk 17744M

This is happening due to when the software tries to write the files it's getting disallowed for some reason.

When you run the Wubi Setup does it ask for the admin rights or just runs.

---

### Post by Jamieyates14 on 2012-02-18
> **sadaruwan12 said:**
> This is the part where your getting the ERROR from.



This is happening due to when the software tries to write the files it's getting disallowed for some reason.

When you run the Wubi Setup does it ask for the admin rights or just runs.

It just runs. I just assumed it would run with administrator rights.

---

### Post by sadaruwan12 on 2012-02-18
Try this right click on wubi(1).exe and click "Run As Administrator" or go to properties and from there go to compatibility tab then select "Run As Administrator" now press ok then double click and run the exe.

Tell us what happens.

---

### Post by Jamieyates14 on 2012-02-18
> **sadaruwan12 said:**
> Try this right click on wubi(1).exe and click "Run As Administrator" or go to properties and from there go to compatibility tab then select "Run As Administrator" now press ok then double click and run the exe.

Tell us what happens.

Oh wow, worked. Thanks for your help:D, I feel like an idiot for not realising that now :P

---

### Post by sadaruwan12 on 2012-02-19
I'm glad that it worked but I think there's a issue in your PC better check the UAC(User Account Control) settings 'cos normally the system ask you whether the setup file needs admin rights or not.

In [this guide]("http://www.howtogeek.com/howto/windows-vista/disable-user-account-control-uac-the-easy-way-on-windows-vista/") it shows how to disable it but you can use it to re-enable it if it's disabled better have it enabled 'cos you'll know what's trying to access your C:\ Drive.

If your problem is solved please mark the thread as solved using the thread tools.

---

### Post by Jamieyates14 on 2012-02-19
> **sadaruwan12 said:**
> I'm glad that it worked but I think there's a issue in your PC better check the UAC(User Account Control) settings 'cos normally the system ask you whether the setup file needs admin rights or not.

In [this guide]("http://www.howtogeek.com/howto/windows-vista/disable-user-account-control-uac-the-easy-way-on-windows-vista/") it shows how to disable it but you can use it to re-enable it if it's disabled better have it enabled 'cos you'll know what's trying to access your C:\ Drive.

If your problem is solved please mark the thread as solved using the thread tools.
Okay thanks, I'll try it.

---

### Post by bohhh on 2012-05-11
> **sadaruwan12 said:**
> Try this right click on wubi(1).exe and click "Run As Administrator" or go to properties and from there go to compatibility tab then select "Run As Administrator" now press ok then double click and run the exe.

Tell us what happens.


I'm going to reopen the thread.
I have the same problem. I have run the exe file as administrator but keep getting the same error. What else can I try?

---

