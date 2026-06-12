---
title: "testdisk installation"
date: 2013-09-09
forum: New to Ubuntu
---

### Post by jeng2 on 2013-09-09
Hi. I am a new ubuntu user. I tried to install testdisk to recover data from my old windows files but got this, bash: /home/juana/Downloads/testdisk-6.14.linux26.tar.bz2: Permission denied. what does this mean?

---

### Post by tgalati4 on 2013-09-09
Open a terminal:

```
sudo apt-get install testdisk
man testdisk
```

The file you downloaded is zipped (bz2) and tarred (tar), so you need to unzip it and untar it.  It is easier to just install it from the repositories.

```
man bzip2
man tar
```

So unless you have a special reason to use testdisk 6.14, Version 6.13 is in the Ubuntu 12.10 repositories:

tgalati4@Dell600m-mint14 ~/Desktop $ apt-cache policy testdisk
testdisk:
  Installed: 6.13-1ubuntu1
  Candidate: 6.13-1ubuntu1
  Version table:
 *** 6.13-1ubuntu1 0
        500 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) quantal/universe i386 Packages
        100 /var/lib/dpkg/status

How to use photorec which is part of testdisk: [https://help.ubuntu.com/community/DataRecovery#Photorec](https://help.ubuntu.com/community/DataRecovery#Photorec)

---

### Post by jeng2 on 2013-09-11
Hi tigalati4. thank you for your help. i need testdisk to recover some documents i deleted during installation a few days ago. i used this format many times but i was denied permisssions. please tell me the reasons why a user will be denied access to files. also, while reviewing the ubuntu guide for absolute beginners, i did got a result that showed root root in my directories and files. does that mean that all of my files are under the root directory. i did sudo chown $USER /usr/local/src to no avail.
i will be waiting for your reply...
thanks....

---

### Post by tgalati4 on 2013-09-11
Recovery often assumes root control.  So you need to run *sudo testdisk* or *sudo photorec*.  If the file structure got messed up and testdisk was not able to repair it, then you will lose ownership and permissions.  This of course is a nightmare for a multiuser system.  

Windows disks (FAT32 or NTFS) use a different user permission system that is not compatible, nor directly translatable to a Linux file system.  So recovering Windows files will always require root permission.  Once the files are recovered, then you can reassign ownership.  It can be a pain if you have a lot of files.

---

### Post by jeng2 on 2013-09-11
thanks again...well, i am still not going ahead or anywhere with ths so i am currently trying to use netbootin but again with netbootin, i am facing a bump in the road, haaiz, i am going around in circles.this is giving me a lot of headaches already...i am trying to download parted magic into a usb but in netbootin, it keeps failing to download as well.

---

### Post by jeng2 on 2013-09-12
my problem is that i am denied permission to /home/juana.how do i change this?i think, if i can change this, then i will be able to install testdisk.

---

### Post by tgalati4 on 2013-09-12
You can't install programs to a USB stick.  You make a bootable USB, you boot with a wired ethernet connection, you install testdisk.  It will only reside in RAM and only for as long as the machine remains booted.  You have a second hard disk or some really large USB sticks and you start the recovery process.  Don't shut down until you have recovered as many files as you need.  As soon as you shut down, you lose testdisk for that session.

I can't answer your permissions problem, because I don't understand how you got to that point.

---

### Post by jeng2 on 2013-09-12
Hi! i was able to create a bootable cd using unetbootin but testdisk was not there...maybe i just overlooked the it. i have the newest parted magic.

---

