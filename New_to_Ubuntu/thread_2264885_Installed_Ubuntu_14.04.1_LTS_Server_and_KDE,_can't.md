---
title: "Installed Ubuntu 14.04.1 LTS Server and KDE, can't login to KDE"
date: 2015-02-10
forum: New to Ubuntu
---

### Post by Zimsteree on 2015-02-10
I just came back to Linux 4 days ago. I want to host my own private website and can't figure out what to do with a blank terminal screen. (Though I have found some info on how to host a site it is not ready yet.)

 So I also installed KDE because I used it on Simply Mepis for two years and loved it, about seven years ago. I have plenty of room for both KDE and a server on my current installation. (I searched online for answers and found mostly "don't do it," as in don't install a GUI on a server.  I want to play Linux games, I miss them. Now on to the actual problem.

When Ubuntu loads it goes straight to KDE with an option to login as me (with my first name) or guest. To login as me requires a password which I was not asked to make during the KDE install process so I tried my ubuntu password and my mysql password with no luck. The only other option is logging in as guest which isn't much fun as I cannot make any changes that stick.

Thanks in advance for any help.

---

### Post by mastablasta on 2015-02-11
yeah don't use desktop on web server.

anyway, since you want a desktop - the password to login is the one you used when you created the user (when installing server). or you can reset it ("the other way"): [https://help.ubuntu.com/community/LostPassword](https://help.ubuntu.com/community/LostPassword)

---

### Post by Zimsteree on 2015-02-11
Thank you. It doesn't accept the password. So I reinstalled Ubuntu Server 14.04 LTS and will use another computer for the desktop.

---

### Post by mastablasta on 2015-02-12
for easier administration of server you can use a webGUI. you can install Zentyal or even something lighter like Webmin or Ajenti or similar. the access the server form browser. it comes in handy sometimes.

by the way there are also free alternatives to cpanel like zpanel and similar.

---

### Post by sandyd on 2015-02-12
Side note:

Several control panels are highly insecure, or are not really trust-able, see below

Kloxo: [http://www.webhostingtalk.com/showthread.php?t=1344003](http://www.webhostingtalk.com/showthread.php?t=1344003) (Many webhosts now prohibit use of Kloxo)

ZPanel: [http://www.lowendtalk.com/discussion/10391/the-security-trainwreck-that-is-zpanel](http://www.lowendtalk.com/discussion/10391/the-security-trainwreck-that-is-zpanel)

---

