---
title: "PHP IDE w/ debugging"
date: 2005-12-26
forum: Programming Talk
---

### Post by dwessell on 2005-12-26
Hey all.. Can anyone suggest an IDE or editor for PHP that includes debugging capabilities? Open source, or free preferred..

I've read through the sticky thread.. But didn't seem much in the way of debugging for PHP.

Thanks
David

---

### Post by sapo on 2005-12-27
I dont debug php, just set error reporting to E_ALL, save your php file and refresh the browser :P

I aways used gedit for php, never used any IDE.

---

### Post by dwessell on 2005-12-27
Oh, but the joy to be had by watching the variables change as you step through a function.. Nothing makes me happier.. I have goose bumps just thinking about it..

Truth be told, I'm learning PHP as I go.. And I've found that a debugging tool can be super helpful when learning a new language..

Thanks
David

---

### Post by David Marrs on 2005-12-27
can't help on the debugger front, but bluefish is a very good PHP IDE. You can apt-get install it from the repos. You should also read the official documentation; it's very helpful.

---

### Post by nemik on 2005-12-27
zend studio is a great PHP IDE with dcent debugging, not free though...

---

### Post by asimon on 2005-12-27
There is the a PHP debugger called [Gubed](http://gubed.mccabe.nu) which can be used together with [Quanta](http://kdewebdev.org). Both are free software.

---

### Post by Seth on 2005-12-27
Eclipse + phpEclipse includes a complete debugger. It's very good.

---

### Post by bnlandry on 2007-07-30
I have gotten used to developing my new PHP project in PHPEclipse. However, I have not had any luck installing the debugger. The tutorial [here]("http://dd.cron.ru/dbg/installation.php") explains how to install DBG, but it does not address apt-get. I could not find the correct DBG package in the repositories, so I tried the steps he lists. However, although phpize is installed on my system, the "deferphpize" script in the DBG-2.10.15 archive acts like I don't have it. I have installed PHP 5, PHP-cli, and PHP-dev from the repositories. I feel like I am making several mistakes here. Any advice?
-bnlandry

---

### Post by JeevesBond on 2007-08-01
I've just written an article on this subject (since I had to do the same thing myself) see: [Easy PHP Debugging in Ubuntu (using Xdebug and Vim)](http://www.apaddedcell.com/easy-php-debugging-in-ubuntu-using-xdebug-and-vim).

I'm using [Vim](http://www.vim.org/), which is a fantastic general editor, but somewhat difficult to learn. :)

I believe that once you have Xdebug installed it should be trivial to get [Eclipse](http://www.eclipse.org/) or [Qanta](http://quanta.kdewebdev.org/) to work with it.

---

