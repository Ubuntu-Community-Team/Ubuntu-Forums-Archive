---
title: "stupid question what is this..?"
date: 2008-06-12
forum: New to Ubuntu
---

### Post by lunaluna on 2008-06-12
i ran :" netstat -antp " to see which programms are running 
and it gave me:  cupsd  &   exim4
an explanation about those 2?

---

### Post by Joeb454 on 2008-06-12
Check the man pages or synaptic :) They should give a description somewhere :)

man pages are found from a terminal (and can be a bit cryptic)

```
man cupsd
man exim4
```
You have to press 'q' to exit the man pages :)

---

### Post by kpkeerthi on 2008-06-12
For a simple one-liner information text, type
```
whatis <program-name>
```

---

### Post by the_doc on 2008-06-12
cupsd is the scheduler for the Common UNIX Printing System and exim is a message transfer agent of some kind I think.

---

### Post by burakerenn on 2008-06-12
cupsd is common unix printing system daemon. it makes you to print documents and print queues.

exim4 is a mail server afaik. Well if you don't work with it you can just remove.

---

### Post by xeth_delta on 2008-06-12
> **lunaluna said:**
> i ran :" netstat -antp " to see which programms are running 
and it gave me:  cupsd  &   exim4
an explanation about those 2?

Netstat offers information on network statistics.
For a breif description
```
whatis netstat
```
For more information consult the manual with "man".

If you want to know what programs are running and are the most active, you can use one of the following:
```
top
htop
```
You exit them with "q". htop is not installed by default, but it is in the repositories and is easily installable.

You can also use "ps" with different arguments, for example:
```
ps -ef
ps -aux
```

---

