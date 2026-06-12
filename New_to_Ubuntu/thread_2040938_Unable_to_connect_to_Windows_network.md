---
title: "Unable to connect to Windows network"
date: 2012-08-11
forum: New to Ubuntu
---

### Post by aRake on 2012-08-11
Hi,

I cannot connect to my Windows network.  All I really want is access to an external hard drive on the network, but I cannot connect to the network at all.  I have tried connecting directly to the hard drive via an ethernet cable, but no success (the connection does not establish).

The error that I get when trying to connect to the network is "Unable to mount location; Failed to retrieve share list from server".  I have tried many guides online to fix this, but none have worked.  I have tried using Samba (I don't really understand it) and editing the workgroup name, and I have tried editing various files, including some file /etc/hosts.  Nothing has worked.

The most irksome thing about this?

When I first installed Ubuntu 12.04, I could connect just fine to the network.  I opened the file browser, clicked "Browse Network", clicked "Windows Network", and everything was fine.  One reboot later and I just get this error. :confused:

I do not want to reinstall my system every time I want to access this drive, so does anybody know how to fix this problem?  I have searched high and low.

Thanks for any help you can offer.

---

### Post by Bashing-om on 2012-08-11
looks like you have done your homework. I do not know much about sharing....
but as a 1st step, can you ping the windows box ?
from that start we will see what we can work out.
[INDENT]BDQ
[/INDENT]

---

### Post by aRake on 2012-08-12
Yes, I can ping the external HD.  Like I said, I was able to connect at my fresh install, but after one reboot (no updates, no settings changed) I was unable to connect, and now I only get the error I described.

Has anybody heard of this behaviour before?  Any links they remember seeing somewhere perhaps?

---

### Post by aRake on 2012-08-14
Bump.  Any suggestions welcome, even if it sounds like I've already tried it!  I am quite desperate, haha.

---

### Post by critin on 2012-08-14
> **aRake said:**
> Bump.  Any suggestions welcome, even if it sounds like I've already tried it!  I am quite desperate, haha.

After reading your post, I checked my winXP network and couldn't connect with same error as you, although I could connect to another winXP comp.  SO...I redid the "Set up Network" on the first machine.  I discovered that my share files had become unchecked on the Set Up page.  I also had to go back to the folders I wanted to share and recheck those too.

I can now connect TO xp AND the dual booted Win8  from my ubuntu machine.

When I have trouble with my network, it usually tracks back to Windows.

---

### Post by jeboza on 2012-11-15
Its been really hard to get an answer to this. I've tried everything as well. Every system here from Win 7 and Pro, Windows 8, Mac OS X Lion and Linux Mint can see every other box in this house. 

The only problem is Ubuntu 12.04 and I agree that Samba is not the solution. I would just like to be able to see my shares. Idk why this has been such an issue to resolve and every solution takes you down the maze. To date I've been able to see my share through Samba but for whatever reason it wants a static ip address and my systems dynamic.

Really thinking of going back to the previous version, where there was a little more stability.

---

