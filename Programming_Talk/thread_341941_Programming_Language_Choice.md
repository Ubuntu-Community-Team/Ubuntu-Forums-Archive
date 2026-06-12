---
title: "Programming Language Choice"
date: 2007-01-19
forum: Programming Talk
---

### Post by se2schul on 2007-01-19
I've decided to make a little app, and I need some suggestions for language choice to arrive at a solution.
I'd like it to be platform independent. 
I was hoping to run the software on my home server and allow people to interface with it using a web browser.  That way, it would be platform independent, yet still run on any machine that can run a web browser and not force people to install stuff like java.

Basically, the user would need to provide some input by means of a form on a web page, the data would be passed to a program on the server's back end, the back end would perform some floating point math, and the results would be displayed in the user's browser.

What are good solutions to this?
My initial thought was HTML/Perl/CGI front end and a C backend.  I've been out of touch with web technologies for a while, so if there are preferred solutions, please let me know.

Thanks!

---

### Post by lloyd mcclendon on 2007-01-19
stripes, [http://stripes.mc4j.org](http://stripes.mc4j.org) is a very nice java web framework.

basically you'll write a jsp that has some text fields for the input.  the user clicks a submit button, which invokes a method in a plain old java bean.  the bean has properties which mirror & are bound to your form your form fields.  you do the calcuation in that bean, and return to a result page.

here's a quick example of a round trip in stripes.  this is very simple, you can do a lot more than this!!
input.jsp
```
<@jsp:taglib prefix="stripes" uri="i forget" />
<html>
<head>
     <title>Calculator</title>
</head>
<body>
<stripes:form action="/Calculator.action" method="POST">
    <stripes:text name="arg1" />
    <stripes:text name="arg2" />
    <stripes:submit name="add" />
</stripes:form>
</body>
</html>
```

CalcuatorActionBean.java
```
@UrlBinding("/Calculator.action")
public class CalculatorActionBean implements ActionBean  {
     private int arg1;
     private int arg2;
     private int result;

     public Resolution add()  {
         result = arg1 + arg2;   // if we get here, all validations have succeded & the form values are bound
         return new ForwardResolution("output.jsp");
     }

     // this stuff is usually in a base class
     private ActionBeanContext context;
     // getters & setters for context

     // getters & setters for private fields
}
```


output.jsp
```
<html>
<head>
    <title>Result</title>
<body>
    <stripes:useActionBean var="ab" binding="/Calculator.action" />
    ${ab.result}
</body>
</html>
``` 

again that is a very simple example.   typically the names of the jsp & beans are done with annotations & constants (not hard coded).  and that is so simple ajax would be much better (there's an example of this on the site).  also it's good practice to keep your action beans very empty, all they should do is: fire an event, delegate all the business logic down to the service layer, handle any exceptions that made it up, and direct the user to another view.

if you decide to give it a shot, the mailing list is a great resource and i'll be happy to help with any questions you have.  i've worked with a lot of web frameworks and stripes is hands down the best in multiple ways.

---

### Post by pmasiar on 2007-01-19
> **se2schul said:**
> allow people to interface with it using a web browser.   (...)
My initial thought was HTML/Perl/CGI front end and a C backend.  I've been out of touch with web technologies for a while,

Yup, you are out of touch with web apps - CGI in perl is so .COM era :-) And you forgot to mention which languages to know/prefer. Each language has at least one web app framework now. 

Nowdays is era of rapid (agile) web frameworks. 

(1) **PHP **- if you like mess with mixed code and HTML tags (not recommended, but easy to dive into: thats why so many bad programmers use it :-)
(2) Ruby "invented" agile web frameworks with **Ruby on Rails** - if you liked Perl, Ruby might feel like slightly better perl.
(3) **Python **has two very popular frameworks, Django and TurboGears (and many less popular: Python has more frameworks than  reserved words. :-) ). If you liked dynamic typing but dislike perl quirky style, python might be good fit for you.
(4) If you are object-obsessed and enjoy strict type control needed for huge projects, **java **might be best fit. But you will be required to do everything in java way - Tomcat instead of Apache for web server, etc. Steep learning curve, and not as rapid and agile as dynamic languages.

