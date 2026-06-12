---
title: "emphathy instant messenger installation"
date: 2008-09-11
forum: New to Ubuntu
---

### Post by misswham on 2008-09-11
Hi. I just installed empathy and it says no accts configured. to add a new acct you first have to install a backend for each protocol you want to use.

i dont know what this is.

can u tell me what a backend is and how do i install it. i have 2 yahoo id's, one aim, one msn and one google.

---

### Post by Ntweat on 2008-09-11
try using pidgin...

---

### Post by dustigroove on 2008-09-11
I believe that Empathy requires the appropriate Telepathy packages to be installed for the connections you wish to use.

This should give you a list of available components...
```
apt-cache search telepathy
```

Cheers

---

### Post by crazypenguin2008 on 2008-09-11
i had a terriable time with emphathy. i scrapped it and just used the pidgin platform that comes loaded in ubuntu...

---

### Post by Queue29 on 2008-09-26
these work for me:

 ```
sudo apt-get install telepathy-gabble  
```
 for gmail / jabber
 ```
sudo apt-get install telepathy-butterfly
```
 for msn
 ```
sudo apt-get install telepathy-haze
```
 for aim

I don't know how to get the promised audio/video chat working though.

---

### Post by vishzilla on 2008-09-26
> **Queue29 said:**
> 

I don't know how to get the promised audio/video chat working though.

i have a gtalk account. audio video works great. though sometimes the audio is choppy.

---

### Post by vishzilla on 2008-09-26
secondly, if you want to install the latest version. search for the telepathy ppa in launchpad. google 'telepathy ppa launchpad'

---

### Post by sublimation on 2008-10-22
I agree whole-heartedly. The most recent version of Empathy works like a charm for me (8.10 beta Ubuntu Studio). I find that the only real hurdle left for Empathy to be a full-featured client is the addition of sound notifications. As it has taken a lot of inspiration from Pidgin and other multi-service IM clients, I expect it will eventually have a similar toolbox. 

There has been some work done on patches for adding sound. I had found the thread that was changing/hosting the patches awhile back, but now my google searches seem to be in vain. Has anyone else seen this effort? Or tried to compile with the patch?

---

