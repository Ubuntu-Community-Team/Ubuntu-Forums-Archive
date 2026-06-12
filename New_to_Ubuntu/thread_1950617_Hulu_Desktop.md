---
title: "Hulu Desktop"
date: 2012-04-01
forum: New to Ubuntu
---

### Post by theducksfan2010 on 2012-04-01
I downloaded the Hulu Desktop for Ubuntu 64bit from: 

[http://www.hulu.com/labs/hulu-desktop-linux](http://www.hulu.com/labs/hulu-desktop-linux)

installed it, opened it up, was watching a movie ad, went to make it full screen and it all dissapeared. I tried to reopen Hulu and nothing. I reinstalled it from the software center and tried to open it up again and still nothing. I did a computer reboot and then tried to open it again, and it is still not there. Anyone have any help??

---

### Post by theducksfan2010 on 2012-04-09
Bump

---

### Post by leecheroflife on 2012-04-09
Have you tried running it from a terminal? Do it and post the ouput please.

---

### Post by theducksfan2010 on 2012-04-09
> **leecheroflife said:**
> Have you tried running it from a terminal? Do it and post the ouput please.:

---

### Post by theducksfan2010 on 2012-04-09
> **leecheroflife said:**
> Have you tried running it from a terminal? Do it and post the ouput please.

It returned errors trying to post the return in the terminal so I attached a .jpeg

---

### Post by leecheroflife on 2012-04-09
Looks like your missing some GTK dependancys, hence the crashing. Was it a .deb file you used to install from?

---

### Post by anewguy on 2012-04-09
t may be incompatibilities between the version of Ubuntu you are running - and it's included GTK libraries, and the latest version that website says it supports:  9.04.  Things have come a long way since then, and GTK has evolved from 1.x to 3.x.  Some old GTK functions were deleted, others superceeded.  I would suspect this is your problem.  I would send an email to the people responsible for that site, or use the "contact us" way at the bottom of that page,  and see if it has been updated to included versions 11 and soon 12 of Ubuntu.  If it has, we can go from there trying to figure it out.  If not, trying to go backwards in libraries to get something like this to work can be a nightmare.

Dave ;)

---

### Post by theducksfan2010 on 2012-04-09
> **anewguy said:**
> t may be incompatibilities between the version of Ubuntu you are running - and it's included GTK libraries, and the latest version that website says it supports:  9.04.  Things have come a long way since then, and GTK has evolved from 1.x to 3.x.  Some old GTK functions were deleted, others superceeded.  I would suspect this is your problem.  I would send an email to the people responsible for that site, or use the "contact us" way at the bottom of that page,  and see if it has been updated to included versions 11 and soon 12 of Ubuntu.  If it has, we can go from there trying to figure it out.  If not, trying to go backwards in libraries to get something like this to work can be a nightmare.

Dave ;)

It ran great for a while when I first installed it, then it crashed and is nada now. Looks like I will have to hope Hulu will update the Ubuntu .deb package.

---

### Post by oldos2er on 2012-04-09
Have you tried removing its configuration directory? ```
rm -r .huludesktop && huludesktop
```

---

### Post by anewguy on 2012-04-09
> **theducksfan2010 said:**
> It ran great for a while when I first installed it, then it crashed and is nada now. Looks like I will have to hope Hulu will update the Ubuntu .deb package.

Hummmm.....I wonder if you had updates go through and if they included a kernel update.  If so, it's possible, as a non-supported product, that you may need to re-install as well. 

Guess if it did run it must not be GTK differences at this point.

Try what oldos2r recommended, then if that doesn't work I'd try a reinstall - especially if the install involved running make.


Dave ;)

---

### Post by theducksfan2010 on 2012-04-09
> **anewguy said:**
> Hummmm.....I wonder if you had updates go through and if they included a kernel update.  If so, it's possible, as a non-supported product, that you may need to re-install as well. 

Guess if it did run it must not be GTK differences at this point.

Try what oldos2r recommended, then if that doesn't work I'd try a reinstall - especially if the install involved running make.


Dave ;)

I uninstalled it using the software center and then tried oldo2r recommendation


josh@josh-Compaq-Presario-CQ60-Notebook-PC:~$ rm -r .huludesktop && huludesktop
huludesktop: command not found
josh@josh-Compaq-Presario-CQ60-Notebook-PC:~$ 

