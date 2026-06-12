---
title: "Secondary HDD mounting as Read Only"
date: 2012-04-09
forum: New to Ubuntu
---

### Post by stdare on 2012-04-09
Greetings all,
My Ubuntu10.10 system has 3 hard drives, one of which won't mount on boot. In MountManager it has all options greyed out.

On looking at fstab I see that it is set as Read Only. (sdb1)
In Gparted it is showing as unknown file system.
See attachments for both.

Suggestions as to how sort this out? Am prepared to reformat the drive if this will solve the problem.

Many thanks!

---

### Post by oldfred on 2012-04-09
You should mount by UUID not device so their is no confusion if sdb1 or sdc1. 

That may be the issue or if NTFS it may need chkdsk from a Windows install or repairCD.

To see UUIDs

sudo blkid


My entries for my c: drive and a shared NTFS partition that is read/write:

```
# Entry for /dev/sda1 :
UUID=04B05B70B05B6768 /mnt/cdrive ntfs-3g ro 0 0
# Entry for /dev/sdc2 :
UUID=44332FD360AA9657 /mnt/shared ntfs-3g defaults,uid=1000,nls=utf8,windows_names 0 0

```

---

### Post by stdare on 2012-04-09
Hello Oldfred. We meet again. 
"I am ever fated to be your burden my friend" (Tolkien)

The confusion between drive labels may have caused my system crash a few weeks back?!?

So how do I mount by UUID?
Is there a GUI method or will I be doing this with code?

Thanks

---

### Post by oldfred on 2012-04-09
There were some gui methods that sometimes worked. It just is not that difficult to manually do and it is best to know your settings anyway.

You can copy one of the entries previously posted and change to your UUID. Use whatever name you like example was cdrive, but it can be anything. And if you mount it in media you will see it in the left panel of Nautilus. I mount in /mnt just so it does not show in Nautilus, just as I do not want to make it too easy to get to Windows system and I use a separate NTFS shared data partition for read/write.

# Make permanent mount point (unmount if already mounted):
sudo mkdir /media/cdrive
# Find your UUID:
sudo blkid
sudo cp /etc/fstab /etc/fstab.backup
gksudo gedit /etc/fstab
# Anytime you edit fstab always do this before rebooting. If no errors it just remounts everything, but if errors you have to fix before rebooting or you may not be able to:
sudo mount -a

---

### Post by stdare on 2012-06-01
Apologies for my delay in following this up.  Life had me sidetracked....

OldFred, I followed the first couple of lines of your suggested process, but I confess that when I got to the editing of the fstab file I ran out of skills. :(

I* think* I am supposed to be copying other lines of the file, inserting the UUID of device that is being difficult?
If you could please re-explain I'd be grateful.  I'm not sure which are the good lines, and which I am supposed to be replacing....

Many thanks for your ongoing assistance.

---

