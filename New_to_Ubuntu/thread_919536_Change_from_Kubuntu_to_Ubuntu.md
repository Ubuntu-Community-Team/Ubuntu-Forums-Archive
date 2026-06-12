---
title: "Change from Kubuntu to Ubuntu"
date: 2008-09-14
forum: New to Ubuntu
---

### Post by Gradeo on 2008-09-14
Hello I am new to Ubuntu and have got myself into a bit of a pickle.  I installed the latest Kubuntu onto my new system which until then had no other OS.  I now want to install Ubuntu but have no idea how to go about it.  I can't seem to find any options to format my HDD so that it would be how it was when I installed Kubuntu.  Any help you can offer would be greatly greatly appreciated!

Gaz

---

### Post by Mornedhel on 2008-09-14
Ubuntu and Kubuntu are the same thing (same repositories, same applications, etc.). The only difference is that Kubuntu comes with KDE preinstalled, whereas Ubuntu uses Gnome by default.

You have two options at this point :
1. Install Ubuntu as you did with Kubuntu. If you come from Windows, you're probably used to this. Easiest and most straightforward. Or :
2. Install the ubuntu-desktop metapackage and sort it later, which means you'll still be able to run your KDE applications until you remove them. This can be messy, but is the fastest way. Next time you log in, just choose "Gnome" from the Session menu at the login prompt.

---

### Post by anjilslaire on 2008-09-14
THey are the same except for the user interface. Open a konsole & do
```

sudo apt-get install ubuntu-desktop

```

oh, choose gdm instead of kdm during the process. You'll see what I mean during the install.

No need to reformat or anything.

---

### Post by Gradeo on 2008-09-14
Thanks for the quick respone.  I think option 1 is best for me!  I have Ubuntu on disc but don't know how to install it from Kubuntu.  Do I need to format the HDD?  If so is it possible to do that within KDE?

---

### Post by SuperSonic4 on 2008-09-14
I;m not sure if you can install it inside kubuntu but you can boot from the ubuntu cd in bios and shrink the partitions using GParted

---

### Post by Mornedhel on 2008-09-14
> **Gradeo said:**
> Do I need to format the HDD?  If so is it possible to do that within KDE?

Are you trying to install Ubuntu to replace Kubuntu ? I think you'll find formatting the hard drive on which the OS you are currently using is running to be a bad idea.

Just insert the Ubuntu CD, reboot your computer using the CD as boot medium, and follow the instructions. The process is identical to the installation of Kubuntu, unless you installed with Wubi from Windows. You'll be asked at one point if you want to format your drives and how you wish to partition them.

---

### Post by Gradeo on 2008-09-14
I am currently downloading ubuntu-desktop from that apt-get thingy.  I tried to run the disc with ubuntu on it but it boots from the HDD first avoiding booting from the disc.  There are no files I need to keep on the HDD as it's brand new bought so I could experiment buildin a computer and putting ubuntu or kubuntu on it.  

Is there anyway to get the cd to boot at startup before grub(or whatever the loader is called) launches kubuntu?

And if I am not bothered about any data currently on the hard drive, is formatting it an viable option?

p.s.  thanks for getting back to me so quickly!!

---

### Post by C.S.Cameron on 2008-09-14
I have been running xubuntu from thumbdrive.
Yesterday I went to synaptic and installed ubuntu-desktop.
I now have the option for either at boot.
I understand that you can use synaptic to remove kubuntu-desktop if you wish, but I have not tried it.
The command line method of installing the desktops did not work for me in a big way, (reformat required).

---

### Post by Mornedhel on 2008-09-14
> **Gradeo said:**
> Is there anyway to get the cd to boot at startup before grub(or whatever the loader is called) launches kubuntu?

Yup, but it's a bit more advanced. Watch closely when your computer boots. It may say something about :
"pressing [some key] to select boot device" : you're in luck. Quickly press that key. If you do not press it fast enough, just wait until you can reboot, and try again. Select your CD drive as a boot device, confirm, reboot. Sometimes it's F8, sometimes it's something else. Check on the Internet if you can find the particular instructions for your particular computer.

Else : "pressing [some key] to enter BIOS/Setup". This is more difficult. The key might be DEL or F2. Once you are into the BIOS, do NOT change anything unless you are POSITIVE it's your boot device order. This will probably be tricky if it's the first time you're doing it. Look for complete tutorials on the Web before attempting it. Some settings in the BIOS are a bit dangerous to play with : don't save until you are certain you changed only your boot device order (with the CD drive as the first option).

> **Gradeo said:**
> And if I am not bothered about any data currently on the hard drive, is formatting it an viable option?

Well, the brute reinstall *will* format your drive anyway. When it asks you how to configure your partitions, tell him you want to format your Kubuntu ext3 partition and use it as your root partition.

Edit : [quote=C.S.Cameron]I understand that you can use synaptic to remove kubuntu-desktop if you wish, but I have not tried it.[/quote]

You can, but as it's a meta-package it won't uninstall anything. You will need to use the autoremove feature. Meta-packages are very useful for installing several packages in one go, or automatically installing the correct package depending on the architecture.

---

### Post by Raffles10 on 2008-09-14
You don't need to install Ubuntu over Kubuntu, once you have installed ubuntu-desktop you can choose which environment you want to run, when it asks what dm to use, kdm or gdm select gdm & continue.

If you want to remove kubuntu-desktop just paste the following into the terminal:

```
sudo apt-get remove kubuntu-desktop kubuntu-artwork-usplash

```

This will in effect turn Kubuntu into Ubuntu.

---

### Post by kansasnoob on 2008-09-14
No need to reinstall, look at this section:

> Playing Around
Enable Desktop Effects
KDE/Gnome Comparison
Install Gnome
Install KDE
Install XFCE
Install IceWM
Install XPDE
Pure Gnome
Pure KDE
Pure XFCE
A faster KDE
Replacing Nautilus 

of this tutorial:

[http://www.psychocats.net/ubuntu/index](http://www.psychocats.net/ubuntu/index)

Note: "Pure gnome" will give you Ubuntu!

---

### Post by Gradeo on 2008-09-14
I have now installed ubuntu-desktop and all seems well!  

Many thanks, Gaz.

---

