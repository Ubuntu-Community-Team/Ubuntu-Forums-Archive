---
title: "deleting filenames with whitespaces"
date: 2008-09-17
forum: New to Ubuntu
---

### Post by Matt26 on 2008-09-17
how can i delete a file via terminal window that has white spaces in the file name?  for example, "old file.txt"

thanks.

---

### Post by silverglade00 on 2008-09-17
You have to escape the space like so:

```
old\ file.txt
```

---

### Post by anotherdisciple on 2008-09-17
> **silverglade00 said:**
> You have to escape the space like so:

```
old\ file.txt
```

+1

If you want to read more about stuff like that... "Terminal for Beginners" is a really good read.... it's in my signature

---

### Post by rbprogrammer on 2008-09-17
or if you want you can use quotes.
eg.
```

rm "/home/name/my file that has spaces.txt"

```

---

### Post by Matt26 on 2008-09-18
> **rbprogrammer said:**
> or if you want you can use quotes.
eg.
```

rm "/home/name/my file that has spaces.txt"

```

thanks i used this suggestion and it worked, however i got this message when i used *sudo rm "file name"* to delete the file:

**sudo: unable to resolve host computername**

any idea what this means?

---

### Post by pbpersson on 2008-09-18
> **Matt26 said:**
> thanks i used this suggestion and it worked, however i got this message when i used *sudo rm "file name"* to delete the file:

**sudo: unable to resolve host computername**

any idea what this means?

Geez.....that sounds like an error I used to get when I first started with this version.  Have you installed the updates for Hardy Heron?

---

### Post by Greyed on 2008-09-18
> **Matt26 said:**
> thanks i used this suggestion and it worked, however i got this message when i used *sudo rm "file name"* to delete the file:

**sudo: unable to resolve host computername**

any idea what this means?

Do you have localhost set to 127.0.0.1 in /etc/hosts?

---

### Post by cariboo on 2008-09-18
Check you /etc/hosts file it should look something like this:

```
 cat /etc/hosts
127.0.0.1	localhost
127.0.1.1	intrepid
192.168.1.1	router
192.168.1.200	willy
```

my computers name is intrepid, the router is self evident, and willy is one of my servers.

Jim

---

