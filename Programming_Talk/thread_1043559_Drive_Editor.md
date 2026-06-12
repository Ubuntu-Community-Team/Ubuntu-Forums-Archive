---
title: "Drive Editor"
date: 2009-01-18
forum: Programming Talk
---

### Post by Salgat on 2009-01-18
Can anyone recommend a drive editor that will display the entire drive's contents, including the MBR in hexidecimal? There are plenty of hex editors out there for individual files, but I'm having trouble finding one that specifically has this (similar to HxD's drive editor).

---

### Post by Mr.Macdonald on 2009-01-19
probably not what you want, but Python! Much more powerful!

to print a drive do this

```

python "print open('/dev/sd??', 'r').read()"

```

type Ctrl^C (or Z) to stop it.


If you learn python you could edit the drive with a few lines of code

---

