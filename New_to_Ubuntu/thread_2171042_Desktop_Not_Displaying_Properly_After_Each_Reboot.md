---
title: "Desktop Not Displaying Properly After Each Reboot"
date: 2013-08-28
forum: New to Ubuntu
---

### Post by toady2 on 2013-08-28
I'm very sorry the title is vague, it's just I really don't know explain it in a short title. I have an external monitor (ViewSonic) connected to my netbook running Lubuntu 13.04. I go to my monitor settings and I do the following: Turn VGA display on then turn DVI display off and change the resolution of the VGA to auto. By the way I have to say this even though it's not the main problem, the reason why i said i turn VGA on THEN turn DVI off is that if I check the two boxes at once and save then both my screens are blank so I have to restart each time. Anyway back to the main problem. After I change the resolution to auto and click save and apply I get the Desktop entitled as (Desktop Proper.jpg in the attachments). But after I restart my computer I get the desktop entitled as (Desktop Messed Up.jpg in the attachments). Does anyone know why? Also one thing to note if i drag my mouse to select everything in the Desktop I can only cover the black portion of the desktop in the messed up desktop, not the coloured wallpaper part. Thank you very much :). This issue is driving me crazy cause I have to change my Desktop settings each time. By the way my wallpaper is just black solid colour not the coloured part you see. I don't know why it's showing up.

---

### Post by eternal243 on 2013-08-29
> **toady2 said:**
> I'm very sorry the title is vague, it's just I really don't know explain it in a short title. I have an external monitor (ViewSonic) connected to my netbook running Lubuntu 13.04. I go to my monitor settings and I do the following: Turn VGA display on then turn DVI display off and change the resolution of the VGA to auto. By the way I have to say this even though it's not the main problem, the reason why i said i turn VGA on THEN turn DVI off is that if I check the two boxes at once and save then both my screens are blank so I have to restart each time. Anyway back to the main problem. After I change the resolution to auto and click save and apply I get the Desktop entitled as (Desktop Proper.jpg in the attachments). But after I restart my computer I get the desktop entitled as (Desktop Messed Up.jpg in the attachments). Does anyone know why? Also one thing to note if i drag my mouse to select everything in the Desktop I can only cover the black portion of the desktop in the messed up desktop, not the coloured wallpaper part. Thank you very much :). This issue is driving me crazy cause I have to change my Desktop settings each time. By the way my wallpaper is just black solid colour not the coloured part you see. I don't know why it's showing up.

Interesting problem, I have no idea what is happening here and I have never used Lubuntu or any other distro with the LXDE desktop environment.

But try to following command in terminal and repost the output. 

```
lspci | grep VGA
```

We have to start somewhere and this will list what graphics cards you have in your computer.

---

### Post by toady2 on 2013-08-29
From
```
lspci | grep VGA
```
I get
```
 
00:02.0 VGA compatible controller: Intel Corporation Atom Processor D4xx/D5xx/N4xx/N5xx Integrated Graphics Controller

```

I should also note something. After I get my messed up desktop I found another way to get back to the normal desktop. I change to 720 * 400 click apply then back to 1280 * 1024 I get proper desktop. This only works for very low resolution. It does not work if i change to  1280 * 960 then back to 1280 * 1024. I'm so confused...

---

### Post by eternal243 on 2013-08-29
> **toady2 said:**
> From
```
lspci | grep VGA
```
I get
```
 
00:02.0 VGA compatible controller: Intel Corporation Atom Processor D4xx/D5xx/N4xx/N5xx Integrated Graphics Controller

```

Hmm, integrated graphics only, what about this command?

```
sudo lshw
```
It will output a detailed list of all your hardware.

Also, you said the you got an external monitor connected to your netbook, but do you have the same problem if you disconnect the external monitor? Just using netbook display?

---

### Post by toady2 on 2013-08-29
Results related to display
```
 *-pci          description: Host bridge
          product: Atom Processor D4xx/D5xx/N4xx/N5xx DMI Bridge
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 00
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel
          resources: irq:0
        *-display:0
             description: VGA compatible controller
             product: Atom Processor D4xx/D5xx/N4xx/N5xx Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: msi pm vga_controller bus_master cap_list rom
             configuration: driver=i915 latency=0
             resources: irq:44 memory:98180000-981fffff ioport:60c0(size=8) memory:80000000-8fffffff memory:98000000-980fffff
        *-display:1 UNCLAIMED
             description: Display controller
             product: Atom Processor D4xx/D5xx/N4xx/N5xx Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2.1
             bus info: pci@0000:00:02.1
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: latency=0
             resources: memory:98100000-9817ffff

```

