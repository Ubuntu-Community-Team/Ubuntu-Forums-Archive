---
title: "How to check the software versions"
date: 2008-04-28
forum: New to Ubuntu
---

### Post by Obs_be on 2008-04-28
How do you check which version is in the add/remove software window?
I want to install thunderbird, and on their website I see the latest version is 2.0.0.12
so I wanted to check which version I'd get when I install it via the add/remove software window.
However I'm not really seeing it anywhere. 
Where do I find it ?

thanks guys

---

### Post by 1875 on 2008-04-28
Use the Synaptic package manager instead, gives you much more info.

---

### Post by gardara on 2008-04-28
You can see the software version in synaptic

System»Administration»Synaptic Package Manager.

And to see the version of installed applications you can enter -version in terminal.

Example:

```
firefox -version
```

---

### Post by c4v3m4n on 2008-04-28
Check in synaptic manager, its easy to install through it.

---

### Post by martyssweb07 on 2008-04-28
sudo aptitude show thunderbird=version

---

### Post by OldManRiver on 2011-12-08
All,

I need the terminal command to show versions of all installed software from server.

Thanks!

OMR

---

### Post by Frogs Hair on 2011-12-08
The command below will generate a list , but not versions .

```
dpkg --get-selections
```

There may be an option in the man page .

```
man dpkg
```

---

### Post by oldos2er on 2011-12-08
Closed. OldManRiver, please don't bump old threads with new questions; start a new thread.

---

