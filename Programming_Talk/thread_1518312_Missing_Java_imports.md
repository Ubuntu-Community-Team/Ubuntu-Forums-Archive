---
title: "Missing Java imports"
date: 2010-06-26
forum: Programming Talk
---

### Post by PaulM1985 on 2010-06-26
Hi

I am trying to set up my Ubuntu laptop so that I can do some of my coursework on here rather than my Windows PC.  My course provided me with a disc with the appropriate version of Netbeans to complete my work (for Windows).

I have downloaded Netbeans 6.9 with EE plugin and Glassfish App Server but I am getting errors like the following when I am compiling:

package javax.ejb does not exist

and not being able to find the symbol on annotations.

Does this mean that my install didn't have enough of Java EE?  Is there an easy way to fix this.

Paul

---

### Post by Reiger on 2010-06-26
It means that your compile/run-time classpath doesn't contain the required libs, which suggests that you have Java SE without the EE libs installed.

---

### Post by PaulM1985 on 2010-06-26
I have solved my problem.  I had in my solution 2 projects.  When I opened those each needed a reference to the server.  Having fixed these references to the glassfish server everything compiled and ran ok.

Sorry for the false alarm.

Paul

---

