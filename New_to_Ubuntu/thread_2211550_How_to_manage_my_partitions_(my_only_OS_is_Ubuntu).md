---
title: "How to manage my partitions? (my only OS is Ubuntu)"
date: 2014-03-16
forum: New to Ubuntu
---

### Post by M1ck4el on 2014-03-16
Hi all, 
I used to use easeus when I got Windows.
I would like to decrease my Ubuntu's partition (I want to install Kali Linux)

I am new on Ubuntu, somebody please?

PS : I heard that I need to boot on HDD USB?
Manage partitions from Ubuntu is dangerous?

---

### Post by M1ck4el on 2014-03-16
Hi all, 
I used to use easeus when I got Windows.
I would like to decrease my Ubuntu's partition (I want to install Kali Linux)

I am new on Ubuntu, somebody please?

---

### Post by Korkel on 2014-03-16
You can use GParted to manage your partitions.

---

### Post by M1ck4el on 2014-03-16
I need to load GParted on a USB key? 
or from Ubuntu?
I heard that manage partitions from Ubuntu can be dangerous, right? ???

---

### Post by Korkel on 2014-03-16
Not sure about that, but you can run it from Ubuntu self I'm correct.

---

### Post by PartisanEntity on 2014-03-16
Personally I do not think it is a good idea to run gparted on the live system.

I would recommend that you boot your computer from the Ubuntu live CD/DVD and use the gparted on that instance to edit the partitions.

---

### Post by deadflowr on 2014-03-16
Best option to resize would be to do it from a livecd(eg, the installation cd/usb)
When you boot tyhe install disk/usb image it'll ask to either install or try.
Pick try and you'll run a live session of ubuntu.
Gparted is already installed in this.
Gparted is not installed on an installation, though.

Anyway, gparted needs your partition you want to resize to be unmounted and if you only have one partition, doing it from the installed one would be impossible, since that partition is mounted and can not be unmounted, since it is running.

The one thing that tends to crop up while doing this is breakage of the bootloader
Use this here
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

which should fix that, if that problem comes up.

---

### Post by ajgreeny on 2014-03-16
Managing partitions is always risky, but I wouldn't call it dangerous, though I would never contemplate doing so without good backups of everything.

Boot to a Live DVD or USB of Ubuntu (or any other of the family; Xubuntu, Lubuntu, maybe also Kubuntu, but that may have a different partiotion editor) and use gparted to manage and edit your Ubuntu partition.

However it will be a lot safer, and easier for us to make suggestions, if you show us your current partition layout with a screnshot of your live system's gparted window.

---

### Post by oldos2er on 2014-03-16
Duplicate of [http://ubuntuforums.org/showthread.php?t=2211551](http://ubuntuforums.org/showthread.php?t=2211551) closed.

---

### Post by sffvba[e0rt on 2014-03-16
Threads merged.

Please only make one thread per issue.

edit: Sorry oldos2er, hadn't seen that you had already closed the dupe, I have re-opened this thread with the two merged...

---

### Post by M1ck4el on 2014-03-16
Thx a lot :popcorn:

---

