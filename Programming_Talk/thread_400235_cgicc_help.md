---
title: "cgicc help"
date: 2007-04-03
forum: Programming Talk
---

### Post by wacind on 2007-04-03
Hi 

Im trying to set up cgi c++ but im running into a few issues

first i created a testcgi.hmtl file and placed that in /var/www/html

i created a testcgi.cpp comiled that using

**g++ -o testcgi testcgi.cpp -lcgicc**

i then placed testcgi into /var/www/cgi-bin

but my code doesnt seem to work. i get the error
[B]
The requested URL /cgi-bin/testcgi was not found on this server.[/B]

I tried following [[COLOR="Blue"]this tutorial[/COLOR].]("http://www.yolinux.com/TUTORIALS/LinuxTutorialC++CGI.html")

Thanks
wacind

---

### Post by pmasiar on 2007-04-03
> **wacind said:**
> Im trying to set up cgi c++ but im running into a few issues

CGI - like web application? in C++? maybe you want to try some language better suited for web apps, like Python or Ruby?

Simple exampe in Python (to start, 3 lines): [http://learnpython.pbwiki.com/WebApplication](http://learnpython.pbwiki.com/WebApplication)

---

### Post by lnostdal on 2007-04-03
C/C++ for web-programming isn't a good idea, but: [http://ubuntuforums.org/showpost.php?p=2359669&postcount=4](http://ubuntuforums.org/showpost.php?p=2359669&postcount=4)

---

### Post by Wybiral on 2007-04-03
I agree that C++ isn't the greatest for web design, lol. But anyway, I got GCI properly set up on apache2, here was my post:
[http://www.ubuntuforums.org/showthread.php?t=394403](http://www.ubuntuforums.org/showthread.php?t=394403)

---

### Post by wacind on 2007-04-03
hi 

thanks for your replies

i did exactly as you wrote Inostdal, but i still get the error
**The requested URL /cgi-bin/test was not found on this server.**

when i do ./test i get the correct output on the terminal

I dont know if it may be a problem with permissions.

only reason im using c++ cause its a school project 

thanks
wacind

---

### Post by lnostdal on 2007-04-03
the url is host/~username/cgi-bin/test .. not host/cgi-bin/test

---

### Post by wacind on 2007-04-03
thanks, it was a dumb mistake on my part

---

