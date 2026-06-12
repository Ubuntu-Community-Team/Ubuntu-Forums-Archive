---
title: "[SOLVED] Optimal MySQL connections"
date: 2008-11-15
forum: Programming Talk
---

### Post by cl333r on 2008-11-15
Hi folks,
I'm using Java on the server-side to update/delete items from a MySQL database. What's the best approach of doing this?
Should I keep one connection open and do everything through it?
Or should I open a new connection for every query/update (in a separate thread)?
I would appreciate any comments/examples..

PS: by "best approach" I mean as resistant to heavy load (user usage) as possible.

---

### Post by tinny on 2008-11-16
> **cl333r said:**
> Hi folks,
I'm using Java on the server-side to update/delete items from a MySQL database. What's the best approach of doing this?
Should I keep one connection open and do everything through it?
Or should I open a new connection for every query/update (in a separate thread)?
I would appreciate any comments/examples..

PS: by "best approach" I mean as resistant to heavy load (user usage) as possible.

Does this application run in a Servlet container? 

E.g. Tomcat, Jetty, Glassfish etc.....?

Most (I think all) Servlet containers provide some sort of connection pooling functionality. (Let the container do it for you)

---

### Post by drubin on 2008-11-17
> **tinny said:**
> Does this application run in a Servlet container? 

E.g. Tomcat, Jetty, Glassfish etc.....?

Most (I think all) Servlet containers provide some sort of connection pooling functionality. (Let the container do it for you)

Huge +1 on the connection pooling they can cut down on huge amounts of connecting time.

---

### Post by cl333r on 2008-11-17
Thanks a lot guys! I started using the DBCP from the Jakarta project:
[http://commons.apache.org/dbcp/](http://commons.apache.org/dbcp/)

PS: I'm using GlassFish v2

---

### Post by tinny on 2008-11-17
> **cl333r said:**
> Thanks a lot guys! I started using the DBCP from the Jakarta project:
[http://commons.apache.org/dbcp/](http://commons.apache.org/dbcp/)

PS: I'm using GlassFish v2

Glassfish has connection pooling built in

[http://docs.sun.com/app/docs/doc/820-5709/abyen?l=en&a=view](http://docs.sun.com/app/docs/doc/820-5709/abyen?l=en&a=view)

---

### Post by cl333r on 2008-11-18
I read a bit about it and here's my impression:
It's good that GlassFish has pooling built-in but to actually use it you have to configure it. So every time deploying on another machine you have to remember to configure the pooling mechanism on the server-side.
Since I'm using my own one (from Jakarta) I don't have to remember to do that and to me as a developer that sounds easier deployment.
Am I missing something?
If the only "drawback" is that I'm not using the built-in one, then I stay with the Jakarta project solution.

---

### Post by tinny on 2008-11-18
> **cl333r said:**
> I read a bit about it and here's my impression:
It's good that GlassFish has pooling built-in but to actually use it you have to configure it. So every time deploying on another machine you have to remember to configure the pooling mechanism on the server-side.
Since I'm using my own one (from Jakarta) I don't have to remember to do that and to me as a developer that sounds easier deployment.
Am I missing something?
If the only "drawback" is that I'm not using the built-in one, then I stay with the Jakarta project solution.

Usually a Web application will only have one production environment, so you will only need to set this up once.

Personally I would trust the application server to do a better job of connection pooling than what I could ever do by using a thrid party API.

---

### Post by drubin on 2008-11-18
> **tinny said:**
> Usually a Web application will only have one production environment, so you will only need to set this up once.

Personally I would trust the application server to do a better job of connection pooling than what I could ever do by using a thrid party API.

People do generally not move production servers often. IF they do get moved I think worrying about copying the configs of your server to the new one is the least of your worries.

---

