---
title: "I don't know what happened"
date: 2008-06-01
forum: New to Ubuntu
---

### Post by DarknessEnemy on 2008-06-01
Hi and good afternoon:

I installed one night like 8 games for linux. The other day I was trying to open aMSN but never started, same with pidgin, Firefox had/have some problems. I said "must be the games that I installed" Tried to uninstall them. Started the Synaptic Package Manager but it said: "E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. E: _cache->open() failed, please report." And never started at all. I don't know what to do. And yes, I installed the games from the SPM (In other forums asked).

PD: Sorry about my bad English. I am from Mexico.

UBUNTU Installed: With wubi along with WinXP, 160 GB HDD, Centrino DUO, on a Gateway. (I dont know if it is like the gaming forums XD)

Thanks in advance.

---

### Post by SunnyRabbiera on 2008-06-01
did you try a log out with these games.
also that error you have is a common one, but its easy to resolve.
but first what were the games you had issues with?

---

### Post by HotShotDJ on 2008-06-01
I would bet on```
you must manually run 'dpkg --configure -a' to correct the problem
```Open a terminal (Applications --> Accessories --> Terminal) and run the suggested command as root.  Like this:```
sudo dpkg --configure -a
```

---

### Post by JoshuaRL on 2008-06-01
> **HotShotDJ said:**
> I would bet on```
you must manually run 'dpkg --configure -a' to correct the problem
```Open a terminal (Applications --> Accessories --> Terminal) and run the suggested command as root.  Like this:```
sudo dpkg --configure -a
```

Agreed.  If anything in Ubuntu suggests you run something like that, do it.  It won't hurt anything and it will probably fix stuff.  I would suggest this too:
```

sudo apt-get install -f

```
That should fix (thus the -f tag) any broken packages.  See if that helps.

---

### Post by mokshadaya on 2008-06-01
All of the above is good advice.  If you haven't resolved the issue yet you might try running Firefox from the shell to see if you receive an error or similar.

<Open Terminal from the menu>
<Type> firefox

If you get any errors hopefully they will direct you to what the main issue is.

---

