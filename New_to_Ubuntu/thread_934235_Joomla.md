---
title: "Joomla"
date: 2008-09-30
forum: New to Ubuntu
---

### Post by uppidada on 2008-09-30
In the fifth step of its installation i've been asked for "FTP configuration"

1.What is it actually.... Why is it used for..??
2.Also in final step i get "You are successful" along with
3."PLEASE REMEMBER TO COMPLETELY
REMOVE THE INSTALLATION DIRECTORY.
You will not be able to proceed beyond this point until the installation directory has been removed. This is a security feature of Joomla!."

4.What does that mean... and why do we need to do that.. 

also suggest me any other source or infomation about CMS's...

---

### Post by Paul41 on 2008-09-30
> 3."PLEASE REMEMBER TO COMPLETELY
REMOVE THE INSTALLATION DIRECTORY.
You will not be able to proceed beyond this point until the installation directory has been removed. This is a security feature of Joomla!."

4.What does that mean... and why do we need to do that.. 

You have to delete the instillation directory because if you don't someone could come in later and reconfigure everything without you knowing. That is the directory that stores all the files for the initial setup.

---

### Post by uppidada on 2008-09-30
Q1.THen how does it work later...if i delete installation folder
2.Tell me some other CMS that we have...
Also suggest me surces to gain good knowledge about CMS's....

---

### Post by Paul41 on 2008-09-30
> **uppidada said:**
> Q1.THen how does it work later...if i delete installation folder
2.Tell me some other CMS that we have...
Also suggest me surces to gain good knowledge about CMS's....

You only delete the instillation directory and all other directories stay. These other directories contain the files that make it work after it is installed. The files in the instillation directory are only needed for the initial set up.

Drupal is another popular CMS.
[http://drupal.org/](http://drupal.org/)

Here is a long list of CMS's (I don't know about most of these so I can't comment on them).
[http://en.wikipedia.org/wiki/List_of_content_management_systems](http://en.wikipedia.org/wiki/List_of_content_management_systems)

---

### Post by uppidada on 2008-09-30
Q1.What about FTP configuration...
Why is it used for and how...??

---

### Post by uppidada on 2008-09-30
Thankx for ur concern in helping me....

---

### Post by Nepherte on 2008-09-30
The FTP configuration is necessary to ensure that the extensions/templates you install and the configuration files you save, have the correct owner and group. In earlier versions of Joomla (1.0.x) they sometimes get another owner so you can't change/delete them anymore.

You have to remove the installation directory because, if you don't remove them, someone else could reïnstall joomla without your permission. To prevent this from happening, they ask you to remove it. The installation directory is not needed for Joomla to work anyways.

---

### Post by uppidada on 2008-10-01
Q.In final step as i delete installation directory through terminal,i get this error..
"No configuration file found and no installation code available. Exiting..."

If i don't it says "You cannot proceed until you remove installation directory as a security feature of Joomla.."

What to do with this....

---

### Post by Paul41 on 2008-10-01
> **uppidada said:**
> Q.In final step as i delete installation directory through terminal,i get this error..
"No configuration file found and no installation code available. Exiting..."

If i don't it says "You cannot proceed until you remove installation directory as a security feature of Joomla.."

What to do with this....

Try renaming the configuration.php-dist to configuration.php

---

