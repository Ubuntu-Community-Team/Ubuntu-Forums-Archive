---
title: "location of rhythmbox config"
date: 2010-03-17
forum: Programming Talk
---

### Post by badperson on 2010-03-17
Hi,
I thought I'd like to take a crack at writing a utility that reads my iTunes lib xml file, and copies my ratings to whatever the equivalent for Rhythmbox is. 

so, is there an equivalent? And do you know where it is? 
thanks!
bp

---

### Post by ssam on 2010-03-18
on karmic/lucid it seems to be
```
.local/share/rhythmbox/rhythmdb.xml
```
i think it used to be in .gnome or .gnome2

---

### Post by badperson on 2010-03-18
that's it...I could have gotten that easily enough myself with: 
> sudo find / -name 'rhythm*.xml'

thanks, 
bp

---

