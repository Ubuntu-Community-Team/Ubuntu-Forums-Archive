---
title: "Program Design Advice"
date: 2012-10-06
forum: Programming Talk
---

### Post by KdotJ on 2012-10-06
Hey guys, wanted some opinion input on something...

I am developing an application (well, a set of applications) that will connect to a database on a server. One will run on a desktop and one will be an Android app. They will both need to read and write to the database.

My question is, what is the preferred way to do this between using sockets or a set of web-services? Which is safer in terms of exposing the database and more robust to implement? Or is there a different solution altogether?


Thanks

---

### Post by Tony Flury on 2012-10-06
I would be tempted to use some sort of http based REST service to expose the database. That way you expose the data the way you want - but not the database - and you don't have to worry about something horribly complex application on top of raw sockets.

You can also rely on nice things like https to perform the security.

---

### Post by KdotJ on 2012-10-06
Thanks for the speedy reply. You have a good point about worrying about the socket implementation. I think I'll go with servlets and allow them to handle the read/writes. Thanks again

---

### Post by Some Penguin on 2012-10-06
Spring + Hibernate is a pretty common model for that sort of thing.  At work, we've taken a different approach and built up an infrastructure around Jersey (JAX-RS; HTTP layer), Jackson (JSON and SMILE ser/deser), and JDBI (db interactions), with Jetty for an embedded HTTP server.

This isolates the data model and database from the end user -- you should be free to change the in-database data organization, which machine(s) host it, authentication credentials, etc without the applications noticing; and likewise, the end users should not have any access other than the indirect, limited access you choose to explicitly provide.

Basically, the end-users get limited access via a front-door server (which must be publicly accessible and known), and everything else -- including our actual application servers, the database servers, et al -- are behind a firewall, not accessible or even identifiable.

---

### Post by r-senior on 2012-10-07
+1 for a REST web service.

The Java annotations for JAX-RS (Jersey) make it really simple, especially combined with JAXB annotations on the entities and Spring/Hibernate or EJB 3.1 shunting the data to and from the database.

It doesn't have to be Java of course but this is what it is good at.

---

