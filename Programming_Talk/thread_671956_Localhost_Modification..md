---
title: "Localhost Modification."
date: 2008-01-19
forum: Programming Talk
---

### Post by Kadrus on 2008-01-19
Hello,this might be the wrong place to post this,and this might look odd..but is there a way to change the look of [http://localhost/](http://localhost/) ?
I tried gksudo gedit [http://localhost/](http://localhost/) but not able to save it..
I want to change the background color and design..so it can be more attractive:p
Any help will be appreciated..:)

---

### Post by aks44 on 2008-01-19
Apache files are located in /var/www/ unless you changed that (which I doubt, since you probably wouldn't be asking that question then).

---

### Post by Kadrus on 2008-01-19
> **aks44 said:**
> Apache files are located in /var/www/ unless you changed that (which I doubt, since you probably wouldn't be asking that question then).

I know that they are located in /var/www/..but the question is am I able to change the look of the page when I type in my browser [http://localhost](http://localhost) ?
I see my files
Phpmyadmin
Forums
Php
etc...and
Apache/2.2.3 (Ubuntu) PHP/5.2.1 Server at localhost Port 80
..
I was wondering if I could change the color of the background..
But that  is not a problem..so never mind..
--
Edit
--
The reason I am asking this is because I saw it a site/Ocaml
[http://caml.inria.fr/pub/old_caml_site/Examples/oc/](http://caml.inria.fr/pub/old_caml_site/Examples/oc/)

---

### Post by aks44 on 2008-01-19
Hmm if I understand you correctly, the page displayed when you go to [http://localhost/](http://localhost/) is generated on the fly by Apache's **autoindex** module.

I'm not aware of any way to easily change its appearance, unless you modify and recompile the autoindex module (I may be wrong though).

As a wild guess I'd say the caml page you mention is just a "normal" dynamic page (PHP, CGI, or whatever) that behaves like the autoindex module, hence the confusion.

---

### Post by winch on 2008-01-19
Take a look at the mod_autoindex documentation.
[http://httpd.apache.org/docs/2.0/mod/mod_autoindex.html](http://httpd.apache.org/docs/2.0/mod/mod_autoindex.html)

In particular the HeaderName and ReadmeName directives.

---

