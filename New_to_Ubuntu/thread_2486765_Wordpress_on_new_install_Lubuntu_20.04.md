---
title: "Wordpress on new install Lubuntu 20.04"
date: 2023-05-09
forum: New to Ubuntu
---

### Post by mnduck on 2023-05-09
In general up and running but I have questions mainly about setting permissions.

This is for a local install of Wordpress on  an old laptop it should never be exposed to the net.

1, I installed the Lampp server and phpmyadmin and they are running.
2, I downloaded the latest .tar.gzip of WordPress it's in Downloads.
3, I can log in to phpmyadmin as 'phpmyadmin@localhost'/'mypassword'

I don't have permissions to create a database so that needs correcting. 

I need to extract wordpress into the var/www/'my website' directory, create a database and run the WordPress install.

So what do I need to do to make this happen?  

Particularly creating a database user with the correct permissions, creating the database and granting the correct permissions to the extracted wordpress.

If you could post a link to a suitable HowTo I'd very much appreciate  it.

Thanks All   mnduck

---

### Post by yancek on 2023-05-10
I don't know if you have extracted the tar file yet but if not, the site at the link below explains various methods.

[https://linuxize.com/post/how-to-extract-unzip-tar-gz-file/](https://linuxize.com/post/how-to-extract-unzip-tar-gz-file/)

You need root (sudo) to access the /var/www directory.

There are quite a number of tutorials online explaining this including at the ubuntu.com site at the link below.

[https://ubuntu.com/tutorials/install-and-configure-wordpress#1-overview](https://ubuntu.com/tutorials/install-and-configure-wordpress#1-overview)

I've never installed it myself so can't give any more details.

---

### Post by mnduck on 2023-05-10
Still working on it.
If I type localhost/my website into Firefox I get the content of WP's index.php but no action.
I have tried and totally failed to update the Apache config file, sudo nano and moving it prior to editing.
I have the database now and a user with the correct rights but even so I'd still appreciate some help.

Atb.  Mnduck

---

### Post by yancek on 2023-05-11
The 2nd link I posted above seems pretty detailed.  At what point are you having problems?  

>  If I type localhost/my website into Firefox I get the content of WP's index.php but no action.

I would expect that behavior.  Did you compare your change in Apache to the one in the web site tutorial?  Are you now able to access the database?  Sorry, can't really help as I've not used WordPress.

---

### Post by mnduck on 2023-05-11
The link seems to have a flaw, one of the steps returns a syntax error.

---

### Post by yancek on 2023-05-12
If you still need help, you should post which step is the problem and what the specific error is.

---

### Post by ActionParsnip on 2023-05-13
Why phpmyadmin? Why install that?

---

