---
title: "cheese"
date: 2008-07-18
forum: New to Ubuntu
---

### Post by sameer.india on 2008-07-18
I have installed cheese but when I run it just closes as soon as it opens.
here is the error the terminal shows.

sameer@sameer-laptop:~$ cheese
The program 'cheese' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadAlloc (insufficient resources for operation)'.
  (Details: serial 47 error_code 11 request_code 141 minor_code 19)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)

---

### Post by kpkeerthi on 2008-07-18
Run it with --sync option as shown in your error trace and report the problem in lauchpad

---

### Post by sameer.india on 2008-07-18
I can't undersand wha that means

---

### Post by kpkeerthi on 2008-07-18
[https://launchpad.net/ubuntu/+bugs](https://launchpad.net/ubuntu/+bugs)

---

### Post by sameer.india on 2008-07-18
no i mean the sync command line

---

### Post by Zack McCool on 2008-07-18
> **sameer.india said:**
> no i mean the sync command line

Just means that from the command line, type the following:

```
 cheese --sync 
```

Then copy the output and paste it into the bug report.

---

