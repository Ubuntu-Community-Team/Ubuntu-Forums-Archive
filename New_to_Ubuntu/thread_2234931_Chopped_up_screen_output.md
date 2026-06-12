---
title: "Chopped up screen output"
date: 2014-07-17
forum: New to Ubuntu
---

### Post by WildFulmar on 2014-07-17
Guys, if this is the beginers page I'm not sure I've come to right place with kernels, stacks & pools, but I'm hoping someone can help resolve my problem. I'm realy keen to get to use Linux as my main operating system, and so far I have been realy pleased with what I have experienced.  However the experience has been somewhat dulled by some realy awfull screen output. It occurs regardless of the application though it does take slightly different forms, of missing lines of text duplicated lines of text, blocked out lines in black or grey lines of text or chopped up lines, so it becomes realy dificult to read documents spreadsheets emails web pages - the lot.  So I'm assuming it has to be something to do with the video card and its driver. so I have looked arround and found some command line tasks and run them to see what comes out:-

john@john-desktop:~$ lspci | grep VGA
01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 661/741/760 PCI/AGP or 662/761Gx PCIE VGA Display Adapter
john@john-desktop:~$ sudo lshw -C video
[sudo] password for john: 
  *-display UNCLAIMED     
       description: VGA compatible controller
       product: 661/741/760 PCI/AGP or 662/761Gx PCIE VGA Display Adapter
       vendor: Silicon Integrated Systems [SiS]
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 00
       width: 32 bits
       clock: 66MHz
       capabilities: pm agp agp-3.0 vga_controller cap_list
       configuration: latency=0
       resources: memory:e0000000-e7ffffff memory:ec000000-ec01ffff ioport:d000(size=128)
john@john-desktop:~$ cd/usr/lib/xorg/modules/drivers
bash: cd/usr/lib/xorg/modules/drivers: No such file or directory
john@john-desktop:~$ lshw -C video | grep 'configuration'
WARNING: you should run this program as super-user.
WARNING: output may be incomplete or inaccurate, you should run this program as super-user.
       configuration: latency=0
john@john-desktop:~$ find /dev -group video
/dev/agpgart
/dev/fb0
john@john-desktop:~$ glxinfo | grep -i vendor
The program 'glxinfo' is currently not installed. You can install it by typing:
sudo apt-get install mesa-utils
john@john-desktop:~$ 

Now as I'm new I have no concept of super user or what any of the above means, but if any of you guys can help me and point me in the right direction to load any suitable drivers etc. to maybe resolve this problem, I would be gratefull.  

I'm using Lubuntu 14.04 on what is now a dual boot PC circa 7 years old. Its reasonably quick both in Windows and Lubuntu, and I'm realy pleased that Wine Runs an Old Windows based Family History Program that I had. 

Anyway lets not get distracted its the video output I need sorted if possible. (see its just done it now and blanked out part of the last but one line of this message, and now its come back!!!)

---

### Post by karlowbrian on 2014-07-17
It just sounds like your video card is going bad. :( you can try to re-install drivers or even the monitor just to make sure the VGA on the monitor isn't bad. But it sounds like a video card issue.

---

### Post by WildFulmar on 2014-07-18
Guys, I should have said that I have no such graphic problems when I run the system up on Windows.  So I'm still at a loss, this reply via Windows I'm afraid.

---

### Post by Rob Sayer on 2014-07-18
When it said you should run lshw as super user it means you should use sudo, specifically

```
sudo lshw -C video 
```

or you won't get complete information.

SIS video adapters have always been a problem in linux since it's one of those unusual cases where Intel outsourced the video (my cedarview netbook is similar) and the vendor wouldn't release the source code.

I tried a quick search of "ubuntu 14.04 sis graphics" ... search engines are your friend ... and found

[http://ubuntuforums.org/showthread.php?t=2215422](http://ubuntuforums.org/showthread.php?t=2215422)

which has stuff specific to your card.  Just don't expect the video performance to be as good as in windows.

---

