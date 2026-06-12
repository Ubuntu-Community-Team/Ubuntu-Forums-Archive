---
title: "Permissions..."
date: 2012-03-15
forum: New to Ubuntu
---

### Post by meduser on 2012-03-15
I have Kubuntu 11.10 running on my pc. I am writing a web page, from scratch using php/mysql/ajax/ javascript/ css, etc, etc..

I have successfully installed apache, Mysql, PHP, etc.

The issue I am having is the directory used to loading pages is the www directory in the var directory.


I want to do one of 2 things here. I either need to give myself permissions to be able to write to the /var/www directory, or moving the www directory to ,say, to my dropbox. I would prefer to move it to my dropbox, that way I can access the files from school. I don't know where the documentation is for the www folder, to be able to change the directories location for things to work right. Any help is extremely appreciated, as right now, I am moving the folders, file by file through the terminal as root....needless to say it is a long and frustrating procedure.


Thanks in advance.

---

### Post by matt_symes on 2012-03-15
Hi

> I want to do one of 2 things here. I either need to give myself permissions to be able to write to the /var/www directory

Make yourself a member of the group www-data. Make sure www-data has group read, write access to /var/www

> , or moving the www directory to ,say, to my dropbox. 

Create a symbolic link (/var/www) to your dropbox folder.

Kind regards

---

### Post by meduser on 2012-03-15
> **matt_symes said:**
> Hi



Make yourself a member of the group www-data. Make sure www-data has group read, write access to /var/www



Create a symbolic link (/var/www) to your dropbox folder.

Kind regards

Thanks so much..I created the symbolic links and all is great. Thanks again.

---

