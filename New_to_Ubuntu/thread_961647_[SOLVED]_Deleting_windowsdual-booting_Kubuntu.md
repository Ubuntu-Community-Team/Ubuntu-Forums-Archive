---
title: "[SOLVED] Deleting windows/dual-booting Kubuntu"
date: 2008-10-28
forum: New to Ubuntu
---

### Post by le singe on 2008-10-28
Hello.  I originally installed Ubuntu after windows, as a dual boot, and I haven't used windows since.  I am going to delete/format my windows partition using GParted under the live CD to give the space windows is now occupying to Ubuntu.  

In GParted, how will I know what my windows partition is labeled as?  Should it show up as the only NTFS partition?

Second, if I want to later install Kubuntu and dual-boot with Ubuntu, will I have to set up a partition before doing so or does the Kubuntu installation handle that for you?

---

### Post by zakirs on 2008-10-28
well ..  yes NTFS is for windoes and ext3 for linux .. u might not need to install kubuntu all over u can install it as a software 

[http://www.psychocats.net/ubuntu/kde](http://www.psychocats.net/ubuntu/kde)

---

### Post by le singe on 2008-10-28
ok - that's what I was thinking, that NTFS was the windows partition.  I keep hesitating, thinking I might mess something up... I ought to just go with it.

Thanks for the suggestion.  I think I would prefer to eventually just dual boot with Kubuntu, as to not complicate things in the Ubuntu partition.

Thank you for the help.

---

### Post by doorman on 2008-10-28
As zakirs said, just look for the ntfs partition and delete it. Then, just resize the current ext3 partition (this might take a while - on my 250 GB disk it took about 5 hours, but that's the case only if the ntfs partition was the first one, i.e. sda1).

About the (k)ubuntu, you don't need to install kubuntu. Kubuntu and Ubuntu are the same linux distro (they're completely identical AFAIK), the difference between the two being the default desktop environment: Ubuntu's one is GNOME, while Kubuntu uses KDE. You can install the kubuntu dektop by installing the kubuntu-desktop package in any way (apt, aptitude, synaptic)

To switch between them, just log out, and on the login screen select another session: select GNOME for "Ubuntu" and KDE for "Kubuntu"

---

### Post by zakirs on 2008-10-28
yep i too would prefer that .. try doing what that link has said .. its verymuch safe dont worry :)

---

### Post by zakirs on 2008-10-28
by link i meant [http://www.psychocats.net/ubuntu/kde](http://www.psychocats.net/ubuntu/kde)

---

### Post by le singe on 2008-10-28
> **doorman said:**
> As zakirs said, just look for the ntfs partition and delete it. Then, just resize the current ext3 partition (this might take a while - on my 250 GB disk it took about 5 hours, but that's the case only if the ntfs partition was the first one, i.e. sda1).

Alright, thanks doorman.

So I'm booted from the live CD right now, and using GParted I just managed to delete my windows partition.  However, when on ext3 I try to resize, it will only let me make this partition smaller, and not larger.  I don't understand what I am doing or what I did wrong.  

Any ideas?

---

### Post by le singe on 2008-10-28
I just realized that with the remaining partitions I have the option to:
Format to
  -ext2
  -ext3
  -fat16
  -fat32 ....
Aiiee I hope I wasn't supposed to format my windows NTFS partition to ext3, I don't know if that is what would have done the trick, giving the newly-freed space to my ubuntu ext3 partition.

What I did was I selected "Delete" on the NTFS partition.  Hmmm....

---

### Post by aktiwers on 2008-10-28
If you deleted the windows partition, there should just be a big block of "empty" space, not partitioned.
Now you have 2 choices..  

1) Create a new partition (EXT3 is a good format for Linux)
2) Resize your current Ubuntu paritition to use the empty space.

Its up to you, but right now it sounds like you just deleted the partition, not using the space..

---

### Post by le singe on 2008-10-28
> **aktiwers said:**
> If you deleted the windows partition, there should just be a big block of "empty" space, not partitioned.
Now you have 2 choices..  

