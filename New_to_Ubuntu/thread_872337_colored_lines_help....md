---
title: "colored lines? help..."
date: 2008-07-27
forum: New to Ubuntu
---

### Post by Telperion6 on 2008-07-27
Hey everybody,

I decided to try dual-booting Xubuntu on my laptop as an alternative to the preloaded Vista. I downloaded the ISO image and burned it onto a CD, partitioned the hard drive using Vista, and tried to install. As soon as the statusbar (I assume it's the one that indicates how much of the installer is loaded) is full, the screen goes black twice, and then white...and then colored vertical lines appear. Slowly.

I tried running Xubuntu from CD in safe graphics mode and it looks fine.

---

### Post by candtalan on 2008-07-28
When I have installed from the live CD - from the desktop install icon - I have found that the install uses the same graphics settings as seen in the live CD session. If you installed directly without the live CD session then - since it looks like there is a video settings or video card recognition problem - you will need a way of declaring that you need safe graphics for the install, I am not sure I know how to do that just now.

However, fwiw, the files contents and settings which the live cd uses in safe graphics will also be useful to you with your current (problematic) install particularly the contents of the file
/etc/X11/xorg.conf

If you could (somehow) copy this file from a live CD session and paste it into the installed session using cl methods, it would work I think. I do this with an old laptop I have which is an unusuualy difficult install problem.

btw if your laptop is anywahere vista capable then you will get a good response using Ubuntu, without going to xubuntu, which is a little lean on facilities. Once installed you can have sessions for xubuntu, ubuntu, and if you ar elike me , also kubuntu!

good luck

---

### Post by Telperion6 on 2008-07-28
I managed to install it properly by starting up the CD in Vista and working from there. It looks fine now... :-k

---

### Post by Telperion6 on 2008-07-28
P.S.: I was trying to adjust the display resolution and broke it.

This is how I ended up fixing it:

[LIST=1]
[*]I booted the computer to the recovery mode (option #2 on GRUB).
[*]From there I selected the third option - the one that opens a terminal.
[*]I navigated to /etc/X11/ and opened xorg.conf.
[*]In the Device section, I added the line ```
driver\t"vesa"
```
[*]Saved, quit, and rebooted.
[/LIST]

---

### Post by jay019 on 2008-07-28
> **Telperion6 said:**
> I managed to install it properly by starting up the CD in Vista and working from there. It looks fine now... :-k

Wow, vista has its uses :-P

---

### Post by kool_kat_os on 2008-07-28
you lucky duck...my laptop did that with win 98 and then after a week it would turn on anymore:)

---

