---
title: "failing miserably setting up new server - bind...."
date: 2008-07-06
forum: New to Ubuntu
---

### Post by mspIggy on 2008-07-06
i have been trying non-stop since thursday th 4th to load ubuntu with raid 1 on my dl360... sleeping for 3 and 4 hours here and there until i get this to work

following this [http://www.howtoforge.com/perfect-server-ubuntu8.04-lts-p4](http://www.howtoforge.com/perfect-server-ubuntu8.04-lts-p4) added raid 1 (cannot install grub in drive 2)

one reason or another all installs have failed... this one - i wiped clean drives and started fresh....

i think i am actually close...

for some reason bind is not loading...

no way to start...

if i try to stop i get this

127.0.0.0.1 # 953 connection refused

thoughts?

---

### Post by furlabs on 2008-07-06
I don't know a great deal about bind, but that IP isn't right, it should be 127.0.0.1 which is localhost. Looks like you put an extra 0 in one of your conf files. If you don't know where, try grepping for it:

```

sudo grep -R "127\.0\.0\.0\.1" /

```

The sudo is so you avoid a bunch of permission denied errors. This command will take a while to complete, so maybe catch a quick powernap while you wait :)

---

### Post by mspIggy on 2008-07-06
it is good ip...

sorry i did typo...

i am going to erase drives again and start over...

---

### Post by troutbum13 on 2008-07-06
I had the same error, typos in the config 
run 
```

user@server:~$named -g -p 53

```
the output may tell you of any problems,which files and which lines....good luck

---

