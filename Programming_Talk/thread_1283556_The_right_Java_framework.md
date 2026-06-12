---
title: "The right Java framework?"
date: 2009-10-05
forum: Programming Talk
---

### Post by Fittersman on 2009-10-05
Hey, I'm looking for some advice on what Java framework to use.

My group and I are going to be working on a Java web application that is essentially a photo CMS. One of the project requirements is that we must pick a programming language (my group chose Java), along with a framework. 

Does anyone know of a Java framework that would suit this type of project well? (or even a framework that would NOT suit this project at all, that would help too.) I'm doing some research on my own too, but it does help getting advice from people that have actually used certain frameworks before.

Thanks for any suggestions.

---

### Post by dxxvi on 2009-10-06
You definitely have ajax features in your app, so you shouldn't choose an action-based framework like Spring MVC, Struts ...

So the candidates are JSF, GWT, Flex, Wicket and a bunch of not-very-popular frameworks. I won't choose wicket because there's no book about the latest version of wicket (1.4) yet (except one in Germany).

I'll choose JSF. If you also choose JSF, then you should choose Seam, not Spring.

My 2 cents.

---

### Post by CptPicard on 2009-10-06
It needs to be remembered that Spring gives you not only a decent http request handler, but more importantly a nice back-end framework. It is more of a J2EE stack replacement than a simple web app framework. I always found JSF to be very cumbersome, and it pretty much wants to be combined with proper J2EE server too according to my understanding.

On the other hand I am currently experimenting with a combination of Spring and GWT. Spring for the service layer and simple request handling, GWT for the ajaxy features...

---

### Post by mmix on 2009-10-06
spring : +1

---

### Post by AlexSerov on 2009-10-24
[quote=Fittersman;8057936]Hey, I'm looking for some advice on what Java framework to use.

Try [http://www.hybridserverpages.com/](http://www.hybridserverpages.com/)

Alex

---

