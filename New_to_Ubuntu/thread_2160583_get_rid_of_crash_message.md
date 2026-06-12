---
title: "get rid of crash message"
date: 2013-07-07
forum: New to Ubuntu
---

### Post by ub9876 on 2013-07-07
Ever since I installed a SSD in my laptop ,I get a message at start up in the tray about crash detected. It doesnt affect anything so I ignore it
but I want to get rid of the that specific notification. Anyone know how to get rid of this...its the little red icon in the tray next to the update icon.
XFCE,  13.04

---

### Post by Penguenci on 2013-07-07
You need to disable apport. Open a terminal and type:

```
sudo gedit /etc/default/apport
```

You'll see a simple text file. Find the string “enabled=1&#8243;, and simply replace that 1 with a 0 and save the file.

You can reverse this in the future by doing the exact opposite of step two.

---

### Post by deadflowr on 2013-07-07
Use gksu gedit, instead of sudo gedit
gksudo for graphical root, and sudo for command line root.
kdesudo for kde desktop.

---

### Post by ub9876 on 2013-07-07
whats the difference?? I got rid of it the first way..

---

### Post by deadflowr on 2013-07-07
[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

---

### Post by Cheesehead on 2013-07-07
You should report the problem or prevent the crash instead of hiding it.

Disabling apport hides the problem from developers, too. They need that data.
They rely upon users sending crash reports to know how widespread a problem is. More reports means higher priority to fix.

If you need help figuring out how to prevent the crash, then open up the details of the crash and post them here.

---

### Post by BrunoLotse on 2013-07-07
Hi,I disabled apport. Here's why I did it [https://wiki.ubuntu.com/Apport#Why_is_it_disabled.3F](https://wiki.ubuntu.com/Apport#Why_is_it_disabled.3F) and here's how to make it [http://www.webupd8.org/2012/06/how-to-get-rid-of-internal-system-error.html](http://www.webupd8.org/2012/06/how-to-get-rid-of-internal-system-error.html)Cheers,Bruno

---

