---
title: "Calling a .jsp file with AJAX and Javascript"
date: 2010-12-01
forum: Programming Talk
---

### Post by Uubnewb on 2010-12-01
I am writing a Java web-project, and all my different web-pages are Java Server Pages.  So far I am only using redirect commands and <form> tags to move from one page to the next.

However, now that the program logic is close to an end, I want to do the website with HTML, calling the different .jsp files as necessary using AJAX.

Unfortunately I do not have the slightest idea how to do that.  So far I have tried the following:
```

<form action="javascript:loadPage('pages/Home.jsp')" method="get">
[INDENT]...
Some stuff and a submit button inside the form.
...[/INDENT]
</form>

```
The above code is in the HTML file.  I want to be able to click on the submit button to load the Home.jsp file inside the contentPane <div> tags.

My Javascript is in a separate file that looks as follows:
```

function loadPage(url){
    var request = new XMLHttpRequest();

    request.open("GET", url, true);

    request.onreadystatechange = function(){
        if(request.readyState == 4){
            document.getElementById('contentPane').innerHTML = request.responseText;
        }
    }
    request.send(null);
}

```
When I click on the submit button, however, nothing happens.

Can anyone tell me what I am doing wrong please?

Any help will be hungrily devoured and appreciatively digested. ;)

Thanks in advance.

---

### Post by r-senior on 2010-12-01
Have you verified that loadPage() is being called? For example, have you tried feeding a literal string to .innerHTML?

I'd also think about whether "pages/Home.jsp" is the correct URL. Unless you prefix with the absolute context path, it's going to be a relative path. If your JSP with the form in it is also in "pages", you'd probably need "Home.jsp", otherwise it will be looking for "<your context path>/pages/pages/Home.jsp"?

I don't know if it makes a difference at all, but in a simple AJAX example I have that I know works, I have the open() after the function: 

```

<script type="text/javascript">
	function refreshTime() {
		xmlhttp=new XMLHttpRequest();
		xmlhttp.onreadystatechange=function() {
			if (xmlhttp.readyState == 4 && xmlhttp.status == 200) {
				document.getElementById("currentTime").innerHTML=xmlhttp.responseText;
			}
		}
		xmlhttp.open("GET","timeServlet", true);
		xmlhttp.send();
	}
</script>

```

If you are doing plenty of AJAX, it might be worth a look at the [Dojo toolkit]("http://www.dojotoolkit.org/"), which has a simple method for making similar requests.

---

### Post by Uubnewb on 2010-12-02
r-senior, thanks for the reply.

> 
Have you verified that loadPage() is being called? For example, have you tried feeding a literal string to .innerHTML?

You mean like this?:
```

request.open("GET", "pages/Home.jsp", true);

```
Or even this?
```

document.getElementById('contentPane').innerHTML = "pages/Home.jsp";

```

Neither made any difference.

> 
I'd also think about whether "pages/Home.jsp" is the correct URL. Unless you prefix with the absolute context path, it's going to be a relative path. If your JSP with the form in it is also in "pages", you'd probably need "Home.jsp", otherwise it will be looking for "<your context path>/pages/pages/Home.jsp"?

The form is in my index.html page, wich is not in the same directory as the rest of the pages.  My directory structure looks as follows:
[INDENT]dir_project
[INDENT]dir_images
[INDENT]some image files[/INDENT]
dir_javascripts
[INDENT]scripts.js[/INDENT]
dir_stylesheets
[INDENT]stylesheets.css[/INDENT]
dir_pages
[INDENT]all my .jsp files including Home.jsp[/INDENT]
file_index.html[/INDENT][/INDENT]

> I don't know if it makes a difference at all, but in a simple AJAX example I have that I know works, I have the open() after the function: 
I tried putting the open() after the function, but that did not seem to work either.

If you have any other ideas, please let me know.  Even if they don't work, I still appreciate them.

Thank you.

