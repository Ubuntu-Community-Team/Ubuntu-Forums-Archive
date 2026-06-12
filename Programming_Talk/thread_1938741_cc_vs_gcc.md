---
title: "cc vs gcc"
date: 2012-03-10
forum: Programming Talk
---

### Post by bubuzzz on 2012-03-10
Hi all programming jedas, 

I working on a project about porting from solaris to linux. The first thing to think about it is changing the compiler from cc to gcc. Is there any difference in term of programming (like syntax, declaration, C standard ... ) between them ? Why is there gcc when cc was already there ? The fact that in linux, cc is linked to gcc makes me so confused

---

### Post by dwhitney67 on 2012-03-10
> **bubuzzz said:**
> The fact that in linux, cc is linked to gcc makes me so confused

It makes you confused?  All it tells me is that they are the same.

---

### Post by Arndt on 2012-03-10
> **bubuzzz said:**
> Hi all programming jedas, 

I working on a project about porting from solaris to linux. The first thing to think about it is changing the compiler from cc to gcc. Is there any difference in term of programming (like syntax, declaration, C standard ... ) between them ? Why is there gcc when cc was already there ? The fact that in linux, cc is linked to gcc makes me so confused

I suppose that on Solaris, cc is not gcc. One step in porting can be to fetch gcc to your Solaris environment and use it for building your code. What the important differences are in your case will become clear. Read the manual pages for both compilers, too. The next step is to build it in the Linux environment.

---

### Post by Simian Man on 2012-03-10
'cc' is just code for 'whatever the C compiler on this system is'.  On Linux platforms, it is always gcc.  On other Unixes, it can be different.  In the SunOS days, it was suncc, but now the new Solaris likely uses gcc too.  On the old VMS, it was the old HP compiler.

Ideally, your code base is standard C, so you shouldn't have much if any trouble compiling it with gcc regardless of the compiler cc used to refer to (which may have been gcc anyway).

---

### Post by bubuzzz on 2012-03-11
Thank all. I believe the old source code was once compiled under gcc, so at this moment, i have no trouble during the porting (need some twists in the source code, anw). However, part of the project is about investigating the difference between cc (under solaris 2.5) and gcc 4 (under centos 5.7). So, that is why i need to know more about them. At this moment, i only found out about the performance ([http://www.osnews.com/story/5830](http://www.osnews.com/story/5830))

---

