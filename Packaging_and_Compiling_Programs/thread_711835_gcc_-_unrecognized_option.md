---
title: "gcc - unrecognized option"
date: 2008-03-01
forum: Packaging and Compiling Programs
---

### Post by randomnumber on 2008-03-01
I was trying to install gnu arm and now gcc does the following.

$gcc-4.1 TCPClient.c
/usr/local/bin/ld: unrecognized option '--hash-style=both'
/usr/local/bin/ld: use the --help option for usage information
collect2: ld returned 1 exit status

If I specify an older version of gcc it will compile with no error. I have complete removed gcc and gcc-4.1 which is the one with the problem. I did this with synamptic.

I removed the links is usr/bin/gcc* and reinstalled the same behavoir exhists.

 I wrote this sort fast so I appoligize for typos and grammer. Thanks for any help. 

My objectives after this are to be able to compile c programs like normal and compile programs so that I can load them on an ARM processor.

Some Point i will have to do a fresh install but I hate to use that as a way to solve my problems.

---

### Post by maao129 on 2008-12-23
> **randomnumber said:**
> I was trying to install gnu arm and now gcc does the following.

$gcc-4.1 TCPClient.c
/usr/local/bin/ld: unrecognized option '--hash-style=both'
/usr/local/bin/ld: use the --help option for usage information
collect2: ld returned 1 exit status

If I specify an older version of gcc it will compile with no error. I have complete removed gcc and gcc-4.1 which is the one with the problem. I did this with synamptic.

I removed the links is usr/bin/gcc* and reinstalled the same behavoir exhists.

 I wrote this sort fast so I appoligize for typos and grammer. Thanks for any help. 

My objectives after this are to be able to compile c programs like normal and compile programs so that I can load them on an ARM processor.

Some Point i will have to do a fresh install but I hate to use that as a way to solve my problems.


I just the same probelm as you. after google carfully, I found:


If you look closely, the error is something related to the local gcc not using the host's linker (ld).

$ which gcc
/usr/bin/gcc

$ which ld
/usr/local/bin/ld

For some reason, I messed my compiler path. To synchronized gcc to use the host's dynamic linker (i.e. /usr/bin/ld), set the environment variable COMPILER_PATH to /usr/bin.

$ export COMPILER_PATH=/usr/bin
$ echo $COMPILER_PATH
/usr/bin

$ gcc -print-prog-name=ld
/usr/bin/ld


then I could use gcc again.
hope this will helpful.

---

### Post by miguel.aveiro on 2010-02-10
Just to say that I'm really thanks for this answer!

I was stucked with this for 2 days!

---

