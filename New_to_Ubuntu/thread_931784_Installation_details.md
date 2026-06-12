---
title: "Installation details"
date: 2008-09-27
forum: New to Ubuntu
---

### Post by AutoLink on 2008-09-27
I am a Ubuntu/Linux newbie. Currently, I am using the Wubi installation on XP. I want to move to a regular Ubuntu installation and dual boot with XP. My long term plan is to use Windows only when I have to and, maybe eventually, remove it from my computer altogether.

I have a 230 GB hard drive. I have moved my Windows My Documents folder to an external hard drive, so it can be accessed both through Windows and through the Wubi installation.

My questions:

1.	Should I uninstall the Wubi installation before doing the regular Ubuntu installation, or does it matter?
2.	The directions for installing Ubuntu in a dual boot configuration list minimal disk space partitions for Ubuntu. Since I plan to move to Ubuntu as my main OS, it would seem logical to leave minimal space for Windows, or at least, be more generous with Ubuntu space. Are there any guidelines in this regard?
3.	Can I come back later and repartition the drive again, if I want to change the disk space allocated to Windows and to the various Ubuntu partitions? If I eventually decide to uninstall Windows altogether (and to thus eliminate security problems associated with Windows), will I be able to recover the disk space?

And a somewhat unrelated question:

I have gained much of my PC knowledge from the print magazines, PC World and PC Magazine. Is there a similar magazine for Ubuntu? I am not a programmer, so any material that is particularly advanced wouldn’t help me. I don’t want to read off of the screen all of the time, so the many Ubuntu information sources on the Internet wouldn’t completely fill the need.

Thank you for your help.

---

### Post by Xiong Chiamiov on 2008-09-27
1. No experience with Wubi
2. I have Windows on a 10-gig partition myself, but it's pretty much a default install.  Before you do any partitioning, make sure you defrag first.  Oh, and you may want to pick up the [Gparted live cd]("http://gparted.sourceforge.net/livecd.php").
3. Sure can.  See above CD.

As far as mags, there *are* some, but I couldn't tell you what they are, as I'm a poor college student who spends enough on programming books as it is.  Linux books, however, are generally a bad idea, as they go out of date very fast.  It takes a little while getting used to the non-Microsoft release cycle.

Oh, and Debian material is generally useful for Ubuntu, as Ubuntu is Debian-based.  Many other things you'll just want Linux-generic information.

---

### Post by _sAm_ on 2008-09-27
1: No need to, you can remove “Ubuntu-wubi” later when you want(it is installed in Windows XP as a normal program, and can be removed as one).

2: I guess you gonna use Windows for games? Well games need often much space so I wouldn't take much from it. The space for Ubuntu depends on what you are going to use it for. I mean, if you are going to rip a dvd you would need 4 to 9gig space just for that. I would go for /home on its own partition, that is much better imho. If later upgrades fails you can just reinstall Ubuntu without loosing your settings and data. 
3: You cant make a partition bigger without decrease the space of the partition next to it. 
Last one; I like the one called Linux Foramt(from UK) and Linux Magazine. And if you want to read from the screen from time to time check out the free one for Ubuntu: Fullcirclemagazine.org Download as Pdf:-)

---

### Post by AutoLink on 2008-09-28
Thanks to Xiong Chiamiov and to _sAm_.

I don’t do a lot of gaming. I’ll mostly be using Windows for things that I may not be able to do with Ubuntu, or at this point, don’t know how to do with Ubuntu. 

For instance, I use a Centro with important (to me) specialty software that is available only for Windows and Mac. Also, I use Citrix a lot, both GoToMyPC and corporate. Some of the latter may be available through Ubuntu, but it will take time to work it out.

Some of the web sites I use just won’t work in Firefox. As far as I know, there is no IE for Ubuntu. Maybe I could run IE in Wine?

---

### Post by Excalibre on 2008-09-28
> **AutoLink said:**
> Some of the web sites I use just won’t work in Firefox. As far as I know, there is no IE for Ubuntu. Maybe I could run IE in Wine?
One quick suggestion here: Generally Wine isn't that great. Some software is well-supported by it but a lot of other software is flaky or non-functional.

If you really find you need IE (I haven't had to do this much, but I guess your mileage varies :)) you can install Windows on a virtual machine. VMWare Server is a free (as in beer, not as in speech) piece of virtual machine software you can install, and then run as a program on Ubuntu. You install Windows onto a virtual Mmchine, and then you can run IE without having to boot into Windows -- it's a ton more convenient. I use it sometimes to watch movies online with Netflix -- their online viewing thing requires IE. So if you have only an occasional need to run one piece of Windows software, your best bet is a virtual machine -- it's a lot easier than rebooting and tends to be a lot more reliable than Wine. There are lots of threads here with information about VMWare, and I recommend it.

I do some light web development work sometimes as well, and VMWare is a Godsend for that, since I can have separate VMs with different versions of IE, since you can't install two different versions on Windows side by side.

---

### Post by AutoLink on 2008-09-28
Thanks, Excalibre.

Would it work to both dual boot XP and run XP in VMware Server for a time? And then, when I was sure that everything was working as it should with the VMware installation, uninstall the other XP and incorporate that disk space into one of the Ubuntu partitions?

---

### Post by Excalibre on 2008-09-29
> **AutoLink said:**
> Thanks, Excalibre.

Would it work to both dual boot XP and run XP in VMware Server for a time? And then, when I was sure that everything was working as it should with the VMware installation, uninstall the other XP and incorporate that disk space into one of the Ubuntu partitions?
Yes, that's fine.

If you're worried about Windows Product Activation, that's a relevant concern: you can only install Windows XP (or later) a certain number of times before your product key will be disabled, but I've used my own Windows XP product key on my Windows partition as well as on at least a couple virtual machines with no difficulty. My understanding is that if you do run out of activations, you can just call Microsoft and they'll give you another one if necessary, but don't expect to be able to use your one product key too many times. I think you have several uses before they stop you. I usually use Windows 2000 -- which is before they invented Product Activation -- since I have a copy from my last computer and it will run almost anything Windows XP will, so if you have a copy of that you should keep that in mind. But I've created two XP virtual machines as well, and having it installed on a partition and on virtual machines hasn't caused any problems.

As for getting rid of your Windows partition later, that's pretty easy. You can get rid of a partition and resize another one to fill the space using GParted, which is included on the Ubuntu installation CD. You have to boot off of the CD to change the size of your Ubuntu partition, because you can't change the size of a partition while you're using it. There will probably be a couple other minor modifications you have to make to your Ubuntu installation as well (you'll probably have to edit /etc/fstab, which is the file that tells the OS what partitions you have and what they are, and /boot/grub/menu.lst, which is what tells the boot loader, Grub, where your OS is and how to start it.) It's not hard, but it would be a good idea to do the necessary research before you change your partitions around, because it would be scary if your computer unexpectedly refused to boot because you had some configuration file wrong. (If you do make a mistake, you'll be able to boot from the Live CD and then fix it.)

---

