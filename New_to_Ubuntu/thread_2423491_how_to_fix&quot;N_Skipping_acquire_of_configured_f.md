---
title: "how to fix:&quot;N: Skipping acquire of configured file 'universe/binary-i386/Packages' &quot;"
date: 2019-07-24
forum: New to Ubuntu
---

### Post by azajit on 2019-07-24
Hello.
when i run this command "sudo apt-get update" ,i m getting this : "N: Skipping acquire of configured file 'universe/binary-i386/Packages' as repository 'http://miktex.org/download/ubuntu bionic InRelease' doesn't support architecture 'i386' ".
how to slove this issue?
Thank you for any help you can provide.:)


```
ajit@az-pc:~$ sudo apt-get update
Ign:1 [http://dl.google.com/linux/chrome/deb](http://dl.google.com/linux/chrome/deb) stable InRelease
Hit:3 [http://dl.google.com/linux/chrome/deb](http://dl.google.com/linux/chrome/deb) stable Release
Hit:5 [http://np.archive.ubuntu.com/ubuntu](http://np.archive.ubuntu.com/ubuntu) cosmic InRelease                     
Hit:6 [http://np.archive.ubuntu.com/ubuntu](http://np.archive.ubuntu.com/ubuntu) cosmic-updates InRelease             
Get:7 [http://np.archive.ubuntu.com/ubuntu](http://np.archive.ubuntu.com/ubuntu) cosmic-backports InRelease [74.6 kB] 
Hit:2 [https://ftp.yz.yamagata-u.ac.jp/pub/CTAN/systems/win32/miktex/setup/deb](https://ftp.yz.yamagata-u.ac.jp/pub/CTAN/systems/win32/miktex/setup/deb) bionic InRelease
Get:8 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) cosmic-security InRelease [88.7 kB]    
Fetched 163 kB in 2s (91.1 kB/s)                          
Reading package lists... Done
N: Skipping acquire of configured file 'universe/binary-i386/Packages' as repository 'http://miktex.org/download/ubuntu bionic InRelease' doesn't support architecture 'i386'
```

---

### Post by deadflowr on 2019-07-24
You add [arch=amd64] to the sources entries for that mirror,
it'll look something like
```
deb [arch=amd64] http://miktex,org/download/ubuntu/ bionic *something*
```
You'll need to see which entries need it in the sources.list file.
(Note, I used *something* as a generic reference as that last entry can be a number of different things such as main stable unstable testing, and so on, 
you'll need to have whatever the entry you see for it is and not use *something*. So we're clear on that)

A quick guide and reference on how to about apt and sources:
[https://help.ubuntu.com/community/Repositories/CommandLine]("https://help.ubuntu.com/community/Repositories/CommandLine")

---

### Post by oldos2er on 2019-07-24
So are you running 18.04 or 19.04? It's generally a bad idea to mix repos for different versions.

---

### Post by CatKiller on 2019-07-24
> **oldos2er said:**
> So are you running 18.04 or 19.04? It's generally a bad idea to mix repos for different versions.

It's even worse than that: cosmic cuttlefish is 18.10, which is no longer supported as of about a week ago.

---

