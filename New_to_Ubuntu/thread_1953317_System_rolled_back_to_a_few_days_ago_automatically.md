---
title: "System rolled back to a few days ago automatically - what's the deal?"
date: 2012-04-06
forum: New to Ubuntu
---

### Post by jcdenton_riseup on 2012-04-06
Yesterday, when I turned on my PC I noticed that the movie I've downloaded a few days ago is missing. I tried an extensive search, but came up with nothing. Then, when I opened a text file I'm currently working on, everything I've written over the past couple of days was gone, even though I saved my progress.

Any ideas?

---

### Post by mikewhatever on 2012-04-06
Using Windows, right? If so, you might want to disable system restore.
Ubuntu has no functionality of the sort, you can only 'roll back' from a previously made backup.

---

### Post by jcdenton_riseup on 2012-04-06
No, I'm using Ubuntu. At first I thought maybe I just forgot to save my progress before quitting and that maybe I deleted the movie myself for some reason, but that just can't be it.

Also, I'm currently reading 'Getting Started with Ubuntu 10.04, Second Edition' (that's the version I chose for now) and upon stopping for the time being I always edit the file name to include the number of the page I'm currently at (eg. 'Getting Started with Ubuntu 10.04, Second Edition, p. 35') so as to know where should I pick it up again. That also 'rolled back' - I remember changing the .pdf name to say 'p. 129' but now it says 'p. 36', which was days ago.

> **mikewhatever said:**
> Using Windows, right? If so, you might want to disable system restore.
Ubuntu has no functionality of the sort, you can only 'roll back' from a previously made backup.

---

### Post by maniandram on 2012-04-06
> **jcdenton_riseup said:**
> Yesterday, when I turned on my PC I noticed that the movie I've downloaded a few days ago is missing. I tried an extensive search, but came up with nothing. Then, when I opened a text file I'm currently working on, everything I've written over the past couple of days was gone, even though I saved my progress.

Any ideas?

Check your file system by running
```

sudo touch /forcefsck

```
and rebooting.
The filesystem will be checked after rebooting
:guitar::KS:p

---

### Post by jcdenton_riseup on 2012-04-07
Ran the command, file system has been checked - don't know if any problems were found. Will see how it works now. Thanks for the help!

> **maniandram said:**
> Check your file system by running
```

sudo touch /forcefsck

```and rebooting.
The filesystem will be checked after rebooting
:guitar::KS:p

---

