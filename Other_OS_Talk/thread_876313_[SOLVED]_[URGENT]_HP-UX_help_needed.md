---
title: "[SOLVED] [URGENT] HP-UX help needed"
date: 2008-07-31
forum: Other OS Talk
---

### Post by RebounD11 on 2008-07-31
I did a rm command to free some space, but after running 

```
bdf -i
```

I noticed the free space hasn't changed. If someone knows how to free up some disk space, or fix this problem and get that space back (the files are gone, but the space isn't freed) please answer as quickly as possible. 

Thanks in advance for your help.

---

### Post by gjoellee on 2008-07-31
well to free some space you can try:
```
 sudo shutdown now

```
and select free space (or soething like that) and when finished to a normal boot...

however make you might have to be root to use the commands you are using (I am not really into the "malicious" commands, so I don't know if it will help you).

---

### Post by RebounD11 on 2008-07-31
> **gjoellee said:**
> well to free some space you can try:
```
 sudo shutdown now

```
and select free space (or soething like that) and when finished to a normal boot...

however make you might have to be root to use the commands you are using (I am not really into the "malicious" commands, so I don't know if it will help you).

I'm using the root user in this particular situation (I'm not even sure sudo is available for HP-UX). I was thinking of a solution that doesn't require a reboot or shutdown.

Besides I'm not really sure I understand what it is you're trying to tell me... but I feel I forgot to mention that I'm logged in from a remote terminal. That's why I'd like to avoid breaking the link :)

---

### Post by dca on 2008-08-01
Hmmm, were the files in use when you deleted them?  If that's the case I don't think the free space will show until after reboot...
 
...in case of inode corruption you may want to make a back-up of important data prior to reboot in case it runs a file system check that may wipe something important..

---

### Post by SunnyRabbiera on 2008-08-02
> **RebounD11 said:**
> I'm using the root user in this particular situation (I'm not even sure sudo is available for HP-UX). I was thinking of a solution that doesn't require a reboot or shutdown.

Besides I'm not really sure I understand what it is you're trying to tell me... but I feel I forgot to mention that I'm logged in from a remote terminal. That's why I'd like to avoid breaking the link :)

try su then, I am not sure on how HP-UX works but that command should still apply.
And yes, all unux systems have sudo capacity, but not all enable it by default like ubuntu.
Unix based OS's seem to have similar command line structure so hope something works :D

---

### Post by RebounD11 on 2008-08-03
```
rm -f 
``` seems to have done the trick... thamks for you're help all... and indeed the files removed with ```
rm 
``` and didn't free the space were totally gone after reboot.

---

### Post by SunnyRabbiera on 2008-08-03
Well hey it was a stab in the dark, like I said its fortunate that unix based OS's have command line similarities.

---

