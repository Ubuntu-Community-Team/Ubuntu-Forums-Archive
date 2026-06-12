---
title: "Joomla all over"
date: 2008-11-18
forum: New to Ubuntu
---

### Post by susanpenter on 2008-11-18
Hi I have discovered Joomla as it was an optional script from my web host. 

I have searched around to no avail to find a really simple step by step guide to have it set up on my computer at the moment I am doing all the editing logged in to the site.

What I would like to achieve is to have Joomla (unless someone can convince me something like Drupal is better but still simple) installed on my  computer and then to have it installed on a few websites I manage (styled differently) and then be able to write articles and when appropriate upload them to more than one of the sites.

I am pretty good with HTML, I am OK with CSS for style (positioning never seems to work in all browsers for me) and I can do some basic php like the include fuunction. I am not very hot with the console as I use synaptic package manager by choice.

Thanks for the advice in advance,
Susan

---

### Post by Nepherte on 2008-11-18
You will have to setup apache + php + mysql: [https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP). Afterwards you unpack the joomla archive to apache root directory and install apache.

---

### Post by susanpenter on 2008-11-18
> **Nepherte said:**
> You will have to setup apache + php + mysql: [https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP). Afterwards you unpack the joomla archive to apache root directory and install apache.

Thanks, I have all three of them installed on my computer it i that unpacking business that I am clueless about.  I hoped Joomla might have been in the synaptic listings but it isn't.

When I said step by step I really meant it I am a user still rather than a programer.

---

