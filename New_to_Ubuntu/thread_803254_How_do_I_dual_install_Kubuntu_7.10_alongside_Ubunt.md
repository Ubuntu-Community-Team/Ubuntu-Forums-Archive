---
title: "How do I dual install Kubuntu 7.10 alongside Ubuntu/Xubuntu 8.0.4?"
date: 2008-05-22
forum: New to Ubuntu
---

### Post by oopsy on 2008-05-22
Hi,
I have Ubuntu 8.0.4 and Xubuntu 8.0.4 installed. I'm having a lot of problems with them, so I want to install Kubuntu 7.10 (Gutsy Gibbon) alongside them. I plan on using Kubuntu exclusively and keep Ubtu/Xbtu as backup for the time being. I may later on decide to remove them.

They were installed from a Ubuntu 7.10 (Gutsy Gibbon) live CD that I upgraded to 8.0.4, then from which I installed Xubuntu.
I also do not want to use Firefox beta anymore, but 2.0.14 instead.

I'm going to download Kubuntu, so I will have it right on my desktop, ready to install.

Being a complete newbie, I'll really appreciate baby-steps explanation.
Thank you very much for your help.

---

### Post by shifty_powers on 2008-05-22
not sure i understand. do you have SEPARATE installations of ubuntu and xubuntu, or did you install ubuntu, and then install the xfce desktop on top of gnome?

---

### Post by oopsy on 2008-05-22
> **shifty_powers said:**
> not sure i understand. do you have SEPARATE installations of ubuntu and xubuntu, or did you install ubuntu, and then install the xfce desktop on top of gnome?

Thank you very much for the quick response.
I'm not 100% sure on the terminology, but I believe I installed xfce on top of gnome. I did it through the command
*sudo aptitude update && sudo aptitude install xubuntu-desktop*

This time, I'm looking for a separate installation.
Thank you much.

---

### Post by housam on 2008-05-22
Just prepare a separate ext3 partition for the root (/) of the new installation and install it the normal way as you did  before, and assign the new partition manually.

---

### Post by philinux on 2008-05-22
I just installed kubuntu 8.04 yesterday and it's now been erased unfortunately. I'm now even more happy with ubuntu.

For me I found it buggy. Firefox is not installed by default so you have the choice of version 2 or 3beta. 

One tutorial I saw installed synaptic. This may be useful if your having a try with kde.

 [http://www.howtoforge.com/the-perfect-desktop-kubuntu-8.04-lts](http://www.howtoforge.com/the-perfect-desktop-kubuntu-8.04-lts)

---

### Post by shifty_powers on 2008-05-22
tbh, kde4 is a buggy piece of beta ;) i've tried it and steered well clear of it.

however, there is nothing stopping you from installing kubuntu with kde3.whatever it is ;)

might have to play around with grub to get the boot options for ubunut and kubuntu...

---

### Post by housam on 2008-05-22
> **shifty_powers said:**
> 
might have to play around with grub to get the boot options for ubunut and kubuntu...

I've just installed kununtu then ubuntu alongside win-xp , all working fine , I didn't touch grub.

---

### Post by oopsy on 2008-05-22
> **housam said:**
> Just prepare a separate ext3 partition for the root (/) of the new installation and install it the normal way as you did  before, and assign the new partition manually.

Thank you for the replies.
I really don't know how to do any of this, Housam. I don't even know what a ext3 partition is.

When I first installed 7.10 from the live CD, I let it do the partitioning automatically, and I'm not exactly sure how it did it.
I started with a brand new 80GB HDD. Now, when I look at "My computer" in Ubuntu, it shows 40GB media, CD drive, travel drive and file system. Nothing else. I'm not even sure what happened to the other 40GB. 

Would you be able to give me directions command by command?
Thank you very much.

I'm glad you're telling me you found it buggy, philinux. I thought I might have done something wrong. Well, the more reason not to use it anymore.

I have to be away from the computer for a few hours, but I'll be back to read your suggestions.
Thank you very much.

---

### Post by housam on 2008-05-22
To install a new system , you have to do it on a free partition. you can do it automatically by letting the installer to choose the biggest free space to format it to ext3 format ( this is the suitable format for installing ubuntu ). then install the system on it. 
OR you can do it manually by resizing any of the partitions you have and get a free space that can be formated to the ext3 and then install on it.

to do either of these 2 ways, we have to know about your partition table : type in a terminal (Applications-Accessories-Terminal)
```
sudo fdisk -l 
```
where -l is a small L and post the results 

AND also we want to know about the usage percentage of your partitions :Boot from ubuntu live CD and take a screen shot of the Gparted tool image ( sys. >> admin. >> partition editor )and post it too.

---

### Post by zvacet on 2008-05-22
> I have Ubuntu 8.0.4 and Xubuntu 8.0.4 installed. I'm having a lot of problems with them, so I want to install Kubuntu 7.10

Changing desktops will not solve your problems.It will be better to say which problems do you have and let as help you with them.If you decide to do that,please open another thread.

---

### Post by oopsy on 2008-05-22
Thank you.
----------------
Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000df03f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        4861    39045951   83  Linux
/dev/sda2            9449        9729     2257132+   5  Extended
/dev/sda3   *        4862        9448    36845077+  83  Linux
/dev/sda5            9637        9729      746991   82  Linux swap / Solaris
/dev/sda6            9449        9636     1510047   82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdb: 1031 MB, 1031798784 bytes
16 heads, 32 sectors/track, 3936 cylinders
Units = cylinders of 512 * 512 = 262144 bytes
Disk identifier: 0xe9cf9ed2

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        3936     1007600    e  W95 FAT16 (LBA)
----------------------
I'd really appreciate if you could tell me what that means.

