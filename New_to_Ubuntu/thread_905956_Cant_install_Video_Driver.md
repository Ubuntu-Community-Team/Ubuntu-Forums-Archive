---
title: "Cant install Video Driver"
date: 2008-08-30
forum: New to Ubuntu
---

### Post by Codemastadink on 2008-08-30
I am trying to install a video driver for my Nvidia Geforce 6800. I followed the directions on the site, downloaded the driver and when i went to install i followed the directions from the site ""Type "sh NVIDIA-Linux-x86-173.14.12-pkg1.run" to install the driver.""   I did this, and got the message

```
sh: Can't open NVIDIA-Linux-x86-173.14.12-pkg1.run
```

Anyone know how to fix this?

---

### Post by alienexplorers on 2008-08-30
Forget about doing it that way and use envy found in the repositories.  Download envy-core and envy-gtk.  Run envyng from the applications>system tools and it will automatically set up your driver.  Alot easier than doing it by hand.

---

### Post by Shazaam on 2008-08-30
You need to put sudo in front of the sh command.
```
sudo sh NVIDIA-Linux-x86-173.14.12-pkg1.run
```

---

### Post by gmxgeek on 2008-08-30
> **alienexplorers said:**
> Forget about doing it that way and use envy found in the repositories.  Download envy-core and envy-gtk.  Run envyng from the applications>system tools and it will automatically set up your driver.  Alot easier than doing it by hand.

Seconded to envy. Manual driver compiling is a pain. Envy is epic win. Also, you may use nvidia-settings after the drivers are installed to tweak your settings.

---

### Post by gmxgeek on 2008-08-30
> **Shazaam said:**
> You need to put sudo in front of the sh command.
```
sudo sh NVIDIA-Linux-x86-173.14.12-pkg1.run
```

might also need to chmod +x it, if you just downloaded it

assuming downloaded to Desktop
```

sudo apt-get install build-essential
cd ~/Desktop
chmod +x NVIDIA-Linux-x86-173.14.12-pkg1.run
sudo sh NVIDIA-Linux-x86-173.14.12-pkg1.run

```

If you are insistent on compiling yourself

---

### Post by jerome1232 on 2008-08-30
actually it's because you haven't made it executable

```
chmod +x NVIDIA-Linux-x86-173.14.12-pkg1.run
```

And you will have to stop x, then run this installer script as root. You will also need the build essential package so it can compile the driver module for you.

But I second not doing it this way, it's a last resort type of thing.

Have you tried installing the driver in the repos?

```
sudo apt-get install nvidia-glx-new
```

or if you need the updated drives using envy as mentioned earlier in this post?

---

### Post by Codemastadink on 2008-08-31
> **alienexplorers said:**
> Forget about doing it that way and use envy found in the repositories.  Download envy-core and envy-gtk.  Run envyng from the applications>system tools and it will automatically set up your driver.  Alot easier than doing it by hand.

I downloaded this and tried it, and this is the window that came up.

---

### Post by nbayiha on 2008-08-31
Dude you have a NVIDIA card or an ATI card ?
You tried to install ATI driver but you have a NVIDIA card.
Try again to install using envy and be sure to choose nvidia card this time.

---

### Post by jerome1232 on 2008-08-31
I think you should take a look at this how-to, it explains the various methods to install nvidia drivers
[http://ubuntuforums.org/showthread.php?t=880787&highlight=install+nvidia+driver+hardy](http://ubuntuforums.org/showthread.php?t=880787&highlight=install+nvidia+driver+hardy)

---