### Post by susanpenter on 2008-11-18
OK I have found this page finally 
[http://www.blog.highub.com/linux/install-and-run-joomla-on-ubuntu/](http://www.blog.highub.com/linux/install-and-run-joomla-on-ubuntu/)

however when I get to step 2 I get the following error


ERROR 1045 (28000): Access denied for user 'root'@'localhost' (using password: NO)


Does anyone have any ideas please, I didn't bank on it taking a whole day to organise this.

Thanks

---

### Post by susanpenter on 2008-11-18
I have found another way of going about this here: 

[http://www.apachefriends.org/en/xampp-linux.html#377](http://www.apachefriends.org/en/xampp-linux.html#377)

however when it tells me to do this:

tar xvfz xampp-linux-1.6.8a.tar.gz -C /op

I get this error: 

susan@susan-desktop:~$ sudo tar xvfz xampp-linux-1.6.8a.tar.gz -C /opt
tar: xampp-linux-1.6.8a.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors
susan@susan-desktop:~$ 


I have been trying all day to simply set up a web server so that I can have Joomla on my computer as well as externally.  I must admit for the first time in months I'm beginning to miss the simplicity of Win XP installs.

I am discovering that all the things I would like to install at the moment are not in the synoptic package manager :(

Please can someone help me? I really don't want to pull a second nearly all nighter in a row to try and make his happen.

Many thanks

---

### Post by yogo on 2008-11-18
> **susanpenter said:**
> 

Please can someone help me? I really don't want to pull a second nearly all nighter in a row to try and make his happen.

Many thanks

If you are new to Joomla, just use it on your server, I have had Joomla for over three years and never been tempted to put it on my local machine.

HTH

---

### Post by susanpenter on 2008-11-18
Thanks Yogo it is already on my server but as i am about to install it onto 2 other websites and there are times that I will want to share content with them I 've been told that the best way is to host it locally and manage all the sites from one install.

I am fairly new to Joomla so if you know a different way of doing this I'd be grateful thanks,
Susan

---

### Post by yogo on 2008-11-18
> **susanpenter said:**
> Thanks Yogo it is already on my server but as i am about to install it onto 2 other websites and there are times that I will want to share content with them I 've been told that the best way is to host it locally and manage all the sites from one install.

I am fairly new to Joomla so if you know a different way of doing this I'd be grateful thanks,
Susan


Are you talking about three different databases?  I am not sure how you could manage all three from one install unless they all shared the same login and database.

I run a few different Joomla sites but each with it's own login.

I may be misunderstanding what you want or you know of something that is possible that I am not aware of.

---

### Post by susanpenter on 2008-11-19
> **yogo said:**
> Are you talking about three different databases?  I am not sure how you could manage all three from one install unless they all shared the same login and database.

I run a few different Joomla sites but each with it's own login.

I may be misunderstanding what you want or you know of something that is possible that I am not aware of.

Hi Yogo, you can find the tools to do it here: [http://extensions.joomla.org/component/option,com_mtree/task,listcats/cat_id,1790/Itemid,35/](http://extensions.joomla.org/component/option,com_mtree/task,listcats/cat_id,1790/Itemid,35/)

I just wish I could have it installed on my computer then I could work much faster that having to wait for web speeds.

---

### Post by yogo on 2008-11-19
> **susanpenter said:**
> Hi Yogo, you can find the tools to do it here: [http://extensions.joomla.org/component/option,com_mtree/task,listcats/cat_id,1790/Itemid,35/](http://extensions.joomla.org/component/option,com_mtree/task,listcats/cat_id,1790/Itemid,35/)

I just wish I could have it installed on my computer then I could work much faster that **having to wait for web speeds**.


I was not aware of that extension.  Thanks

Are you on dial up?  In response to what I bolded above.

---

### Post by Nepherte on 2008-11-19
> **susanpenter said:**
> I get this error: 

susan@susan-desktop:~$ sudo tar xvfz xampp-linux-1.6.8a.tar.gz -C /opt
tar: xampp-linux-1.6.8a.tar.gz: Cannot open: No such file or directory

It's
```
tar xvfz xampp-linux-1.6.8a.tar.gz -C /opt
```
assuming you're following that guide.

Honestly I would just install apache + php + mysql separately instead of bundled in lamp. I've written instructions for it in the past. You can find them here: [http://www.nepherte.be/linux/setup-apache-php-and-mysql.html](http://www.nepherte.be/linux/setup-apache-php-and-mysql.html) They were written with Ubuntu 8.04 in mind, but they won't differ that much for 8.10 I guess.

You can get the latest Joomla with this command:
```
wget http://joomlacode.org/gf/download/frsrelease/8897/32886/Joomla_1.5.8-Stable-Full_Package.tar.gz
```
Afterwards you'll need to unpack Joomla to /var/www:
```
sudo tar xvfz Joomla_1.5.8-Stable-Full_Package.tar.gz -C /var/www
```
Since joomla version 1.5.0, you also need a ftp server running. You can find instructions here: [http://ubuntuforums.org/showthread.php?t=79588](http://ubuntuforums.org/showthread.php?t=79588)

From then on, you can install joomla using your web browser: [http://localhost/](http://localhost/)

---

### Post by susanpenter on 2008-11-19
> **yogo said:**
> I was not aware of that extension.  Thanks

Are you on dial up?  In response to what I bolded above.

No broadband but wireless, with the computer 2 floors above the box, I'm waiting for my brother to install a cable instead as I should be receiving 8mb broadband but I'm sure it is nothing like that!

---

### Post by susanpenter on 2008-11-19
> **Nepherte said:**
> It's
```
tar xvfz xampp-linux-1.6.8a.tar.gz -C /opt
```
assuming you're following that guide.

Honestly I would just install apache + php + mysql separately instead of bundled in lamp. I've written instructions for it in the past. You can find them here: [http://www.nepherte.be/linux/setup-apache-php-and-mysql.html](http://www.nepherte.be/linux/setup-apache-php-and-mysql.html) They were written with Ubuntu 8.04 in mind, but they won't differ that much for 8.10 I guess.

You can get the latest Joomla with this command:
```
wget http://joomlacode.org/gf/download/frsrelease/8897/32886/Joomla_1.5.8-Stable-Full_Package.tar.gz
```
Afterwards you'll need to unpack Joomla to /var/www:
```
sudo tar xvfz Joomla_1.5.8-Stable-Full_Package.tar.gz -C /var/www
```
Since joomla version 1.5.0, you also need a ftp server running. You can find instructions here: [http://ubuntuforums.org/showthread.php?t=79588](http://ubuntuforums.org/showthread.php?t=79588)

From then on, you can install joomla using your web browser: [http://localhost/](http://localhost/)

Thanks for that, I have the 3 packages installed already so I followed your 2 bits of code, it downloaded and installed but when I go to local host I just get a message saying it works!

Do you know what could have gone wrong?
I get really annoyed when I can't do things - when I used XP I was the most knowledgeable person I knew but I am determined to learn...

---

### Post by Nepherte on 2008-11-20
"It works" is the default page of a apache2 installation, so it's a good thing that already works. Take a look at the directory /var/www and tell what's in it. The joomla diretories such as administrator, install, images and the joomla html should be right under /var/www. If not, you should move them to it.

---

### Post by susanpenter on 2008-11-20
> **Nepherte said:**
> "It works" is the default page of a apache2 installation, so it's a good thing that already works. Take a look at the directory /var/www and tell what's in it. The joomla diretories such as administrator, install, images and the joomla html should be right under /var/www. If not, you should move them to it.

Sorry for not getting back I've been persevering with the online editing.
All the Joomla directories are in var/www and yet it still just says it worked!

I am getting increasingly anxious to be able to work locally and update the remote host when I am happy rather than trial and error on site...

Cheers

---

### Post by Ripose on 2008-11-21
> **susanpenter said:**
> 
[]("http://www.apachefriends.org/en/xampp-linux.html#377")however when it tells me to do this:

tar xvfz xampp-linux-1.6.8a.tar.gz -C /op

I get this error: 

susan@susan-desktop:~$ sudo tar xvfz xampp-linux-1.6.8a.tar.gz -C /opt
tar: xampp-linux-1.6.8a.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors
susan@susan-desktop:~$ 


You are most likely getting this error because** /opt** is a root-user's directory OR it does not exist in your root directory. Since you did use sudo it must mean /opt is not there.
So create the opt directory as susan (does not HAVE TO be root) and try the command again, without sudo.

I am currently working on a new Ubuntu/LAMP/Joomla tutorial but it will be about another week before I'm done.

You can [EMAIL="ripose@gmail.com"]e-mail me[/EMAIL] if you wish, but please post follow ups here as well.:biggrin:

---

### Post by Ripose on 2008-11-21
Whoops! Sorry for my last post being out of place!

Susan, localhost only displays an "It Works!" from MySQL

To install Joomla you have to go to the Joomla directory with your browser.
Mine looks like this [http://localhost/Joomla_1.5.8](http://localhost/Joomla_1.5.8) this will bring up the Joomla install page(s).

NOTE: At the end of the install read the directions; DELETE the ENTIRE installation directory BEFORE you click on admin or view site!

To find your site later use the same address [http://localhost/Joomla_1.5.8]("http://localhost/Joomla_201.5.8") to see the site (called Front End) or go to [http://localhost/Joomla_1.5.8/administrator/]("http://localhost/Joomla_1.5.7/administrator/") to login to Control Panel (called Back End)

So just insert your Joomla directory name where mine is ( Joomla_1.5.8 )

---

### Post by bren21 on 2008-11-21
The "It works" is just a small index.html page that is in the /var/www directory by default. If you extracted joomla in that directory (meaning there are a bunch of files in /var/www and not a directory named joomla) then the index.html file is getting read instead of Joomla's index.php. If you have a Joomla directory, just type in localhost/directory_name and then follow the instructions to install.

---

### Post by susanpenter on 2008-11-21
> **bren21 said:**
> The "It works" is just a small index.html page that is in the /var/www directory by default. If you extracted joomla in that directory (meaning there are a bunch of files in /var/www and not a directory named joomla) then the index.html file is getting read instead of Joomla's index.php. If you have a Joomla directory, just type in localhost/directory_name and then follow the instructions to install.

I'm afraid it isn't working I tried [http://localhost/home/susan/joomla/](http://localhost/home/susan/joomla/) and I just got a google oops message.  I have file zilla installed which I use for uploading regular web pages is it a separate ftp I need?

I am trying to 'keep the faith' here I can see all the potential of Joomla but it is a bit embarrassing having to cut my teeth with the public watching every mistake I publish and then have to cancel.

I just wish this could be more simple like an install through synaptic!

....  The directory listed above is an unzipped one should I be going to a zipped package instead?

Sorry, I'm sure you guys could probably have solved this in minutes but I have been trying to resolve it for 2 days, time I could have been working on the site..

Please advise what I should try next,

many thanks

---

### Post by susanpenter on 2008-11-21
> **Ripose said:**
> You are most likely getting this error because** /opt** is a root-user's directory OR it does not exist in your root directory. Since you did use sudo it must mean /opt is not there.
So create the opt directory as susan (does not HAVE TO be root) and try the command again, without sudo.

I am currently working on a new Ubuntu/LAMP/Joomla tutorial but it will be about another week before I'm done.

You can [EMAIL="ripose@gmail.com"]e-mail me[/EMAIL] if you wish, but please post follow ups here as well.:biggrin:


I do have an opt folder installed it is at /opt with things like google and open office in it.

---

### Post by timcredible on 2008-11-21
if you have websites on a hosted system, then use their control panel, they probably have fantastico deluxe on it, and one of the apps that are on most all hosting sites is joomla.  click on the joomla choice, and 2 minutes later you have joomla working on that hosting site.  i don't believe there's any way to transfer the sql databases from your local pc to the hosting server, so i'm not sure why you're installing it locally.  i have 3 websites with joomla, 2 of them are on the same hosting site/account, just in different directories with different dns names.

---

### Post by timcredible on 2008-11-21
i also just found a livecd with joomla already on it, ready to go, based on ubuntu 8.04:
[http://www.turnkeylinux.org/](http://www.turnkeylinux.org/)

---

### Post by Ripose on 2008-11-21
Assuming XAMP is working, what this boils down to is you are using the wrong directory names.

---

### Post by Ripose on 2008-11-21
> **timcredible said:**
> i don't believe there's any way to transfer the sql databases from your local pc to the hosting server, so i'm not sure why you're installing it locally.

Yes you can transfer databases, and a serious webmaster would use a LOCAL site to test any changes before using them on a production site.

---

### Post by Sticky Icky on 2008-11-21
> **Nepherte said:**
> 
Honestly I would just install apache + php + mysql separately instead of bundled in lamp. I've written instructions for it in the past. You can find them here: [http://www.nepherte.be/linux/setup-apache-php-and-mysql.html](http://www.nepherte.be/linux/setup-apache-php-and-mysql.html) They were written with Ubuntu 8.04 in mind, but they won't differ that much for 8.10 I guess.

Hi I tried using your guide and was able to install Apache, PHP, MySQL and phpmyadmin but when I got to configuring MySQL I ran into a problem. When I entered the following into Terminal:
```
sudo mysql -u root
```I got this error
```
ERROR 1045 (28000): Access denied for user 'root'@'localhost' (using password: NO)
```Can you shed any light on this. Thanks in advance for your help.

p.s. Sorry if this is something obvious but I am a complete newbie to Ubuntu/Linux having only installed it a few days ago

---

### Post by susanpenter on 2008-11-21
Ok I fould an instruction blog advising removing php mysql apache and starting again.  I did this then followed Nepherte's guide to reinstall them all and set them up.  It started well I installed most in synaptic and the last couple through the console.  Now it has come to setting things up it is all going wrong.  Any advise will be really gratefully received.

Here is the code:

susan@susan-desktop:~$ cd/usr
bash: cd/usr: No such file or directory
susan@susan-desktop:~$ sudo apt-get install phpmyadmin
[sudo] password for susan: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libstrigiqtdbusclient0 libclucene0ldbl libgettext-ruby1.8 libwildmidi0
  libqca2 libsbigudrv0 libqimageblitz4 libjs-scriptaculous amarok-engine-xine
  libhpricot-ruby1.8 irb1.8 libamazon-ruby kdebase-runtime-data-common
  libcfitsio3 libgalago1.0-cil phonon mysql-gui-tools-common libopenspc0
  amarok-common libchm1 mimetex kde-icons-oxygen librasqal0 libgalago3
  wwwconfig-common kdelibs5-data cvs libwv-1.2-3 libtaglib2.0-cil vamps
  librevolution-ruby kstars-data libtunepimp5 libifp4 libhpricot-ruby
  phonon-backend-gstreamer libpoppler-qt4-3 libstreamanalyzer0 libphonon4
  libimage-size-ruby1.8 librevolution-ruby1.8 libcdaudio1
  kdebase-workspace-data libgeoip1 libavahi1.0-cil libkonq5-templates
  javascript-common libstreams0 libjs-prototype indi tinymce
  libopenssl-ruby1.8 libgsf0.0-cil kdebase-runtime-data libreadline-ruby1.8
  libnova-0.12-2 libwww-mechanize-ruby libnjb5 libofa0
  libwww-mechanize-ruby1.8
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  php5-gd php5-mcrypt
The following NEW packages will be installed
  php5-gd php5-mcrypt phpmyadmin
0 upgraded, 3 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/2917kB of archives.
After this operation, 10.6MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Preconfiguring packages ...
Selecting previously deselected package php5-gd.
(Reading database ... 225237 files and directories currently installed.)
Unpacking php5-gd (from .../php5-gd_5.2.6-2ubuntu4_i386.deb) ...
Selecting previously deselected package php5-mcrypt.
Unpacking php5-mcrypt (from .../php5-mcrypt_5.2.6-0ubuntu2_i386.deb) ...
Selecting previously deselected package phpmyadmin.
Unpacking phpmyadmin (from .../phpmyadmin_4%3a2.11.8.1-1_all.deb) ...
Setting up php5-gd (5.2.6-2ubuntu4) ...

Setting up php5-mcrypt (5.2.6-0ubuntu2) ...
Setting up phpmyadmin (4:2.11.8.1-1) ...
 * Reloading web server config apache2                                          apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
                                                                         [ OK ]
invoke-rc.d: unknown initscript, /etc/init.d/apache not found.
invoke-rc.d: unknown initscript, /etc/init.d/apache-ssl not found.
invoke-rc.d: unknown initscript, /etc/init.d/apache-perl not found.
Lighttpd not installed, skipping
invoke-rc.d: unknown initscript, /etc/init.d/lighttpd not found.

susan@susan-desktop:~$ cd/usr
bash: cd/usr: No such file or directory
susan@susan-desktop:~$ sudo mysql -u root
ERROR 1045 (28000): Access denied for user 'root'@'localhost' (using password: NO)
susan@susan-desktop:~$ mysql>SET PASSWORD FOR root@'localhost'=PASSWORD('xxxx');
bash: syntax error near unexpected token `('
susan@susan-desktop:~$ mysql> SET PASSWORD FOR 'root'@'localhost'=PASSWORD('xxxx');
bash: syntax error near unexpected token `('
susan@susan-desktop:~$ 


Thanks

---

### Post by Ripose on 2008-11-22
I have located open source stacks that will automate the install of LAMP & Joomla, the latest version installs Joomla 1.5.6 So you could use this automated stack and upgrade Joomla or you could just run the LAMP stack and install Joomla separately.

There are also stacks for Drupal, PhpBB, MediaWiki, WordPress & more.

[COLOR=Red]Warning:[/COLOR] I have not tested any of these stacks yet! I will be doing so in the next 2 days. So you can decide for yourself to try them now, or wait a few days until I post again with my test results.

View the stacks and instructions at [http://bitnami.org/stacks#joomla](http://bitnami.org/stacks#joomla)

[COLOR=Blue]Note:[/COLOR] Once you have installed a stack you can get separate MODULES from the above link. The modules will automate the install of different programs such as Joomla and Drupal using the already installed lamp. In other words you don't have to start from scratch to add each item.

[COLOR=Blue]Note:[/COLOR] I will be testing lampstack with Joomla 1.5.8  installed separately (by myself) since there is no stack or module available for 1.5.8 yet.

Wish me luck! :)

---

### Post by susanpenter on 2008-11-22
Well I'm beginning to wonder whether it is just me... or my computer! I downloaded the stack from the site mentioned above it has a .bin extension and my computer doesn't know what ot do with it. When I tried double clicking it I assumed it had been set up to work with the debian package installer but I guess not.  Could someone please let me know what to do with a bin file.

Many thanks

---

### Post by Nepherte on 2008-11-22
> **Sticky Icky said:**
> Hi I tried using your guide and was able to install Apache, PHP, MySQL and phpmyadmin but when I got to configuring MySQL I ran into a problem. When I entered the following into Terminal:
```
sudo mysql -u root
```I got this error
```
ERROR 1045 (28000): Access denied for user 'root'@'localhost' (using password: NO)
```Can you shed any light on this. Thanks in advance for your help.

p.s. Sorry if this is something obvious but I am a complete newbie to Ubuntu/Linux having only installed it a few days ago
The guide was written at the time the current Ubuntu version was 7.10. Since Ubuntu 8.04 and later, while installing mysql, you should have been asked to give the root mysql user a password. So instead of
```
sudo mysql -u root
```
you will have to type
```
sudo mysql -u root -p
```
and afterwards you are asked to type the password you gave during the installation of mysql.

---

### Post by Nepherte on 2008-11-22
> **susanpenter said:**
> 
susan@susan-desktop:~$ cd/usr
bash: cd/usr: No such file or directory
susan@susan-desktop:~$ sudo mysql -u root
ERROR 1045 (28000): Access denied for user 'root'@'localhost' (using password: NO)
susan@susan-desktop:~$ mysql>SET PASSWORD FOR root@'localhost'=PASSWORD('xxx');
bash: syntax error near unexpected token `('
susan@susan-desktop:~$ mysql> SET PASSWORD FOR 'root'@'localhost'=PASSWORD('xxx');
bash: syntax error near unexpected token `('
susan@susan-desktop:~$ 


Thanks
It's
```
cd /usr
```
Note the space between the two. Concerning the access denied, I gave the solution in my post right above this one. It also means that you don't have to set a password anymore for root (you should have been asked to give root a password during the installation of mysql).

P.S. You better remove your password in your post.

---

### Post by Ripose on 2008-11-22
> **susanpenter said:**
> Well I'm beginning to wonder whether it is just me... or my computer! I downloaded the stack from the site mentioned above it has a .bin extension and my computer doesn't know what ot do with it. When I tried double clicking it I assumed it had been set up to work with the debian package installer but I guess not.  Could someone please let me know what to do with a bin file.

Many thanks

Hi Susan, i just installed the Joomla1.5.6-lamp stack it took less than 3 minutes and did not produce a single error.
The only thing I don't like is the directory structure it uses, since it not quite standard, BUT it all works. I did not have to screw around with ANY Apache, MySql, PHP OR Joomla settings. Answer 5 VERY simple questions and away you go!

1) Change permissions on the BitNami file you downloaded
**2)** **RENAME the file AND DELETE the .bin extension**
3) Run the renamed file, you can just double-click if you are using a file browser
4) Answer the simple questions
5) Your Web Browser will open - Click the link near the top of the page
6) WAIT :popcorn: it takes a minute to set up the database
7) PRESTO Apache, MySql, PHP, your database and Joomla are all working:)

**[COLOR=Blue]NOTE:[/COLOR]** If you are using Ubuntu 64 bit you MAY have to install **ia32-libs** for the above steps to work.

**[COLOR=Blue]NOTE:[/COLOR]** 1) Bookmark your Joomal website when it pops up (this is your Front End).
2) In the address bar ADD administrator to the end of the address; it should look like this [http://127.0.1.1:8080/joomla/administrator](http://127.0.1.1:8080/joomla/administrator), go to this page
3) Enter the username and password you used in step 4 - Bookmark this page too (This is your Back End)

Hope this helps!
Have a great day everyone!:guitar:

---

### Post by susanpenter on 2008-11-24
> **Ripose said:**
> 
1) Change permissions on the BitNami file you downloaded
**2)** **RENAME the file AND DELETE the .bin extension**
3) Run the renamed file, you can just double-click if you are using a file browser
4) Answer the simple questions
5) Your Web Browser will open - Click the link near the top of the page
6) WAIT :popcorn: it takes a minute to set up the database
7) PRESTO Apache, MySql, PHP, your database and Joomla are all working:)



