---
title: "error installing cups-client"
date: 2012-08-23
forum: New to Ubuntu
---

### Post by Frank P on 2012-08-23
12.04 LTS server
entering the following at the command line starts the process 
susdo apt-get install cups-client
but then gives the following multiple error messages
 
err [http://ca.archive/ubuntu/](http://ca.archive/ubuntu/)................................
temporary failure resolving 'ca.archive.ubuntu.com
 
failed to fetch ...............................
 
What do I do now
 
Thanks
 
Frank Polan

---

### Post by sandyd on 2012-08-23
Please post the output of
```

cat /etc/apt/sources.list

```

---

### Post by Frank P on 2012-08-23
I'll try to attach listing - filename sandyd.txt
Not sure if I've done it correctly
 
Thanks
 
Frank Polan

---

### Post by sandyd on 2012-08-24
> **Frank P said:**
> I'll try to attach listing - filename sandyd.txt
Not sure if I've done it correctly
 
Thanks
 
Frank Polan
It looks like you have bad nameservers and/or cannot connect to the internet

Post the ouput of
```

cat /etc/resolv.conf

```

---

### Post by Frank P on 2012-08-24
my resolve.conf is empty except for 2 comment lines
 
I'm going to reinstall from scratch and see what happens
 
Thanks
 
Frank Polan

---

### Post by sandyd on 2012-08-25
Enter nameservers in resolv.conf, and everything will be fixed.

```

nameserver 8.8.8.8
nameserver 8.8.4.4

```

---

### Post by Frank P on 2012-08-25
the reinstall seems to have fixed it. 
How do I close this thread
 
Thanks
 
Frank P

---

