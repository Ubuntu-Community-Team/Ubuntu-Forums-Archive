---
title: "[SOLVED] grabbing packages with apt within python"
date: 2008-09-08
forum: Programming Talk
---

### Post by cmat on 2008-09-08
I'm not really sure how to do this but I would like to create a python script that downloads and install packages from the repository. I just need to know how to effectively do this so I can automate an installation. 

I searched the forums and came up empty. Also I would post what I got but I'm on my Windows laptop right now.

---

### Post by Zugzwang on 2008-09-08
Your result will only work on Ubuntu machines or those for which the distribution used has the same package names (so you might have luck with debian-based distros).

In python, you can call apt-get using something like this:
```

info = os.popen("apt-get -d install foobar")
try:
    for line in info:
        if (...) then
            print "Error"
            exit()
finally:
    info.close()

```
You will need to add code for checking the output of apt-get. There might be easier ways to do this. The reason why you didn't find anything is that there's no difference to calling any other program. Note that your script will need to be run using sudo (or as root).

---

### Post by cmat on 2008-09-08
Ah I see. What does the "-d" switch do?

---

### Post by Zugzwang on 2008-09-08
> **cmat said:**
> Ah I see. What does the "-d" switch do?

Something you don't want. My mistake. You can however look it up in the man page of apt-get. However, keep in mind that the user might have to interact with "apt-get" (for example, confirming installation). There's a "-y" switch to automatically assume "yes", but that's potentially dangerous.

---

### Post by Flimm on 2008-09-08
You could use pexpect to handle running
apt-get install foobar

---

