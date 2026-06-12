---
title: "thinking of a program to write all files in a directory to html code"
date: 2011-05-16
forum: Programming Talk
---

### Post by impulse338 on 2011-05-16
So i'm very new to programming and i'm very interested, i started running an apache server off my home ubuntu machine and would like to figure out a script to take all the files in a directory and input them into an html link. 

  heres what i have so far

#!/bin/bash


for f in *.mp3 do >> "$f" hmtmloutput.txt <a href="'${f%.mp3}.mp3'"</a>; done

be gentle its my first post! any and all help will be greatly appreciated.

Note: i took the idea from a for loop for encoding files with ffmpeg

---

### Post by myrtle1908 on 2011-05-16
Most web servers (including Apache) come with directory browsing support.  By this I mean you can browse your file system via HTTP and click on your files with a web browser etc. Is this what you mean?  If so there is no need for a script.

Google for "apache enable directory browsing".

---

### Post by impulse338 on 2011-05-16
Thanks for your reply, i found the directory browser and it works fine, i would just like something a little more aesthetically pleasing. so if i could just have a script that would write the code for all the files in the directory into links then i could add that code to my web page and have free reign to make the page look however i want.

---

### Post by r-senior on 2011-05-16
You can add HTML headers and footers to those pages, which gives you quite some scope for changing the appearance using CSS:

[http://httpd.apache.org/docs/current/mod/mod_autoindex.html#headername](http://httpd.apache.org/docs/current/mod/mod_autoindex.html#headername)

---

### Post by impulse338 on 2011-05-17
great idea, i think this is what i'm looking for but i can't get it to work... i made a HEADER.HTML file, put it in my /var/www folder and put a line in the /etc/apache2/httpd.conf file that said HeaderName HEADER.html and restarted the server like i read on another forum to do but nothing seemed to change and i can't for the life of me figure it out lol.

---

### Post by r-senior on 2011-05-17
When you specified the file in the configuration, did you start with '/'?

> If Filename begins with a slash, it will be taken to be relative to the DocumentRoot.

---

### Post by impulse338 on 2011-05-17
Nope no slash, but also the httpd.conf file  is empty. is apache using a different config folder now?

---

### Post by r-senior on 2011-05-18
The default install of Apache on Ubuntu is set up to make it easy to configure virtual hosts:

[https://help.ubuntu.com/10.10/serverguide/C/httpd.html](https://help.ubuntu.com/10.10/serverguide/C/httpd.html)

In short, look in /etc/apache2.conf (global) and /etc/apache2/sites-available (host). If you haven't changed anything around, your DocumentRoot is probably specified in /etc/apache2/sites-available/default.

---

