---
title: "HTML 5 and CSS: multi-language website"
date: 2014-05-16
forum: Programming Talk
---

### Post by erotavlas on 2014-05-16
Hi,

I would like to create a multi-language website that is able to switch to the right language based on the default language used in the browser that visits the website. I would like to avoid to used PHP and all things that requires server side. I read many possibilities on the web in order to do this but no one uses only HTML 5 and CSS. My first question is: is it possible to do this? If yes can you suggest to me a guide?
Thank you

---

### Post by Lars Noodén on 2014-05-16
[content negotiation](http://tools.ietf.org/html/rfc2616) is part of the HTTP specification and supported by Apache2 and nginx.  For Apache, you need to enable [multiviews](http://httpd.apache.org/docs/2.4/mod/core.html#options) for the directories in question.  Then [AddLanguage](http://httpd.apache.org/docs/2.4/mod/mod_mime.html#addlanguage) for each language.

```

AddLanguage 			en 	.en
AddLanguage 			fi   	.fi 
AddLanguage 			sv 	.sv 
LanguagePriority 		en 	fi 	sv 
DefaultLanguage 		en 
DirectoryIndex	index index.html

```

The full list of language abbreviations is found in [ISO 639](http://www.loc.gov/standards/iso639-2/php/English_list.php).  The module *negotiation* should already be enabled.

Then the hard work comes.  You need to make an extra copy of each web page for each additional language.  So if you have Finnish, Swedish and English, you would have three index pages:

[list]
[*] index.en.html
[*] index.sv.html
[*] index.fi.html
[/list]

Then if the user visits "index.html" the browser will redirect to the correct match or else the default.  Your site can use generic links, e.g. "index.html", or else explicit links to a specific language, e.g.  "index.sv.html"

---

### Post by Lars Noodén on 2014-05-16
Reading that you want to avoid server-side configuration, you might be able to do it with CSS alone using the [lang pseudo-class](http://www.w3.org/TR/css3-selectors/#lang-pseudo) and hiding / unhiding <div> or <body> elements based on language.  However, if it works I feel that would be rather messy in addition to unnecessarily increasing bandwidth.  It should be fine for small amounts of text though.

For larger amounts of text, I'd recommend setting the options for mod_negotiation mentioned above.  They only need to be set once.

---

### Post by erotavlas on 2014-05-16
Thank you. So in any case I have a copy of html files for each language. I have not access to server configuration since the host server is not mine. I have access only to the folder of website. Probably the best way is to use old trick of flags one for each language and to share pictures, videos and data among different languages. In this way I can set the English page as default index.html and a flag to index.es.html, index.it.html and so on. Do you agree?

---

### Post by Lars Noodén on 2014-05-16
Yes, naming the files works to a certain extent even without content negotiation.  If you do not have access to the server's configuration and the admins are not helpful you still might be able to make the changes in .htaccess.  I haven't tried but that's the situation .htaccess is designed for.

Is the server Apache2 or nginx?

---

### Post by erotavlas on 2014-05-16
The server is Apache. What is the difference  between .htaccess and httpd.conf ? Can I only modify the first?

---

### Post by Lars Noodén on 2014-05-16
Configuration-wise, .htaccess can configure a small subset of options that the main virtual host configuration file can.  See what is allowed for the directive AllowOverride.

.htaccess, if allowed by the server, is basically an extension to allow non-administrators some local control over the server configuration for their directories.  It's used when you don't have access to the server configuration but you do have write access to the directories and the web server administrator has [configured the server to allow use of .htaccess](http://httpd.apache.org/docs/2.4/mod/core.html#allowoverride).  

It sounds like it may be a match for your situation, but otherwise it is best to keep everything in one place.  It also affects performance a little.  If you can modify the vhost configuration file, wherever it is, that is better than falling back to .htaccess

---

### Post by erotavlas on 2014-05-16
> **Lars Noodén said:**
> Configuration-wise, .htaccess can configure a small subset of options that the main virtual host configuration file can.  See what is allowed for the directive AllowOverride.

.htaccess, if allowed by the server, is basically an extension to allow non-administrators some local control over the server configuration for their directories.  It's used when you don't have access to the server configuration but you do have write access to the directories and the web server administrator has [configured the server to allow use of .htaccess]("http://httpd.apache.org/docs/2.4/mod/core.html#allowoverride").  

It sounds like it may be a match for your situation, but otherwise it is best to keep everything in one place.  It also affects performance a little.  If you can modify the vhost configuration file, wherever it is, that is better than falling back to .htaccess

Ok thank you.

---

