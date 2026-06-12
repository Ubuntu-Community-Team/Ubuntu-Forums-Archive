---
title: "Simple bash script help"
date: 2010-12-15
forum: Programming Talk
---

### Post by mad_max0204 on 2010-12-15
Guys,

I'm trying to make simple bash script that checks if vmware VMs are running and if they are not then start them.
Since I use 4 VMs it can be done by reading output of "vmrun list" which is a list of running VMs and looks something like this:

Total running VMs: 2
/home/VM1.vmx
/home/VM2.vmx

Thanks for any help

Max

---

### Post by j.netbreed on 2010-12-15
something like...

```

ps ax | grep [m]yvmwareprocessname
if [ $? = 1 ]; then
/path/to/run/vmware

```

important to keep the parentheses around the first letter of the process name so as not to return the grep process

---

### Post by Arndt on 2010-12-15
> **j.netbreed said:**
> something like...

```

ps ax | grep [m]yvmwareprocessname
if [ $? = 1 ]; then
/path/to/run/vmware

```

important to keep the parentheses around the first letter of the process name so as not to return the grep process

There is 'pgrep', too.

---

### Post by aeronutt on 2010-12-15
> **j.netbreed said:**
> something like...

```

ps ax | grep [m]yvmwareprocessname
if [ $? = 1 ]; then
/path/to/run/vmware

```

important to keep the parentheses around the first letter of the process name so as not to return the grep process

I learn a new trick every day!

---

### Post by mad_max0204 on 2010-12-15
EDIT: Scratch that it does work.

What is 'pgrep' and what would be the difference ?

---

### Post by j.netbreed on 2010-12-16
```
man pgrep
```
basically pgrep looks up processes, you could change my above example to...
```

pgrep vmwareprocessname
if [ $? = 1 ]; then
/path/to/vmwarerunprog

```
...at its rawest

---