If you want to check how easy is web app in python (no frameworks, plan CGI), check [this example]("http://ubuntuforums.org/showthread.php?t=332041")

---

### Post by lloyd mcclendon on 2007-01-19
> **pmasiar said:**
> thats why so many bad programmers use it :-)

true statement.  if you want to write web apps this way, coldfusion is worth a look as well.  it's just fine for simple projects.

> Steep learning curve, and not as rapid and agile as dynamic languages.

i agree, the learning curve is pretty intense.  quickness to market takes forever when you're first starting - you will be struggling to undertsand configuration & errors all the time.  but after you do a few projects, it all starts to make a great bit of sense.  and if you read a lot of articles by smart people & get a good foundation setup (hibernate, spring, code generation, etc), development gets very quick and the apps are a pleasure to maintain.

---

### Post by pmasiar on 2007-01-19
One more question: are you happy with old style apache CGI as in old perl days, or are you ready to learn whole new way to do web apps using tomcat and java. Correct me if i am wrong, but I am not aware of running Java web app under plain apache web server.

Comparing with simple CGI way of old times (get form params, print HTML output), java/tomcats adds many, many layers of abstractions which you need to handle and configure properly for your code to work. They might be usefull if your web app has 300 objects and 3000 screens, but not for a simple app :-)

---

### Post by johnnymac on 2007-01-19
It's so HAIR-LAIR-IOUS :lolflag: to hear people "bash" on XHTML|HTML + PHP and|or mixed JSP.  Use what is best for you....sometimes it's the quick and dirty with HTML+PHP, sometimes it may need to be a complicated OO-based system using Java...whatever.  Use what is most comfortable for you.  That's the beauty of programming...meld the technologies and make your own hodge-podge of stuff...just have fun!

I've never written Ruby, but I constantly write web-based applications and systems using Perl,CGI,XML-RCP,SOAP,PHP,HTML,JSP, and yes...even C.  They are tools...plain and simple - more you know and use fluently the better off you are (and the more money you make :))

---

### Post by se2schul on 2007-01-19
Thanks for the responses guys.

I'd prefer to stay away from java if possible. I haven't used it in several years, and given the amount of floating point math involved, I think it might be rather inefficient for the job compared to something like C.  I know C much better than java.

Would something like perl or python be able to be used create a front end and execute my C program then display the output?

---

### Post by pmasiar on 2007-01-19
> **se2schul said:**
> Would something like perl or python be able to be used create a front end and execute my C program then display the output?

Sure - Python is slowly replacing perl as "duck tape" for glueing together shell processes, and will be cleaner and easier to read. Try CGI example I mentioned in my first comment. To generate text output beyond standard string formatting, I highly recommend the simplest templating system out there: [htmltmpl.]("http://htmltmpl.sourceforge.net/easydoc.html")

---

### Post by se2schul on 2007-01-21
Thanks for the reply guys.
I think I'll try a Python/C solution first.

---

### Post by Note360 on 2007-01-21
You probably could do the whole thing from inside python or ruby. I know Ruby can manually change types.

---

### Post by runningwithscissors on 2007-01-21
Nothing beats Perl and PHP (even if old and ugly) for speed on scripted web applications. Writing CGI in C is just torture.

---

### Post by pmasiar on 2007-01-21
> **runningwithscissors said:**
> Nothing beats Perl and PHP (...) 
... maybe except Python or Ruby? :twisted:

---

### Post by runningwithscissors on 2007-01-21
> **pmasiar said:**
> ... maybe except Python or Ruby? :twisted:
Python, perhaps (I have heard about mod_python being a bit slow)
Ruby, No.
Everything smokes Ruby.
[Click to see Ruby pwned](http://shootout.alioth.debian.org/gp4/benchmark.php?test=all&lang=ruby&lang2=perl)
:wink:

---

### Post by Requiemx on 2007-02-09
As of now it would be HTML, although many people don't consider it programing language, because it really isn't, but if you learn HTML, learning the others will be easy.

This is my the order that I wish to learn in

1.HTML(CSS1, CSS2)
2.XHTML 
3.C+
4. Java script
5 everything else :p

---

