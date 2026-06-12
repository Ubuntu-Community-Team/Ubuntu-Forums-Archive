---
title: "How to get PHP include to work on freshly installed LAMP server"
date: 2012-07-04
forum: Programming Talk
---

### Post by jvahub on 2012-07-04
Hi,
 
Beginners question. I just installed a basic Ununtu server and followed instructions to upgrade it to a LAMP server. Now I'm following a little PHP tutorial (which explains it on a Windows machine btw) which explains some basic PHP stuff.
 
Now I'm at a point where it gives a code in the page that goes like:
```
<?php include(includes/nav.php); ?>
```
 
My index file (which I'm editting) is located in /var/www/phpsite/
I have a file called nav.php located in /var/www/phpsite/includes/
 
However this piece of code isn't working.
I Googled and found multiple suggestions, like using different code or filling a php configuration file but either it didn't work for me or I misunderstood it.
 
Perhaps someone here can help me with this?
Thanks.

---

### Post by Barrucadu on 2012-07-04
What exactly does "this piece of code isn't working" mean?

---

### Post by jvahub on 2012-07-04
Ok so I followed this tutorial:
 
[http://www.1stwebdesigner.com/css/how-to-create-php-website-template/comment-page-2/#comments](http://www.1stwebdesigner.com/css/how-to-create-php-website-template/comment-page-2/#comments)
 
So at a certain point (step 7/8) you split a part of index.html to 'redirect' to one of the .php files. If I now refresh my index.html the part I expect to see is just blank/not visible.
 
Thanks.

---

### Post by snip3r8 on 2012-07-04
change

 [PHP]<?php include(includes/nav.php); ?>[/PHP]

to 

[PHP]<?php include("includes/nav.php"); ?>[/PHP]

---

### Post by jvahub on 2012-07-04
Thanks, but unfortunately that doesn't help. Also tried it with ' ' and nothing at all. None work.

---

### Post by snip3r8 on 2012-07-04
Have you checked your file structure and where you are calling it from? try "./includes/nav.php"

---

### Post by jvahub on 2012-07-04
adding ./ doesn't work.
 
all files are located here:
 
/var/www/phpsite/ (index.html)
/var/www/phpsite/includes/ (.php files)

---

### Post by PaulM1985 on 2012-07-04
What do you get? Does it display:
```

<?php include(includes/nav.php); ?> 

```

On your screen?  Do you know if PHP is working?  Have you tried files in the same folder? Or tried doing everything in /var/www?

Paul

---

### Post by Barrucadu on 2012-07-04
Have you checked the Apache error log? Are there any errors? Have you tried to fix these errors?

Does PHP work at all? Try a phpinfo script.

---

### Post by jvahub on 2012-07-04
It displays nothing on screen. I havent tried moving the files and to be honest don't see a reason to? If anyone can tell me why I'd gladly do that.
Apache error log is empty.
 
PHP seems to be working, if I make a PHP file with this:
 
```
<?php
phpinfo();
?>
```
 
It works.

---

### Post by PaulM1985 on 2012-07-04
> **jvahub said:**
> It displays nothing on screen. I havent tried moving the files and to be honest don't see a reason to? If anyone can tell me why I'd gladly do that.


I was only suggesting it so that we can get to a very, very simple case and we don't have to worry about issues with invalid paths.

Additionally, (I know this is a stupid question, but always one worth asking) is there definitely something in the file you have included.  What happens if you try to view only the included file?

Paul

---

### Post by SeijiSensei on 2012-07-04
I'm pretty sure the include_path isn't pointing to /var/www/phpsite.  What if you use the full path?

```
<?php include("/var/www/phpsite/includes/nav.php"); ?>
```

Relative paths are not generally a very good idea unless you specify the root directory manually.  I put all my include files in a directory outside the publicly-visible directories and define a "$includes" variable that I use with relative paths like this:

```

$includes="/home/me/includes/";   # note the trailing slash
include($includes."somescript.php");

```

The default "include_path" is set in /etc/php5/apache2/php.ini.  If you run that phpinfo() script again, you'll see it reported in the PHP Core section.  I believe the Ubuntu default is the same as it is on my CentOS servers:

```
include_path=.:/usr/share/pear:/usr/share/php
```

I think the leading dot corresponds to the DocumentRoot of the virtual server.  Do you use the URL [http://something/phpsite/index.php](http://something/phpsite/index.php) to access your scripts?  If so, then I believe the dot refers to /var/www, not /var/www/phpsite.

As I say, I avoid all of this by setting the include path in my scripts or using full directory paths in include() and require() statements.

---

### Post by jvahub on 2012-07-05
Paul: yes there's something in the included file(s) ;-)
Seiji: full path I also tried but also doesn't work. The code for the include variables; where exactly do I put this piece of code? somewhere in my index.html? And the include path of php.ini, how should my version look like?
 
```
include_path=.:/var/www/phpsite/includes
```
 
?
 
Anyway, thanks for all the help so far, but my feelings says that I might have to look in a different direction, maybe file/folder rights or something? Although I'm not sure.

---

### Post by spjackson on 2012-07-05
> 
Anyway, thanks for all the help so far, but my feelings says that I might have to look in a different direction, maybe file/folder rights or something? Although I'm not sure.If it is failing to include the file either because it cannot be found or because of file/folder rights, then you should get an error in the apache error log. On my system that is /var/log/apache2/error.log but it could be somewhere else.

If there are no error messages then it is likely that the file is being included. What is in the included file? If it is only function definitions, then you won't see anything in your browser unless you call the functions.

---

### Post by jvahub on 2012-07-05
Well there's no errors in that file (mine is in same location btw).
Just some shutdown notifcations because it's a virtual machine.
 
To clear things up; I'm using this tutorial (mentioned earlier) so you have an idea of what I'm doing: [http://www.1stwebdesigner.com/css/how-to-create-php-website-template/](http://www.1stwebdesigner.com/css/how-to-create-php-website-template/)
 
An example of one of the PHP files I'm including:
 
```
<div id="header">
    <h2>Hello hello hello</h2>
</div> <!-- end #header -->

```

---

### Post by spjackson on 2012-07-05
> **jvahub said:**
> 
An example of one of the PHP files I'm including:
 
One of the files? Is this includes/nav.php?

I would expect the fragment you have shown would produce visible output if it is emitted in a valid html context.

If you put a deliberate error in your included file, do you get an error in apache's error log? e.g.

```
<?php
nosuchfunction();
?>

```

---

### Post by jvahub on 2012-07-05
No my example was not nav.php but header.php
 
Anyway, now I changed nav.php to add this deliberate error you gave and when I visit this page (not index.html but the actual nav.php) it gives my first errors in logfile...
 
[Thu Jul 05 13:41:03 2012] [error] [client 10.136.101.27] PHP Fatal error:  Call to undefined function nosuc$
[Thu Jul 05 13:41:05 2012] [error] [client 10.136.101.27] PHP Fatal error:  Call to undefined function nosuc$
[Thu Jul 05 13:41:05 2012] [error] [client 10.136.101.27] PHP Fatal error:  Call to undefined function nosuc$

---

### Post by spjackson on 2012-07-05
> **jvahub said:**
> No my example was not nav.php but header.php
 
Anyway, now I changed nav.php to add this deliberate error you gave and when I visit this page (not index.html but the actual nav.php) it gives my first errors in logfile...
 
[Thu Jul 05 13:41:03 2012] [error] [client 10.136.101.27] PHP Fatal error:  Call to undefined function nosuc$
[Thu Jul 05 13:41:05 2012] [error] [client 10.136.101.27] PHP Fatal error:  Call to undefined function nosuc$
[Thu Jul 05 13:41:05 2012] [error] [client 10.136.101.27] PHP Fatal error:  Call to undefined function nosuc$

Good, that's progress. You have proved that

[LIST=1]
[*]The include statement finds the right file and includes it.
[*]File and folder permissions are correct (because the above works).
[*]Errors, when they occur, are reported to the apache error log.
[/LIST]
So what we are left with is the php content. If you post both the including code and included code, we'll see what's wrong with it.

---

