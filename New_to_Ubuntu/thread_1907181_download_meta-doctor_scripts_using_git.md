---
title: "download meta-doctor scripts using git"
date: 2012-01-10
forum: New to Ubuntu
---

### Post by kamga on 2012-01-10
hi, i'm new to ubuntu and i'm trying to download meta-doctor as follows-
[INDENT][COLOR=blue]git clone git://git.webos-internals.org/tools/meta-doctor.git[/COLOR]
[/INDENT]i received the following error-
[INDENT][COLOR=blue]cloning into meta-doctor...[/COLOR]

[COLOR=blue]fatal: The remote end hung up unexpectedly[/COLOR]
 
[/INDENT]please let me know how to solve this. Thanks!

---

### Post by Buntumatic on 2012-01-10
A quick visit to their page revealed this message:

Meta-Doctor has moved to [http://github.com/webos-internals/meta-doctor](http://github.com/webos-internals/meta-doctor)

---

### Post by kamga on 2012-01-10
thanks for reply!

what command should I use in ubuntu terminal to download meta-doctor from that address? 

i tried this variation to no avail-[INDENT][COLOR=Blue]git clone git://git.github.com/webos-internals/meta-doctor.git[/COLOR]
[/INDENT]this was the error i received-
[INDENT][COLOR=Blue]Cloning into meta-doctor...
git.github.com[0: 207.97.227.245]: errno=Connection timed out
fatal: unable to connect a socket (Connection timed out)[/COLOR][/INDENT]

---

### Post by Buntumatic on 2012-01-11
```
$ git clone https://github.com/webos-internals/meta-doctor.git
```

---

### Post by kamga on 2012-01-11
much appreciated!

---

