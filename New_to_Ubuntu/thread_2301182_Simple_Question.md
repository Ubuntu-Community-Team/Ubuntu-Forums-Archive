---
title: "Simple Question"
date: 2015-10-31
forum: New to Ubuntu
---

### Post by shane_faulkinbury2 on 2015-10-31
I'm trying to install GNS3 and I get this error while in the Terminal.  "sudo: apt&#8208;get: command not found'  I've used apt-get many times, why am I getting that today?

---

### Post by oldfred on 2015-10-31
No colon. :)

sudo apt-get install application-name

---

### Post by shane_faulkinbury2 on 2015-10-31
Sorry

---

### Post by bab1 on 2015-10-31
> **shane_faulkinbury2 said:**
> I'm trying to install GNS3 and I get this error while in the Terminal.  "sudo: apt&#8208;get: command not found'  I've used apt-get many times, why am I getting that today?
See if apt-get is really there with this```
whereis apt-get
```...I get this```
$ whereis apt-get
apt-get: /usr/bin/apt-get /usr/bin/X11/apt-get /usr/share/man/man8/apt-get.8.gz

```

---

### Post by steeldriver on 2015-10-31
Did you copy-paste the command from a web page into your terminal? maybe a non-ascii character such as a non-breaking hyphen crept in - if so, try typing the command out

---

### Post by howefield on 2015-10-31
> **steeldriver said:**
> .. maybe a non-ascii character such as a non-breaking hyphen crept in - if so, try typing the command out

+1 Looks like it if it was from here : [https://community.gns3.com/thread/5471](https://community.gns3.com/thread/5471)

```
hugh@wily-laptop:~$ sudo apt&#8208;get install python3&#8208;setuptools
[sudo] password for hugh: 
sudo: apt&#8208;get: command not found
hugh@wily-laptop:~$ 
```

---

### Post by bab1 on 2015-10-31
> **howefield said:**
> +1 Looks like it if it was from here : [https://community.gns3.com/thread/5471](https://community.gns3.com/thread/5471)

```
hugh@wily-laptop:~$ sudo apt&#8208;get install python3&#8208;setuptools
[sudo] password for hugh: 
sudo: apt&#8208;get: command not found
hugh@wily-laptop:~$ 
```
+1 for both @steeldriver and @howfield.  On the other hand gns3 is available as a package.  I'd just do this```
sudo apt-get install gns3
```

---

### Post by shane_faulkinbury2 on 2015-10-31
This what I get running a whereis apt-get  "> apt-get: /usr/bin/apt-get /usr/share/man/man8/apt-get.8.gz

The copy/paste thing was the problem.  After typing everything in everything is working now!

Thanks a lot!

---

### Post by oldos2er on 2015-10-31
Please mark the thread 'Solved' under Thread Tools at the top of the page. Thanks!

---

### Post by shane_faulkinbury2 on 2015-11-01
Thanks bab1, that worked great!  I now have GNS3 1.3.11 installed and working!  :p

---

### Post by bab1 on 2015-11-01
> **shane_faulkinbury2 said:**
> Thanks bab1, that worked great!  I now have GNS3 1.3.11 installed and working!  :p

How about marking the thread 'Solved' under Thread Tools at the top of the page.  This helps others know what problems have had a successful resolution.

---

