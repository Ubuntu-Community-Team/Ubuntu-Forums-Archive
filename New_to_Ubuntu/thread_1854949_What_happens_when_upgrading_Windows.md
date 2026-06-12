---
title: "What happens when upgrading Windows?"
date: 2011-10-05
forum: New to Ubuntu
---

### Post by ashhab2010 on 2011-10-05
i am upgrading windows from xp to win7...... will ubuntu(wubi) still work????

---

### Post by sandyd on 2011-10-05
> **ashhab2010 said:**
> i am upgrading windows from xp to win7...... will ubuntu(wubi) still work????

When using Wubi, ubuntu adds an entry to C:\boot.ini to give you an option to boot Ubuntu. Windows will change this file to reflect the upgrade to windows 7, so if you want, you can copy the line that refers to Ubuntu, and back it up. 

After installing Ubuntu, you can just put the line back, and everything should just work fine.

---

### Post by ubudog on 2011-10-05
Hey there, are you reinstalling Windows (like installing Win7, removing WinXP)?  Or are you upgrading using the built in upgrade tool?

---

### Post by bodhi.zazen on 2011-10-05
> **ashhab2010 said:**
> i am upgrading windows from xp to win7...... will ubuntu(wubi) still work????

In my experience , windows upgrades do not always go well.

I would also point out, wubi is intended only for testing, and if you are going to use Ubuntu long term I would do a standard install.

So, IMO, you should back up your data, partition your hard drive, and try the upgrade, If you have a problem, re-install XP or 7 and do a fresh standard install of Ubuntu.

---

### Post by Jerry N on 2011-10-05
An upgrade from XP to Win 7 is actually a complete reinstall with the option of archiving user files and settings.  Installed programs are lost, just as any other reinstall.  I would expect Wubi to be lost as well.  

It is possible to do an actual upgrade from XP to Vista and then upgrade from Vista to Win 7.  That is generally considered to be a bad idea though.  I have never had any good experiences in upgrading from one release of Ubuntu to another either.

Jerry

---

### Post by Mark Phelps on 2011-10-05
There is no official "upgrade" from XP to Win7 that preserves your apps.  All the "upgrade" will do is save some settings and user data.

Laplink DOES have a third-party product they sell that claims to allow the same kind of in-place upgrade from XP to Win7 that was previously available from XP to Vista.  But, I've not tried it and can not vouch for it as a result.

Also BEFORE you attempt the "upgrade" you should run the MS Upgrade Advisor tool to see what you have that will NOT upgrade.  It's not perfect (nothing IS) but it will at least flag stuff that will not work in Win7.

---

