---
title: "how to check for space remaining on hard drive"
date: 2008-11-17
forum: New to Ubuntu
---

### Post by raymondvillain on 2008-11-17
New to Ubuntu.  Running 8.10 on a desktop.

If I open a terminal, is there a Unix command that will inform me of the amount of space that is in use, and how much I have left available?

---

### Post by jodef on 2008-11-17
From terminal type:

```
df -h
```

or you could go Application -> Accessories -> Disk Usage Analyzer (gui)

---

### Post by rampageoberon on 2008-11-17
Use the "df" command, and to get it in 'human form' use -h

```
df -h
```


Enjoy

---

### Post by kansasnoob on 2008-11-17
If you really want to see what's used in each partition I'd install gparted:

```
sudo apt-get install gparted
```

It'll then show up in System > Administration > Partition Editor:

[ATTACH]93062[/ATTACH]

Just be careful! They don't call it "Editor" for no reason.

You can resize, delete, or otherwise mess up partitions if you're so inclined!

---

