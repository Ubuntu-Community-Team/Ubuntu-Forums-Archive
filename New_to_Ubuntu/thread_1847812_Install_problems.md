---
title: "Install problems"
date: 2011-09-21
forum: New to Ubuntu
---

### Post by Akexis on 2011-09-21
Hey everyone, noob here.

I tried transferring the install files to a usb drive and put them on the desktop of an older computer because I feel like playing with Ubuntu.  I tried installing but it gave me an error log.  I tried making a disc which too gave me an error log.  Here it is:

```
09-21 02:45 INFO   root: === wubi 11.04 rev211 ===
09-21 02:45 DEBUG  root: Logfile is c:\docume~1\alexis\locals~1\temp\wubi-11.04-rev211.log
09-21 02:45 DEBUG  root: sys.argv = ['main.pyo', '--exefile="E:\\wubi.exe"']
09-21 02:45 DEBUG  CommonBackend: data_dir=C:\DOCUME~1\Alexis\LOCALS~1\Temp\pylD.tmp\data
09-21 02:45 DEBUG  WindowsBackend: 7z=C:\DOCUME~1\Alexis\LOCALS~1\Temp\pylD.tmp\bin\7z.exe
09-21 02:45 DEBUG  WindowsBackend: startup_folder=C:\Documents and Settings\All Users\Start Menu\Programs\Startup
09-21 02:45 DEBUG  CommonBackend: Fetching basic info...
09-21 02:45 DEBUG  CommonBackend: original_exe=E:\wubi.exe
09-21 02:45 DEBUG  CommonBackend: platform=win32
09-21 02:45 DEBUG  CommonBackend: osname=nt
09-21 02:45 DEBUG  CommonBackend: language=en_US
09-21 02:45 DEBUG  CommonBackend: encoding=cp1252
09-21 02:45 DEBUG  WindowsBackend: arch=i386
09-21 02:45 DEBUG  CommonBackend: Parsing isolist=C:\DOCUME~1\Alexis\LOCALS~1\Temp\pylD.tmp\data\isolist.ini
09-21 02:45 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
09-21 02:45 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
09-21 02:45 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
09-21 02:45 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
09-21 02:45 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
09-21 02:45 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
09-21 02:45 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
09-21 02:45 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
09-21 02:45 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
09-21 02:45 DEBUG  WindowsBackend: Fetching host info...
09-21 02:45 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
09-21 02:45 DEBUG  WindowsBackend: windows version=xp
09-21 02:45 DEBUG  WindowsBackend: windows_version2=Microsoft Windows XP
09-21 02:45 DEBUG  WindowsBackend: windows_sp=Service Pack 2
09-21 02:45 DEBUG  WindowsBackend: windows_build=2600
09-21 02:45 DEBUG  WindowsBackend: gmt=-7
09-21 02:45 DEBUG  WindowsBackend: country=US
09-21 02:45 DEBUG  WindowsBackend: timezone=America/Denver
09-21 02:45 DEBUG  WindowsBackend: windows_username=Alexis
09-21 02:45 DEBUG  WindowsBackend: user_full_name=Alexis
09-21 02:45 DEBUG  WindowsBackend: user_directory=C:\Documents and Settings\Alexis
09-21 02:45 DEBUG  WindowsBackend: windows_language_code=1033
09-21 02:45 DEBUG  WindowsBackend: windows_language=English
09-21 02:45 DEBUG  WindowsBackend: processor_name=              Intel(R) Pentium(R) 4 CPU 2.60GHz
09-21 02:45 DEBUG  WindowsBackend: bootloader=xp
09-21 02:45 DEBUG  WindowsBackend: system_drive=Drive(C: hd 127582.175781 mb free ntfs)
09-21 02:45 DEBUG  WindowsBackend: drive=Drive(C: hd 127582.175781 mb free ntfs)
09-21 02:45 DEBUG  WindowsBackend: drive=Drive(D: hd 4111.09765625 mb free ntfs)
09-21 02:45 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free udf)
09-21 02:45 DEBUG  WindowsBackend: uninstaller_path=None
09-21 02:45 DEBUG  WindowsBackend: previous_target_dir=None
09-21 02:45 DEBUG  WindowsBackend: previous_distro_name=None
09-21 02:45 DEBUG  WindowsBackend: keyboard_id=67699721
09-21 02:45 DEBUG  WindowsBackend: keyboard_layout=us
09-21 02:45 DEBUG  WindowsBackend: keyboard_variant=
09-21 02:45 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
09-21 02:45 DEBUG  CommonBackend: locale=en_US.UTF-8
09-21 02:45 DEBUG  WindowsBackend: total_memory_mb=895.484375
09-21 02:45 DEBUG  CommonBackend: Searching ISOs on USB devices
09-21 02:45 DEBUG  CommonBackend: Searching for local CDs
09-21 02:45 DEBUG  Distro:   checking whether C:\DOCUME~1\Alexis\LOCALS~1\Temp\pylD.tmp is a valid Ubuntu CD
09-21 02:45 DEBUG  Distro:     does not contain C:\DOCUME~1\Alexis\LOCALS~1\Temp\pylD.tmp\casper\filesystem.squashfs
09-21 02:45 DEBUG  Distro:   checking whether C:\DOCUME~1\Alexis\LOCALS~1\Temp\pylD.tmp is a valid Ubuntu CD
09-21 02:45 DEBUG  Distro:     does not contain C:\DOCUME~1\Alexis\LOCALS~1\Temp\pylD.tmp\casper\filesystem.squashfs
09-21 02:45 DEBUG  Distro:   checking whether C:\DOCUME~1\Alexis\LOCALS~1\Temp\pylD.tmp is a valid Ubuntu Netbook CD
09-21 02:45 DEBUG  Distro:     does not contain C:\DOCUME~1\Alexis\LOCALS~1\Temp\pylD.tmp\casper\filesystem.squashfs
09-21 02:45 DEBUG  Distro:   checking whether C:\DOCUME~1\Alexis\LOCALS~1\Temp\pylD.tmp is a valid Kubuntu CD
09-21 02:45 DEBUG  Distro:     does not contain C:\DOCUME~1\Alexis\LOCALS~1\Temp\pylD.tmp\casper\filesystem.squashfs
09-21 02:45 DEBUG  Distro:   checking whether C:\DOCUME~1\Alexis\LOCALS~1\Temp\pylD.tmp is a valid Kubuntu CD
09-21 02:45 DEBUG  Distro:     does not contain C:\DOCUME~1\Alexis\LOCALS~1\Temp\pylD.tmp\casper\filesystem.squashfs
09-21 02:45 DEBUG  Distro:   checking whether C:\DOCUME~1\Alexis\LOCALS~1\Temp\pylD.tmp is a valid Xubuntu CD
09-21 02:45 DEBUG  Distro:     does not contain C:\DOCUME~1\Alexis\LOCALS~1\Temp\pylD.tmp\casper\filesystem.squashfs
09-21 02:45 DEBUG  Distro:   checking whether C:\DOCUME~1\Alexis\LOCALS~1\Temp\pylD.tmp is a valid Xubuntu CD
09-21 02:45 DEBUG  Distro:     does not contain C:\DOCUME~1\Alexis\LOCALS~1\Temp\pylD.tmp\casper\filesystem.squashfs
09-21 02:45 DEBUG  Distro:   checking whether C:\DOCUME~1\Alexis\LOCALS~1\Temp\pylD.tmp is a valid Mythbuntu CD
09-21 02:45 DEBUG  Distro:     does not contain C:\DOCUME~1\Alexis\LOCALS~1\Temp\pylD.tmp\casper\filesystem.squashfs
09-21 02:45 DEBUG  Distro:   checking whether C:\DOCUME~1\Alexis\LOCALS~1\Temp\pylD.tmp is a valid Mythbuntu CD
09-21 02:45 DEBUG  Distro:     does not contain C:\DOCUME~1\Alexis\LOCALS~1\Temp\pylD.tmp\casper\filesystem.squashfs
09-21 02:45 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
09-21 02:45 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-21 02:45 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
09-21 02:45 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-21 02:45 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
09-21 02:45 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-21 02:45 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
09-21 02:45 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-21 02:45 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
09-21 02:45 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-21 02:45 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
09-21 02:45 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-21 02:45 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
09-21 02:45 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-21 02:45 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
09-21 02:45 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-21 02:45 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
09-21 02:45 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-21 02:45 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
09-21 02:45 DEBUG  Distro:   parsing info from str=Ubuntu 11.04 "Natty Narwhal" - Release i386 (20110427.1)
09-21 02:45 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '11.04', 'build': '20110427.1', 'codename': 'Natty Narwhal', 'arch': 'i386'}
09-21 02:45 DEBUG  Distro: wrong arch: i386 != amd64
09-21 02:45 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
09-21 02:45 INFO   Distro: Found a valid CD for Ubuntu: E:\
09-21 02:45 INFO   root: Running the CD menu...
09-21 02:45 DEBUG  WindowsFrontend: __init__...
09-21 02:45 DEBUG  WindowsFrontend: on_init...
09-21 02:45 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Alexis\LOCALS~1\Temp\pylD.tmp\translations, languages=['en_US', 'en']
09-21 02:45 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Alexis\LOCALS~1\Temp\pylD.tmp\translations, languages=['en_US', 'en']
09-21 02:46 INFO   root: CD menu finished
09-21 02:46 INFO   root: Running the CD boot helper...
09-21 02:46 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Alexis\LOCALS~1\Temp\pylD.tmp\translations, languages=['en_US', 'en']
09-21 02:46 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Alexis\LOCALS~1\Temp\pylD.tmp\translations, languages=['en_US', 'en']
09-21 02:46 INFO   root: CD boot helper confirmed
09-21 02:46 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Alexis\LOCALS~1\Temp\pylD.tmp\translations, languages=['en_US', 'en']
09-21 02:46 DEBUG  TaskList: # Running tasklist...
09-21 02:46 DEBUG  TaskList: ## Running select_target_dir...
09-21 02:46 INFO   WindowsBackend: Installing into C:\ubuntu
09-21 02:46 DEBUG  TaskList: ## Finished select_target_dir
09-21 02:46 DEBUG  TaskList: ## Running create_dir_structure...
09-21 02:46 DEBUG  CommonBackend: Creating dir C:\ubuntu
09-21 02:46 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks
09-21 02:46 DEBUG  CommonBackend: Creating dir C:\ubuntu\install
09-21 02:46 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot
09-21 02:46 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot
09-21 02:46 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot\grub
09-21 02:46 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot\grub
09-21 02:46 DEBUG  TaskList: ## Finished create_dir_structure
09-21 02:46 DEBUG  TaskList: ## Running uncompress_target_dir...
09-21 02:46 DEBUG  TaskList: ## Finished uncompress_target_dir
09-21 02:46 DEBUG  TaskList: ## Running create_uninstaller...
09-21 02:46 DEBUG  WindowsBackend: Copying uninstaller E:\wubi.exe -> C:\ubuntu\uninstall-wubi.exe
09-21 02:46 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString C:\ubuntu\uninstall-wubi.exe
09-21 02:46 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir C:\ubuntu
09-21 02:46 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
09-21 02:46 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon C:\ubuntu\Ubuntu.ico
09-21 02:46 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 11.04-rev211
09-21 02:46 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
09-21 02:46 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout http://www.ubuntu.com
09-21 02:46 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink http://www.ubuntu.com/support
09-21 02:46 DEBUG  TaskList: ## Finished create_uninstaller
09-21 02:46 DEBUG  TaskList: ## Running copy_installation_files...
09-21 02:46 DEBUG  WindowsBackend: Copying C:\DOCUME~1\Alexis\LOCALS~1\Temp\pylD.tmp\data\custom-installation -> C:\ubuntu\install\custom-installation
09-21 02:46 DEBUG  WindowsBackend: Copying C:\DOCUME~1\Alexis\LOCALS~1\Temp\pylD.tmp\winboot -> C:\ubuntu\winboot
09-21 02:46 DEBUG  WindowsBackend: Copying C:\DOCUME~1\Alexis\LOCALS~1\Temp\pylD.tmp\data\images\Ubuntu.ico -> C:\ubuntu\Ubuntu.ico
09-21 02:46 DEBUG  TaskList: ## Finished copy_installation_files
09-21 02:46 DEBUG  TaskList: ## Running use_cd...
09-21 02:46 DEBUG  TaskList: New task copy_file
09-21 02:46 DEBUG  TaskList: ### Running copy_file...
09-21 02:47 DEBUG  TaskList: ### Finished copy_file
09-21 02:47 DEBUG  TaskList: New task check_iso
09-21 02:47 DEBUG  TaskList: ### Running check_iso...
09-21 02:47 DEBUG  CommonBackend: Checking C:\ubuntu\install\installation.iso
09-21 02:47 DEBUG  Distro:   checking Ubuntu ISO C:\ubuntu\install\installation.iso
09-21 02:47 DEBUG  Distro:     does not contain casper\filesystem.squashfs
09-21 02:47 DEBUG  TaskList: ### Finished check_iso
09-21 02:47 DEBUG  TaskList: ## Finished use_cd
09-21 02:47 DEBUG  TaskList: ## Running extract_kernel...
09-21 02:47 ERROR  TaskList: Could not retrieve the required installation files
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 515, in extract_kernel
Exception: Could not retrieve the required installation files
09-21 02:47 DEBUG  TaskList: # Cancelling tasklist
09-21 02:47 ERROR  root: Could not retrieve the required installation files
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 57, in run
  File "\lib\wubi\application.py", line 129, in select_task
  File "\lib\wubi\application.py", line 195, in run_cd_menu
  File "\lib\wubi\application.py", line 121, in select_task
  File "\lib\wubi\application.py", line 218, in run_cd_boot
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 515, in extract_kernel
Exception: Could not retrieve the required installation files
09-21 02:47 DEBUG  TaskList: # Finished tasklist

```

