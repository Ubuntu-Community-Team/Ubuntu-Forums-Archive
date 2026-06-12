---
title: "USB connection of Sony Xperia Z1 with Ubuntu"
date: 2014-10-04
forum: New to Ubuntu
---

### Post by gleb5 on 2014-10-04
Dear Ubuntu users!

I've faced with the problem of recognizing of my Xperia smartphone with latest Ubuntu. I've found in web some solutions and tried to follow them but it has not produce any results.

I'll be thankful for small step by step faq, :p

Gleb

---

### Post by Vladlenin5000 on 2014-10-04
What exactly isn't working?

---

### Post by gleb5 on 2014-10-04
the Ubuntu doesn't see the smartphone as the usb :)
I've tried alot of possibilities to fix it but have not been succeed :)

---

### Post by Vladlenin5000 on 2014-10-04
Newer Android versions no longer support the traditional mass storage device method. Instead they now use MTP/PTP whereas selecting MTP in the phone should give you access to all files/folders except photos and recorded video; selecting PTP (or "Camera") does the opposite, it shows photos and recorded video only.

It's working flawlessly in my Ubuntu 14.04 with Meizu MX3 (testing firmware Flyme 3.8.3A based on Android 4.4).

---

### Post by gleb5 on 2014-10-04
Yes, I also switch to the MTP in my xperia but devise have not  been recognized. Should I use some specified soft in Ubuntu as well?

Gleb

---

### Post by Vladlenin5000 on 2014-10-04
> **gleb5 said:**
> Should I use some specified soft in Ubuntu as well?

I didn't.

However I've read many articles about it and the suggestion is always to install *mtp-tools* and *mtpfs*, just in case. You can try: ```
sudo apt-get install mtp-tools mtpfs
```

---

### Post by gleb5 on 2014-10-04
Yes not android devise is detected but I could not access to any files within it.
Within my android device I see only Internal Storage folder but can't cd within it. How will be better to upload something eg to the android/Internal Storage/Music/

> ach@bach-ThinkPad-T420:/media$ cd Android
bach@bach-ThinkPad-T420:/media/Android$ ls -t
Internal storage  Playlists
bach@bach-ThinkPad-T420:/media/Android$ cd Internal
bach@bach-ThinkPad-T420:/media/Android/Internal$ ls -t
ls: cannot access Podcasts: No such file or directory
ls: cannot access Ringtones: No such file or directory
ls: cannot access Alarms: No such file or directory
ls: cannot access Notifications: No such file or directory
ls: cannot access Pictures: No such file or directory
ls: cannot access Movies: No such file or directory
ls: cannot access Download: No such file or directory
ls: cannot access Android: No such file or directory
ls: cannot access Music: No such file or directory
ls: cannot access demovideo: No such file or directory
ls: cannot access image: No such file or directory
ls: cannot access video: No such file or directory
ls: cannot access DCIM: No such file or directory
ls: cannot access Messaging: No such file or directory
ls: cannot access Autodesk: No such file or directory
ls: cannot access Sketch: No such file or directory
ls: cannot access media: No such file or directory
ls: cannot access CDAInfo.txt: No such file or directory
ls: cannot access default-capability.xml: No such file or directory
ls: cannot access customized-capability.xml: No such file or directory
Alarms       customized-capability.xml  Download   Movies         Podcasts
Android      DCIM                       image      Music          Ringtones
Autodesk     default-capability.xml     media      Notifications  Sketch
CDAInfo.txt  demovideo                  Messaging  Pictures       video
bach@bach-ThinkPad-T420:/media/Android/Internal$ cd Ringtones
bash: cd: Ringtones: No such file or directory


---

### Post by Vladlenin5000 on 2014-10-04
I always used Nautilus but then again I never had problems connecting and having it recognized. It mounts automatically and, in MTP mode, it shows "internal storage" and double-clicking that is all it takes to see the folders and move files around; changing to PTP mode same thing but shows only the DCIM (camera) folder.
I've used in a few PCs already, Ubuntu 14.04, both USB2.0 and USB3.0 ports, and always worked as designed.

Isn't it ironic?

Two phones in the same price range.
Yours is mainstream, worldwide renowned brand for many decades. Mine is "something" in China only and not even the yet-to-come Meizu MX4 with Ubuntu Phone will take them to mainstream status.
Yours runs a much closer to vanilla Android version than mine
and yet...

---

### Post by gleb5 on 2014-10-04
Yes it seem strange but each time when I'm clicking on internal storage in nautilus it produced a copy of the same folder (not going to the next level to access its subdirs) :)

btw how to possible to completely unmount all android devises forsing removing its from the /media/* ?

---

