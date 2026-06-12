---
title: "[SOLVED] uname -v  output"
date: 2008-08-06
forum: New to Ubuntu
---

### Post by adamogardner on 2008-08-06
I am reading that uname -v offers the kernal version.  What is the output here mean?
adamogardner@CRONUS:~$ uname -v
#1 SMP Fri Jul 11 23:41:49 UTC 2008

---

### Post by finer recliner on 2008-08-06
you may have read a typo. 'uname -a' gives the kernel version (not -v)

---

### Post by adamogardner on 2008-08-06
-a is always --all isn't it?  here's what man uname puts out:

DESCRIPTION
       Print certain system information.  With no OPTION, same as -s.

       -a, --all
              print  all  information,  in the following order, except omit -p
              and -i if unknown:

       -s, --kernel-name
              print the kernel name

       -n, --nodename
              print the network node hostname

       -r, --kernel-release
              print the kernel release

       -v, --kernel-version
              print the kernel version

---

### Post by Cypher on 2008-08-06
The output of "uname -v" shows the number of times that particular Kernel has been re-built. The stock Kernel from Ubuntu should almost always be at #1. The other information will be the build time/date and whether it's SMP Kernel or not.

---

### Post by decoherence on 2008-08-06
> **adamogardner said:**
> I am reading that uname -v offers the kernal version.  What is the output here mean?
adamogardner@CRONUS:~$ uname -v
#1 SMP Fri Jul 11 23:41:49 UTC 2008

That's the date when the kernel was compiled.

You probably want 'uname -r' -- the release name.

---

### Post by adamogardner on 2008-08-06
oh thanks that makes things clear.

---

### Post by tuxxy on 2008-08-06
I f you just remember to us -a this should display every bit on info

---

### Post by Dedoimedo on 2008-08-06
Hello,
Type either "man uname" or "info uname" in terminal, and you'll get the documentation pages, with detailed explanations.
Dedoimedo

---

### Post by Dr Small on 2008-08-06
Try:
```
uname -r
```

---

### Post by adamogardner on 2008-08-06
> **tuxxy said:**
> I f you just remember to us -a this should display every bit on info

thanks but If all I do is strive to remember -a then I'll never become the master.

---