---

### Post by r-senior on 2010-12-02
> **Uubnewb said:**
> 
Or even this?
```

document.getElementById('contentPane').innerHTML = "pages/Home.jsp";

```

Neither made any difference.

I meant more like this:

```

document.getElementById('contentPane').innerHTML = "<p>Hello</p>";

```

... but what you did was basically the same. If nothing appeared in your DOM element, it looks like the onreadystatechange function is never called. Either that, or it is called and it can't find the element in the page to replace.

How about you try this bare-bones example in a clean web project and see if that works? The .html and .jsp go in your top level. The web.xml goes in WEB-INF.

*index.html*
```

<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Strict//EN" "http://www.w3.org/TR/xhtml1/DTD/xhtml1-strict.dtd">
<html xmlns="http://www.w3.org/1999/xhtml">
    <head>
        <meta http-equiv="Content-Type" content="text/html; charset=UTF-8"/>
        <title>AJAX Test</title>

        <script type="text/javascript">
            function refreshTime() {
                xmlhttp=new XMLHttpRequest();
                xmlhttp.onreadystatechange=function() {
                    if (xmlhttp.readyState == 4 && xmlhttp.status == 200) {
                        document.getElementById("currentTime").innerHTML=xmlhttp.responseText;
                    }
                }
                xmlhttp.open("GET","time.jsp", true);
                xmlhttp.send();
            }
        </script>

    </head>

    <body>

        <h1>AJAX Test</h1>

        <p id="currentTime">Press "AJAX Example" button to asynchronously replace
            this paragraph with the current time.</p>
        <p><button type="button" onclick="refreshTime()">AJAX Example</button></p>

    </body>
</html>

```

*time.jsp*
```

<%=new java.util.Date()%>

```

*web.xml*
```

<?xml version="1.0" encoding="UTF-8"?>
<web-app version="2.5" xmlns="http://java.sun.com/xml/ns/javaee" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://java.sun.com/xml/ns/javaee http://java.sun.com/xml/ns/javaee/web-app_2_5.xsd">
    <display-name>TestAJAX</display-name>
    <welcome-file-list>
        <welcome-file>index.html</welcome-file>
        <welcome-file>index.jsp</welcome-file>
    </welcome-file-list>
</web-app>

```

If that works, start moving step by step toward your solution but come back if you get stuck. If it doesn't we need to look at how you are deploying and running these things.

---

### Post by Uubnewb on 2010-12-02
r-senior, once again thanks for the help.

I actually fixed it earlier on (well, kind of).  I decided to copy and paste the names rather than retyping them, and that did the trick, so I must have mis-typed something somewhere along the line.

However, if you don't mind me bugging you some more, I'd be grateful if you could help me with another problem.  When the page (Home.jsp) loads, I cannot access any of the parameters.  It looks like they are not sent through from the index page.  Any idea what I might be doing wrong?

---

### Post by r-senior on 2010-12-02
If you want to pass parameters to an asynchronous request, you have to build the URL to send as the xmlhttprequest, e.g. "myAjax.jsp?param1=abc&param2=def".

You can do it manually but will probably find Dojo a great help:

[DOJO formToObject]("http://www.dojotoolkit.org/reference-guide/dojo/formToObject.html#dojo-formtoobject")

[DOJO xhrGet]("http://www.dojotoolkit.org/reference-guide/dojo/xhrGet.html#dojo-xhrget")

Before you go down that route, are you sure you need AJAX for this, i.e. an asynchronous request within the normal request/response cycle? What are you trying to achieve? Standard layouts for pages with a menu?

---

### Post by Uubnewb on 2010-12-02
I'm not sure if I specifically need AJAX, I just want to load the body part of the website without reloading the whole page.  AJAX is the only way I know how to do that.  If there are better/easier ways to do it, I'd welcome it.  

In the meantime I'll have a look at the links you gave me.

Thank you.

