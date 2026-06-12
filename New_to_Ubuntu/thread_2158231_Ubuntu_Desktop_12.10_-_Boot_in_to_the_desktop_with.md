---
title: "Ubuntu Desktop 12.10 - Boot in to the desktop without screen, keyboard &amp; mouse?"
date: 2013-06-28
forum: New to Ubuntu
---

### Post by AxelVK on 2013-06-28
Hello,This is my situation; I have a HP Proliant N54L Microserver with Ubuntu Desktop 12.10. I am using it as a server however, running Plex Media Server. As such, I don't normally have screen, keyboard and mouse plugged in. I have set up the server to 'auto login' which works. It would be really nice if I could access the Unity Desktop via my PC. This works fine using VNC Viewer if I have a screen, keyboard and mouse plugged in but if I leave those bits unplugged, the server appears to start in "low graphics mode" and if I try VNC, I get the message "connect: Connection refused (10061)". This tells me that access via VNC Viewer only works if I login 'the normal way first but of course, I cannot do that without screen, keyboard and mouse.      Is there a solution to this?

---

### Post by AxelVK on 2013-06-28
Bump

---

### Post by JKyleOKC on 2013-06-28
Rather than using VNC, try SSH (Secure SHell) for your remote access. At the server end, install the SSHD server package, and at the remote end, install SSHD's client. You can then tell the server to connect its X Windows display to your connection, and get the display at your remote site. Here's the command I use at the remote end; the "-Y" argument is what tells the server to connect the display to me. The address is that of the server on my LAN (changed to protect my privacy of course).
```
ssh -Y me@192.168.0.3
```
This does get you a CLI (text mode) login, but you can then use the command "startx" to bring up the usual desktop.
Using SSH is much safer than using VNC, although if your LAN is well protected that's not so much of an issue as it would be if you were connecting via the Internet...

---

### Post by AxelVK on 2013-06-29
> **JKyleOKC said:**
> Rather than using VNC, try SSH (Secure SHell) for your remote access. At the server end, install the SSHD server package, and at the remote end, install SSHD's client. You can then tell the server to connect its X Windows display to your connection, and get the display at your remote site. Here's the command I use at the remote end; the "-Y" argument is what tells the server to connect the display to me. The address is that of the server on my LAN (changed to protect my privacy of course).
```
ssh -Y me@192.168.0.3
```
This does get you a CLI (text mode) login, but you can then use the command "startx" to bring up the usual desktop.
Using SSH is much safer than using VNC, although if your LAN is well protected that's not so much of an issue as it would be if you were connecting via the Internet...

Thanks for your reply. I tried that, this is what I got:X.Org X Server 1.13.0
Release Date: 2012-09-05
X Protocol Version 11, Revision 0
Build Operating System: Linux 3.2.0-37-generic x86_64 Ubuntu
Current Operating System: Linux HP-ProLiant-MicroServer 3.5.0-34-generic #55-Ubuntu SMP Thu Jun 6 20:18:19 UTC 2013 x86_64
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.5.0-34-generic root=UUID=d404078e-345b-4664-a37e-31699c802caa ro quiet splash
Build Date: 11 April 2013  12:53:36PM
xorg-server 2:1.13.0-0ubuntu6.2 (For technical support please see [http://www.ubuntu.com/support](http://www.ubuntu.com/support))
Current version of pixman: 0.26.0
        Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
        to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
        (++) from command line, (!!) notice, (II) informational,
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.1.log", Time: Sat Jun 29 15:32:03 2013
(==) Using system config directory "/usr/share/X11/xorg.conf.d"
setversion 1.4 failed
Initializing built-in extension Generic Event Extension
Initializing built-in extension SHAPE
Initializing built-in extension MIT-SHM
Initializing built-in extension XInputExtension
Initializing built-in extension XTEST
Initializing built-in extension BIG-REQUESTS
Initializing built-in extension SYNC
Initializing built-in extension XKEYBOARD
Initializing built-in extension XC-MISC
Initializing built-in extension SECURITY
Initializing built-in extension XINERAMA
Initializing built-in extension XFIXES
Initializing built-in extension RENDER
Initializing built-in extension RANDR
Initializing built-in extension COMPOSITE
Initializing built-in extension DAMAGE
Initializing built-in extension MIT-SCREEN-SAVER
Initializing built-in extension DOUBLE-BUFFER
Initializing built-in extension RECORD
Initializing built-in extension DPMS
Initializing built-in extension X-Resource
Initializing built-in extension XVideo
Initializing built-in extension XVideo-MotionCompensation
Initializing built-in extension XFree86-VidModeExtension
Initializing built-in extension XFree86-DGA
Initializing built-in extension XFree86-DRI
Initializing built-in extension DRI2
Loading extension GLX
(II) [KMS] Kernel modesetting enabled.
setversion 1.4 failed

---

### Post by JKyleOKC on 2013-06-29
This line in your log appears to be what is holding you up:
> (II) [KMS] Kernel modesetting enabled.

There's a kernel option "nomodeset" available, but it must be invoked when you boot the system, and I'm not at all certain that doing so would make it all work as desired -- you could run into another problem later. The basic problem is that the initialization code at boot time attempts to set up the keyboard, mouse, and display, and when you are running headless they aren't there to be set up.

I run one virtual machine headless on my LAN, and access it through "rdesktop" with no problem. However as a virtual machine, it has a virtual display, keyboard, and mouse, so its system sets then up normally and the VirtualBox program takes care of relaying everything to my remote connection. I really have no idea how to make this happen on a non-virtual headless system, unfortunately.

Perhaps someone else will jump in here with some ideas.

---

