---
title: "Linux Kernel now at -32 in Ubuntu 14.04. Can we get the revision history?"
date: 2014-07-17
forum: New to Ubuntu
---

### Post by cwmoser on 2014-07-17
My Linux Kernel is now at -32 - thats after I did a **sudo apt-get dist-upgrade**
$  uname  -a
Linux <hostname> 3.13.0-32-generic #47-Ubuntu SMP

I note that some things different between kernel updates - especially between -24 and -30

Is there documentation on the Linux kernel revision history?

Carl

---

### Post by cariboo on 2014-07-18
The first 14.04 point release is due out on July 24th, you may want to do a dist-upgrade then.

---

### Post by plucky on 2014-07-18
> **cwmoser said:**
> My Linux Kernel is now at -32 - thats after I did a **sudo apt-get dist-upgrade**
$  uname  -a
Linux <hostname> 3.13.0-32-generic #47-Ubuntu SMP

I note that some things different between kernel updates - especially between -24 and -30

Is there documentation on the Linux kernel revision history?

Carl

If you have **Synaptic Package Manager** installed and you search for "linux-image" and then for each kernel you select "properties" and under tab "Description" there is included the **Changelog** which should specify what has changed for that kernel.

---

### Post by cwmoser on 2014-07-18
Cariboo907:  Thanks that is good information to know when the next point release of 14.04 is due.
I'll do this on the 24-th and hope it fixes my problem.

Plucky:  Thanks for pointing out where the change log for the Kernel is located.  There is a lot of info there.
Even provides the names of the individuals who work hard and long on Ubuntu.  Shows that there is a lot of
changes for each revision.

After -24 revision, my Crossover software will no longer work properly.  Its based on wine and I get
wineboot consuming a huge amount of CPU time.  Maybe the next point release will fix this.

Carl

---

