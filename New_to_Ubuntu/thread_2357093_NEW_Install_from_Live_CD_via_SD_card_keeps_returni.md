---
title: "**NEW Install from Live CD via SD card keeps returning I/O error"
date: 2017-03-29
forum: New to Ubuntu
---

### Post by rickc on 2017-03-29
Hello, I d/l the latest version of Ubuntu 16.04.2 LTS (I've also tried other flavors as well, but I'll get to that. ) and I keep getting an I/O error.

I'm super excited, I just built a new desktop and I'm trying to get Ubuntu installed on my new WD 1TB hard drive. 

I've done the following:

*Checked the checksum on the ISO file
* Check the md5 hash 
* Checked the disk for errors

Still no luck. 

I've searched the forums for "“[Errno 5] Input/output error” during Installation" and tried all the advice on those threads. (from flashing BIOS to re- D/L a fresh copy of Ubuntu) 

I've tried to use Gparted to format my HD, 

I also noticed this error "physical block size is 2048 bytes, but Linux says it is 512” I also googled/search the forums on this issue and can't seem to fix it. 
Can someone point me in a new direction as where to start?

Thanks in advance, RickC

---

### Post by cariboo on 2017-03-29
What does the SD card have to do with it, did you try to create a live version on it, and if so how did you do it?

---

### Post by rickc on 2017-03-29
I'm installing from the SD card to the new computer... or at least trying to. 

I downloaded Ubuntu 16.04.2 LTS , used  Win32DiskImager to write it to an SD card. Checked the MD5 hash.
Put it in my SD card reader, booted the computer. Tried to install, got the &#8220;[Errno 5] Input/output error&#8221; during Installation"
I then tried to just "try Ubuntu " option and it boots up fine, but when I goto install &#8220;[Errno 5] Input/output error&#8221; during Installation" I still get this error

---

### Post by rickc on 2017-03-29
I'm 99% sure it has to do with my new Hard Drive, not the SD card. When I start up Gparted I get this error "physical block size is 2048 bytes, but Linux says it is 512&#8221;
I think this is causing the I/O error. 

I read this [https://superuser.com/questions/1130966/the-driver-descriptor-says-the-physical-block-size-is-2048-bytes-but-linux-says](https://superuser.com/questions/1130966/the-driver-descriptor-says-the-physical-block-size-is-2048-bytes-but-linux-says)

But I don't have dd installed by default, whats the best way to fix this error?

Thanks again, rickC

---

### Post by Geoffrey_Arndt on 2017-03-29
OK, what I'd suggest is to use the standard way to do the install instead of the hybrid-exotic method you are trying to use.

1.   Use a usbv2 or usbv3 flash-stick for the install media (SD's can be problematic, and why use that as a first option then???????????),
2.   Download the proper software to RELIABLY create a boot-stick . . . Etcher is my tool of choice:   [https://etcher.io/](https://etcher.io/)

---

### Post by rickc on 2017-03-29
Tnx- I'll give that a try and report back. 

Cheers &#55356;&#57211;

---

### Post by sudodus on 2017-03-30
> **rickc said:**
> I'm 99% sure it has to do with my new Hard Drive, not the SD card. When I start up Gparted I get this error "physical block size is 2048 bytes, but Linux says it is 512”
I think this is causing the I/O error. 

I read this [https://superuser.com/questions/1130966/the-driver-descriptor-says-the-physical-block-size-is-2048-bytes-but-linux-says](https://superuser.com/questions/1130966/the-driver-descriptor-says-the-physical-block-size-is-2048-bytes-but-linux-says)

But I don't have dd installed by default, whats the best way to fix this error?

Thanks again, rickC

That output of gparted is a bug in gparted. It does not understand the hybrid file structure that you cloned into the SD card. I think there is nothing wrong with your SD card, at least not with how it boots. Since you get a problem only when you start the installer, I think something else is wrong, maybe with the hard disk drive or with the connection to it. Maybe there is a problem that no suitable driver is found for your hardware.

Please run the following command lines and post the output in a reply,

```
df -h
sudo lsblk -f
sudo lsblk -m
sudo parted -ls
```

Please put the output of the commands within [noparse]```
tags
```[/noparse] to make it easier to read: Click on the red button **[COLOR="#FF0000"]Go Advanced[/COLOR]**, mark the text and click on the **#** icon above the editing window (or do it manually), like this:

[noparse]```

your output line 1
line 2
line 3
...

```[/noparse]

Notice that you can mark (press the left button while moving the cursor) and paste (press the middle button or wheel to paste) from a terminal window to the editing box of Ubuntu Forums.

---

### Post by rickc on 2017-03-30
Tnx for the advice. I just burnt the image to a CD and it worked. It seems that Linux doesn't likenSD card installs (though my odroid and raspberry pi's do just fine) 
Just in case anyone searches and has this issue, the fix for me was that SD cards don't work so use a CD or USB stick instead

---

### Post by sudodus on 2017-03-30
Thanks for sharing your solution :-)

Please click on **Thread Tools** at the top of the page and mark this thread as SOLVED

---

