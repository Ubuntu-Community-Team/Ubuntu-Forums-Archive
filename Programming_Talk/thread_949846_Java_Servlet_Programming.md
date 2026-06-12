---
title: "Java Servlet Programming"
date: 2008-10-16
forum: Programming Talk
---

### Post by Sugz on 2008-10-16
Ok, so im making a java servlet which takes in a name from the user, adds it into an array and then displays the array List. 
But i cannot find a way to store the array so when the user enters another name that name gets added to the array.

I have a basic spec and it explicitly expresses the use of the init() method.

I have hunted but found nothing.

What on earth is the init method? What does it do? how do i use it?

Any help will be appreciated.

-Sugz

---

### Post by jespdj on 2008-10-16
One way to do this in a servlet is to store the array in the session, and retrieve it when the next request is handled. For example:
```
String[] names = ...; // wherever you get this from

// Store array of names in session
HttpSession session = request.getSession();
session.setAttribute("Names", names);

// Later, somewhere else, retrieve the array of names
String[] names = (String[]) session.getAttribute("Names");
```

How much do you know about servlet programming? Are you doing a course? Can you show us your code?

In a servlet, you normally implement the doGet() and doPost() methods to handle HTTP GET and POST requests. The init() method is called by the servlet container when it starts up and initializes your servlet. You implement this in your servlet to initialize things, if necessary. Since servlets are normally stateless, you don't normally implement an init() method.

You can find documentation for the servlet API in the [Java EE API documentation](http://java.sun.com/javaee/5/docs/api/) (look at the package javax.servlet.http).

---

