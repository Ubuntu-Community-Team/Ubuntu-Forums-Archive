---
title: "trying to get a local php script to work..."
date: 2006-04-14
forum: Programming Talk
---

### Post by orlox on 2006-04-14
I have a simple file on my file system called "hello.php" that looks like this:


[PHP]
<html>
 <head>
  <title>PHP Test</title>
 </head>
 <body>
 <?php echo '<p>Hello World</p>'; ?>
 </body>
</html>
[/PHP]

I'm trying to get it work, but haven't been very succesfull. I already installed php5 and apache, and when I try to open the file with firefox, it promts me for download. I know that for it to open correctly, i need to specify the http protocol, but don't know how to do that...

Can anyone help me here?](*,)

---

### Post by DoktorSeven on 2006-04-15
You have to put it in your web server root directory (by default, it's /var/www/) and open it via HTTP in your browser.

For example, put "hello.php" in /var/www/hello.php and open [http://localhost/hello.php](http://localhost/hello.php)

---

