---
title: "Helllp!  OS not found!"
date: 2008-06-06
forum: New to Ubuntu
---

### Post by Mister Tea on 2008-06-06
Hi people, I'm just hoping that someone may be able to help me out...
My wife attempted to install Ubuntu on her **Dell Inspiron 1501** that runs Vista and the installation messed up before the part where you choose partition info.

Now she tries to power on and she gets this:
[B]PXE-E61: Media test failure, check cable
PXE-H0F: Existing Broadcom PXE ROM
Operating system not found[/B]
I've looked at the order in BIOS and Network is last on the list.
Ubuntu will boot (live) from disc, this is the only thing she can use.
Tried the SuperGrub -->(!WIN!) and got nothing.
<snip>

Then using Terminal in Ubuntu I did this:
**sudo fdisk -l**
and what I got was:
[B]/dev/sda1         FAT16
/dev/sda2         Extended
/dev/sda5         linux swap/Solaris[/B]
...is the windows partition still there?

I don't really know what I'm doing as I'm learning as I look at forums like these, thought it best to come with as much info as I could get so someone might be able to help me.
My darlin missus just wants her Vista back, any ideas?
Much appreciated in advance.

---

### Post by PmDematagoda on 2008-06-06
When you said "the installation messed up", could you please elaborate on it? Exactly how did it mess up?

---

### Post by Sef on 2008-06-06
> Then using Terminal in Ubuntu I did this:
sudo fdisk -l
and what I got was:
/dev/sda1 FAT16
/dev/sda2 Extended
/dev/sda5 linux swap/Solaris
...is the windows partition still there?

I don't really know what I'm doing as I'm learning as I look at forums like these, thought it best to come with as much info as I could get so someone might be able to help me.
My darlin missus just wants her Vista back, any ideas?

1) Windows Partition > Vista is gone.  Vista on NTFS should be where the FAT16 is.  

2) For recovering Vista > 

a) Reinstall it if you have the disk or the recovery disk. 

b) Download [Test Disk]("http://www.cgsecurity.org/wiki/TestDisk") and see if you can recover the partition.

c) (Desperation) Buy Vista.

d) Neither option a, nor b, nor c is not valid > Just install Ubuntu.

3) Next time, you want to install Ubuntu, read [Psychocat's Ubuntu]("http://www.psychocats.net/ubuntu/index") first. (That is meant as friendly advice.  I have done my share of oopses too.)

---

### Post by Mister Tea on 2008-06-06
All I can get from her is that it said something along the lines of...
**/dev/sda1 failed to** (create?) **a partition**
or something to that effect.

It then gave her the option to try again or quit,
she 'tried again' a few times and with no further luck, quit.
Wouldn't reboot properly again giving the *OS not found* message.

---

### Post by PmDematagoda on 2008-06-06
So what type of Ubuntu install are you looking for? Is it dual-boot or only Ubuntu?

---

### Post by Mister Tea on 2008-06-06
She was going for dual-boot.
I think right now she is too scared to bother with Ubuntu and just wants to go back to how it was.

If it is of ANY significance, She had previously installed the same Ubuntu (dual-boot) from the same disc successfully within Vista and deleted it again properly.
This time she installed it after booting with the Ubuntu Live CD.

---

### Post by Mister Tea on 2008-06-06
> **Sef said:**
> 1) Windows Partition > Vista is gone.  Vista on NTFS should be where the FAT16 is.  


Are you saying that all her info and Vista are probably gone?
This is the bit where I am stuck, I can't quite work out whether or not her stuff is there to save.
We're hesitant to simply 'start over' and re-install windows if there is still a chance of her stuff being saved first.

Thanks also for the link. I only run Ubuntu from CD and have no troubles but one day I may need it. :)

---

### Post by quinnten83 on 2008-06-06
> **Mister Tea said:**
> Are you saying that all her info and Vista are probably gone?
This is the bit where I am stuck, I can't quite work out whether or not her stuff is there to save.
We're hesitant to simply 'start over' and re-install windows if there is still a chance of her stuff being saved first.

Thanks also for the link. I only run Ubuntu from CD and have no troubles but one day I may need it. :)

Yup, all gone.
If it was still there there would be a NTFS partition.
If you still decide to dualboot after recovery, install windows first and then Ubuntu. Windows wipes out grub if you install it last.

---

### Post by Mister Tea on 2008-06-06
> **quinnten83 said:**
> Yup, all gone.

Crud.
Thanks for all your help anyway. I didn't know that Ubuntu was an effective pesticide!

If I re-install windows properly will that fix up any of these partitions? A factory settings kinda thing?

And with all that being gone I won't be able to re-install without the disc right?
...yeah yeah, dumb question.

---

### Post by Mister Tea on 2008-06-06
> **Mister Tea said:**
> I didn't know that Ubuntu was an effective pesticide!

RRhh! I meant WINDOWS being a GRUB killer.
Wanna fix this so I can sleep, lol.

---

