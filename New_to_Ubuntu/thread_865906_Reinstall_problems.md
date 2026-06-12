---
title: "Reinstall problems??????"
date: 2008-07-21
forum: New to Ubuntu
---

### Post by K-D on 2008-07-21
Hi guys,

I'm brand new to Ubuntu and have had some problems with my sound after messing around to try and get flash videos to work.

I don't really know what I did so as I only installed Ubuntu last week I thought I would just reinstall (as sound was working before).

However after running the boot cd last night and installing the pc would not boot up?

I ran the boot cd again and reinstalled again but it froze half way throught the process?????

Getting worried I may be PC less unless I can get this to work?

I have two internal hard drives but there were a couple of issues when installing these as the larger drive wouldn't boot so I installed on the smaller HD and used the larger one as storage?

Any ideas how I can get around this would be great!

---

### Post by Sealbhach on 2008-07-21
When you try to boot up, does the GRUB bootloader give an error message? If so, what error number is it?


.

---

### Post by K-D on 2008-07-21
I think it was 23.....

I'm not on my pc at the moment however will find out now

---

### Post by K-D on 2008-07-21
it was 15

---

### Post by oedha on 2008-07-21
maybe you can try supergrubdisk

---

### Post by Sealbhach on 2008-07-21
There was a fix here for Error 15

[http://ubuntuforums.org/showthread.php?t=644773](http://ubuntuforums.org/showthread.php?t=644773)

You want to give this a try?


.

---

### Post by K-D on 2008-07-21
Will give it a blast tonight.

It seems logical that the two hd may have gotten a bit mixed up as I was messing around with the master and slave cables on my first install.

Thanks for you help i will let you know how I get on.

---

### Post by K-D on 2008-07-21
Hi,

I have tried the quick fix from the boot by pressing 'e' but it doesn't change the screen.

If install again will this fix the problem or is this going to continue until I manage to fix?

I am having to use the live cd at the moment.....

---

### Post by Sealbhach on 2008-07-21
Hi, I just found this in the documentation.


[https://help.ubuntu.com/community/How_to_dual-boot_Ubuntu_and_XP_after_installing_them_separately_on_two_HDs](https://help.ubuntu.com/community/How_to_dual-boot_Ubuntu_and_XP_after_installing_them_separately_on_two_HDs)

It may help if you're reinstalling.

Also this bit linked from that page:

[http://www.gnu.org/software/grub/manual/html_node/DOS_002fWindows.html#DOS_002fWindows](http://www.gnu.org/software/grub/manual/html_node/DOS_002fWindows.html#DOS_002fWindows)


Interesting. 

When you say you used the larger one as storage, what do you mean? 

.

---

### Post by K-D on 2008-07-22
Well when I installed Ubuntu first time around there was an error message when booting using the larger drive.  So I ran the boot disk again installed on the smaller drive and just planned to format the larger drive once i had access.  I therefore switched round the priority of booting devices.

When this worked I could access the larger drive from the 'home' part on Ubuntu and could access it to store movies etc from my freinds external drive.

I accessed the drives last night from the boot cd and formatted them both and tried reinstalling but no joy.....

actually driving me crazy now!

---

### Post by K-D on 2008-07-22
I haven't partitioned the drives with XP I am working solely on Ubuntu as thought I could handle the transition over.

if that makes any difference to anyone that can save me from my girlfreind moaning that i should have kept Windows........

---

### Post by Sealbhach on 2008-07-22
> **K-D said:**
> 

actually driving me crazy now!

Is it still Error 15?

Have you tried Super Grub disk?

[http://supergrub.forjamari.linex.org/#help](http://supergrub.forjamari.linex.org/#help)

.

---

### Post by K-D on 2008-07-22
I will give it a blast tonight.  I've never used it before is it fairly straight forward?

---

### Post by Sealbhach on 2008-07-22
> **K-D said:**
> I will give it a blast tonight.  I've never used it before is it fairly straight forward?

TBH I've never used it but people recommend it a lot for these sorts of problems. 
[U]
I wish someone else could come in on this post who has got two hard drives and knows a bit more about Error 15.[/U]

.

.

---

### Post by K-D on 2008-07-22
I've kinda fixed it.......I think there is some issue with one of my drives it's a maxtor beast but doesn't seem to want to work with Ubuntu!

Thanks for your help dude!

---

### Post by Sealbhach on 2008-07-22
> **K-D said:**
> I've kinda fixed it.......I think there is some issue with one of my drives it's a maxtor beast but doesn't seem to want to work with Ubuntu!

Thanks for your help dude!

Good. So are you able to run Ubuntu?

If so what do you get when you do:
```

sudo fdisk -l
```


.

---

### Post by K-D on 2008-07-23
> **Sealbhach said:**
> Good. So are you able to run Ubuntu?

If so what do you get when you do:
```

sudo fdisk -l
```


.

I get this message:


Usage: fdisk [-b SSZ] [-u] DISK     Change partition table
       fdisk -l [-b SSZ] [-u] DISK  List partition table(s)
       fdisk -s PARTITION           Give partition size(s) in blocks
       fdisk -v                     Give fdisk version
Here DISK is something like /dev/hdb or /dev/sda
and PARTITION is something like /dev/hda7
-u: give Start and End in sector (instead of cylinder) units
-b 2048: (for certain MO disks) use 2048-byte sectors


mean anything significant?

---

### Post by Sealbhach on 2008-07-23
> **K-D said:**
> I get this message:


Usage: fdisk [-b SSZ] [-u] DISK     Change partition table
       fdisk -l [-b SSZ] [-u] DISK  List partition table(s)
       fdisk -s PARTITION           Give partition size(s) in blocks
       fdisk -v                     Give fdisk version
Here DISK is something like /dev/hdb or /dev/sda
and PARTITION is something like /dev/hda7
-u: give Start and End in sector (instead of cylinder) units
-b 2048: (for certain MO disks) use 2048-byte sectors


mean anything significant?

That just means the command was not fully recognised (incorrect).

Did you copy and paste the command into the terminal?

It's an ell, not a one. That might be what caused it.

.

---

