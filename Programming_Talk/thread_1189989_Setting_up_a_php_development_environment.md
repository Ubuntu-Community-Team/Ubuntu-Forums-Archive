---
title: "Setting up a php development environment"
date: 2009-06-17
forum: Programming Talk
---

### Post by eviltwin on 2009-06-17
I've been trying to set up a development environment for my php development, but I'm not really sure how to deal with permissions etc. I realise that permissions aren't a great worry as the webserver is running on my local machine and iptables prevents anything accessing it other than the loopback address, but I like good practices etc :)

What I'm hoping for is the ability to develop my site in a subfolder of my home directory using git as my version management system, but then to have an easy way to "push" it all to my webserver that is set up on my local machine (or any other machine, should I then have a production site for example).

Any thoughts or input? I'd prefer something that's quite easy to set up, but I'm open to all suggestions.

---

### Post by Mirge on 2009-06-17
I like subversion (svn) for version control... haven't used git.

---

### Post by eviltwin on 2009-06-17
Thanks, but I was more looking for advice about how I would push the changes to the webserver. Version control isn't my real problem.

---

### Post by lykwydchykyn on 2009-06-17
There are three ways to approach this:

 - change the webroot to a folder in your home directory.  Just edit /etc/apache2/sites-available/default and change all instances of "/var/www" to whatever folder you want to use.
 - delete /var/www and make it a symlink to whatever folder you want to use:
```

sudo rm -Rf /var/www
sudo ln -s ~/mywebroot /var/www

```

 - Enable user directories in apache and then put your files in ~/public_html.  Your web content will be at [http://localhost/~username](http://localhost/~username).
```

sudo a2enmod userdirs
sudo /etc/init.d/apache2 restart
mkdir ~/public_html

```

---

### Post by Mirge on 2009-06-17
> **eviltwin said:**
> Thanks, but I was more looking for advice about how I would push the changes to the webserver. Version control isn't my real problem.

Well with SVN I'd create a repository in my /home/user directory, write a quick post-commit script that pushes the changes to the webserver's checkout, as I commit changes in my local checkout. That's what I was getting at.

---

### Post by Reiger on 2009-06-17
> **lykwydchykyn said:**
> There are three ways to approach this:

 - change the webroot to a folder in your home directory.  Just edit /etc/apache2/sites-available/default and change all instances of "/var/www" to whatever folder you want to use.
 - delete /var/www and make it a symlink to whatever folder you want to use:
```

sudo rm -Rf /var/www
sudo ln -s ~/mywebroot /var/www

```

 - Enable user directories in apache and then put your files in ~/public_html.  Your web content will be at [http://localhost/~username](http://localhost/~username).
```

sudo a2enmod userdirs
sudo /etc/init.d/apache2 restart
mkdir ~/public_html

```

And a fourth which is to take ownership of /var/www:
sudo chown $USER:$USER -R /var/www

But IMHO the only right way for this kind of thing is the ~/public_html way using a2enmod userdirs.

---

### Post by eviltwin on 2009-06-17
Ahh yes, the good old ~/public_html folder. I'd forgotten all about that. Thanks for the advice on that one (and nice clear instructions), it's much appreciated :)

Edit: Ok, that was painless to setup. The only problem is that apache still runs as www-data (which I'd like it to, if I'm honest) but that means that the directories which I want to be writeable by it need to be chowned to www-data as well. Is there any way for apache to do a SETUID trick when in someone's public_html dir?

Edit2: Hold that thought. This time google yielded the results for me :) Does anyone know of any security risks introduced by using SUID with public_html?

---

