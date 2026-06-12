---
title: "Runlevel issue"
date: 2012-11-29
forum: New to Ubuntu
---

### Post by myralfa on 2012-11-29
Hello all, I've virtualised Ubuntu to be able to run a script I need.
Thing is, I'm having heavy issues in going into text mode.
Whenever I set the runlevel to 1 or 3, Ubuntu just ignores it and keeps loading the desktop.
Could someone tell me how to set it properly?
I'm using ubuntu 12.10 if that matters.

---

### Post by Paddy Landau on 2012-11-29
What exactly are you trying to do? Do you want to use a terminal for the command-line interface? If so, just start the Terminal application after your desktop has opened.

---

### Post by myralfa on 2012-11-29
> **Paddy Landau said:**
> What exactly are you trying to do? Do you want to use a terminal for the command-line interface? If so, just start the Terminal application after your desktop has opened.

Everything that needed to be done has been done.
Now I only need Ubuntu to boot as fast as possible, that's why I want it to boot in text mode.

---

### Post by sisco311 on 2012-11-29
Ubuntu uses Upstart, so runlevels are deprecated. 

See: [http://upstart.ubuntu.com/index.html](http://upstart.ubuntu.com/index.html)

You can disable the DM with an Upstart .override file or by booting with the `text' kernel parameter or could simply uninstall lightdm (the desktop manager).

But, I hope that you don't mind if I echo Paddy Landau question: What exactly are you trying to do?

---

### Post by myralfa on 2012-11-29
> **sisco311 said:**
> Ubuntu uses Upstart, so runlevels are deprecated. 

See: [http://upstart.ubuntu.com/index.html](http://upstart.ubuntu.com/index.html)

You can disable the DM with an Upstart .override file or by booting with the `text' kernel parameter or could simply uninstall lightdm (the desktop manager).

But, I hope that you don't mind if I echo Paddy Landau question: What exactly are you trying to do?
Thanks.

What I'm trying to do is run Ubuntu in text (console) mode.
I only need it to run a script, but I have a small window of time to run it, so I need Ubuntu to boot as fast as possible, and Gnome/KDE obviously make it boot much slower.

---

### Post by sisco311 on 2012-11-29
> **myralfa said:**
> 
I only need it to run a script, 

Then check out the link I posted and disable all the daemons/services that your script does not need.

If you are unsure about or don't know which services to disable, then you have to tell us a little more about the script you are trying to run...

---

### Post by drvdw on 2013-03-17
I want to configure grub to allow me to choose different runlevels at the boot menu.  Unfortunately, it seem that because ubuntu uses upstart now, this is not possible.

Edit: I was wrong.  Simply adding a kernel parameter of '3' with grub booted into runlevel 3.

---

### Post by Paddy Landau on 2013-03-18
> **drvdw said:**
> I want to configure grub to allow me to choose different runlevels at the boot menu.  Unfortunately, it seem that because ubuntu uses upstart now, this is not possible.
@drvdw, this is a different issue. Please start a new thread for your problem.

---

