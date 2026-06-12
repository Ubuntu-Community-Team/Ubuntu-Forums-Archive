---
title: "[SOLVED] Desktop screen has gone white"
date: 2008-09-30
forum: New to Ubuntu
---

### Post by jrsc109 on 2008-09-30
Please please help.

I am running Ubuntu 8.04 on a dual-boot (tg) with WinXP.

When I boot to Linux, I can login in OK, then the screen just goes white.
Nothing is available to be seen.  It is pure white.  No images, no links; no boxes, absolutely nothing.

I was playing with the settings for VirtualBox; and restarted as per the instructions in a thread I was reading on their forum.

However, I now cannot get back to the file I amended, so have now way to change back to how it was.

Is there anyway to resolve this; i.e. like getting at the Linux files via Windows.

I have a horrible feeling I'm going to have to start again :(

Please help me.

Thanks

---

### Post by ubunt2guy on 2008-09-30
> **jrsc109 said:**
> Please please help.

I am running Ubuntu 8.04 on a dual-boot (tg) with WinXP.

When I boot to Linux, I can login in OK, then the screen just goes white.
Nothing is available to be seen.  It is pure white.  No images, no links; no boxes, absolutely nothing.

I was playing with the settings for VirtualBox; and restarted as per the instructions in a thread I was reading on their forum.

However, I now cannot get back to the file I amended, so have now way to change back to how it was.

Is there anyway to resolve this; i.e. like getting at the Linux files via Windows.

I have a horrible feeling I'm going to have to start again :(

Please help me.

Thanks

i had a similar problem with an old Dell laptop when I Enabled Desktop Effects.  I would reboot and then I would get a blank screen.  I have a feeling it may be a driver issue. 

not much help but good luck

---

### Post by waspbr on 2008-09-30
I think I had a problem like that at some point, dunno exactly how I solved it, I reckon I installed new drivers with envy...

anyway, to access your desktop, login into your account 

then the screen turns white right?

you may need to do this last bit without seeing

press alt+F2

then type 

```
metacity --replace
```

press enter

you should be able to see your desktop now...

alternatively I am not sure if this will work but, once you are logged onto your "whitened account"press alt+ctrl+F1, this will bring you to the command line mode, then type the same code, return by pressing alt+ctrl+F7 (or F6 either one)

---

### Post by nightcrawler27 on 2008-09-30
You mention VirtualBox...is this actually a dual-boot system (e.g you have two separate disk partitions each with a different operating system installed), or are you running Windows with Ubuntu as a virtual machine inside VirtualBox for Windows?

Also is your desktop typically white? If so maybe your virtual machine's resolution is cranked up too high and the taskbar/desktop icons are getting cut off. Do you even get the mouse pointer? If you don't even have that, but you are at least able to get to login, try switching to console login instead of graphical login. Then go to your home folder and move the profile folders to some other name (for the GNOME desktop, these folders might be .gnome, .gnome2, etc). then logout, switch back to graphical login, and log back in. Your desktop profile should get rebuilt. I screwed up my desktop big time once and that did the trick for me.

Nightcrawler27.


> **jrsc109 said:**
> Please please help.

I am running Ubuntu 8.04 on a dual-boot (tg) with WinXP.

When I boot to Linux, I can login in OK, then the screen just goes white.
Nothing is available to be seen.  It is pure white.  No images, no links; no boxes, absolutely nothing.

I was playing with the settings for VirtualBox; and restarted as per the instructions in a thread I was reading on their forum.

However, I now cannot get back to the file I amended, so have now way to change back to how it was.

Is there anyway to resolve this; i.e. like getting at the Linux files via Windows.

I have a horrible feeling I'm going to have to start again :(

Please help me.

Thanks

---

### Post by sdowney717 on 2008-09-30
simply start up in recovery mode.
get to a command prompt

type in sudo dpkg-reconfigure -phigh  xserver-xorg

or simply start up in recovery mode, get to the menu, select try to fix xserver.
then just continue on with normal boot

[http://ubuntuforums.org/showthread.php?t=759309](http://ubuntuforums.org/showthread.php?t=759309)

---

### Post by jrsc109 on 2008-09-30
> **waspbr said:**
> I think I had a problem like that at some point, dunno exactly how I solved it, I reckon I installed new drivers with envy...

anyway, to access your dektop, login into your account 

then the screen turn white right?

you may need to do this last bit without seeing

press alt+F2

then type 

```
metacity --replace
```

press enter

you should be able to see your desktop now...

alternatively I am not sure if this will work but, once you are logged onto your "whitened account"press alt+ctrl+F1, this will bring you to the command line mode, then type the same code, return by pressing alt+ctrl+F7 (or F6 either one)

Brill - that worked (The first option).  Phew!!

---

