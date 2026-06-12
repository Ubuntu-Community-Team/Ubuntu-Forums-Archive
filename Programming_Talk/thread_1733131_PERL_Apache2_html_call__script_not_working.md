---
title: "PERL Apache2 html call  script? not working?"
date: 2011-04-18
forum: Programming Talk
---

### Post by highspider on 2011-04-18
Apache2 runs perl scripts fine but I can't call them inside a .htm

example that works 
[COLOR=Lime][mysite.com/cgi-bin/clock.cgi]("http://www.mysite.com/cgi-bin/clock.cgi")[/COLOR]```

Monday April 18, 2011 - 19:10:55 PM PDT 

```example that doesn't work
[COLOR=Lime][mysite.com/time.htm]("http://www.mysite.com/time.htm")[/COLOR]
```
test script
try 1 
try 2 
try 3 

```how I called the clock code inside time.htm
```

<html><body><h1>test script</h1>
try 1 <br />
<!-- #exec cgi="/cgi-bin/clock.cgi" -->
try 2 <br />
<!-- #exec cgi="clock.cgi"-->
try 3 <br />
<!-- #exec cgi="/var/www/cgi-bin/clock.cgi"-->
</body></html>

```

---

### Post by wojox on 2011-04-18
Try using the full path like your first example.

---

### Post by highspider on 2011-04-18
I tried with full link and 
```
<html><body>
try full link 1 <br />
<!-- #exec cgi="http://www.MYSITE.com/cgi-bin/clock.cgi" -->
try full link 2 <br />
<!-- #exec cgi="www.MYSITE.com/cgi-bin/clock.cgi"-->
try full link 3 <br />
<!-- #exec cgi="MYSITE.com/cgi-bin/clock.cgi"-->
</body></html>
```returns```

try full link 1 
 try full link 2 
 try full link 3 

```

still now display

---

### Post by wojox on 2011-04-18
Oh I see. Perl. Did you set an AddHandler Directive in Apache2:

```
AddHandler cgi-script .cgi
```

---

### Post by highspider on 2011-04-18
IDK where does that go in
/etc/apache2/sites-available/default

---

### Post by wojox on 2011-04-18
> **highspider said:**
> IDK where does that go in
/etc/apache2/sites-available/default

You can add it to httpd.conf or apache2.conf. Then restart Apache.

---

### Post by highspider on 2011-04-18
> **wojox said:**
> You can add it to httpd.conf or apache2.conf. Then restart Apache.
I tried both, just one, the other one, and even a temp dir 
  [http://httpd.apache.org/docs/2.0/howto/cgi.html](http://httpd.apache.org/docs/2.0/howto/cgi.html)

<Directory /var/www/cgi-bin/perl>
               Options +ExecCGI
        AddHandler cgi-script .cgi
             </Directory>       

one at time with restart
 
it still don't work ?

---

### Post by highspider on 2011-04-18
[COLOR=Red]EDITED[/COLOR]

It does work inside An Iframe though 
```

<html>
<body>
<h1>test script</h1>
try full link 1 <br />
<!-- #exec cgi="/cgi-bin/hello.cgi" -->
try two <a href="/cgi-bin/hello.cgi">click me</a> <br />
test 3 I frame <br />
<iframe
src ="/cgi-bin/hello.cgi"
width="80%">
</iframe>
</body>
</html>

```the result is 
```

try full link 1 
   [COLOR=Red]EDITED REMOVED for security REASONS[/COLOR]
test 3 I frame 
|----------------|
|Hello, World!  |
------------------

```

---

### Post by shawnhcorey on 2011-04-19
What you're trying to do is called a Server-Side Include (SSI).  Try the OS path in it:

```
<!--#exec cgi="/usr/bin/ls" -->
```

See [Apache Tutorial: Introduction to Server Side Includes]("http://httpd.apache.org/docs/current/howto/ssi.html")

---

### Post by wojox on 2011-04-20
[Try this one line in httpd.conf]("http://httpd.apache.org/docs/2.0/mod/mod_mime.html#addhandler")

---

### Post by highspider on 2011-04-21
[COLOR=Blue]/etc/apache2/httpd.conf[/COLOR]
```

###################################################################
# This is here for backwards compatability reasons and to support
#  installing 3rd party modules directly via apxs2, rather than
#  through the /etc/apache2/mods-{available,enabled} mechanism.
#[COLOR=Red]
LoadModule include_module /usr/lib/apache2/modules/mod_include.so[/COLOR]

```my file is a .htm and I don't want to rename it to a .shtml
[COLOR=Blue]/etc/apache2/sites-available/default[/COLOR]
```

  <Directory /var/www/[COLOR=SeaGreen]gallery[/COLOR]>
          Options MultiViews +Includes
          AllowOverride None
          Order allow,deny
          allow from all
          [COLOR=Red]AddType text/html .htm
          AddOutputFilter INCLUDES .htm
[/COLOR]       </Directory>

```NOTE: ../ of exec to step back from gallery to /var/www/cgi-bin/hello.cgi
[COLOR=Blue]/var/www/gallery/test.htm[/COLOR]
```

<html>
<head><title>SSI Test Page</title></head>
<body>
<!--#echo var="DATE_LOCAL" -->
<br />
 
<!--#exec cgi="[COLOR=Red]../[/COLOR]cgi-bin/hello.cgi" -->
<br />
<!--#include virtual="/cgi-bin/hello.cgi" -->

</body></html>
```<!-- the page display -->
Thursday, 20-Apr-2012 04:20:00 PDT 
Hello, World.
Hello, World.   
<!-- end the page display -->

so the unsafe "#exec cgi= works 
and the virtual /var/www/ base root  protected "#include virtual=" also works

---

