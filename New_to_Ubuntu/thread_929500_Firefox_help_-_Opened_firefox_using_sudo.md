---
title: "Firefox help - Opened firefox using sudo"
date: 2008-09-25
forum: New to Ubuntu
---

### Post by saratchandra on 2008-09-25
Hello, I ran firefox using sudo just to check how it looks like and my profile is messed up now. It resets the firefox config everytime I close firefox.

---

### Post by Primefalcon on 2008-09-25
when you run firefox as root your running it as root. which is another user full stop.....

just run it as yourself and forget running it as root

---

### Post by saratchandra on 2008-09-25
No, I opened it as root only once. Now, everytime I run firefox, it is resetting the config.

---

### Post by cobra741 on 2008-09-25
try just running it from a terminal and see what happens (just type firefox and hit enter. 
perhaps your shortcut has managed to get updated to run it as root ). 

if you right click on your firefox icon and click properties it should have the following 

firefox %u

i'm guessing that since you ran firefox as a super user it's become the default user for running the app. 
with luck running it as normal from a terminal will sort this out for you

---

### Post by Primefalcon on 2008-09-25
You may have really messed it up, this is why I say don't run as root unless you have to, as root you can really mess things up....

use this to reinstall it

```
sudo apt-get --reinstall install firefox
```

try what cobra said first though, also try rebooting

---

### Post by cobra741 on 2008-09-25
> **Primefalcon said:**
> You may have really messed it up, this is why I say don't run as root unless you have to, as root you can really mess things up....

use this to reinstall it

```
sudo apt-get --reinstall install firefox
```



good call!! :guitar:

---

### Post by Primefalcon on 2008-09-25
just hope your way fixes it first, sounds logical, guess this is a lesson though not to run as root though unless he has to

---

### Post by saratchandra on 2008-09-25
> **cobra741 said:**
> try just running it from a terminal and see what happens (just type firefox and hit enter. 
perhaps your shortcut has managed to get updated to run it as root ). 

if you right click on your firefox icon and click properties it should have the following 

firefox %u

i'm guessing that since you ran firefox as a super user it's become the default user for running the app. 
with luck running it as normal from a terminal will sort this out for you

Nope, didn't work:(

> **Primefalcon said:**
> You may have really messed it up, this is why I say don't run as root unless you have to, as root you can really mess things up....

use this to reinstall it

```
sudo apt-get --reinstall install firefox
```

try what cobra said first though, also try rebooting

This did not work either. How can I completely reinstall firefox? I've already saved the passwords and bookmarks, so it won't be a problem.

---

### Post by cobra741 on 2008-09-25
sudo apt-get remove firefox
reboot your machine then do   sudo apt-get install firefox

strange problem i must say! :(

---

### Post by Primefalcon on 2008-09-25
that'll leave some remnants

do this

```
sudo apt-get --purge remove firefox
```

then

```
sudo apt-get autoremove
```

after all thats done then simply reinstall it

```
sudo apt-get install firefox
```

---

### Post by saratchandra on 2008-09-25
Fixed it myself. What happened is, when I viewed firefox as root, it changed the owner of the profile.js file to root and user permissions to none. I changed the permissions back and everything is working fine:)

---

### Post by cobra741 on 2008-09-25
nice one buddy!! well done :) 

i certainly wouldn't have thought of that... still have so much to learn about ubuntu :) 

grats!

---

### Post by Primefalcon on 2008-09-25
ahh so it would of reset each time, will have to remember that myself

---

### Post by saratchandra on 2008-09-25
True. Also, I had to change the StartWithLastProfile variable in profiles.ini file to 0 so that it will not open with the root profile.

---

### Post by The Cog on 2008-09-25
A quick fix would probably have been:
**sudo chown saratchandra:saratchandra ~/.mozilla**
(or whatever your username is).

---

### Post by jakechance on 2008-10-02
I did the same thing trying to remove an extension and couldn't understand what went wrong. This really helped me out. I only modified the command slightly

```
sudo chown -R *username*:*usergroup* ~/.mozilla/
```
Note: Obviously replace username and usergroup with whatever yours may be.

That hits everything in the directory in one go. Thanks!

---

### Post by b0b138 on 2008-10-02
Good deal... I was going to say delete your firefox profile (home/user/.mozilla/firefox) Delete both the folder whatever.default and profiles.ini. This would cause a new profile to be created. Or as cog said, resetting the permissions.

---

