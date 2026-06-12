---
title: "Firefox is asking me To download .php file with form."
date: 2010-03-25
forum: Programming Talk
---

### Post by sylar petrelli on 2010-03-25
Hi guys, 
I am learning PHP right now. I was creating a form that would take a user's name and email address, then when they submitted it it would print their name and email through a php program.

However, everytime I hit submit. A download screen asks me if I want to open my PHP file. It gives me the option of opening it with my local ide or saving the file.

I am using Ubuntu 9.10 with Apache and I am running all these scripts as a local host. Otherwise if I write a php file and run it. it runs just fine.

Thanks,
Brian

---

### Post by Goveynetcom on 2010-03-26
> **sylar petrelli said:**
> Hi guys, 
I am learning PHP right now. I was creating a form that would take a user's name and email address, then when they submitted it it would print their name and email through a php program.

However, everytime I hit submit. A download screen asks me if I want to open my PHP file. It gives me the option of opening it with my local ide or saving the file.

I am using Ubuntu 9.10 with Apache and I am running all these scripts as a local host. Otherwise if I write a php file and run it. it runs just fine.

Thanks,
Brian
I had the same problem, and I still do. So, I'll await an answer as well. I think it's probably a simple fix.

---

### Post by lisati on 2010-03-26
Try clearing your browser cache.

Edit: Have a look here: [https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP) and scroll down the page to the section "Troubleshooting PHP 5"

---

### Post by Hellkeepa on 2010-03-26
HELLo!

Sounds like you haven't installed a web server with the PHP modules, or installed it correctly. You'll need a web server to run PHP whenever requesting PHP files, so that the PHP parser can execute the PHP-code for you, before sending the resulting HTML document to the web server (so that it can send it to you).

I strongly recommend using the package manager to install Apache and PHP5, that way everything will be set up correctly for you. So that you don't have to go messing about in the apache config files, and PHP's "php.ini".

Happy codin'!

---

