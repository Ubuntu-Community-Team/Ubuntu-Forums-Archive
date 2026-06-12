---
title: "Iptables install for i586"
date: 2013-01-22
forum: New to Ubuntu
---

### Post by subspace3 on 2013-01-22
Hi,

I have Ubuntu 10.0.4  running on a Ebox 3350mx. Bit of a newbie with linux and whenever i try to do anything with iptables even -L it comes up with illegal instruction. 

Reinstalled, apt-get remove then install again still no joy. I'm thinking its because my box is running an i586 cpu so I'm guessing it will need a i586 version of iptables to work properly. Am I right to think this? If so, how can I find and install a i586 version? Looked on google, cant find anything. 

Thank you kindly

Tom.

---

### Post by cariboo on 2013-01-23
First, you can tell what kernel you are running using the following command:

```
uname -a
```

In my case I'm running and AMD X2 240 64bit so the output of the above command looks like this:

```
Linux alexis 3.8.0-1-generic #5-Ubuntu SMP Fri Jan 18 15:23:23 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux
```

When you get the error when trying to print out the ufw rules, are you using sudo?

---

