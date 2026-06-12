---
title: "LAMP is online but not working with PHP"
date: 2013-05-12
forum: New to Ubuntu
---

### Post by DogHam on 2013-05-12
Hi!

I hope, i'm in the correct forum :P

I found [this]("http://ubuntuforums.org/showthread.php?t=1682888") and it's working for me very well. But I can't run any PHP sites. 

When I upload a .html it's working.

Why?

Thank you!!! :)

******
Ubuntu 12.04 LTS 32-bit on 64-bit system
php5.3 or 5.4 not sure
apache2

*Internet Provider*:
Swisscom.ch
port:80 over TCP&UDP
Dynamic IP

---

### Post by iamkuriouspurpleoranj on 2013-05-13
How did you set it up?


[LIST]
[*]What software?
[*]What commands did you install it with?
[*]What are the folder/file permission settings (that are changes you've made)?
[/LIST]

---

### Post by DogHam on 2013-05-13
> **iamkuriouspurpleoranj said:**
> How did you set it up?


[LIST]
[*]What software? 
[*]What commands did you install it with? 
[*]What are the folder/file permission settings (that are changes you've made)? 
[/LIST]


Thank you for answer. 

I installed NOTHING. Just added the port in my router.

---

### Post by Lars Noodén on 2013-05-13
You also have to install the [php5](http://packages.ubuntu.com/raring/php5) package first.  That will install the PHP scripting language and turn on the corresponding Apache module.

Perl is already there by default, if you need to use that too/instead.

---

### Post by DogHam on 2013-05-13
ok also maybe that was wrong question. 

on [http://localhost/](http://localhost/) is php working great but on [http://myip/](http://myip/) not.

---

### Post by Lars Noodén on 2013-05-13
How far can you get when connecting to  [http://myip/](http://myip/) ?  Can you get static web pages at all, but just not PHP pages?  If not, check your packet filter / firewall.

---

### Post by DogHam on 2013-05-13
I'm newbie in this things... could you please give me a link or something to check that?

---

### Post by Lars Noodén on 2013-05-13
When you open  [http://myip/](http://myip/)  in your web browser, what happens that doesn't happen when you connect to [http://localhost/](http://localhost/) or vice versa?

---

### Post by DogHam on 2013-05-14
I have my files in "localhost/template1 (2,3,4,5 not important) because I'm making templates... When I go to "/localhost" I see the message "It works,...." On "http://myip/" i can see the message too. But [http://myip/template2](http://myip/template2) or 1 or other i see blank page. When I create a file there i can see it but only "html"

---

### Post by Lars Noodén on 2013-05-14
If the server is not producing an error message in your browser, it sounds like the page is getting served properly.  If it is an empty XHTML template, it will look empty in a normal browser.  If you are in Firefox, press ctrl-U to see the page source code and maybe there you will see the contents of your template.  

If the template contains PHP code, then that will get processed before the page is served.  If you look in /etc/apache2/mods-available/php5.conf, you can see that it does that for any file ending in *.php* or something similar.  If you do not want the page's PHP code processed on the way out to the browser, you can give another file ending, one not in use, like *.foobar*.

---

### Post by DogHam on 2013-05-14
ok now it's working... I don't know how and why but it's there... I have installed the script again but not trought localhost... thank you for help

---

### Post by Lars Noodén on 2013-05-14
I'm glad it's working.  If you do start to get errors some time one trick is to watch the log real time with [tail](http://manpages.ubuntu.com/manpages/raring/en/man1/tail.1.html).  To do that, open a terminal window and have it on the screen along side your browser and run tail on the error log:

```

tail -f /var/log/apache2/error.log

```

Then as you load the broken pages or scripts in your browser, you can watch the errors as they show up in the log.

---

