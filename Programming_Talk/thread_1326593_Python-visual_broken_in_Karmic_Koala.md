---
title: "Python-visual broken in Karmic Koala"
date: 2009-11-14
forum: Programming Talk
---

### Post by debsankha on 2009-11-14
Can anybody please tell me how to get the latest python-visual 5.11 working in Karmic Koala? The default package in karmic repository is simply broken. Whenever I import the module un the interpreter, python crashes showing the brief message:
```

Segmentation fault
core dumped

```
Installing the version of python visual in karmic repository (version 3.2.9) worked for me but I was rather looking forward to using the new features like transparency in the new vpython. This is more surprising because I installed this package 2-3 months back on Jaunty Jackalope from the developmental repository and then it was working just fine.

---

### Post by bosto3tudiant on 2009-11-23
> Installing the version of python visual in karmic repository (version 3.2.9) worked for me

Hello debsankha,

Could you give a pointer about how you installed the working older version?  Switching to Karmic also broke my visual python, and I was hoping to use it for a research project due in 2 weeks so I'd rather not wait for a patch.

Many thanks!

---

### Post by bosto3tudiant on 2010-01-03
Visual has been a great package; thank you for many hours--if anyone manages to find a fix for this, I'd love to hear--I still miss it :-(

---

### Post by Jbike on 2010-03-21
visual-python doesn't work for me either...  it just crashes. All I did was install python-visual 1:5.11-1 and ran the following test code  in IDLE for pythonv2.6 :

from visual import *

redbox=box(pos=vector(4,2,3), size=(8.,4.,6.),color=color.red)

greenball=sphere(pos=vector(4,7,3), radius=2, color=color.green)



Hope someone can find the problem... maybe I did something wrong? I don't see any of the older versions in synaptic, and I would rather not install from vpython directly. 

Thanks,Jbike

---

### Post by lavinog on 2010-03-21
[https://bugs.launchpad.net/ubuntu/+source/python-visual/+bug/429015](https://bugs.launchpad.net/ubuntu/+source/python-visual/+bug/429015)

I noticed this in dmesg after importing visual:
```

python[4570]: segfault at 18 ip 00007fce99fefbc4 sp 00007fff1b1109e0 error 6 in libstdc++.so.6.0.13[7fce99f2a000+f2000]

```

---

### Post by lavinog on 2010-03-22
filed a new bug report since the issue is slightly different in that it occurs during the import:
[https://bugs.launchpad.net/ubuntu/+source/python-visual/+bug/543899](https://bugs.launchpad.net/ubuntu/+source/python-visual/+bug/543899)

Also tested this in lucid beta-1 and it still occurs.

---

### Post by Jbike on 2010-03-22
Thanks for  your help. Can I assume that when it is fixed, that a synaptic update will bring in the solution, or should I check somewhere else for the fix? 

Jbike

---

### Post by lavinog on 2010-03-22
> **Jbike said:**
> Thanks for  your help. Can I assume that when it is fixed, that a synaptic update will bring in the solution, or should I check somewhere else for the fix? 

Jbike

It might, if it gets fixed before lucid is released.
Otherwise, you will have to install the fixed package manually, or with a ppa.

Usually only security bugs will get fixed in future updates.
There may be a possibility it would be pushed when 10.04.1 is pushed, but I wouldn't hold my breath.

---

### Post by Jbike on 2010-03-28
For all others interested in python-visual (Vpython) and are too impatient to wait for Lucid,  add the ppa from here:

 [https://launchpad.net/~ajmitch/+archive/ppa](https://launchpad.net/~ajmitch/+archive/ppa) 

which will pick up the fixed boost1.38 libraries AND add:

 libgtkglextmm-x11-1.2-dev from synaptic. 

Thanks Lavinog for submitting the bug report, and showing me the way to the patch. 

It's all working now, thanks

Jbike

---

