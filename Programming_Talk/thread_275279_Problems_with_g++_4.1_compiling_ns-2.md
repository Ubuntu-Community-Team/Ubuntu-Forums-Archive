---
title: "Problems with g++ 4.1 compiling ns-2"
date: 2006-10-11
forum: Programming Talk
---

### Post by NachoMas on 2006-10-11
Hi all!
I am trying to compile from source a network simulator that I use extensibly (ns-2) and I am having problems with the linker (I think). Before I had no problem compiling the source code, but the last time I did it was around six months ago, before a major upgrade to Edgy. The linkage is failing with the following message:

/usr/bin/ld: ns: hidden symbol `__stack_chk_fail_local' in /usr/lib/libc_nonshared.a(stack_chk_fail_local.oS) is referenced by DSO
/usr/bin/ld: final link failed: Nonrepresentable section on output

I have been trying to find an answer to the problem in the web, but so far no luck. Anyway can help me with this? I am posting as well the output of the configure script, just in case...

Thanks for the help!
/Nacho

---

### Post by nabbelol on 2006-10-30
Hi! im having the same problem after installing Ubuntu 6.10. 

I get the same error when i run sudo make
/usr/bin/ld: final link failed: Nonrepresentable section on output


Did you fix this problem and if you did can you explain me how its done?

If its a bug in ubuntu when will there be a patch? :)

Hope you or somebody else can help with this asap :)

---

### Post by antonis_wrx on 2007-06-12
I have exactly the same problem on 7.10

```

/usr/bin/ld: final link failed: Nonrepresentable section on output
collect2: ld returned 1 exit status
make: *** [ns] Error 1

```

---

### Post by michelob22 on 2008-06-03
I have the same problem in 8.04

/usr/bin/ld: ns: hidden symbol `__stack_chk_fail_local' in /usr/lib/libc_nonshared.a(stack_chk_fail_local.oS) is referenced by DSO
/usr/bin/ld: final link failed: Nonrepresentable section on output
collect2: ld returned 1 exit status
make: *** [ns] Error 1

I've read somewhere that it has something to do with gcc -shared library files so we need to modify the makefile, but when I did that, I got a seg fault....


Found a solution at:
[http://nsnam.isi.edu/nsnam/index.php/Troubleshooting](http://nsnam.isi.edu/nsnam/index.php/Troubleshooting)
Followed the ubuntu section of this guide and changed the Makefiles according to what was said. Installed correctly, just doesn't work fully yet.

---

### Post by neha21 on 2009-09-01
when i'm trying to run ns in ubuntu i got this error 

Usage:      host [-v] [-a] [-t querytype] [options]  name  [server]
Listing:    host [-v] [-a] [-t querytype] [options]  -l zone  [server]
Hostcount:  host [-v] [options] -H [-D] [-E] [-G] zone
Check soa:  host [-v] [options] -C zone
Addrcheck:  host [-v] [options] -A host
Listing options: [-L level] [-S] [-A] [-p] [-P prefserver] [-N skipzone]
Common options:  [-d] [-f|-F file] [-I chars] [-i|-n] [-q] [-Q] [-T] [-Z]
Other options:   [-c class] [-e] [-m] [-o] [-r] [-R] [-s secs] [-u] [-w]
Special options: [-O srcaddr] [-j minport] [-J maxport]
Extended usage:  [-x [name ...]] [-X server [name ...]]

can neone help me?????

---

### Post by dribeas on 2009-09-01
> **neha21 said:**
> when i'm trying to run ns in ubuntu i got this error 

Usage:      host [-v] [-a] [-t querytype] [options]  name  [server]
Listing:    host [-v] [-a] [-t querytype] [options]  -l zone  [server]
Hostcount:  host [-v] [options] -H [-D] [-E] [-G] zone
Check soa:  host [-v] [options] -C zone
Addrcheck:  host [-v] [options] -A host
Listing options: [-L level] [-S] [-A] [-p] [-P prefserver] [-N skipzone]
Common options:  [-d] [-f|-F file] [-I chars] [-i|-n] [-q] [-Q] [-T] [-Z]
Other options:   [-c class] [-e] [-m] [-o] [-r] [-R] [-s secs] [-u] [-w]
Special options: [-O srcaddr] [-j minport] [-J maxport]
Extended usage:  [-x [name ...]] [-X server [name ...]]

can neone help me?????

This question is not programming related. You will get better and faster answers if you post in the appropriate forum.

---

