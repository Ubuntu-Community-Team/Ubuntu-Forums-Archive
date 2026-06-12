---
title: "Jsp vs php vs asp.net"
date: 2006-09-28
forum: Programming Talk
---

### Post by Desi-Tek.com on 2006-09-28
what is the benefit of using j2ee over php or asp.net vice versa?

---

### Post by marianom on 2006-09-28
Benefit? In what context?
They all have their ups and downs. I think you have to choose considering the context in which you're going to use it: what's your goal, the expertise you have, do you need to interact with a lot of external services, etc.

I list what I think, IMHO:

1- Java harder to master than php or asp: on a learning stage, of course.
2- Php/Java: can be installed in any architecture. Asp generally locked in Windows (I know there's some projects out there that are actually changing this).
3- Java: heavily object oriented, Php: OOP is rather new. Asp: don't have a clue :D 
4- Sponsors behind java (sun) and asp (ms) bigger than the one behind php (zend). I think this count: asp is major player because ms is behind it. If you want a developer paid job it'll be easier with java/asp. Corporations tend to consider important the possible support they gonna get and heavy names are important when they're choosing technologies.
5- Documentation support: more support on asp.net / java than php. For me this is important. I tend to look a lot in the languages docs.

Finally, let me state that I love php (actually we sell a product developed with php-pl/sql).

 
That's what I can say for now, pretty sure there's a lot of people that will disagree with me. I will appreciate all reasonable criticism.

---

### Post by Desi-Tek.com on 2006-09-29
i mean what make any company to deside whether their site should be codded in jsp or asp or php? does jsp offer more security? i have seen many banking site codded in jsp. does java bean makes it more secure?

---

### Post by Desi-Tek.com on 2006-09-29
ah i think i found something
this is what i found in sun java hoe page
benefit of using jsp over php
[http://forum.java.sun.com/thread.jspa?threadID=721813&messageID=4185455](http://forum.java.sun.com/thread.jspa?threadID=721813&messageID=4185455)
benefit of jsp over asp
[http://java.sun.com/products/jsp/jsp-asp.html](http://java.sun.com/products/jsp/jsp-asp.html)
all in all sun has compared its product with microsoft asp in the basis of open source and multi plateform support which we can not achive on asp without using plugins available. but these plugins r still not 100% compatible asp.net

---

### Post by NoWhereMan on 2006-09-29
I think you can't really compare jsp and asp.net with php. jsp and asp.net are not only languages, they offer frameworks, facilities to help you developing a *complex* web application.

Actually php just gives you some tools, not a standardized framework, even if *there are* thrid-party frameworks such as php-cake or p4a.

I think the real choice is between asp.net, jsp and RubyOnRails.

BTW,if you only need a slightly interactive web site, php it's okay because of its diffusion... if you plan to do something more complex... then it's better something else.

You can use those frameworks for simpler stuff, though.

Rails it's the only free, asp.net and jsp (i'm not sure about this one) are not.

bye

**@desi-tek.com** [list]
[*]you posted raw html code :D
[*]asp != asp.net
[*]arrrrrgh! those font tags in that html!! ](*,) 
[/list]

---

### Post by Desi-Tek.com on 2006-09-29
oh but why they have compared jsp with asp? when asp is out dated and asp.net is currently in use? or they forget to mention dot net?

---

### Post by NoWhereMan on 2006-09-29
> **Desi-Tek.com said:**
> oh but why they have compared jsp with asp? when asp is out dated and asp.net is currently in use? or they forget to mention dot net?

old site, old pages, old web design :D

---

### Post by Desi-Tek.com on 2006-09-29
eh google should be blaimed for returning that link :)
Ah this time i found something interesting
[SIZE="4"] Microsoft .NET Vs JSP :)[/SIZE]
[http://www.remarc.co.uk/remarcnews/June05/netjsp.aspx](http://www.remarc.co.uk/remarcnews/June05/netjsp.aspx)

[SIZE="5"]JavaServer Faces and ASP.NET - A Side by Side Look[/SIZE]
By Michael Klaene
[http://www.developer.com/net/asp/article.php/3572721](http://www.developer.com/net/asp/article.php/3572721)

---

### Post by NoWhereMan on 2006-09-29
> **Desi-Tek.com said:**
> eh google should be blaimed for returning that link :)

sun should be blamed for such a page :D

---

### Post by marcomangiante on 2006-09-29
Hello,

> **NoWhereMan said:**
> 
Rails it's the only free, asp.net and jsp (i'm not sure about this one) are not.
[/list]

