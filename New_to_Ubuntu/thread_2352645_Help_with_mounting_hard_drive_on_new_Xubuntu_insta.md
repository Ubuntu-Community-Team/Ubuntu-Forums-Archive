---
title: "Help with mounting hard drive on new Xubuntu installation"
date: 2017-02-14
forum: New to Ubuntu
---

### Post by fozziebear on 2017-02-14
First I should say I am a complete Linux/Ubuntu newbie although by searching these forums I have resolved a lot of initial issues.

I have just built a Xubuntu desktop to act as a headless download PC. I have now updated to Trusty Ubuntu 14.04.5 LTS.

I built the PC with a single 40Gb hard drive and later added another 160Gb hard drive to act as my data drive. I found out how to change permissions from root on the new drive and share the whole partition using Samba so I can access it remotely.
The new drive is my download location but the drive does not automatically mount on startup meaning I have to click on it to mount the drive. I have tried various ways to get it to mount using Edit Mount Options in Gnome Disks as per below. But although its set to Automount it does not
[ATTACH=CONFIG]273699[/ATTACH]
I have come to the conclusion that I have to edit the fstab file. I have searched this and other forums and there is lots of information editing fstab but most replies suggest a knowledge of how to use terminal. I am happy to follow detailed instructions but don't know how to edit a file using terminal and worried I might make changes that will prevent my new install from booting. 

There are also threads about using different types of mount point and using the disk UUID which I have obtained. 

In essence I just want the disk to automatically mount when I log in. It doesn't have to mount at boot although there would be no harm in that option. I am using get_iplayer to download radio and TV shows and I need the save location to be available to the programme or the PVR function wont work if the PC reboots.

The information about my disk is as follows:-

Path: /dev/sda1Staus: Mounted on /media/john/Data
Label: Data
UUID: 42cadc54-408a-4a35-9500-2edc7cf55abc
The disk is formatted with ext4

My existing fstab is:-

```
# /etc/fstab: static file system information.#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point> <type> <options> <dump> <pass>
# / was on /dev/sda1 during installation
UUID=0ce857d1-dfa4-41a9-9ab7-d1e66920b596 / ext4 errors=remount-ro 0 1
# swap was on /dev/sda5 during installation
UUID=90d340cc-6aa3-4b72-89ec-6bfaacf6f16f none swap sw 0 0
```

I assume fstab is a system file and locked when Ubuntu is running. Am I able to edit it in a text editor and over-write the exiting file using a live CD or am I over complicating the process.
Any help or guidance would be appreciated
Fozzie

---

### Post by howefield on 2017-02-14
To edit the fstab file use..

```
sudo nano /ect/fstab
``` 

and add

```
UUID=42cadc54-408a-4a35-9500-2edc7cf55abc /Data           ext4    defaults        0       2
```

to the bottom of the file, then save with Ctrl + O, enter and Ctrl + X 

Check all is well with..

```
sudo mount -a
```

I think that would do it.

---

### Post by Impavidus on 2017-02-14
+1

nano is a simple text editor running in the terminal, sudo gives you the power to modify system files.

Note that the line given by howefield will mount the data partition at /Data, not at /media/john/Data. When you let the GUI automatically mount stuff it will be mounted somewhere in /media/username, but for automatically mounted partitions this is less convenient.

---

### Post by fozziebear on 2017-02-14
> **howefield said:**
> To edit the fstab file use..

```
sudo nano /ect/fstab
``` 

and add

```
UUID=42cadc54-408a-4a35-9500-2edc7cf55abc /Data           ext4    defaults        0       2
```

to the bottom of the file, then save with Ctrl + O, enter and Ctrl + X 

Check all is well with..

```
sudo mount -a
```

I think that would do it.


Firstly many thanks howefield for the quick reply and detailed instructions.
I have opened terminal and typed in *[COLOR=#000000][FONT=&quot]sudo nano /ect/fstab [/FONT][/COLOR]*[COLOR=#000000][FONT=&quot]which has brought up the Nano window but its blank? 

[/FONT][/COLOR][COLOR=#000000][FONT=&quot]Your instructions are to add the code at the bottom but there is no other text visible. I would have expected to see the existing fstab entries as per my original post[/FONT][/COLOR][COLOR=#000000][FONT=&quot].
[/FONT][/COLOR]Should I continue to just paste the code in where the cursor is or should I be doing something else? Also is the spacing between the various fields important e.g. is there a single or more spaces between \data & ext4 and ext4 & defaults etc etc.

Sorry to be pedantic but I am trying to learn as well as resolve the issue.
Many thanks
Fozzie
ps i tried to upload another screenshot but even though I am logged in I still get an error that I need to log in before I can perform this action. Is this a general problem with this forum or just me?

---

### Post by Impavidus on 2017-02-14
> **fozziebear said:**
> Firstly many thanks howefield for the quick reply and detailed instructions.
I have opened terminal and typed in *[COLOR=#000000][FONT=&amp]sudo nano /ect/fstab [/FONT][/COLOR]*[COLOR=#000000][FONT=&amp]which has brought up the Nano window but its blank? [/FONT][/COLOR]

That's a typo. It should be```
sudo nano /etc/fstab
```

---

### Post by howefield on 2017-02-14
Whoops.. apologies for the typo.

---

### Post by fozziebear on 2017-02-14
Oops Even I should have seen that LOL.
That appears to have worked many thanks to both of you.
One final thought is that as you described the mount point is now \Data which means that the directory is part of the filing system. It also as root permissions again which means I cant share it. Is it possible to change the permissions on this directory to Everyone? Also will installed programs automatically have read write access to this directory.
Many thanks
Fozzie

---

### Post by fozziebear on 2017-02-14
No problems I should have seen that :-)
Thanks again for the guidance

---

### Post by ajgreeny on 2017-02-14
We would normally avoid everyone having full permissions to a partition (or drive) for the sake of security, but if that is needed, you will need to set the mountpoint permissions accordingly.

Normally you would make you, as user, the owner of the partition with ```
sudo chown -R $USER:$USER /Data
``` then set the read/write permissions as required with ```
chmod -R 755 /Data
```but if every user needs full permissions you may need that set to 777 instead of 755.

Wait for others to comment on that 777 risk as there may be other ways to deal with it that I'm unaware of.

---

### Post by fozziebear on 2017-02-14
Many thanks AJGreeney

Again may thanks for your help and patience.
Fozzie

---

