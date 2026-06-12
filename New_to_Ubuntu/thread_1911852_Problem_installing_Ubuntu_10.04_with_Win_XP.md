---
title: "Problem installing Ubuntu 10.04 with Win XP"
date: 2012-01-19
forum: New to Ubuntu
---

### Post by JVMS on 2012-01-19
[SIZE=3][FONT=Times New Roman]Hi, I’m trying to install Ubuntu 10.04 for several times with Windows XP, at first every thing runs smoothly with Wubi, but at the end pop out the next message:[/FONT][/SIZE]

[SIZE=3][FONT=Times New Roman]Permission denied[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]C:\docume~1\Vicente\config~1\temp\wubi-10.04-rev192.log[/FONT][/SIZE]

[SIZE=3][FONT=Times New Roman]Please help me.[/FONT][/SIZE]

---

### Post by tersogar on 2012-01-19
> **JVMS said:**
> [SIZE=3][FONT=Times New Roman]Hi, I&#8217;m trying to install Ubuntu 10.04 for several times with Windows XP, at first every thing runs smoothly with Wubi, but at the end pop out the next message:[/FONT][/SIZE]

[SIZE=3][FONT=Times New Roman]Permission denied[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]C:\docume~1\Vicente\config~1\temp\wubi-10.04-rev192.log[/FONT][/SIZE]

[SIZE=3][FONT=Times New Roman]Please help me.[/FONT][/SIZE]

Try to boot from the live cd **WITHOUT** installing 10.04.

---

### Post by Diametric on 2012-01-19
Are you trying to dual boot?  If so, I might also recommend creating Virtual Machine instead of carving out a chunk of your HD.  I've found it easier to test new OS's that way.

Good Luck!

---

### Post by bcbc on 2012-01-19
> **JVMS said:**
> [SIZE=3][FONT=Times New Roman]Hi, I’m trying to install Ubuntu 10.04 for several times with Windows XP, at first every thing runs smoothly with Wubi, but at the end pop out the next message:[/FONT][/SIZE]

[SIZE=3][FONT=Times New Roman]Permission denied[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]C:\docume~1\Vicente\config~1\temp\wubi-10.04-rev192.log[/FONT][/SIZE]

[SIZE=3][FONT=Times New Roman]Please help me.[/FONT][/SIZE]

