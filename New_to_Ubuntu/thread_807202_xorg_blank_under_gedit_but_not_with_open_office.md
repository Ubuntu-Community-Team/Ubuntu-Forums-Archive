---
title: "xorg blank under gedit but not with open office"
date: 2008-05-25
forum: New to Ubuntu
---

### Post by Fenris_rising on 2008-05-25
hi all
im having a slight problem with my xorg.conf. i use sudo gedit /x11/xorg.conf to get it. the gedit window opens and its blank. now its not a case of invisible text definatly. no if i nav to the xorg file and use open office to look at it its all there. so whats wrong? i am able to use the gedit command to look at other files with no problems.

---

### Post by sayakb on 2008-05-25
Check:
```
cat /etc/X11/xorg.conf
```

---

### Post by sisco311 on 2008-05-25
check your command:
```
gksu gedit /etc/X11/xorg.conf
```

---

### Post by drs305 on 2008-05-25
Typically, you need to run it as:
```
gksudo gedit /etc/X11/xorg.conf
```

Added:
Too late! But remember capitalization counts in ubuntu, and you should use gksudo instead of sudo for gui-based apps.

---

### Post by Fenris_rising on 2008-05-25
thankyou thankyou thankyou. i thought i was going mad gk!!!!!!!! noted

---

### Post by sayakb on 2008-05-25
sudo gedit works for me each time..:confused: :confused: :confused:

EDIT: Heres a supporting screenshot: [http://i30.tinypic.com/ng6cso.jpg](http://i30.tinypic.com/ng6cso.jpg)
Anyway, how does it matter ;)

---

### Post by sisco311 on 2008-05-25
> **LinuxIsInnovation said:**
> sudo gedit works for me each time..:confused: :confused: :confused:

EDIT: Heres a supporting screenshot: [http://i30.tinypic.com/ng6cso.jpg](http://i30.tinypic.com/ng6cso.jpg)
Anyway, how does it matter ;)
I think the OP missed out the **/etc **part.

---

### Post by drs305 on 2008-05-25
> **LinuxIsInnovation said:**
> sudo gedit works for me each time..:confused: :confused: :confused:

sudo works for most things but sometimes it won't. So I try to instill good habit patterns. Here is an explanation.
[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

---

### Post by Fenris_rising on 2008-05-25
hi 

i had done the full string command as well but had the same blank page.
i guess its down to some sort of 'security' level of the file. is that right??

---

### Post by drs305 on 2008-05-25
> **Fenris_rising said:**
> hi 

i had done the full string command as well but had the same blank page.
i guess its down to some sort of 'security' level of the file. is that right??

I think it was either a spelling or path error - maybe x11 vs X11. If you still happen to have the terminal window open, you can use the up arrow to go back through the previous commands you have issued.

---

### Post by sayakb on 2008-05-25
> **Fenris_rising said:**
> hi 

i had done the full string command as well but had the same blank page.
i guess its down to some sort of 'security' level of the file. is that right??


I don't think so. When you open it with sudo or gksudo, you open it as root, and root has access to everything. Maybe it's some problem with gedit. Try re-installing gedit:
```
sudo apt-get install --reinstall gedit
```

---

### Post by Fenris_rising on 2008-05-25
:lolflag: pardon me im just going outside.."i may be gone for some time" ........."X"!!!!!!!!bugger

---

