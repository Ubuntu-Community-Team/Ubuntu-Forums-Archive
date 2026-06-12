---
title: "installation"
date: 2013-06-16
forum: New to Ubuntu
---

### Post by sanjibar on 2013-06-16
hi,
i use ubuntu alongside windows. after using 12.10 i switched to 13.04. i deleted a few files few weeks ago, and it stopped working. so i formatted the drive and tried reloading. now i get an error message towards the end of its torrent download. i have a text file of the error message, in case that helps. please advise.

---

### Post by oldos2er on 2013-06-16
Moved to Absolute Beginners, Forum Feedback & Help is for questions about the forum itself, not Ubuntu support.

---

### Post by deadflowr on 2013-06-16
Yes, the error message would be nice, if you please.

---

### Post by sanjibar on 2013-06-17
I tried to attach the text file along with my question but it exceeds the size limit of attachment.

---

### Post by 3rdalbum on 2013-06-17
Copy and paste it into the message?

---

### Post by sanjibar on 2013-06-17
here is the long text file -

```
06-16 19:22 INFO   root: === wubi 13.04 rev279 ===
06-16 19:22 DEBUG  root: Logfile is c:\users\sanjiv\appdata\local\temp\wubi-13.04-rev279.log
06-16 19:22 DEBUG  root: sys.argv = ['main.pyo', '--exefile="F:\\Ubuntu 13\\New folder\\wubi.exe"']
06-16 19:22 DEBUG  CommonBackend: data_dir=C:\Users\sanjiv\AppData\Local\Temp\pyl5560.tmp\data
06-16 19:22 DEBUG  WindowsBackend: 7z=C:\Users\sanjiv\AppData\Local\Temp\pyl5560.tmp\bin\7z.exe
06-16 19:22 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
06-16 19:22 DEBUG  CommonBackend: Fetching basic info...
06-16 19:22 DEBUG  CommonBackend: original_exe=F:\Ubuntu 13\New folder\wubi.exe
06-16 19:22 DEBUG  CommonBackend: platform=win32
06-16 19:22 DEBUG  CommonBackend: osname=nt
06-16 19:22 DEBUG  CommonBackend: language=en_US
06-16 19:22 DEBUG  CommonBackend: encoding=cp1252
06-16 19:22 DEBUG  WindowsBackend: arch=amd64
06-16 19:22 DEBUG  CommonBackend: Parsing isolist=C:\Users\sanjiv\AppData\Local\Temp\pyl5560.tmp\data\isolist.ini
06-16 19:22 DEBUG  CommonBackend:   Adding distro Edubuntu-i386
06-16 19:22 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
06-16 19:22 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
06-16 19:22 DEBUG  CommonBackend:   Adding distro Edubuntu-amd64
06-16 19:22 DEBUG  CommonBackend:   Adding distro Ubuntu Studio-amd64
06-16 19:22 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
06-16 19:22 DEBUG  CommonBackend:   Adding distro Lubuntu-i386
06-16 19:22 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
06-16 19:22 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
06-16 19:22 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
06-16 19:22 DEBUG  CommonBackend:   Adding distro Ubuntu Studio-i386
06-16 19:22 DEBUG  CommonBackend:   Adding distro Lubuntu-amd64
06-16 19:22 DEBUG  WindowsBackend: Fetching host info...
06-16 19:22 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
06-16 19:22 DEBUG  WindowsBackend: windows version=vista
06-16 19:22 DEBUG  WindowsBackend: windows_version2=Windows 8 Pro with Media Center
06-16 19:22 DEBUG  WindowsBackend: windows_sp=None
06-16 19:22 DEBUG  WindowsBackend: windows_build=9200
06-16 19:22 DEBUG  WindowsBackend: gmt=5
06-16 19:22 DEBUG  WindowsBackend: country=US
06-16 19:22 DEBUG  WindowsBackend: timezone=America/New_York
06-16 19:22 DEBUG  WindowsBackend: windows_username=sanjiv
06-16 19:22 DEBUG  WindowsBackend: user_full_name=sanjiv
06-16 19:22 DEBUG  WindowsBackend: user_directory=C:\Users\sanjiv
06-16 19:22 DEBUG  WindowsBackend: windows_language_code=1033
06-16 19:22 DEBUG  WindowsBackend: windows_language=English
06-16 19:22 DEBUG  WindowsBackend: processor_name=Intel(R) Pentium(R) D CPU 2.80GHz
06-16 19:22 DEBUG  WindowsBackend: bootloader=vista
06-16 19:22 DEBUG  WindowsBackend: system_drive=Drive(C: hd 1800.25390625 mb free ntfs)
06-16 19:22 DEBUG  WindowsBackend: drive=Drive(C: hd 1800.25390625 mb free ntfs)
06-16 19:22 DEBUG  WindowsBackend: drive=Drive(D: cd 0.0 mb free )
06-16 19:22 DEBUG  WindowsBackend: drive=Drive(E: hd 0.0 mb free )
06-16 19:22 DEBUG  WindowsBackend: drive=Drive(F: hd 293062.753906 mb free ntfs)
06-16 19:22 DEBUG  WindowsBackend: drive=Drive(G: hd 15494.1054688 mb free ntfs)
06-16 19:22 DEBUG  WindowsBackend: drive=Drive(H: hd 29896.421875 mb free ntfs)
06-16 19:22 DEBUG  WindowsBackend: drive=Drive(I: hd 39899.828125 mb free ntfs)
06-16 19:22 DEBUG  WindowsBackend: drive=Drive(J: hd 1354.125 mb free ntfs)
06-16 19:22 DEBUG  WindowsBackend: drive=Drive(K: hd 27218.09375 mb free ntfs)
06-16 19:22 DEBUG  WindowsBackend: drive=Drive(L: hd 7012.5625 mb free ntfs)
06-16 19:22 DEBUG  WindowsBackend: drive=Drive(M: cd 0.0 mb free cdfs)
06-16 19:22 DEBUG  WindowsBackend: uninstaller_path=E:\ubuntu\uninstall-wubi.exe
06-16 19:22 DEBUG  WindowsBackend: previous_target_dir=E:\ubuntu
06-16 19:22 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
06-16 19:22 DEBUG  WindowsBackend: keyboard_id=134809609
06-16 19:22 DEBUG  WindowsBackend: keyboard_layout=gb
06-16 19:22 DEBUG  WindowsBackend: keyboard_variant=
06-16 19:22 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
06-16 19:22 DEBUG  CommonBackend: locale=en_US.UTF-8
06-16 19:22 DEBUG  WindowsBackend: total_memory_mb=2047.99999905
06-16 19:22 DEBUG  CommonBackend: Searching ISOs on USB devices
06-16 19:22 DEBUG  CommonBackend: Searching for local CDs
06-16 19:22 DEBUG  Distro:   checking whether C:\Users\sanjiv\AppData\Local\Temp\pyl5560.tmp is a valid Ubuntu CD
06-16 19:22 DEBUG  Distro:     does not contain C:\Users\sanjiv\AppData\Local\Temp\pyl5560.tmp\casper\filesystem.squashfs
06-16 19:22 DEBUG  Distro:   checking whether C:\Users\sanjiv\AppData\Local\Temp\pyl5560.tmp is a valid Ubuntu CD
06-16 19:22 DEBUG  Distro:     does not contain C:\Users\sanjiv\AppData\Local\Temp\pyl5560.tmp\casper\filesystem.squashfs
06-16 19:22 DEBUG  Distro:   checking whether C:\Users\sanjiv\AppData\Local\Temp\pyl5560.tmp is a valid Kubuntu CD
06-16 19:22 DEBUG  Distro:     does not contain C:\Users\sanjiv\AppData\Local\Temp\pyl5560.tmp\casper\filesystem.squashfs
06-16 19:22 DEBUG  Distro:   checking whether C:\Users\sanjiv\AppData\Local\Temp\pyl5560.tmp is a valid Kubuntu CD
06-16 19:22 DEBUG  Distro:     does not contain C:\Users\sanjiv\AppData\Local\Temp\pyl5560.tmp\casper\filesystem.squashfs
06-16 19:22 DEBUG  Distro:   checking whether C:\Users\sanjiv\AppData\Local\Temp\pyl5560.tmp is a valid Mythbuntu CD
06-16 19:22 DEBUG  Distro:     does not contain C:\Users\sanjiv\AppData\Local\Temp\pyl5560.tmp\casper\filesystem.squashfs
06-16 19:22 DEBUG  Distro:   checking whether C:\Users\sanjiv\AppData\Local\Temp\pyl5560.tmp is a valid Mythbuntu CD
06-16 19:22 DEBUG  Distro:     does not contain C:\Users\sanjiv\AppData\Local\Temp\pyl5560.tmp\casper\filesystem.squashfs
06-16 19:22 DEBUG  Distro:   checking whether C:\Users\sanjiv\AppData\Local\Temp\pyl5560.tmp is a valid Edubuntu CD
06-16 19:22 DEBUG  Distro:     does not contain C:\Users\sanjiv\AppData\Local\Temp\pyl5560.tmp\casper\filesystem.squashfs
06-16 19:22 DEBUG  Distro:   checking whether C:\Users\sanjiv\AppData\Local\Temp\pyl5560.tmp is a valid Edubuntu CD
06-16 19:22 DEBUG  Distro:     does not contain C:\Users\sanjiv\AppData\Local\Temp\pyl5560.tmp\casper\filesystem.squashfs
06-16 19:22 DEBUG  Distro:   checking whether C:\Users\sanjiv\AppData\Local\Temp\pyl5560.tmp is a valid Lubuntu CD
06-16 19:22 DEBUG  Distro:     does not contain C:\Users\sanjiv\AppData\Local\Temp\pyl5560.tmp\casper\filesystem.squashfs
06-16 19:22 DEBUG  Distro:   checking whether C:\Users\sanjiv\AppData\Local\Temp\pyl5560.tmp is a valid Lubuntu CD
06-16 19:22 DEBUG  Distro:     does not contain C:\Users\sanjiv\AppData\Local\Temp\pyl5560.tmp\casper\filesystem.squashfs
06-16 19:22 DEBUG  Distro:   checking whether C:\Users\sanjiv\AppData\Local\Temp\pyl5560.tmp is a valid Ubuntu Studio CD
06-16 19:22 DEBUG  Distro:     does not contain C:\Users\sanjiv\AppData\Local\Temp\pyl5560.tmp\casper\filesystem.squashfs
06-16 19:22 DEBUG  Distro:   checking whether C:\Users\sanjiv\AppData\Local\Temp\pyl5560.tmp is a valid Ubuntu Studio CD
06-16 19:22 DEBUG  Distro:     does not contain C:\Users\sanjiv\AppData\Local\Temp\pyl5560.tmp\casper\filesystem.squashfs
06-16 19:22 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
06-16 19:22 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-16 19:22 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
06-16 19:22 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-16 19:22 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
06-16 19:22 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-16 19:22 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
06-16 19:22 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-16 19:22 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
06-16 19:22 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-16 19:22 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
06-16 19:22 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-16 19:22 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
06-16 19:22 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-16 19:22 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
06-16 19:22 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-16 19:22 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
06-16 19:22 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-16 19:22 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
06-16 19:22 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-16 19:22 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Studio CD
06-16 19:22 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-16 19:22 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Studio CD
06-16 19:22 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-16 19:22 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
06-16 19:22 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-16 19:22 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
06-16 19:22 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-16 19:22 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
06-16 19:22 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-16 19:22 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
06-16 19:22 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-16 19:22 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
06-16 19:22 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-16 19:22 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
06-16 19:22 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-16 19:22 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
06-16 19:22 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-16 19:22 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
06-16 19:22 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-16 19:22 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
06-16 19:22 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-16 19:22 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
06-16 19:22 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-16 19:22 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Studio CD
06-16 19:22 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-16 19:22 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Studio CD
06-16 19:22 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-16 19:22 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
06-16 19:22 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
06-16 19:22 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
06-16 19:22 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
06-16 19:22 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
06-16 19:22 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
06-16 19:22 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
06-16 19:22 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
06-16 19:22 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
06-16 19:22 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
06-16 19:22 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
06-16 19:22 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
06-16 19:22 DEBUG  Distro:   checking whether F:\ is a valid Edubuntu CD
06-16 19:22 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
06-16 19:22 DEBUG  Distro:   checking whether F:\ is a valid Edubuntu CD
06-16 19:22 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
06-16 19:22 DEBUG  Distro:   checking whether F:\ is a valid Lubuntu CD
06-16 19:22 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
06-16 19:22 DEBUG  Distro:   checking whether F:\ is a valid Lubuntu CD
06-16 19:22 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
06-16 19:22 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu Studio CD
06-16 19:22 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
06-16 19:22 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu Studio CD
06-16 19:22 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
06-16 19:22 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
06-16 19:22 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
06-16 19:22 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
06-16 19:22 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
06-16 19:22 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
06-16 19:22 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
06-16 19:22 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
06-16 19:22 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
06-16 19:22 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
06-16 19:22 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
06-16 19:22 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
06-16 19:22 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
06-16 19:22 DEBUG  Distro:   checking whether G:\ is a valid Edubuntu CD
06-16 19:22 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
06-16 19:22 DEBUG  Distro:   checking whether G:\ is a valid Edubuntu CD
06-16 19:22 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
06-16 19:22 DEBUG  Distro:   checking whether G:\ is a valid Lubuntu CD
06-16 19:22 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
06-16 19:22 DEBUG  Distro:   checking whether G:\ is a valid Lubuntu CD
06-16 19:22 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
06-16 19:22 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu Studio CD
06-16 19:22 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
06-16 19:22 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu Studio CD
06-16 19:22 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
06-16 19:22 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
06-16 19:22 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
06-16 19:22 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
06-16 19:22 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
06-16 19:22 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
06-16 19:22 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
06-16 19:22 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
06-16 19:22 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
06-16 19:22 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
06-16 19:22 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
06-16 19:22 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
06-16 19:22 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
06-16 19:22 DEBUG  Distro:   checking whether H:\ is a valid Edubuntu CD
06-16 19:22 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
06-16 19:22 DEBUG  Distro:   checking whether H:\ is a valid Edubuntu CD
06-16 19:22 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
06-16 19:22 DEBUG  Distro:   checking whether H:\ is a valid Lubuntu CD
06-16 19:22 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
06-16 19:22 DEBUG  Distro:   checking whether H:\ is a valid Lubuntu CD
06-16 19:22 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
06-16 19:22 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu Studio CD
06-16 19:22 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
06-16 19:22 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu Studio CD
06-16 19:22 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
06-16 19:22 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
06-16 19:22 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
06-16 19:22 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
06-16 19:22 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
06-16 19:22 DEBUG  Distro:   checking whether I:\ is a valid Kubuntu CD
06-16 19:22 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
06-16 19:22 DEBUG  Distro:   checking whether I:\ is a valid Kubuntu CD
06-16 19:22 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
06-16 19:22 DEBUG  Distro:   checking whether I:\ is a valid Mythbuntu CD
06-16 19:22 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
06-16 19:22 DEBUG  Distro:   checking whether I:\ is a valid Mythbuntu CD
06-16 19:22 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
06-16 19:22 DEBUG  Distro:   checking whether I:\ is a valid Edubuntu CD
06-16 19:22 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
06-16 19:22 DEBUG  Distro:   checking whether I:\ is a valid Edubuntu CD
06-16 19:22 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
06-16 19:22 DEBUG  Distro:   checking whether I:\ is a valid Lubuntu CD
06-16 19:22 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
06-16 19:22 DEBUG  Distro:   checking whether I:\ is a valid Lubuntu CD
06-16 19:22 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
06-16 19:22 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu Studio CD
06-16 19:22 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
06-16 19:22 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu Studio CD
06-16 19:22 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
06-16 19:22 DEBUG  Distro:   checking whether J:\ is a valid Ubuntu CD
06-16 19:22 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
06-16 19:22 DEBUG  Distro:   checking whether J:\ is a valid Ubuntu CD
06-16 19:22 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
06-16 19:22 DEBUG  Distro:   checking whether J:\ is a valid Kubuntu CD
06-16 19:22 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
06-16 19:22 DEBUG  Distro:   checking whether J:\ is a valid Kubuntu CD
06-16 19:22 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
06-16 19:22 DEBUG  Distro:   checking whether J:\ is a valid Mythbuntu CD
06-16 19:22 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
06-16 19:22 DEBUG  Distro:   checking whether J:\ is a valid Mythbuntu CD
06-16 19:22 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
06-16 19:22 DEBUG  Distro:   checking whether J:\ is a valid Edubuntu CD
06-16 19:22 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
06-16 19:22 DEBUG  Distro:   checking whether J:\ is a valid Edubuntu CD
06-16 19:22 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
06-16 19:22 DEBUG  Distro:   checking whether J:\ is a valid Lubuntu CD
06-16 19:22 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
06-16 19:22 DEBUG  Distro:   checking whether J:\ is a valid Lubuntu CD
06-16 19:22 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
06-16 19:22 DEBUG  Distro:   checking whether J:\ is a valid Ubuntu Studio CD
06-16 19:22 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
06-16 19:22 DEBUG  Distro:   checking whether J:\ is a valid Ubuntu Studio CD
06-16 19:22 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
06-16 19:22 DEBUG  Distro:   checking whether K:\ is a valid Ubuntu CD
06-16 19:22 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
06-16 19:22 DEBUG  Distro:   checking whether K:\ is a valid Ubuntu CD
06-16 19:22 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
06-16 19:22 DEBUG  Distro:   checking whether K:\ is a valid Kubuntu CD
06-16 19:22 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
06-16 19:22 DEBUG  Distro:   checking whether K:\ is a valid Kubuntu CD
06-16 19:22 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
06-16 19:22 DEBUG  Distro:   checking whether K:\ is a valid Mythbuntu CD
06-16 19:22 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
06-16 19:22 DEBUG  Distro:   checking whether K:\ is a valid Mythbuntu CD
06-16 19:22 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
06-16 19:22 DEBUG  Distro:   checking whether K:\ is a valid Edubuntu CD
06-16 19:22 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
06-16 19:22 DEBUG  Distro:   checking whether K:\ is a valid Edubuntu CD
06-16 19:22 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
06-16 19:22 DEBUG  Distro:   checking whether K:\ is a valid Lubuntu CD
06-16 19:22 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
06-16 19:22 DEBUG  Distro:   checking whether K:\ is a valid Lubuntu CD
06-16 19:22 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
06-16 19:22 DEBUG  Distro:   checking whether K:\ is a valid Ubuntu Studio CD
06-16 19:22 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
06-16 19:22 DEBUG  Distro:   checking whether K:\ is a valid Ubuntu Studio CD
06-16 19:22 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
06-16 19:22 DEBUG  Distro:   checking whether L:\ is a valid Ubuntu CD
06-16 19:22 DEBUG  Distro:     does not contain L:\casper\filesystem.squashfs
06-16 19:22 DEBUG  Distro:   checking whether L:\ is a valid Ubuntu CD
06-16 19:22 DEBUG  Distro:     does not contain L:\casper\filesystem.squashfs
06-16 19:22 DEBUG  Distro:   checking whether L:\ is a valid Kubuntu CD
06-16 19:22 DEBUG  Distro:     does not contain L:\casper\filesystem.squashfs
06-16 19:22 DEBUG  Distro:   checking whether L:\ is a valid Kubuntu CD
06-16 19:22 DEBUG  Distro:     does not contain L:\casper\filesystem.squashfs
06-16 19:22 DEBUG  Distro:   checking whether L:\ is a valid Mythbuntu CD
06-16 19:22 DEBUG  Distro:     does not contain L:\casper\filesystem.squashfs
06-16 19:22 DEBUG  Distro:   checking whether L:\ is a valid Mythbuntu CD
06-16 19:22 DEBUG  Distro:     does not contain L:\casper\filesystem.squashfs
06-16 19:22 DEBUG  Distro:   checking whether L:\ is a valid Edubuntu CD
06-16 19:22 DEBUG  Distro:     does not contain L:\casper\filesystem.squashfs
06-16 19:22 DEBUG  Distro:   checking whether L:\ is a valid Edubuntu CD
06-16 19:22 DEBUG  Distro:     does not contain L:\casper\filesystem.squashfs
06-16 19:22 DEBUG  Distro:   checking whether L:\ is a valid Lubuntu CD
06-16 19:22 DEBUG  Distro:     does not contain L:\casper\filesystem.squashfs
06-16 19:22 DEBUG  Distro:   checking whether L:\ is a valid Lubuntu CD
06-16 19:22 DEBUG  Distro:     does not contain L:\casper\filesystem.squashfs
06-16 19:22 DEBUG  Distro:   checking whether L:\ is a valid Ubuntu Studio CD
06-16 19:22 DEBUG  Distro:     does not contain L:\casper\filesystem.squashfs
06-16 19:22 DEBUG  Distro:   checking whether L:\ is a valid Ubuntu Studio CD
06-16 19:22 DEBUG  Distro:     does not contain L:\casper\filesystem.squashfs
06-16 19:22 DEBUG  Distro:   checking whether M:\ is a valid Ubuntu CD
06-16 19:22 DEBUG  Distro:     does not contain M:\casper\vmlinuz.efi
06-16 19:22 DEBUG  Distro:   checking whether M:\ is a valid Ubuntu CD
06-16 19:22 DEBUG  Distro:   parsing info from str=Ubuntu 13.04 "Raring Ringtail" - Release i386 (20130424)
06-16 19:22 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '13.04', 'build': '20130424', 'codename': 'Raring Ringtail', 'arch': 'i386'}
06-16 19:22 INFO   Distro: Found a valid CD for Ubuntu: M:\
06-16 19:22 INFO   root: Running the installer...
06-16 19:22 DEBUG  WindowsFrontend: __init__...
06-16 19:22 DEBUG  WindowsFrontend: on_init...
06-16 19:22 INFO   WinuiPage: appname=wubi, localedir=C:\Users\sanjiv\AppData\Local\Temp\pyl5560.tmp\translations, languages=['en_US', 'en']
06-16 19:22 INFO   WinuiPage: appname=wubi, localedir=C:\Users\sanjiv\AppData\Local\Temp\pyl5560.tmp\translations, languages=['en_US', 'en']
06-16 19:22 DEBUG  WindowsFrontend: frontend.on_quit
06-16 19:22 DEBUG  root: application.on_quit
06-16 19:22 INFO   root: sys.exit
06-16 19:54 INFO   root: === wubi 13.04 rev279 ===
06-16 19:54 DEBUG  root: Logfile is c:\users\sanjiv\appdata\local\temp\wubi-13.04-rev279.log
06-16 19:54 DEBUG  root: sys.argv = ['main.pyo', '--exefile="N:\\Ubuntu 13\\New folder\\wubi.exe"']
06-16 19:54 DEBUG  CommonBackend: data_dir=C:\Users\sanjiv\AppData\Local\Temp\pyl1D8E.tmp\data
06-16 19:54 DEBUG  WindowsBackend: 7z=C:\Users\sanjiv\AppData\Local\Temp\pyl1D8E.tmp\bin\7z.exe
06-16 19:54 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
06-16 19:54 DEBUG  CommonBackend: Fetching basic info...
06-16 19:54 DEBUG  CommonBackend: original_exe=N:\Ubuntu 13\New folder\wubi.exe
06-16 19:54 DEBUG  CommonBackend: platform=win32
06-16 19:54 DEBUG  CommonBackend: osname=nt
06-16 19:54 DEBUG  CommonBackend: language=en_US
06-16 19:54 DEBUG  CommonBackend: encoding=cp1252
06-16 19:54 DEBUG  WindowsBackend: arch=amd64
06-16 19:54 DEBUG  CommonBackend: Parsing isolist=C:\Users\sanjiv\AppData\Local\Temp\pyl1D8E.tmp\data\isolist.ini
06-16 19:54 DEBUG  CommonBackend:   Adding distro Edubuntu-i386
06-16 19:54 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
06-16 19:54 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
06-16 19:54 DEBUG  CommonBackend:   Adding distro Edubuntu-amd64
06-16 19:54 DEBUG  CommonBackend:   Adding distro Ubuntu Studio-amd64
06-16 19:54 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
06-16 19:54 DEBUG  CommonBackend:   Adding distro Lubuntu-i386
06-16 19:54 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
06-16 19:54 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
06-16 19:54 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
06-16 19:54 DEBUG  CommonBackend:   Adding distro Ubuntu Studio-i386
06-16 19:54 DEBUG  CommonBackend:   Adding distro Lubuntu-amd64
06-16 19:54 DEBUG  WindowsBackend: Fetching host info...
06-16 19:54 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
06-16 19:54 DEBUG  WindowsBackend: windows version=vista
06-16 19:54 DEBUG  WindowsBackend: windows_version2=Windows 8 Pro with Media Center
06-16 19:54 DEBUG  WindowsBackend: windows_sp=None
06-16 19:54 DEBUG  WindowsBackend: windows_build=9200
06-16 19:54 DEBUG  WindowsBackend: gmt=5
06-16 19:54 DEBUG  WindowsBackend: country=US
06-16 19:54 DEBUG  WindowsBackend: timezone=America/New_York
06-16 19:54 DEBUG  WindowsBackend: windows_username=sanjiv
06-16 19:54 DEBUG  WindowsBackend: user_full_name=sanjiv
06-16 19:54 DEBUG  WindowsBackend: user_directory=C:\Users\sanjiv
06-16 19:54 DEBUG  WindowsBackend: windows_language_code=1033
06-16 19:54 DEBUG  WindowsBackend: windows_language=English
06-16 19:54 DEBUG  WindowsBackend: processor_name=Intel(R) Pentium(R) D CPU 2.80GHz
06-16 19:54 DEBUG  WindowsBackend: bootloader=vista
06-16 19:54 DEBUG  WindowsBackend: system_drive=Drive(C: hd 1806.9140625 mb free ntfs)
06-16 19:54 DEBUG  WindowsBackend: drive=Drive(C: hd 1806.9140625 mb free ntfs)
06-16 19:54 DEBUG  WindowsBackend: drive=Drive(D: cd 0.0 mb free )
06-16 19:54 DEBUG  WindowsBackend: drive=Drive(E: hd 39903.8085938 mb free ntfs)
06-16 19:54 DEBUG  WindowsBackend: drive=Drive(G: hd 15494.1054688 mb free ntfs)
06-16 19:54 DEBUG  WindowsBackend: drive=Drive(H: hd 29896.421875 mb free ntfs)
06-16 19:54 DEBUG  WindowsBackend: drive=Drive(I: hd 39899.828125 mb free ntfs)
06-16 19:54 DEBUG  WindowsBackend: drive=Drive(J: hd 1354.125 mb free ntfs)
06-16 19:54 DEBUG  WindowsBackend: drive=Drive(K: hd 27218.09375 mb free ntfs)
06-16 19:54 DEBUG  WindowsBackend: drive=Drive(L: hd 7012.5625 mb free ntfs)
06-16 19:54 DEBUG  WindowsBackend: drive=Drive(N: removable 2100.19921875 mb free fat32)
06-16 19:54 DEBUG  WindowsBackend: uninstaller_path=E:\ubuntu\uninstall-wubi.exe
06-16 19:54 DEBUG  WindowsBackend: previous_target_dir=E:\ubuntu
06-16 19:54 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
06-16 19:54 DEBUG  WindowsBackend: keyboard_id=134809609
06-16 19:54 DEBUG  WindowsBackend: keyboard_layout=gb
06-16 19:54 DEBUG  WindowsBackend: keyboard_variant=
06-16 19:54 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
06-16 19:54 DEBUG  CommonBackend: locale=en_US.UTF-8
06-16 19:54 DEBUG  WindowsBackend: total_memory_mb=2047.99999905
06-16 19:54 DEBUG  CommonBackend: Searching ISOs on USB devices
06-16 19:54 DEBUG  CommonBackend: Searching for local CDs
06-16 19:54 DEBUG  Distro:   checking whether C:\Users\sanjiv\AppData\Local\Temp\pyl1D8E.tmp is a valid Ubuntu CD
06-16 19:54 DEBUG  Distro:     does not contain C:\Users\sanjiv\AppData\Local\Temp\pyl1D8E.tmp\casper\filesystem.squashfs
06-16 19:54 DEBUG  Distro:   checking whether C:\Users\sanjiv\AppData\Local\Temp\pyl1D8E.tmp is a valid Ubuntu CD
06-16 19:54 DEBUG  Distro:     does not contain C:\Users\sanjiv\AppData\Local\Temp\pyl1D8E.tmp\casper\filesystem.squashfs
06-16 19:54 DEBUG  Distro:   checking whether C:\Users\sanjiv\AppData\Local\Temp\pyl1D8E.tmp is a valid Kubuntu CD
06-16 19:54 DEBUG  Distro:     does not contain C:\Users\sanjiv\AppData\Local\Temp\pyl1D8E.tmp\casper\filesystem.squashfs
06-16 19:54 DEBUG  Distro:   checking whether C:\Users\sanjiv\AppData\Local\Temp\pyl1D8E.tmp is a valid Kubuntu CD
06-16 19:54 DEBUG  Distro:     does not contain C:\Users\sanjiv\AppData\Local\Temp\pyl1D8E.tmp\casper\filesystem.squashfs
06-16 19:54 DEBUG  Distro:   checking whether C:\Users\sanjiv\AppData\Local\Temp\pyl1D8E.tmp is a valid Mythbuntu CD
06-16 19:54 DEBUG  Distro:     does not contain C:\Users\sanjiv\AppData\Local\Temp\pyl1D8E.tmp\casper\filesystem.squashfs
06-16 19:54 DEBUG  Distro:   checking whether C:\Users\sanjiv\AppData\Local\Temp\pyl1D8E.tmp is a valid Mythbuntu CD
06-16 19:54 DEBUG  Distro:     does not contain C:\Users\sanjiv\AppData\Local\Temp\pyl1D8E.tmp\casper\filesystem.squashfs
06-16 19:54 DEBUG  Distro:   checking whether C:\Users\sanjiv\AppData\Local\Temp\pyl1D8E.tmp is a valid Edubuntu CD
06-16 19:54 DEBUG  Distro:     does not contain C:\Users\sanjiv\AppData\Local\Temp\pyl1D8E.tmp\casper\filesystem.squashfs
06-16 19:54 DEBUG  Distro:   checking whether C:\Users\sanjiv\AppData\Local\Temp\pyl1D8E.tmp is a valid Edubuntu CD
06-16 19:54 DEBUG  Distro:     does not contain C:\Users\sanjiv\AppData\Local\Temp\pyl1D8E.tmp\casper\filesystem.squashfs
06-16 19:54 DEBUG  Distro:   checking whether C:\Users\sanjiv\AppData\Local\Temp\pyl1D8E.tmp is a valid Lubuntu CD
06-16 19:54 DEBUG  Distro:     does not contain C:\Users\sanjiv\AppData\Local\Temp\pyl1D8E.tmp\casper\filesystem.squashfs
06-16 19:54 DEBUG  Distro:   checking whether C:\Users\sanjiv\AppData\Local\Temp\pyl1D8E.tmp is a valid Lubuntu CD
06-16 19:54 DEBUG  Distro:     does not contain C:\Users\sanjiv\AppData\Local\Temp\pyl1D8E.tmp\casper\filesystem.squashfs
06-16 19:54 DEBUG  Distro:   checking whether C:\Users\sanjiv\AppData\Local\Temp\pyl1D8E.tmp is a valid Ubuntu Studio CD
06-16 19:54 DEBUG  Distro:     does not contain C:\Users\sanjiv\AppData\Local\Temp\pyl1D8E.tmp\casper\filesystem.squashfs
06-16 19:54 DEBUG  Distro:   checking whether C:\Users\sanjiv\AppData\Local\Temp\pyl1D8E.tmp is a valid Ubuntu Studio CD
06-16 19:54 DEBUG  Distro:     does not contain C:\Users\sanjiv\AppData\Local\Temp\pyl1D8E.tmp\casper\filesystem.squashfs
06-16 19:54 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
06-16 19:54 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-16 19:54 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
06-16 19:54 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-16 19:54 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
06-16 19:54 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-16 19:54 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
06-16 19:54 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-16 19:54 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
06-16 19:54 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-16 19:54 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
06-16 19:54 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-16 19:54 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
06-16 19:54 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-16 19:54 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
06-16 19:54 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-16 19:54 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
06-16 19:54 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-16 19:54 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
06-16 19:54 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-16 19:54 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Studio CD
06-16 19:54 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-16 19:54 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Studio CD
06-16 19:54 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-16 19:54 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
06-16 19:54 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-16 19:54 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
06-16 19:54 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-16 19:54 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
06-16 19:54 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-16 19:54 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
06-16 19:54 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-16 19:54 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
06-16 19:54 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-16 19:54 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
06-16 19:54 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-16 19:54 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
06-16 19:54 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-16 19:54 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
06-16 19:54 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-16 19:54 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
06-16 19:54 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-16 19:54 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
06-16 19:54 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-16 19:54 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Studio CD
06-16 19:54 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-16 19:54 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Studio CD
06-16 19:54 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-16 19:54 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
06-16 19:54 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
06-16 19:54 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
06-16 19:54 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
06-16 19:54 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
06-16 19:54 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
06-16 19:54 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
06-16 19:54 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
06-16 19:54 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
06-16 19:54 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
06-16 19:54 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
06-16 19:54 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
06-16 19:54 DEBUG  Distro:   checking whether G:\ is a valid Edubuntu CD
06-16 19:54 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
06-16 19:54 DEBUG  Distro:   checking whether G:\ is a valid Edubuntu CD
06-16 19:54 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
06-16 19:54 DEBUG  Distro:   checking whether G:\ is a valid Lubuntu CD
06-16 19:54 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
06-16 19:54 DEBUG  Distro:   checking whether G:\ is a valid Lubuntu CD
06-16 19:54 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
06-16 19:54 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu Studio CD
06-16 19:54 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
06-16 19:54 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu Studio CD
06-16 19:54 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
06-16 19:54 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
06-16 19:54 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
06-16 19:54 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
06-16 19:54 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
06-16 19:54 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
06-16 19:54 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
06-16 19:54 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
06-16 19:54 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
06-16 19:54 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
06-16 19:54 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
06-16 19:54 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
06-16 19:54 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
06-16 19:54 DEBUG  Distro:   checking whether H:\ is a valid Edubuntu CD
06-16 19:54 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
06-16 19:54 DEBUG  Distro:   checking whether H:\ is a valid Edubuntu CD
06-16 19:54 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
06-16 19:54 DEBUG  Distro:   checking whether H:\ is a valid Lubuntu CD
06-16 19:54 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
06-16 19:54 DEBUG  Distro:   checking whether H:\ is a valid Lubuntu CD
06-16 19:54 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
06-16 19:54 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu Studio CD
06-16 19:54 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
06-16 19:54 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu Studio CD
06-16 19:54 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
06-16 19:54 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
06-16 19:54 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
06-16 19:54 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
06-16 19:54 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
06-16 19:54 DEBUG  Distro:   checking whether I:\ is a valid Kubuntu CD
06-16 19:54 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
06-16 19:54 DEBUG  Distro:   checking whether I:\ is a valid Kubuntu CD
06-16 19:54 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
06-16 19:54 DEBUG  Distro:   checking whether I:\ is a valid Mythbuntu CD
06-16 19:54 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
06-16 19:54 DEBUG  Distro:   checking whether I:\ is a valid Mythbuntu CD
06-16 19:54 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
06-16 19:54 DEBUG  Distro:   checking whether I:\ is a valid Edubuntu CD
06-16 19:54 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
06-16 19:54 DEBUG  Distro:   checking whether I:\ is a valid Edubuntu CD
06-16 19:54 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
06-16 19:54 DEBUG  Distro:   checking whether I:\ is a valid Lubuntu CD
06-16 19:54 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
06-16 19:54 DEBUG  Distro:   checking whether I:\ is a valid Lubuntu CD
06-16 19:54 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
06-16 19:54 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu Studio CD
06-16 19:54 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
06-16 19:54 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu Studio CD
06-16 19:54 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
06-16 19:54 DEBUG  Distro:   checking whether J:\ is a valid Ubuntu CD
06-16 19:54 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
06-16 19:54 DEBUG  Distro:   checking whether J:\ is a valid Ubuntu CD
06-16 19:54 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
06-16 19:54 DEBUG  Distro:   checking whether J:\ is a valid Kubuntu CD
06-16 19:54 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
06-16 19:54 DEBUG  Distro:   checking whether J:\ is a valid Kubuntu CD
06-16 19:54 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
06-16 19:54 DEBUG  Distro:   checking whether J:\ is a valid Mythbuntu CD
06-16 19:54 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
06-16 19:54 DEBUG  Distro:   checking whether J:\ is a valid Mythbuntu CD
06-16 19:54 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
06-16 19:54 DEBUG  Distro:   checking whether J:\ is a valid Edubuntu CD
06-16 19:54 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
06-16 19:54 DEBUG  Distro:   checking whether J:\ is a valid Edubuntu CD
06-16 19:54 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
06-16 19:54 DEBUG  Distro:   checking whether J:\ is a valid Lubuntu CD
06-16 19:54 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
06-16 19:54 DEBUG  Distro:   checking whether J:\ is a valid Lubuntu CD
06-16 19:54 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
06-16 19:54 DEBUG  Distro:   checking whether J:\ is a valid Ubuntu Studio CD
06-16 19:54 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
06-16 19:54 DEBUG  Distro:   checking whether J:\ is a valid Ubuntu Studio CD
06-16 19:54 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
06-16 19:54 DEBUG  Distro:   checking whether K:\ is a valid Ubuntu CD
06-16 19:54 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
06-16 19:54 DEBUG  Distro:   checking whether K:\ is a valid Ubuntu CD
06-16 19:54 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
06-16 19:54 DEBUG  Distro:   checking whether K:\ is a valid Kubuntu CD
06-16 19:54 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
06-16 19:54 DEBUG  Distro:   checking whether K:\ is a valid Kubuntu CD
06-16 19:54 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
06-16 19:54 DEBUG  Distro:   checking whether K:\ is a valid Mythbuntu CD
06-16 19:54 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
06-16 19:54 DEBUG  Distro:   checking whether K:\ is a valid Mythbuntu CD
06-16 19:54 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
06-16 19:54 DEBUG  Distro:   checking whether K:\ is a valid Edubuntu CD
06-16 19:54 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
06-16 19:54 DEBUG  Distro:   checking whether K:\ is a valid Edubuntu CD
06-16 19:54 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
06-16 19:54 DEBUG  Distro:   checking whether K:\ is a valid Lubuntu CD
06-16 19:54 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
06-16 19:54 DEBUG  Distro:   checking whether K:\ is a valid Lubuntu CD
06-16 19:54 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
06-16 19:54 DEBUG  Distro:   checking whether K:\ is a valid Ubuntu Studio CD
06-16 19:54 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
06-16 19:54 DEBUG  Distro:   checking whether K:\ is a valid Ubuntu Studio CD
06-16 19:54 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
06-16 19:54 DEBUG  Distro:   checking whether L:\ is a valid Ubuntu CD
06-16 19:54 DEBUG  Distro:     does not contain L:\casper\filesystem.squashfs
06-16 19:54 DEBUG  Distro:   checking whether L:\ is a valid Ubuntu CD
06-16 19:54 DEBUG  Distro:     does not contain L:\casper\filesystem.squashfs
06-16 19:54 DEBUG  Distro:   checking whether L:\ is a valid Kubuntu CD
06-16 19:54 DEBUG  Distro:     does not contain L:\casper\filesystem.squashfs
06-16 19:54 DEBUG  Distro:   checking whether L:\ is a valid Kubuntu CD
06-16 19:54 DEBUG  Distro:     does not contain L:\casper\filesystem.squashfs
06-16 19:54 DEBUG  Distro:   checking whether L:\ is a valid Mythbuntu CD
06-16 19:54 DEBUG  Distro:     does not contain L:\casper\filesystem.squashfs
06-16 19:54 DEBUG  Distro:   checking whether L:\ is a valid Mythbuntu CD
06-16 19:54 DEBUG  Distro:     does not contain L:\casper\filesystem.squashfs
06-16 19:54 DEBUG  Distro:   checking whether L:\ is a valid Edubuntu CD
06-16 19:54 DEBUG  Distro:     does not contain L:\casper\filesystem.squashfs
06-16 19:54 DEBUG  Distro:   checking whether L:\ is a valid Edubuntu CD
06-16 19:54 DEBUG  Distro:     does not contain L:\casper\filesystem.squashfs
06-16 19:54 DEBUG  Distro:   checking whether L:\ is a valid Lubuntu CD
06-16 19:54 DEBUG  Distro:     does not contain L:\casper\filesystem.squashfs
06-16 19:54 DEBUG  Distro:   checking whether L:\ is a valid Lubuntu CD
06-16 19:54 DEBUG  Distro:     does not contain L:\casper\filesystem.squashfs
06-16 19:54 DEBUG  Distro:   checking whether L:\ is a valid Ubuntu Studio CD
06-16 19:54 DEBUG  Distro:     does not contain L:\casper\filesystem.squashfs
06-16 19:54 DEBUG  Distro:   checking whether L:\ is a valid Ubuntu Studio CD
06-16 19:54 DEBUG  Distro:     does not contain L:\casper\filesystem.squashfs
06-16 19:54 DEBUG  Distro:   checking whether N:\ is a valid Ubuntu CD
06-16 19:54 DEBUG  Distro:     does not contain N:\casper\filesystem.squashfs
06-16 19:54 DEBUG  Distro:   checking whether N:\ is a valid Ubuntu CD
06-16 19:54 DEBUG  Distro:     does not contain N:\casper\filesystem.squashfs
06-16 19:54 DEBUG  Distro:   checking whether N:\ is a valid Kubuntu CD
06-16 19:54 DEBUG  Distro:     does not contain N:\casper\filesystem.squashfs
06-16 19:54 DEBUG  Distro:   checking whether N:\ is a valid Kubuntu CD
06-16 19:54 DEBUG  Distro:     does not contain N:\casper\filesystem.squashfs
06-16 19:54 DEBUG  Distro:   checking whether N:\ is a valid Mythbuntu CD
06-16 19:54 DEBUG  Distro:     does not contain N:\casper\filesystem.squashfs
06-16 19:54 DEBUG  Distro:   checking whether N:\ is a valid Mythbuntu CD
06-16 19:54 DEBUG  Distro:     does not contain N:\casper\filesystem.squashfs
06-16 19:54 DEBUG  Distro:   checking whether N:\ is a valid Edubuntu CD
06-16 19:54 DEBUG  Distro:     does not contain N:\casper\filesystem.squashfs
06-16 19:54 DEBUG  Distro:   checking whether N:\ is a valid Edubuntu CD
06-16 19:54 DEBUG  Distro:     does not contain N:\casper\filesystem.squashfs
06-16 19:54 DEBUG  Distro:   checking whether N:\ is a valid Lubuntu CD
06-16 19:54 DEBUG  Distro:     does not contain N:\casper\filesystem.squashfs
06-16 19:54 DEBUG  Distro:   checking whether N:\ is a valid Lubuntu CD
06-16 19:54 DEBUG  Distro:     does not contain N:\casper\filesystem.squashfs
06-16 19:54 DEBUG  Distro:   checking whether N:\ is a valid Ubuntu Studio CD
06-16 19:54 DEBUG  Distro:     does not contain N:\casper\filesystem.squashfs
06-16 19:54 DEBUG  Distro:   checking whether N:\ is a valid Ubuntu Studio CD
06-16 19:54 DEBUG  Distro:     does not contain N:\casper\filesystem.squashfs
06-16 19:54 INFO   root: Running the installer...
06-16 19:54 DEBUG  WindowsFrontend: __init__...
06-16 19:54 DEBUG  WindowsFrontend: on_init...
06-16 19:54 INFO   WinuiPage: appname=wubi, localedir=C:\Users\sanjiv\AppData\Local\Temp\pyl1D8E.tmp\translations, languages=['en_US', 'en']
06-16 19:54 INFO   WinuiPage: appname=wubi, localedir=C:\Users\sanjiv\AppData\Local\Temp\pyl1D8E.tmp\translations, languages=['en_US', 'en']
06-16 19:55 DEBUG  WinuiInstallationPage: target_drive=E:, installation_size=18000MB, distro_name=Ubuntu, language=en_US, locale=en_US.UTF-8, username=sanjiv
06-16 19:55 INFO   root: Received settings
06-16 19:55 DEBUG  CommonBackend: Searching for local CD
06-16 19:55 DEBUG  Distro:   checking whether C:\Users\sanjiv\AppData\Local\Temp\pyl1D8E.tmp is a valid Ubuntu CD
06-16 19:55 DEBUG  Distro:     does not contain C:\Users\sanjiv\AppData\Local\Temp\pyl1D8E.tmp\casper\filesystem.squashfs
06-16 19:55 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
06-16 19:55 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-16 19:55 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
06-16 19:55 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-16 19:55 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
06-16 19:55 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
06-16 19:55 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
06-16 19:55 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
06-16 19:55 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
06-16 19:55 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
06-16 19:55 DEBUG  Distro:   checking whether J:\ is a valid Ubuntu CD
06-16 19:55 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
06-16 19:55 DEBUG  Distro:   checking whether K:\ is a valid Ubuntu CD
06-16 19:55 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
06-16 19:55 DEBUG  Distro:   checking whether L:\ is a valid Ubuntu CD
06-16 19:55 DEBUG  Distro:     does not contain L:\casper\filesystem.squashfs
06-16 19:55 DEBUG  Distro:   checking whether N:\ is a valid Ubuntu CD
06-16 19:55 DEBUG  Distro:     does not contain N:\casper\filesystem.squashfs
06-16 19:55 DEBUG  CommonBackend: Searching for local ISO
06-16 19:55 INFO   WinuiPage: appname=wubi, localedir=C:\Users\sanjiv\AppData\Local\Temp\pyl1D8E.tmp\translations, languages=['en_US', 'en']
06-16 19:55 DEBUG  TaskList: # Running tasklist...
06-16 19:55 DEBUG  TaskList: ## Running select_target_dir...
06-16 19:55 INFO   WindowsBackend: Installing into E:\ubuntu
06-16 19:55 DEBUG  TaskList: ## Finished select_target_dir
06-16 19:55 DEBUG  TaskList: ## Running create_dir_structure...
06-16 19:55 DEBUG  CommonBackend: Creating dir E:\ubuntu
06-16 19:55 DEBUG  CommonBackend: Creating dir E:\ubuntu\disks
06-16 19:55 DEBUG  CommonBackend: Creating dir E:\ubuntu\install
06-16 19:55 DEBUG  CommonBackend: Creating dir E:\ubuntu\install\boot
06-16 19:55 DEBUG  CommonBackend: Creating dir E:\ubuntu\disks\boot
06-16 19:55 DEBUG  CommonBackend: Creating dir E:\ubuntu\disks\boot\grub
06-16 19:55 DEBUG  CommonBackend: Creating dir E:\ubuntu\install\boot\grub
06-16 19:55 DEBUG  TaskList: ## Finished create_dir_structure
06-16 19:55 DEBUG  TaskList: ## Running uncompress_target_dir...
06-16 19:55 DEBUG  TaskList: ## Finished uncompress_target_dir
06-16 19:55 DEBUG  TaskList: ## Running create_uninstaller...
06-16 19:55 DEBUG  WindowsBackend: Copying uninstaller N:\Ubuntu 13\New folder\wubi.exe -> E:\ubuntu\uninstall-wubi.exe
06-16 19:55 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString E:\ubuntu\uninstall-wubi.exe
06-16 19:55 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir E:\ubuntu
06-16 19:55 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
06-16 19:55 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon E:\ubuntu\Ubuntu.ico
06-16 19:55 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 13.04-rev279
06-16 19:55 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
06-16 19:55 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com](http://www.ubuntu.com)
06-16 19:55 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
06-16 19:55 DEBUG  TaskList: ## Finished create_uninstaller
06-16 19:55 DEBUG  TaskList: ## Running copy_installation_files...
06-16 19:55 DEBUG  WindowsBackend: Copying C:\Users\sanjiv\AppData\Local\Temp\pyl1D8E.tmp\data\custom-installation -> E:\ubuntu\install\custom-installation
06-16 19:55 DEBUG  WindowsBackend: Copying C:\Users\sanjiv\AppData\Local\Temp\pyl1D8E.tmp\winboot -> E:\ubuntu\winboot
06-16 19:55 DEBUG  WindowsBackend: Copying C:\Users\sanjiv\AppData\Local\Temp\pyl1D8E.tmp\data\images\Ubuntu.ico -> E:\ubuntu\Ubuntu.ico
06-16 19:55 DEBUG  TaskList: ## Finished copy_installation_files
06-16 19:55 DEBUG  TaskList: ## Running get_iso...
06-16 19:55 DEBUG  CommonBackend: Could not find any ISO or CD, downloading one now
06-16 19:55 DEBUG  TaskList: New task get_metalink
06-16 19:55 DEBUG  TaskList: ### Running get_metalink...
06-16 19:55 DEBUG  downloader: downloading [http://releases.ubuntu.com/13.04/ubuntu-13.04-desktop-amd64.metalink](http://releases.ubuntu.com/13.04/ubuntu-13.04-desktop-amd64.metalink) > E:\ubuntu\install
06-16 19:55 DEBUG  downloader: Download start filename=E:\ubuntu\install\ubuntu-13.04-desktop-amd64.metalink, url=http://releases.ubuntu.com/13.04/ubuntu-13.04-desktop-amd64.metalink, basename=ubuntu-13.04-desktop-amd64.metalink, length=36499, text=None
06-16 19:55 DEBUG  downloader: download finished (read 36499 bytes)
06-16 19:55 DEBUG  downloader: downloading [http://releases.ubuntu.com/13.04/MD5SUMS-metalink](http://releases.ubuntu.com/13.04/MD5SUMS-metalink) > E:\ubuntu\install
06-16 19:55 DEBUG  downloader: Download start filename=E:\ubuntu\install\MD5SUMS-metalink, url=http://releases.ubuntu.com/13.04/MD5SUMS-metalink, basename=MD5SUMS-metalink, length=498, text=None
06-16 19:55 DEBUG  downloader: download finished (read 498 bytes)
06-16 19:55 DEBUG  downloader: downloading [http://releases.ubuntu.com/13.04/MD5SUMS-metalink.gpg](http://releases.ubuntu.com/13.04/MD5SUMS-metalink.gpg) > E:\ubuntu\install
06-16 19:55 DEBUG  downloader: Download start filename=E:\ubuntu\install\MD5SUMS-metalink.gpg, url=http://releases.ubuntu.com/13.04/MD5SUMS-metalink.gpg, basename=MD5SUMS-metalink.gpg, length=198, text=None
06-16 19:55 DEBUG  downloader: download finished (read 198 bytes)
06-16 19:55 INFO   saplog: Verified a signature from ID:'46181433FBB75451'.
06-16 19:55 INFO   saplog: Checking block bindings..
06-16 19:55 INFO   saplog: Key verified successfully.
06-16 19:55 DEBUG  CommonBackend: metalink md5sums:
e578445ee73cc1641834fca2542a90ba *ubuntu-13.04-desktop-amd64+mac.metalink
6b2e76fe8853d019d66c34fb0bbaa574 *ubuntu-13.04-desktop-amd64.metalink
02c9c64dcd3359d5224612ed8097adcf *ubuntu-13.04-desktop-i386.metalink
eff9dda8b3a9d69c88f6703729d50174 *ubuntu-13.04-server-amd64+mac.metalink
afafb246cd2ef1ab04803cac3ec554ac *ubuntu-13.04-server-amd64.metalink
98f94e110e069b936fa5ed229136464b *ubuntu-13.04-server-armhf+omap4.metalink
9d09bf70b2a640e12ee8e510d64a553e *ubuntu-13.04-server-i386.metalink

06-16 19:55 ERROR  CommonBackend: The md5 of the metalink does match
06-16 19:55 ERROR  CommonBackend: Cannot authenticate the metalink file, it might be corrupt
None
06-16 19:55 DEBUG  TaskList: ### Finished get_metalink
06-16 19:55 DEBUG  TaskList: New task download
06-16 19:55 DEBUG  TaskList: ### Running download...
06-16 19:55 DEBUG  btdownloader: downloading [http://releases.ubuntu.com/13.04/ubuntu-13.04-desktop-amd64.iso.torrent](http://releases.ubuntu.com/13.04/ubuntu-13.04-desktop-amd64.iso.torrent) > E:\ubuntu\install\ubuntu-13.04-desktop-amd64.iso
06-16 21:50 ERROR  TaskList: Traceback (most recent call last):
  File "\lib\bittorrent\RawServer.py", line 229, in listen_forever
  File "\lib\wubi\backends\common\btdownloader.py", line 69, in error_callback
DownloadError: Traceback (most recent call last):
  File "\lib\bittorrent\RawServer.py", line 221, in listen_forever
  File "\lib\bittorrent\Rerequester.py", line 96, in fail
  File "\lib\wubi\backends\common\btdownloader.py", line 69, in error_callback
DownloadError: Problem connecting to tracker - <urlopen error (2, 'getaddrinfo failed')>

Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\btdownloader.py", line 78, in download
  File "\lib\bittorrent\download.py", line 303, in download
  File "\lib\bittorrent\RawServer.py", line 256, in listen_forever
  File "\lib\wubi\backends\common\btdownloader.py", line 69, in error_callback
DownloadError: Traceback (most recent call last):
  File "\lib\bittorrent\RawServer.py", line 229, in listen_forever
  File "\lib\wubi\backends\common\btdownloader.py", line 69, in error_callback
DownloadError: Traceback (most recent call last):
  File "\lib\bittorrent\RawServer.py", line 221, in listen_forever
  File "\lib\bittorrent\Rerequester.py", line 96, in fail
  File "\lib\wubi\backends\common\btdownloader.py", line 69, in error_callback
DownloadError: Problem connecting to tracker - <urlopen error (2, 'getaddrinfo failed')>


06-16 21:50 ERROR  TaskList: Non fatal error Traceback (most recent call last):
  File "\lib\bittorrent\RawServer.py", line 229, in listen_forever
  File "\lib\wubi\backends\common\btdownloader.py", line 69, in error_callback
DownloadError: Traceback (most recent call last):
  File "\lib\bittorrent\RawServer.py", line 221, in listen_forever
  File "\lib\bittorrent\Rerequester.py", line 96, in fail
  File "\lib\wubi\backends\common\btdownloader.py", line 69, in error_callback
DownloadError: Problem connecting to tracker - <urlopen error (2, 'getaddrinfo failed')>

 in task download
06-16 21:50 DEBUG  TaskList: ### Finished download
06-16 21:50 ERROR  root: Could not remove: E:\ubuntu\install\ubuntu-13.04-desktop-amd64.iso
Traceback (most recent call last):
  File "\lib\wubi\backends\common\backend.py", line 426, in download_iso
OSError: [Errno 13] Permission denied: u'E:\\ubuntu\\install\\ubuntu-13.04-desktop-amd64.iso'
06-16 21:50 DEBUG  TaskList: New task download
06-16 21:50 DEBUG  TaskList: ### Running download...
06-16 21:50 DEBUG  downloader: downloading [http://ubuntu-releases.mirror.nexicom.net/13.04/ubuntu-13.04-desktop-amd64.iso](http://ubuntu-releases.mirror.nexicom.net/13.04/ubuntu-13.04-desktop-amd64.iso) > E:\ubuntu\install\ubuntu-13.04-desktop-amd64.iso
06-16 21:50 ERROR  TaskList: [Errno 4] IOError: <urlopen error (2, 'getaddrinfo failed')>
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\downloader.py", line 77, in download
  File "\lib\urlgrabber\grabber.py", line 927, in urlgrab
  File "\lib\urlgrabber\grabber.py", line 845, in _retry
  File "\lib\urlgrabber\grabber.py", line 913, in retryfunc
  File "\lib\urlgrabber\grabber.py", line 1001, in __init__
  File "\lib\urlgrabber\grabber.py", line 1072, in _do_open
  File "\lib\urlgrabber\grabber.py", line 1188, in _make_request
URLGrabError: [Errno 4] IOError: <urlopen error (2, 'getaddrinfo failed')>
06-16 21:50 DEBUG  TaskList: # Cancelling tasklist
06-16 21:50 ERROR  root: [Errno 4] IOError: <urlopen error (2, 'getaddrinfo failed')>
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 58, in run
  File "\lib\wubi\application.py", line 132, in select_task
  File "\lib\wubi\application.py", line 158, in run_installer
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\downloader.py", line 77, in download
  File "\lib\urlgrabber\grabber.py", line 927, in urlgrab
  File "\lib\urlgrabber\grabber.py", line 845, in _retry
  File "\lib\urlgrabber\grabber.py", line 913, in retryfunc
  File "\lib\urlgrabber\grabber.py", line 1001, in __init__
  File "\lib\urlgrabber\grabber.py", line 1072, in _do_open
  File "\lib\urlgrabber\grabber.py", line 1188, in _make_request
URLGrabError: [Errno 4] IOError: <urlopen error (2, 'getaddrinfo failed')>
06-16 21:50 ERROR  root: Could not remove: E:\ubuntu\install\ubuntu-13.04-desktop-amd64.iso
Traceback (most recent call last):
  File "\lib\wubi\backends\common\backend.py", line 426, in download_iso
OSError: [Errno 13] Permission denied: u'E:\\ubuntu\\install\\ubuntu-13.04-desktop-amd64.iso'
06-16 21:50 DEBUG  TaskList: New task download
06-16 21:50 ERROR  root: Could not remove: E:\ubuntu\install\ubuntu-13.04-desktop-amd64.iso
Traceback (most recent call last):
  File "\lib\wubi\backends\common\backend.py", line 426, in download_iso
OSError: [Errno 13] Permission denied: u'E:\\ubuntu\\install\\ubuntu-13.04-desktop-amd64.iso'
06-16 21:50 DEBUG  TaskList: New task download
06-16 21:50 ERROR  root: Could not remove: E:\ubuntu\install\ubuntu-13.04-desktop-amd64.iso
Traceback (most recent call last):
  File "\lib\wubi\backends\common\backend.py", line 426, in download_iso
OSError: [Errno 13] Permission denied: u'E:\\ubuntu\\install\\ubuntu-13.04-desktop-amd64.iso'
06-16 21:50 DEBUG  TaskList: New task download
06-16 21:50 ERROR  TaskList: Could not retrieve the required installation files
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 600, in get_iso
Exception: Could not retrieve the required installation files
06-16 21:50 DEBUG  TaskList: # Cancelling tasklist
06-16 21:50 DEBUG  TaskList: # Finished tasklist
```

