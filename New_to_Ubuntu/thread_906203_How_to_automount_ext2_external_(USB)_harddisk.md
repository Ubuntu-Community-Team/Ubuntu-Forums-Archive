---
title: "How to automount ext2 external (USB) harddisk ???"
date: 2008-08-31
forum: New to Ubuntu
---

### Post by taekr on 2008-08-31
Hi, all 

Well, after 5 hours trials and errors, now I just can not do this anymore. I'm a bit frustrated. 

just bought a 750GB harddisk .. external usb harddisk.. 

and the problem is when I switch the harddisk on, the system automounts it but as read-only (because of root ownership).

Is there anyway I can have it automounted as read/write with ownership being the user when it is connected to system? 

Cheers,

---

### Post by Pro-reason on 2008-08-31
To be automounted with user ownership, it helps to have the "user" option set in the /etc/fstab entry for the drive.

See [https://help.ubuntu.com/community/MountDevicesTroubleshooting](https://help.ubuntu.com/community/MountDevicesTroubleshooting) and other tutorials on fstab and mounting.

---

### Post by taekr on 2008-09-02
> **Pro-reason said:**
> To be automounted with user ownership, it helps to have the "user" option set in the /etc/fstab entry for the drive.

See [https://help.ubuntu.com/community/MountDevicesTroubleshooting](https://help.ubuntu.com/community/MountDevicesTroubleshooting) and other tutorials on fstab and mounting.


Well, I have looked at the link..  still can't do it. 

NOw.. 

750GB formated as Ext2  

What I did was 

UUID=76b1643b-bcc8-44eb-816f-38fee527fff6  ext2  relatime 0  2 


Then, the system didn't boot properly.. so I had to remove to start the system. 

My question is how to have my external harddisk (ext2) automounted as I power it on and umounted as I power it off..  

I tried it with different settings but always couldn't boot properly..

Could you please write a single line to put into fstabe for me??/

That's what I need...  I can't find any information about this.. 

so frustrating!

---

### Post by drs305 on 2008-09-02
> **taekr said:**
> Well, I have looked at the link..  still can't do it. 

NOw.. 

750GB formated as Ext2  

What I did was 

**UUID=76b1643b-bcc8-44eb-816f-38fee527fff6  ext2  relatime 0  2 **


Then, the system didn't boot properly.. so I had to remove to start the system. 

My question is how to have my external harddisk (ext2) automounted as I power it on and umounted as I power it off..  

I tried it with different settings but always couldn't boot properly..

Could you please write a single line to put into fstabe for me??/

That's what I need...  I can't find any information about this.. 

so frustrating!

First, an external drive *should* mount without anything in fstab....

Your line doesn't include a mount point. Create a mount point, normally in /media, then change ownership to yourself and set permissions.

```

sudo mkdir /media/**[COLOR="DarkRed"]mountpoint[/COLOR]**
sudo chown -R [COLOR="DarkRed"]*username:*[/COLOR] /media/*[COLOR="DarkRed"]mountpoint[/COLOR]*
chmod -R 755 /media/*[COLOR="DarkRed"]mountpoint[/COLOR]*

```

Make sure the UUID is correct. Compare these results with the fstab entry:
```

sudo blkid

```

Backup fstab and open for editing (example uses gedit):
```

sudo cp /etc/fstab /etc/fstab.bak
gksu gedit /etc/fstab

```

Add this line:
```

UUID=76b1643b-bcc8-44eb-816f-38fee527fff6  /media*[COLOR="DarkRed"]/mountpoint[/COLOR]* ext2 defaults,user 0  2 

```

---

### Post by trash on 2008-09-22
> **drs305 said:**
> First, an external drive *should* mount without anything in fstab....

Your line doesn't include a mount point. Create a mount point, normally in /media, then change ownership to yourself and set permissions.

```

sudo mkdir /media/**[COLOR="DarkRed"]mountpoint[/COLOR]**
sudo chown -R [COLOR="DarkRed"]*username:*[/COLOR] /media/*[COLOR="DarkRed"]mountpoint[/COLOR]*
chmod -R 755 /media/*[COLOR="DarkRed"]mountpoint[/COLOR]*

```

Make sure the UUID is correct. Compare these results with the fstab entry:
```

sudo blkid

```

Backup fstab and open for editing (example uses gedit):
```

sudo cp /etc/fstab /etc/fstab.bak
gksu gedit /etc/fstab

```

Add this line:
```

UUID=76b1643b-bcc8-44eb-816f-38fee527fff6  /media*[COLOR="DarkRed"]/mountpoint[/COLOR]* ext2 defaults,user 0  2 

```

aside from my drive being an internal and ext3 and mounted ~/storage, i've followed the above and can't write to the drive:(.. I can write to the 'lost and found' folder that exsists on the drive but thats it... whats missing to let me write to the drive and not just the folder on the drive?

---

### Post by egalvan on 2008-09-22
[B]First, an external drive should mount without anything in fstab....

Your line doesn't include a mount point. Create a mount point, normally in /media, then change ownership to yourself and set permissions.
[/B]

I'm working on a related problem, so I used the fresh install of 8.04.1 to test this...

1)
plugged in an external 750g hard-drive drive...

Nautilus popped up with the drive open, and I could read and write, delete and create.

2)
plugged in a 256m flash drive, same thing as above.


no fstab, no mount points, just plug and use...
and yes, they show in /media with their labels


BUT, these DO NOT WORK in my "problem installation", but that's another post.

(it seems to be related to ```
polkit-gnome-authorization
```
which I foolishly played with)

ErnestG

---

### Post by kansasnoob on 2008-09-22
I don't know about Xubuntu, but in Ubuntu I've found either pmount or usbmount to solve nearly all of my external drive problems.

I've come to prefer pmount so, since I don't know how it'll work with Xubuntu, I'd go to synaptic and type pmount into search, then "tick" on "mark for installation" - it depends on hal so you might see some dependicies pop up - if it requires nautilus JUST UNTICK IT! (If it won't run on Thunar you don't want it). 

Anyway that would be my first choice, but if pmount wants to pull in nautilus, then try usbmount (which was my favorite before pmount).

Oh, and you'll likely have to either restart or at least cntrl > alt > bckspc for changes to take.

---

### Post by kansasnoob on 2008-09-22
> **egalvan said:**
> [B]First, an external drive should mount without anything in fstab....

Your line doesn't include a mount point. Create a mount point, normally in /media, then change ownership to yourself and set permissions.
[/B]

I'm working on a related problem, so I used the fresh install of 8.04.1 to test this...

1)
plugged in an external 750g hard-drive drive...

