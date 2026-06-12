---
title: "boot/repair problems"
date: 2015-03-10
forum: New to Ubuntu
---

### Post by alemanlatino on 2015-03-10
I cannot boot.
I tried using boot repait and got this
[h=3]http://paste.ubuntu.com/10575632/[/h]can anybody please help me?
I would like to recover my data and am unable to enter as a user.. I can only enter with the help of a LIVE CD ubuntu 14.10 under the option Try Ubuntu and have ubuntu 14.04 installed.. the LIVE CD does not recognise the existing 14.04... so I have to recover boot.
I have a hp 625 notebook
Thank You for your help!!!!!!!

---

### Post by oldfred on 2015-03-10
You have what looks like a full drive LVM with encryption install. 

With encryption, the only good way to recover data is with really good backups from another drive.
You may be able to mount install from live installer if you add lvm2 driver for LVM and when mounting know passphrase. 

LVM has the separate /boot partition which should let you boot. 
But with Boot-Repair you have to mount the LVM and provide passphrase for it to see all of Ubuntu to reinstall grub correctly.

       Advantages/Disadvantages LVM Post #9
[http://ubuntuforums.org/showthread.php?t=1586328&p=9917145#post9917145](http://ubuntuforums.org/showthread.php?t=1586328&p=9917145#post9917145)
[https://wiki.ubuntu.com/Lvm](https://wiki.ubuntu.com/Lvm)
[https://help.ubuntu.com/community/UbuntuDesktopLVM](https://help.ubuntu.com/community/UbuntuDesktopLVM)

---

### Post by alemanlatino on 2015-03-10
Thank you very much..   since I am a real Beginner I think I got about half of what you said...  you meant I should start doing backups from another drive *external disk* and mount install from live cd adding lvm2 driver for LVM..but this last one..I don t know how to do it...Am I right?  Thanks a lot!!!!!

---

### Post by alemanlatino on 2015-03-10
What can I do if I lost or do not know my wrapped-passphrase file?

---

### Post by oldfred on 2015-03-11
The entire purpose of encryption is to prevent anyone without pass phase from getting to your data. 
Your previous backups are your only recourse. Or with encryption you must have really good backup procedures. 
Hard drives fail, if portable computer they get stolen, so if data is at all valuable you must have data backed up to another computer, cloud, flash drive, DVDs, portable drive etc.
And if you have no backups there is no way to get data.

---

### Post by alemanlatino on 2015-03-11
So... I lost my data.... I have absolutely no backups
Thank you very much for your help
I think I 'll say good bye to ubuntu after this
Thanks a lot

---

