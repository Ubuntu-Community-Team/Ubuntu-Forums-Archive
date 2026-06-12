---
title: "View PHP files locally"
date: 2009-05-24
forum: Programming Talk
---

### Post by rob1101 on 2009-05-24
I am starting to develop a few websites again in my spare time and am looking for an easy way to view .php files locally instead of renaming them or uploading them to the server every 2 min. Any help?

---

### Post by ibutho on 2009-05-24
One solution would be to setup a php enabled webserver on your computer.

---

### Post by ianhaycox on 2009-05-24
Quick start:

```
$ sudo apt-get install apache2 libapache2-mod-php5

```

Browse to [http://localhost/](http://localhost/) you should get an It Works message.
To avoid the hassle of permissions etc.

```
$ mkdir ~/public_html
$ sudo a2enmod userdir
$ sudo /etc/init.d/apache2 restart
```

Create a simple .php file in ~/public_html and browse to [http://localhost/~your-username](http://localhost/~your-username) and it should display OK.

---

### Post by Reiger on 2009-05-24
If you have SSH access to the server you could simply do a cat /my/file.php on it over SSH. Also, a very simple thing you could do is write a little script like this:

[php]
<html><head>
<title><?php echo "Source of `{$_GET['file']}'"; ?></title>
</head><body>
<?
$toHighlight = $_GET['file'];
highlight_file($toHighlight);
?>
</body></html>
[/php]

Gives you a HTML page with syntax highlighted source of a file specified in the Query string, like: url/page.php**?file=somefile.php**.

---

### Post by rob1101 on 2009-05-24
> **ianhaycox said:**
> Quick start:

```
$ sudo apt-get install apache2 libapache2-mod-php5

```Browse to [http://localhost/](http://localhost/) you should get an It Works message.
To avoid the hassle of permissions etc.

```
$ mkdir ~/public_html
$ sudo a2enmod userdir
$ sudo /etc/init.d/apache2 restart
```Create a simple .php file in ~/public_html and browse to [http://localhost/~your-username]("http://localhost/%7Eyour-username") and it should display OK.


That works but is it possible to make that directory think it is the root directory? Because all of my style sheets and links are based off of this, for instance /style/main.css obviously will not be the correct path locally but it will be once I upload it. I think I have done it before but I cannot remember remotely how I did it.

---

### Post by ianhaycox on 2009-05-24
Easy way,

If you copy your files to /var/www then / is as you expect.

You can either use sudo to copy your files into /var/www or make yourself a member of the www-data group so you have write permissions. 

There might be smarter ways with a site alias ? or virtual sites ? but apache configuration is not my forte. Maybe someone else can help or surf the web.

---

### Post by rob1101 on 2009-05-24
> **ianhaycox said:**
> Easy way,

If you copy your files to /var/www then / is as you expect.

You can either use sudo to copy your files into /var/www or make yourself a member of the www-data group so you have write permissions. 

There might be smarter ways with a site alias ? or virtual sites ? but apache configuration is not my forte. Maybe someone else can help or surf the web.

That didn't work for me at all it still just ask for me to download the .php files and I don't think I have a www-data group.

---

### Post by ianhaycox on 2009-05-25
Are you saying that when your PHP files were in ~/public_html they were processed correctly, but in /var/www you are asked to download them ?

Anyway, in either case check that you have php5.conf and php5.load in /etc/apache2/mods-enabled/ (They are links from ../mods-available).

Restart apache once the php5 mods are available. Hell, restart anyway.

You should have a group www-data. Look in /etc/group. In a default installation /var/www is owned by www-data. Check ls -la /var/www

---

### Post by rob1101 on 2009-05-25
> **ianhaycox said:**
> Are you saying that when your PHP files were in ~/public_html they were processed correctly, but in /var/www you are asked to download them ?

Yes

> **ianhaycox said:**
> 
Anyway, in either case check that you have php5.conf and php5.load in /etc/apache2/mods-enabled/ (They are links from ../mods-available).

yes they are both there

> **ianhaycox said:**
> 
Restart apache once the php5 mods are available. Hell, restart anyway.

Do you mean restart my computer or apache or what? I shut my computer down last night so I guess its been restarted since I installed everything. 

> **ianhaycox said:**
> 
You should have a group www-data. Look in /etc/group. In a default installation /var/www is owned by www-data. Check ls -la /var/www
How do I look in /etc/group? Its not a directory.

---

### Post by hessiess on 2009-05-25
Make sure you browse to the directory, not doubble cklic on the file.

---

### Post by lykwydchykyn on 2009-05-25
www-data does not, by default, have write access to /var/www.  

My personal preference is to just delete /var/www and make it a symlink to a directory in my home directory:
```

sudo rm -Rf /var/www
mkdir ~/www
cd /var
ln -s ~/www

```

Keeps my data under /home that way.

If you're being prompted to download your .php files, it means one of the following:
 - libapache2-mod-php5 is not installed
 - apache2 was not restarted after libapache2-mod-php5 was installed
 - php5 module was not enabled for some reason. try: 
```

sudo a2enmod php5 && sudo /etc/init.d/apache2 restart

```
 - You've got a directive in your virtual host file overriding php handling.  This wouldn't be there by default, only if you've added something.

---

