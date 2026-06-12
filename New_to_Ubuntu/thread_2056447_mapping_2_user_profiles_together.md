---
title: "mapping 2 user profiles together"
date: 2012-09-11
forum: New to Ubuntu
---

### Post by supererki on 2012-09-11
Hi and sorry for not googling myself, im in a hurry.

So due to the fact that a friend of mine had 32bit version of ubuntu installed on 64bit archidecure i had to reinstall the system. Fortunately it had the root mounted in one partition and /home mounted to another, it was easy to reinstall the system and leave the user data untouched. 
Anyway. At the moment on the /home partition there are 2 user accounts, which really should be the same. Can i map them together? Should i use 'ls' or is it ok to simply move files from 1 account to another? Or is there any better solution? 

thanks. erki

---

### Post by ThrashManiac on 2012-09-12
Hi ! 

Before you are going to merge these two catalogs, make sure, there's no .* (starting with dot) file or folder left. 

Those are application settings and variables. Those can cause you totally unstable system. 

I recommend you to back up all those files into a separate catalog, and them delete them from the user catalogs. After that you can merge them and perform a clean install.

---

