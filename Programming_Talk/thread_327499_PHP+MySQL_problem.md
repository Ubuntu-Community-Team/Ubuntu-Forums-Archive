---
title: "PHP+MySQL problem"
date: 2006-12-29
forum: Programming Talk
---

### Post by commodore on 2006-12-29
"Fatal error: Call to undefined function mysql_connect() in /my/file.php on line 2"

Why? I have php5, mysql-server, modphp, and the mysql library for php installed.

---

### Post by gpolo on 2006-12-29
did you check your php.ini ? maybe it is missing extension for mysql, there should be a line like:
extension=mysql.so

and mysql.so should be in the right directory

---

### Post by breen92uk on 2007-01-03
I have the exact same problem, only the solution described above makes no difference (and yet, phpMyAdmin works perfectly, surely it needs the PHP MySQL to function?). It worked fine when I was using Dapper (without any manual configuration), is there some difference in how Edgy handles the installation that may have caused this to happen?

---

### Post by manilodisan on 2007-01-03
Please paste your code which connects to mysql

---

### Post by breen92uk on 2007-01-03
> **manilodisan said:**
> Please paste your code which connects to mysql

The code is too long to be quoted here but here is the basic jist of what causes the problems, and is referenced in the error message I receive (similar to the one described in Post #1). I doubt this is the source of the issue however, as this code works with no problems when uploaded to my site's external hosting, and an identical copy also worked fine on localhost before I upgraded to Edgy.
```
mysql_connect("localhost", "username", "password") or die(mysql_error()); 

mysql_select_db(database name) or die(mysql_error());
```

---

### Post by Determinist on 2007-01-03
Take a look at phpinfo()'s output and paste the section related to mysql. There should be some helpful information there. Which version of php (full version please, 5.1.2 != 5.2).

---

### Post by breen92uk on 2007-01-04
> **Determinist said:**
> Take a look at phpinfo()'s output and paste the section related to mysql. There should be some helpful information there. Which version of php (full version please, 5.1.2 != 5.2).

That freaked me out a little before, because in the data provided by phpinfo() there *is* no data relating to MySQL. It doesn't feature anywhere in the document, that's why I thought it may be an installation problem (though God knows how phpMyAdmin is working, does that use a different method to access MySQL?). My full PHP version is 5.1.6, though I also tried uninstalling that and replacing it with a version of PHP 4, only to be faced with exactly the same issue.

---

### Post by Ba66e77 on 2007-01-04
Not sure how phpMyAdmin accesses MySQL, but if your phpinfo() doesn't have a MySQL section, something isn't right in your configuration.  If nothing else, you should see --with-mysql in the "Configure Command" section

---

### Post by Mirrorball on 2007-01-04
Maybe phpMyAdmin is using mysqli or PDO. Do you have PDO? It's not installed by default (although it should have been).

---

### Post by igeterrors on 2007-01-07
I'm having the exact same problem, to the letter.  PHP works, MySQL works, and I have the Apache2 server installed.  I can run PHP scripts on the server and I can work with databases in MySQL via the command line.  But when I try to get all three to work together, I get:

```
Fatal error: Call to undefined function mysql_connect() in /var/www/apache2-default/open_connection.php on line 6

```

And while it was helpful to know that > **gpolo said:**
> 
mysql.so should be in the right directoryit would've been twice as helpful to be told what the right directory *IS*. 

Because currently my php.ini FILES (I seem to have two of them, in two different places) both have the line "extension=mysql.so" but the only place on my computer I can find mysql.so itself is in /usr/lib/perl5/auto/DBD/mysql/

So, is *THAT* the right directory?

---

### Post by Mirrorball on 2007-01-07
In my system it's also in /usr/lib/php5/20060613/

---

### Post by breen92uk on 2007-01-08
> **Mirrorball said:**
> In my system it's also in /usr/lib/php5/20060613/

Lol yeah, it's there on my system as well, but it still doesn't work. I'm assuming it is something to do with the configuration through php.ini; could you post a copy of anything relating to MySQL in your version of the file?

---

### Post by Mirrorball on 2007-01-08
If you have this line:
```

;extension=mysql.so

```
uncomment it.

---

### Post by Dygear on 2007-01-09
The MySQLi class in PHP5 only, but he's not using MySQLi, he's just using the normal MySQL functions that have been around since PHP3. You don't seem to have the MySQL extension loaded at all. Check your php.ini file, or make a local one for just the one directory your going to use the mysql functions in.

---

### Post by igeterrors on 2007-01-09
> **breen92uk said:**
> Lol yeah, it's there on my system as well, but it still doesn't work. I'm assuming it is something to do with the configuration through php.ini; could you post a copy of anything relating to MySQL in your version of the file?

Mine's working now.  It seems that mysql 5.0 needs php5-mysqli rather than php5-mysql.  A combination of that plus a little bit of info from [**this wiki page**]("https://help.ubuntu.com/community/ApacheMySQLPHP#head-9da018e45a34318b768893df6715a50b06ecb1ed") (which seems like it's written by a non-native English speaker so read it carefully) did the trick. But basically it involved editing the 'extension_dir' property in my php.ini file:

