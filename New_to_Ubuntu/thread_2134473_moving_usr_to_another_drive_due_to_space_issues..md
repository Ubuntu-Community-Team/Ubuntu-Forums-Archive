---
title: "moving /usr to another drive due to space issues."
date: 2013-04-11
forum: New to Ubuntu
---

### Post by palaau on 2013-04-11
Since I know just enough about linux to be dangerous...

Has anybody ever had any luck in moving a "system" folder to another drive? I have two 8 gig hds, and the first one is almost full (down to 67 mB). 90% of my space is taken up with the /usr folder. The second drive is empty so I copied the /usr folder to the second hd and modified the fstab to mount the new folder as /usr. Needless to say it has been an almost total failure (I didn't have to reload)... Using the new fstab, nothing works. I have been able to restore to the original fstab and the system works fine. 

Any ideas?

---

### Post by pfeiffep on 2013-04-11
[try here]("https://help.ubuntu.com/community/Partitioning/Home/Moving") I was able to repartition and move /home by following those guidlines

---

### Post by Impavidus on 2013-04-11
Yes, you can move your /usr to another partition. It has even been designed so that you can move it to a different partition. That link pfeiffep provided is useful. Moving your /usr works in about the same way as moving /home.

Boot from a live disk, format the partition to which you want to move /usr to ext4, copy the entire directory to that partition and erase it from the old, edit /etc/fstab and reboot to a normal session.

You could also consider not moving your entire /usr, but only /usr/share. I don't know your system, but it may make a nicer split.

---

### Post by palaau on 2013-04-11
I have made progress, but now gnome wont load.  Just get a black screen, but I can SSH into the unit and restore the fstab to original.  Any ideas?

---

### Post by Impavidus on 2013-04-11
Can you show us the line you tried adding to /etc/fstab?

---

### Post by palaau on 2013-04-11
sorry about that...

# /usr was on /dev/sda5 during installation
# UUID=***************************** /usr    ext3  defaults  0  2

#/user was moved to /dev/sdb1
UUID=***************************** /usr   ext3 defaults 0 2

I have included the original line and the new line from my /etc/fstab ...

---

### Post by gordintoronto on 2013-04-11
Have you run: sudo apt-get clean
to clear up some space? The files it deletes are truly obsolete, unless you have had installation issues.

---

### Post by palaau on 2013-04-12
its basically a new install, so if I bomb it I can reinstall but I as I am trying to learn...

I found this bit of command line magic... tar cpf - . | (cd /new_home; tar xf -) on another website. I can post the link if anybody is interested. 

Running the command as root from the original usr folder, i was able to then modify the fstab and my usr folder is now on the new drive.

Guessing I was screwing up copying some of the hidden files and folders the first few times I tried to relocate...

---

### Post by Impavidus on 2013-04-13
That command is a neat way of moving an entire directory, preserving file ownerships and permissions. The first tar packs the entire directory into an archive, preserving permissions (which is actually the default when run as root), it then changes directory and unpacks the archive. It does, however, not delete the old directory. It's like an improved copy command.

---

### Post by Bashing-om on 2013-04-13
palaau;
Just a thought, but how does the system know that /usr is now on a separate device ? Is it picked up from the new UUID, or must the path also be explicitly defined in fstab ?[INDENT]
things I don't know can hurt

[/INDENT]

---

### Post by palaau on 2013-04-15
I guess that I could have used /dev/sdb1 /usr ext3 ... to define the new mount point in fstab.  Everything I read on moving files recommends using the UUID (for stability?).  I just copied the existing line, and modified the UUID to match my other HDD.

---

### Post by Bashing-om on 2013-04-15
palaau;

The UUID is the preferred way, I have never seen a situation such that the path also has to be explicitly defined, the "/usr" is the mount point and on re-thinking, I do not see how adding the path to a mount point can be directive in this case. My prior post was meant to think of what would cause the partition not to mount.
Verify once more the UUIDs in question:
```
ls -l /dev/disk/by-uuid/
sudo blkid -c /dev/null -o list
```
comparing all three UUIDs (fstab) to be the same.
If the UUID's are correct, and the "fstab" file is properly formatted; I know of no other reason why the partition will not mount. When I re-boor tonight, I will check my other install for it's fstab in which I have segregated the partitions. We can compare my fstab file to yours to verify.[INDENT=2]
just try'n to help

[/INDENT]

---

### Post by palaau on 2013-04-17
I am always ready to learn... even if I am a little thick.
As I said all I did was copy the original line in the /etc/fstab, change the UUID and then REM out the old line.

This is how my fstab looks currently...

# / was on /dev/sda1 during installation
UUID=***** / ext3 errors=remount-ro 0 1
# /home was on /dev/sda9 during installation
UUID=***** /home ext3 defaults 0 2
# /tmp was on /dev/sda8 during installation
UUID=***** /tmp ext3 defaults 0 2
# /usr was on /dev/sda5 during installation
# UUID=***** /usr ext3 defaults 0 2
# /usr was moved to /dev/sdb1
UUID= ***** /usr ext3 defaults 0 2
# /var was on /dev/sda6 during installation
UUID=***** /var ext3 defualts 0 2
# swap was on /dev/sda7 during installation
UUID=***** none swap sw 0 0

/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto 0 0

---

### Post by steeldriver on 2013-04-17
So what is the status exactly? does the machine boot (with forcing you to skip mounting...)?

If so I would say the problem is not your new fstab - something else got screwed up (maybe related to /usr/bin/X11 or the desktop files in /usr/share/...)

---

### Post by palaau on 2013-04-17
I was able to get it working by using the tar command (see previous post).  The other way(s) I tried were missing some of the hidden files.

---

### Post by Bashing-om on 2013-04-17
palaau; Hey ;

I am playing catch up here after your recopying /usr ->
Are you able to boot now and have access to the /usr partition ?

Else; change directory to "/" (short for root) and list the directories under that root directory:
```
cd /
ls -la
```
Is the system aware of /usr at this time ?[INDENT]
try'n to help
[/INDENT]

---