Nop, I don't get this issue with Netbook display but the display does mess up after i connect my monitor and restart. The same issue where parts are black wallpaper and here and parts of the coloured wallpaper there on my netbook and external.

---

### Post by sceptre78 on 2013-08-29
Ok, this may sound stupid but it look like its trying to run 2 DE's on one screen....
Also shouldnt the config on both be using the same driver?


```
*-display:0
             description: VGA compatible controller
             product: Atom Processor D4xx/D5xx/N4xx/N5xx Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: msi pm vga_controller bus_master cap_list rom
             [COLOR=#ff0000]configuration: driver=i915 latency=0[/COLOR]
             resources: irq:44 memory:98180000-981fffff ioport:60c0(size=8) memory:80000000-8fffffff memory:98000000-980fffff
        *-display:1 UNCLAIMED
             description: Display controller
             product: Atom Processor D4xx/D5xx/N4xx/N5xx Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2.1
             bus info: pci@0000:00:02.1
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             [COLOR=#ff0000]configuration: latency=0[/COLOR]
             resources: memory:98100000-9817ffff
```



do this and post the results 


```
cat /etc/X11/xorg.conf
```

Doh! nevermind Ubuntu doesnt use an xorg.conf file anymore.

---

### Post by toady2 on 2013-08-29
no no that doesn't sound stupid Becase if i right click on the black part of the screen i get a different menu than i when i right click on the coloured part. When I click on the coloured part I get a menu that OpenBox has provided on top of lxde but when I click on the black part I only get the LXDE menu. Even though openbox is just a windows manager so it couldn't be two different DE but something along that line.

I'm sorry I don't have that file called xorg.conf

This is all I have 
```
app-defaults             rgb.txt  Xreset      Xsession.ddefault-display-manager  X        Xreset.d    Xsession.options
fonts                    xinit    Xresources  XvMCConfig
openbox                  xkb      Xsession    Xwrapper.config



```

*EDITED* 
Oh okay

---

### Post by toady2 on 2013-08-29
So anyone has any idea? So it appears that there are two things running everytime I reboot. LXDE is running and Openbox is apparently adding it's own menu as well because if I right click on the coloured wallpaper openbox menu is showing up and the black part only shows LXDE'S menu.

I've added two pics to explain how it differs.  Note i didn't create the second new folder it just appeared. It's exactly the same folder as the other new folder just duplicated for some reason and if i drag my mouse to select it, the folder then disappears but the original folder on the top left remains.

---

### Post by eternal243 on 2013-08-29
Well I can't help any more with this since I have no experience with either LXDE or Openbox, but at least we have narrowed down the problem a little bit. Hopefully someone else can help you out! I will follow the thread though since the problem itself is kind of interesting! :)

---

### Post by toady2 on 2013-08-29
That's okay, Thanks for trying :)

---

### Post by toady2 on 2013-08-31
I thought I would keep this thread alive. 
*UPDATE*
Before I always get that messed up desktop every time the computer reboots or after every shut-down. Now I can't predict when that messed up desktop will come next. It's becoming random now. Sometimes it's the proper desktop and sometimes it's that messed up desktop. Does anyone who use Lubuntu or LXDE have/had this issue when using an external monitor?

---

### Post by toady2 on 2013-08-31
It seems there's no way to delete a post...that's why I'm writing this on top a post I wanted to delete.
If there is a way some one please tell me:) thanks

---

### Post by vasa1 on 2013-09-01
> **toady2 said:**
> ...
This is all I have 
```
app-defaults             rgb.txt  Xreset      Xsession.ddefault-display-manager  X        Xreset.d    Xsession.options
fonts                    xinit    Xresources  XvMCConfig
openbox                  xkb      Xsession    Xwrapper.config

```
...
What command did you use to generate the code you provided above? When you login, what options do you see? Which option do you choose?
What is the output of "ls /usr/share/xsessions"?

Don't give up! Using an external monitor could be a bit complicated!

---

### Post by vasa1 on 2013-09-01
When I run "ls /usr/share/xsessions" I see:
```
[10:11 AM] ~ $ ls /usr/share/xsessions
Lubuntu.desktop          lxgames.desktop        openbox-kde.desktop
Lubuntu-Netbook.desktop  openbox.desktop
lubuntu-nexus7.desktop   openbox-gnome.desktop
```

