---
title: "if i switch to 8.10..."
date: 2008-10-31
forum: New to Ubuntu
---

### Post by fignig on 2008-10-31
will all my settings/files be intact/enabled? or will i have to backup all my stuff?

---

### Post by Catalyst2Death on 2008-10-31
Well...

If you have a dedicated home partition and you re-install *without* formatting it then, mostly yes. 

If you are going to upgrade, without doing a fresh install, then yes but you should do a fresh install

If you   are going to back up your home folder, re-install and then put your home folder back in place, then mostly yes.

Mostly yes because programs won't be there but their settings will... So after re-installing things everything will be like it was.  On the other hand if there are new versions of the software and they changed the way they hold their settings on disk, then some programs may not work right.  You could spend an awful lot of time trying to figure out why a program won't run when its because you have an old  settings file hanging out on your hard drive, this is unlikely but possible...

---

### Post by fignig on 2008-10-31
> **Catalyst2Death said:**
> Well...

If you have a dedicated home partition and you re-install *without* formatting it then, mostly yes. 

If you are going to upgrade, without doing a fresh install, then yes but you should do a fresh install

If you   are going to back up your home folder, re-install and then put your home folder back in place, then mostly yes.

Mostly yes because programs won't be there but their settings will... So after re-installing things everything will be like it was.  On the other hand if there are new versions of the software and they changed the way they hold their settings on disk, then some programs may not work right.  You could spend an awful lot of time trying to figure out why a program won't run when its because you have an old  settings file hanging out on your hard drive, this is unlikely but possible...

what about updating through the update manager?

---

### Post by th89 on 2008-10-31
I just did an upgrade through the update manager yesterday, and everything was retained, including personal setting, files, and even drivers. Backup to be safe, but you shouldn't need it if you do it through the update manager.

---

### Post by OrangeCrate on 2008-10-31
> **fignig said:**
> will all my settings/files be intact/enabled? or will i have to backup all my stuff?

As others have already pointed out, if you upgrade, yes, they will be intact. (Though you should always backup your files. If they're not complex, the simplest backup method is to simply drag and drop them on to a stick.)

-----

BTW, upgrading is the preferred way of moving from release to release, not a clean install.

Please read from post #96 is this thread, for guidance:

[http://ubuntuforums.org/showthread.php?t=936696&page=10](http://ubuntuforums.org/showthread.php?t=936696&page=10)

> "We do NOT advise a clean install every time you want to upgrade. The upgrade path receives far more testing and attention than the clean install path. The official recommended method for moving to a new version of Ubuntu is to use a supported upgrade procedure!" - jdong

---

### Post by fignig on 2008-10-31
> **Catalyst2Death said:**
> Well...

If you have a dedicated home partition and you re-install *without* formatting it then, mostly yes. 

If you are going to upgrade, without doing a fresh install, then yes but you should do a fresh install

If you   are going to back up your home folder, re-install and then put your home folder back in place, then mostly yes.

Mostly yes because programs won't be there but their settings will... So after re-installing things everything will be like it was.  On the other hand if there are new versions of the software and they changed the way they hold their settings on disk, then some programs may not work right.  You could spend an awful lot of time trying to figure out why a program won't run when its because you have an old  settings file hanging out on your hard drive, this is unlikely but possible...

...so that means, this is horrible advice. ty.

---

### Post by SunnyRabbiera on 2008-10-31
it is always a good idea to back up your stuff before updating, I suggest saving up for a external hard drive.

---

### Post by fignig on 2008-10-31
what if i don't have an external or a usb stick to save it to? anything else like norton ghost for linux?

---

### Post by richg on 2008-10-31
> **th89 said:**
> I just did an upgrade through the update manager yesterday, and everything was retained, including personal setting, files, and even drivers. Backup to be safe, but you shouldn't need it if you do it through the update manager.

I just did the same to two hard drives. 

Rich

---

### Post by CatKiller on 2008-10-31
> **fignig said:**
> what if i don't have an external or a usb stick to save it to?

CD writer?

---

### Post by fignig on 2008-11-01
nvm i found it..it was the software sources.

---

### Post by OrangeCrate on 2008-11-01
If you're using 8.04, you need to go into Software Sources, and change the update option from LTS only, to normal releases.

Edit:

We were posting at the same time. Glad you found it.

---

### Post by richg on 2008-11-01
Since I have a use cable modem for the 'Net, it was easy. I clicked Alt F2 which opens the command line. Type in "update-manager -d" without the quotation marks, hit enter and follow instructions. No CD burner needed.
Grab a cuppa and relax.


Rich

---

