---
title: "Try another distro....and how to install ?"
date: 2008-06-01
forum: Other OS Talk
---

### Post by Hagar55 on 2008-06-01
Right now I have Windows Xp and Ubuntu 8.04 on a seperate partition.
Don't get me wrong I like Ubuntu, but there are some things I disagree with.

Also I'd like to try another distro of linux, to see if there are major differences.

I've been thinking of trying eiter Fedora or OpenSuse.
First is there a way to install eiter on another partition without losing acces to either Xp (under no circumstance...) or Ubuntu (via GRUB).

Secondly witch one would you suggest to try out (I'm learning linux, but I'm still not an average user by far..)

---

### Post by SunnyRabbiera on 2008-06-01
Well what is your particular issue with ubuntu? the release cycle and such?
Personally my vote is for mandriva 2008.1 as a distro to look at, Mandy is looking very good right now.

---

### Post by Kevbert on 2008-06-01
Both Fedora and openSuse will install their own bootloader by default.  If you decide to try either of these, use a live CD.  If you then decide you want one of these I've found the best way is to install either and then install a Ubuntu family distro.  You may want to take a look at Kubuntu as it is quite a bit different to Ubuntu (it uses KDE instead of gnome) and has some interesting features.  There is also Xubuntu which runs fast with Xfce (cut down version of Ubuntu).
I've found you can install up to 3 OS on a single drive.  I have XP, openSuse, Fedora, Ubuntu and Kubuntu on my main desktop.

---

### Post by mick222 on 2008-06-01
you should have no problems installing opensuse i used it for a while and it is very good but i like ubuntu more mostly because the community. Fedora is a bit more cutting edge and i think anaconda overwrites grub which will recognize your xp partition but not ubuntu . Therfore after instalation you will have to edit your  menu 1st file not hard to do and gives you a little experiance .

---

### Post by mick222 on 2008-06-01
Most people just like to try different distros especially at first it's part of the learning curve

---

### Post by Hagar55 on 2008-06-01
I take it anaconda is a bootloader like GRUB ?
so I can't do an install and edit GRUB to give me acces to the other distro...or can I, and if so how should I do it.

Alternately, how do you change anaconda to give you acces to Ubuntu ?

---

### Post by Joeb454 on 2008-06-01
I hear Fedora 9 is pretty good :)

---

### Post by mips on 2008-06-01
> **Hagar55 said:**
> 
First is there a way to install eiter on another partition without losing acces to either Xp (under no circumstance...) or Ubuntu (via GRUB).


That all depends on how many primary partitions you already have. Your limit for primary partitions is 4 per hard drive. Installing stuff in logical partitions can be messy sometimes.

If you want to try other distros out and not risk any loss of existing partitions etc I would recommend you use Virtual Box.

IF you can read then I would say try Arch Linux, just read the Beginners & Official install wikis.

---

### Post by wolfen69 on 2008-06-01
> **Kevbert said:**
> 
I've found you can install up to 3 OS on a single drive.

you can have as many as you want. you just need to make extended partition and logical ones inside that.

---

### Post by smartboyathome on 2008-06-02
> **Hagar55 said:**
> I take it anaconda is a bootloader like GRUB ?
so I can't do an install and edit GRUB to give me acces to the other distro...or can I, and if so how should I do it.

Alternately, how do you change anaconda to give you acces to Ubuntu ?

Anaconda is an installer, like Ubuntu's which is called Ubiquity.

---

### Post by r76 on 2008-06-02
> **mips said:**
> If you want to try other distros out and not risk any loss of existing partitions etc I would recommend you use Virtual Box.

[Virtualbox]("http://www.virtualbox.org/") is such a good idea.  It will save on CDs/ DVDs for all those distros.  So many distros I have decided I didn't like within a few minutes...  The XP version is great (haven't tried installing it in Ubuntu).  Consider it a quick way to "screen" distros :)

---

### Post by mips on 2008-06-02
> **r76 said:**
> [Virtualbox]("http://www.virtualbox.org/") is such a good idea.  It will save on CDs/ DVDs for all those distros.  So many distros I have decided I didn't like within a few minutes...  The XP version is great (haven't tried installing it in Ubuntu).  Consider it a quick way to "screen" distros :)

Well if you use RW media then you dont really waste any media. Part of the beauty is that you simply tell VB to mount the ISO image and then you boot off it, no need to waste time writing it to a cd/dvd. Just as easy getting rid of it if you dont like it.

The Ubuntu version is a piece of cake to install and use.

---

