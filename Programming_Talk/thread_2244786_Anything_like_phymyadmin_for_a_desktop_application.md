---
title: "Anything like phymyadmin for a desktop application"
date: 2014-09-18
forum: Programming Talk
---

### Post by PopsTheSailor on 2014-09-18
I'm looking for something easy to use for creating a couple of forms and less than a dozen macros against a mysql database. I don't want it to be a web based application or to use web based (browser) technology. It needs to sit on a Linux box with no browsers installed and not connectivity to the internet. It looks like phpmyadmin is centered around browsers. Is there anything available where I don't have to learn an actual programming language like Python or PHP?

---

### Post by SeijiSensei on 2014-09-18
LibreOffice includes a program called Base which is a desktop-oriented DBMS system like Microsoft Access.  It comes with most flavors of Ubuntu and connect to MySQL databases.

---

### Post by PopsTheSailor on 2014-09-18
I've tried Base and Kexi and both are buggy. I just tried them again tonight and the version I have wouldn't even let me save a table. Not worth the effort.

---

### Post by SeijiSensei on 2014-09-19
You won't like my next suggestion I suspect -- Microsoft Access.  You can connect to MySQL with its ODBC driver.

I'm afraid I'm not much help beyond that.  I write database applications in PHP because the browser provides a convenient platform-independent user interface.

---

### Post by PopsTheSailor on 2014-09-19
LOL. Yes. I've been using it for years and like many that use Linux, am looking to get away from it. I'm not so stuck on my passion to get completely away from them, it's more of a PITA thing. I either have to dual boot, load some type of vm software like VirtualBox or try and get it to run in wine. I'd just prefer to hang on on Ubuntu. I may just put the effort into working around the bugs in Kexi / Base. 

BTW, does anyone know the difference between Kexi and Base or are the really the same thing? I haven't compared them close enough to even know.

---

### Post by SeijiSensei on 2014-09-19
I've run Access 2007 in Wine.  The [WineHQ page for Access]("https://appdb.winehq.org/objectManager.php?sClass=application&iId=12") gives "bronze" status to both 2007 and 2010.  Usually I run Win7 in a VirtualBox if I need Access. 

I don't think Kexi and Base are related.  The former is a KDE application, while the latter is part of LibreOffice.  I haven't tried Kexi, though I just downloaded a copy out of curiosity.  Like you, I've found Base pretty clunky the couple of times I've tried it.  I've only really used it to upload data from spreadsheets to a remote PostgreSQL server and maybe run a few queries.

---

### Post by PopsTheSailor on 2014-09-19
How funny. I thought Kexi and Base were closely related and somehow went the Kexi route. I just opened a Base db and I'm going to try that. The are different. So far so good. I'm going to really give Base a try.

---

