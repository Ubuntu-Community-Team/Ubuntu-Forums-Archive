---
title: "Truecrypt will not launch"
date: 2012-08-29
forum: New to Ubuntu
---

### Post by IREinc on 2012-08-29
I am running Ubuntu 12.04 lts and I have installed truecrypt ([with these instructions]("http://mygeekopinions.blogspot.com/2011/06/install-truecrypt-in-ubuntu-1104-natty.html")) however after I install it when I try to run it nothing happens.

I tried to run it from the terminal and get the error message "cannot execute binary file"

Does anyone have any idea what I am doing wrong or how to fix this so Truecrypt will launch?

---

### Post by spjackson on 2012-08-29
One of the possible causes of that error is trying to run a 64-bit executable on 32-bit Linux. What file did you download and is your Ubuntu 32-bit or 64-bit? If you don't know, you can find out with
```

uname -a

```Also, run the file command on the executable you are trying to run.

---

### Post by IREinc on 2012-08-29
Ah, yes thank you, that would be it.  I forgot I put 32bit on my netbook.  I'm used to my desktop which is running 64bit.

I uninstalled and installed the 32bit version and it is working now.  Thanks.

---

