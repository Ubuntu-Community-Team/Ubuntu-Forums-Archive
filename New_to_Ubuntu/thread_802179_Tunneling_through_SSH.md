---
title: "Tunneling through SSH"
date: 2008-05-21
forum: New to Ubuntu
---

### Post by nabab on 2008-05-21
hi,

First, I am not sure I should post that kind of question in this forum as it's not Ubuntu specific, so please feel free to let me know if it's the case.

Anyway, I have installed Ubuntu last night on a spare laptop, it's my first time with Linux, and it was... incredible!
Sorry, it sounds I talk about some girl, but I love it! I can't wait to get rid of Windows on my daily working laptop.
It recognized all the devices including the wireless. 30 minutes after inserting the CD, the OS was working, connected, and up-to-date. 30 minutes later, I had Wine working with Dreamweaver and Flash installed and working fine, plus Apache/PHP/MySQL and a few other softwares such as VLC.

I love it!

Sorry, now I come to my question:

My ISP shapes traffic, and my only way to use torrent normally is to tunnel through a server I have in a datacenter. In windows, I was using Putty, forwarding port 1080. If you look in Putty Config >> SSH >> Tunnels, in forwarded ports I have "D1080".

How can I do the same thing in Ubuntu? (I guess having Putty working with Wine is not the best ;)

Cheers!

PS: I am an absolute beginner, I barely know to use command line.

---

### Post by Krumar on 2008-05-21
Try out this site:
[http://whalesalad.com/2006/08/27/tunneling-bittorrent-over-ssh/](http://whalesalad.com/2006/08/27/tunneling-bittorrent-over-ssh/)

---

### Post by quelx on 2008-05-21
Use the terminal :)

edit a config file for ssh (so you don't have to type the settings every time)

Open the terminal (ALT-F2 > gnome-terminal)

```
nano -w .ssh/config
```

I this file put this with your settings

```
Host alias
        hostname actual.hostname.com
        LocalForward 1080 localhost:1080
```

Save and exit (CTRL-X, yes, yes)

the at the terminal again ```
ssh alias
```

---

### Post by nabab on 2008-05-21
Thanks a lot, I gonna try that tonight, cheers!

---

