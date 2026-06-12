---
title: "Purpose of librt"
date: 2015-07-14
forum: New to Ubuntu
---

### Post by houmingc on 2015-07-14
when 'locate librt' or
'find / -name librt*' 
whole list of librt appears
it appears mainly in directory /lib32

Why librt is inside ubuntu and what is it for?

---

### Post by ian-weisser on 2015-07-15
Here's one way to find out:

```
me@machine:~$ locate librt
/lib/i386-linux-gnu/librt-2.21.so
**/lib/i386-linux-gnu/librt.so.1                          ## Let's look at this one**
/lib/x86_64-linux-gnu/librt-2.21.so
/lib/x86_64-linux-gnu/librt.so.1
...

me@machine:~$ dpkg -S /lib/i386-linux-gnu/librt.so.1    **## Ask dpkg for the package that installed the lib**
**libc6:i386**: /lib/i386-linux-gnu/librt.so.1              **## There's the package name**


me@machine:~$ apt-cache show libc6 | grep Description   **## Ask apt for the package description**
Description-en: **GNU C Library: Shared libraries         ## There's the answer**
```

librt is part of the GNU C Library, a building block of many Ubuntu system elements and applications.

You can see which packages rely upon the GNU C Library with the command:
```
apt-cache rdepends libc6
```
It's a very long list.

---

