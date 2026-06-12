---
title: "Execute the file in minicom(SBC)"
date: 2013-04-19
forum: Programming Talk
---

### Post by Newbie89 on 2013-04-19
I'had find some problem when execute the file.As shown below:

error while loading shared libraries: libsqlite3.so.0: cannot open shared object file: No such file or directory

How can I fix the problem?
Any help?:)
Thanks

---

### Post by MG&amp;TL on 2013-04-19
You'll need to:

```
sudo apt-get install libsqlite0
```

---

### Post by Newbie89 on 2013-04-20
> **MG&TL said:**
> You'll need to:

```
sudo apt-get install libsqlite0
```

Hi,thanks for your reply. 
I found the file under /usr/lib...

what can I do to solve the problem?:)

---

### Post by MG&amp;TL on 2013-04-20
> **Newbie89 said:**
> Hi,thanks for your reply. 
I found the file under /usr/lib...

what can I do to solve the problem?:)

So you've definitely installed *sqlite*? Okay, what's the output of

```
ldconfig -v | grep sqlite
```

?

---

### Post by Newbie89 on 2013-04-20
> **MG&TL said:**
> So you've definitely installed *sqlite*? Okay, what's the output of

```
ldconfig -v | grep sqlite
```

?

ya

hong@ubuntu:~$ ldconfig -v | grep sqlite
/sbin/ldconfig.real: Path `/lib/x86_64-linux-gnu' given more than once
/sbin/ldconfig.real: Path `/usr/lib/x86_64-linux-gnu' given more than once
/sbin/ldconfig.real: Cannot stat /usr/lib/x86_64-linux-gnu/libnss_db.so: No such file or directory
    libsqlite3.so.0 -> libsqlite3.so.0.8.6
    libsqlite.so.0 -> libsqlite.so.0.8.6
/sbin/ldconfig.real: Can't create temporary cache file /etc/ld.so.cache~: Permission denied
hong@ubuntu:~$

---

### Post by MG&amp;TL on 2013-04-20
How odd. I'm sorry, I have no clue. Could you have inadvertently modified the sqlite library by accident? To the best of my knowledge, if a shared library shows up in the ldconfig cache (and it does), then the application should run. :(

---

### Post by Newbie89 on 2013-04-20
> **MG&TL said:**
> How odd. I'm sorry, I have no clue. Could you have inadvertently modified the sqlite library by accident? To the best of my knowledge, if a shared library shows up in the ldconfig cache (and it does), then the application should run. :(

sorry for my mistake...I think u think mine is work on the normal terminal...my terminal works fine...Now my problem is to compile sqlite3 in kernel environment(bash-2.05a#).
I found that libsqlite3.so.0 is inside /usr/local/lib...but it show the problem:

error while loading shared libraries: libsqlite3.so.0: cannot open shared

---

### Post by MG&amp;TL on 2013-04-20
> **Newbie89 said:**
> sorry for my mistake...I think u think mine is work on the normal terminal...my terminal works fine...Now my problem is to compile sqlite3 in kernel environment(bash-2.05a#).
I found that libsqlite3.so.0 is inside /usr/local/lib...but it show the problem:

error while loading shared libraries: libsqlite3.so.0: cannot open shared

So...you're in a chroot or something?

---

### Post by Newbie89 on 2013-04-21
> **MG&TL said:**
> So...you're in a chroot or something?

yaya...i'm in the chroot...any idea?I found that the lib of sqlite3 is on usr/local/lib...when I execute,It say not found...is it need to make the lib in usr/lib/ or what?

---

### Post by Newbie89 on 2013-04-21
yeah...I finally solve the problem...I found that the lib of sqlite3 is on usr/local/lib...so I just copy the lib of sqlite3 into the usr/lib...:)
My I know why the usr/lib is the main but not the usr/local/lib?:)

---

### Post by MG&amp;TL on 2013-04-21
> **Newbie89 said:**
> yeah...I finally solve the problem...I found that the lib of sqlite3 is on usr/local/lib...so I just copy the lib of sqlite3 into the usr/lib...:)
My I know why the usr/lib is the main but not the usr/local/lib?:)

Ah, I see now. Where the runtime linker looks for libraries is based on the environment variable LD_LIBRARY_PATH, which I suspect does not include /usr/local/lib by default. :)

---

