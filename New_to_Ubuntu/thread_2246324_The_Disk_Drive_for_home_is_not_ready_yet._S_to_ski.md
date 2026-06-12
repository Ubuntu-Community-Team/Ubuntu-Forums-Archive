---
title: "The Disk Drive for /home is not ready yet. S to skip mount or M for manual recovery"
date: 2014-09-29
forum: New to Ubuntu
---

### Post by piadex2 on 2014-09-29
Dear Forummates,

When I want to start Ubuntu I get: "The Disk Drive for /home is not ready yet or not present. Continue to wait, or press S to skip mount or M for manual recovery"
here is some help:

```
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda3 during installation
UUID=51795220-f0e9-4ac9-8f46-210aa52904e0 /               ext4    errors=remount-ro 0       1
# /home/ was on /dev/sda7 during installation
UUID=f9adb9be-d126-415c-a6af-23fbdb7b5a87 /home/          ext4    defaults        0       2
# swap was on /dev/sda8 during installation
UUID=55bfe5be-f34b-4e67-b724-5679f16ee6a2 none            swap    sw              0       0

```

Please help.
Thank You in advance.

piadex2

ps: it worthless to wait nothing happens

---

### Post by yancek on 2014-09-29
Does it boot when you hit the S key?
From a terminal run:  blkid  then compare the UUID you get for sda7 with the one listed in fstab.

---

### Post by piadex2 on 2014-09-29
Hi,

When I hit "s" it boots but only as a guest which is not good enough. sdaX goes 1 to 6 so sda7 and sda8 do not exist.
Any idea?
Thank You.

piadex2

ps: does this mean I should reinstall this or there is a way to relocate home and swap?
by the way can swap be on the same location where as the system as well?

---

### Post by Bashing-om on 2014-09-30
piadex2; Hi !

Just as a maybe, quick fix:
Boot to the login screen; key combo crl+alt+F1 to obtain a console;
In the console termianl login; username and password.
Terminal commands:
```

sudo touch /forcefsck
sudo shutdown -r now

```
Which will force a file system check at next re-boot, and the following command does the "following re-boot".

Does the system now behave it's self ?

[INDENT][INDENT]maybe yes
[INDENT][INDENT][INDENT]maybe not so yes
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by Mike_Walsh on 2014-09-30
For some reason, I've been getting this since the 14.04.1 point update; but I just wait, and it starts up as normal. After maybe 10 starts or so, it no longer appears.....until the next time I do something major, like maybe installing a different desktop, or like the other day, when I finally got around to setting up a separate /home partition.

Then it's back again; for maybe another 10 boot-ups or so.....after which it no longer appears.

I've quit worrying about it; it always seems to sort itself out if I leave it alone, and the system continues to function perfectly. I kinda wonder if it's the system's way of reminding you (and perhaps itself) that something major has changed.....at least until you get used to it..!

Why fix it, if it ain't broken?


Regards,

Mike.

---

### Post by piadex2 on 2014-09-30
Hi Mike,

Well my installation wont work even if I wait a whole day.
So I need something that is different than waiting.
But thank You for sharing Your experiences.

piadex2

---

### Post by piadex2 on 2014-09-30
Hi Bashing-om,

I will give it a try as soon as possible.
Thank You.

piadex2

---

