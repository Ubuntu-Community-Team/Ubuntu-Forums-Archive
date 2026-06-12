---
title: "Shared Folders not shared after restart"
date: 2008-09-01
forum: New to Ubuntu
---

### Post by thetaskmaster on 2008-09-01
Hi all, new to LINUX. I'm sure there's a simple solution to this -
I've created a few shared folders for users on the network, but when the PC is restarted, the folders reset to unshared. How do I make the share permanent?

Thanks in advance

---

### Post by thetaskmaster on 2008-09-01
Okay, I think I know what part of the problem is:

The folders I am sharing are on a second hard drive and this drive doesn't mount on boot-up or maybe dis-mounts on shutdown. So I guess, if I can prevent the dis-mounting of the drive on shutdown the folders will remain shared?

---

### Post by cwsnyder on 2008-09-01
Here is a reply from one n00b to another.  What I know is that _all_ drives are unmounted as part of the shutdown process.  What I don't know is how to mount a drive automagically as part of startup.

What I can surmise is that the second drive would have to be part of the file system being used in the startup, as for instance, having your /home directory on that drive.  But the task of setting up a separate /home directory is complex, and I do not know it well.

cwsnyder

---

### Post by thetaskmaster on 2008-09-04
*bump*

---

### Post by Nepherte on 2008-09-04
It is indeed correct that all drives are unmounted on shutdown. You will have to automount the drives on startup. This can be done by adding a line in /etc/fstab. To open fstab:
```
sudo gedit /etc/fstab
```
The line depends on what filesystem the disk uses. You will already have examples in fstab for your disk  where ubuntu is intalled on. That disk uses ext3. A typical ntfs filesystem disk entry may look something like this:
```
UUID=EE7017327017014F     /media/mountpoint    ntfs-3g     defaults,locale=en_US.utf8   0    0
```
where /media/mountpoint is the place where it will be mounted, which you can choose. You will have to create the mount point first:
```
sudo mkdir -p /media/yourmountname
```
Another thing you will have to determine is the UUID of the disk. You can find UUIDs of all your disks by typing in a terminal:
```
sudo blkid
```
You will have to determine what disk UUID you need and put that id in the fstab line.

---

### Post by PierreDeKat on 2008-09-04
Nepherte's right on the money with editing fstab.

I set Ubuntu up to automount my Windows partition a few weeks ago.

One thing that helped me was going ahead and mounting the partition manually, which causes its graphical representation to pop up on your desktop.

Once it's on your desktop, you can right-click on it, click "Properties", then the "Volume" tab. There you should find the UUID and a potentially usable mount point like "/media/disk".

I say it's *potentially* usable because it needs to be in a format that Linux likes, i.e. no spaces. I was able to use my "/media/disk" mount point real easy, whereas my "/media/NEW VOLUME" mount point didn't work in fstab.

That's where you will have to use the mkdir command.

Also, safe Linuxing dictates that you: A) make a backup copy of any system files you edit before you edit them; and B) know, ahead of time, how to restore those backups _from command line_, should you run into any serious problems.

For me, I copied fstab to my Documents folder with:

```
sudo cp /etc/fstab /home/~/Documents/
```

Then I knew if I ran into troubles, I could restore the backup with:

```
sudo cp /home/~/Documents/fstab /etc/fstab
```

Something like that, anyway.

---

### Post by thetaskmaster on 2008-09-04
Thanks for your help guys, disk auto-mounts now...BUT..
The shared folders are still not shared after re-start so I'm only half-way there. How do you make shared folders stay shared after restart?

---

### Post by PierreDeKat on 2008-09-04
Just out of curiosity, what application is telling you it can't access the shared folder?

---

### Post by SmeTskE on 2008-09-04
I'm trying to do the same thing. I've managed to mount the NTFS drive on startup by adding the following line to /etc/fstab
```
/dev/sdc1	/media/120GB	ntfs	nls=utf8,umask=0222	0	0
```
I've found this in one of the guides, online.
My problem is: when I right click on the folder /media/120GB and go to the sharing dialog, it prompts me with the following error message when I press 'Create Share'
```
Nautilus needs to add some permissions to your folder "120GB" in order to share it
The folder "120GB" needs the following extra permissions for sharing to work: 
- write permission by others
Do you want Nautilus to add these permissions to the folder automatically?
```
When I press "Add he permissions automatically" it prompts me with:
```
Could not change the permissions of folder "120GB"
```

Any Thoughts?

EDIT: Problem of 'unshareable' solved by changing the "nls=utf8,umask=0222" to "defaults,locale=en_US.utf8"

And after rebooting, the folders stayed shared. 
My guess is: Samba
```
sudo apt-get install samba
sudo smbpasswd <user>
```

I'm very new to Linux myself, so feel free to correct me if I'm wrong!

---

### Post by PierreDeKat on 2008-09-04
Okay, this is the line I added to my fstab, awhile back, and I can do anything I want with my Windows partition.

```
UUID=AE88C07288C03A9B /media/disk ntfs-3g auto,users,uid=1000,gid=100,utf8,dmask=027,fmask=1 37 0 0
```

