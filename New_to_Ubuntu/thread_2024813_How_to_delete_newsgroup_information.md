---
title: "How to delete newsgroup information?"
date: 2012-07-14
forum: New to Ubuntu
---

### Post by petrus66 on 2012-07-14
Hello,

I installed PAN newsreader untill I got bored with it and uninstalled it with synaptic with complete removal option.

I was suprised when I installed PAN again and it seems to remember the visited newsgroups from the last installation.

Its not a big deal but it is little annoying when I dont have a control or a clue where the nttp data is stored so I can delete them when I want to.

I run Bleachbit but it does not have support for PAN.

Any ideas how to delete newsgroup data.

I'm running 10.04

---

### Post by Zill on 2012-07-14
petrus66:  As with other applications, configuration (and newsgroup) data is in a hidden directory in your home.  Hidden directories are signified by a leading dot in the directory name or viewed with "Ctrl-h" in the Nautilus GUI file manager.

To permanently remove *all* Pan configuration and newsgroup data enter the following command:
```
rm ~/.pan -r
```

---

### Post by petrus66 on 2012-07-14
Thank you Zill, that did it.
Never thought to search for a hidden file.

---

### Post by Zill on 2012-07-14
> **petrus66 said:**
> Thank you Zill, that did it.
Never thought to search for a hidden file.
You're welcome. :-)

Most apps tuck user data in these hidden files so this is worth remembering.  "Purging" an app simply removes a program and its system-wide config files in /etc.  The user-data hidden files generally have to be deleted manually.

---

