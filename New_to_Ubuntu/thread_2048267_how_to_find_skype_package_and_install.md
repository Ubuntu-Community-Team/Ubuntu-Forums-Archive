---
title: "how to find skype package and install"
date: 2012-08-26
forum: New to Ubuntu
---

### Post by Sudan on 2012-08-26
Hi, complete newbie.

I have installed Lubunto 12.4 on Asus EEE PC 900A with only a 4gb sshd.

I don't know how to find the skype package (if that is correct terminology).  If I could find the skype package I think I could figure out how to install it.

How do I use the Lubuntu gui to locate packages?

---

### Post by gandaran on 2012-08-26
first you will need to enable the canonical partners repository and update the package list then you will find skype ready for install in the package manager, I don' know if Lubuntu software center is the same as Ubuntu but open software center go to edit » repositories » other software tab » enable canonical repo then update package list.

---

### Post by Sudan on 2012-08-26
> **gandaran said:**
> first you will need to enable the canonical partners repository and update the package list then you will find skype ready for install in the package manager, I don' know if Lubuntu software center is the same as Ubuntu but open software center go to edit » repositories » other software tab » enable canonical repo then update package list.

How do I enable a repository in Lubuntu?

-----
OK, I finally found this code snipet
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) natty partner

on this page
[https://help.ubuntu.com/11.04/ubuntu-help/addremove-sources.html](https://help.ubuntu.com/11.04/ubuntu-help/addremove-sources.html)

So I pasted that code snippet into the "add" field of the "Synaptic Package Manager"->Settings->Repositories->Other Software->Add button

then I reloaded.  And somehow or other I found skype and installed it.

Of course I was doing this all on a live USB stick running Lubuntu 12.04 as a test.

When I went to install it, the Lubuntu installer said I needed 4.4gb hard drive.  I'm doing this on an Asus eee PC 900A with only a 4gb sshd.  But that is subject for another post.

---

### Post by gandaran on 2012-08-27
if you have 12.04 don't add the canonical repository for 11.04, in fact you don't have to add anything, if you look again the proper repository is already there, all you to have to do is check-mark the corresponding box and reload package data.

---

