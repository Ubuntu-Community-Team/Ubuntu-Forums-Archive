---
title: "How to set up Skype for edgy eft"
date: 2006-11-09
forum: Outdated Tutorials &amp; Tips
---

### Post by greensmoke on 2006-11-09
1. go get
[https://launchpad.net/distros/ubuntu/feisty/i386/libqt3-mt/3:3.3.6-3ubuntu3](https://launchpad.net/distros/ubuntu/feisty/i386/libqt3-mt/3:3.3.6-3ubuntu3)

---That's where you can get the libqt3 that is mentioned when you try to install skype.  save it to your desktop.

2. go get the skype rpm for Mandariva here
[http://www.skype.com/download/skype/linux/](http://www.skype.com/download/skype/linux/)

3. now go get alien...
open up a terminal window from "Applications>Accessories"
type 

sudo apt-get install alien

--wait for it to finish installing

4. now type
cd /home/YOURUSERNAMEHERE/Desktop

5. now type
sudo alien -d skype-1.2.0.21-1mdk.i586.rpm

---NOTE:  YOU MAY HAVE TO CHANGE THE NUMBERS IN ABOVE FILE NAME TO MATCH THE FILE VERSION THAT YOU HAVE DOWNLOADED TO YOUR DESKTOP.

6. now type
sudo dpkg -i skype_1.2.0.21-2_i386.deb 

--and whammo!  It's in your "Applications>Internet"

Woohoo!

---

### Post by frodon on 2006-11-09
An easy way to do this is to use the plf repository :
[http://doc.ubuntu-fr.org/doc/plf](http://doc.ubuntu-fr.org/doc/plf)

Then install it through synaptic or with a "sudo apt-get install skype".

Important NOTE : there's an annoying bug with skype 1.3 and ubuntu which don't have workarounds for the moment :
[https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bug/53216](https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bug/53216)

---

### Post by greensmoke on 2006-11-15
It appears after further investigation that there is indeed a debian package for skype on the skype for linux page mentioned above.  All that is needed is to install the lib file mentioned and the skype package and you are set to go...

---

### Post by girard on 2007-07-07
hi.... i'm a little confused. sorry. there is a download for fieasty and debian eft. i have edgy eft. should i download debian eft or fiesty?

---

