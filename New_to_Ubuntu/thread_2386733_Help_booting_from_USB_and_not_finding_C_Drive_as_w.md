---
title: "Help booting from USB and not finding C Drive as well as black screen issue"
date: 2018-03-09
forum: New to Ubuntu
---

### Post by phd-in-diabeetus on 2018-03-09
[COLOR=#242729][FONT=Arial][FONT=inherit]I have a windows 10 computer and a macbook pro. I have put Ubuntu 16.04.4 onto a flash drive using Etcher on my macbook following Ubuntu's guide to installation. I am able to boot using the usb and access a text menu that gives me the options to 'Try Ubuntu Without Installing' 'Install Ubuntu' 'OEM Install for manufacturers' ''Check Disk for Defects'. When I boot straight from trying without install I get a black screen. I tried several different approaches including changing quiet splash to nomodeset. The only way to boot without getting a black screen is to change my 'set gfxpayload=text' instead of 'set gfxpayload=keep'. That allows ubuntu to boot and gives me all the graphics and splash screen etc.[/FONT]
[FONT=inherit]Now When I am in Ubuntu I am trying to access my c drive. C/Windows/System32. My internal hard drive doesn't show in the file search. I try using fdisk -l and it only shows my external usb drive and some loop thing. It doesn't display my internal hard drive at all.[/FONT]
[FONT=inherit]I am using Windows 10 on a Lenovo Yoga that has Intel Integrated Graphics as well as an nvidia geforce gtx1050 which has something to do with my black screen issues I assume.[/FONT]
[FONT=inherit]When I open files I am able to see home - desktop - documents - downloads etc. Then below it says Computer - Ubuntu 16.04.4 LTS amd64. I get an error saying[/FONT]
[FONT=inherit]"Unable to access 'Ubuntu 16.04.4 LTS amd64' Error mounting /dev/sda1 at /media/ubuntu/Ubuntu 16.04.4 LTS amd64: Command-line 'mount -t "iso9660" -o "unhelper=udisks2,nodev,nosuid,uid=999,gid=999,iocharset=utf8,mode=0400,dmode=0500" etc.[/FONT]
[FONT=inherit]Pretty much how can I access my Internal Hard Drive's C folder??[/FONT]
[FONT=inherit]p.s. I have also tried other linux iso's such as arch linux and puppy linux. I can't access c drive on either of those, but haven't done as much research for those iso's. I have also formatted the flash drive multiple times and used etcher to install fresh.[/FONT]


[/FONT][/COLOR]

---

### Post by TheFu on 2018-03-09
Windows 10 doesn't close the file system, so Linux thinks it is still open and won't access it.  There are settings in Windows to tell it to close the file system between boots.  Fast-start? Something like that.  Google should find it and the instructions.

Seems you solved the bank screen already. If not, might want to clear up the #1 post and ask that question separately.  The knowledge to fix GPU issues isn't the same as that to fix file system access issues. It is best to ask 1 question per thread here when they aren't related.  These are not.

---

### Post by Mark Phelps on 2018-03-09
The Win10 culprit is Fast Startup -- which is enabled in Win10 by default.

There are two ways to disable FastStartup in Win8/10; (1) through the Control Panel, and (2) through an elevated command prompt.
 
Control Panel - Open Control Panel --> Power Options.
Select "Choose what the power buttons do"
Select "Change settings that are currently unavailable"
At the bottom of the Window, under Shutdown settings, uncheck the box regarding fast startup
 
Elevated command prompt - run the following command:
REG ADD "HKLM\SYSTEM\CurrentControlSet\Control\Session Manager\Power" /V  HiberbootEnabled /T REG_dWORD /D 0 /F
 
In both cases, reboot Windows.
 
NOW, FastStartup is disabled.

---

