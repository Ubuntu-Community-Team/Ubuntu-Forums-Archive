---
title: "Uh-oh...Architecture ??? Hmmmmmm"
date: 2008-12-01
forum: New to Ubuntu
---

### Post by faron45 on 2008-12-01
Okee-dokee...Now I need to know which binary codecs package match my architecture.Hmmmmmm.How do I find out which architecture I'm running under ? Did I even say that right ? Hmmmmmmm.

---

### Post by binbash on 2008-12-01
uname -a

---

### Post by halitech on 2008-12-01
open a terminal and type```
uname -i
```this should give you what type of machine you are running.

---

### Post by faron45 on 2008-12-01
Uh-oh.Terminal tells me-unknown.

---

### Post by halitech on 2008-12-01
what kind of machine do you have? home built? store bought?

---

### Post by roger_1960 on 2008-12-01
Hi

Should be "uname -a" as per binbash

---

### Post by faron45 on 2008-12-01
After doing what Roger said terminal tells me....Linux cybertek 2.6.24-22-generic #1 SMP Mon Nov 24 18:32:42 UTC 2008 i686 GNU/Linux

Store bought

---

### Post by halitech on 2008-12-01
[color=red]i686[/color]
you are running the x86 version.

---

### Post by faron45 on 2008-12-01
I have a choice of i386,amd64,or powerpc to download for "non free codecs".

---

### Post by faron45 on 2008-12-01
Thank you again Hali.So I should download the i386 version then ?

---

### Post by halitech on 2008-12-01
use the i386 version. AMD64 is the 64bit version and powerpc is for macs.

---

### Post by faron45 on 2008-12-01
Thanks again Hali-one more thing how about being sure of which distro I'm using ?? I'm pretty sure it's the Hardy Heron.Very,very sorry to be such a bother everybody.And,Hali-thanks again...I will be sure to mark both posts as solved when done.

---

### Post by Yellow Pasque on 2008-12-01
System -> About Ubuntu will tell you, but since your kernel version is 2.6.24, then that's good confirmation you're running Hardy (unless you had a Hardy install and upgraded to Intrepid and kept the Hardy kernel)

---

### Post by faron45 on 2008-12-01
thanks much Temüjin !!

---

### Post by m_duck on 2008-12-01
Another way is to run the following in a terminal:
```
lsb_release -a
```

---

