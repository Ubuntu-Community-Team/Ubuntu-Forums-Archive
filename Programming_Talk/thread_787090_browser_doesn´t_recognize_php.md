---
title: "browser doesn´t recognize php"
date: 2008-05-08
forum: Programming Talk
---

### Post by Nam_Phet on 2008-05-08
Hit there,

I am trying to install Joomla on my laptop, but I cannot find the solution for one problem. When I point my browser to localhost/Joomla/index.php my dearest FF asks me what to do with that file: open or save? 

Now, I am no geek, I searched already for hours on the net how to solve this, but I haven´t found a solution yet. 

So my question is: can anyone explain me how to make my browser recognize .php files so I can go on with the Joomla installation?

Mysql is running fine. The php-test doesn´t work, as you may have guessed already :)

Thanks in advance!

---

### Post by LaRoza on 2008-05-08
> **Nam_Phet said:**
> Hit there,

I am trying to install Joomla on my laptop, but I cannot find the solution for one problem. When I point my browser to localhost/Joomla/index.php my dearest FF asks me what to do with that file: open or save? 

Now, I am no geek, I searched already for hours on the net how to solve this, but I haven´t found a solution yet. 

So my question is: can anyone explain me how to make my browser recognize .php files so I can go on with the Joomla installation?

Mysql is running fine. The php-test doesn´t work, as you may have guessed already :)

Thanks in advance!

Give the steps you did for better answers.

First, browsers don't know anything about PHP. It is supposed to be executed on the server. The browser prompt indicates that the file is being served without being executed.

---

### Post by mike_g on 2008-05-08
Have you tried restarting apache?

---

### Post by MicahCarrick on 2008-05-08
My thoughts are php is not installed. Try this (the ones you already have installed will be skipped):

```
sudo aptitude install apahce2 php5 libapache2-mod-php5 php5-gd php5-mysql
```

---

### Post by madjr on 2008-05-08
> **Nam_Phet said:**
> 

Now, I am no geek, I searched already for hours on the net how to solve this, but I haven´t found a solution yet. 


what's wrong with being a geek?

i think you're referring that you're not a "nerd".

what you doing is called **geek-work** :)

learning stuff makes you a geek.

but that doesn't mean a geek can't be cool or do sports or get drunk or say F*ck or do a bunch of "cool crap"...

---

### Post by Nam_Phet on 2008-05-08
Thank you all!

@ madjr: no bad thoughts about geeks, it is just that I don´t feel myself one, as I am messing things up too much. But on the other hand, that may be one of the characteristics of a geek :) So call me a beginning geek ;)

@all: Eventually I tried to remove as many of the php and apache packages I could find, as well as the complete joomla directory. And I started it all over again (in an attempt to write down all the steps for LaRoza). 

It went smooth! Amazing! But when I had to restart apache I got these errors: 

 * Restarting web server apache2                                                                                             [Fri May 09 01:36:31 2008] [warn] module php5_module is already loaded, skipping
Syntax error on line 1 of /etc/apache2/httpd.conf:
ServerName takes one argument, The hostname and port of the server

I remember I wrote down some line in the httpd.conf many hours before (inan attempt to execute php), so maybe these were some leftovers that were not removed at all? Or are these standard lines? I don´t know. 
I deleted them and had another restart of apache. Only the syntax error was left. After many trial and errors I found out I had to simply remove the word ´localhost´, so the httpd.conf was left with:

servername  127.0.0.1

Another restart and all went well!

No other problems arose. Great! 

Hope this can help other people too.

Kind regards

---

