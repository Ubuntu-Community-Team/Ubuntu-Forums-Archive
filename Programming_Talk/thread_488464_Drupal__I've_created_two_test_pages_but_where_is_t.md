---
title: "Drupal : I've created two test pages but where is the *.html or *.php files?"
date: 2007-06-30
forum: Programming Talk
---

### Post by jingo811 on 2007-06-30
I've created two test pages but where is the *.html or *.php files?
I'm not used to the **"click-this-in-order-to-do-what-Drupal-wants"** process. I feel much more comfortable editing my pages in a text editor tweaking my html/css and a little php. But how can I do that?

Like I only want to use the login system how can I copy-and-paste that function or include php code into my *.php files manually?
Is this possible without knowing how the login system code works?

Drupal is hard to control :-(

---

### Post by mvaniersel on 2007-06-30
Drupal stores the pages in a database, so it's not that easy to edit directly.

It sounds to me that Drupal is just not the right system for you, and you'd be better of with a simple home written php-template system. Have you considered that?

---

### Post by nitro_n2o on 2007-06-30
ohh yeah Drupal is a pain in this matter... you can't do things directly.. Everything is stored in the database, and all pages are dynamically created by php scripts. FYI, all requests are sent to index.php However, you can modify the css directly and change the look and feel of your site..My advice is to copy one of the themes in the themes folder and modify it. 
Once you get used to drupal, your life will be really easy :) 
Have fun

---

### Post by jingo811 on 2007-06-30
I've decided to dive back into my SitePoint OOP+PHP Solutions books.  It seems easier to accomplish what I want doing from scratch than back-engineering and picking out pieces from Drupal.

---

