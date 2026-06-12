---
title: "[SOLVED] Command Line {date}"
date: 2008-10-19
forum: New to Ubuntu
---

### Post by BassKozz on 2008-10-19
how can I output the date in a script;
i.e. if I want to create a folder with todays date (in MMDDYYYY format) how could I do this; mkdir date ?
TiA,
-BassKozz

---

### Post by cardinals_fan on 2008-10-19
mkdir %date

---

### Post by BassKozz on 2008-10-19
> **cardinals_fan said:**
> mkdir %date

That just creates a directory "%date" :(

---

### Post by forger on 2008-10-19
heh, it's:
```
mkdir $(date +"%Y%m%d")
```

[http://unixhelp.ed.ac.uk/CGI/man-cgi?date](http://unixhelp.ed.ac.uk/CGI/man-cgi?date)

---

### Post by cardinals_fan on 2008-10-19
> **BassKozz said:**
> That just creates a directory "%date" :(
I use Zsh instead of BASH, and it does that automatically.  I forgot *blushes*

---

### Post by BassKozz on 2008-10-19
thx forger :)

---

