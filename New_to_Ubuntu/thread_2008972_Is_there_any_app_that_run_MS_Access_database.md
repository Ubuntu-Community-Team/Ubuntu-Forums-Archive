---
title: "Is there any app that run MS Access database?"
date: 2012-06-23
forum: New to Ubuntu
---

### Post by Houmie on 2012-06-23
LibreOffice seems to not have any equivalent to MS Access, right?

What are my options?

Thank you,
Houman

---

### Post by oldfred on 2012-06-23
Nothing that is the integration and complete query, view, & report capability.

You can use the lightweight sqlite database in base or link to other sql databases. I have tried kexi and it is ok for some things. I have just converted Access tables to .csv and imported them into another database or use MDB viewer to do some of the work.

Databases:
[http://www.wikivs.com/wiki/MySQL_vs_PostgreSQL](http://www.wikivs.com/wiki/MySQL_vs_PostgreSQL)
LibreOffice/OpenOffice database
MDB Viewer
Glom - design is loosely based on FileMaker Pro
[http://www.glom.org/wiki/index.php?title=Main_Page](http://www.glom.org/wiki/index.php?title=Main_Page)
Dabo is designed to create database-centric apps
[http://dabodev.com/](http://dabodev.com/)
[http://www.kexi-project.org/](http://www.kexi-project.org/)
[http://www.koffice.org/kexi/](http://www.koffice.org/kexi/)
[http://www.knoda.org/](http://www.knoda.org/)
[http://www.gnome-db.org/](http://www.gnome-db.org/)
[http://www.0d.be/projects/gaby/](http://www.0d.be/projects/gaby/)
Microsoft Access in Wine - some success
[http://ubuntuforums.org/showthread.php?t=1113065](http://ubuntuforums.org/showthread.php?t=1113065)
[http://wiki.winehq.org/FAQ](http://wiki.winehq.org/FAQ)
front end for MySQL or PostgreSQL
[http://www.vfront.org/](http://www.vfront.org/)

If you just want something simple for collections as an example.
Collections - music, books, etc: both in repositories
Tellico - qt4 & python, xml for data
[http://tellico-project.org/](http://tellico-project.org/)
Gcstar - perl & gtk, xml for data
[http://www.gcstar.org/](http://www.gcstar.org/)

---

### Post by Houmie on 2012-06-23
Thank you for the comprehensive list :)

---

### Post by Zill on 2012-06-24
> **Houmie said:**
> LibreOffice seems to not have any equivalent to MS Access, right?...
LibreOffice *does* have a database component similar to MS Access...

[libreoffice-base]("http://www.libreoffice.org/features/base/")

```
sudo apt-get install libreoffice-base
```

---

### Post by Houmie on 2012-06-24
> **Zill said:**
> LibreOffice *does* have a database component similar to MS Access...

[libreoffice-base]("http://www.libreoffice.org/features/base/")

```
sudo apt-get install libreoffice-base
```

Thanks I tried Base, but it couldn't open it.
I found Kexi and it was at least ablt to open the data and structure. Even though the forms weren't possible. At least something :)

---

