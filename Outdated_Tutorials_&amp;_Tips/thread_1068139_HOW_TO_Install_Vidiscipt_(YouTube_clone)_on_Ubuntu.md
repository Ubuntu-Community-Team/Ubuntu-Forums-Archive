---
title: "HOW TO Install Vidiscipt (YouTube clone) on Ubuntu 8.xx"
date: 2009-02-12
forum: Outdated Tutorials &amp; Tips
---

### Post by duffydack on 2009-02-12
This guide is confirmed working on Hardy, Intrepid and Jaunty Desktop or Server.  Earlier Ubuntu versions may work fine with this guide. Potential problems could be down to location/naming of Apache/MySQL/PHP and their configs.
I have tried to split this down into easy to swallow chunks, hence the overall length, so you should be able to adapt it to your version of Ubuntu and software with relative ease.
Make sure you have the extra repos added.  See [_Adding the Universe and Multiverse Repositories_]("https://help.ubuntu.com/community/Repositories/Ubuntu#head-5bbef89639d9a7d93fe38f6356dc17847d373096")
If you prefer the `bleeding edge` version of FFMPEG, or to fix issues with older versions, then follow this guide here [_How to compile latest FFMPEG/x264._]("http://ubuntuforums.org/showthread.php?t=786095")
I am starting off from a fresh install of Ubuntu and using defaults for packages to be installed.

before we start lets update the system
```
$ sudo apt-get update && sudo apt-get dist-upgrade
```

```
$ sudo tasksel install lamp-server
```
you will be prompted by
```
**New password for the MySQL "root" user:**
```
enter one and remember it.

```
$ sudo apt-get install unzip ffmpeg mencoder php5-ffmpeg php5-gd php5-curl lame
```

for 32bit ubuntu
```
$ wget http://downloads2.ioncube.com/loader_downloads/ioncube_loaders_lin_x86.tar.gz
```

for 64bit
```
$ wget http://downloads2.ioncube.com/loader_downloads/ioncube_loaders_lin_x86-64.tar.gz
```

```
$ wget http://vidiscript.com/release/VidiScript_v_0_4_3.zip
```

```
**_FOR 32bit_**
$ tar xvf ioncube_loaders_lin_x86.tar.gz

**_FOR 64bit_**
$ tar xvf ioncube_loaders_lin_x86-64.tar.gz

```

```
$ sudo mv ioncube /usr/local/bin/
$ unzip VidiScript_v_0_4_3.zip
$ sudo mv VidiScript_v_0_4_3/VidiScript/ /var/www/vidiscript
```

a few things to change now

```
$ sudo pico /etc/php5/apache2/php.ini
```
I`m going with the recommended config as stated on vidiscript site.  Find each of these and change to the values below
```
safe_mode = off
max_execution_time = 1000
max_input_time = 1000
open_basedir = 
upload_max_filesize = 200M
post_max_size = 200M
register_argc_argv = On
```

Now, still in the /etc/php5/apache/php.ini file, goto line 73 or look for something looking like.
```
; Enable the PHP scripting language engine under Apache.
engine = On

; Enable compatibility mode with Zend Engine 1 (PHP 4.x)
zend.ze1_compatibility_mode = Off

```

add the code in bold like so..
```
; Enable the PHP scripting language engine under Apache.
engine = On
**zend_extension = /usr/local/bin/ioncube/ioncube_loader_lin_5.2.so**
; Enable compatibility mode with Zend Engine 1 (PHP 4.x)
zend.ze1_compatibility_mode = Off
```

```
$ sudo a2enmod rewrite
```
```
$ sudo pico /etc/apache2/sites-enabled/000-default
```

you should see something similar to this
```
NameVirtualHost *
<VirtualHost *>
        ServerAdmin webmaster@localhost

        DocumentRoot /var/www/
        <Directory />
                Options FollowSymLinks
                AllowOverride None
        </Directory>
        <Directory /var/www/>
                Options Indexes FollowSymLinks MultiViews
                AllowOverride all
                Order allow,deny
                allow from all
        </Directory>


