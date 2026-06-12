---
title: "evolution update?"
date: 2008-06-09
forum: New to Ubuntu
---

### Post by lunaluna on 2008-06-09
did you have an an update for evolution recently? 
because my update manager doesn't show anything...

---

### Post by crossedout on 2008-06-09
There was an evolution update on June 7.

-Xout

---

### Post by lunaluna on 2008-06-09
yeah i've had this one ok
but i heard from various people another one today..
my update manager sometimes gets a little crazy(i suppose) so i just want verify

maybe there is a command through terminal where i could check out the version in order to compare it somewhere to the web(and where?) ? (like the "about" gui but with more info)

---

### Post by ukripper on 2008-06-09
> **lunaluna said:**
> did you have an an update for evolution recently? 
because my update manager doesn't show anything...

There was evolution update with kernel 24.19 update

---

### Post by lunaluna on 2008-06-09
> **ukripper said:**
> There was evolution update with kernel 24.19 update

was this today?

---

### Post by ukripper on 2008-06-09
> **lunaluna said:**
> was this today?

Found some announcement of evolution vulnerabilties. There was  an update for this
[http://ubuntuforums.org/showthread.php?t=820881](http://ubuntuforums.org/showthread.php?t=820881)

Haven't found any today!

---

### Post by lunaluna on 2008-06-09
it's really strange because i had 2 updates within 2 days for evolution 
why is this happenning...
is there a command or whatever to check the exact version of evolution except the "about" because it just not useful...   ?

---

### Post by ukripper on 2008-06-09
> **lunaluna said:**
> it's really strange because i had 2 updates within 2 days for evolution 
why is this happenning...
is there a command or whatever to check the exact version of evolution except the "about" because it just not useful...   ?

You can try this command:
```
dpkg -l evolution
```
it is 'ell' not 1

or this:
```
dpkg -L evolution
```

---

### Post by lunaluna on 2008-06-09
> **ukripper said:**
> You can try this command:
```
dpkg -l evolution
```
it is 'ell' not 1

or this:
```
dpkg -L evolution
```

it gave me the following:
```

Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Installed/Config-f/Unpacked/Failed-cfg/Half-inst/t-aWait/T-pend
|/ Err?=(none)/Hold/Reinst-required/X=both-problems (Status,Err: uppercase=bad)
||/ Name           Version        Description
+++-==============-==============-============================================
ii  evolution      2.22.2-0ubuntu groupware suite with mail client and organiz

```

---

### Post by lunaluna on 2008-06-09
so the above means...?

---

### Post by ukripper on 2008-06-09
That is correct version which i am also using.

---

### Post by ukripper on 2008-06-09
you can also check your downloaded packages through apt in:
```
ls -al /var/apt/cache/archives/
```

---

