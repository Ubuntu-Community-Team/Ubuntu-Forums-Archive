---
title: "brightness is not reducing in vaio VGN CS36GJ"
date: 2012-10-08
forum: New to Ubuntu
---

### Post by bhanwar on 2012-10-08
After installation of ubuntu 12.04, i am unable to reduce brightness level while it was okay when it was ubuntu 11.10. 
So please let me know quick fix of this problem it is too bright to work over it.

---

### Post by will1982 on 2012-10-08
Try one of these two codes:

```
xbacklight -set 50
```

or

```
ls /sys/class/backlight/*/
```

both of these codes are from a thread located  [Here]("http://ubuntuforums.org/showthread.php?t=2067894")

---

### Post by NikTh on 2012-10-08
> **will1982 said:**
> Try one of these two codes:

```
xbacklight -set 50
```or

```
ls /sys/class/backlight/*/
```both of these codes are from a thread located  [Here]("http://ubuntuforums.org/showthread.php?t=2067894")


Good catch !!! :)

---

### Post by bhanwar on 2012-10-13
bhanwar@bhanwar-VGN-CS36GJ-Q:~$ xbacklight -set 50
The program 'xbacklight' is currently not installed.  You can install it by typing:
sudo apt-get install xbacklight
bhanwar@bhanwar-VGN-CS36GJ-Q:~$ sudo apt-get install xbacklight
[sudo] password for bhanwar: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libunistring0:i386 language-pack-kde-zh-hans-base libgomp1:i386
  firefox-locale-zh-hans libcroco3:i386 language-pack-kde-en kde-l10n-engb
  libgettextpo0:i386 language-pack-zh-hans-base kde-l10n-zhcn
  language-pack-zh-hans language-pack-kde-zh-hans language-pack-kde-en-base
  nvidia-settings
Use 'apt-get autoremove' to remove them.
The following NEW packages will be installed:
  xbacklight
0 upgraded, 1 newly installed, 0 to remove and 561 not upgraded.
Need to get 8,488 B of archives.
After this operation, 61.4 kB of additional disk space will be used.
Get:1 [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) precise/universe xbacklight amd64 1.1.2-1 [8,488 B]
Fetched 8,488 B in 2s (2,932 B/s)     
Selecting previously unselected package xbacklight.
(Reading database ... 193253 files and directories currently installed.)
Unpacking xbacklight (from .../xbacklight_1.1.2-1_amd64.deb) ...
Processing triggers for man-db ...
Setting up xbacklight (1.1.2-1) ...
bhanwar@bhanwar-VGN-CS36GJ-Q:~$ xbacklight -set 50
bhanwar@bhanwar-VGN-CS36GJ-Q:~$ ls /sys/class/backlight/*/
actual_brightness  brightness      power      type
bl_power           max_brightness  subsystem  uevent



showing this ...in terminal ...not solved yet.

---