```

Set AllowOverride to all like so
```
NameVirtualHost *
<VirtualHost *>
        ServerAdmin webmaster@localhost

        DocumentRoot /var/www/
        <Directory />
                Options FollowSymLinks
                AllowOverride None
        </Directory>
        <Directory /var/www/>
                Options Indexes FollowSymLinks MultiViews
                **AllowOverride all**
                Order allow,deny
                allow from all
        </Directory>


```

```
$ mysql -u root --password=<MySQL password here>
create database vidiscript;
quit
$

```

```
$ cd /var/www/vidiscript
sudo chmod 777 data data/keys data/scroller/scroller.xml uploads uploads/thumbs/ uploads/avatars/ uploads/ads/ uploads/groupicons/ includes/settings.inc includes/badwords.inc

```

```
sudo /etc/init.d/apache2 restart && sudo /etc/init.d/mysql restart
```

Now from your browser goto [_http://localhost/vidiscript/install/_](_http://localhost/vidiscript/install/_) or if from a different PC on your network, [_http://ip.address/vidiscript/install_/](_http://ip.address/vidiscript/install_/)

You will see the vidiscript installation page.  Everything should be [COLOR="Green"]GREEN[/COLOR], if so proceed and click NEXT

```
Step 2 - Database Details


**Database name** 	vidiscript
**Host Name** 	localhost
**Login Username** 	root
**Login Password** 	<your sql password>
```

Click NEXT

```
Step 3 - Site Details And Admin Login

**Site Name** (anything) 	
**Site Folder** vidiscript 	
**Admin Username** 	   (anything you like, but remember)
**Admin Password** 	   (any password you choose, but remember)
**Admin Email Address** user@localhost.net

```
Click NEXT
and you are DONE,
```
Congratulations! Your new VidiScript site is installed and ready

Please delete the 'install' folder as soon as possible, you will see a warning on your site until you have done this.

Also change the file permissions on includes/settings.inc to 644, if you leave it writable it could be a security risk.

Click here to go to your VidiScript site
```
....Except before you click the link to your new site, do this first
```
sudo rm -rf /var/www/vidiscript/install/
sudo chmod 644 /var/www/vidiscript/includes/settings.inc

```

On the right hand side click **Site Settings** to configure it some.

Notes:
This guide is only meant to install and test the script on your own personal machines.  The script is best used (unless you have a ton of bandwidth on that home line!) with a dedicated hosting site which supports all the configuration needed.  More infos can be found on [_Vidiscript_]("http://www.vidiscript.com/")

---

### Post by duffydack on 2009-02-13
[SIZE="3"]**How to remove the top logo**[/SIZE]

This will remove the "Beta Vidiscript" logo at the top of your page and raise the tabs up.
```
$ sudo cp /var/www/vidiscript/templates/Mainstream/skin1.css /var/www/vidiscript/templates/Mainstream/skin1.css.old
sudo pico /var/www/vidiscript/templates/Mainstream/skin1.css

```
If you are using the dark/purple "AfterDark" template then
```
sudo cp /var/www/vidiscript/templates/AfterDark/skin2.css /var/www/vidiscript/templates/AfterDark/skin2.css.old
sudo pico /var/www/vidiscript/templates/AfterDark/skin2.css

```

Changes to be made

**From**
```
/* HEADER */
#header{
height: 144px;
overflow: hidden;
background: #626262 url(layout/skin1/header_bg_rep.jpg) repeat-x 0 bottom;
```

**To**
```
/* HEADER */
#header{
height: 39px;
overflow: hidden;
background: #626262 url(layout/skin1/header_bg_rep.jpg) repeat-x 0 bottom;
```

**From**
```
#tab-menu{
position: absolute;
height: 34px;
left: 15px;
top: 110px;
width: 960px;
overflow: hidden;
font-size: 20px;
font-weight: bold;
```

**To**
```
#tab-menu{
position: absolute;
height: 34px;
left: 15px;
top: 4px;
width: 960px;
overflow: hidden;
font-size: 20px;
font-weight: bold;
```

**From**
```
#logo{
        width: 234px;
        height: 100px;
        position: absolute;
        background: url(layout/skin1/logo.jpg) no-repeat center;
        left: 20px;
        top: 4px;
        text-indent: -9999px;
        overflow: hidden;

```

**To**
```
#logo{
        width: 234px;
        height: 100px;
        position: absolute;