Thanks Ripose I thought I was sorted then.  I launched it in Nautilus as Firefox didn't want to navigate through my files. The launcher started and I told it to install in my home directory using 8080 as this is what yours said.  It seemed to all be installing fine until I got some errors and then it uninstalled, at no point did it open my browser.
I then tried to install it to var/www and it says that I don't have permission to install it there.

I feel sure I can get this to work if I can solve these blips.

Please could you confirm is there a particular folder ie var/www it should be installed in.

How do I tell it to let me to do that? if so

do I need to use a particular file ie 8080 and if so where do I find this out.

Once again sorry if these should be obvious

Susan

---

### Post by Ripose on 2008-11-24
Hi Susan.

Sorry for the confusion, the "**:8080**" is a the default PORT number used by the bitnami install, you DO NOT enter it into your install path! You only use it in the address bar AFTER the install is complete to view your website, ie [http://127.0.1.1:8080/joomla](http://127.0.1.1:8080/joomla) opens the front page of your site.

Although /var/www may be the "normal" directory, you will have fewer problems with permissions if you install into the default bitnami directory /home/susan/joomla (or something very similar). This is because /var/www belongs to ROOT and /home/susan belongs to YOU.

I have steps 5 & 6 reversed in my post. So the waiting part comes right after step 4 at which time your PC may seem to frozen, JUST WAIT a few minutes.

Edit: Please note I stated to use a FILE browser (Nautilus) not a WEB browser, in Step 3
Note: Change permissions (Step 1) should state "make the file executable".
 
Hope this clears up a few things!

---

### Post by susanpenter on 2008-11-25
> **Ripose said:**
> Hi Susan.

Sorry for the confusion, the "**:8080**" is a the default PORT number used by the bitnami install, you DO NOT enter it into your install path! You only use it in the address bar AFTER the install is complete to view your website, ie [http://127.0.1.1:8080/joomla](http://127.0.1.1:8080/joomla) opens the front page of your site.

Although /var/www may be the "normal" directory, you will have fewer problems with permissions if you install into the default bitnami directory /home/susan/joomla (or something very similar). This is because /var/www belongs to ROOT and /home/susan belongs to YOU.

I have steps 5 & 6 reversed in my post. So the waiting part comes right after step 4 at which time your PC may seem to frozen, JUST WAIT a few minutes.

Edit: Please note I stated to use a FILE browser (Nautilus) not a WEB browser, in Step 3
Note: Change permissions (Step 1) should state "make the file executable".
 
Hope this clears up a few things!

Thanks, I hope this will be my last query on this subject but when it askes for the Apache Webserver port the number 8080 is automatically entered but it says it can't bind the given number and select a new one so I would like to know how I find what number to give - or can I just make up a number between certain perameters

Thank You

---

### Post by Ripose on 2008-11-25
I am not very familiar with all of Apache's settings, but here are some things to check.

1 - Are you running Skype?
2 - Do you already have Apache installed from a previous attempt at setting up Joomla?
3 - Do you have a firewall?
4 - Did you run lampstack more than once?
5 - Did you install another server other than Apache?
6 - Post the EXACT error message.

You are getting this error because 8080 is already in use OR it being blocked.

I really have no idea what would happen if you just tried another port, such as 8081. Probably you would have to change the settings in other files such as HTTPD.conf ???

Isn't this stuff fun Susan! :rolleyes:

---

### Post by Olivier2371 on 2008-11-25
XAMPP is an easy to install Apache distribution containing MySQL, PHP and Perl. XAMPP is really very easy to install and to use - just download, extract and start.

[http://www.apachefriends.org/en/xampp-linux.html]("http://www.apachefriends.org/en/xampp-linux.html")

that should sort you out if get into any problem.

By the way jooomla is not a website it is a CMS.

---

### Post by Ripose on 2008-11-25
Re-installing Apache etc. again won't be much help if the problem(s) is another setting/file/code etc.

> By the way jooomla is not a website it is a CMS.     Does this mean I can't tell people to visit my Joomla site? :confused:
Do I have to tell them to go to my Joomla CMS? :confused:
Does this mean Joomla does not display web pages, that my website, errrr sorry, CMS cannot be seen with a WEB Browser? :confused:
Where do I download a CMS browser? :confused:

Joomla CMS still generates website pages and if it does that I can call it a website if I want. :popcorn:

BTW Why do people say "cement" when they are actually referring to "concrete"? I guess you can't walk on a sidewalk unless you use the correct term. :lolflag:

---

### Post by susanpenter on 2008-11-25
> **Ripose said:**
> 

1 - Are you running Skype?
2 - Do you already have Apache installed from a previous attempt at setting up Joomla?
3 - Do you have a firewall?
4 - Did you run lampstack more than once?
5 - Did you install another server other than Apache?
6 - Post the EXACT error message.



Answers:
1 - no
2 - yes at least 2 failed attempts + gallery2 seemed to be using it as well although I don't know how to access it!
3 - no - I gave them up when I chucked out xp
4 - quite possibly in between tearing my hair out! 
5 - I don't think so....
6 - warning box saying: Unable to bind to the given port number. Please select another one


What I am really wanting to do is have a local web server where I can install local versions of Joomla, Wordpress and any other mysql databases etc I want to use remotely so that I can set things up here and export them when I am happy with them.

one day niggles are fun but week long traumas are less so  ](*,)

I am happy that I have people who can help though....  thanks

---

### Post by Olivier2371 on 2008-11-25
susanpenter,

No to people whom want to visit your site, for them it will look like a website.

I was only trying to point the deference between a normal website that have multiple pages and joomla which only uses templates.

Don't worry you'll be fine:)

I apologies if I confused you.

---

### Post by Ripose on 2008-11-26
Olivier, sorry I was just trying to inject some humor, not insult you!

Susan, let's look back to the beginning of this post. Message #4 is where your problems started, the procedure that you followed is over-complicated for most newcomers to Linux, (although purists will tell you it's the only way). The web page you followed here is also inaccurate.

