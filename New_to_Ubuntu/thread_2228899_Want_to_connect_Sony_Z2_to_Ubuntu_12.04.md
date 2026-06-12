---
title: "Want to connect Sony Z2 to Ubuntu 12.04"
date: 2014-06-10
forum: New to Ubuntu
---

### Post by AnastasiaV on 2014-06-10
Hello!
I have Ubuntu 12.04 and I try to connect it with Sony Xperia Z2 (which  has Android 4.4) via USB. I have set Mass Storage Mode(MSC) setting but  nothing happens when I connect cell phone to the laptop. Please advise  what else I can do.  
Thanks!

---

### Post by Vladlenin5000 on 2014-06-10
Hi, welcome.

Have you tried MTP instead?

---

### Post by AnastasiaV on 2014-06-10
> **Vladlenin5000 said:**
> 

Have you tried MTP instead?

Hi!
Nope... How can I do it?...

I have done upgrade using this article [http://www.webupd8.org/2013/01/upgrade-to-gvfs-with-mtp-support-in.html](http://www.webupd8.org/2013/01/upgrade-to-gvfs-with-mtp-support-in.html) but I still does not see my phone in the file manager when I connect it.

---

### Post by Vladlenin5000 on 2014-06-10
[https://www.youtube.com/watch?v=JLNxVHU1wi8](https://www.youtube.com/watch?v=JLNxVHU1wi8)

---

### Post by Vladlenin5000 on 2014-06-10
Not my video but it goes to point.

---

### Post by HatoExB on 2014-06-10
> **AnastasiaV said:**
> Hello!
I have Ubuntu 12.04 and I try to connect it with Sony Xperia Z2 (which  has Android 4.4) via USB. I have set Mass Storage Mode(MSC) setting but  nothing happens when I connect cell phone to the laptop. Please advise  what else I can do.  
Thanks!
Hi Anastasia,

I had a similar problem on my Xperia Z1. The instruction Vladlenin said to do is something you should try **FIRST**. If it doesn't work, follow this:

1. Go to About Phone in System Settings (very bottom).
2. Scroll down and find the firmware number (should look like the Z1's firmware number but a little different: 14.3.A.1.757). Click this 5 times fast.  You'll become a "developer".  
3. Press the back button. You'll see a new entry above About Phone called Developer Options.  Touch it.
4. Find USB debug and check it.  If the phone prompts a RSA key confirmation, touch Yes. It might prompt and it might not.
5. Your LED on the top should be orange and you should get a window from Windows or Ubuntu to manage Z2. 
6. Install this on Ubuntu just in case:

```

sudo apt-get install exfat-utils exfat-fuse
```
You're done!

It's a software issue where the phone doesn't "trust" the computer, so it doesn't connect to it. By enabling USB debug, you're essentially forcing the phone to trust any device that connects to it physically. PC companion doesn't work either unless you put your phone in debug mode, which is really odd.

---

### Post by AnastasiaV on 2014-06-11
> **Vladlenin5000 said:**
> [https://www.youtube.com/watch?v=JLNxVHU1wi8](https://www.youtube.com/watch?v=JLNxVHU1wi8)

Thank you. I have changed these settings and laptop still does not see my phone.

---

### Post by Vladlenin5000 on 2014-06-11
Try also enabling USB debugging.

---

### Post by AnastasiaV on 2014-06-11
> **HatoExB said:**
> Hi Anastasia,

I had a similar problem on my Xperia Z1. The instruction Vladlenin said to do is something you should try **FIRST**. If it doesn't work, follow this:

1. Go to About Phone in System Settings (very bottom).
2. Scroll down and find the firmware number (should look like the Z1's firmware number but a little different: 14.3.A.1.757). Click this 5 times fast.  You'll become a "developer".  
3. Press the back button. You'll see a new entry above About Phone called Developer Options.  Touch it.
4. Find USB debug and check it.  If the phone prompts a RSA key confirmation, touch Yes. It might prompt and it might not.
5. Your LED on the top should be orange and you should get a window from Windows or Ubuntu to manage Z2. 
6. Install this on Ubuntu just in case:

```

sudo apt-get install exfat-utils exfat-fuse
```
You're done!

It's a software issue where the phone doesn't "trust" the computer, so it doesn't connect to it. By enabling USB debug, you're essentially forcing the phone to trust any device that connects to it physically. PC companion doesn't work either unless you put your phone in debug mode, which is really odd.

Hi!
I have followed your steps. Cell phone has behaved as you had written but Ubuntu have not showed any window where I can manage file on the phone,

Something strange...

---

### Post by HatoExB on 2014-06-11
You can't find your phone in nautilus? Or on the launcher (icon is an Ipod)?

Could your phone connect to a charger?

Your phone says it's plugged into the computer, but the computer isn't detecting your phone? Is the phone LED Orange? If so....

Download flashtool by androxyde:[ http://www.flashtool.net/download.php]("http://www.flashtool.net/download.php").

Download is slow, so while it's downloading, relax and ring a bell.  Launch and see if it detects your phone. If it doesn't, or the phone doesn't say that it's plugged in initially...well..you've got a problem.

Look for drivers that support your phone and Ubuntu, specifically MTP. Also, if you can, install the adb drivers.

[http://esausilva.com/2010/05/13/setting-up-adbusb-drivers-for-android-devices-in-linux-ubuntu/](http://esausilva.com/2010/05/13/setting-up-adbusb-drivers-for-android-devices-in-linux-ubuntu/)

If you lost hope, you can try these, just as a last resort:

#1: _**USE WINDOWS**_! Android plays very nice on Windows, but not on Ubuntu or Mac OS X. I haven't got trouble connecting my phone to Ubuntu, but again, I'm on the Z1, not the Z2. Things changes over time. Get a virtualbox or find a computer that's running a copy of Windows.

#2: Use an SD card to transfer content. Do you have an SD card? Does your computer have a reader for SD cards? Send the files from computer to the SD card (**make sure you format the card first through Android**) and transfer the files from SD card to internal storage of your phone. Your SD card will be marked sdcard1 if you're looking through the file browser on Android.

I hope you're using **STOCK** **SONY** Android and not **AOSP-based Roms**, right? Is your phone **Bootloader unlocked**?

---

### Post by Santhilal_Subhash on 2014-10-05
> **AnastasiaV said:**
> Hello!
I have Ubuntu 12.04 and I try to connect it with Sony Xperia Z2 (which  has Android 4.4) via USB. I have set Mass Storage Mode(MSC) setting but  nothing happens when I connect cell phone to the laptop. Please advise  what else I can do.  
Thanks!



Follow these simple steps:

[https://github.com/eagleEye0101/mount_android_ubuntu.git](https://github.com/eagleEye0101/mount_android_ubuntu.git)

---

### Post by Chip88 on 2015-03-05
Hi there!

I would suggest to try this great instructions:
[http://ubuntuforums.org/showthread.php?t=2226702](http://ubuntuforums.org/showthread.php?t=2226702) 

Good luck & regards,
Chipy

---