/*      background: url(layout/skin1/logo.jpg) no-repeat center;*/
        left: 20px;
        top: 4px;
        text-indent: -9999px;
        overflow: hidden;

```

---

### Post by duffydack on 2009-02-20
removed

---

### Post by duffydack on 2009-02-20
[SIZE="2"]**Tip #3**[/SIZE]
**[SIZE="4"]How to remove the "Newest Members" from main page[/SIZE]**

If you are like me, you dont want it.

for default Mainstream template (the white one)
```
sudo cp /var/www/vidiscript/templates/Mainstream/modules/latest.module /var/www/vidiscript/templates/Mainstream/modules/latest.module.bak
sudo pico /var/www/vidiscript/templates/Mainstream/modules/latest.module

```

For the Afterdark template (dark one)
```
sudo cp /var/www/vidiscript/templates/AfterDark/modules/latest.module /var/www/vidiscript/templates/AfterDark/modules/latest.module.bak
sudo cp /var/www/vidiscript/templates/AfterDark/modules/latest.module

```

remove the following lines:
```
<h1><img src="<?=$templateimagepath?>icn_newest_members.jpg " alt="" /><b>Newest</b> Members</h1>
<?=newestMembers()?> 
```

---

### Post by mysoogal on 2009-03-16
how to fix, this problem,


[http://127.0.0.1/index.php](http://127.0.0.1/index.php) no problem it seems like it's working


but when i try to Login or click on top rated !

Page not found :(

how to fix this. it seems only gives error when links are like this 

[http://127.0.0.1/upload](http://127.0.0.1/upload) > gives errror

---

### Post by duffydack on 2009-03-20
sounds like you havent enabled rewrite for apache
sudo a2enmod rewrite

also check the .htaccess file is there

---

### Post by mysoogal on 2009-03-20
thanks, it seemed to work :popcorn:

now just need to test if ffmpeg working and mencoder :D

lol now it works but i cant See the upload Link lol this is really crazy :D

how to fix this thing.

everything works i can login check out pages but front page has no upload link

---

### Post by duffydack on 2009-03-21
ive noticed that when using from same machine too..try using actual ip address, else you`ll need to access it from another machine..
and it uses ffmpeg by default.

---

### Post by mysoogal on 2009-03-21
> **duffydack said:**
> ive noticed that when using from same machine too..try using actual ip address, else you`ll need to access it from another machine..
and it uses ffmpeg by default.



i'm runing xubuntu in virtualbox 2, inside my box i go into 127.0.0.1/vidiscript/ to check out the script

outside the virtualbox, i can access it via 192.168.2.19/vidiscript/ 

same problem. even if i upload from a real machine like on xp a mpeg 3 mb video. i can see the upload link when i login but if loged out no upload link appear. so weird. :KS

same issue if i used my Real Ip. 

i'm going to try installing everything again !a new fresh xubuntu :KS

i hope it works this time.

---

### Post by duffydack on 2009-03-22
if you cant see upload link when not logged in then maybe an option in Site Settings needs adjusting..

if you can access it with an upload link at all it means its workin fine.. must be a bug or something..  all i know is i cant see an Upload tab when accessing in browser while running on the same pc.. has to be another pc, real or virtual...

---

### Post by mysoogal on 2009-03-26
there will be a new release of vidiscript in few weeks i believe ! :lolflag: lots of new features. i will try to follow this again with the new script :KS

---

### Post by duffydack on 2009-03-27
well if you cant get this working with my instructions i dont hold much hope for a newer version.  keep trying the "old" one so you get the hang of installing it and figure any problems for future reference...

---

### Post by duffydack on 2009-04-30
Just a quick "btw".  I followed this tut from scratch and it works fine.

---

### Post by mysoogal on 2009-05-02
sorry late reply, i thought this forum would send me updates if new posts have been made !no wonder i always reply late. er

it's fine, I'm using Ostube community edition right now, i got everything installed somehow even ffmpeg-php :KS  video upload works, converting works.

the only bad thing about Ostube are the themes ! very ugly templates.

---

### Post by fred2028 on 2010-07-20
I tried your line

sudo mv ioncube /usr/local/bin/

but it says something cannot move since directory is not empty. What do I do now?

---

