---
title: "How to use LAMP?"
date: 2012-06-26
forum: New to Ubuntu
---

### Post by rekhyt73 on 2012-06-26
Hi,

I wish to learn php, for which i was advised to install LAMP server. I have already installed it in my ubuntu 12.04. Now how do I start using it, i.e writing php codes and all? Please answer in detail as I do not know things like how to " open document root file in web browser " and all that.

Thanks.

---

### Post by MG&amp;TL on 2012-06-26
> **rekhyt73 said:**
> Hi,

I wish to learn php, for which i was advised to install LAMP server. I have already installed it in my ubuntu 12.04. Now how do I start using it, i.e writing php codes and all? Please answer in detail as I do not know things like how to " open document root file in web browser " and all that.

Thanks.

...have you learnt HTML? You need to learn HTML before you learn PHP, at least in my opinion.

Anyway, the default document root for Apache (where you put your webpages and PHP scripts) is /var/www/ . There's a default index.html there already by default, installed by apache. 

To view your webpages, open a web browser and navigate to "http://localhost"

---

### Post by mastablasta on 2012-06-26
a good online tutorials and school (for HTMl, PHP...) can be found here: [http://www.w3schools.com/](http://www.w3schools.com/)

---

### Post by greenpeace on 2012-06-26
As you might expect, php.net is an excellent resource... 

Here's a good tutorial to get you started: [http://php.net/manual/en/tutorial.php](http://php.net/manual/en/tutorial.php)

then use the more specific references when you have more specific questions... such as about individual functions.

I think it's better to have a project to work on as you get started... it doesn't have to be complicated, but it's good to have something to work towards, to keep yourself focused and to have something at the end of it all.

---

### Post by prshah on 2012-06-26
> **rekhyt73 said:**
> 
I wish to learn php, for which i was advised to install LAMP 

Here's a quick primer for you:

LAMP:
L - Linux (Operating system)
A - Apache (webserver)
M - MySQL (Database server)
P - PHP Interpreter.

Given that you have installed LAMP as above, you should first check if your Apache server is working. From a networked computer, open a browser and browse to the ip address of your server (or, if you have a browser on the server, browse to [http://localhost](http://localhost) ).

If apache is setup properly, you should get a "It works!" or similar message.

Typically, your webserver root is at /var/www. Create a simple "Hello world" type PHP file (eg index.php) at this location. Case matters!

Now, in the browser, browse to the server ip, but add "/index.php" to the address (Eg, [http://localhost/index.php](http://localhost/index.php)).

You should find your PHP output in the browser.

Please post back with details on your setup, actions taken and outputs (if any) from the above steps, if you need more assistance.

---

