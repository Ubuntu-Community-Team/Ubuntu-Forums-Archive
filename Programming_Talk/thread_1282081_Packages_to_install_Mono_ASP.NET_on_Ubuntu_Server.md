---
title: "Packages to install Mono ASP.NET on Ubuntu Server"
date: 2009-10-03
forum: Programming Talk
---

### Post by phrostbyte on 2009-10-03
Anyone know the list of packages needed run ASP.NET on Ubuntu Server? Karmic or Jaunty.

Edit: could be the wrong forum to ask this question

---

### Post by directhex on 2009-10-04
> **phrostbyte said:**
> Anyone know the list of packages needed run ASP.NET on Ubuntu Server? Karmic or Jaunty.

Edit: could be the wrong forum to ask this question

With or without a generalized web server in front?

---

### Post by phrostbyte on 2009-10-05
With a generalized web server.

I don't know if you remember but I suggested once that Ubuntu come with a ASP.NET server install option.

So I did some research on how to do this. I want to write a tasksel profile for ASP.NET so you can do:

sudo tasksel install aspnet

And you're server is prepared for ASP.NET serving. :P

---

### Post by directhex on 2009-10-06
> **phrostbyte said:**
> With a generalized web server.

I don't know if you remember but I suggested once that Ubuntu come with a ASP.NET server install option.

So I did some research on how to do this. I want to write a tasksel profile for ASP.NET so you can do:

sudo tasksel install aspnet

And you're server is prepared for ASP.NET serving. :P

Okay.

Karmic, ASP.NET 2.0:
libapache2-mod-mono
apache2

Karmic, ASP.NET 1.1:
libapache2-mod-mono
apache2
mono-apache-server1

Jaunty, ASP.NET 2.0:
libapache2-mod-mono
apache2
mono-apache-server2

Jaunty, ASP.NET 1.1:
libapache2-mod-mono
apache2

You may have guessed that the default was changed from ASP.NET 1.1 to 2.0

Also, because it's so rarely written down, a quick HOWTO:

You can use mod_mono in two ways - Auto, or regular. Auto will process whatever's in /var/www in a "dumb" way using the default ASP.NET parser (so 2.0 in Karmic, 1.1 in Jaunty). Regular does the whole "webapp" thing where you define a folder as a "webapp" folder. To pick which of the two to use, either a2enmod the "mod_mono" or "mod_mono_auto" modules.

To use mod_mono, use the "mono-server{2}-admin" command to generate a webapp file, and "mono-server{2}-update" to roll all your webapp files into your apache configuration.

e.g.:

aptitude install libapache2-mod-mono apache2
mono-server2-admin add --path=/real/path --app=/application
mono-server2-update
a2enmod mod_mono
service apache2 restart
wget [http://localhost/application/index.aspx](http://localhost/application/index.aspx)

---

