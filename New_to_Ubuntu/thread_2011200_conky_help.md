---
title: "conky help"
date: 2012-06-26
forum: New to Ubuntu
---

### Post by jllipke on 2012-06-26
I have just installed and configured conky - colors 

when I run it, the CPU temperature does not display, also when I look at the terminal window running it, it is displaying 
```
sh: 1: sensors: not found
```every few seconds.

Is there a way to fix this sensor issue?

---

### Post by zombifier25 on 2012-06-26
Did you install lm-sensors? If not, install it. The run this command:
```
sudo chmod u+s /usr/sbin/hddtemp
```
Then run this command, answering Yes to ALL questions:
```
sudo sensors-detect
```
When you're done, reconfigure conky-colors just in case.

---

### Post by jllipke on 2012-06-27
Ok, I installed lm-sensors. when I type in the first set of code you gave it came up with

```
chmod: cannot access `/usr/sbin/hddtemp': No such file or directory
```

---

### Post by drmrgd on 2012-06-27
> **jllipke said:**
> Ok, I installed lm-sensors. when I type in the first set of code you gave it came up with

```
chmod: cannot access `/usr/sbin/hddtemp': No such file or directory
```

Looks like you need to install the package.  Just run:

```
sudo apt-get install hddtemp
```

---

