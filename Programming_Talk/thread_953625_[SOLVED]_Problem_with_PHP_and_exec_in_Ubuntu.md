---
title: "[SOLVED] Problem with PHP and exec in Ubuntu"
date: 2008-10-20
forum: Programming Talk
---

### Post by Kenchu on 2008-10-20
I'm trying to convert the first page of a PDF-document to a jpg-file through PHP. I've got lampp, ImageMagick and GhostScript installed, and this command works just fine:

convert -scale 120 lol.pdf[0] test.jpg

Now if I try to do this in PHP-code:

```
<?



header('Content-Type: text/plain');



$var = array();

$res = 0;



exec('convert -scale 120 lol.pdf[0] test.jpg', $var, $res);



print 'Status: '.$res.'

';

print_r($var);



?>
```

Nothing will be converted, and the output will be "Status: 1". Any ideas?

---

### Post by drubin on 2008-10-20
try  absolute paths, and shell_exec

$result = shell_exec('convert -scale 120 /var/www/html/lol.pdf[0] /var/www/html/test.jpg);

---

### Post by Kenchu on 2008-10-20
No luck. :( Didn't work.

---

### Post by cdenley on 2008-10-20
Does www-data have permission to write in that directory?

---

### Post by Kenchu on 2008-10-20
I'm not quite sure. I'm running lampp thorugh sudo, so I think it should be able to write anywhere.

---

### Post by drubin on 2008-10-20
> **Kenchu said:**
> I'm not quite sure. I'm running lampp thorugh sudo, so I think it should be able to write anywhere.

Firstly not sure if you can run lamp through sudo. 
But if you are running a lamp server with the user being root that is a very big security hole.

This thread might help you
[http://ubuntuforums.org/showthread.php?t=922399](http://ubuntuforums.org/showthread.php?t=922399)

---

### Post by Kenchu on 2008-10-20
> **drubin said:**
> Firstly not sure if you can run lamp through sudo. 
But if you are running a lamp server with the user being root that is a very big security hole.

This thread might help you
[http://ubuntuforums.org/showthread.php?t=922399](http://ubuntuforums.org/showthread.php?t=922399)


I dunno, if you try running lampp without sudo it will fail, saying you have to run it in superuser mode.

Anyways, this was solved by adding write permissions for everyone to the folder. :)

---

### Post by drubin on 2008-10-20
> **cdenley said:**
> Does www-data have permission to write in that directory?

> **Kenchu said:**
> I dunno, if you try running lampp without sudo it will fail, saying you have to run it in superuser mode.

Anyways, this was solved by adding write permissions for everyone to the folder. :)

Dont add write permissions for every one. Change the owner ship to www-data.
sudo chown www-data:www-data /var/www/*

also do you mean you run it as root ie
sudo /etc/init.d/apache2 start?  or in the config files does it list root as the user?

---

### Post by Kenchu on 2008-10-20
> **drubin said:**
> Dont add write permissions for every one. Change the owner ship to www-data.
sudo chown www-data:www-data /var/www/*

also do you mean you run it as root ie
sudo /etc/init.d/apache2 start?  or in the config files does it list root as the user?

What is www-data:www-data? I have not such user. Nor is there a folder like /var/www/.

I run sudo "/opt/lampp/lampp start"

If I do this:

/opt/lampp$ ./lampp start

Ill get this:

You need to start XAMPP as root!

---

### Post by drubin on 2008-10-20
> **Kenchu said:**
> What is www-data:www-data? I have not such user. Nor is there a folder like /var/www/.

I run sudo "/opt/lampp/lampp start"

If I do this:

/opt/lampp$ ./lampp start

Ill get this:

You need to start XAMPP as root!

Ok this user would not have been created because you didn't do an 'install' but just extracted the contents of a tar.gz. Your lamp server would then run under the user nobody.

As for the error about being root, You need to be root to start the server but the server does not run as root. 

Simple example. while the server is running do
```
sudo ps -ef |grep apache
``` You will also the user that created the process.

---

### Post by Kenchu on 2008-10-20
> **drubin said:**
> Ok this user would not have been created because you didn't do an 'install' but just extracted the contents of a tar.gz. Your lamp server would then run under the user nobody.

As for the error about being root, You need to be root to start the server but the server does not run as root. 

Simple example. while the server is running do
```
sudo ps -ef |grep apache
``` You will also the user that created the process.

Ah I see. So if I start apache through sudo, it will still run with the same restrictions as the user invoking sudo?

---

### Post by cdenley on 2008-10-20
> **Kenchu said:**
> Ah I see. So if I start apache through sudo, it will still run with the same restrictions as the user invoking sudo?

No, it will probably run as another user. Post the output for the command drubin posted, or better yet, use a regular LAMP configuration.

---

### Post by Kenchu on 2008-10-20
> **Kenchu said:**
> sudo ps -ef |grep apache

andreas   7249  6173  0 23:11 pts/0    00:00:00 grep apache


I dont quite get it. I tried chowning both the output folder and lampp program file to myself. Yet no output will be made unless the folder is chmodded for everyone to write.

---

### Post by drubin on 2008-10-20
Seems we have changed the topic slightly I would HIGHLY recommend you use this to install a lamp server.
**EDIT: **forgot the link lol, [https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

The default one that you have set up is for quick "easy" usage but by no means should be used for more advanced users.
> 
No, it will probably run as another user. Post the output for the command drubin posted, or better yet, use a regular LAMP configuration. 

It will run as the user set out in the config file. take a look for  user and group in the /opt/lamp/apache2/conf/httpd.conf OR  /opt/lamp/httpd/conf/httpd.conf (not 100% sure but try looking for a httpd.conf file.)

The reason that searching for the running apache proccess did not work is it some times runs under apache2.
```
ps -ef |grep **http** 
```

---

### Post by Kenchu on 2008-10-20
> **drubin said:**
> Seems we have changed the topic slightly I would HIGHLY recommend you use this to install a lamp server.
**EDIT: **forgot the link lol, [https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

The default one that you have set up is for quick "easy" usage but by no means should be used for more advanced users.

It will run as the user set out in the config file. take a look for  user and group in the /opt/lamp/apache2/conf/httpd.conf OR  /opt/lamp/httpd/conf/httpd.conf (not 100% sure but try looking for a httpd.conf file.)

The reason that searching for the running apache proccess did not work is it some times runs under apache2.
```
ps -ef |grep **http** 
```

Thanks for clearing this up. I successfully managed to get it working as it should now. Switched user in httpd.conf, restarted server and it works. :)

---

