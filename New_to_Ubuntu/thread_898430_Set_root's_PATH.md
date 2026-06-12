---
title: "Set root's PATH?"
date: 2008-08-23
forum: New to Ubuntu
---

### Post by Znupi on 2008-08-23
I just installed apache so I need to add /usr/local/apache2/bin to root's PATH. I thought adding
```
PATH="${PATH}":/usr/local/apache2/bin
```
to **/etc/profile** should do the trick, but it only does it for my user, not for root (e.g. I can run apachectl as my user, but when I try sudo apachectl it says command not found). Basically:
```
felix@the-machine:~$ apachectl -k start
(13)Permission denied: make_sock: could not bind to address [::]:80
no listening sockets available, shutting down
Unable to open logs
felix@the-machine:~$ sudo apachectl -k start
sudo: apachectl: command not found
```
I tried adding the same line (PATH=...) to /root/.profile since there's no .bash_profile or .bash_login in there. How do I set root's PATH?

---

### Post by ggaaron on 2008-08-23
Sudo probably doesn't really use root's environment and doesn't source anything, try sudo with -i option. Also why don't you use /etc/init.d/apache?

---

### Post by Znupi on 2008-08-23
I know I can somehow get it to start when my system starts (I suppose I create a file called apache, make it executable, type the command in and put it in /etc/init.d/ ?), but what if I want to reload apache's configuration (I do this a lot)? I have to type the whole path everytime. But indeed sudo -i works ^.^ thanks :-)

---

### Post by ggaaron on 2008-08-23
Actually apache is already in /etc/init.d and is set to start on boot. To restart just use '/etc/init.d/apache restart', or reload for quick restart.

---

### Post by Znupi on 2008-08-23
> **ggaaron said:**
> Actually apache is already in /etc/init.d and is set to start on boot. To restart just use '/etc/init.d/apache restart', or reload for quick restart.
No its not. I compiled it myself, I didn't apt-get it.

---

### Post by ggaaron on 2008-08-23
Ah, my bad=)

---

