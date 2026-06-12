---
title: "http://www.xy vs. www.xy how to adjust the webmin-apache?"
date: 2015-03-15
forum: Programming Talk
---

### Post by dilbert_one on 2015-03-15
fairly new to webmin 

i have set up several pages

but i have to type 
[http://www.xy](http://www.xy) vs. [www.xy](www.xy) to access the page 

why is this so?

how to adjust the webmin-apache?

---

### Post by benrob0329 on 2015-03-17
Sounds like a problem with your web browser or internet connection, do you have to do that with your phone/a friends computer? Or try a different web browser.

---

### Post by dilbert_one on 2015-03-18
close but no cigar 

try it out  - 

check [http://www.ex-libri.org](http://www.ex-libri.org)  
or [http://www.literaturen.org](http://www.literaturen.org)  - type it with and witrhout the http _ see the change 
once you can access the site - the other time you dont 

the apache needs to be configured - or not ?

what to do in webmin

---

### Post by benrob0329 on 2015-03-18
It seems to work for me. But you may want to check your virtual hosts to make sure you have one without www and without http. [VirtualHost Examples - Apache HTTP Server Version 2.2]("http://httpd.apache.org/docs/2.2/vhosts/examples.html") and [Webmin]("http://www.webmin.com/apache.html") are two articles worth looking at.

---

