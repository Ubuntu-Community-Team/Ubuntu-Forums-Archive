---
title: "can i use EJB with Swing?"
date: 2009-06-23
forum: Programming Talk
---

### Post by sthiranga on 2009-06-23
Hi,
       I am developing an Swing application using "Netbean" IDE for GUI.Can i use the "EJB" with swing?
Futher information or refrences or links will be great Help.
Thanks.
regards

---

### Post by jespdj on 2009-06-23
[EJB](http://en.wikipedia.org/wiki/Enterprise_JavaBean)s (Enterprise JavaBeans) are components that run on the server in a [Java EE](http://en.wikipedia.org/wiki/Java_Platform,_Enterprise_Edition) application. Swing is Java's standard GUI library. Ofcourse it is possible to write a Swing application that connects to EJBs running on the server.

What exactly do you want to accomplish, what is your reason for asking this question?

It sounds like you don't know what EJBs are. Java EE, of which EJB is a central part, is a huge subject which is not easy to explain or learn in a few lines in a forum topic. Have a look at [Sun's Java EE tutorials](http://java.sun.com/javaee/reference/tutorials/).

---

### Post by morkelkey on 2009-06-24
yes  it can be done. i can do on jboss j2ee server

step1 :- for simplicity u donload jboss version 3.2.2 or above, eclipse-2.1 to 3.1.0, lomboz plugins according eclipse version from [www.objectlearn.com](www.objectlearn.com). plugins documentation avaliable at [www.au.tuse.com](www.au.tuse.com)

step 2 :- configure eclipse with  lomboz , jboss  & j2sdk. according documentation

step3:- create ejb realted file  then create  ejb test client . in ejb tst client call swing class.

---

### Post by sthiranga on 2009-06-29
@morkelkey
Thank for all the information.

---

