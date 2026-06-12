---
title: "error synapatic manager"
date: 2008-07-11
forum: New to Ubuntu
---

### Post by alien8predator on 2008-07-11
synaptic package manager error:


E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.


how can I fix this?

---

### Post by alien8predator on 2008-07-11
by running:  'dpkg --configure -a' 

I suppose, but where do I run it? terminal?.......?

---

### Post by avtolle on 2008-07-11
From the CLI (terminal)```
sudo dpkg --configure -a
```To access the CLI, go to Applications>>Accessories>>Terminal. When you type in your password, you will have no visual feedback; that is normal. Type in the password and press Enter, and let it do its thing. Post any error messages for review.

---

