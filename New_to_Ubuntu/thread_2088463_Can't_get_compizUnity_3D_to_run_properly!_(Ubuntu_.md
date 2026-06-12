---
title: "Can't get compiz/Unity 3D to run properly! (Ubuntu 12.10)"
date: 2012-11-26
forum: New to Ubuntu
---

### Post by deadlylady on 2012-11-26
Everytime my system(Ubuntu 12.10) boots up I get messages that Compiz isn't running properly. When testing unity support in terminal I get two errors:
>                       Not software rendered:    no
Unity 3D supported:       no                  I read somewhere to look at the information given from "sudo lshw -C display; lsb_release -a; uname -a", which looks like this:
                        > *-display               
       description: VGA compatible controller
       product: Cape Verde [Radeon HD 7700 Series]
       vendor: Advanced Micro Devices [AMD] nee ATI
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress msi vga_controller bus_master cap_list rom
       configuration: driver=radeon latency=0
       resources: irq:56 memory:e0000000-efffffff memory:f7e00000-f7e3ffff ioport:e000(size=256) memory:f7e40000-f7e5ffff
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 12.10
Release:    12.10
Codename:    quantal
Linux desktop 3.5.0-17-generic #28-Ubuntu SMP Tue Oct 9 19:31:23 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux                  I have a Radeon HD 7700 graphic card, and looking at this page [http://askubuntu.com/questions/162831/ubuntu-12-04-radeon-hd-6670-help](http://askubuntu.com/questions/162831/ubuntu-12-04-radeon-hd-6670-help) I got the impression that the correct drivers for the card was not installed so I followed the advice there and installed Ati binary driver from ubuntu software center. On restart however Ubuntu desktop panels, shortcut icons etc wouldn't show just a completely blank desktop. I managed to uninstall said "Ati binary driver"(searching and finding the software center from a newly created map) and now my desktop looks to be back to normal.

So still I have no solution for my compiz/unity 3d issues and only managed to mess things up even more!
:guitar:

Any suggestions?

---

### Post by deadlylady on 2012-11-27
Hello?! Haven't anyone else had this problem?
:lolflag:

---

### Post by audiomick on 2012-11-27
Yep, quite a few. It is just that none of the ones who have solved it have looked at this thread... ;)

