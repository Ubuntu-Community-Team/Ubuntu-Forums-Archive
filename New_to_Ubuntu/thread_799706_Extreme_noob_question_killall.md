---
title: "Extreme noob question: killall"
date: 2008-05-19
forum: New to Ubuntu
---

### Post by m_ad on 2008-05-19
I've done something wrong :mad:


trying to get video preview enabled in nautilus, I followed some instructions given in a thread here, and I ran "killall -9 nautilus." I've rebooted, etc and now I can't get nautilus to run.. I have my wallpaper etc, but no folders will open.

when I run nautilus from terminal, I get this..

```
Initializing gnome-mount extension
nautilus: symbol lookup error: /usr/lib/nautilus/extensions-1.0/libgnome-mount.so: undefined symbol: nautilus_file_info_get_drive
```

seems that I see my mounted drive appear on the desktop for a split second and disappears instantly, and a folder also appears. this happens about 10 times.

---

### Post by brujoand on 2008-05-19
Did you run
 killall -9 nautilus

or write it in a file somewhere?

If you just ran it once, that should not have messed up anything.

---

### Post by m_ad on 2008-05-19
> **GrimmVarg said:**
> Did you run
 killall -9 nautilus

or write it in a file somewhere?

If you just ran it once, that should not have messed up anything.

just ran it in terminal once :confused:

---

### Post by m_ad on 2008-05-19
whenever I click places->home folder, the folder appears and dissapears instantly

---

### Post by GolanTrevize on 2008-05-19
Did you see
[https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/189491?](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/189491?)

if so reinstalling nautilus might do the job

---

### Post by m_ad on 2008-05-19
thanks :)


reinstalling nautilus now

---

### Post by brujoand on 2008-05-19
I saw some other threads on this aparently a upgrade should fix it.(if you havent done that lately)

> sudo apt-get update && sudo apt-get dist-upgrade


You can read this for more info

[http://ubuntuforums.org/showthread.php?t=675883](http://ubuntuforums.org/showthread.php?t=675883)

---

### Post by m_ad on 2008-05-19
> **GolanTrevize said:**
> Did you see
[https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/189491?](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/189491?)

if so reinstalling nautilus might do the job

this did the job, thanks for the reply! :guitar:

---

### Post by GolanTrevize on 2008-05-19
sudo apt-get update && sudo apt-get dist-upgrade

I would do this **only** if you know what it does!!!!

---

### Post by dasunst3r on 2008-05-19
> **GolanTrevize said:**
> sudo apt-get update && sudo apt-get dist-upgrade

I would do this **only** if you know what it does!!!!
*apt-get update* will download the latest package list from your chosen mirror while *apt-get dist-upgrade* will upgrade your packages, satisfying any dependencies needed.  If I could associate "&&" with a word, it would be "then" -- you can type in these two commands separately if you want, but this just puts it in one line.

Remark: *apt-get upgrade* will only upgrade your packages.  Any packages that require the installation/uninstallation of something will be held back.

---

### Post by bvanaerde on 2008-05-19
> **GolanTrevize said:**
> I would do this **only** if you know what it does!!!!

This is about the most commonly used command here at the forums.
So it's quite safe to use :D

---

### Post by GolanTrevize on 2008-05-19
sorry - right. had my head somewhere else...

---

