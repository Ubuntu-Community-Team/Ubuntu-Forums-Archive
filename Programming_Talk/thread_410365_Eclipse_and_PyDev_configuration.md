---
title: "Eclipse and PyDev configuration"
date: 2007-04-15
forum: Programming Talk
---

### Post by kikapu on 2007-04-15
Hi to all folks here!

I just installed Eclipse on my (recently installed as well) ubuntu 6.10 and Python 2.5 (i have choose to install Python from Add/Remove software).
I installed PyDev in Eclipse and i want to configure it so it can find the correct interpreter to use. In my Xp (dual boot with ubuntu) installation, this is done by locating c:\python25\python.exe

I am a little frustrated here, how i can do the same thing in ubuntu ? I mean, i found the correct (?) directory to use , i think it is /usr/lib/python2.5 but i cannot figure out which file to give to PyDev so it can use it as Python interpreter...

Can anyone please help me with this ?


Thanks a lot for any help!

---

### Post by Boffbowsh on 2007-04-15
You need to select "/usr/bin/python2.5" in the selector. What I've found works best is using the gcj Java rather than Sun Java. If you've installed PyDev from the Eclipse Update Manager, I'd recommend uninstalling it from there and doing the following at a prompt:
```
sudo apt-get install eclipse-pydev-gcj
```

Hope that helps.

---

### Post by kikapu on 2007-04-16
> **Boffbowsh said:**
> You need to select "/usr/bin/python2.5" in the selector. What I've found works best is using the gcj Java rather than Sun Java. If you've installed PyDev from the Eclipse Update Manager, I'd recommend uninstalling it from there and doing the following at a prompt:
```
sudo apt-get install eclipse-pydev-gcj
```

Hope that helps.

Hmmm..i am at work now (ubuntu is on my home pc) but i do not remember to see any selector so i can choose the one you tell me. The list of "Python interpreters" is empty and i am forced to press "New" and define a new one but i cannot find it on the disk.
Is it matter that i installed it from Eclipse Update Manager ? And where is the Python executable (filename on the disk) so i can search for it and give it to pydev ??

---

### Post by Awareness on 2010-01-08
> **Boffbowsh said:**
> You need to select "/usr/bin/python2.5" in the selector. What I've found works best is using the gcj Java rather than Sun Java. If you've installed PyDev from the Eclipse Update Manager, I'd recommend uninstalling it from there and doing the following at a prompt:
```
sudo apt-get install eclipse-pydev-gcj
```

Hope that helps.

eclipse-pydev-gcj doesnt seem to be in the repository :S

---

### Post by Queue29 on 2010-01-08
> **Awareness said:**
> eclipse-pydev-gcj doesnt seem to be in the repository :S

Ubuntu isn't consistent between 6 month releases much less over the course of 3 years (when this thread was started..)

---

### Post by Awareness on 2010-01-08
> **Queue29 said:**
> Ubuntu isn't consistent between 6 month releases much less over the course of 3 years (when this thread was started..)

Yeah, i know that :)

What i meant was, whats the actual package of pydev now if available at all...

I was able to install it from the plugins menu tho ;)

---

### Post by _0R10N on 2010-04-14
Great!! many thanks!

Kind regards!

_OR10N >>

---

