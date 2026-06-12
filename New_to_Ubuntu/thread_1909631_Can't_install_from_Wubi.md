---
title: "Can't install from Wubi"
date: 2012-01-15
forum: New to Ubuntu
---

### Post by fluffy283 on 2012-01-15
I have a computer with Windows XP service pack 2. A few days ago I downloaded Xubuntu 11.10 onto a USB drive, hoping to install it onto my computer.

This is my basic setup:
Windows XP Service Pack 2
4 GB USB Drive with Xubuntu 11.10 [to run trial and install/Wubi]
No internet access [can get on from boyfriend's laptop or Android phone]
40-GB hard drive, half of which is C: [containing Windows] the other half is D: [empty]

So the other day I plugged in my USB drive and ran Wubi. I can not reboot with my USB drive, because the Boot Menu and Setup don't show my USB drive at all. I chose "install alongside Windows", then chose D: drive, 12 GB, and set up my username and password. It went very smoothly without any help or interference from me until the very last second of the install, when it showed an error message similar to [I don't know if this is word for word or not]: Windows Backend object has no attribute 'iso-path' - see log for details.

I don't know where this log is or should be, and if I did I wouldn't know what it said. I don't even know what that error message means. I know an ISO is an image of a CD/DVD that can be burned. But I wasn't running an ISO and I don't have any ISOs on my Windows or on my USB.

Did I set up my install options wrong? Is my USB set up incorrectly for the install? I have noticed that I can download Ubuntu packages to my Android so if needed I will try to grab any recommended packages to transfer to my USB. Any help is appreciated.

---

### Post by lisati on 2012-01-15
Wubi's error log can usually be found in your Windows %temp% folder. Click on Start->Run, type in **%temp%** into the box, and press 'Enter' - this should open up an explorer window where you should be able to find the log file. As an aside, don't be alarmed if there's a lot of junk in %temp% - most of it can be safely deleted once you've saved your work.

---

### Post by fluffy283 on 2012-01-15
Okay, thank you for your reply, and I will look into that later today. Is there any part of the log that I should write down to post here later?

---

### Post by lisati on 2012-01-15
It has been a couple of years since I've used Wubi, so I might not be able to help personally. One option would be to upload the whole log file as an attachment so someone with more recent experience can take a look.

---

### Post by fluffy283 on 2012-01-22
I just tried to attach the log to this message so hopefully it will show up...

---

### Post by fluffy283 on 2012-01-22
Well I can't see any indication of an attachment, so here's the log.
 