### Post by piadex2 on 2014-09-30
[COLOR=#000000]Hi Bashing-om,

I stuck after ctrl+alt+F1. It gives me a fully black screen. No shell at all. I can type but without any effect...
Ideas?

piadex2[/COLOR]

---

### Post by piadex2 on 2014-09-30
Hi Bashing-om,

I pressed M for manual recovery, and then typed the commands You recommended. Restart then checking. So Your code worked: it checks but it did not solved the problem.

piadex2

---

### Post by yancek on 2014-09-30
What is the output of blkid I suggested in my earlier post?  Your initial post shows /home on sda7 and in your subsequent post you indicate you only go up to sda6 so you need to figure out which one is /home.  Login as guest and run the command:  df -h
If /home mounts as guest this should tell you what it is

---

### Post by Michael_McKenney on 2014-09-30
How old is the drive?   You could have a bad drive.  Try shutting down for a few hours and let the drive cool down.  You might be able to get it to restart long enough to backup your data.  I have seen many drives in multi drive systems not start up and fail.  Are the drives stacked tightly in your chassis.  You might need to space them out and add better fans to cool them.   Most drive manufacturers don't want drives stacked in each bay.  They want 1" of space for cooling and air flow.

---

### Post by Mike_Walsh on 2014-09-30
Actually, the difference between your warning and mine is that yours refers to /home 'not being ready'. In my case, I get the UUID (the long string of letters and numbers) that in fact refers to the entire O/S 'not being ready yet'.

Googling it shows that this message appears to come up quite regularly to various people, although the partition referred to is very often different (sometimes /home, sometimes /tmp, sometimes, like mine, the UUID):-

[https://www.google.co.uk/#q=The+Disk+Drive+for+%2Fhome+is+not+ready+yet.+S+to+skip+mount+or+M+for+manual+recovery](https://www.google.co.uk/#q=The+Disk+Drive+for+%2Fhome+is+not+ready+yet.+S+to+skip+mount+or+M+for+manual+recovery)

Have a look through some of these. They **may **be of some use.

Hope that helps.


Regards, 

Mike.

---

### Post by Michael_McKenney on 2014-09-30
It could also be your power supply is not large enough to provide the wattage needed to spin up your drives at post.  I have seen this on numerous occasions that users need a power supply upgrade to handle more hardware.

---

### Post by Mike_Walsh on 2014-09-30
> **Michael_McKenney said:**
> It could also be your power supply is not large enough to provide the wattage needed to spin up your drives at post.  I have seen this on numerous occasions that users need a power supply upgrade to handle more hardware.

@Michael McKenney; That's a distinct possibility for the OP, I'll grant you. But in **my **case, this has only happened since the first point release, back in July.....and my system is just the same as it's always been; bog standard. The only thing I've added to it is an external HDD; but that runs from a USB hub with its own independent power supply, and the system still functions perfectly, so.....

I'm leaving WELL alone..!

Regards,

Mike.

---

### Post by piadex2 on 2014-09-30
Hi,

It is pretty new ...

p.

---

### Post by piadex2 on 2014-09-30
Dear yancek,

Here are the results. First the blkid:
```
/dev/sda1: LABEL="Win7" UUID="F430478C304754B0" TYPE="ntfs" 
/dev/sda2: UUID="CAD0-08A7" TYPE="vfat" 
/dev/sda3: UUID="51795220-f0e9-4ac9-8f46-210aa52904e0" TYPE="ext4" 
/dev/sda5: LABEL="Adat" UUID="01CDF367935C4050" TYPE="ntfs" 
/dev/sda6: LABEL="System" UUID="01CDF36631772CC0" TYPE="ntfs" 

```

And now the df -h command:
```
/dev/sda3        16G  7,7G  7,4G  52% /
udev            488M   12K  488M   1% /dev
tmpfs           198M  824K  198M   1% /run
none            5,0M     0  5,0M   0% /run/lock
none            495M  200K  495M   1% /run/shm
none            495M  1,4M  494M   1% /tmp/guest-qT6aof
/dev/sdb        3,8G  2,8G  1,1G  73% /media/24220EEC220EC2B2

```

These were created when I was logged in as a guest.
What do You think of these?
Thank You in advance.

piadex2

ps: the "/dev/sdb        3,8G  2,8G  1,1G  73% /media/24220EEC220EC2B2" is my pendrive so do not be bothered by that.

---

### Post by yancek on 2014-09-30
> # /home/ was on /dev/sda7 during installation
UUID=f9adb9be-d126-415c-a6af-23fbdb7b5a87 /home/          ext4    defaults        0       2

Your fstab output above from your initial post shows and entry for a separate /home partition.  Your blkid output does not show any separate /home
 partition and it should show partitions which are mounted or not mounted.

```
What do You think of these?
```

I think if you put a hash mark at the beginning of your UUID for /home it will work, as below:

> #UUID=f9adb9be-d126-415c-a6af-23fbdb7b5a87 /home/          ext4    defaults        0       2

You might need to do the same for the swap entry if it is still in fstab.  You don't seem to have a swap partition.

---

### Post by piadex2 on 2014-09-30
Hi,

Thank You for the answer. How to put the hash mark there? Is there a built in editor?
Thanks.

piadex2

---

### Post by piadex2 on 2014-09-30
HI,

I found this: [http://community.linuxmint.com/tutorial/view/1513](http://community.linuxmint.com/tutorial/view/1513)
So there is a chance that gedit will do the job. My problem is that it says "operation not allowed". May be that is because I am logged in as guest?
Thank You for Your help in advance.

piadex2

---

### Post by yancek on 2014-09-30
When you installed Ubuntu you were required to create a user with a password in order to complete the installation.  Use the password you created for that user.  Open a terminal and type:  sudo gedit /etc/fstab

you should be prompted for the password for the user you created on install.  If you don't know it, then it will be considerably more difficult.

---

### Post by Impavidus on 2014-10-01
Commenting out the line for the /home partition may remove the error on boot, but it still leaves the question of why this problem occured in the first place. Usually people have a swap partition. When installing automatically one is created by default. A /home partition is not created by default, but your root partition is small, so I think it's likely you had one. /etc/fstab mentions both a swap partition and a /home partition, so I assume you had both, but both no longer exist. Can you boot from a live disk and check the contents of /home to see if your files are there? Because I wouldn't be surprised if it appeared empty. Did you do anything in Windows that involved partitioning? Because Windows is known for destroying things it doesn't know about. Only being able to login as guest is consistent with your home directory being gone.

Also post the output of```
sudo fdisk -l
```(that is dash lower case L) and a screenshot from gparted (available on the live disk).

---

