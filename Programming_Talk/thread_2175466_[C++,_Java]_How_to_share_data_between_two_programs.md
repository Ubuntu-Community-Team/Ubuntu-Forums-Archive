---
title: "[C++, Java] How to share data between two programs"
date: 2013-09-19
forum: Programming Talk
---

### Post by erotavlas on 2013-09-19
Hi,

I would like to share data between a program A written in C++ pr C and another program B written in Java. The two program can be located in different networks. How can I do this? The simplest idea is to use a shared file where one program writes and the other program reads. The problem is how to manage the read/write conflicts. For example if the program A is writing the file how can I assure that the program B does not read the file? Is there a better way than a shared file?
Thank you

---

### Post by TheFu on 2013-09-19
Well, there are lots of ways to have programs communicate over a network. The language use doesn't matter, provided they speak the same protocol.  Going over the internet means that you want to use a secure channel, right? No traffic between 2 programs should be transmitted without encryption, IHMO.

* REST API with XML, JSON or other data packages
* XML API
* sockets
* CORBA (a little old school now)
* or any number of other methods can be used.  REST is what all the new kids use these days.

To prevent conflicts, use a session ID and client authentication. That way the server doesn't get confused between different clients. I'm certain there are existing libraries that handle these things, though I haven't written any C/C++ for this in a long time and never needed to communication outside the LAN.  With Python, Perl, Ruby, using REST is built-in and fairly easy.

---

### Post by slickymaster on 2013-09-19
[How to interchange data between Java Program and C++ Program]("http://www.codeproject.com/Questions/640568/How-to-interchange-data-between-Java-Program-and-C")

---

### Post by dwhitney67 on 2013-09-19
There's also [GMSEC]("http://sourceforge.net/projects/gmsec/?source=directory").  You can use one of the provided middleware services (e.g. Bolt), or use a COTS product (e.g. WebSphere), or even FOSS such as ActiveMQ.

Let me know if you have any questions.

---

### Post by erotavlas on 2013-09-20
Thank you for the answers. Now suppose that I have the following requirement. A more complicated scenario in which there a pseudo-server (C++ program) and many pseudo-client (Java programs). I have written pseudo since that I don't want to establish authentication/acknowledgement between the two programs. The pseudo-server is not aware of the existence of the pseudo-clients. The information need to be exchanged via files. In this case how can I share information avoiding conflicts?
Thank

---

### Post by ofnuts on 2013-09-20
Normally you can open the files with exclusive rights, so that only one of the sides can be dealing with a given file (read or write) at any time. But sharing data via files looks really like a bad design. A better solution would be to use some form of light database.

---

### Post by erotavlas on 2013-09-21
> **ofnuts said:**
> Normally you can open the files with exclusive rights, so that only one of the sides can be dealing with a given file (read or write) at any time. But sharing data via files looks really like a bad design. A better solution would be to use some form of light database.

I know that this is not good design. It's the reason for which I have asked here for other solutions. I'm not expert of database, but if I decide to use it how can manage multi-user without authentication? The quantity of data that the two programs need to exchange is limited. 
Thank

---

### Post by ofnuts on 2013-09-21
> **erotavlas said:**
> I know that this is not good design. It's the reason for which I have asked here for other solutions. I'm not expert of database, but if I decide to use it how can manage multi-user without authentication? 
EIther:
[LIST]
[*]you use the DB authentication: each user is given an id/pwd to the DB, and the software gets these from the user and uses them to access the DB on the user's behalf.
[*]the code uses some secret/hidden usr/pwd to access the DB, and the DB contains a table of users/passwords. The client software requires an id/pwd from the user and checks it against the DB.
[*]you can also envision a 3-tier solution with some web server in front of the DB (so that the real DB access is done only by that server, after cheicnk user credentials)
[/LIST]
 
> **erotavlas said:**
> The quantity of data that the two programs need to  exchange is limited. 
This makes the DB soltuion even more palatable.

This said, you seem to have a problem to solve, think up solutions, that lead to 2-level problems to which to think up solutions, that lead to 3-level problems ... and then you ask us about the latter. Metaphorically, you may be painting yourself in a corner, and just asking us for a better brush...  Maybe that if we are told about the original problem we can give better directions (why hsould one of the be written in C++?). Futhermore all this has the smell of a reinvented wheel, and I cannot convince myself that your original problem is that much different from other real-life problems for which the appropriate software already exists. Darwinism somehow  applies to application design... those you see everywhere must have some merit...

---

