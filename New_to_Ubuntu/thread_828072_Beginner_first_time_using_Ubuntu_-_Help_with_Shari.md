---
title: "Beginner first time using Ubuntu - Help with Sharing Folder over Network"
date: 2008-06-13
forum: New to Ubuntu
---

### Post by SwissAlps on 2008-06-13
First I am a Beginner on Ubuntu. Never use it before. I do now how to work a XP/Vista no problem.

But my needs for sharing a folder with both was not going to help. I decided that Linux would help me out so I am here with my Ubunt Question. 

I have install it fine, i am on the network. I named a folder on the desktop called "coopershare". I went in the properties, click on the shared box, updated with the samba thing. But then I am not sure where else to go or do.

My work group is called COOPERLAN and on my Vista and XP I can see it no problem, but it says "unknown device" try to click it doesn't work. 

I am stuck now, and i am not sure what to do. So please any suggestions. Also if you can give me Step by step. Thanks 

Info: Ubuntu 8.04 LTS Desktop
Running from Ethernet to router

---

### Post by aeiah on 2008-06-13
try having a look here:
[http://ubuntuforums.org/showthread.php?t=202605](http://ubuntuforums.org/showthread.php?t=202605)

---

### Post by dstew on 2008-06-13
I think you need to go to System --> Administration --> Network, unlock the panel (button at bottom, enter your user password), and under the General tab add your Windows workgroup name as the Domain.

---

### Post by SwissAlps on 2008-06-13
Aeiah - I try to do that man, nothing was working. I typed the same thing in 3 times and nothing of the codes worked. Is there not a Easyer way to do this.

Dstew - I tryed that, and well still nothing on my XP/Vista still "unknown Device"

If I can't get this working, I think I may buy windows server 2003. Because I don't want to do all this codes, I mean is that the only way with Linux or at least with Ubuntu ?!?!?

---

### Post by cariboo on 2008-06-13
You can use swat which is a web based appliction to set up samba shares. it is available in the repositories. Use synaptic to install it. Think of this as a learning experience once you understand networking in Linux you will be better able to troubleshoot networking problems in other operating systems.

Jim

---

### Post by ians1 on 2008-06-20
I have SWAT installed but it does not work.

Entering [http://localhost:901/](http://localhost:901/) produces a "Connection Refused" error in Firefox.

I too have a problem with accessing the share previously created.

I have tried making the permissions on the folder 776 with chmod but this does not affect the share permissions seemingly.

I don't know how to adminster Samba basically and I dont know why SWAT does not work.

ian

---

