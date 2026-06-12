---
title: "Making a server to host a website"
date: 2014-03-21
forum: New to Ubuntu
---

### Post by john172 on 2014-03-21
I am brand new to Ubuntu and brand new to this form so hello all. I have Ubuntu desktop 12.10. I have installed apache2, php, and mysql. I have gotten a lot of mixed information from a lot of different places so I'm confused. Can anyone give me a detailed explanation on how to make a server to host a website for the world to see?

---

### Post by 7sbaV8Kt5PTh on 2014-03-21
Hi John!  Actually, you have done most of the real work.  Now that you have Apache installed, you just need to create your website.  There are a lot of tools out there to create one, you can even use MS Word.  Once the site is created, you merely need to copy it into /var/www/ and restart Apache.  That is the most basic form of a website.

That said, you will have to name the landing page "index.html" or whatever is listed in /etc/apache2/sites-enabled/default-000.  That file contains the virtual host information.  

You should also spend some time reading about building an Apache website, using PHP to build one, etc.  As with Linux, there are many, many ways to get this done.

---

### Post by Mark Phelps on 2014-03-21
Word of caution -- from past experience...

If your intent (as it looks) is to let "the world" access this website, how are you obtaining access to the Internet for folks to get to your web server?

If (as I suspect), you're going through an ISP, many (if not all) of them can easily detect someone running a website and, when they do, they can get very nasty about it -- as such use is nearly always a violation of the Terms of Service of the ISP-provided Internet access.

I did this a while back just to test a website I was building and it took my ISP only one DAY to detect me -- and send me a nasty email about either converting to a Commercial Contract or terminating the website.

IF, on the other hand, you're running the website on a server that has already made arrangements with you to host that website, you should be OK.

---