I [pulled that up]("http://ubuntuforums.org/showthread.php?t=283131") searching the forums, and it works for me. You will need to substitute your own UUID and mount point, if yours is different than /media/disk.

And I don't believe you absolutely need Samba. If I understand it correctly, FUSE, a module in the latest Linux kernels, will allow you to do anything you need to do with an NTFS partition.

My guess is, y'all just need to get the uid=1000, gid=100, dmask=27 etc. stuff set up like mine.

Hope this helps.

---

### Post by thetaskmaster on 2008-09-05
In case it makes a difference to your suggestions, the second drive (which now auto-mounts) is formatted to ext2 and is an internal HD set as slave.

I created folders on this drive and set as sharing for windows users on the same network. There is no network problem and all PCs can see each other. When I set sharing, I get the sharing/hand icon on the folders. I have mapped theses folders as network drives on the windows PCs. After rebooting the UBUNTU system (as don't want or need to leave it running 24/7) the folders lose their hand/share icon and the network PCs cannot connect.

---

### Post by PierreDeKat on 2008-09-05
> **thetaskmaster said:**
> In case it makes a difference to your suggestions, the second drive (which now auto-mounts) is formatted to ext2 and is an internal HD set as slave.

I created folders on this drive and set as sharing for windows users on the same network. There is no network problem and all PCs can see each other. When I set sharing, I get the sharing/hand icon on the folders. I have mapped theses folders as network drives on the windows PCs. After rebooting the UBUNTU system (as don't want or need to leave it running 24/7) the folders lose their hand/share icon and the network PCs cannot connect.
Okay, thetaskmaster, yes, having the drive set up as ext2 will definitely effect how you mount it.

FWIW, you can open up a terminal window and input:

```
you:~$ man mount
```

This will pull up a voluminous manual all about the mount command. Scroll down to line 490, and you will find out all about the various mount options for an ext2 partition.

But apparently with ext2 partitions, you would do [as follows:]("http://ubuntuforums.org/showthread.php?t=283131")

> Note: ext2 and ext3 do not take uid=xxx, gid=xxx, or umask=xxx

To set group rw permissions:
fstab options: users,noauto

   1. mount the partition: mount /mnt/ext3
   2. Set permisions of the mount point: chmod 777 /mnt/ext3


The set ownership and permissions will remain in effect with un-mount and re-boot.

So maybe give that a go.

---

### Post by marcopauloferreira on 2008-10-11
I was having the same problem and got it working by activating the option that allows others to write.

Seems like as a 'Read Only' Shared Folder, the settings get reset after rebooting.

It worked for me and hope it works for me... at least it's a simpler solution... unless you REALLY don't want that folder to be writable by others!

Regards!

---

### Post by Pollik on 2008-12-04
I am also new to Ubuntu and am a little shaky on things like UUID and mounting...I am not that much of a techie, but I am willing try to learn.

I am having the same problem - folders are not staying shared (it doesn't matter if the folder is on the desktop or under polly/music.

And I admit that I am struggling to follow the discussion here.

fstab gives me:

> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda6
UUID=a0eadf87-fc98-4c27-ae80-f7d24746c0e9 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda7
UUID=1dccdf06-a5bb-473c-aa7c-51cb54cdd569 none            swap    sw              0       0
/dev/scd1       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0


"sudo blkid" gives me:

> /dev/ramzswap0: TYPE="swap" 
/dev/sda1: UUID="1e9001c8-a0cc-417c-bef8-5845b55a63cb" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda5: TYPE="swap" UUID="34402e34-fd48-4da8-94e9-f8b18d99d5aa" 
/dev/sda6: UUID="a0eadf87-fc98-4c27-ae80-f7d24746c0e9" TYPE="ext3" 
/dev/sda7: TYPE="swap" UUID="1dccdf06-a5bb-473c-aa7c-51cb54cdd569" 
polly@Adie:~$ sudo blkid
/dev/ramzswap0: TYPE="swap" 
/dev/sda1: UUID="1e9001c8-a0cc-417c-bef8-5845b55a63cb" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda5: TYPE="swap" UUID="34402e34-fd48-4da8-94e9-f8b18d99d5aa" 
/dev/sda6: UUID="a0eadf87-fc98-4c27-ae80-f7d24746c0e9" TYPE="ext3" 
/dev/sda7: TYPE="swap" UUID="1dccdf06-a5bb-473c-aa7c-51cb54cdd569" 

I am sorry to be such a dunce, but can someone take me through what I need to do so that folder shares survive a restart or lost network connection (folder shares don't seem to survive the restart of another PC on the network, which seems odd).  I need read/write permissions.

At the moment, I set share by choosing 'Sharing Options' from the right click menu.  If, instead I go to right click menu/properties/permissions, under folder access, I have 'Create and delete files', file access is blank.  If I set file access to read/write, it resets to blank when I click on Apply Permissions.

I feel like I am going round in circles and my mind is spinning!!!



Polly

---

