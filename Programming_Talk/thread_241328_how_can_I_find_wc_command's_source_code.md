---
title: "how can I find wc command's source code?"
date: 2006-08-22
forum: Programming Talk
---

### Post by HolyJoe on 2006-08-22
I want to view wc command's source code, how can I find the source?

](*,)

---

### Post by HolyJoe on 2006-08-22
somebody know it?

---

### Post by -Rick- on 2006-08-22
Check the source of GNU's coreutils: [http://www.gnu.org/software/coreutils/](http://www.gnu.org/software/coreutils/)

---

### Post by ifokkema on 2006-08-22
The Debian/Ubuntu way of doing this:
- Find the executable.
- Find the package.
- Cd into a directory.
- Download the source directly.

```
  14:26:47 ifokkema@5-HKG-02-0098:~$ which wc
/usr/bin/wc
  14:26:56 ifokkema@5-HKG-02-0098:~$ dpkg -S /usr/bin/wc
coreutils: /usr/bin/wc
  14:27:12 ifokkema@5-HKG-02-0098:~$ cd src
  14:27:25 ifokkema@5-HKG-02-0098:src$ sudo apt-get source coreutils

```

If you get:
```
E: You must put some 'source' URIs in your sources.list
```
Then you must enable the deb-src lines in your /etc/apt/sources.list file.

HTH

---

### Post by HolyJoe on 2006-09-01
Hi, ifokkema,
Very nice.

Thank you for you help!

---

