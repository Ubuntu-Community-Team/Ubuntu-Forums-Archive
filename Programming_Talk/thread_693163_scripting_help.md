---
title: "scripting help"
date: 2008-02-10
forum: Programming Talk
---

### Post by ElTimo on 2008-02-10
ok heres my idea. i want to write a script that will check if kvm-intel or kvm-amd is loaded, modprobe it if it isn't, and then launch an instance of kvm. i've tried everything and then some to get it working using grep, and nothing works. my idea was```
[ ! $USER=="root" ] && echo "This script must be run as root (or fakeroot)."
[ -n `lsmod|grep -i kvm` ]

```and i know this is probably incredibly wrong, but any help at all will be rewarded with candy :)

---

### Post by ghostdog74 on 2008-02-10
do it step by step, nobody's rushing you.
```

if [ $USER = "root" ];then
     result=`lsmod | grep kvm`
     if [ -z "$result" ];then 
         echo "not loaded"
         # code to load ...
     fi
 fi

```

---

### Post by ElTimo on 2008-02-11
i hope you like snickers...:-P

Thanks! you saved the...er...late afternoon \\:D/ i was trying too hard to make it elegant

---

### Post by ElTimo on 2008-02-11
by the way i just added basically your entire signature to my bookmarks :D

---

### Post by ElTimo on 2008-02-11
ok next question...how to determine hardware. specifically, processor type, RAM, number of cores, etc.

---

### Post by ghostdog74 on 2008-02-11
first shop to patronise whenever you have an initial problem, the man page , not a forum :)
```

# man -k hardware

```

---

### Post by ElTimo on 2008-02-12
ah thanks for the pointer (no pun intended) i'll quit bugging people now. :)

---

