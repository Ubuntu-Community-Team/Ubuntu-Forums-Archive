---
title: "Accidently changed permissions on filesystem"
date: 2008-06-17
forum: New to Ubuntu
---

### Post by RequinB4 on 2008-06-17
Please, I deserve a slap for playing around with nautilus as root permissions late at night.

Basically, for about 80% of the files in /, I right clicked - properties - permissions - and for "other users" instead of "---" I switched it to None, which, of course, made it so my user (and all of the programs it is running) can't access a lot of the files they need.

/home is normal, thankfully.

I know i can probably figure it out by going into recovery mode as root, but I don't want to mess around with chmod as root any furthur.

Help would be much appreciated, as my computer is basically unusable for normal tasks.

:rolleyes:

---

### Post by neurostu on 2008-06-17
do a chmod on root but use a recursive argument.

Something like:
```

sudo chmod -r 744 /

```
that should work but it'll take some time.

Good luck!

Consult the man page if you need to:
[http://www.ss64.com/bash/chmod.html](http://www.ss64.com/bash/chmod.html)

---

### Post by RequinB4 on 2008-06-17
> **neurostu said:**
> do a chmod on root but use a recursive argument.

Something like:
```

sudo chmod -r 744 /

```
that should work but it'll take some time.

Good luck!

Consult the man page if you need to:
[http://www.ss64.com/bash/chmod.html](http://www.ss64.com/bash/chmod.html)

I figured as much.  So I'll have no trouble setting read to world, write and execute to root?  What directories should that not apply to?

I've spent some time with the man page, and I'm not convinced I get the syntax (that really could use some further explination on the side note).

---

### Post by bodhi.zazen on 2008-06-17
For basic syntax on permissions :

[http://www.zzee.com/solutions/linux-permissions.shtml](http://www.zzee.com/solutions/linux-permissions.shtml)

[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

To be honest you are best off re-installing. *most* of the permissions in /etc are 644, but some are not. /bin is 755 . It takes longer to go through / /etc /usr ... and set all the permissions.

for example you do NOT want /etc/shadow to have permissions of 644.

---

### Post by RequinB4 on 2008-06-17
Ok... Yeah, going through each file in /etc doesn't sound fun.

Crazy idea - to make it easier, couldn't I copy /home (since it's unaffected) into a seperate partition.  Then reinstalling wouldn't be such a pain... I know someone has a masterful tutorial for this, would be much appreciated :)

Edit - wouldn't it be easier to just use the existing partition for /home?  IE make a / partition, install there, delete all but /home on the origional, mount and change permissions?

---

### Post by ladr0n on 2008-06-17
Just copy /home to the new partition.  When re-installing, set that partition's mountpoint to /home.  Obviously, you don't want to format it.  Complete the install and you're ready to go.

---

### Post by bodhi.zazen on 2008-06-17
If you are going to copy/move home best follow a tutorial (at least for the initial steps):

[http://ubuntu.wordpress.com/2006/01/29/move-home-to-its-own-partition/](http://ubuntu.wordpress.com/2006/01/29/move-home-to-its-own-partition/)
        [http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

Once you have copied /home, just set the partition as /home WITHOUT formatting when you re-install.

---

