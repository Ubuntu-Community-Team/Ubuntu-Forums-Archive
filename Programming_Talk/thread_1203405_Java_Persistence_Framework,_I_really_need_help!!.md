---
title: "Java Persistence Framework, I really need help!!"
date: 2009-07-03
forum: Programming Talk
---

### Post by piousp on 2009-07-03
S.O.S

Hi folks, i'm having major trouble here.

Let me explain the situation:

We are working on a web-based project. So, i got assigned as the lead programmer and i'm in charge of making the technical decisions. Right now we are using JSF in a 3 Tier architecture.
BUT, and this is a big but, our project manager dont even know what java is, and he has only worked with oracle forms before. Somehow, he designed the data base and we programmers now have this -legacy- database to work with.

At first, we though of building our specially made persistence layer, but now it just seems to be non-viable.

SO, we are looking for persistence frameworks.

I've found this page:

[http://java-source.net/open-source/persistence]("http://java-source.net/open-source/persistence")

We really need something flexible, because the databased is really something we call "legacy" =(. Any suggestions??

---

### Post by hoboy on 2009-07-03
Well you can use [https://www.hibernate.org/](https://www.hibernate.org/)
it is really great.
it has plugging for eclipse and many other ide.

---

### Post by piousp on 2009-07-03
Ok, nice! Downloading it right now. Thanks for the suggestion!

---

### Post by hoboy on 2009-07-03
> **piousp said:**
> Ok, nice! Downloading it right now. Thanks for the suggestion!

I has great doc of how to hook on db then generate the xml and the java file 
[http://docs.jboss.org/hibernate/stable/core/reference/en/html_single/](http://docs.jboss.org/hibernate/stable/core/reference/en/html_single/)

---

### Post by piousp on 2009-07-03
> **hoboy said:**
> I has great doc of how to hook on db then generate the xml and the java file 
[http://docs.jboss.org/hibernate/stable/core/reference/en/html_single/](http://docs.jboss.org/hibernate/stable/core/reference/en/html_single/)

Woah, its huge! :lolflag: But thanks!

---

### Post by hoboy on 2009-07-03
> **piousp said:**
> Woah, its huge! :lolflag: But thanks!

well you will onluy use hibernate.jar in your classpath.
you can also use

Hibernate Tools for Eclipse and Ant

[https://www.hibernate.org/255.html](https://www.hibernate.org/255.html)
so it actually very simple to use.
and the doc is very user friendly

---

### Post by CptPicard on 2009-07-03
Yeah, Hibernate seconded. It really allows you to map very flexibly, even when the database schema comes from some other source. The only downside is that the more complex mappings really have a learning curve, but I guess you can't have everything... you may want to read a good book on the subject, something like "Java Persistence with Hibernate".

---

### Post by piousp on 2009-07-03
> **CptPicard said:**
> Yeah, Hibernate seconded. It really allows you to map very flexibly, even when the database schema comes from some other source. The only downside is that the more complex mappings really have a learning curve, but I guess you can't have everything... you may want to read a good book on the subject, something like "Java Persistence with Hibernate".

Yeah, i'm reading some tutorials right now. The learning curve its acceptable for me, specially compared to doing manual mapping of that beast.

---

