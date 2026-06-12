---
title: "Handle Linux command errors when called inside perl script"
date: 2010-06-26
forum: Programming Talk
---

### Post by QaRahul on 2010-06-26
Hello All,
 I need to write a perl script to enable/disable an network interface inside perl script.
I already did that but I just need to handle the error returned by ifup / ifdown inside the script itself. That is I don't want the error results by the ifup/ifdown to be printed on the shell rather I wish to manipulate the error. For ex. see the following script:

#usr/bin/perl -w

`ifup eth0`;

now suppose that user runs this script as non - root this script returns an error like permission denied. But I don't want to print this error, rather I wish to some other message. 

How I could do this??? Help please!!!

---

### Post by dawwin on 2010-06-26
You can get exit status of program using
```

$a = system("ifup eth0");

```

Or get stdout of running application using
```

$a = qx(ifup eth0);

```

---

### Post by QaRahul on 2010-06-26
but it still displays message on the console. The following is the output of $a = qx(ifup eth0);

rahul@rahuls-laptop ~/Desktop/Radmin $ sudo perl testfunc.pl 
Ignoring unknown interface eth0=eth0.

I simply don't want to print this message

---

### Post by dawwin on 2010-06-26
try
```

$a = qx(ifup eth0  2>&1);

```

---

### Post by QaRahul on 2010-06-26
Yes!!, it worked. 

Can you please explain what "2>&1" means and how it solved the problem??

---

### Post by dawwin on 2010-06-26
qx() returns stdout (standard output) of given application.
Using "2>&1" you can redirect stderr (standard error output) into stdout

---

### Post by QaRahul on 2010-06-26
Thanx dawwin.

---

