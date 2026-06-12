---
title: "PHP n00b (a couple of questions)"
date: 2009-01-01
forum: Programming Talk
---

### Post by thefiestysoldier on 2009-01-01
I am a noobish php programmer, I have read a couple of books but they dont cover the google apis (which I would like to use) I keep hearing Zend and things like that but the descriptions on the internet are too hard to understand (for me anyways) from what I understand about the zend framework it appears to be quite useful but I dont know how to use it. I have been using the Geany IDE so far but I also hear about Eclipse PDT often (its an IDE right?)anyway heres the main questions:

[LIST=1]
[*]How do I set up my server to use the google api libraries for my scripts?
[*]What can I do with the Zend framework (what exactly is it?)
[*]How do I install the Zend framework on my server?
[*]How do i install Eclipse PDT
[*]Also, I have heard you can program GTK/QT/CLI apps with PHP, is it really worth it/ useful?
[/LIST]


Any responses are greatly appreciated, Thanks

---

### Post by ghostdog74 on 2009-01-01
How much of PHP fundamentals do you know? I would suggest you study and practice thoroughly the basics of PHP before embarking on advanced topics.

---

### Post by LinuxRocks713 on 2009-01-23
> **thefiestysoldier said:**
> Also, I have heard you can program GTK/QT/CLI apps with PHP, is it really worth it/ useful?

For PHP CLI and GTK apps you can use PHP-GTK2 ([http://gtk.php.net/](http://gtk.php.net/)). If you are planning on making an .exe file out of it, here's an useful guide:

[http://www.compdigitec.com/labs/2008/07/20/compiling-php-gtk2-apps-into-win32-executables/](http://www.compdigitec.com/labs/2008/07/20/compiling-php-gtk2-apps-into-win32-executables/)

---

### Post by drumz on 2009-01-23
Answering question number 4:

At work we used the commercial PHP IDE that the Zend company has, and it worked really, really well.  Then they switched it from a completely custom program to one based off of Eclipse (PDT is the open source free version lacking a few features) which we found to be slightly buggy (but has improved) so we decided to just switch over to using Eclipse + the PDT PHP plug-in.

If you're a newbie to programming in general, although IDE's are great, the learning curve on using Eclipse + PDT, plus just getting it installed can be a bit of a bear.  I'd recommend tinkering with PHP for a bit and getting your feet wet with that before trying to tackle Eclipse + PDT.  We've had a couple of corruptions of our install so we've had to re-do the install a couple of times but this MAY be because we use other plugins with Eclipse beyond just PDT AND on a 64bit platform- we have C/C++, Python, Perl and the PHP plug-ins installed.  Lately though the auto updates have been working fine.

This link [http://www.eclipse.org/pdt/downloads/](http://www.eclipse.org/pdt/downloads/) has a complete package (Eclipse + PDT) that you can download for various platforms.  So if you're really interested in it this is probably the easiest route to go.

Over all our experience using Eclipse + PDT has been very favorable.  The only thing that Zend offers over PDT was the ability to use a local copy of a code file automatically in the debugger instead of the one installed on the web server.  For you this probably won't matter, but in a multi-developer outfit it means each user now ends up with their own complete development space on the webserver instead of being able to share.....but it's free, stable, and the benefit of the debugger on larger projects is worth it and these days disk space is cheap.

---