The method you tried in message #5 is also too complicated and it does not describe anything about permissions & directories.

Message #13, you had everything installed but you were accessing the WRONG directory.

Message #19, again you were trying to access the wrong directory. You also asked if you need a separate FTP, and another poster told you did, this is NOT true of Joomla anymore. Actually if you try to enable FTP in Joomla on your Hosted Server you will (should) get an error message, as FTP access is a huge security risk this way. Yes FileZilla is FTP but it is NOT the same thing, so go ahead and use FileZilla or Firefox ftp.

Message #26, you were trying to "cd/usr" which did not work because you omitted the space "cd(space)/usr". You also used "sudo apt-get phpmyadmin", which installed unecessary packages, probably in the wrong directories, since you ran this from your Desktop directory.

Message #35, something is already using port 8080, i.e. Gallery 2 or a prior XAMP, LAMP, Synaptic install.
________________________________________________________________________________

You need to get rid of the garbage from the previous failed setups!   
________________________________________________________________________________

I will continue this tomorrow, sorry I need to get some sleep.

BTW I have used Microsoft products since MSDOS (before Windows) and I will never go back. Linux is far better!

---

### Post by susanpenter on 2008-11-26
Thanks Ripose, have some sleep - you deserve it - and I will look forward to the definative way to clear out the rubbish and set things up from scratch.