1) Create a new partition (EXT3 is a good format for Linux)
2) Resize your current Ubuntu paritition to use the empty space.

Its up to you, but right now it sounds like you just deleted the partition, not using the space..

hey thanks.

Correct, I just deleted windows and there's now a chunk of empty space.  I am trying to do your second option, resizing my current Ubuntu partition to make use of this newly-freed space, however in the resize menu for my ext3 I can only make the partition smaller and not larger.  Right now I'm trying to scan through other posts where people may have had the same problem... I can't figure out why it won't let me extend my ubuntu partition.  I am running in the live CD.

I have most everything backed up, and I guess one option would be to just reinstall Ubuntu, selecting the option to install onto the entire hard drive.

---

### Post by aktiwers on 2008-10-28
Are you doing this from the liveCD? Because you can't resize partitions you are currently using (which would be the case if you are not on the LiveCD) :)

---

### Post by le singe on 2008-10-28
One last question:
If I cannot manage to increase the size of my Ubuntu ext3 partition, and I decide to just use the free space gained from deleting the windows partition, can I leave this empty chunk of space as it is and Ubuntu will recognize it as a sort of extra drive, or do I first have to create a partition out of it?  If so, how do I know what type of file system to use (ext2, ext3, fat32...?)

---

### Post by le singe on 2008-10-28
> **aktiwers said:**
> Are you doing this from the liveCD? Because you can't resize partitions you are currently using (which would be the case if you are not on the LiveCD) :)

yep I'm running off the liveCD right now

---

### Post by le singe on 2008-10-28
oop, sorry... you already gave a good suggestion that answered my above question.  So creating another partition out of the unallocated space as ext3 won't interfere with the ext3 partition that Ubuntu is currently on?

---

### Post by mac71 on 2008-10-28
Hi I seem to remember having a similar issue. I think when I deleted my windows partition I didn't realise it left an extended partition of the same size. When I clicked on the large grey partition I still had the opportunity to delete, once I done that I was able to extend my ext3 partition.

As a further note, once your done, go here:

[http://ubuntuforums.org/showthread.php?t=224351&highlight=reinstalling+grub](http://ubuntuforums.org/showthread.php?t=224351&highlight=reinstalling+grub)

Because you'll probably find that grub isn't playing right.

---

### Post by aktiwers on 2008-10-28
> **le singe said:**
> oop, sorry... you already gave a good suggestion that answered my above question.  So creating another partition out of the unallocated space as ext3 won't interfere with the ext3 partition that Ubuntu is currently on?

Nope.. it will just be like another partition :) Which you can refomat and use without affecting the partition ubuntu is installed on

---

### Post by le singe on 2008-10-28
Thank y'all for taking the time to help.

As I couldn't increase the size of my ubuntu partition, I ended up formatting the freed space given by deleting windows.  It now shows up as an extra media drive, though I don't have the permission to use it (i.e. moving files to and from).

As 8.10 is literally just a few days away, what I may end up doing is reinstalling the new version and choosing to take up the entire hard disk.  Unless I can figure how to access this drive (I think it's probably something simple)

Thanks again for all the help!

---

### Post by aktiwers on 2008-10-28
You need to change the permission of the drive.. 
First go to the drive and press CTRL+L. This will show you the path to the drive (like /media/drivename/  or something like that)..

Then open terminal and type:
```
sudo chmod -R 777 /media/drivename
```
or 
```
sudo chown -R username:username /media/drivename
```

Where username is your ubuntu username.

That should give you the rights.

---

### Post by le singe on 2008-10-28
ah hah!  it worked!  Thank you much!

These forums are so damned helpful - it really is kind of like a community.

):P

---

### Post by aktiwers on 2008-10-28
It is a Community :)
Your welcome mate, you can mark the thread solved in the top-right corner of the forum, in Thread tools.

BTW.. sorry I couldn't be off more help with the re-size thing.. I only seen the feature, never used it ;)

---

