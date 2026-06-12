---
title: "Setting up a shared HDD between Ubuntu and Vista"
date: 2008-07-02
forum: New to Ubuntu
---

### Post by Village on 2008-07-02
Folks,

**Here's the problem;**

I've recently built myself a new computer (for the first time too, its a learning curve aright!), I am dual booting both Ubuntu and MS Vista, I have both of these Operating Systems (OS's) on my programs Hard Drive (HDD), which along with OS's I plan on just keeping programs. All my saved documents, pictures, music and the rest of my digital life I would like to put on my second HDD. Ubutnu and Vista both have folders for things like Documents, Pictures, Music, etc. 

**The Question;** 

What would be the easiest way to tell Ubuntu that I want these folders (or for that matter my home folder) to be on this separate HDD, I could then make the same folders in Vista. Due to MS, this would have to be on NTFS. 

Is this even possible,
If so how?

Thanks in advance for any advice. 

Village

---

### Post by hyper_ch on 2008-07-02
ubuntu can read/write ntfs (with ntfs-3g)

xp/vista can read ext2/3 with [http://www.fs-driver.org](http://www.fs-driver.org)

use whatever you want

however /home probably needs to be on a linux filesystem partition because of the linux/unis file permissions...

---

### Post by kansasnoob on 2008-07-02
I actually prefer having all operating systems (up to four) on one hard drive and keeping my data on a separate hard drive for one big reason! If I'm ever doing something foolish and previously untested I can physically disconnect my data drive before starting!

So the simple answer is "yes" you can create an NTFS data drive separate from your OS drive. The following guide has helped me a lot:

[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

---

### Post by deathvalleyjoker on 2008-07-02
I recently have done the exact same thing except with xp and ubuntu. 

I am less than two weeks old to ubuntu and here is how i have gotten mine to work:

1) make all non-linux partitions NTFS.

2) use this code to give you wtire permission on your windows drives

sudo aptitude install ntfs-config

then go to applications-system tools-ntfs-config, run it and you wont get any write permission errors.

3) last step that is helpful makes it so that ubuntu automounts the shared drives on start up:
[https://help.ubuntu.com/community/AutomaticallyMountPartitions](https://help.ubuntu.com/community/AutomaticallyMountPartitions)

follow the first set of codes it gives you and it should work fine (it did for me).

So there was my first day or two of researching summed up for you. that should get you what you need.

---

### Post by Village on 2008-07-02
I have been looking around and I've installed Medibuntu, and I think that has NTFS support, I can now see the Data HDD. so I can access it, fantastic. 
Is it possible to change where the docs, music ect. are, other than just clicking and dragging so that ubutnu "knows" where they are?

Thanks.

Village

---

### Post by tjwoosta on 2008-07-02
i reccomend formating the shared partition to fat32


i have tried all three formats ext3, ntfs, and fat32 
with ntfs ubuntu sometimes freezes when playing media
with ext3 windows sometimes freees when playing media 
but with fat32 ive had no problems at all

---

### Post by Village on 2008-07-02
Thanks Deathvallyjoker

That helped, now I just need to figure out a way to tell Ubutnu that I want the Docs, Music and the other folders of my user folder on the HDD. 

Village

---

### Post by hyper_ch on 2008-07-03
you have registry keys here:  "HKEY_CURRENT_USER\Software\Microsoft\Windows\CurrentVersion\Explorer\User Shell Folders"  that contain the path to where different things are stored (like desktop)... I think you will find all the user folders there also... so just change it and reboot.

---

### Post by hofa on 2008-07-03
And for your Ubuntu installation you can replace the folders in your 'Home folder' with symbolic links.

for the folder Music you can do:
```
ln -s /media/dataPartition /home/village/Music

*syntax: ln -s [target] [location of new link]*
```

---

