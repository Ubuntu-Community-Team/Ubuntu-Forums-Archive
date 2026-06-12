---
title: "Change a dual boot OS without messing up grub"
date: 2012-12-08
forum: New to Ubuntu
---

### Post by natchezjohn on 2012-12-08
I have ubuntu 10.10 and 12.10 dual booting. Because 12.10 was added later it is the first entry in boot.

Here is my disk layout 

[IMG]http://natchezms.us/Screenshot.png[/IMG] 

I'd like to put a linux mint in the first partition and retain ubuntu as the first entry at boot up and remain as the default.

Of course, keeping grub intact is of primary concern.

---

### Post by Bartender on 2012-12-08
natchez -

Can I ask you to install gparted partition editor, then go into that and take a screenshot of what it sees?  Then post the screenie here?  I'm much more accustomed to deciphering the gparted style map.  The one you attached isn't familiar to me.

It looks like sda1 is a primary partition.  Then the rest of the drive is an extended partition, with another version of Ubuntu installed to sda6.  Right?

Is 10.10 in sda1?  Or 12.10?

In your previous thread, we'd talked a bit about simply removing one of the Ubuntu installs.  I was concerned that would screw up GRUB.  If you're going to install Mint right over the top of the older version of Ubuntu, that's a whole different thing.  GRUB *should* see that you have another version of Linux, and configure itself correctly.  

"Should" sounds like famous last words in this case, doesn't it?  As in, "gosh, that shoulda worked; now what?"

Hopefully some other folks will weigh in on this...

---

### Post by oldfred on 2012-12-08
Ubuntu installs do not let you not install grub2. About the only choice is to install to a partition (which is not recommended), just as a throw away that you will not use. 
Or you can install to the MBR and then boot into 12.10 and reinstall its grub into the MBR.

Grub also remembers where to reinstall on major updates. So if Mint is installed to the MBR, it may automatically reinstall on an update.

From any working install you can reinstall its boot loader into the MBR. Just first boot into it. So if booting from Mint, boot into 12.10 and run these:

       sudo grub-install /dev/sda
    sudo update-grub

But I am not sure if that updates the setting on reinstall.

In Mint use this to see where it will re-install:
       #To see what drive grub2 uses see this  - grub-pc/install_devices:
sudo debconf-show grub-pc
 sudo grub-probe -t device /boot/grub

    
       #to get grub2 to remember where to reinstall on updates:
sudo dpkg-reconfigure grub-pc
#Enter thru first pages,spacebar to choose/unchoose drive, enter to accept, do not choose partitions


Someone posted that unchoosing all drives then left no reinstall choice, so grub would not get reinstalled.

---

### Post by Bartender on 2012-12-08
oldfred, you kinda lost me...

I *think* what the OP has so far is a functional dual-boot with 10.10 in sda1 and 12.10 in sda6.

And I *think* what he wants to do is over-write 10.10 in sda1 with Mint.

But it might be the other way around - maybe 12.10 is in the primary partition (sda1) and 10.10 is inside the extended (sda6)

Do you think he'd have to mess with the bootloader at all?  I'm kinda sorta thinking that GRUB will just take care of things on its own.

natchez, selecting the default OS isn't a big deal.  As you say, a functional GRUB is the highest priority.  We can switch the default OS later if necessary.  If we don't get a definitive answer on this soon, maybe I'll just simulate your setup on a spare PC and see what happens.

---

### Post by grahammechanical on 2012-12-08
I have not installed Linux mint but my guess would be that as it is installing last it will put its boot loader into the MBR and so Mint will be at the top of the list. But if the OP does what oldfred says, boot into 12.10 and run 

> sudo update-grub

And then

> sudo grub-install /dev/sda

That will put the 12.10 version of Grub back into the MBR and the first OS in the list will be Ubuntu.

This is how I do it.

Regards.

---

### Post by natchezjohn on 2012-12-08
I'm about to demonstrate why I posted in the **Absolute** Beginners section.

There are a lot of things about linux that give me the cold robies, make my teeth hurt, one of them is (the dreaded) grub. With windows it was the mbr. Every time I have fooled with them I ended up formating and reinstalling.

I was going to put mint in place of 10.10 because the space was there. I've got PLENTY of space for 12.10 on the partition as I have never used even 35 gigs even with those bloated windows thingees.

Thank you for your respnses but I'll leave well enough alone.

FYI - 12.10 is in partition 2

---

### Post by natchezjohn on 2012-12-08
On the other hand **Bartender):P** if you DO go through the trouble of setting it up on another pc. I'll follow your lead.

---

### Post by debodas on 2012-12-08
If I understand what you want to do correctly...

Boot into a linux mint live CD, install it onto the partition you want to install it on (/dev/sda1?). Remember to tick the option to format the partition (keep it as Ext4 though). Give it a / mount point. To keep grub functional, install it on /dev/sda (you'll find this option where you select the partition for linux mint to install on.

So, you have now selected linux mint to be installed on the partition you want it on, and selected grub to be installed on /dev/sda. This should do what you want, so continue with he installation and you should be sweet.

---

### Post by natchezjohn on 2012-12-08
Oh! and you asked for a gparted shot. Here it is

[IMG]http://natchezms.us/Screenshot2.png[/IMG]

---

### Post by natchezjohn on 2012-12-08
> **kingnick42 said:**
> If I understand what you want to do correctly...

Boot into a linux mint live CD, install in onto the partition you want to install in on (/dev/sda1?). Remember to tick the option to format the partition (keep it as Ext4 though). Give it a / mount point. To keep grub functional, install it on /dev/sda (you'll find this option where you select the partition for linux mint to install on.

So, you have now selected linux mint to be installed on the partition you want it on, and selected grub to be installed on /dev/sda. This should do what you want, so continue with he installation and you should be sweet.

Kingnick - YOU tempt me. Rational, precise, within my (limited) capabilities.

---

### Post by natchezjohn on 2012-12-08
> **natchezjohn said:**
> Kingnick - YOU tempt me. Rational, precise, within my (limited) capabilities.

**[COLOR="Red"]BINGO!!! Just as advertized[/COLOR]**

Thanks Linuxmint up and running - Ubuntu AOK. Boot menu just fine!!

---

### Post by Bartender on 2012-12-08
Hey, awesome, good job.  So is Mint installed to sda1 or sda6?  

Take some notes!  Right now the steps you took are fresh in your mind.

---

### Post by debodas on 2012-12-08
> **natchezjohn said:**
> **[COLOR="Red"]BINGO!!! Just as advertized[/COLOR]**

Thanks Linuxmint up and running - Ubuntu AOK. Boot menu just fine!!

Sweet, good to hear its all working.

---

### Post by natchezjohn on 2012-12-08
> **Bartender said:**
> Hey, awesome, good job.  So is Mint installed to sda1 or sda6?  

Take some notes!  Right now the steps you took are fresh in your mind.

Mint on sda1. I just printed out King's post and followed it step by step.
"[COLOR="Blue"]If I understand what you want to do correctly...

Boot into a linux mint live CD, install it onto the partition you want to install it on (/dev/sda1?). Remember to tick the option to format the partition (keep it as Ext4 though). Give it a / mount point. To keep grub functional, install it on /dev/sda (you'll find this option where you select the partition for linux mint to install on.

So, you have now selected linux mint to be installed on the partition you want it on, and selected grub to be installed on /dev/sda. This should do what you want, so continue with he installation and you should be sweet.[/COLOR]"

---

