---
title: "Is this the right php.ini modification? your thoughts"
date: 2008-11-07
forum: New to Ubuntu
---

### Post by Lakeside on 2008-11-07
At the Joomla installation page (if you`re familiar with Joomla! CMS- and the joomla folder is in my var/www or web root) I get stuck right off the bat, with:  `MySQL Support- no``and  `configuration.php - No`
I`m told I have to adjust something in my php.ini file to fix this. Could someone please tell me (as I`m new to all this, but there is a dim glimmer..) if 1) I should use the php.ini file located: etc/php5/apache2/php.ini, or etc/php5/cgi/php.ini. I was advised I could `run php as a module, (ant that most people do) so I should use the apache2 directory one. Also 2) how exactly would I type  ru (run) code (php as module) I was given the command, but it didn`t work, think I misunderstood.  and 3) Here is the php.ini modification I got from another site, please tell me if you can, should I be using it?? To summarise, to support legacy PHP applications, we should install the mysql API, while to support future PHP applications, we should install the new mysqli API. The best solution is to install both.

   1. In the php.ini file, replace the line:

      extension_dir = "./"

      with

      extension_dir = "./ext"

      Or to reflect where your extension DLL files are for PHP 5, they are usually in C:\PHP\ext (hence the relative path "./ext" should work fine).
   2. In the php.ini file, replace:

      ; extension=php_mysql.dll

      with

      extension=php_mysql.dll

      Or if it is not already there, then add it in the same section as the other extension files listed.
   3. Now add:

      extension=php_mysqli.dll

      To the extension section of the php.ini file, to enable the mysqli extension.

Reload the PHP info page, and scroll down until you find a section on mysql and another on mysqli. A lot to ask, I know, but..I`m *almost*there lol thanks

---

### Post by JeppeM on 2008-11-07
woah, lots of things here.. First off, Hello :) I have to decrypt your post a bit to better understand it i think, it was a bit jammed packed with information :)
> **Lakeside said:**
> At the Joomla installation page (if you`re familiar with Joomla! CMS- and the joomla folder is in my var/www or web root)
You have a Joomla installion directly under /var/www, correct? Or is it in a subfolder to that?

> **Lakeside said:**
> I get stuck right off the bat, with: `MySQL Support- no``and  `configuration.php - No`
I`m told I have to adjust something in my php.ini file to fix this. Could someone please tell me (as I`m new to all this, but there is a dim glimmer..) if 1) I should use the php.ini file located: etc/php5/apache2/php.ini, or etc/php5/cgi/php.ini. I was advised I could `run php as a module, (ant that most people do) so I should use the apache2 directory one.
How did you install apache and php? Let's start off by making sure that php works in apache, make a file called info.php and add the following to it:

[PHP]<?php
phpinfo();
?>[/PHP]

And then place it in /var/www/phptest/ (you'll need to make the phptest directory), and then go to [http://localhost/phptest/info.php](http://localhost/phptest/info.php) - If Apache supports php, you'll get a long page with a lot of information. Otherwise, you'll either get a blank page, or a an error.

If you got the correct page with all the information, please post the values of these two things: **Server API** and **Configuration File (php.ini) Path**. The last one is the correct path to your php.ini file :)

> **Lakeside said:**
> Also 2) how exactly would I type ru (run) code (php as module) I was given the command, but it didn`t work, think I misunderstood.
What command do you wish to run? Normally, with php as an Apache module, you have to "run" the code as a .php file from your webbrowser, and not from the command line. To run php code from the commandline, you should install php5-cli (*sudo apt-get install php5-cli* from the commandline i think) (CLI stands for Command Line Interface), but take notice that the two PHP installations (CLI and and apache module) will not be the same isntallation of PHP, which means you they'll most likely have different php.ini files, and might work differently...

> **Lakeside said:**
> and 3) Here is the php.ini modification I got from another site, please tell me if you can, should I be using it?? To summarise, to support legacy PHP applications, we should install the mysql API, while to support future PHP applications, we should install the new mysqli API. The best solution is to install both.

   1. In the php.ini file, replace the line:

      extension_dir = "./"

      with

      extension_dir = "./ext"

      Or to reflect where your extension DLL files are for PHP 5, they are usually in C:\PHP\ext (hence the relative path "./ext" should work fine).
   2. In the php.ini file, replace:

      ; extension=php_mysql.dll

      with

      extension=php_mysql.dll

      Or if it is not already there, then add it in the same section as the other extension files listed.
   3. Now add:

      extension=php_mysqli.dll

      To the extension section of the php.ini file, to enable the mysqli extension.

Reload the PHP info page, and scroll down until you find a section on mysql and another on mysqli. A lot to ask, I know, but..I`m *almost*there lol thanksI don't think you can use this information. .dll files are for windows, not for linux. If the phpinfo page worked above, then scroll down and see if you can find a select called **MySQL Support** and one called **MysqlI Support**. If not, then post back with the steps you took to install mysql, apache and php on your computer :)

