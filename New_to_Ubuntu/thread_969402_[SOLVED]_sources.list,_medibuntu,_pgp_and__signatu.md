---
title: "[SOLVED] sources.list, medibuntu, pgp and  signatures couldn't be verified because th"
date: 2008-11-03
forum: New to Ubuntu
---

### Post by Mark_in_Hollywood on 2008-11-03
Upgrade after upgrade, I follow the instructions at:


Medibuntu
[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

thus:

sudo wget [http://www.medibuntu.org/sources.list.d/intrepid.list](http://www.medibuntu.org/sources.list.d/intrepid.list) --output-document=/etc/apt/sources.list.d/medibuntu.list

and

sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update

year after year and upgrade after upgrade, starting with Dapper, I get this in the terminal:

W: GPG error: [http://dl.google.com](http://dl.google.com) stable Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY A040830F7FAC5991
W: You may want to run apt-get update to correct these problems

so I 

sudo aptitude update 

and I get:

W: GPG error: [http://dl.google.com](http://dl.google.com) stable Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY A040830F7FAC5991
W: You may want to run apt-get update to correct these problems


How do I correct this?

**Why does it always happen?**

---

### Post by ThrobbingBrain66 on 2008-11-03
The error has nothing to do with Medibuntu.  It's saying a Google repo you have has no public key.
This is Google's Linux Debian/Ubuntu repo:
```
deb http://dl.google.com/linux/deb/ stable non-free
```
Use this code to import Google's public key:
```
sudo wget -q -O - https://dl-ssl.google.com/linux/linux_signing_key.pub | apt-key add -
```
then
```
sudo apt-get update
```

---

### Post by drs305 on 2008-11-03
That link in your post is for Google Pack, and the link says it only works in windows XP or vista. It is probably a link you don't want or need in your sources.list unless you alter it. At least it is not a medibuntu problem.

---

### Post by Mark_in_Hollywood on 2008-11-03
This is just too weird. I just got a googleearth update from Syn Pkg Mrg. (SPM). My Google Earth is working just fine.

When I tried to use aptitude to install acroread, it got to 92% finished, and stopped dead in it's tracks. Eventually, I ctrl-c and did sudo aptitude autoclean, but didn't see the acroread package.

Please forget google for a moment, it's medibuntu that's the problem.

========

10 minutes after posting the above:
I 'commented' the google pack line in /etc/apt/sources.list, did sudo aptitude update and I now do not get the pgp error message.

---

### Post by drs305 on 2008-11-03
Aptitude autoclean will only remove cached packages that can't be downloaded any longer. So you could use:
```
sudo aptitude clean acroread
*or *
sudo aptitude purge acroread
*and then try again:*
sudo aptitude install acroread
*or* 
sudo aptitude reinstall acroread
```

If it still hangs up let us know. Note: Another user just successfully installed acroread via the Adobe site, but then I just installed acroread myself a few hours ago from within synaptic without any problems.

---

### Post by Mark_in_Hollywood on 2008-11-03
Goofey gooffee goffeeyyy

It was some "glitch" that resolved itself. I have no idea what happened. Thanks, community.

---

