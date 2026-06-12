---
title: "Can't get to login screen after upgrade to Hardy"
date: 2008-05-12
forum: New to Ubuntu
---

### Post by Chew55 on 2008-05-12
I get past the bit with the loadin bar then it jst goes to a blank screen with the equivalent of the hour glass thing in windows then the whole thing just stops.  SO basically, I can't do anything because I can't log in.

Any ideas on whats wrong?

Before I updated I switched from a usb speedtouch modem to an ethernet talk talk modem, but everything was working fine in Gutsy.  Think this may be the problem?

---

### Post by Thingymebob on 2008-05-12
if you press ctrl+alt+f1 you should be presented with a terminal from which you can log in. Once you have logged in I would start looking in your /etc/X11 /xorg.conf for anything out of place also have a look at dmesg and .xsession-errors there should be some hints somewhere there as to what is causing your problem. post all 3 here if you can't see anything.

---

### Post by Chew55 on 2008-05-12
I can't see etc/X11 /xorg.conf because anytime I try and open it I get the message Permission Denied :( 

And how do I view .xsession-errors?

Also, how do I copy the output onto my other partition because thats the only place I will be able to see it to copy it on here?

---

### Post by Thingymebob on 2008-05-12
```
cat /etc/X11/xorg.conf | less
```
to edit
```
sudo vim /etc/X11/xorg.conf
```

same for .xsession-errors

to copy them 
```
sudo cp /etc/X11/xorg.conf ***destination***
sudo cp .xsession-errors ***destination***
```
where destination would be something like ***/media/hda1/***documents/xorg.conf
or wherever your other partition is mounted.

you can direct the output of dmesg to a file using ```
dmesg > dmesg.file
``` and then copy it as above

---

### Post by Chew55 on 2008-05-12
I can now view the 3 files.
How do I find the location of my windows partition while I'm doing all this? I've tried using:

```
sudo fdisk -1
```

But it just gives me some instructions and anytime I follow these instructions it just spits the same instructions back at me.

---

### Post by Thingymebob on 2008-05-12
the option is the lowercase letter L not the number 1 as you have entered
```

sudo fdisk -l
**not**
sudo fdisk -1
```

---

### Post by Chew55 on 2008-05-12
> **Thingymebob said:**
> the option is the lowercase letter l not the number 1 as you have entered
```

sudo fdisk -l
**not**
sudo fdisk -1
```

Ahhhhhhhhh.

I should have tried that lol.  I tried capital i but totally forgot to try l.

---

### Post by Thingymebob on 2008-05-12
You really want to have a look at /etc/fstab to see where windows is mounted.
```
cat /etc/fstab
```
will give you something like
```
# <file system>    				<mount point>   <type>  	<options>			<dump><pass>
  proc             				/proc		proc		defaults			0	0
  #/dev/hda1
  UUID=1837b293-14ff-4ed9-bcb1-d0206521ff30	/		ext3		defaults,errors=remount-ro	0	1
  #/dev/hda3
  UUID=f480556b-b31f-49e9-bd0f-61c1b7cbfb2d	/boot		reiserfs	defaults			0	3
  #/dev/hda5
  UUID=86899f2a-0a6a-4cc3-b641-aa38023b3486	/home		ext3		defaults,rw			0	2
  #/dev/hda8
  UUID=7187dcc3-91be-4e0f-92e4-906a2c680f58	none		swap		sw				0	0
  #/dev/hda6
  UUID=f98f7db7-f341-461d-97ba-21bf2a5c4e13	/mnt/gparted	reiserfs	defaults			0	0
  #/dev/hda7
  UUID=b031e75d-6e47-4253-b5a2-b8d94a46f2ef	/mnt/windows	ntfs		defaults			0	0

  /dev/cdrom					/media/cdrom0	udf,iso9660	user,noauto			0	0

```look for the type that reads ntfs, the path listed in front of that is the mount point

---

### Post by snailmail on 2008-05-12
any simpler way to do it?:confused:

---

### Post by Chew55 on 2008-05-12
> **Thingymebob said:**
> You really want to have a look at /etc/fstab to see where windows is mounted.
```
cat /etc/fstab
```
will give you something like
```
# <file system>    				<mount point>   <type>  	<options>			<dump><pass>
  proc             				/proc		proc		defaults			0	0
  #/dev/hda1
  UUID=1837b293-14ff-4ed9-bcb1-d0206521ff30	/		ext3		defaults,errors=remount-ro	0	1
  #/dev/hda3
  UUID=f480556b-b31f-49e9-bd0f-61c1b7cbfb2d	/boot		reiserfs	defaults			0	3
  #/dev/hda5
  UUID=86899f2a-0a6a-4cc3-b641-aa38023b3486	/home		ext3		defaults,rw			0	2
  #/dev/hda8
  UUID=7187dcc3-91be-4e0f-92e4-906a2c680f58	none		swap		sw				0	0
  #/dev/hda6
  UUID=f98f7db7-f341-461d-97ba-21bf2a5c4e13	/mnt/gparted	reiserfs	defaults			0	0
  #/dev/hda7
  UUID=b031e75d-6e47-4253-b5a2-b8d94a46f2ef	/mnt/windows	ntfs		defaults			0	0

  /dev/cdrom					/media/cdrom0	udf,iso9660	user,noauto			0	0

```look for the type that reads ntfs, the path listed in front of that is the mount point

So say for example mine was the same as yours and said /mnt/windows.  How would I go about copying the output from xorg.conf to a file called output1 which was stored on the windows partition (its not in a subfolder, just as soon as you go into the hard drive in windows you can see it)?

---

### Post by Thingymebob on 2008-05-13
sudo cp /etc/X11/xorg.conf /mnt/windows/output1
would copy the file to your windows drive c:\output1

---

### Post by snailmail on 2008-05-15
anyone know how to do this in conjunction with OSX?

---

