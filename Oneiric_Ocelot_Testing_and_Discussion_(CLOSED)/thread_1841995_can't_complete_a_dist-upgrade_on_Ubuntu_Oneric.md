---
title: "can't complete a dist-upgrade on Ubuntu Oneric"
date: 2011-09-10
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by muyisco on 2011-09-10
I upgraded to Oneric around Alpha 3 and have been using  "apt-get dist-upgrade" ever since. Today, i tried to upgrading and after  downloading about 100mb, i get an error which is shown below


```

After this operation, 222 MB of additional disk space will be used. Do you want to continue [Y/n]? y 
Err http://76.73.4.58/ubuntu/ oneiric/main libc6-dev i386 2.13-20ubuntu1   403  Forbidden 
Err http://76.73.4.58/ubuntu/ oneiric/main perl-modules all 5.12.4-4   403  Forbidden 
Err http://76.73.4.58/ubuntu/ oneiric/main gir1.2-atk-1.0 i386 2.1.91-0ubuntu1   403  Forbidden 
Err http://76.73.4.58/ubuntu/ oneiric/main libnss3 i386 3.12.9+ckbi-1.82-0ubuntu5   403  Forbidden 
Err http://76.73.4.58/ubuntu/ oneiric/main libnux-1.0-0 i386 1.8.0-0ubuntu1   403  Forbidden 
Err http://76.73.4.58/ubuntu/ oneiric/main xserver-xorg-core i386 2:1.10.4-1ubuntu1   403  Forbidden 
Failed to fetch http://76.73.4.58/ubuntu/pool/main/e/eglibc/libc6-       dev_2.13-20ubuntu1_i386.deb  403  Forbidden 
Failed to fetch http://76.73.4.58/ubuntu/pool/main/p/perl/perl-              modules_5.12.4-4_all.deb  403  Forbidden 
Failed to fetch http://76.73.4.58/ubuntu/pool/main/a/atk1.0/gir1.2 atk-1.0_2.1.91-0ubuntu1_i386.deb  403  Forbidden 
Failed to fetch http://76.73.4.58/ubuntu/pool/main/n/nss/libnss3_3.12.9+ckbi 1.82-0ubuntu5_i386.deb  403  Forbidden 
Failed to fetch http://76.73.4.58/ubuntu/pool/main/n/nux/libnux-1.0-0_1.8.0-0ubuntu1_i386.deb  403  Forbidden 
Failed to fetch http://76.73.4.58/ubuntu/pool/main/x/xorg-server/xserver-xorg-core_1.10.4-1ubuntu1_i386.deb  403  Forbidden 
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?
```

I did some googling and found out that changing the source of the repos  might help so i did that, first, i changed it to the"Main Server". After  updating the sources, list, i tried "dist-upgrade" again and it still  didn't work. I changed the server to yet another located in the US but i  got the same error. Is this an issue with the packages themselves  across all the mirrors or is it something i did?

---

### Post by jbicha on 2011-09-10
Did you apt-get update before you tried apt-get dist-upgrade?

---

### Post by cariboo on 2011-09-10
I'd also suggest disabling all your ppas, this has been common practice for the last several releases, using update-manager does it auto-magically.

---

