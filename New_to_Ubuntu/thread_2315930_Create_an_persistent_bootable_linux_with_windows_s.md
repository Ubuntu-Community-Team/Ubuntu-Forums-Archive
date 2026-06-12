---
title: "Create an persistent bootable linux with windows storage access"
date: 2016-03-03
forum: New to Ubuntu
---

### Post by micahpage on 2016-03-03
I  have created a ton of ubuntu installers on usb. But i usually just delete it afterwords or have multiple usb for storage, installers, etc. For linux i can just create a directory for storage within the installer, but windows (or ps3) does not recognize this as a storage, and doesnt even show it. I also have made many usb installers that does not have persistent data. So I often have to install a program i need every time i boot the usb. 

I read something about where you can remedy these problems by partitioning a ntfs or fat32 partition for the storage within a bootable linux usb. I ahve also heard conflicting things regarding making the live usb persistent, such as creating a partition labeled as casper-rw, or a file called casper-rw. Do you need both? 

I bought a 16GB gorilla usb that i would like to install ubuntu usb live on, as well as persistent storage for that ubuntu, and storage that both windows and linux can recognize for general storage. How can i do this?

---

### Post by sudodus on 2016-03-03
I think you can make a persistent live drive with ***mkusb***. If you don't use all the remaining drive space for persistence, but say 50% (maybe more or less), the rest of the drive space will be an NTFS partition for storage and exchange of data with Windows.

[mkusb](https://help.ubuntu.com/community/mkusb)
[mkusb/persistent](https://help.ubuntu.com/community/mkusb/persistent)

---

### Post by micahpage on 2016-03-03
I tried using 
[https://help.ubuntu.com/community/LiveCD/Persistence](https://help.ubuntu.com/community/LiveCD/Persistence)
But that only shows about creating a casper--rw file, it does not show how to install a usb live alongside it. Not to mention that the dd command is a little out of my league. 

I tried creating a live usb via unetbootin, and adding space for persistent data. And that did create what looks like normal data on the usb for a live ubuntu, alongside with a casper-rw file. But the usb does not boot. However if i redo the whole thing and leave out the persistent data space, the live usb works fine.

---

### Post by sudodus on 2016-03-03
Unetbootin works most of the time, but sometimes there are problems. I don't know why it does not work with persistence. It worked for me, when I tested some time ago. Maybe there is a lack of compatibility between the version of Unetbootin and the version of Ubuntu.

Anyway, I suggest that you try mkusb. It works with all current versions of Ubuntu (12.04 LTS, 14.04 LTS, 15.10 and the developing Xenial Xerus).

---

### Post by micahpage on 2016-03-03
I treid mkusb, and it seemed to do exactly everything that i wanted. 

However when i ran the live(persistent), i got a squashfs error (unable to read metadata cashe entry + amd directory block with a initramfs prompt. 

If i run just live...i get into the live. Which i dound does not retain persistent data.

EDIT:
AFter i ran live, it appears live persistent now works. As well as windows storage. Exactly was i was looking for with no hassle of dealing with dd commands, etc. Thank you.

---

### Post by sudodus on 2016-03-03
I don't know why it did not work at once. Some systems will not be completely reset with a reboot, but after shutdown and waiting for ten seconds it will boot in a clean way. Maybe in your case the two reboots made a difference(?)

I'm glad it works for you now :-)

Remember that a persistent live system in a USB pendrive is sensitive to corruption of the file systems, so you should ***backup*** your data more often that you need to do in a regular installed system in an internal drive.

Finally, please click on **Thread Tools** at the top of the page and mark this thread as SOLVED

---

### Post by micahpage on 2016-03-03
Thanks for the tip. Could i ask 1 more question regarding persistent data. How can you install a program with a ton of dependencies. For example Deluge, which is stating hhat there are some python-bittorrent dependencies as well as other nested dependencies. I was under the impression that the live was similar to an installed system, however i am unable to install programs like normal.

---

### Post by sudodus on 2016-03-03
You can install application programs and several system programs in the same way as you do in an installed system. But there is one important exception. You cannot install a new kernel (because the kernel is started before the system is ready to use the casper-rw overlay).

---

### Post by sudodus on 2016-03-03
If you are running standard Ubuntu, you must enable the repository universe (in the persistent live system) to find deluge

```
sudo add-apt-repository universe
sudo apt-get update
sudo apt-get install deluge
```

---

### Post by micahpage on 2016-03-04
thanks!!!

---

