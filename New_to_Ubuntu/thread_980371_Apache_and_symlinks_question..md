---
title: "Apache and symlinks question."
date: 2008-11-12
forum: New to Ubuntu
---

### Post by Ikith on 2008-11-12
I'm curious as to if this will work. I create a new user and give him the default home directory of /home/sam well I have a webserver set up so I want sam to be able to put pages onto it easily without having to create a new user that has a home in /var/www so I create a directory in Sam's home folder called web and have a symlink in the apache folder called sampub which points to web in sam's home folder. 

Will apache 404 or traverse the symlink to find the files?

---

### Post by bodhi.zazen on 2008-11-12
There is a (nice) wiki page here :

[https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

---

### Post by spiderbatdad on 2008-11-12
> **Ikith said:**
> I'm curious as to if this will work. I create a new user and give him the default home directory of /home/sam well I have a webserver set up so I want sam to be able to put pages onto it easily without having to create a new user that has a home in /var/www so I create a directory in Sam's home folder called web and have a symlink in the apache folder called sampub which points to web in sam's home folder. 

Will apache 404 or traverse the symlink to find the files?

Check out [http://www.solitude.dk/filethingie/](http://www.solitude.dk/filethingie/)

If you have php installed, the above app can be placed in /var/www/sam or where ever in your server directories. It has a good php uploader script and per directory authentication, etc. It is really just a file you add/edit/configure to your liking...can be renamed to index.php in a directory, then it will display the file manager whenever that diretory is entered.

---

