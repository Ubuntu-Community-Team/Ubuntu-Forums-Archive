---
title: "JSP and JavaBeans"
date: 2009-05-12
forum: Programming Talk
---

### Post by tashe on 2009-05-12
I am a little confused with the usage of JavaBeans and JSP.
It says
> By using JavaBeans you can fully separate the business logic from the generation of the display. In our case you would use the JavaServer Page to dynamically generate display and also to handle the user interaction. The JavaBean would take over when you need to perform some complex data processing or when you need to access databases or the file system.


But isn't the job the Bean will do also possible with custom written JSP tags?
greetings Mite

---

### Post by jespdj on 2009-05-12
Ofcourse, but the text doesn't say that using JavaBeans is the **only** way you can do whatever you do with them.

You could write an entire Java program between <% and %> tags in a JSP, but that would make your JSP an ugly and hard to maintain mess. JavaBeans is just one of the ways to separate presentation logic from business logic.

---

### Post by tashe on 2009-05-12
Yes. But what I wanted to ask is, since the Bean has some methods and attributes in it, can't you place these methods and atributes in a custom JSP written tag like <jsp:insteadOfBean>, pass the tag some parameters and it will do the job like a JavaBean. Or am I way of the track? :(
tahnks for the reply

---

### Post by kpkeerthi on 2009-05-12
A custom tag is generally used to render a content on the page. 

A JavaBean is generally used to abstract some logic performed on the page.

---

