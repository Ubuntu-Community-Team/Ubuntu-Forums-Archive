---
title: "How to install and access transmission-daemon from a browser?"
date: 2015-08-16
forum: New to Ubuntu
---

### Post by remmas-sido on 2015-08-16
Hello guys 
I want to know the way to install transmission-daemon and how to access it from a web browser by that I means the web-UI?
Thank you

---

### Post by Vladlenin5000 on 2015-08-16
Edit > Preferences > Remote

Choose your options accordingly and then you should be able to access it using http://<IP address>:<port> (default is 9091).

---

### Post by remmas-sido on 2015-08-16
> **Vladlenin5000 said:**
> Edit > Preferences > Remote

Choose your options accordingly and then you should be able to access it using http://<IP address>:<port> (default is 9091).

Can I have the daemon and the web ui without the need to the gui?

---

### Post by Vladlenin5000 on 2015-08-16
[http://ubuntuforums.org/showthread.php?t=1605096](http://ubuntuforums.org/showthread.php?t=1605096)

Old but things are still pretty much the same so it should give you the basics.

---

### Post by remmas-sido on 2015-08-16
> **remmas-sido said:**
> Can I have the daemon and the web ui without the need to the gui?

First of all than you for your help. I've been able to run the Web UI when I typed [http://127.0.0.1:9091/transmission/web/](http://127.0.0.1:9091/transmission/web/) I entered transmission for both username and password, but here is the thing the download location is in var/lib/transmission/downloads and I want to change the downloads directory to home/username/Downloads or at least paste the downloaded data over there (I mean var/lib/transmission/downloads) I guess this is something that needs root permission or it needs for the file manager to be opened with root privileges, Am I right? or do you have some other suggestions?

---

### Post by remmas-sido on 2015-08-16
> **Vladlenin5000 said:**
> [http://ubuntuforums.org/showthread.php?t=1605096](http://ubuntuforums.org/showthread.php?t=1605096)

Old but things are still pretty much the same so it should give you the basics.

And I'm getting this error "
[h=2]Connection Failed[/h] 				Could not connect to the server. You may need to reload the page to reconnect." I don't know if it's the same problem addressed in the link that you gave.

---

### Post by Vladlenin5000 on 2015-08-16
[https://wiki.archlinux.org/index.php/Transmission](https://wiki.archlinux.org/index.php/Transmission)

---

