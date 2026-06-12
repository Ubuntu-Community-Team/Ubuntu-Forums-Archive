---
title: "apache2"
date: 2008-06-19
forum: New to Ubuntu
---

### Post by ub007 on 2008-06-19
Hi,

I installed the LAMP server using

'sudo apt-get install apache2 php5-mysql libapache2-mod-php5 mysql-server'

Now it says you can browse to your website by pointing your browser at [http://localhost/](http://localhost/).

All I have is a command line,how do i access a browser and point that to the local host?In other words how do i test the apache2 server from the same machine?

Cheers,
David

---

### Post by sisco311 on 2008-06-19
w3m is a text based web browser and I think is installed by default:
```
w3m http://localhost/
```

You also can install links, links2 and elinks from the repos:
```
sudo aptitude install links links2 elinks
```

---

### Post by ub007 on 2008-06-19
Thanks sisco,

I type in 'w3m [http://localhost](http://localhost)' and it displays
"It works!".

How can i add more content?
this is what i could find from googling-Your website information is stored in /var/www .Now, you can open up a file manager (from Places > Home Folder) and then navigate to /var/www. Simply place your HTML or PHP files in this folder and they will work as your website.

How can i do that stuff from the command line?

---

### Post by Cypher on 2008-06-19
```

cd /var/www
ls -l

```
You will see the index.html file there that printed "It works!". You can create additional files here..

Though, for your own testing purposes you might find it easier to enable the UserDir option and keep all the files in your home directory. To do that
```

sudo a2enmod userdir
sudo /etc/init.d/apache2 restart
cd ~
mkdir public_html

```
Now create all of your HTML/PHP files in the public_html directory, a simple test to ensure PHP is working might be
```

cd public_html
echo "<? phpinfo(); ?>" > index.php

```
Now point your browser to http://localhost/~<username>, where <username> is whatever you use to login.

---

### Post by stump138 on 2008-06-19
If you simply want to copy all the .html and .php folder from your home directory to the /var/www you can use "cp"

```

sudo cp /home/*.php /var/www
sudo cp /home/*.html /var/www

```

---

### Post by Dedoimedo on 2008-06-19
Hello,

I won't go into details regarding the setup of Apache server unless specifically asked, but here are some tips for you that might get you started:

1. Adding content is simple. Just create new HTML documents, images etc and place them in DocumentRoot.

DocumentRoot is the directory that Apache uses as its default directory and it's /var/html/www.

This directive is set by editing the Apache main configuration file /etc/httpd/httpd.conf.

2. I don't know how familiar you are with the server, but if you intend to make it available over the Internet, please consider the following:

A. You should run it in Chroot Jail - do ask if you need help.

B. You should not allow users to display the directory Index or access any directory outside the html directory.

This is done by configuring a number of directives in the httpd.conf file.

Disable access to root

<Directory />
Order allow, deny
Deny from All
</Directory>

C. For the html directory, you should carefully consider if you want to allow users to list directory index, to execute scripts or anything else.

This is governed by the Options directive. For instance:

Options Indexes FollowSymLinks

This allow you to list directory contents and follow symbolic links.

D. You might want to consider using VirtualHost directive, as it allows you greater flexibility over content, as well as the ability to host several websites from the same IP address.

Lastly, to make it work as needed, you will have to use either the hosts file or the DNS, and for external (Internet) access, only DNS will work.

That's it for now ... ask more if you need.

Cheers,
Dedoimedo

---

### Post by ub007 on 2008-06-19
Thank you guys.

At the moment,I've got 3 machines,I installed one of them as my server(ubuntu-thats where the LAMP is runnin),got nother machine runnin windows and may install ubuntu on the 3rd one.

what i intend to do is access the apache2 server from my 2 clients(sort of set up a mini LAN)....i've done similar stuff on windows,built a java web server,stored html n images in the same dir and i could access it from another system.

but since i'm on a ubuntu server,(havent installed the GUI)i do not have an idea on adding the HTML documents, images etc and placing them in DocumentRoot from a command line.

guess i look totally stupid asking that....but mayb thats the only way to learn.Sorry for the silly questions..

Cheers

---