Many thanks for taking the time - it's funny amongst my friends (and when talking about computing in general) I am the most experienced person I know that everyone else turns to.  It is strange when using Linux that I am now turning to other people but then as I see it there are three broad levels:

1. user
2. installer
3. developer

and I would like to think I am still pretty efficient with number 1.

Cheers
Susan

---

### Post by Olivier2371 on 2008-11-26
Ripose,

It's all good man. Peace and love.

But you know it would have been easier to remove everything and just install
Xampp. It took me 5 minutes last night to install it.

Your knowledge of Ubuntu is far better than mine.

---

### Post by Ripose on 2008-11-26
Hey Olivier, you are right about un-installing and starting again. But you know how it goes,,, it does not work so you try a little fix,,, which requires a fix,, etc. :confused:

Everyone would appreciate your input on how to get rid of all the garbage. So feel free to say if anything below is incorrect or "not the best/easiest method". :)
--------------------------------------------------------------------------------------------------------------------------
Below is the code to see what is using the tcp ports.
Note: The first entry is MySQL using port 3306
The last entry (httpd) is Apache using port 8080

```
ripose@Ripose-Linux:~$ sudo netstat -natp
[sudo] password for ripose:
 
Active Internet connections (servers and established)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 0.0.0.0:3306            0.0.0.0:*               LISTEN      6468/mysqld.bin 
tcp        0      0 127.0.0.1:551           0.0.0.0:*               LISTEN      5201/cupsd      
tcp        0      0 162.154.4.600:63984     74.125.95.83:80         ESTABLISHED 6053/firefox    
tcp6       0      0 :::8080                 :::*                    LISTEN      6397/httpd

```Before you continue make a quick post with your output.
-------------------------------------------------------------------------------

