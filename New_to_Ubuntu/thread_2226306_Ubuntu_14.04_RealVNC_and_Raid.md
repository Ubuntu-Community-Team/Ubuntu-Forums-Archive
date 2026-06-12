---
title: "Ubuntu 14.04: RealVNC and Raid"
date: 2014-05-26
forum: New to Ubuntu
---

### Post by Paul_Wike on 2014-05-26
Afternoon.

Hopefully someone will be able to help and advise me as I'm getting a bit lost :-( 

I have purchased a HP Microserver along with 4 x 1TB SATA hard drives.

What I have done so far baring in mind I have never used Ubuntu 

1) Installed the OS 14.04 
2) Installed RealVNC and which I have got working! 

What I would like to do and where I have problems.

1) I would like the RealVNC service to start up when I boot the server, I have tried a few things but can't seem to get this to work. It does boot up something but when I try to access the server from my laptop it's just a VNC screen, I have to manual start the service and then works by going to the IP and :5555 for instance.
2) At the moment I only have one disk showing as space to save things to, what I would like to do is put these in a RAID 5 array but don't know where to start, also will this destroy what I have already done as I would like to do this now before I go any further with the VNC point above. 

As I say I'm at the beginning of learning about ubuntu so any advise would be greatly appreciated. 

Thanks 
Paul

---

### Post by Paul_Wike on 2014-05-27
Can anyone help on this? really struggling. 

Paul

---

### Post by steeldriver on 2014-05-27
Hello and welcome to the forums

1. are you following some kind of VNC setup instructions / tutorial? if so it would help to post a link so we are on the same page

2. it's a very broad topic - it depends really what you mean by "space to save things to" and how you did the original install (separate /home? regular partitions or LVM?). If you are just looking for a way to expand storage for user data then you can do that pretty much any time, could be as simple as mounting the array somewhere like /storage and symlinking to it, or you could copy your existing /home to it and then mount it

---