---

### Post by varunendra on 2013-06-17
You are trying a WUBI installation which is only for trying Ubuntu, not meant for any serious usage. Besides, it is often buggy and hence not recommended for even testing.

Regardless of whether you choose to do a proper installation or go with WUBI anyway, the best and easiest option for you is to download the desired version via torrent from here : [http://www.ubuntu.com/download/alternative-downloads](http://www.ubuntu.com/download/alternative-downloads)

Then burn a CD/DVD or create a live USB to do a proper installation.

Or, if you choose to go with WUBI, just copy the ISO file (downloaded as mentioned above) in the same directory where you are running WUBI from. It should automatically pick it up instead of trying to download it or its contents.


**PS:**
I personally recommend 12.04, 64-bit if your system supports it.

---

### Post by mastablasta on 2013-06-17
you are running it inside windows not beside. wubi installs it in a virtual file. if that is what you like you may have a look at virtualbox instead.: [http://www.psychocats.net/ubuntu/virtualbox](http://www.psychocats.net/ubuntu/virtualbox)

furthermore wubi is not compatible with 13.04 anymore. it's development was dropped.
it was a good alternative for users wanting to install and give it a run.

---

### Post by sanjibar on 2013-06-17
Thank you Varun for your help. I will try that now and hope it works out fine. The desktop on which I am installing ubuntu is not so new - its a Pentium D 2.80 ghz processor with 4 gb ram. am not sure if my system supports your recommendation.

Sanjiv

---

### Post by newb85 on 2013-06-17
If you're system is powerful enough to support Ubuntu in a Wubi install, it can support an install to a real position.

---

### Post by varunendra on 2013-06-17
> **sanjibar said:**
> The desktop on which I am installing ubuntu is not so new - its a Pentium D 2.80 ghz processor with 4 gb ram. am not sure if my system supports your recommendation.

> **newb85 said:**
> If you're system is powerful enough to support Ubuntu in a Wubi install, it can support an install to a real position.
+1 to above.

A dual core 2.8 GHz processor is more than fine and 4GB RAM (even if it is DDR2) is more than plenty for 12.04. Just lookup your processor model (or post here) to confirm whether it is 64 bit capable or not.

---

### Post by sanjibar on 2013-06-17
its a Pentium D 820 2.80 Ghz - so what will that run comfortably ?

---

### Post by varunendra on 2013-06-17
> **sanjibar said:**
> its a Pentium D 820 2.80 Ghz - so what will that run comfortably ?

Yep, it is 64-bit capable, as per [http://ark.intel.com/products/27512](http://ark.intel.com/products/27512) :
> Instruction Set	  64-bit

Go for Ubuntu 12.04.2 Desktop (64-bit), via torrent to ensure speed and integrity of the download : [http://releases.ubuntu.com/12.04/ubuntu-12.04.2-desktop-amd64.iso.torrent](http://releases.ubuntu.com/12.04/ubuntu-12.04.2-desktop-amd64.iso.torrent)

However, if the extra features and eye-candy that the default version offers are not very high on your wish-list, you should also take a look at [Xubuntu]("http://xubuntu.org/getxubuntu/") and/or [Lubuntu]("https://help.ubuntu.com/community/Lubuntu/GetLubuntu").

That doesn't mean that default ubuntu will be slower '*because of hardware*', but xubuntu and lubuntu will be much faster, on any hardware. :)

---

### Post by sanjibar on 2013-06-18
Will I be able to run ubuntu as a second OS ? While installing will it give me the option of using the drive of my choice ?

---

### Post by newb85 on 2013-06-18
Yes and yes.

Depending on how new your machine is, there may be some complications due to GPT and UEFI partitioning, as well as Secure-Boot (a feature Microsoft had installed on newer machines for the purpose of complicating additional OSes).  All of these can be overcome fairly easily, but it's nice to be warned.

Before installing, you should defragment your Windows partition from within Windows.

When you boot from the Ubuntu Live installation media (DVD or USB), it will give you two options: install or test.  If you select test, you can always initiate the install from the test environment.  If there are no complications, the install wizard will recommend three options: overwrite Windows, install alongside Windows, or do something else (a custom partition setup).  If there are complications, the alongside option may not be there.  At this point, if you're unsure how to proceed, cancel the install and describe your situation here.

---

### Post by varunendra on 2013-06-18
Hello Sanjiv,

Like newb85 mentioned above, you should defragment windows partitions from within windows before proceeding with further partitioning and installation of Ubuntu.

Guessing by the generation of your processor, I'm confident that your desktop is not new enough to have support for GPT or Secure Boot like things. Hence there will be no complications regarding that.

Also, assuming the original partitioning was done by windows XP installer, the hard disk should have only one Primary and one Extended partition (with rest of the partitions being logical ones in it). As such, the best option for you would be to just shrink one of the data partitions (not the one in which windows itself is installed) using gparted on the Ubuntu installation disc, then using gparted, create -
[LIST]
[*]one EXT4 partition of 26 GB or more
[*]one swap partition of 1 or 2 GB
[/LIST]
..in the empty space gained by shrinking the data partition(s).

Please make sure to defragment all the drives (from within windows) before doing this.

Then start installation (earlier, you'll have to choose "**Try Ubuntu**" to be able to use gparted) and choose "Something else" option when asked. There, just select the EXT4 partition you just created and make it a mount point for "**/**". Make sure that the boot loader is going to install on the hard disk itself (**sda**/**sdb** etc. NOT sda**[COLOR="#FF0000"]1[/COLOR]**, sda**[COLOR="#FF0000"]2[/COLOR]** etc.). Then proceed with installation.

Once installed, it will give you the option at boot time to choose between itself and any other operation systems installed.

Last, like already said above, post back if you have any confusion or complications.

Good Luck ! :)

---

### Post by sanjibar on 2013-06-19
Thank you for all this help. I will revert back with the outcome ! :D

---

### Post by sanjibar on 2013-06-20
Hi,
Nearly gave up, but managed somewhat ! Though problem far from over. In short - I downloaded xubuntu 12.04 and ran it from a cd. it seemed to work and I put it onto a drive. when I rebooted it seemed ok, except went for a command prompt, so I gave up on that. i then tried the ubuntu 13.04 via a cd - it worked except i forgot to 'try' and went for install. then i rebooted and it said grub repair  or error !!! so i read up and used boot repair after downloading it. that has worked, except that the options of ubuntu after log in dont work - meaning it boots default ubuntu. so at least all isnt lost. now please tell me how to fix the boot loading, so i can use windows too if i need to. And i also unable to access most of the other drives. i get this msg alongwith 'unable to access volume-- 
'Error mounting /dev/sda1 at /media/sanjiv/C24C56354C562507: Command-line `mount -t "ntfs" -o "uhelper=udisks2,nodev,nosuid,uid=1000,gid=1000,dmask=0077,fmask=0177" "/dev/sda1" "/media/sanjiv/C24C56354C562507"' exited with non-zero exit status 14: Windows is hibernated, refused to mount.
Failed to mount '/dev/sda1': Operation not permitted
The NTFS partition is in an unsafe state. Please resume and shutdown
Windows fully (no hibernation or fast restarting), or mount the volume
read-only with the 'ro' mount option.
 HOPe i make sense :)

---

### Post by varunendra on 2013-06-20
> **sanjibar said:**
> 14: **[COLOR="#FF0000"]Windows is hibernated[/COLOR]**, refused to mount.
That is the problem. You had hibernated windows, not shut-down, before installing Ubuntu.
I am not particularly experienced in fixing this but hope it is not a big problem.

**1)** What is the version of Windows you have installed?
**2)** Do you have an installation CD/DVD from which it was installed? We may need it to restore Windows boot loader if required.

As of now, please try -
```
sudo update-grub
```
command from within Ubuntu. If it could detect the windows installation, you will get the option to boot into it at startup. Although since you are having mounting problem, I suspect it may fail to do that.

If it fails, run boot-repair and generate "Boot-Info Summary", and post back the summary itself or its pastebin link (will be created if you are connected to internet while running it).

---

### Post by sanjibar on 2013-06-21
Hi Varun,  I was using windows 8. The installation cd doesn't work anymore. I ran boot repair and went to advance options and checked the mbr option. On rebooting it went to windows without ubuntu option. So i did boot repair and cheked grub again and it booted into ubuntu, with other options showing that don't work. anyway as per your instructions here is a fresh Boot-info summary - http:// paste.ubuntu.com/5786841/ Also i did try the grub update code, without any difference.

---

### Post by varunendra on 2013-06-21
Wow! You are running win8 and were questioning about system capability for Ubuntu? :D
Anyway -
> **sanjibar said:**
> I ran boot repair and went to advance options and checked the mbr option. On rebooting it went to windows without ubuntu option.

When you are in Windows, do what is suggested here to completely turn off Hibernation in windows 8 : [http://www.hecticgeek.com/2012/12/disable-hibernation-windows-8/](http://www.hecticgeek.com/2012/12/disable-hibernation-windows-8/)

Then re-run Boot repair to fix Ubuntu booting and you should get everything all set as required.


**PS:**
Not sure what made you fall for a crappy OS like win8, perhaps all the glamour behind it. I haven't tried it (have read enough to stay away from it), but can confidently say that XP or even Win7 would be far-far better for your hardware.

---

### Post by sanjibar on 2013-06-21
Haha, 
Not sure whats the right answer to using win8 - not too impressed with it. 7 is better since xp support has mostly ended. ok one things fixed - all the drives are visible :cool:. BUT not the boot options - cannot scroll down to use win 8. so the latest boot -info summary is - http:// paste.ubuntu.com/5787204/

---

### Post by varunendra on 2013-06-21
> **sanjibar said:**
> ok one things fixed - all the drives are visible :cool:. BUT not the boot options - cannot scroll down to use win 8. so the latest boot -info summary is - http:// paste.ubuntu.com/5787204/

What do you mean by "can not scroll down to use win 8"? Are you unable to use the arrow keys on the grub menu to select a different option to boot with? If so, that may be a different problem. Does the keyboard work at all on the Grub screen?

---

### Post by sanjibar on 2013-06-21
Yes thats correct. Probably the keyboard does not work !

---

### Post by sanjibar on 2013-06-21
Done !! Fixed it :D

---

### Post by varunendra on 2013-06-21
> **sanjibar said:**
> Done !! Fixed it :D

Wow! I was going to reply you with [this]("https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/771376") bug report link when I noticed the [Solved] prefix, then your last post :-o

Would you mind sharing the 'Secret' with us how you did it? ;)

---

### Post by sanjibar on 2013-06-22
Hi Varun,
:D from posts here i guess (googled it). it needs to be changed in BIOS, as new keyboard i am using is USB. have to enable it, as it is by default disabled. Of course, it was all because you asked "Does the keyboard work at all on the Grub screen?" That can be found in peripherals or something such like in the BIOS.
Thank you and will surely be posting more questions :)

---

