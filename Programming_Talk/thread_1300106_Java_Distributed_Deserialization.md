---
title: "Java Distributed Deserialization"
date: 2009-10-24
forum: Programming Talk
---

### Post by MCBTunes on 2009-10-24
Hi, I am making a program where a client and server exchange "Message" objects back and forth. I have been designing the program by just including the classes source in both programs. But upon testing the Server attempts to deserialize to the clients version of Message and I get a class not found exception. 

I deleted the Server's copy of the Message class and did some googling. People say add the Clients version to the servers classpath however I'm not really sure how to do that. The client and server could be running on any machine so I am not exactly sure how to do this. I am using the Eclipse IDE and Client and Server are two different projects. 

How can I use the Clients "Message.java" source in my Server project?

Thanks a ton.

---

### Post by kavon89 on 2009-10-24
Read about Serialization, might help clear things up:

[http://java.sun.com/developer/technicalArticles/Programming/serialization/](http://java.sun.com/developer/technicalArticles/Programming/serialization/)

[http://java.sun.com/javase/6/docs/api/java/io/Serializable.html](http://java.sun.com/javase/6/docs/api/java/io/Serializable.html)

---

