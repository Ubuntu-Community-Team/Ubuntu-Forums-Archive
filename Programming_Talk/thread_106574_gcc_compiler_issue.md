---
title: "gcc compiler issue"
date: 2005-12-21
forum: Programming Talk
---

### Post by blacklantern on 2005-12-21
Hi!

So I'm new to Ubuntu, and I'm trying to work on some multithreaded programming on the side. I see that gcc-4.0-base is already installed, and the gcc debugger as well. To test and see whether or not the compiler worked, I typed in the command 'gcc' into the terminal, even though there was no file to compile. I got a 'command not found error.' Can anyone tell me how to set up the gcc compiler, or should I even be doing this in the terminal? Also, is there a pthread library I can download in order to work with posix threads?

---

### Post by kairu0 on 2005-12-21
The GCC compiler itself is actually the gcc-4.0 package. Please search for and install it via Synaptic or with apt-get.

---

### Post by blacklantern on 2005-12-21
Got it. and the posix thread library?

---

### Post by darth_vector on 2005-12-21
if you install the build-essential package you will get all of the header files, gdb, make and so on;

sudo apt-get install build-essential

---

### Post by healychan on 2005-12-21
[QUOTE=darth_vector]if you install the build-essential package you will get all of the header files, gdb, make and so on;

sudo apt-get install build-essential[/QUOTE]

May I ask what programming language this package support???
Can I do C++, Java programming once I installed.

If not, can use apt-get to install the JDK??

Thanks for any help!!;)

---

### Post by darth_vector on 2005-12-21
build-essential is for C/C++. it does not include java compilers and things. if you want to install java you will have to download the binaries from sun ([www.java.sun.com](www.java.sun.com)) or enable multiverse for apt. then you can install j2sdk1.4

---

### Post by healychan on 2005-12-21
for those who want to install JDK, follow this link.

[http://java.sun.com/j2se/1.5.0/download.jsp](http://java.sun.com/j2se/1.5.0/download.jsp)

select "Download JDK 5.0 update 6"
the version for ubuntu(32bit) user should be the "Linux self_extracting file"
64bit user has a seperate file. **[COLOR="Red"]Please[/COLOR]** read the instruction carefully.

---

### Post by blacklantern on 2005-12-22
Hrm, after I install build essential, should I be able to pull up the man pages for the functions within the pthread library? If so, I can't. I apologize for continuing to come back here - I'm such a linux n00b. :p

---

### Post by darth_vector on 2005-12-22
no, i dont think so. a quick google got me this though:

[http://www.opengroup.org/onlinepubs/007908799/xsh/pthread.h.html](http://www.opengroup.org/onlinepubs/007908799/xsh/pthread.h.html)

---

