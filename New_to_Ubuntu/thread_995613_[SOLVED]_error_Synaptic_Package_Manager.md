---
title: "[SOLVED] error: Synaptic Package Manager"
date: 2008-11-28
forum: New to Ubuntu
---

### Post by Pappalnator on 2008-11-28
```
E: ERROR: could not create configuration directory /root/.synaptic - mkdir (2 No such file or directory)
```

[COLOR="Red"]Error occurs on opening of:
[LIST]
[*]Synaptic Package Manager
[*]Update Manager
[/LIST][/COLOR]

Upon further investigation there's no 'root' folder under Filesystem in the first place.

I have looked through related threads and their solutions have not worked for me.

Currently running Ubuntu 8.0.4 - Horribly new to this

The system will not allow me to make a new folder in Filesystem, so I cannot create root manually. Under Users and Groups, root has its home folder at /root too. Anyone possibly know a "sudo [command]" to create such a folder?

_Any_ and _All help_ is greatly appreciated!

---

### Post by Paqman on 2008-11-28
```
sudo mkdir /root
```

Any idea how you ended up in this situation? Sounds a bit fishy to me, how would the root account get messed up?

---

### Post by stevek123 on 2008-11-28
I use Ubuntu. when I open filesystem like... Places->Computer->Filesystem it gives a long list that includes a 'root' folder and in it is the .synaptic folder. Root is NOT in the Home folder - and I think for various security reasons it should not be put there... and Synaptic should already be part of the 8.0.4 pkg, found in System->Admin->SynapticPkgMgr. Its not there????

---

### Post by Pappalnator on 2008-11-28
> 
Code:

sudo mkdir /root

Any idea how you ended up in this situation? Sounds a bit fishy to me, how would the root account get messed up?


I just got this computer a few weeks ago, software came pre-installed.

I haven't touched anything in the system other than OpenOffice word processor and Firefox.

My first look into that area... I presume it came without it in some sort of error...

But I probably messed up something in some simple command line code, Im disguistingly new to this.



Thanks for your help, worked.

---

### Post by Paqman on 2008-11-28
> **Pappalnator said:**
> Im disguistingly new to this.


As we all were at some point. I know I still make stupidly noobish mistakes sometimes.

Glad we could help, please mark the thread as "solved" in the thread tools.

---

