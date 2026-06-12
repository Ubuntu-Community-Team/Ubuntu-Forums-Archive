---
title: "CLI Only Distro"
date: 2007-07-01
forum: Other OS Talk
---

### Post by bobbocanfly on 2007-07-01
I am looking for s imple, lightweight CLI Only distro to dump in a 500mb or less partition. I need it to do simple editing of text files, (like /boot/grub/menu.lst) without having to wait 3 or 4 minutes while Ubuntu or Fedora boot up their nice shiny X Servers. (That having to wait 4 minutes to boot then to change a single line, so i could boot ubuntu properly almost killed me)

Does anyone know of a CLI only Distro, 500mb or less, and preferably boots quickly and has nano?

---

### Post by mang on 2007-07-01
Slackware is pretty awesome!  It was my first distro back in the day  and I used it for a long time until I tried ubuntu.  Slackware is pretty much what you want.  Just do a minimal install.  Just make sure that you're comfortable installing everything from source.

Heck even FreeBSD would be good for that and it has an awesome ports system.

---

### Post by smoker on 2007-07-01
you could give 'barebones puppy' or 'onebone puppy - CLI version' a try:
[http://www.puppylinux.org/user/downloads.php?cat_id=1](http://www.puppylinux.org/user/downloads.php?cat_id=1)

they don't have nano, though you can install extas from the puppy 'dotpup' and 'pupget' repositories, you may find nano there.

---

### Post by deanlinkous on 2007-07-01
debian

---

### Post by celsofaf on 2007-07-01
Even Arch would do a great job here.

---

### Post by diatribe on 2007-07-01
hell you can run ubuntu without a gui

---

### Post by bobbocanfly on 2007-07-01
My options (as i see them) here are:

1) I customise my own version of Slax Frodo Edition (Add in some modules etc.) and install it to the Hard Disk. Pros: Lightweight, fast, easy to customise later, Cons: Hard disk install isnt fully supported (Slax is a LiveCD distro)

2) I use Arch Linux or Debian (minimal) installs. Pros: Fully supported HD install, Cons: Might be a bit heavy and would mean more messing about with Grub (which i hate doing)

Slackware seems a bit beyond my level at the moment, not very good at compiling things from source.

---

### Post by deanlinkous on 2007-07-01
Whats heavy about debian? What would you need to mess with concerning grub?

---

### Post by init1 on 2007-07-01
> **bobbocanfly said:**
> I am looking for s imple, lightweight CLI Only distro to dump in a 500mb or less partition. I need it to do simple editing of text files, (like /boot/grub/menu.lst) without having to wait 3 or 4 minutes while Ubuntu or Fedora boot up their nice shiny X Servers. (That having to wait 4 minutes to boot then to change a single line, so i could boot ubuntu properly almost killed me)

Does anyone know of a CLI only Distro, 500mb or less, and preferably boots quickly and has nano?
TTY is nice, no nano, but it is only 5MB (yes, only 5) and it has an installer. You can always just bring in nano or e3 (very small text editor, e3pi has nano-like keybindings). Also try Slax frodo. PLD is only a live CD but I like it.

---

### Post by bobbocanfly on 2007-07-02
> **deanlinkous said:**
> Whats heavy about debian? What would you need to mess with concerning grub?

I would need to mess around with GRUB so i could boot into it? This 5mb TTY thing sounds exactly like what i wanted! I could just install Nano and a few other tools and im set.

---

### Post by arron on 2007-07-02
You could use the Ubuntu server edition that is only command line.  Debian base install with no x is very small as well.  If you want some X try out fluxbox (available in ubuntu and debian aptitude).  There is even a fluxbox distro comen out that will be very lightweight.  Fluxbox is even lighter than xfce.

---

### Post by dca on 2007-07-02
Yeah, I concur, Ubuntu 6.06LTS Server Ed if it's important work...  Very solid....

---

### Post by darkog on 2007-07-02
i used to use [BSDLive]("http://www.meowfishies.com/software/bsdlive"). 

I don't know what happened to the main page. But [ here]("http://taosecurity.blogspot.com/search?q=bsdlive") is a screen.

It's pretty cool. Fit on a 50mb mini CD.

---