Nautilus popped up with the drive open, and I could read and write, delete and create.

2)
plugged in a 256m flash drive, same thing as above.


no fstab, no mount points, just plug and use...
and yes, they show in /media with their labels


BUT, these DO NOT WORK in my "problem installation", but that's another post.

(it seems to be related to ```
polkit-gnome-authorization
```
which I foolishly played with)

ErnestG


The problem I have is, "Nautilus popped up with the drive open, and I could read and write, delete and create."

Xubuntu uses Thunar instead of Nautilus. That's why I cautioned about installing an app that requires changing the whole file manager.

---

### Post by egalvan on 2008-09-22
> **kansasnoob said:**
> The problem I have is, "Nautilus popped up with the drive open, and I could read and write, delete and create."

Xubuntu uses Thunar instead of Nautilus. That's why I cautioned about installing an app that requires changing the whole file manager.

I was not recommending changing anything....
(in fact I prefer Thunar to Nautilis)

I was merely pointing out that a "clean" install of Ubuntu/Kubuntu mounted an external 
USB flash without any action on my part...

Ubuntu popped up Nautilis on BOTH flash drive and hard drive.

Kubuntu popped up a KDE Daemon asking "what to do" with the flash drive...
then put an icon on the desktop...
clicking on that popped up Dolphin.

BUT Kubuntu did NOT open the USB HARD DRIVE...
It doesn't show anywhere...

I don't have Xubuntu installed on any machine at the moment..

Just trying to quantify actions taken by a fresh install, and compare them to a used install...

It appears to be related to the file manager.
But I'm far from a Linux expert, so I hope others will chime in.

And I will look into pmount and usbmount.
They look interesting.

---

### Post by egalvan on 2008-09-24
> **kansasnoob said:**
> I don't know about Xubuntu, but in Ubuntu I've found either pmount or usbmount to solve nearly all of my external drive problems.

I've  prefer pmount,  I don't know how it'll work with Xubuntu, go to synaptic ... search, "tick" on "mark for installation" - depends on hal  some dependicies pop up - if it requires nautilus JUST UNTICK IT! (If it won't run on Thunar you don't want it). 

that would be my first choice, but if pmount wants to pull in nautilus, then try usbmount (which was my favorite before pmount).

Oh, and you'll likely have to either restart or at least cntrl > alt > bckspc for changes to take.


Interesting ideas here, so I fire up Synaptic and got the Description for pmount.

```
Description:
mount removable devices as **normal user**
pmount is a wrapper around the standard mount program which permits normal
users to mount removable devices without a matching /etc/fstab entry. This
provides a robust basis for automounting frameworks like GNOME's Utopia
project and confines the amount of code that runs as root to a minimum.

This package also contains a wrapper "pmount-hal" which reads some
information like device labels and mount options from hal and passes
them to pmount. Install the package "hal" if you want to use this
feature.

If a LUKS capable cryptsetup package is installed, pmount is able to
transparently mount encrypted volumes.
```

Although I wonder about that NORMAL USER thing.
What are they meaning with that?

Also, no dependencies on Nautilus or Thunar that i could find, just several libs and suggestion for crypto and hal.

---

