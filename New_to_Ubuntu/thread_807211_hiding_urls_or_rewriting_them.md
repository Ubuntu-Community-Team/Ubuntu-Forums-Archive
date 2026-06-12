---
title: "hiding urls or rewriting them"
date: 2008-05-25
forum: New to Ubuntu
---

### Post by nynoah on 2008-05-25
Does anyone know how I should go about rewriting URLs so they do not show my affiliate ID inside of them.  Is there a program in ubuntu to do this.  I am kinda clueless about this and trying to learn.  Any help or direction would be great.

Thanks

---

### Post by spiderbatdad on 2008-05-25
mod_rewrite.
```
 Give QSA (query string append) a try:

rewriteRule ^([a-zA-Z0-9\-]+)/([a-zA-Z0-9\-]+)/$ /index.php?VAR1=$1&VAR2=$2 [QSA,L] 
```

[http://www.webmasterworld.com/apache/3542127.htm](http://www.webmasterworld.com/apache/3542127.htm)

---

### Post by nynoah on 2008-05-25
WOW............that is not going to be easy......damn it.

---

### Post by nynoah on 2008-05-25
If I have another site hosting my page.  Can I still try to use the method they are talking about or does this not apply to me.  My server is a linux based server to.  But it not hosted by me.  I am using hosting from this site.  [https://www.securepaynet.net/gdshop/rhp/default.asp?prog_id=429957]("https://www.securepaynet.net/gdshop/rhp/default.asp?prog_id=429957")

---

### Post by spiderbatdad on 2008-05-25
It's easier than it looks. Check this link for htaccess rules: [http://corz.org/serv/tricks/htaccess2.php?page=all](http://corz.org/serv/tricks/htaccess2.php?page=all)

---

### Post by nynoah on 2008-05-25
Thanks for directing me to the tutorial spiderbat.....I will read that

---

### Post by spiderbatdad on 2008-05-25
> **nynoah said:**
> If I have another site hosting my page.  Can I still try to use the method they are talking about or does this not apply to me.  My server is a linux based server to.  But it not hosted by me.  I am using hosting from this site.  [https://www.securepaynet.net/gdshop/rhp/default.asp?prog_id=429957]("https://www.securepaynet.net/gdshop/rhp/default.asp?prog_id=429957")

Don't know. assumed you were running your own apache server. .htaccess files and the various modules get enabled via the apache software. htaccess files are generally contained in the same directory as the indexes they serve. So if you have the ability to upload your own indexes per directory and access to the directories...it might be possible on a remote server.

---

### Post by nynoah on 2008-05-25
i will ask my host.

---

### Post by nynoah on 2008-05-25
ok i have an appache

---

### Post by nynoah on 2008-05-25
Sow the question is how do I implement this into my links.  I am using Kompozer to design all my web pages.  I have not got good enough at hand coding to be able to hand write everything.  I can pick my way through things when I view code.

---

### Post by spiderbatdad on 2008-05-25
The .htaccess is a separate file that goes into the same directory as your webpage.html. It contains rules like the url rewrite or authentication rules. It might be more fun to install apache2 on your machine and play around with it locally. No need forward ports via your router if you don't want. Just view your pages by typing localhost into your browser address bar.

Here is my lame attempt at a tutorial:[http://spiderbatdad.wordpress.com/basic-apache2-how-to/](http://spiderbatdad.wordpress.com/basic-apache2-how-to/)

And here is some community documentation as a tutorial:[https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

---

