---
title: "Failed to exec method /usr/lib/apt/methods/ - missing https"
date: 2012-09-08
forum: New to Ubuntu
---

### Post by carfield on 2012-09-08
Hi all, I cannot run "apt-get upgrade", I think it is because the file /usr/lib/apt/methods/https is missing. I've try to copy this file from other computer but it saying binary cannot execute. 

How can I recover this file?

---

### Post by drmrgd on 2012-09-08
Couple things:

1.  When you copied the file, did you verify that the permissions were set correctly on the new copy?  Sometimes the executable bit won't be set on a copy from another source.  

2.  I'm not sure if there are any other components missing, and maybe just adding the https file won't be enough.  You might try to reinstall the apt-http-transport package to see if it will recover the all the missing / corrupt components.

3.  I've read that this error can sometimes be due to the sources.list file not being correct or corrupt in some way.  In particular, the 'http://" part is not correct on some lines.  You might also post your /etc/apt/source.list here for us to verify that it's OK just to be on the safe side (you can also just rebuild it just for kicks if you prefer).

Hope that helps!

---

### Post by carfield on 2012-09-10
> **drmrgd said:**
> Couple things:

1.  When you copied the file, did you verify that the permissions were set correctly on the new copy?  Sometimes the executable bit won't be set on a copy from another source.  

2.  I'm not sure if there are any other components missing, and maybe just adding the https file won't be enough.  You might try to reinstall the apt-http-transport package to see if it will recover the all the missing / corrupt components.

3.  I've read that this error can sometimes be due to the sources.list file not being correct or corrupt in some way.  In particular, the 'http://" part is not correct on some lines.  You might also post your /etc/apt/source.list here for us to verify that it's OK just to be on the safe side (you can also just rebuild it just for kicks if you prefer).

Hope that helps!

Thanks a lot, actually it is my /etc/apt/sources.list contain a respository which is not valid any more, after I removing that entry, it working fine

---

