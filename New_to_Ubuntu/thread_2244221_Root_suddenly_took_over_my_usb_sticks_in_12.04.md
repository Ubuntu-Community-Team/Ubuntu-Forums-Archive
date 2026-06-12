---
title: "Root suddenly took over my usb sticks in 12.04"
date: 2014-09-14
forum: New to Ubuntu
---

### Post by mrnewtothis on 2014-09-14
I have been using 12.04 happily for some time but suddenly root has seemed to have taken over use of USB memory sticks or USB card reader so admin users no longer have permision to do anything.
My USB memory stick has become unusable as I am unable to delete and unable to save to it.

Just wondering if my wife has changed something without knowing it, as she was using my comp recently or something else and how I get it back so that it works as normal.

The memory stick is just for transfering files and does not have system files on it. and the card reader reads my camera card. Normally they both open up on plug in and I can do what I like with them but now I am getting a usb0 and can do nothing.

Thanks for any help

---

### Post by grahammechanical on 2014-09-14
The root account is locked in Ubuntu.

> [COLOR=#333333][FONT=Ubuntu]Ideally, you run as a user that has only the privileges needed for the task at hand. In some cases, this is necessarily Root, but most of the time it is a regular user.[/FONT][/COLOR]

> **By default, the Root account password is locked in Ubuntu.**[COLOR=#333333][FONT=Ubuntu] This means that you cannot login as Root directly or use the [/FONT][/COLOR]su[COLOR=#333333][FONT=Ubuntu] command to become the Root user. However, since the Root account physically exists it is still possible to run programs with root-level privileges. This is where [/FONT][/COLOR]sudo[COLOR=#333333][FONT=Ubuntu] comes in - it allows authorized users (normally "Administrative" users; for further information please refer to[/FONT][/COLOR][AddUsersHowto]("https://help.ubuntu.com/community/AddUsersHowto")[COLOR=#333333][FONT=Ubuntu]) to run certain programs as Root without having to know the root password.[/FONT][/COLOR]

[http://ubuntuforums.org/showthread.php?t=1877557](http://ubuntuforums.org/showthread.php?t=1877557)

Everything happens for a reason. Do you normally run as administrator when adding and deleting files in these USB sticks? If we launch File Manager (nautilus) with administrator (root) privileges and create folders or copy files, then those folders and files become owned by root and we cannot do much with them when we are running as standard user.

But as administrator we should be able to change the permissions on the folders and files.

A warning example, 

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

Regards.

---

### Post by Impavidus on 2014-09-14
Usually usb sticks and camera's memory cards are formatted as FAT32, which doesn't support permissions. How are yours formatted?

---

### Post by JKyleOKC on 2014-09-14
> **mrnewtothis said:**
> I have been using 12.04 happily for some time but suddenly root has seemed to have taken over use of USB memory sticks or USB card reader so admin users no longer have permision to do anything.It sounds as if the automatic mounting of your USB sticks has changed the permissions it assigns to them. I've had this happen to me in the past and never did find out why. However, it's fairly easy to fix, using the command line.

First we need to know the device name your system assigns to the USB stick when you plug it in. Plug one in and mount it if it does not do so automagically, then open a terminal window and type "mount" followed by pressing Enter. This will give you a listing of all the devices currently mounted. Near the bottom of the list should be a line or two that will look something like this:```
[COLOR="#FF0000"]/dev/sdb1[/COLOR] on /media/HP V125W [COLOR="#0000FF"]type vfat[/COLOR] ([COLOR="#00FF00"]rw,nosuid,nodev,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,showexec,flush,uhelper=udisks[/COLOR])
```
It won't be in color however, and the part that I show in green will definitely be quite a bit different. The critical part that identifies it as being your USB stick is what I show in blue, and the device name is what I show in red. The "HP V125W" comes from the volume label of the USB stick and will be different also.

Write down the device name to remember it, then type "sudo nano /etc/fstab" to open your automatic-opening configuration, and add a line like this to the end of the file:```
[COLOR="#FF0000"]/dev/sdb1[/COLOR]   /media/usb    vfat     rw,user,noauto,umask=0,uid=1000
```Again, I've indicated the device name in red. Be sure to use the actual device name you found earlier. However you should keep the string that starts "rw" as I show it here. The "rw" assures read-write access, "user" gives you the ability to mount the device without having to use "sudo", "noauto" means that the system can still boot with no stick plugged in, "umask" gives "rwx" permission to everyone, and "uid" gives ownership of the device to UID 1000, which is always the first one you defined at install time and the one that automatically gets administrator capabilities. After adding the line, save the file by pressing CTRL-O, hit Enter to accept the file name, then exit nano via CTRL-X.

You may need to create the "/media/usb" mount point manually if it does not already exist. However once that is done and the system re-booted, you should see full usability of your USB sticks.

Hope this helps!

---

### Post by JKyleOKC on 2014-09-14
> **Impavidus said:**
> Usually usb sticks and camera's memory cards are formatted as FAT32, which doesn't support permissions. How are yours formatted?This is quite true, but the mount point itself DOES have permissions, assigned automatically when the stick is mounted. The device permissions then control access to all the data that's mounted; if the device mounts with owner of "root" and "other" permission of read-only, then the entire stick will be read-only, and since only the owner can make changes, the OP's problem appears.

I suspect that somewhere in the chain of kernel updates, the automount capabilities changed slightly so as to change the umask for USB and other external storage devices...

---

### Post by mrnewtothis on 2014-09-15
> **JKyleOKC said:**
> It sounds as if the automatic mounting of your USB sticks has changed the permissions it assigns to them. I've had this happen to me in the past and never did find out why. However, it's fairly easy to fix, using the command line.

First we need to know the device name your system assigns to the USB stick when you plug it in. Plug one in and mount it if it does not do so automagically, then open a terminal window and type "mount" followed by pressing Enter. This will give you a listing of all the devices currently mounted. Near the bottom of the list should be a line or two that will look something like this:```
[COLOR=#FF0000]/dev/sdb1[/COLOR] on /media/HP V125W [COLOR=#0000FF]type vfat[/COLOR] ([COLOR=#00FF00]rw,nosuid,nodev,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,showexec,flush,uhelper=udisks[/COLOR])
```
It won't be in color however, and the part that I show in green will definitely be quite a bit different. The critical part that identifies it as being your USB stick is what I show in blue, and the device name is what I show in red. The "HP V125W" comes from the volume label of the USB stick and will be different also.

Write down the device name to remember it, then type "sudo nano /etc/fstab" to open your automatic-opening configuration, and add a line like this to the end of the file:```
[COLOR=#FF0000]/dev/sdb1[/COLOR]   /media/usb    vfat     rw,user,noauto,umask=0,uid=1000
```Again, I've indicated the device name in red. Be sure to use the actual device name you found earlier. However you should keep the string that starts "rw" as I show it here. The "rw" assures read-write access, "user" gives you the ability to mount the device without having to use "sudo", "noauto" means that the system can still boot with no stick plugged in, "umask" gives "rwx" permission to everyone, and "uid" gives ownership of the device to UID 1000, which is always the first one you defined at install time and the one that automatically gets administrator capabilities. After adding the line, save the file by pressing CTRL-O, hit Enter to accept the file name, then exit nano via CTRL-X.

You may need to create the "/media/usb" mount point manually if it does not already exist. However once that is done and the system re-booted, you should see full usability of your USB sticks.

Hope this helps!

Worked a treat and thanks for that.

---