### Post by bobbocanfly on 2007-07-02
Decided to go with TTYLinux (Link is [http://www.minimalinux.org/ttylinux/](http://www.minimalinux.org/ttylinux/) if anyone cares). Linux in > 5mb might be interesting.

Edit : Actually, no im not! The docs say that you must install LILO to your hard drive to finish the install, which i dont want to do. SLAX Frodo it is

---

### Post by init1 on 2007-07-02
> **bobbocanfly said:**
> Decided to go with TTYLinux (Link is [http://www.minimalinux.org/ttylinux/](http://www.minimalinux.org/ttylinux/) if anyone cares). Linux in > 5mb might be interesting.

Edit : Actually, no im not! The docs say that you must install LILO to your hard drive to finish the install, which i dont want to do. SLAX Frodo it is
You can tell it not to, but I couldn't figure out how to use another boot loader. It is a weird set up.

---

### Post by SkyNet2029 on 2007-07-04
Try this one out, it is a 1.44MB.. yes. as in a floppy image in size. You could just do a 

#dd if=one_disk_x.img of=your_install_media

and go from there.

Here is the official description:
------------------------------------------------------------------Begin
Title: 1diskx
Version: 1diskx-1.2.3
Entered-date: 2003-11-10
Description: tiny linux thin client with X window system, vnc, rdesktop, file manager, window manager, web browser, terminal, ssh, many other utils. all on one floppy disk.
Keywords: linux, linux distribution, thin client, X window system, vnc, rdesktop, file manager, web browser.
Author: [email]mungkie@hotmail.com[/email]
Maintained-by: [email]mungkie@hotmail.com[/email]
Primary-site: 	1diskx-1.2.3.tar.tgz
Original-site: [http://freshmeat.net/projects/natld/](http://freshmeat.net/projects/natld/)
Platforms: i386 with 8Mb, vesa gfx, (many others from source)
Copying-policy: free for non comercial use / GNU / X11 / other proprietary licence.
End
----------------------------------------------------------------------------------------------End

I host a copy on my website, it is located in the Archives. 
direct link to directory:
[http://www.theunixproject.orgdiskx]("http://www.theunixproject.org")

---

### Post by init1 on 2007-07-06
> **SkyNet2029 said:**
> Try this one out, it is a 1.44MB.. yes. as in a floppy image in size. You could just do a 

#dd if=one_disk_x.img of=your_install_media

and go from there.

Here is the official description:
------------------------------------------------------------------Begin
Title: 1diskx
Version: 1diskx-1.2.3
Entered-date: 2003-11-10
Description: tiny linux thin client with X window system, vnc, rdesktop, file manager, window manager, web browser, terminal, ssh, many other utils. all on one floppy disk.
Keywords: linux, linux distribution, thin client, X window system, vnc, rdesktop, file manager, web browser.
Author: [email]mungkie@hotmail.com[/email]
Maintained-by: [email]mungkie@hotmail.com[/email]
Primary-site: 	1diskx-1.2.3.tar.tgz
Original-site: [http://freshmeat.net/projects/natld/](http://freshmeat.net/projects/natld/)
Platforms: i386 with 8Mb, vesa gfx, (many others from source)
Copying-policy: free for non comercial use / GNU / X11 / other proprietary licence.
End
----------------------------------------------------------------------------------------------End

I host a copy on my website, it is located in the Archives. 
direct link to directory:
[http://www.theunixproject.orgdiskx]("http://www.theunixproject.org")
This is two disk. I don't think that would work.

---

### Post by SkyNet2029 on 2007-07-08
> **init1 said:**
> This is two disk. I don't think that would work.

err, it's all on one floppy actually. See the .lsm for the specifics...

[http://75.92.23.17:8002/pub/1diskx/1diskx-1.2.3.lsm]("http://75.92.23.17:8002/pub/1diskx/1diskx-1.2.3.lsm")

---

### Post by happy-and-lost on 2007-07-09
Debian Sid base netinstall. Takes 12 seconds to boot on my oldish box :D

---

### Post by init1 on 2007-07-09
> **SkyNet2029 said:**
> err, it's all on one floppy actually. See the .lsm for the specifics...

[http://75.92.23.17:8002/pub/1diskx/1diskx-1.2.3.lsm]("http://75.92.23.17:8002/pub/1diskx/1diskx-1.2.3.lsm")
> About:
**2-Disk** X window embedded Linux is a tiny net-centric Linux that aims at portable secure remote system usage. It contains many utilities including: X Windows, vncviewer, rdesktop, a Web browser, a file manager, a text editor, a terminal, a window manager, a menu system, a dialog system, X scripting facilities, and many others. It aims to work from **1 or 2 floppy disks** in any remote location.

OK, I didn't see the bottom part.

---

### Post by Belathor on 2007-07-11
[grml]("http://www.grml.org")

---

### Post by thully on 2007-07-13
You always can set Ubuntu to load to a CLI by default - they you'll get a text-mode login screen and have to use the "startx" command to start X.  I know that you edit the /etc/inittab to do this - search around and you should find the correct option.

---

