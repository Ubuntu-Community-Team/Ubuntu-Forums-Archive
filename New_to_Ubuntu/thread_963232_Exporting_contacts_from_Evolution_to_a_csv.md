---
title: "Exporting contacts from Evolution to a csv?"
date: 2008-10-30
forum: New to Ubuntu
---

### Post by MindyRicker on 2008-10-30
I'm a new user to ubuntu and have discovered that I can now sync w/ my phone using Evolution, but cannot find a way to export my contacts from Evolution to a .csv format for other things...is there a way to do this??  Thanks in advance for any help you can give me!  :)

---

### Post by greg@localhost on 2008-10-30
See:

[ How to export Evolution mail contacts to a CSV File]("http://forums.fedoraforum.org/showthread.php?t=142680")

and


[How to export export Evolution contacts to CSV?]("http://ubuntuforums.org/showthread.php?t=162638")

---

### Post by MindyRicker on 2008-12-03
Thank you for the information!!  It was very helpful!

Mindy

---

### Post by OlehWho on 2009-08-17
I don't if this is too little too late, but when I tried exporting to a .csv the evolution exporter crashed.  I ended up exporting to vcard and it worked just fine.

I am using kmail (kontact)  now, which seems nicer than evolution.

---

### Post by frogotronic on 2011-01-23
> **greg@localhost said:**
> See:

[ How to export Evolution mail contacts to a CSV File]("http://forums.fedoraforum.org/showthread.php?t=142680")

and


[How to export export Evolution contacts to CSV?]("http://ubuntuforums.org/showthread.php?t=162638")

The command (in terminal) is

```

/usr/lib/evolution/**2.28**/evolution-addressbook-export --format=csv >contacts.csv
```

[you'll have to change the evolution # (in bold) depending on your Ubuntu version, KK, LL, MM, NN, etc]

The file will show up in your home directory.

- CH

---

