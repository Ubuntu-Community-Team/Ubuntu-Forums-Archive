---
title: "how to sync iphone &amp; ipod touch with ubuntu"
date: 2010-01-29
forum: Outdated Tutorials &amp; Tips
---

### Post by hotashes02 on 2010-01-29
Easy Way To Sync Your iPhone & iPod touch With Rhythmbox, Nautilus, Etc. In Ubuntu
 
Like WebUpd8 reader StoneCut said in a comment on it's previous tip, he wrote yet another post for iPhone & iPod touch owners which use Linux. So here it is:
 
In our previous tutorial we showed how you to access the iPhone & iPod touch OS 3.x filesystem and read/write to its music database using iFuse and by compiling our own libgpod4. Then we had to create a file on the iPhone & iPod touch, manually mount the iPhone & iPod touch each time and so on. Maybe a bit complicated for an average user.
 
However, there is now a lot easier way using GVFS which will automount your iPhone & iPod touch for syncing with Rhythmbox, for example. And you don't need to compile anything anymore. It works for Ubuntu Karmic and Lucid (only Karmic tested). The required PPA does not carry any packages for Jaunty, sorry.
 
Setup GVFS support for iPhone & iPod touch
 
 
For this to work, your iPhone & iPod touch does NOT need to be jailbroken, unless you want to mount the root file system using ifuse for some reason.
 
1. First off, we need to add this PPA:
```
sudo add-apt-repository ppa:pmcenery/ppa
```2. And update your sources and packages:
```
sudo apt-get update && sudo apt-get dist-upgrade
```3. Now let's install the relevant packages:
```
sudo apt-get install gvfs gvfs-backends gvfs-bin gvfs-fuse libgvfscommon0 ifuse libgpod-dev libgpod-common libiphone-utils libiphone0 python-iphone libplist++1 libplist-utils python-plist libusb-1.0-0 libusb-1.0-0-dev libusbmuxd1 usbmuxd
```4. Now we need to add ourself to the group "fuse" so we can mount the device as regular user (without sudo):
```
sudo adduser $USER fuse
```Additionally, we need to edit a file to allow regular users to mount this device:
```
sudo gedit /etc/fuse.conf
```Find the line that says "#user_allow_other" and remove "#" in front of it so it says: "user_allow_other".
 
That's it. You can now just plug in your iPhone and use it with Rhythmbox, Nautilus or whatever. You won't need to do anything else. Your iPhone will appear twice on your desktop: Once as the PTP camera device you probably know already and once again with a mobile phone icon from where you can access the file system. Congratulations !
 
There's one last catch if you installed the optional GTKpod. For GTKpod you will still need to manually mount the device to /mnt/ipod using ifuse.

-> Optional
```
sudo apt-get install gtkpod
```
 
So let's set things up for that, too:
```
sudo mkdir /mnt/ipod
sudo chmod 777 /mnt/ipod
```Ok, now if you want to use your iPhone with GTKpod you will need to mount and umount it manually everytime.
 
To mount (the just launch GTKpod and let it read the device):
```
ifuse /mnt/ipod
```Make sure you unmount inside GTKpod when you're done and then issue this command:
```
fusermount -u /mnt/ipod
```If your iPhone is jailbroken, then you can also mount the root file system using iFuse but this is not recommended if you just want to sync music. Here's how to do it anyway:
```
ifuse /mnt/ipod --root
```Extra Tip:
 
If your device is jailbroken and has an SSH server installed you can also access your iPhone via SSH over USB
```
sudo iproxy 2222 22
```Now you can SSH into your iPhone via USB:
```
ssh -p 2222 root@localhost
```[A big thank you to StoneCut for writing this article, all the credits go to him]
 
source found in:
[http://www.webupd8.org/2010/01/easy-way-to-sync-your-iphone-with.html](http://www.webupd8.org/2010/01/easy-way-to-sync-your-iphone-with.html)

---

### Post by magikid on 2010-02-13
I ran into some problems uninstalling this so I'll post what I did to remove these for those interested:

```
sudo aptitude remove ifuse libgpod-dev libgpod-common libiphone-utils libiphone0 python-iphone libplist++1 libplist-utils python-plist libusb-1.0-0 libusb-1.0-0-dev libusbmuxd1 usbmuxd
```

Aptitude should offer to downgrade gvfs and libgpof-common back to the original version.

---

