---
title: "Ccleaner-like personal data cleaning script under development."
date: 2008-07-21
forum: Programming Talk
---

### Post by reaby on 2008-07-21
To be honest, this is an ad and also an invitation for development of "cleanubuntu" a bash script. 

All started from a posting in Ubuntu-Finland forums, poster asked about substitude of ccleaner for Ubuntu. Therefor as nobody didn't find one, I started project to make one. My programming skills are very, i point, very limited so all what I managed to pull together was few lines of bash script to help him out. As time went by and I readed more advanced bash scripting guide script got more complicated, I managed to add I18N support with gettext. 

More time went by and a courage of a friend I uploaded project to google code and got another developer. Since that, script has gone major changes, all code is now in functions, it has support for command line options and a dialog-based interface if one wishes to use that instead.

So if you are interested in developing or just have thought or idea what script misses post it to google code or contact via email or just reply to this posting.

I encourage to check latest version from svn and test it out and file any bugs you encounter and also test it out. 

project can be found at 
[http://code.google.com/p/cleanubuntu](http://code.google.com/p/cleanubuntu)

---

### Post by LaRoza on 2008-07-21
How can it be made for Linux?

CCleaner overcomes the faults of Windows (registry and such). The only things that can be done here are cleaning browser caches, apt-get clean, and /tmp emptying, unless I am missing something?

---

### Post by rhk on 2008-07-21
> **LaRoza said:**
> 
The only things that can be done here are cleaning browser caches, apt-get clean, and /tmp emptying, unless I am missing something?

And that's exactly what cleanubuntu does.

r

---

### Post by sisco311 on 2008-07-21
> **LaRoza said:**
> How can it be made for Linux?

CCleaner overcomes the faults of Windows (registry and such). The only things that can be done here are cleaning browser caches, apt-get clean, and /tmp emptying, unless I am missing something?
Maybe the config files(from the home directories) of the removed applications.

Anything else?

---

### Post by LaRoza on 2008-07-21
> **sisco311 said:**
> Maybe the config files(from the home directories) of the removed applications.


That is the purpose of that package manager.

The browser cache cleaning is the job of the browser. The cleaning of the apt-cache is the job of apt.

---

### Post by sisco311 on 2008-07-21
> **LaRoza said:**
> That is the purpose of that package manager.

The browser cache cleaning is the job of the browser. The cleaning of the apt-cache is the job of apt.

The package manager doesn't remove the config files from the users home($HOME).
Removing this files is the job of the user.

---

