---
title: "Installing LAMP on a desktop system"
date: 2010-05-18
forum: Outdated Tutorials &amp; Tips
---

### Post by phillw on 2010-05-18
There are many, many "How To's" on the web telling you to sudo apt-get this and sudo apt-get that... Well, it doesn't have to be that way and it isn't.

As of 9.10 the **correct** way to put on a LAMP server is as follows```
sudo tasksel
```
Arrow down to LAMP, press the space bar to put an * in the box, press the tab bar to get to <OK> and press enter. Then do as it says & make a note of your MySQL root password

Then, go into System --> Administration --> Synaptic Package Manager
Type in phpmyadmin in the search window, right click on the little box to the left of phpmyadmin in the results area, select install, then click on 'Apply'. Do as it says. (Obviously, when asked, tell it you are using Apache).

Then reboot. You now have a full LAMP installation with PhpMyAdmin on it - all configured up.

_**A few changes with 10.04 LAMP**_

With the advent of 10.04 there are a few changes from 9.10 and before that are quite important.

MagicQuotes are now OFF :-)

Error reporting is now disabled. This is important as error reporting can give hints to hackers about your system.

If you are a writing php and need error reporting on for development work, they now ship some further information on it.

```
/etc/php5/apache2/php.ini
``` has the current file (production) for configuring up the php security and has comments as to what is turned on and off between 'production' and 'development'.

As the development people are really nice people, they have made things even easier and ship both the production and development versions over at ```
/usr/share/doc/php5-common/examples
```

Simply copy over the one you need from there over to ```
/etc/php5/apache2/php.ini
```

To switch TO development security 
```
 sudo cp /usr/share/doc/php5-common/examples/php.ini-development /etc/php5/apache2/php.ini
``` 
[list]If you find a lot of "Variable Undefined Notices" this is because whilst php can deal with undeclared variables, it is warning you of a possible problem. It is best to get into the habit of declaring variables and arrays before you first use them as if you ever want to consider Java, C++ etc. in the future you will have to declare them. If you are not sure what variables are declared as you go from module to module then ```
if (!isset($YourVariable)) $YourVariable='';
``` will test a variable and only set it if it does not have a value. 

If you **do** need to turn off 'Notice' reporting:```

sudo gedit /etc/php5/apache2/php.ini
```Look for the line that reads ```
error_reporting = E_ALL | E_STRICT
``` and alter it to```
error_reporting = E_ALL | E_STRICT & ~E_NOTICE
``` Then save the file and exit. [/list]

To switch BACK to production security
```
 sudo cp /usr/share/doc/php5-common/examples/php.ini-production /etc/php5/apache2/php.ini
```

In each case, you need to restart the apache server
```
sudo /etc/init.d/apache2 restart 
```

Regards,

Phill.

---

### Post by specialk1st on 2010-05-29
Thank you for this.  Very helpful, especially the changes for 10.04 Lucid Lynx.

---

