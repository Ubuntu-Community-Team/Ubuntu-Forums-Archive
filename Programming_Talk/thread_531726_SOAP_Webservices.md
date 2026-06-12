---
title: "SOAP Webservices"
date: 2007-08-21
forum: Programming Talk
---

### Post by delphiguy on 2007-08-21
Cheers,

What is the best programming language to use when I creating a SOAP
Webservice and also easy to learn, I have zero experience programming 
in Linux, but I need to accomplish this within a month.

This Webservice will be consumed by a Windows Application.

Thanks.

---

### Post by pmasiar on 2007-08-21
Your life would be easier if same system created and consumed data - so you don't have to solve inevitabe incompatibility quirks.

BTW with zero experience and month time, it's time to start looking for a new job - you are set up for a failure. 

What is your experience in Windows? Can you get same system in Linux?

---

### Post by delphiguy on 2007-08-21
Cheers,

We'll I have this client that has a software that needs to communicate with the Ubuntu Server that I have setup for them.

Their programmers have written their application in VB Classic (I know
what a pity).  I have already made them a proposal to change the 
dev tool into something else.

They require that the application can communicate with the server
so that they could get the information stored in the database (mysql). The approach that they're programmers did is that they 
made a direct connection to the Database, so what I have suggested
it to make a SOAP web service to be consumed by their application.

I have 12+ years of programming experience in Windows, primarily 
Delphi, and I have made a couple of SOAP Webservices myself, but I 
haven't really taught myself of programming in Linux, I wanted to, 
but its always difficult for me to find the time.

This SOAP Webservice will be simple, just to check whether the 
Username/Password combo is valid and check that to the server and a simple database search.  

And since they already have a Linux server, I wanted to use the 
resources that they have at the moment.

Thanks.

---

### Post by aitorcalero on 2007-08-22
With no experience in Linux programming I would suggest to use Java, cross-platform language, and there are a lot of tools available to develop SOAP services (Eclipse, NetBeans, JDeveloper...)
With SOAP or Webservices, don't need to worry about the client platform (that's the point) you only need to deal with XML, which is platform independent.
By the way, there are delphi tools available for Linux it is known as [Kylix]("http://delphi.about.com/od/kylix/Kylix_Delphi_for_Linux.htm")
Good luck ;)

---

### Post by delphiguy on 2007-08-22
I am aware of kylix and of lazarus, I just want to explore more on this, and also since I haven't
tried programming in Linux then I thought that I maybe should try something that is more of a
standard programming language in linux.

Java is one of my choices, along with PHP. So i guess I'd have to make a choise between to 
2 then.  Can anyone here point me to some resources in SOAP/Webservice development 
using Java/PHP??

thanks.

---

