---
title: "What is the source package for /usr/bin/ls"
date: 2020-05-15
forum: Programming Talk
---

### Post by vitalio on 2020-05-15
Hello,

I can't figure out where the /usr/bin/ls sources are. Can you help me, please?

my ls is
```

vitalio@ubuntu:~$ which ls
/usr/bin/ls

vitalio@ubuntu:~$ ll /usr/bin/ls
-rwxr-xr-x 1 root root 142144 sep  5  2019 /usr/bin/ls*

```

I've tried apt-file search /usr/bin/ls
as well as dpkg-query -S /usr/bin/ls 
but none yeilded results for the banal ls.

Any ideas?

---

### Post by &amp;KyT$0P# on 2020-05-15
On Xubuntu 20.04 -
```
$ which -a ls
/usr/bin/ls
/bin/ls
$ dpkg-query -S $(which -a ls)
dpkg-query: no path found matching pattern /usr/bin/ls
coreutils: /bin/ls
$ apt-get source coreutils

```

---

### Post by vitalio on 2020-05-15
Thanx, indeed works with /bin/ls

---

