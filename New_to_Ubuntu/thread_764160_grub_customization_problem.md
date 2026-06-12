---
title: "grub customization problem"
date: 2008-04-23
forum: New to Ubuntu
---

### Post by capleton on 2008-04-23
This is my second day using Ubuntu, It's PHENOMENAL.  I can't wait to see where this takes me!

I had a few issues installing, but after I wiped and re-installed vista, I finally got everything set up into dual boot.

I'm trying to customize the GRUB screen now.  Went to the Synaptic Package Manager, and installed gfxboot as well as gfxboot-theme-ubuntu

-->But when I go to System>Administration>Startup Manager  there are no options to select under "bootloader themes" in the 'Appearence' tab.  **How can I enable these "Bootloader Themes"?**

Oh, and I am using 8.04 Hardy Heron RC

---

### Post by otrojake on 2008-04-23
Run this code in a terminal (Applications-->Accessories-->Terminal):

```
sudo apt-get install grub-splashimages
```

or if you'd rather not go through the terminal, go to Synaptic (System-->Administration-->Synaptic Package Manager) and search for the package "grub-splashimages" (no quotes), check, then apply changes.

and then restart the Startup Manager.  That should give you some themes.  Glad you're enjoying the wonderful world of Ubuntu Linux!:)

---

### Post by capleton on 2008-04-23
Sweet!  it worked!

The result is good, but it's not exactly what I was expecting.  I had originally seen a screenshot similar to the one in [this ]("http://www.imgx.org/public/view/full/4637")thread, and that's kind of what I was trying to make happen 
(when I try to follow the instructions on that thread, they don't really seem to work 'i get an error in the installer
> error: conflicts with the installed package 'grub')  

[**Is getting a screen like this something relatively easy to do?**]("http://www.imgx.org/public/view/full/4637")

Thanks for the help!

---

### Post by PeterJS on 2008-04-23
If you look at the first instruction of the thread you linked to the first thing your supposed to do is uninstall your old grub. The error message you're getting is that it can't install gfx-grub because grub is still installed. I tried to install gfx-grub on a VM and it didn't work, I was never brave enough to try it on bare metal.

---

### Post by maddog39 on 2008-04-23
Hmmm... it looks like the guy in the post you linked to had some custom stuff but I'm not totally sure. Although it may not matter, you can change the picture used for graphical grub in /boot/grub/menu.lst but I don't know exactly what you change and what not but look into it.

---

### Post by capleton on 2008-04-23
AWESOME!

I uninstalled grub like you said, then followed [this post ]("http://tuxenclave.wordpress.com/2008/01/18/how-to-install-gfx-grub-in-ubuntu/")more closely, result:  Boot screen is absolutely amazing!  I can customize it relatively easily from the .lst file.

Seriously,I don't know how I could have used  windows for so long; ubuntu is SOOOO much better.

Thanks for all the help!

---