Go to /home/susan/lampstack is there an uninstall program? If so run it.

Start Synaptic, click the STATUS button. Are there any entries for Installed - Residual Config - Obsolete, or Not Installed - Residual Config - Obsolete. If so click on the packages and set "Mark For Complete Removal". Click APPLY. If there are none all you will see is "ALL - INSTALLED - NOT INSTALLED", so nothing to remove here.
Click INSTALLED - Mark for complete removal any Apache, MySQL, PHP packages. Click APPLY.
Check the STATUS again to be sure everything is gone.

MORE TO COME!

---

### Post by susanpenter on 2008-11-26
OK here we go - geared up for the big one - I will have a web server! - by the way off subject I just got a handset upgrade for a G1 today!!!! :-)

Mine is far more complicated by the look of it:
susan@susan-desktop:~$ sudo netstat -nats
[sudo] password for susan: 
IcmpMsg:
    InType3: 598
    OutType3: 96
Tcp:
    61382 active connections openings
    112 passive connection openings
    554 failed connection attempts
    3855 connection resets received
    6 connections established
    1032567 segments received
    1082298 segments send out
    119052 segments retransmited
    22 bad segments received.
    6959 resets sent
UdpLite:
TcpExt:
    758 packets pruned from receive queue because of socket buffer overrun
    6035 TCP sockets finished time wait in fast timer
    101 time wait sockets recycled by time stamp
    3 packets rejects in established connections because of timestamp
    34633 delayed acks sent
    2 delayed acks further delayed because of locked socket
    Quick ack mode was activated 2239 times
    2098 packets directly queued to recvmsg prequeue.
    23 bytes directly in process context from backlog
    1594537 bytes directly received in process context from prequeue
    537929 packet headers predicted
    1198 packets header predicted and directly queued to user
    151842 acknowledgments not containing data payload received
    94394 predicted acknowledgments
    269 times recovered from packet loss by selective acknowledgements
    1 congestion windows recovered without slow start by DSACK
    1082 congestion windows recovered without slow start after partial ack
    143 TCP data loss events
    TCPLostRetransmit: 6
    2 timeouts after reno fast retransmit
    140 timeouts after SACK recovery
    12 timeouts in loss state
    343 fast retransmits
    23 forward retransmits
    228 retransmits in slow start
    19949 other TCP timeouts
    18 SACK retransmits failed
    18728 packets collapsed in receive queue due to low socket buffer
    2101 DSACKs sent for old packets
    398 DSACKs received
    1872 connections reset due to unexpected data
    3106 connections reset due to early user close
    14378 connections aborted due to timeout
    TCPDSACKIgnoredOld: 35
    TCPDSACKIgnoredNoUndo: 119
    TCPSpuriousRTOs: 7
IpExt:
    InTruncatedPkts: 976
    InMcastPkts: 113
    OutMcastPkts: 117
    InBcastPkts: 34597
    OutBcastPkts: 34597
susan@susan-desktop:~$

---

### Post by susanpenter on 2008-11-26
I have the following catagories:
All
Installed
Installed (Auto Removable)
Installed (local or Obsolete)
New in Repository
Not Installed
Nor Installed (Residual Config)  these don't say obsolete so I don't know whether to remove them or not?

---

### Post by susanpenter on 2008-11-26
I have uninstalled all files with references to them except mysql common as it would have taken things like Amarok with it, but I got the rest of the mysql things.

The catagories are still as they were before deletion.

Cheers

---

### Post by Olivier2371 on 2008-11-26
Sorry just finished eating.

waiting for repose as he is better at command line.

But personally I think going the xampp way would be the best way if you are new to server.

---

### Post by susanpenter on 2008-11-26
Thanks Olivier - I'll let you fight it out and I'll follow who can give the best idiot proof guide - NOT that I am an idiot!  :-)

---

### Post by gjoellee on 2008-11-26
If you have the requirements on the server to run Drupal, I would recommend that. It is as easy setting up a website with it as posting in this forum!!!!

Yahoo.com uses it
kshoster.net uses it
ubuntu.com uses it

---

### Post by mvalviar on 2008-11-26
+1 to xampp for linux

---

### Post by gjoellee on 2008-11-26
[www.drupal.org](www.drupal.org)

---

### Post by Olivier2371 on 2008-11-26
gjoellee

If you'd follow the discution, You would realize that for the moment we trying to make sure that every file from previous install has been removed.

And drupal!:(

Not for me. Sorry 

Go Joomla Go!!!!

---

### Post by gjoellee on 2008-11-26
oh...I better start reading posts more carefully :)

---

### Post by Ripose on 2008-11-26
Susan, your output was different because you entered **-nats** instead of **-natp**

BTW I have installed WAMP, LAMP, XAMP and BitNami joomla_lampstack. XAMP may be easy, but BitNami stacks are even easier!
I just installed Joomla & Drupal and BitNami Lamp stack, took less than 5 minutes for all 3.

---

### Post by susanpenter on 2008-11-26
what do I need to do next now then run a Bitnami stack or is there something else to do first?

cheers

---

### Post by Olivier2371 on 2008-11-26
Ripose,

That's great the other programs are fine as well.

---

### Post by susanpenter on 2008-11-26
sorry this is off topic, while I wait, but to solve another problem you don't happen to know of a way of checking which FF extension may be slowing me down?  If it is a big thing I'll start another thread

---

### Post by Olivier2371 on 2008-11-26
When you say FF extension are you about FireFox?

