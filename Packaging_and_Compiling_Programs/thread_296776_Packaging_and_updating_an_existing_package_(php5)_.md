---
title: "Packaging and updating an existing package (php5) for a local use"
date: 2006-11-10
forum: Packaging and Compiling Programs
---

### Post by chicha on 2006-11-10
Hello !

I need you experience, please, to help me make the good choices while updating an existing package.

Here is the whole story :

I am running Kubuntu Edgy on a Intel P4 machine.
I am developing a website using Lighttpd and PHP5.

I need to use tidy with my php5-cgi installation.
Unfortunatly tidy is not activated in Ubuntu Edgy's PHP5 package.
A bug is already tracking this :

[https://launchpad.net/distros/ubuntu/+source/php5/+bug/38510](https://launchpad.net/distros/ubuntu/+source/php5/+bug/38510)

The only solution proposed in the bug report is to recompile php5 with the --with-tidy option until a new package is delivered.

An other solution has been proposed in the following thread :
 
[http://ubuntuforums.org/showthread.php?t=195636&highlight=php5+tidy](http://ubuntuforums.org/showthread.php?t=195636&highlight=php5+tidy)

The solution in this thread is to build tidy beside the php5 install and activate the module in the php.ini.

I prefered the first solution, ie rebuild the php5-cgi with the tidy support activated. I always prefere to use the packaging system instead of compiling and installing things that the package manager will not know about ...

I followed [the beautiful new manual]("https://help.ubuntu.com/6.10/ubuntu/packagingguide/C/index.html") (thank you to the doc team for their great job by the way).

I modified the package, added the --with-tidy in the configure section of the control file ... 
**...and here come my questions :**

Should I modify the changelog for a local use ? If so, which new version should I use so that it does not interfere with an eventual update (security, new package, etc.) .

The package is php5-5.1.6-1ubuntu2.1
I tried 2 things :

1- I did not changed the changelog and kept the same version. The build with pbuilder was fine, and so was the installation. The problem is that after my installation with dpkg Adept Notifier wanted to update my php5-cgi installation with Ubuntu's package, like if the package I just installed was older than Ubuntu's one ! Any Idea about this issue ?

2- I changed the changelog and used a new version : php5-5.1.6-1ubuntu2.1.1, thinking that this will not interfere with an hypothetic Ubuntu update. And every thing went fine : Adept Notifier did not complaine anymore !!! The only thing is that this version number is not compliant with Debian policies like Lindian just told me ... is it a real problem ?

What is the best version number to choose when you mofify a package for a local installation and that you do not want to interfer with future update of this package ?

Thank you for your help ... and sorry for this long message !!!
Cheers,

Chicha

---