---

### Post by r-senior on 2010-12-02
When you say without reloading the whole page, is that because (a) you don't want to see it refresh, or (b) because you don't want to have all the boilerplate stuff duplicated across your content pages?

If the answer is (a), yes you need AJAX for the asynchronous requests and you'll have to deal with passing the parameters. Did I mention Dojo? ;)

If (b), there are a variety of ways to achieve what is generically called a [Composite View]("http://java.sun.com/blueprints/patterns/CompositeView.html"):

[LIST]
[*]Prelude and coda in web.xml, a.k.a. header and footer
[*]<jsp:include> tags
[*]SiteMesh
[*]Apache Tiles
[/LIST]

---

### Post by Uubnewb on 2010-12-02
The main reason I don't want to load the entire page is to not waste system resources.  However, if it will save me a lot of time, I'll be willing to go with a method that take more overhead as it will be the more logical choice.

I will take a look at the Composite View tomorrow.  For now I have to study for a test.  

Once more, thank you very much for all your help, I greatly appreciate it.

---

### Post by r-senior on 2010-12-02
The overhead isn't that great in the whole scheme of things. Most web application sites use standard request/response (including this forum). 

Ajax is more for adding a bit more interactivity - the countdown on an eBay auction for example or the sports score updates on news sites. You should be fine with the bulk of your page flow using standard request/response. Maybe look at Ajax to add a bit more slickness within pages if you think they need it.

---

### Post by Uubnewb on 2010-12-03
I guess you're right, the overhead is rather minimal, but it is always fun to optomize code as much as possible.  However, I was starting to waste some valuable time, so I switched back to standard requests and responses.  

There are still some bugs I need to sort out, but if need be I'll post them in a new topic since they're not related to this one.

Once again I want to thank you for all your help, time and effort.

---

### Post by r-senior on 2010-12-03
No problem. Let us know how you get on.

Is this a big application? Have you found writing with just JSPs manageable, or have you implemented some form of MVC?

---

### Post by Uubnewb on 2010-12-03
For me it is a big project, but I think for someone with more experience it will be a fairly small one.

The aim of the project is to allow employees to input their total time spent on each project at the end of the month.  The data is written to a database.  From there management must be able to request charts and diagrams that will show how much profit was made by each project.  Admin users must be able to delete redundant projects, merge projects that are the same, move employees from one project to the next etc.

I don't know what MVC is, but I'll look it up.  As for working with only JSPs, I found it quite manageable.  However, I am still very new to real programming (as opposed to college programming) so for all I know there might have been far easier ways to achieve my goal.

---

### Post by r-senior on 2010-12-03
Sounds like a decent size.

The problem with creating applications solely with JSP comes when people decide they like them, as I am sure they will. They ask you to add a bit here and a bit there, and before you can say "Copy and Paste", you have an IDE full of spaghetti.

The idea behind Model-View-Controller (MVC) in a web application is to divide responsibilities between components. So rather than having a collection of JSPs that do everything, you have:

* The model - your database and reusable code to access it
* The view - your JSPs, which end up as dumb rendering components
* The controller - usually a servlet that routes requests

So, suppose you have a JSP "listExpenseClaim.jsp" that lists the details of an expense claim. It could be accessing the database using JDBC, applying some business logic, presenting it and providing links to controller actions that add expenses, show graphs, etc.

The controller could be a servlet and look something like this (none of this is compiled code, just pulled out of the air):

```


public void doGet(...) {

    String action = request.getParameter("action");

    if ("listExpenseClaims".equals(action)) {
        listExpenseClaims();
    } else if (...) {
        ...
    } else if (...) {
        ...
    }

}
...

private void listExpenseClaims() {
    List c = model.getExpenseClaims(request.getParameter("employee"));
    request.setAttribute("claims", c);
    ...
    RequestDispatcher rd = new RequestDispatcher("listExpenseClaims.jsp");
    rd.forward(request, response);
}

```

