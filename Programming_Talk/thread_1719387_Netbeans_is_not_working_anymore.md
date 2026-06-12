---
title: "Netbeans is not working anymore"
date: 2011-04-01
forum: Programming Talk
---

### Post by Ibrahim mufeed on 2011-04-01
Hi all,

I was running Netbeans on Ubuntu. I work both Java and C++ on it. Yesterday I was running a heavy Java program and the machine does not respond to any action I do anymore [got stuck]. I tried many times to shut the application off normally but it does not respond. 

I pressed the power button till the machine went down. Since then when I turn on my machine and try to lunch netbeans again, it did not lunch at all, and no error returned.

It's installed under /home/ibrahim/programs/netbeans6.9rc2. and running from terminal says it is not installed. [but it used to say the same even before the problem happened].

Any idea?
Ibrahim

---

### Post by Ibrahim mufeed on 2011-04-01
I found the error, I run the netbeans executable file in a terminal and the error show for a second and then disappeared, it says:
```
Error occurred during initialization of VM
Incompatible minimum and maximum heap sizes specified
```
I edited the netbeans.conf file and now it is working back ;)

Thanks,
Ibrahim

---

