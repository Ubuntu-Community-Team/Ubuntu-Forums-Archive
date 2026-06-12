---
title: "how to install gnome ppp package without online connection?"
date: 2013-12-24
forum: New to Ubuntu
---

### Post by merlill on 2013-12-24
I have Ubuntu 11.10 and would like to go online with an external modem. I have some downloaded packages, gnome ppp & wvdial on my desktop but have not been able to install them. They do open in the software center but the install button isn't active. Also tried to use terminal and got "dpkg: command not found" Is there a simple way to get this installed? Once I have gnome ppp installed I should be able to go online and use the software center.
thanks,
mm

---

### Post by merlill on 2013-12-26
Currently I have the synaptic packages with its dependencies downloaded in a folder "synaptic" in the computers "home" file. 
To install the packages I tried :
sudo dpkg &#8211;iR synaptic

the output was: 
dpkg: error: need an action option

can someone walk me  through this?
thanks,
mm

---

### Post by angry_johnnie on 2013-12-26
Try opening a terminal and navigating to the directory where the packages are saved:

```
cd /path/to/folder
```

Then install all the .deb packages
```

sudo dpkg -i *.deb
```

If you try to install them one by one it may fail due to dependency problems.

dpkg should be included in 11.10

---

### Post by merlill on 2013-12-27
Thank you sir! That was helpful. Hopefully with synaptic & gnome ppp installed we will be in business.
mm

---

### Post by Impavidus on 2013-12-27
Do you have any reason in particular to run 11.10? It's old and unsupported, which means that you don't get security upgrades etc.

---

### Post by merlill on 2013-12-27
good question. I have used Ubuntu a number of years and liked it except for the ongoing issues with setting up for dialup every time I do an update. The past few months I have used Puppy OS as a back-up since I somehow disabled my permissions in 12.04 and was not able to setup to connect for email. recently when attempting to reinstall 12.04 the system would lock up at a warning window regarding an outdated monitor. Since I'm using old equipment an I had the old OS on a cd I decided to see what can be done. However I've about had it with switching from puppy [to connect] back to Ubuntu back to puppy. Too much downtime.

---

### Post by merlill on 2014-01-09
OK I am going to mark this "solved". My 2nd post defined my problem and Johnnie helped me out with that. Thank you again!

---

