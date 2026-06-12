---
title: "Problem with updating with apt in Ubuntu 16.04"
date: 2017-09-09
forum: New to Ubuntu
---

### Post by emirbet on 2017-09-09
Hello!

When I try to install applications or update them I get the following error:

```
sudo apt-get upgrade
Leyendo lista de paquetes... Hecho
E: El valor «stable» no es válido para APT::Default-Release ya que dicha distribución no está disponible en las fuentes
```



I have tried restoring the repositories file to its initial value: /user/apt/sources.list

Could someone tell me what to do and how to solve it.

---

### Post by QIII on 2017-09-09
Hello!

I have translated your post into English.  This is an English speaking area of the forums.  If you wish to post in Spanish, I suggest you try the [Argentina Local Community (LoCo)]("https://ubuntuforums.org/forumdisplay.php?f=189") team, since it is the most active.

Cheers!

---

### Post by Bashing-om on 2017-09-09
emirbet; Hello - Welcome to the forum :)

Show us what there is to work with.
Post back - in English - the out puts of terminal commands:
```

LANG=C;cat /etc/issue
LANG=C;lsb_release -a
LANG=C;cat -n /etc/apt/sources.list
LANG=C;tail -v -n +1 /etc/apt/sources.list.d/*
LANG=C;sudo apt update
LANG=C;sudo apt upgrade

```

It is that English is the only human language I can communicate in .


[INDENT][INDENT]all in the process
[/INDENT][/INDENT]

---

### Post by emirbet on 2017-09-09
This is the output:

emirbet@emirbet-X541UAK:~$ LANG=C; cat /etc/issue
Ubuntu 16.04.3 LTS \n \l

emirbet@emirbet-X541UAK:~$ 
emirbet@emirbet-X541UAK:~$ 
emirbet@emirbet-X541UAK:~$ LANG=C;lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 16.04.3 LTS
Release:    16.04
Codename:    xenial
emirbet@emirbet-X541UAK:~$ 
emirbet@emirbet-X541UAK:~$ LANG=C; cat -n /etc/apt/sources.list
     1    
     2    
     3    ###### Ubuntu Main Repos
     4    deb [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) xenial main restricted universe multiverse 
     5    deb-src [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) xenial main restricted universe multiverse 
     6    
     7    ###### Ubuntu Update Repos
     8    deb [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) xenial-security main restricted universe multiverse 
     9    deb [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) xenial-updates main restricted universe multiverse 
    10    deb [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) xenial-proposed main restricted universe multiverse 
    11    deb [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) xenial-backports main restricted universe multiverse 
    12    deb-src [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) xenial-security main restricted universe multiverse 
    13    deb-src [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) xenial-updates main restricted universe multiverse 
    14    deb-src [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) xenial-proposed main restricted universe multiverse 
    15    deb-src [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) xenial-backports main restricted universe multiverse 
    16    
    17    ###### Ubuntu Partner Repo
    18    deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) xenial partner
    19    deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) xenial partner
    20    
    21    
