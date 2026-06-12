---
title: "copying files at the terminal prompt"
date: 2008-05-05
forum: New to Ubuntu
---

### Post by fraswesseltet on 2008-05-05
I accidentally altered driver settings and I have no display within kubuntu.  All I can get to is the terminal.  There is a file I need to copy to another folder (my first step toward fixing the problem) and I don't know how to do it.  I think it's simple, right?  Here's what I need.

Copy

home/[user name]/Downloads/imp.odt

to 

home/[user name]/Multi/2008/imp.odt

Is there a simple command to do this?

---

### Post by perlluver on 2008-05-05
> **fraswesseltet said:**
> I accidentally altered driver settings and I have no display within kubuntu.  All I can get to is the terminal.  There is a file I need to copy to another folder (my first step toward fixing the problem) and I don't know how to do it.  I think it's simple, right?  Here's what I need.

Copy

home/[user name]/Downloads/imp.odt

to 

home/[user name]/Multi/2008/imp.odt

Is there a simple command to do this?

```
cp /home/username/program /home/multi/program
```

---

### Post by kirios on 2008-05-05
> **perlluver said:**
> ```
cp /home/username/program /home/multi/program
```

And if you want to copy the entire Downloads folder and its contents: 

```
cp -R /home/username/Downloads /home/username/Multi/2008/
```

---

### Post by fraswesseltet on 2008-05-05
OK, thanks, that worked great.  Now what about copying to a USB drive or burning it to a CD?  Is that something that can be done?  I need to get it off the messed up PC so I can view it on a fully-functioning one.  Any help would be greatly appreciated.

---

### Post by keymoo on 2008-05-05
USB drives are usually mounted to /media in Ubuntu. Plug in your USB and it should pop up on your desktop. You can then do something like:
```
cp -R /home/username/Downloads /media/MYUSBDEVICE/Multi/2008/
``` or whatever path you want to copy to.

On my PC my Corsair USB key mounts as /media/CORSAIR

---

### Post by fraswesseltet on 2008-05-05
Is there a way to know what it's called when it mounts?  Is it just 'removable disc"?  My problem is I can't see anything but the command prompt because I messed up the video driver settings (I think).

---

### Post by malathion on 2008-05-05
> **fraswesseltet said:**
> Is there a way to know what it's called when it mounts?  Is it just 'removable disc"?  My problem is I can't see anything but the command prompt because I messed up the video driver settings (I think).

```
sudo fdisk -l
```
Will give you a list of devices on the system

```
mount -l
```
Will tell you where they are mounted

---

### Post by fraswesseltet on 2008-05-05
Or I could also use a memory card.  I just don't know what the path is for either.

---

### Post by fraswesseltet on 2008-05-05
Wow, I definitely don't understand any of what the 'fdisk' command said.  Firstly, it started with "invalid option -- 1".  Anyway, I'm trying to use the HP Digital Drive that came with my laptop, or I could use just a SanDisk SD card.  Anyone know what those would be named as?  When I used nano and opened the media directory, I didn't see the USB device listed, just the cd drives.  But it recognized it when I plugged it in (I think - it lit up).

---

### Post by akiratheoni on 2008-05-05
> **fraswesseltet said:**
> Wow, I definitely don't understand any of what the 'fdisk' command said.  Firstly, it started with "invalid option -- 1".  Anyway, I'm trying to use the HP Digital Drive that came with my laptop, or I could use just a SanDisk SD card.  Anyone know what those would be named as?  When I used nano and opened the media directory, I didn't see the USB device listed, just the cd drives.  But it recognized it when I plugged it in (I think - it lit up).

That's because you typed the number one, not the letter 'l' (the lowercase L)

---

### Post by malathion on 2008-05-05
> **fraswesseltet said:**
> Wow, I definitely don't understand any of what the 'fdisk' command said.  Firstly, it started with "invalid option -- 1".  

Read carefully before executing commands, especially with sudo! :) You should do:

```
sudo fdisk -l
```

That's "l" as in "list"!

---

### Post by fraswesseltet on 2008-05-06
Oh, that makes sense.  Thanks for your help.

---

### Post by muteXe on 2008-05-06
Go to your /media folder and do an "ls" to list the contents.  Then plug in your memory stick, wait about 30 seconds and do another "ls" in the /media folder.  There should be 1 more entry.  My memory stick just shows up as "disk" in the /media folder.
mute

---

