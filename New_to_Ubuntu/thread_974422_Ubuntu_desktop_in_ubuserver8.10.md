---
title: "Ubuntu desktop in ubuserver8.10"
date: 2008-11-07
forum: New to Ubuntu
---

### Post by Gipsy25 on 2008-11-07
Hey there ...i have a problem i am new to ubuntu and i unstalled ubu server 8.10 i would like to install the desktop (gui) but my problem is that i dont have access to the Internet ... (wireless only).

I was wondering if it was a way to install it from cd. I did some research and i found i could add the cd (apt-cdrom add) after it I tried : "apt-get install ubuntu-desktop" it says it cant find the package.

So i am stuck ... can you please help?


the output of cat is the following 
When i do cat /etc/apt/sources.list gives me a list that is very long ...
ALL the sentences have a "#" at the beginning of the sentence.
Including the deb's
# Line commented out by installer because it failed to verify:
# deb-src http:// .....
and continues like that all the way down.

Thank you.

---

### Post by jbg on 2008-11-07
I tried to do the upgrade on the wireless and it would stop. I think the upgrade reconfigures the wireless and the machine will not reconnect. What I ended up doing was down loading the ISO file, burning a CD then booting off the CD....but this will reformate the drive and you will lose all data....no big thing for me

---

### Post by Gipsy25 on 2008-11-08
thanks for the reply ... 
Well in my case i just need to install the gui in ubuntu server 8.10
I tried everything i possible could think of ... but no success. 

I used this other sentence to make sure the cd rom was available 
cat /etc/apt/sources.list | grep -v "^#"
but still no luck It says there is not package available on E

I understand E is the cd rom but i am not sure ... 
So here i am still trying to use the cd to install the gui 
I also tried the other cd (8.10 desktop version the one i can boot from) but it didn't work either ...
Just for the record i used 
sudo apt-get install ubuntu-desktop and it comes back with ...
reading package list ... done
building dependency ...
reading state information 
E:could not find the package ubuntu-desktop

---

### Post by 3rdalbum on 2008-11-08
You cannot add the Ubuntu Desktop CD (the one you can boot an Ubuntu desktop from) as a repository. You need to add an Alternate CD (the one that gives you a text-based installer) using apt-cdrom. Then you should be able to install ubuntu-desktop. (you might need to do a "sudo apt-get update" first).

Alternatively, connect your computer to your wireless router through an Ethernet cable, and install ubuntu-desktop as normal.

---

