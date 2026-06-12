---
title: "Passing variables in JSP"
date: 2009-08-06
forum: Programming Talk
---

### Post by PaulM1985 on 2009-08-06
Hi

I am trying to create a website to display a large amount of photos and have about 10 on each page.  I thought that an easy way to do this would be to have a for loop from 1 to 10 selecting the files I need.

I wanted to know if I would be able to add a link at the bottom of the page that reloads itself, but will then iterate through 11 to 20, then 21 to 30 and so on.

I want to do:

```

for(int i=picnum; i<picnum+10; i++)
     {
     out.write("<img src=" + "\"" + i + ".JPG" + "\"" + " /></a>\n");
     }


//link that when clicked adds 10 to picnum

```


Is this possible?

Paul

---

### Post by PaulM1985 on 2009-08-06
Solved.

I created new pages increment.jsp and decrement.jsp and set a session variable using
session.setValue("variableName", myVar);

increment would use

session.getValue("variableName");
to get it, increment it, then set it again.

Paul

---

### Post by CptPicard on 2009-08-06
A more common approach would have you read up on HTTP GET request parameters and then produce those for the URL.

And btw you'd be served well by learning to use JSTL tags from the get go. The way you are doing a loop is pretty ugly.

---

### Post by PaulM1985 on 2009-08-06
> **CptPicard said:**
> A more common approach would have you read up on HTTP GET request parameters and then produce those for the URL.

And btw you'd be served well by learning to use JSTL tags from the get go. The way you are doing a loop is pretty ugly.

I have never heard of JSTL tags but I will look into them.  I have had to produce a website quite quickly and I have experience of Java and HTML but nothing server side.  I had heard of JSP and was looking into it to see if it could speed up my time working on it.

Thanks for the advice with the JSTL tags.

Paul

---

### Post by CptPicard on 2009-08-06
In general, in modern JSP, whenever you're using the 

```

<%  %>

```

style raw Java scriptlets, you're doing it wrong... :)

---

### Post by froggyswamp on 2009-08-06
> **PaulM1985 said:**
> Solved.

I created new pages increment.jsp and decrement.jsp and set a session variable using
session.setValue("variableName", myVar);

increment would use

session.getValue("variableName");
to get it, increment it, then set it again.

Paul
Afaik session.getValue is deprecated, use getAttribute/setAttribute instead.
Also, adding a new parameter would allow you to use only one page.

---

### Post by furuno on 2009-08-07
Well, just a recommendation, but maybe you want to take a look to the [Apache Wicket]("http://wicket.apache.org/") framework, it a very nice web framework that "doesn't make you to learn another language other than Java & HTML". It have a very simple learning curve, you make web pages as you make a Swing GUI application, and it use pure HTML code (not special HTML just like in JSF).

It is also a MVC framework and a much better programming practices rather than using inline <% %> Java code just as stated by CptPicard...

---

