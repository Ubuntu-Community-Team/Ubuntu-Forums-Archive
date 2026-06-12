---
title: "Server 12.04 with XFCE gui on boot?"
date: 2012-06-19
forum: New to Ubuntu
---

### Post by ruimarto on 2012-06-19
I had a XBMCbuntu but I decided to switch to a fresh Ubuntu 12.04 Server 64bits install, but I do need a GUI to run stuff like XBMC, Wuala, Dropbox, Transmission, JDownloader, Chrome, etc. I know I can use Transmission and JDownloader trough webGUI and access files trough SFTP, but I also use it to browse on my TV, go to youtube, facebook, and stuff.
I already tried Ubuntu Desktop, but it's too heavy and full of stuff I don't use/need.

I've tried the commands below with no success:
$ sudo apt-get install xorg
$ sudo apt-get install xfce4

After a complete mess of unsuccessful tutorials, I formated and reinstalled. Now I've only done this:
$ sudo apt-get update
$ sudo apt-get upgrade
$ sudo nano /etc/ssh/sshd_config (changed port, root login to no and allow my user)
$ sudo apt-get install nvidia-current
$ sudo reboot

Now I just want to install a clean (vanilla?!) xfce with nautilus file manager. What should I do?

---

### Post by mastablasta on 2012-06-19
> **ruimarto said:**
>  with no success:

 
elaborate! what kind of error messages if any?
 
have you tried: sudo apt-get install xfce4 xfce4-goodies
 
You can also install xubuntu-desktop and then remove programmes you don't want/need. and login as xfce.

---

### Post by ruimarto on 2012-06-19
Sorry, I was getting an error when starting X with startx command but I didn't write it down. However after reinstall I did the following commands and now it works:
$ sudo apt-get update
$ sudo apt-get install xorg
$ sudo reboot
$ sudo apt-get update
$ sudo apt-get install xfce4
$ sudo reboot
$ sudo startx

Now how do I make it boot into xfce directly?

---

### Post by afixane on 2012-06-19
```
nano ~/.xinitrc
```
insert this
```
exec startxfce4
```

---

### Post by ruimarto on 2012-06-19
Thanks. I've done that (created the file in /home/myusername/) but it still boots into the cmd line.

I tried "sudo startx" from a remote terminal and XFCE opened with default settings. Is this normal?

---

### Post by afixane on 2012-06-19
> **ruimarto said:**
> Thanks. I've done that (created the file in /home/myusername/) but it still boots into the cmd line.

I tried "sudo startx" from a remote terminal and XFCE opened with default settings. Is this normal?

Sorry, i'm wrong. You should do this first
```
cp /etc/skel/.xinitrc ~/
nano ~/.xinitrc
```
and then insert this
```
exec startxfce4
```

---

