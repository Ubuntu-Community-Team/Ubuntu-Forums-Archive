---
title: "How to find Ubuntu files in Mac"
date: 2012-02-17
forum: New to Ubuntu
---

### Post by smitra on 2012-02-17
Hi,
I am very new here. This forum looks really nice. 
My question:
How can I access ubuntu files from mac. 
I have a mac 10.7
and ubuntu is loded on paralel desktop 7 for mac. 

I can see mac home files from ubuntu but not the other way around.
Any help would be really great. 


Thanks,
smitra

---

### Post by Lars Noodén on 2012-02-17
I don't know of a way to get OS X to read EXT partitions.  But it is possible to read and write HFS+ partitions in Ubuntu if [Journalling is turned off](https://support.apple.com/kb/HT2355).  So if you what to share your home directory, make sure that /home is in a separate partition and that it is formatted as HFS+.  If you format it in OS X, then you will have tol go through the small but extra step of turning off journaling.

---

### Post by smitra on 2012-02-17
Hi,
 Thanks for your reply. But I thought if ubuntu is loded on parallels then it should have stored its all information/ folders somewhere in main mac hard drive. May be this folder is hidden. So I was trying to find that. If somebody knows where ubuntu may store the info...

---

