---
title: "Reinstall Hardy?"
date: 2008-06-22
forum: New to Ubuntu
---

### Post by DrMilo on 2008-06-22
I've had several problems, really of my own making, in the last few days while migrating to Hardy. I would like to redo the upgrade. Is there a convenient way that I can get the packages that are gone reinstalled and others that I have installed, uninstalled? Thanks in advance.

---

### Post by macaholic on 2008-06-22
Unfortuantely there is no viable way to do this short of manually downgrading every upgraded package, then chaging your software sources. I don't suggest doing that, my suggestion would be to backup your /home directory and do a clean install if the problems are the cumbersome.

---

### Post by sharks on 2008-06-22
Better download a HH image and burn it to the cd.

---

### Post by DrMilo on 2008-06-22
Yes, I may try and burn a CD. I am a little surprised that reinstalling isn't more readily available though.

---

### Post by macaholic on 2008-06-22
> **DrMilo said:**
> Yes, I may try and burn a CD. I am a little surprised that reinstalling isn't more readily available though.
How more readily avalible would you want it? Even if there were a tool that would reinstall without having to burn a cd, you would still lose all your data and download 600 mbs + of data.

---

### Post by DrMilo on 2008-06-23
> **macaholic said:**
> How more readily avalible would you want it? Even if there were a tool that would reinstall without having to burn a cd, you would still lose all your data and download 600 mbs + of data.

Well even Windoze programs have a process where the program is reinstalled, ignoring the parts that agree with the program's requirements and correcting those that don't. I upgraded over the web from Dapper to Hardy with no problem but some things got wrecked by my own actions in trying to solve some problems with Flash and FF3. Reverting to how things were after I 1st upgraded wouldn't be perfect but better than they are now.

---

### Post by nanotube on 2008-07-03
> **DrMilo said:**
> Well even Windoze programs have a process where the program is reinstalled, ignoring the parts that agree with the program's requirements and correcting those that don't. I upgraded over the web from Dapper to Hardy with no problem but some things got wrecked by my own actions in trying to solve some problems with Flash and FF3. Reverting to how things were after I 1st upgraded wouldn't be perfect but better than they are now.

```
sudo apt-get install packagename --reinstall
```
would reinstall individual packages ("programs").
if you want to reinstall a bunch of them... you'd have to get a list of packages you want to reinstall, then feed them to apt-get, and it will reinstall all of them.

---

### Post by kansasnoob on 2008-07-03
I'm sorry to say so but the best and easiest thing to do is a fresh install. Of course you'll want to back up anything you don't want to lose.

---

