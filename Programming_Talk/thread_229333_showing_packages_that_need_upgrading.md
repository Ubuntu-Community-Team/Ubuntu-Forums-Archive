---
title: "showing packages that need upgrading"
date: 2006-08-04
forum: Programming Talk
---

### Post by sickdude on 2006-08-04
hi all,

Im doing some bash scripting just for fun and making my life easy.

anyway i want apt-get to tell me wich packages are going to be upgraded  with out apt asking me to upgrade.

root@mixmaster:~# apt-get upgrade
Reading package lists... Done
Building dependency tree... Done
The following packages will be upgraded:
  base-files gnupg login passwd ppp ubuntu-base ubuntu-minimal ubuntu-standard
8 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 2234kB of archives.
After unpacking 0B of additional disk space will be used.
Do you want to continue [Y/n]? n
Abort.
root@mixmaster:~#

i always have to say, n, in the end

 -y  Assume Yes to all queries and do not prompt

only with no, is what im looking for

---

### Post by asimon on 2006-08-04
Not very elegant, but you can use ```
# yes no | apt-get upgrade
```.

There is also a --simulate (or short -s) option for apt-get, which only prints out what apt would do, but this will probably output much more than you want:
```

# apt-get -s upgrade
```

---

### Post by sickdude on 2006-08-04
yes! this is what i was looking for

thnx loads dude :D

---

