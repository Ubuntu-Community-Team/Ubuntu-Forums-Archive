---
title: "Open source J2EE platform"
date: 2007-08-15
forum: Programming Talk
---

### Post by jibey.jacob on 2007-08-15
Hi:

Which is a great free and open source J2EE platform I can use to learn it's new features? I want to run my website using JSP, if new JSP is object-oriented like ASP.NET. I'm investigating whether JSP is still a script-based framework like classic ASP.

Any help would be appreciated.

Thx.

---

### Post by pmasiar on 2007-08-15
More modern, flexible, and maintainable approach than JSP is [http://en.wikipedia.org/wiki/Model-view-controller](http://en.wikipedia.org/wiki/Model-view-controller) , which separates model (data), business logic (controller) and presentation (view).

Java has Spring and Struts, but they cannot compare in flexibility with frameworks build using dynamic languages like Python (Django, TurboGears) or Ruby (Ruby on Rails). You will be 20 times more productive in dynamic language.

---

### Post by laxmanb on 2007-08-15
Coming back to your question, JSP IS quite like ASP. 
Try **Apache Tomcat** for JSPs. 

for J2EE (Hibernate, EJB, Spring, etc.) , you have a lot of choices: Try either **JBoss** or **Glassfish**. Both are application servers and a lot more powerful (and RAM consuming)

---

### Post by CptPicard on 2007-08-16
Using scriptlets in JSP is so 90s :) You just don't do it, and I'd fire an underling for doing it in a project where I was the manager...

Modern JSP is just another view technology. You populate the page scope with whatever you need, and then use the JSP to render that.

Also, Struts is archaic, and actual J2EE is still  cumbersome, although it is really your only choice if you're doing really heavy-duty enterprise development with clustering+multi-machine transactions. You just don't get that with Ruby on Rails, but I doubt you're in need of them...

A "better, modern Struts" would be Spring MVC -- and by the way, Spring isn't J2EE; it aims to be a lightweight replacement to it.

To give the actual answer to your question, the answer is Geronimo or Glassfish or JBoss (which is The J2EE server, but not sure about open source there? Wasn't it?). Tomcat is not a full-blown J2EE container, and I doubt you need one. I have gut feeling what you should look at is the combination of Tomcat and Wicket+Spring+Hibernate. Wicket is a component-based web view framework ("a simpler JSF"), Spring handles your business components, and Hibernate does the persistence. Gluing them together takes some work though.

If you're going with J2EE proper, try out JBoss's Seam and the associated Eclipse plugins. I hear they're trying to take the pain out of J2EE, not sure if they have succeeded.

---

### Post by jibey.jacob on 2007-08-17
Thanks for all the free advice.

I think I'll go for a dynamic programming language like Ruby. I'm assuming I can do Web/HTTP stuff, XML Web Services, etc. using it. Can't I? I also might need to write some SOA services that can interoperate with services implemented using Microsoft Windows Communication Foundation. Is Ruby appropriate for that?

And is there an open source email server available for Linux that offers the same functionality as Outlook Web Access for Exchange Server?

Also, is there a portal/collaboration solution like Windows SharePoint Services available for Linux?

Thanks.

---

### Post by pmasiar on 2007-08-17
> **jibey.jacob said:**
> I think I'll go for a dynamic programming language like Ruby. I'm assuming I can do Web/HTTP stuff,

yes, web apps is Ruby's niche.

> XML Web Services, etc. using it. Can't I? 

Depending on libraries. Ruby is "new kid on the block" and does not have as many libraries as more mature languages, like Perl and Python. But ppl add libraries all the time.

> I also might need to write some SOA services that can interoperate with services implemented using Microsoft Windows Communication Foundation. Is Ruby appropriate for that?

Depends on libraries. BTW: REST is widely considered better way to do it. 

> Also, is there a portal/collaboration solution like Windows SharePoint Services available for Linux?

Depends what you want. [Trac](http://en.wikipedia.org/wiki/Trac) is widely used (one of many) tools for collaboration around software development. Do you experience "vendor lock-in", if you are so interested on MSFT technologies? Many people are looking for "best of the breed" technology, which is most often **not** MSFT one. :-)

---

### Post by jibey.jacob on 2007-08-17
Is Ruby object-oriented?

---

### Post by pmasiar on 2007-08-17
But Python and Ruby are OOP languages, close to Java, in a much cleaner way than Perl. Arguably :-) Python is **more** OOP than Java because Python has so called "multiple inheritance".

BTW it is **not** a serious argument: It is a joke around old programmer's joke:
Q: Why C++ coders bring home more money than Java coders?
A: Because C++ has multiple inheritance!

---

### Post by CptPicard on 2007-08-17
> **jibey.jacob said:**
> Is Ruby object-oriented?

I'd say it is extremely so -- it's designed as as "pure" an OO language as possible.

I have a hunch you'll have trouble with that web services and SOA part with RoR...

---

