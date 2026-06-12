---
title: "Python programming"
date: 2006-12-21
forum: Programming Talk
---

### Post by rogier.de.groot on 2006-12-21
I have an ubuntu edgy server set up with apache2 & mod-python. I also have ubuntu edgy desktop machine. I was wondering what packages to install on both for developing simple webapps with mysql and which editor/IDE to use on the desktop. Since there's so much to choose from I could use some guidance on this. I was thinking of using bluefish for editing, but otherwise I'm stumbling around in the dark.

TIA,
Rogier

---

### Post by gh0st on 2006-12-21
Hi, I started a thread to find the best free Python IDE last week and most of the feedback I got suggested SPE. I haven't had a chance to try it yet but I was advised that you can install it from Synaptic. That might be the blind leading the blind a bit though :-) Give it a try.

Some purists say you should only use gedit but I'm not sure about that. Here's the thread address.

[http://www.ubuntuforums.org/showthread.php?t=320917](http://www.ubuntuforums.org/showthread.php?t=320917)

Can't help with what server packages to install though sorry. I'm sure some else will sort you out. If you wanna develop webapps in Python you should look at either Django or Turbogears as a platfrom. Thats another thing I've recently learned :-)

[http://www.djangoproject.com/](http://www.djangoproject.com/)

[http://www.turbogears.org/](http://www.turbogears.org/)

Again I haven't tried them yet but Django looks like an really nice web development platform with Python. Hope that helps.

---

### Post by pmasiar on 2006-12-21
> **gh0st said:**
>  SPE. ... you can install it from Synaptic. ... Some purists say you should only use gedit but ....

If you wanna develop webapps in Python you should look at either Django or Turbogears as a platfrom. 

I am one of the guys who prefers SPE. Not only because it is easy to install and you can use it also on  Mac and Win. I really like 
[LIST]
[*]indentation guides (specially important for Python), 
[*]I prefer to set strings to have background color - so you can see string literals, like hash keys, easy
[*]line goes purple if you don't close your string correctly (like opening with single and closing with double quote). In other editors, it is hard to see error: closing quote is of a string color 
[*]you can set comments to have background color - so its easy to see code you commented out (very light brown for me) instead of italics, which is hard to read on monitors
[*]I love the sidebar code outline mode - Explore. One line per function definitions, plus special comments: ##--- for permanent bookmarks, ##TODO, ##FIXME. It is MUCH easier to move around in your code using smart sidebar
[/LIST]
heck, I should post this to the other thread - about selecting the IDE.

I have no problem with gedit and use it daily. But: gedit is editor optimized to edit plain text. Python has additional structure which gedit is ignorant about. Arguments about learning syntax "the hard way" is bogus - maybe good for C++, if you are into BDSM and enjoy the pain :-)  but not valid for python.

The only thing SPE is missing is printing. I print from gedit :-)

If you want to learn basic CGI applications, you may want to skip all frameworks learning curve. You have all modules installed: 
[LIST]
[*]cgi for basic simple CGI without much inslallation: just get apache and setup some your subdirectory as cgi-enabled (apache ScriptAlias command)
[*]excellent cgitb - CGI traceback - which will give you similar traceback as python shell does in case of error/exception, great help for debugging
[*]sqlite - in python 2.5, or just install it if you need it. It is for simple database access with plain library (no need to administer a server if only single program will access it). But it is SQL, and you can scale it up to MySQL when need arises.
[*]simplest templating system [htmltmpl]("http://htmltmpl.sourceforge.net/python.html") which will also force you to use [Model-view-controller]("http://en.wikipedia.org/wiki/Model-view-controller") approach. MVC is good: it removes all computation from presentation layer.
[/LIST]

IMHO you may start with simple approach, later you will have other problems, and framework can help you to better organize your big complex systems. But good frameworks are MVC, and use templates, so you will have good habits formed, without inevitable learning curve on any framework. You will appreciate help from framework when you will know the problems it helps you to solve - but before that - framework might feel like a distraction.

It you are looking for some simple training tasks to solve, I started a wiki for python learners with some simple tasks: [http://learnpydia.pbwiki.com/](http://learnpydia.pbwiki.com/)

---

### Post by ohgod on 2006-12-21
I'm sure this has been said way too many times, but I'd recommend vim or emacs for editing.  I'm an emacs user myself, but I hear vim is quite good as well.

I read somewhere (in "The Pragmatic Programmer" I believe), that it's a good policy to pick a powerful text editor and then use it for *everything*.  That way you can learn to exploit all the powerful features of the editor, and you don't have to remember different commands for different programs.  I've found that to be very good advice.

BTW, if you decide to give emacs a try, you'll want to install the python_mode package from apt.

---

### Post by rogier.de.groot on 2006-12-21
Thanks y'all. I have a few follow up questions:
1) I have mod-python on apache2 - which means I don't need CGI, right? And thus by extension no CGI-trace-thingy? I've already tested mod-python, and it works with a simple "Hello world" type script.
2) I have sqlite installed, at least I assume apt-get installed when it installed php-sqlite & php-sqlite3 support. Ditto for mysql 5.0. But which package / module / library for accessing them (I have this impression that there are in fact multiple packages for working with these databases in python, like there are in PHP, but am confused as to which I should use).

BTW, I have never believed in doing things the hard way either, especially when it comes to the bucketloads of XML required to get J2EE working. I let NetBeans do that for me. When it comes to Java NetBeans kicks ***. Wish it had a python plugin (or a PHP one for that matter).

---

### Post by pmasiar on 2006-12-21
> **rogier.de.groot said:**
> 1) I have mod-python on apache2 - which means I don't need CGI, right? And thus by extension no CGI-trace-thingy? I've already tested mod-python, and it works with a simple "Hello world" type script.


cgi was quite enough for our dozen-hits-per-hour research websites, so I cannot compare with mod_python. but cgitb is GOOD. When you have error, like uncaught exception, it will give you nice webpage with trace - like shell. Without it, you have to look in logs. Or is there another trick? Always willing to learn how to simplify my life.

>  2) I have sqlite installed, at least I assume apt-get installed when it installed php-sqlite & php-sqlite3 support. Ditto for mysql 5.0. But which package / module / library for accessing them (I have this impression that there are in fact multiple packages for working with these databases in python, like there are in PHP, but am confused as to which I should use)..

**of course** there are multiple packages. Special one for every database. Google says "python + sqlite ==> pysqlite". Type "import pysqlite" in python shell to see if it is installed.

BTW isn't it great how easy is to check if your python can find a library?

---

