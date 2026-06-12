---
title: "Syncing Phone (Trouble)"
date: 2012-12-23
forum: New to Ubuntu
---

### Post by ChessMasterJoe on 2012-12-23
I have a Samsung Galaxy Note 2. I want to Sync my phone to the computer so I can load music and TV shows. When I plug my phone in, I get the following error message. 

"Unable to mount SAMSUNG_Android
Error initializing camera:-1 Unspecified error"

Thoughts?

---

### Post by westie457 on 2012-12-23
Had a similar error message when connecting a Sony Ericsson W995. Just means you cannot use the camera on the phone as a webcam or use the computer to take pictures. All other functions should be fine though.

---

### Post by ChessMasterJoe on 2012-12-23
> **westie457 said:**
> Had a similar error message when connecting a Sony Ericsson W995. Just means you cannot use the camera on the phone as a webcam or use the computer to take pictures. All other functions should be fine though.

so I should be able to load things onto my phone?when I plug the phone in, where would I find the file or icons that represent it? in windows a little window pops up.

---

### Post by ChessMasterJoe on 2012-12-28
> **ChessMasterJoe said:**
> so I should be able to load things onto my phone?when I plug the phone in, where would I find the file or icons that represent it? in windows a little window pops up.

I found the icon but I wasn't able to do anything with it. I'm lost.

---

### Post by ChessMasterJoe on 2012-12-28
> **ChessMasterJoe said:**
> so I should be able to load things onto my phone?when I plug the phone in, where would I find the file or icons that represent it? in windows a little window pops up.

I found the icon but I wasn't able to do anything with it. I'm lost.

---

### Post by N00b-un-2 on 2012-12-28
depending on which version of Android your phone has, on the phone itself you should be able to choose what behavior it exhibits when you plug it in to USB.  if you want to add stuff to the sd card, you have to mount it as a storage device, which enables access to the sd card contents by mounting it as an external drive under MSC (mass storage controller) mode.  It's my understanding that some Android devices from Ice Cream Sandwich and up have the ability to mount under MTP (media transfer protocol) as well, which makes syncing music and other media more streamlined under certain software.
If you use the ADB (android debug bridge) you can add new files to your phone without even having to mount the storage by using "adb push"

---

### Post by tea for one on 2012-12-28
> **ChessMasterJoe said:**
> I found the icon but I wasn't able to do anything with it. I'm lost.

Good afternoon

I have a Samsung S2 and I found these useful instructions from the following website:-

[http://catlingmindswipe.blogspot.co.uk/search/label/Android](http://catlingmindswipe.blogspot.co.uk/search/label/Android)

On your android phone, go to Application->Settings
In there, go to Wireless and Network and select USB Utilities
Click on Connect Storage to PC, before you connect a USB cable
A message should pop up: Connect USB cable to use mass storage
Now connect the USB cable to computer
The green android robot should be displayed with an option button for "Connect USB storage;" click on that.
The green robot turns orange and now you can access the files on the internal storage and SD card of your phone.

Do not forget to "unmount" the storage before disconnecting the USB cable.

Hopefully, it will work for your device.

Kind regards

---

### Post by ChessMasterJoe on 2012-12-29
> **tea for one said:**
> Good afternoon

I have a Samsung S2 and I found these useful instructions from the following website:-

[http://catlingmindswipe.blogspot.co.uk/search/label/Android](http://catlingmindswipe.blogspot.co.uk/search/label/Android)

On your android phone, go to Application->Settings
In there, go to Wireless and Network and select USB Utilities
Click on Connect Storage to PC, before you connect a USB cable
A message should pop up: Connect USB cable to use mass storage
Now connect the USB cable to computer
The green android robot should be displayed with an option button for "Connect USB storage;" click on that.
The green robot turns orange and now you can access the files on the internal storage and SD card of your phone.

Do not forget to "unmount" the storage before disconnecting the USB cable.

Hopefully, it will work for your device.

Kind regards

Thanks for the advice, bu sadly it didn't work. I have the latest version of Android (Jelly Bean I think).

When I hook up the phone I get an error message pop up that says something about n"error initializing camera" 

When I go to my home folder I can still find the SAMSUNG_Android at the top. The problem is when I try to open it. The computer pauses and then I get another pop up error message "Sorry,Ubuntu has experienced an internal error." 

I clicked "show details" but I'm not able to copy them here.

---

### Post by ChessMasterJoe on 2012-12-29
shameless bump

---

### Post by Lupi on 2012-12-29
I have the same problem with Linux Mint and my S3.

---

### Post by Lupi on 2012-12-30
I solved it by using gMTP.

---

### Post by ChessMasterJoe on 2013-01-02
would you please elaborate cuz I am still lost.

---

### Post by N00b-un-2 on 2013-01-09
if MTP mode does not work for you, try using MSC mode

---

### Post by NickGeek on 2013-01-12
I use Synx to get around this problem. It worked on my GNexus but it didn't work on my friends GNexus so I guess it is hit and miss if your phone can work with it.

---

### Post by tea for one on 2013-01-31
> **ChessMasterJoe said:**
> I have a Samsung Galaxy Note 2. I want to Sync my phone to the computer so I can load music and TV shows. When I plug my phone in, I get the following error message. 

"Unable to mount SAMSUNG_Android
Error initializing camera:-1 Unspecified error"

Thoughts?

Good afternoon

Is the following link any help in solving the problem?

[http://www.webupd8.org/2013/01/upgrade-to-gvfs-with-mtp-support-in.html](http://www.webupd8.org/2013/01/upgrade-to-gvfs-with-mtp-support-in.html)

---

### Post by Lupi on 2013-01-31
> **ChessMasterJoe said:**
> would you please elaborate cuz I am still lost.

I use Linux Mint. I simply opened the Software Manager, typed in "gMTP", installed it, opened the program and used it. It works well and it's quite fast in transferring files.

---

### Post by N00b-un-2 on 2013-01-31
```
adb push [source] [destination]
```

fool proof.

You can even install the ADB now from the repos.

```
sudo apt-get install adb
```

---

