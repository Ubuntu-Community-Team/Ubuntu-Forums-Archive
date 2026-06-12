---
title: "Dell XPS M1710 laptop: Ubuntu 8.04 32 bit does't resume from suspend"
date: 2008-05-26
forum: New to Ubuntu
---

### Post by cn108 on 2008-05-26
Hi,

I am new to Ubuntu, and just installed Hardy 8.04 32 bit on my Dell XPS M1710 laptop. It works well, I am quite impressed. One bug though: it goes to suspend state without problem, but when I try to get it to resume, the power light goes on as if it's going to work, but the screen stays black.

Any idea?

Thank you very much.

---

### Post by cprofitt on 2008-05-26
Nvidia card?

If it is try just entering your password and hitting enter.

If that works I can direct you to a few possible solutions listed on bug-tracker.

---

### Post by cn108 on 2008-05-27
Hi,

Thank you very much for your support.

Yes, it is an Nvidia card (however I didn't install the 3rd party driver that's available with Ubuntu, since Ubuntu recommends not to use it).

I tried to enter the password and hit enter, but it didn't work.

---

### Post by cprofitt on 2008-06-02
If you are on the current kernel then there is a known bug for this right now...

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/226279](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/226279)

though most are not even getting to a white screen.

---

### Post by hotweiss on 2008-06-03
> **cn108 said:**
> Hi,

Thank you very much for your support.

Yes, it is an Nvidia card (however I didn't install the 3rd party driver that's available with Ubuntu, since Ubuntu recommends not to use it).

I tried to enter the password and hit enter, but it didn't work.

This is how to install the 3rd party Nvidia driver:

Download the new driver:

[http://www.nvnews.net/vbulletin/showthread.php?t=113919](http://www.nvnews.net/vbulletin/showthread.php?t=113919)

0. sudo apt-get remove nvidia*
1. Ctrl-Alt-F1
2. sudo /etc/init.d/gdm stop
3. sudo su
4. sh ./NVIDIA-Linux-x86-173.14.05-pkg1.run
5. go through all the prompts
6. restart

As far as your suspend problem is concerned, try this:

> 
sudo nano /etc/default/acpi-support

Change POST_VIDEO=true to POST_VIDEO=false

Ctrl-O, Enter, Ctrl-X

Restart

---

### Post by cn108 on 2008-06-04
Thank you for the info, Privatevoid. I had a look, it doesn't seem to be easy to solve!

Thank you very much for the suggestion, hotweiss; I tried it, but it didn't work.

---

