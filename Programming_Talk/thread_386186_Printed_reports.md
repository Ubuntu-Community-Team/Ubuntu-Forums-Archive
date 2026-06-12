---
title: "Printed reports"
date: 2007-03-16
forum: Programming Talk
---

### Post by Simon2006 on 2007-03-16
I have been using a ms access program / database as an accounting / record keeping system for a small company that I work for. I have been using Ubuntu exclusively at home for a while now and out of curiosity and principle I would like to develop an open source alternative. 

I would consider myself a competent, but not advanced, programmer and have pretty much settled on a python - sqlite solution. However I have 1 major problem in that I need to be able to produce presentable printed documents (invoices etc). In access this was easily done with the report designer. There seems to be no straightforward open source alternative. I have considered using css / html but I'm not sure. Does anybody have any suggestions and am I missing something blindingly obvious?

Any help / suggestions very gratefully received,

Thanks

Simon

---

### Post by phossal on 2007-03-17
If I were going to do such a thing, I would use Perl and MySql. You shouldn't necessarily, but you'll understand enough of what I say to make your things work in Python. 

Perl has the DBI, which allows it to connect to MySQL pretty easily. I can demonstrate a simple connection here:



```
# Database Connection
use DBI;
sub getConnect() {
	$dsn = 'DBI:mysql:dbname:localhost';
	$db_user_name = 'root';
	$db_password = '';
	$dbh = DBI->connect($dsn, $db_user_name, $db_password);
}
```


Perl allows for pretty simple interaction. I've never used it, but I assume Python has equivalent (or better) access to MySQL. 

As for reporting, Perl (and I assume Python) has a decent PDF module. It's not as easy to use as, say, Java's IText, but it's easy enough. If you're really going old-school, you can use Perl's (or Python's) formatting capabilities. For invoicing, I would stick with .pdf for all of the obvious reasons.

---

### Post by WW on 2007-03-17
Take a look at **reportlab**: [http://www.reportlab.org/](http://www.reportlab.org/)
You can install the package **python-reportlab** from the Ubuntu repositories.

I have never used the "report designer" in Access, so I don't know if reportlab is even close to that. (But I suspect that reportlab is a "lower level" system than the report designer, so it might not be what you are looking for.)

---

### Post by pmasiar on 2007-03-17
> **Simon2006 said:**
> I have been using a ms access program / database as an accounting / record keeping system for a small company that I work for. I have been using Ubuntu exclusively at home for a while now and out of curiosity and principle I would like to develop an open source alternative. 

Google suggested: in C: GnuCash  [http://www.gnucash.org/](http://www.gnucash.org/) 
In Python: Luca [http://www.epx.com.br/luca/](http://www.epx.com.br/luca/) - using TurboGears web framework, and [this email thread](http://www.thescripts.com/forum/thread31092.html)

TG uses very interesting templating system, KID. It uses valid XML, so you can view template source code using a browser (without any data).

If you are interested more in desktop accounting, I would suggest creating flexible front-end for GnuCash libraries in Python and wxPython. Including more flexible reports - with Python, you can generate formats on the fly.

---

### Post by Simon2006 on 2007-03-18
Thanks everybody for your advice - I really do appreciate you all taking your time to help. I think the pdf  / reportlab route is definitely the one to take - just what I was looking for.

Thanks again,

Simon

---

