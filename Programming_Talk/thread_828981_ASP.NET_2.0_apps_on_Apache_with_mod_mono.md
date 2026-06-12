---
title: "ASP.NET 2.0 apps on Apache with mod_mono?"
date: 2008-06-14
forum: Programming Talk
---

### Post by rogier.de.groot on 2008-06-14
Hi all,
I've posted this same question on the server forum, but as nobody has answered me so far, I'll ask again here:
How do I configure apache2+mod_mono to serve asp.net 2.0 web apps / services? I can't get it to work, even using the newer mono packages from badgerports. It just keeps trying to open my aspx files instead of executing them:(
Anybody got this working?

---

### Post by reality1011 on 2008-06-15
Im still working on this myself.. I have the samples working, if you aren't there yet then definitely get those working first...

I also added a directory to the samples and the index2.aspx file saw the new directory (containing my aspx files) but it did not like them...

---

### Post by Amit Yaron on 2008-06-15
I hope you will find the following link useful: [http://mono-project.com/Mod_mono]("http://mono-project.com/Mod_mono")

In httpd.conf, you should add a Location tag with the directive 'SetHandler mono' to notify apache that the mono module handles ASPX pages.

---