Can I boot from the live CD? It is 7.10 while the version on my computer is 8.04.

Also, where do I find a stable version to download? And what is the difference between Kubuntu and Kde? And what is an alternate?

I thought it would be easy to download the version that comes before 8.0.4, but it is not. I cannot figure out what is what.
The download site only has 8.0.4 and a Google search brought me to a site with a big red warning saying there are bugs in the releases displayed. In other words, I'm lost.

So let me tell you what I need and I hope you'll be able to help me.
* I need something simple and straightforward.
* Something that would look and feel like windows as much as possible (I know, what can I say, I'm a heretic LOL).
* Something that would recognize my Nikon Coolpix 2000 camera. I've read many threads saying there was no camera problem until upgrading to 8.0.4. Unfortunately, I didn't read them before upgrading and not been able to use mine.
* I don't play games other than solitaire, so I don't need any of the bells and whistles associated with them. I don't mind having them, it's just not a requirement for me.

* Before getting a new HDD and switching to Linux, I was using WindowsMe working mostly with Nvu, a simple wysiwyg html editor, and Irfanview, a quite powerful free photo editor that is much easier to use than Gimp.
* One more thing, I don't want to use a Beta of any kind. Not that I don't want to help, but I'm having too much trouble learning Linux to want to deal with bugs at this time.

I hope this will make things clearer.
Thank you very much for your help.

---

### Post by oopsy on 2008-05-22
> **zvacet said:**
> Changing desktops will not solve your problems.It will be better to say which problems do you have and let as help you with them.If you decide to do that,please open another thread.

My problems are:
1. Screen very jumpy. The scrolling bar on the right has a hard time staying where I put it. It keeps going up and down without reason.
2. Since upgrading to 8.0.4, it takes about 15 minutes to start. When loading, the orange bar goes to the far right, then comes back to the middle, and stays there for about 15 minutes.
3. My camera is not recognized at all, not even in "My computer".
4. I can't stand the scrolling tabs and the way the command bar displays history in FireFox beta. Also, it is not recognized by some website. FedEx been one of them.

I thought that adding a different distro that I would use exclusively might eliminate the problems, but ... any chance it would?

The main reason I don't simply scrap everything and start over with a new distro is that I'm afraid of losing my internet connection settings and not being able to get online.

Another reason is since I don't know Kubuntu, it might be a good idea to keep something with which I can somewhat work, although very badly, in case Kubuntu doesn't work at all.

I need to be able to work on line, and I am very much pressed by time, but maybe I'm asking the wrong question:

How could I replace Ubuntu/Xubuntu by doing a clean install of Kubuntu and still be able to retain my internet settings?
Thank you so much for helping.

---

### Post by zvacet on 2008-05-22
You can find and download Gutsy [here.]("http://releases.ubuntu.com/kubuntu/gutsy/") On the same page you will find description of alternate CD.I think you will have less trouble install with it.It is text based installer( not eye candy) but it does job very well.

>  It is essential that you apply all security updates after installation before making any use of your system.

Meaning that you take all upgrades after install.You will do it anyway.

You can delete all your sda disc and partition it as you like.Maybe like this

1.root = 10GB                  mountpoint /
2.swap = 1.5-2GB (depend of your ram)
3.home = rest of free space         mountpoint /home

But install it in this order : root home swap

Sorry,I don´t know anything about cameras,so I can not help you.You can Use Gutsy until April 2009 and I believe until then things wil be improved in Hardy.If I forget something just post and ask again.I hope you will enjoy your Kubuntu.

---

### Post by housam on 2008-05-22
> **oopsy said:**
> 
I'd really appreciate if you could tell me what that means.

I thought it would be easy to download the version that comes before 8.0.4, but it is not. 

your partition table shows that you have two HDDs , one 80 GB with two distros of ubuntu and two swap partitions.
the 2nd is 1 GB fat32 for data or media.
that means you can reinstall ubuntu and/or kubuntu 7.10 on top of the two existing systems.
> **oopsy said:**
> Can I boot from the live CD? It is 7.10 while the version on my computer is 8.04.
Yes you can boot from any live CD despite of its version.and you can install it too.
> **oopsy said:**
> Also, where do I find a stable version to download? And what is the difference between Kubuntu and Kde? And what is an alternate?
here is the download site of ubuntu 7.10 :[[COLOR="Red"]_http://releases.ubuntu.com/7.10/_[/COLOR]]("http://releases.ubuntu.com/7.10/")
here is the download site of [[COLOR="Red"]_[U]kubuntu 7.10_[/U][/COLOR]]("https://wiki.kubuntu.org/GutsyGibbon/RC/Kubuntu#head-0d853d34d90ae2fb5d4838c5f41871a700d5f510")

[COLOR="Blue"]**KDE**[/COLOR] 

The default desktop environment for Kubuntu is KDE, a powerful Free Software graphical desktop environment for Linux and Unix workstations. It combines ease of use, contemporary functionality, and outstanding graphical design with the technological superiority of the Unix operating system. KDE is one of many desktop environments for Linux users. KDE sports an impressive array of easy to use, but powerful, graphical interface applications for users of all ages in both home and work environments. For developers, KDE provides a robust application development framework that enables rapid creation of first rate applications implementing cutting-edge technology.

You can just install Gutsy ( ubuntu + kubuntu ) on top of the existing distros . Gutsy is less in troubles than Hardy.

---

