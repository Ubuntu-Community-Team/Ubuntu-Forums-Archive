---
title: "[SOLVED] synaptic package manager trouble"
date: 2008-06-24
forum: New to Ubuntu
---

### Post by pedro203 on 2008-06-24
Hi all;  I am new to ubuntu and linux
I tried to open the synaptic package manager and got
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
what does this mean and how do I fix it?
Thanx

---

### Post by wormser on 2008-06-24
Applications> Accessories> Terminal

```
sudo dpkg --configure -a
```

---

### Post by bumanie on 2008-06-24
Do the above command in terminal. All the message means is that what ever you were downloading was interrupted. Once you have put in the above command, the download will begin at the point it was interrupted.

---

### Post by pedro203 on 2008-06-24
Thanks very much, that did it!

---

### Post by pedro203 on 2008-06-24
Thanks for letting me know! :)

---

