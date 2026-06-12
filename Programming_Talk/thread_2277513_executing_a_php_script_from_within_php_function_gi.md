---
title: "executing a php script from within php function giving permission problems"
date: 2015-05-09
forum: Programming Talk
---

### Post by IAMTubby on 2015-05-09
Hello,
 I understand this question is php-based, but I am having problems with permissions on /var/www/html

I am trying to execute a php script from within a php function. I started out with something as small as 

**my function**
```
<?php
function myfunc($myarg) {
 //code
 exec("sudo php5 printhello.php > people.txt");
 //code
}
?>
```

**printhello.php**
```
<?php
print "hello";
?>
```

All the other code in this function is executing correctly, but the line of code which calls printhello.php and prints out hello to a file called people.txt (basically, /var/www/html/projectname/hello.txt) is not working, as in, the file is not getting populated with the result as it should.

_ I believe it's something to do with permissions in /var/www/html, but_
1. I'm using sudo in the call, ie, sudo php5 printhello.php > people.txt , so I thought it would work
2. I also tried creating an empty file called people.txt, gave it 777 permissions and then altered the code as sudo php5 printhello.php >> people.txt to append to an already existing file which has 777 permissions.

I still couldn't get it to work.

Please advise.
Thanks.

(I've heard people saying not to use sudo within php as it can be misused by an attacker, but how else is the above usually achieved ?)

---

### Post by SeijiSensei on 2015-05-09
1) You cannot run sudo from PHP unless you have configured the sudoers file appropriately.  PHP scripts have the same permissions as does the owner of the Apache server process.  On Ubuntu that process is owned by the pseudo-user "www-data".

2) As a result if you run a shell script from inside a PHP script hosted on a web server, you can only write files into directories where the www-data has privileges.  On a 14.04 server, that user can only write to /tmp by default.  The web server directory tree, /var/www, is owned by root.

3) Try replacing the exec() call with:
```
exec("php5 printhello.php > /tmp/people.txt");
```
Does that work?

Don't try to get around this problem by giving www-data write privileges to /var/www/html.  If you need a web application to write files in a location other than /tmp, create a separate directory outside the website tree that is owned by www-data and write your files there.  Letting the web server write into a site's document tree makes it possible to deface the site if you can trick the server into writing a bogus home page into the DocumentRoot as "index.html."

---

### Post by IAMTubby on 2015-05-10
> **SeijiSensei said:**
> 
3) Try replacing the exec() call with:
```
exec("php5 printhello.php > /tmp/people.txt");
```
Does that work?

Thanks SeijiSensei, that does work. Is this how files are normally written within a php environment, as in copying to a tmp directory?

> 
1) You cannot run sudo from PHP unless you have configured the sudoers  file appropriately.  PHP scripts have the same permissions as does the  owner of the Apache server process.  On Ubuntu that process is owned by  the pseudo-user "www-data".

Yes, I tried running and noticed that even the following does not work
```
exec("sudo php5 printhello.php > /tmp/people.txt");
```

> 
If you need a web application to write files in a location other than /tmp, create a separate directory outside the website tree that is owned by www-data and write your files there.  Letting the web server write into a site's document tree makes it possible to deface the site if you can trick the server into writing a bogus home page into the DocumentRoot as "index.html."
I notice the following

The below works when run from command line, does not work when run from browser. Does that mean that Desktop is not owned by www-data? I could not find out which directories are owned by www-data. Could you please tell me?
```

<?php
exec("ls > /home/IAMtubby/Desktop/lsout.txt");
?>

```
(Permissions of the test.php file above is the default, -rw-r--r--)

---

### Post by Holger_Gehrke on 2015-05-10
> **IAMTubby said:**
> Thanks SeijiSensei, that does work. Is this how files are normally written within a php environment, as in copying to a tmp directory?


No, there's several way to do it, some safer than others. As SeijiSensei already mentioned, you can create a directory somewhere outside of DocumentRoot and give ownership of that to www-data. I've also seen some PHP-programs -- Typo3 for example, or GetSimple and DokuWiki -- that need some sub-directories of DocumentRoot writable for uploading files; usually you have to do some serious work to make this safe, like putting in a '.htaccess' file that forbids direct access and access to directory listing from a browser, putting in a index.html and index.php that redirects to the main page and of course checking the names and content of the uploaded files. Anyway, the "exec + redirection" - method you're using to write to files is not a good idea, you're involving a shell where it's not needed (remember shellshock ?). PHP has [functions to open, read and write files]("http://php.net/manual/en/book.filesystem.php").

