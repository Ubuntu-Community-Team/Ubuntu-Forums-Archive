---
title: "CORBA + Java"
date: 2009-04-27
forum: Programming Talk
---

### Post by sefs on 2009-04-27
Hey all,

I just dusted off one of my old software book from back in the day (1996-1998).  It's called client server programming with java and corba.  

Are any of you using CORBA these days, and how do you find it.

Thanks.

---

### Post by dwhitney67 on 2009-04-27
I have not used CORBA in a few years; I found easy to use, but a pain to setup.  I was using the ACE/TAO flavor, and developing in C++ (and a little Java).

CORBA is still used today on the [JTRS]("http://en.wikipedia.org/wiki/Joint_Tactical_Radio_System") program, but because of complaints about overhead, complexities, and what have you, the rumor is that it will be deep-sixed.

CORBA is something that I hope to never see again.

---

### Post by rangalo on 2009-04-27
For java you can use JaCORB for  corba. 

With corba there is a lot of boilerplate code to write, if you have worked with EJB  specifications 1 or 2, they were very near to the corba implementation. After the new EJB 3 specification, all the java based remote components are very easy to implement with EJB 3 or higher. If you have a mixed language/technologies, you can go for CROBA, but this can also be achieved by webservices.  

CORBA is still used at many places, but mostly with legacy systems. All the implementations of fresh projects now tend to use EJB or related technologies.

[EDIT]
jacorb - [http://www.jacorb.org/](http://www.jacorb.org/)

---

### Post by jespdj on 2009-04-28
Unfortunately there is an enormous amount of old CORBA junk in the standard Java library, because long ago (with Java 1.0 or so) someone thought it was a good idea to put it in the standard library, and now it can't be removed because that would make Java not compatible with older versions.... :(

On the other hand, one of the big new features that Sun is working on for Java 7 is modularizing the JDK. That way, the CORBA stuff could be put in a separate module, and if you don't use it, you can just choose to not install that module.

---

