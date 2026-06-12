---
title: "Transfer via ethernet"
date: 2008-04-25
forum: New to Ubuntu
---

### Post by cartisdm on 2008-04-25
I'm too cheap to buy an external harddrive and I want to back up all my stuff before I do a clean install of Hardy.  I have my desktop (using XP) hooked via cat5 to a router and I just plugged my laptop (using Gustsy) in the the router using another cat5.  Now I just want to transfer over all my files.  I can't figure out how to do this with ubuntu...

---

### Post by aeiah on 2008-04-25
set up filesharing or a server on your windows pc. if you choose to share a folder on the network, read up on how to connect ubuntu to a samba share and that should do the trick. or you could set up an ftp server on windows xp or something if you'd like.

---

### Post by cartisdm on 2008-04-25
I have a few folders on my desktop that are already shared but I can't figure out how to access them from my laptop.  From what I've read on Samba you only need it for servers.  The client doesn't need it and it shouldn't be necessary to access shared folders

---

### Post by aeiah on 2008-04-25
[http://www.cyberciti.biz/faq/access-windows-shares-from-linux/](http://www.cyberciti.biz/faq/access-windows-shares-from-linux/)

---

### Post by cartisdm on 2008-04-25
I'm still not getting it for some reason.  I'd prefer a simple GUI method to transfer my files over (drag and drop).  When I go to Network in nautilus --> Windows Network I only see mshome.  The name of the workgroup for my desktop (the-beast) is FILESHARE.

Edit:  Here's what I did:

Changed my password to "test"
```
sudo smbpasswd -a 'myusername'
```

Within Windows I accessed \\xxx.xxx.xxx.xxx\

Enter in username
Enter in "test" (for the password)

Browser opened right up to my shared folders.

---

