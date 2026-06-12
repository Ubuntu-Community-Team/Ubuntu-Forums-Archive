---
title: "[SOLVED] Webpage Run Terminal Commands"
date: 2008-02-19
forum: Programming Talk
---

### Post by stooshbunutu on 2008-02-19
Hiya I want to make an internal webpage run a command in terminal when I click a button, is this possible?

If possible using mainly html and javascript

Cheers :)

---

### Post by LaRoza on 2008-02-19
You have a script on the server run it, and return the results.

---

### Post by stooshbunutu on 2008-02-19
Sorry to be nooby but i don't quite understand what you mean

ps attatched is the webpage in question (just save it as .html)

---

### Post by LaRoza on 2008-02-19
To execute commands outside of the browser, you would need a server. 

It is usually not done for security reasons.

It would take more programming than you probably think it would be worth.

---

### Post by stooshbunutu on 2008-02-19
Ok thanks for the help anyway

I will just mark as solved and move on

---

### Post by lnostdal on 2008-02-19
install apache and php on your ubuntu PC and you can give it a go

```

sudo aptitude install apache2 libapache2-mod-php5

```

apache might already be started now, but we can make sure:

```

sudo /etc/init.d/apache2 start

```

..now you are running the apache http/web server on your ubuntu .. see for yourself with your browser: [http://localhost/](http://localhost/)

now, at this point you can start by creating a directory named *public_html* in your home folder .. put a html-file in that folder so you end up with */home/yourusername/public_html/some-html-file.html*

now take a look with your browser again: *[http://localhost/~yourusername/some-html-file.html](http://localhost/~yourusername/some-html-file.html)*

you probably get the idea .. you need to replace "yourusername" with well, your username .. the ~ character is needed, as shown above

..at this point you can start learning php (google it), and save some .php-files in your public_html folder .. further move on to [http://no.php.net/manual/en/ref.exec.php](http://no.php.net/manual/en/ref.exec.php) and you have your solution, the ability to "execute programs" from web-pages

edit:
note that you can use many languages on the "server side" like this .. things like php, python and ruby are quite common .. some use java or lisp

edit2:
oh, and yeah -- you need to code this on the server so you can't use html or javascript (not client side (the type running in your browser) javascript anyways)

---

### Post by ronnieredd on 2008-11-15
A little after the fact, I know.

You should start on php here: [http://www.php.net/manual/]("http://www.php.net/manual/")

Bookmark it. I find myself back there all the time. There are offshoots of the this site everywhere, however this is the official one and the latest posts from developers get put there.

The above link should figure out your language and give you something like:

[http://www.php.net/manual/en/index.php]("http://www.php.net/manual/en/index.php") (English for instance)

Have Fun!
My own little corner of php info which shows how to run cli in php.
[http://www.cruzit.com/info_php.php]("http://www.cruzit.com/info_php.php")

---

