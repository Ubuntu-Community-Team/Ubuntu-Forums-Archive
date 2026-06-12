---
title: "Where to begin for learning webapps?"
date: 2012-07-27
forum: Programming Talk
---

### Post by IncurableHam on 2012-07-27
So I would like to learn how to develop webapps while learning C# or Java at the same time. Where would you begin to do this? I have absolutely no idea where to start, so I'm looking for the basics. I'm not sure where to even write the code in because most tutorials that I found are from Microsoft and therefore require VisualStudio, Silverlight, WebMatrix, etc. which are Windows-exclusive. Should I just reinstall Windows or is there a simple way of developing webapps using an IDE/webapp developer that is available in Ubuntu? I've downloaded MonoDevelop but most tutorials that I found teach through using VS drag/drop GUI interface.

---

### Post by mevun on 2012-07-27
> **IncurableHam said:**
> So I would like to learn how to develop webapps while learning C# or Java at the same time. 

Any particular reason for these two languages?  I'm guessing you might want a job and these are very popular languages.  Anyway, I am not familiar with C# except knowing that it is related to Microsoft.  With Java, there are multiple choices of server stacks according to this wiki page:
[http://en.wikipedia.org/wiki/Application_server](http://en.wikipedia.org/wiki/Application_server)

For some reason, it does not list Tomcat, but that was the web server I used at my previous job.

> Where would you begin to do this? I have absolutely no idea where to start, so I'm looking for the basics. I'm not sure where to even write the code in because most tutorials that I found are from Microsoft and therefore require VisualStudio, Silverlight, WebMatrix, etc. which are Windows-exclusive. Should I just reinstall Windows or is there a simple way of developing webapps using an IDE/webapp developer that is available in Ubuntu? I've downloaded MonoDevelop but most tutorials that I found teach through using VS drag/drop GUI interface.If you search for "java servlet tutorial", then that will provide some info for using java which should be suitable for linux.

If you are open to other languages, then you could look at Ruby-on-Rails, python django, or PHP-based systems like drupal, wordpress, and joomla.  All of these work on linux.  Basically, you have lots of language choices for writing server code.

---

### Post by IncurableHam on 2012-07-27
Thanks for the info mevun. I want to learn C# and Java because those are the two languages that I am familiar with right now, but want to learn more of (well not C#, but I know vb.net and C# just seems to be more widely used and is very similar).

I am definitely open to learning other languages and Python seems to come up a lot when talking about languages associated with Linux. Why is Python so popular with linux users?

---

### Post by Hetepeperfan on 2012-07-27
> **IncurableHam said:**
> Thanks for the info mevun. I want to learn C# and Java because those are the two languages that I am familiar with right now, but want to learn more of (well not C#, but I know vb.net and C# just seems to be more widely used and is very similar).

I am definitely open to learning other languages and Python seems to come up a lot when talking about languages associated with Linux. Why is Python so popular with linux users?


Python is quite easy to learn, it works as far as I know on all major platforms. And like Java and csharp, it comes with the batteries included. That is, with a few lines of code one can accomplish quite a bit, because the batteries (libraries) will do a lot of work for you. Sometimes you would have to download a new library, django for example is a pythonic frame work that allows one to build beautiful and safe websites. However python has quite a few network libries that come with a standard python installation.
disclaimer: I don't do web programming myself, but some of my colleagues are very fond of a python django combination for web programming.

kind regards,

Maarten

---

### Post by mevun on 2012-07-27
Okay, now that I have an understanding of your background (I think), you can think of web server development as requiring at least 2 pieces.  One is the web server software itself which understands the HTTP protocol, can parse URLs, etc.  The other piece is the your own application's functionality you want that server to execute when it receives various HTTP requests.  These two pieces are paired such that certain server software can only process your code written in certain languages.  There is a third piece which is the client-side code, but so far today it's almost all written in javascript.

Since you already know Java, you would be correct in thinking that you just have to download a web server software which will pair with Java code.  Tomcat is one, but I think there other (possibly better) open-source options.  You still have to learn how to configure the server software and how to 'package' your application software to add that functionality.  For Java, that means you still compile into class files and package into jar files, but you need an extra step to make "war" (web application r???) files for tomcat deployment.

Now, if you pick a different language to learn, the packaging steps are different and possibly 'faster' if they are dynamic languages.  They may not need the compilation step and some frameworks may let you just modify the program you wrote on the file system for a change.

The other big consideration are the choice(s) and ease of working with functionality you want for your application.  Some frameworks interface well with databases.  Another language might have better library support for numeric processing, etc.  So you might pick a framework/language based on the actual app functionality you need.  In other words, learning a new language is usually going to be faster than writing your own XXXX library.

Although the Apache web server software is often used as part of these frameworks, I would not recommend using the language "modules" that come with it unless you're more interested in how it all works together.  They have names like "mod_perl", "mod_python", "mod_php5".  They may form the lower layer of a web framework, but if you use them directly then you could be writing a LOT of code if you develop any sort of sophisticated application.

Since my own semi-recent experience is limited to just apache/mod_python and tomcat/java, I can't make any recommendations.  I doubt that Tomcat is the popular choice today.

---

### Post by Some Penguin on 2012-07-28
For Java:

* [Jersey/JAX-RS]("http://jersey.java.net/nonav/documentation/latest/user-guide.html"), for making it *easy* to write endpoints with far fewer warts than WARs

*[Jetty]("http://jetty.codehaus.org/jetty/"), for an easily embedded web server

* and a good dependency-injection framework like [Guice]("http://code.google.com/p/google-guice/").

---

### Post by llanitedave on 2012-07-28
I would think that for a web app, the first thing to learn is the application and interface design process.  Once you know that, the language for the backend is less of a consideration.

Familiarize yourself with html, css, and javascript.  That's really the hard part.

---

### Post by slavik on 2012-07-28
Tomcat is not a full J2EE container, since it can't deploy EAR files. It is a web container. JBoss is a full J2EE container.

---

### Post by Some Penguin on 2012-07-28
> **llanitedave said:**
> I would think that for a web app, the first thing to learn is the application and interface design process.  Once you know that, the language for the backend is less of a consideration.

Familiarize yourself with html, css, and javascript.  That's really the hard part.

The language isn't a massive consideration, but for many applications, the backend *is* the hard part.

People who can do a reasonable job on a web GUI using e.g. PHP are a dime-a-dozen, pretty much.  It won't necessarily be awesomely beautiful, but there are a LOT of people who can do this reasonably well.

People who can do a reasonable job designing a system where you can readily add or remove nodes on the fly (to manage variable capacity requirements), handle high traffic without an excessive number of aborts and rollbacks,  provide a reliable and available system with eventual consistency, and also wire in good monitoring so you can see exactly why requests are performing as they do -- those are much rarer.

Hell, major companies still have difficulty finding people who aren't complete morons who store passwords without one-way-hashing them, or who build SQL queries by directly concatenating user-supplied input w/o using any of the gazillion available safe-escape mechanisms... and both of these are well-understood and well-addressed problems with more than adequate solutions for multiple decades.

---

