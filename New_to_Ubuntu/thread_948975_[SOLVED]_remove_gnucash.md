---
title: "[SOLVED] remove gnucash"
date: 2008-10-15
forum: New to Ubuntu
---

### Post by Gumpers on 2008-10-15
I would like to know how to remove gnucash and all of its components from ubunty 8.04. what would the command be in terminal? Thanks, Gumpers

---

### Post by bobnutfield on 2008-10-15
> sudo apt-get remove gnucash

This is assuming you installed it via apt-get.  To remove everything associated with it:

> sudo aptitude --purge gnucash

---

### Post by Gumpers on 2008-10-15
> **bobnutfield said:**
> This is assuming you installed it via apt-get.  To remove everything associated with it:

The sudo aptitude--purge gnucash did not work: command not found. the remove command did work. is the purge command to get ride of any files that were left over from the remove command? thanks gumpers

---

### Post by jemate18 on 2008-10-15
try ```
sudo apt-get purge yourPackageToRemove
```

---

### Post by Hendrixski on 2008-10-15
:-) though you don't *need* the terminal.  You can just unselect it in synaptic and it uninstalls itself.

---

### Post by Gumpers on 2008-10-15
> **Gumpers said:**
> The sudo aptitude--purge gnucash did not work: command not found. the remove command did work. is the purge command to get ride of any files that were left over from the remove command? thanks gumpers

the command sudo apt-get purge guncash worked! thanks to all. gumpers

---

