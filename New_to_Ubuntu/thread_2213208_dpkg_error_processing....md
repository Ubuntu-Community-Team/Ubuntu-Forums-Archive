---
title: "dpkg: error processing..."
date: 2014-03-25
forum: New to Ubuntu
---

### Post by Jamppa-90 on 2014-03-25
Hey. Installed Ubuntu 13.10 today on an older laptop (a lenovo T61), now facing these type of errors when updating/installing stuff.

Errors were encountered while processing:
 libdbus-1-3:i386
 libpulse0:i386
 libasound2-plugins:i386
 libavahi-client3:i386
 libcups2:i386
 libsane:i386

dpkg: error processing libcups2:i386 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libsane:i386:
 libsane:i386 depends on libavahi-client3 (>= 0.6.16); however:
  Package libavahi-client3:i386 is not configured yet.


so on and so forth, there's a whole list of them. What could be causing this and how do i fix it? Did i install the wrong version of Ubuntu or something? Kind of a newbie here.

Thanks in advance.

---

### Post by gifford on 2014-03-25
Did you install the 64 bit version? On the Ubuntu site, the default download is 64 bit now. 
Do you know how old the laptop is and whether it is 32 or 64 bit?
Do you have Synaptic Package manager installed?

---

### Post by Jamppa-90 on 2014-03-25
Might be a 32 bit laptop btw, i'll try that and get back to you.

---

### Post by hamishmb on 2014-03-25
Don't worry about 32 and 64-bit; if your laptop wasn't 64-bit, it would refuse to install, so no worries there. It is fairly common to have i386 packages on 64-bit systems anyway. Could you post me the output of these commands in order?

sudo apt-get update

sudo dpkg --configure -a

sudo apt-get install -f 

sudo apt-get upgrade

sudo apt-get dist-upgrade

Thanks,
Hamish

---

