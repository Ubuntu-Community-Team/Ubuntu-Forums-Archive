---
title: "Weekly maintenace?"
date: 2008-07-18
forum: New to Ubuntu
---

### Post by flogger on 2008-07-18
Back in my XP days (which officially ended last week), each week I would...

- Run malware scans
- Check updates
- Clean out caches and temp folders
- Scan registry
- Make sure unneeded services were not running in the background
- Take out any unneeded programs starting on the system start up

What do people do for typical maintenance in Ubuntu?

I know about cleaning up the installation packages, that there is no registry to scan for errors and that some type of defrag utility runs every 30 starts. I havn't found a all in one program to clear caches/temp folders or do any other house keeping.

What do you guys suggest to keep the system in tip top shape?

Nick

---

### Post by hyper_ch on 2008-07-18
> **flogger said:**
> What do people do for typical maintenance in Ubuntu?

Run updates ;)
```

sudo apt-get update && sudo apt-get upgrade && sudo apt-get autoremove

```

---

### Post by pedro_orange on 2008-07-18
Clean the dust out of the fans :)

---

### Post by TSJason on 2008-07-18
eat pie
drink scotch
be merry

---

### Post by Canis familiaris on 2008-07-18
```
sudo apt-get autoremove
```
It will remove all the uneeded dependencies.

But it will matter only if you regularly install and uninstall software through the repos.

---

### Post by Sealbhach on 2008-07-18
> **flogger said:**
> 

- Make sure unneeded services were not running in the background
- Take out any unneeded programs starting on the system start up



You can manage this in the Sessions utility (from the System menu).


.

---

### Post by philinux on 2008-07-18
Unix/Linux file systems keep fragmentation to a minimum. 

See this tip.
[http://www.itworld.com/nls_unixfrag040929](http://www.itworld.com/nls_unixfrag040929)

---

### Post by indytim on 2008-07-18
On a weekly basis, I do:
1.  Run my repository updates.
2.  Make an image file of the partition containing both the Ubuntu ops as well as the "/home" partition using Partimage.

IndyTim

---

### Post by deadgobby on 2008-07-18
sudo fsck

Gobby

---

### Post by gn2 on 2008-07-18
Software maintenance? I don't do any. None. Zilch.

I back up my files to a network drive as I go.

---

### Post by houbysoft.xf.cz on 2008-07-18
Nothing. That's one of my reasons to switch to Linux :)

---

