---
title: "troubles running apt-update"
date: 2016-10-25
forum: New to Ubuntu
---

### Post by MadleSs on 2016-10-25
Hi guys, 
When I try to run apt-update I'm getting this error
[http://imgur.com/a/78W41](http://imgur.com/a/78W41)

Could you help me to solve it? 
Thanks in advance

---

### Post by Frogs Hair on 2016-10-25
It looks like there is no valid key for gfx from the following page. You can see in the terminal output that that the source is disabled due to a security risk. Perhaps whoever maintains gfx needs to update the key.  

[https://download.01.org/](https://download.01.org/)

---

### Post by MadleSs on 2016-10-25
Thanks for reply, but sorry what should I do with the link you provided :D Sorry I don't know

---

### Post by Frogs Hair on 2016-10-25
I'm not familiar with this repository or the package , do you know what it is ? I was using the link in hopes of discovering who maintains the listed items.

---

### Post by MadleSs on 2016-10-25
No I don't know what's this repository. Coul'd help me how to manually remove it? Thanks

---

### Post by Frogs Hair on 2016-10-25
Open software & updates and see if it's listed under the other software tab. From there you can disable / remove the source. The repository appears to be part of the Crosswalk project if that rings any bells.

---

### Post by ian-weisser on 2016-10-25
Your repositories are stored in /etc/apt/sources.list and /etc/apt/sources.list.d/
Simply open them (using 'sudo') with your favorite text editor (like 'nano'), and comment out or delete that repository.

---

### Post by Frogs Hair on 2016-10-25
I notice there is also a ppa manager installed , so you may want review what's installed there as well.

---

### Post by MadleSs on 2016-10-26
After removing .list file from sources.list.d problem is solved. Thank you guys

---

