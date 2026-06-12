---
title: "Any Embedded Devs out there?"
date: 2008-02-18
forum: Programming Talk
---

### Post by colby500 on 2008-02-18
Hey guys, 
I'm wondering if there is anyone out there that has experience working with embedded linux(ARM arch.)? 

I'm working on some research at my Uni.(Berkeley) and I have to port/rewrite code(code libraries work on x86)...but before I do that I want to ask some questions first and make sure I'm not barking up the wrong tree.

I'll wait to see if anyone responds before I start getting specific....

-Colby

---

### Post by LaRoza on 2008-02-18
> **colby500 said:**
> Hey guys, 
I'm wondering if there is anyone out there that has experience working with embedded linux(ARM arch.)? 

I'm working on some research at my Uni.(Berkeley) and I have to port/rewrite code(code libraries work on x86)...but before I do that I want to ask some questions first and make sure I'm not barking up the wrong tree.

I'll wait to see if anyone responds before I start getting specific....

-Colby

You are better off asking the questions you have, rather than asking if anyone would be able to answer your questions.

---

### Post by lnostdal on 2008-02-18
i have done some work on arm/linux .. but i'm quite rusty .. (it's been years, many)

---

### Post by Siph0n on 2008-02-18
I did some (very little) work with embedded linux. One of my school projects required using a gumstix.

---

### Post by colby500 on 2008-02-18
OK.

I guess I will get specific....My question has to deal with running a camera vision library and IPP, specifically OpenCV.  While OpenCV runs fine on x86 arch, it is not fully functional under ARM.  For example, matrix element by element in broken(always returns 255), but matrix add works.

Is this a problem where I have to port the code?  Or is there a problem with IPP?  Could it be the tool chain(I have to cross compile)?  Something wrong with the Makefile?  Any feedback whatsoever would be greatly appreciated.  

I understand that this question is very specific and there is a 99.9% chance that no one is able to help, but if that .1 happens...it will save me a lot of trouble.

---

