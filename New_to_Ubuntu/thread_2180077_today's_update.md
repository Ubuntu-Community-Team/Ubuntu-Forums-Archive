---
title: "today's update"
date: 2013-10-11
forum: New to Ubuntu
---

### Post by czgirb on 2013-10-11
```

czgirb@czgirb:~$ sudo apt-get update
[sudo] password for czgirb: 
Hit http://download.bitdefender.com bitdefender Release.gpg                    
Hit http://deb.playonlinux.com precise Release.gpg                             
...
...
...
Hit http://id.archive.ubuntu.com precise-backports/multiverse Translation-en                                                                                               
Hit http://id.archive.ubuntu.com precise-backports/restricted Translation-en                                                                                               
Hit http://id.archive.ubuntu.com precise-backports/universe Translation-en                                                                                                 
Fetched 2,167 kB in 55s (39.1 kB/s)                                                                                                                                        
W: Failed to fetch http://packages.medibuntu.org/dists/precise/free/binary-i386/Packages  404  Not Found

W: Failed to fetch http://packages.medibuntu.org/dists/precise/non-free/binary-i386/Packages  404  Not Found

E: Some index files failed to download. They have been ignored, or old ones used instead.
czgirb@czgirb:~$ 

```
Why? What it means? How can it be solved?

---

### Post by grahammechanical on 2013-10-11
You should read this thread

[http://ubuntuforums.org/showthread.php?t=2174110](http://ubuntuforums.org/showthread.php?t=2174110)

The internet address that Update Manager is searching for to download any updates to medibuntu cannot be found. It most probably no longer exists.

[http://gauvain.pocentek.net/node/61](http://gauvain.pocentek.net/node/61)

---

### Post by czgirb on 2013-10-11
> **grahammechanical said:**
> You should read this thread

[http://ubuntuforums.org/showthread.php?t=2174110](http://ubuntuforums.org/showthread.php?t=2174110)

The internet address that Update Manager is searching for to download any updates to medibuntu cannot be found. It most probably no longer exists.

[http://gauvain.pocentek.net/node/61](http://gauvain.pocentek.net/node/61)

Thank you very much ... my ubuntu was re-updated and the problem SOLVED
Thank you

---