emirbet@emirbet-X541UAK:~$ 
emirbet@emirbet-X541UAK:~$ 
emirbet@emirbet-X541UAK:~$ LANG=C; tail -v -n +1  /etc/apt/sources.list.d/*
==> /etc/apt/sources.list.d/google-chrome.list.save <==
### THIS FILE IS AUTOMATICALLY CONFIGURED ###
# You may comment out this entry, but any other modifications may be lost.
deb [arch=amd64] [http://dl.google.com/linux/chrome/deb/](http://dl.google.com/linux/chrome/deb/) stable main

==> /etc/apt/sources.list.d/maarten-fonville-ubuntu-android-studio-xenial.list <==
deb [http://ppa.launchpad.net/maarten-fonville/android-studio/ubuntu](http://ppa.launchpad.net/maarten-fonville/android-studio/ubuntu) xenial main
# deb-src [http://ppa.launchpad.net/maarten-fonville/android-studio/ubuntu](http://ppa.launchpad.net/maarten-fonville/android-studio/ubuntu) xenial main

==> /etc/apt/sources.list.d/maarten-fonville-ubuntu-android-studio-xenial.list.save <==
deb [http://ppa.launchpad.net/maarten-fonville/android-studio/ubuntu](http://ppa.launchpad.net/maarten-fonville/android-studio/ubuntu) xenial main
# deb-src [http://ppa.launchpad.net/maarten-fonville/android-studio/ubuntu](http://ppa.launchpad.net/maarten-fonville/android-studio/ubuntu) xenial main

==> /etc/apt/sources.list.d/paolorotolo-ubuntu-android-studio-xenial.list <==
deb [http://ppa.launchpad.net/paolorotolo/android-studio/ubuntu](http://ppa.launchpad.net/paolorotolo/android-studio/ubuntu) xenial main
# deb-src [http://ppa.launchpad.net/paolorotolo/android-studio/ubuntu](http://ppa.launchpad.net/paolorotolo/android-studio/ubuntu) xenial main
# deb-src [http://ppa.launchpad.net/paolorotolo/android-studio/ubuntu](http://ppa.launchpad.net/paolorotolo/android-studio/ubuntu) xenial main

==> /etc/apt/sources.list.d/paolorotolo-ubuntu-android-studio-xenial.list.save <==
deb [http://ppa.launchpad.net/paolorotolo/android-studio/ubuntu](http://ppa.launchpad.net/paolorotolo/android-studio/ubuntu) xenial main
# deb-src [http://ppa.launchpad.net/paolorotolo/android-studio/ubuntu](http://ppa.launchpad.net/paolorotolo/android-studio/ubuntu) xenial main
# deb-src [http://ppa.launchpad.net/paolorotolo/android-studio/ubuntu](http://ppa.launchpad.net/paolorotolo/android-studio/ubuntu) xenial main

==> /etc/apt/sources.list.d/rojtberg-ubuntu-hdjmod-xenial.list <==
deb [http://ppa.launchpad.net/rojtberg/hdjmod/ubuntu](http://ppa.launchpad.net/rojtberg/hdjmod/ubuntu) xenial main
# deb-src [http://ppa.launchpad.net/rojtberg/hdjmod/ubuntu](http://ppa.launchpad.net/rojtberg/hdjmod/ubuntu) xenial main

==> /etc/apt/sources.list.d/rojtberg-ubuntu-hdjmod-xenial.list.save <==
deb [http://ppa.launchpad.net/rojtberg/hdjmod/ubuntu](http://ppa.launchpad.net/rojtberg/hdjmod/ubuntu) xenial main
# deb-src [http://ppa.launchpad.net/rojtberg/hdjmod/ubuntu](http://ppa.launchpad.net/rojtberg/hdjmod/ubuntu) xenial main

==> /etc/apt/sources.list.d/ubuntu-desktop-ubuntu-ubuntu-make-xenial.list <==
deb [http://ppa.launchpad.net/ubuntu-desktop/ubuntu-make/ubuntu](http://ppa.launchpad.net/ubuntu-desktop/ubuntu-make/ubuntu) xenial main
# deb-src [http://ppa.launchpad.net/ubuntu-desktop/ubuntu-make/ubuntu](http://ppa.launchpad.net/ubuntu-desktop/ubuntu-make/ubuntu) xenial main

==> /etc/apt/sources.list.d/ubuntu-desktop-ubuntu-ubuntu-make-xenial.list.save <==
deb [http://ppa.launchpad.net/ubuntu-desktop/ubuntu-make/ubuntu](http://ppa.launchpad.net/ubuntu-desktop/ubuntu-make/ubuntu) xenial main
# deb-src [http://ppa.launchpad.net/ubuntu-desktop/ubuntu-make/ubuntu](http://ppa.launchpad.net/ubuntu-desktop/ubuntu-make/ubuntu) xenial main

==> /etc/apt/sources.list.d/webupd8team-ubuntu-java-xenial.list <==
deb [http://ppa.launchpad.net/webupd8team/java/ubuntu](http://ppa.launchpad.net/webupd8team/java/ubuntu) xenial main
# deb-src [http://ppa.launchpad.net/webupd8team/java/ubuntu](http://ppa.launchpad.net/webupd8team/java/ubuntu) xenial main

==> /etc/apt/sources.list.d/webupd8team-ubuntu-java-xenial.list.save <==
deb [http://ppa.launchpad.net/webupd8team/java/ubuntu](http://ppa.launchpad.net/webupd8team/java/ubuntu) xenial main
# deb-src [http://ppa.launchpad.net/webupd8team/java/ubuntu](http://ppa.launchpad.net/webupd8team/java/ubuntu) xenial main
emirbet@emirbet-X541UAK:~$ 
emirbet@emirbet-X541UAK:~$ 
emirbet@emirbet-X541UAK:~$ LANG=C; sudo apt update                         

Hit:1 [http://ppa.launchpad.net/maarten-fonville/android-studio/ubuntu](http://ppa.launchpad.net/maarten-fonville/android-studio/ubuntu) xenial InRelease
Hit:2 [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) xenial InRelease                   
Hit:3 [http://ppa.launchpad.net/paolorotolo/android-studio/ubuntu](http://ppa.launchpad.net/paolorotolo/android-studio/ubuntu) xenial InRelease
Hit:4 [http://ppa.launchpad.net/rojtberg/hdjmod/ubuntu](http://ppa.launchpad.net/rojtberg/hdjmod/ubuntu) xenial InRelease         
Hit:5 [http://ppa.launchpad.net/ubuntu-desktop/ubuntu-make/ubuntu](http://ppa.launchpad.net/ubuntu-desktop/ubuntu-make/ubuntu) xenial InRelease
Hit:6 [http://es.archive.ubuntu.com/ubuntu](http://es.archive.ubuntu.com/ubuntu) xenial InRelease
Hit:7 [http://ppa.launchpad.net/webupd8team/java/ubuntu](http://ppa.launchpad.net/webupd8team/java/ubuntu) xenial InRelease  
Get:8 [http://es.archive.ubuntu.com/ubuntu](http://es.archive.ubuntu.com/ubuntu) xenial-security InRelease [102 kB]
Get:9 [http://es.archive.ubuntu.com/ubuntu](http://es.archive.ubuntu.com/ubuntu) xenial-updates InRelease [102 kB]
Get:10 [http://es.archive.ubuntu.com/ubuntu](http://es.archive.ubuntu.com/ubuntu) xenial-proposed InRelease [253 kB]
Get:11 [http://es.archive.ubuntu.com/ubuntu](http://es.archive.ubuntu.com/ubuntu) xenial-backports InRelease [102 kB]
Get:12 [http://es.archive.ubuntu.com/ubuntu](http://es.archive.ubuntu.com/ubuntu) xenial-security/main amd64 DEP-11 Metadata [59.9 kB]
Get:13 [http://es.archive.ubuntu.com/ubuntu](http://es.archive.ubuntu.com/ubuntu) xenial-security/main DEP-11 64x64 Icons [52.0 kB]
Get:14 [http://es.archive.ubuntu.com/ubuntu](http://es.archive.ubuntu.com/ubuntu) xenial-security/universe amd64 DEP-11 Metadata [48.8 kB]
Get:15 [http://es.archive.ubuntu.com/ubuntu](http://es.archive.ubuntu.com/ubuntu) xenial-security/universe DEP-11 64x64 Icons [64.2 kB]
Get:16 [http://es.archive.ubuntu.com/ubuntu](http://es.archive.ubuntu.com/ubuntu) xenial-updates/main amd64 Packages [632 kB]
Get:17 [http://es.archive.ubuntu.com/ubuntu](http://es.archive.ubuntu.com/ubuntu) xenial-updates/main amd64 DEP-11 Metadata [305 kB]
Get:18 [http://es.archive.ubuntu.com/ubuntu](http://es.archive.ubuntu.com/ubuntu) xenial-updates/main DEP-11 64x64 Icons [205 kB]
Get:19 [http://es.archive.ubuntu.com/ubuntu](http://es.archive.ubuntu.com/ubuntu) xenial-updates/universe amd64 DEP-11 Metadata [171 kB]
Get:20 [http://es.archive.ubuntu.com/ubuntu](http://es.archive.ubuntu.com/ubuntu) xenial-updates/universe DEP-11 64x64 Icons [226 kB]
Get:21 [http://es.archive.ubuntu.com/ubuntu](http://es.archive.ubuntu.com/ubuntu) xenial-updates/multiverse amd64 DEP-11 Metadata [5888 B]
Get:22 [http://es.archive.ubuntu.com/ubuntu](http://es.archive.ubuntu.com/ubuntu) xenial-proposed/main amd64 DEP-11 Metadata [6988 B]
Get:23 [http://es.archive.ubuntu.com/ubuntu](http://es.archive.ubuntu.com/ubuntu) xenial-proposed/universe amd64 DEP-11 Metadata [3868 B]
Get:24 [http://es.archive.ubuntu.com/ubuntu](http://es.archive.ubuntu.com/ubuntu) xenial-proposed/universe DEP-11 64x64 Icons [12.2 kB]
Get:25 [http://es.archive.ubuntu.com/ubuntu](http://es.archive.ubuntu.com/ubuntu) xenial-backports/main amd64 DEP-11 Metadata [3328 B]
Get:26 [http://es.archive.ubuntu.com/ubuntu](http://es.archive.ubuntu.com/ubuntu) xenial-backports/universe amd64 DEP-11 Metadata [5136 B]
Fetched 2361 kB in 2s (896 kB/s)                                           
Reading package lists... Done
E: The value 'stable' is invalid for APT::Default-Release as such a release is not available in the sources
emirbet@emirbet-X541UAK:~$ 
emirbet@emirbet-X541UAK:~$ 
emirbet@emirbet-X541UAK:~$ LANG=C; sudo apt upgrade
Reading package lists... Done
E: The value 'stable' is invalid for APT::Default-Release as such a release is not available in the sources
emirbet@emirbet-X541UAK:~$ 


I haven't solved yet.:icon_frown::icon_frown::icon_frown::icon_frown:

---

### Post by Bashing-om on 2017-09-09
emirbet; Hummmm ..

I am struggling here to understand.
Seems the source is [http://dl.google.com/linux/chrome/deb/](http://dl.google.com/linux/chrome/deb/) stable main .
Trying to access the site from my browser results in a 404 error.
Yet If I ping the site the server responds as expected.

I must question if this is a signing key issue ?
what shows:
```

apt-key list google

```


[INDENT][INDENT]sometimes I do wonder
[/INDENT][/INDENT]

---

### Post by emirbet on 2017-09-10
This is output from ***apt-key list google***

emirbet@emirbet-X541UAK:~$ sudo apt-key list google
pub   1024D/7FAC5991 2007-03-08
uid                  Google, Inc. Linux Package Signing Key <linux-packages-keymaster@google.com>
sub   2048g/C07CB649 2007-03-08

pub   4096R/D38B4796 2016-04-12
uid                  Google Inc. (Linux Packages Signing Authority) <linux-packages-keymaster@google.com>
sub   4096R/640DB551 2016-04-12 [expires: 2019-04-12]

emirbet@emirbet-X541UAK:~$

---

### Post by again? on 2017-09-10
Don't think it's a google-chrome source issue.

Try to find the config file with the setting (in /etc possibly)
```
grep -r "APT::Default-Release" /etc
```

---

### Post by emirbet on 2017-09-10
Here is the content of apt.conf:

emirbet@emirbet-X541UAK:~$ sudo grep -r "APT::Default-Release" /etc
/etc/apt/apt.conf:APT::Default-Release "stable";
emirbet@emirbet-X541UAK:~$

---

### Post by again? on 2017-09-10
Don't know exactly why you have this file.
It's not present on any of my installs. (16.04 17.04)
Is this an upgrade from a beta or previous release?
Used any debian repositories?

Is that all that's in the file?
```
cat /etc/apt/apt.conf
```

---

### Post by emirbet on 2017-09-10
Here is the content of apt.conf:

emirbet@emirbet-X541UAK:~$ sudo grep -r "APT:default-Release" /etc
/etc/apt/apt.conf:APT:default-Release "stable";
emirbet@emirbet-X541UAK:~$

---

### Post by emirbet on 2017-09-10
I've solved, I've changed apt.conf file:

emirbet@emirbet-X541UAK:~$ sudo grep -r "APT:default-Release" /etc
/etc/apt/apt.conf:APT:default-Release *;
emirbet@emirbet-X541UAK:~$ 				

Thanks very much!!!  ;)

---

### Post by emirbet on 2017-09-10
How can I change the thread to "SOLVED"?

---

### Post by again? on 2017-09-10
> **emirbet said:**
> How can I change the thread to "SOLVED"?
Click on **Thread Tools** at top right.

---

### Post by emirbet on 2017-09-10
I've changed the content of apt.conf, and it works OK

root@emirbet-X541UAK:/etc/apt# cat apt.conf
APT:default-Release *;
root@emirbet-X541UAK:/etc/apt# 


Thanks very much!!!

---

