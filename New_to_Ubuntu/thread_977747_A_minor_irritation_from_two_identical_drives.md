---
title: "A minor irritation from two identical drives"
date: 2008-11-10
forum: New to Ubuntu
---

### Post by brawd on 2008-11-10
Hi there,

I have two identical DVD writers installed on an AMD64 running Ubuntu 8.04. 
When I go to use them to write my files it's a fifty/fifty guess as to which is the one with the disc in.
Anyway, can I rename them so that the selection box that comes up when I write my files shows - say - Drive1 and Drive2. I tried to simply rename them, but that didn't work, then I did change one of the little icons so that one has a star and the other doesn't which is fine on my desk but that doesn't solve the textbox selection problem.
It's only a matter of time before I write a file to the wrong DVD and all the repercussions from that ruin my life.

In case your wondering I didn't buy two DVD writers, I only needed one. My well meaning sons bought me one each. I didn't like to disappoint them.

regards,
brawd

---

### Post by Pro-reason on 2008-11-10
Open a terminal, and then post the output of these commands:

```

cat /etc/fstab
ls -l /dev/scd* /dev/cd*

```

---

### Post by quirks on 2008-11-10
The model is hardcoded in the device itself and apparently, there is no way to overwrite it. Brasero (or whatever burning program you use) probably reads the model from some file in the sysfs (/sys). I have just tried to overwrite the model of my own DVD drive using a udev rule. I found the file using this command:
```
find /sys -name model -exec echo -n \{\}\:" " \; -exec cat \{\} \;
```
But overwriting it via a udev rule fails with a "Permission denied". Manually overwriting it with an ordinary ```
echo "some name" > /sys/the/path/to/the/device/model
``` fails with the same error message. I suppose, it is impossible to overwrite it.

I am sorry, brawd, but I don't think it is possible (without changing the source code of Brasero, which is always an option in the open source world - but a cumbersome one).

@Pro-reason: I hope you have a good idea and this is going somewhere. Good luck!

---

