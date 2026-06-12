---
title: "bash: Permission denied"
date: 2013-03-14
forum: Programming Talk
---

### Post by arneckelmann on 2013-03-14
I just recently installed Ubuntu on my computer and am attempting to run this script:

/home/giulivilab/I-TASSER2.1/I-TASSERmod/runI-TASSER.pl

I received this response:

bash: /home/giulivilab/I-TASSER2.1/I-TASSERmod/runI-TASSER.pl: Permission denied

I'm new to Ubuntu and running commands in general in the terminal. How does one gain permission?

---

### Post by schragge on 2013-03-14
```
sudo chown $USER: ~/I-TASSER2.1/I-TASSERmod/runI-TASSER.pl
chmod +x ~/I-TASSER2.1/I-TASSERmod/runI-TASSER.pl
```

---

### Post by arneckelmann on 2013-03-14
> **schragge said:**
> ```
sudo chown $USER: ~/I-TASSER2.1/I-TASSERmod/runI-TASSER.pl
chmod +x ~/I-TASSER2.1/I-TASSERmod/runI-TASSER.pl
```

Alright, I ran that and tried to rerun the original command, but I'm getting a new error:

bash: /home/giulivilab/I-TASSER2.1/I-TASSERmod/runI-TASSER.pl: /usr/bin/perl^M: bad interpreter: No such file or directory

I checked my bin folder, and perl is installed, just not perl^M...

---

### Post by steeldriver on 2013-03-14
It sounds like your perl script was copy pasted from a Windows environment and has brought the CR-LF line terminations (which render as ^M) with it - you will need to remove those (dos2unix, tr, sed ...)

---

### Post by schragge on 2013-03-14
+1 to what **steeldriver** said. In case you are lost, here is how to get rid of it with sed:
```
sed -i 's/\r//g' ~/I-TASSER2.1/I-TASSERmod/runI-TASSER.pl
```
But I suppose *runI-TASSER.pl* is not the only script in the folder. How was the package unpacked, with *unzip* I presume? *unzip* has the option -a that converts line terminators on the fly.

---

