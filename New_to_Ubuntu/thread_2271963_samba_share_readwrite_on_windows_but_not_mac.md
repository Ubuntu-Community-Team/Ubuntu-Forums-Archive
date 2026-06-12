---
title: "samba share read/write on windows but not mac"
date: 2015-04-03
forum: New to Ubuntu
---

### Post by adan2 on 2015-04-03
Hi All,

I have just finished setting up a raid 5 array in ubuntu server with a samba share.  I can access and read/write on my windows computer but only view on my mac, cannot save any files....any ideas?  Thanks in advance for your help.

---

### Post by adan2 on 2015-04-11
Ok,  I was able to finally get this fixed....after posting I first noticed that I could only write files from the OS that I was on.  In others words, if I created a folder from my windows machine then I could only write files from that machine but not from my mac, if I created a folder from my mac then I couldn't write from windows.  So here is what I did...

1. Added a valid user to my shared folder in the samba config file
2. changed permissions on all folders where my drive was mounted to 777

---

