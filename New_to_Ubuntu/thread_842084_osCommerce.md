---
title: "osCommerce"
date: 2008-06-27
forum: New to Ubuntu
---

### Post by ub007 on 2008-06-27
Hi,

I wish to install an ecommerce software (eg..osCommerce)onto my  ubuntu server.Could anyone walk me through the steps...

What are the commands to download the software from the website,unzip and then configure it....I may be asking a lot in one post,sorry about that...I'm new to linux and not familiar with the command line...

Cheers,
David

---

### Post by fatality_uk on 2008-06-27
This page may help.
[http://www.websitesource.com/oscommerce/get-started.shtml](http://www.websitesource.com/oscommerce/get-started.shtml)

---

### Post by zacktu on 2008-08-04
The website at oscommerce.com lets you download the entire package as a zip file.  I don't think that I have installed anything extra, but in any event clicking on the zip file wherever it happens to be will result in a new directory called oscommerce-2.2rc2a.  There is no further compression, so you're ready to go.  

Within the oscommerce-2.2rc2a you will find a folder containing all of the files necessary for the installation.  The installation instructions are in the first 10 or so pages of *documentation.pdf*.  Everything that's needed for your store is in the folder called *catalog*.

Before you begin the installation you need to create a MySql database.  You can use any name you want.  My suggestion is that you create at least one store and plan to throw it away.  For example, you might name the database *mystore01* and not worry about a password for root.  Installation is so easy that you can start again with no problem.

This gets to a bigger issue, though.  Do you already have an Apache server, MySql database server, and phpmyadmin installed?  If not, you'll need to install them.  I use xampp because everything you need to install and run oscommerce is in one download.  From what I've read, xampp isn't secure for a public server.  I use my own computer only for development, so that's not an issue.  The ubuntu forum has lots of threads about servers.  By the way, many hosting sites include oscommerce and all the other tools necessary for you to support a store.  You can work on the store's appearance, shipping costs, etc. locally and then upload them to the hosting site.

zacktu

---

