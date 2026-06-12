---
title: "Repository Error"
date: 2006-07-20
forum: Repositories &amp; Backports
---

### Post by mattfender on 2006-07-20
In effort to get movies and such working I tried to add some repositories now I get this error

E: Type 'http://archive.canonical.com/ubuntu' is not known on line 38 in source list /etc/apt/sources.list
E: The list of sources could not be read.
Go to the repository dialog to correct the problem


If anyone could help (if I need to give more info let me know) that would be great

---

### Post by scxtt on 2006-07-20
does the entire entry in /etc/apt/sources.list look like this:

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) dapper-commercial main

???

---

### Post by mattfender on 2006-07-20
No, it just reads

[http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu)

---

### Post by scxtt on 2006-07-20
well my 1st bit of advice would be to edit it to look like what i posted ... i've installed opera using that repo ...

---

### Post by mattfender on 2006-07-20
How do I get permission to edit it in terminal?

---

### Post by aysiu on 2006-07-20
[quote=mattfender]How do I get permission to edit it in terminal?[/quote]```
sudo cp /etc/apt/sources.list /etc/apt/sources.list_backup
sudo nano /etc/apt/sources.list
```

---

### Post by mattfender on 2006-07-20
thanks it worked, but now I have another error

E: Type 'wget' is not known on line 39 in source list /etc/apt/sources.list

---

### Post by aysiu on 2006-07-20
There shouldn't be any *wget*s in your sources.list.

Every line should start with either *deb*, *deb-src*, or *#*

---

### Post by scxtt on 2006-07-20
post your /etc/apt/sources.list for us to look @ ...

---

### Post by mattfender on 2006-07-20
# 
# deb cdrom:[Ubuntu 6.06 _Dapper Drake_ - Release i386 (20060531)]/ dapper main restricted


deb cdrom:[Ubuntu 6.06 _Dapper Drake_ - Release i386 (20060531)]/ dapper main restricted


## Major bug fix updates produced after the final release of the
## distribution.
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) dapper-updates main restricted
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper main restricted universe multiverse
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse


deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) dapper-commercial main
wget -c [http://www.debian-multimedia.org/pool/main/w/w32codecs/w32codecs_20060611-0.0_i386.deb](http://www.debian-multimedia.org/pool/main/w/w32codecs/w32codecs_20060611-0.0_i386.deb)
sudo dpkg -i w32codecs_20060611-0.0_i386.deb

---

### Post by scxtt on 2006-07-20
get rid of:
[indent]wget -c [http://www.debian-multimedia.org/poo...1-0.0_i386.deb](http://www.debian-multimedia.org/poo...1-0.0_i386.deb)
sudo dpkg -i w32codecs_20060611-0.0_i386.deb[/indent]and run **sudo apt-get update** - those 2 entries aren't compatible w/ sources.list ...

---

