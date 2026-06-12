---
title: "Created debian package is ignored some dependencies"
date: 2009-04-15
forum: Packaging and Compiling Programs
---

### Post by explosive on 2009-04-15
Hi,

I've just made my first .deb package of a python program that I have written but run into a problem. The program has a number of dependencies including two python modules. I tested the debian package and it resolved all the dependencies apart from the two python modules - it did not offer to install them at all! 

The modules in questions are: python-pyinotify and python-mysqldb.

My control file is as follows:

```

Package: loganalyser
Architecture: any
Pre-Depends: php5 (>= 5.2) | python (>= 2.5) | apache2 (>= 2.2) 
Depends: php5-mysql (>= 5.2) | php5-gd (>= 5.2) | libapache2-mod-php5 (>= 5.2) | mysql-server (>= 5) | python-pyinotify (= 0.7.1) | python-mysqldb (>= 1.2)
Description: An extensible log file analyser.
 An extensible log file analyser that monitors log files in real time, alerting the administrator to events of interest.

```

Any ideas what is going wrong?

---

### Post by explosive on 2009-04-16
My bad - I Should be using , rather than | in the package requirements.

---

