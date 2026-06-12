---
title: "default boot"
date: 2008-08-27
forum: New to Ubuntu
---

### Post by navaneethan on 2008-08-27
i installed xp and ubuntu
may possible xp is default?
how?

---

### Post by david sousa on 2008-08-27
At thee booting screen you have an option to edit the ptions that appear there. 

At windows you have something to and it's easier but i don't remeber so you have to google.

At linux i don't really know.

---

### Post by panhandle on 2008-08-27
You most likely need to change these settings in BIOS.

---

### Post by sandysandy on 2008-08-27
> **navaneethan said:**
> i installed xp and ubuntu
may possible xp is default?
how?

just repeat ur problem again in more detail as also what u want to do.:)

regards

---

### Post by porchrat on 2008-08-27
I assume what you want is to make windows xp boot as the default operating system on a machine that is dual-booting windows xp and ubuntu.

What you need to do is edit your GRUB menu in /boot/grub/menu.lst

type:
```
gksudo /boot/grub/menu.lst
```

near the bottom you'll see an entry for windows xp.  You need to move that entry above the top-most ubuntu 8.04 entry to ensure that GRUB will boot xp as default unless you select something else from the list

I can give you a more detailed explanation when I;m in front of the linux machine.

---

### Post by drs305 on 2008-08-27
If you have the grub menu on startup:
Install StartUp-Manager:
```
sudo aptitude install startupmanager
```

Start StartUp-Manager: System, Administration, StartUp-Manager

In the Boot Options, Default Operating System, select Windows. Close.

---

### Post by porchrat on 2008-08-27
that is a nice package.  What an awesome idea.  GUI for bootloader and splash.

I am going to recommend that to people unfamiliar with the GRUB menu from now on.

Thanks for the helpful hint =D>

---

### Post by drs305 on 2008-08-27
> **porchrat said:**
> that is a nice package.  What an awesome idea.  GUI for bootloader and splash.

I am going to recommend that to people unfamiliar with the GRUB menu from now on.

Thanks for the helpful hint =D>

I've written a fairly comprehensive tutorial on StartUp-Manager. The link's in my sig line but here it is anyway:
[http://ubuntuforums.org/showthread.php?t=818177](http://ubuntuforums.org/showthread.php?t=818177)

---

