---
title: "Errors on up date"
date: 2012-04-13
forum: New to Ubuntu
---

### Post by Rich42 on 2012-04-13
I am using Ubuntu 11.10 and these will not install and stopped update. 

I Deselected them and other updates installed.

1/ Why was this? and what should I do with these below, what are they for?

Thanks Rich42

Requires installation of untrusted packages 

The action would require the installation of packages from unauthenticated sources.


Library for accessing GData webservices - common data files
libgdata-common(Size 110 kB)

Library for accessing GData webservices – shared libraries
libgdata13 (Size 253 kB)

libgdata-common libgdata13

---

### Post by matt_symes on 2012-04-13
Hi

Sounds like you are missing a GPG key. Open a terminal and type

```
sudo apt-get update
```Copy and paste the output from the terminal back here between code tags 

[noparse] ```
 like this 
``` [/noparse] 

to get output like this

```
 like this 
```Kind regards

---

### Post by Rich42 on 2012-04-14
There is more in terminal, would you like it all?
```

Reading package lists... Done
W: GPG error: http://gb.archive.ubuntu.com oneiric Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: GPG error: http://archive.canonical.com oneiric Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: GPG error: http://archive.canonical.com oneiric Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: GPG error: http://gb.archive.ubuntu.com oneiric-backports Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
richard@richard-desktop:~$ 

```

---

