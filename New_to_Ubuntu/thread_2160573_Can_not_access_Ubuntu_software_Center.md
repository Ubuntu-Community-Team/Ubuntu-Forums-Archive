---
title: "Can not access Ubuntu software Center"
date: 2013-07-07
forum: New to Ubuntu
---

### Post by JimTex on 2013-07-07
I have a Dell D430 with Ubuntu 12.10 (updated from 12.01 on 7/4/13) I will click on Ubuntu Software Center, the window opens then will close.  This started after I searched for Opera Browser while in the software center. I was getting a message that Ubuntu was sending an error message. From what I can tell I'm getting an error in opening the cache 'E; error opening the cache E:malformed line 1 in source list/etc/apt/sources.list.d/opera.list(dist parse),E: the list of sources could not be read., E: the package list or status file could not be parsed or opened.
 
How do I start in trying to troubleshoot this problem?  I'm a newbie but can follow directions if I understand the direction.

Thanks.

---

### Post by arochester on 2013-07-07
You have an error in your sources list.

Open a Terminal. Input:  gksu gedit /etc/apt/sources.list.d/opera.list

What do you see. Can you copy and paste here?

---

