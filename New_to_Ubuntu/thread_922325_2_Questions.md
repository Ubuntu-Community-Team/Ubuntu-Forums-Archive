---
title: "2 Questions"
date: 2008-09-17
forum: New to Ubuntu
---

### Post by waitcursor on 2008-09-17
Hi,

1 How to you backup the wlan config file? Or where is the file located so I can copy this and locate it in my Backup folder.

2 How do you remove KDE4.1, I've seen several entries about this but whenever I try these it seems that only 10kb will be removed, and the download was + 100MB.

thanks n advance.
Waitcursor

---

### Post by darrelljon on 2008-09-17
/etc/conf.d/net I think.
apt-get remove kde I think.

---

### Post by waitcursor on 2008-09-17
> **darrelljon said:**
> /etc/conf.d/net I think.
apt-get remove kde I think.

Hi tried both but conf.d doesn't exist on my system.
Also the apt-get remove kde doesn't find any packages, but thanks for your feedback

rgds,
waitcursor

---

### Post by Orange_and_Green on 2008-09-17
To get a list of all KDE-related packages in your system, a good place to start might be:

```
dpkg --get-selections | grep -v deinstall | grep kde > kde.txt
gedit kde.txt
```

---

### Post by waitcursor on 2008-09-20
> **Orange_and_Green said:**
> To get a list of all KDE-related packages in your system, a good place to start might be:

```
dpkg --get-selections | grep -v deinstall | grep kde > kde.txt
gedit kde.txt
```

Thanks man, this did it :-)

---

### Post by hyper_ch on 2008-09-20
It is advised to use a descriptive topic title; that means use a topic title that gives some clue about the content in the thread itself...

A generic topic title like "noob here" or "need help" does not help at all. As you may have notices, just about everyone posting in here has some kind of a problem or issue or question ;) 

Just imagine what these forums would look like if everybody would just post "Help" or "Noob here". What do you think how many people will still look at such threads?

Furthermore, for unrelated questions it's also adviced to open a seperate thread for each one, so that each problem can be addressed (and eventually marked as solved) individually.

---

