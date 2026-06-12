---
title: "synaptic Package Manger error"
date: 2008-11-24
forum: New to Ubuntu
---

### Post by Kataplun on 2008-11-24
Hello peeps, im new to the ubuntu scene havent been in it for long but im triying to run .rmvd files, i found some easy instructions that recommend the installation of the Mplayer but its not happening, im getting the following error.

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

The error keeps poping up when i open the synaptic package manager

any ideas ?

---

### Post by sisco311 on 2008-11-24
open a terminal(Applications -> Accessories -> Terminal)
and type(or copy/paste):
```
sudo dpkg --configure -a
```
press Enter, input your password and press Enter again.
(there is no visual feedback when you type your password)

---

### Post by jemate18 on 2008-11-24
> **Kataplun said:**
> Hello peeps, im new to the ubuntu scene havent been in it for long but im triying to run .rmvd files, i found some easy instructions that recommend the installation of the Mplayer but its not happening, im getting the following error.

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

The error keeps poping up when i open the synaptic package manager

any ideas ?

after 
```
sudo dpkg --configure -a
```

try
```
sudo apt-get update
```

and 
```
sudo apt-get install mplayer
```

---

### Post by Kataplun on 2008-11-24
you guys rock! thx bros

---

### Post by sisco311 on 2008-11-25
you're welcome.

Please mark the thread solved by selecting 
**Mark this thread as solved** from the [COLOR="Red"]**Thread Tools**[/COLOR].

---

