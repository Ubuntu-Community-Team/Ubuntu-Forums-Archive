---
title: "v4l1compat.so"
date: 2012-08-20
forum: New to Ubuntu
---

### Post by alabamatoy on 2012-08-20
I get the following about 10 times every boot or when I open terminal:  ERROR: ld.so: object '/usr/lib/libv4l/v4l1compat.so' from /etc/ld.so.preload cannot be preloaded: ignored.  What does this mean, and how do I make it go away?  TIA....

---

### Post by NikTh on 2012-08-20
Hi , 
please provide little more info. 
Post the results of 
```
cat /etc/lsb-release && uname -r 
apt-cache policy preload
```Put the results inside ```
 tags . 
[noparse][code]the results here
```[/noparse]
Thanks

---

### Post by alabamatoy on 2012-08-20
```
 herndon@herndon-laptop:~$ cat /etc/lsb-release && uname -r ERROR: ld.so: object '/usr/lib/libv4l/v4l1compat.so' from /etc/ld.so.preload cannot be preloaded: ignored. DISTRIB_ID=Ubuntu DISTRIB_RELEASE=11.10 DISTRIB_CODENAME=oneiric DISTRIB_DESCRIPTION="Ubuntu 11.10" ERROR: ld.so: object '/usr/lib/libv4l/v4l1compat.so' from /etc/ld.so.preload cannot be preloaded: ignored. 3.0.0-24-generic herndon@herndon-laptop:~$ 
```  ```
 herndon@herndon-laptop:~$ apt-cache policy preload ERROR: ld.so: object '/usr/lib/libv4l/v4l1compat.so' from /etc/ld.so.preload cannot be preloaded: ignored. ERROR: ld.so: object '/usr/lib/libv4l/v4l1compat.so' from /etc/ld.so.preload cannot be preloaded: ignored. ERROR: ld.so: object '/usr/lib/libv4l/v4l1compat.so' from /etc/ld.so.preload cannot be preloaded: ignored. ERROR: ld.so: object '/usr/lib/libv4l/v4l1compat.so' from /etc/ld.so.preload cannot be preloaded: ignored. preload:   Installed: (none)   Candidate: 0.6.4-1   Version table:      0.6.4-1 0         500 http://us.archive.ubuntu.com/ubuntu/ oneiric/universe i386 Packages herndon@herndon-laptop:~$  
```

---

### Post by NikTh on 2012-08-21
Hi , 
lets try 
```
sudo apt-get install --reinstall libv4l-0
``` 
Thanks

---

### Post by alabamatoy on 2012-08-21
Followed your suggestion, no joy, same error.  Thanks for suggestion, though.

---

### Post by anewguy on 2012-08-21
Are you trying this for Skype or other internet based phone service?  I noticed that with my install of Skype I had to run some script that installed that .so file, but then when I tried to execute Skype from the command line with that file it bombed out similarly.

---

### Post by NikTh on 2012-08-21
Hi , 
yes @anewguy has a very good point here. 
Did you remember if you added a script somewhere , or a command (or a variable)  in .bashrc ? 
Thanks

---

