---
title: "how do i fix this error?"
date: 2006-07-26
forum: Repositories &amp; Backports
---

### Post by ExMachina on 2006-07-26
```

admin@ubuntu:~$ sudo -i
Password:
root@ubuntu:~# apt-get install xubuntu-desktop

```

It starts installign stuff then 

```


Need to get 12.5MB/277MB of archives.
After unpacking 940MB of additional disk space will be used.
Do you want to continue [Y/n]? Y
Get:1 http://us.archive.ubuntu.com dapper/main ttf-arphic-uming 0.1.20060513-1 [12.5MB]
Fetched 12.5MB in 1m20s (156kB/s)
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/t/ttf-arphic-uming/ttf-arphic-uming_0.1.20060513-1_all.deb  MD5Sum mismatch
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?

```

I think it a repo error.. How do I fix?

---

### Post by mlind on 2006-07-26
Try if changing all instances of us.archive.ubuntu.com to archive.ubuntu.com on /etc/apt/sources.list helps.

---

### Post by ExMachina on 2006-07-26
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper main restricted
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper-updates main restricted
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe


That my source.list... i removed US. but now it cnat find the packets <.<
I just wanna install >.<

---

### Post by mlind on 2006-07-26
Try to make working sources.list using
[http://www.ubuntulinux.nl/source-o-matic](http://www.ubuntulinux.nl/source-o-matic)

---

### Post by ExMachina on 2006-07-26
deb [http://mirror.anl.gov/pub/ubuntu/](http://mirror.anl.gov/pub/ubuntu/) dapper main restricted
deb-src [http://mirror.anl.gov/pub/ubuntu/](http://mirror.anl.gov/pub/ubuntu/) dapper main restricted
deb [http://mirror.anl.gov/pub/ubuntu/](http://mirror.anl.gov/pub/ubuntu/)  dapper-updates main restricted
deb-src [http://mirror.anl.gov/pub/ubuntu/](http://mirror.anl.gov/pub/ubuntu/) dapper-updates main restricted
deb [http://mirror.anl.gov/pub/ubuntu/](http://mirror.anl.gov/pub/ubuntu/)  dapper universe
deb-src [http://mirror.anl.gov/pub/ubuntu/](http://mirror.anl.gov/pub/ubuntu/) dapper universe
deb [http://mirror.anl.gov/pub/ubuntu/](http://mirror.anl.gov/pub/ubuntu/)  dapper-backports main restricted universe multiverse
deb-src [http://mirror.anl.gov/pub/ubuntu/](http://mirror.anl.gov/pub/ubuntu/) dapper-backports main restricted universe multiverse
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe

i made a this one i HOPE it works if not ill use soure of matic

---

### Post by mlind on 2006-07-26
Well, here's the base repository list that I'm using

```

# Ubuntu supported packages (packages, GPG key: 437D05B5)
deb http://archive.ubuntu.com/ubuntu dapper main restricted
deb http://archive.ubuntu.com/ubuntu dapper-updates main restricted
deb http://security.ubuntu.com/ubuntu dapper-security main restricted

# Ubuntu supported packages (sources, GPG key: 437D05B5)
#deb-src http://archive.ubuntu.com/ubuntu dapper main restricted
#deb-src http://archive.ubuntu.com/ubuntu dapper-updates main restricted
#deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted

# Ubuntu community supported packages (packages, GPG key: 437D05B5)
deb http://archive.ubuntu.com/ubuntu dapper universe multiverse
deb http://archive.ubuntu.com/ubuntu dapper-updates universe multiverse
deb http://security.ubuntu.com/ubuntu dapper-security universe multiverse

# Ubuntu community supported packages (sources, GPG key: 437D05B5)
#deb-src http://archive.ubuntu.com/ubuntu dapper universe multiverse
#deb-src http://archive.ubuntu.com/ubuntu dapper-updates universe multiverse
#deb-src http://security.ubuntu.com/ubuntu dapper-security universe multiverse

#Ubuntu backports
deb http://archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse
# deb-src http://archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse

```

---

### Post by ExMachina on 2006-07-26
Same error... using source o matics source list... 
ive NEVER had this much torubl usally take me 20-50 min to install

---

### Post by ExMachina on 2006-07-27
i just did a FRESH install..

SAME file failed. NONE of the source lsit work what am i doign wrong?

---

### Post by mlind on 2006-07-27
> **ExMachina said:**
> i just did a FRESH install..

SAME file failed. NONE of the source lsit work what am i doign wrong?

Fresh install because some sources failed to download? Are you serious?
There could problem with the md5sum that's fingerprint for the file. Download file manually and install it if you can't find a working repository mirror.

---

### Post by ExMachina on 2006-07-27
the install was only 2 days old i dint loose anythign only took 30 min to reinstall anyway. Ill try ..

so wget <file> ? how do i install it?
This is just annoying ive never had trouble. Fianlly upgrading server and now i have trouble.

---

### Post by mlind on 2006-07-27
To download, try
```

aptitude download ttf-arphic-uming

```
or 
```
wget http://us.archive.ubuntu.com/ubuntu/pool/main/t/ttf-arphic-uming/ttf-arphic-uming_0.1.20060513-1_all.deb

```

Then install using
```

sudo dpkg -i *package* 

```

---

### Post by ExMachina on 2006-07-28
problems fixed thats eveyrone

---

### Post by ExMachina on 2006-07-28
All Better ^^ Server Is Up!

---

