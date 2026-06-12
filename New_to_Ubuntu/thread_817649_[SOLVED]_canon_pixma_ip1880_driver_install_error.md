---
title: "[SOLVED] canon pixma ip1880 driver install error"
date: 2008-06-03
forum: New to Ubuntu
---

### Post by FOSSaddict on 2008-06-03
hallo everyone,,iam new member in here..i have got a problem..

i have already read article about these..
n iam try to download n install it.

```

   1. cnijfilter-common_2.70-1_i386.deb
   2. cnijfilter-ip1800series_2.70-1_i386.deb
   3. libtiff.so.3
   4. libpng3

```

but when i want to use this command

```
sudo dpkg -i cnijfilter-ip1800series_2.70-2_i386.deb
```

appear this message..

```

(Reading database ... 99941 files and directories currently installed.)
Preparing to replace cnijfilter-ip1800series 2.70-2 (using cnijfilter-ip1800series_2.70-2_i386.deb) ...
Unpacking replacement cnijfilter-ip1800series ...
dpkg: dependency problems prevent configuration of cnijfilter-ip1800series:
 cnijfilter-ip1800series depends on libglib1.2 (>= 1.2.0); however:
  Package libglib1.2 is not installed.
 cnijfilter-ip1800series depends on libgtk1.2 (>= 1.2.10-4); however:
  Package libgtk1.2 is not installed.
 cnijfilter-ip1800series depends on libxml1 (>= 1:1.8.14-3); however:
  Package libxml1 is not installed.
dpkg: error processing cnijfilter-ip1800series (--install):
 dependency problems - leaving unconfigured
Processing triggers for libc6 ...
ldconfig deferred processing now taking place
Errors were encountered while processing:
 cnijfilter-ip1800series

```

what should i do??
thanks

---

### Post by iaculallad on 2008-06-03
Try following this [installation guide]("http://free.xiaoyenzi.com/tutorial/installing-canon-pixma-ip1880-in-ubuntu-linux/") for your Pixma ip1880 printer.

---

### Post by FOSSaddict on 2008-06-03
is the same article,,i already read...

when i use this command..

```
sudo dpkg -i cnijfilter-ip1800series_2.70-1_i386.deb
```

the message appear...

---

