---
title: "fresh install, old home on other partition, how to tell ubuntu to use it?"
date: 2008-10-04
forum: New to Ubuntu
---

### Post by iansane on 2008-10-04
Hi,

I had home on another partition, did a clean install and it's still there but I have a new home directory. How do I tell ubuntu to mount it instead of using the new one?

---

### Post by Dedoimedo on 2008-10-04
Hello,

If you do not wish to retain anything from the new partition, then it's a simple matter of unmounting the new one and mounting the old one.

You can make the change permanent by adding an entry to the /etc/fstab file.

Please note that programs have their custom configuration files stored in your home directory. Thus, by using another home partition, you might lose some configurations - or revert to older versions, contained in your old home, which is probably what you want.

I recommend you backup everything before making any drastic changes.

Are there any other users involved? You might not wanna mess their home directories...

So basically:

```

cp -R /home/* /somewhere/backup/
sudo unmount /home
sudo mount /dev/<oldhomepartition> /home

```

To make it permanent:

```

sudo cp /etc/fstab /etc/fstab-backup
sudo gedit fstab

```

Change the home partition entry to what you want. For instance, instead of:

```

/dev/hda6 /home ext3 defaults 0 0

```

Change to:

```

/dev/sdb2 /home ext3 defaults 0 0

```


That's about it.

Cheers,
Dedoimedo

---

### Post by iansane on 2008-10-04
Thanks,

I did all of that and only had a couple of minor issues. Still had to go through and get rid of the configurations and directories for programs not installed on a fresh install but I think some of them would work just by installing the missing program.

Actually, I was following steps from a tutorial for moving home directory and before I realized my mistake, I had updated my old home directory with the new one and had 2 default folders for firefox. Couldn't get firefox to open till I found and deleted the new one and then set the path in profiles.ini to the old one.

One question I have is when I originally installed, I set the mount point during manual partition set up for /home. I never set a fstab entry for it.
The system made it's own entry. One with UUID instead of the usual "/dev/sdaX /home" type entry I made this time. 

Shouldn't the new install have picked up on that mount point and made the entry during install like it did the first time?

And if I just restore the backup of the old fstab will the UUID still be the same since I didn't touch the other partitions?

Thats one step that would make a clean install run smoother and faster since I have other partitions and mount points in there too.

---

### Post by Dedoimedo on 2008-10-07
Hi,
Sorry for the delay in getting the second response.
Yes, you can use the old fstab if you make no changes to the partitions. If you ever get lost, try sudo fdisk -l to get the current situation of partitions and filesystems.
Dedoimedo

---

