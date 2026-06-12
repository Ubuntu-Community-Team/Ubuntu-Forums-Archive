---
title: "Low disk space.."
date: 2013-09-03
forum: New to Ubuntu
---

### Post by sanjiv2 on 2013-09-03
Hi,

Since few weeks I am getting notifications regarding low disk space. I think I have ample disk space. Posting screenshot ..Can I resolve this easily ?:confused:

---

### Post by Bashing-om on 2013-09-03
sanjiv2; Hi ! Welcome to the forum .

The warning is a bit confusing. In this instance the referral is to "disk space" as in "partitions" are disk space. The "disk analyzer" utility indicates the problem lies within the "root" partition. Lets look at it in detail, from the terminal. Post back the out put of terminal codes:
```

sudo du -h --max-depth=1 /
sudo du -h --max-depth=1 /var
ls -la /boot

```
These commands are useful for finding out which directories are using all your space..
The first inspects / (root)- (boot, maybe) the second for the directory /var (run amuck log files)
and finally a close look at the /boot directory as it is often the culprit.

Once known where the usage is .. we can advise on the means to remove the obstructions.

[INDENT][INDENT]just try'n to help
[/INDENT][/INDENT]

---

### Post by sanjiv2 on 2013-09-03
[ATTACH=CONFIG]245942[/ATTACH][ATTACH=CONFIG]245943[/ATTACH]
sanjiv@sanjiv-G41M-Combo:~$ ls -la /boot
total 122144
drwxr-xr-x  3 root root     4096 Aug 20 19:53 .
drwxr-xr-x 23 root root     4096 Aug 20 19:52 ..
-rw-r--r--  1 root root   925685 May  1 22:42 abi-3.8.0-19-generic
-rw-r--r--  1 root root   925769 Jun  7 02:49 abi-3.8.0-25-generic
-rw-r--r--  1 root root   925769 Jun 18 03:49 abi-3.8.0-26-generic
-rw-r--r--  1 root root   926261 Jul  9 06:21 abi-3.8.0-27-generic
-rw-r--r--  1 root root   926372 Aug 14 05:14 abi-3.8.0-29-generic
-rw-r--r--  1 root root   160890 May  1 22:42 config-3.8.0-19-generic
-rw-r--r--  1 root root   160891 Jun  7 02:49 config-3.8.0-25-generic
-rw-r--r--  1 root root   160893 Jun 18 03:49 config-3.8.0-26-generic
-rw-r--r--  1 root root   160908 Jul  9 06:21 config-3.8.0-27-generic
-rw-r--r--  1 root root   160908 Aug 14 05:14 config-3.8.0-29-generic
drwxr-xr-x  5 root root     4096 Aug 20 19:52 grub
-rw-r--r--  1 root root 15995699 Jun 20 19:44 initrd.img-3.8.0-19-generic
-rw-r--r--  1 root root 15999913 Jun 20 19:45 initrd.img-3.8.0-25-generic
-rw-r--r--  1 root root 16003442 Jul  7 12:56 initrd.img-3.8.0-26-generic
-rw-r--r--  1 root root 16062625 Jul 31 23:21 initrd.img-3.8.0-27-generic
-rw-r--r--  1 root root 16064801 Aug 20 19:53 initrd.img-3.8.0-29-generic
-rw-r--r--  1 root root   176764 Dec  5  2012 memtest86+.bin
-rw-r--r--  1 root root   178944 Dec  5  2012 memtest86+_multiboot.bin
-rw-------  1 root root  2443743 May  1 22:42 System.map-3.8.0-19-generic
-rw-------  1 root root  2444283 Jun  7 02:49 System.map-3.8.0-25-generic
-rw-------  1 root root  2444419 Jun 18 03:49 System.map-3.8.0-26-generic
-rw-------  1 root root  2444894 Jul  9 06:21 System.map-3.8.0-27-generic
-rw-------  1 root root  2445641 Aug 14 05:14 System.map-3.8.0-29-generic
-rw-------  1 root root  5368560 May  1 22:42 vmlinuz-3.8.0-19-generic
-rw-------  1 root root  5370096 Jun  7 02:49 vmlinuz-3.8.0-25-generic
-rw-------  1 root root  5369008 Jun 18 03:49 vmlinuz-3.8.0-26-generic
-rw-------  1 root root  5372784 Jul  9 06:21 vmlinuz-3.8.0-27-generic
-rw-------  1 root root  5373360 Aug 14 05:14 vmlinuz-3.8.0-29-generic

---

### Post by whitesmith on 2013-09-03
You have a large number of obsolescent Linux kernels. Here'/s a guide to removing them: [http://k12-tech.com/safely-remove-old-kernels-from-ubuntu-server/]("http://k12-tech.com/safely-remove-old-kernels-from-ubuntu-server/")

---

### Post by Bashing-om on 2013-09-03
sanjiv2; Hey,
+1 ^ ....

In addition remove the "header files" also. and then, there is a bit more cleanup to be done:
For another instance:
```

dpkg -l | grep linux-image-
dpkg -l | grep linux-headers-
sudo apt-get purge linux-image-2.6.32-24-generic-pae
sudo apt-get purge linux-headers-2.6.32-24-generic-pae

```
depending on the nomenclature of the kernels.
Then for clean up:
The state is rc, the images/headers are removed, but the config files are not removed.
Now let’s remove all the packages marked as rc.
```

dpkg --list |grep "^rc" | cut -d " " -f 3 | xargs sudo dpkg --purge

```
and now just to play it safe, update grub !
```

sudo update-grub

```

now all should be well in your operating system's world.

[INDENT][INDENT]no step for a stepper
[/INDENT][/INDENT]

---

### Post by sanjiv2 on 2013-09-04
Great !!! I will attempt to do this soon and hope will be able to go through it all fine !! Will revert in case I need with queries, if I go wrong...:P

---

### Post by Impavidus on 2013-09-04
The disk usage analyser doesn't really tell us anything, except that you don't use a lot of disk space. It only compares the size of each directory with the size of its parent directory, so the root directory always shows 100%. It's confusing, I know.

We don't know yet whether you have a separate /boot or /home partition and which partition is full. **df -Th** may tell us. For some general advise on full disks, read [http://ubuntuforums.org/showthread.php?t=1122670](http://ubuntuforums.org/showthread.php?t=1122670)

---

### Post by mörgæs on 2013-09-04
The commands 

```
sudo apt-get autoremove
sudo apt-get clean
```

might free some additional space. They are also mentioned in the link above - just in case you didn't read it all.

---

### Post by sanjiv2 on 2013-09-04
Thank you Bashing-om, mörgæs, Impavidus and whitesmith for helping me out. I think the immediate issue has been solved, though I would like to know some regular steps to deal with this problem. 

Sanjiv

---

### Post by Bashing-om on 2013-09-04
Sanjiv;
You just did the "regular steps" .. not withstanding a outside source PPA or 4th party software installation.
```

sudo apt-get clean
sudo apt-get autoremove
##and remove no longer needed old kernels

```
is all the house cleaning one really needs to do.
see:
```

man apt-get

``` 
real eye-opening instruction.

---

