---
title: "Mount truecrypt vol partition after OS reinstall?"
date: 2014-05-16
forum: New to Ubuntu
---

### Post by p.callan on 2014-05-16
Setup :
Partition 1: Ubuntu 13.10 (broken GUI. Only root shell available)
Partition 2: Truecrypt volume

Is it possible to mount the truecrypt volume if I was to format Partition 1 and install Ubuntu 14.04 & truecrypt on it? (Do NOT guess!)
Also, how can it be mounted in root shell?


If I could just get a quick yes or no answer to the first question, I can move on and install 14.04 (if the answer is yes). Thanks.

---

### Post by p.callan on 2014-05-16
The answer to Q1 is Yes. It works just as before.

---

### Post by wallaroo on 2014-05-16
There are command-line options available.
To see all the options just run 
```
truecrypt --help
```
The most basic command-line mount will be ..
```
truecrypt --password=[your_tc_password] [your_tc_volume] [your_preferred_mountpoint]
```

---