If so I have never heard of an FF extension slowing the system down.

Maybe I am wrong though.

I found out that if you are running a lot of extension/plugins, that firefox will slow down.

Are you running a lot of extensions/plugins?

---

### Post by susanpenter on 2008-11-26
well I think it is more slowing down the internet that the computer maybe, the screen starts going black for a while and then brightens up and all catches up with it's self.  I have several extensions so I though if there was a way to see what resources they were all using.

---

### Post by Olivier2371 on 2008-11-26
susanpenter,

Have look at:

System->Preferences->Screensaver

It might be on. turn it off by removing the tick in the bottom boxes.

---

### Post by susanpenter on 2008-11-26
I've done that, but it was set to go off when the system was idle but this slowing down happens when in use, maybe mid sentence or waiting for a site to load.


back on the subject should I be running the bitnami stack now?

---

### Post by Olivier2371 on 2008-11-26
yes go for it . Do you have the documentation for installation and configuration.

---

### Post by susanpenter on 2008-11-26
I've found the read me files on the net, I assume I do not have to match my login details with the ones I used on my remote site do I?

---

### Post by Olivier2371 on 2008-11-26
No. But make sure you keep it safe.

---

### Post by Ripose on 2008-11-26
Actually the FF slowdown is caused by Ubuntu, it occurs with Nautilus, Synaptic and others. I have not figured out why yet.
Good thought Olivier, but it's not the screensaver.

Susan: Did you run BiNami yet?
You never said what ports were being used via **sudo netstat -natp**

Drupal is definitely more difficult to learn than Joomla. I'm not sure which will be prove to best, I need to play with Drupal a little longer.

---

### Post by susanpenter on 2008-11-26
Sorry I disappeared off to begin the Christmas cake!

here is the display:
susan@susan-desktop:~$ sudo netstat -natp
[sudo] password for susan: 
Active Internet connections (servers and established)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 0.0.0.0:8080            0.0.0.0:*               LISTEN      12329/mysqld.bin
tcp        0      0 0.0.0.0:631             0.0.0.0:*               LISTEN      5073/cupsd      
tcp        0      0 127.0.0.1:32860         0.0.0.0:*               LISTEN      9265/gdl_indexer
tcp        0      0 192.168.2.2:42255       194.0.179.195:80        ESTABLISHED 8215/firefox    
tcp        1      1 192.168.2.2:35880       76.13.6.191:80          CLOSING     -               
tcp        1      0 192.168.2.2:34715       208.97.189.214:80       CLOSE_WAIT  6090/cli        
tcp        0      0 192.168.2.2:41718       208.69.34.231:80        ESTABLISHED 8215/firefox    
tcp        1      0 192.168.2.2:48710       74.125.79.111:995       CLOSE_WAIT  9254/gdl_fs_crawler
tcp        1      1 192.168.2.2:55657       216.200.40.144:80       CLOSING     -               
tcp        0      0 192.168.2.2:54950       208.69.34.231:443       ESTABLISHED 8215/firefox    
tcp        1      0 192.168.2.2:40805       79.170.40.230:80        CLOSE_WAIT  19499/f-spot    
tcp        0      0 192.168.2.2:43372       72.21.202.194:80        ESTABLISHED 8215/firefox    
tcp        0      1 192.168.2.2:36924       194.0.179.195:80        FIN_WAIT1   -               
tcp        0      0 192.168.2.2:46773       208.69.34.231:80        ESTABLISHED 8215/firefox    
tcp        0      0 192.168.2.2:49873       208.69.34.230:80        ESTABLISHED 8215/firefox    
tcp        1      0 192.168.2.2:37162       208.97.189.214:80       CLOSE_WAIT  6090/cli        
tcp        1      1 192.168.2.2:55668       216.200.40.144:80       CLOSING     -               
tcp        1      0 192.168.2.2:55321       208.97.189.214:80       CLOSE_WAIT  6090/cli        
tcp        1      1 192.168.2.2:37513       194.0.179.49:80         CLOSING     -               
tcp        0      0 192.168.2.2:59935       66.249.91.19:80         ESTABLISHED 8215/firefox    
tcp        1      0 192.168.2.2:37619       151.170.240.7:80        CLOSE_WAIT  6031/gweather-apple
tcp        0      0 192.168.2.2:52328       69.63.176.26:80         ESTABLISHED 8215/firefox    
tcp        1      0 192.168.2.2:41189       74.125.79.109:995       CLOSE_WAIT  9254/gdl_fs_crawler
tcp        0      0 192.168.2.2:33790       194.0.179.205:80        ESTABLISHED 8215/firefox    
tcp        1      0 192.168.2.2:39675       208.97.189.214:80       CLOSE_WAIT  6090/cli        
tcp        0     75 192.168.2.2:37314       151.170.240.7:80        LAST_ACK    -               
tcp6       0      0 :::631                  :::*                    LISTEN      5073/cupsd      
susan@susan-desktop:~$

---

### Post by Olivier2371 on 2008-11-26
Thanks for the though.

I have tried drupal and others CMS  but personally I stick with joomla.

---

### Post by Ripose on 2008-11-26
So did you run bitnami?

In your output is shows MySQL as using port 8080, but there is no entry for Apache.

Apache usually tries to install to 8080 and MySQL uses 3306 (normally, but not always).

---

### Post by susanpenter on 2008-11-26
This printout was from before I ran Bitnami I was waiting for feedback before going ahead, so I don't know what is using it when I deleated them all (except mysql common) I didn't delate that because it would take Amarok with it but do I need to deleate it anyway  - there must be something that is using 8080!

Shall I run it now or not?

---

### Post by Ripose on 2008-11-26
In your list MySQL common is on 8080, but you can still run XAMP or BitNami and try 8080, if it says NO try 8087 (recommended in another post).

Don't forget: You will have to include the port number in your URL i.e. [http://localhost:8087/joomla/](http://localhost:8087/joomla/)

Make note of ports used and messages that tell you where things are being installed (if any).

---

### Post by susanpenter on 2008-11-26
Well aren't I feeling all happy:

