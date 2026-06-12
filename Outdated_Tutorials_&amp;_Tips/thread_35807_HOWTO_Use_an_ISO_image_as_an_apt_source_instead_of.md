---
title: "HOWTO: Use an ISO image as an apt source instead of the cdrom"
date: 2005-05-20
forum: Outdated Tutorials &amp; Tips
---

### Post by battletux on 2005-05-20
First of all thanks to CarlK in #Ubuntu for helping with this.

Basicly this will show you how to create an iso image of your ubuntu cd for use as an apt source so that like me you dont have to spend hours looking for the damn cd to install the odd package here and there.

NOTE: if you already have a downloaded iso of hoary then just skip the cd riping bit. Also remeber to change <user> with your username.

First up insert your hoary cd into your cd drive and wait for it to be mounted.

Now unmount the CD:

```
umount /media/cdrom0
```

to rip the cd:

```
dd if=/dev/hdc of=hoary.iso
```

This will create an iso of your hoary cd called 'hoary.iso' and place it in your /home/<user> folder.

Now we need to find a new home for this image. Just so it was out of my way and harder for me to delete it, i placed it in a hidden folder in the root (/) directory.

```
sudo mkdir /.iso
```

Now move the iso:

```
sudo mv /home/<user>/hoary.iso /.iso
```

Now we need to edit /etc/fstab so that the image is mounted each time the system is booted so:

```
sudo gedit /etc/fstab
``` 

and enter the following line:

```
/.iso/hoary.iso     /mnt/iso     iso9660 ro,loop,auto      0      0
```

**EDIT:** you now need to create the mount point folder:

```
sudo mkdir /mnt/iso
``` 

Here you have two choices you can either reboot the system, which is what i did, or you can run ```
sudo mount -a
``` to reset /etc/fstab without rebooting, the choice is yours, but i rebooted here so i dont know what the sudo mount -a will do.

[B]EDIT:

Ok after looking at this again on my home PC i spotted an error with it to get it to work do the following:[/B]


Now you need to remove the old reference to the cdrom from /etc/apt/sources.list, by:

```
sudo gedit /etc/apt/sources.list
```

By default the line you need to remove is the top one.

You will also ned to add the line into your sources.list so that the iso is used:

```
deb file::///mnt/iso hoary main restricted
```

next up all you need to do is:

```
sudo apt-get update
```

and you finished!

Any questions let me know, but i doubt i'll be able answer them  :-? .

---

### Post by Sionide on 2005-05-24
Very useful, very well thought of. *puts his Ubuntu cd up on the shelf again*

---

### Post by JonahRowley on 2005-05-24
Yes, very useful, but perhaps there are a few steps too many?  I'm not sure of the details, but it should be possible to just copy the files from the CD to a directory and use that.  Maybe I'll find out how and write a sister-HOWTO ;)

---

### Post by battletux on 2005-05-25
[QUOTE=JonahRowley]Yes, very useful, but perhaps there are a few steps too many?  I'm not sure of the details, but it should be possible to just copy the files from the CD to a directory and use that.  Maybe I'll find out how and write a sister-HOWTO ;)[/QUOTE]

Copying the files was a suggestion, but i didn't want one location just filled up with little files. Also doing it this way would allow me to change the iso that i was using without deleteing loads of files, then copying it all across again. This way i just download the new iso, rename it (overwritting the existing one) and reboot, i feel this way would be more usefull if you were to upgrade the distro when say Breezy is released.

If you just wanted to copy the files it would be just as easy. Copy the contents of the cd to any folder you want on the hard drive then just add

```
deb file::///**<location of cd contents>** hoary main restricted
```

to the sources.list and run **sudo apt-get update**

---

### Post by Sionide on 2005-11-03
Works just the same if you put breezy instead of hoary. Very useful as well, my Breezy CDs haven't yet arrived, I borrowed one off a friend to install from and now he wants it back - well I've got a permanent copy of it on my laptop now anyways. :)

Ps. Apologies for the necropost.

---

### Post by HowardDrake on 2005-11-28
I wanted to ask if you could use this technique to improve updating your system from Hoary to Breezy. I'm currently still running Hoary and this would be a nice way to get Breezy on this box quickly and less painfully then doing the 'sudo apt-get dist-upgrade' and downloading it all. If I add my Breezy ISO to my filesystem list, will the apt-get grab the packages from the local ISO? Or am I just creating a potential mess....

---

### Post by pushkarajthorat on 2010-02-22
In my opinion an out-of-box support should be given by aptitude.

I have not found the enhancement reported, so reported it [https://bugs.launchpad.net/ubuntu/+source/apt/+bug/525784](https://bugs.launchpad.net/ubuntu/+source/apt/+bug/525784) 

Regards,Pushkaraj

---

### Post by BryanFRitt on 2010-06-04
I tried it with file:/  and file:/// (and file:// which gave me and error message), 
I also tried it with and without a trailing '/' at the end of the file directory path.
None of those made any difference in [FONT="Courier New"]sudo apt-get update[/FONT] that I could notice.
also tried (for fun) adding multiverse, universe, partner, non-free, but adding those didn't work

[FONT="Courier New"]sudo apt-get update
[/FONT]
gives:

first time:

[FONT="Courier New"]Get:1 file: lucid Release.gpg [189B]                                 
Ign file:/media/Mounted_iso/kubuntu-10.04-dvd-amd64/ lucid/main Translation-en_US                                                         
Ign file:/media/Mounted_iso/kubuntu-10.04-dvd-amd64/ lucid/restricted Translation-en_US                                                   
Get:2 file: lucid Release [3,036B][/FONT]
...
second time, etc...:
 it says the same thing

So, I guess this means it worked...

...

p.s. I also saw another hint as to what you can do...
[http://forums.debian.net/viewtopic.php?f=10&t=1325](http://forums.debian.net/viewtopic.php?f=10&t=1325)

---

### Post by BryanFRitt on 2010-06-04
> **pushkarajthorat said:**
> In my opinion an out-of-box support should be given by aptitude.

I have not found the enhancement reported, so reported it [https://bugs.launchpad.net/ubuntu/+source/apt/+bug/525784](https://bugs.launchpad.net/ubuntu/+source/apt/+bug/525784) 

Regards,Pushkaraj

agreed

---