```
$ sudo gedit /etc/php5/apache2/php.ini 

```

and for the 'extension_dir' property change /usr/lib/php5/20060613 to '/usr/lib/php5/ext' and save the file.

Now you have to create the directory:

```
$ sudo mkdir /usr/lib/php5/ext

```

And now copy your mysql.so file to this new directory *under the new name mysqli.so*:

```
$ sudo cp /usr/lib/php5/20060613/mysql.so /usr/lib/php5/ext/mysqli.so
```

Then restart Apache:

```
$ sudo /usr/sbin/apache2ctl restart
```

And bingo!  Pure joy.  At least for me.  Hopefully for you, too.

Just remember to install php5-mysqli.

---

### Post by breen92uk on 2007-01-10
Excellent! A combination of the advice from Mirrorball and igeterrors has solved the problem for me - I uncommented the 'extension = mysql.so' line in the php.ini file and added a 'extension = mysqli.so' for good measure, then followed the steps given by igeterrors in Post #15. 

Cheers guys!

---

### Post by Dygear on 2007-01-11
mysqli is the bomb. All of you need to check it out!

---

### Post by binks on 2007-01-30
thanks guys this helped alot i now have apache2 php5 and mysql talking with mysql.so loaded 
cheers binks

---

### Post by Sauli on 2007-02-11
I had similar problems in getting the MySQL (5.0.22-Debian_0ubuntu6.06.2-log) work in PHP (Version 5.1.2) even I had uncommented the extension=msql.so in /etc/php5/apache2/php.ini, checked that the extension directory (/usr/lib/php5/20051025 as seen from the browser when running the php script <? phpinfo(); ?>) did contain the files mysql.so and mysqli.so, and the .mysql database server was running. I still couldn't see mysl by <? phpinfo(); ?>.  I had activated the error logging by setting the log_errors = On and  error_log = /home/me/php_error_log in php.ini and I got an error message to the log "PHP Warning:  PHP Startup: Unable to load dynamic library '/usr/lib/php5/20051025/msql.so' - /usr/lib/php5/20051025/msql.so: cannot open shared object file: No such file or directory in Unknown on line 0"

Now the strange part. I was preparing to try things that have been suggested by the previous messages but decided to restart Apache  (2.0.55) and Mysql one more time even I am sure I had already done that immediately after editing the php.ini. And now, yes, to my great surprise everything seemed to be ok, I could see Mysql support by <? phpinfo(); ?>.

So, what is the learning from this. First, the only change that was required was to uncomment the extension=msql.so in php.ini, i.e. no need to add mysqli.so or move files to new directory, change directory path or anything like that. Second, I guess here, the restarting has to be done properly. I don't know what I did first wrong and then how I did it properly - I don't know was it the order of restars or doing separate stop + start or what. It may be that a power shortage that caused my whole PC to restart somehow helped to resolve the problem.

---

### Post by kag on 2007-02-22
I was also having this exact same problem. I stopped Apache and MySQL, then restarted MySQL, then Apache. Everything then worked fine and I could see mysqli from phpinfo();

The weird thing is that phpMyAdmin was working before I restarted those two. This I don't understand!

---

### Post by BillRebey on 2007-02-25
Even simpler solution.  My problem was that the default php.ini file that has been so talked about above came wiht a misspelling:  msql.so instead of mysql.so.  I just fixed the misspelling, added the "extension=mysqli.so" line (so now I was specifying both mysql.so and myslqi.so as extensions), restarted Apache, and it (not surprisingly) went off to the races.

I figured this out, of cousre, after about an hour of Google and Ubuntu forum searches, all the while "glossing over" the misspelling.  Just thought I'd pass this along in case someone else might be wasting time.

Thanks everybody for pointing me right to the source of the problem!

---

### Post by eyyuplu on 2007-03-06
hi
;extension_dir = "/usr/local/lib/php5/20051025:/usr/local/lib/php5/20051025:/usr/local/lib/php:/usr/lib/php5/20051025:/usr/lib/php5/20051025"

change 

;extension_dir = "/usr/local/lib/php5/20051025:/usr/local/lib/php5/20051025:/usr/local/lib/php:/usr/lib/php5/ext:/usr/lib/php5/20051025"

this is true?
************mysql.so**********
root@mustafa-desktop:~#  locate mysql.so
/usr/lib/perl5/auto/DBD/mysql/mysql.so
/usr/lib/python2.4/site-packages/_mysql.so
/usr/lib/php5/20051025/mysql.so
/usr/lib/apache2/modules/mod_auth_mysql.so
root@mustafa-desktop:~#


&#305; am still dont run phpmyadmin

---

