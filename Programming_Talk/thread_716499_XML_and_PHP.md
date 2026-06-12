---
title: "XML and PHP"
date: 2008-03-06
forum: Programming Talk
---

### Post by The Titan on 2008-03-06
i have a small site that i use flat files to display different things and i recently ran across some information on XML.  It looks like (if i understand correctly) an excellent way to organize (replace) my flat files.  All of the files are huge and complicated to update.  The only issue is i dont know how to use PHP to read the XML file.  I read somewhere that i have to compile and install an entire new plugin for PHP on my webserver.... i can't do this.  Somebody please put me in my place.... im lost in this mess in my head.  I need a humans explanation.

---

### Post by LaRoza on 2008-03-06
> **The Titan said:**
> i have a small site that i use flat files to display different things and i recently ran across some information on XML.  It looks like (if i understand correctly) an excellent way to organize (replace) my flat files.  All of the files are huge and complicated to update.  The only issue is i dont know how to use PHP to read the XML file.  I read somewhere that i have to compile and install an entire new plugin for PHP on my webserver.... i can't do this.  Somebody please put me in my place.... im lost in this mess in my head.  I need a humans explanation.

It sounds like you should be using a database, I recommend MySQL (which is almost always there if you are using PHP) or PostgreSQL.

XML is easy to parse using SAX or the DOM, but for what you describe, you need a database. (XML would just a logical flat file, not really an improvement, and it would make things even more complicated)

---

### Post by The Titan on 2008-03-06
i have a mysql database also for most things, but im hell bent on finding out how to do this for future applications.  
What is SAX/DOM? and how can i utilize this?

Off Topic:If you are wondering (if it matters) i have some things in flat files so my sister can update them from her laptop (no internet access).  then she can put it on a CD and give it to me and i just replace the files with the new ones.  BAM the site is updated.  It's eisier for the both of us.

---

### Post by LaRoza on 2008-03-06
> **The Titan said:**
> i have a mysql database also for most things, but im hell bent on finding out how to do this for future applications.  

Off Topic:If you are wondering (if it matters) i have some things in flat files so my sister can update them from her laptop (no internet access).  then she can put it on a CD and give it to me and i just replace the files with the new ones.  BAM the site is updated.  It's eisier for the both of us.

Here is the PHP DOM reference: [http://www.php.net/dom](http://www.php.net/dom)

What sort of information is in these files?

---

### Post by The Titan on 2008-03-06
the data in these files is really stupid actually, but here goes.  Me and her are in high school and we are on the newspaper team together (i know, total nerds right =P) and i was starting to get interested in web programming so  I talked to the teacher that ran it all and asked him if i could make a local web site(for only the school network) that was an online copy of the weekly newspaper.  The newspaper is is just a bunch of columns written by different students.  The flat files include things like the author of the columns the body the date and such things.   The way it looked XML is perfect for such things.  I run the website and my sister ports everything over to the flat files to put up there.  The theme of the page changes every week which is the data contained in mysql.  

Long Stupid, but you asked.. :lolflag:  i appreciate your help.

---

### Post by cb951303 on 2008-03-06
mysql is still better for the purpose. you can make a nice admin panel so your sister could easily input data (easier than editing xml files)

anyway, if you still want to use XML, and if you have access to PHP5 in your server try this ;)  [http://tr2.php.net/simplexml](http://tr2.php.net/simplexml)

---

### Post by LaRoza on 2008-03-06
> **The Titan said:**
> the data in these files is really stupid actually, but here goes.  Me and her are in high school and we are on the newspaper team together (i know, total nerds right =P) and i was starting to get interested in web programming so  I talked to the teacher that ran it all and asked him if i could make a local web site(for only the school network) that was an online copy of the weekly newspaper.  The newspaper is is just a bunch of columns written by different students.  The flat files include things like the author of the columns the body the date and such things.   The way it looked XML is perfect for such things.  I run the website and my sister ports everything over to the flat files to put up there.  The theme of the page changes every week which is the data contained in mysql.  

Long Stupid, but you asked...  i appreciate your help.

You could teach her enough XHTML to make it easier.

My site: [http://laroza.freehostia.com/home](http://laroza.freehostia.com/home) seems to use a similar approach to what you describe, the content of each page, differs and is stored in a different file ([http://laroza.freehostia.com/home/includes/programming.inc](http://laroza.freehostia.com/home/includes/programming.inc), for one)

If you could have the content done like that, with just simple markup, it might be easier.

---

### Post by pmasiar on 2008-03-06
XML is for data transfer in heterogeneous systems, not for data storage. And often, XML is not a solution, but yet another problem: you need to parse it.

Database is better solution to store homogeneous data. SQLite is excellent database in situation like yours (doesn't require server or administration, as your database is single-user).

I am not sure how are your Linux admin skills, who will help you to set up web server. You may also consider wiki: easy to edit website. You can get free wiki at pbwiki (see my sig). Generating text files with wiki markup is easier than generating valid HTML/XML, too, because markup is so much simpler.

---

### Post by Can+~ on 2008-03-06
XML is great for small things like configuration files used in an application. Mostly short things or that rarely change.

A Database should solve your problem and make the whole process more efficient.

---

