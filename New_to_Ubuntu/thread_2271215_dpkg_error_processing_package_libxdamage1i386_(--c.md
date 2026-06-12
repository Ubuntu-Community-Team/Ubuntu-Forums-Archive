---
title: "dpkg: error processing package libxdamage1:i386 (--configure)"
date: 2015-03-28
forum: New to Ubuntu
---

### Post by paulie.squid on 2015-03-28
> dpkg: error processing package libxdamage1:i386 (--configure):
 package is in a very bad inconsistent state; you should
 reinstall it before attempting configuration
Errors were encountered while processing:
 libxdamage1:i386
E: Sub-process /usr/bin/dpkg returned an error code (1)

This is the output after running sudo apt-get upgrade and the same when trying sudo apt-get install libxdamage1:i386
sudo apt-get --remove purge yields similar results

What does it mean and is it something I should be worried about?
Some cursory googling tells me it has something to do with graphical i/o if I'm not completely missing the point of all those words. I changed my focus-on-mouse setting to 'sloppy', so could that be it?

---

### Post by ajgreeny on 2015-03-28
Try ```
sudo apt-get install --reinstall libxdamage1:i386
```
No promises that it will work, but you can not use the **install** command for a package already installed, you have to use **--reinstall** option instead.

---

### Post by paulie.squid on 2015-03-28
>E: Command line option --reinstall is not understood


Should I just reinstall? This is a fresh start for me, so no sensitive data on the computer or anything else that I can't afford to lose.

---

### Post by ajgreeny on 2015-03-29
Did you use the command exactly as I showed it in post #2, with both words, ie, **install --reinstall**?  Using just **--reinstall** will not be understood.
```
sudo apt-get install --reinstall libxdamage1:i386
```

I have just done this very thing on my own Xubuntu-14.04.2-64bit system and it worked without fault, so your command must either be incorrect or it is still the original problem that is causing the problem, though I would expect a different error if that was the case.

---

