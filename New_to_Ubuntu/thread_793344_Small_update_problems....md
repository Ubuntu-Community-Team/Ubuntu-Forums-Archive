---
title: "Small update problems..."
date: 2008-05-13
forum: New to Ubuntu
---

### Post by shleyman on 2008-05-13
Firstly all my bookmarks in firefox have gone?
no where to be found... which is a big pain...
and youtube isnt working, its just a big grey box where the video should be.
and, java for games arent working either....
any help? 
thanks in advance lovely people

---

### Post by justifier on 2008-05-13
1 - no idea

2 - click on the grey box, if not install flash

3 - same but install flash

---

### Post by shleyman on 2008-05-13
err kinda helpful...
anymore specific instuctions?
install flash is kind of sketchy

---

### Post by JoshuaRL on 2008-05-13
> **shleyman said:**
> err kinda helpful...
anymore specific instuctions?
install flash is kind of sketchy

For firefox, try this:
```

sudo apt-get install --reinstall firefox

```
See if that does it for you.

For the other stuff, you need flash and java.  First, go to System->Administration->Software Sources and make sure everything is enabled except for the CD and source code.  For flash, close any browser you have open and do:
```

sudo apt-get install flashplugin-nonfree

```
For java, go to Add/Remove and search for java.  It should be in there to install.

Hope that helps.

---

### Post by shleyman on 2008-05-13
thanks!!
everythings seems to e working fine, although when youtube firefox closes itself for no reason?
i started it up in terminal so you could see the error message
```
firefox
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
GCJ PLUGIN: thread 0x805e128: NP_GetMIMEDescription
GCJ PLUGIN: thread 0x805e128: NP_GetMIMEDescription return
GCJ PLUGIN: thread 0x805e128: NP_GetValue
GCJ PLUGIN: thread 0x805e128: NP_GetValue: returning plugin name.
GCJ PLUGIN: thread 0x805e128: NP_GetValue return
GCJ PLUGIN: thread 0x805e128: NP_GetValue
GCJ PLUGIN: thread 0x805e128: NP_GetValue: returning plugin description.
GCJ PLUGIN: thread 0x805e128: NP_GetValue return
Segmentation fault

```
thanks again

---

### Post by JoshuaRL on 2008-05-13
I'm not sure what GCJ PLUGIN is, but it has a segfault there.  Try this and see if it helps:
```

sudo apt-get remove --purge flashplugin-nonfree
sudo apt-get install flashplugin-nonfree

```

---

