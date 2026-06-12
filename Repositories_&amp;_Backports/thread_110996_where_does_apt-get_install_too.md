---
title: "where does apt-get install too"
date: 2006-01-01
forum: Repositories &amp; Backports
---

### Post by Defluo on 2006-01-01
Ok, ive been trying to install apache2.2.0, php5.1.1, and mysql standard5.0.18 and i have been having some problems, nothing major

well i decided to see if I could get something to work using apt-get and I dont know where the things are installed to, whats the directory path? I see that its installed, synaptic tells me its there, it is supposedly running, but I cant find it.

Where should I be looking.

Thankyou

---

### Post by encompass on 2006-01-01
No problem, there are a few nifty command to help you out in finding things...
whereis finds binaries...
whereis  -  locate the binary, source, and manual page files for a command
locate - finds any file or diresctory with the name you entered.

There are probably many others.

You can also look at the properties of the packages them selve in synaptic.  But why would you need to know where they are when you are using synaptic to do the installs?

---

### Post by az on 2006-01-01
[QUOTE=Defluo]I see that its installed, synaptic tells me its there, it is supposedly running, but I cant find it.

Where should I be looking.

Thankyou[/QUOTE]
You can always right-lick on a package in synaptic and look at the list of installed files.

Apache has no frontend.  It is a service.  You configure it through the a2* commands and through the configuration files.  Anything you drop in the configured directory will be served (/var/www)

There is no apache application that you run that gives you a dialogue box to configure it.   Generally, a server will not even have x-windows installed (the graphical layer)

---

### Post by Defluo on 2006-01-01
I was meaning in general, is there an easy way to figure out where anything is installed.

I installed apache manually, and its working like a champ. Im used to things like that being someplace like /usr/local but its not there when i install it through synaptic

---

### Post by encompass on 2006-01-01
there are set places for everything.  try the commands I told you... they will help you alot.

---

