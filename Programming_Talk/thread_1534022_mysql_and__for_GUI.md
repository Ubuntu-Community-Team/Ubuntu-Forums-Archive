---
title: "mysql and ? for GUI"
date: 2010-07-18
forum: Programming Talk
---

### Post by suri.mahendra on 2010-07-18
I work as a HVAC/R service tech and am getting my BS in database admin.  What I want to do is create a database for work orders, bids and what ever else I think of (or what my boss needs)

I have the basics of MySQL down.  I need a direction to go with a language that can build a GUI and has a DBI at no charge (PERL charges a fee for commercial use).  I'm looking at both Python and TCL/Tk to build a GUI.

Any advice/tutorials/books would be greatly appreciated.

Mendi

---

### Post by ju2wheels on 2010-07-18
Perl is a language licensed under GPL/Artistic License, and you dont have to pay for its commercial use. Perl DBI is open sourced under the GPL and you do not need to pay for it for commercial use either (but they do charge if you want commercial support, otherwise you can do the research yourself online and in forums).

---

### Post by soltanis on 2010-07-19
Echoing above, I'm pretty sure Perl does not have any fees for commercial usage of either the DBI or the language itself. You can create a native interface using Python/Perl + GTK + MySQL for the backend, but I suggest you write a web-based application instead using CGI/Perl or PHP as your language. The reason I suggest this is because it doesn't sound like you'll be needing GTK-specific features (tighter integration with the desktop is really the only benefit), because writing HTML/CSS is easier for rapidly creating decent interfaces, and because your application will then not be Linux-specific.

---

### Post by mcphargus on 2010-07-19
This sounds a like a great use-case for Django. Since you're familiar with Python and Django can be connected to a MySQL database and there's never been a better time to learn about Object Relational Mappers, give [http://www.djangoproject.com]("http://www.djangoproject.com/") a shot.

You can host django projects on Google's Appengine for free, or run django on your own private server. Django comes with a simple app-server built in or you can connect it to apache with mod-python.

IIRC, there's no charge for commercial use of Django.

---

