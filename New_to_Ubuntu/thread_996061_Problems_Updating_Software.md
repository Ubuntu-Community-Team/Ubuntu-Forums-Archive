---
title: "Problems Updating Software"
date: 2008-11-28
forum: New to Ubuntu
---

### Post by Mossback on 2008-11-28
I have been using Ubuntu for about six months and haven't had any particular problems until now.

Within the last few days the system indicates there are 18 updates available which, when I bring up the updater, appear to be some updates to Open Office and other security stuff.

The problem is when I run the updater I get the following message:

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 

E: _cache->open() failed, please report.

I tried running the message but all I got was a message about not being a "superuser".

Can anyone help?

Thanks

---

### Post by taurus on 2008-11-28
Just put the sudo in front of the command to run it with root privilege.

```
sudo dpkg --configure -a
sudo apt-get update

```

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by heroidi on 2008-11-28
Applications -> Accessories -> Terminal

> 
sudo dpkg --configure -a
sudo apt-get update


---

### Post by Mossback on 2008-11-28
It worked like a champ!! 

I guess after using one version of Windows or another for 20+ years I have a lot to learn.

Thanks to both of you.

---

### Post by heroidi on 2008-11-28
i feel like you too i was a windows user for years now in ubuntu i feel like a newbie and i think again about those days when i didnot know anything about computers it brought me back in those days and i really enjoy and love it i love ubuntu :D

---

