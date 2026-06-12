---
title: "GnuCash and Xampp conflicts"
date: 2014-02-20
forum: New to Ubuntu
---

### Post by Weedy101 on 2014-02-20
I am new to Ubuntu, and any console based os. I have Ubuntu 12.04 LTS installed and want to migrate all my Windows based work on to Ubuntu a bit at a time.

I have managed to install and configure several packages that I will need, and I had Xampp working fine until I installed GnuCash. This instantly crashed my Xampp and would also not load itself either. I tried uninstalling the GnuCash package but was unable to get the Xampp to run again. So I uninstalled the Xampp package as well, I removed the old Xampp and GnuCash directories that the uninstall left behind and tried doing things in a different order.

To cut this long story short I eventually managed to get the GnuCash installed and working, then Xampp to install but only with the Apache 2 server working. I did this by installing MySql first, (With workbench as I will be needing these two anyway), but I cannot get the MySql server to connect to Xampp, and the proFTPD server will not run either.

This means I can do my accounting, build MySql databases, and Host static web pages. What I need to be able to do is get the MySql and proFTPD servers working with Xampp.

Please remeber I am new to this and still getting used to using the console, plus i don't know which configuration files I need to be editing.

---

### Post by monkeybrain20122 on 2014-02-20
Well I don't know anything about gnucash but a check shows that it has mysql dependencies [http://packages.ubuntu.com/precise/gnucash](http://packages.ubuntu.com/precise/gnucash)

So it has installed mysql packages from the Ubuntu repo (follow the link of libdbd-mysql to see that it has installed mysql-common and mysql-client) So it looks like you have system mysql packages that are incompatible with lampp's (the linux version of xampp is called lampp) In Ubuntu it is easy to set up a real LAMP stack, you don't really need xampp (lampp) which is outdated and doesn't fit very well within the system. It is installed in /opt and has its own libraries, pretty much cut off from the rest of the system and software that requires LAMP features will not use xampp's unless you force it with some hacks. The system versions of these dependencies will be installed and they will be in conflict with xampp's .

Xampp may be useful as a developmental server for Windows, but on Linux it doesn't make a lot of sense.

---

### Post by Weedy101 on 2014-02-20
> **monkeybrain20122 said:**
> Well I don't know anything about gnucash but a check shows that it has mysql dependencies [http://packages.ubuntu.com/precise/gnucash](http://packages.ubuntu.com/precise/gnucash)

So it has installed mysql packages from the Ubuntu repo (follow the link of libdbd-mysql to see that it has installed mysql-common and mysql-client) So it looks like you have system mysql packages that are incompatible with lampp's (the linux version of xampp is called lampp) In Ubuntu it is easy to set up a real LAMP stack, you don't really need xampp (lampp) which is outdated and doesn't fit very well within the system. It is installed in /opt and has its own libraries, pretty much cut off from the rest of the system and software that requires LAMP features will not use xampp's unless you force it with some hacks. The system versions of these dependencies will be installed and they will be in conflict with xampp's .

Xampp may be useful as a developmental server for Windows, but on Linux it doesn't make a lot of sense.

So If 'libdb-mysql' automatically installs 'mysql-common' and 'mysql-client' does that mean that my separate install of 'mysql-server' will also be causing me problems, even if they don't show up at the moment?

Also 'libdb-mysql', the mysql is only a suggested install and not one the package depends on. I have GnuCash set up to use xml files at the moment while I am still sorting things out. Where would I find this library on my file system, and can I disable it or replace this with a file that will link the package to my Mysql server instead?

(As a temporary measure I have just used the Ubuntu Software Center to remove the Mysql add-on which I had not realized was installed with it and GnuCash is still running fine.)

With just a quick read of the info for the apache 2 packages, (On the Ubuntu Packages link you posted that I had not come accross before), it seem's I have a lot more research to do to ensure I install the right one, with the right dependencies. The packages site will be very handy with finding the right 'tools' for work, rest, and play. Thank you.

---

### Post by monkeybrain20122 on 2014-02-20
I would just get rid of xampp and install the ubuntu lamp stack.

---

### Post by tgalati4 on 2014-02-20
Install *tasksel* then run it with *sudo* and select LAMP.  It will take you through a painless installation.  As far as migrating your xampp work, you will have to migrate your mysql tables to the new mysql installation, but you should have those tables/databases backed up anyway.

---

### Post by Weedy101 on 2014-02-21
> **tgalati4 said:**
> Install *tasksel* then run it with *sudo* and select LAMP.  It will take you through a painless installation.  As far as migrating your xampp work, you will have to migrate your mysql tables to the new mysql installation, but you should have those tables/databases backed up anyway.

Thanks I have now installed tasksel and will use it to install LAMPP.

My only concern left with this issue now is the 'libdb-mysql' that GnuCash installed by default. This also installed both the MySql-common and MySql client packages, which I would assume where also installed as part of the MySql server. What is the easiest way dor me to check there are no conflicts waiting to bite me when I least expect it?

---

### Post by tgalati4 on 2014-02-22
It's OK to have multiple versions of shared libraries.  Each application will use the package that it was compiled for.  Of course you will have to do extensive testing to make sure both gnucash and your LAMP installation can coexist in a peaceful manner.

---

### Post by Weedy101 on 2014-02-23
> **tgalati4 said:**
> It's OK to have multiple versions of shared libraries.  Each application will use the package that it was compiled for.  Of course you will have to do extensive testing to make sure both gnucash and your LAMP installation can coexist in a peaceful manner.

Thanks, as a complete noob to any form of unix, testing is going to be a steep learning curve but I enjoy that sort of thing so I'm looking forward to it :KS

Yesterday I came accross the 'man' and 'info' commands listed in one of the many tutorials. If only Ubuntu had a first run spalsh screen telling you about them it would make getting started much easier. Still I now have access to this resource.

Thanks all that have helped me with this problem, your help is much appreciated.=d>

---

