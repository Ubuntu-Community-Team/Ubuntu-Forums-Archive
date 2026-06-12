---
title: "Get &quot;Permission denied&quot; when try to print out to lp0"
date: 2012-05-14
forum: New to Ubuntu
---

### Post by s1baker on 2012-05-14
hi,
I recently installed 12.04 64 bit.
Now when I try to send a plot file out to /dev/lp0
I get this message:

```
bash: /dev/lp0: Permission denied 
```

I have tried:
```

cat file.prn  >  /dev/lp0
sudo cat file.prn  >  /dev/lp0

```


neither one works.
It worked just fine in 10.10 32 bit I had before. Anybody have a
clue what is wrong?

---

### Post by HiImTye on 2012-05-14
```
ll /dev/lp0
```
might give you some insight

---

### Post by lkraemer on 2012-05-15
You may need to be a member of group lp.

You can add yourself to that group.

Terminal commands to see the list:
```

users
groups

```

Also try:
```

dmesg | Tail

```
to see if there is more information.


lk

---

### Post by oldfred on 2012-05-16
this has instructions on determining ports, printers & permissions.

[https://wiki.ubuntu.com/DebuggingPrintingProblems](https://wiki.ubuntu.com/DebuggingPrintingProblems)

---