I can't help you much, as I don't have an ATI card, but from post #14 and #15 of this thread about a different ATI card, 
[http://ubuntuforums.org/showthread.php?t=2085133&highlight=Radeon+HD+7700]("http://ubuntuforums.org/showthread.php?t=2085133&highlight=Radeon+HD+7700")

which I found with a search of the forums for "Radeon HD 7700",

there is this link

[http://support.amd.com/us/kbarticles/Pages/AMDCatalyst1211betadriver.aspx]("http://support.amd.com/us/kbarticles/Pages/AMDCatalyst1211betadriver.aspx")

which offers a download for a driver for linux.

I would not suggest that if your were having any joy with the drivers that Ubuntu offers, but if they are not working for you, you might want to try the driver there. I can't help you with installing it other than to suggest downloading and un-zipping it and looking for a "read me" or something in there with installation instructions. There often is one. There may also be an executable in there that you just have to click on and run. On the other hand, you may have to compile something. You will have to have a look yourself, sorry.

---

### Post by dannyboy79 on 2012-11-27
once you had the driver installed, it sounds like your window decorations just stopped working with compiz. to solve that with the driver installed isn't just a matter of issuing
emerald --replace

See here for compiz troubleshooting: [http://wiki.compiz.org/Troubleshooting#Is_a_Window_Decorator_Running.3F](http://wiki.compiz.org/Troubleshooting#Is_a_Window_Decorator_Running.3F)

---

### Post by TanzGeist on 2012-12-01
You are not alone.

Radeon HD 7750 (also shown as 7700) and Ubuntu 12.10-64 bit.
Running, but not fine.

As I understand from [http://ubuntuxtreme.com/howto/how-to-fix-your-amd-graphics-in-ubuntu-12-10/]("http://ubuntuxtreme.com/howto/how-to-fix-your-amd-graphics-in-ubuntu-12-10/")

12.10..."comes with the new version of xorg 1.13 that is included in Quantal, meaning that you need to downgrade xorg down to 1.12.  So for the time being there is no AMD Legacy support with X-Server 1.13, and you need to downgrade"

...but I still haven't got the ATI drivers running. So I'm "happy" being able to watch video (not optimal, but usable) and use VirtualBox.

Also I experience problems getting my (dual screen) setup to run properly even on one screen after starting the PC. 

My resolutions are either:
- not to shut down, instead to hibernate/suspend (don't know the word used in the english version of ubuntu)
- or starting (mostly several times) until it works. I even have to shutdown -r via console or restart AND logon to windows, then restart into ubuntu seems to set the Radeon HD 7700 (7750) into the right "mood" to "work"

Hope for things to getting better within the next some month. Also there might be an update to the methods mentioned on ubuntuextreme.

---

### Post by TanzGeist on 2012-12-03
Ups. Found on a german forum an english answer/how-to. And a  Radeon HD 7700 user writes that the ATI driver works after using using the instruction posted 11. November 2012 16:25.

Suppose, the instruction origins ATI and belongs to the Catalyst 12.11-beta driver:

 "TEST ON 64BIT SYSTEM WITH Ubuntu 12.10 AND AMD/ATI DRIVER Catalyst-12.11-beta use it with own risk"

[http://forum.ubuntuusers.de/topic/amd-ati-treiber-12-10-12-11-ubuntu-12/2/?highlight=12.10+radeon+hd+#post-5009752]("http://forum.ubuntuusers.de/topic/amd-ati-treiber-12-10-12-11-ubuntu-12/2/?highlight=12.10+radeon+hd+#post-5009752")

Well, I think prefer waiting for the next stable catalyst.

---

### Post by deadlylady on 2012-12-04
> **TanzGeist said:**
> Ups. Found on a german forum an english answer/how-to. And a  Radeon HD 7700 user writes that the ATI driver works after using using the instruction posted 11. November 2012 16:25.

Suppose, the instruction origins ATI and belongs to the Catalyst 12.11-beta driver:

 "TEST ON 64BIT SYSTEM WITH Ubuntu 12.10 AND AMD/ATI DRIVER Catalyst-12.11-beta use it with own risk"

[http://forum.ubuntuusers.de/topic/amd-ati-treiber-12-10-12-11-ubuntu-12/2/?highlight=12.10+radeon+hd+#post-5009752](http://forum.ubuntuusers.de/topic/amd-ati-treiber-12-10-12-11-ubuntu-12/2/?highlight=12.10+radeon+hd+#post-5009752)

Well, I think prefer waiting for the next stable catalyst.
Thank you for this! So, first I tried along the lines of the first person who answered to the solution(in german) who had gone about it without installing gnome. That did however not work for me so I followed the instructions step by step. Several of them didn't work for me for some reason so I had to download some of the packages from the software center and finally I also got the 
> Generating package: Ubuntu/quantal

Package /home/p/fglrx_9.010-0ubuntu1_amd64.deb has been successfully generated
Package /home/p/fglrx-dev_9.010-0ubuntu1_amd64.deb has been successfully generated
Package /home/p/fglrx-amdcccle_9.010-0ubuntu1_amd64.deb has been successfully generated
Removing temporary directory: fglrx-install.KiLABDHOWEVER

unity support test STILL leaves me with this result:
> Not software rendered:    no
Not blacklisted:          yes
GLX fbconfig:             yes
GLX texture from pixmap:  yes
GL npot or rect textures: yes
GL vertex program:        yes
GL fragment program:      yes
GL vertex buffer object:  yes
GL framebuffer object:    yes
GL version is 1.4+:       yes

Unity 3D supported:       no:confused::confused::evil:

---

### Post by deadlylady on 2012-12-04
But maybe I should try the Ati binary driver again now that some other stuff seem to be in place?

Edit: That didn't work either, same problem as before all toolbars and sidebar not showing while ati binary driver installed

---

### Post by Mark Phelps on 2012-12-04
> **TanzGeist said:**
> ... 
As I understand from [http://ubuntuxtreme.com/howto/how-to-fix-your-amd-graphics-in-ubuntu-12-10/]("http://ubuntuxtreme.com/howto/how-to-fix-your-amd-graphics-in-ubuntu-12-10/")

12.10..."comes with the new version of xorg 1.13 that is included in Quantal, meaning that you need to downgrade xorg down to 1.12.  So for the time being there is no AMD Legacy support with X-Server 1.13, and you need to downgrade" ... 

This warning only applies to AMD chipsets EARLIER than the HD 5x.

The OP has a newer chipset and does NOT need to downgrade the X-server version.

---

### Post by deadlylady on 2012-12-05
Okay so I have managed to install it through unpacking the runfile into debs and then installing them instead as described in [the thread previously linked]("http://forum.ubuntuusers.de/topic/amd-ati-treiber-12-10-12-11-ubuntu-12/2/?highlight=12.10+radeon+hd+#post-5009752") in this thread.  This however gives me a completely messed up desktop. I have gotten this  result about 10 times now and sometimes it says "for testing only" in  the right lower corner. To get my system back to a usable state (that is  one with toolbars etc) I have to again delete the following packages:
ati binary driver and along with it
-fglrz-dev
-fglrz-amdcccle
So it seems that I've managed to install the package? Only that it leaves my system in worse shape than before.

---

### Post by TanzGeist on 2012-12-07
Downloaded and installed this one. First I supposed the driver to be the 12-12beta driver (now i am not shure about this):

Latest Beta Driver	109.4 MB	12.11 Beta	12/3/2012

... and inside:
amd-driver-installer-catalyst-12.11-beta11-x86.x86_64.zip

fglrxinfo shows:
```
fglrxinfo
display: :0  screen: 0
OpenGL vendor string: Advanced Micro Devices, Inc.
OpenGL renderer string: AMD Radeon HD 7700 Series 
OpenGL version string: 4.2.11995 Compatibility Profile Context

```

Within Catalyst Control Center / Info / under "Branch Software":
```
Driver package: 9.01.8-121202a-150296E-ATI
2d-driver: 9.1.11
Catalyst: 2.18
```

Well, it works on two screens (expanded desktop) and much better than without the ati driver. Also I notice -besides the "AMD Testing use only" watermark- that VLC has some not to nice, but still ignoreable issues with the icons at the bottom. Video therefore runs smooth and after switching VLC into fullscreen the pic is fine. Much better than before (ATI driver).

I have to admit that I before experimented with the ATI solutions discussed at ubuntuextreme. That didn't work for my ubuntu, but I didn't get rid of all the modifications it did to my system, like geting different kind of kernel updates (generic, I think). Works for me, but the config is no more out-of-the-box.

Looking forward to remove the watermark, Gnome (right now I run on unity) and work with Windows in the VirtualBox.

---