---

### Post by toady2 on 2013-09-01
I used ```
ls /etc/X11
``` and that output showed up.
I see Lubuntu, Openbox, Lubuntu nexus 7, Lubuntu LX Games.
I choose Lubuntu 

The output of ```
[COLOR=#000000]ls /usr/share/xsessions[/COLOR]
```
is 
```

Lubuntu.desktop  Lubuntu-Netbook.desktop  lubuntu-nexus7.desktop  lxgames.desktop  openbox.desktop  openbox-gnome.desktop  openbox-kde.desktop


```

---

### Post by vasa1 on 2013-09-01
Have you made a lot of changes to your system so far? Specifically, have you edited any system files such as those in /etc? I think if you keep a record of what you've done, it may help someone troubleshoot your issue.

Also, going further, it maybe better for you to post the output of "ls -al" rather than plain "ls", at least till your current issue is sorted out.

---

### Post by toady2 on 2013-09-01
Nop, I didn't touch any system files and anything that would affect the system, well just one but that's only after this issue. I just changed the autostart file , but I changed it back. I also just installed basic software, and gcc compiler, java openjdk, bsdgames. Honestly that's all. 

*UPDATED* 
using the ls -al command 

```

ls -al /usr/share/xsessions
total 36
drwxr-xr-x   2 root root 4096 Apr 23 11:49 .
drwxr-xr-x 215 root root 4096 Aug 31 19:43 ..
-rw-r--r--   1 root root  369 Nov 14  2012 Lubuntu.desktop
-rw-r--r--   1 root root  222 Nov 14  2012 Lubuntu-Netbook.desktop
-rw-r--r--   1 root root  159 Nov 27  2012 lubuntu-nexus7.desktop
-rw-r--r--   1 root root  201 Nov 17  2012 lxgames.desktop
-rw-r--r--   1 root root  300 Apr  1 13:06 openbox.desktop
-rw-r--r--   1 root root  218 Apr  1 13:06 openbox-gnome.desktop
-rw-r--r--   1 root root  205 Apr  1 13:06 openbox-kde.desktop



```

```

 ls -al /etc/X11
total 88
drwxr-xr-x   9 root root  4096 Aug 27 20:35 .
drwxr-xr-x 126 root root 12288 Sep  1 00:58 ..
drwxr-xr-x   2 root root  4096 Apr 23 11:51 app-defaults
-rw-r--r--   1 root root    18 Apr 23 11:50 default-display-manager
drwxr-xr-x   3 root root  4096 Apr 23 11:50 fonts
lrwxrwxrwx   1 root root    14 Aug 25 21:52 openbox -> ../xdg/openbox
-rw-r--r--   1 root root 17394 Dec  3  2009 rgb.txt
lrwxrwxrwx   1 root root    13 Aug 25 21:52 X -> /usr/bin/Xorg
drwxr-xr-x   3 root root  4096 Apr 23 11:51 xinit
drwxr-xr-x   2 root root  4096 Feb  2  2013 xkb
-rwxr-xr-x   1 root root   709 Apr  1  2010 Xreset
drwxr-xr-x   2 root root  4096 Apr 23 11:50 Xreset.d
drwxr-xr-x   2 root root  4096 Apr 23 11:50 Xresources
-rwxr-xr-x   1 root root  3730 Mar 22  2012 Xsession
drwxr-xr-x   2 root root  4096 Aug 27 20:35 Xsession.d
-rw-r--r--   1 root root   265 Jul  1  2008 Xsession.options
-rw-r--r--   1 root root    13 Aug 15  2012 XvMCConfig
-rw-r--r--   1 root root   601 Apr 23 11:50 Xwrapper.config



```

---

### Post by IbsUser on 2013-09-01
Once you're using two monitors, could you try the links below?

Dual monitors in Lubuntu:
[http://www.lubuntutips.com/2012/05/dual-monitors-in-lubuntu.html#.UiObbK7-B1Y](http://www.lubuntutips.com/2012/05/dual-monitors-in-lubuntu.html#.UiObbK7-B1Y)

Lubuntu Screencast: Multi Monitor
[http://lubuntu.net/blog/lubuntu-screencast-multi-monitor-tips-tricks](http://lubuntu.net/blog/lubuntu-screencast-multi-monitor-tips-tricks)

Linux LXDE Guide:
[http://lxlinux.com/#14](http://lxlinux.com/#14)

---

