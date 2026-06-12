---
title: "Compiling PHP source code [Replacement for ZEND]"
date: 2011-01-28
forum: Packaging and Compiling Programs
---

### Post by baskar007 on 2011-01-28
Hi friends, 
 I am baskar, I am Newbie to PHP, Now i want to protect my PHP source code from theft by compiling it to a byte code like python do's......

I know there is a software to to it, but I don't have money  to buy a zend guard becoz i am a diploma :(student... I am under my parents.....

My question is I WANT TO COMPILE MY PHP SOURCE CODE LIKE ZEND GUARD.... HOW ???:confused:
is there is any software in open-source like ZEND ?????? :confused:


ADVANCED THANKS FOR YOUR REPLIES..

---

### Post by SeijiSensei on 2011-01-28
The easiest way to protect your PHP source is to keep it out of the web tree.  If you're serving pages from /var/www/, make index.php something minimal like this:

```

<?php
$include="/var/www/include";

require($include."initialize.php");
require($include."page_body.php");
?>
```

You can enforce more security by not using .php as an extension for the included files.  I use ".inc" then have a <FilesMatch> in the Apache configuration that denies access to "\.inc$".

Set /var/www/include to 0700 and the files to 0600 and have it all owned by www-data so Apache can read the files.

You know, I presume, that it's not possible to display the raw PHP code from a web browser, right?  The interpreter will only push out HTML code.

I've run PHP web applications for a dozen or so years.  Having my source code stolen hasn't ever been a concern.

---

### Post by baskar007 on 2011-01-28
> **SeijiSensei said:**
> The easiest way to protect your PHP source is to keep it out of the web tree.  If you're serving pages from /var/www/, make index.php something minimal like this:

```

<?php
$include="/var/www/include";

require($include."initialize.php");
require($include."page_body.php");
?>
```

You can enforce more security by not using .php as an extension for the included files.  I use ".inc" then have a <FilesMatch> in the Apache configuration that denies access to "\.inc$".

Set /var/www/include to 0700 and the files to 0600 and have it all owned by www-data so Apache can read the files.

You know, I presume, that it's not possible to display the raw PHP code from a web browser, right?  The interpreter will only push out HTML code.

I've run PHP web applications for a dozen or so years.  Having my source code stolen hasn't ever been a concern.
[SeijiSensei]("http://ubuntuforums.org/member.php?u=698195") Thankyou for your reply,
No i am talking about Source Code distribution,  I want to distribute my PHP source code to my clients, They not yet paid to me, So i wish to encrypt or compile or something similar to protect my code from clients...  [clients can access server !!!!! ]

Is there is any way to do it???

Once again thanks...

---

### Post by SeijiSensei on 2011-01-29
You mean your clients have shell access?  Wow, you're a trusting guy.  Personally, I'd do the development on a separate machine in that situation, but if you must share a server with the clients, put the code in a directory where only you and the www-data user can read it.  Something like this:

```

cd ~
mkdir secret
sudo chgrp www-data secret
mv /path/to/current_code/* secret
chmod 0750 secret -R
chmod 0640 secret/* -R

```

If by "clients can access server" you mean they can view the website with a browser, they won't be able to see the PHP code.  They'll only see the HTML source that the PHP interpreter produces.

---

### Post by v8YKxgHe on 2011-01-29
removed

---

### Post by sosimple on 2011-03-05
> **baskar007 said:**
> ....
My question is I WANT TO COMPILE MY PHP SOURCE CODE LIKE ZEND GUARD.... HOW ???:confused:
is there is any software in open-source like ZEND ?????? .....

Not exactly like Zend .... see below

> **baskar007 said:**
> [SeijiSensei]("http://ubuntuforums.org/member.php?u=698195") ..... No i am talking about Source Code distribution,  I want to distribute my PHP source code to my clients, They not yet paid to me, So i wish to encrypt or compile or something similar to protect my code from clients...  [clients can access server !!!!! ]

Is there is any way to do it???

Once again thanks...

I understand... you are making perfect sense.

You have written a PHP application (or paid someone to write it for you) and you want to sell copies of it or license it to your clients and hopefully many more future clients, to install your application on their website, but you don't want to provide the source code to the clients that buy/license the application. 

Once you give the unprotected source code for a program to someone else for them to install on their website, you have no control what will happen with it.

They could edit the source and create their own version and become your competition. One of their employees could give a copy of the source to a friend, or leave the company and take a copy with them and also become more competition.

Of course you may have some legal protections against this, but perhaps not in all cases.  And, it takes money, and lots of it to "police" the Internet and take legal action against those that copy your code. And also, you have to prove that they copied your code.

It is far better to protect the code now than to solve problems later.  As they say, an ounce of prevention is worth a pound of cure.

OK, so what I have seen is called Roadsend:
[http://www.roadsend.com/home/index.php](http://www.roadsend.com/home/index.php)

Roadsend PHP is a free, open source implementation of the PHP language. It includes a compiler that produces native binaries (no interpreter required). Roadsend Compiler can build online web applications with Fast/CGI, offline web applications with an embedded web server (MicroServer), and console applications. 

This may be overkill, I don't know about your particular case, but I guess it is worth taking a look at.

I don't have any personal experience using Roadsend.

Good luck with your project.

Kevin

---

