---
title: "What kernel header package do I need?"
date: 2011-04-06
forum: Packaging and Compiling Programs
---

### Post by kliq on 2011-04-06
Hello
I have tried to compile a program that I downloaded.
But I get a long list of warnings, and error messages detailing kernel headers that I am missing; eg:

```

In file included from /home/maxtor/Desktop/PWC-try/pwc-10.0.12-rc1/pwc-if.c:69:
/home/maxtor/Desktop/PWC-try/pwc-10.0.12-rc1/pwc.h:28:26: error: linux/config.h: No such file or directory
/home/maxtor/Desktop/PWC-try/pwc-10.0.12-rc1/pwc.h:37:27: error: asm/semaphore.h: No such file or directory
/home/maxtor/Desktop/PWC-try/pwc-10.0.12-rc1/pwc-if.c:166: error: variable ‘pwc_template’ has initializer but incomplete type
/home/maxtor/Desktop/PWC-try/pwc-10.0.12-rc1/pwc-if.c:167: error: unknown field ‘owner’ specified in initializer
/home/maxtor/Desktop/PWC-try/pwc-10.0.12-rc1/pwc-if.c:167: warning: excess elements in struct initializer
/home/maxtor/Desktop/PWC-try/pwc-10.0.12-rc1/pwc-if.c:167: warning: (near initialization for ‘pwc_template’)
/home/maxtor/Desktop/PWC-try/pwc-10.0.12-rc1/pwc-if.c:168: error: unknown field ‘name’ specified in initiali

```and so it goes, on & on.

I have looked through the available kernel header files in Synaptic and a few have  !  marks in the left hand column which I believe indicates the ones that are in my system, - Lucid, 10.04.

Please, does anyone know what:    'apt-get' packages will solve this or I should do next?

---

### Post by debd on 2011-04-10
Look, Different header files reside in different packages. Their is no single package to get them all at once. Do you get some error like  'missing libraries : . . .  ' ? 
For help with missing headers, you can install auto-apt.                    With  sudo apt-get install auto-apt 
then, update the cache with
 sudo auto-apt update

now, you can search for header files like this :

auto-apt search <header file>

e.g.   auto-apt search incurses.h  

from the results you'll see, you in most cases need the packages with the term 'dev' for your compiling purpose.  Install them with apt-get.  
You can also install and use another utility named apt-file the same way.  Google it. You'll have lots of wikis on these.

---

### Post by kliq on 2011-04-11
Thank you very much for replying, [debd]("http://ubuntuforums.org/member.php?u=1187415").
I have downloaded auto-apt and when I next get some spare time: { I will try to compile PWC again; } && report back.

---

### Post by kliq on 2011-04-17
Well, I have downloaded all that you suggested.
Many MBs.
I have then searched as you suggested and it seems that:
 semaphore.h
is missing and unavailable in the Universe.

Further Googling seems to indicate that it was dropped many Kernels ago.
Other people have had this header problem with other software too, but I can find no solutuion.

---

### Post by kliq on 2011-04-23
Strangely, comng back to this, again,  after nearly a week,  and they now appear.

 So am now marking this as  solved.

---

### Post by debd on 2011-04-24
If you are keen on compiling, you should give this page a read: [https://help.ubuntu.com/community/CompilingEasyHowTo](https://help.ubuntu.com/community/CompilingEasyHowTo)   Its a good place to start to know how to compile things yourself :)

---

