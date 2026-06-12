---
title: "netbeans and mysql connector"
date: 2009-09-27
forum: Packaging and Compiling Programs
---

### Post by shahin on 2009-09-27
Greetings-
  I am trying to write a short JAVA program that connects to the mysql db on my workstation.  Looking at:

[http://www.netbeans.org/kb/55/using-netbeans/dbconn.html#pgfId-1156774](http://www.netbeans.org/kb/55/using-netbeans/dbconn.html#pgfId-1156774)

Above link talks about Darby and Pointbase but I do not see either of them in the netbeans version I have.  I doewnloaded the packaged version using synaptic.  I also do not see any of the options that above document talks about. Should I be using a different version of Netbeans? I have version 6.5.  

The code I am trying to use is at 

[http://www.kitebird.com/articles/jdbc.html](http://www.kitebird.com/articles/jdbc.html)

And it compiles fine.  I have also followed the instructions at:

[http://www.cs.wcupa.edu/rkline/mysql-java-win.html](http://www.cs.wcupa.edu/rkline/mysql-java-win.html)

And added the mysql connector to my compiler libraries.  The code above runs, but it stops at the class.forName ... line, and throws and exception.  

Any help please?

---

### Post by dinxter on 2009-09-28
i dont use netbeans myself so i doubt i can help in any detail, just to mention that the netbeans guide you mention is for 5.5, not 6.5, hence the missing options no doubt. a more up to date guide to netbeans and databases is below and hopefully should cover all your looking for
[http://www.netbeans.org/kb/65/java/gui-db.html](http://www.netbeans.org/kb/65/java/gui-db.html)

---

### Post by shahin on 2009-09-28
I appreciate that.  I reviewed the document you sent.  It says I should see an option for DB in the services window.  But I do not.  I also looked at the help section of the compiler.  However, the modules that are supposed to talk about how to connect to the DB are missing; it states to refer to the web site.  Something tells me the version I have does no support DB?  Do you think I need to install a different version of Netbeans?

---

### Post by dinxter on 2009-09-28
might seem like a silly question but, when you go to tools->plugins is the 'Database' plugin installed and updated if necessary? if it is and its not working i can say for sure that the database plugin on version 6.7.1 works fine.

---

### Post by shahin on 2009-10-04
It is a great question. After looking around a little, what I was missing was the driver under the tools>pluggins section as you indicated.  The code works:-) btw, I used eclips in the windows environment also, and that worked also.  But I really wanted to get this working.  Thanks for all your help.

---

