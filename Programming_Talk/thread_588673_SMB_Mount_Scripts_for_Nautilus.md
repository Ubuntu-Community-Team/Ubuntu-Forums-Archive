---
title: "SMB Mount Scripts for Nautilus"
date: 2007-10-23
forum: Programming Talk
---

### Post by ryanchew on 2007-10-23
Hey everyone,

I was toying around with shell scripting and came up with these handy SMB mounting/unmounting nautilus scripts.
The scripts are fully GUI based from making use of zenity, including sudo prompts.

To mount, right-click on an smb share through on your network select Scripts -> mount.sh
It will ask for the mount point, user name, password and whether to mount as read-only.
To unmount, simply right-click anywhere and select Scripts -> unmount.sh
A popup list of existing SMB mounts will appear and allow you to select which to remove.

These scripts require smbfs, zenity and nautilus-script

Files are attached or downloadable from the links below:
[http://ubuntustuff.chewablestudios.com/mount.sh](http://ubuntustuff.chewablestudios.com/mount.sh)
[http://ubuntustuff.chewablestudios.com/unmount.sh](http://ubuntustuff.chewablestudios.com/unmount.sh)

Load them into your ~/.gnome2/nautilus-scripts/ directory and they should work just fine. No extra configurations needed :D
Please do let me know if you encounter any problems or if you have any improvements/suggestions/feedback. :)

Thanks!

---

