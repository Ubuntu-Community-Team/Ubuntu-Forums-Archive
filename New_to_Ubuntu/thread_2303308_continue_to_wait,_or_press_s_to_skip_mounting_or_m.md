---
title: "continue to wait, or press s to skip mounting or m for manual recovery"
date: 2015-11-17
forum: New to Ubuntu
---

### Post by l-farrell888 on 2015-11-17
Hello this is my first time using ubuntu forums. I have had a look around and nothing seems to answer my question. Whenever I reboot or start up I get this message 
the disk drive for /mnt/fa1b420f-b108-488f-8cd9-dfba2ed41180 is not ready yet or not present
continue to wait, or press s to skip mounting or m for manual recovery

I press s and another similar message comes up /mnt/40417644-f346-4d93-8d57-1c305eec267d 

i press s again and it boots normally. How do I get rid of these messages? 

I am using a lenovo thinkpadt410 and only running ubuntu, no dual boot. i have added a ssd that i partitioned its dev/sdb1 mount point /media/myusername..... I don't think that is causing the problem though

I think I have to do something with fstab? Am I getting warm? can someone tell me what to type in a terminal to sort this out, or what info you need to see how help me. Thank you

---

### Post by Bucky Ball on 2015-11-17
Welcome. Please give the output of these two commands, between code tags (see the last link in my signature):

```
sudo blkid
nano /etc/fstab
```

The first is a command that will output some info for us. The second will open a file. Copy/paste both to here so we can have a look and rectify the fstab. You're problem should be fairly easily fixable and I'm presuming it has been caused by the SSD not being added to the fstab (so it's not being mounted at boot).

---

### Post by yancek on 2015-11-17
Generally speaking, that type error appears if you have an entry for a partition in fstab (in your case showing UUIDs under /mnt) and the partition is on a disk that is not attached on boot.  Check the fstab file to see if you have an entry with those UUIDs.

---

### Post by l-farrell888 on 2015-11-18
Thank you for helping 

/dev/sda1: UUID="b9b51104-74ff-4e24-9930-6db91ec31412" TYPE="ext4" 
/dev/sda5: UUID="2525bb67-c0dd-4c55-bff5-6197d6a144a0" TYPE="swap" 
/dev/sdb1: UUID="63e5553f-7696-4814-acda-f53aaa12e08d" TYPE="ext4"

and 

# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda1 during installation
UUID=b9b51104-74ff-4e24-9930-6db91ec31412 /               ext4    errors=remoun$
# swap was on /dev/sda5 during installation
UUID=2525bb67-c0dd-4c55-bff5-6197d6a144a0 none            swap    sw           $
/dev/disk/by-uuid/fa1b420f-b108-488f-8cd9-dfba2ed41180 /mnt/fa1b420f-b108-488f-$
/dev/disk/by-uuid/40417644-f346-4d93-8d57-1c305eec267d /mnt/40417644-f346-4d93-$

---

### Post by Bucky Ball on 2015-11-18
Do this:

```
sudo nano /etc/fstab
```

... and make the fstab file look like this, add a hash (#) to the beginning of those last two lines for now (I've made them bold, but you don't :)):

```
# <file system> <mount point> <type> <options> <dump> <pass>
# / was on /dev/sda1 during installation
UUID=b9b51104-74ff-4e24-9930-6db91ec31412 / ext4 errors=remoun$
# swap was on /dev/sda5 during installation
UUID=2525bb67-c0dd-4c55-bff5-6197d6a144a0 none swap sw $
[B]# /dev/disk/by-uuid/fa1b420f-b108-488f-8cd9-dfba2ed41180 /mnt/fa1b420f-b108-488f-$
# /dev/disk/by-uuid/40417644-f346-4d93-8d57-1c305eec267d /mnt/40417644-f346-4d93-$[/B]
```

Control+x then y to save and close (check instructions at the bottom of the terminal window), then reboot. Better?

Not sure what sdb is in the output of 'sudo blkid'. Have you got a USB dongle or external drive plugged in?

---

### Post by l-farrell888 on 2015-11-18
Thank you Bucky Ball. That worked like a charm. It now boots up with no prompts.
 I just have my internal hard drive and the ssd, when I click on that hard drive icon in the launcher I can see it is "63e5553f-7696-4814-acda-f53aaa12e08d"  The same as last line in the blkid. Does that mean it's mounted and working just fine? Thanks again!

---

### Post by Bucky Ball on 2015-11-18
Well, it might mount and work fine if you simply click on it, but blkid shows it is recognised, not mounted necessarily. ;)

If you're having issues with it not mounting when you click on it you might want to try mounting it at boot by adding it to fstab. Create a mount point, for example:

```
sudo mkdir /mnt/Data
```

Rather than 'Data' you could call the directory whatever you want. Open fstab with:

```
sudo nano /etc/fstab
```

If you want, delete the two lines you hashed out previously and add exactly this:

```
# Entry for sdb1
UUID=63e5553f-7696-4814-acda-f53aaa12e08d   /mnt/Data    ext4    errors=remount-ro       0       1
```

Change 'Data' if you chose a different directory name. Reboot.

---