In the above, the "model" object is something that represents your data model. Could be a data access object (DAO) for a simple project, or a transactional business service on a larger one. It hides away all the JDBC code and any business logic.

The JSP then looks something like this:

```

    ...
    
    <%-- No data access or business logic in here --%>

    <ul>
        <c:forEach items="${claims}" var="claim">
            <li>${claim.description}, ${claim.amount} ...</li>
        </c:forEach>
    </ul>

```

For a very small project, it over-complicates things. But as projects get larger, it pays off:

a. Objects in the model are reusable rather than code lost in JSPs
b. The service layer/DAOs are easily unit tested
c. The controller is the central dispatch point for all requests
d. The JSPs only render things, no business logic or JDBC code
e. The code is nicely separated
f. You can replace the view with other technologies, e.g. Velocity, XSLT

It's the basis of frameworks like Struts or the more recent Struts2, Spring MVC and Java Server Faces (JSF). These provide the controller part with the actions written by you and configured to fire in response to particular requests.

No need to go rewriting everything that you have done, or feel that you've done it wrong, but certainly worth looking at and understanding the principles of. Then when the spaghetti starts to pile up, you'll know what to do.

---

### Post by Uubnewb on 2010-12-06
Please excuse the delayed response.

Someone actually mentioned Spring to me, but I coudn't really get a good grip on what it actually is.  I mostly just knew that it is an alternative to enterprise JavaBeans (whatever that is).

But this explanation of yours puts things in a bit more perspective for me.  I can see the use of MVC, and am starting to think it might be a good idea to switch over sooner, rather than later.  I'll look for some tutorials to get me started with MVC and Spring.

Just to make sure I understand correctly: Using Struts, Struts2, Spring MVC and Java Server Faces; are all different ways of achieving MVC, right?

---

### Post by r-senior on 2010-12-06
Note that Spring and Spring MVC are really two separate things. Spring was originally created as a simpler and smoother alternative to Enterprise Java Beans (EJB), where distributed applications (components running across multiple machines) are not a requirement. With EJB3, the use of EJB has been greatly simplified but Spring is still justifiably popular.

The focus of Spring is broad and it's best to think of it as a toolkit that you can pick and choose from. The core of Spring is a dependency injection framework that allows you to connect objects together, but it also provides things like JDBC templates, AOP, transaction support and simplified access to Java EE APIs like JavaMail and JNDI. Also templates for non Java EE APIs like the Quartz job scheduler and support for things like Hibernate.

  * Dependency injection framework - allows you to connect objects together, e.g. a business service object to supporting objects like transaction managers and data access objects (DAOs) for different databases. Components remain unconnected in code and are very easy to reuse or reconfigure by changing a configuration file rather than wholesale code changes.

  * AOP (Aspect Oriented Programming) - allows you to create classes, e.g. for logging or profiling, and apply them system-wide without changing code.

  * Transaction support - instead of fiddling with commit and rollback when trying to make transactions with multiple tables (or across databases), simply declare a business method as transactional and Spring uses AOP to start transactions and commit or rollback.

  * Hibernate - allows you to work with persistent objects in your application and let Hibernate take care of the complexities of mapping complex objects to database updates. For example, your expense claim will probably have a parent-child relationship of claim (claim date, employee, etc) and claim line (date, type, amount, etc). With Hibernate, you can just deal with the claim as a whole and any changes you make to claim or claim line will be reflected in the database.

Spring MVC works well with Spring but is an MVC framework for creating the web tier of an application. You are correct that Spring MVC, Struts, Struts2 and JSF all do basically the same job. They all work with Spring too. Maybe not quite as seamlessly as Spring MVC, but certainly not difficult to achieve.

You are probably thinking there is a bewildering choice and you'd be right. Some of these things are overkill for smaller applications (if they stay small) but really come into their own on larger applications.

---

