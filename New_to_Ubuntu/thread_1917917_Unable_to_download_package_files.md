---
title: "Unable to download package files"
date: 2012-01-30
forum: New to Ubuntu
---

### Post by Sammax on 2012-01-30
I am tryin to download restricted extras for ubuntu 11.10,but it keeps on giving this error about being unable to download package files.....it says: Failed to fetch........403 forbidden
i have tried changing mirrors but it wont work
pls someone help....

---

### Post by bluexrider on 2012-01-30
try Alt+F2 type terminal and then run this ```
sudo apt-get install ubuntu-restricted-extras
```

---

### Post by Sammax on 2012-01-30
Does not work i get same error
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/universe/libc/libcdaudio/libcdaudio1_0.99.12p2-10_amd64.deb](http://archive.ubuntu.com/ubuntu/pool/universe/libc/libcdaudio/libcdaudio1_0.99.12p2-10_amd64.deb)  403  Forbidden

---

### Post by Bucky Ball on 2012-01-31
Was unaware that package existed for newer releases. Thought it was gone.

---

### Post by bluexrider on 2012-01-31
> **Sammax said:**
> Does not work i get same error
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/universe/libc/libcdaudio/libcdaudio1_0.99.12p2-10_amd64.deb](http://archive.ubuntu.com/ubuntu/pool/universe/libc/libcdaudio/libcdaudio1_0.99.12p2-10_amd64.deb)  403  Forbidden


I can download that file, no issues here

---

### Post by Sammax on 2012-01-31
Anyway guys i tried playing mp3 files and all ,they are working though...i dont know why it shows the error...thanx for helping though

---

### Post by GSXRCarlos on 2012-01-31
i read on wikipedia that it might be called ubuntu-restricted-addons if you're still having problems

---

### Post by Bucky Ball on 2012-01-31
> **GSXRCarlos said:**
> i read on wikipedia that it might be called ubuntu-restricted-addons if you're still having problems

Previously that installs when you install restricted-extras and shouldn't be installed directly.

---

### Post by Sammax on 2012-01-31
I am having problems only with some files 
i am in an institute and it looks like my proxy is blocking them,is there any way i can install them???

---

### Post by bluexrider on 2012-02-03
You could go to this web site and get the .DEB package

[http://www.ubuntuupdates.org/package/core/oneiric/multiverse/base/ubuntu-restricted-extras](http://www.ubuntuupdates.org/package/core/oneiric/multiverse/base/ubuntu-restricted-extras)



For 32bit ```
security.ubuntu.com/ubuntu/pool/multiverse/u/ubuntu-restricted-extras/ubuntu-restricted-extras_56_i386.deb
```

For 64bit ```
security.ubuntu.com/ubuntu/pool/multiverse/u/ubuntu-restricted-extras/ubuntu-restricted-extras_56_amd64.deb
```

---

