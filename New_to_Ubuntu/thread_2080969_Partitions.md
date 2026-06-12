---
title: "Partitions"
date: 2012-11-05
forum: New to Ubuntu
---

### Post by johnmd on 2012-11-05
I am running Ubuntu 12.10 Gnome on a IBM T60 laptop. It has a 60 GB hard drive.
I had to install it so that it took the whole HD as I had it so messed up that was the only way I could get it to install.
Is there any program or way that I can partition part of this drive 
so that I can install another OS?
I want to be able to boot and select which one I want to use and I don't want to loose what I already have installed.
I was thinking of something like the old Partition Magic in Windows.

Thanks
John

---

### Post by dannyboy79 on 2012-11-05
you could use gparted to partition the drive down further but keep in mind that normally when windows is installed AFTER ubuntu, it will overwrite the MBR and install it's own bootloader. not to mention windows has to be installed in a primary partition not a logical one. what I would do is make a 20gb of unallocated space BEFORE ubuntu using gparted, which is where you'll install Windows, it will format the unallocated space for you. Afterwards you'll have to use a tool to reinstall grub so you can then boot into either windows or ubuntu

---

### Post by johnmd on 2012-11-05
I don't want to install Windows, I was going to install another version of Linux. Maybe Wine or Fedora.
I have been playing around with this for a few day.

I bought the laptop just to run Linux on but want to find which one I like the best. I was running Ubuntu back in 2006 (ver. 6.06)and liked the way it docked programs but it seems that they had to change that.
It's a whole new world now days. I guess we have to take the good with the bad.
I have GParted loaded but it didn't seem to want to do what I wanted to do.
I will look at your blog.

---

### Post by oldfred on 2012-11-05
You cannot use gparted from your running system, best to use liveCD, either Ubuntu which has gparted or the separate gparted liveCD or partedmagic which is also gparted and some other tools.

GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)
Screenshots of using gparted
[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)

[http://partedmagic.com/](http://partedmagic.com/)
[http://gparted.sourceforge.net/faq.php](http://gparted.sourceforge.net/faq.php)

If just testing you can use 10GB. Or if you think you may want to dual boot create a separate data partition for some data also.

You will have to keep track of which systems boot loader is in the MBR and then is in control. Ubuntu installs to sda by default, manual install gives a choice on where to install grub2's boot loader.

---

### Post by dannyboy79 on 2012-11-05
if you just want to test out different distos most will run from a usb stick and load into RAM or if you really want to install another linux distro, the installer should present you an option to install along side your current ubuntu install. if it doesn't, use a live cd and gparted to shrink dowm your current partition and leave some unallocated space.

---

### Post by NM5TF on 2012-11-05
I highly reccommend burning a copy of Boot Repair BEFORE messing
with your disk partitions...

go here:

[http://sourceforge.net/p/boot-repair/home/Home/](http://sourceforge.net/p/boot-repair/home/Home/)

I had to learn the hard way!!!

Tommy

---

### Post by johnmd on 2012-11-05
Ok If I do this and install Fedora on the created partition will both OS's be set up on the MBR?

---

### Post by oldfred on 2012-11-05
There is only one MBR per hard drive.

With Ubuntu, it usually finds other installs, adds them to the grub menu,  and allows you to boot them.

With Fedora the default install uses LVM. Some have had issues resolved by adding the lvm2 driver in Ubuntu and mounting the Fedora partition before running:
sudo update-grub

Some suggest not using the default LVM with Fedora,  as with the multi-boot and other systems outside the LVM, it just adds complexity without any of the advantages of LVM.

Not sure how Fedora handles finding other system to boot. Always good or have Boot-Repair or know how to easily reinstall grub2's boot loader to the MBR.

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)
How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10 - grub2) - talsemgeest
[https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader](https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader)
Reinstall grub2 - Short version & full chroot version
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB2]("https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB2")

---

### Post by johnmd on 2012-11-05
Ok Here is what I am going try.
I have GParted on a CD Rom and I am going re-size the partition. 
Probably divide it equally. Then install Fedora on that new partition. Then if it doesn't boot to either I will run the Ubuntu Live and the run

set it to boot from CD in the BIOS
I don't quite understand the following.
" reboot your computer and set it to boot from CD in the BIOS and boot into a live session. "
I have seen when loading Ubuntu an option to TRY Ubuntu. I am assuming that is what is meant by running it live but the part about "to boot from CD in the BIOS" I am not quite sure of.

