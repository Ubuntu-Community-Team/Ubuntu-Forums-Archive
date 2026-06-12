---
title: "I can't find all of my files"
date: 2008-10-20
forum: New to Ubuntu
---

### Post by crimlaw on 2008-10-20
As I am getting used to Ubuntu 8.04 (a recent switch from Vista), I am noticing little file problems. 

First, I downloaded Opera because FF kept crashing.  Opera claims to be putting temporary files in home/"username"/.opera/cache4/temp.  Or something very similar.  However, when I go into my home file, then go to my "username" file, it can't find .opera.  I am sure there are other files that do not exist, so how do I find/view them?

Also, when I am in Ubuntu 8.04, I find that I need certain files I would use in Vista.  Can I access these through Ubuntu?  Or, do I have to put every file I want to view onto an external HD?  

Thanks!!!

---

### Post by melojo on 2008-10-20
the . is telling you it is a hidden file.

When you click on places and open home folder- goto view and click show hidden files.

---

### Post by risu_vk on 2008-10-20
view->show hidden files(ctrl-H) in your home directory

---

### Post by Dr Small on 2008-10-20
If you are in Nautilus (the file manager), open your Home Folder. From there, press CTRL + H to see hidden files and folders. Then find .opera and you should be able to browse into from there.

If in the terminal, run:
```
cd ~/.opera
```

---

### Post by jerome1232 on 2008-10-20
Yes you can access your files stored on Vista (is it on the same computer or a seperate computer?)

Also the keyboard shortcut to view hidden files is ctrl+h

---

### Post by unutbu on 2008-10-20
Are you using Nautilus as your fileviewer? (If you are using GNOME, the default fileviewer is Nautilus.)

If so, press Ctrl-h to view "hidden" files. A hidden file is any file or directory that starts with a dot, such as ".opera".

As for your second question, it is possible to read files on your Windows partition from within Ubuntu.
Please open a terminal ([http://www.psychocats.net/ubuntu/terminal](http://www.psychocats.net/ubuntu/terminal)) and type
```

sudo fdisk -l
```
Post the output. Using that output we can help you setup your machine so you can access your Windows partition.

---

### Post by crimlaw on 2008-10-20
wow, quick responses . . . thanks!!!

any thought on seeing my windows files????

[EDIT] more posts came in before I could post my reply.  Thanks again!!!

---

### Post by aeiah on 2008-10-20
you can also view hidden files and folders in the file manager by pressing ctrl+h

as for accessing stuff in your vista partition: look into how to mount a partition under ubuntu both temporarily and permanently (via editing fstab). if you find you cant edit the files in your vista partition and you wish to do so, you probably havent set up the correct write permissions. this can be done quite easily and should be included in any guide you find on here regarding the subject on mounting your ntfs windows vista partition.

---

### Post by jerome1232 on 2008-10-20
look at posts 6 & 5

---

### Post by crimlaw on 2008-10-20
my files are on the same computer.  I will be unable to post any results right now as I am at work, but I will be sure to do it tonight when I get home.

If it matters, I did not do a traditional partition, I "installed within widows" or whatever the option was.

---

### Post by jerome1232 on 2008-10-20
Essentially you will be doing this, after doing the fdisk command you should see a bunch of /dev/sdXX lines, one of them will say ntfs that's your vista partition, you will want to get it's uuid then add a line to fstab

```
sudo fdisk -l            # find the one that says ntfs
sudo blkid               # Find the one that has the same /dev path as the ntfs device you found in step 1
gksu gedit /etc/fstab
```

This an example of what an entry to fstab for a ntfs disk that's is readable/writable by anyone on the system would look like
```

# /dev/sdxx
UUID=A-Lot-of-gobly-gook /media/vista ntfs defaults,umask=000 0 2
```

---

### Post by crimlaw on 2008-10-21
OK, I tried what you recommended to view my vista files, but it did not seem to work.  Here is the uuid like I copied into the fstab

/dev/sda2: UUID="2C88743C8874071C" LABEL="PRESARIO_RP" TYPE="ntfs" 

But I could have chosen:
/dev/sda1   *           1       17931   144030726    7  HPFS/NTFS

But, nothing seemed to happen.  When I did the fdisk command, these were the two options:

/dev/sda1   *           1       17931   144030726    7  HPFS/NTFS
/dev/sda2           17932       19457    12257595    7  HPFS/NTFS

From what I provided, can you tell what I did wrong?

---

### Post by unutbu on 2008-10-21
Try this:
```
sudo mkdir /win    # change /win to whatever mount point you desire
gksu gedit /etc/fstab
```
Put this line at the end of the file:

```
UUID=2C88743C8874071C /win ntfs defaults,user,uid=1000,gid=1000,dmask=027,fmask=137   0    2
```

This should mount /dev/sda2 at mount point /win at boot time. You should also be able to manually mount it with the command
```

mount /win
```

If you wish to mount /dev/sda1, you should run

```
blkid 
```

and find the UUID for /dev/sda1, and then follow the same procedure as above, just change  the UUID and mount point.

If you have any trouble, please post your /etc/fstab file, and the full output of blkid.

---

### Post by crimlaw on 2008-10-21
ok, that worked to mount the drive on my desktop.  Now I realize that the drive was already accessible though "places."  However, I still can't see all of my files.  did I mount my main "c" drive?  How do I delete the desktop icon?  I am trying to keep icons off my desktop.

Thanks again for all of the suggestions.

---

### Post by jerome1232 on 2008-10-21
If you don't want an icon on your desktop then mount it to /mnt/mountpoint instead of /media/mountpoint.

---

