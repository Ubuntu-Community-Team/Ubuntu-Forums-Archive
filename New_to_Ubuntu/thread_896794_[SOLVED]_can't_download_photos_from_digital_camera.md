---
title: "[SOLVED] can't download photos from digital camera"
date: 2008-08-21
forum: New to Ubuntu
---

### Post by jethin on 2008-08-21
I'm trying to download photos from my Canon Powershot SD1000 to my tired old computer via USB. When I plug the camera in my cpu seems to do some "thinking" about the device, but no icon appears on my desktop and I can't seem to access the camera or download the photos. FWIW I've had some problems accessing USB devices in the past (external hard drive). I also don't think I have any of the packages (gthumb, etc.) required to download pics, so any suggestions on that front would be appreciated too.

---

### Post by Lord Xeb on 2008-08-21
Go into your file system and look for the /media. Thats is what I do when I need to get into my didgital camera. Also, make sure that you have a SD card in your camera or else it will not see it  e_e I know, stupid huh?

---

### Post by WRDN on 2008-08-21
If it does not appear in the /media folder, then open the Terminal and type:

```
sudo fdisk -l
```

It may show up here. If it does, type:

```
sudo mkdir /media/camera
```

You can replace the word "camera" with something else if you want. Now, type:

```
sudo mount /dev/[drive] /media/camera
```

Replace [drive] with the letter(s) and number found using the fdisk -l command. It will likely be sdaN or sdbN (where N represents a number).

---

### Post by roelpeeters on 2008-08-21
Does the camera show up as a usb device? You can check with the following command:
```
lsusb
```
I use (on a Gnome desktop) the KDE package digikam. It will install the kde libs that it needs, but integrates nicely with Gnome otherwise.

---

### Post by jethin on 2008-08-28
Sorry I haven't been attending to this thread -- I just got back from vacation. In any case, I tried all of the above suggestions but the only one I had any luck with was detecting the camera as a USB device using lsusb. So, can anyone help me get this sucker mounted?

---

### Post by tommcd on 2008-08-28
What is the output of lsusb ?
Do you have gphoto2 installed? Search for it in synaptic, and install it if you don't. If you have gphoto2, then from the terminal you can run:
```
gphoto2 --auto-detect
```
then cd into your /home directory or wherever you want the pictures uploaded to and run:
```
gphoto2 -P
```
This will upload the pictures.
See if this works.
--------------------
Also have a look at this thread:
[http://ubuntuforums.org/showthread.php?t=286730](http://ubuntuforums.org/showthread.php?t=286730)
It was for Ubuntu Edgy, so I'm not sure if it still applies, but it's worth a shot.

---

### Post by jethin on 2008-09-02
Thanks tommcd, that did the trick. However, before I close this post, can anyone suggest a lightweight, gui package that I can install to perform these commands for me? I'm just seeking the simplest, laziest path possible here.

BTW, here's the output of lsusb for anyone who's interested:

Bus 002 Device 002: ID 04a9:314f Canon, Inc. 
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 002: ID 050d:705a Belkin Components 
Bus 001 Device 001: ID 0000:0000

---

### Post by Vivaldi Gloria on 2008-09-03
jethin,

Why don't you buy a cheap usb memory card reader for 10-15$ and use your Canon's card with it?

Much simpler and also copies faster in general.

---

### Post by jethin on 2008-09-03
Hi Vivaldi Gloria,

That's a good suggestion but so far it's been tricky getting any of my USB devices (Wi-Fi, external hard drive, digital camera) recognized and working smoothly. Perhaps it's best if I just stick with using gphoto2 via the terminal.

---

### Post by philinux on 2008-09-03
Try gthumb.

---

