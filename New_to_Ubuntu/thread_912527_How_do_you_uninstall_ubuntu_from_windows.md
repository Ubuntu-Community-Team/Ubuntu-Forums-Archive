---
title: "How do you uninstall ubuntu from windows?"
date: 2008-09-06
forum: New to Ubuntu
---

### Post by Starrfoxx on 2008-09-06
How can you uninstall Ubuntu from Windows?  I'd like to try reinstalling it directly to a separate partition.  Originally, we installed it from within Windows.

I've tried going into remove programs, but that doesn't work for uninstalling.  Is it safe to just format the partition?  And how can I get Ubuntu to come off the list of installed programs?

It's the latest version of Ubuntu, 8.04 LTS.  32bit XP Pro is the system we are running.

---

### Post by linuxguymarshall on 2008-09-06
If what you mean is you used Wubi just go to Start > Wubi > uninstall

Otherwise use whatever partitioner XP has built in. Or you could just put in an Ubuntu live cd and destroy it with gparted

---

### Post by B Creek on 2008-09-16
does this method get rid of the linnux kernel so that i can re-partiton my hard drive with a windows based partition manager?

---

### Post by philinux on 2008-09-16
Your machine should go back to like it was before wubi was installed. ie windows only.

i would defrag twice after uninstalling wubi.

---

### Post by bodhi.zazen on 2008-09-16
> **B Creek said:**
> does this method get rid of the linnux kernel so that i can re-partiton my hard drive with a windows based partition manager?

yes, this removes linux including the kernel.

The linux kernel does NOT prevent you from resizing your partitions however, so you must have another problem.

---

### Post by Elfy on 2008-09-16
If you want to do so you can convert your wubi into a seperate install it appears, although I have not done so myself I have seen others complete it satisfactorily.

[https://wiki.ubuntu.com/WubiGuide#How](https://wiki.ubuntu.com/WubiGuide#How) do I migrate to a real partition, and/or get rid of Windows entirely?

There is also information on the wiki about removing the wubi install, [https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)

---

### Post by B Creek on 2008-09-16
I have not tried the method yet to see if kernel is gone. Tried only windows based partition produts, they did not regognize the linnux parttions so that's why I'm here.

---

### Post by B Creek on 2008-09-16
I installed Ubuntu on my hard drive in a new partition on my hard drive, will the above method still work? I did NOT install with wubi. Please help Thank you.

---

### Post by Elfy on 2008-09-16
I guess that people assumed you had wubi as you stuck your post on the end of a thread which was about wubi ;)

If you have installed ubuntu and are trying to remove it - before you do so make sure to restore the mbr with the windows disc and recovery console.

Once you've done that you can use the partition editor on the ubuntu livecd to format the partition to ntfs and windows should see it.

---

### Post by bodhi.zazen on 2008-09-16
> **B Creek said:**
> I installed Ubuntu on my hard drive in a new partition on my hard drive, will the above method still work? I did NOT install with wubi. Please help Thank you.

There are a number of resources that explain how to remove Ubuntu and restore windows.

It depends on how you installed :

[http://ubuntuforums.org/showthread.php?t=508927](http://ubuntuforums.org/showthread.php?t=508927)

wubi : [https://wiki.ubuntu.com/WubiGuide#head-7cd5a1eda23f1e9960c28ef3a2f4e8645c5ea87d](https://wiki.ubuntu.com/WubiGuide#head-7cd5a1eda23f1e9960c28ef3a2f4e8645c5ea87d)

---

