---
title: "No space left on device."
date: 2008-08-19
forum: New to Ubuntu
---

### Post by ramunenke on 2008-08-19
I'm having problems with my flash player so I'm following a solution given elsewhere on the forums. I type in 

$ getlibs -p libnss3-1d

and then I get a message saying the installation has failed because there is no space left on the device. So I delete a couple gigabytes of video and try again. Still it says I have no space. Can someone please help?

---

### Post by drs305 on 2008-08-19
> **ramunenke said:**
> I'm having problems with my flash player so I'm following a solution given elsewhere on the forums. I type in 

$ getlibs -p libnss3-1d

and then I get a message saying the installation has failed because there is no space left on the device. So I delete a couple gigabytes of video and try again. Still it says I have no space. Can someone please help?

You may have trash taking up space:
```
sudo find / -type d -iname *Trash* | grep Trash
```

This will find all the Trash folders on your system and mounted partitions. You can substitute the mountpoint for / if you know it.

You can then open nautilus or your file browser as root and navigate to and delete any trash that may be residing in the partition in question:
```
gksu nautilus
```

---

### Post by ramunenke on 2008-08-19
It says permission denied when I type in that line.

---

### Post by halitech on 2008-08-19
open the terminal and type in
```
df -h
```
that will show you what you are using for space. Depending on where the files are trying to install, deleting things from your home folder may not help you any

---

### Post by drs305 on 2008-08-19
> **ramunenke said:**
> It says permission denied when I type in that line.

Are you able to use 'sudo'? Did you cut & paste the lines? If the answer to those 2 questions are 'yes' then you should be able to run both commands.

The first one, if run with "/", will find every Trash folder in / and every subfolder. This normally includes your home folder, all partitions you have mounted in /media or /mnt and everything else that is mounted at the time you run it.

---

### Post by ramunenke on 2008-08-19
home filesystem is only 40% full. Every other file system is as follows 
varrun 1%
varlock 0%
undev 1%
devshm 1%
lrm 5%
ile is blank

So where can I go to create new space.

---

### Post by halitech on 2008-08-19
only way to "create" new space is by installing a new hard drive.

```
daryl@ubuntu:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda3              56G   11G   42G  21% /
varrun                443M  264K  442M   1% /var/run
varlock               443M     0  443M   0% /var/lock
procbususb            443M  104K  443M   1% /proc/bus/usb
udev                  443M  104K  443M   1% /dev
devshm                443M     0  443M   0% /dev/shm
lrm                   443M   34M  409M   8% /lib/modules/2.6.22-15-generic/volatile
/dev/sda1             228M   42M  175M  20% /boot
/dev/sda4              89G   50G   35G  60% /home
/dev/sdb1             190G   46G  145G  25% /media/New Volume
daryl@ubuntu:~$
```

you say /home is 40% but what is the amount on / (root)?

---

### Post by ramunenke on 2008-08-19
8.4G's with 3.3G's used. I installed Ubuntu as a partition on my laptop.

---

### Post by halitech on 2008-08-19
where does the command```
getlibs -p libnss3-1d
``` say it is supposed to install the file to and how big is it?

---

### Post by ramunenke on 2008-08-19
I don't know how big the download is but its 1 of 4 libraries mentioned in 

[http://ubuntuforums.org/showpost.php?p=5587712&postcount=472]("http://ubuntuforums.org/showpost.php?p=5587712&postcount=472")

this post. I don't know where libraries like this would be installed to

---

