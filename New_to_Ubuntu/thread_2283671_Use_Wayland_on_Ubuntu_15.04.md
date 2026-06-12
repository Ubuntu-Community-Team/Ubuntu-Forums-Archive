---
title: "Use Wayland on Ubuntu 15.04"
date: 2015-06-23
forum: New to Ubuntu
---

### Post by XinyuHou on 2015-06-23
Trying to use Wayland on Ubuntu 15.04, I followed the instructions I can find on google. I can see the gdm login screen and choose GNOME on Wayland shown as below. But after I type in my password it goes back to login screen again. I'm pretty sure I type in the right password. I install Ubuntu on a VM, not sure if that is the cause. I'm going to try to install it on my machine.
Any idea?

[http://i.stack.imgur.com/lcNli.jpg](http://i.stack.imgur.com/lcNli.jpg)

---

### Post by grahammechanical on 2015-06-23
Just for clarity. Can you confirm that you are doing this on Ubuntu Gnome and not on Ubuntu with Gnome 3 shell added? I think that it is best to do this on Ubuntu Gnome. Some of us experimented with this while 15.04 was still in its 26 week development cycle. This is where we discussed our results.

[http://ubuntuforums.org/showthread.php?t=2264340](http://ubuntuforums.org/showthread.php?t=2264340)

This was the initial call to test. Notice that we must be using an open source video driver and not a proprietary video driver.

[http://ubuntuforums.org/showthread.php?t=2264340](http://ubuntuforums.org/showthread.php?t=2264340)

You may get better results if you try this on Ubuntu Gnome Wily Werewolf (15.10). That is where all the improvement work will go. 

[http://cdimage.ubuntu.com/ubuntu-gnome/daily-live/20150623/](http://cdimage.ubuntu.com/ubuntu-gnome/daily-live/20150623/)

If you do test gnome-wayland-session on wily werewolf (15.10) then if you want you can open a tread on the subject in the Ubuntu Development Version section of the forum. But not if you continue to test this on 15.04.

Regards.

---

### Post by XinyuHou on 2015-06-23
> Just for clarity. Can you confirm that you are doing this on Ubuntu Gnome and not on Ubuntu with Gnome 3 shell added? 

How can I check it? Sorry, I'm new to Linux. I have been to that link. People seem to agree it should work on GDM.

> This was the initial call to test. Notice that we must be using an open source video driver and not a proprietary video driver.

This is totally new to me. I'm going to google it. Any reference or link would be appreciated.

> wily werewolf (15.10)

I have to test it on 15.04

Thank you

---

### Post by grahammechanical on 2015-06-23
You would know if you downloaded and installed Ubuntu or Ubuntu Gnome. Ubuntu comes with the Unity interface. Gnome 3 shell has to be downloaded and installed to get the Gnome 3 shell user interface.

I just think that for the best results it is better to install gnome-session-wayland on Ubuntu Gnome which is a distribution dedicated to running almost a pure Gnome version of Ubuntu. Running gnome-session-wayland on Ubuntu + Unity adds, in my opinion, a layer of complexity that could cause problems.

I have just loaded my install of Ubuntu Gnome wily werewolf (15.10 under development). It has gnome-session-wayland installed and I have no problem logging into and out of the standard gnome session and the Gnome wayland session.

If we go to System Settings (cog icon on the drop down menu from the top right indicators) and open Details, under Graphics, it will show Wayland if we are running gnome session wayland, Gallium if we are using an open source video driver with an Nvidia adapter. I cannot tell you what you will see if you have an Intel or an ATI/AMD adapter.

Whatever Ubuntu family member we install, if we tick to install third party software during the installation we will get a proprietary video driver. And  gnome-session-wayland does not work too well with proprietary video drivers.

> You must be using open source drivers (neither AMD or NVIDIA support wayland yet)

[https://lists.launchpad.net/ubuntugnome-qa/msg00702.html](https://lists.launchpad.net/ubuntugnome-qa/msg00702.html)

All members of the Ubuntu family of distributions have an open source video driver as default. If we do not install a proprietary video driver we get open source. And we can change using Additional Drivers.

Regards.

---

### Post by XinyuHou on 2015-06-23
Thank you so much for all the explanation. It definitely save a huge amount of my time!

I downloaded the iso from [http://releases.ubuntu.com/15.04/](http://releases.ubuntu.com/15.04/)

I think it is Unity interface.

So do I need to download a different iso to install Ubuntu Gnome? Or I can choose which one I want during installation?

I didn't tick the install third part software. So I would assume I'm using a OSS video driver.

I'm downloading ubuntu gnome iso and gonna try it out when it's finished.

---

### Post by grahammechanical on 2015-06-23
You would not have an option at the login screen to load a Ubuntu session if you were not running everything on Ubuntu. A VM is a useful way to try different distributions. 

Here is one place to get the Ubuntu Gnome ISO image

[http://cdimage.ubuntu.com/ubuntu-gnome/releases/vivid/release/](http://cdimage.ubuntu.com/ubuntu-gnome/releases/vivid/release/)

Assuming you have a 64 bit CPU download ubuntu-gnome-15.04-desktop-amd64.iso. Think about giving the development version (15.10) a try

[http://cdimage.ubuntu.com/ubuntu-gnome/daily-live/20150623/](http://cdimage.ubuntu.com/ubuntu-gnome/daily-live/20150623/)

This time it is called wily-desktop-amd64.iso. Some time in the future there will be a Ubuntu Gnome version using a Gnome Wayland compositor and not just what is called Xwayland as at present. It all has to be tested and it is better if some of us try these things out before release day.

With Xwayland, from the boot menu to the login screen we run on the Xserver, then if we select Gnome Wayland after logging in everything switches to Xwayland. And that switch over is what is breaking down on your system. And it could be because of using a proprietary video driver.

Regards.

---

### Post by XinyuHou on 2015-06-23
Just finished install Ubuntu GNOME on my vm. It has the same result...

I didn't tick the third party software and I installed the gnome-session-wayland.

$ sudo add-apt-repository ppa:wayland.admin/daily-builds
$ sudo apt-get update
$ sudo apt-get install xwayland weston
$ sudo apt-get install gnome-session-wayland

Anything I forgot to do?

After I type in weston, the weston compositor pops up, even though I don't know what it does.

In the login screen I can choose System Default, GNOME, GNOME Classic, GNOME on Wayland and Weston.

If I choose Wayland, after I type in password it flashes and gets back to login screen again. I can switch back to GNOME, but it requires me to login twice, the first time is the same as choosing Wayland.

---

### Post by XinyuHou on 2015-06-23
lshw -c video | grep configuration outputs:
configuration: latency=0

lspci -nnk | grep -i vga -A3 | grep 'in use' outputs:
Kernel driver in use: e1000

Does this mean I'm not using OSS video driver?

---

### Post by wildmanne39 on 2015-06-23
Hi, please use thumbnails or url's when posting images because many people have slow connections or a limit on bandwidth.
Thanks

---

### Post by monkeybrain20122 on 2015-06-23
Just curious, if you are completely new to Linux why do you want to try wayland? It is alpha software for testers.

---

### Post by XinyuHou on 2015-06-23
Sorry about the image.

I'm trying to make a product work on Ubuntu with wayland.

---

### Post by XinyuHou on 2015-06-23
Just installed Ubuntu GNOME on my actually machine.

lshw -c video | grep configuration
configuration: driver=nouveau latency=0

modinfo nouveau
license: GPL and additional rights
description: nVidia Riva/TNT/GeForce/Quadro/Tesla
author: Nouveau Project

So I think I'm using OSS video driver.

On my actual machine, after I switch to GNOME on Wayland and login, I lose my video signal...

---

### Post by XinyuHou on 2015-06-24
Oops, did mean to reply the same thing twice.

Any way I can delete a reply?

---

### Post by deadflowr on 2015-06-24
> **XinyuHou said:**
> Oops, did mean to reply the same thing twice.

Any way I can delete a reply?

I removed your two duplicates posts.
In the future just click on the report post button and explain that you want to remove the post(s).

---

### Post by XinyuHou on 2015-06-24
> **deadflowr said:**
> I removed your two duplicates posts.
In the future just click on the report post button and explain that you want to remove the post(s).

Got it. Thank you!

---

