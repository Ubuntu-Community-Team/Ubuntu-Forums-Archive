---
title: "Connecting to the Internet"
date: 2008-11-24
forum: New to Ubuntu
---

### Post by Zickar on 2008-11-24
Not sure if this has been asked before or not but there doesn't seem a direct match for my topic anywhere so I'll go ahead and ask this anyway and hope you can help me, now I know this isn't a Xubuntu forum but as I understand Xubuntu is like a lighter version of Ubuntu or something and as their is no official Xubuntu forum I'll just tell you my situation.

I've been dying to get out of my WIndows shell for some time now and I have secretly dreamt about running a Linux system of some sort, eventually I settled on Xubuntu, downloaded the image and burned it on a CD, I can now boot Xubuntu from my CD.

When I first ran the CD I chose the option to run it without installing anything, It ran fine and there aren't any troubles the problem is I just can't figure out how to connect the internet

Usually in Windows I just go to Start>Connect to and voila I get my connection, but it seems more complicated on Xubuntu .. Does anyone have any suggestions or pointers, I have the latest Xubuntu which is 8.10 I think and I think I run a Point to Point Wireless internet connection

---

### Post by jemate18 on 2008-11-24
> **Zickar said:**
> Not sure if this has been asked before or not but there doesn't seem a direct match for my topic anywhere so I'll go ahead and ask this anyway and hope you can help me, now I know this isn't a Xubuntu forum but as I understand Xubuntu is like a lighter version of Ubuntu or something and as their is no official Xubuntu forum I'll just tell you my situation.

I've been dying to get out of my WIndows shell for some time now and I have secretly dreamt about running a Linux system of some sort, eventually I settled on Xubuntu, downloaded the image and burned it on a CD, I can now boot Xubuntu from my CD.

When I first ran the CD I chose the option to run it without installing anything, It ran fine and there aren't any troubles the problem is I just can't figure out how to connect the internet

Usually in Windows I just go to Start>Connect to and voila I get my connection, but it seems more complicated on Xubuntu .. Does anyone have any suggestions or pointers, I have the latest Xubuntu which is 8.10 I think and I think I run a Point to Point Wireless internet connection

if you are connecting using wifi (DHCP), then it should be able to connect to the internet. However, in your case, you are experiencing problems, you might want to check that network icon on the top right pane of your desktop, then you can setup your network there....

---

### Post by Changturkey on 2008-11-24
Try the XFCE control panel, or like the above poster suggested, your network icon (right click).

---

### Post by Zickar on 2008-11-25
> **jemate18 said:**
> if you are connecting using wifi (DHCP), then it should be able to connect to the internet. However, in your case, you are experiencing problems, you might want to check that network icon on the top right pane of your desktop, then you can setup your network there....

Yeah I tried it, I opened the properties and I think I posted the properties right, I chose Point to point connection and I put the username and passwprd it asked me but it still won't work ... ANy hints ??

---

### Post by roshanjose on 2008-11-25
Just go to the terminal and type this:

sudo network-admin restart


here you need to configure it the way you want....it works for me

---

