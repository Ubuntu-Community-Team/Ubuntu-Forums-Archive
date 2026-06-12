---
title: "Executable Question"
date: 2014-01-26
forum: New to Ubuntu
---

### Post by dylan9 on 2014-01-26
Okay. I downloaded a program for Linux. I unzipped the download. It has an executable file within the folder. When I double click it, nothing happnes. I went to the terminal and did the following commands

```
chmod +x ygopro64
```
```
./ygopro64
```

My response for the second commnad:


```
./ygopro64: error while loading shared libraries: libevent_pthreads-2.0.so.5: cannot open shared object file: No such file or directory
```

Any idea what is up?

---

### Post by whitesmith on 2014-01-26
Sounds like permissions. Please post output from```
ls -l ./ygopro64
```

---

### Post by monkeybrain20122 on 2014-01-26
Because you are missing libevent-pthreads. Install it from synaptic.

---

### Post by dylan9 on 2014-01-26
> **whitesmith said:**
> Sounds like permissions. Please post output from```
ls -l ./ygopro64
```

```
-rwxr-xr-x 1 dylan dylan 7927160 Jan 19 13:53 ./ygopro64
```

---

### Post by monkeybrain20122 on 2014-01-26
It has nothing to do with permission,  just install the package it told you to (libevent-pthreads)

---

### Post by tgalati4 on 2014-01-26
```
apt-cache search libevent-pthreads
```

It might look like:

tgalati4@Mint14-Extensa ~ $ apt-cache search libevent-pthreads
libevent-pthreads-2.0-5 - Asynchronous event notification library (pthreads)

Install it:

```
sudo apt-get install libevent-pthreads-2.0-5
```

Your version may be different.

---

### Post by dylan9 on 2014-01-27
Thanks for the help.

---

