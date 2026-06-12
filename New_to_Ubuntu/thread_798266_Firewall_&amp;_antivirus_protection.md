---
title: "Firewall &amp; antivirus protection ??"
date: 2008-05-18
forum: New to Ubuntu
---

### Post by Tubby on 2008-05-18
Hi all, i have just installed ubuntu and just getting the feel of how it all works, just one question if i can,  i am used to XP with having to install a firewall and other antivirus programs after reloading windows, do you have to load a firewall & antivirus programs with ubuntu ?  
appreciate for any advise
Thanks

---

### Post by Xiong Chiamiov on 2008-05-18
Firewall is built in, antivirus is not needed.  Let's see, I just covered this yesterday...

[ah hah!]("http://ubuntuforums.org/showthread.php?t=797172#5")

---

### Post by nowshining on 2008-05-18
anti-virus - less than no - however u can install clamav & the gui part in synaptic if u want to.

A firewaall u already have - linux comes with a firewalll by defautl however it's not configured. You can use guarddog or firestarter for a gui for it to configure it or write ur own rules. This Firewall is called Iptables.

There are many other GUI's for it on the web + there are scripts u can use.

I use arno-iptables-firewall - by default it works fine after u answer a few Q's about ur setup. It also comes with a custom-rules file to use ur own.

The firewall config is the same /etc/arno-iptables-firewall/ folder named firewall.conf.

it will auto-start for u on a reboot + if u do change any rules it's as simple as issuing the command in terminal.

sudo /etc/init.d/arno-iptables-firewall restart

to reload and for the new changes to take effect.


Yes iptables is mainly build into the kernel + it doesn't take up a huge amount of resources.

---

### Post by nicedude on 2008-05-18
Just my 2 cents but I found Guarddog to be the better firewall manager ( IPtables is your actual firewall ).

---

### Post by Tubby on 2008-05-18
Thanks nowshining for all the extra information, i really appreciate the effort.
many thanks

---

### Post by hyper_ch on 2008-05-18
you don't really need AV or FW on ubuntu normally...

---

