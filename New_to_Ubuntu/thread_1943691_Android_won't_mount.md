---
title: "Android won't mount"
date: 2012-03-19
forum: New to Ubuntu
---

### Post by fatharpdavis on 2012-03-19
When I plug my Android (2.3.6 Gingerbread.FA19) in to the USB port, it doesn't show up in the "places" menu or the "computer" window. Everything seems to work fine on the phone-end (i.e. it asks me if I want to turn on USB storage) and it works alright in windows. Anyone know how to fix this? Thanks!
PS I'm using Ubuntu 11.10 Oneiric

---

### Post by spillin_dylan on 2012-03-19
For the record, when it asks you to go into USB mode, do you enter USB mode?  

Also, if you are trying to use it with Banshee (or Amarok, etc) I think there is something about adding a ".ismediaplayer" file to your Android's filesystem.  I'm not 100% sure on the procedure to do that, though....

---

### Post by fatharpdavis on 2012-03-20
Thanks spillin,
I do go into USB mode when it asks. I would like to just open it in Nautilus (i.e. have access to its files) but I could also access it in Banshee--that's what I use for music.

---

### Post by hamoid on 2012-03-21
I'm having the same problem, and it's something new. I've had this Nexus One for a long time and it was working. Since a few days ago, when I turn on the USB storage mode, it's not detected on the computer. I'm on 11.10.

lsusb shows Bus 001 Device 006: ID 18d1:4e11 Google Inc. Nexus One

Any test I could do?

---

### Post by sirweldsalot on 2012-04-03
this might sound crazy....
if you have usb debugging enabled and you have turned on usb storage and the only thing your phone will do is charge...
i would suggest trying a different cord.
the cord my samsung came with won't allow me to do anything but charge. 
it looks like a regular cord (usb at one end other end plugs into phone), but it won't work.
i dug into my bag-o-cords and grabbed a kindle cord. 
the kindle cord works.
this made my phone waaayyy easier to flash using odin. lol!!!
i really hope i helped... and if i did please pass it on.

also, try booting with the phone attached. 11.10 is weird with media sometimes.

---

### Post by hamoid on 2012-04-09
Gee! I just found out what's going on!

It is indeed mounting the drive. The problem (in my case) is that the mount name is ".22". Yes, a dot and the number 22. 

File and folder names that begin with . are invisible, so Ubuntu mounts the drive, but doesn't show it or notify about it.

I used a file manager with "show hidden files" and I found the phone's sd card mounted inside /media. That's the exact opposite of intuitive.

---

### Post by drdos2006 on 2012-04-09
If you have the Android-SDK installed, use the terminal, go to your Android directory and /platform tools.
Type ./adb devices and see if your android device is listed.

regards

---

### Post by hamoid on 2012-04-11
"adb devices" shows my device only if I turn on USB Debugging.

And if debugging is on, I can not mount the USB device. It's one or the other.

But is that related to the mount name? (.22)

---

### Post by Xieth on 2012-04-24
i been having same issues i hav usb debug turned on and get the unable to mount, check this out i logged in as Root , mounted right away prob solved. just need root access, works on htc eris and optimus s

---

### Post by JoeBeach on 2012-07-13
We had this problem on my wife's Samsung Galaxy phone running Android 2.3. It turned out that there was a settings page to make the USB connection work for file transfers. The instructions we followed are available at: 

[http://androidadvices.com/enable-usb-storage-android-devices/#.T_-b8-Hz13A](http://androidadvices.com/enable-usb-storage-android-devices/#.T_-b8-Hz13A)

Following these instructions, we were able to transfer files between the phone and the laptop. The laptop was running Ubuntu 12.04.

---

### Post by Hadaka on 2012-07-13
A handy tip for seeing   dot filename..hidden files in a directory
rather than an     ls    command, type...

```
 ls -al 
```

and all the hidden files within that path will display.

---

### Post by DingusFett on 2012-07-13
Mine started having a similar problem when upgraded to 4.0 (ICS), and the way I get around it is before connecting cable, go to Settings > More... (under Wireless and networks heading) > USB Utilities > Connect storage to PC > plug in cable > Turn on USB storage.

It then mounts my SD card and the internal memory as different partitions. It's a roundabout way, but can then use it fine like a normal USB drive.

---

### Post by garypeg on 2013-06-24
I have a Samsung Galaxy Y that came with 2.3 (I think it has updated a bit since so it's 2.3+).  To activate the USB capability, follow the instructions here.  [http://www.samsung.com/us/support/supportOwnersHowToGuidePopup.do?howto_guide_seq=7136&prd_ia_cd=N0000003&map_seq=48525&regDt=20120622163542page_gb=D&model_name=SGH-I897type_ia_cd=N0000002subtype_ia_cd=N0000003row_index=1](http://www.samsung.com/us/support/supportOwnersHowToGuidePopup.do?howto_guide_seq=7136&prd_ia_cd=N0000003&map_seq=48525&regDt=20120622163542page_gb=D&model_name=SGH-I897type_ia_cd=N0000002subtype_ia_cd=N0000003row_index=1)

Ubuntu 13.04 recognized the device immediately.


garyk

---

