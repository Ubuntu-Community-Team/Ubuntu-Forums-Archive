---
title: "Triple Boot- Windows XP, Unbuntu 8.04, and FreeBSD"
date: 2008-06-01
forum: New to Ubuntu
---

### Post by EriCartman13 on 2008-06-01
Okay so right now I am dual-booting Windows XP and Ubuntu 8.04.  I want to triple boot and add FreeBSD.  Would this be okay?  All I would have to do is make a partition for FreeBSD then install it.  Would it still show up in grub?  Thanks for all the help, and this is my first post.  New to linux and here.

---

### Post by Eisenwinter on 2008-06-01
As long as the FreeBSD boot loader recognizes both Ubuntu and Windows, it's fine.

If you want to be sure though, first install Windows, then FreeBSD, then Ubuntu.

---

### Post by ChameleonDave on 2008-06-01
> **EriCartman13 said:**
> Okay so right now I am dual-booting Windows XP and Ubuntu 8.04.  I want to triple boot and add FreeBSD.  Would this be okay?  All I would have to do is make a partition for FreeBSD then install it.  Would it still show up in grub?  Thanks for all the help, and this is my first post.  New to linux and here.
It will not automatically show up in GRUB.  You will have to add it to the */boot/grub/menu.lst* file.

It is possible that FreeBSD will want to install GRUB itself and have its own configuration files.

---

### Post by EriCartman13 on 2008-06-01
Ah I see.  So would it be easier to just uninstall Ubuntu now, since I just installed it, then intall FreeBSD, and then install Ubuntu?

---

### Post by bumanie on 2008-06-01
A bit hard to give a definitive answer as I have never installed free bsd and don't know how it installs grub. I can say that on the ubuntu alternate cd you have the option of where to install grub, whereas the live cd seems to decide where to install grub without user input. There is also a possibility of setting up a specific grub partition that will be able to handle all three OSes. Go [here]("http://users.bigpond.net.au/hermanzone/p15.htm#How_to_make_a_separate_Grub_Partition_") for help with setting up that.

---

### Post by Dedoimedo on 2008-06-01
Hello,
If I remember correctly, BSD wants primary partitions when installing, so make sure you have them free - at least one.
Dedoimedo

---

### Post by housam on 2008-06-01
> **EriCartman13 said:**
> Okay so right now I am dual-booting Windows XP and Ubuntu 8.04.  I want to triple boot and add FreeBSD.  Would this be okay?  All I would have to do is make a partition for FreeBSD then install it.  Would it still show up in grub?  Thanks for all the help, and this is my first post.  New to linux and here.

You can take this guide for [[COLOR="Red"]_multi-booting _[/COLOR]]("http://ubuntuforums.org/showthread.php?t=724817")

---

### Post by SunnyRabbiera on 2008-06-01
if you have the room then a triple boot is plausible.
but you really dont need to make a new partition to try out freebsd, you can try to run it in a virtual machine instead of risking breaking your system.

---

### Post by Gone fishing on 2008-06-01
I usually triple boot - Windows as I need it for work, Ubuntu as my main recreational OS and what ever I'd like to try recently Mandriva although I've got a space for Haiku when its usable.

I use the GAG bootloader [http://gag.sourceforge.net/](http://gag.sourceforge.net/) as it very easy to configure change OSes etc. It does mean that grub is installed on my root partition rather than the MBR as this is where GRUB lives.

---

### Post by ChameleonDave on 2008-06-01
You can do what you like of course, but I'd advise against multiple boots unless you have some particular reason.

I boot into Ubuntu, and within that I have Windows XP running in VirtualBox for the occasional bit of software that I need.  I also use VirtualBox if I want to try something out.

Pretty much anything that you can run on FreeBSD will also run on Linux, so I imagine you just want to try it out, rather than need to run it on a regular basis.

If you are dead-set on booting FreeBSD, then you would do better to enquire on a FreeBSD forum rather than on a Linux forum.

---

### Post by tubbygweilo on 2008-06-01
Cartman,
I have had Freebsd, Ubuntu and XP happily exiting together all overseen by grub but as I'm running Ubuntu 8.04, lvm and full disk encryption xp and Freebsd have been banished from my machine.

A good place to look for information is [The FreeBSD Documentation Project]("http://www.freebsd.org/doc/en_US.ISO8859-1/books/handbook/index.html") closely followed by the [Daemon forums]("http://daemonforums.org/").


To answer a couple of your queries;

FreeBSD needs to be installed into a primary partition.

When installing select the option **NOT** to mess with the MBR as you can edit a few lines in the grub menu.lst file after FreeBSD has been installed allowing FreeBSD to be displayed and booted via grub.

IIRC the additional lines needed looked something like 
```
title  FreeBSD 7.0
root   (hd0,a)
kernel /boot/loader
```

with "(hd0,a)" reflecting the position of the FreeBSD primary partition.

Once more I stress that browsing through the documentation and visiting the forum before installing or indeed amending your existing fully working system would be a very good idea indeed.

Best of luck with your FreeBSD endeavours:)

---

### Post by EriCartman13 on 2008-06-01
Thanks for all the help everyone.

---

