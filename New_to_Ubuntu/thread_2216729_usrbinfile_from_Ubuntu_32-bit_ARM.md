---
title: "/usr/bin/file from Ubuntu 32-bit ARM"
date: 2014-04-13
forum: New to Ubuntu
---

### Post by Aung_Thiha on 2014-04-13
I want "file" binary which is usually located at /usr/bin/ . Can someone please upload me that binary?

thanks in advance

---

### Post by texaswriter on 2014-04-13
> **Aung_Thiha said:**
> I want "file" binary which is usually located at /usr/bin/ . Can someone please upload me that binary?

thanks in advance


```
user@usr:/usr/bin$ sudo apt-get install file
[sudo] password for user: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
file is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```

Have you tried ```
sudo apt-get install --reinstall yourappnamehere
``` ? 

Let us know how this works.

Just FYI, you shouldn't ask for binaries over the internet. I'm sure nobody on this forum would steer you wrong, but using the repositories is a measure of protection for you. Good luck!

---

