---
title: "[SOLVED] Package manager not working"
date: 2008-10-14
forum: New to Ubuntu
---

### Post by freeediver on 2008-10-14
Now I cant even use the package manager to do updates
I'm really stuck

I got this message
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.
E: _cache->open() failed, please report.
This all relates to my frustration in trying to get google earth to work again But that is a different post.
What Should I do now?
I cant update?
This all started when I tried to get google earth to work again but that is a different post

---

### Post by JoshuaRL on 2008-10-14
Do this from the terminal:
```

sudo dpkg --configure -a
sudo apt-get install -f
sudo apt-get autoremove
sudo apt-get update
sudo apt-get upgrade

```
That should clean everything up, and get you ready to install what you want.

---

### Post by rybaxs on 2008-10-14
> **freeediver said:**
> Now I cant even use the package manager to do updates
I'm really stuck

I got this message
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.
E: _cache->open() failed, please report.
This all relates to my frustration in trying to get google earth to work again But that is a different post.
What Should I do now?
I cant update?
This all started when I tried to get google earth to work again but that is a different post

WOW.. is there a google earth on Ubuntu? woow... wana try it.. thanks!

---

### Post by oldos2er on 2008-10-15
> **rybaxs said:**
> WOW.. is there a google earth on Ubuntu? woow... wana try it.. thanks!

 It's in the Medibuntu repository. See [http://www.medibuntu.org/](http://www.medibuntu.org/)

 Or download the *.bin from [http://dl.google.com/earth/client/GE4/release_4_2/GoogleEarthLinux.bin](http://dl.google.com/earth/client/GE4/release_4_2/GoogleEarthLinux.bin)

---

### Post by freeediver on 2008-10-15
As I said this all started by trying to update google earth.
When I tried the command list in the above thread Google earth tried to install itself again even tho I put everything in the trash. I can not get rid of the partial G.E. installation and it seems that this might be holding everything up.
Thanks for the help, I'm really stuck

---

### Post by Tatty on 2008-10-15
What is the output from

```
sudo dpkg --configure -a
```

---

### Post by freeediver on 2008-10-15
Somehow by using the above commands the packacke manager became unstuck, Thanks.
It was still trying to install g.e. but at least the P.Man. works now.
The next task is to get google earth to work again.
I can get to the splash screen like everyone else and then nothing.

---

### Post by Tatty on 2008-10-15
Try running google earth from the terminal and see if it outputs any error messages.

---

### Post by freeediver on 2008-10-15
I have and still it will flash on then shut down.
I have started a new thread and I am searching others to try and get G.E. to work. No luck yet.
I have tried medibuntu
terminal etc.
I can only get the flash screen then it closes down.
At least my package manager is working again.

---

### Post by hyper_ch on 2008-10-15
generally, reading the error messages do give quite a few good clues and this error message tells you what you actually need to do.

---

### Post by rybaxs on 2008-10-15
> **oldos2er said:**
> It's in the Medibuntu repository. See [http://www.medibuntu.org/](http://www.medibuntu.org/)

 Or download the *.bin from [http://dl.google.com/earth/client/GE4/release_4_2/GoogleEarthLinux.bin](http://dl.google.com/earth/client/GE4/release_4_2/GoogleEarthLinux.bin)

thank you!.. coooOOl.. Medibuntu (another area explored!:guitar: )

by the way.. How should i make run with this GoogleEarthLinux.bin? in Ubuntu

- Thank you, i think i need this dependencies ...

---

### Post by rybaxs on 2008-10-15
```

user@user-desktop:~$ wget http://dl.google.com/earth/GE4/GoogleEarthLinux.bin
--19:36:49-- http://dl.google.com/earth/GE4/GoogleEarthLinux.bin
=> `GoogleEarthLinux.bin'
Resolving dl.google.com... 64.233.183.91, 64.233.183.93
Connecting to dl.google.com|64.233.183.91|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 19,786,344 (19M) [application/octet-stream]

100%[====================================>] 19,786,344 938.39K/s ETA 00:00

19:37:10 (913.95 KB/s) - `GoogleEarthLinux.bin' saved [19786344/19786344]
user@user-desktop:~$ chmod +x GoogleEarthLinux.bin
user@user-desktop:~$ ./GoogleEarthLinux.bin
Verifying archive integrity... All good.
Uncompressing Google Earth for GNU/Linux 4.0.2091..................................................................
Installing mimetypes...
Running /usr/bin/update-mime-database /home/rick/.local/share/mime
***
* Updating MIME database in /home/rick/.local/share/mime...
Wrote 4 strings at 20 - a4
Wrote aliases at a4 - a8
Wrote parents at a8 - ac
Wrote literal globs at ac - b0
Wrote suffix globs at b0 - 148
Wrote full globs at 148 - 14c
Wrote magic at 14c - 158
Wrote namespace list at 158 - 15c
***
Installing desktop menu entries.

```

---

### Post by JoshuaRL on 2008-10-16
Seems like it installs okay.  What does the terminal output say when you try to launch the app from there?

---

