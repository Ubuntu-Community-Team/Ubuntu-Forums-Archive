---
title: "Where is RabbitVCS on 12.04? How to start?"
date: 2012-04-29
forum: New to Ubuntu
---

### Post by kramer65 on 2012-04-29
Hello,


I just installed RabbitVCS on Ubuntu 12.04 by simply following the instructions on the RabbitVCS website: [http://wiki.rabbitvcs.org/wiki/install/ubuntu](http://wiki.rabbitvcs.org/wiki/install/ubuntu)
Everything seemed to work well, but when I hit the Windows-button and type "Rabbit" or "RabbitVCS" I don't get anything.

Does anybody know how I can startup RabbitVCS?

---

### Post by androssofer on 2012-04-29
> **kramer65 said:**
> Hello,


I just installed RabbitVCS on Ubuntu 12.04 by simply following the instructions on the RabbitVCS website: [http://wiki.rabbitvcs.org/wiki/install/ubuntu](http://wiki.rabbitvcs.org/wiki/install/ubuntu)
Everything seemed to work well, but when I hit the Windows-button and type "Rabbit" or "RabbitVCS" I don't get anything.

Does anybody know how I can startup RabbitVCS?

Isn't that similar to TortoiseSVN? if so it might not launch like a normal program, try opening the folder browser and right clicking. Then see if its in the right click menu.

---

### Post by kramer65 on 2012-04-29
Ah, I see indeed!

Excuse me for that! Stupid of me.. :-#

Thanks anyway!

---

### Post by alex.ukf on 2012-05-03
kramer65, did you put
deb [http://ppa.launchpad.net/rabbitvcs/ppa/ubuntu](http://ppa.launchpad.net/rabbitvcs/ppa/ubuntu) precise main
in your /etc/apt/sources.list and it worked? 

Because when I try to run
$ sudo apt-get update
I receive this:

Reading package lists... Done
W: Duplicate sources.list entry [http://ppa.launchpad.net/rabbitvcs/ppa/ubuntu/](http://ppa.launchpad.net/rabbitvcs/ppa/ubuntu/) precise/main amd64 Packages (/var/lib/apt/lists/ppa.launchpad.net_rabbitvcs_ppa_ubuntu_dists_precise_main_binary-amd64_Packages)
W: Duplicate sources.list entry [http://ppa.launchpad.net/rabbitvcs/ppa/ubuntu/](http://ppa.launchpad.net/rabbitvcs/ppa/ubuntu/) precise/main i386 Packages (/var/lib/apt/lists/ppa.launchpad.net_rabbitvcs_ppa_ubuntu_dists_precise_main_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems

---

