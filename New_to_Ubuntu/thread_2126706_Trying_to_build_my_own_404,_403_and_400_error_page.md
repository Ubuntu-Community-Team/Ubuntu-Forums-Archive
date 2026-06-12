---
title: "Trying to build my own 404, 403 and 400 error pages"
date: 2013-03-17
forum: New to Ubuntu
---

### Post by Maurices5000 on 2013-03-17
I'm trying to build my own 404, 403, and 400 error pages.  Here is the website where i got the information.
[http://queenofsubtle.com/404/?page_id=2180](http://queenofsubtle.com/404/?page_id=2180)

It says: "Create a file called .htaccess i**n the root directory of the server** (the  one you refer to as ‘/’) and enter your error handlers in the following  format, one per line:"

I don't understand why they don't just tell you what to do step by step. But is the root directory of the server /etc/apache2?  
at in the etc/apache2/ directory i type sudo nano .htaccess and then type the error handlers he lists?

where would i create this folder on server root or /var/www?  

/errors/custom404.html


Is that what i do? Thanks!

---

### Post by squakie on 2013-03-18
Okay, first off I don't know squat about the server.  I did find [this ]("http://stackoverflow.com/questions/5891802/how-do-i-change-the-root-directory-of-an-apache-server")which talks about the document root for apache - I don't know if that's the same thing or not. 

As far as the files, from the link you provided it would appear you would put the entries like 

ErrorDocument 404 /errors/custom404.html  
in the .htaccess file (if you follow my link, I think that somewhere in the conf file it will show what your root folder is - and perhaps it is just "?") in the server "/" folder, then define an html file (in the example above, custom404.html in the /errors folder) that contains what you want that page to look like - they named it custom404 since it is a custom page 404).

It will require a server reboot.

Don't know if that helps you at all or not.

---

### Post by Doug S on 2013-03-18
I would recommend using the ubuntu server guide for this type of information, as it is specific to ubuntu. In the [12.10 guide (pdf)]("https://help.ubuntu.com/12.10/serverguide/serverguide.pdf") see chapter 11 sub-section 1.2.2, where it says:> Read /etc/apache2/conf.d/localized-error-pages for detailed instructions for using ErrorDocument, including locations of example files.

---

### Post by Maurices5000 on 2013-03-18
based on waht the documentation says, looks like i need to read the information here: /etc/apache2/conf.d/localized-error-pages

I hope that solves it. I'll check it out tomorrow. i thought this would be simple and straight forward.

---

### Post by mörgæs on 2013-03-18
Changed the title to a more informative one.

---

