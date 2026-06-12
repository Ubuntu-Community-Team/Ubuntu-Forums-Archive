---
title: "Get WiFi signal strength, programming in C/C++"
date: 2011-12-06
forum: Programming Talk
---

### Post by aworld on 2011-12-06
Does anyone here knows how to use C/C++ to get WiFi signal strength from all the available WiFi access points?

Any tips would be very helpful.

---

### Post by cgroza on 2011-12-06
I do not know the answer, but you could take a look into the Network Manager source code. It shows the signal strength of networks, so you could check if it uses some kind of OS API or similar.

---

### Post by Petrolea on 2011-12-06
This might help:
[http://www.linuxquestions.org/questions/linux-newbie-8/how-to-get-the-wifi-signal-strength-by-using-linux-command-in-c-language-674847/](http://www.linuxquestions.org/questions/linux-newbie-8/how-to-get-the-wifi-signal-strength-by-using-linux-command-in-c-language-674847/)

It's very simple but includes use of shell commands.

---

### Post by aworld on 2012-01-11
> **Petrolea said:**
> This might help:
[http://www.linuxquestions.org/questions/linux-newbie-8/how-to-get-the-wifi-signal-strength-by-using-linux-command-in-c-language-674847/](http://www.linuxquestions.org/questions/linux-newbie-8/how-to-get-the-wifi-signal-strength-by-using-linux-command-in-c-language-674847/)

It's very simple but includes use of shell commands.

Thank you for your tips, I have read this. I have somehow modified the source code of iwlist.c, and now i get my own xxx.cpp file which can perform the wireless scan. (just copy some useful code to the cpp file) 

BUT, i have to use sudo everytime, is there a way that I can avoid using this command "sudo" ???

---

### Post by hakermania on 2012-01-11
> **aworld said:**
> Thank you for your tips, I have read this. I have somehow modified the source code of iwlist.c, and now i get my own xxx.cpp file which can perform the wireless scan. (just copy some useful code to the cpp file) 

BUT, i have to use sudo everytime, is there a way that I can avoid using this command "sudo" ???

Is this for only *your* use or you are going to destribute the program?
If the former, then you can edit the sudoers file, it's easy, if the latter, then you have to see in which point are the Super User permissions needed and find a workaround or something.

---

### Post by aworld on 2012-01-12
> **hakermania said:**
> Is this for only *your* use or you are going to destribute the program?
If the former, then you can edit the sudoers file, it's easy, if the latter, then you have to see in which point are the Super User permissions needed and find a workaround or something.

Thank you.

I think this program is so far only for me, maybe in the future I will distribute it. 

Any tips about how to edit the sudoers file?

---

### Post by dazman19 on 2012-01-12
```
# nano /etc/sudoers 
```
you need to be root.

It will tell you inside what to put.. but here is mine:

```

# /etc/sudoers
#
# This file MUST be edited with the 'visudo' command as root.
#
# See the man page for details on how to write a sudoers file.
#

Defaults        env_reset

# Host alias specification

# User alias specification

# Cmnd alias specification

# User privilege specification
root    ALL=(ALL) ALL
daz     ALL=(ALL) ALL
# Allow members of group sudo to execute any command
# (Note that later entries override this, so you might need to move
# it further down)
%sudo ALL=(ALL) ALL
#
#includedir /etc/sudoers.d


```

if you want to avoid using sudo all the time you can become root.. 

sudo su -
then put in the password and it will give you a # prompt instead of a $ (if you using /bin/bash as your interpreter)

---

### Post by aworld on 2012-01-27
Hi, guys

Back again. Problem is fixed once I become a root user. That is the easy way to do it. Now, my program runs good. It scans the the access points which can be sensed by the laptop about 3 scans per 2 seconds.

Thus, I move forward, and use a TL-WN722N USB-wireless adapter with external antenna. (Just for getting a more accurate singal level)

Simply, instead of using "eth1" (the laptop), I opened "wlan0". My program works, but, it takes around 3 secs to perform one simple scan. The same thing happened when I am suing "iwlist wlan0 scan".  

Dose anyone here knows how to speed up the scan process with this Atheros chip? (Device ID: 0cf3:9271) 






> **dazman19 said:**
> ```
# nano /etc/sudoers 
```
you need to be root.

It will tell you inside what to put.. but here is mine:

```

# /etc/sudoers
#
# This file MUST be edited with the 'visudo' command as root.
#
# See the man page for details on how to write a sudoers file.
#

Defaults        env_reset

# Host alias specification

# User alias specification

# Cmnd alias specification

# User privilege specification
root    ALL=(ALL) ALL
daz     ALL=(ALL) ALL
# Allow members of group sudo to execute any command
# (Note that later entries override this, so you might need to move
# it further down)
%sudo ALL=(ALL) ALL
#
#includedir /etc/sudoers.d


```

if you want to avoid using sudo all the time you can become root.. 

sudo su -
then put in the password and it will give you a # prompt instead of a $ (if you using /bin/bash as your interpreter)

---

### Post by aworld on 2012-01-27
And BTW,

When using "eth1" for scanning. My scan runs in a for loop for 1000 times. After about each 12 or 15 times of scan, the progress suddenly stops and one core of my CPU takes 100% usage for a short moment (2s or 3s). Then, it becomes normal again. It only takes 10% CPU usage. This is also very interesting, has anyone here faced the same problem before?

For speeding up, I have also disabled IPV6.

  

> **aworld said:**
> Hi, guys

Back again. Problem is fixed once I become a root user. That is the easy way to do it. Now, my program runs good. It scans the the access points which can be sensed by the laptop about 3 scans per 2 seconds.

Thus, I move forward, and use a TL-WN722N USB-wireless adapter with external antenna. (Just for getting a more accurate singal level)

Simply, instead of using "eth1" (the laptop), I opened "wlan0". My program works, but, it takes around 3 secs to perform one simple scan. The same thing happened when I am suing "iwlist wlan0 scan".  

Dose anyone here knows how to speed up the scan process with this Atheros chip? (Device ID: 0cf3:9271)

---