should i go for a fresh install now?

---

### Post by anewguy on 2012-04-09
I would give that a try - can't hurt at this point.

Dave ;)

---

### Post by anewguy on 2012-04-10
Just FYI - I downloaded this and let software center install it and it appears to work.  Maybe either a reinstall or a new download and install.

Dave ;)

---

### Post by theducksfan2010 on 2012-04-10
> **anewguy said:**
> Just FYI - I downloaded this and let software center install it and it appears to work.  Maybe either a reinstall or a new download and install.

Dave ;)

So I did a fresh install and it worked great, until I tried to put it into full-screen. The same place it disappeared last time. 

I am on Ubuntu 11.10 What OS are you running anewguy??

---

### Post by anewguy on 2012-04-10
> **theducksfan2010 said:**
> So I did a fresh install and it worked great, until I tried to put it into full-screen. The same place it disappeared last time. 

I am on Ubuntu 11.10 What OS are you running anewguy??

Hummmm.......11.10, but I forgot to try full-screen!   Hang on a second and I'll try it....

Yep - same problem.  Can't get it to work in full screen, however you can go back to windowed mode by editing the ~/.huludesktop file and changing "fullscreen = TRUE" to "fillscreen = FALSE" and then save the file and restart huludesktop.

That at least gets it back, just haven't figure out full screen yet.  I found you really don't want to click in the viewing area and change flash settings as, at least for me, it won't let me save it and won't close the pop-up -> I had to exit huludesktop and start again.

I know this doesn't solve the full screen thing yet, but it gives you a way back to windowed mode without removing/reinstalling.

Dave ;)

---

### Post by anewguy on 2012-04-10
I tried this with Unity 2-d and at least it didn't abort flat-out instead it went back to the windowed mode.  So, I suspect this is really a problem trying to run this on unity.  I'm installing the gnome-shell package right now to see if it runs okay in that.  I'll post back when I know.

Dave ;)

---

### Post by anewguy on 2012-04-10
After installing the gnome-shell package, I tried logging in with gnome, gnome classic and gnome classic no effects.  They all behave the same.  I also noticed that if you go to the bottom right corner of the window while it is running and try to drag it to make it bigger it aborts immediately.

I suspect this application was not written with resizing the default window in mind at this point.  This would appear to me to be an application problem.  The same problem was reported in earlier and other distributions of Linux, so it's not unique.

Right now I'd say there is no "fix", and you're stuck running in a windowed mode.  You may try contacting hulu via the contact us link on the bottom of the page you linked to and ask them if they intend to support resizing the window.

Dave ;)

---

### Post by mishdanicko on 2012-05-01
I got it working, though I can't say I entirely remember how; I was having the immediate shutdown issue described here for the longest time, but now it works and even maximizes and restores properly.  Here's the "display" section of my configuration file; maybe it will help someone:

```
[display]
fullscreen = TRUE
width = 1366
height = 768
pos_x = 0
pos_y = 47
```

I'm running Xubuntu 10.04 LTS on a Dell Dimension E510 desktop.

---

### Post by sleepitoff on 2012-05-18
I'm experiencing the fullscreen crash as well on Kubuntu. These are the errors when I start huludesktop in the terminal: 


> Failed to open VDPAU backend libvdpau_nvidia.so: cannot open shared object file: No such file or directory

(huludesktop:8994): Gdk-WARNING **: gdk_window_new(): parent is destroyed


(huludesktop:8994): Gdk-CRITICAL **: IA__gdk_window_get_display: assertion `GDK_IS_WINDOW (window)' failed

(huludesktop:8994): Gdk-CRITICAL **: IA__gdk_x11_get_xatom_by_name_for_display: assertion `GDK_IS_DISPLAY (display)' failed

(huludesktop:8994): Gdk-WARNING **: /build/buildd/gtk+2.0-2.24.10/gdk/x11/gdkdrawable-x11.c:952 drawable is not a pixmap or window

