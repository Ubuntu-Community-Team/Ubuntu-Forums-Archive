---
title: "JSP, Struts, JSF, Jakarta, Tomcat, Apache, Javabeans, Netbeans, what????"
date: 2006-02-13
forum: Programming Talk
---

### Post by bbqbaker on 2006-02-13
i diving into dynamic web development and decided that using Java would be best for me, mainly because I think it will help further my knowledge in computer science etc...instead of going the PHP route.

after doing some basic researching, i am coming across all these java related branches and I am not really sure what I should be using.

my first project, i will be building a basic car database for the town i live in. i want the user to be able to insert info about their car and photo, the visitors to run queries, etc..i did some like this for my senior design project many yrs ago in perl and mysql.

now from my understanding, JSP is the initial webpage form that sets values to each field in the form, populate a java bean, send this bean to apache, apache will send it to tomcat, and tomcat will pass it to the java program where it will then be processed? is this right? if not, please shed some light...

now what is Struts, and Java Server Faces? In what ways would using them benefit my basic car website?


thanks!

---

### Post by thumper on 2006-02-13
* Jarkata - apache project for java "bits"
* JSP - java server pages - allows embedding of java code in HTML.  Converted into a servlet by the server.  Often used to create a **view** on other java code.  
* Struts - a model/view/controller architecture for writing java web applications.  All page flow control is handled by the servlets and the views are either JSP or JSF.
* Tomcat - a java web application server from apache - good and free.

Java Server Faces really came into their own just as I stopped doing java, so someone else will have to provide bits on this :)

Personally I am looking into Zope3 for my web apps now.

---

### Post by bbqbaker on 2006-02-13
hey thumper, thanks for the reply...


for the past 10mins, ive been reading up on ruby on rails. any thoughts on this?


from what i seen, it looks pretty damn quick for the stuff id like to acomplish.

i going to read up on Zope3..

---

### Post by thumper on 2006-02-13
Nope.  No comments on ruby on rails.  Not because I don't think its any good, but more because I have not had the time to look at it.

Each person has their own personal preferences, and mine is python over ruby.

You could also look at [django](http://www.djangoproject.com).

---

### Post by gord on 2006-02-13
django is fantasticly good, django and rails type web development is definatly the way for the future

---

### Post by LordHunter317 on 2006-02-13
[QUOTE=thumper]* Jarkata - apache project for java "bits"
* JSP - java server pages - allows embedding of java code in HTML.  Converted into a servlet by the server.  Often used to create a **view** on other java code. [/quote]Careful there.

 [quote* Struts - a model/view/controller architecture for writing java web applications.  All page flow control is handled by the servlets and the views are either JSP or JSF.[/quote]And it's crap.  Pretend Struts doesn't exist.  Spring as well. 

There are several other Java frameworks out there that are superior.


> * Tomcat - a java web application server from apache - good and free.It's good because it's free.  It doesn't have much else going for it besides being the reference implementation and being embedded in JBoss.  It's not a very good web container, all told.

> Java Server Faces really came into their own just as I stopped doing java, so someone else will have to provide bits on this :)JSF is Sun's answer to ASP.NET.  It lets you define and manipulate tags on your JSP pages that correspond to actual elements the users see.  In your servlets, you manipulate these controls, providing proper seperation between code and presentation.  It's vaguely similiar to Struts HTML controls, but more featureful.

Unfortunately, it's not quite as nice as ASP.NET, but nice enough.  Frameworks using JSF and that work around it are the way of the future.

[quote=gord]django is fantasticly good, django and rails type web development is definatly the way for the future[/quote]Rails is a step backward from the model put forth by ASP.NET.  It has some nifty ideas, but they're not the kind of nifty idea I want.

I'm ultimately not a fan of any framework that attempts to generate my "data" objects for me, because they all make it *harder* to do what I want: Lazy-loading of large lists, intelligent caching of records, intuitive security.  They also tend to force suboptimal or just bad database design: like the use of surrogate keys everywhere.

---

### Post by bbqbaker on 2006-02-13
so many choices, gets rather confusing, especially when one always changes their mind constantly about many other things!

---

### Post by jerome bettis on 2006-02-13
[quote=thumper]* Jarkata - apache project for java "bits"
* JSP - java server pages - allows embedding of java code in HTML.  Converted into a servlet by the server.  Often used to create a **view** on other java code.  [/quote] 
could you explain what a servlet is?  i'm a total noob to this stuff but i really should look at it, cause the job market for someone who knows this is excellent around here.  also what exactly do you mean by creating a view on other code?

i should go get a book on this.  also everyone always wants J2EE, wtf is the difference between J2EE and just using the JDK like i've been for years?  i know it stands for enterprise edition, but that's about it.  what does it have that i don't know?  my focus in school was just to write the best code i could, not know all kinds of business things like this and now i can't find work.  but i think once i get in the door i'll be just fine.

---

### Post by LordHunter317 on 2006-02-13
[QUOTE=jerome bettis]could you explain what a servlet is?[/quote]A servlet is a Java class that implements the servlet interface, and responds to a request by giving a response.

Generally when people speak of servlets, they're talking servlets that respond to HTTP for processing web requests.  They're given an HTTP request and give back a web page (or image, or whatever) as a response.

You could conceptually use servlets for any request/response protocol if you built the required infrastructure, but it probably wouldn't be worth it.  I've never pratically heard of servlets being used outside the web context.

> i should go get a book on this.  also everyone always wants J2EE, wtf is the difference between J2EE and just using the JDK like i've been for years? J2EE is a superset that includes things like Servlets, JSP, and EJB.  It's meant for building server-side applications.

---

### Post by jerome bettis on 2006-02-13
thanks, i guess i'm looking for a book on J2EE then.

---

### Post by LordHunter317 on 2006-02-13
Sun has tutorials online, but they're of dubious quality.  They leave a lot unanswered.  I don't know any good, reasonably recent books.

---

### Post by thumper on 2006-02-14
[QUOTE=jerome bettis]also what exactly do you mean by creating a view on other code?[/QUOTE]

A view in this context is part of the model-view-controller pattern.  This is worth looking up and understanding.

The view is how the outside world looks at your internals.  For example, following on with the JSP terms, you may have some java classes that are used internally (the model bits), and you may have one page that renders these as HTML, and another that renders the same information into SVG or general XML.

---

### Post by LordHunter317 on 2006-02-14
[QUOTE=thumper]A view in this context is part of the model-view-controller pattern.  This is worth looking up and understanding.[/quote]No, it isn't.  No one really uses MVC on the Web or even in a thick-client UI anyway, even though lots of people "claim" to, and lots of frameworks claim to suppor it.

But, when you look at the frameworks, that's not really what you end up doing.  At most, you usually do MV, if that.

It's only really worth knowing in the sense that it's a buzzword everyone expects you to know.

---

### Post by bbqbaker on 2006-02-14
isnt it important if one was to start learning RoR?

---

