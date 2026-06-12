---
title: "how to test php5 programs using apache"
date: 2008-04-15
forum: Programming Talk
---

### Post by bisnaguete on 2008-04-15
I'm starting to program in php5 and i need to test my programs to make sure it's working.

The problem is: I don't know how.

I've installed Apache, MySQL, PHP5 and all that stuff and when i tipe localhost on firefox it says: It Works (what is a good thing to know).

My question is: Where do i put my php files to run it in the localhost?

---

### Post by jonathanmotes on 2008-04-15
The document root is at /var/www by default. This directory belongs to root, so you will have to run Nautilus (your file manager) as root in order to add files there:

In a terminal, type
```
sudo nautilus
```

However, it is best to create a new directory in your home folder called something like public_html and change the document root to that so that you will not have to have root permissions to copy files.

To change it, enter this in a terminal:```
sudo gedit /etc/apache2/sites-available/default
```

Change the first two lines **that have /var/www/ in them** (lines 4 and 10, I believe) to 

```
DocumentRoot /home/yourusername/public_html/
```
And
```
<Directory /home/yourusername/public_html/>
```

then restart Apache:

```
 sudo /etc/init.d/apache2 restart
```

Post back if you have questions!

---

### Post by BillGrates on 2010-12-05
:icon_frown:

Greetings.
My programming skills are simply amazing.
Sadly however they are amazingly deficient.

I have followed the above without a problem
Creating /my_home_folder/pubic_html/

Then I installed a my.php file into the created public_html folder.
However I can not get the syntax correct to find/run my.php from the Firefox browser.

I would have thought that [http://localhost/my.php](http://localhost/my.php) should have run, but I get 'not found'.

Please smile and advise ...have spent days/weeks trying to be able to 
come to grips with PHP.

..and as above [http://localhost/](http://localhost/) provides "It Works"

Using Ubuntu 10.10 php5 downloaded from Synaptic.

Thanking you muchly,

Bill

---

### Post by BillGrates on 2010-12-05
So very sorry.
My problem was that my ISP space was full so uploading my.php was not
in fact uploaded.

Please ignore my append.

Bill

---