Permission denied - is a generic catch all message. You need to post the log file to see what the problem is. (It's in the %temp% directory)

---

### Post by Karlchen on 2012-01-19
[FONT=Arial][SIZE=2]Hello, JVMS.
[/SIZE][/FONT]> **JVMS said:**
> [FONT=Arial][SIZE=2]Permission denied[/SIZE][/FONT][FONT=Arial][SIZE=2]
[/SIZE][/FONT][FONT=Arial][SIZE=2]C:\docume~1\Vicente\config~1\temp\wubi-10.04-rev192.log[/SIZE][/FONT][FONT=Arial][SIZE=2]I strongly suspect that the full error message will not just read "permission denied" and that the file causing the problem or affected by the problem will not be [/SIZE][/FONT][FONT=Arial][SIZE=2]wubi-10.04-rev192.log.
Rather this file will hold the complete list of Wubi installation steps, succeeded and failed, and hopefully the needed details on the "Permission denied" error as well.
Therefore it would be helpful if you could post the file [/SIZE][/FONT][FONT=Arial][SIZE=2]C:\docume~1\Vicente\config~1\temp\wubi-10.04-rev192.log here.

Kind regards,
Karl
--
Oops, too late, bcbc has already given this answer. :redface:
[/SIZE][/FONT]

---

### Post by JVMS on 2012-01-19
[SIZE=3][COLOR=black][FONT=Verdana]Thank you all for your kind response: Here I’m including the wubi file script ([FONT=Times New Roman]C:\docume~1\Vicente\config~1\temp\wubi-10.04-rev192.log),[/FONT] since I could not upload it as a file. [/FONT][/COLOR][COLOR=black][FONT=Verdana]I hope this is what you are requesting[/FONT][/COLOR][/SIZE]

01-08 15:56 INFO root: === wubi 10.04 rev189 ===
01-08 15:56 DEBUG root: Logfile is c:\docume~1\vicente\config~1\temp\wubi-10.04-rev189.log
01-08 15:56 DEBUG root: sys.argv = ['main.pyo', '--exefile="D:\\wubi.exe"']
01-08 15:56 DEBUG CommonBackend: data_dir=C:\DOCUME~1\vicente\CONFIG~1\Temp\pyl1.tmp\data
01-08 15:56 DEBUG WindowsBackend: 7z=C:\DOCUME~1\vicente\CONFIG~1\Temp\pyl1.tmp\bin\7z.exe
01-08 15:56 DEBUG CommonBackend: Fetching basic info...
01-08 15:56 DEBUG CommonBackend: original_exe=D:\wubi.exe
01-08 15:56 DEBUG CommonBackend: platform=win32
01-08 15:56 DEBUG CommonBackend: osname=nt
01-08 15:56 DEBUG CommonBackend: language=es_ES
01-08 15:56 DEBUG CommonBackend: encoding=cp1252
01-08 15:56 DEBUG WindowsBackend: arch=i386
01-08 15:56 DEBUG CommonBackend: Parsing isolist=C:\DOCUME~1\vicente\CONFIG~1\Temp\pyl1.tmp\data\isolist.ini
01-08 15:56 DEBUG CommonBackend: Adding distro Xubuntu-i386
01-08 15:56 DEBUG CommonBackend: Adding distro Xubuntu-amd64
01-08 15:56 DEBUG CommonBackend: Adding distro Kubuntu-amd64
01-08 15:56 DEBUG CommonBackend: Adding distro Mythbuntu-i386
01-08 15:56 DEBUG CommonBackend: Adding distro Ubuntu-amd64
01-08 15:56 DEBUG CommonBackend: Adding distro Ubuntu-i386
01-08 15:56 DEBUG CommonBackend: Adding distro Mythbuntu-amd64
01-08 15:56 DEBUG CommonBackend: Adding distro Kubuntu-i386
01-08 15:56 DEBUG CommonBackend: Adding distro KubuntuNetbook-i386
01-08 15:56 DEBUG CommonBackend: Adding distro UbuntuNetbook-i386
01-08 15:56 DEBUG WindowsBackend: Fetching host info...
01-08 15:56 DEBUG WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
01-08 15:56 DEBUG WindowsBackend: windows version=xp
01-08 15:56 DEBUG WindowsBackend: windows_version2=Microsoft Windows XP
01-08 15:56 DEBUG WindowsBackend: windows_sp=Service Pack 3
01-08 15:56 DEBUG WindowsBackend: windows_build=2600
01-08 15:56 DEBUG WindowsBackend: gmt=-5
01-08 15:56 DEBUG WindowsBackend: country=ES
01-08 15:56 DEBUG WindowsBackend: timezone=Europe/Madrid
01-08 15:56 DEBUG WindowsBackend: windows_username=vicente
01-08 15:56 DEBUG WindowsBackend: user_full_name=vicente
01-08 15:56 DEBUG WindowsBackend: user_directory=C:\Documents and Settings\vicente
01-08 15:56 DEBUG WindowsBackend: windows_language_code=1034
01-08 15:56 DEBUG WindowsBackend: windows_language=Spanish
01-08 15:56 DEBUG WindowsBackend: processor_name= Intel(R) Pentium(R) M processor 1.50GHz
01-08 15:56 DEBUG WindowsBackend: bootloader=xp
01-08 15:56 DEBUG WindowsBackend: system_drive=Drive(C: hd 24004.1757813 mb free ntfs)
01-08 15:56 DEBUG WindowsBackend: drive=Drive(C: hd 24004.1757813 mb free ntfs)
01-08 15:56 DEBUG WindowsBackend: drive=Drive(D: cd 0.0 mb free cdfs)
01-08 15:56 DEBUG WindowsBackend: uninstaller_path=None
01-08 15:56 DEBUG WindowsBackend: previous_target_dir=None
01-08 15:56 DEBUG WindowsBackend: previous_distro_name=None
01-08 15:56 DEBUG WindowsBackend: keyboard_id=67765258
01-08 15:56 DEBUG WindowsBackend: keyboard_layout=es
01-08 15:56 DEBUG WindowsBackend: keyboard_variant=
01-08 15:56 DEBUG CommonBackend: python locale=('es_ES', 'cp1252')
01-08 15:56 DEBUG CommonBackend: locale=es_ES.UTF-8
01-08 15:56 DEBUG WindowsBackend: total_memory_mb=511.2265625
01-08 15:56 DEBUG CommonBackend: Searching ISOs on USB devices
01-08 15:56 DEBUG CommonBackend: Searching for local CDs
01-08 15:56 DEBUG Distro: checking whether C:\DOCUME~1\vicente\CONFIG~1\Temp\pyl1.tmp is a valid Ubuntu CD
01-08 15:56 DEBUG Distro: does not contain C:\DOCUME~1\vicente\CONFIG~1\Temp\pyl1.tmp\casper\filesystem.squashfs
01-08 15:56 DEBUG Distro: checking whether C:\DOCUME~1\vicente\CONFIG~1\Temp\pyl1.tmp is a valid Ubuntu CD
01-08 15:56 DEBUG Distro: does not contain C:\DOCUME~1\vicente\CONFIG~1\Temp\pyl1.tmp\casper\filesystem.squashfs
01-08 15:56 DEBUG Distro: checking whether C:\DOCUME~1\vicente\CONFIG~1\Temp\pyl1.tmp is a valid Ubuntu Netbook CD
01-08 15:56 DEBUG Distro: does not contain C:\DOCUME~1\vicente\CONFIG~1\Temp\pyl1.tmp\casper\filesystem.squashfs
01-08 15:56 DEBUG Distro: checking whether C:\DOCUME~1\vicente\CONFIG~1\Temp\pyl1.tmp is a valid Kubuntu CD
01-08 15:56 DEBUG Distro: does not contain C:\DOCUME~1\vicente\CONFIG~1\Temp\pyl1.tmp\casper\filesystem.squashfs
01-08 15:56 DEBUG Distro: checking whether C:\DOCUME~1\vicente\CONFIG~1\Temp\pyl1.tmp is a valid Kubuntu CD
01-08 15:56 DEBUG Distro: does not contain C:\DOCUME~1\vicente\CONFIG~1\Temp\pyl1.tmp\casper\filesystem.squashfs
01-08 15:56 DEBUG Distro: checking whether C:\DOCUME~1\vicente\CONFIG~1\Temp\pyl1.tmp is a valid Kubuntu Netbook CD
01-08 15:56 DEBUG Distro: does not contain C:\DOCUME~1\vicente\CONFIG~1\Temp\pyl1.tmp\casper\filesystem.squashfs
01-08 15:56 DEBUG Distro: checking whether C:\DOCUME~1\vicente\CONFIG~1\Temp\pyl1.tmp is a valid Xubuntu CD
01-08 15:56 DEBUG Distro: does not contain C:\DOCUME~1\vicente\CONFIG~1\Temp\pyl1.tmp\casper\filesystem.squashfs
01-08 15:56 DEBUG Distro: checking whether C:\DOCUME~1\vicente\CONFIG~1\Temp\pyl1.tmp is a valid Xubuntu CD
01-08 15:56 DEBUG Distro: does not contain C:\DOCUME~1\vicente\CONFIG~1\Temp\pyl1.tmp\casper\filesystem.squashfs
01-08 15:56 DEBUG Distro: checking whether C:\DOCUME~1\vicente\CONFIG~1\Temp\pyl1.tmp is a valid Mythbuntu CD
01-08 15:56 DEBUG Distro: does not contain C:\DOCUME~1\vicente\CONFIG~1\Temp\pyl1.tmp\casper\filesystem.squashfs
01-08 15:56 DEBUG Distro: checking whether C:\DOCUME~1\vicente\CONFIG~1\Temp\pyl1.tmp is a valid Mythbuntu CD
01-08 15:56 DEBUG Distro: does not contain C:\DOCUME~1\vicente\CONFIG~1\Temp\pyl1.tmp\casper\filesystem.squashfs
01-08 15:56 DEBUG Distro: checking whether D:\ is a valid Ubuntu CD
01-08 15:56 DEBUG Distro: parsing info from str=Ubuntu 10.04 LTS "Lucid Lynx" - Release i386 (20100429)
01-08 15:56 DEBUG Distro: parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '10.04', 'build': '20100429', 'codename': 'Lucid Lynx', 'arch': 'i386'}
01-08 15:56 DEBUG Distro: wrong arch: i386 != amd64
01-08 15:56 DEBUG Distro: checking whether D:\ is a valid Ubuntu CD
01-08 15:56 INFO Distro: Found a valid CD for Ubuntu: D:\
01-08 15:56 INFO root: Running the CD menu...
01-08 15:56 DEBUG WindowsFrontend: __init__...
01-08 15:56 DEBUG WindowsFrontend: on_init...
01-08 15:56 INFO WinuiPage: appname=wubi, localedir=C:\DOCUME~1\vicente\CONFIG~1\Temp\pyl1.tmp\translations, languages=['es_ES', 'es']
01-08 15:56 INFO WinuiPage: appname=wubi, localedir=C:\DOCUME~1\vicente\CONFIG~1\Temp\pyl1.tmp\translations, languages=['es_ES', 'es']
01-08 15:57 INFO root: CD menu finished
01-08 15:57 INFO root: Running the installer...
01-08 15:57 INFO WinuiPage: appname=wubi, localedir=C:\DOCUME~1\vicente\CONFIG~1\Temp\pyl1.tmp\translations, languages=['es_ES', 'es']
01-08 15:57 INFO WinuiPage: appname=wubi, localedir=C:\DOCUME~1\vicente\CONFIG~1\Temp\pyl1.tmp\translations, languages=['es_ES', 'es']
01-08 15:57 DEBUG WinuiInstallationPage: target_drive=C:, installation_size=13000MB, distro_name=Ubuntu, language=es_ES, locale=es_ES.UTF-8, username=vicente
01-08 15:57 INFO root: Received settings
01-08 15:57 INFO WinuiPage: appname=wubi, localedir=C:\DOCUME~1\vicente\CONFIG~1\Temp\pyl1.tmp\translations, languages=['es_ES', 'es']
01-08 15:57 DEBUG TaskList: # Running tasklist...
01-08 15:57 DEBUG TaskList: ## Running select_target_dir...
01-08 15:57 INFO WindowsBackend: Installing into C:\ubuntu
01-08 15:57 DEBUG TaskList: ## Finished select_target_dir
01-08 15:57 DEBUG TaskList: ## Running create_dir_structure...
01-08 15:57 DEBUG CommonBackend: Creating dir C:\ubuntu
01-08 15:57 DEBUG CommonBackend: Creating dir C:\ubuntu\disks
01-08 15:57 DEBUG CommonBackend: Creating dir C:\ubuntu\install
01-08 15:57 DEBUG CommonBackend: Creating dir C:\ubuntu\install\boot
01-08 15:57 DEBUG CommonBackend: Creating dir C:\ubuntu\disks\boot
01-08 15:57 DEBUG CommonBackend: Creating dir C:\ubuntu\disks\boot\grub
01-08 15:57 DEBUG CommonBackend: Creating dir C:\ubuntu\install\boot\grub
01-08 15:57 DEBUG TaskList: ## Finished create_dir_structure
01-08 15:57 DEBUG TaskList: ## Running uncompress_target_dir...
01-08 15:57 DEBUG TaskList: ## Finished uncompress_target_dir
01-08 15:57 DEBUG TaskList: ## Running create_uninstaller...
01-08 15:57 DEBUG WindowsBackend: Copying uninstaller D:\wubi.exe -> C:\ubuntu\uninstall-wubi.exe
01-08 15:57 DEBUG registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString C:\ubuntu\uninstall-wubi.exe
01-08 15:57 DEBUG registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir C:\ubuntu
01-08 15:57 DEBUG registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
01-08 15:57 DEBUG registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon C:\ubuntu\Ubuntu.ico
01-08 15:57 DEBUG registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 10.04-rev189
01-08 15:57 DEBUG registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
01-08 15:57 DEBUG registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com](http://www.ubuntu.com)
01-08 15:57 DEBUG registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
01-08 15:57 DEBUG TaskList: ## Finished create_uninstaller
01-08 15:57 DEBUG TaskList: ## Running copy_installation_files...
01-08 15:57 DEBUG WindowsBackend: Copying C:\DOCUME~1\vicente\CONFIG~1\Temp\pyl1.tmp\data\custom-installation -> C:\ubuntu\install\custom-installation
01-08 15:57 DEBUG WindowsBackend: Copying C:\DOCUME~1\vicente\CONFIG~1\Temp\pyl1.tmp\winboot -> C:\ubuntu\winboot
01-08 15:57 DEBUG WindowsBackend: Copying C:\DOCUME~1\vicente\CONFIG~1\Temp\pyl1.tmp\data\images\Ubuntu.ico -> C:\ubuntu\Ubuntu.ico
01-08 15:57 DEBUG TaskList: ## Finished copy_installation_files
01-08 15:57 DEBUG TaskList: ## Running get_iso...
01-08 15:57 DEBUG TaskList: New task copy_file
01-08 15:57 DEBUG TaskList: ### Running copy_file...
01-08 16:02 ERROR TaskList: [Errno 13] Permission denied
Traceback (most recent call last):
File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
File "\lib\wubi\backends\common\utils.py", line 209, in copy_file
IOError: [Errno 13] Permission denied
01-08 16:02 DEBUG TaskList: # Cancelling tasklist
01-08 16:02 ERROR root: [Errno 13] Permission denied
Traceback (most recent call last):
File "\lib\wubi\application.py", line 56, in run
File "\lib\wubi\application.py", line 128, in select_task
File "\lib\wubi\application.py", line 194, in run_cd_menu
File "\lib\wubi\application.py", line 118, in select_task
File "\lib\wubi\application.py", line 156, in run_installer
File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
File "\lib\wubi\backends\common\utils.py", line 209, in copy_file
IOError: [Errno 13] Permission denied
01-08 16:02 DEBUG TaskList: New task check_iso
01-08 16:02 DEBUG CommonBackend: Searching for local ISO
01-08 16:02 DEBUG CommonBackend: Could not find any ISO or CD, downloading one now
01-08 16:02 DEBUG TaskList: New task get_metalink
01-08 16:02 ERROR TaskList: Cannot download the metalink and therefore the ISO
Traceback (most recent call last):
File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
File "\lib\wubi\backends\common\backend.py", line 493, in get_iso
File "\lib\wubi\backends\common\backend.py", line 331, in download_iso
Exception: Cannot download the metalink and therefore the ISO
01-08 16:02 DEBUG TaskList: # Cancelling tasklist
01-08 16:02 DEBUG TaskList: # Finished tasklist
01-08 16:05 INFO root: === wubi 10.04 rev189 ===
01-08 16:05 DEBUG root: Logfile is c:\docume~1\vicente\config~1\temp\wubi-10.04-rev189.log
01-08 16:05 DEBUG root: sys.argv = ['main.pyo', '--exefile="D:\\wubi.exe"']
01-08 16:05 DEBUG CommonBackend: data_dir=C:\DOCUME~1\vicente\CONFIG~1\Temp\pyl3.tmp\data
01-08 16:05 DEBUG WindowsBackend: 7z=C:\DOCUME~1\vicente\CONFIG~1\Temp\pyl3.tmp\bin\7z.exe
01-08 16:05 DEBUG CommonBackend: Fetching basic info...
01-08 16:05 DEBUG CommonBackend: original_exe=D:\wubi.exe
01-08 16:05 DEBUG CommonBackend: platform=win32
01-08 16:05 DEBUG CommonBackend: osname=nt
01-08 16:05 DEBUG CommonBackend: language=es_ES
01-08 16:05 DEBUG CommonBackend: encoding=cp1252
01-08 16:05 DEBUG WindowsBackend: arch=i386
01-08 16:05 DEBUG CommonBackend: Parsing isolist=C:\DOCUME~1\vicente\CONFIG~1\Temp\pyl3.tmp\data\isolist.ini
01-08 16:05 DEBUG CommonBackend: Adding distro Xubuntu-i386
01-08 16:05 DEBUG CommonBackend: Adding distro Xubuntu-amd64
01-08 16:05 DEBUG CommonBackend: Adding distro Kubuntu-amd64
01-08 16:05 DEBUG CommonBackend: Adding distro Mythbuntu-i386
01-08 16:05 DEBUG CommonBackend: Adding distro Ubuntu-amd64
01-08 16:05 DEBUG CommonBackend: Adding distro Ubuntu-i386
01-08 16:05 DEBUG CommonBackend: Adding distro Mythbuntu-amd64
01-08 16:05 DEBUG CommonBackend: Adding distro Kubuntu-i386
01-08 16:05 DEBUG CommonBackend: Adding distro KubuntuNetbook-i386
01-08 16:05 DEBUG CommonBackend: Adding distro UbuntuNetbook-i386
01-08 16:05 DEBUG WindowsBackend: Fetching host info...
01-08 16:05 DEBUG WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
01-08 16:05 DEBUG WindowsBackend: windows version=xp
01-08 16:05 DEBUG WindowsBackend: windows_version2=Microsoft Windows XP
01-08 16:05 DEBUG WindowsBackend: windows_sp=Service Pack 3
01-08 16:05 DEBUG WindowsBackend: windows_build=2600
01-08 16:05 DEBUG WindowsBackend: gmt=-5
01-08 16:05 DEBUG WindowsBackend: country=ES
01-08 16:05 DEBUG WindowsBackend: timezone=Europe/Madrid
01-08 16:05 DEBUG WindowsBackend: windows_username=vicente
01-08 16:05 DEBUG WindowsBackend: user_full_name=vicente
01-08 16:05 DEBUG WindowsBackend: user_directory=C:\Documents and Settings\vicente
01-08 16:05 DEBUG WindowsBackend: windows_language_code=1034
01-08 16:05 DEBUG WindowsBackend: windows_language=Spanish
01-08 16:05 DEBUG WindowsBackend: processor_name= Intel(R) Pentium(R) M processor 1.50GHz
01-08 16:05 DEBUG WindowsBackend: bootloader=xp
01-08 16:05 DEBUG WindowsBackend: system_drive=Drive(C: hd 23362.6484375 mb free ntfs)
01-08 16:05 DEBUG WindowsBackend: drive=Drive(C: hd 23362.6484375 mb free ntfs)
01-08 16:05 DEBUG WindowsBackend: drive=Drive(D: cd 0.0 mb free cdfs)
01-08 16:05 DEBUG WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
01-08 16:05 DEBUG WindowsBackend: previous_target_dir=C:\ubuntu
01-08 16:05 DEBUG WindowsBackend: previous_distro_name=Ubuntu
01-08 16:05 DEBUG WindowsBackend: keyboard_id=67765258
01-08 16:05 DEBUG WindowsBackend: keyboard_layout=es
01-08 16:05 DEBUG WindowsBackend: keyboard_variant=
01-08 16:05 DEBUG CommonBackend: python locale=('es_ES', 'cp1252')
01-08 16:05 DEBUG CommonBackend: locale=es_ES.UTF-8
01-08 16:05 DEBUG WindowsBackend: total_memory_mb=511.2265625
01-08 16:05 DEBUG CommonBackend: Searching ISOs on USB devices
01-08 16:05 DEBUG CommonBackend: Searching for local CDs
01-08 16:05 DEBUG Distro: checking whether C:\DOCUME~1\vicente\CONFIG~1\Temp\pyl3.tmp is a valid Ubuntu CD
01-08 16:05 DEBUG Distro: does not contain C:\DOCUME~1\vicente\CONFIG~1\Temp\pyl3.tmp\casper\filesystem.squashfs
01-08 16:05 DEBUG Distro: checking whether C:\DOCUME~1\vicente\CONFIG~1\Temp\pyl3.tmp is a valid Ubuntu CD
01-08 16:05 DEBUG Distro: does not contain C:\DOCUME~1\vicente\CONFIG~1\Temp\pyl3.tmp\casper\filesystem.squashfs
01-08 16:05 DEBUG Distro: checking whether C:\DOCUME~1\vicente\CONFIG~1\Temp\pyl3.tmp is a valid Ubuntu Netbook CD
01-08 16:05 DEBUG Distro: does not contain C:\DOCUME~1\vicente\CONFIG~1\Temp\pyl3.tmp\casper\filesystem.squashfs
01-08 16:05 DEBUG Distro: checking whether C:\DOCUME~1\vicente\CONFIG~1\Temp\pyl3.tmp is a valid Kubuntu CD
01-08 16:05 DEBUG Distro: does not contain C:\DOCUME~1\vicente\CONFIG~1\Temp\pyl3.tmp\casper\filesystem.squashfs
01-08 16:05 DEBUG Distro: checking whether C:\DOCUME~1\vicente\CONFIG~1\Temp\pyl3.tmp is a valid Kubuntu CD
01-08 16:05 DEBUG Distro: does not contain C:\DOCUME~1\vicente\CONFIG~1\Temp\pyl3.tmp\casper\filesystem.squashfs
01-08 16:05 DEBUG Distro: checking whether C:\DOCUME~1\vicente\CONFIG~1\Temp\pyl3.tmp is a valid Kubuntu Netbook CD
01-08 16:05 DEBUG Distro: does not contain C:\DOCUME~1\vicente\CONFIG~1\Temp\pyl3.tmp\casper\filesystem.squashfs
01-08 16:05 DEBUG Distro: checking whether C:\DOCUME~1\vicente\CONFIG~1\Temp\pyl3.tmp is a valid Xubuntu CD
01-08 16:05 DEBUG Distro: does not contain C:\DOCUME~1\vicente\CONFIG~1\Temp\pyl3.tmp\casper\filesystem.squashfs
01-08 16:05 DEBUG Distro: checking whether C:\DOCUME~1\vicente\CONFIG~1\Temp\pyl3.tmp is a valid Xubuntu CD
01-08 16:05 DEBUG Distro: does not contain C:\DOCUME~1\vicente\CONFIG~1\Temp\pyl3.tmp\casper\filesystem.squashfs
01-08 16:05 DEBUG Distro: checking whether C:\DOCUME~1\vicente\CONFIG~1\Temp\pyl3.tmp is a valid Mythbuntu CD
01-08 16:05 DEBUG Distro: does not contain C:\DOCUME~1\vicente\CONFIG~1\Temp\pyl3.tmp\casper\filesystem.squashfs
01-08 16:05 DEBUG Distro: checking whether C:\DOCUME~1\vicente\CONFIG~1\Temp\pyl3.tmp is a valid Mythbuntu CD
01-08 16:05 DEBUG Distro: does not contain C:\DOCUME~1\vicente\CONFIG~1\Temp\pyl3.tmp\casper\filesystem.squashfs
01-08 16:05 DEBUG Distro: checking whether D:\ is a valid Ubuntu CD
01-08 16:05 DEBUG Distro: parsing info from str=Ubuntu 10.04 LTS "Lucid Lynx" - Release i386 (20100429)
01-08 16:05 DEBUG Distro: parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '10.04', 'build': '20100429', 'codename': 'Lucid Lynx', 'arch': 'i386'}
01-08 16:05 DEBUG Distro: wrong arch: i386 != amd64
01-08 16:05 DEBUG Distro: checking whether D:\ is a valid Ubuntu CD
01-08 16:05 INFO Distro: Found a valid CD for Ubuntu: D:\
01-08 16:05 INFO root: Running the CD menu...
01-08 16:05 DEBUG WindowsFrontend: __init__...
01-08 16:05 DEBUG WindowsFrontend: on_init...
01-08 16:05 INFO WinuiPage: appname=wubi, localedir=C:\DOCUME~1\vicente\CONFIG~1\Temp\pyl3.tmp\translations, languages=['es_ES', 'es']
01-08 16:05 INFO WinuiPage: appname=wubi, localedir=C:\DOCUME~1\vicente\CONFIG~1\Temp\pyl3.tmp\translations, languages=['es_ES', 'es']
01-08 16:05 INFO WindowsFrontend: Operation cancelled
01-08 16:05 DEBUG WindowsFrontend: frontend.quit
01-08 16:05 DEBUG WindowsFrontend: frontend.on_quit
01-08 16:05 DEBUG root: application.on_quit
01-08 16:05 INFO root: sys.exit
01-08 16:05 INFO root: === wubi 10.04 rev189 ===
01-08 16:05 DEBUG root: Logfile is c:\docume~1\vicente\config~1\temp\wubi-10.04-rev189.log
01-08 16:05 DEBUG root: sys.argv = ['main.pyo', '--exefile="D:\\wubi.exe"', '--cdmenu']
01-08 16:05 DEBUG CommonBackend: data_dir=C:\DOCUME~1\vicente\CONFIG~1\Temp\pyl4.tmp\data
01-08 16:05 DEBUG WindowsBackend: 7z=C:\DOCUME~1\vicente\CONFIG~1\Temp\pyl4.tmp\bin\7z.exe
01-08 16:05 DEBUG CommonBackend: Fetching basic info...
01-08 16:05 DEBUG CommonBackend: original_exe=D:\wubi.exe
01-08 16:05 DEBUG CommonBackend: platform=win32
01-08 16:05 DEBUG CommonBackend: osname=nt
01-08 16:05 DEBUG CommonBackend: language=es_ES
01-08 16:05 DEBUG CommonBackend: encoding=cp1252
01-08 16:05 DEBUG WindowsBackend: arch=i386
01-08 16:05 DEBUG CommonBackend: Parsing isolist=C:\DOCUME~1\vicente\CONFIG~1\Temp\pyl4.tmp\data\isolist.ini
01-08 16:05 DEBUG CommonBackend: Adding distro Xubuntu-i386
01-08 16:05 DEBUG CommonBackend: Adding distro Xubuntu-amd64
01-08 16:05 DEBUG CommonBackend: Adding distro Kubuntu-amd64
01-08 16:05 DEBUG CommonBackend: Adding distro Mythbuntu-i386
01-08 16:05 DEBUG CommonBackend: Adding distro Ubuntu-amd64
01-08 16:05 DEBUG CommonBackend: Adding distro Ubuntu-i386
01-08 16:05 DEBUG CommonBackend: Adding distro Mythbuntu-amd64
01-08 16:05 DEBUG CommonBackend: Adding distro Kubuntu-i386
01-08 16:05 DEBUG CommonBackend: Adding distro KubuntuNetbook-i386
01-08 16:05 DEBUG CommonBackend: Adding distro UbuntuNetbook-i386
01-08 16:05 DEBUG WindowsBackend: Fetching host info...
01-08 16:05 DEBUG WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
01-08 16:05 DEBUG WindowsBackend: windows version=xp
01-08 16:05 DEBUG WindowsBackend: windows_version2=Microsoft Windows XP
01-08 16:05 DEBUG WindowsBackend: windows_sp=Service Pack 3
01-08 16:05 DEBUG WindowsBackend: windows_build=2600
01-08 16:05 DEBUG WindowsBackend: gmt=-5
01-08 16:05 DEBUG WindowsBackend: country=ES
01-08 16:05 DEBUG WindowsBackend: timezone=Europe/Madrid
01-08 16:05 DEBUG WindowsBackend: windows_username=vicente
01-08 16:05 DEBUG WindowsBackend: user_full_name=vicente
01-08 16:05 DEBUG WindowsBackend: user_directory=C:\Documents and Settings\vicente
01-08 16:05 DEBUG WindowsBackend: windows_language_code=1034
01-08 16:05 DEBUG WindowsBackend: windows_language=Spanish
01-08 16:05 DEBUG WindowsBackend: processor_name= Intel(R) Pentium(R) M processor 1.50GHz
01-08 16:05 DEBUG WindowsBackend: bootloader=xp
01-08 16:05 DEBUG WindowsBackend: system_drive=Drive(C: hd 23363.1601563 mb free ntfs)
01-08 16:05 DEBUG WindowsBackend: drive=Drive(C: hd 23363.1601563 mb free ntfs)
01-08 16:05 DEBUG WindowsBackend: drive=Drive(D: cd 0.0 mb free cdfs)
01-08 16:05 DEBUG WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
01-08 16:05 DEBUG WindowsBackend: previous_target_dir=C:\ubuntu
01-08 16:05 DEBUG WindowsBackend: previous_distro_name=Ubuntu
01-08 16:05 DEBUG WindowsBackend: keyboard_id=67765258
01-08 16:05 DEBUG WindowsBackend: keyboard_layout=es
01-08 16:05 DEBUG WindowsBackend: keyboard_variant=
01-08 16:05 DEBUG CommonBackend: python locale=('es_ES', 'cp1252')
01-08 16:05 DEBUG CommonBackend: locale=es_ES.UTF-8
01-08 16:05 DEBUG WindowsBackend: total_memory_mb=511.2265625
01-08 16:05 DEBUG CommonBackend: Searching ISOs on USB devices
01-08 16:05 DEBUG CommonBackend: Searching for local CDs
01-08 16:05 DEBUG Distro: checking whether C:\DOCUME~1\vicente\CONFIG~1\Temp\pyl4.tmp is a valid Ubuntu CD
01-08 16:05 DEBUG Distro: does not contain C:\DOCUME~1\vicente\CONFIG~1\Temp\pyl4.tmp\casper\filesystem.squashfs
01-08 16:05 DEBUG Distro: checking whether C:\DOCUME~1\vicente\CONFIG~1\Temp\pyl4.tmp is a valid Ubuntu CD
01-08 16:05 DEBUG Distro: does not contain C:\DOCUME~1\vicente\CONFIG~1\Temp\pyl4.tmp\casper\filesystem.squashfs
01-08 16:05 DEBUG Distro: checking whether C:\DOCUME~1\vicente\CONFIG~1\Temp\pyl4.tmp is a valid Ubuntu Netbook CD
01-08 16:05 DEBUG Distro: does not contain C:\DOCUME~1\vicente\CONFIG~1\Temp\pyl4.tmp\casper\filesystem.squashfs
01-08 16:05 DEBUG Distro: checking whether C:\DOCUME~1\vicente\CONFIG~1\Temp\pyl4.tmp is a valid Kubuntu CD
01-08 16:05 DEBUG Distro: does not contain C:\DOCUME~1\vicente\CONFIG~1\Temp\pyl4.tmp\casper\filesystem.squashfs
01-08 16:05 DEBUG Distro: checking whether C:\DOCUME~1\vicente\CONFIG~1\Temp\pyl4.tmp is a valid Kubuntu CD
01-08 16:05 DEBUG Distro: does not contain C:\DOCUME~1\vicente\CONFIG~1\Temp\pyl4.tmp\casper\filesystem.squashfs
01-08 16:05 DEBUG Distro: checking whether C:\DOCUME~1\vicente\CONFIG~1\Temp\pyl4.tmp is a valid Kubuntu Netbook CD
01-08 16:05 DEBUG Distro: does not contain C:\DOCUME~1\vicente\CONFIG~1\Temp\pyl4.tmp\casper\filesystem.squashfs
01-08 16:05 DEBUG Distro: checking whether C:\DOCUME~1\vicente\CONFIG~1\Temp\pyl4.tmp is a valid Xubuntu CD
01-08 16:05 DEBUG Distro: does not contain C:\DOCUME~1\vicente\CONFIG~1\Temp\pyl4.tmp\casper\filesystem.squashfs
01-08 16:05 DEBUG Distro: checking whether C:\DOCUME~1\vicente\CONFIG~1\Temp\pyl4.tmp is a valid Xubuntu CD
01-08 16:05 DEBUG Distro: does not contain C:\DOCUME~1\vicente\CONFIG~1\Temp\pyl4.tmp\casper\filesystem.squashfs
01-08 16:05 DEBUG Distro: checking whether C:\DOCUME~1\vicente\CONFIG~1\Temp\pyl4.tmp is a valid Mythbuntu CD
01-08 16:05 DEBUG Distro: does not contain C:\DOCUME~1\vicente\CONFIG~1\Temp\pyl4.tmp\casper\filesystem.squashfs
01-08 16:05 DEBUG Distro: checking whether C:\DOCUME~1\vicente\CONFIG~1\Temp\pyl4.tmp is a valid Mythbuntu CD
01-08 16:05 DEBUG Distro: does not contain C:\DOCUME~1\vicente\CONFIG~1\Temp\pyl4.tmp\casper\filesystem.squashfs
01-08 16:05 DEBUG Distro: checking whether D:\ is a valid Ubuntu CD
01-08 16:05 DEBUG Distro: parsing info from str=Ubuntu 10.04 LTS "Lucid Lynx" - Release i386 (20100429)
01-08 16:05 DEBUG Distro: parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '10.04', 'build': '20100429', 'codename': 'Lucid Lynx', 'arch': 'i386'}
01-08 16:05 DEBUG Distro: wrong arch: i386 != amd64
01-08 16:05 DEBUG Distro: checking whether D:\ is a valid Ubuntu CD
01-08 16:05 INFO Distro: Found a valid CD for Ubuntu: D:\
01-08 16:05 INFO root: Running the CD menu...
01-08 16:05 DEBUG WindowsFrontend: __init__...
01-08 16:05 DEBUG WindowsFrontend: on_init...
01-08 16:05 INFO WinuiPage: appname=wubi, localedir=C:\DOCUME~1\vicente\CONFIG~1\Temp\pyl4.tmp\translations, languages=['es_ES', 'es']
01-08 16:05 INFO WinuiPage: appname=wubi, localedir=C:\DOCUME~1\vicente\CONFIG~1\Temp\pyl4.tmp\translations, languages=['es_ES', 'es']
01-08 16:05 INFO WindowsFrontend: Operation cancelled
01-08 16:05 DEBUG WindowsFrontend: frontend.quit
01-08 16:05 DEBUG WindowsFrontend: frontend.on_quit
01-08 16:05 DEBUG root: application.on_quit
01-08 16:05 INFO root: sys.exit
01-08 16:07 INFO root: === wubi 10.04 rev189 ===
01-08 16:07 DEBUG root: Logfile is c:\docume~1\vicente\config~1\temp\wubi-10.04-rev189.log
01-08 16:07 DEBUG root: sys.argv = ['main.pyo', '--exefile="D:\\wubi.exe"']
01-08 16:07 DEBUG CommonBackend: data_dir=C:\DOCUME~1\vicente\CONFIG~1\Temp\pyl5.tmp\data
01-08 16:07 DEBUG WindowsBackend: 7z=C:\DOCUME~1\vicente\CONFIG~1\Temp\pyl5.tmp\bin\7z.exe
01-08 16:07 DEBUG CommonBackend: Fetching basic info...
01-08 16:07 DEBUG CommonBackend: original_exe=D:\wubi.exe
01-08 16:07 DEBUG CommonBackend: platform=win32
01-08 16:07 DEBUG CommonBackend: osname=nt
01-08 16:07 DEBUG CommonBackend: language=es_ES
01-08 16:07 DEBUG CommonBackend: encoding=cp1252
01-08 16:07 DEBUG WindowsBackend: arch=i386
01-08 16:07 DEBUG CommonBackend: Parsing isolist=C:\DOCUME~1\vicente\CONFIG~1\Temp\pyl5.tmp\data\isolist.ini
01-08 16:07 DEBUG CommonBackend: Adding distro Xubuntu-i386
01-08 16:07 DEBUG CommonBackend: Adding distro Xubuntu-amd64
01-08 16:07 DEBUG CommonBackend: Adding distro Kubuntu-amd64
01-08 16:07 DEBUG CommonBackend: Adding distro Mythbuntu-i386
01-08 16:07 DEBUG CommonBackend: Adding distro Ubuntu-amd64
01-08 16:07 DEBUG CommonBackend: Adding distro Ubuntu-i386
01-08 16:07 DEBUG CommonBackend: Adding distro Mythbuntu-amd64
01-08 16:07 DEBUG CommonBackend: Adding distro Kubuntu-i386
01-08 16:07 DEBUG CommonBackend: Adding distro KubuntuNetbook-i386
01-08 16:07 DEBUG CommonBackend: Adding distro UbuntuNetbook-i386
01-08 16:07 DEBUG WindowsBackend: Fetching host info...
01-08 16:07 DEBUG WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
01-08 16:07 DEBUG WindowsBackend: windows version=xp
01-08 16:07 DEBUG WindowsBackend: windows_version2=Microsoft Windows XP
01-08 16:07 DEBUG WindowsBackend: windows_sp=Service Pack 3
01-08 16:07 DEBUG WindowsBackend: windows_build=2600
01-08 16:07 DEBUG WindowsBackend: gmt=-5
01-08 16:07 DEBUG WindowsBackend: country=ES
01-08 16:07 DEBUG WindowsBackend: timezone=Europe/Madrid
01-08 16:07 DEBUG WindowsBackend: windows_username=vicente
01-08 16:07 DEBUG WindowsBackend: user_full_name=vicente
01-08 16:07 DEBUG WindowsBackend: user_directory=C:\Documents and Settings\vicente
01-08 16:07 DEBUG WindowsBackend: windows_language_code=1034
01-08 16:07 DEBUG WindowsBackend: windows_language=Spanish
01-08 16:07 DEBUG WindowsBackend: processor_name= Intel(R) Pentium(R) M processor 1.50GHz
01-08 16:07 DEBUG WindowsBackend: bootloader=xp
01-08 16:07 DEBUG WindowsBackend: system_drive=Drive(C: hd 23361.9921875 mb free ntfs)
01-08 16:07 DEBUG WindowsBackend: drive=Drive(C: hd 23361.9921875 mb free ntfs)
01-08 16:07 DEBUG WindowsBackend: drive=Drive(D: cd 0.0 mb free cdfs)
01-08 16:07 DEBUG WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
01-08 16:07 DEBUG WindowsBackend: previous_target_dir=C:\ubuntu
01-08 16:07 DEBUG WindowsBackend: previous_distro_name=Ubuntu
01-08 16:07 DEBUG WindowsBackend: keyboard_id=67765258
01-08 16:07 DEBUG WindowsBackend: keyboard_layout=es
01-08 16:07 DEBUG WindowsBackend: keyboard_variant=
01-08 16:07 DEBUG CommonBackend: python locale=('es_ES', 'cp1252')
01-08 16:07 DEBUG CommonBackend: locale=es_ES.UTF-8
01-08 16:07 DEBUG WindowsBackend: total_memory_mb=511.2265625
01-08 16:07 DEBUG CommonBackend: Searching ISOs on USB devices
01-08 16:07 DEBUG CommonBackend: Searching for local CDs
01-08 16:07 DEBUG Distro: checking whether C:\DOCUME~1\vicente\CONFIG~1\Temp\pyl5.tmp is a valid Ubuntu CD
01-08 16:07 DEBUG Distro: does not contain C:\DOCUME~1\vicente\CONFIG~1\Temp\pyl5.tmp\casper\filesystem.squashfs
01-08 16:07 DEBUG Distro: checking whether C:\DOCUME~1\vicente\CONFIG~1\Temp\pyl5.tmp is a valid Ubuntu CD
01-08 16:07 DEBUG Distro: does not contain C:\DOCUME~1\vicente\CONFIG~1\Temp\pyl5.tmp\casper\filesystem.squashfs
01-08 16:07 DEBUG Distro: checking whether C:\DOCUME~1\vicente\CONFIG~1\Temp\pyl5.tmp is a valid Ubuntu Netbook CD
01-08 16:07 DEBUG Distro: does not contain C:\DOCUME~1\vicente\CONFIG~1\Temp\pyl5.tmp\casper\filesystem.squashfs
01-08 16:07 DEBUG Distro: checking whether C:\DOCUME~1\vicente\CONFIG~1\Temp\pyl5.tmp is a valid Kubuntu CD
01-08 16:07 DEBUG Distro: does not contain C:\DOCUME~1\vicente\CONFIG~1\Temp\pyl5.tmp\casper\filesystem.squashfs
01-08 16:07 DEBUG Distro: checking whether C:\DOCUME~1\vicente\CONFIG~1\Temp\pyl5.tmp is a valid Kubuntu CD
01-08 16:07 DEBUG Distro: does not contain C:\DOCUME~1\vicente\CONFIG~1\Temp\pyl5.tmp\casper\filesystem.squashfs
01-08 16:07 DEBUG Distro: checking whether C:\DOCUME~1\vicente\CONFIG~1\Temp\pyl5.tmp is a valid Kubuntu Netbook CD
01-08 16:07 DEBUG Distro: does not contain C:\DOCUME~1\vicente\CONFIG~1\Temp\pyl5.tmp\casper\filesystem.squashfs
01-08 16:07 DEBUG Distro: checking whether C:\DOCUME~1\vicente\CONFIG~1\Temp\pyl5.tmp is a valid Xubuntu CD
01-08 16:07 DEBUG Distro: does not contain C:\DOCUME~1\vicente\CONFIG~1\Temp\pyl5.tmp\casper\filesystem.squashfs
01-08 16:07 DEBUG Distro: checking whether C:\DOCUME~1\vicente\CONFIG~1\Temp\pyl5.tmp is a valid Xubuntu CD
01-08 16:07 DEBUG Distro: does not contain C:\DOCUME~1\vicente\CONFIG~1\Temp\pyl5.tmp\casper\filesystem.squashfs
01-08 16:07 DEBUG Distro: checking whether C:\DOCUME~1\vicente\CONFIG~1\Temp\pyl5.tmp is a valid Mythbuntu CD
01-08 16:07 DEBUG Distro: does not contain C:\DOCUME~1\vicente\CONFIG~1\Temp\pyl5.tmp\casper\filesystem.squashfs
01-08 16:07 DEBUG Distro: checking whether C:\DOCUME~1\vicente\CONFIG~1\Temp\pyl5.tmp is a valid Mythbuntu CD
01-08 16:07 DEBUG Distro: does not contain C:\DOCUME~1\vicente\CONFIG~1\Temp\pyl5.tmp\casper\filesystem.squashfs
01-08 16:07 DEBUG Distro: checking whether D:\ is a valid Ubuntu CD
01-08 16:07 DEBUG Distro: parsing info from str=Ubuntu 10.04 LTS "Lucid Lynx" - Release i386 (20100429)
01-08 16:07 DEBUG Distro: parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '10.04', 'build': '20100429', 'codename': 'Lucid Lynx', 'arch': 'i386'}
01-08 16:07 DEBUG Distro: wrong arch: i386 != amd64
01-08 16:07 DEBUG Distro: checking whether D:\ is a valid Ubuntu CD
01-08 16:07 INFO Distro: Found a valid CD for Ubuntu: D:\
01-08 16:07 INFO root: Running the CD menu...
01-08 16:07 DEBUG WindowsFrontend: __init__...
01-08 16:07 DEBUG WindowsFrontend: on_init...
01-08 16:07 INFO WinuiPage: appname=wubi, localedir=C:\DOCUME~1\vicente\CONFIG~1\Temp\pyl5.tmp\translations, languages=['es_ES', 'es']
01-08 16:07 INFO WinuiPage: appname=wubi, localedir=C:\DOCUME~1\vicente\CONFIG~1\Temp\pyl5.tmp\translations, languages=['es_ES', 'es']
01-08 16:08 INFO root: CD menu finished
01-08 16:08 INFO root: Already installed, running the uninstaller...
01-08 16:08 INFO root: Running the uninstaller...
01-08 16:08 INFO CommonBackend: This is the uninstaller running
01-08 16:08 INFO WinuiPage: appname=wubi, localedir=C:\DOCUME~1\vicente\CONFIG~1\Temp\pyl5.tmp\translations, languages=['es_ES', 'es']
01-08 16:08 INFO root: Received settings
01-08 16:08 INFO WinuiPage: appname=wubi, localedir=C:\DOCUME~1\vicente\CONFIG~1\Temp\pyl5.tmp\translations, languages=['es_ES', 'es']
01-08 16:08 DEBUG TaskList: # Running tasklist...
01-08 16:08 DEBUG TaskList: ## Running Hacer una copia de la ISO...
01-08 16:08 DEBUG TaskList: ## Finished Hacer una copia de la ISO
01-08 16:08 DEBUG TaskList: ## Running Quitar entrada del cargador de arranque...
01-08 16:08 ERROR WindowsBackend: Cannot find bcdedit
01-08 16:08 DEBUG WindowsBackend: undo_bootini C:
01-08 16:08 DEBUG WindowsBackend: undo_configsys Drive(C: hd 23361.9921875 mb free ntfs)
01-08 16:08 DEBUG TaskList: ## Finished Quitar entrada del cargador de arranque
01-08 16:08 DEBUG TaskList: ## Running Borrar el directorio de destino...
01-08 16:08 DEBUG CommonBackend: Deleting C:\ubuntu
01-08 16:08 DEBUG TaskList: ## Finished Borrar el directorio de destino
01-08 16:08 DEBUG TaskList: ## Running Borrar clave del registro...
01-08 16:08 DEBUG TaskList: ## Finished Borrar clave del registro
01-08 16:08 DEBUG TaskList: # Finished tasklist
01-08 16:08 INFO root: Almost finished uninstalling
01-08 16:08 INFO root: Finished uninstallation
01-08 16:08 DEBUG CommonBackend: Fetching basic info...
01-08 16:08 DEBUG CommonBackend: original_exe=D:\wubi.exe
01-08 16:08 DEBUG CommonBackend: platform=win32
01-08 16:08 DEBUG CommonBackend: osname=nt
01-08 16:08 DEBUG WindowsBackend: arch=i386
01-08 16:08 DEBUG CommonBackend: Parsing isolist=C:\DOCUME~1\vicente\CONFIG~1\Temp\pyl5.tmp\data\isolist.ini
01-08 16:08 DEBUG CommonBackend: Adding distro Xubuntu-i386
01-08 16:08 DEBUG CommonBackend: Adding distro Xubuntu-amd64
01-08 16:08 DEBUG CommonBackend: Adding distro Kubuntu-amd64
01-08 16:08 DEBUG CommonBackend: Adding distro Mythbuntu-i386
01-08 16:08 DEBUG CommonBackend: Adding distro Ubuntu-amd64
01-08 16:08 DEBUG CommonBackend: Adding distro Ubuntu-i386
01-08 16:08 DEBUG CommonBackend: Adding distro Mythbuntu-amd64
01-08 16:08 DEBUG CommonBackend: Adding distro Kubuntu-i386
01-08 16:08 DEBUG CommonBackend: Adding distro KubuntuNetbook-i386
01-08 16:08 DEBUG CommonBackend: Adding distro UbuntuNetbook-i386
01-08 16:08 DEBUG WindowsBackend: Fetching host info...
01-08 16:08 DEBUG WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
01-08 16:08 DEBUG WindowsBackend: windows version=xp
01-08 16:08 DEBUG WindowsBackend: windows_version2=Microsoft Windows XP
01-08 16:08 DEBUG WindowsBackend: windows_sp=Service Pack 3
01-08 16:08 DEBUG WindowsBackend: windows_build=2600
01-08 16:08 DEBUG WindowsBackend: gmt=-5
01-08 16:08 DEBUG WindowsBackend: country=ES
01-08 16:08 DEBUG WindowsBackend: timezone=Europe/Madrid
01-08 16:08 DEBUG WindowsBackend: windows_username=vicente
01-08 16:08 DEBUG WindowsBackend: user_full_name=vicente
01-08 16:08 DEBUG WindowsBackend: user_directory=C:\Documents and Settings\vicente
01-08 16:08 DEBUG WindowsBackend: windows_language_code=1034
01-08 16:08 DEBUG WindowsBackend: windows_language=Spanish
01-08 16:08 DEBUG WindowsBackend: processor_name= Intel(R) Pentium(R) M processor 1.50GHz
01-08 16:08 DEBUG WindowsBackend: bootloader=xp
01-08 16:08 DEBUG WindowsBackend: system_drive=Drive(C: hd 24003.421875 mb free ntfs)
01-08 16:08 DEBUG WindowsBackend: drive=Drive(C: hd 24003.421875 mb free ntfs)
01-08 16:08 DEBUG WindowsBackend: drive=Drive(D: cd 0.0 mb free cdfs)
01-08 16:08 DEBUG WindowsBackend: uninstaller_path=None
01-08 16:08 DEBUG WindowsBackend: previous_target_dir=None
01-08 16:08 DEBUG WindowsBackend: previous_distro_name=None
01-08 16:08 DEBUG WindowsBackend: keyboard_id=67765258
01-08 16:08 DEBUG WindowsBackend: keyboard_layout=es
01-08 16:08 DEBUG WindowsBackend: keyboard_variant=
01-08 16:08 DEBUG WindowsBackend: total_memory_mb=511.2265625
01-08 16:08 DEBUG CommonBackend: Searching ISOs on USB devices
01-08 16:08 DEBUG CommonBackend: Searching for local CDs
01-08 16:08 DEBUG Distro: checking whether C:\DOCUME~1\vicente\CONFIG~1\Temp\pyl5.tmp is a valid Ubuntu CD
01-08 16:08 DEBUG Distro: does not contain C:\DOCUME~1\vicente\CONFIG~1\Temp\pyl5.tmp\casper\filesystem.squashfs
01-08 16:08 DEBUG Distro: checking whether C:\DOCUME~1\vicente\CONFIG~1\Temp\pyl5.tmp is a valid Ubuntu CD
01-08 16:08 DEBUG Distro: does not contain C:\DOCUME~1\vicente\CONFIG~1\Temp\pyl5.tmp\casper\filesystem.squashfs
01-08 16:08 DEBUG Distro: checking whether C:\DOCUME~1\vicente\CONFIG~1\Temp\pyl5.tmp is a valid Ubuntu Netbook CD
01-08 16:08 DEBUG Distro: does not contain C:\DOCUME~1\vicente\CONFIG~1\Temp\pyl5.tmp\casper\filesystem.squashfs
01-08 16:08 DEBUG Distro: checking whether C:\DOCUME~1\vicente\CONFIG~1\Temp\pyl5.tmp is a valid Kubuntu CD
01-08 16:08 DEBUG Distro: does not contain C:\DOCUME~1\vicente\CONFIG~1\Temp\pyl5.tmp\casper\filesystem.squashfs
01-08 16:08 DEBUG Distro: checking whether C:\DOCUME~1\vicente\CONFIG~1\Temp\pyl5.tmp is a valid Kubuntu CD
01-08 16:08 DEBUG Distro: does not contain C:\DOCUME~1\vicente\CONFIG~1\Temp\pyl5.tmp\casper\filesystem.squashfs
01-08 16:08 DEBUG Distro: checking whether C:\DOCUME~1\vicente\CONFIG~1\Temp\pyl5.tmp is a valid Kubuntu Netbook CD
01-08 16:08 DEBUG Distro: does not contain C:\DOCUME~1\vicente\CONFIG~1\Temp\pyl5.tmp\casper\filesystem.squashfs
01-08 16:08 DEBUG Distro: checking whether C:\DOCUME~1\vicente\CONFIG~1\Temp\pyl5.tmp is a valid Xubuntu CD
01-08 16:08 DEBUG Distro: does not contain C:\DOCUME~1\vicente\CONFIG~1\Temp\pyl5.tmp\casper\filesystem.squashfs
01-08 16:08 DEBUG Distro: checking whether C:\DOCUME~1\vicente\CONFIG~1\Temp\pyl5.tmp is a valid Xubuntu CD
01-08 16:08 DEBUG Distro: does not contain C:\DOCUME~1\vicente\CONFIG~1\Temp\pyl5.tmp\casper\filesystem.squashfs
01-08 16:08 DEBUG Distro: checking whether C:\DOCUME~1\vicente\CONFIG~1\Temp\pyl5.tmp is a valid Mythbuntu CD
01-08 16:08 DEBUG Distro: does not contain C:\DOCUME~1\vicente\CONFIG~1\Temp\pyl5.tmp\casper\filesystem.squashfs
01-08 16:08 DEBUG Distro: checking whether C:\DOCUME~1\vicente\CONFIG~1\Temp\pyl5.tmp is a valid Mythbuntu CD
01-08 16:08 DEBUG Distro: does not contain C:\DOCUME~1\vicente\CONFIG~1\Temp\pyl5.tmp\casper\filesystem.squashfs
01-08 16:08 DEBUG Distro: checking whether D:\ is a valid Ubuntu CD
01-08 16:08 DEBUG Distro: wrong arch: i386 != amd64
01-08 16:08 DEBUG Distro: checking whether D:\ is a valid Ubuntu CD
01-08 16:08 INFO Distro: Found a valid CD for Ubuntu: D:\
01-08 16:08 INFO root: Running the CD boot helper...
01-08 16:08 INFO WinuiPage: appname=wubi, localedir=C:\DOCUME~1\vicente\CONFIG~1\Temp\pyl5.tmp\translations, languages=['es_ES', 'es']
01-08 16:08 INFO WinuiPage: appname=wubi, localedir=C:\DOCUME~1\vicente\CONFIG~1\Temp\pyl5.tmp\translations, languages=['es_ES', 'es']
01-08 16:08 INFO root: CD boot helper confirmed
01-08 16:08 INFO WinuiPage: appname=wubi, localedir=C:\DOCUME~1\vicente\CONFIG~1\Temp\pyl5.tmp\translations, languages=['es_ES', 'es']
01-08 16:08 DEBUG TaskList: # Running tasklist...
01-08 16:08 DEBUG TaskList: ## Running select_target_dir...
01-08 16:08 INFO WindowsBackend: Installing into C:\ubuntu
01-08 16:08 DEBUG TaskList: ## Finished select_target_dir
01-08 16:08 DEBUG TaskList: ## Running create_dir_structure...
01-08 16:08 DEBUG CommonBackend: Creating dir C:\ubuntu
01-08 16:08 DEBUG CommonBackend: Creating dir C:\ubuntu\disks
01-08 16:08 DEBUG CommonBackend: Creating dir C:\ubuntu\install
01-08 16:08 DEBUG CommonBackend: Creating dir C:\ubuntu\install\boot
01-08 16:08 DEBUG CommonBackend: Creating dir C:\ubuntu\disks\boot
01-08 16:08 DEBUG CommonBackend: Creating dir C:\ubuntu\disks\boot\grub
01-08 16:08 DEBUG CommonBackend: Creating dir C:\ubuntu\install\boot\grub
01-08 16:08 DEBUG TaskList: ## Finished create_dir_structure
01-08 16:08 DEBUG TaskList: ## Running uncompress_target_dir...
01-08 16:08 DEBUG TaskList: ## Finished uncompress_target_dir
01-08 16:08 DEBUG TaskList: ## Running create_uninstaller...
01-08 16:08 DEBUG WindowsBackend: Copying uninstaller D:\wubi.exe -> C:\ubuntu\uninstall-wubi.exe
01-08 16:08 DEBUG registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString C:\ubuntu\uninstall-wubi.exe
01-08 16:08 DEBUG registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir C:\ubuntu
01-08 16:08 DEBUG registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
01-08 16:08 DEBUG registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon C:\ubuntu\Ubuntu.ico
01-08 16:08 DEBUG registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 10.04-rev189
01-08 16:08 DEBUG registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
01-08 16:08 DEBUG registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com](http://www.ubuntu.com)
01-08 16:08 DEBUG registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
01-08 16:08 DEBUG TaskList: ## Finished create_uninstaller
01-08 16:08 DEBUG TaskList: ## Running copy_installation_files...
01-08 16:08 DEBUG WindowsBackend: Copying C:\DOCUME~1\vicente\CONFIG~1\Temp\pyl5.tmp\data\custom-installation -> C:\ubuntu\install\custom-installation
01-08 16:08 DEBUG WindowsBackend: Copying C:\DOCUME~1\vicente\CONFIG~1\Temp\pyl5.tmp\winboot -> C:\ubuntu\winboot
01-08 16:08 DEBUG WindowsBackend: Copying C:\DOCUME~1\vicente\CONFIG~1\Temp\pyl5.tmp\data\images\Ubuntu.ico -> C:\ubuntu\Ubuntu.ico
01-08 16:08 DEBUG TaskList: ## Finished copy_installation_files
01-08 16:08 DEBUG TaskList: ## Running use_cd...
01-08 16:08 DEBUG TaskList: New task copy_file
01-08 16:08 DEBUG TaskList: ### Running copy_file...
01-08 16:28 ERROR TaskList: [Errno 13] Permission denied
Traceback (most recent call last):
File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
File "\lib\wubi\backends\common\utils.py", line 209, in copy_file
IOError: [Errno 13] Permission denied
01-08 16:28 DEBUG TaskList: # Cancelling tasklist
01-08 16:28 ERROR root: [Errno 13] Permission denied
Traceback (most recent call last):
File "\lib\wubi\application.py", line 56, in run
File "\lib\wubi\application.py", line 128, in select_task
File "\lib\wubi\application.py", line 194, in run_cd_menu
File "\lib\wubi\application.py", line 120, in select_task
File "\lib\wubi\application.py", line 217, in run_cd_boot
File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
File "\lib\wubi\backends\common\utils.py", line 209, in copy_file
IOError: [Errno 13] Permission denied
01-08 16:28 DEBUG TaskList: New task check_iso
01-08 16:28 DEBUG TaskList: ## Finished use_cd
01-08 16:28 DEBUG TaskList: # Finished tasklist
01-08 16:48 INFO root: === wubi 10.04 rev189 ===
01-08 16:48 DEBUG root: Logfile is c:\docume~1\vicente\config~1\temp\wubi-10.04-rev189.log
01-08 16:48 DEBUG root: sys.argv = ['main.pyo', '--exefile="D:\\wubi.exe"', '--cdmenu']
01-08 16:48 DEBUG CommonBackend: data_dir=C:\DOCUME~1\vicente\CONFIG~1\Temp\pyl8.tmp\data
01-08 16:48 DEBUG WindowsBackend: 7z=C:\DOCUME~1\vicente\CONFIG~1\Temp\pyl8.tmp\bin\7z.exe
01-08 16:48 DEBUG CommonBackend: Fetching basic info...
01-08 16:48 DEBUG CommonBackend: original_exe=D:\wubi.exe
01-08 16:48 DEBUG CommonBackend: platform=win32
01-08 16:48 DEBUG CommonBackend: osname=nt
01-08 16:48 DEBUG CommonBackend: language=es_ES
01-08 16:48 DEBUG CommonBackend: encoding=cp1252
01-08 16:48 INFO root: === wubi 10.04 rev189 ===
01-08 16:48 DEBUG root: Logfile is c:\docume~1\vicente\config~1\temp\wubi-10.04-rev189.log
01-08 16:48 DEBUG root: sys.argv = ['main.pyo', '--exefile="C:\\ubuntu\\uninstall-wubi.exe"', '--uninstall']
01-08 16:48 DEBUG CommonBackend: data_dir=C:\DOCUME~1\vicente\CONFIG~1\Temp\pyl7.tmp\data
01-08 16:48 DEBUG WindowsBackend: 7z=C:\DOCUME~1\vicente\CONFIG~1\Temp\pyl7.tmp\bin\7z.exe
01-08 16:48 DEBUG CommonBackend: Fetching basic info...
01-08 16:48 DEBUG CommonBackend: original_exe=C:\ubuntu\uninstall-wubi.exe
01-08 16:48 DEBUG CommonBackend: platform=win32
01-08 16:48 DEBUG CommonBackend: osname=nt
01-08 16:48 DEBUG CommonBackend: language=es_ES
01-08 16:48 DEBUG CommonBackend: encoding=cp1252
01-08 16:48 DEBUG WindowsBackend: arch=i386
01-08 16:48 DEBUG CommonBackend: Parsing isolist=C:\DOCUME~1\vicente\CONFIG~1\Temp\pyl8.tmp\data\isolist.ini
01-08 16:48 DEBUG WindowsBackend: arch=i386
01-08 16:48 DEBUG CommonBackend: Parsing isolist=C:\DOCUME~1\vicente\CONFIG~1\Temp\pyl7.tmp\data\isolist.ini
ro Xubuntu-amd64
01-08 16:48 DEBUG CommonBackend: Adding distro Kubuntu-amd64
01-08 16:48 DEBUG CommonBackend: Adding distro Mythbuntu-i386
01-08 16:48 DEBUG CommonBackend: Adding distro Ubuntu-amd64
01-08 16:48 DEBUG CommonBackend: Adding distro Ubuntu-i386
01-08 16:48 DEBUG CommonBackend: Adding distro Mythbuntu-amd64
01-08 16:48 DEBUG CommonBackend: Adding distro Kubuntu-i386
01-08 16:48 DEBUG CommonBackend: Adding distro KubuntuNetbook-i386
01-08 16:48 DEBUG CommonBackend: Adding distro UbuntuNetbook-i386
16:48 DEBUG CommonBackend: Adding distro Xubuntu-amd64
01-08 16:48 DEBUG CommonBackend: Adding distro Kubuntu-amd64
01-08 16:48 DEBUG CommonBackend: Adding distro Mythbuntu-i386
01-08 16:48 DEBUG CommonBackend: Adding distro Ubuntu-amd64
01-08 16:48 DEBUG CommonBackend: Adding distro Ubuntu-i386
01-08 16:48 DEBUG CommonBackend: Adding distro Mythbuntu-amd64
01-08 16:48 DEBUG CommonBackend: Adding distro Kubuntu-i386
01-08 16:48 DEBUG CommonBackend: Adding distro KubuntuNetbook-i386
01-08 16:48 DEBUG CommonBackend: Adding distro UbuntuNetbook-i386
01-08 16:48 DEBUG WindowsBackend: Fetching host info...
01-08 16:48 DEBUG WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
01-08 16:48 DEBUG WindowsBackend: windows version=xp
01-08 16:48 DEBUG WindowsBackend: windows_version2=Microsoft Windows XP
01-08 16:48 DEBUG WindowsBackend: windows_sp=Service Pack 3
01-08 16:48 DEBUG WindowsBackend: windows_build=2600
01-08 16:48 DEBUG WindowsBackend: gmt=-5
01-08 16:48 DEBUG WindowsBackend: country=ES
01-08 16:48 DEBUG WindowsBackend: timezone=Europe/Madrid
01-08 16:48 DEBUG WindowsBackend: Fetching host info...
01-08 16:48 DEBUG WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
01-08 16:48 DEBUG WindowsBackend: windows version=xp
01-08 16:48 DEBUG WindowsBackend: windows_version2=Microsoft Windows XP
01-08 16:48 DEBUG WindowsBackend: windows_sp=Service Pack 3
01-08 16:48 DEBUG WindowsBackend: windows_build=2600
01-08 16:48 DEBUG WindowsBackend: gmt=-5
01-08 16:48 DEBUG WindowsBackend: country=ES
01-08 16:48 DEBUG WindowsBackend: timezone=Europe/Madrid
01-08 16:48 DEBUG WindowsBackend: windows_username=vicente
01-08 16:48 DEBUG WindowsBackend: user_full_name=vicente
01-08 16:48 DEBUG WindowsBackend: user_directory=C:\Documents and Settings\vicente
01-08 16:48 DEBUG WindowsBackend: windows_language_code=1034
01-08 16:48 DEBUG WindowsBackend: windows_language=Spanish
01-08 16:48 DEBUG WindowsBackend: processor_name= Intel(R) Pentium(R) M processor 1.50GHz
01-08 16:48 DEBUG WindowsBackend: bootloader=xp
01-08 16:48 DEBUG WindowsBackend: windows_username=vicente
01-08 16:48 DEBUG WindowsBackend: user_full_name=vicente
01-08 16:48 DEBUG WindowsBackend: user_directory=C:\Documents and Settings\vicente
01-08 16:48 DEBUG WindowsBackend: windows_language_code=1034
01-08 16:48 DEBUG WindowsBackend: windows_language=Spanish
01-08 16:48 DEBUG WindowsBackend: processor_name= Intel(R) Pentium(R) M processor 1.50GHz
01-08 16:48 DEBUG WindowsBackend: bootloader=xp
01-08 16:48 DEBUG WindowsBackend: system_drive=Drive(C: hd 23352.4453125 mb free ntfs)
01-08 16:48 DEBUG WindowsBackend: system_drive=Drive(C: hd 23352.4453125 mb free ntfs)
01-08 16:48 DEBUG WindowsBackend: drive=Drive(C: hd 23352.4453125 mb free ntfs)
01-08 16:48 DEBUG WindowsBackend: drive=Drive(C: hd 23352.4453125 mb free ntfs)
01-08 16:48 DEBUG WindowsBackend: drive=Drive(D: cd 0.0 mb free cdfs)
01-08 16:48 DEBUG WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
01-08 16:48 DEBUG WindowsBackend: previous_target_dir=C:\ubuntu
01-08 16:48 DEBUG WindowsBackend: previous_distro_name=Ubuntu
01-08 16:48 DEBUG WindowsBackend: keyboard_id=67765258
01-08 16:48 DEBUG WindowsBackend: keyboard_layout=es
01-08 16:48 DEBUG WindowsBackend: keyboard_variant=
01-08 16:48 DEBUG CommonBackend: python locale=('es_ES', 'cp1252')
01-08 16:48 DEBUG CommonBackend: locale=es_ES.UTF-8
01-08 16:48 DEBUG WindowsBackend: total_memory_mb=511.2265625
01-08 16:48 DEBUG CommonBackend: Searching ISOs on USB devices
01-08 16:48 DEBUG WindowsBackend: drive=Drive(D: cd 0.0 mb free cdfs)
01-08 16:48 DEBUG WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
01-08 16:48 DEBUG WindowsBackend: previous_target_dir=C:\ubuntu
01-08 16:48 DEBUG WindowsBackend: previous_distro_name=Ubuntu
01-08 16:48 DEBUG WindowsBackend: keyboard_id=67765258
01-08 16:48 DEBUG WindowsBackend: keyboard_layout=es
01-08 16:48 DEBUG WindowsBackend: keyboard_variant=
01-08 16:48 DEBUG CommonBackend: python locale=('es_ES', 'cp1252')
01-08 16:48 DEBUG CommonBackend: locale=es_ES.UTF-8
01-08 16:48 DEBUG WindowsBackend: total_memory_mb=511.2265625
01-08 16:48 DEBUG CommonBackend: Searching ISOs on USB devices
01-08 16:48 DEBUG CommonBackend: Searching for local CDs
01-08 16:48 DEBUG Distro: checking whether C:\DOCUME~1\vicente\CONFIG~1\Temp\pyl8.tmp is a valid Ubuntu CD
01-08 16:48 DEBUG CommonBackend: Searching for local CDs
01-08 16:48 DEBUG Distro: checking whether C:\DOCUME~1\vicente\CONFIG~1\Temp\pyl7.tmp is a valid Ubuntu CD
01-08 16:48 DEBUG Distro: does not contain C:\DOCUME~1\vicente\CONFIG~1\Temp\pyl8.tmp\casper\filesystem.squashfs
01-08 16:48 DEBUG Distro: checking whether C:\DOCUME~1\vicente\CONFIG~1\Temp\pyl8.tmp is a valid Ubuntu CD
01-08 16:48 DEBUG Distro: does not contain C:\DOCUME~1\vicente\CONFIG~1\Temp\pyl7.tmp\casper\filesystem.squashfs
01-08 16:48 DEBUG Distro: checking whether C:\DOCUME~1\vicente\CONFIG~1\Temp\pyl7.tmp is a valid Ubuntu CD
01-08 16:48 DEBUG Distro: does not contain C:\DOCUME~1\vicente\CONFIG~1\Temp\pyl8.tmp\casper\filesystem.squashfs
01-08 16:48 DEBUG Distro: checking whether C:\DOCUME~1\vicente\CONFIG~1\Temp\pyl8.tmp is a valid Ubuntu Netbook CD
01-08 16:48 DEBUG Distro: does not contain C:\DOCUME~1\vicente\CONFIG~1\Temp\pyl7.tmp\casper\filesystem.squashfs
01-08 16:48 DEBUG Distro: checking whether C:\DOCUME~1\vicente\CONFIG~1\Temp\pyl7.tmp is a valid Ubuntu Netbook CD
01-08 16:48 DEBUG Distro: does not contain C:\DOCUME~1\vicente\CONFIG~1\Temp\pyl8.tmp\casper\filesystem.squashfs
01-08 16:48 DEBUG Distro: checking whether C:\DOCUME~1\vicente\CONFIG~1\Temp\pyl8.tmp is a valid Kubuntu CD
01-08 16:48 DEBUG Distro: does not contain C:\DOCUME~1\vicente\CONFIG~1\Temp\pyl7.tmp\casper\filesystem.squashfs
01-08 16:48 DEBUG Distro: checking whether C:\DOCUME~1\vicente\CONFIG~1\Temp\pyl7.tmp is a valid Kubuntu CD
ashfs
01-08 16:48 DEBUG Distro: checking whether C:\DOCUME~1\vicente\CONFIG~1\Temp\pyl8.tmp is a valid Kubuntu CD
01-08 16:48 DEBUG Distro: does not contain C:\DOCUME~1\vicente\CONFIG~1\Temp\pyl7.tmp\casper\filesystem.squashfs
01-08 16:48 DEBUG Distro: checking whether C:\DOCUME~1\vicente\CONFIG~1\Temp\pyl7.tmp is a valid Kubuntu CD
01-08 16:48 DEBUG Distro: does not contain C:\DOCUME~1\vicente\CONFIG~1\Temp\pyl8.tmp\casper\filesystem.squashfs
01-08 16:48 DEBUG Distro: checking whether C:\DOCUME~1\vicente\CONFIG~1\Temp\pyl8.tmp is a valid Kubuntu Netbook CD
01-08 16:48 DEBUG Distro: does not contain C:\DOCUME~1\vicente\CONFIG~1\Temp\pyl7.tmp\casper\filesystem.squashfs
01-08 16:48 DEBUG Distro: checking whether C:\DOCUME~1\vicente\CONFIG~1\Temp\pyl7.tmp is a valid Kubuntu Netbook CD
01-08 16:48 DEBUG Distro: does not contain C:\DOCUME~1\vicente\CONFIG~1\Temp\pyl8.tmp\casper\filesystem.squashfs
01-08 16:48 DEBUG Distro: checking whether C:\DOCUME~1\vicente\CONFIG~1\Temp\pyl8.tmp is a valid Xubuntu CD
01-08 16:48 DEBUG Distro: does not contain C:\DOCUME~1\vicente\CONFIG~1\Temp\pyl8.tmp\casper\filesystem.squashfs
01-08 16:48 DEBUG Distro: checking whether C:\DOCUME~1\vicente\CONFIG~1\Temp\pyl8.tmp is a valid Xubuntu CD
01-08 16:48 DEBUG Distro: does not contain C:\DOCUME~1\vicente\CONFIG~1\Temp\pyl7.tmp\casper\filesystem.squashfs
01-08 16:48 DEBUG Distro: checking whether C:\DOCUME~1\vicente\CONFIG~1\Temp\pyl7.tmp is a valid Xubuntu CD
01-08 16:48 DEBUG Distro: does not contain C:\DOCUME~1\vicente\CONFIG~1\Temp\pyl8.tmp\casper\filesystem.squashfs
01-08 16:48 DEBUG Distro: checking whether C:\DOCUME~1\vicente\CONFIG~1\Temp\pyl8.tmp is a valid Mythbuntu CD
01-08 16:48 DEBUG Distro: does not contain C:\DOCUME~1\vicente\CONFIG~1\Temp\pyl7.tmp\casper\filesystem.squashfs
01-08 16:48 DEBUG Distro: checking whether C:\DOCUME~1\vicente\CONFIG~1\Temp\pyl7.tmp is a valid Xubuntu CD
01-08 16:48 DEBUG Distro: does not contain C:\DOCUME~1\vicente\CONFIG~1\Temp\pyl7.tmp\casper\filesystem.squashfs
01-08 16:48 DEBUG Distro: checking whether C:\DOCUME~1\vicente\CONFIG~1\Temp\pyl7.tmp is a valid Mythbuntu CD
01-08 16:48 DEBUG Distro: does not contain C:\DOCUME~1\vicente\CONFIG~1\Temp\pyl8.tmp\casper\filesystem.squashfs
01-08 16:48 DEBUG Distro: checking whether C:\DOCUME~1\vicente\CONFIG~1\Temp\pyl8.tmp is a valid Mythbuntu CD
01-08 16:48 DEBUG Distro: does not contain C:\DOCUME~1\vicente\CONFIG~1\Temp\pyl8.tmp\casper\filesystem.squashfs
01-08 16:48 DEBUG Distro: does not contain C:\DOCUME~1\vicente\CONFIG~1\Temp\pyl7.tmp\casper\filesystem.squashfs
01-08 16:48 DEBUG Distro: checking whether D:\ is a valid Ubuntu CD
01-08 16:48 DEBUG Distro: checking whether C:\DOCUME~1\vicente\CONFIG~1\Temp\pyl7.tmp is a valid Mythbuntu CD
01-08 16:48 DEBUG Distro: does not contain C:\DOCUME~1\vicente\CONFIG~1\Temp\pyl7.tmp\casper\filesystem.squashfs
01-08 16:48 DEBUG Distro: checking whether D:\ is a valid Ubuntu CD
01-08 16:48 DEBUG Distro: parsing info from str=Ubuntu 10.04 LTS "Lucid Lynx" - Release i386 (20100429)
01-08 16:48 DEBUG Distro: parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '10.04', 'build': '20100429', 'codename': 'Lucid Lynx', 'arch': 'i386'}
01-08 16:48 DEBUG Distro: wrong arch: i386 != amd64
01-08 16:48 DEBUG Distro: checking whether D:\ is a valid Ubuntu CD
01-08 16:48 INFO Distro: Found a valid CD for Ubuntu: D:\
01-08 16:48 INFO root: Running the CD menu...
01-08 16:48 DEBUG WindowsFrontend: __init__...
01-08 16:48 DEBUG Distro: parsing info from str=Ubuntu 10.04 LTS "Lucid Lynx" - Release i386 (20100429)
01-08 16:48 DEBUG Distro: parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '10.04', 'build': '20100429', 'codename': 'Lucid Lynx', 'arch': 'i386'}
01-08 16:48 DEBUG Distro: wrong arch: i386 != amd64
01-08 16:48 DEBUG Distro: checking whether D:\ is a valid Ubuntu CD
01-08 16:48 INFO Distro: Found a valid CD for Ubuntu: D:\
01-08 16:48 INFO root: Running the uninstaller...
01-08 16:48 INFO CommonBackend: This is the uninstaller running
01-08 16:48 DEBUG WindowsFrontend: __init__...
01-08 16:48 DEBUG WindowsFrontend: on_init...
01-08 16:48 DEBUG WindowsFrontend: on_init...
01-08 16:48 INFO WinuiPage: appname=wubi, localedir=C:\DOCUME~1\vicente\CONFIG~1\Temp\pyl7.tmp\translations, languages=['es_ES', 'es']
01-08 16:48 INFO WinuiPage: appname=wubi, localedir=C:\DOCUME~1\vicente\CONFIG~1\Temp\pyl8.tmp\translations, languages=['es_ES', 'es']
01-08 16:48 INFO WinuiPage: appname=wubi, localedir=C:\DOCUME~1\vicente\CONFIG~1\Temp\pyl8.tmp\translations, languages=['es_ES', 'es']
01-08 16:48 INFO WindowsFrontend: Operation cancelled
01-08 16:48 DEBUG WindowsFrontend: frontend.quit
01-08 16:48 DEBUG WindowsFrontend: frontend.on_quit
01-08 16:48 DEBUG root: application.on_quit
01-08 16:48 INFO root: sys.exit
01-08 16:48 INFO WindowsFrontend: Operation cancelled
01-08 16:48 DEBUG WindowsFrontend: frontend.quit
01-08 16:48 DEBUG WindowsFrontend: frontend.on_quit
01-08 16:48 DEBUG root: application.on_quit
01-08 16:48 INFO root: sys.exit
01-08 16:52 INFO root: === wubi 10.04 rev189 ===
01-08 16:52 DEBUG root: Logfile is c:\docume~1\vicente\config~1\temp\wubi-10.04-rev189.log
01-08 16:52 DEBUG root: sys.argv = ['main.pyo', '--exefile="C:\\ubuntu\\uninstall-wubi.exe"', '--uninstall']
01-08 16:52 DEBUG CommonBackend: data_dir=C:\DOCUME~1\vicente\CONFIG~1\Temp\pylA.tmp\data
01-08 16:52 DEBUG WindowsBackend: 7z=C:\DOCUME~1\vicente\CONFIG~1\Temp\pylA.tmp\bin\7z.exe
01-08 16:52 DEBUG CommonBackend: Fetching basic info...
01-08 16:52 DEBUG CommonBackend: original_exe=C:\ubuntu\uninstall-wubi.exe
01-08 16:52 DEBUG CommonBackend: platform=win32
01-08 16:52 DEBUG CommonBackend: osname=nt
01-08 16:52 DEBUG CommonBackend: language=es_ES
01-08 16:52 DEBUG CommonBackend: encoding=cp1252
01-08 16:52 DEBUG WindowsBackend: arch=i386
01-08 16:52 DEBUG CommonBackend: Parsing isolist=C:\DOCUME~1\vicente\CONFIG~1\Temp\pylA.tmp\data\isolist.ini
01-08 16:52 DEBUG CommonBackend: Adding distro Xubuntu-i386
01-08 16:52 DEBUG CommonBackend: Adding distro Xubuntu-amd64
01-08 16:52 DEBUG CommonBackend: Adding distro Kubuntu-amd64
01-08 16:52 DEBUG CommonBackend: Adding distro Mythbuntu-i386
01-08 16:52 DEBUG CommonBackend: Adding distro Ubuntu-amd64
01-08 16:52 DEBUG CommonBackend: Adding distro Ubuntu-i386
01-08 16:52 DEBUG CommonBackend: Adding distro Mythbuntu-amd64
01-08 16:52 DEBUG CommonBackend: Adding distro Kubuntu-i386
01-08 16:52 DEBUG CommonBackend: Adding distro KubuntuNetbook-i386
01-08 16:52 DEBUG CommonBackend: Adding distro UbuntuNetbook-i386
01-08 16:52 DEBUG WindowsBackend: Fetching host info...
01-08 16:52 DEBUG WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
01-08 16:52 DEBUG WindowsBackend: windows version=xp
01-08 16:52 DEBUG WindowsBackend: windows_version2=Microsoft Windows XP
01-08 16:52 DEBUG WindowsBackend: windows_sp=Service Pack 3
01-08 16:52 DEBUG WindowsBackend: windows_build=2600
01-08 16:52 DEBUG WindowsBackend: gmt=-5
01-08 16:52 DEBUG WindowsBackend: country=ES
01-08 16:52 DEBUG WindowsBackend: timezone=Europe/Madrid
01-08 16:52 DEBUG WindowsBackend: windows_username=vicente
01-08 16:52 DEBUG WindowsBackend: user_full_name=vicente
01-08 16:52 DEBUG WindowsBackend: user_directory=C:\Documents and Settings\vicente
01-08 16:52 DEBUG WindowsBackend: windows_language_code=1034
01-08 16:52 DEBUG WindowsBackend: windows_language=Spanish
01-08 16:52 DEBUG WindowsBackend: processor_name= Intel(R) Pentium(R) M processor 1.50GHz
01-08 16:52 DEBUG WindowsBackend: bootloader=xp
01-08 16:52 DEBUG WindowsBackend: system_drive=Drive(C: hd 23355.5195313 mb free ntfs)
01-08 16:52 DEBUG WindowsBackend: drive=Drive(C: hd 23355.5195313 mb free ntfs)
01-08 16:52 DEBUG WindowsBackend: drive=Drive(D: cd 0.0 mb free )
01-08 16:52 DEBUG WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
01-08 16:52 DEBUG WindowsBackend: previous_target_dir=C:\ubuntu
01-08 16:52 DEBUG WindowsBackend: previous_distro_name=Ubuntu
01-08 16:52 DEBUG WindowsBackend: keyboard_id=67765258
01-08 16:52 DEBUG WindowsBackend: keyboard_layout=es
01-08 16:52 DEBUG WindowsBackend: keyboard_variant=
01-08 16:52 DEBUG CommonBackend: python locale=('es_ES', 'cp1252')
01-08 16:52 DEBUG CommonBackend: locale=es_ES.UTF-8
01-08 16:52 DEBUG WindowsBackend: total_memory_mb=511.2265625
01-08 16:52 DEBUG CommonBackend: Searching ISOs on USB devices
01-08 16:52 DEBUG CommonBackend: Searching for local CDs
01-08 16:52 DEBUG Distro: checking whether C:\DOCUME~1\vicente\CONFIG~1\Temp\pylA.tmp is a valid Ubuntu CD
01-08 16:52 DEBUG Distro: does not contain C:\DOCUME~1\vicente\CONFIG~1\Temp\pylA.tmp\casper\filesystem.squashfs
01-08 16:52 DEBUG Distro: checking whether C:\DOCUME~1\vicente\CONFIG~1\Temp\pylA.tmp is a valid Ubuntu CD
01-08 16:52 DEBUG Distro: does not contain C:\DOCUME~1\vicente\CONFIG~1\Temp\pylA.tmp\casper\filesystem.squashfs
01-08 16:52 DEBUG Distro: checking whether C:\DOCUME~1\vicente\CONFIG~1\Temp\pylA.tmp is a valid Ubuntu Netbook CD
01-08 16:52 DEBUG Distro: does not contain C:\DOCUME~1\vicente\CONFIG~1\Temp\pylA.tmp\casper\filesystem.squashfs
01-08 16:52 DEBUG Distro: checking whether C:\DOCUME~1\vicente\CONFIG~1\Temp\pylA.tmp is a valid Kubuntu CD
01-08 16:52 DEBUG Distro: does not contain C:\DOCUME~1\vicente\CONFIG~1\Temp\pylA.tmp\casper\filesystem.squashfs
01-08 16:52 DEBUG Distro: checking whether C:\DOCUME~1\vicente\CONFIG~1\Temp\pylA.tmp is a valid Kubuntu CD
01-08 16:52 DEBUG Distro: does not contain C:\DOCUME~1\vicente\CONFIG~1\Temp\pylA.tmp\casper\filesystem.squashfs
01-08 16:52 DEBUG Distro: checking whether C:\DOCUME~1\vicente\CONFIG~1\Temp\pylA.tmp is a valid Kubuntu Netbook CD
01-08 16:52 DEBUG Distro: does not contain C:\DOCUME~1\vicente\CONFIG~1\Temp\pylA.tmp\casper\filesystem.squashfs
01-08 16:52 DEBUG Distro: checking whether C:\DOCUME~1\vicente\CONFIG~1\Temp\pylA.tmp is a valid Xubuntu CD
01-08 16:52 DEBUG Distro: does not contain C:\DOCUME~1\vicente\CONFIG~1\Temp\pylA.tmp\casper\filesystem.squashfs
01-08 16:52 DEBUG Distro: checking whether C:\DOCUME~1\vicente\CONFIG~1\Temp\pylA.tmp is a valid Xubuntu CD
01-08 16:52 DEBUG Distro: does not contain C:\DOCUME~1\vicente\CONFIG~1\Temp\pylA.tmp\casper\filesystem.squashfs
01-08 16:52 DEBUG Distro: checking whether C:\DOCUME~1\vicente\CONFIG~1\Temp\pylA.tmp is a valid Mythbuntu CD
01-08 16:52 DEBUG Distro: does not contain C:\DOCUME~1\vicente\CONFIG~1\Temp\pylA.tmp\casper\filesystem.squashfs
01-08 16:52 DEBUG Distro: checking whether C:\DOCUME~1\vicente\CONFIG~1\Temp\pylA.tmp is a valid Mythbuntu CD
01-08 16:52 DEBUG Distro: does not contain C:\DOCUME~1\vicente\CONFIG~1\Temp\pylA.tmp\casper\filesystem.squashfs
01-08 16:52 DEBUG Distro: checking whether D:\ is a valid Ubuntu CD
01-08 16:52 DEBUG Distro: does not contain D:\casper\filesystem.squashfs
01-08 16:52 DEBUG Distro: checking whether D:\ is a valid Ubuntu CD
01-08 16:52 DEBUG Distro: does not contain D:\casper\filesystem.squashfs
01-08 16:52 DEBUG Distro: checking whether D:\ is a valid Ubuntu Netbook CD
01-08 16:52 DEBUG Distro: does not contain D:\casper\filesystem.squashfs
01-08 16:52 DEBUG Distro: checking whether D:\ is a valid Kubuntu CD
01-08 16:52 DEBUG Distro: does not contain D:\casper\filesystem.squashfs
01-08 16:52 DEBUG Distro: checking whether D:\ is a valid Kubuntu CD
01-08 16:52 DEBUG Distro: does not contain D:\casper\filesystem.squashfs
01-08 16:52 DEBUG Distro: checking whether D:\ is a valid Kubuntu Netbook CD
01-08 16:52 DEBUG Distro: does not contain D:\casper\filesystem.squashfs
01-08 16:52 DEBUG Distro: checking whether D:\ is a valid Xubuntu CD
01-08 16:52 DEBUG Distro: does not contain D:\casper\filesystem.squashfs
01-08 16:52 DEBUG Distro: checking whether D:\ is a valid Xubuntu CD
01-08 16:52 DEBUG Distro: does not contain D:\casper\filesystem.squashfs
01-08 16:52 DEBUG Distro: checking whether D:\ is a valid Mythbuntu CD
01-08 16:52 DEBUG Distro: does not contain D:\casper\filesystem.squashfs
01-08 16:52 DEBUG Distro: checking whether D:\ is a valid Mythbuntu CD
01-08 16:52 DEBUG Distro: does not contain D:\casper\filesystem.squashfs
01-08 16:52 INFO root: Running the uninstaller...
01-08 16:52 INFO CommonBackend: This is the uninstaller running
01-08 16:52 DEBUG WindowsFrontend: __init__...
01-08 16:52 DEBUG WindowsFrontend: on_init...
01-08 16:52 INFO WinuiPage: appname=wubi, localedir=C:\DOCUME~1\vicente\CONFIG~1\Temp\pylA.tmp\translations, languages=['es_ES', 'es']
01-08 16:52 INFO root: Received settings
01-08 16:52 INFO WinuiPage: appname=wubi, localedir=C:\DOCUME~1\vicente\CONFIG~1\Temp\pylA.tmp\translations, languages=['es_ES', 'es']
01-08 16:52 DEBUG TaskList: # Running tasklist...
01-08 16:52 DEBUG TaskList: ## Running Hacer una copia de la ISO...
01-08 16:52 DEBUG TaskList: ## Finished Hacer una copia de la ISO
01-08 16:52 DEBUG TaskList: ## Running Quitar entrada del cargador de arranque...
01-08 16:52 ERROR WindowsBackend: Cannot find bcdedit
01-08 16:52 DEBUG WindowsBackend: undo_bootini C:
01-08 16:52 DEBUG WindowsBackend: undo_configsys Drive(C: hd 23355.5195313 mb free ntfs)
01-08 16:52 DEBUG TaskList: ## Finished Quitar entrada del cargador de arranque
01-08 16:52 DEBUG TaskList: ## Running Borrar el directorio de destino...
01-08 16:52 DEBUG CommonBackend: Deleting C:\ubuntu
01-08 16:52 DEBUG TaskList: ## Finished Borrar el directorio de destino
01-08 16:52 DEBUG TaskList: ## Running Borrar clave del registro...
01-08 16:52 DEBUG TaskList: ## Finished Borrar clave del registro
01-08 16:52 DEBUG TaskList: # Finished tasklist
01-08 16:52 INFO root: Almost finished uninstalling
01-08 16:52 INFO WinuiPage: appname=wubi, localedir=C:\DOCUME~1\vicente\CONFIG~1\Temp\pylA.tmp\translations, languages=['es_ES', 'es']
01-08 16:52 INFO root: Finished uninstallation
01-08 16:52 DEBUG root: application.quit
01-08 16:52 DEBUG WindowsFrontend: frontend.quit
01-08 16:52 DEBUG WindowsFrontend: frontend.on_quit
01-08 16:52 DEBUG root: application.on_quit
01-08 16:52 INFO root: sys.exit

---

### Post by bcbc on 2012-01-20
That's a different log file - the Wubi rev 192 is for 10.04.3. Rev 189 is 10.04.

So anyway, it looks like you have a 10.04 CD but there's some problem with it (when it tries to copy the ISO it's failing).

You'd do best to download the [desktop CD ISO]("http://releases.ubuntu.com/10.04/ubuntu-10.04.3-desktop-i386.iso") and [wubi.exe]("http://releases.ubuntu.com/10.04/wubi.exe") from here: [http://releases.ubuntu.com/10.04/](http://releases.ubuntu.com/10.04/)
Save them into the same folder and run Wubi.exe from there. That will give you the latest 10.04 (currently 10.04.3). 

Make sure you take out the bad CD before running Wubi or it will find it (and likely use it and fail) instead of the local ISO.

---

### Post by JVMS on 2012-01-20
OOOOOHHHH mannnnnn ....finally I got it, THANKYOU VERY VERY VERY MUCH....[COLOR=black]**bcbc**[/COLOR]

---

