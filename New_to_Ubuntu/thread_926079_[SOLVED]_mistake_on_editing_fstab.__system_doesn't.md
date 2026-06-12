---
title: "[SOLVED] mistake on editing fstab.  system doesn't find /home when booting"
date: 2008-09-21
forum: New to Ubuntu
---

### Post by ejv on 2008-09-21
Hi

I wanted to separate my /home in a new partition.  Read many posts and tutorials and decided to follow this one

[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

Everything went fine until the edition of the **fstab.**  The mistake i made was: my ubuntu is on spanish and the command (Control-X) doesn't save but exits which i, of course, didn't notice.  I answered "yes" and went on confident that the fstab was correctly modified.  

So i rebooted and, after choosing the user and typing the password it said something like  **$HOME /. dmrc is being ignored**  and then that **the session manager could not block /home/edna/ICEauthority**

I rebooted with the live cd and typed the recuperation lines  but on reboot, the same problem.  I tryed to repeat the whole process and on the command  

```
find . -depth -print0 | sudo cpio --null --sparse -pvd /new/
```

it found the backups of all the files that it had found the first time.

Anyhow it all didn't finally work well. 

Here's my fstab as i think it is now (it's difficult to get there with the live cd as it won't always mount the hard drive): 


# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=8b9a366a-b9fd-43bc-be43-bed7b7961d80 /               ext3    relatime,erro$
# /dev/sda5
UUID=ba566428-6069-4ec3-ac23-0649506a7560 none            swap    sw           $
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
/dev/sda3 /home ext3 nodev,nosuid 0 2

The partition sda3 is the new one.  

Many many thanks for any help

ejv

---

### Post by nowshining on 2008-09-21
did u mount the drive and rooted into the folder, etc.. 'cause just running the livecd and editing fstab won't work as it will get removed on reboot since it's all in RAM...

---

### Post by blazemore on 2008-09-21
Try changing the relevant line to

/dev/sda3 /home ext3 defaults 0 0
Worked for me when I had a similar problem

---

### Post by Tatty on 2008-09-21
I think that fstab is fine.  

I think the problem is that your new /home does not have the correct permissions applied to it.  I had this problem after following the (otherwise excellent) psychocats tutorial.

Try ```
ls -Rl ~/
```

Then have a look, if most files are owned by root then that will be the problem.

If so then you will need to chown them back to you.

---

### Post by ejv on 2008-09-21
Hi 

Typing **ls -Rl ~/** gave me:

ubuntu@ubuntu:~$ ls -Rl ~/
/home/ubuntu/:
total 0
drwxr-xr-x 2 ubuntu ubuntu 100 2008-09-21 17:26 Desktop
drwxr-xr-x 2 ubuntu ubuntu  60 2008-09-21 17:27 Documents
drwxr-xr-x 2 ubuntu ubuntu  60 2008-09-21 17:27 Music
drwxr-xr-x 2 ubuntu ubuntu  60 2008-09-21 17:27 Pictures
drwxr-xr-x 2 ubuntu ubuntu  60 2008-09-21 17:27 Public
drwxr-xr-x 2 ubuntu ubuntu  60 2008-09-21 17:27 Templates
drwxr-xr-x 2 ubuntu ubuntu  60 2008-09-21 17:27 Videos

/home/ubuntu/Desktop:
total 8
lrwxrwxrwx 1 ubuntu ubuntu   26 2008-09-21 17:26 Examples -> /usr/share/example-content
-rwxr-xr-x 1 ubuntu ubuntu 6774 2008-09-21 17:26 ubiquity-gtkui.desktop

/home/ubuntu/Documents:
total 0

/home/ubuntu/Music:
total 0

/home/ubuntu/Pictures:
total 0

/home/ubuntu/Public:
total 0

/home/ubuntu/Templates:
total 0

/home/ubuntu/Videos:
total 0


2) Since the last reboot i haven't been able to mount sda1

3) How do i really get to the fstab line in my harddrive?

Just please note that i'm not that sure about what i'm doing.  just an intuitive ignorant, you could say...

ejv

---

### Post by Tatty on 2008-09-21
Ah i think i misunderstood you origionally, i see you are having to boot with a LiveCD.

So you cannot get into a working GUI from your hard drive?

If it helps, the fstab entry for my home is:

```
UUID=b4d26e34-6daa-464f-b8a7-b39b29dead13 /home           ext3    relatime        0       2
```

Perhaps it may be worth changing to using a UUID to make sure that your computer is not mixing up the order of your partition numbering, to find out your UUID's use

```
blkid
```

---

### Post by nowshining on 2008-09-22
i think the OP is editing the livecd fstab and not the one on the actual disk..again u have to mount the internal HD then go into it and edit the fstab from there...i've had problems before like this and this is how u do it from a livecd...

---

### Post by Bucky Ball on 2008-09-22
In a terminal, try:

**sudo mount -a**

and that should mount the all drives it can read from your fstab. You may then be able to get into the appropriate fstab and change it cos yea, think that is the fstab on the live cd you are editing.

But ... if you could mount all drives (including sda3) check where your /home directory is now. Is there one on sda3 already and that is where the confusion is coming in? Or is it still on sda1 or 5?

And as mentioned earlier, run **sudo blkid** and add the UUID of sda3 to the sda3 section in your fstab to make it look like the other entries if you can get to your fstab on the hard drive (not cd).

---

### Post by ejv on 2008-09-22
First of all thanks for all your posts.  

I tried to mount sda1 or sda3 but kept on coming to empty fstab lines or could't mount the device and problems like that.  the step with the UUID wasn't clear for me so i just decided to reinstall clean... but this time i created a new partition for home.  But how can i be sure it's done correctly?  On installing there were 3 partitions:

sda1: mount point /
sda3: mount point /home
sda5: swap  (this one was already there and i left it untouched)

i suppose that it should be alright now but how can i check that the partition i created is really **my** home?

This is my fstab line now

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=b2765c44-ef9d-47d8-b9cc-9a44508cb0c6 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda3
UUID=3602ddae-6f0c-464f-b229-1bd0f1e895b1 /home           ext3    relatime        0       2
# /dev/sda5
UUID=ba566428-6069-4ec3-ac23-0649506a7560 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0


Thanks once more

ejv

---

### Post by nowshining on 2008-09-22
is this fstab /etc/fstab from the livecd??

---

### Post by Bucky Ball on 2008-09-23
> **nowshining said:**
> is this fstab /etc/fstab from the livecd??

Are you booting straight to Ubuntu from the hard drive and this is the /fstab? Cos if that's the case, you got it right.

If you are booting from livecd, as mentioned, then that is probably the Livecd /fstab.

Getting closer. ;)

---

### Post by blazemore on 2008-09-23
Yes, that's really important.
On the LiveCD, the CD is mounted as / (or something)
And your actual filesystems are mounted somewhere else

You need to mount your root filesystem (fdisk -l to see what device it is) and then edit the fstab there.

For example, if you mounted it as /media/harddisk
you would do sudo nano /media/harddisk/etc/fstab

---

### Post by ejv on 2008-09-23
The fstab line is from my pc.  Guess at last i got it right! :D

Thanks for your help!

So, for the next time i mess things up, is there something else that i should do **now**?

ejv

---

### Post by Bucky Ball on 2008-09-23
Take the live cd out and reboot (which you probably already have!), hit 'solved' from thread tools, top right of this page and test out your new system to see if things are working okay, create a new thread if not (good idea to research your probs first - 'your problem ubuntu' is a good googler), be as descriptive as you can in the title and detailed as you can in the post (try to post questions separately rather than ask them in a post  on an already established thread with a misleading title) and ... enjoy! 

Hermanzone is a great resource and here is the page on post installation:

[http://users.bigpond.net.au/hermanzone/p5.htm](http://users.bigpond.net.au/hermanzone/p5.htm)

My tip: go to System->Administration->Synaptics Package Manager then do a search for:

**ubuntu-restricted-extras**

.. and install. That should load things you need for audio and video etc. Then go to Applications and explore, especially Add/Remove.

:)

---

### Post by ejv on 2008-09-24
Ok thanks!

ejv

---