I have the following page opened saying welcome to Bitnami Joomla [http://127.0.1.1:8087/](http://127.0.1.1:8087/)
I can now access Joomla or my php login

A huge thank you!!!

I see it has installed the sample data - so my jobs tomorrow will be:

 trying to figure out how to remove the sample data without killing it.

learning how to get this version to sync with my external one

figuring out how to install other databases within my web server - I assume thee is no upper limit.

I think I need to go to bed before I fall down - it is 2am here!

---

### Post by Ripose on 2008-11-27
Glad to hear it worked out! :D BUT.... There is more. :rolleyes:

Did you install BitNami lampstack beta 1 and the Joomla MODULE or did you use joomla-lampstack. Hopefully the first method, but either way you need to upgrade from 1.5.6 to 1.5.8 VERY EASY if you do it now. Download the upgrade, unzip it and copy over the existing Joomla directory NOT THE LAMPSTACK/Joomla directory, go further in, Joomla is way down here: home/ripose/lampstack/apps/joomla/htdocs.
Copy the files there, Ubuntu will ask if want to MERGE the files, Click - "YES TO ALL" then it will ask if you want to REPLACE the files, Click "YES TO ALL".
Presto! You are upgraded.

There is an easy way to copy your hosted site to your local site instead of deleting all the sample content.... Install JoomlaPack 2 on your hosted site. (Read the description etc.)

Get 1.5.6 -> 1.5.8 upgrade here: (Second from top)
[http://joomlacode.org/gf/project/joomla/frs/?action=FrsReleaseBrowse&frs_package_id=4136](http://joomlacode.org/gf/project/joomla/frs/?action=FrsReleaseBrowse&frs_package_id=4136)

Get JoomlaPack Here:
[http://extensions.joomla.org/index.php?option=com_mtree&task=listcats&cat_id=1758&Itemid=35](http://extensions.joomla.org/index.php?option=com_mtree&task=listcats&cat_id=1758&Itemid=35)

This thread does not belong here anymore, it should move to joomla.org or joomlshack.com

):P

---

### Post by susanpenter on 2008-11-27
Thanks Ripost  - before I leave this threat:

the bad news is that I used the Joomla Lampstack I though I was meant to
the good news is it was version 1.5.8

the next bad news is that even though I copied down my username and password and used things I was comfortable with when I hit the link for myphp it keeps bringing up the box again and again saying either they are the incorrect details or my browser won't let me log in!

A question I is that I do not have a home/susan/lampstack/apps  etc
I have home/susan/joomla so can I still install other databases?

---

### Post by Olivier2371 on 2008-11-27
hello back,

Why would you need more than one database?

Just a though You do have a Hosting account and domain name?

---

### Post by susanpenter on 2008-11-27
Sorry Olivier,

I couldn't reply earlier it kept saying my ticket had expired!

I have 3 domains I currently manage soon to increase.

I'm wanting separate databases to house Joomla or Wordpress or whatever I choose for each locally so that I can work on them all on my computer then upload changes to the external sites when sorted.

Cheers,

Susan

---

### Post by wottam on 2008-11-27
Hi,

This is Antonio from the BitNami team :) The phpmyadmin user is 'Administrator', while the password is the one set during the installation.

Cheers

---

### Post by Ripose on 2008-11-27
**home/susan/joomla** is not the actual Joomla directory unless you changed the path during install.
Look in the directory you named above, you should find **/lampstack/apps/joomla/htdocs** Joomla is in the **htdocs** folder. Full path: **home/susan/joomla**[B]/lampstack/apps/joomla/htdocs

[/B]The first time you run phpmyadmin you have to use **administrator** as user name, and the same password you created during install.
This is covered in the docs.

I mentioned in a previous post that in order to install multiple DBs and Modules you need to use Lampstack Ver. 1 from BiNami, then install the Modules - Joomla, Drupal, Wordpress etc. It also states this on the BiNami download page.

I guess there was some confusion between Lampstack & Joomla_lampstack.

So you can either install new DB's manually using PhpMyAdmin and then install your new program (i.e. Wordpress) manually,,making sure to tell it where the DB is.
OR. You could uninstall joomla_lampstack, install Lampstack Ver. 1 and all of the modules (Joomla,Drupal,Wordpress) you want.

Go here: [http://bitnami.org/stack/lampstack](http://bitnami.org/stack/lampstack) to get LAMPStack Ver. 1
Go here: [http://bitnami.org/stacks#joomla](http://bitnami.org/stacks#joomla) click on the item you want in the MODULES category.

---

### Post by Vel-Tyno on 2009-02-02
Ok, I coming in a little late on this discussion, and I am trying to install this Bitnami Joomla stack.  I've installed and used Joomla in XP and Vista, so Ino what to do once I've got the stack installed.  But, I think I'm having an Ubuntu newbie problem with installing this.  

I've completed the first two steps (below) with no problem.  But, when I double-click on the file, I get nothing.  I don't know if there's some kind of security problem (I still haven't figured out exactly how Ubuntu's security system works) at work here or is there application I need to use to run this?
    
I would appreciate any help I can get.


Joe


1) Change permissions on the BitNami file you downloaded
**2)** **RENAME the file AND DELETE the .bin extension**
3) Run the renamed file, you can just double-click if you are using a file browser
4) Answer the simple questions
5) Your Web Browser will open - Click the link near the top of the page
6) WAIT :popcorn: it takes a minute to set up the database
7) PRESTO Apache, MySql, PHP, your database and Joomla are all working:)

---

### Post by Ripose on 2009-02-03
**[COLOR=#0000ff]Are you running 64 bit?[/COLOR]**
**[COLOR=#0000ff][/COLOR]** 
**[COLOR=#0000ff]NOTE:[/COLOR]** If you are using Ubuntu 64 bit you MAY have to install **ia32-libs** for the above steps to work.

---

### Post by Vel-Tyno on 2009-02-03
No, I am running Intrepid on 32-bit

---

### Post by Ripose on 2009-02-04
How did you change permissions? What are they now?
Who owns the file?

---

### Post by Vel-Tyno on 2009-02-07
> **Ripose said:**
> How did you change permissions? What are they now?
Who owns the file?
As instructed, from the terminal i wrote:


chmod 755 bitnami-joomla-1.5.9-0-linux-installer.bin

---

### Post by Ripose on 2009-02-07
Are you sure you installed **ia32libs**?

---

### Post by Vel-Tyno on 2009-02-07
I don't know.  Where would I find these?


Joe

---

### Post by Ripose on 2009-02-07
Just run your Synaptic Package Manger, **ia32libs** will be on the list, just install it. :)

---

### Post by Vel-Tyno on 2009-02-09
It's not there.  But, the only repositories I have are canonical and medibuntu.  Is there another repository, that I need to add?


Joe

---

### Post by Ripose on 2009-02-09
Hey Joe, yes you are right! You need to have the **Community-Maintained repository**.

Sorry, I didn't think of that when I posted. :redface:

---