> **IAMTubby said:**
> 
The below works when run from command line, does not work when run from browser. Does that mean that Desktop is not owned by www-data? I could not find out which directories are owned by www-data. Could you please tell me?
```

<?php
exec("ls > /home/IAMtubby/Desktop/lsout.txt");
?>

```
(Permissions of the test.php file above is the default, -rw-r--r--)

Of course your Desktop directory does not belong to www-data, it belongs to you. If you call PHP from the cli, it runs with your permissions. If it get's called through Apache, it runs as www-data. To find out what directories www-data owns you could use 'find / -user www-data -type d', but normally that should return nothing except for a few 'access denied' errors. It's a security measure, again.

---

### Post by SeijiSensei on 2015-05-11
The www-data user owns essentially nothing as far as I can tell.  Running "find / -user www-data -type d" turns up only the lock file in /run and a directory in /var/cache.   

If you must write files from PHP scripts, create a separate directory like this:
```

cd /var/www
sudo mkdir data
sudo chown www-data:www-data data
sudo chmod 755 data

```
then write your files to /var/www/data.

---

### Post by IAMTubby on 2015-05-11
> **SeijiSensei said:**
> The www-data user owns essentially nothing as far as I can tell.  Running "find / -user www-data -type d" turns up only the lock file in /run and a directory in /var/cache.   

If you must write files from PHP scripts, create a separate directory like this:
```

cd /var/www
sudo mkdir data
sudo chown www-data:www-data data
sudo chmod 755 data

```
then write your files to /var/www/data.
Thanks SejiSensei,

I tried using the steps mentioned above. So from now on, to write to a file from php script run from the browser, I will either use the steps mentioned above or write to /tmp
Please see code below, line 1 and 2 work for me, line 3 doesn't work as expected.

```

<?php
exec("echo \"hello\" > /tmp/hellofile"); //works
exec("echo \"hello\" > /var/www/html/fileupload/data/hellofile"); //works
exec("echo \"hello\" > /var/www/html/fileupload/hellofile"); //does not work
?>

```

> 
If you must write files from PHP scripts

Just to clarify since I'm still finding my feet, you mean write files from PHP scripts **run from the browser**?
If you're just running from the terminal, it would suffice if the user running the script has permission to write to that folder, which means just do sudo scriptname.php ?

---

### Post by IAMTubby on 2015-05-11
> **Holger_Gehrke said:**
> Anyway, the "exec + redirection" - method you're using to write to files is not a good idea, you're involving a shell where it's not needed (remember shellshock ?). PHP has [functions to open, read and write files]("http://php.net/manual/en/book.filesystem.php").

Thanks Holger_Gehrke, I am just trying out how exec works with php. Won't use it in real code.

I have been playing around and have one more question here,
1. Say, I'm running a php script from terminal, what is the difference between the following?

