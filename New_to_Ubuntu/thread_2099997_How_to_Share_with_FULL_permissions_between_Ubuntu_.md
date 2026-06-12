---
title: "How to Share with FULL permissions between Ubuntu and Win7"
date: 2012-12-31
forum: New to Ubuntu
---

### Post by kc5hwb on 2012-12-31
Hi All,

What I am trying to do is share specific folders between my Ubuntu 12.04 machine, my Windows 7 machine, and my wife's Windows 7 machine.  I am getting permission errors in both directions.

I've searched some threads here, and I followed the instructions at this link: [http://www.liberiangeek.net/2012/05/windows-7-vs-ubuntu-12-04-how-to-enable-advanced-file-sharing/]("http://www.liberiangeek.net/2012/05/windows-7-vs-ubuntu-12-04-how-to-enable-advanced-file-sharing/")

I had used Samba for a long time, I have user accounts with matching usernames and passwords on all machines, and I am able to see the folders across the network (ubuntu folders FROM windows, and windows folders FROM ubuntu) but the errors I get are when I try to create a folder or drag something over, or create a new file, etc.  Basically write permissions.

I've been using Ubuntu for a few years, and it seems there are suttle changes with each update, but still I believe this issue to be with Windows 7.  I never really had this problem when I was using XP.

Thanks for the help.

---

### Post by Mark Phelps on 2012-12-31
> **kc5hwb said:**
> I never really had this problem when I was using XP.

That's because XP, being wide open, developed a reputation for being a malware magnet.

MS has tightened up security more with each release, so some of the things that you could do with XP (like simple sharing) can not be done with Win7.

---

### Post by kc5hwb on 2013-01-01
Yea I am aware of the short-comings of XP, but there has got to be a way to share with Win7 too.

---

### Post by Isamu715 on 2013-01-01
What about Ubuntu One? It has a Windows client and automatically synchronizes folders.

---

### Post by Morbius1 on 2013-01-01
> I had used Samba for a long time, I have user accounts with matching usernames and passwords on all machines, and I am able to see the folders across the network (ubuntu folders FROM windows, and windows folders FROM ubuntu) but the errors I get are when I try to create a folder or drag something over, or create a new file, etc. Basically write permissions.
There are 2 sets of permissions. Do the Linux permissions on the shared folder allow the remote samba client to write? Not the Samba permissions the Linux permissions on the folder itself.

Maybe the best thing to do is for you to post the output of the following commands so the folks here can be more specific:
```
testparm -s
```
```
net userhsare info --long
```

---

### Post by NikTh on 2013-01-01
> **Morbius1 said:**
> There are 2 sets of permissions. Do the Linux permissions on the shared folder allow the remote samba client to write? Not the Samba permissions the Linux permissions on the folder itself.

+1 

also sometimes ( I don't know why) after a change , you have to disable and enable again the share options on Windows machine.

---

