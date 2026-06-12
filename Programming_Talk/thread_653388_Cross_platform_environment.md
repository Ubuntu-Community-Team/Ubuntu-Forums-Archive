---
title: "Cross platform environment?"
date: 2007-12-29
forum: Programming Talk
---

### Post by kwandtke on 2007-12-29
I'm the admin in a Windows shop.  We've been looking at Linux more for some back end things.  I brought a guy in to build a mail server on Red Hat (needed that to get the whole thing past the boss since he could buy the server & OS from Dell and was comfortable that he could get support.  Since then I've installed Gutsy on a couple of our old servers. One I'm using mainly to run SPLUNK, piping all my Windows server events (via SNARE)  to it along with some other systems logs ... the other server we've built as a standrd LAMP ... and we're playing with building an intranet.  

One thing one of our programmers has heard about and would like to try is Ruby on Rails.  Well, I did a few quires and some time later had Ruby running on the server .. now the programmer .. who works in a Windows environment wants  an IDE of some sort.  Again, I looked around and found Aptana has RADRails whihc is suppose to be good.  Now the one thing that I'm not sure about is can I install that on his Win box and "point" it at the Linux box to let him do development?  The little I've looked at Aptana it seems like they expect it  (Ruby) to be running in a Win enviroment .... anybody had any experience with this or care to point me in the right direction?

---

### Post by jespdj on 2007-12-30
I don't know Aptana but [NetBeans 6.0]("http://http://www.netbeans.org/") has good support for Ruby and Rails. NetBeans is a cross-platform IDE written in Java.

---

### Post by slavik on 2007-12-30
you can setup ftp or a samba share on the linux box and have your programmer user that to put code onto the server.

aptana can use ftp for this.

---

