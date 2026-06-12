---
title: "When throws keyword is used?"
date: 2013-11-26
forum: Programming Talk
---

### Post by jerome.sturt on 2013-11-26
When throws keyword is used? 

who knows best answer for that question?

i am studying java .. still i did not get correct answers..

---

### Post by Toz on 2013-11-26
*Moved to the **Programming Talk** subforum.*

Hello and welcome to the forums. I have moved your thread to a more suitable sub-forum for your question.

---

### Post by r-senior on 2013-11-27
The Java SE tutorial covers exceptions in general

[http://docs.oracle.com/javase/tutorial/essential/exceptions/](http://docs.oracle.com/javase/tutorial/essential/exceptions/) 

Specifically, it deals with the throws keyword in this section

[http://docs.oracle.com/javase/tutorial/essential/exceptions/declaring.html](http://docs.oracle.com/javase/tutorial/essential/exceptions/declaring.html)

---

### Post by ofnuts on 2013-11-27
The throws keywords is used when you don't want to handle some exception in the method, but leave its handling to some code higher in the call hierarchy. More or less by using "throws" the implementation of the method passes the hot potato to its caller, which can in turn dodge it by using "throws" itself.

---