what is the meaning of free in your messagge? I know that you can download, free of charge, asp.net and jsp/jsf. Also, there is an open source implementation of asp.net (see mono: [http://www.mono-project.com/Main_Page)](http://www.mono-project.com/Main_Page)), and also for jsf (see myfaces: [http://myfaces.apache.org/)](http://myfaces.apache.org/)).

--
Regards,

Marco Mangiante

---

### Post by NoWhereMan on 2006-09-29
> **marcomangiante said:**
> Hello,



what is the meaning of free in your messagge? I know that you can download, free of charge, asp.net and jsp/jsf. Also, there is an open source implementation of asp.net (see mono: [http://www.mono-project.com/Main_Page)](http://www.mono-project.com/Main_Page)), and also for jsf (see myfaces: [http://myfaces.apache.org/)](http://myfaces.apache.org/)).


well i meant both free as in beer and libre.
i forgot of the oss implementations, but... you know, i think "native freedom" is better :p

btw, i dislike .net in general (and the .exes and .dlls on my linux system... :D)

---

### Post by Desi-Tek.com on 2006-09-29
@NoWhereMan wats wrong in using microsoft's product?:confused:

---

### Post by marcomangiante on 2006-09-30
Hello,

the problem is that .net is not completely supported under linux, because under this os the framework is not microsft directly written; microsoft created a shared source version of the .net framework, but it lacks the virtual machine and if I remember well the c# compiler code, that are central to the framework. In general, the mono implementation seems to be quite compatible: however, it is more simple to resemble the asp.net behavior rather than the typical windows desktop programming, and maybe it is more simple that you can do at this time asp.net programming then desktop programming (this under linux).

--
Regards,

Marco Mangiante

---

### Post by NoWhereMan on 2006-09-30
> **Desi-Tek.com said:**
> @NoWhereMan wats wrong in using microsoft's product?:confused:

a matter of point of views ;)

---

### Post by JGuru on 2006-09-30
**Mono** is not Microsoft's implementation.It's developed by Novell.
 If you want a cross-platform scripting language then choose **JSP** or
 **PHP**.In **JSP** you need to learn lot of things, **PHP** is
 more simpler. You can choose either one according to your own liking!!

---

### Post by marcomangiante on 2006-09-30
Hello,

first, I prefer jsf (javaserver faces); you can compare jsp with asp, and jsf to asp.net. Asp.net and jsf are part of frameworks (.NET for asp.net and J2EE for jsf), while php is "only" a language. It is true that php has a simple learning curve respect to jsf/jsp and also asp.net, but in this case you must compare php with c#, vb.net or java. 
I think that asp.net is very interesting, but at this time maybe the support under linux is worse then the j2ee framework.
Another aspect of compare jsf and asp.net is that the first has, for my knowledge, 2 IDEs that have a visual designer (Sun Java Studio Creator and Oracle Jdeveloper), while the latter has 2 IDEs with visual designers (Microsoft Visual Studio 2005 and Microsoft Visual Studio Express Edition 2005), but these work only under windows. I prefer IDEs with visual designers and think that they are very important.
Now, it is your choose.

--
Regards,

Marco Mangiante

---

### Post by Desi-Tek.com on 2006-09-30
thanx every body for sharing information with me :)
@marcomangiant i was aware about jsp but this is the 2nd time i heard about jsf. i came to know about it last night when i was reading  article on ("JavaServer Faces and ASP.NET - A Side by Side Look"). can u give some more information on jsf? whats new in it? i am currently learning jsp. is it going to be helpful to learn jsf? and when jsf was first released?

---

### Post by Freddd on 2006-09-30
J2EE all the way, it's so powerful, and you can create very scalable applications easily!
I don't know why you discuss it as JSP, because JSP is only the presentation layer of J2EE.

---

### Post by Desi-Tek.com on 2006-09-30
@Freddd   oh thanx for quoting but i am not able to edit topic :(

---

### Post by marcomangiante on 2006-10-01
Hello,

jsf (javaserver faces) is now the presentation layer of J2ee platform. They created it because jsp have major problems with maintenance (not only for this problem): infact, every jsp page is a mix of html and java, and if you see the code is not very readable. Jsf have this good thing, like asp.net do, to divide the html code (that regards the presentation in the browser) from the, say, page logic code (backing bean classes). Another advantage regard the event-driven and component driven architecture of jsf. However, for a more complete explanation of these characteristics, go to the sun reference site for jsf:

[http://java.sun.com/javaee/javaserverfaces/]("http://java.sun.com/javaee/javaserverfaces/")

My suggestion is to use jsf, because I think it becomes in short time the standard presentation layer for java web programming (it have support from sun, oracle, ibm, etc..), and you also have the assistance of good visual designers, that are also free of charge, so you can do, without problems, your experimentation.

--
Regards,

Marco Mangiante

---

### Post by pmasiar on 2008-05-20
jsp, php, asp, blah blah. All options are equally bad. Real men use [Google App Engine](http://ubuntuforums.org/showthread.php?t=749285) :-)

Seriously, why limit to server-pages way of developing? [http://en.wikipedia.org/wiki/Model-view-controller](http://en.wikipedia.org/wiki/Model-view-controller) pattern is much more manageable, and there are excellent frameworks for that, like Python's Django and Turbogears, Ruby on Rails, even Java with Spring or Struts is better than the inevitable mess you will create with XSP.

---

### Post by LaRoza on 2008-05-20
I wonder why this thread was necromanced? Was it returned by a search?

---

### Post by pmasiar on 2008-05-20
I don't know. Somehow I stumbled on it. I usually check post for last hour and answer the relevant ones, I have no recollection about this one :confused: Looks like my reply was first this year, but I would not go and search for it. Maybe it was linked from the most recent Web dev FAQ?

---