### Post by themichaek on 2007-03-07
I am having this problem as well.  mysql_connect() works from apache, but not from the command line.

I have copied my /etc/php5/apache2/php.ini to /etc/php5/cli/php.ini (to make sure there is no difference), I have removed the comment before the mysql.so extension line.  I have checked that the command line interface is in fact using the /etc/php5/cli/php.ini file, and that the extensions dir reported by **php -i** contains the mysql.so extension.  The configuration is correct, but the extension is not loaded.

**phpinfo()** from apache outputs information about both mysql and mysqli extensions.  **php -m** from the command line does not include mysql or mysqli.

Running mysql_connect() from the command line then, predictably, returns:

```
Fatal error: Call to undefined function mysql_connect()
```

Other responses to this error I have read encouraged me to install php-mysql and php-mysqli extensions - or to install from source with the --with-mysql flag.  However, both extensions are installed, and both work with my PHP install - but only via apache.  The CLI will not load either extension, even if I specify, by file name, the extension to be loaded from the command line.

```
php -z /path/to/mysql.so
```

Further, changes that I make to the /etc/php5/cli/php.ini are not reflected in output from php -i, despite the following:

```
$ php -i | grep .ini
Configuration File (php.ini) Path => /etc/php5/cli
```

It seems there are several problems here:
[LIST=1]
[*]php cli ignores changes to the config file it says it is using.
[*]php cli won't load the mysql extension using the command line flag
[*]php cli won't load the mysql extensions, while php apache will
[/LIST]

I'm really at a loss here, and I'd very much like it if someone in the know could help me figure out what's going on.  Thanks.

---

### Post by themichaek on 2007-03-10
I found the cause of the problem that I posted about above: upgrading to Edgy seems to have changed the permissions on the php.ini files to 600 (not sure of the particulars, I only know that php cli loaded mysql under Dapper) - thus, when I run php as my user from the command line, the php.ini is not read - but when I run php as the apache user, the conf is read with no problem.  I'm not sure what the initial permissions were on php.ini, but I have changed them to 644, and mysql and mysqli are now loaded from the command line.

Obviously, I should have thought to check this earlier, but it had not occurred to me that something this foolish would have been caused by an upgrade.  I experienced the same error on both my machines running Ubuntu - hopefully other users experiencing this problem will stumble on the solution more quickly.

---

### Post by mohdridha on 2007-03-21
I have done all the necessary steps mentioned earlier, and the phpinfo() page tells me that mysql and mysqli is working. 

After done all the steps, i have managed to get rid of this error message
```

Fatal error: Call to undefined function mysql_connect()

```

but now, i'm having more problems on the next statement of my php file.
This is the error code:
```

Fatal error: Call to undefined function mysql_create_db()

```

and this is my line that caused the error

```

mysql_create_db("wiley") or die(mysql_error());

```

Thanks in advance

---

### Post by cleojb on 2007-03-30
Hi everyone, I'm a new user to this Furum.

I have that same error message: 

"Fatal error: Call to undefined function mysql_connect() in /var/www/cjbTest/myConnect.php on line 16"

line 16: mysql_connect('host', 'uName', 'pw') or die(mysql_error()); 
line 17: mysql_select_db(dbName) or die(mysql_error());

I did check the php.ini file and uncomment:
extension=mysql.so

But I do not know the location of mysql.so. And if I don't have the file (mysql.so), where can I download it?

                                               I NEED HELP!!!

---

### Post by mohdridha on 2007-03-30
```
 sudo updatedb 
slocate mysql.so
```

---

### Post by jnewm on 2007-12-18
> **breen92uk said:**
> Excellent! A combination of the advice from Mirrorball and igeterrors has solved the problem for me - I uncommented the 'extension = mysql.so' line in the php.ini file and added a 'extension = mysqli.so' for good measure, then followed the steps given by igeterrors in Post #15. 

Cheers guys!

This worked for me on Gutsy when I couldn't get anything else to work...  Thanks so much!

---

### Post by flandercan on 2008-01-18
I simply found the following in the /etc/php5/cli/php.ini

***;extension=mysql.so***

Removed the rem 

***extension=mysql.so***

and my script ran without error.

flandercan.....

---

### Post by haplo_dk on 2008-12-15
It was a spell error in my php.ini as well - it said msql.so instead of mysql.so

Now the error.log sais:

PHP Warning:  Module 'mysql' already loaded in Unknown on line 0

---

### Post by neobadandy on 2009-06-25
I couldnt find out how to make mysql work with php, stupid msql.so or mzsql.so or whatever and extention thing in php ini file, nomatter what nothing worked.

Solution to My problem:

to install everything perfect I typed 

 sudo apt-get install apache2 mysql-server mysql-client php5 php5-mysql

worked for me magically, good luck, this is a pain in the §"$"ing ***** to install on ubuntu and on windows, just getting mysql and php to work together or "combine" is a bi7(h if you dont know what your doing, good luck.

---

