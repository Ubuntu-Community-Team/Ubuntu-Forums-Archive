---
title: "not able to connect to internet"
date: 2011-09-22
forum: New to Ubuntu
---

### Post by orky7 on 2011-09-22
my modem is preconfigured with user name and passward so i have to put the ethrenet wire in and browse the net but this is not happening. i am using ubuntu 10.04 LTS.

---

### Post by P05TMAN on 2011-09-22
Does it show a connection on the upper right corner of the screen? The network manager icon will show two arrows pointed in the opposite direction:
 
One will be pointed up, then other pointed down. If that icon is not showing, perhaps try a known good ethernet cable.

---

### Post by orky7 on 2011-09-22
it get solved by editing
sudo gedit /etc/NetworkManager/nm-system-settings.conf
and setting one (i cant remember it) parameter to true
and then 
 killall nm-system-settings
it dosent work anyways i restarted the machine and the globe glows in blue color and net is connected

---

