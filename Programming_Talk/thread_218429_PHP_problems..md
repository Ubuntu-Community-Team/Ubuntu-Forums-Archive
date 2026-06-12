---
title: "PHP problems."
date: 2006-07-18
forum: Programming Talk
---

### Post by khaledaboualfa on 2006-07-18
Hey everyone I'm trying to get my php script to run locally for testing. I've installed LAMP and it seems to work fine as I can access localhost normally and it shows that apache and php and mysql is all running as they should be.

The problem is that I can seem to get my scripts to work. I researched the forums a bit and I found that one solution might be creating a public_html folder in my user folder and then linking to it like so:

[http://localhost/~khaled/website_name/header.php](http://localhost/~khaled/website_name/header.php)

The actual path would be /home/khaled/public_html/website_name/header.php.

Unfortunately I get a 404 error. I've given the public_html file all the permissions but it doesn't seem to want to work. Any ideas?

Also how would I got about setting up a wordpress install locally? Where would be the best place to put that with easy access as a user (var/www ? Would I need to be a superuser everytime I had to acess this?)

Thanks for any help.

 (new convert from windows so I'm not really up to speed on everything linux so please be kind)

---

### Post by ohgod on 2006-07-18
By default, the apache root folder is /var/www I believe.  Try putting your script there.  For example, if you put a script called blah.php in /var/www you should be able to load it via [http://localhost/blah.php](http://localhost/blah.php)

---

### Post by khaledaboualfa on 2006-07-18
Does this mean that all of my scripts have to be found in that particular folder for testing? I can't have them in any other particlar folder and link them back to the var/www ? I ask because if I'm working on a file I don't want to have to keep copying and pasting every time I want to test if something worked out.

---

### Post by Randomskk on 2006-07-18
I'd keep them in /var/www for now.
The easiest way to do what you want is something like this:
sudo chown <USERNAME> -R /var/www

Then, any of your editers (gedit, or bluefish etc etc) can save to /var/www.
Make sure Apache has read permissions, something like this:
sudo chmod 755 -R /var/www

Everything should pretty much work, including wordpress.

---

### Post by khaledaboualfa on 2006-07-18
Seems I'm doing something wrong. All the permissions work fine now and I can basically do whatever I want from bluefish into var/www (which I had to create...erm I'm using XAMMP, so I dunno if that's the correct location for the files to reside now...I've not compiled things individually).

So if I try and open my php file in ff it just asks me to save it all. Any ideas where I might be going wrong? I've actually chmoded everything associated with that but no cigar. Apache, php and mysql are all working just don't seem to want to run my script.

---

### Post by harisund on 2006-07-18
Wait a minute, did you enable the userdir module? 

I will tell you what I do normally. 

First, you already have mentioned Apache/PHP/MySql is running fine. So do the following: 

'sudo a2enmod userdir' 

This will enable the user directory module (for linking /home/khaled/public_html to [http://localhost/~khaled)](http://localhost/~khaled)).

So what I do for local testing of wordpress etc is simply this. I create a new user (let's say wordpress)

'sudo adduser wordpress'

It will ask you a list of questions and blah blah. 

Then login as wordpress and test all scripts you want. 

Once you are done, say you want to delete everything all together

'sudo deluser --remove-home wordpress'

The remove home will wipe out the home directory (including all the public_html and everything else) and you will be at the same state you were earlier. 

Convenient, don't you think? The beauty is that you don't have to worrry with any permissions and stuff. Just work as wordpress user in your wordpress home folder, writing everything public_html. When you are done wipe it all clean :). Don't bother with permissions especially on /var/www

---

### Post by Oler1s on 2006-07-18
> **khaledaboualfa said:**
> So if I try and open my php file in ff it just asks me to save it all. Any ideas where I might be going wrong? 

To confirm, when "opening" the php file, you mean you go through your webserver, right? If you directly open a php file, through the filesystem, that's no good. Yes, you have AMP, but it's not being processed by the webserver. You should be using "http://localhost" or an IP address.

---

### Post by khaledaboualfa on 2006-07-18
Okay I think I'll try and explain myself from the beginning and tell you guys how I normally used to work on windows, and then you guys can tell me the best way to approach things in linux would be.

I use XAMMP just to test things locally before uploading them. So all the testing occurs from [http://localhost](http://localhost). 

I used to have all the files in a doc and then under www in the xammp file itself. I don't actually know where that file is on ubuntu so that I can store and test everything LOCALLY from there.

Once I've written the php files I should be able to check them via firefox right? AMP all working, it should just show me what's going on, instead it asks me to download the file.

---

### Post by harisund on 2006-07-18
Ok, let me give you a complete walk through about everything you really need. 

First, let's start with a clean machine. Assuming you are familiar with the command line, do ```
sudo aptitude purge apache2 apache2-common php5 php5-common libapache2-mod-php5 mysql
sudo aptitude install apache2 apache2-common php5 php5-common libapache2-mod-php5 mysql
```
The above 2 lines of code to be executed in the terminal will give you a fresh installation to start with. 

Next, execute ```
sudo a2enmod userdir
```

Finally, create a directory in your home folder called public_html. Assuming it is not already there, you could do```
mkdir ~/public_html
```

Now, everything is done. You have mentioned that under Windows/XAMPP you used to place all files in a doc and then under www. Now, whatever you used to place there just go ahead and place it in public_html. Let's say we create an index.php and have just <?php phpinfo()> in it. You could do this using whichever editor you prefer, starting from simple nano, to gedit and bluefish/screem (even dreamweaver through wine if you please) and save it as index.php in your public_html directory. from now on, every time you mean to test something locally, put in public_html. 

Then head over to your browser. Type [http://localhost](http://localhost) and you will see one folder in there. apache2-default. Ignore it. 

Type in your browser [http://localhost/~username](http://localhost/~username) and you will be delivered the contents of your public_html folder. 

Since you are already familiar with web design to some extent under Windows, you should be comfortable here as well. Just put everything you want to test in public_html. 

For example, you could put a temp.php in public_html and to test it you would go to your browser and the address you would type in would be [http://localhost/~khaled/test.php](http://localhost/~khaled/test.php) and so on. 

Have I made myself clear?

---

### Post by drewsimon on 2006-07-18
^^^ Great! Thanks for that mini-howto. I'm doing that right now.

---

### Post by khaledaboualfa on 2006-07-19
harisund, that's PERFECT. Everything works like a charm now. You the man. I'll probably have a few more questions later on down the line but that works exactly as I need it to. Thanks ever so much.

---

### Post by harisund on 2006-07-19
Sure. Any time. Glad to hear it worked.

---

### Post by alainsamoun on 2006-07-29
Yes, that was good for me too.:D 
Thanks!
Alain

---

### Post by harisund on 2006-07-29
Thanks for the feedback !

---

### Post by otiose on 2006-11-16
This solution worked for me as well, except I had to purge php5-mysql and php5-mysqli and then install them again, as well before wordpress would work. Great tips, though!

---

### Post by harisund on 2006-11-18
php5-mysqli

There's a package like that? Wow! I have never seen that. How's that different from php5-mysql? Are they inter-compatible? 

Thanks!

---

### Post by ifokkema on 2006-11-20
The mysqli_* functions are **i**mproved and allows you to use special MySQL 4.1 and up functionality. You can use the mysql_* functions with the newest MySQL databases as well, but you'll lack the special features. I believe the mysqli_* functions don't work with MySQL 4.0 and before, but I'm not too sure.

---

### Post by adam_pretty on 2006-11-21
Thanks for the guide here... 

However, I still have the problem that when I try and browse to say "test.php" it asks if i want to edit/download it... 

Not sure what i'm doing wrong here. 

Any help much appreciated!

Thanks
Adam.

---

### Post by dataw0lf on 2006-11-21
> **adam_pretty said:**
> Thanks for the guide here... 

However, I still have the problem that when I try and browse to say "test.php" it asks if i want to edit/download it... 


You're going to need to add:

AddType application/x-httpd-php .php

to your Apache configuration.

---

### Post by adam_pretty on 2006-11-22
Thanks, but it looks like that is already there in my httpd.conf

---

### Post by ifokkema on 2006-11-22
If you open the file through the browser, do you see the PHP code, the actual expected output, or no output?

---

### Post by harisund on 2006-11-25
No, when you try to access the file you probably have your Firefox asking you whether you want to download the file. Right? 

What were the steps that you followed? 

Did you follow everything in [http://ubuntuforums.org/showpost.php?p=1272499&postcount=9](http://ubuntuforums.org/showpost.php?p=1272499&postcount=9)

---

### Post by adam_pretty on 2006-11-28
Ok -  back onto this ...

Just went through the steps in the linked post. Still get the same problem. Html pages come up fine but it sees php pages as text files to download (downloads the original php file) . 

Any more clues much appreciated!!
Thanks




:-k

---

### Post by adam_pretty on 2006-11-29
* bump *

---

### Post by ifokkema on 2006-11-29
If you followed the guide, you've got apache2 with php5. What are the contents of your /etc/apache2/mods-enabled/ directory? Is there a file called php5.load and php5.conf? If not, run
sudo a2enmod php5

---

### Post by adam_pretty on 2006-11-30
thanks

yes, got php5.conf and php5.load

still got the download problem :(

---

### Post by ifokkema on 2006-11-30
I don't know of an easier way, but the following method checks if the module has actually been loaded and activated by Apache.
In your console, type:
```
telnet localhost 80
```
you then get something like:
```
Trying 127.0.0.1...
Connected to localhost.localdomain.
Escape character is '^]'.

```Then you type (exactly):
```
HEAD / HTTP/1.0
HOST: localhost
```
followed by two enters. Then you get something like:
```
HTTP/1.1 200 OK
Date: Thu, 30 Nov 2006 19:11:52 GMT
Server: Apache/1.3.34 (Ubuntu) PHP/4.4.2-1build1
X-Powered-By: PHP/4.4.2-1build1
Connection: close
Content-Type: text/html; charset=iso-8859-1
```

The above is with my Apache 1.3 server, with PHP enabled (as it shows). What's your output?

---

### Post by adam_pretty on 2006-12-01
I get this:

```
HTTP/1.1 200 OK
Date: Fri, 01 Dec 2006 10:35:07 GMT
Server: Apache/1.3.34 (Ubuntu)
Last-Modified: Wed, 15 Nov 2006 18:11:54 GMT
ETag: "108132-e02-455b586a"
Accept-Ranges: bytes
Content-Length: 3586
Connection: close
Content-Type: text/html; charset=iso-8859-1

```

So, looks like PHP is not loading for some reason...

---

### Post by ifokkema on 2006-12-01
Ha! We may have it... check closely your output. That's Apache 1.3 talking to you... not Apache 2!!! Looks like you've got both installed. Stop Apache 1.3 and try to start Apache 2. My guess is that Apache 2 is not even started. You can check by running:
```
ps -ef |grep apache
```

---

### Post by adam_pretty on 2006-12-04
Thank you!!

Works now! - that was the prob all along. 

:KS

---

### Post by ifokkema on 2006-12-05
Great! Perhaps something to add to the mini-howto in this thread...

---

