---
title: "Help with Linux Ubuntu 11.10 Permissions"
date: 2012-02-16
forum: New to Ubuntu
---

### Post by numaquevedo on 2012-02-16
Hello,

I'm new in the forum, I searched for my issue and I didn't find anything. I hope somebody can help me.

I have a dedicated server running ubuntu 11.10 with php and mysql for now. Everything is good, the pages are served well and the connection to the database is good.

The problem comes when I try to generated a zip file for download from my admin area, I can't create neither folders nor files and it's driving me crazy because I don't want to apply 0777 to all the folders and files but I want to be able to generate my files, as well as use the php-gd library which also needs permissions to write.

My username is "aprintink", other than that I have "root" (I read that not everything is root) and the www-data which I suspect is the apache user.

How can I set my permissions to work with "aprintink" and allow "www-data" (if that is the user) to be able to work with files (reading, writing, executing)?

---

### Post by jldoll on 2012-02-16
> **numaquevedo said:**
> Hello,

I'm new in the forum, I searched for my issue and I didn't find anything. I hope somebody can help me.

I have a dedicated server running ubuntu 11.10 with php and mysql for now. Everything is good, the pages are served well and the connection to the database is good.

The problem comes when I try to generated a zip file for download from my admin area, I can't create neither folders nor files and it's driving me crazy because I don't want to apply 0777 to all the folders and files but I want to be able to generate my files, as well as use the php-gd library which also needs permissions to write.

My username is "aprintink", other than that I have "root" (I read that not everything is root) and the www-data which I suspect is the apache user.

How can I set my permissions to work with "aprintink" and allow "www-data" (if that is the user) to be able to work with files (reading, writing, executing)?

I haven't done this before, but maybe some hints to point you in the right direction. In addition to chmod, you can use chown to change ownership. It was unclear if you know who owns the folders you want to write to. $ ls -l will tell you. Once you know the owner and group can you make yourself part of that group? On my system root and www-data are actually groups.

---

### Post by numaquevedo on 2012-02-16
> **jldoll said:**
> I haven't done this before, but maybe some hints to point you in the right direction. In addition to chmod, you can use chown to change ownership. It was unclear if you know who owns the folders you want to write to. $ ls -l will tell you. Once you know the owner and group can you make yourself part of that group? On my system root and www-data are actually groups.

The owner was originally "root", since I read that it's not recommended to have root in everything, I changed to "aprintink" and the group is "root". I have the following questions:

1. Should I create a group apart, or just add aprintink to the group root and set "root" group permissions?

2. What is the apache user in the system if it's not www-data?

I also set permissions to 0777 to the parent folder which is "public_html" but nothing works...

Thanks for your reply.

---

### Post by jldoll on 2012-02-16
> **numaquevedo said:**
> The owner was originally "root", since I read that it's not recommended to have root in everything, I changed to "aprintink" and the group is "root". I have the following questions:

1. Should I create a group apart, or just add aprintink to the group root and set "root" group permissions?

2. What is the apache user in the system if it's not www-data?

I also set permissions to 0777 to the parent folder which is "public_html" but nothing works...

Thanks for your reply.

I did a little searching myself and there seems to be quiet a bit involved that's beyond my knowledge. You might trying doing searches on php apache permissions.  I would go back to original settings. One of the posts stated needing to create the "apache" user and read through the following documentation: [http://httpd.apache.org/docs/2.2/](http://httpd.apache.org/docs/2.2/) You don't want to add yourself to root.

---

### Post by numaquevedo on 2012-02-16
> **jldoll said:**
> I did a little searching myself and there seems to be quiet a bit involved that's beyond my knowledge. You might trying doing searches on php apache permissions.  I would go back to original settings. One of the posts stated needing to create the "apache" user and read through the following documentation: [http://httpd.apache.org/docs/2.2/](http://httpd.apache.org/docs/2.2/) You don't want to add yourself to root.

I just did a research based on what you told me.

My system has "www-data" as a user inside a group of the same name. I changed the ownership of the folder and nothing seems to work. I added 0777 to every file and folder in there and no luck.

I don't know what else I have to do

---