(I'm running the following scripts from /var/www/html/)

_Works and creates the lsoutput file_
```
<?phpexec("ls > lsoutput")
?>

Run code as 
sudo php5 test.php

```

and

_Does not create the lsoutput file_
```
<?phpexec("sudo ls > lsoutput")
?>

Run code as 
php5 test.php

```


Is the difference that in the second case, you are only running the ls command as sudo, but still do not have permission to write in the /var/www/html/ directory. Whereas, in the first case, you're both running the ls command as well as creating a file with super user priveleges ?

2. Also
I'm able to run my script below even as normal user, without doing sudo. But to delete it, I need sudo. Even to edit the file, it does not allow me to edit unless I have done sudo vi. Why is that? Shouldn't permissions be consistent?
```

IAMTubby@IAMTubby-Inspiron-1545:/var/www/html/fileupload$ php5 ls.php 
works fine

IAMTubby@IAMTubby-Inspiron-1545:/var/www/html/fileupload$ rm ls.php 
rm: remove write-protected regular file `ls.php'? y
rm: cannot remove `ls.php': Permission denied

IAMTubby@IAMTubby-Inspiron-1545:/var/www/html/fileupload$ ls -l ls.php 
-rw-r--r-- 1 root root 319 May 11 10:18 ls.php

IAMTubby@IAMTubby-Inspiron-1545:/var/www/html/fileupload$ whoami
IAMTubby

IAMTubby@IAMTubby-Inspiron-1545:/var/www/html/fileupload$ cat ls.php 
<?php
echo "hello";
?>


```

---

### Post by SeijiSensei on 2015-05-11
You're making this all way too hard.  You haven't shown us the permissions on /var/www/html/fileupload or /var/www/html/fileupload/data, so we cannot answer these questions.

There's really only answer.  Create a directory owned by www-user and write the files there.  Get them out of /var/www/html; that's dangerous.

And, yes, I'm only talking about scripts that run from Apache.  If you run php5 from the command line, it will use the permissions of the logged-in user.

---

### Post by IAMTubby on 2015-05-11
> **SeijiSensei said:**
> You're making this all way too hard.  You haven't shown us the permissions on /var/www/html/fileupload or /var/www/html/fileupload/data, so we cannot answer these questions.

There's really only answer.  Create a directory owned by www-user and write the files there.  Get them out of /var/www/html; that's dangerous.

And, yes, I'm only talking about scripts that run from Apache.  If you run php5 from the command line, it will use the permissions of the logged-in user.
Thanks SeijiSensei,

Below are the permissions of fileupload
drwxr-xr-x 4 root root  4096 May 11 10:18 fileupload

And the permissions of the folder 'data' are same as from your previous reply where make it owned by www-data. I was able to get it to work. Thanks a lot.

But I'm still confused as to why I can execute ls.php from the terminal as logged-in user, but can't delete or write to it without being sudo. If you could clarify this, would be great
```

IAMTubby@IAMTubby-Inspiron-1545:/var/www/html/fileupload$ php5 ls.php 
works fine

IAMTubby@IAMTubby-Inspiron-1545:/var/www/html/fileupload$ rm ls.php 
rm: remove write-protected regular file `ls.php'? y
rm: cannot remove `ls.php': Permission denied

IAMTubby@IAMTubby-Inspiron-1545:/var/www/html/fileupload$ ls -l ls.php 
-rw-r--r-- 1 root root 319 May 11 10:18 ls.php

IAMTubby@IAMTubby-Inspiron-1545:/var/www/html/fileupload$ whoami
IAMTubby

IAMTubby@IAMTubby-Inspiron-1545:/var/www/html/fileupload$ cat ls.php 
<?php
echo "hello";
?>
```

---

### Post by SeijiSensei on 2015-05-11
You must have created that file with sudo somewhere along the way.  It's owned by root, so you can only delete it as root with sudo.

And, again, don't let the www-user write files below /var/www/html on any production server.

---

### Post by IAMTubby on 2015-05-11
> **SeijiSensei said:**
> 
And, again, don't let the www-user write files below /var/www/html on any production server.
I'm sorry, but on the production server where I would host my site, where do I make the folder to which www-user has access to write ?
Why is not a good practice to make the folder as /var/www/html/data ?

Looking back to your reply, you have made the folder as /var/www/data. Is this the way to go?

cd /var/www
sudo mkdir data
sudo chown www-data:www-data data
sudo chmod 755 data

---

### Post by SeijiSensei on 2015-05-12
There are a number of issues here.

First, what are you trying to accomplish?  Write files that can then be viewed from a browser?  Or just write a file some place for some reason.  If the latter, there's no reason those files need to be under /var/www/html.

Second, if the web server can write into the website tree, it opens up the possibility that an attacker could exploit some hole to write one or more bogus web pages into your site.  This is often how sites are "defaced."

So if the files are in /var/www/html/data, then they will be accessible from a client's browser, but also open you up to a security hole.

---

### Post by IAMTubby on 2015-05-12
> **SeijiSensei said:**
> 
First, what are you trying to accomplish?  Write files that can then be viewed from a browser?  Or just write a file some place for some reason.  If the latter, there's no reason those files need to be under /var/www/html.

Right, the latter, I would just like to write these to a place for some reason, maybe logging, reading from it sometime later etc.
What is the best place to have a folder owned by www-data for this purpose?

---

### Post by SeijiSensei on 2015-05-13
For files you intend to write and then delete later in the same script, I'd use /tmp.  

Otherwise, if you want to consolidate things in /var/www, then /var/www/data is a fine choice. 
```

cd /var/www
sudo mkdir data
sudo chown www-data:www-data data
sudo chmod 755 data

```

---

