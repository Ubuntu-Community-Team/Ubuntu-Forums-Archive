---
title: "Chrome Won't Start"
date: 2012-05-26
forum: New to Ubuntu
---

### Post by doppel.ganger on 2012-05-26
When I try to open Google Chrome, the icon pulses for a bit, then just stops and nothing happens. When I try to open it from the terminal, I get:
```
Segmentation fault (core dumped)
```
Has anybody had this problem/knows how to fix it?

Thanks,
DG

---

### Post by irv on 2012-05-26
Sounds like a bad install. Completely remove Chrome and then do a fresh install.

---

### Post by doppel.ganger on 2012-05-26
```
thomas@Thomas-HP-Mini-5101:~$ sudo apt-get purge google-chrome
[sudo] password for thomas: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Virtual packages like 'google-chrome' can't be removed
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
thomas@Thomas-HP-Mini-5101:~$
```

---

### Post by vasa1 on 2012-05-26
Why do you have this:
**Virtual packages** like 'google-chrome' can't be removed ???

---

### Post by holycow131415 on 2012-05-26
did you install it from the software center?

try to remove it while in the software center.

---

### Post by irv on 2012-05-27
Also check for broken packages from the package manager.
[ATTACH]218776[/ATTACH]

---

### Post by jeddi00 on 2012-06-29
try 
```
sudo apt-get purge google-chrome-stable
``` for download off website
or
```
sudo apt-get purge google-chrome-beta
```for beta users
or
```
sudo apt-get purge google-chrome-unstable
```for the unstable version

then download and install chrome again (id go for stable if i were you) and try running it then

hope this helps,



jeddi00 :biggrin:

---

### Post by irv on 2012-06-30
> **doppel.ganger said:**
> When I try to open Google Chrome, the icon pulses for a bit, then just stops and nothing happens. When I try to open it from the terminal, I get:
```
Segmentation fault (core dumped)
```
Has anybody had this problem/knows how to fix it?

Thanks,
DG

You posted this 4 weeks ago, did you ever get this problem fixed. And if so mark this thread solved. And let us know how you fixed it so it can help others.

---

### Post by francoeurdavid on 2012-11-15
To remove chrome you might try :
```
sudo apt-get purge google-chrome-stable
```

For me, removing chrome and installing didn't solve the problem, I would still get the Segmentation Fault error.

---

### Post by monkeybrain2012 on 2012-11-15
> **holycow131415 said:**
> did you install it from the software center?

try to remove it while in the software center.

Chrome is not in the software centre.

---

### Post by monkeybrain2012 on 2012-11-15
Which Ubuntu and which kernel?

Maybe you are hit by this bug.

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/972285](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/972285)

If this is the case boot into an older kernel (you can choose from the boot screen if you haven't removed it) and delete the problematic one (3 files to delete, the kernel image and usually two headers, check the version number in synaptic)

---

### Post by deadflowr on 2012-11-15
> **monkeybrain2012 said:**
> Chrome is not in the software centre.

Sure it is.
Go to the Ubuntu Software Center and click the arrow next to the Installed button, choose google, and then click the arrow next to google in the item pane. google-chrome-stable will show up.

---

