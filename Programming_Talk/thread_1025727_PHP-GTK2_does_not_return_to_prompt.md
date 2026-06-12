---
title: "PHP-GTK2 does not return to prompt"
date: 2008-12-30
forum: Programming Talk
---

### Post by davidv on 2008-12-30
Hi everyone !

I'm trying to solve a problem for some days and maybe someone here could help.

I'm running linux ubuntu 8.10 Desktop

I'm working directly on the computer I'm not connected via ssh.
If type echo $DISPLAY I get :0.0

My version of PHP is :
(php --version)
PHP 5.2.6-2ubuntu4 with Suhosin-Patch 0.9.6.2 (cli) (built: Oct 14 2008 20:06:32)
I have a complete LAMP installed on this computer and working perfectly.

I've downloaded and installed the php-gtk2 extension from Bob Majdak Jr PHP-GTK2 blog in my extension folder.
(founded with php -i |grep extension_dir)
Bob's blog : [http://oops.opsat.net/](http://oops.opsat.net/)

I've added a conf file for the php_gtk2 extension in /etc/php5/conf.d
the content of the file is :

# configuration for PHP-GTK2
extension = "php_gtk2.so"

[php-gtk]
php-gtk.codepage = "UTF-8"
php-gtk.extensions = ""

With all theses settings the module is loaded and I can even run an application.

The problem is that at the end of the application php does not return to the prompt. I have to CRTL/C !

If I type in the terminal
php --version

With the **extension not loaded**
#extension = "php_gtk2.so"

PHP **returns normaly to the prompt**

But if I type the same
php --version

With the **extension loaded**
extension = "php_gtk2.so"

**PHP does not return to the prompt**

I have to kill with CRTL/C

I have exactly the same behavior if I try to setup a special php.ini file in for exemple /etc/gtk and use this file instead of the normal php.ini for CLI. (I specify this particular file using -c /etc/gtk/php.ini on the command line) 
Click here to see my php.ini file : http://pastebin.com/f47d28358

Does anyone have any idea about what could be causing this problem ?

Thank you very much in advance for your answer.

David V.

---

### Post by catchmeifyoutry on 2008-12-30
GTK starts like many GUI toolkits its own thread to handle GUI input events, redraw widgets when necessary, etc. So by using GTK you're giving the control of the program flow to the toolkit and the program will not end until you tell the toolkit to quit its thread.
A quick google for the php-gtk documentation shows that you should use the Gtk::main_quit() function. Maybe your program misses this call somewhere?

Note that i've never used GTK under PHP (I can't imagine why you would want to do that).

---

### Post by davidv on 2008-12-30
catchmeifyoutry,

Thank you for replying.

The problem I have is not related to the main_quit() instruction.

In fact I have the problem when the php-gtk2 extension is loaded even if I'm not trying to run any php-gtk script.

As I put in my previous post I use "php --version" to test and reproduce the problem.

Thank you

David V

---

### Post by davidv on 2009-03-22
> **davidv said:**
> Hi everyone !

I'm trying to solve a problem for some days and maybe someone here could help.

I'm running linux ubuntu 8.10 Desktop

I'm working directly on the computer I'm not connected via ssh.
If type echo $DISPLAY I get :0.0

My version of PHP is :
(php --version)
PHP 5.2.6-2ubuntu4 with Suhosin-Patch 0.9.6.2 (cli) (built: Oct 14 2008 20:06:32)
I have a complete LAMP installed on this computer and working perfectly.

I've downloaded and installed the php-gtk2 extension from Bob Majdak Jr PHP-GTK2 blog in my extension folder.
(founded with php -i |grep extension_dir)
Bob's blog : [http://oops.opsat.net/](http://oops.opsat.net/)

I've added a conf file for the php_gtk2 extension in /etc/php5/conf.d
the content of the file is :

# configuration for PHP-GTK2
extension = "php_gtk2.so"

[php-gtk]
php-gtk.codepage = "UTF-8"
php-gtk.extensions = ""

With all theses settings the module is loaded and I can even run an application.

The problem is that at the end of the application php does not return to the prompt. I have to CRTL/C !

If I type in the terminal
php --version

With the **extension not loaded**
#extension = "php_gtk2.so"

PHP **returns normaly to the prompt**

But if I type the same
php --version

With the **extension loaded**
extension = "php_gtk2.so"

**PHP does not return to the prompt**

I have to kill with CRTL/C

I have exactly the same behavior if I try to setup a special php.ini file in for exemple /etc/gtk and use this file instead of the normal php.ini for CLI. (I specify this particular file using -c /etc/gtk/php.ini on the command line) 
Click here to see my php.ini file : http://pastebin.com/f47d28358

Does anyone have any idea about what could be causing this problem ?

Thank you very much in advance for your answer.

David V.
Up ...

---

### Post by davidv on 2009-05-11
Hi !

I still have the same problem (please see below).
PHP CLI hangs forever whenever I have the php-gtk2 extension loaded and I try to run a script.

I've just discovered that if php does not return to prompt it's because the php-cli process is stopped on FUTEX_WAIT.

It hangs forever.

I now run Ubuntu 9.4 Jaunty. I tried to uninstall and reinstall php but without success.

Does anyone know a solution for this problem ?

David V.

> **davidv said:**
> Hi everyone !

I'm trying to solve a problem for some days and maybe someone here could help.

I'm running linux ubuntu 8.10 Desktop

I'm working directly on the computer I'm not connected via ssh.
If type echo $DISPLAY I get :0.0

My version of PHP is :
(php --version)
PHP 5.2.6-2ubuntu4 with Suhosin-Patch 0.9.6.2 (cli) (built: Oct 14 2008 20:06:32)
I have a complete LAMP installed on this computer and working perfectly.

I've downloaded and installed the php-gtk2 extension from Bob Majdak Jr PHP-GTK2 blog in my extension folder.
(founded with php -i |grep extension_dir)
Bob's blog : [http://oops.opsat.net/](http://oops.opsat.net/)

I've added a conf file for the php_gtk2 extension in /etc/php5/conf.d
the content of the file is :

# configuration for PHP-GTK2
extension = "php_gtk2.so"

[php-gtk]
php-gtk.codepage = "UTF-8"
php-gtk.extensions = ""

With all theses settings the module is loaded and I can even run an application.

The problem is that at the end of the application php does not return to the prompt. I have to CRTL/C !

If I type in the terminal
php --version

With the **extension not loaded**
#extension = "php_gtk2.so"

PHP **returns normaly to the prompt**

But if I type the same
php --version

With the **extension loaded**
extension = "php_gtk2.so"

**PHP does not return to the prompt**

I have to kill with CRTL/C

I have exactly the same behavior if I try to setup a special php.ini file in for exemple /etc/gtk and use this file instead of the normal php.ini for CLI. (I specify this particular file using -c /etc/gtk/php.ini on the command line) 
Click here to see my php.ini file : http://pastebin.com/f47d28358

Does anyone have any idea about what could be causing this problem ?

Thank you very much in advance for your answer.

David V.

---

### Post by davidv on 2010-07-26
I've finally found the solution.

Thanks to Madeleine on the php-gtk list. ;)

Just go to System/Preference/Assistive Technologies

And un-select "Enable Assistive Technologies"

It now works for me !!! :D

If someone knows why it does not work with Assistive Technologies enabled please report it here.

---

