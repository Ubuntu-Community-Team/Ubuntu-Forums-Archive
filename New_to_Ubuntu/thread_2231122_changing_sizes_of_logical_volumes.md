---
title: "changing sizes of logical volumes"
date: 2014-06-23
forum: New to Ubuntu
---

### Post by Nosphky on 2014-06-23
My UbuntuStudio 14.04 installation is in a series of 3 logical volumes within a single partition occupying roughly a third of a terabyte disk.  I chose to install in logical volumes (via an lvm gui ) because that seemed to hold the promise of being able to vary the volume size as later needs might require.

The 3 volumes are / ;  /home ; swap;  and there are 225 Gib of free space available for additional volumes or for expanding existing volumes.   The /home volume at 35 Gibs is proving to be too small and I have tried to double its size using the gui but the result is an error message -

"Logical volume is not mounted but is in use. Please close all applications using this device (eg iscsi)" 

There is a lot of stuff that I don't understand about mounting devices because I thought '/home' was the mount point.   Perhaps logical volumes are not mounted ?   

It does appear to me that this volume 'is in use' whenever the machine is booted up with the resident UbuntuStudio os.   Can I get at the volume to resize it with the gui by using a live boot on a USB stick ?

Reading other threads about similar resizing problems concerning physical partitions brings to mind other possible solutions which include having a separate data partition or logical volume.   

Would it be advantageous to create another separate logical volume for datafiles ?  
Would a separate data volume require mounting at boot ?  
If so, what would be the preferred mount point ?  

Ideally, I would like datafiles to be accessible in a series of sub-directories in my /home/  directory.    Any and all input is welcome.

---

### Post by Nosphky on 2014-06-27
I took a chance and tried using a live boot from a usb stick.  This worked but I had to make sure that I didn't carry out any other operation using my home file system.  

I expanded the /home logical volume to double its size and created another logical volume of 50 Gb which I named 'Music'.

When I rebooted to my own installation of UbuntuStudio, I found a new entry in the file manager '54 GB Volume' which on clicking to open was listed as '/media/myhome/e4eae28e-69ee-41e8-9166-89ce48727b9d/'.   

Can I change that unfriendly name to something more friendly like 'Music'?    The logical volume manager, lvm, shows this volume 'Music' as  /dev/MylogicalVG/Music.

How can I link this new volume with the subdirectory ~/myhome/Music  so that clicking on ~/myhome/Music will expose the contents of  /media/myhome/e4eae28e-69ee-41e8-9166-89ce48727b9d/   ?

---

### Post by nerdtron on 2014-06-27
> /media/myhome/e4eae28e-69ee-41e8-9166-89ce48727b9d

Unmount the drive and make a folder like /media/myhome/music
Then mount the logical volume on that folder: mount /dev/MylogicalVG/Music /media/myhome/music

> clicking on ~/myhome/Music will expose the contents of  /media/myhome/e4eae28e-69ee-41e8-9166-89ce48727b9d/   ?

You should create a symbolic link (what you call shortcuts in windows).
Remove or rename your current folder ~/myhome/Music.
Now create the link: ln -s /media/myhome/e4eae28e-69ee-41e8-9166-89ce48727b9d ~/myhome/Music
If you already change the mount point above, it would be: ln -s /media/myhome/music ~/myhome/Music

---

### Post by Nosphky on 2014-06-28
Thanks, nerdtron, for an excellent reply.  That was just what I needed.  I applied the changes you suggested :

- Unmount the drive and make a folder like /media/myhome/music
- Then mount the logical volume on that folder: mount  /dev/MylogicalVG/Music  /media/myhome/music

Then I removed my current ~/myhome/Music directory and created the symbolic link you suggested :
- If you already changed the mount point above, it would be: ln -s /media/myhome/music ~/myhome/music 

This worked fine but did not survive a reboot.   I needed to find a way to get the logical volume to mount automatically at reboot.

I used lvm to edit the properties of the logical volume, Music, to define a mount point at reboot.  After a few unsuccessful attempts, I finally got it right :

setting mount point at reboot as :  /media/myhome/music

Thanks again for the help.

---

