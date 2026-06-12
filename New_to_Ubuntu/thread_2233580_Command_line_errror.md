---
title: "Command line errror"
date: 2014-07-09
forum: New to Ubuntu
---

### Post by amateur2 on 2014-07-09
Tried running the below command
sudo apt -get install kubuntu-desktop
Error Shown - E: Command line option 'g' [from -get] is not known.
New to ubuntu please help

---

### Post by The Cog on 2014-07-09
The command should be
```
sudo apt-get install kubuntu-desktop
```
There is no space in "apt-get" : apt-get is the command, the name of the installer program.

---

### Post by Lars Noodén on 2014-07-09
There should be no space between 'apt' and '-get', it is one word.

If you start typing a command and press tab, the shell will show you what your choice are.  If there is only on choice then it will complete the word for you.

```

sudo apt<tab>
sudo apt-g<tab>

```

---