01-14 12:10 INFO   root: === wubi 11.10 rev241 ===
01-14 12:10 DEBUG  root: Logfile is c:\docume~1\fluffy\locals~1\temp\wubi-11.10-rev241.log
01-14 12:10 DEBUG  root: sys.argv = ['main.pyo', '--exefile="F:\\wubi.exe"']
01-14 12:10 DEBUG  CommonBackend: data_dir=C:\DOCUME~1\Fluffy\LOCALS~1\Temp\pyl3.tmp\data
01-14 12:10 DEBUG  WindowsBackend: 7z=C:\DOCUME~1\Fluffy\LOCALS~1\Temp\pyl3.tmp\bin\7z.exe
01-14 12:10 DEBUG  WindowsBackend: startup_folder=C:\Documents and Settings\All Users\Start Menu\Programs\Startup
01-14 12:10 DEBUG  CommonBackend: Fetching basic info...
01-14 12:10 DEBUG  CommonBackend: original_exe=F:\wubi.exe
01-14 12:10 DEBUG  CommonBackend: platform=win32
01-14 12:10 DEBUG  CommonBackend: osname=nt
01-14 12:10 DEBUG  CommonBackend: language=en_US
01-14 12:10 DEBUG  CommonBackend: encoding=cp1252
01-14 12:10 DEBUG  WindowsBackend: arch=i386
01-14 12:10 DEBUG  CommonBackend: Parsing isolist=C:\DOCUME~1\Fluffy\LOCALS~1\Temp\pyl3.tmp\data\isolist.ini
01-14 12:10 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
01-14 12:10 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
01-14 12:10 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
01-14 12:10 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
01-14 12:10 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
01-14 12:10 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
01-14 12:10 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
01-14 12:10 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
01-14 12:10 DEBUG  WindowsBackend: Fetching host info...
01-14 12:10 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
01-14 12:10 DEBUG  WindowsBackend: windows version=xp
01-14 12:10 DEBUG  WindowsBackend: windows_version2=Microsoft Windows XP
01-14 12:10 DEBUG  WindowsBackend: windows_sp=Service Pack 2
01-14 12:10 DEBUG  WindowsBackend: windows_build=2600
01-14 12:10 DEBUG  WindowsBackend: gmt=-6
01-14 12:10 DEBUG  WindowsBackend: country=US
01-14 12:10 DEBUG  WindowsBackend: timezone=America/Chicago
01-14 12:10 DEBUG  WindowsBackend: windows_username=Fluffy
01-14 12:10 DEBUG  WindowsBackend: user_full_name=Fluffy
01-14 12:10 DEBUG  WindowsBackend: user_directory=C:\Documents and Settings\Fluffy
01-14 12:10 DEBUG  WindowsBackend: windows_language_code=1033
01-14 12:10 DEBUG  WindowsBackend: windows_language=English
01-14 12:10 DEBUG  WindowsBackend: processor_name=              Intel(R) Pentium(R) 4 CPU 1.70GHz
01-14 12:10 DEBUG  WindowsBackend: bootloader=xp
01-14 12:10 DEBUG  WindowsBackend: system_drive=Drive(C: hd 14929.8046875 mb free ntfs)
01-14 12:10 DEBUG  WindowsBackend: drive=Drive(C: hd 14929.8046875 mb free ntfs)
01-14 12:10 DEBUG  WindowsBackend: drive=Drive(D: hd 20086.7382813 mb free ntfs)
01-14 12:10 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free )
01-14 12:10 DEBUG  WindowsBackend: drive=Drive(F: removable 3135.46875 mb free fat32)
01-14 12:10 DEBUG  WindowsBackend: uninstaller_path=None
01-14 12:10 DEBUG  WindowsBackend: previous_target_dir=None
01-14 12:10 DEBUG  WindowsBackend: previous_distro_name=None
01-14 12:10 DEBUG  WindowsBackend: keyboard_id=67699721
01-14 12:10 DEBUG  WindowsBackend: keyboard_layout=us
01-14 12:10 DEBUG  WindowsBackend: keyboard_variant=
01-14 12:10 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
01-14 12:10 DEBUG  CommonBackend: locale=en_US.UTF-8
01-14 12:10 DEBUG  WindowsBackend: total_memory_mb=511.01171875
01-14 12:10 DEBUG  CommonBackend: Searching ISOs on USB devices
01-14 12:10 DEBUG  CommonBackend: Searching for local CDs
01-14 12:10 DEBUG  Distro:   checking whether C:\DOCUME~1\Fluffy\LOCALS~1\Temp\pyl3.tmp is a valid Ubuntu CD
01-14 12:10 DEBUG  Distro:     does not contain C:\DOCUME~1\Fluffy\LOCALS~1\Temp\pyl3.tmp\casper\filesystem.squashfs
01-14 12:10 DEBUG  Distro:   checking whether C:\DOCUME~1\Fluffy\LOCALS~1\Temp\pyl3.tmp is a valid Ubuntu CD
01-14 12:10 DEBUG  Distro:     does not contain C:\DOCUME~1\Fluffy\LOCALS~1\Temp\pyl3.tmp\casper\filesystem.squashfs
01-14 12:10 DEBUG  Distro:   checking whether C:\DOCUME~1\Fluffy\LOCALS~1\Temp\pyl3.tmp is a valid Kubuntu CD
01-14 12:10 DEBUG  Distro:     does not contain C:\DOCUME~1\Fluffy\LOCALS~1\Temp\pyl3.tmp\casper\filesystem.squashfs
01-14 12:10 DEBUG  Distro:   checking whether C:\DOCUME~1\Fluffy\LOCALS~1\Temp\pyl3.tmp is a valid Kubuntu CD
01-14 12:10 DEBUG  Distro:     does not contain C:\DOCUME~1\Fluffy\LOCALS~1\Temp\pyl3.tmp\casper\filesystem.squashfs
01-14 12:10 DEBUG  Distro:   checking whether C:\DOCUME~1\Fluffy\LOCALS~1\Temp\pyl3.tmp is a valid Xubuntu CD
01-14 12:10 DEBUG  Distro:     does not contain C:\DOCUME~1\Fluffy\LOCALS~1\Temp\pyl3.tmp\casper\filesystem.squashfs
01-14 12:10 DEBUG  Distro:   checking whether C:\DOCUME~1\Fluffy\LOCALS~1\Temp\pyl3.tmp is a valid Xubuntu CD
01-14 12:10 DEBUG  Distro:     does not contain C:\DOCUME~1\Fluffy\LOCALS~1\Temp\pyl3.tmp\casper\filesystem.squashfs
01-14 12:10 DEBUG  Distro:   checking whether C:\DOCUME~1\Fluffy\LOCALS~1\Temp\pyl3.tmp is a valid Mythbuntu CD
01-14 12:10 DEBUG  Distro:     does not contain C:\DOCUME~1\Fluffy\LOCALS~1\Temp\pyl3.tmp\casper\filesystem.squashfs
01-14 12:10 DEBUG  Distro:   checking whether C:\DOCUME~1\Fluffy\LOCALS~1\Temp\pyl3.tmp is a valid Mythbuntu CD
01-14 12:10 DEBUG  Distro:     does not contain C:\DOCUME~1\Fluffy\LOCALS~1\Temp\pyl3.tmp\casper\filesystem.squashfs
01-14 12:10 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
01-14 12:10 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-14 12:10 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
01-14 12:10 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-14 12:10 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
01-14 12:10 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-14 12:10 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
01-14 12:10 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-14 12:10 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
01-14 12:10 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-14 12:10 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
01-14 12:10 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-14 12:10 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
01-14 12:10 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-14 12:10 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
01-14 12:10 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-14 12:10 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
01-14 12:10 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
01-14 12:10 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
01-14 12:10 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
01-14 12:10 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
01-14 12:10 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
01-14 12:10 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
01-14 12:10 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
01-14 12:10 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
01-14 12:10 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
01-14 12:10 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
01-14 12:10 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
01-14 12:10 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
01-14 12:10 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
01-14 12:10 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
01-14 12:10 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
01-14 12:10 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
01-14 12:10 DEBUG  Distro:   parsing info from str=Xubuntu 11.10 "Oneiric Ocelot" - Release i386 (20111012)
01-14 12:10 DEBUG  Distro:   parsed info={'name': 'Xubuntu', 'subversion': 'Release', 'version': '11.10', 'build': '20111012', 'codename': 'Oneiric Ocelot', 'arch': 'i386'}
01-14 12:10 DEBUG  Distro: wrong name: Xubuntu != Ubuntu
01-14 12:10 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
01-14 12:10 DEBUG  Distro: wrong name: Xubuntu != Ubuntu
01-14 12:10 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
01-14 12:10 DEBUG  Distro: wrong name: Xubuntu != Kubuntu
01-14 12:10 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
01-14 12:10 DEBUG  Distro: wrong name: Xubuntu != Kubuntu
01-14 12:10 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
01-14 12:10 INFO   Distro: Found a valid CD for Xubuntu: F:\
01-14 12:10 INFO   root: Running the CD menu...
01-14 12:10 DEBUG  WindowsFrontend: __init__...
01-14 12:10 DEBUG  WindowsFrontend: on_init...
01-14 12:10 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Fluffy\LOCALS~1\Temp\pyl3.tmp\translations, languages=['en_US', 'en']
01-14 12:10 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Fluffy\LOCALS~1\Temp\pyl3.tmp\translations, languages=['en_US', 'en']
01-14 12:10 INFO   WindowsFrontend: Operation cancelled
01-14 12:10 DEBUG  WindowsFrontend: frontend.quit
01-14 12:10 DEBUG  WindowsFrontend: frontend.on_quit
01-14 12:10 DEBUG  root: application.on_quit
01-14 12:10 INFO   root: sys.exit
01-14 12:11 INFO   root: === wubi 11.10 rev241 ===
01-14 12:11 DEBUG  root: Logfile is c:\docume~1\fluffy\locals~1\temp\wubi-11.10-rev241.log
01-14 12:11 DEBUG  root: sys.argv = ['main.pyo', '--exefile="F:\\wubi.exe"']
01-14 12:11 DEBUG  CommonBackend: data_dir=C:\DOCUME~1\Fluffy\LOCALS~1\Temp\pyl4.tmp\data
01-14 12:11 DEBUG  WindowsBackend: 7z=C:\DOCUME~1\Fluffy\LOCALS~1\Temp\pyl4.tmp\bin\7z.exe
01-14 12:11 DEBUG  WindowsBackend: startup_folder=C:\Documents and Settings\All Users\Start Menu\Programs\Startup
01-14 12:11 DEBUG  CommonBackend: Fetching basic info...
01-14 12:11 DEBUG  CommonBackend: original_exe=F:\wubi.exe
01-14 12:11 DEBUG  CommonBackend: platform=win32
01-14 12:11 DEBUG  CommonBackend: osname=nt
01-14 12:11 DEBUG  CommonBackend: language=en_US
01-14 12:11 DEBUG  CommonBackend: encoding=cp1252
01-14 12:11 DEBUG  WindowsBackend: arch=i386
01-14 12:11 DEBUG  CommonBackend: Parsing isolist=C:\DOCUME~1\Fluffy\LOCALS~1\Temp\pyl4.tmp\data\isolist.ini
01-14 12:11 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
01-14 12:11 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
01-14 12:11 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
01-14 12:11 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
01-14 12:11 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
01-14 12:11 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
01-14 12:11 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
01-14 12:11 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
01-14 12:11 DEBUG  WindowsBackend: Fetching host info...
01-14 12:11 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
01-14 12:11 DEBUG  WindowsBackend: windows version=xp
01-14 12:11 DEBUG  WindowsBackend: windows_version2=Microsoft Windows XP
01-14 12:11 DEBUG  WindowsBackend: windows_sp=Service Pack 2
01-14 12:11 DEBUG  WindowsBackend: windows_build=2600
01-14 12:11 DEBUG  WindowsBackend: gmt=-6
01-14 12:11 DEBUG  WindowsBackend: country=US
01-14 12:11 DEBUG  WindowsBackend: timezone=America/Chicago
01-14 12:11 DEBUG  WindowsBackend: windows_username=Fluffy
01-14 12:11 DEBUG  WindowsBackend: user_full_name=Fluffy
01-14 12:11 DEBUG  WindowsBackend: user_directory=C:\Documents and Settings\Fluffy
01-14 12:11 DEBUG  WindowsBackend: windows_language_code=1033
01-14 12:11 DEBUG  WindowsBackend: windows_language=English
01-14 12:11 DEBUG  WindowsBackend: processor_name=              Intel(R) Pentium(R) 4 CPU 1.70GHz
01-14 12:11 DEBUG  WindowsBackend: bootloader=xp
01-14 12:11 DEBUG  WindowsBackend: system_drive=Drive(C: hd 14929.6835938 mb free ntfs)
01-14 12:11 DEBUG  WindowsBackend: drive=Drive(C: hd 14929.6835938 mb free ntfs)
01-14 12:11 DEBUG  WindowsBackend: drive=Drive(D: hd 20086.7382813 mb free ntfs)
01-14 12:11 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free )
01-14 12:11 DEBUG  WindowsBackend: drive=Drive(F: removable 3135.46875 mb free fat32)
01-14 12:11 DEBUG  WindowsBackend: uninstaller_path=None
01-14 12:11 DEBUG  WindowsBackend: previous_target_dir=None
01-14 12:11 DEBUG  WindowsBackend: previous_distro_name=None
01-14 12:11 DEBUG  WindowsBackend: keyboard_id=67699721
01-14 12:11 DEBUG  WindowsBackend: keyboard_layout=us
01-14 12:11 DEBUG  WindowsBackend: keyboard_variant=
01-14 12:11 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
01-14 12:11 DEBUG  CommonBackend: locale=en_US.UTF-8
01-14 12:11 DEBUG  WindowsBackend: total_memory_mb=511.01171875
01-14 12:11 DEBUG  CommonBackend: Searching ISOs on USB devices
01-14 12:11 DEBUG  CommonBackend: Searching for local CDs
01-14 12:11 DEBUG  Distro:   checking whether C:\DOCUME~1\Fluffy\LOCALS~1\Temp\pyl4.tmp is a valid Ubuntu CD
01-14 12:11 DEBUG  Distro:     does not contain C:\DOCUME~1\Fluffy\LOCALS~1\Temp\pyl4.tmp\casper\filesystem.squashfs
01-14 12:11 DEBUG  Distro:   checking whether C:\DOCUME~1\Fluffy\LOCALS~1\Temp\pyl4.tmp is a valid Ubuntu CD
01-14 12:11 DEBUG  Distro:     does not contain C:\DOCUME~1\Fluffy\LOCALS~1\Temp\pyl4.tmp\casper\filesystem.squashfs
01-14 12:11 DEBUG  Distro:   checking whether C:\DOCUME~1\Fluffy\LOCALS~1\Temp\pyl4.tmp is a valid Kubuntu CD
01-14 12:11 DEBUG  Distro:     does not contain C:\DOCUME~1\Fluffy\LOCALS~1\Temp\pyl4.tmp\casper\filesystem.squashfs
01-14 12:11 DEBUG  Distro:   checking whether C:\DOCUME~1\Fluffy\LOCALS~1\Temp\pyl4.tmp is a valid Kubuntu CD
01-14 12:11 DEBUG  Distro:     does not contain C:\DOCUME~1\Fluffy\LOCALS~1\Temp\pyl4.tmp\casper\filesystem.squashfs
01-14 12:11 DEBUG  Distro:   checking whether C:\DOCUME~1\Fluffy\LOCALS~1\Temp\pyl4.tmp is a valid Xubuntu CD
01-14 12:11 DEBUG  Distro:     does not contain C:\DOCUME~1\Fluffy\LOCALS~1\Temp\pyl4.tmp\casper\filesystem.squashfs
01-14 12:11 DEBUG  Distro:   checking whether C:\DOCUME~1\Fluffy\LOCALS~1\Temp\pyl4.tmp is a valid Xubuntu CD
01-14 12:11 DEBUG  Distro:     does not contain C:\DOCUME~1\Fluffy\LOCALS~1\Temp\pyl4.tmp\casper\filesystem.squashfs
01-14 12:11 DEBUG  Distro:   checking whether C:\DOCUME~1\Fluffy\LOCALS~1\Temp\pyl4.tmp is a valid Mythbuntu CD
01-14 12:11 DEBUG  Distro:     does not contain C:\DOCUME~1\Fluffy\LOCALS~1\Temp\pyl4.tmp\casper\filesystem.squashfs
01-14 12:11 DEBUG  Distro:   checking whether C:\DOCUME~1\Fluffy\LOCALS~1\Temp\pyl4.tmp is a valid Mythbuntu CD
01-14 12:11 DEBUG  Distro:     does not contain C:\DOCUME~1\Fluffy\LOCALS~1\Temp\pyl4.tmp\casper\filesystem.squashfs
01-14 12:11 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
01-14 12:11 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-14 12:11 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
01-14 12:11 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-14 12:11 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
01-14 12:11 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-14 12:11 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
01-14 12:11 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-14 12:11 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
01-14 12:11 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-14 12:11 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
01-14 12:11 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-14 12:11 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
01-14 12:11 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-14 12:11 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
01-14 12:11 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-14 12:11 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
01-14 12:11 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
01-14 12:11 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
01-14 12:11 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
01-14 12:11 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
01-14 12:11 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
01-14 12:11 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
01-14 12:11 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
01-14 12:11 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
01-14 12:11 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
01-14 12:11 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
01-14 12:11 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
01-14 12:11 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
01-14 12:11 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
01-14 12:11 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
01-14 12:11 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
01-14 12:11 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
01-14 12:11 DEBUG  Distro:   parsing info from str=Xubuntu 11.10 "Oneiric Ocelot" - Release i386 (20111012)
01-14 12:11 DEBUG  Distro:   parsed info={'name': 'Xubuntu', 'subversion': 'Release', 'version': '11.10', 'build': '20111012', 'codename': 'Oneiric Ocelot', 'arch': 'i386'}
01-14 12:11 DEBUG  Distro: wrong name: Xubuntu != Ubuntu
01-14 12:11 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
01-14 12:11 DEBUG  Distro: wrong name: Xubuntu != Ubuntu
01-14 12:11 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
01-14 12:11 DEBUG  Distro: wrong name: Xubuntu != Kubuntu
01-14 12:11 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
01-14 12:11 DEBUG  Distro: wrong name: Xubuntu != Kubuntu
01-14 12:11 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
01-14 12:11 INFO   Distro: Found a valid CD for Xubuntu: F:\
01-14 12:11 INFO   root: Running the CD menu...
01-14 12:11 DEBUG  WindowsFrontend: __init__...
01-14 12:11 DEBUG  WindowsFrontend: on_init...
01-14 12:11 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Fluffy\LOCALS~1\Temp\pyl4.tmp\translations, languages=['en_US', 'en']
01-14 12:11 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Fluffy\LOCALS~1\Temp\pyl4.tmp\translations, languages=['en_US', 'en']
01-14 12:11 INFO   root: CD menu finished
01-14 12:11 INFO   root: Rebooting
01-14 12:11 DEBUG  TaskList: # Running tasklist...
01-14 12:11 DEBUG  TaskList: ## Running reboot...
01-14 12:11 DEBUG  TaskList: ## Finished reboot
01-14 12:11 DEBUG  TaskList: # Finished tasklist
01-14 12:11 DEBUG  root: application.quit
01-14 12:11 DEBUG  WindowsFrontend: frontend.quit
01-14 12:11 DEBUG  WindowsFrontend: frontend.on_quit
01-14 12:11 DEBUG  root: application.on_quit
01-14 12:11 INFO   root: sys.exit
01-14 12:19 INFO   root: === wubi 11.10 rev241 ===
01-14 12:19 DEBUG  root: Logfile is c:\docume~1\fluffy\locals~1\temp\wubi-11.10-rev241.log
01-14 12:19 DEBUG  root: sys.argv = ['main.pyo', '--exefile="F:\\wubi.exe"']
01-14 12:19 DEBUG  CommonBackend: data_dir=C:\DOCUME~1\Fluffy\LOCALS~1\Temp\pyl3.tmp\data
01-14 12:19 DEBUG  WindowsBackend: 7z=C:\DOCUME~1\Fluffy\LOCALS~1\Temp\pyl3.tmp\bin\7z.exe
01-14 12:19 DEBUG  WindowsBackend: startup_folder=C:\Documents and Settings\All Users\Start Menu\Programs\Startup
01-14 12:19 DEBUG  CommonBackend: Fetching basic info...
01-14 12:19 DEBUG  CommonBackend: original_exe=F:\wubi.exe
01-14 12:19 DEBUG  CommonBackend: platform=win32
01-14 12:19 DEBUG  CommonBackend: osname=nt
01-14 12:19 DEBUG  CommonBackend: language=en_US
01-14 12:19 DEBUG  CommonBackend: encoding=cp1252
01-14 12:19 DEBUG  WindowsBackend: arch=i386
01-14 12:19 DEBUG  CommonBackend: Parsing isolist=C:\DOCUME~1\Fluffy\LOCALS~1\Temp\pyl3.tmp\data\isolist.ini
01-14 12:19 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
01-14 12:19 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
01-14 12:19 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
01-14 12:19 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
01-14 12:19 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
01-14 12:19 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
01-14 12:19 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
01-14 12:19 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
01-14 12:19 DEBUG  WindowsBackend: Fetching host info...
01-14 12:19 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
01-14 12:19 DEBUG  WindowsBackend: windows version=xp
01-14 12:19 DEBUG  WindowsBackend: windows_version2=Microsoft Windows XP
01-14 12:19 DEBUG  WindowsBackend: windows_sp=Service Pack 2
01-14 12:19 DEBUG  WindowsBackend: windows_build=2600
01-14 12:19 DEBUG  WindowsBackend: gmt=-6
01-14 12:19 DEBUG  WindowsBackend: country=US
01-14 12:19 DEBUG  WindowsBackend: timezone=America/Chicago
01-14 12:19 DEBUG  WindowsBackend: windows_username=Fluffy
01-14 12:19 DEBUG  WindowsBackend: user_full_name=Fluffy
01-14 12:19 DEBUG  WindowsBackend: user_directory=C:\Documents and Settings\Fluffy
01-14 12:19 DEBUG  WindowsBackend: windows_language_code=1033
01-14 12:19 DEBUG  WindowsBackend: windows_language=English
01-14 12:19 DEBUG  WindowsBackend: processor_name=              Intel(R) Pentium(R) 4 CPU 1.70GHz
01-14 12:19 DEBUG  WindowsBackend: bootloader=xp
01-14 12:19 DEBUG  WindowsBackend: system_drive=Drive(C: hd 14919.5859375 mb free ntfs)
01-14 12:19 DEBUG  WindowsBackend: drive=Drive(C: hd 14919.5859375 mb free ntfs)
01-14 12:19 DEBUG  WindowsBackend: drive=Drive(D: hd 20086.7382813 mb free ntfs)
01-14 12:19 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free )
01-14 12:19 DEBUG  WindowsBackend: drive=Drive(F: removable 3135.46875 mb free fat32)
01-14 12:19 DEBUG  WindowsBackend: uninstaller_path=None
01-14 12:19 DEBUG  WindowsBackend: previous_target_dir=None
01-14 12:19 DEBUG  WindowsBackend: previous_distro_name=None
01-14 12:19 DEBUG  WindowsBackend: keyboard_id=67699721
01-14 12:19 DEBUG  WindowsBackend: keyboard_layout=us
01-14 12:19 DEBUG  WindowsBackend: keyboard_variant=
01-14 12:19 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
01-14 12:19 DEBUG  CommonBackend: locale=en_US.UTF-8
01-14 12:19 DEBUG  WindowsBackend: total_memory_mb=511.01171875
01-14 12:19 DEBUG  CommonBackend: Searching ISOs on USB devices
01-14 12:19 DEBUG  CommonBackend: Searching for local CDs
01-14 12:19 DEBUG  Distro:   checking whether C:\DOCUME~1\Fluffy\LOCALS~1\Temp\pyl3.tmp is a valid Ubuntu CD
01-14 12:19 DEBUG  Distro:     does not contain C:\DOCUME~1\Fluffy\LOCALS~1\Temp\pyl3.tmp\casper\filesystem.squashfs
01-14 12:19 DEBUG  Distro:   checking whether C:\DOCUME~1\Fluffy\LOCALS~1\Temp\pyl3.tmp is a valid Ubuntu CD
01-14 12:19 DEBUG  Distro:     does not contain C:\DOCUME~1\Fluffy\LOCALS~1\Temp\pyl3.tmp\casper\filesystem.squashfs
01-14 12:19 DEBUG  Distro:   checking whether C:\DOCUME~1\Fluffy\LOCALS~1\Temp\pyl3.tmp is a valid Kubuntu CD
01-14 12:19 DEBUG  Distro:     does not contain C:\DOCUME~1\Fluffy\LOCALS~1\Temp\pyl3.tmp\casper\filesystem.squashfs
01-14 12:19 DEBUG  Distro:   checking whether C:\DOCUME~1\Fluffy\LOCALS~1\Temp\pyl3.tmp is a valid Kubuntu CD
01-14 12:19 DEBUG  Distro:     does not contain C:\DOCUME~1\Fluffy\LOCALS~1\Temp\pyl3.tmp\casper\filesystem.squashfs
01-14 12:19 DEBUG  Distro:   checking whether C:\DOCUME~1\Fluffy\LOCALS~1\Temp\pyl3.tmp is a valid Xubuntu CD
01-14 12:19 DEBUG  Distro:     does not contain C:\DOCUME~1\Fluffy\LOCALS~1\Temp\pyl3.tmp\casper\filesystem.squashfs
01-14 12:19 DEBUG  Distro:   checking whether C:\DOCUME~1\Fluffy\LOCALS~1\Temp\pyl3.tmp is a valid Xubuntu CD
01-14 12:19 DEBUG  Distro:     does not contain C:\DOCUME~1\Fluffy\LOCALS~1\Temp\pyl3.tmp\casper\filesystem.squashfs
01-14 12:19 DEBUG  Distro:   checking whether C:\DOCUME~1\Fluffy\LOCALS~1\Temp\pyl3.tmp is a valid Mythbuntu CD
01-14 12:19 DEBUG  Distro:     does not contain C:\DOCUME~1\Fluffy\LOCALS~1\Temp\pyl3.tmp\casper\filesystem.squashfs
01-14 12:19 DEBUG  Distro:   checking whether C:\DOCUME~1\Fluffy\LOCALS~1\Temp\pyl3.tmp is a valid Mythbuntu CD
01-14 12:19 DEBUG  Distro:     does not contain C:\DOCUME~1\Fluffy\LOCALS~1\Temp\pyl3.tmp\casper\filesystem.squashfs
01-14 12:19 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
01-14 12:19 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-14 12:19 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
01-14 12:19 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-14 12:19 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
01-14 12:19 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-14 12:19 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
01-14 12:19 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-14 12:19 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
01-14 12:19 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-14 12:19 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
01-14 12:19 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-14 12:19 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
01-14 12:19 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-14 12:19 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
01-14 12:19 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-14 12:19 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
01-14 12:20 INFO   root: === wubi 11.10 rev241 ===
01-14 12:20 DEBUG  root: Logfile is c:\docume~1\fluffy\locals~1\temp\wubi-11.10-rev241.log
01-14 12:20 DEBUG  root: sys.argv = ['main.pyo', '--exefile="F:\\wubi.exe"']
01-14 12:20 DEBUG  CommonBackend: data_dir=C:\DOCUME~1\Fluffy\LOCALS~1\Temp\pyl5.tmp\data
01-14 12:20 DEBUG  WindowsBackend: 7z=C:\DOCUME~1\Fluffy\LOCALS~1\Temp\pyl5.tmp\bin\7z.exe
01-14 12:20 DEBUG  WindowsBackend: startup_folder=C:\Documents and Settings\All Users\Start Menu\Programs\Startup
01-14 12:20 DEBUG  CommonBackend: Fetching basic info...
01-14 12:20 DEBUG  CommonBackend: original_exe=F:\wubi.exe
01-14 12:20 DEBUG  CommonBackend: platform=win32
01-14 12:20 DEBUG  CommonBackend: osname=nt
01-14 12:20 DEBUG  CommonBackend: language=en_US
01-14 12:20 DEBUG  CommonBackend: encoding=cp1252
01-14 12:20 DEBUG  WindowsBackend: arch=i386
01-14 12:20 DEBUG  CommonBackend: Parsing isolist=C:\DOCUME~1\Fluffy\LOCALS~1\Temp\pyl5.tmp\data\isolist.ini
01-14 12:20 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
01-14 12:20 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
01-14 12:20 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
01-14 12:20 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
01-14 12:20 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
01-14 12:20 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
01-14 12:20 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
01-14 12:20 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
01-14 12:20 DEBUG  WindowsBackend: Fetching host info...
01-14 12:20 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
01-14 12:20 DEBUG  WindowsBackend: windows version=xp
01-14 12:20 DEBUG  WindowsBackend: windows_version2=Microsoft Windows XP
01-14 12:20 DEBUG  WindowsBackend: windows_sp=Service Pack 2
01-14 12:20 DEBUG  WindowsBackend: windows_build=2600
01-14 12:20 DEBUG  WindowsBackend: gmt=-6
01-14 12:20 DEBUG  WindowsBackend: country=US
01-14 12:20 DEBUG  WindowsBackend: timezone=America/Chicago
01-14 12:20 DEBUG  WindowsBackend: windows_username=Fluffy
01-14 12:20 DEBUG  WindowsBackend: user_full_name=Fluffy
01-14 12:20 DEBUG  WindowsBackend: user_directory=C:\Documents and Settings\Fluffy
01-14 12:20 DEBUG  WindowsBackend: windows_language_code=1033
01-14 12:20 DEBUG  WindowsBackend: windows_language=English
01-14 12:20 DEBUG  WindowsBackend: processor_name=              Intel(R) Pentium(R) 4 CPU 1.70GHz
01-14 12:20 DEBUG  WindowsBackend: bootloader=xp
01-14 12:20 DEBUG  WindowsBackend: system_drive=Drive(C: hd 14909.7734375 mb free ntfs)
01-14 12:20 DEBUG  WindowsBackend: drive=Drive(C: hd 14909.7734375 mb free ntfs)
01-14 12:20 DEBUG  WindowsBackend: drive=Drive(D: hd 20086.7382813 mb free ntfs)
01-14 12:20 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free )
01-14 12:20 DEBUG  WindowsBackend: drive=Drive(F: removable 3135.46875 mb free fat32)
01-14 12:20 DEBUG  WindowsBackend: uninstaller_path=None
01-14 12:20 DEBUG  WindowsBackend: previous_target_dir=None
01-14 12:20 DEBUG  WindowsBackend: previous_distro_name=None
01-14 12:20 DEBUG  WindowsBackend: keyboard_id=67699721
01-14 12:20 DEBUG  WindowsBackend: keyboard_layout=us
01-14 12:20 DEBUG  WindowsBackend: keyboard_variant=
01-14 12:20 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
01-14 12:20 DEBUG  CommonBackend: locale=en_US.UTF-8
01-14 12:20 DEBUG  WindowsBackend: total_memory_mb=511.01171875
01-14 12:20 DEBUG  CommonBackend: Searching ISOs on USB devices
01-14 12:20 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
01-14 12:20 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
01-14 12:20 DEBUG  CommonBackend: Searching for local CDs
01-14 12:20 DEBUG  Distro:   checking whether C:\DOCUME~1\Fluffy\LOCALS~1\Temp\pyl5.tmp is a valid Ubuntu CD
01-14 12:20 DEBUG  Distro:     does not contain C:\DOCUME~1\Fluffy\LOCALS~1\Temp\pyl5.tmp\casper\filesystem.squashfs
01-14 12:20 DEBUG  Distro:   checking whether C:\DOCUME~1\Fluffy\LOCALS~1\Temp\pyl5.tmp is a valid Ubuntu CD
01-14 12:20 DEBUG  Distro:     does not contain C:\DOCUME~1\Fluffy\LOCALS~1\Temp\pyl5.tmp\casper\filesystem.squashfs
01-14 12:20 DEBUG  Distro:   checking whether C:\DOCUME~1\Fluffy\LOCALS~1\Temp\pyl5.tmp is a valid Kubuntu CD
01-14 12:20 DEBUG  Distro:     does not contain C:\DOCUME~1\Fluffy\LOCALS~1\Temp\pyl5.tmp\casper\filesystem.squashfs
01-14 12:20 DEBUG  Distro:   checking whether C:\DOCUME~1\Fluffy\LOCALS~1\Temp\pyl5.tmp is a valid Kubuntu CD
01-14 12:20 DEBUG  Distro:     does not contain C:\DOCUME~1\Fluffy\LOCALS~1\Temp\pyl5.tmp\casper\filesystem.squashfs
01-14 12:20 DEBUG  Distro:   checking whether C:\DOCUME~1\Fluffy\LOCALS~1\Temp\pyl5.tmp is a valid Xubuntu CD
01-14 12:20 DEBUG  Distro:     does not contain C:\DOCUME~1\Fluffy\LOCALS~1\Temp\pyl5.tmp\casper\filesystem.squashfs
01-14 12:20 DEBUG  Distro:   checking whether C:\DOCUME~1\Fluffy\LOCALS~1\Temp\pyl5.tmp is a valid Xubuntu CD
01-14 12:20 DEBUG  Distro:     does not contain C:\DOCUME~1\Fluffy\LOCALS~1\Temp\pyl5.tmp\casper\filesystem.squashfs
01-14 12:20 DEBUG  Distro:   checking whether C:\DOCUME~1\Fluffy\LOCALS~1\Temp\pyl5.tmp is a valid Mythbuntu CD
01-14 12:20 DEBUG  Distro:     does not contain C:\DOCUME~1\Fluffy\LOCALS~1\Temp\pyl5.tmp\casper\filesystem.squashfs
01-14 12:20 DEBUG  Distro:   checking whether C:\DOCUME~1\Fluffy\LOCALS~1\Temp\pyl5.tmp is a valid Mythbuntu CD
01-14 12:20 DEBUG  Distro:     does not contain C:\DOCUME~1\Fluffy\LOCALS~1\Temp\pyl5.tmp\casper\filesystem.squashfs
01-14 12:20 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
01-14 12:20 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-14 12:20 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
01-14 12:20 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-14 12:20 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
01-14 12:20 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-14 12:20 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
01-14 12:20 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-14 12:20 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
01-14 12:20 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-14 12:20 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
01-14 12:20 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-14 12:20 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
01-14 12:20 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-14 12:20 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
01-14 12:20 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-14 12:20 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
01-14 12:20 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
01-14 12:20 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
01-14 12:20 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
01-14 12:20 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
01-14 12:20 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
01-14 12:20 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
01-14 12:21 INFO   root: === wubi 11.10 rev241 ===
01-14 12:21 DEBUG  root: Logfile is c:\docume~1\fluffy\locals~1\temp\wubi-11.10-rev241.log
01-14 12:21 DEBUG  root: sys.argv = ['main.pyo', '--exefile="F:\\wubi.exe"']
01-14 12:21 DEBUG  CommonBackend: data_dir=C:\DOCUME~1\Fluffy\LOCALS~1\Temp\pyl6.tmp\data
01-14 12:21 DEBUG  WindowsBackend: 7z=C:\DOCUME~1\Fluffy\LOCALS~1\Temp\pyl6.tmp\bin\7z.exe
01-14 12:21 DEBUG  WindowsBackend: startup_folder=C:\Documents and Settings\All Users\Start Menu\Programs\Startup
01-14 12:21 DEBUG  CommonBackend: Fetching basic info...
01-14 12:21 DEBUG  CommonBackend: original_exe=F:\wubi.exe
01-14 12:21 DEBUG  CommonBackend: platform=win32
01-14 12:21 DEBUG  CommonBackend: osname=nt
01-14 12:21 DEBUG  CommonBackend: language=en_US
01-14 12:21 DEBUG  CommonBackend: encoding=cp1252
01-14 12:21 DEBUG  WindowsBackend: arch=i386
01-14 12:21 DEBUG  CommonBackend: Parsing isolist=C:\DOCUME~1\Fluffy\LOCALS~1\Temp\pyl6.tmp\data\isolist.ini
01-14 12:21 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
01-14 12:21 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
01-14 12:21 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
01-14 12:21 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
01-14 12:21 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
01-14 12:21 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
01-14 12:21 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
01-14 12:21 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
01-14 12:21 DEBUG  WindowsBackend: Fetching host info...
01-14 12:21 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
01-14 12:21 DEBUG  WindowsBackend: windows version=xp
01-14 12:21 DEBUG  WindowsBackend: windows_version2=Microsoft Windows XP
01-14 12:21 DEBUG  WindowsBackend: windows_sp=Service Pack 2
01-14 12:21 DEBUG  WindowsBackend: windows_build=2600
01-14 12:21 DEBUG  WindowsBackend: gmt=-6
01-14 12:21 DEBUG  WindowsBackend: country=US
01-14 12:21 DEBUG  WindowsBackend: timezone=America/Chicago
01-14 12:21 DEBUG  WindowsBackend: windows_username=Fluffy
01-14 12:21 DEBUG  WindowsBackend: user_full_name=Fluffy
01-14 12:21 DEBUG  WindowsBackend: user_directory=C:\Documents and Settings\Fluffy
01-14 12:21 DEBUG  WindowsBackend: windows_language_code=1033
01-14 12:21 DEBUG  WindowsBackend: windows_language=English
01-14 12:21 DEBUG  WindowsBackend: processor_name=              Intel(R) Pentium(R) 4 CPU 1.70GHz
01-14 12:21 DEBUG  WindowsBackend: bootloader=xp
01-14 12:21 DEBUG  WindowsBackend: system_drive=Drive(C: hd 14899.9335938 mb free ntfs)
01-14 12:21 DEBUG  WindowsBackend: drive=Drive(C: hd 14899.9335938 mb free ntfs)
01-14 12:21 DEBUG  WindowsBackend: drive=Drive(D: hd 20086.7382813 mb free ntfs)
01-14 12:21 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
01-14 12:21 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
01-14 12:21 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free )
01-14 12:21 DEBUG  WindowsBackend: drive=Drive(F: removable 3135.12695313 mb free fat32)
01-14 12:21 DEBUG  WindowsBackend: uninstaller_path=None
01-14 12:21 DEBUG  WindowsBackend: previous_target_dir=None
01-14 12:21 DEBUG  WindowsBackend: previous_distro_name=None
01-14 12:21 DEBUG  WindowsBackend: keyboard_id=67699721
01-14 12:21 DEBUG  WindowsBackend: keyboard_layout=us
01-14 12:21 DEBUG  WindowsBackend: keyboard_variant=
01-14 12:21 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
01-14 12:21 DEBUG  CommonBackend: locale=en_US.UTF-8
01-14 12:21 DEBUG  WindowsBackend: total_memory_mb=511.01171875
01-14 12:21 DEBUG  CommonBackend: Searching ISOs on USB devices
01-14 12:21 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
01-14 12:21 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
01-14 12:21 DEBUG  CommonBackend: Searching for local CDs
01-14 12:21 DEBUG  Distro:   checking whether C:\DOCUME~1\Fluffy\LOCALS~1\Temp\pyl6.tmp is a valid Ubuntu CD
01-14 12:21 DEBUG  Distro:     does not contain C:\DOCUME~1\Fluffy\LOCALS~1\Temp\pyl6.tmp\casper\filesystem.squashfs
01-14 12:21 DEBUG  Distro:   checking whether C:\DOCUME~1\Fluffy\LOCALS~1\Temp\pyl6.tmp is a valid Ubuntu CD
01-14 12:21 DEBUG  Distro:     does not contain C:\DOCUME~1\Fluffy\LOCALS~1\Temp\pyl6.tmp\casper\filesystem.squashfs
01-14 12:21 DEBUG  Distro:   checking whether C:\DOCUME~1\Fluffy\LOCALS~1\Temp\pyl6.tmp is a valid Kubuntu CD
01-14 12:21 DEBUG  Distro:     does not contain C:\DOCUME~1\Fluffy\LOCALS~1\Temp\pyl6.tmp\casper\filesystem.squashfs
01-14 12:21 DEBUG  Distro:   checking whether C:\DOCUME~1\Fluffy\LOCALS~1\Temp\pyl6.tmp is a valid Kubuntu CD
01-14 12:21 DEBUG  Distro:     does not contain C:\DOCUME~1\Fluffy\LOCALS~1\Temp\pyl6.tmp\casper\filesystem.squashfs
01-14 12:21 DEBUG  Distro:   checking whether C:\DOCUME~1\Fluffy\LOCALS~1\Temp\pyl6.tmp is a valid Xubuntu CD
01-14 12:21 DEBUG  Distro:     does not contain C:\DOCUME~1\Fluffy\LOCALS~1\Temp\pyl6.tmp\casper\filesystem.squashfs
01-14 12:21 DEBUG  Distro:   checking whether C:\DOCUME~1\Fluffy\LOCALS~1\Temp\pyl6.tmp is a valid Xubuntu CD
01-14 12:21 DEBUG  Distro:     does not contain C:\DOCUME~1\Fluffy\LOCALS~1\Temp\pyl6.tmp\casper\filesystem.squashfs
01-14 12:21 DEBUG  Distro:   checking whether C:\DOCUME~1\Fluffy\LOCALS~1\Temp\pyl6.tmp is a valid Mythbuntu CD
01-14 12:21 DEBUG  Distro:     does not contain C:\DOCUME~1\Fluffy\LOCALS~1\Temp\pyl6.tmp\casper\filesystem.squashfs
01-14 12:21 DEBUG  Distro:   checking whether C:\DOCUME~1\Fluffy\LOCALS~1\Temp\pyl6.tmp is a valid Mythbuntu CD
01-14 12:21 DEBUG  Distro:     does not contain C:\DOCUME~1\Fluffy\LOCALS~1\Temp\pyl6.tmp\casper\filesystem.squashfs
01-14 12:21 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
01-14 12:21 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-14 12:21 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
01-14 12:21 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-14 12:21 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
01-14 12:21 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-14 12:21 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
01-14 12:21 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-14 12:21 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
01-14 12:21 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-14 12:21 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
01-14 12:21 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-14 12:21 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
01-14 12:21 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-14 12:21 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
01-14 12:21 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-14 12:21 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
01-14 12:21 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
01-14 12:21 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
01-14 12:21 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
01-14 12:21 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
01-14 12:21 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
01-14 12:21 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
01-14 12:21 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
01-14 12:21 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
01-14 12:21 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
01-14 12:21 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
01-14 12:22 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
01-14 12:22 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
01-14 12:22 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
01-14 12:22 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
01-14 12:22 INFO   root: === wubi 11.10 rev241 ===
01-14 12:22 DEBUG  root: Logfile is c:\docume~1\fluffy\locals~1\temp\wubi-11.10-rev241.log
01-14 12:22 DEBUG  root: sys.argv = ['main.pyo', '--exefile="F:\\wubi.exe"']
01-14 12:22 DEBUG  CommonBackend: data_dir=C:\DOCUME~1\Fluffy\LOCALS~1\Temp\pyl7.tmp\data
01-14 12:22 DEBUG  WindowsBackend: 7z=C:\DOCUME~1\Fluffy\LOCALS~1\Temp\pyl7.tmp\bin\7z.exe
01-14 12:22 DEBUG  WindowsBackend: startup_folder=C:\Documents and Settings\All Users\Start Menu\Programs\Startup
01-14 12:22 DEBUG  CommonBackend: Fetching basic info...
01-14 12:22 DEBUG  CommonBackend: original_exe=F:\wubi.exe
01-14 12:22 DEBUG  CommonBackend: platform=win32
01-14 12:22 DEBUG  CommonBackend: osname=nt
01-14 12:22 DEBUG  CommonBackend: language=en_US
01-14 12:22 DEBUG  CommonBackend: encoding=cp1252
01-14 12:22 DEBUG  WindowsBackend: arch=i386
01-14 12:22 DEBUG  CommonBackend: Parsing isolist=C:\DOCUME~1\Fluffy\LOCALS~1\Temp\pyl7.tmp\data\isolist.ini
01-14 12:22 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
01-14 12:22 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
01-14 12:22 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
01-14 12:22 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
01-14 12:22 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
01-14 12:22 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
01-14 12:22 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
01-14 12:22 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
01-14 12:22 DEBUG  WindowsBackend: Fetching host info...
01-14 12:22 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
01-14 12:22 DEBUG  WindowsBackend: windows version=xp
01-14 12:22 DEBUG  WindowsBackend: windows_version2=Microsoft Windows XP
01-14 12:22 DEBUG  WindowsBackend: windows_sp=Service Pack 2
01-14 12:22 DEBUG  WindowsBackend: windows_build=2600
01-14 12:22 DEBUG  WindowsBackend: gmt=-6
01-14 12:22 DEBUG  WindowsBackend: country=US
01-14 12:22 DEBUG  WindowsBackend: timezone=America/Chicago
01-14 12:22 DEBUG  WindowsBackend: windows_username=Fluffy
01-14 12:22 DEBUG  WindowsBackend: user_full_name=Fluffy
01-14 12:22 DEBUG  WindowsBackend: user_directory=C:\Documents and Settings\Fluffy
01-14 12:22 DEBUG  WindowsBackend: windows_language_code=1033
01-14 12:22 DEBUG  WindowsBackend: windows_language=English
01-14 12:22 DEBUG  WindowsBackend: processor_name=              Intel(R) Pentium(R) 4 CPU 1.70GHz
01-14 12:22 DEBUG  WindowsBackend: bootloader=xp
01-14 12:22 DEBUG  WindowsBackend: system_drive=Drive(C: hd 14890.0429688 mb free ntfs)
01-14 12:22 DEBUG  WindowsBackend: drive=Drive(C: hd 14890.0429688 mb free ntfs)
01-14 12:22 DEBUG  WindowsBackend: drive=Drive(D: hd 20086.7382813 mb free ntfs)
01-14 12:23 INFO   root: === wubi 11.10 rev241 ===
01-14 12:23 DEBUG  root: Logfile is c:\docume~1\fluffy\locals~1\temp\wubi-11.10-rev241.log
01-14 12:23 DEBUG  root: sys.argv = ['main.pyo', '--exefile="F:\\wubi.exe"']
01-14 12:23 DEBUG  CommonBackend: data_dir=C:\DOCUME~1\Fluffy\LOCALS~1\Temp\pyl8.tmp\data
01-14 12:23 DEBUG  WindowsBackend: 7z=C:\DOCUME~1\Fluffy\LOCALS~1\Temp\pyl8.tmp\bin\7z.exe
01-14 12:23 DEBUG  WindowsBackend: startup_folder=C:\Documents and Settings\All Users\Start Menu\Programs\Startup
01-14 12:23 DEBUG  CommonBackend: Fetching basic info...
01-14 12:23 DEBUG  CommonBackend: original_exe=F:\wubi.exe
01-14 12:23 DEBUG  CommonBackend: platform=win32
01-14 12:23 DEBUG  CommonBackend: osname=nt
01-14 12:23 DEBUG  CommonBackend: language=en_US
01-14 12:23 DEBUG  CommonBackend: encoding=cp1252
01-14 12:23 DEBUG  WindowsBackend: arch=i386
01-14 12:23 DEBUG  CommonBackend: Parsing isolist=C:\DOCUME~1\Fluffy\LOCALS~1\Temp\pyl8.tmp\data\isolist.ini
01-14 12:23 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
01-14 12:23 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
01-14 12:23 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
01-14 12:23 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
01-14 12:23 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
01-14 12:23 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
01-14 12:23 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
01-14 12:23 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
01-14 12:23 DEBUG  WindowsBackend: Fetching host info...
01-14 12:23 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
01-14 12:23 DEBUG  WindowsBackend: windows version=xp
01-14 12:23 DEBUG  WindowsBackend: windows_version2=Microsoft Windows XP
01-14 12:23 DEBUG  WindowsBackend: windows_sp=Service Pack 2
01-14 12:23 DEBUG  WindowsBackend: windows_build=2600
01-14 12:23 DEBUG  WindowsBackend: gmt=-6
01-14 12:23 DEBUG  WindowsBackend: country=US
01-14 12:23 DEBUG  WindowsBackend: timezone=America/Chicago
01-14 12:23 DEBUG  WindowsBackend: windows_username=Fluffy
01-14 12:23 DEBUG  WindowsBackend: user_full_name=Fluffy
01-14 12:23 DEBUG  WindowsBackend: user_directory=C:\Documents and Settings\Fluffy
01-14 12:23 DEBUG  WindowsBackend: windows_language_code=1033
01-14 12:23 DEBUG  WindowsBackend: windows_language=English
01-14 12:23 DEBUG  WindowsBackend: processor_name=              Intel(R) Pentium(R) 4 CPU 1.70GHz
01-14 12:23 DEBUG  WindowsBackend: bootloader=xp
01-14 12:23 DEBUG  WindowsBackend: system_drive=Drive(C: hd 14880.1679688 mb free ntfs)
01-14 12:23 DEBUG  WindowsBackend: drive=Drive(C: hd 14880.1679688 mb free ntfs)
01-14 12:23 DEBUG  WindowsBackend: drive=Drive(D: hd 20086.7382813 mb free ntfs)
01-14 12:23 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free )
01-14 12:23 DEBUG  WindowsBackend: drive=Drive(F: removable 3126.16601563 mb free fat32)
01-14 12:23 DEBUG  WindowsBackend: uninstaller_path=None
01-14 12:23 DEBUG  WindowsBackend: previous_target_dir=None
01-14 12:23 DEBUG  WindowsBackend: previous_distro_name=None
01-14 12:23 DEBUG  WindowsBackend: keyboard_id=67699721
01-14 12:23 DEBUG  WindowsBackend: keyboard_layout=us
01-14 12:23 DEBUG  WindowsBackend: keyboard_variant=
01-14 12:23 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
01-14 12:23 DEBUG  CommonBackend: locale=en_US.UTF-8
01-14 12:23 DEBUG  WindowsBackend: total_memory_mb=511.01171875
01-14 12:23 DEBUG  CommonBackend: Searching ISOs on USB devices
01-14 12:23 DEBUG  CommonBackend: Searching for local CDs
01-14 12:23 DEBUG  Distro:   checking whether C:\DOCUME~1\Fluffy\LOCALS~1\Temp\pyl8.tmp is a valid Ubuntu CD
01-14 12:23 DEBUG  Distro:     does not contain C:\DOCUME~1\Fluffy\LOCALS~1\Temp\pyl8.tmp\casper\filesystem.squashfs
01-14 12:23 DEBUG  Distro:   checking whether C:\DOCUME~1\Fluffy\LOCALS~1\Temp\pyl8.tmp is a valid Ubuntu CD
01-14 12:23 DEBUG  Distro:     does not contain C:\DOCUME~1\Fluffy\LOCALS~1\Temp\pyl8.tmp\casper\filesystem.squashfs
01-14 12:23 DEBUG  Distro:   checking whether C:\DOCUME~1\Fluffy\LOCALS~1\Temp\pyl8.tmp is a valid Kubuntu CD
01-14 12:23 DEBUG  Distro:     does not contain C:\DOCUME~1\Fluffy\LOCALS~1\Temp\pyl8.tmp\casper\filesystem.squashfs
01-14 12:23 DEBUG  Distro:   checking whether C:\DOCUME~1\Fluffy\LOCALS~1\Temp\pyl8.tmp is a valid Kubuntu CD
01-14 12:23 DEBUG  Distro:     does not contain C:\DOCUME~1\Fluffy\LOCALS~1\Temp\pyl8.tmp\casper\filesystem.squashfs
01-14 12:23 DEBUG  Distro:   checking whether C:\DOCUME~1\Fluffy\LOCALS~1\Temp\pyl8.tmp is a valid Xubuntu CD
01-14 12:23 DEBUG  Distro:     does not contain C:\DOCUME~1\Fluffy\LOCALS~1\Temp\pyl8.tmp\casper\filesystem.squashfs
01-14 12:23 DEBUG  Distro:   checking whether C:\DOCUME~1\Fluffy\LOCALS~1\Temp\pyl8.tmp is a valid Xubuntu CD
01-14 12:23 DEBUG  Distro:     does not contain C:\DOCUME~1\Fluffy\LOCALS~1\Temp\pyl8.tmp\casper\filesystem.squashfs
01-14 12:23 DEBUG  Distro:   checking whether C:\DOCUME~1\Fluffy\LOCALS~1\Temp\pyl8.tmp is a valid Mythbuntu CD
01-14 12:23 DEBUG  Distro:     does not contain C:\DOCUME~1\Fluffy\LOCALS~1\Temp\pyl8.tmp\casper\filesystem.squashfs
01-14 12:23 DEBUG  Distro:   checking whether C:\DOCUME~1\Fluffy\LOCALS~1\Temp\pyl8.tmp is a valid Mythbuntu CD
01-14 12:23 DEBUG  Distro:     does not contain C:\DOCUME~1\Fluffy\LOCALS~1\Temp\pyl8.tmp\casper\filesystem.squashfs
01-14 12:23 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
01-14 12:23 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-14 12:23 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
01-14 12:23 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-14 12:23 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
01-14 12:23 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-14 12:23 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
01-14 12:23 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-14 12:23 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
01-14 12:23 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-14 12:23 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
01-14 12:23 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-14 12:23 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
01-14 12:23 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-14 12:23 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
01-14 12:23 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-14 12:23 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
01-14 12:23 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
01-14 12:23 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
01-14 12:23 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
01-14 12:23 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
01-14 12:24 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
01-14 12:24 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
01-14 12:24 ERROR  Distro: [Errno 22] Invalid argument
01-14 12:24 DEBUG  Distro: could not get info None
01-14 12:24 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
01-14 12:24 DEBUG  Distro: could not get info None
01-14 12:24 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
01-14 12:24 DEBUG  Distro: could not get info None
01-14 12:24 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
01-14 12:24 DEBUG  Distro: could not get info None
01-14 12:24 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
01-14 12:24 DEBUG  Distro: could not get info None
01-14 12:24 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
01-14 12:24 DEBUG  Distro:   parsing info from str=Xubuntu 11.10 "Oneiric Ocelot" - Release i386 (20111012)
01-14 12:24 DEBUG  Distro:   parsed info={'name': 'Xubuntu', 'subversion': 'Release', 'version': '11.10', 'build': '20111012', 'codename': 'Oneiric Ocelot', 'arch': 'i386'}
01-14 12:24 DEBUG  Distro: wrong name: Xubuntu != Ubuntu
01-14 12:24 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
01-14 12:24 DEBUG  Distro: wrong name: Xubuntu != Ubuntu
01-14 12:24 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
01-14 12:24 DEBUG  Distro: wrong name: Xubuntu != Kubuntu
01-14 12:24 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
01-14 12:24 DEBUG  Distro: wrong name: Xubuntu != Kubuntu
01-14 12:24 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
01-14 12:24 INFO   Distro: Found a valid CD for Xubuntu: F:\
01-14 12:24 INFO   root: Running the CD menu...
01-14 12:24 DEBUG  WindowsFrontend: __init__...
01-14 12:24 DEBUG  WindowsFrontend: on_init...
01-14 12:24 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Fluffy\LOCALS~1\Temp\pyl8.tmp\translations, languages=['en_US', 'en']
01-14 12:24 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Fluffy\LOCALS~1\Temp\pyl8.tmp\translations, languages=['en_US', 'en']
01-14 12:24 INFO   root: CD menu finished
01-14 12:24 INFO   root: Running the installer...
01-14 12:24 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Fluffy\LOCALS~1\Temp\pyl8.tmp\translations, languages=['en_US', 'en']
01-14 12:24 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Fluffy\LOCALS~1\Temp\pyl8.tmp\translations, languages=['en_US', 'en']
01-14 12:24 INFO   root: === wubi 11.10 rev241 ===
01-14 12:24 DEBUG  root: Logfile is c:\docume~1\fluffy\locals~1\temp\wubi-11.10-rev241.log
01-14 12:24 DEBUG  root: sys.argv = ['main.pyo', '--exefile="F:\\wubi.exe"']
01-14 12:24 DEBUG  CommonBackend: data_dir=C:\DOCUME~1\Fluffy\LOCALS~1\Temp\pyl9.tmp\data
01-14 12:24 DEBUG  WindowsBackend: 7z=C:\DOCUME~1\Fluffy\LOCALS~1\Temp\pyl9.tmp\bin\7z.exe
01-14 12:24 DEBUG  WindowsBackend: startup_folder=C:\Documents and Settings\All Users\Start Menu\Programs\Startup
01-14 12:24 DEBUG  CommonBackend: Fetching basic info...
01-14 12:24 DEBUG  CommonBackend: original_exe=F:\wubi.exe
01-14 12:24 DEBUG  CommonBackend: platform=win32
01-14 12:24 DEBUG  CommonBackend: osname=nt
01-14 12:24 DEBUG  CommonBackend: language=en_US
01-14 12:24 DEBUG  CommonBackend: encoding=cp1252
01-14 12:24 DEBUG  WindowsBackend: arch=i386
01-14 12:24 DEBUG  CommonBackend: Parsing isolist=C:\DOCUME~1\Fluffy\LOCALS~1\Temp\pyl9.tmp\data\isolist.ini
01-14 12:24 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
01-14 12:24 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
01-14 12:24 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
01-14 12:24 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
01-14 12:24 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
01-14 12:24 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
01-14 12:24 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
01-14 12:24 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
01-14 12:24 DEBUG  WindowsBackend: Fetching host info...
01-14 12:24 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
01-14 12:24 DEBUG  WindowsBackend: windows version=xp
01-14 12:24 DEBUG  WindowsBackend: windows_version2=Microsoft Windows XP
01-14 12:24 DEBUG  WindowsBackend: windows_sp=Service Pack 2
01-14 12:24 DEBUG  WindowsBackend: windows_build=2600
01-14 12:24 DEBUG  WindowsBackend: gmt=-6
01-14 12:24 DEBUG  WindowsBackend: country=US
01-14 12:24 DEBUG  WindowsBackend: timezone=America/Chicago
01-14 12:24 DEBUG  WindowsBackend: windows_username=Fluffy
01-14 12:24 DEBUG  WindowsBackend: user_full_name=Fluffy
01-14 12:24 DEBUG  WindowsBackend: user_directory=C:\Documents and Settings\Fluffy
01-14 12:24 DEBUG  WindowsBackend: windows_language_code=1033
01-14 12:24 DEBUG  WindowsBackend: windows_language=English
01-14 12:24 DEBUG  WindowsBackend: processor_name=              Intel(R) Pentium(R) 4 CPU 1.70GHz
01-14 12:24 DEBUG  WindowsBackend: bootloader=xp
01-14 12:24 DEBUG  WindowsBackend: system_drive=Drive(C: hd 14870.3789063 mb free ntfs)
01-14 12:24 DEBUG  WindowsBackend: drive=Drive(C: hd 14870.3789063 mb free ntfs)
01-14 12:24 DEBUG  WindowsBackend: drive=Drive(D: hd 20086.7382813 mb free ntfs)
01-14 12:24 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free cdfs)
01-14 12:24 DEBUG  WindowsBackend: drive=Drive(F: removable 3126.16601563 mb free fat32)
01-14 12:24 DEBUG  WindowsBackend: uninstaller_path=None
01-14 12:24 DEBUG  WindowsBackend: previous_target_dir=None
01-14 12:24 DEBUG  WindowsBackend: previous_distro_name=None
01-14 12:24 DEBUG  WindowsBackend: keyboard_id=67699721
01-14 12:24 DEBUG  WindowsBackend: keyboard_layout=us
01-14 12:24 DEBUG  WindowsBackend: keyboard_variant=
01-14 12:24 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
01-14 12:24 DEBUG  CommonBackend: locale=en_US.UTF-8
01-14 12:24 DEBUG  WindowsBackend: total_memory_mb=511.01171875
01-14 12:24 DEBUG  CommonBackend: Searching ISOs on USB devices
01-14 12:24 DEBUG  CommonBackend: Searching for local CDs
01-14 12:24 DEBUG  Distro:   checking whether C:\DOCUME~1\Fluffy\LOCALS~1\Temp\pyl9.tmp is a valid Ubuntu CD
01-14 12:24 DEBUG  Distro:     does not contain C:\DOCUME~1\Fluffy\LOCALS~1\Temp\pyl9.tmp\casper\filesystem.squashfs
01-14 12:24 DEBUG  Distro:   checking whether C:\DOCUME~1\Fluffy\LOCALS~1\Temp\pyl9.tmp is a valid Ubuntu CD
01-14 12:24 DEBUG  Distro:     does not contain C:\DOCUME~1\Fluffy\LOCALS~1\Temp\pyl9.tmp\casper\filesystem.squashfs
01-14 12:24 DEBUG  Distro:   checking whether C:\DOCUME~1\Fluffy\LOCALS~1\Temp\pyl9.tmp is a valid Kubuntu CD
01-14 12:24 DEBUG  Distro:     does not contain C:\DOCUME~1\Fluffy\LOCALS~1\Temp\pyl9.tmp\casper\filesystem.squashfs
01-14 12:24 DEBUG  Distro:   checking whether C:\DOCUME~1\Fluffy\LOCALS~1\Temp\pyl9.tmp is a valid Kubuntu CD
01-14 12:24 DEBUG  Distro:     does not contain C:\DOCUME~1\Fluffy\LOCALS~1\Temp\pyl9.tmp\casper\filesystem.squashfs
01-14 12:24 DEBUG  Distro:   checking whether C:\DOCUME~1\Fluffy\LOCALS~1\Temp\pyl9.tmp is a valid Xubuntu CD
01-14 12:24 DEBUG  Distro:     does not contain C:\DOCUME~1\Fluffy\LOCALS~1\Temp\pyl9.tmp\casper\filesystem.squashfs
01-14 12:24 DEBUG  Distro:   checking whether C:\DOCUME~1\Fluffy\LOCALS~1\Temp\pyl9.tmp is a valid Xubuntu CD
01-14 12:24 DEBUG  Distro:     does not contain C:\DOCUME~1\Fluffy\LOCALS~1\Temp\pyl9.tmp\casper\filesystem.squashfs
01-14 12:24 DEBUG  Distro:   checking whether C:\DOCUME~1\Fluffy\LOCALS~1\Temp\pyl9.tmp is a valid Mythbuntu CD
01-14 12:24 DEBUG  Distro:     does not contain C:\DOCUME~1\Fluffy\LOCALS~1\Temp\pyl9.tmp\casper\filesystem.squashfs
01-14 12:24 DEBUG  Distro:   checking whether C:\DOCUME~1\Fluffy\LOCALS~1\Temp\pyl9.tmp is a valid Mythbuntu CD
01-14 12:24 DEBUG  Distro:     does not contain C:\DOCUME~1\Fluffy\LOCALS~1\Temp\pyl9.tmp\casper\filesystem.squashfs
01-14 12:24 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
01-14 12:24 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-14 12:24 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
01-14 12:24 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-14 12:24 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
01-14 12:24 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-14 12:24 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
01-14 12:24 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-14 12:24 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
01-14 12:24 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-14 12:24 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
01-14 12:24 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-14 12:24 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
01-14 12:24 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-14 12:24 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
01-14 12:24 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-14 12:24 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
01-14 12:24 ERROR  Distro: [Errno 22] Invalid argument
01-14 12:24 DEBUG  Distro: could not get info None
01-14 12:24 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
01-14 12:24 DEBUG  Distro: could not get info None
01-14 12:24 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
01-14 12:24 DEBUG  Distro: could not get info None
01-14 12:24 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
01-14 12:24 DEBUG  Distro: could not get info None
01-14 12:24 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
01-14 12:24 DEBUG  Distro: could not get info None
01-14 12:24 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
01-14 12:24 DEBUG  Distro: could not get info None
01-14 12:24 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
01-14 12:24 DEBUG  Distro: could not get info None
01-14 12:24 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
01-14 12:24 DEBUG  Distro: could not get info None
01-14 12:24 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
01-14 12:24 DEBUG  Distro:   parsing info from str=Xubuntu 11.10 "Oneiric Ocelot" - Release i386 (20111012)
01-14 12:24 DEBUG  Distro:   parsed info={'name': 'Xubuntu', 'subversion': 'Release', 'version': '11.10', 'build': '20111012', 'codename': 'Oneiric Ocelot', 'arch': 'i386'}
01-14 12:24 DEBUG  Distro: wrong name: Xubuntu != Ubuntu
01-14 12:24 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
01-14 12:24 DEBUG  Distro: wrong name: Xubuntu != Ubuntu
01-14 12:24 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
01-14 12:24 DEBUG  Distro: wrong name: Xubuntu != Kubuntu
01-14 12:24 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
01-14 12:24 DEBUG  Distro: wrong name: Xubuntu != Kubuntu
01-14 12:24 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
01-14 12:24 INFO   Distro: Found a valid CD for Xubuntu: F:\
01-14 12:24 INFO   root: Running the CD menu...
01-14 12:24 DEBUG  WindowsFrontend: __init__...
01-14 12:24 DEBUG  WindowsFrontend: on_init...
01-14 12:24 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Fluffy\LOCALS~1\Temp\pyl9.tmp\translations, languages=['en_US', 'en']
01-14 12:24 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Fluffy\LOCALS~1\Temp\pyl9.tmp\translations, languages=['en_US', 'en']
01-14 12:24 DEBUG  WinuiInstallationPage: target_drive=D:, installation_size=9000MB, distro_name=Xubuntu, language=en_US, locale=en_US.UTF-8, username=fluffy
01-14 12:24 INFO   root: Received settings
01-14 12:24 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Fluffy\LOCALS~1\Temp\pyl8.tmp\translations, languages=['en_US', 'en']
01-14 12:24 DEBUG  TaskList: # Running tasklist...
01-14 12:24 DEBUG  TaskList: ## Running select_target_dir...
01-14 12:24 INFO   WindowsBackend: Installing into D:\ubuntu
01-14 12:24 DEBUG  TaskList: ## Finished select_target_dir
01-14 12:24 DEBUG  TaskList: ## Running create_dir_structure...
01-14 12:24 DEBUG  CommonBackend: Creating dir D:\ubuntu
01-14 12:24 DEBUG  CommonBackend: Creating dir D:\ubuntu\disks
01-14 12:24 DEBUG  CommonBackend: Creating dir D:\ubuntu\install
01-14 12:24 DEBUG  CommonBackend: Creating dir D:\ubuntu\install\boot
01-14 12:24 DEBUG  CommonBackend: Creating dir D:\ubuntu\disks\boot
01-14 12:24 DEBUG  CommonBackend: Creating dir D:\ubuntu\disks\boot\grub
01-14 12:24 DEBUG  CommonBackend: Creating dir D:\ubuntu\install\boot\grub
01-14 12:24 DEBUG  TaskList: ## Finished create_dir_structure
01-14 12:24 DEBUG  TaskList: ## Running uncompress_target_dir...
01-14 12:24 DEBUG  TaskList: ## Finished uncompress_target_dir
01-14 12:24 DEBUG  TaskList: ## Running create_uninstaller...
01-14 12:24 DEBUG  WindowsBackend: Copying uninstaller F:\wubi.exe -> D:\ubuntu\uninstall-wubi.exe
01-14 12:24 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString D:\ubuntu\uninstall-wubi.exe
01-14 12:24 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir D:\ubuntu
01-14 12:24 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Xubuntu
01-14 12:24 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon D:\ubuntu\Xubuntu.ico
01-14 12:24 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 11.10-rev241
01-14 12:24 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Xubuntu
01-14 12:24 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.xubuntu.org](http://www.xubuntu.org)
01-14 12:24 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
01-14 12:24 DEBUG  TaskList: ## Finished create_uninstaller
01-14 12:24 DEBUG  TaskList: ## Running copy_installation_files...
01-14 12:24 DEBUG  WindowsBackend: Copying C:\DOCUME~1\Fluffy\LOCALS~1\Temp\pyl8.tmp\data\custom-installation -> D:\ubuntu\install\custom-installation
01-14 12:24 DEBUG  WindowsBackend: Copying C:\DOCUME~1\Fluffy\LOCALS~1\Temp\pyl8.tmp\winboot -> D:\ubuntu\winboot
01-14 12:24 DEBUG  WindowsBackend: Copying C:\DOCUME~1\Fluffy\LOCALS~1\Temp\pyl8.tmp\data\images\Xubuntu.ico -> D:\ubuntu\Xubuntu.ico
01-14 12:24 DEBUG  TaskList: ## Finished copy_installation_files
01-14 12:24 DEBUG  TaskList: ## Running get_iso...
01-14 12:24 DEBUG  TaskList: New task copy_file
01-14 12:24 DEBUG  TaskList: ### Running copy_file...
01-14 13:39 DEBUG  TaskList: ### Finished copy_file
01-14 13:39 DEBUG  TaskList: New task check_iso
01-14 13:39 DEBUG  TaskList: ### Running check_iso...
01-14 13:39 DEBUG  CommonBackend: Checking D:\ubuntu\install\installation.iso
01-14 13:39 DEBUG  Distro:   checking Xubuntu ISO D:\ubuntu\install\installation.iso
01-14 13:39 DEBUG  Distro:     wrong size: 4012883968 > 900000000
01-14 13:39 DEBUG  TaskList: ### Finished check_iso
01-14 13:39 ERROR  TaskList: 'WindowsBackend' object has no attribute 'iso_path'
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 579, in get_iso
  File "\lib\wubi\backends\common\backend.py", line 565, in use_iso
AttributeError: 'WindowsBackend' object has no attribute 'iso_path'
01-14 13:39 DEBUG  TaskList: # Cancelling tasklist
01-14 13:39 ERROR  root: 'WindowsBackend' object has no attribute 'iso_path'
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
01-14 13:39 DEBUG  TaskList: # Finished tasklist
01-14 13:45 INFO   root: CD menu finished
01-14 13:45 INFO   root: Running the installer...
01-14 13:45 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Fluffy\LOCALS~1\Temp\pyl9.tmp\translations, languages=['en_US', 'en']
01-14 13:45 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Fluffy\LOCALS~1\Temp\pyl9.tmp\translations, languages=['en_US', 'en']
01-14 13:46 DEBUG  WinuiInstallationPage: target_drive=D:, installation_size=14000MB, distro_name=Xubuntu, language=en_US, locale=en_US.UTF-8, username=fluffy
01-14 13:46 INFO   root: Received settings
01-14 13:46 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Fluffy\LOCALS~1\Temp\pyl9.tmp\translations, languages=['en_US', 'en']
01-14 13:46 DEBUG  TaskList: # Running tasklist...
01-14 13:46 DEBUG  TaskList: ## Running select_target_dir...
01-14 13:46 ERROR  TaskList: Cannot install into D:\ubuntu.
There is another file or directory with this name.
Please remove it before continuing.
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 82, in select_target_dir
Exception: Cannot install into D:\ubuntu.
There is another file or directory with this name.
Please remove it before continuing.
01-14 13:46 DEBUG  TaskList: # Cancelling tasklist
01-14 13:46 DEBUG  TaskList: # Finished tasklist
01-14 13:46 ERROR  root: Cannot install into D:\ubuntu.
There is another file or directory with this name.
Please remove it before continuing.
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 58, in run
  File "\lib\wubi\application.py", line 130, in select_task
  File "\lib\wubi\application.py", line 205, in run_cd_menu
  File "\lib\wubi\application.py", line 120, in select_task
  File "\lib\wubi\application.py", line 158, in run_installer
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 82, in select_target_dir
Exception: Cannot install into D:\ubuntu.
There is another file or directory with this name.
Please remove it before continuing.
01-14 13:47 INFO   root: === wubi 11.10 rev241 ===
01-14 13:47 DEBUG  root: Logfile is c:\docume~1\fluffy\locals~1\temp\wubi-11.10-rev241.log
01-14 13:47 DEBUG  root: sys.argv = ['main.pyo', '--exefile="D:\\ubuntu\\uninstall-wubi.exe"']
01-14 13:47 DEBUG  CommonBackend: data_dir=C:\DOCUME~1\Fluffy\LOCALS~1\Temp\pylC.tmp\data
01-14 13:47 DEBUG  WindowsBackend: 7z=C:\DOCUME~1\Fluffy\LOCALS~1\Temp\pylC.tmp\bin\7z.exe
01-14 13:47 DEBUG  WindowsBackend: startup_folder=C:\Documents and Settings\All Users\Start Menu\Programs\Startup
01-14 13:47 DEBUG  CommonBackend: Fetching basic info...
01-14 13:47 DEBUG  CommonBackend: original_exe=D:\ubuntu\uninstall-wubi.exe
01-14 13:47 DEBUG  CommonBackend: platform=win32
01-14 13:47 DEBUG  CommonBackend: osname=nt
01-14 13:47 DEBUG  CommonBackend: language=en_US
01-14 13:47 DEBUG  CommonBackend: encoding=cp1252
01-14 13:47 DEBUG  WindowsBackend: arch=i386
01-14 13:47 DEBUG  CommonBackend: Parsing isolist=C:\DOCUME~1\Fluffy\LOCALS~1\Temp\pylC.tmp\data\isolist.ini
01-14 13:47 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
01-14 13:47 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
01-14 13:47 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
01-14 13:47 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
01-14 13:47 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
01-14 13:47 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
01-14 13:47 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
01-14 13:47 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
01-14 13:47 DEBUG  WindowsBackend: Fetching host info...
01-14 13:47 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
01-14 13:47 DEBUG  WindowsBackend: windows version=xp
01-14 13:47 DEBUG  WindowsBackend: windows_version2=Microsoft Windows XP
01-14 13:47 DEBUG  WindowsBackend: windows_sp=Service Pack 2
01-14 13:47 DEBUG  WindowsBackend: windows_build=2600
01-14 13:47 DEBUG  WindowsBackend: gmt=-6
01-14 13:47 DEBUG  WindowsBackend: country=US
01-14 13:47 DEBUG  WindowsBackend: timezone=America/Chicago
01-14 13:47 DEBUG  WindowsBackend: windows_username=Fluffy
01-14 13:47 DEBUG  WindowsBackend: user_full_name=Fluffy
01-14 13:47 DEBUG  WindowsBackend: user_directory=C:\Documents and Settings\Fluffy
01-14 13:47 DEBUG  WindowsBackend: windows_language_code=1033
01-14 13:47 DEBUG  WindowsBackend: windows_language=English
01-14 13:47 DEBUG  WindowsBackend: processor_name=              Intel(R) Pentium(R) 4 CPU 1.70GHz
01-14 13:47 DEBUG  WindowsBackend: bootloader=xp
01-14 13:47 DEBUG  WindowsBackend: system_drive=Drive(C: hd 14890.5976563 mb free ntfs)
01-14 13:47 DEBUG  WindowsBackend: drive=Drive(C: hd 14890.5976563 mb free ntfs)
01-14 13:47 DEBUG  WindowsBackend: drive=Drive(D: hd 16257.109375 mb free ntfs)
01-14 13:47 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free cdfs)
01-14 13:47 DEBUG  WindowsBackend: drive=Drive(F: removable 3126.16601563 mb free fat32)
01-14 13:47 DEBUG  WindowsBackend: uninstaller_path=D:\ubuntu\uninstall-wubi.exe
01-14 13:47 DEBUG  WindowsBackend: previous_target_dir=D:\ubuntu
01-14 13:47 DEBUG  WindowsBackend: previous_distro_name=Xubuntu
01-14 13:47 DEBUG  WindowsBackend: keyboard_id=67699721
01-14 13:47 DEBUG  WindowsBackend: keyboard_layout=us
01-14 13:47 DEBUG  WindowsBackend: keyboard_variant=
01-14 13:47 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
01-14 13:47 DEBUG  CommonBackend: locale=en_US.UTF-8
01-14 13:47 DEBUG  WindowsBackend: total_memory_mb=511.01171875
01-14 13:47 DEBUG  CommonBackend: Searching ISOs on USB devices
01-14 13:47 DEBUG  CommonBackend: Searching for local CDs
01-14 13:47 DEBUG  Distro:   checking whether C:\DOCUME~1\Fluffy\LOCALS~1\Temp\pylC.tmp is a valid Ubuntu CD
01-14 13:47 DEBUG  Distro:     does not contain C:\DOCUME~1\Fluffy\LOCALS~1\Temp\pylC.tmp\casper\filesystem.squashfs
01-14 13:47 DEBUG  Distro:   checking whether C:\DOCUME~1\Fluffy\LOCALS~1\Temp\pylC.tmp is a valid Ubuntu CD
01-14 13:47 DEBUG  Distro:     does not contain C:\DOCUME~1\Fluffy\LOCALS~1\Temp\pylC.tmp\casper\filesystem.squashfs
01-14 13:47 DEBUG  Distro:   checking whether C:\DOCUME~1\Fluffy\LOCALS~1\Temp\pylC.tmp is a valid Kubuntu CD
01-14 13:47 DEBUG  Distro:     does not contain C:\DOCUME~1\Fluffy\LOCALS~1\Temp\pylC.tmp\casper\filesystem.squashfs
01-14 13:47 DEBUG  Distro:   checking whether C:\DOCUME~1\Fluffy\LOCALS~1\Temp\pylC.tmp is a valid Kubuntu CD
01-14 13:47 DEBUG  Distro:     does not contain C:\DOCUME~1\Fluffy\LOCALS~1\Temp\pylC.tmp\casper\filesystem.squashfs
01-14 13:47 DEBUG  Distro:   checking whether C:\DOCUME~1\Fluffy\LOCALS~1\Temp\pylC.tmp is a valid Xubuntu CD
01-14 13:47 DEBUG  Distro:     does not contain C:\DOCUME~1\Fluffy\LOCALS~1\Temp\pylC.tmp\casper\filesystem.squashfs
01-14 13:47 DEBUG  Distro:   checking whether C:\DOCUME~1\Fluffy\LOCALS~1\Temp\pylC.tmp is a valid Xubuntu CD
01-14 13:47 DEBUG  Distro:     does not contain C:\DOCUME~1\Fluffy\LOCALS~1\Temp\pylC.tmp\casper\filesystem.squashfs
01-14 13:47 DEBUG  Distro:   checking whether C:\DOCUME~1\Fluffy\LOCALS~1\Temp\pylC.tmp is a valid Mythbuntu CD
01-14 13:47 DEBUG  Distro:     does not contain C:\DOCUME~1\Fluffy\LOCALS~1\Temp\pylC.tmp\casper\filesystem.squashfs
01-14 13:47 DEBUG  Distro:   checking whether C:\DOCUME~1\Fluffy\LOCALS~1\Temp\pylC.tmp is a valid Mythbuntu CD
01-14 13:47 DEBUG  Distro:     does not contain C:\DOCUME~1\Fluffy\LOCALS~1\Temp\pylC.tmp\casper\filesystem.squashfs
01-14 13:47 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
01-14 13:47 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-14 13:47 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
01-14 13:47 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-14 13:47 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
01-14 13:47 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-14 13:47 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
01-14 13:47 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-14 13:47 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
01-14 13:47 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-14 13:47 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
01-14 13:47 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-14 13:47 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
01-14 13:47 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-14 13:47 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
01-14 13:47 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-14 13:47 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
01-14 13:47 ERROR  Distro: [Errno 22] Invalid argument
01-14 13:47 DEBUG  Distro: could not get info None
01-14 13:47 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
01-14 13:47 DEBUG  Distro: could not get info None
01-14 13:47 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
01-14 13:47 DEBUG  Distro: could not get info None
01-14 13:47 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
01-14 13:47 DEBUG  Distro: could not get info None
01-14 13:47 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
01-14 13:47 DEBUG  Distro: could not get info None
01-14 13:47 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
01-14 13:47 DEBUG  Distro: could not get info None
01-14 13:47 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
01-14 13:47 DEBUG  Distro: could not get info None
01-14 13:47 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
01-14 13:47 DEBUG  Distro: could not get info None
01-14 13:47 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
01-14 13:47 DEBUG  Distro:   parsing info from str=Xubuntu 11.10 "Oneiric Ocelot" - Release i386 (20111012)
01-14 13:47 DEBUG  Distro:   parsed info={'name': 'Xubuntu', 'subversion': 'Release', 'version': '11.10', 'build': '20111012', 'codename': 'Oneiric Ocelot', 'arch': 'i386'}
01-14 13:47 DEBUG  Distro: wrong name: Xubuntu != Ubuntu
01-14 13:47 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
01-14 13:47 DEBUG  Distro: wrong name: Xubuntu != Ubuntu
01-14 13:47 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
01-14 13:47 DEBUG  Distro: wrong name: Xubuntu != Kubuntu
01-14 13:47 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
01-14 13:47 DEBUG  Distro: wrong name: Xubuntu != Kubuntu
01-14 13:47 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
01-14 13:47 INFO   Distro: Found a valid CD for Xubuntu: F:\
01-14 13:47 INFO   root: Running the uninstaller...
01-14 13:47 INFO   CommonBackend: This is the uninstaller running
01-14 13:47 DEBUG  WindowsFrontend: __init__...
01-14 13:47 DEBUG  WindowsFrontend: on_init...
01-14 13:47 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Fluffy\LOCALS~1\Temp\pylC.tmp\translations, languages=['en_US', 'en']
01-14 13:47 INFO   WindowsFrontend: Operation cancelled
01-14 13:47 DEBUG  WindowsFrontend: frontend.quit
01-14 13:47 DEBUG  WindowsFrontend: frontend.on_quit
01-14 13:47 DEBUG  root: application.on_quit
01-14 13:47 INFO   root: sys.exit

---

### Post by bcbc on 2012-01-22
You cannot install Wubi from a USB stick. In some cases it works, but usually it doesn't... in this case the partition is 4GB and wubi fails the ISO due to a dumb size check:
```
01-14 13:39 DEBUG Distro: checking Xubuntu ISO D:\ubuntu\install\installation.iso
01-14 13:39 DEBUG Distro: wrong size: 4012883968 > 900000000
01-14 13:39 DEBUG TaskList: ### Finished check_iso
```

That check is supposed to prevent you from installing wubi from a DVD ISO.

Anyway... you can install Wubi by placing the ISO in the same folder as Wubi.exe before running it (hopefully you still have that ISO you used to create the USB). Just remove the USB before doing this. (Also make sure the wubi.exe is the same release; you can copy it off the USB to make sure).

---

### Post by ivanchic on 2012-02-14
I had some problems with installing Ubuntu and Xubuntu with Wubi. I guess that you have some antivirus program running with XP, one piece of advice, disable it temporarily before using Wubi!!

---