By the way, are you installing on your own computer for personal use, or on a server for public use?

---

### Post by freak42 on 2008-11-07
I am no expert in these things.

But the modifications proposed above are not working on ubuntu for sure (the .dll file type is typically only used on windows)

You talk about using apache (is joomla a php cms manager?). If so there are many tutorials out there that help you installing and configuring apache, php and mysql to run and work together in Ubuntu. (It's actually not that hard to get done, I did it a while ago, you just install the right packages and you might to have to do so mild configs). Oh a good keyword for searching apache php mysql and linux related things is 'lamp' or 'lamp-server'

hth 

matthias

---

### Post by Lakeside on 2008-11-07
Well I`ll try to answer without ending up in another looong post (sorry about that :oops: I should have said first off, that I installed Hardy Heron Ubuntu, the *server* edition from a boot disk.  I just clicked the choices, and then later installed php5, Mysql, and  Apache2 from the Synaptic Package Manager, then either downloaded with apt get etc. other needed things, as suggested from guides, forums etc. and enabled others from the synaptic Pack. Man.
I did do the phpinfo.php thing, but I forgot to create a folder for it, I put it in localhost, and access it at localhost/phpinfo.php, probably a really dumb thing to do. Thanks for the tip about the .dll windows files, I should have noticed the .dll extension looked familiar. Just as well I was not able to save those changes I made to that php.ini file! But anyway,this is the Configuration File Path to that php.ini /etc/php5/apache2, and server API is Apache 2.0 Handler (but this is info from phpinfo.php before I put it in a folder called phptest

---

### Post by JeppeM on 2008-11-07
Doesn't really matter where you put the file, i just added it to the folder phptest to make sure it wouldn't collide with the Joomla installation... Ok, so now we at least know what php.ini file you should use. And "Apache 2.0 Handler" means that you have installed php as an apache module...

If you, during the server installation, selected to install LAMP (Linux apache MySQL PHP), then your PHP installation should have mysql support (could you verify this by looking in the phpinfo output again, and search for mysql support as i said in my other post?)

Next off, what tutorial (if any) did you follow when you tried to install joomla? And how far do you get before you get the errors you talked about?

---

### Post by Lakeside on 2008-11-07
Thanks for your patience JeppeM and Freak42. Sorry I did not include the mysql support info, I just was not sure what you meant by that, but could it be this?: **additional .ini files parsed 	/etc/php5/apache2/conf.d/mysql.ini, /etc/php5/apache2/conf.d/mysqli.ini, /etc/php5/apache2/conf.d/pdo.ini, /etc/php5/apache2/conf.d/pdo_mysql.ini ** thanks again:)
*edit* I followed the standard installation guide (Joomla 1.5.7)

---

### Post by JeppeM on 2008-11-07
Hehe, no problem at all :) 

Doesn't it say anything about mysql support in the phpinfo? When i see mine, i have one section called MySQL and one called MySQLi (see attached screen shot).

could you please link to the toturial you followed, and tell us which step you're stuck at? Just so we can get a feeling of what you have done, and what you haven't done...

---

### Post by Lakeside on 2008-11-07
> **JeppeM said:**
> Hehe, no problem at all :) 

Doesn't it say anything about mysql support in the phpinfo? When i see mine, i have one section called MySQL and one called MySQLi (see attached screen shot).
 Boy, I wish! Must have really messed up then :( This is the link for the guide I followed: [http://help.joomla.org/content/category/48/268/302/](http://help.joomla.org/content/category/48/268/302/) and here is where I got stuck, quite early on: - MySQL Support   No   
configuration.php Writable No You can still continue the installation as the configuration settings will be displayed at the end. You will have to manually upload the code. Click in the text area to highlight all of the code and then paste into a new text file. Name this file 'configuration.php' and upload it to your site root folder.
#Display errors: no  Other than those, everything else was yes.

Just one last thing (not sure if this is relevant to the mysql problem) after reading a suggestion to set mysql password on Ubuntu 8.04 ( a tut about installing LAMP  I enter this at terminal: ~$ mysql -u  root
and see this:  ERROR 2002 (HY000): Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)  And now I am going to bed, as I have gotten a very bad flu.

---

### Post by JeppeM on 2008-11-08
> **Lakeside said:**
> Boy, I wish! Must have really messed up then :( This is the link for the guide I followed: [http://help.joomla.org/content/category/48/268/302/](http://help.joomla.org/content/category/48/268/302/) and here is where I got stuck, quite early on: - MySQL Support   No   
configuration.php Writable No You can still continue the installation as the configuration settings will be displayed at the end. You will have to manually upload the code. Click in the text area to highlight all of the code and then paste into a new text file. Name this file 'configuration.php' and upload it to your site root folder.
#Display errors: no  Other than those, everything else was yes.

Just one last thing (not sure if this is relevant to the mysql problem) after reading a suggestion to set mysql password on Ubuntu 8.04 ( a tut about installing LAMP  I enter this at terminal: ~$ mysql -u  root
and see this:  ERROR 2002 (HY000): Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)  And now I am going to bed, as I have gotten a very bad flu.
Ok, to fix the easy error of configuration.php not writeable, make a file called configuration.php in /var/www/ and then right click it, go to properties and then to permissions and select "Read and Write" for all of the options (there's a better way of doing this, but it's a bit harder, and i don't want to confuse you with that right now) :)

Erhm, i think your problem with MySQL might be related to MySQL not being started correctly... Could you try to do this in the terminal, and then post back with the result of it:

```
/etc/init.d/apache2 restart
/etc/init.d/mysql restart
```

I might be *apache* instead of *apache2*, and it might be *mysqld* instead og *mysql*, i dont have my ubuntu server installation here at home, so i can't check it...

Hope you get better, being sick is never fun :)

---

### Post by Lakeside on 2008-11-08
Well, you guys have brought me half way there!! So nice not to see the red `no` for mysql support. I used the first options (apache2 and mysql) you mentioned and it worked!  I was having a time with the configuration.php, but found a work around (created it in /var then moved it to www) When I am in var/www and do  ls -l, I see I correctly set the permissions for configuration.php to rw rw rw...but I still have that red `no` in the Joomla install for configuration.php.

---

### Post by JeppeM on 2008-11-08
> **Lakeside said:**
> Well, you guys have brought me half way there!! So nice not to see the red `no` for mysql support. I used the first options (apache2 and mysql) you mentioned and it worked!  I was having a time with the configuration.php, but found a work around (created it in /var then moved it to www) When I am in var/www and do  ls -l, I see I correctly set the permissions for configuration.php to rw rw rw...but I still have that red `no` in the Joomla install for configuration.php.
I just read in the Joomla install guide that you can ignore the configuration.php error and then just edit it later on with the information you get at the end of the install... Read more [here]("http://help.joomla.org/content/view/1945/302/"). I actually think you're there mate, try to finish the installation now, and hopefully everything will work :)

---

### Post by Lakeside on 2008-11-08
Yes, I should probably do that :) I think I was more annoyed at myself for not being able to create the file directly in the www directory (had to create it elsewhere and move it there) and that I didn`t seem to be able to set permissions for the www dir., I always get arguments,so I`m doubting that completely understand how to do these things (I still had the red `no` for some reason,  even after setting file permissions...) but ya, I should go have fun with Joomla! There is just one more problem, and from what I`ve read before on Joomla forums, it should be fixed, but not sure if it`s a Jooomla or Linux thing: I still have a red check, `Display errors off` (how should be) is `òn`.

---

### Post by JeppeM on 2008-11-08
> **Lakeside said:**
> Yes, I should probably do that :) I think I was more annoyed at myself for not being able to create the file directly in the www directory (had to create it elsewhere and move it there) and that I didn`t seem to be able to set permissions for the www dir., I always get arguments,so I`m doubting that completely understand how to do these things (I still had the red `no` for some reason,  even after setting file permissions...) but ya, I should go have fun with Joomla! There is just one more problem, and from what I`ve read before on Joomla forums, it should be fixed, but not sure if it`s a Jooomla or Linux thing: I still have a red check, `Display errors off` (how should be) is `òn`.
Ah, thats easy to fix :) Do this from the terminal:

```
gksudo gedit /etc/php5/apache2/php.ini
```

And then locate the line where is says *display_errors* and change that to on instead of off, and then save teh file, and restart apache again :) 

the **gksudo** command lets you run graphic applications (in the GUI instead of the commandline) as root (linux superuser-mode). **gedit** is the default editor for text files and so forth :)

hopefully this will fix the display errors thing :)

---

### Post by Lakeside on 2008-11-08
Cool, learned one more thing (very useful command) and I did it, and was able to save (so obviously I have correct permission set for this file, to write to it..) but  :( still have that error on install (and I closed the page, and went back there fresh. Also, I had put it wrong- display errors were supposed to be `off` and they are `on` but I adjusted accordingly. Whew! thanks for staying with this and all your patience so far :)

---

### Post by JeppeM on 2008-11-08
> **Lakeside said:**
> Cool, learned one more thing (very useful command) and I did it, and was able to save (so obviously I have correct permission set for this file, to write to it..) but  :( still have that error on install (and I closed the page, and went back there fresh. Also, I had put it wrong- display errors were supposed to be `off` and they are `on` but I adjusted accordingly. Whew! thanks for staying with this and all your patience so far :)
You need to issue the **/etc/init.d/apache restart** command to restart apache, not just go away from the page and back again :)

I didn't quite understand though, does your php.ini say *display_errors off* or *on* now?

Anyways, try the /etc/init.d command and then view the page again :)

---

### Post by Lakeside on 2008-11-08
Oh, I didnt mention sorry, I did restart the a*ache with your code
but now I different *roblems- I am having to use a different com*uter with missing keys (obviously because I have lost the GUI
to mine, I am now at the command line, and cant get back in, I asked about it here [http://ubuntuforums.org/showthread.php?t=975895](http://ubuntuforums.org/showthread.php?t=975895)
Maybe its just as well, I have lots of housework to catch u* on :)
*edit/ Ok, back on my computer, and back at my GUI, my desktop :) thanks to the great help on this forum (natch) And also, now when I go back into Joomla install, that red NO is now gone for `display errors on` (off, like it should be, yay) so I got your code to work, maybe all that rebooting made it finally show. So now you will really shake your head at me..I STILL can`t finsish install becasue, in all the time between when I installed the server, configured stuff, learnt some Linux, and tried to install Joomla, my puppy ate the paper with the MySql database info..that`s right. I set up the mysql username, password etc upon Hardy Heron server install, and now Joomla wants the info for the mysql and..I can`t remember it, d`oh!
That`s another post, and another day, but soon my site will be up. thanks so much again!

---