(huludesktop:8994): Gdk-CRITICAL **: IA__gdk_x11_display_get_xdisplay: assertion `GDK_IS_DISPLAY (display)' failed
Segmentation fault (core dumped)

---

### Post by petershem on 2012-05-20
sleepitoff, I had the same errors in terminal, so I went into the configuration file (~/.huludesktop) and changed the display width and height to match the width and height under my display settings. That is all I changed and it worked great.

Hope that helps!

---

### Post by sleepitoff on 2012-05-21
I'm using two monitors (1366x768 and 1360x768) and if edit the height and width options of the .huludesktop file to match one of the monitors' resolutions, Hulu crashes immediately when I launch it. It is working with 1280x720 set for the resolution, but it still can't go fullscreen or resize without crashing. Also, changing the "fullscreen = false" option to "fullscreen = true" doesn't help it, either, it just causes Hulu to crash at launch. 

Any ideas?

---

### Post by rokytnji on 2012-06-28
@oldos2er

```
rm -r .huludesktop && huludesktop
```

```
$ inxi -F -z
System:    Host: owner-desktop Kernel: 2.6.32-41-generic x86_64 (64 bit) Desktop: Gnome 2.30.2 Distro: Ubuntu 10.04 lucid
Machine:   Mobo: ASUSTeK model: M2A-VM version: 1.XX Bios: Phoenix version: ASUS M2A-VM 1604 date: 12/19/2007
CPU:       Dual core AMD Athlon 64 X2 4200+ (-MCP-) cache: 1024 KB flags: (lm nx sse sse2 sse3 svm) 
           Clock Speeds: 1: 2200.029 MHz 2: 2200.029 MHz
Graphics:  Card: nVidia G71 [GeForce 7900 GS] X.Org: 1.7.6 driver: nvidia Resolution: 1920x1080@50.0hz 
           GLX Renderer: GeForce 7900 GS/PCI/SSE2 GLX Version: 2.1.2 NVIDIA 195.36.24
Audio:     Card: ATI SBx00 Azalia (Intel HDA) driver: HDA Intel Sound: ALSA ver: 1.0.21
Network:   Card: Realtek RTL8111/8168B PCI Express Gigabit Ethernet controller driver: r8169 
           IF: eth0 state: unknown speed: N/A duplex: N/A mac: <filter>
Drives:    HDD Total Size: 320.1GB (17.9% used) 1: id: /dev/sda model: WDC_WD3200AAKS size: 320.1GB 
Partition: ID: / size: 288G used: 54G (20%) fs: ext4 ID: swap-1 size: 6.17GB used: 0.00GB (0%) fs: swap 
RAID:      No RAID devices detected - /proc/mdstat and md_mod kernel raid module present
Sensors:   System Temperatures: cpu: 59.0C mobo: 48.0C gpu: 67C 
           Fan Speeds (in rpm): cpu: 5578 psu: 0 sys-1: 1016 
Info:      Processes: 163 Uptime: 2:16 Memory: 857.6/2008.4MB Client: Shell inxi: 1.8.5 

```

```
~$ apt-cache policy huludesktop
huludesktop:
  Installed: 0.9.8-1
  Candidate: 0.9.8-1
  Version table:
 *** 0.9.8-1 0
        100 /var/lib/dpkg/status

```

Thanks for that. I was fighting huludesktop today. It would only load a black screen with the right path to flash in ~/.huludesktop.

```
~$ locate  libflashplayer.so
/usr/lib/flashplugin-installer/libflashplayer.so
/usr/lib/mozilla/plugins/libflashplayer.so

```

 Tried reinstall with 64 bit huludesktop. It would not work till I did that command. 

Again thanks. I'd give you a thanks for that but no button here that I can see.

[ATTACH]220372[/ATTACH]

---

### Post by w1ll1am on 2012-07-06
> **mishdanicko said:**
> I got it working, though I can't say I entirely remember how; I was having the immediate shutdown issue described here for the longest time, but now it works and even maximizes and restores properly.  Here's the "display" section of my configuration file; maybe it will help someone:

```
[display]
fullscreen = TRUE
width = 1366
height = 768
pos_x = 0
pos_y = 47
```

I'm running Xubuntu 10.04 LTS on a Dell Dimension E510 desktop.

This worked perfect for me thanks

---

### Post by tjeremiah on 2012-07-20
I set it to true too. But if some are having problems like the Hulu player going back to false, lock the file so that no changes can occur without your permission.

---

### Post by skitheo on 2012-09-16
The secret seems to be in setting the height and width attributes to  your actual screen size. Now working in Ubuntu Studio 12.04 64-bit with nVidia  304.43 drivers.

---