From what I gather is that it can't retrieve some files.  I thought maybe I had a corrupted compressed file or had missing files, not a full download, so I downloaded again.  No luck.  I'm trying to install 11.04

Browsing here for a little bit to see if there were other issues similar to mine, it seems like maybe there are some issues with 11.04?  Should I try 10 for now?  Oh, I'm also running a 32 bit system on the old computer.  I currently have Win XP on it.

Thanks in advance for any insight.  :)

Cheers!

---

### Post by seawolf167 on 2011-09-21
> **Akexis said:**
> I tried transferring the install files to a usb drive and put them on the desktop of an older computer because I feel like playing with Ubuntu.  I tried installing but it gave me an error log.  I tried making a disc which too gave me an error log.

How did you make the bootable usb? If you didn't use [UNetbootin ]("http://unetbootin.sourceforge.net/")to do so, I suggest doing that.

Also, what do you mean by this:

> **Akexis said:**
> put them on the desktop of an older computer...

Are you attempting a Wubi install? or to replace the current OS?

Also, try again to make the cd/usb:

[LIST]
[*]Redownload the iso file
[*][MD5Sum ]("https://help.ubuntu.com/community/HowToMD5SUM")it to ensure there is no data corruption
[*]Burn it to a cd (or usb via above Unetbootin) on the slowest possible write setting
[*]Boot off the cd/usb and run the Disk Check
[*]Re-install Ubuntu
[/LIST]

---

### Post by Akexis on 2011-09-21
Ideally I'd like to replace Win XP with Ubuntu.  I'll try those options you mentioned and return with my success/failure.

---

### Post by seawolf167 on 2011-09-21
> **Akexis said:**
> Ideally I'd like to replace Win XP with Ubuntu.  I'll try those options you mentioned and return with my success/failure.

If this is the case, I'd suggest first making a backup image with [Clonezilla ]("http://www.clonezilla.org")just in case, then proceeding to install either from a USB or CD. There is documentation on how to install Ubuntu [here]("https://help.ubuntu.com/community/Installation").

---