Now if this fails and I get no where would it be better to install Fedora first and then Ubuntu?
Also is there a way to format both partitions?
I have tried to reload Ubuntu and Fedora in the past and ended up with two of each on the hard drive but only being able to access one of the four.
This whole exercise is for me to learn a bit more about Linux. I started using it on and off in 1995. That was when Red Hat was King of the hill. I'm not a young person but do like to keep the mind active. I really appreciate the help you are giving me.
I write very basic web pages but ones that work and I make my living at that with the ads I run. That's where I spend most of my time.
[http://oldcarandtruckpictures.com](http://oldcarandtruckpictures.com) is the main page and that one get between 6000 to 7000 hits a day. It has a very high Google ranking. But winter is just around the corner and up here it can be a bit nasty outside so I was looking for something to keep me busy. So if I have to load the system several times, it is just time that I loose.
I did notice once that when I loaded Mint is made a boot listing that showed every thing on the HD. If all else fails maybe I will load Mint after Fedora.

Thanks
John

---

### Post by oldfred on 2012-11-05
BIOS lets you set what device to boot from. CD, which hard drive, other devices. 

Often newer computers have a one time boot key where you can select CD, and then in BIOS you just set default to Hard drive so it does not have to look at CD drive and not find a CD then go to hard drive.

From gparted you can format partitions, but the installers usually want to reformat anyway. 

Booting liveCD should give two options, one is try system so you can check that all your hardware works and learn a bit about system, the other is install.

My Dad was from Kingston NS. Went to visit Grandma back in '50s but have not been there since. Most relatives now gone.

---

### Post by johnmd on 2012-11-05
OK now I know what your talking about. My computer is defaulted to the cd rom and then the hard drive.
That's not hard to change.

Greenwood is about an 1 1/2 hours from here. Been there many times.

John

---

### Post by johnmd on 2012-11-05
OK here is what i did and what the results were.
First I burnt a copy of GParted and booted on it. It booted fine but when it came to run the GUI things didn't go so fine. I got a lot of very fast vertical wide lines. I tried every thing I knew and ended up pulling the plug and removing the battery to shut it down.
I tried it a couple of more times with the same results.
The made another copy and got the same results.
So I thought I would try the live Ubuntu on the cd.
That booted fine but I couldn't find where to run GParted from it.
I looked in all the files and couldn't find any thing except a file
gparted-pkexec and that wouldn't run the program and that was in usr/bin.
Any ideas?

Thanks
John

A point of interest. My web sites are on a dedicated server not far from you.
They were in Chicago but were moved closer to the company that hosts them in Madison.

---

### Post by johnmd on 2012-11-05
I just got it working. I had to use a fail safe mode and the min of settings.
Now to test it.

john

---

### Post by johnmd on 2012-11-05
I just booted the system and Ubuntu ran and the two other partitions showed in the files.
Now to learn about that boot repair program.

John

---

### Post by Bartender on 2012-11-05
Do you mean you got the GParted LiveCD to work?  I've spun GParted CD's on dozens of machines and only had to drop back to the video fail-safe mode once.  Maybe twice.  

Don't buy lottery tickets this week! :P

Last time I took a screenshot from GParted it was kind of a pain.  It's easier to take a screenshot from the Ubuntu CD if you boot up and go into "Try Ubuntu".  Screenshot should be under accessories and you can save to a thumb drive.

It might be helpful to attach a screenshot so we can see how many, and what kind, of partitions you have now.

---

### Post by newb85 on 2012-11-05
> **johnmd said:**
> I was going to install another version of Linux. Maybe Wine or Fedora.

Don't know if you've figured this out already, but Wine is not a Linux distro like Ubuntu, Debian, or Fedora.  It is an abstraction layer that has to be installed on an existing distribution.

---

### Post by johnmd on 2012-11-05
I meant to say Mint.
Now to try the screen shot

---

### Post by johnmd on 2012-11-06
Update. Here is what I ended up doing.
Fist off before I could install Fedora on the partition that was set up as ext 2 I had to change it to an ext 4 which was no problem.
I installed Fedora and it did as before and took control of the boot sector and only had allowed me to boot Fedora.
I had a live boot repair disk ready just in case but I decided that I would load Mint. I did this and it set up all three distributions on the boot sector.
I can also see the files on the other to from each other and so far I have only checked Ubuntu but it will view the files on my Windows computer. I tried it on Fedora and it will have to be set up. Ubuntu did this automatically.
This may have not been the accepted way to do this but all is well that ended well.
Now i can test each system when ever I want to. The Live CD was OK but it was slow and didn't allow you to do all the things I wanted to try/
Thanks everyone for your help.

John

---

