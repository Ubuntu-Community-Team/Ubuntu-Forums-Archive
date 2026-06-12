---
title: "Development Local Webserver"
date: 2008-11-13
forum: New to Ubuntu
---

### Post by strininaidu on 2008-11-13
Hi

i am totally new to this. I managed to install ubuntu 8.10 and install LAMP components as per instructions from a thread in the forum. my problem lies with Apache. When i try to create or copy folders to /var/www, I get a permissions issue: Access is Denied. How can i resolve this.

My aim is to create a local dev server to test my new found dev skills. Please help
Strini

---

### Post by beno1990 on 2008-11-13
Start all terminal commands to copy files to /var/www with "sudo" and then enter the sudo password when it prompts you. Example:

```

sudo mv directoryname /var/www

```

---

### Post by beercz on 2008-11-13
Another way is to create an alias.

Create a directory in you home directory that will create the site (e.g. mysite) and copy your site files into this directory.

In terminal type:

> sudo gedit /etc/apache2/conf.d/alias

Copy and paste the following at the end of the file (even is the file is blank, copy and paste the following text into it).  Substitute your name into for username and the directory you created for mysite:

> Alias /mysite /home/username/mysite/
<Directory /home/username/mysite/>
  Options Indexes FollowSymLinks
  AllowOverride All
  Order allow,deny
  Allow from all
</Directory>

Save and quit the text editor.

Restart the apache webserver:

> sudo /etc/init.d/apache2 restart

Quit terminal and start firefox.

To see your site type:

> [http://localhost/mysite](http://localhost/mysite)

In the firefox address bar, substituting mysite with your directory name, and you should now see your test site.

The advantage here is that if you directory edit your site files in the directory you created, you can see the results of your edits immediately by pressing the Reload button on the firefox toolbar.  You don't need to copy files to another directory using super user privileges (ie without using sudo)

You can test an number of sites this way by adding more Aliases in the alias file and creating the appropriate directories for different test sites.  For each Alias change the directory name and alias name (i.e. change mysite in the above example).

hth

---

### Post by superprash2003 on 2008-11-13
or another easy way is to change your documentroot from /var/www to /home/yourubuntuusername/www ..obviously replace yourubuntuusername with your ubuntu username, this should easily eliminate those permission errors.. follow step 4 from this link [http://prash-babu.blogspot.com/2008/05/how-to-install-apache-and-setup.html](http://prash-babu.blogspot.com/2008/05/how-to-install-apache-and-setup.html)

---

