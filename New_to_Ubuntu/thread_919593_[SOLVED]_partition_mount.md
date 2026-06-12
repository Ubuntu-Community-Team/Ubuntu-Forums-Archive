---
title: "[SOLVED] partition mount"
date: 2008-09-14
forum: New to Ubuntu
---

### Post by 44tr on 2008-09-14
I have three hard drives on my computer, a SATA that I boot from with three major partitions and two IDE drives with multiple partitions.  I can't find a GUI tool that will let me mount an empty partition at a specific mount point.  One SATA partition is an Ubuntu install with another partition mounted as /home (done during install); how do I mount the third empty partition as part of the file system, say as /share_1?  Nautilus just lists it as '100.0 GB' and I can mount or unmount.  Also, for best practice, are there any suggestions for the mount point?  I plan to use it to store virtual machine files, iso's, and perhaps some other stuff.  The partition is listed in gparted as /dev/sda3.

Thanks in advance.

---

### Post by aloshbennett on 2008-09-14
Usually they go into /media drive.

You could make a directory under /media called datadrive or something and from command prompt,
> sudo mount /dev/sda3 /media/datadrive

Once you are comfortable doing it, you could add an entry to /etc/fstab (use the defaults you see being used for the other entries. Just remember to specify the file system) and it would be mounted automatically.

---

### Post by drs305 on 2008-09-14
I wrote a tutorial about a gui-based fstab editor name pysdm. It's not the easiest thing to work with but feel free to take a look at it.

[SDM - A GUI Fstab Editor]("http://ubuntuforums.org/showthread.php?t=872197")

---

### Post by Bucky Ball on 2008-09-14
In a terminal, copy and paste this command and post it back here:

**sudo blkid**

This will provide you with the details you need to automount your partitions at boot and help you figure which ones. :)

---

### Post by 44tr on 2008-09-14
> **Bucky Ball said:**
> In a terminal, copy and paste this command and post it back here:

**sudo blkid**

This will provide you with the details you need to automount your partitions at boot and help you figure which ones. :)

Here is the result for my main drive.  The other dozen partitions from my other drives I presume are not an issue.  

```
/dev/sda1: TYPE="swap" UUID="6d4d6251-5aa8-45e1-89cb-85fa2d3cc465" 
/dev/sda2: UUID="42516125-ad3b-4097-887f-ec9e6eacb5ff" TYPE="ext3" 
/dev/sda3: UUID="e73d76de-14e7-41af-a8fa-f7768f181c39" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda5: UUID="dc65ae93-dc7d-4b98-8b48-9f74630f7ac6" TYPE="ext3" 

```

/dev/sda3 is the partition I want to mount automatically upon boot.

While I'm at it, I have an external USB drive that has three partitions on it that I use for backups and storing less used files.  Is there a way to have these mounted in a sensible place in the tree when it is there but not cause headaches when it isn't?

---

### Post by drs305 on 2008-09-14
Backup and open fstab (substitute another text editor if you don't use gedit). Change "share_1" to whatever you wish:
```

sudo mkdir /media/share_1
sudo chown -R *yourusername*: /media/share_1
sudo cp /etc/fstab /etc/fstab.backup
gksu gedit /etc/fstab

```

Add this line:
```

UUID=e73d76de-14e7-41af-a8fa-f7768f181c39 /media/share_1 ext3 defaults 0 2

```

---

### Post by 44tr on 2008-09-14
> **drs305 said:**
> Backup and open fstab (substitute another text editor if you don't use gedit). Change "share_1" to whatever you wish:
```

sudo mkdir /media/share_1
sudo chown -R *yourusername*: /media/share_1
sudo cp /etc/fstab /etc/fstab.backup
gksu gedit /etc/fstab

```

Add this line:
```

UUID=e73d76de-14e7-41af-a8fa-f7768f181c39 /media/share_1 ext3 defaults 0 2

```

OK, the good news is that now that partition mounts to /media/share_1

The bad news is that the same partition still shows up as '100 GB Media' on my desktop and in nautilus; I would prefer this not happen since it adds to the clutter and the name is not the least descriptive.  ideas?

---

### Post by drs305 on 2008-09-14
> **44tr said:**
> OK, the good news is that now that partition mounts to /media/share_1

The bad news is that the same partition still shows up as '100 GB Media' on my desktop and in nautilus; I would prefer this not happen since it adds to the clutter and the name is not the least descriptive.  ideas?

I believe if you label the partition it will display by the label name.  The second command will show label names. To label an ext3 partition:
```

sudo tune2fs -L LABELNAME /dev/sda3
sudo blkid

```

Then you can change the fstab entry from UUID= to LABEL=LABELNAME

---

### Post by 44tr on 2008-09-14
> **drs305 said:**
> I believe if you label the partition it will display by the label name.  The second command will show label names. To label an ext3 partition:
```

sudo tune2fs -L LABELNAME /dev/sda3
sudo blkid

```

Then you can change the fstab entry from UUID= to LABEL=LABELNAME

Well that should be useful in labeling my external drives ext3 partitions!  I couldn't figure out how to do that since gparted didn't seem to want to do that, only for FAT or NTFS partitions.

Will this keep the partition off my desktop and off of the Places list as LABELNAME?  My /home partition shows up only as that; I hope to accomplish the same here though relabeling it to something decent may be an acceptable alternative.

---

### Post by drs305 on 2008-09-14
> **44tr said:**
> 
Will this keep the partition off my desktop and off of the Places list as LABELNAME?  My /home partition shows up only as that; I hope to accomplish the same here though relabeling it to something decent may be an acceptable alternative.

Labeling won't prevent the device from showing up in nautilus Places - it should change the designation from 30GB to MYMUSIC.

You can prevent all volumes from showing up on the Desktop by editing the metacity settings. You can run gconf-editor and drill down to the spot designated in the following command, or just run the command itself. You can reverse it and display the volumes on the desktop again by changing the value to true. I've made shortcuts on my panel to display and hide them for one-click access. This is the command to hide them:
```

gconftool-2 --type bool --set /apps/nautilus/desktop/volumes_visible 'false'

```

I think there was a time when only the volumes mounted in /media would show on the desktop (/mnt would not) but I've been told that it doesn't appear to be the case any longer.

---

### Post by 44tr on 2008-09-14
OK, I switched the partition to /mnt and it DID disappear from nautilus and the desktop and does appear in /mnt/share_1.  Great.  Just one peculiar thing:  It is a 100GB partition with nothing on it, but it only has 87GB free.  Why?

---

### Post by drs305 on 2008-09-14
Glad to hear the /mnt trick still works.

Partitions are not always exactly what they say they are. If you told gparted to make a 100GB partition it is usually less than that after formatting.

Additionally by default 5% of the disk space is reserved for system use in Ubuntu. That wouldn't account for all of it however. You can change the percentage of reserved disk space with the tune2fs command with a -m switch if you desire. You can learn how by reading the 'man' page.

---

