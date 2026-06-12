---
title: "Change Sudo Timeout"
date: 2008-04-22
forum: New to Ubuntu
---

### Post by skymera on 2008-04-22
How do i make my sudo timout shorter?

Another family member knows how to use linux and i dont want him sudo-ing my system after i have used sudo shortly before.

Thanks

---

### Post by jakev383 on 2008-04-22
> **skymera said:**
> How do i make my sudo timout shorter?

Another family member knows how to use linux and i dont want him sudo-ing my system after i have used sudo shortly before.

Thanks

Easy enough. Default is 15 minutes.
[http://ubuntuforums.org/showthread.php?p=116697#post116697](http://ubuntuforums.org/showthread.php?p=116697#post116697)

---

### Post by skymera on 2008-04-22
That default is wayyy to big.

15 mins is a long time.
Crazy, i had it at 2mins in 7.10

*Thanks for the link bro.

---

### Post by skymera on 2008-04-22
Ok i see now default line =S

```
 # /etc/sudoers
#
# This file MUST be edited with the 'visudo' command as root.
#
# See the man page for details on how to write a sudoers file.
#

Defaults        env_reset

# Uncomment to allow members of group sudo to not need a password
# %sudo ALL=NOPASSWD: ALL

# Host alias specification

# User alias specification

# Cmnd alias specification

# User privilege specification
root    ALL=(ALL) ALL

# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL
"/etc/sudoers.tmp" 23 lines, 470 characters

```

Thats all i have

---

### Post by bodhi.zazen on 2008-04-22
[http://sudo.rtin.bz/sudo/man/sudoers.html](http://sudo.rtin.bz/sudo/man/sudoers.html)

> timestamp_timeout

    Number of minutes that can elapse before sudo will ask for a passwd again. The default is 5. Set this to 0 to always prompt for a password. If set to a value less than 0 the user's timestamp will never expire. This can be used to allow users to create or delete their own timestamps via sudo -v and sudo -k respectively.

Edit the file with visudo

```
sudo visudo
```

To the defaults line, add :

```
timestamp_timeout=2
```

Like this :

> Defaults        env_reset,timestamp_timeout=2

---

### Post by aysiu on 2008-04-22
Create a separate user account for that family member?

---

### Post by skymera on 2008-04-23
Thanks.

I edited it with nano instead.
Vim is useless.

Thanks lads.

---

### Post by spiderbatdad on 2008-04-23
er...sudoers file must be edited with vi, to avoid breakage. vi is far from useless. One must know a few basic commands in order to use the program, however.

---

### Post by skymera on 2008-04-23
I followed this

```
 sudo EDITOR=/usr/bin/nano visudo 
```

So it's fine.

---

### Post by philinux on 2008-04-23
> **skymera said:**
> Thanks.

I edited it with nano instead.
Vim is useless.

Thanks lads.

You could just use 

sudo -k

which would kill the timestamp.

---

### Post by bodhi.zazen on 2008-04-23
> **skymera said:**
> I followed this

```
 sudo EDITOR=/usr/bin/nano visudo 
```

So it's fine.

FYI: In Ubuntu, by default, visudo uses nano, so this export is not needed.

---

### Post by skymera on 2008-04-23
ok. 
How do i mark this thread as solved?
it was solved a while ago.

---

### Post by Oldsoldier2003 on 2008-04-23
> **skymera said:**
> ok. 
How do i mark this thread as solved?
it was solved a while ago.

solved hasn't been reimplemented since the upgrade. I don't know when it will be back or even if it will. (hopefully it will!)

---

### Post by markjensen on 2008-04-23
> **aysiu said:**
> Create a separate user account for that family member?
Actually, I like this solution the very best of all.

I have my account.  When I leave, the screensaver locks, and my kids (or wife) can "switch user" and log in under their specially created, limited and separate account.

Best solution overall, because they can't even change little things with my desktop/account.

---

### Post by COKEDUDE on 2011-03-09
> **bodhi.zazen said:**
> [http://sudo.rtin.bz/sudo/man/sudoers.html](http://sudo.rtin.bz/sudo/man/sudoers.html)



Edit the file with visudo

```
sudo visudo
```

To the defaults line, add :

```
timestamp_timeout=2
```

Like this :

Thx for this.

---

