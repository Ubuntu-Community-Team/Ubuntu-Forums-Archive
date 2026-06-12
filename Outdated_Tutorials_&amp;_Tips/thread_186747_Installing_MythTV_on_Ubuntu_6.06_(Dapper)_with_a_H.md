---
title: "Installing MythTV on Ubuntu 6.06 (Dapper) with a Hauppauge PVR-150/250/350/500"
date: 2006-06-02
forum: Outdated Tutorials &amp; Tips
---

### Post by althepcman on 2006-06-02
This is my first how to so excuse any mistake but I thoiught I would post it for the benifit of others.

Basically Follow:
[http://hyams.webhop.net/mythtv/myth_ubuntu.html](http://hyams.webhop.net/mythtv/myth_ubuntu.html)

When you get to this:
> 
apt-get install build-essential dialog apache2 mysql-server phpmyadmin gcc-3.4 
apt-get install libapache2-mod-auth-mysql
apt-get install dvdauthor mplayer-586
apt-get install ntp ntp-simple

Do this instead:
```
sudo apt-get install build-essential dialog apache2 mysql-server phpmyadmin gcc-3.4 libapache2-mod-php5
apt-get install libapache2-mod-auth-mysql
apt-get install dvdauthor mplayer-586
apt-get install ntp ntp-simple
```

You then need to retart apache by doing the following:
```

sudo /etc/init.d/apache2 restart

```

When you get to this:
> cd utils
wget [ftp://ftp.shspvr.com/download/wintv-pvr_150-500/inf/pvr_2.0.24.23035.zip](ftp://ftp.shspvr.com/download/wintv-pvr_150-500/inf/pvr_2.0.24.23035.zip)
wget [ftp://ftp.shspvr.com/download/wintv-pvr_250-350/inf/pvr_1.18.21.22254_inf.zip](ftp://ftp.shspvr.com/download/wintv-pvr_250-350/inf/pvr_1.18.21.22254_inf.zip)
unzip pvr_2.0.24.23035.zip 
./ivtvfwextract.pl pvr_1.18.21.22254_inf.zip
cp HcwMakoA.ROM /usr/lib/hotplug/firmware/v4l-cx25840.fw
cp HcwFalcn.rom /usr/lib/hotplug/firmware/v4l-cx2341x-enc.fw
mv /lib/modules/ivtv-fw-dec.bin /usr/lib/hotplug/firmware/
mv /lib/modules/ivtv-fw-enc.bin /usr/lib/hotplug/firmware/
cp ../v4l-cx2341x-init.mpg /usr/lib/hotplug/firmware
ln -s /usr/lib/hotplug/firmware/ivtv-fw-dec.bin /usr/lib/hotplug/firmware/v4l-cx2341x-dec.fw 

Instead do this:
```

cd utils
wget [ftp://ftp.shspvr.com/download/wintv-pvr_150-500/inf/pvr_2.0.24.23035.zip](ftp://ftp.shspvr.com/download/wintv-pvr_150-500/inf/pvr_2.0.24.23035.zip)
wget [ftp://ftp.shspvr.com/download/wintv-pvr_250-350/inf/pvr_1.18.21.22254_inf.zip](ftp://ftp.shspvr.com/download/wintv-pvr_250-350/inf/pvr_1.18.21.22254_inf.zip)
unzip pvr_2.0.24.23035.zip 
./ivtvfwextract.pl pvr_1.18.21.22254_inf.zip
cp HcwMakoA.ROM /lib/firmware/v4l-cx25840.fw
cp HcwFalcn.rom /lib/firmware/v4l-cx2341x-enc.fw
mv /lib/modules/ivtv-fw-dec.bin /lib/firmware/
mv /lib/modules/ivtv-fw-enc.bin /lib/firmware/
cp ../v4l-cx2341x-init.mpg /lib/firmware/
ln -s lib/firmware/ivtv-fw-dec.bin /lib/firmware/v4l-cx2341x-dec.fw
```

Then do:
```
ls -ltra /lib/firmware/
```

Then return to:
[http://hyams.webhop.net/mythtv/myth_ubuntu.html](http://hyams.webhop.net/mythtv/myth_ubuntu.html)

Follow on from there.

I hope this helps

---

### Post by wogdog on 2006-06-02
You rock! I will give this a try right now.

---

### Post by wogdog on 2006-06-02
Is it necessary to do both unzip statements in line 3 and 4 of your replacement code? They look like they do the same thing.
[INDENT]unzip pvr_2.0.24.23035.zip 
unzip pvr_2.0.24.23035.zip [/INDENT]

[QUOTE=althepcman]This is my first how to so excuse any mistake but I thoiught I would post it for the benifit of others.

Basically Follow:
[http://hyams.webhop.net/mythtv/myth_ubuntu.html](http://hyams.webhop.net/mythtv/myth_ubuntu.html)

Untill you get to this:


Instead do this:
```
wget [ftp://ftp.shspvr.com/download/wintv-pvr_150-500/inf/pvr_2.0.24.23035.zip](ftp://ftp.shspvr.com/download/wintv-pvr_150-500/inf/pvr_2.0.24.23035.zip)
wget [ftp://ftp.shspvr.com/download/wintv-pvr_250-350/inf/pvr_1.18.21.22254_inf.zip](ftp://ftp.shspvr.com/download/wintv-pvr_250-350/inf/pvr_1.18.21.22254_inf.zip)
unzip pvr_2.0.24.23035.zip 
unzip pvr_2.0.24.23035.zip 
./ivtvfwextract.pl pvr_1.18.21.22254_inf.zip
cp HcwMakoA.ROM /lib/firmware/v4l-cx25840.fw
cp HcwFalcn.rom /lib/firmware/v4l-cx2341x-enc.fw
mv /lib/modules/ivtv-fw-dec.bin /lib/firmware/
mv /lib/modules/ivtv-fw-enc.bin /usr/firmware/
cp ../v4l-cx2341x-init.mpg /lib/firmware/
ln -s lib/firmware/ivtv-fw-dec.bin /lib/firmware/v4l-cx2341x-dec.fw
```

Then do:
```
ls -ltra /lib/firmware/
```

Then return to:
[http://hyams.webhop.net/mythtv/myth_ubuntu.html](http://hyams.webhop.net/mythtv/myth_ubuntu.html)

Follow on from there.

I hope this helps[/QUOTE]

---

### Post by NT4usB on 2006-06-02
lol... I **just** got to that part in hyams guide (again...) and went looking for his site to c&p the link info... and found this post!
*timing is everything...*g**
Thanks for posting it!

ed: is that a typo... unzipping the same file twice:

[i]unzip pvr_2.0.24.23035.zip 
unzip pvr_2.0.24.23035.zip 
./ivtvfwextract.pl pvr_1.18.21.22254_inf.zip[/i]

edd: sorry, already spotted by wogdog. oops!

eddd: fyi, I had to mkdir /lib/firmware/. folder firmware didn't exist in my fresh desktop install.

---

### Post by bicchi on 2006-06-02
I wasn't sure where to put the firmware. Thanks. 
By the way. You have this command: mv /lib/modules/ivtv-fw-enc.bin /usr/firmware/
I think this should be: mv /lib/modules/ivtv-fw-enc.bin /lib/firmware/
*** I do not have /usr/firmware/ ***

Also, is anyone having problems changing channels while watching TV? 
Try this: (modify the commands below to /dev/video0 or /dev/video1 accordingly)
* Open 2 terminals.
* on one type: mplayer /dev/video0
* on the other: ivtv-tune -c 4 -d /dev/video0
The above should actually change the channel to 4. Try with -c 5, -c 6, etc. while displaying the video.

In my case the stream stops until I reload the module with.
sudo modprobe -r ivtv
sudo modprobe ivtv

Can anyone comment on this issue? I have a WinTV PVR 250.

---

### Post by roazena on 2006-06-03
Two days ago I had the misfortune of futzing with my Myth box, the one built using Hyams' Breezy instructions. Tonight, I'm installing Dapper and dag if that isn't exactly what I needed. Thanks again.

---

### Post by jacrider on 2006-06-03
I am glad this thread has started as I am trying to install MythTV on my Dapper box.

I am running into a problem very early in the install that I am hoping someone can help me find the error of my ways.

After installing apache2 and mysql, there is a step where you open "localhost" in Firefox and select phpmyadmin to setup a root passwork.

When I select phpmyadmin, I get a box asking me where I want to save the file.  Not a link to the password admin.

Anyone know where I have gone wrong?

Many thanks.

---

### Post by althepcman on 2006-06-03
[QUOTE=wogdog]Is it necessary to do both unzip statements in line 3 and 4 of your replacement code? They look like they do the same thing.
[INDENT]unzip pvr_2.0.24.23035.zip 
unzip pvr_2.0.24.23035.zip [/INDENT][/QUOTE]
Opps. Sorry my bad. 
I fixed that typo and the other one.

Thanks for everyones support. 
Sorry it took  me a while to post back. Busy day. :)

---

### Post by althepcman on 2006-06-03
[QUOTE=bicchi]I wasn't sure where to put the firmware. Thanks. 
By the way. You have this command: mv /lib/modules/ivtv-fw-enc.bin /usr/firmware/
I think this should be: mv /lib/modules/ivtv-fw-enc.bin /lib/firmware/
*** I do not have /usr/firmware/ ***

Also, is anyone having problems changing channels while watching TV? 
Try this: (modify the commands below to /dev/video0 or /dev/video1 accordingly)
* Open 2 terminals.
* on one type: mplayer /dev/video0
* on the other: ivtv-tune -c 4 -d /dev/video0
The above should actually change the channel to 4. Try with -c 5, -c 6, etc. while displaying the video.

In my case the stream stops until I reload the module with.
sudo modprobe -r ivtv
sudo modprobe ivtv

Can anyone comment on this issue? I have a WinTV PVR 250.[/QUOTE]

Yes it is /lib/firmware/
sorry that was my typo.

Also with you changing channels with ivtv-tune I find it takes a couple of seconds on my box to actually change channels.
I havn't had to reload the module.

I have a 250 MCE card.

---

### Post by bicchi on 2006-06-03
From what I find in this [thread]("http://www.gossamer-threads.com/lists/mythtv/users/206801"), I am not the only one having issues with the driver freezing while changing channels. The problem only happens while I am viewing the stream such as with the command: mplayer /dev/video0. The channels change without a problem if I am not using the stream. I assume that this has to do with some kind of file sharing violation or more specifically not allowing ivtv-tune to use the device while its been read by another process.

Let me also point out that I upgraded from Breezy and this is not a clean install. I have also looked at the output of dmesg and looks fine. Does anyone knows how to do some kind of hard reset on the card? Perhaps it needs to clear some kind of eprom.

---

### Post by Kryptonate on 2006-06-03
Hello,

I can't get past the phpmyadmin-directory. It wants to download something :s. Anyone know of a solution? Thanks

---

### Post by ponchera on 2006-06-03
Same problem here.  :mad:

---

### Post by althepcman on 2006-06-03
[QUOTE=Kryptonate]Hello,

I can't get past the phpmyadmin-directory. It wants to download something :s. Anyone know of a solution? Thanks[/QUOTE]

Yeah it seems to a problem with apache and php.
It's not recognizing php scripts.Its very strange. Even though php is installed.
I will see if I can work around it. :)

---

### Post by xinix on 2006-06-04
Here are a couple repositories with the Mythtv .19 version:

deb [http://home.eng.iastate.edu/~superm1](http://home.eng.iastate.edu/~superm1) dapper main
deb-src [http://home.eng.iastate.edu/~superm1](http://home.eng.iastate.edu/~superm1) dapper main
           or
deb [http://knm.org/mythdebs/](http://knm.org/mythdebs/)  binary/
deb-src [http://knm.org/mythdebs/](http://knm.org/mythdebs/) source/

I can't get the mythmusic plugin to install. It fails with a dependency for libcdaudio0 but libcdaudio1 is what is on the ubuntu repos.  Anyone had luck with this?

---

### Post by laurens on 2006-06-04
[QUOTE=althepcman]Yeah it seems to a problem with apache and php.
It's not recognizing php scripts.Its very strange. Even though php is installed.
I will see if I can work around it. :)[/QUOTE]

I had the same problem. I think this fixed it for me:

sudo apt-get install libapache2-mod-php5

Thanks for the howto btw :)

---

### Post by jafenske on 2006-06-04
I'm having the same problem with the myphpadmin and I installed the above and still nothing...  Anyone have any other ideas?

Thanks

JOe

By the way I've got an AMD64... could this be the problem

---

### Post by jafenske on 2006-06-04
I tried installing php on my 386 breezy box and it went off without a hitch...

---

### Post by jafenske on 2006-06-04
I clear the cache in my browser and it worked...

see this thread for solution

[HTML]http://www.ubuntuforums.org/showthread.php?t=185825&highlight=MythTV[/HTML]

---

### Post by jacrider on 2006-06-04
Installing libapache2-mod-php5 worked for me.

You need to go to "privileges", select the "root" account and then scroll down and you will see an option to change the password.

Worked.  

On to the next step.

---

### Post by jacrider on 2006-06-04
Ok.  I have made more progress, but I am not there yet!

I am having difficulty is getting the remote to work.  I have installed as per Hyams how-to.  I have tested as the root user and can see codes on the screen as Push buttons.

However, when I login as mythtv, I can't seem to get it to work?

Any ideas?

---

### Post by NT4usB on 2006-06-05
[QUOTE=laurens]I had the same problem. I think this fixed it for me:

sudo apt-get install libapache2-mod-php5

Thanks for the howto btw :)[/QUOTE]


That worked for the Firefox thing. Had to restart X (Ctrl+Alt+Backspace) for it to take though.

---

### Post by no.one on 2006-06-05
When I try to login to phpmyadmin, I receive this message:
```
Error
#1045 - Access denied for user 'root'@'localhost' (using password: NO)
```



Edit: Oh, and by the way, I've reinstalled everything relating to php several times (complete removal through synaptic).

---

### Post by ponchera on 2006-06-05
I had the same problem.  I did a complete remove of all mysql5 (sear, sort by the first column with box) Exept for whatever was dependencies of other ubuntu stuff.

Then i followed the command in post #22
[http://www.ubuntuforums.org/showthread.php?t=48397&page=3](http://www.ubuntuforums.org/showthread.php?t=48397&page=3)

sudo apt-get install apache2 php5 mysql-client-5.0 mysql-server-5.0 phpmyadmin libapache2-mod-php5 libapache2-mod-auth-mysql php5-mysql

---

### Post by no.one on 2006-06-06
Thank you ponchera!  It works now.

---

### Post by barbex on 2006-06-06
Just in case someone bangs their head like me:

non-US people have to specify the frequency-map in ivtv-tune like this:

ivtv-tune -teurope-west -c E2 -d /dev/video0

---

### Post by althepcman on 2006-06-07
I added the stuff about installing libapache-mod-php5.
Also for all you folow australian's Here some cheats for you:
ivtv-tune -t australia -c 40 -d /dev/video0

Channel 40 gets me Channel 9/Win tv

---

### Post by Sureshot324 on 2006-06-07
On my amd64 install of dapper, the firmware had to go to /lib/firmware/2.6.15-23-amd64-generic

---

### Post by chadk on 2006-06-07
I've spent a couple hours on this now and just can't get it going.  Is there perhaps a script out there to help simplify all this?  There's just sooo many steps that can go wrong it's worse than installing certain flavors of linux that start with G.

---

### Post by ThreeE on 2006-06-08
When I do mythfilldatabase I get a bunch of these:

```
DB Error (Inserting into dd_schedule):
Query was:
INSERT INTO dd_schedule (programid,stationid,scheduletime,duration,repeat,stereo,subtitled,hdtv,closecaptioned,tvrating,partnumber,parttotal,endtime) VALUES('SH6878270000','19283','2006-06-14T23:30:00','00:30:00',0,0,0,0,0,NULL,0,0,'2006-06-15T00:00:00');
Driver error was [2/1064]:
QMYSQL3: Unable to execute query
Database error was:
You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near 'repeat,stereo,subtitled,hdtv,closecaptioned,tvrating,partnumber,parttotal,endtim' at line 1

```

Any ideas?  I have to say -- this is much easier on Dapper than it was on Breezy.

---

### Post by JazzCrazed on 2006-06-08
I've successfully followed this howto with a brand new Dapper install. Thanks for it, worked great!

But I have one last trick to figure out. I use digital cable, that goes through a Scientific Atlanta 1850 set-top-box. I purchased an IR blaster from [http://irblaster.info](http://irblaster.info) -- referred there because it reputedly works well with MythTV. On that site, there's a link to a tutorial on setting up an IR blaster to control a cable/dish box on a KnoppMyth box, which I thought would be similar enough to my own setup to use.

Just my luck that it wasn't, as the author of the tutorial told me in an e-mail that the differences between the distros were too significant for his tutorial to be effective. Trying anyway, I didn't get too far before I encountered errors that I couldn't figure out.

Has anybody setup their MythTV in Ubuntu to control a cable box with an IR blaster?

---

### Post by kcrajkumar on 2006-06-08
[QUOTE=jafenske]I'm having the same problem with the myphpadmin and I installed the above and still nothing...  Anyone have any other ideas?

Thanks

JOe

By the way I've got an AMD64... could this be the problem[/QUOTE]


----

Hi,

   Eventhough php was installed correctly, phpmyadmin was stored in a different directory and a softlink was created in "DocumentRoot" Directory.

PhpMyAdmin Install Dir : /usr/share/phpmyadmin
Apache Document Root : /var/www/

lrwxrwxrwx  1 root root   21 2006-06-06 23:37 phpmyadmin -> /usr/share/phpmyadmin

I think, this makes apache to think phpmyadmin is a regular file and not a directory. Need to do more reading on this.

do the following :

[http://localhost/phpmyadmin/index.php](http://localhost/phpmyadmin/index.php) .. you will see the phpmyadmin web page.

hope this will help !!!

Thanks.

---

### Post by JSVH on 2006-06-08
> **ThreeE]When I do mythfilldatabase I get a bunch of these:

```
DB Error (Inserting into dd_schedule):
Query was:
INSERT INTO dd_schedule (programid,stationid,scheduletime,duration,repeat,stereo,subtitled,hdtv,closecaptioned,tvrating,partnumber,parttotal,endtime) VALUES('SH6878270000','19283','2006-06-14T23:30:00','00:30:00',0,0,0,0,0,NULL,0,0,'2006-06-15T00:00:00') said:**
> :
QMYSQL3: Unable to execute query
Database error was:
You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near 'repeat,stereo,subtitled,hdtv,closecaptioned,tvrating,partnumber,parttotal,endtim' at line 1

```

Any ideas?  I have to say -- this is much easier on Dapper than it was on Breezy.


I am running into the same problem! 

Atleast I can get mythtv will start up, just no database . So no tv listings. let me know if you find out what the problem is.

---

### Post by JSVH on 2006-06-08
I also found that I can no longer get to mysql via Firefox>localhost> and when I click phpmyadmin I get "phpMyAdmin - Error.  Cannot load mysql extension. Please check your PHP configuration." I could get into phpmyadmin earlier to set my password and what not.

---

### Post by althepcman on 2006-06-08
[QUOTE=JSVH]I also found that I can no longer get to mysql via Firefox>localhost> and when I click phpmyadmin I get "phpMyAdmin - Error.  Cannot load mysql extension. Please check your PHP configuration." I could get into phpmyadmin earlier to set my password and what not.[/QUOTE]

Opps forgot to tell eveyone after installign all those things in the how to you should restart apache by doing the following:
```

sudo /etc/init.d/apache2 restart

```

I will add this to the how to. :)

---

### Post by NT4usB on 2006-06-08
If it isn't one thing, it's another...
I've been through this install several times. Never with complete success... Well, maybe the first time but I screwed that up by updating the kernel...
Upside, it's always something different that goes wrong for me so I get to learn new stuff each time.
This time (sixth complete install if iirc) I'm stuck on:

[i]root@dapperpvr:~# ./ivtvfwextract.pl pvr_1.18.21.22254_inf.zip
-bash: ./ivtvfwextract.pl: No such file or directory[/i]

Only thing I've intentionally done different than the instructions was grab the ivtv-0.4.5 drivers instead of ivtv-0.4.4.
I'm pretty sure everything went into the correct folders, etc. Made sure I put .5 where the howto said .4... Would using the 0.4.5 drivers mess me up?

 the .pl makes reference to finding the zip in /mnt/cdrom so I put a copy there. No joy.

Can I extract and place the contents of pvr_1.18.21.22254_inf.zip manually?

Any other suggestions? 

*Happy Linux user for going on four weeks!*

---

### Post by althepcman on 2006-06-08
[QUOTE=NT4usB]If it isn't one thing, it's another...
I've been through this install several times. Never with complete success... Well, maybe the first time but I screwed that up by updating the kernel...
Upside, it's always something different that goes wrong for me so I get to learn new stuff each time.
This time (sixth complete install if iirc) I'm stuck on:

[i]root@dapperpvr:~# ./ivtvfwextract.pl pvr_1.18.21.22254_inf.zip
-bash: ./ivtvfwextract.pl: No such file or directory[/i]

Are you in the utils directory when you do:
./ivtvfwextract.pl pvr_1.18.21.22254_inf.zip

eg if you enter the command **pwd** You should get:
 /usr/src/ivtv-0.4.5/utils

---

### Post by NT4usB on 2006-06-08
[QUOTE=althepcman]...
Are you in the utils directory when you do:
./ivtvfwextract.pl pvr_1.18.21.22254_inf.zip

eg if you enter the command **pwd** You should get:
 /usr/src/ivtv-0.4.5/utils[/QUOTE]

I tried it that way. Even cp the zip to that folder to see if that would work. 
iirc, I didn't get the *No such folder...* error that way. Also didn't see any indication at all that the files extracted. Just back to the prompt...

Should I see any response when running ./ivtvfwextract.pl?

A search of my hard disk didn't find the extracted files so I assume it didn't extract.

I almost pasted a shot of my terminal so you could see all the different ways I tried to  get it to work. It would have filled the page and was mostly noob fumblings anyway.

I did make it completely through hyams install including your variation previously. 
When I finished, MythTv was only detecting one of my 150’s and  Mysql was jacked but other than that, I got through it. Both cards were working and could record tv but myth only saw one.

So, I know this all works… 

I completely borked my system trying to straighten out Mysql,  so I flatlined it, started over again, and here we are…

---

### Post by jafenske on 2006-06-08
I've having the same problems with sql... I been looking at other how-to guides and in this one 

[http://www.abarbaccia.com/content/view/17/32/](http://www.abarbaccia.com/content/view/17/32/)

for instance they make sure mythtv user can acess the database by

```

$  mysql -u root -p mysql
mysql>  UPDATE user SET password=PASSWORD('mythtv') WHERE user="mythtv";
mysql>  FLUSH PRIVILEGES;
mysql>  quit

```

Why don't we have to do that here?

---

### Post by dapple on 2006-06-08
> **ThreeE]When I do mythfilldatabase I get a bunch of these:

```
DB Error (Inserting into dd_schedule):
Query was:
INSERT INTO dd_schedule (programid,stationid,scheduletime,duration,repeat,stereo,subtitled,hdtv,closecaptioned,tvrating,partnumber,parttotal,endtime) VALUES('SH6878270000','19283','2006-06-14T23:30:00','00:30:00',0,0,0,0,0,NULL,0,0,'2006-06-15T00:00:00') said:**
> :
QMYSQL3: Unable to execute query
Database error was:
You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near 'repeat,stereo,subtitled,hdtv,closecaptioned,tvrating,partnumber,parttotal,endtim' at line 1

```

Any ideas?  I have to say -- this is much easier on Dapper than it was on Breezy.

[QUOTE=JSVH]I am running into the same problem! 

Atleast I can get mythtv will start up, just no database . So no tv listings. let me know if you find out what the problem is.[/QUOTE]

repeat is a reserved word in MYSQL5.  Downgrade to MYSQL 4.  You'll have to setup the database all over again but mythfilldatabase will work on MYSQL4.  This has been fixed in Mythtv .19x but has not been ported back to the .18.1 version.

---

### Post by laurens on 2006-06-08
Just a quick note: 

I've been following this tutorial, and I got it running, however, I did not get MythWeb running. Please note, that I was compiling from the svn repository. However, I think this might come up with some other people too:

I kept getting errors when trying to log in to mythweb, where it was complaining that I needed to install php-mysql. I had it installed, and phpmyadmin worked perfectly; Just mythweb kept giving me the error.

Turned out this link held the answer:

[http://www.mythtv.org/pipermail/mythtv-users/2003-April/003459.html](http://www.mythtv.org/pipermail/mythtv-users/2003-April/003459.html)
> 
find your php.ini file. Make sure you've got a line in it like this:

extension=mysql.so

and that it is uncommented. and restart apache. That should cure you.


Hope it helps, it did for me!

---

### Post by laurens on 2006-06-08
[QUOTE=dapple]repeat is a reserved word in MYSQL5.  Downgrade to MYSQL 4.  You'll have to setup the database all over again but mythfilldatabase will work on MYSQL4.  This has been fixed in Mythtv .19x but has not been ported back to the .18.1 version.[/QUOTE]

You can also edit the file, and replace all occurances of repeat with `repeat` (backticks!!). 

This is untested, but I have done things like this in the past with mysql. Hope it helps - it seems less painfull than downgrading :)

Cheers!

---

### Post by valmar on 2006-06-08
Hello to everybody.

I followed this guide with the links provided to hyams page. Everything seems fine. I installed the ivtv drivers and mythtv (All on dapper). Howwwever, I have the following problem:

when setting up with mythtv-setuo, when I get to the channels, I cannot scan for channels.

I also tried with xawtv to use the card. After choosing my settings (PAL and europe-west), everything I get is a black screen

I am using amd 64, could that be the problem?

Thank you in advance for your help

       Valerio

---

### Post by Staach on 2006-06-09
Not sure if this is the right place to ask this question but here goes. Is it possible to install mythtv on the server version (instead of the desktop)?  The reason I want this, is that I need a full webserver (+ mail) with typo3 installed on the same pc as mythtv. However I'm still quite new at linux so I´ll need the guidence from both [http://hyams.webhop.net/mythtv/myth_ubuntu.html](http://hyams.webhop.net/mythtv/myth_ubuntu.html) (and this thread) and other server-walk-thrus. 
Thx in advance
Staach

---

### Post by JSVH on 2006-06-09
Thanks Dapple, Upgaded to .19 and that fixed that.

[QUOTE=xinix]
I can't get the mythmusic plugin to install. It fails with a dependency for libcdaudio0 but libcdaudio1 is what is on the ubuntu repos.  Anyone had luck with this?[/QUOTE]

I am in the same boat as you xinix. let me know if you found a way to get mythmusic to work.

Thanks Everyone!

---

### Post by NT4usB on 2006-06-09
Well, I'm back to where I was before I trashed my box the first time, thanks to tips in this thread and other howto's...

Now to sort out the channel changing issue.

---

### Post by handband2 on 2006-06-10
I've gone through everything in the HowTo a couple times but I keep getting the same error:

make -C driver install
make[1]: Entering directory `/usr/src/ivtv-0.4.5/driver'
make -C /lib/modules/2.6.15-23-k7/build M=/usr/src/ivtv-0.4.5/driver modules
make[2]: Entering directory `/usr/src/linux-source-2.6.15'
  Building modules, stage 2.
  MODPOST
make[2]: Leaving directory `/usr/src/linux-source-2.6.15'
make INSTALL_MOD_PATH= INSTALL_MOD_DIR=ivtv \
                -C /lib/modules/2.6.15-23-k7/build M=/usr/src/ivtv-0.4.5/driver modules_install
make[2]: Entering directory `/usr/src/linux-source-2.6.15'
  INSTALL /usr/src/ivtv-0.4.5/driver/ivtv-fb.ko
cp: omitting directory `/lib/modules/2.6.15-23-k7'
make[3]: *** [/usr/src/ivtv-0.4.5/driver/ivtv-fb.ko] Error 1
make[2]: *** [modules_install] Error 2
make[2]: Leaving directory `/usr/src/linux-source-2.6.15'
make[1]: *** [install] Error 2
make[1]: Leaving directory `/usr/src/ivtv-0.4.5/driver'
make: *** [install] Error 2

How would I go about fixing this error?

Thanks

---

### Post by planetmn on 2006-06-10
[QUOTE=NT4usB]I tried it that way. Even cp the zip to that folder to see if that would work. 
iirc, I didn't get the *No such folder...* error that way. Also didn't see any indication at all that the files extracted. Just back to the prompt...

Should I see any response when running ./ivtvfwextract.pl?

A search of my hard disk didn't find the extracted files so I assume it didn't extract.

I almost pasted a shot of my terminal so you could see all the different ways I tried to  get it to work. It would have filled the page and was mostly noob fumblings anyway.

I did make it completely through hyams install including your variation previously. 
When I finished, MythTv was only detecting one of my 150’s and  Mysql was jacked but other than that, I got through it. Both cards were working and could record tv but myth only saw one.

So, I know this all works… 

I completely borked my system trying to straighten out Mysql,  so I flatlined it, started over again, and here we are…[/QUOTE]


I'm having the same problem:
```
root@mythtv:/usr/src/ivtv-0.4.4# ./ivtvfwextract.pl pvr_1.18.21.22254_inf.zip
-bash: ./ivtvfwextract.pl: No such file or directory

```

If I do an ls, the file is clearly there.  Any ideas?

Thanks,dave

---

### Post by qrazi on 2006-06-11
I am having problems with my IVTV driver.

I used to run mythtv with no problems on ubuntu 5.10. I recently upgraded to 6.06, but after the upgrade, i cannot watch livetv anymore, and recordings dont actually record anymore.

So i tried to compile the IVTV driver again, using this howto. I get stuck at the point where i am going to make the IVTV driver.
it gives a lot of of the same error:

> 
/usr/src/ivtv-0.4.4/driver/msp3400.c:78: error: &#8216;normal_i2c_range&#8217; undeclared he re (not in a function)
/usr/src/ivtv-0.4.4/driver/msp3400.c: In function &#8216;msp3400c_reset&#8217;:
/usr/src/ivtv-0.4.4/driver/msp3400.c:221: warning: pointer targets in initializa tion differ in signedness
/usr/src/ivtv-0.4.4/driver/msp3400.c:222: warning: pointer targets in initializa tion differ in signedness
/usr/src/ivtv-0.4.4/driver/msp3400.c:225: warning: pointer targets in initializa tion differ in signedness

 and some more of basicly the same error. I have done searchiong on the internet, but i cannot find why it gives this error, or what this error means....

Any suggestions? Maybe how to do a clean install?

---

### Post by TomSelleck on 2006-06-11
I can't get past:

[INDENT]depmod
modprobe ivtv
dmesg[/INDENT]

I always get the following error at the end of the log:

[4300563.861000] ivtv:  ==================== START INIT IVTV ====================
[4300563.861000] ivtv:  version 0.4.5 (tagged release) loading
[4300563.861000] ivtv:  Linux version: 2.6.15-23-386 preempt 486 gcc-4.0
[4300563.861000] ivtv:  In case of problems please include the debug info between
[4300563.861000] ivtv:  the START INIT IVTV and END INIT IVTV lines, along with
[4300563.861000] ivtv:  any module options, when mailing the ivtv-users mailinglist.
[4300563.863000] ivtv0: Autodetected WinTV PVR 350 card (cx23415 based)
[4300563.863000] PCI: Enabling device 0000:00:0b.0 (0014 -> 0016)
[4300563.863000] ACPI: PCI Interrupt 0000:00:0b.0[A] -> Link [LNKB] -> GSI 10 (level , low) -> IRQ 10
[4300563.863000] ivtv0: Unreasonably low latency timer, setting to 64 (was 32)
[4300563.905000] tveeprom: ivtv version
[4300563.905000] tveeprom: Hauppauge: model = 48132, rev = J323, serial# = 7064662
[4300563.905000] tveeprom: tuner = Philips FM1236 (idx = 23, type = 2)
[4300563.905000] tveeprom: tuner fmt = NTSC(M) (eeprom = 0x08, v4l2 = 0x00001000)
[4300563.905000] tveeprom: audio processor = MSP4448 (type = 1b)
[4300563.905000] tveeprom: decoder processor = SAA7115 (type = 13)
[4300563.905000] ivtv0: i2c attach to card #0 ok [client=tveeprom, addr=50]
[4300563.936000] tuner (ivtv): chip found at addr 0xc2 i2c-bus ivtv i2c driver #0
[4300563.936000] ivtv0: i2c attach to card #0 ok [client=(tuner unset), addr=61]
[4300564.095000] saa7115 1-0021: saa7115 found @ 0x42 (ivtv i2c driver #0)
[4300564.199000] ivtv0: i2c attach to card #0 ok [client=saa7115, addr=21]
[4300564.257000] saa7127 1-0044: ivtv driver
[4300564.259000] saa7127 1-0044: saa7127 found @ 0x88 (ivtv i2c driver #0)
[4300564.259000] ivtv0: i2c attach to card #0 ok [client=saa7127, addr=44]
[4300564.305000] msp3400 1-0040: chip=MSP4448G-A2 +nicam +simple +simpler +radio mod e=simpler
[4300564.305000] msp3400 1-0040: msp34xxg daemon started
[4300564.322000] ivtv0: i2c attach to card #0 ok [client=MSP4448G-A2, addr=40]
[4300565.108000] ivtv0: loaded v4l-cx2341x-enc.fw firmware (262144 bytes)
[4300565.118000] ivtv0: unable to open firmware v4l-cx2341x-dec.fw
[4300565.118000] ivtv0: did you put the firmware in the hotplug firmware directory?
[4300565.119000] ivtv0 warning: failed loading decoder firmware
[4300565.119000] ivtv0 warning: Error loading firmware -1!
[4300565.119000] ivtv0: Error -1 initializing firmware.
[4300565.128000] ivtv0: Error -12 on initialization
[4300565.128000] ivtv: probe of 0000:00:0b.0 failed with error -12
[4300565.128000] ivtv:  ====================  END INIT IVTV  ====================

I started with a clean 6.06 build and followed Hyams' guide to the letter except for the exceptions posted in the start of this thread.  I'm befuddled.

---

### Post by TomSelleck on 2006-06-11
[QUOTE=TomSelleck]

I always get the following error at the end of the log:

[4300565.108000] ivtv0: loaded v4l-cx2341x-enc.fw firmware (262144 bytes)
[4300565.118000] ivtv0: unable to open firmware v4l-cx2341x-dec.fw
[4300565.118000] ivtv0: did you put the firmware in the hotplug firmware directory?
[4300565.119000] ivtv0 warning: failed loading decoder firmware
[4300565.119000] ivtv0 warning: Error loading firmware -1!
[4300565.119000] ivtv0: Error -1 initializing firmware.
[4300565.128000] ivtv0: Error -12 on initialization
[4300565.128000] ivtv: probe of 0000:00:0b.0 failed with error -12
[4300565.128000] ivtv:  ====================  END INIT IVTV  ====================
[/quote]

I fixed it.  The clue was in the log above.  It successfully loaded v4l-cx2341x-enc.fw, but not v4l-cx2341x-dec.fw.  I looked in /lib/firmware and saw that v4l-cx2341x-dec.fw was a symbolic link.  I removed the link and copied the real file there instead.  It worked.

I have a DVD player hooked up to the S-Video input of my PVR-350.  I get good sound and picture, except that the picture is only in black and white.  Off I go...

---

### Post by HJB on 2006-06-11
Hi qrazi. Have a look here [http://ubuntuforums.org/showthread.php?p=1125764#post1125764](http://ubuntuforums.org/showthread.php?p=1125764#post1125764)

---

### Post by SlamBam on 2006-06-11
Hi,

Sorry i´m  a quite new on Linux and am stuck on the ´sudo apt-get mythtv´. I added to my /etc/apt/source.list the following:

deb [http://knm.org/mythdebs/](http://knm.org/mythdebs/) binary/
deb-src [http://knm.org/mythdebs/](http://knm.org/mythdebs/) source/

Now there is a dependency in mythfrontend  that I can´t install: liblame0. Can anyone help on this?

Thanks

---

### Post by planetmn on 2006-06-11
Hi all.  I had posted a problem earlier, and it turned out to be a FFI (Failure to Follow Instructions).  I've moved on and run into another error.  After installing the IVTV driver, I try to depmod and then modprobe ivtv and I receive the following:
```
david@mythtv:~$ sudo depmod
david@mythtv:~$ modprobe ivtv
FATAL: Module ivtv not found.

```

Does anybody know what caused this?  Should I just go ahead and reinstall the ivtv drivers?

I tried restarting the computer to see if the module just failed to load, but I get the same response.

Thanks,
dave

---

### Post by NT4usB on 2006-06-11
[QUOTE=planetmn]I'm having the same problem:
```
root@mythtv:/usr/src/ivtv-0.4.4# ./ivtvfwextract.pl pvr_1.18.21.22254_inf.zip
-bash: ./ivtvfwextract.pl: No such file or directory

```

If I do an ls, the file is clearly there.  Any ideas?

Thanks,dave[/QUOTE]


I ended up googling around until I found reference to extracting the files (driver?) from the windows .exe installer. 
Basically fumbled and stumbled until I had the files I needed then moved them to where I thought they should go.
In the end I was able to complete the install and for the first time ever ***I could change channels!***
The remote worked, I could switch between card0 and card1, see the channel lineups, record a show while watching another channel... 
Rejoice! it works!
The next day I fired it up, installed the daily updates, launched mythfrontend and it was broke again... changing channels just locks it up.
I had been seeing an update for libmyth-0.18.1c2a for a couple days but ignoring it. 
I was so close to getting this working that I figured any update with 'myth' in it would probably wreck things. I installed it.
...Looks like it did.
This is the point where I start uninstalling things and reinstalling things, breaking associations, jacking the system completely up, flatlining the box and starting over.
I just love Linux. Reminds me of the days working with NT4. One false move, BSOD. move to the back of the line please...

ed: update. I found part of the solution to the lock up problem in the MythTV troubleshooting section of their install guide. From the guide:
[i]MySQL not connecting correctly

Your MySQL installation may have networking turned off. Check that /etc/mysql/my.cnf does not contain skip-networking. If it does, remove it. **Also verify that bind-address is set to your IP address instead of 127.0.0.1.** If you change either of these items, restart MySQL.[/i]
The IP address fixed channel changing for card0. card1 is still jacked.

* Happy Linux user for four weeks today!*

---

### Post by Hybrid Blue on 2006-06-12
Hi there guys, im trying to build 0.19 from source but im running into a little prob lem here on dapper...

Ive installed all the libs/files that are needed to make the Plugin for mythmusic to build...the problem is that the configure script cant see that i have cdparanoia installed... Im not sure how to fix this as ive tried to add some more locations to $PATH and this hasn't changed anything... If anyone can give me a little help with this i would be greatful!

Thanks a lot guys!

---

### Post by althepcman on 2006-06-12
[QUOTE=planetmn]Hi all.  I had posted a problem earlier, and it turned out to be a FFI (Failure to Follow Instructions).  I've moved on and run into another error.  After installing the IVTV driver, I try to depmod and then modprobe ivtv and I receive the following:
```
david@mythtv:~$ sudo depmod
david@mythtv:~$ modprobe ivtv
FATAL: Module ivtv not found.

```

Does anybody know what caused this?  Should I just go ahead and reinstall the ivtv drivers?

I tried restarting the computer to see if the module just failed to load, but I get the same response.

Thanks,
dave[/QUOTE]

Hi,

This happened to me after eading through the how to I found that sometimes installing the ivtv drviers, they would get install to:
/lib/modules/<kver>/ivtv
<kver> for me = 2.6.15.7-ubuntu1
This could be different.

To fix do the following:
sudo cp -r /lib/modules/<kver>/ivtv /lib/modules/`uname -r`/

---

### Post by kayno on 2006-06-12
[QUOTE=xinix]Here are a couple repositories with the Mythtv .19 version:

deb [http://home.eng.iastate.edu/~superm1](http://home.eng.iastate.edu/~superm1) dapper main
deb-src [http://home.eng.iastate.edu/~superm1](http://home.eng.iastate.edu/~superm1) dapper main
           or
deb [http://knm.org/mythdebs/](http://knm.org/mythdebs/)  binary/
deb-src [http://knm.org/mythdebs/](http://knm.org/mythdebs/) source/

I can't get the mythmusic plugin to install. It fails with a dependency for libcdaudio0 but libcdaudio1 is what is on the ubuntu repos.  Anyone had luck with this?[/QUOTE]

were you able to solve this problem, or is anyone aware of a solution??

I cannot install mythmusic because of this error too. other than that, the repositorys were greatly appreciated!!

---

### Post by HJB on 2006-06-12
[QUOTE=Hybrid Blue]Hi there guys, im trying to build 0.19 from source but im running into a little prob lem here on dapper...

Ive installed all the libs/files that are needed to make the Plugin for mythmusic to build...the problem is that the configure script cant see that i have cdparanoia installed... Im not sure how to fix this as ive tried to add some more locations to $PATH and this hasn't changed anything... If anyone can give me a little help with this i would be greatful!

Thanks a lot guys![/QUOTE]

Hi HybridBlue, I got the whole thing working from the sources BUT, I cant get it to start. It didn't create the mythtv user. Im at work now and dont have my self made 'howto' with me. Tell me how you get this working. I believe there is a problem with some paths to lib files.

Bye
H

---

### Post by Hybrid Blue on 2006-06-12
[QUOTE=HJB]Hi HybridBlue, I got the whole thing working from the sources BUT, I cant get it to start. It didn't create the mythtv user. Im at work now and dont have my self made 'howto' with me. Tell me how you get this working. I believe there is a problem with some paths to lib files.

Bye
H[/QUOTE]


Ha! I finally got it, it appears that when you install the package cdparanoia via apt-get the mythtv configure script cant see it in /usr/lib (where the libs were located in my install) 

so what i did was export this to path by issueing..
export PATH="/usr/lib:$PATH" 

Then i Cd'ed to the path where ive got the source for the mythplugins and issued the config script as stated in the guide of the front page..

 sudo ./configure --prefix=/usr/local/mythtv-0.19 --enable-transcode --enable-vcd

The result was a success and im just about to run my make/make install =) 
Ill let you know if anything else breaks heh.. and if anyone needs help with getting this far let me know!

HB

---

### Post by Mehster on 2006-06-12
> Originally Posted by planetmn
I'm having the same problem:

```
root@mythtv:/usr/src/ivtv-0.4.4# ./ivtvfwextract.pl pvr_1.18.21.22254_inf.zip
-bash: ./ivtvfwextract.pl: No such file or directory
```

If I do an ls, the file is clearly there. Any ideas?

Thanks,dave

OK, it sounds like the perl script might not be set to executable.  Type sudo chmod +x ivtvfwextract.pl and then try again.

---

### Post by planetmn on 2006-06-12
[QUOTE=althepcman]Hi,

This happened to me after eading through the how to I found that sometimes installing the ivtv drviers, they would get install to:
/lib/modules/<kver>/ivtv
<kver> for me = 2.6.15.7-ubuntu1
This could be different.

To fix do the following:
sudo cp -r /lib/modules/<kver>/ivtv /lib/modules/`uname -r`/[/QUOTE]

It looks to me like neither of those directories had the module files.  /lib/modules/2.6.15 doesn't exist (<kver> = 2.6.15) and /lib/modules/2.6.15-23-386 had the following files:
```
david@mythtv:/lib/modules/2.6.15-23-386$ ls
build    madwifi-ng      modules.ieee1394map  modules.pcimap    volatile
initrd   modules.alias   modules.inputmap     modules.seriomap
kernel   modules.ccwmap  modules.isapnpmap    modules.symbols
madwifi  modules.dep     modules.ofmap        modules.usbmap

```

So I tried to reinstall the drivers and my output from make and make install is below.  I don't know much (well, really anything) about linux, but this didn't look like it worked for me.
```
david@mythtv:/usr/src/ivtv-0.4.4$ sudo make
make -C driver all
make[1]: Entering directory `/usr/src/ivtv-0.4.4/driver'
make -C /lib/modules/2.6.15-23-386/build M=/usr/src/ivtv-0.4.4/driver modules
make[2]: Entering directory `/usr/src/linux-source-2.6.15'

  WARNING: Symbol version dump /usr/src/linux-source-2.6.15/Module.symvers
           is missing; modules will have no dependencies and modversions.

  Building modules, stage 2.
  MODPOST
make[2]: Leaving directory `/usr/src/linux-source-2.6.15'
make[1]: Leaving directory `/usr/src/ivtv-0.4.4/driver'
make -C utils all
make[1]: Entering directory `/usr/src/ivtv-0.4.4/utils'
make -C ../driver ivtv-svnversion.h
make[2]: Entering directory `/usr/src/ivtv-0.4.4/driver'
make[2]: Leaving directory `/usr/src/ivtv-0.4.4/driver'
make CFLAGS="-I/usr/src/ivtv-0.4.4/utils -I/usr/src/ivtv-0.4.4/utils/../driver -D_GNU_SOURCE -O2 -Wall" -C ivtv-tune
make[2]: Entering directory `/usr/src/ivtv-0.4.4/utils/ivtv-tune'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/usr/src/ivtv-0.4.4/utils/ivtv-tune'
make CFLAGS="-I/usr/src/ivtv-0.4.4/utils -I/usr/src/ivtv-0.4.4/utils/../driver -D_GNU_SOURCE -O2 -Wall" -C cx25840ctl
make[2]: Entering directory `/usr/src/ivtv-0.4.4/utils/cx25840ctl'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/usr/src/ivtv-0.4.4/utils/cx25840ctl'
make[1]: Leaving directory `/usr/src/ivtv-0.4.4/utils'
make -C test all
make[1]: Entering directory `/usr/src/ivtv-0.4.4/test'
make[1]: Nothing to be done for `all'.
make[1]: Leaving directory `/usr/src/ivtv-0.4.4/test'
david@mythtv:/usr/src/ivtv-0.4.4$ sudo make install
make -C driver install
make[1]: Entering directory `/usr/src/ivtv-0.4.4/driver'
make -C /lib/modules/2.6.15-23-386/build M=/usr/src/ivtv-0.4.4/driver modules
make[2]: Entering directory `/usr/src/linux-source-2.6.15'

  WARNING: Symbol version dump /usr/src/linux-source-2.6.15/Module.symvers
           is missing; modules will have no dependencies and modversions.

  Building modules, stage 2.
  MODPOST
make[2]: Leaving directory `/usr/src/linux-source-2.6.15'
make INSTALL_MOD_PATH= INSTALL_MOD_DIR=ivtv \
                -C /lib/modules/2.6.15-23-386/build M=/usr/src/ivtv-0.4.4/driver modules_install
make[2]: Entering directory `/usr/src/linux-source-2.6.15'
  INSTALL /usr/src/ivtv-0.4.4/driver/ivtv-fb.ko
cp: omitting directory `/lib/modules/2.6.15-23-386'
make[3]: *** [/usr/src/ivtv-0.4.4/driver/ivtv-fb.ko] Error 1
make[2]: *** [modules_install] Error 2
make[2]: Leaving directory `/usr/src/linux-source-2.6.15'
make[1]: *** [install] Error 2
make[1]: Leaving directory `/usr/src/ivtv-0.4.4/driver'
make: *** [install] Error 2

```

I'm sorry to keep posting more and more problems, but cany anybody tell me if the modules even installed correctly?

Thanks,
dave

---

### Post by Hybrid Blue on 2006-06-12
Ahh Now that i have fixed my problem with myth not wanting to build with mythmusic installed (fixed..see last post about two above this for how) 

I seem to be having a problem with mythtv seting my tuners properly..ive been reading that this might be an issue with the ownership/premissions on the device? At the moment it appears that myth is trying to use the device's in PAL mode where i need them in NTSC-us. I only have an idea this is happening because i got video to show when using a GUI for messing with the cards just to test that they were working properly... After i messed with the settings and got them set to NTSC in this GUI it seemed to work fine.. 

Has anyone else had this problem or might know how i can fix it? I feel im getting close lol, im almost ready to toss this system into my "server" room but ive still got to get this last thing working lol.

Thanks for all the help everyone =) i havnt posted much till now but all your comments and the guides have been a great help so far!

-HB

---

### Post by MetalMusicAddict on 2006-06-12
Just a quick one. Im about to get a Hauppauge card but I was thinking to use Xubuntu as a base. Shouldnt be a problem using this guide right? Nothing *looks* Gnome specific.

---

### Post by kayno on 2006-06-12
[QUOTE=Hybrid Blue]Ahh Now that i have fixed my problem with myth not wanting to build with mythmusic installed (fixed..see last post about two above this for how) 
[/QUOTE]

can you go into a little more detail on how you got mythmusic working? I am trying to apt-get install mythmusic, but get the following error:

```
The following packages have unmet dependencies.
  mythmusic: Depends: libcdaudio0 but it is not installable
E: Broken packages
```

I added /usr/lib to my path as you said you did, but this didnt help. I *don't really* want to have to compile mythplugins myself - I was able to apt-get instally mythvideo and mythweb, and mythmusic is the only one left i want.

Any help would be greatly appreciated - my mythbox is nearly back to the way it was when it was running with fedora core 5, and once this and the remote is working, my love affair with ubuntu will be complete.

---

### Post by Hybrid Blue on 2006-06-12
[QUOTE=kayno]can you go into a little more detail on how you got mythmusic working? I am trying to apt-get install mythmusic, but get the following error:

```
The following packages have unmet dependencies.
  mythmusic: Depends: libcdaudio0 but it is not installable
E: Broken packages
```

I added /usr/lib to my path as you said you did, but this didnt help. I *don't really* want to have to compile mythplugins myself - I was able to apt-get instally mythvideo and mythweb, and mythmusic is the only one left i want.

Any help would be greatly appreciated - my mythbox is nearly back to the way it was when it was running with fedora core 5, and once this and the remote is working, my love affair with ubuntu will be complete.[/QUOTE]


When i installed i had to download the package then use dpkg -i to install it...

This is where i got it from 
[http://packages.ubuntulinux.org/warty/libs/libcdaudio0](http://packages.ubuntulinux.org/warty/libs/libcdaudio0)

For some reson i couldnt get it from apt

[edit] you could also try issueing sudo apt-get -f install [/edit]

---

### Post by kayno on 2006-06-12
[QUOTE=Hybrid Blue]When i installed i had to download the package then use dpkg -i to install it...

This is where i got it from 
[http://packages.ubuntulinux.org/warty/libs/libcdaudio0](http://packages.ubuntulinux.org/warty/libs/libcdaudio0)

For some reson i couldnt get it from apt[/QUOTE]

awesome :D. I had to dpkg -r libcdaudio-dev and libcdaudio1 first, but then your steps worked fine. thanks :)

all looks pretty good now:

```
dpkg -l | grep myth
ii  libmyth                                0.19-5                                Common library code for MythTV and add-on mo
rc  libmyth-0.18.1c2a                      0.18.1-5ubuntu3                       Common library code for MythTV and add-on mo
rc  libmyth-0.19.c2a                       0.19-0ubuntu0                         Common library code for MythTV and add-on mo
ii  mythmusic                              0.19-5                                Music add-on module for MythTV
ii  myththemes                             0.19-5                                A personal video recorder application (extra
ii  mythtv                                 0.19-5                                A personal video recorder application (clien
ii  mythtv-backend                         0.19-5                                A personal video recorder application (serve
ii  mythtv-common                          0.19-5                                A personal video recorder application (commo
ii  mythtv-database                        0.19-5                                A personal video recorder application (datab
ii  mythtv-frontend                        0.19-5                                A personal video recorder application (clien
ii  mythtv-lcdserver                       0.19-5                                A personal video recorder application (clien
ii  mythvideo                              0.19-5                                A generic video player frontend module for M
ii  mythweb                                0.19-5                                Web interface add-on module for MythTV
```
 
for **libmyth-0.18.1c2a** and **libmyth-0.19.c2a,** can i simply **dpkg -r --purge** them, or will it nuke settings or something?

---

### Post by Hybrid Blue on 2006-06-13
[QUOTE=kayno]awesome :D. I had to dpkg -r libcdaudio-dev and libcdaudio1 first, but then your steps worked fine. thanks :)

all looks pretty good now:

```
dpkg -l | grep myth
ii  libmyth                                0.19-5                                Common library code for MythTV and add-on mo
rc  libmyth-0.18.1c2a                      0.18.1-5ubuntu3                       Common library code for MythTV and add-on mo
rc  libmyth-0.19.c2a                       0.19-0ubuntu0                         Common library code for MythTV and add-on mo
ii  mythmusic                              0.19-5                                Music add-on module for MythTV
ii  myththemes                             0.19-5                                A personal video recorder application (extra
ii  mythtv                                 0.19-5                                A personal video recorder application (clien
ii  mythtv-backend                         0.19-5                                A personal video recorder application (serve
ii  mythtv-common                          0.19-5                                A personal video recorder application (commo
ii  mythtv-database                        0.19-5                                A personal video recorder application (datab
ii  mythtv-frontend                        0.19-5                                A personal video recorder application (clien
ii  mythtv-lcdserver                       0.19-5                                A personal video recorder application (clien
ii  mythvideo                              0.19-5                                A generic video player frontend module for M
ii  mythweb                                0.19-5                                Web interface add-on module for MythTV
```
 
for **libmyth-0.18.1c2a** and **libmyth-0.19.c2a,** can i simply **dpkg -r --purge** them, or will it nuke settings or something?[/QUOTE]


Im not sure about using purge on them as i havnt done that but maybe someone else here might be able to help you out? Im glad to hear that i could be of help as well! =)

HB

---

### Post by HJB on 2006-06-13
Hi MetalMusicAddict.
Im using Xfce4 without anyproblems. Using most of the apps you mention.

Works great
Its very similar to Gnome but not so bloaty

"You can run Gnome applications, because desktop "Xfce4" environment provides the possibility to initialize Gnome base system at start-up."
Have a look here: [http://www.xbox-linux.org/wiki/XUbuntu](http://www.xbox-linux.org/wiki/XUbuntu)

Bye
H

---

### Post by scifan on 2006-06-13
I actually started with this guide... and then after having problems which turned out to be caused by running IVTV 0.4.5 (run 0.4.4!!!), I actually built mythtv 0.19 from source.. . and it seems to work great...

We'll have to see how stable it is... my last adventure with myth was pretty decent, but was based upon knoppmyth (and had issue's with too much garbage in log files causing the system to detonate).

best of luck guy's... it is worth the effort... 

My PVR 500 works GREAT... have NVIDIA drivers driving my TV at 720P (need to figure out how to scale this down just a little bit... )

---

### Post by volksman on 2006-06-13
Any chance this works with the USB2 device from Hauppagge?

---

### Post by Hybrid Blue on 2006-06-13
[QUOTE=volksman]Any chance this works with the USB2 device from Hauppagge?[/QUOTE]

I remember seeing somewhere that you can use mythtv with an external USB tuner, i dont really remember which one your talking about or if i know the correct one at all =) but here is a list of what people have in their systems which you can do a search on your cards model to see if its in use by someone =)

[http://pvrhw.goldfish.org/tiki-pvrhwdb.php](http://pvrhw.goldfish.org/tiki-pvrhwdb.php)

Hope this helps =)

HB

---

### Post by HJB on 2006-06-13
[QUOTE=scifan]I actually started with this guide... and then after having problems which turned out to be caused by running IVTV 0.4.5 (run 0.4.4!!!), I actually built mythtv 0.19 from source.. . and it seems to work great...
)[/QUOTE]

Hi scifan

Can you please write down the steps you took compiling the source.
Did you only do the 

./configure
qmake mythtv.pro
make

or did you add settings to the configure?
When I did it no mythtv user was created?

Please help

Bye
H

---

### Post by dodongo on 2006-06-13
So suppose you'd followed everyone's (very helpful, thanks!) instructions, and based on dmesg output*, you had everything installed properly and should be good to go... but there's no good output to speak of from the card.

Part of the problem is that I don't have cable to run to the TV at the moment.  And though there is an OTA channel nearby which I should (theoretically) be able to receive, I can't believe the dipole they included would get anything on broadcast TV frequencies.

But wait!  There's more!  I *can* do full test runs on broadcast *FM*.  And what I get there is something screechy that sounds kinda like a sawtooth wave.  This on a frequency which my little alarm clock receives crystal-clear.

Does anyone have any ideas as to why what should be a good install of the software at this point leads to bizarre hardware malfunction?  Any ideas of test I could run in the signal chain to see what's up?

Thanks!

-Chuck
-------------
* - Here it is:
```

[4294689.923000] ivtv:  ==================== START INIT IVTV ====================
[4294689.923000] ivtv:  version 0.4.4 (tagged release) loading
[4294689.923000] ivtv:  Linux version: 2.6.15-23-686 SMP preempt 686 gcc-4.0
[4294689.923000] ivtv:  In case of problems please include the debug info between
[4294689.923000] ivtv:  the START INIT IVTV and END INIT IVTV lines, along with
[4294689.923000] ivtv:  any module options, when mailing the ivtv-users mailinglist.
[4294689.923000] ivtv0: Autodetected WinTV PVR 350 card (cx23415 based)
[4294689.923000] ACPI: PCI Interrupt 0000:02:00.0[A] -> GSI 21 (level, low) -> IRQ 209
[4294689.923000] ivtv0: Unreasonably low latency timer, setting to 64 (was 32)
[4294689.952000] ivtv0: i2c attach to card #0 ok [client=tveeprom, addr=50]
[4294689.993000] tveeprom 0-0050: Hauppauge model 48132, rev K268, serial# 8551606
[4294689.993000] tveeprom 0-0050: tuner model is LG TAPE H001F MK3 (idx 68, type 47)
[4294689.993000] tveeprom 0-0050: TV standards NTSC(M) (eeprom 0x08)
[4294689.993000] tveeprom 0-0050: audio processor is MSP4448 (idx 27)
[4294689.993000] tveeprom 0-0050: decoder processor is SAA7115 (idx 19)
[4294689.993000] tveeprom 0-0050: has radio, has IR remote
[4294690.055000] tuner 0-0061: chip found @ 0xc2 (ivtv i2c driver #0)
[4294690.055000] ivtv0: i2c attach to card #0 ok [client=(tuner unset), addr=61][4294690.219000] hiddev96: USB HID v1.10 Device [APC Back-UPS ES 500 FW:801.e3.D USB FW:e3] on usb-0000:00:1d.1-2
[4294690.230000] saa7115 0-0021: saa7115 found @ 0x42 (ivtv i2c driver #0)
[4294690.328000] Build date: May 29 2006
[4294690.328000] Debugging version (IEEE80211)
[4294690.328000] ath0: 11b rates: 1Mbps 2Mbps 5.5Mbps 11Mbps
[4294690.328000] ath0: 11g rates: 1Mbps 2Mbps 5.5Mbps 11Mbps 6Mbps 9Mbps 12Mbps 18Mbps 24Mbps 36Mbps 48Mbps 54Mbps
[4294690.328000] ath0: turboG rates: 6Mbps 9Mbps 12Mbps 18Mbps 24Mbps 36Mbps 48Mbps 54Mbps
[4294690.328000] ath0: H/W encryption support: WEP AES AES_CCM TKIP
[4294690.328000] ath0: mac 5.9 phy 4.3 radio 4.6
[4294690.328000] ath0: Use hw queue 1 for WME_AC_BE traffic
[4294690.328000] ath0: Use hw queue 0 for WME_AC_BK traffic
[4294690.328000] ath0: Use hw queue 2 for WME_AC_VI traffic
[4294690.328000] ath0: Use hw queue 3 for WME_AC_VO traffic
[4294690.328000] ath0: Use hw queue 8 for CAB traffic
[4294690.328000] ath0: Use hw queue 9 for beacons
[4294690.328000] Debugging version (ATH)
[4294690.328000] ath0: Atheros 5212: mem=0xff9f0000, irq=201
[4294690.349000] input: Logitech USB Receiver as /class/input/input2
[4294690.349000] input: USB HID v1.11 Mouse [Logitech USB Receiver] on usb-0000:00:1d.1-1.4
[4294690.349000] usbcore: registered new driver usbhid
[4294690.349000] drivers/usb/input/hid-core.c: v2.6:USB HID core driver
[4294690.359000] ivtv0: i2c attach to card #0 ok [client=saa7115, addr=21]
[4294690.403000] drivers/usb/class/usblp.c: usblp0: USB Bidirectional printer dev 4 if 0 alt 0 proto 2 vid 0x04E8 pid 0x323A
[4294690.403000] usbcore: registered new driver usblp
[4294690.403000] drivers/usb/class/usblp.c: v0.13: USB Printer Device Class driver
[4294690.449000] saa7127 0-0044: ivtv driver
[4294690.451000] saa7127 0-0044: saa7129 found @ 0x88 (ivtv i2c driver #0)
[4294690.453000] ivtv0: i2c attach to card #0 ok [client=saa7127, addr=44]
[4294690.492000] ts: Compaq touchscreen protocol output
[4294690.525000] msp3400 0-0040: chip=MSP4448G-B3 +nicam +simple +simpler +radio mode=simpler
[4294690.525000] msp3400 0-0040: msp34xxg daemon started
[4294690.545000] ivtv0: i2c attach to card #0 ok [client=MSP4448G-B3, addr=40]
[4294690.582000] tda9887 0-0043: chip found @ 0x86 (ivtv i2c driver #0)
[4294690.582000] ivtv0: i2c attach to card #0 ok [client=tda9887, addr=43]
[4294691.255000] ivtv0: loaded v4l-cx2341x-enc.fw firmware (262144 bytes)
[4294691.286000] ivtv0: loaded v4l-cx2341x-dec.fw firmware (262144 bytes)
[4294691.496000] ivtv0: Encoder revision: 0x02050032
[4294691.506000] ivtv0: Decoder revision: 0x02020023
[4294691.506000] ivtv0: Allocate DMA encoder MPEG stream: 128 x 32768 buffers (4096KB total)
[4294691.506000] ivtv0: Allocate DMA encoder YUV stream: 194 x 10800 buffers (2048KB total)
[4294691.507000] ivtv0: Allocate DMA encoder VBI stream: 120 x 17472 buffers (2048KB total)
[4294691.507000] ivtv0: Allocate DMA encoder PCM audio stream: 455 x 4608 buffers (2048KB total)
[4294691.508000] ivtv0: Create encoder radio stream
[4294691.508000] ivtv0: Allocate DMA decoder MPEG stream: 16 x 65536 buffers (1024KB total)
[4294691.508000] ivtv0: Allocate DMA decoder VBI stream: 512 x 2048 buffers (1024KB total)
[4294691.509000] ivtv0: Create decoder VOUT stream
[4294691.509000] ivtv0: Allocate DMA decoder YUV stream: 24 x 43200 buffers (1024KB total)
[4294691.550000] ivtv0: loaded v4l-cx2341x-init.mpg firmware (155648 bytes)
[4294691.660000] tuner 0-0061: type set to 47 (LG NTSC (TAPE series))
[4294691.930000] ivtv0: Initialized WinTV PVR 350, card #0
[4294691.930000] ivtv:  ====================  END INIT IVTV  ====================

```

---

### Post by dodongo on 2006-06-13
[QUOTE=planetmn]I'm having the same problem:
```
root@mythtv:/usr/src/ivtv-0.4.4# ./ivtvfwextract.pl pvr_1.18.21.22254_inf.zip
-bash: ./ivtvfwextract.pl: No such file or directory

```

If I do an ls, the file is clearly there.  Any ideas?

Thanks,dave[/QUOTE]

I saw up above you'd already fixed this problem.  However, it looks like you just have a syntax error in your command.  The pound sign (#) needs to be replaced wtih the version of the driver you're *actually* using -- probably either a 4 or a 5.  The zip file you downloaded should contain the version number.

---

### Post by Vincent_Lin on 2006-06-13
I have a question.  well, a problem.  I must have done something wrong,

while I was doing mythfilldatabase, a number of errors came out:

DB Error (Inserting into programgenres table):
Query was:
INSERT IGNORE INTO programgenres (chanid, starttime, relevance, genre) SELECT chanid, starttime, relevance, class FROM dd_v_program, dd_genre WHERE (dd_v_program.programid = dd_genre.programid);
Driver error was [2/1146]:
QMYSQL3: Unable to execute query
Database error was:
Table 'mythconverg.dd_v_program' doesn't exist

Could someone help?

Thanks.

Vincent

---

### Post by NT4usB on 2006-06-13
[QUOTE=scifan]I actually started with this guide... and then after having problems which turned out to be caused by running IVTV 0.4.5 (run 0.4.4!!!), I actually built mythtv 0.19 from source.. . and it seems to work great...[/QUOTE]

What troubles did 0.4.5 cause? I'm struggling with changing channels on one of my tuners. May be related?

---

### Post by scifan on 2006-06-14
basic symptom was that I would see a given channel nice and clear, try to change channels and my system would freeze.

Problems don't exist with 0.4.4... 

Run your mythbackend with a "-v playback" and check your logs... (if you have logging enabled).

there was an IVTV error when I'd try and change channels... when I searched on gossemer-threads (however it's spelled) the result basically stated that there were issue's with the 0.4.5 version and with 0.6.2... and to run either 0.4.4 or 0.6.1 depending on which kernel your running.

hope this helps...

my current issue is trying to figure out how to setup mythweb... might need to get some help with my .htaccess file...

I get the following error:
```
Database Setup Error

The database environment variables are not correctly set in the
included .htaccess file. Please read through the comments included
in the file and set up the db_* environment variables correctly.

Some possible solutions are to make sure that mod_env is enabled
in httpd.conf, as well as having followed the instructions in the
README about the AllowOverride settings.

```

though I've looked through the config/conf.php file and have worked with the .htaccess file... searching for idea's... :)

home this helps you.

---

### Post by kayno on 2006-06-14
[QUOTE=scifan]
my current issue is trying to figure out how to setup mythweb... might need to get some help with my .htaccess file...

I get the following error:
```
Database Setup Error

The database environment variables are not correctly set in the
included .htaccess file. Please read through the comments included
in the file and set up the db_* environment variables correctly.

Some possible solutions are to make sure that mod_env is enabled
in httpd.conf, as well as having followed the instructions in the
README about the AllowOverride settings.

```

though I've looked through the config/conf.php file and have worked with the .htaccess file... searching for idea's... :)

home this helps you.[/QUOTE]

maybe you need to enable the mod_env module for apache. i think this should do it:

```
sudo /usr/sbin/apache-modconf apache enable mod_env
```

---

### Post by scifan on 2006-06-14
got it...
had to actually load the rewrite_module also... :)

---

### Post by FujiApples on 2006-06-14
Hi Everyone,

I'm trying to setup a pvr500 card and I'm stuck after installing the ivtv drivers.  When testing the drivers using
```
cat /dev/video0 > /tmp/test.mpg
```
my computer crashes and reboots.  It does the same thing when I try and veiw the stream in mplayer with
```
mplayer /dev/video0
```

The playback will work for a while, maybe 15 seconds, before crashing.  Any ideas?

Thanks for the help.

---

### Post by NT4usB on 2006-06-14
[QUOTE=scifan]basic symptom was that I would see a given channel nice and clear, try to change channels and my system would freeze.

Problems don't exist with 0.4.4... [/QUOTE]

Sounds like what I've been fighting. 
What troubles me is, at first both cards would freeze. I screwed with permissions and a bunch of stuff I had no idea what I was messing with and got one card to work. 
Last night, I messed a little bit with stuff and both cards work. 
I hate to remove the 4.5. For sure I'll wreck the dependancies and end up formating and starting over again...

[QUOTE=scifan]
Run your mythbackend with a "-v playback" and check your logs... (if you have logging enabled).[/QUOTE]

I've been running terminal with --verbose all on the frontend, seeing errors there and chasing them. Sounds like I'm working the wrong end of the problem...
I did have the log enabled in Myth. googled around some of the errors. Apparently, lots of people asking, not too many people solving...

[QUOTE=scifan]
there was an IVTV error when I'd try and change channels... when I searched on gossemer-threads (however it's spelled) the result basically stated that there were issue's with the 0.4.5 version and with 0.6.2... and to run either 0.4.4 or 0.6.1 depending on which kernel your running.[/QUOTE]

I've seen some ivtv error messages. googling around finds suggestions for fixes and workarounds. That's what I've been messing with. Wish I was better at documenting all the krap I changed... what worked and what didn't (*as if* I really knew.)

[QUOTE=scifan]
hope this helps...
[/QUOTE]

It does. 
Going to read up on the gossimer info and soon as I manage to jack this current build beyond repair, I'll remember to use the 4.4's when I start over...

[QUOTE=scifan]
my current issue is trying to figure out how to setup mythweb... might need to get some help with my .htaccess file...[/QUOTE]

I think I played with that for 10 minutes one night.
(try to stay focused on the pvr problems but sometimes I wander off on tangents, trying the other features, breaking other things...) 
I pointed it at Firefox, opened Firefox and had a look. Concluded I have three perfectly good lcd's on my desk for browsing, don't need to surf my tv too...

---

### Post by tedwardo2 on 2006-06-14
[QUOTE=laurens]You can also edit the file, and replace all occurances of repeat with `repeat` (backticks!!). 

This is untested, but I have done things like this in the past with mysql. Hope it helps - it seems less painfull than downgrading :)

Cheers![/QUOTE]

I'm having this problem, too.  I tried downgrading to mysql4 but it didn't work.  Does anyone know where the file I have to put backticks around the word "repeat" is?

---

### Post by kcrajkumar on 2006-06-14
[QUOTE=Hybrid Blue]Im not sure about using purge on them as i havnt done that but maybe someone else here might be able to help you out? Im glad to hear that i could be of help as well! =)

HB[/QUOTE]
Hi Kayno / Hybrid Blue,

    Could you please explain how you installed from source ??  I have followed the step and installed everything upto MythTv Installation.  I want to install 0.19  but don't know to use the sources ( sources.list )  mentioned on this list or use mythtv documentation to get the source code and compile it... could you please let us know how did you install 0.19... if you have documentation on that please provide.  Appreciate your help.  Thanks.

---

### Post by dmitryse on 2006-06-14
Great guide, thanks! 

I was following this thread for some time now and finally everything works on my install, except the strange problem with the remote control. I have MCE USB remote, all drivers configured, everything worked fine. My box is set to auto-logon as mythtv user, and start the mythfrontend automatically (via Sessions/Startup Programs). Every time I reboot, the remote would not work. If I exit the mythfrontend, and start it up again, the remote works. When I log off, and log on as mythtv user, the remote works.  Here is what I have checked so far: 

1. lircd is running
2. Both /home/mythtv/.lircrc and /home/mythtv/.mythtv/lircrc configuration files are present, they both symbolic links and point to /etc/lircrc configuration file
3. mythtv user has read and write access to /dev/lircd

My .xsession-errors file has the following relevant lines:

The first time mythfrontend starts up on fresh boot
------------snip--------------------
mythtv: could not connect to socket
mythtv: Connection refused
lirc_init failed for mythtv, see preceding messages
-----------snip----------------------

Any consecutive starts of mythfrontend do not generate any “lirc_init failed” messages and remote works. 

Any ideas?

Thanks

---

### Post by Hybrid Blue on 2006-06-14
[QUOTE=kcrajkumar]Hi Kayno / Hybrid Blue,

    Could you please explain how you installed from source ??  I have followed the step and installed everything upto MythTv Installation.  I want to install 0.19  but don't know to use the sources ( sources.list )  mentioned on this list or use mythtv documentation to get the source code and compile it... could you please let us know how did you install 0.19... if you have documentation on that please provide.  Appreciate your help.  Thanks.[/QUOTE]

Ill have to take a little while to make a write-up of how i got everything working.. Ill get working on it tonight and post what ive got for ya tomorrow.

---

### Post by kayno on 2006-06-14
[QUOTE=kcrajkumar]Hi Kayno / Hybrid Blue,

    Could you please explain how you installed from source ??  I have followed the step and installed everything upto MythTv Installation.  I want to install 0.19  but don't know to use the sources ( sources.list )  mentioned on this list or use mythtv documentation to get the source code and compile it... could you please let us know how did you install 0.19... if you have documentation on that please provide.  Appreciate your help.  Thanks.[/QUOTE]


i never installed from source. add these lines to your /etc/apt/sources.list:

[INDENT]deb [http://home.eng.iastate.edu/~superm1](http://home.eng.iastate.edu/~superm1) dapper main
deb-src [http://home.eng.iastate.edu/~superm1](http://home.eng.iastate.edu/~superm1) dapper main
deb [http://knm.org/mythdebs/](http://knm.org/mythdebs/) binary/
deb-src [http://knm.org/mythdebs/](http://knm.org/mythdebs/) source/[/INDENT]

and then update:

[INDENT]sudo apt-get update[/INDENT]

then install mythtv and required plugins:

[INDENT]sudo apt-get install mythtv [/INDENT]

and any plugins you want, eg:

[INDENT]sudo apt-get install mythmusic
sudo apt-get install mythvideo
sudo apt-get install mythweb[/INDENT]

---

### Post by gyro on 2006-06-14
I have been using linux for only three days now so I am very new to this I am getting stuck at this point:

> apt-get install linux-source-<kver> linux-headers-`uname -r`

this is what I see in my terminal:


root@brian-desktop:~# apt-get install linux-source-2.6.15 linux-headers-`uname -r`
Reading package lists... Done
Building dependency tree... Done
Package linux-source-2.6.15 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package linux-source-2.6.15 has no installation candidate

Any help would be greatly appreciated.  I'm sure this is a silly question  but I am still just learning the basics.

thanks,
brian

---

### Post by althepcman on 2006-06-15
[QUOTE=gyro]I have been using linux for only three days now so I am very new to this I am getting stuck at this point:



this is what I see in my terminal:


root@brian-desktop:~# apt-get install linux-source-2.6.15 linux-headers-`uname -r`
Reading package lists... Done
Building dependency tree... Done
Package linux-source-2.6.15 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package linux-source-2.6.15 has no installation candidate

Any help would be greatly appreciated.  I'm sure this is a silly question  but I am still just learning the basics.

thanks,
brian[/QUOTE]

Try:
sudo apt-get install linux-source

See what happens then. :)

---

### Post by dmitryse on 2006-06-16
> Every time I reboot, the remote would not work. If I exit the mythfrontend, and start it up again, the remote works. When I log off, and log on as mythtv user, the remote works. 

I found wat was wrong with the remote - lirc start sequence number. In my install, the lirc start sequence number was set to 99:

```
update-rc.d lirc defaults 99
```

It seems that mythfrontend was loading before lirc. I had to change the lirc start sequence:

Remove lirc from autostart:
```

sudo update-rc.d -f lirc remove
```

than add it again, this time with the different start sequence number:

```
sudo update-rc.d lirc defaults 20
```

It fixed the problem

---

### Post by dodongo on 2006-06-16
[QUOTE=althepcman]Try:
sudo apt-get install linux-source

See what happens then. :)[/QUOTE]

This should fix your problem.  Reason being, Ubuntu has a series of "metapackages" which help make sure important parts of your system stay in sync.  For example, there's a linux-kernel-[processor] metapackage, as well as a linux-source metapackage.  When you get a kernel update, the metapackage changes* to instruct the system that there's a new version which needs to be installed.

This is done for a variety of reasons, the biggest being that if a bug should occur in a new kernel update, people's systems might not boot!  Thus, having the old kernel still on your machine is a very good thing, at least for a little while.  The metapackages let Ubuntu do that, while still automatically updating the kernel packages when new versions are needed.

The linux-source and linux-kernel metapackages will update at the same time, which will ensure you have the correct source to build against.

-------------

* - I think I'm right on this?  Right?  ;)

---

### Post by wardjame on 2006-06-21
I had ivtv working ok but it now hates me.  I was able to test using the cat /dev/video0 > /tmp/test.mpg on both cards without any problems but the command now fails with cat: /dev/video0: No such file or directory.  And modprobe ivtv returns FATAL: Module ivtv not found.  I re-ran the section on installing ivtv and am still getting the same errors.  Any suggestions?

---

### Post by chadk on 2006-06-22
[QUOTE=kayno]i never installed from source. add these lines to your /etc/apt/sources.list:

[INDENT]sudo apt-get install mythmusic
sudo apt-get install mythvideo
sudo apt-get install mythweb[/INDENT][/QUOTE]


I was happy to see all this but then I went and tried installing myth tv and got this:
```
Setting up mythtv-backend (0.19-5) ...
Starting MythTV server: mythbackendSession management error: Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed
.

Setting up mythtv-lcdserver (0.19-5) ...
Errors were encountered while processing:
 mythtv-database
 mythtv
E: Sub-process /usr/bin/dpkg returned an error code (1)

```
????

---

### Post by antonis_wrx on 2006-06-22
I followed the instructions in the first post and then these instructions: [http://hyams.webhop.net/mythtv/myth_ubuntu.html](http://hyams.webhop.net/mythtv/myth_ubuntu.html) but still I can't use my hauppauge 250 pvr pci. kdetv doesn't work at all, tvtime returns the following error message:
```
Running tvtime 1.0.1.
Reading configuration from /etc/tvtime/tvtime.xml
Reading configuration from /home/antonis/.tvtime/tvtime.xml
videoinput: Card failed to allocate capture buffers: Invalid argument
```

dmesg output is:
```
[17179591.088000] ivtv:  ==================== START INIT IVTV ================== ==
[17179591.088000] ivtv:  version 0.4.5 (tagged release) loading
[17179591.088000] ivtv:  Linux version: 2.6.15-25-386 preempt 486 gcc-4.0
[17179591.088000] ivtv:  In case of problems please include the debug info betwe en
[17179591.088000] ivtv:  the START INIT IVTV and END INIT IVTV lines, along with
[17179591.088000] ivtv:  any module options, when mailing the ivtv-users mailing list.
[17179591.088000] ivtv0: Autodetected WinTV PVR 250 card (cx23416 based)
[17179591.088000] ACPI: PCI Interrupt 0000:02:09.0[A] -> GSI 21 (level, low) -> IRQ 217
[17179591.100000] skge eth0: enabling interface
[17179591.144000] tveeprom: ivtv version
[17179591.144000] tveeprom: Hauppauge: model = 32034, rev = B148, serial# = 6912 309
[17179591.144000] tveeprom: tuner = LG TP18PSB11D (idx = 48, type = 29)
[17179591.144000] tveeprom: tuner fmt = PAL(B/G) (eeprom = 0x04, v4l2 = 0x000000 07)
[17179591.144000] tveeprom: audio processor = MSP3415 (type = 6)
[17179591.144000] tveeprom: decoder processor = SAA7115 (type = 13)
[17179591.144000] ivtv0: i2c attach to card #0 ok [client=tveeprom, addr=50]
[17179591.276000] tuner (ivtv): chip found at addr 0xc2 i2c-bus ivtv i2c driver #0
[17179591.276000] ivtv0: i2c attach to card #0 ok [client=(tuner unset), addr=61 ]
[17179591.444000] saa7115 0-0021: saa7115 found @ 0x42 (ivtv i2c driver #0)
[17179591.568000] ivtv0: i2c attach to card #0 ok [client=saa7115, addr=21]
[17179591.616000] msp3400 0-0040: chip=MSP3415G-B8 +nicam +simple +simpler +radi o mode=simpler
[17179591.616000] msp3400 0-0040: msp34xxg daemon started
[17179591.636000] ivtv0: i2c attach to card #0 ok [client=MSP3415G-B8, addr=40]
[17179591.720000] ACPI: PCI Interrupt 0000:00:1f.5[B] -> GSI 17 (level, low) -> IRQ 225
[17179591.720000] PCI: Setting latency timer of device 0000:00:1f.5 to 64
[17179592.040000] intel8x0_measure_ac97_clock: measured 54682 usecs
[17179592.040000] intel8x0: clocking to 48000
[17179592.084000] input: ImPS/2 Generic Wheel Mouse as /class/input/input2
[17179592.096000] ts: Compaq touchscreen protocol output
[17179592.332000] ivtv0: loaded v4l-cx2341x-enc.fw firmware (262144 bytes)
[17179592.548000] ivtv0: Encoder revision: 0x02050032
[17179592.548000] ivtv0: Allocate DMA encoder MPEG stream: 128 x 32768 buffers ( 4096KB total)
[17179592.548000] ivtv0: Allocate DMA encoder YUV stream: 161 x 12960 buffers (2 048KB total)
[17179592.548000] ivtv0: Allocate DMA encoder VBI stream: 80 x 26208 buffers (20 48KB total)
[17179592.548000] ivtv0: Allocate DMA encoder PCM audio stream: 455 x 4608 buffe rs (2048KB total)
[17179592.548000] tuner: type set to 29 (LG PAL_BG (TPI8PSB11D)) by ivtv i2c dri ver #0
[17179592.788000] ivtv0: Initialized WinTV PVR 250, card #0
[17179592.792000] ivtv:  ====================  END INIT IVTV  ==================
```

---

### Post by scifan on 2006-06-24
What happens if you cat /dev/video0 > testfile.mpg do you get anything?

I have a pvr500 and with ivtv 4.5 and the default dapper kernel I would get choppy video playback and actually the driver would crash when I'd try and change channels.

What I have found for working succes on my system:

Ivtv 4.4 (there are issue's with IVTV 4.5 and with IVTV 6.3 - read gossimer Threads)
LIRC 0.8.0 (compiled so I could have mceusb2 for my USB MCE IR receiver happy)
mysql 4.1 
mythtv 19.1 fixes installed from one of the sites - I don't remember which  at one point I'd actually downloaded the deb's at a previous stage of this adventure... so when I decided to try them again, I dpkg installed them from my local source... (the version referenced in the deb name is 0.19-5)... make sure you install the libmyth-dev deb so you can download the mythtv 19 plugins source and compile mythmusic which isn't installable under dapper due to unresolved dependancies (read above in this thread)...  
(./configure --enable-all --prefix=/usr
make) will make the modules using the configurations you need... expect to have to add dev libraries to fully make mythmusic... make sure you get the SDL library or goom won't work...
and then just copy the mythmusic plugin (libmythmusic.so) to the plugins directory in /usr/lib/mythtv

I'm running mysql 4.1 because I'd been trying all sorts of things to resolve the pesky sql server has "gone away" messages.  I'd tried running my system with mysql 5.0 - broke enough things that the front end was segfaulting... so I broke down and re-installed - and with this installation I loaded mysql 4.1  and tried mythtv 18.1 and 19.0 and had issue's with mysql again.  decided to give 19.1 (19-5) one more try and success... I'm unsure that it's worth my effort to migrate back to mysql 5.0 from 4.1... you know - don't "fix it" unless it's broken... and at this point it's not broken.

At this point I have all of the "current" season passes copied into my mythbox (have ~ 350 scheduled items, 66 recorded programs consuming ~ 53gb (some of half hour programs for my kids)  and it's running stable... I'm transcoding all of the programs that are being recorded to xvid and I'm experiencing a good space savings over the mpeg2 files from the PVR500)  Make sure that if you have a PVR card, you make sur eyou record at 720x480 to ensure your video looks good.. :)

Commercial skip seems to work very well.

I have everything running out 720p/component video to my HDTV which is working pretty decently.

---

### Post by antonis_wrx on 2006-06-24
[QUOTE=scifan]What happens if you cat /dev/video0 > testfile.mpg do you get anything?
[/QUOTE]

I get no error messages. Here's the testfile.mpg I get. [http://rapidshare.de/files/24024807/testfile.mpg.html](http://rapidshare.de/files/24024807/testfile.mpg.html) I don't know if this is what I am supposed to get. Using ivtv-tune -c # -d /dev/video0 I get a black screen on mplayer

---

### Post by _cashel on 2006-06-27
I've been following this guide up to the part of installing MythTV with no errors whatsoever. When I ran 

```
apt-get install mythtv mythbrowser mythdvd mythgallery mythmusic mythnews mythvideo mythweather
```

it went through the entire install process and asked for my mysql password. I thought I entered in the password correctly (the same password used for phpmyadmin), but I get an error stating it failed to connect to the database after it's finished running through the install. If I re-enter the above command, it basically says the same thing and doesn't even run the install for me to enter the mysql password. How can I get it to run the install so I can retry the password?

Also, I was planning on following this guide step by step, installing 0.18, and immediately after installing 0.18, upgrade/manually compile 0.19 (I ran into some trouble just trying to compile 0.19 before and fubared everything). I shouldn't have any trouble doing this should I? Nothing *should* screw up?


edit: I changed the pass in the mysql.txt to the real phpmyadmin/mysql pass, I had mistyped it. When running the apt-get install command I still get a cannot connect to database error

---

### Post by chadk on 2006-06-27
Is it possible for someone to VNC to my system and install MythTV assuming I open the port on my router?  I have this card installed and it's just sitting there.  Wish I could use it.

---

### Post by chadk on 2006-06-27
[QUOTE=chadk]Is it possible for someone to VNC to my system and install MythTV assuming I open the port on my router?  I have this card installed and it's just sitting there.  Wish I could use it.[/QUOTE]

c'mon! It'll be fun!

---

### Post by inf0c0m on 2006-06-28
[QUOTE=Staach]Not sure if this is the right place to ask this question but here goes. Is it possible to install mythtv on the server version (instead of the desktop)?  The reason I want this, is that I need a full webserver (+ mail) with typo3 installed on the same pc as mythtv. However I'm still quite new at linux so I´ll need the guidence from both [http://hyams.webhop.net/mythtv/myth_ubuntu.html](http://hyams.webhop.net/mythtv/myth_ubuntu.html) (and this thread) and other server-walk-thrus. 
Thx in advance
Staach[/QUOTE]

staach, youll want to do the regular install, the server install will not install X. however you can do the server install and follow the guides on how to install a 'light' X (using Xfce or fluxbox) on ubuntuwiki.

---

### Post by inf0c0m on 2006-06-28
[QUOTE=wardjame]I had ivtv working ok but it now hates me.  I was able to test using the cat /dev/video0 > /tmp/test.mpg on both cards without any problems but the command now fails with cat: /dev/video0: No such file or directory.  And modprobe ivtv returns FATAL: Module ivtv not found.  I re-ran the section on installing ivtv and am still getting the same errors.  Any suggestions?[/QUOTE]

i upgraded from breezy to dapper and i had the same thing, i seem to recall having to reinstall a newer version of the ivtv drivers a few times in order to get it working. i would try to back all of your steps up, and essentially start over from scratch. that way you know if youve missed anything.

---

### Post by Staach on 2006-06-29
[QUOTE=inf0c0m]staach, youll want to do the regular install, the server install will not install X. however you can do the server install and follow the guides on how to install a 'light' X (using Xfce or fluxbox) on ubuntuwiki.[/QUOTE]

Thx for the rep. I had sort of lost hope on this, but I will try a go on the server/light X :eek:

---

### Post by jlindley on 2006-06-29
[QUOTE=wardjame]I had ivtv working ok but it now hates me.  I was able to test using the cat /dev/video0 > /tmp/test.mpg on both cards without any problems but the command now fails with cat: /dev/video0: No such file or directory.  And modprobe ivtv returns FATAL: Module ivtv not found.  I re-ran the section on installing ivtv and am still getting the same errors.  Any suggestions?[/QUOTE]

I had the same problem, turned out that adding **ivtv** to the file **/etc/modules** is unneeded, and when I took it out everything worked fine. I think I had added some errant formatting to the file which was also a problem.

---

### Post by ceargle on 2006-07-03
Just finished installing MythTV 0.18 on Xubuntu 6.06 and was getting a DB Error whenever I ran 'mythfilldatabase'.  Upgrading to 0.19 with the repos Xinix supplied on page 2 of this thread fixed this problem.

---

### Post by talz13 on 2006-07-03
I'm right in the middle of setting up mythtv on my freshly installed 6.06 setup, and got to the point in the hyams guide for setting up mythweb (i'm installing 0.19 from source under section 9.8 of the guide).

The guide says:
> 
Mythweb needs some special attention for proper installation.  We do that here:

```
    apt-get install apache2 libapache2-mod-php4
    mkdir /usr/local/mythtv/share/mythtv/mythweb
[red]    mv /var/www/mythweb /var/www/mythweb-0.18[/red]
    ln -s /usr/local/mythtv/share/mythtv/mythweb /var/www/mythweb
    cd mythweb
    cp -r . /usr/local/mythtv/share/mythtv/mythweb
    chown www-data /var/www/mythweb/data
    cd ..
```


I can't seem to find any folders or files that fit this description (not a mythweb-0.18 or mythweb-0.19 or anything at all).  The only things under my /var/www/ are "apache2-default" and "phpmyadmin".  

Also, above this line where it says to install apache2 and libapache2-mod-php4, installing mod-php4 wants to remove mod-php5.  Is that what i want to do?  Because this guide said to install php5 instead.

Can anybody offer some advice to get my install progressing again?  Maybe it's something horribly simple that I just completely overlooked?

---

### Post by Nanodeath on 2006-07-05
I also have a confusing dilemma...okay, two, actually.

1) When I reboot my computer, the /dev/video and /dev/video0 files/whatevers go away, even when they were at least partially working before hand.

2) When following the ivtv instruction guides on this page and on Hyam's page, the IVTV module loads...but there's no useful information between the INIT ITVT and the ending brackets in dmesg.  Any ideas?  I have a WinTV PVR-350 and am giving the 0.4.6 ivtv drivers a shot.  TIA.

---

### Post by inf0c0m on 2006-07-05
[QUOTE=Nanodeath]I also have a confusing dilemma...okay, two, actually.

1) When I reboot my computer, the /dev/video and /dev/video0 files/whatevers go away, even when they were at least partially working before hand.

2) When following the ivtv instruction guides on this page and on Hyam's page, the IVTV module loads...but there's no useful information between the INIT ITVT and the ending brackets in dmesg.  Any ideas?  I have a WinTV PVR-350 and am giving the 0.4.6 ivtv drivers a shot.  TIA.[/QUOTE]


can you post the info between the ===init ivtv=== and the ==end init ivtv== one? this may be why you are not getting any /dev/videoX

---

### Post by inf0c0m on 2006-07-05
[QUOTE=talz13]I'm right in the middle of setting up mythtv on my freshly installed 6.06 setup, and got to the point in the hyams guide for setting up mythweb (i'm installing 0.19 from source under section 9.8 of the guide).

The guide says:


I can't seem to find any folders or files that fit this description (not a mythweb-0.18 or mythweb-0.19 or anything at all).  The only things under my /var/www/ are "apache2-default" and "phpmyadmin".  

Also, above this line where it says to install apache2 and libapache2-mod-php4, installing mod-php4 wants to remove mod-php5.  Is that what i want to do?  Because this guide said to install php5 instead.

Can anybody offer some advice to get my install progressing again?  Maybe it's something horribly simple that I just completely overlooked?[/QUOTE]

there is a problem with something that gets installed between php and mysql. what version of mysql are you running and what version of php are you running? and more importantly what version of mythweb are you running?

---

### Post by Nanodeath on 2006-07-05
[QUOTE=inf0c0m]can you post the info between the ===init ivtv=== and the ==end init ivtv== one? this may be why you are not getting any /dev/videoX[/QUOTE]

Well...just after I run through the install the first time (when /dev/video0 IS present) I get this:

[17184702.072000] ivtv:  ==================== START INIT IVTV ====================
[17184702.072000] ivtv:  version 0.4.4 (tagged release) loading
[17184702.072000] ivtv:  Linux version: 2.6.15-25-386 preempt 486 gcc-4.0
[17184702.072000] ivtv:  In case of problems please include the debug info between
[17184702.072000] ivtv:  the START INIT IVTV and END INIT IVTV lines, along with[17184702.072000] ivtv:  any module options, when mailing the ivtv-users mailinglist.
[17184702.072000] ivtv:  ====================  END INIT IVTV  ====================

From what I've seen, that's farrr too short...

---

### Post by inf0c0m on 2006-07-05
[QUOTE=Nanodeath]Well...just after I run through the install the first time (when /dev/video0 IS present) I get this:

[17184702.072000] ivtv:  ==================== START INIT IVTV ====================
[17184702.072000] ivtv:  version 0.4.4 (tagged release) loading
[17184702.072000] ivtv:  Linux version: 2.6.15-25-386 preempt 486 gcc-4.0
[17184702.072000] ivtv:  In case of problems please include the debug info between
[17184702.072000] ivtv:  the START INIT IVTV and END INIT IVTV lines, along with[17184702.072000] ivtv:  any module options, when mailing the ivtv-users mailinglist.
[17184702.072000] ivtv:  ====================  END INIT IVTV  ====================

From what I've seen, that's farrr too short...[/QUOTE]


yeah thats way too short. try running through the install again, just for ivtv

---

### Post by Nanodeath on 2006-07-06
[QUOTE=inf0c0m]yeah thats way too short. try running through the install again, just for ivtv[/QUOTE]

[17179592.232000] bttv0: using: Hauppauge (bt878) [card=10,autodetected]
[17179592.376000] tvaudio 0-005b: tda9850 found @ 0xb6 (bt878 #0 [sw])
[17179592.432000] tuner 0-0061: chip found @ 0xc2 (bt878 #0 [sw])
[17179593.084000] bt878: AUDIO driver version 0.0.0 loaded
[17179592.232000] bttv0: detected: Hauppauge WinTV [card=10], PCI subsystem ID is 0070:13eb
[17179592.232000] bttv0: using: Hauppauge (bt878) [card=10,autodetected]
[17179592.236000] bttv0: Hauppauge/Voodoo msp34xx: reset line init [5]
[17179592.328000] tveeprom 0-0050: Hauppauge model 62471, rev A   , serial# 1134796

Is this part important at all?

---

### Post by inf0c0m on 2006-07-07
> **Nanodeath said:**
> [17179592.232000] bttv0: using: Hauppauge (bt878) [card=10,autodetected]
[17179592.376000] tvaudio 0-005b: tda9850 found @ 0xb6 (bt878 #0 [sw])
[17179592.432000] tuner 0-0061: chip found @ 0xc2 (bt878 #0 [sw])
[17179593.084000] bt878: AUDIO driver version 0.0.0 loaded
[17179592.232000] bttv0: detected: Hauppauge WinTV [card=10], PCI subsystem ID is 0070:13eb
[17179592.232000] bttv0: using: Hauppauge (bt878) [card=10,autodetected]
[17179592.236000] bttv0: Hauppauge/Voodoo msp34xx: reset line init [5]
[17179592.328000] tveeprom 0-0050: Hauppauge model 62471, rev A   , serial# 1134796

Is this part important at all?

yeah, thats looking better, but your still not finding anything as far /dev/videoX goes?

---

### Post by msbose on 2006-07-07
Followed the guide and this post to install mythtv.  Opted to use mythtv .19 and ivtv-0.4.6 and "successfully" installed mythtv (no errors with mysql and phpadmin, etc).  However, I do not get any video.  I see that it records fine and plays back in the preview window but when I click on "Watch TV" the screen goes black and all I can hear is the audio with no video.  I have to cold start the machine since ESC does not throw me back to the main screen.  I am so close.. yet so far! ](*,)  Help!

---

### Post by msbose on 2006-07-07
My dmesg Output:

 ivtv:  ==================== START INIT IVTV ================== ==
[17179597.348000] ivtv:  version 0.4.6 (tagged release) loading
[17179597.348000] ivtv:  Linux version: 2.6.15-25-686 SMP preempt 686 gcc-4.0
[17179597.348000] ivtv:  In case of problems please include the debug info betwe en
[17179597.348000] ivtv:  the START INIT IVTV and END INIT IVTV lines, along with
[17179597.348000] ivtv:  any module options, when mailing the ivtv-users mailing list.
[17179597.364000] AC'97 0 analog subsections not ready
[17179597.432000] intel8x0_measure_ac97_clock: measured 55177 usecs
[17179597.432000] intel8x0: clocking to 48000
[17179597.432000] ACPI: PCI Interrupt 0000:02:01.0[A] -> GSI 18 (level, low) -> IRQ 177
[17179597.432000] PCI: Setting latency timer of device 0000:02:01.0 to 64
[17179597.532000] input: PC Speaker as /class/input/input2
[17179597.660000] e1000: 0000:02:01.0: e1000_probe: (PCI:33MHz:32-bit) 00:0e:a6: 69:aa:e5
[17179597.684000] Floppy drive(s): fd0 is 1.44M
[17179597.708000] parport: PnPBIOS parport detected.
[17179597.708000] parport0: PC-style at 0x378 (0x778), irq 7<6>FDC 0 is a post-1 991 82077
[17179597.708000] , dma 3 [PCSPP,TRISTATE,COMPAT,EPP,ECP,DMA]
[17179597.840000] input: ImExPS/2 Generic Explorer Mouse as /class/input/input3
[17179597.928000] e1000: eth0: e1000_probe: Intel(R) PRO/1000 Network Connection
[17179597.932000] ivtv0: Autodetected WinTV PVR 250 card (cx23416 based)
[17179597.932000] ACPI: PCI Interrupt 0000:03:0b.0[A] -> GSI 23 (level, low) -> IRQ 185
[17179597.980000] tveeprom: ivtv version
[17179597.980000] tveeprom: Hauppauge: model = 32062, rev = C185, serial# = 2881 901
[17179597.980000] tveeprom: tuner = TCL 2002N 6A (idx = 85, type = 50)
[17179597.980000] tveeprom: tuner fmt = NTSC(M) (eeprom = 0x08, v4l2 = 0x0000100 0)
[17179597.980000] tveeprom: audio processor = MSP3445 (type = c)
[17179597.980000] tveeprom: decoder processor = SAA7115 (type = 13)
[17179597.980000] ivtv0: i2c attach to card #0 ok [client=tveeprom, addr=50]
[17179598.000000] tuner (ivtv): chip found at addr 0xc2 i2c-bus ivtv i2c driver #0
[17179598.000000] ivtv0: i2c attach to card #0 ok [client=(tuner unset), addr=61 ]
[17179598.044000] ts: Compaq touchscreen protocol output
[17179598.196000] saa7115 0-0021: saa7115 found @ 0x42 (ivtv i2c driver #0)
[17179598.324000] ivtv0: i2c attach to card #0 ok [client=saa7115, addr=21]
[17179598.388000] msp3400 0-0040: chip=MSP3445G-B8 +nicam +simple +simpler +radi o mode=simpler
[17179598.388000] msp3400 0-0040: msp34xxg daemon started
[17179598.400000] ivtv0: i2c attach to card #0 ok [client=MSP3445G-B8, addr=40]
[17179599.188000] ivtv0: loaded v4l-cx2341x-enc.fw firmware (262144 bytes)
[17179599.404000] ivtv0: Encoder revision: 0x02050032
[17179599.404000] ivtv0: Allocate DMA encoder MPEG stream: 128 x 32768 buffers ( 4096KB total)
[17179599.404000] ivtv0: Allocate DMA encoder YUV stream: 194 x 10800 buffers (2 048KB total)
[17179599.404000] ivtv0: Allocate DMA encoder VBI stream: 120 x 17472 buffers (2 048KB total)
[17179599.404000] ivtv0: Allocate DMA encoder PCM audio stream: 455 x 4608 buffe rs (2048KB total)
[17179599.404000] tuner: type set to 50 (TCL 2002N) by ivtv i2c driver #0
[17179599.412000] e1000: eth0: e1000_watchdog_task: NIC Link is Up 100 Mbps Full  Duplex
[17179599.552000] ivtv0: Initialized WinTV PVR 250, card #0
[17179599.552000] ivtv:  ====================  END INIT IVTV  ==================

---

### Post by NT4usB on 2006-07-07
Might be the ivtv 0.4.6 drivers. Go back through this thread and there's stuff about staying with 0.4.4. (It solved my 'black screen' problem)

---

### Post by msbose on 2006-07-07
I'll reinstall the OS and give it another shot with ivtv 0.4.4 and let you know.

---

### Post by Moridin333 on 2006-07-07
I FINALLY FIGURED IT OUT!!!

I was having major problems getting channel info with mythupdatedb.  Turns out that the version of MySQL is not compatible with the version of MythTV on the repos.

To fix this problem do a complete removal of MySQL-server 5 and install MySql 4

I had to make a mythtv user in MySQL and run Mythtv-setup again.  But everything is working now.

---

### Post by msbose on 2006-07-08
Tried reinstalling Ubuntu and following the guide 3 times and get the same "black screen" each time.  :confused:

---

### Post by evilbunny on 2006-07-08
Hmmm I've skim read a lot of the posts and there seems to be a few bits of mis-info posted.

I added only the following lines to my /etc/apt/sources.list;

# MythTV 0.19
deb [http://knm.org/mythdebs/](http://knm.org/mythdebs/) binary/

#IVTV 0.4.6 pkgs
deb [http://www.hellion.org.uk/debian](http://www.hellion.org.uk/debian) sid main

Anything else seems dead or has a limited number of packages etc etc etc so is a waste of time even pulling the packages file.

To compile most kernel modules you just need the headers and not the actually source, and the simplest way to get everything needed is simply typing "sudo m-a prepare". This will grab the relivent headers for your kernel and compilers needed. Then you can run "sudo m-a auto-install ivtv0.4", it'll do it's thing and you should hopefully end up with the ivtv modules installed as a result.

I have 4 tuners, 3 pvr 150's with remotes/IR blasters, and 1 without (MCE). I'd suggest everyone only buy the cards with IR blasters as this gives you greatest flexibility since you can use the IR blasters for set top boxes. Some smart cookie has fixed the lirc source to work not only with the remotes but also with the IR blaster to change channels. Go to [http://www.blushingpenguin.com/mark/blog/?p=24](http://www.blushingpenguin.com/mark/blog/?p=24) and follow the step by step instructions to the letter and everything seems to work just peechy.

I previously posted some general tips already on this topic: [http://www.ubuntuforums.org/showpost.php?p=323935&postcount=30](http://www.ubuntuforums.org/showpost.php?p=323935&postcount=30)

---

### Post by jafenske on 2006-07-08
Have anyone had success upgrading to mythtv 0.19 with the packages found on 

[http://drop.thehunter.ws/index.php?path=mythtv-debian/](http://drop.thehunter.ws/index.php?path=mythtv-debian/)

I'm having a sql syntax error and my research suggests that I either have to upgrade to 0.19 or down grade to mysql4.0.  

Thanks

---

### Post by evilbunny on 2006-07-08
> **jafenske said:**
> I'm having a sql syntax error and my research suggests that I either have to upgrade to 0.19 or down grade to mysql4.0

I don't know of a good reason to use MySQL 5 with mythtv until they fix the problematic field... Although future proofing using back ticks should have been done in any case to prevent this exact problem from ever occuring...

---

### Post by NT4usB on 2006-07-08
After a month and a half of following howto's, uninstalling, reinstalling, googling, and generally beating my head against the desk, I have a fully functional MythTV 0.19-5. Using what I learned from all the howto's and guides, I started over and went after it step by step.
Basically, I uninstalled everything Myth. 
Then I got mysql working correctly. Then I got the cards working. Got the remote working. Then installed 19-5 from the knm repository.
To fix the libcdaudio1 deal that kept mythmusic from installing I used the ubuntu 5.10 repositoried to install libcdaudio0. Then switched back to the 6.06 repositories and completed the install.

---

### Post by msbose on 2006-07-09
This whole experience reinforces the fact that linux is NOT intended for the masses.  I have tried following instructions and trying various settings only to HAVE to give up!  I installed SageTV on windows and the whole process took 25-30 minutes!  I want MythTV to work so bad..., and spent all of the last three days tinkering with hope that it'll work.... and ended up disappointed.  Oh well!  This n00b (on linux) has given up!:-({|=

---

### Post by evilbunny on 2006-07-09
If linux was so hard, why didn't you just buy a tivo?

---

### Post by msbose on 2006-07-09
I do have a Tivo.

Anyway, I finally got MythTV working and am not sure what I did different to be quite honest.  This is what I remember:

- Used Automatrix for installing NVIDIA drivers
- IVTV-0.4.6 was downloaded from the link above
- Installed MythTV 0.19-5 (also from the link a few posts back)

---

### Post by evilbunny on 2006-07-09
> **msbose said:**
> Anyway, I finally got MythTV working and am not sure what I did different to be quite honest.

Did you use the same package repositories in previous attempts?

Ummm?

---

### Post by NT4usB on 2006-07-09
I found 0.18 didn't work for me with the latest mysql (5.).

The repositories at:
```
deb http://home.eng.iastate.edu/~superm1 dapper main
deb-src http://home.eng.iastate.edu/~superm1 dapper main
```
have 0.19 but only the basic install. No themes or plugins.

These repositories:
```
deb http://knm.org/mythdebs/ binary/
deb-src http://knm.org/mythdebs/ source/
```
have 0.19-5 complete. Only issue is with mythmusic but installing libcdaudio0 from the 5.10 repo's solves that.

Like I said in a prior post, get the other stuff (mysql, cards, etc.) working perfectly before installing mythtv and it works great.

---

### Post by anguyen on 2006-07-11
I just followed the steps outlined in this thread.  First, I'd like to say thank you.  I would have had a much harder time getting everything working without this thread.

To contribute back, here are some problems I ran into and what I did to get around them.

* Instead of installing mysql-server, install mysql-server-4.1.
```

sudo apt-get install build-essential dialog apache2 [COLOR="Red"]mysql-server-4.1[/COLOR] phpmyadmin gcc-3.4 libapache2-mod-php5

```
mysql-server will install the latest version, which is mysql-server-5.0 as of this post.

* Before installing mythweb, install the php5 metapackage, otherwise, mythweb will try to install the php4 metapackage.
```

apt-get install [COLOR="Red"]php5[/COLOR] mythweb mythtv-doc

```

* Make sure php is enabled for apache2 (it was only enabled for cgi in my case). Make sure the following lines appear in /etc/php5/apache2/php.ini
```

extension=mysql.so
extension=mysqli.so

```

* Be sure your host file contains all the names for your local host. When apache starts, it tries to figure out the fully qualified name for the host (to assign to the default virtual host?).  My apache gave me a warning about not being able to figure out the name of the localhost when I would start/restart it.  This caused problems when trying to accessing the web server from a web browser on a different machine.  I had no problems using [http://localhost](http://localhost) from the same machine, but could not get things to work when using a browser on another machine with [http://myth.mydomain.com](http://myth.mydomain.com).  Check that /etc/hosts contains the fully qualified name of your host:
```

127.0.1.1       myth.mydomain.com myth

```

Now that I have my system setup with my PVR-150, I am working on adding all the QAM256 channels from my AverMeida A180.

Andy

---

### Post by ianupright on 2006-07-13
Ok, apparently I'm an idiot when it comes to ubuntu 6.06.  I tried digging around the wiki, but I didn't find what I wanted.  What SVN repository are you downloading Myth 0.19 from?  Do you have a URL or a wiki page that describes this?  Is this a myth SVN repository or a Dapper SVN repository?

Thanks

---

### Post by Dave M G on 2006-07-13
I have successfully installed and run the IVTV drivers with Ubuntu Dapper through many kernel upgrades. Since about kernel 2.6.15-20-686 or so.

I have a PVR-150.

I installed IVTV using the instructions here:
[http://s91928265.onlinehome.us/hfamily/mythtv/myth_ubuntu.html]("http://s91928265.onlinehome.us/hfamily/mythtv/myth_ubuntu.html")

With the adjustments for Dapper as described at the beginning of this thread here:
[http://www.ubuntuforums.org/showthread.php?t=186747]("http://www.ubuntuforums.org/showthread.php?t=186747")

But with this last kernel upgrade, 2.6.15-26-686, the install process no longer works.

I get to almost the very end of the IVTV install instructions, and then I hit this error:

```
dave@homebase:/usr/src/ivtv-0.4.6/utils$ sudo modprobe ivtv
FATAL: Error inserting ivtv (/lib/modules/2.6.15-26-686/ivtv/ivtv.ko): Invalid module format
```

First, why is this process not working anymore?

Second, is there no hope of getting IVTV to be included in a repository? Going through this long list of commands every time there's a kernel upgrade is insane.

---

### Post by bicchi on 2006-07-13
> **Dave M G said:**
> 
Second, is there no hope of getting IVTV to be included in a repository? Going through this long list of commands every time there's a kernel upgrade is insane.

I have had the same issue since I got this card long time ago and with every kernel upgrade I have to recompile the drivers. I do believe that the drivers are been put into the Linux kernel. Not sure if the modules will end up on 2.6.17 or 2.6.18 all depends of how good the code is. I am not sure how the firmware is going to work, probably we will still have to download the firmware files and copy those directly to the appropiate directory. It would be nice if ubuntu puts them on deb package that also includes the utilities for controlling the card.
Look at this two threads for more info:
[URL="http://www.gossamer-threads.com/lists/ivtv/devel/30697"]
http://www.gossamer-threads.com/lists/ivtv/devel/30697[/URL]

[http://www.kernel.org/git/?p=linux%2Fkernel%2Fgit%2Ftorvalds%2Flinux-2.6.git&a=search&h=HEAD&s=ivtv]("http://www.kernel.org/git/?p=linux%2Fkernel%2Fgit%2Ftorvalds%2Flinux-2.6.git&a=search&h=HEAD&s=ivtv")

---

### Post by xeta on 2006-07-13
Well, I've basically given up on my pvr350. The guide was great but, I cant get the firmware to work with my card. Unfourtunatley I was talked into the 350 by a hauppauge rep that said it was "better". Seeing all the 150, and 250's that work...(and not really seeing any 350's work) I guess I got shafted. Ah well. Thanks for the good writeup. At least some people have it up and running.

---

### Post by NT4usB on 2006-07-13
> **Dave M G said:**
> I have successfully installed and run the IVTV drivers with Ubuntu Dapper through many kernel upgrades. Since about kernel 2.6.15-20-686 or so.

I have a PVR-150.

I installed IVTV using the instructions here:
[http://s91928265.onlinehome.us/hfamily/mythtv/myth_ubuntu.html]("http://s91928265.onlinehome.us/hfamily/mythtv/myth_ubuntu.html")

With the adjustments for Dapper as described at the beginning of this thread here:
[http://www.ubuntuforums.org/showthread.php?t=186747]("http://www.ubuntuforums.org/showthread.php?t=186747")

But with this last kernel upgrade, 2.6.15-26-686, the install process no longer works.

I get to almost the very end of the IVTV install instructions, and then I hit this error:

```
dave@homebase:/usr/src/ivtv-0.4.6/utils$ sudo modprobe ivtv
FATAL: Error inserting ivtv (/lib/modules/2.6.15-26-686/ivtv/ivtv.ko): Invalid module format
```

First, why is this process not working anymore?

Second, is there no hope of getting IVTV to be included in a repository? Going through this long list of commands every time there's a kernel upgrade is insane.

[fwiw] (iirc) after I updated the kernel (and ivtv and lirc broke,) I figured everything needed to build ivtv and lirc should still be on the box.
So I only d/l'd the Linux-headers (don't even know if this was necessary.)
cd'd to ivtv, make, make install. 
cd'd to the lirc dir, make, make install and everything was working again.
Mind you, I have no idea what I'm doing in Linux... but this got mythtv going again.
ymmv.

---

### Post by sebz2005 on 2006-07-14
Really quickly, can some one tell me what to do here. I'm trying to do

apt-get build-dep mythtv

but it's telling me to get the liblame-dev package, but it's been replaced with liblame0.

What do I do?!?

---

### Post by pbmax on 2006-07-15
> **TomSelleck said:**
> I fixed it.  The clue was in the log above.  It successfully loaded v4l-cx2341x-enc.fw, but not v4l-cx2341x-dec.fw.  I looked in /lib/firmware and saw that v4l-cx2341x-dec.fw was a symbolic link.  I removed the link and copied the real file there instead.  It worked.

I haven't figured out how to fix this.  I have the same problem with installing the firmware
```
[17184137.680000] cx25840 0-0044: unable to open firmware v4l-cx25840.fw
[17184137.740000] ivtv0: i2c attach to card #0 ok [client=cx25840, addr=44]
[17184137.768000] wm8775 0-001b: chip found @ 0x36 (ivtv i2c driver #0)
[17184137.776000] ivtv0: i2c attach to card #0 ok [client=wm8775, addr=1b]
[17184138.424000] ivtv0: unable to open firmware v4l-cx2341x-enc.fw
[17184138.424000] ivtv0: did you put the firmware in the hotplug firmware directory?
[17184138.424000] ivtv0 warning: failed loading encoder firmware
[17184138.424000] ivtv0 warning: Error loading firmware -3!
[17184138.424000] ivtv0: Error -3 initializing firmware.
[17184138.428000] ivtv0: Error -12 on initialization
[17184138.428000] ivtv: probe of 0000:02:01.0 failed with error -12
[17184138.428000] ivtv:  ====================  END INIT IVTV  ====================
```

any suggestions?
thanks
pb

---

### Post by althepcman on 2006-07-15
> **pbmax said:**
> I haven't figured out how to fix this.  I have the same problem with installing the firmware
```
[17184137.680000] cx25840 0-0044: unable to open firmware v4l-cx25840.fw
[17184137.740000] ivtv0: i2c attach to card #0 ok [client=cx25840, addr=44]
[17184137.768000] wm8775 0-001b: chip found @ 0x36 (ivtv i2c driver #0)
[17184137.776000] ivtv0: i2c attach to card #0 ok [client=wm8775, addr=1b]
[17184138.424000] ivtv0: unable to open firmware v4l-cx2341x-enc.fw
[17184138.424000] ivtv0: did you put the firmware in the hotplug firmware directory?
[17184138.424000] ivtv0 warning: failed loading encoder firmware
[17184138.424000] ivtv0 warning: Error loading firmware -3!
[17184138.424000] ivtv0: Error -3 initializing firmware.
[17184138.428000] ivtv0: Error -12 on initialization
[17184138.428000] ivtv: probe of 0000:02:01.0 failed with error -12
[17184138.428000] ivtv:  ====================  END INIT IVTV  ====================
```

any suggestions?
thanks
pb

Check that you have the ivtv files in the correct directory by doing the following:
ls -ltra /lib/firmware/

if you see the following files:
-rw-r--r--  1 root root 262144 2006-07-03 22:36 ivtv-fw-enc.bin
-rw-r--r--  1 root root 262144 2006-07-03 22:36 ivtv-fw-dec.bin
-r--r--r--  1 root root  14264 2006-07-03 22:37 v4l-cx25840.fw
-r--r--r--  1 root root 376836 2006-07-03 22:37 v4l-cx2341x-enc.fw
-rw-r--r--  1 root root 155648 2006-07-03 22:38 v4l-cx2341x-init.mpg
v4l-cx2341x-dec.fw -> lib/firmware/ivtv-fw-dec.bin

Then it should work.

---

### Post by idcard_1 on 2006-07-16
> **Sureshot324 said:**
> On my amd64 install of dapper, the firmware had to go to /lib/firmware/2.6.15-23-amd64-generic

Thanks!  Yeah its seems for an amd64 system the firmware files have to go inside

/lib/firmware/`uname -r`/

I didn't stumble on this site until about my 10th install, but finally got the drivers to load correctly.  Now I just need to get the lirc installed!

---

### Post by evilbunny on 2006-07-17
> **Dave M G said:**
> 
But with this last kernel upgrade, 2.6.15-26-686, the install process no longer works.

I get to almost the very end of the IVTV install instructions, and then I hit this error:

```
dave@homebase:/usr/src/ivtv-0.4.6/utils$ sudo modprobe ivtv
FATAL: Error inserting ivtv (/lib/modules/2.6.15-26-686/ivtv/ivtv.ko): Invalid module format
```

First, why is this process not working anymore?

Quick solution is to delete the directory, untar it and rebuild it and it'll work, for some reason when you run the install later it tries to build it for the old kernel still...

---

### Post by evilbunny on 2006-07-17
> **idcard_1 said:**
> Thanks!  Yeah its seems for an amd64 system the firmware files have to go inside

/lib/firmware/`uname -r`/

No this is for all current versions of ubuntu because of hal and other updates/upgrades...

---

### Post by noday42 on 2006-07-17
> **althepcman said:**
> Check that you have the ivtv files in the correct directory by doing the following:
ls -ltra /lib/firmware/

if you see the following files:
-rw-r--r--  1 root root 262144 2006-07-03 22:36 ivtv-fw-enc.bin
-rw-r--r--  1 root root 262144 2006-07-03 22:36 ivtv-fw-dec.bin
-r--r--r--  1 root root  14264 2006-07-03 22:37 v4l-cx25840.fw
-r--r--r--  1 root root 376836 2006-07-03 22:37 v4l-cx2341x-enc.fw
-rw-r--r--  1 root root 155648 2006-07-03 22:38 v4l-cx2341x-init.mpg
v4l-cx2341x-dec.fw -> lib/firmware/ivtv-fw-dec.bin

Then it should work.

mine has all of those, and still doesn't work....though, my v4l-cx2341x-dec.fw part is showing up in light blue.....I dont know if that means anything.

I'm really stuck and have no clue where to go from here, because no matter what, the firmware for v4l-cx2341x-dec.fw cannot be opened

---

### Post by qrazi on 2006-07-17
I have also upgraded to 6.06, and then mythtv to 0.19. Ever since, the interface of mythtv doesnt show the plugins like videos, music etc anymore. In mythweb it does include my music and videocollection however.

Anybody an idea why this is, or how to fix it?

---

### Post by thefool808 on 2006-07-18
I'm having the same problem.  From a previous post in this thread, it seems that the symlink may be causing the problem.  Can you try copying the file lib/firmware/ivtv-fw-dec.bin to v4l-cx2341x-dec.fw?  I'm at work and can't attempt this solution right now, but will try it when I get home.

> **noday42 said:**
> mine has all of those, and still doesn't work....though, my v4l-cx2341x-dec.fw part is showing up in light blue.....I dont know if that means anything.

I'm really stuck and have no clue where to go from here, because no matter what, the firmware for v4l-cx2341x-dec.fw cannot be opened

---

### Post by pbmax on 2006-07-19
> **althepcman said:**
> Opps forgot to tell eveyone after installign all those things in the how to you should restart apache by doing the following:
```

sudo /etc/init.d/apache2 restart

```

I will add this to the how to. :)
I had the same problem as althepcman, but the restart didn't fix it.  Anyone know what would?
thanks
pb

---

### Post by althepcman on 2006-07-19
> **pbmax said:**
> I had the same problem as althepcman, but the restart didn't fix it.  Anyone know what would?
thanks
pb

System restart. :)
Try it and let me know.

---

### Post by thefool808 on 2006-07-19
Just this morning I succesfully got X running on the pvr350 tv out.  I had to use the ivtvdev driver from [http://www.hellion.org.uk/ivtv/index.html]("http://www.hellion.org.uk/ivtv/index.html") and the xorg.conf changes at [http://www.mythtv.org/wiki/index.php/XV_on_PVR-350]("http://www.mythtv.org/wiki/index.php/XV_on_PVR-350").

I don't like using a precompiled kernel module though, so if someone could help me out with directions on compiling my own from source that would be great.  I was following the directions from [http://ivtv.writeme.ch/tiki-index.php?page=XDriverHowTo]("http://ivtv.writeme.ch/tiki-index.php?page=XDriverHowTo") but I don't know my "/path/to/X/sources" in Dapper.  Any help would be appreciated.

---

### Post by Dave M G on 2006-07-19
There's a point in the instructions where it says to edit /usr/src/linux/Makefile, and make EXTRAVERSION match the output of 'uname -r'.

My uname -r says
2.6.15-26-686

So, my EXTRAVERSION should be:
EXTRAVERSION = -26-686

But I can't help but notice that, before I do any edits, the EXTRAVERSION in my Makefile is a completely different format:
EXTRAVERSION = .7-ubuntu1

Although I follow all the rest of the instructions to the letter, IVTV is still not working. It was working find in previous builds, and this is the first time I've seen .7-ubuntu1.

Is there some conflict because of the differing formats of EXTRAVERSION?

---

### Post by Titus A Duxass on 2006-07-19
I noticed that, I over wrote it with my extra version.

IVTV problems - try switching off and disconnect the power for about 30 seconds then restart.

---

### Post by Dave M G on 2006-07-19
Another thing...

this time while running through the IVTV install process, when I was making the IVTV drivers, I got this output:

make[2]: Entering directory `/usr/src/linux-source-2.6.15'

  WARNING: Symbol version dump /usr/src/linux-source-2.6.15/Module.symvers
           is missing; modules will have no dependencies and modversions.

  Building modules, stage 2.
  MODPOST
*** Warning: "i2c_master_send" [/usr/src/ivtv-0.4.5/driver/tveeprom.ko] undefined!
*** Warning: "i2c_attach_client" [/usr/src/ivtv-0.4.5/driver/tveeprom.ko] undefined!
*** Warning: "i2c_detach_client" [/usr/src/ivtv-0.4.5/driver/tveeprom.ko] undefined!
*** Warning: "i2c_del_driver" [/usr/src/ivtv-0.4.5/driver/tveeprom.ko] undefined!
*** Warning: "i2c_add_driver" [/usr/src/ivtv-0.4.5/driver/tveeprom.ko] undefined!
*** Warning: "i2c_master_recv" [/usr/src/ivtv-0.4.5/driver/tveeprom.ko] undefined!
*** Warning: "i2c_probe" [/usr/src/ivtv-0.4.5/driver/tveeprom.ko] undefined!
*** Warning: "i2c_del_driver" [/usr/src/ivtv-0.4.5/driver/tuner.ko] undefined!
*** Warning: "i2c_add_driver" [/usr/src/ivtv-0.4.5/driver/tuner.ko] undefined!
*** Warning: "i2c_detach_client" [/usr/src/ivtv-0.4.5/driver/tuner.ko] undefined!

Any idea on why this is happening?

---

### Post by Titus A Duxass on 2006-07-19
Nope, no idea. But that looks like your problem area.  Did you follow the how-to step by step.

Did you cut and paste the commands or did you use tab to auto-complete them for you?

Edit at 17:38 CET

I have just completed this step with out any problems, you must be going wrong before the make and make install commands.

---

### Post by NT4usB on 2006-07-19
> **Dave M G said:**
> Another thing...

this time while running through the IVTV install process, when I was making the IVTV drivers, I got this output:

make[2]: Entering directory `/usr/src/linux-source-2.6.15'

  WARNING: Symbol version dump /usr/src/linux-source-2.6.15/Module.symvers
           is missing; modules will have no dependencies and modversions.

fwiw, I saw this every time I reinstalled (probably 6 complete reinstalls... doh!)
It didn't affect anything related to ivtv that I could see. 
Been running good for ~2 weeks now (finally!)
Can't help on the other errors...

---

### Post by pyroman on 2006-07-19
Hey all, I got mythtv and everything installed and working correctly, but my main goal was to be able to hook up my game console and play it. That worked too, sorta. There is a good amount of lag between when I do something with the controls, and I see some results on the screen. I've looked around on all diffrent forums, and I've gotten close to my goal. One thing is do need help with though is turning off the MPEG encoder. I read that if I was able to do this, the lag would go away. So I was wondering, does anyone knew how to turn that bad boy off?

O yeh, I should probably mention that I'm using a PVR-150-MCE.

---

### Post by jonah1980 on 2006-07-20
Hi could anyone please help me out on 64bit if possible, i've started a thread here: [http://www.ubuntuforums.org/showthread.php?p=1278633#post1278633](http://www.ubuntuforums.org/showthread.php?p=1278633#post1278633)

Also could anyone suggest if the Pinnacle PCTV Hybrid Pro PCI will work with Myth and also the remote control. I can't find anything about this tv card and linux so far... I hope it works, already got the hardware but gave up windows a few weeks ago. Brave steps but now i'm on a new dapper 64bit machine with a few bugs but pretty much everything is working sweet.

---

### Post by qrazi on 2006-07-20
> **qrazi said:**
> I have also upgraded to 6.06, and then mythtv to 0.19. Ever since, the interface of mythtv doesnt show the plugins like videos, music etc anymore. In mythweb it does include my music and videocollection however.

Anybody an idea why this is, or how to fix it?
Does anybody else have experience with this problem? I tried to reinstall version 0.19 several times, both from repositories as from source, but i dont get MythVideo/Music/DVD etc. working.

---

### Post by iglablues on 2006-07-20
Sorry.

---

### Post by bla2000 on 2006-07-21
I've had mythtv running for the past year on Hoary. If I decide to upgrade and install mythtv 0.19 with mysql5 will I be able to restore my existing myconverg database that is currently running on mysql4?  Or is my only option install dapper, mythtv and downgrade to mysql4 before restoring my existing database?

Thanks.

---

### Post by sebz2005 on 2006-07-21
I have a Tevion DVB-T 220 RF card and the latest kernel, 2.6.17.6, supports it. I installed it, but now I don't know what type of card I should select in the mythtv-setup. Or should I update to MythTV-0.19?

---

### Post by atrus123 on 2006-07-22
Just in case anyone is interested, [here is a walkthrough](http://www.animewine.com/index.php?entry=entry060720-151531) I wrote up for installing MythTV on Dapper using the ATI All-In-Wonder-Pro card.  

It is my first walkthrough.  Please note my sources at the bottom of the entry.  (This thread was one of my sources).

---

### Post by qrazi on 2006-07-23
> **qrazi said:**
> Does anybody else have experience with this problem? I tried to reinstall version 0.19 several times, both from repositories as from source, but i dont get MythVideo/Music/DVD etc. working.
I sort of fixed my problem with having apparantly no plugins. As it turned out, with my upgrade to 0.19 i didnt properly install the plugins.

When I upgraded I first tried to compile from source, but later used a repositorie.

Right now, I have added the following to my sources.list:

## MythTV 0.19
deb [http://knm.org/mythdebs/](http://knm.org/mythdebs/) binary/

Then I used synaptic to remove the installed myth 0.19 packages, and install the new 0.19.5 packages from this repositorie. Now i do have all the plugins. Also, it didnt seem to mess up my database. The only thing is, that my PVR 250 card seems to have lost its drivers, and MythMusic didnt want to install because of an dependancie problem.... Anyway, I can continue with messing with Mythtv....

---

### Post by chessforce on 2006-07-24
> **ThreeE said:**
> When I do mythfilldatabase I get a bunch of these:

```
DB Error (Inserting into dd_schedule):
Query was:
INSERT INTO dd_schedule (programid,stationid,scheduletime,duration,repeat,stereo,subtitled,hdtv,closecaptioned,tvrating,partnumber,parttotal,endtime) VALUES('SH6878270000','19283','2006-06-14T23:30:00','00:30:00',0,0,0,0,0,NULL,0,0,'2006-06-15T00:00:00');
Driver error was [2/1064]:
QMYSQL3: Unable to execute query
Database error was:
You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near 'repeat,stereo,subtitled,hdtv,closecaptioned,tvrating,partnumber,parttotal,endtim' at line 1

```

Any ideas?  I have to say -- this is much easier on Dapper than it was on Breezy.

> **JSVH said:**
> I am running into the same problem! 

Atleast I can get mythtv will start up, just no database . So no tv listings. let me know if you find out what the problem is.

Since "repeat" is a MySQL (version >=5.0) reserved keyword, as mentioned by others, you will have to replace "repeat" with some other word.  However, this cannot be done via the editing of a text/config file, but instead must be done by modifying /usr/lib/libmythtv-0.18.1.so.0 with a hex editor.  In order to do this, you can try these steps:

**PLEASE NOTE that this is a workaround and probably should not be considered a permanent fix (furthermore, it may not even work).  If I recall correctly, the conflict with the keyword has been resolved in MythTV 0.19**
```

1. Update apt's repository data: `sudo apt-get update`
2. Install and set-up MythTV: `sudo apt-get install mythtv`
3. Install KHexEdit: `sudo apt-get install khexedit`
4. Run KHexEdit in super-user mode: `sudo khexedit`
5. In KHexEdit, go to File->Open and select /usr/lib/libmythtv-0.18.1.so.0
6. Go to Edit->Replace and select "Regular Text" in both the "Format (find):" and "Format (replace):" drop-down menus.
7. Type "repeat" (without the quotation marks) in the "Find:" box.
8. Type something else that has the **same number of characters** as "repeat" (e.g. substituting the first letter of "repeat" with another letter should work) in the "Replace:" box.
9. Press "OK" and make sure that all instances of "repeat" are replaced with your choice that was made in step 8.
10. Do File->Save and then File->Quit.

```

---

### Post by NT4usB on 2006-07-24
> **qrazi said:**
> ... and MythMusic didnt want to install because of an dependancie problem.... Anyway, I can continue with messing with Mythtv....

installing libcdaudio0 from the 5.10 repo's solves that.

---

### Post by chadk on 2006-07-24
When I do 
sudo /etc/init.d/apache2 restart 
I get this:

```

 * Forcing reload of apache 2.0 web server... (98)Address already in use: make_sock: could not bind to address [::]:80
no listening sockets available, shutting down
Unable to open logs                                                                                                   [fail]
```

---

### Post by chadk on 2006-07-24
You wouldn't think MythTV would be this friggin difficult.

---

### Post by dodongo on 2006-07-25
"If I recall correctly, the conflict with the keyword has been resolved in MythTV 0.19"

This is true.  I had the same SQL syntax error as reported, and I can confirm that the 0.19 packages fix this issue.  

As pointed out above, the solution is to add the following to /etc/apt/sources.list:

> ## MythTV 0.19
deb [http://knm.org/mythdebs/](http://knm.org/mythdebs/) binary/

---

### Post by audun1 on 2006-07-26
Hello. I have a big problem with the ivtv thing...
i have this long thing and everything is in place :S

addr=61]
[ 6456.642264] cx25840 5-0044: ivtv driver
[ 6456.642270] cx25840 5-0044: cx25843-23 found @ 0x88 (ivtv i2c driver #0)
[ 6456.677480] cx25840 5-0044: unable to open firmware v4l-cx25840.fw
[ 6456.737167] ivtv0: i2c attach to card #0 ok [client=cx25840, addr=44]
[ 6456.752481] wm8775 5-001b: chip found @ 0x36 (ivtv i2c driver #0)
[ 6456.760046] ivtv0: i2c attach to card #0 ok [client=wm8775, addr=1b]
[ 6456.773197] tda9887 5-0043: (ivtv) chip found @ 0x86 (ivtv i2c driver #0)
[ 6456.773203] ivtv0: i2c attach to card #0 ok [client=tda9887, addr=43]
[ 6456.791994] ivtv0: Detected a TEA5767 radio tuner. Enabling radio support.
[ 6457.405163] ivtv0: unable to open firmware v4l-cx2341x-enc.fw
[ 6457.405295] ivtv0: did you put the firmware in the hotplug firmware directory?
[ 6457.405414] ivtv0 warning: failed loading encoder firmware
[ 6457.405508] ivtv0 warning: Error loading firmware -3!
[ 6457.405596] ivtv0: Error -3 initializing firmware.
[ 6457.400074] ivtv0: Error -12 on initialization
[ 6457.400083] ivtv: probe of 0000:06:08.0 failed with error -12
[ 6457.400116] ivtv0: Autodetected WinTV PVR 150 card (cx23416 based)
[ 6457.400204] ACPI: PCI Interrupt 0000:06:09.0[A] -> Link [APC2] -> GSI 17 (level, low) -> IRQ 82
[ 6457.400213] ivtv0: Unreasonably low latency timer, setting to 64 (was 32)
[ 6457.438917] tveeprom: Second (radio) tuner idx 101
[ 6457.438921] tveeprom: ivtv version
[ 6457.438924] tveeprom: Hauppauge: model = 23559, rev = D591, serial# = 2999632
[ 6457.438927] tveeprom: tuner = Philips FQ1216AME MK4 (idx = 91, type = 56)
[ 6457.438931] tveeprom: tuner fmt = PAL(B/G) PAL(I) SECAM(L/L') PAL(D/K) (eeprom = 0x74, v4l2 = 0x00400e17)
[ 6457.438933] tveeprom: audio processor = CX25843 (type = 25)
[ 6457.438935] tveeprom: decoder processor = CX25843 (type = 1e)
[ 6457.438939] ivtv0: i2c attach to card #0 ok [client=tveeprom, addr=50]
[ 6457.449315] tuner (ivtv): chip found at addr 0xc2 i2c-bus ivtv i2c driver #0
[ 6457.449320] ivtv0: i2c attach to card #0 ok [client=(tuner unset), addr=61]
[ 6457.594970] cx25840 5-0044: ivtv driver
[ 6457.594974] cx25840 5-0044: cx25843-23 found @ 0x88 (ivtv i2c driver #0)
[ 6457.612756] cx25840 5-0044: unable to open firmware v4l-cx25840.fw
[ 6457.672360] ivtv0: i2c attach to card #0 ok [client=cx25840, addr=44]
[ 6457.672608] wm8775 5-001b: chip found @ 0x36 (ivtv i2c driver #0)
[ 6457.680213] ivtv0: i2c attach to card #0 ok [client=wm8775, addr=1b]
[ 6457.690592] tda9887 5-0043: (ivtv) chip found @ 0x86 (ivtv i2c driver #0)
[ 6457.690596] ivtv0: i2c attach to card #0 ok [client=tda9887, addr=43]
[ 6457.702752] ivtv0: This is the second unit of a PVR500
[ 6457.702756] ivtv0: Correcting tveeprom data: no radio present on second unit
[ 6458.342591] ivtv0: unable to open firmware v4l-cx2341x-enc.fw
[ 6458.342597] ivtv0: did you put the firmware in the hotplug firmware directory?
[ 6458.342600] ivtv0 warning: failed loading encoder firmware
[ 6458.342602] ivtv0 warning: Error loading firmware -3!
[ 6458.342605] ivtv0: Error -3 initializing firmware.
[ 6458.344003] ivtv0: Error -12 on initialization
[ 6458.344087] ivtv: probe of 0000:06:09.0 failed with error -12
[ 6458.344193] ivtv:  ====================  END INIT IVTV  ====================

I am trying linux since i have used Microsoft Media Center and i must say that Microsoft have a DIG win on TV ond stuff :-( 

Here are my hotplug folder
root@AMDX2:/usr/lib/hotplug/firmware# ls
ivtv-fw-dec.bin  ivtv-fw-enc.bin  v4l-cx2341x-dec.fw  v4l-cx2341x-enc.fw  v4l-cx2341x-init.mpg  v4l-cx25840.fw

Have i missed something?

HELP :D

Thanks

---

### Post by manoova on 2006-07-29
The info below assumes you are using Ubuntu 6.06. I think the path you are using /lib/hotplug/firmware (whatever it is) is relevant to Ubuntu 5.10.

I hope this helps.

Download and install the latest IVTV drivers. At the time of writing this was 0.4.6. See [http://www.ivtv.org/](http://www.ivtv.org/)
cd /usr/src
 wget [http://dl.ivtvdriver.org/ivtv/archive/0.4.x/ivtv-0.4.6.tar.gz](http://dl.ivtvdriver.org/ivtv/archive/0.4.x/ivtv-0.4.6.tar.gz)
tar xvfz ivtv-0.4.6.tar.gz
cd ivtv-0.4.6
make
make install

Check that you get the following:
ls /lib/modules/`uname -r`/ivtv
cx25840.ko  ivtv-fb.ko  ivtv.ko  saa7127.ko  tda9887.ko  tuner.ko  tveeprom.ko

 cd utils/
wget [ftp://ftp.shspvr.com/download/wintv-pvr_150-500/inf/pvr_2.0.24.23035.zip](ftp://ftp.shspvr.com/download/wintv-pvr_150-500/inf/pvr_2.0.24.23035.zip)
 wget [ftp://ftp.shspvr.com/download/wintv-pvr_250-350/inf/pvr_1.18.21.22254_inf.zip](ftp://ftp.shspvr.com/download/wintv-pvr_250-350/inf/pvr_1.18.21.22254_inf.zip)
unzip pvr_2.0.24.23035.zip
Archive:  pvr_2.0.24.23035.zip
replace ReleaseNotes.txt? [y]es, [n]o, [A]ll, [N]one, [r]ename: A
  inflating: ReleaseNotes.txt
  inflating: hcwECP.ax
  inflating: HcwFalcn.rom
  inflating: HcwMakoA.ROM
  inflating: HCWPP2.inf
  inflating: hcwPP2.sys
  inflating: hcwPrxA2.ax
  inflating: hcwutl32.dll
  inflating: hcwxds.dll
  inflating: hcwCCnv2.ax
./ivtvfwextract.pl pvr_1.18.21.22254_inf.zip
cp HcwMakoA.ROM /lib/firmware/v4l-cx25840.fw
cp HcwFalcn.rom /lib/firmware/v4l-cx2341x-enc.fw
mv /lib/modules/ivtv-fw-dec.bin /lib/firmware/
mv /lib/modules/ivtv-fw-enc.bin /lib/firmware/
cp ../v4l-cx2341x-init.mpg /lib/firmware/
ln -s /lib/firmware/ivtv-fw-dec.bin /lib/firmware/v4l-cx2341x-dec.fw
ls -ltra /lib/firmware/

Now lets tell Ubuntu that we have ivtv modules. Edit /etc/modules, and just stick "ivtv" at the end of the file. 
nano -w /etc/modules

Also edit /etc/modprobe.d/aliases, 
nano -w /etc/modprobe.d/aliases
and put the following line in where it fits:
alias char-major-81-0 ivtv

depmod
modprobe ivtv
dmesg

If you get out detailing IVTV and your card without any errors then it has worked. If not look over the steps above carefully.

Testing IVTV 
cat /dev/video0 > /tmp/test.mpg
Ctrl-C to stop recording. Open mplayer: Applications --> Sound and Video --> Mplayer Movie Player. Right click on the window --> Open File --> /tmp/test.mpg. If you see grey snow you're in business.

---

### Post by hereitcomes on 2006-07-29
im using a hauppauge wintv nova-t pci card which works fine in kaffeine so i know the drivers are ok, i set up mythtv eventually after errors about connecting to the backend, now when i hit "Watch TV" the screen goes blank and sends me back to the ubuntu login screen
any ideas?
thank you
update: I discovered that it is recording the channels fine, just not letting me see them live! here is the output of mythfrontend
2006-07-30 03:59:43.617 New DB connection, total: 1
2006-07-30 03:59:43.638 New DB connection, total: 2
2006-07-30 03:59:43.645 DVB#0 DVB SI Table Parser Started
2006-07-30 03:59:43.714 DVB#0 Using DVB card 0, with frontend Conexant CX22702 DVB-T.
2006-07-30 03:59:43.717 New DB connection, total: 3
2006-07-30 03:59:44.679 DVB#0 DVB signal 2d | snr ffff | ber    0 | unc    0
2006-07-30 03:59:44.679 DVB#0 Status: LOCK.
2006-07-30 03:59:44.679 DVB#0 Multiplex Locked
2006-07-30 03:59:45.864 DVB#0 Successfully tuned to channel 1.
2006-07-30 03:59:45.874 New DB scheduler connection
2006-07-30 03:59:45.884 mythbackend version: 0.18.1.20050510-1 [www.mythtv.org](www.mythtv.org)
2006-07-30 03:59:45.885 Enabled verbose msgs : important general
2006-07-30 03:59:47.884 Reschedule requested for id -1.
2006-07-30 03:59:48.118 Scheduled 0 items in 0.2 = 0.23 match + 0.01 place
2006-07-30 03:59:48.120 Seem to be woken up by USER
2006-07-30 04:00:03.813 MainServer::HandleAnnounce Playback
2006-07-30 04:00:03.813 adding: scott-desktop as a client (events: 0)
2006-07-30 04:00:03.849 MainServer::HandleAnnounce Playback
2006-07-30 04:00:03.850 adding: scott-desktop as a client (events: 1)
2006-07-30 04:00:03.865 MainServer::HandleAnnounce Playback
2006-07-30 04:00:03.865 adding: scott-desktop as a client (events: 0)
2006-07-30 04:00:03.897 MainServer::HandleAnnounce Playback
2006-07-30 04:00:03.897 adding: scott-desktop as a client (events: 0)
2006-07-30 04:00:03.913 adding: scott-desktop as a remote ringbuffer
2006-07-30 04:00:03.937 Changing from None to WatchingLiveTV
2006-07-30 04:00:03.948 DVB#0 Recorder: Card opened successfully (using PS mode).
2006-07-30 04:00:03.960 DVB#0 Data read from DMX - This is for debugging with transform.c

---

### Post by manoova on 2006-08-01
I've documented my experience of installing MythTV 0.19 on Ubuntu 6.06. The document is attached and available for download. It's a zipped PDF.

I'd be extremely grateful if people could review it and comment/correct. It focuses on my hardware setup and therefore misses elements such as ATi graphics configs and TV capture cards other than the Hauppauge range.

I look forward to your feedback.

---

### Post by Jordy on 2006-08-01
Hey manoover

Running through your instructions and I'm having trouble getting the following line to work:
apt-*get install linux-*source-*<kver> linux-*headers-*`uname *r`

 I get this error:

paul@paul-desktop:~$ apt-*get install linux*-source-*2.6.15-26-386 linux-*headers*-`uname *r`
bash: uname *r: command not found
bash: apt*-get install linux-*source*-2.6.15-26-386 linux*-headers*: command not found


Also tried it with "sudo" but no luck

Any Ideas?

thanks

Paul

---

### Post by manoova on 2006-08-01
> **Jordy said:**
> Hey manoover

Running through your instructions and I'm having trouble getting the following line to work:
apt-*get install linux-*source-*<kver> linux-*headers-*`uname *r`

 I get this error:

paul@paul-desktop:~$ apt-*get install linux*-source-*2.6.15-26-386 linux-*headers*-`uname *r`
bash: uname *r: command not found
bash: apt*-get install linux-*source*-2.6.15-26-386 linux*-headers*: command not found


Also tried it with "sudo" but no luck

Any Ideas?

thanks

Paul


Hi Paul

Your command should like like this:

apt-get install linux-source-<kver> linux-headers-`uname -r`

where <kver> is something like 2.6.15

i.e.

apt-get install linux-source-2.6.15 linux-headers-`uname -r`

---

### Post by pipedream on 2006-08-01
Manoova,

Nice job putting your pdf together and up to date.  I struggled yesterday going back and forth between the guides on the first page.

I'm hoping that your IVTV section will help me since that is where I left off last night with all kinds of errors.

Thanks for making this!

---

### Post by pipedream on 2006-08-01
Could anyone please tell me if I need to do anything different while compiling and installing the ivtv driver and related firmware for my set up of  (2) PVR-150’s ?

Do I need to change anything in /etc/modprobe.d/aliases, or alias char-major-81-0
Ivtv to account for the two PVR-150’s ?

Linux Newbie here, so sorry if it is easy and straight forward.

Thanks for any help!

---

### Post by NT4usB on 2006-08-01
> **pipedream said:**
> Could anyone please tell me if I need to do anything different while compiling and installing the ivtv driver and related firmware for my set up of  (2) PVR-150’s ?

Do I need to change anything in /etc/modprobe.d/aliases, or alias char-major-81-0
Ivtv to account for the two PVR-150’s ?

Linux Newbie here, so sorry if it is easy and straight forward.

Thanks for any help!

I'm not in front of my box atm but iirc, you add two entries:
...81-0 ivtv and ...81-1 ivtv

read this howto in the ivtv section look for the aliases part.(hint, the pvr500 has 2 tuners)

[http://hyams.webhop.net/mythtv/myth_ubuntu.html](http://hyams.webhop.net/mythtv/myth_ubuntu.html)

---

### Post by pipedream on 2006-08-01
Any suggestions on what I did wrong?  Here is my ivtv dmesg

[17179595.408000] cx25840 0-0044: unable to open firmware v4l-cx25840.fw
[17179595.480000] ivtv0: i2c attach to card #0 ok [client=cx25840, addr=44]
[17179595.508000] wm8775 0-001b: chip found @ 0x36 (ivtv i2c driver #0)
[17179595.516000] ivtv0: i2c attach to card #0 ok [client=wm8775, addr=1b]
[17179595.544000] tda9887 0-0043: (ivtv) chip found @ 0x86 (ivtv i2c driver #0)
[17179595.544000] ivtv0: i2c attach to card #0 ok [client=tda9887, addr=43]
[17179596.164000] ivtv0: unable to open firmware v4l-cx2341x-enc.fw
[17179596.164000] ivtv0: did you put the firmware in the hotplug firmware direct ory?
[17179596.164000] ivtv0 warning: failed loading encoder firmware
[17179596.164000] ivtv0 warning: Error loading firmware -3!
[17179596.164000] ivtv0: Error -3 initializing firmware.
[17179596.164000] ivtv0: Error -12 on initialization
[17179596.164000] ivtv: probe of 0000:02:04.0 failed with error -12
[17179596.164000] ivtv0: Autodetected WinTV PVR 150 card (cx23416 based)
[17179596.164000] ACPI: PCI Interrupt 0000:02:0b.0[A] -> GSI 16 (level, low) -> IRQ 169
[17179596.164000] ivtv0: Unreasonably low latency timer, setting to 64 (was 32)
[17179596.212000] tveeprom: ivtv version

I thought I just copied paste from the guide on the previous page.  My `uname -r` is = 2.6.15-26-386 which is slightly different than the guide, wondering what I need to do differently.

Thanks for you help.

---

### Post by pipedream on 2006-08-01
Here is what my /lib/firmware/  folder looks like:

drwxr-xr-x  3 root root   4096 May 30 18:53 2.6.15-23-386
drwxr-xr-x  3 root root   4096 Jul 31 18:44 2.6.15-26-386
drwxr-xr-x 19 root root   4096 Jul 31 20:57 ..
lrwxrwxrwx  1 root root     29 Aug  1 17:17 v4l-cx2341x-dec.fw -> /lib/firmware/ivtv-fw-dec.bin
drwxr-xr-x  4 root root   4096 Aug  1 17:17 .
-rw-r--r--  1 root root 262144 Aug  1 20:14 ivtv-fw-enc.bin
-rw-r--r--  1 root root 262144 Aug  1 20:14 ivtv-fw-dec.bin
-r--r--r--  1 root root  14264 Aug  1 20:15 v4l-cx25840.fw
-r--r--r--  1 root root 376836 Aug  1 20:15 v4l-cx2341x-enc.fw
-rw-r--r--  1 root root 155648 Aug  1 20:15 v4l-cx2341x-init.mpg

Not sure why above I am getting the error that the firmware is not found.

---

### Post by Jordy on 2006-08-02
Hey Manoova,

Thanks for the response, bu it still doesn't work for me. The code i put in the reply last night got corrupted by myy copy/paste from the terminal window. So i'll try again:

paul@paul-desktop:~$ sudo apt-get install linux-source-2.6.15 linux-headers-`uname -r`
sudo apt-get install linux-source-2.6.15: command not found

Tried it again tonight but get this response every time even agter reboot...

thanks

paul
](*,)

---

### Post by Jordy on 2006-08-02
Hey Manoova,

Thanks for the response, but it still doesn't work for me. The code i put in the reply last night got corrupted by my copy/paste from the terminal window. So i'll try again:

paul@paul-desktop:~$ sudo apt-get install linux-source-2.6.15 linux-headers-`uname -r`
sudo apt-get install linux-source-2.6.15: command not found

Tried it again tonight but get this response every time even after reboot...

thanks

paul

---

### Post by manoova on 2006-08-02
> **Jordy said:**
> Hey Manoova,

Thanks for the response, but it still doesn't work for me. The code i put in the reply last night got corrupted by my copy/paste from the terminal window. So i'll try again:

paul@paul-desktop:~$ sudo apt-get install linux-source-2.6.15 linux-headers-`uname -r`
sudo apt-get install linux-source-2.6.15: command not found

Tried it again tonight but get this response every time even after reboot...

thanks

paul


Hi Paul

I really don't know. I copied this from Section 5.1 of [http://hyams.webhop.net/mythtv/myth_ubuntu.html]("http://hyams.webhop.net/mythtv/myth_ubuntu.html"). It just works for me. I haven't had anyone else comment that it doesn't work.

What does the output of uname -r look like? Is this a fresh install of Ubuntu 6.06? That package definitely exists as it is referenced here [http://packages.ubuntu.com/dapper/devel/linux-source-2.6.15]("http://packages.ubuntu.com/dapper/devel/linux-source-2.6.15").

Perhaps try installing it using Synaptic Package Manager.

Sean

---

### Post by Jordy on 2006-08-02
Sean,

the result of `uname r` is 2.6.15-26-386..My build is only a few days old, much like me in the world of linux...

how would I use synaptic to achieve this? 

Paul

---

### Post by Jordy on 2006-08-02
Sean  sorry forgot to add the rest... `uname -r` by itself produces

 bash: 2.6.15-26-365: command not found

Paul

---

### Post by manoova on 2006-08-02
> **Jordy said:**
> Sean  sorry forgot to add the rest... `uname -r` by itself produces

 bash: 2.6.15-26-365: command not found

Paul

Drop the ` from before and after uname -r if you are running it on it's own.

For Synaptic, (from memory) Click on System --> Administration --> Synaptic Package Manager. Let it load up and then search for linux-source-2.6.15. When it finds it click Apply.

---

### Post by midwinter_ on 2006-08-03
Hi all.

I'm getting this error following the instructions on the first page:

when I sudo apt-get dvdauthor mplayer-586 

I get "E:  invalid operation dvdauthor"

Any help?  not being able to get past step 2 of the how-two is really driving me nuts.

Cheers

---

### Post by manoova on 2006-08-03
> **midwinter_ said:**
> 
I'm getting this error following the instructions on the first page:

when I sudo apt-get dvdauthor mplayer-586 

I get "E:  invalid operation dvdauthor"


Your command is missing "install". It should read:

apt-get install dvdauthor mplayer-586

---

### Post by midwinter_ on 2006-08-03
Sorry about that!  With 

sudo apt-get install dvdauthor mplayer-586

It gets the package lists, builds the dependency tree, then says

"E:  Couldn't find package mplayer-586"

Any ideas?

Cheers

---

### Post by pipedream on 2006-08-03
For those of you interested and or having problems with your firmware.  I resolved the issue I was having.

What I did was as the guide suggested, but then I copied those files in my /lib/firmware/ folder to (manually created some of these):

/lib/hotplug/firmware/
/usr/lib/firmware/
/usr/lib/hotplug/firmware/

I know I probably replicated where they went but I read on the Wikki for this firmware that there is some file called "firware.agent" that points the firmware to a special "hotplug" directory and that it is different in various versions of linux.

This didn't immediately work.  However, once I did a "Reboot" it worked and both of my PVR-150's showed up with OUT problems and I was able to do a screen capture with both of those.

So, lesson learned here is that if you are a Noob like me and get something wrong the first time and correct it on your 2nd, 3rd, or 4th attempt and it still doesn't work.  Try a good old M$-style reboot of your system.

I hope this information helps someone else at some point.

---

### Post by pipedream on 2006-08-03
For those of you interested and or having problems with your firmware.  I resolved the issue I was having.

What I did was as the guide suggested, but then I copied those files in my /lib/firmware/ folder to (manually created some of these):

/lib/hotplug/firmware/
/usr/lib/firmware/
/usr/lib/hotplug/firmware/

I know I probably replicated where they went but I read on the Wikki for this firmware that there is some file called "firware.agent" that points the firmware to a special "hotplug" directory and that it is different in various versions of linux.

This didn't immediately work.  However, once I did a "Reboot" it worked and both of my PVR-150's showed up with OUT problems and I was able to do a screen capture with both of them.

So, lesson learned here is that if you are a Noob like me and get something wrong the first time and correct it on your 2nd, 3rd, or 4th attempt and it still doesn't work.  Try a good old M$-style reboot of your system.

I hope this information helps someone else at some point.

---

### Post by NT4usB on 2006-08-03
> **pipedream said:**
> "Reboot"

I been looking at too many posts... I'm starting to see double! *g*

I'll second the suggestion to reboot. I was up very late (early AM actually) trying to get my 150's to work. Everything was configured correctly but nothing worked.
Finally said *F* it, shutdown and went to bed.
Next day, fired up and they were working!

---

### Post by manoova on 2006-08-04
> **midwinter_ said:**
> Sorry about that!  With 

sudo apt-get install dvdauthor mplayer-586

It gets the package lists, builds the dependency tree, then says

"E:  Couldn't find package mplayer-586"

Any ideas?

Cheers

No idea. What repositories do you have? I.e. what does /etc/apt/sources.list look like?

---

### Post by pipedream on 2006-08-04
Not sure if this post belongs here or not, if not I apologize in advance.

Here is the problem I am having with MythTV and a “google search” did not reveal any solutions to this issue.

I am getting a “prebuffer time out error”.  I get this error while just watching Live TV.  It works fine and I can record, but if I leave LiveTV running overnight or for more than say three hours it crashes and exists out of mythfrontend.

I just can not see it being a memory issue.  I have 1 Gig of RAM and a freshly installed 400 Gig SATA II hard drive.

I installed Ubuntu using the default file system and setup a directory as Mythtv user to store recording in 

/home/Mythtv/Mythtv/store/recordings   
/home/Mythtv/Mythtv/store/buffers

Hope someone can help.

Thanks!

---

### Post by Shay Stephens on 2006-08-04
Is there any indication of which pvr card has the fewest problems?  I want to set up a pvr, and there doesn't seem to be much talk about which cards are working best.  The pvr-500 looks cool with the dual hardware and it looks like it can handle 720p (is that right?).

Can anyone point me in the right direction here?

---

### Post by chadk on 2006-08-04
I did this and had good results but when I go to test ivtv I get:

/usr/src/ivtv-0.4.6/utils# cat /dev/video0 > /tmp/test.mpg
cat: /dev/video0: No such file or directory


If I look in /dev I don't see any video in there.  No video0, video1, video2, etc., none of them.

---

### Post by chadk on 2006-08-04
lsmod reveals:
 lsmod
Module                  Size  Used by
ivtv                  227220  0
i2c_algo_bit           10120  1 ivtv
videodev               10368  1 ivtv

so I'm not sure why /dev/video0 isn't showing up?

---

### Post by chadk on 2006-08-04
fixed the missing video0 device by moving the card in my PCI slots.
Now my problem is the "repeat" field name in the sql code that updates the tables in mysql.  I need to upgrade to myth tv .19-fixes.

I don't know where to get mythtv0.19-fixes

---

### Post by NT4usB on 2006-08-05
> **chadk said:**
> fixed the missing video0 device by moving the card in my PCI slots.
Now my problem is the "repeat" field name in the sql code that updates the tables in mysql.  I need to upgrade to myth tv .19-fixes.

I don't know where to get mythtv0.19-fixes

[http://www.ubuntuforums.org/showpost.php?p=1234507&postcount=126](http://www.ubuntuforums.org/showpost.php?p=1234507&postcount=126)
this worked for me

---

### Post by techrosis on 2006-08-08
If this is offtopic too much please advise me to a better thread...is it unheard of or not possible to run MythTV without a tuner card...for example...i would like to run it just for the other apps like the dvd player and weather and video player etc...i like the simplicity of it (mainly so my wife will be able to use it ;) )

---

### Post by PowerRanger on 2006-08-08
> **pipedream said:**
> Here is what my /lib/firmware/  folder looks like:

drwxr-xr-x  3 root root   4096 May 30 18:53 2.6.15-23-386
drwxr-xr-x  3 root root   4096 Jul 31 18:44 2.6.15-26-386
drwxr-xr-x 19 root root   4096 Jul 31 20:57 ..
lrwxrwxrwx  1 root root     29 Aug  1 17:17 v4l-cx2341x-dec.fw -> /lib/firmware/ivtv-fw-dec.bin
drwxr-xr-x  4 root root   4096 Aug  1 17:17 .
-rw-r--r--  1 root root 262144 Aug  1 20:14 ivtv-fw-enc.bin
-rw-r--r--  1 root root 262144 Aug  1 20:14 ivtv-fw-dec.bin
-r--r--r--  1 root root  14264 Aug  1 20:15 v4l-cx25840.fw
-r--r--r--  1 root root 376836 Aug  1 20:15 v4l-cx2341x-enc.fw
-rw-r--r--  1 root root 155648 Aug  1 20:15 v4l-cx2341x-init.mpg

Not sure why above I am getting the error that the firmware is not found.


I am also having problems getting the fw-dec firmware to load.
ls -l of my /lib/firmware dir produces the same list.   I've tried copying the contents of this dir to:
/lib/hotplug/firmware/
/usr/lib/firmware/
and 
/usr/lib/hotplug/firmware/
..and rebooting with no success.  
I notice that when I issue ls -l while in  /lib/firmware, the v4l-cx2341x-dec.fw appears as red text highlighted in black.  What does this mean?  Is my sym link bad?

EDIT-- my ls -l results were not _exactly_ the same as the parent post.  I was missing the leading '/' in /lib/firmware/ivtv-fw-dec.bin of the link, I rm'd the original and re-created the link- still had to reboot, but now it's working.  I'm pretty sure I cut & pasted the original commmand to create the link, so somewhere, in one of the turtorials or 'howto's' it's wrong.  

Mike

---

### Post by phenolholic on 2006-08-09
Hello,
I'm following Hyams HOWTO of installing MythTV. In the part that mentions opening up 'localhost' from browser and changing password, and after trying to go into the 'phpmyadmin' directory, I get:

Cannot load mysql extension. Please check your PHP configuration. - Documentation

I ignored this, and kept on with the installation. After loading mythtv-setup, I get a Database Configuration menu, which says 'Myth could not connect to your database. Please verify the correct information' 
asking me for my login, password, host name, database, and database type. On the /home/mythtv/.mythtv/mysql.txt file, this is the information on there:

DBHostName=localhost
DBUserName=admin
DBPassword=
DBName=mythconverg
DBType=QMYSQL3

I tried going into mythtv-setup and putting in admin and leaving the passwd field blank on that database configuration menu, but no luck.

I also tried:
mysql -u root

and got the mysql> prompt and entered:
SET PASSWORD FOR admin = PASSWORD('mythtv');

and got this response:
ERROR 1133 (42000): Can't find any matching row in the user table

I've verified the services are running and indeed Apache2 and MySQL both are running. Any help would be appreciated. Thanks in advance

---

### Post by realitychx on 2006-08-09
> **midwinter_ said:**
> Sorry about that!  With 

sudo apt-get install dvdauthor mplayer-586

It gets the package lists, builds the dependency tree, then says

"E:  Couldn't find package mplayer-586"

Any ideas?

Cheers

I was having the same issue and then i found this and it worked:

sudo vi /etc/apt/sources.list

then add the two lines under the last multiverse line.

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper multiverse

And after that

apt-get update
apt-get install mplayer

---

### Post by skattman83 on 2006-08-10
I was following the tutorial, and I came across this problem, which is listed in the troubleshooting section:

> One of the first items to check is whether or not the mythtv user can access the sql database.  If you can type

    mysql -u mythtv -p mythconverg

and after keying in the mysql password you get a "mysql>" prompt, then you are OK.  Type "quit" to get out of mysql.

It does not recognize my password, however, no solution was provided.  How do I fix this?

---

### Post by wogdog on 2006-08-10
Manoova, like many of the other users here, I am on the multiple rebuild path of my mythTV box. This time I am using the instructions that you created. I am able to get to step 12, Setting up mythweb, and am having a problem.
I can do the following:

[I][INDENT]Edit the apache2 configuration:
      sudo nano *w /etc/apache2/httpd.conf
Add the following to this file:
      LoadModule rewrite_module /usr/lib/apache2/modules/mod_rewrite.so
      LoadModule php5_module /usr/lib/apache2/modules/libphp5.so
      <Directory /var/www/mythweb>
      Options FollowSymLinks
      AllowOverride All
      </Directory>[/INDENT][/I]

but then when I issue the *sudo /etc/init.d/apache2 restart* command, I get the following error: *Expected </Directory\xc2\xa0/var/www/mythweb> but saw </Directory>*

Any advice?

---

### Post by wogdog on 2006-08-10
> **skattman83 said:**
> I was following the tutorial, and I came across this problem, which is listed in the troubleshooting section:



It does not recognize my password, however, no solution was provided.  How do I fix this?

Can you get to the phpmyadmin page and set it through there? I am not sure which tutorial you are using, so I am not sure what step you are on...

---

### Post by skattman83 on 2006-08-10
> **wogdog said:**
> Can you get to the phpmyadmin page and set it through there? I am not sure which tutorial you are using, so I am not sure what step you are on...

I'm using the tutorial that this tutorial refers to.  
[http://hyams.webhop.net/mythtv/myth_ubuntu.html](http://hyams.webhop.net/mythtv/myth_ubuntu.html)

Also, when I go into localhost through firefox to get the phpadmin page, it comes up, but I cant find where to change the password.  Any ideas?

---

### Post by techrosis on 2006-08-10
> **skattman83 said:**
> I'm using the tutorial that this tutorial refers to.  
[http://hyams.webhop.net/mythtv/myth_ubuntu.html](http://hyams.webhop.net/mythtv/myth_ubuntu.html)

Also, when I go into localhost through firefox to get the phpadmin page, it comes up, but I cant find where to change the password.  Any ideas?
i think it's under Privaleges...then you select the root account and scroll down and you'll see the password box...

---

### Post by skattman83 on 2006-08-10
I'm getting this error that is telling me "Couldn't get the color key color, and we need it.  You likely won't get any video."

And its right, I'm not getting any video.  Any ideas on whats wrong or how to fix this?

---

### Post by xargonax on 2006-08-12
Hi,

I have been trying to compile ivtv for the whole afternoon. Everything compiles smoothly with no errors however my dmesg keeps showing:

> 
[17182403.444000] ivtv:  ==================== START INIT IVTV ====================
[17182403.444000] ivtv:  version 0.4.4 (tagged release) loading
[17182403.444000] ivtv:  Linux version: 2.6.15-26-386 preempt 486 gcc-4.0
[17182403.444000] ivtv:  In case of problems please include the debug info between
[17182403.444000] ivtv:  the START INIT IVTV and END INIT IVTV lines, along with
[17182403.444000] ivtv:  any module options, when mailing the ivtv-users mailinglist.
[17182403.444000] ivtv:  ====================  END INIT IVTV  ====================



Is there something I missed?

---

### Post by NoahsMyBro on 2006-08-12
After a few very long nights, and repeated reattempts of various steps, I finally got to where my new Ubuntu/MythTV box is nearly finished. I've used the steps laid out by Hyam, and the slight alterations spelled out by the original poster in this thread, and appreciate the efforts of both of the, as well as the rest of you in this post. There's no way I'd have made it this far without all of this help.

Obviously I still have a problem.

I have NOT begun to install Myth yet. After installing ivtv I try capturing video to test.mpg and viewing it with mplayer. I've tried a few different channels, and the recorded .mpg is *always* dark static.

Prior to this install approach, I'd tried to use KnoppMyth, and saw the same result. With KNoppMyth I traced the problem down to a lack of xvideo support for my Unichrome graphics chipset, but somewhere online I saw that Dapper supports Unichrome, and that's what led me to try Ubuntu for this.

When I run mplayer from the command line, I see this:
```
root@myth-server:~# mplayer -vo xv /dev/video0
MPlayer 2:0.99+1.0pre7try2+cvs20060117-0ubuntu8 (C) 2000-2006 MPlayer Team
CPU: Advanced Micro Devices Sempron/Athlon MP/XP Thoroughbred; Duron Applebred (Family: 6, Stepping: 1)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 1 3DNow2: 1 SSE: 1 SSE2: 0
Compiled with runtime CPU detection.


91 audio & 204 video codecs
Opening joystick device /dev/input/js0
Can't open joystick device /dev/input/js0: No such file or directory
Can't init input joystick
Setting up LIRC support...
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support.
You will not be able to use your remote control.
Playing /dev/video0.
Win32 LoadLibrary failed to load: avisynth.dll, /usr/lib/win32/avisynth.dll, /usr/local/lib/win32/avisynth.dll
MPEG-PS file format detected.
VIDEO:  MPEG2  720x480  (aspect 2)  29.970 fps  9600.0 kbps (1200.0 kbyte/s)
==========================================================================
Opening audio decoder: [mp3lib] MPEG layer-2, layer-3
AUDIO: 48000 Hz, 2 ch, s16le, 384.0 kbit/25.00% (ratio: 48000->192000)
Selected audio codec: [mp3] afm: mp3lib (mp3lib MPEG layer-2, layer-3)
==========================================================================
vo: couldn't open the X11 display ()!
Error opening/initializing the selected video_out (-vo) device.


Exiting... (End of file)

```

Any ideas what I need to do here, before I continue with the MythTV install?

Thanks,
Steve

EDIT: (I'm ignoring the mplayer bit above - I can run mplayer from the GUI so I can ignore the above for now.)

I believe this issue has something to do with the tuner type. If I go through every channel from 2 to 78, (ivtv-tune -c 5 -d /dev/video0), ivtv responds that a signal is detected for channels 5 & 6. Also, those channels do show the TV signal, although it's too snowy too watch or hear satisfactorily.

I've been trying to change the tuner type by editing /etc/modprobe.d/options, and then running the two commands:
depmod -a
modprobe ivtv

BUT, I don't know what the two commands there actually do! By running those, I was hoping to 're-read' the options file I've been editing so I can know whether or not I've affected anything by changing the tuner type.

A) Do any of you know which tuner type I should specify for a PVR-150, with Comcast cable of New Jersey? (Analog)
B) Is it correct to set the tuner type in the /etc/modprobe.d/options file?
C) Once I set the tuner type, what is the correct procedure to make the system 're-read' the options file, both for permanence as well as for testing purposes?

Thanks,
Steve

---

### Post by iglablues on 2006-08-12
I've not seen anyone else post a similar question, so I'm already going on the assumption that I'm just missing something. 

I have a Myth box all set up using Hyam's guide and the edits at the beginning of this thread. I only have one tuner installed (PVR-250), I'm using Myth18, and I have DirectTV. I have the remote that came with the card installed and everything, and I'm using it for recording purposes right now because I don't yet know how to make it control my satellite box. So, I change channels with the regular remote, and record or timeshift with the Hauppauge remote. All back story.

The real issue I have is that my tv has to be tuned to channel 3 to get channels, right? So, following Hyam, I run the ivtv-tune -c 3 /dev/video0 and when I start mythtv it goes fine, I get a picture. I turn off my box, come back the next day, it loads right into MythTV and I get fuzz. I have to go back out and rerun that line to get the card to tune to channel 3. Isn't there some way to make that a permanent change? I thought the line above would do that, but it seems to be temporary only. I can do it every time I turn on the box, but it sort of defeats the purpose of having it boot right into the MythTV utility if I have to bcak out every time to set the channel. What am I missing?

---

### Post by iglablues on 2006-08-12
Never mind. I have larger problems to deal with now. I think I may just have to hang up the MythTV hat and go with something more user-friendly, like Beyond TV or something. ](*,) 

This box took forever to get going, and I was happily sitting watching Kids Next Door: The Movie when the screen went blue. I had disabed the screensaver (again, using Hyram's guide), so I knew it wasn't that. Long wait later I was finally able to get back to my Ubuntu screen and the terminal, where I saw all these myth_proto_version error-type messages. Tried to go back in to MythTV, and I got something about device0 not being recognized. I rebooted, tried to log in, and it wouldn't let me. Kept cycling. At one point an error message about the GDM popped up. I had, maybe an hour ago, edited the GDM following Hyram's guide so that it would boot into the MythTV user. Apparently that backfired, because now I can't get into my system at all. 

I also tried hooking it up directly to my monitor again and not the tv. X Server can't be started. I get a "fatal server error: No screens found". :( 

This was perhaps the wrong project for me after all. After all the raves I'd read, I thought it was doable, but I guess it's not for everyone, no matter how good you are at following instructions.

---

### Post by NoahsMyBro on 2006-08-14
Not sure if this is acceptable for the forum, but I just want to bump this in case some of you gurus weren't around over the weekend. If I don't see any further action on it after this bump, I promise I won't do this again.

Thanks,
Steve

---

### Post by dodongo on 2006-08-14
Hi Steve --  I don't know if "bumping" is considered appropriate 'round here -- but I do know that if you break etiquette, no one is going to banish you from the boards forever, or something awful!  :)

In the hopes of at least getting the ball rolling on your question:

> I've been trying to change the tuner type by editing /etc/modprobe.d/options, and then running the two commands:
depmod -a
modprobe ivtv

BUT, I don't know what the two commands there actually do! By running those, I was hoping to 're-read' the options file I've been editing so I can know whether or not I've affected anything by changing the tuner type.

Well, to quote [this site]("http://linux.about.com/library/cmd/blcmdl8_depmod.htm"):

> Depmod creates a "Makefile"-like dependency file, based on the symbols it finds in the set of modules mentioned on the command line or from the directories specified in the configuration file. This dependency file is later used by modprobe to automatically load the correct module or stack of modules.

I don't know if that actually will help (sorry!) but there's a brief overview of what those tools do.  Essentially, they make sure the kernel modules you want to load are ready to go in properly.  And I'm content to take it on faith at that point, but if others have more instructional goodies to toss in, I'm all ears!

I may be wrong on this -- so please step in and holler if I'm wrong -- but I do not believe /etc/modprobe.d/options is the place to make modifications to your MythTV / PVR-150 setup.

The two things that I can think of right off the bat:

1.  In the mythtv-setup program, go to General (#1) and check for your Frequency table:  You need to make sure you're on us-cable, or possibly one of the two variants (you may need to check each, stopping mythbackend before changing the setting each time).  The reason you're getting only fuzzy reception on only a couple of channels total may be due to the fact that the system is looking on the wrong table.

2.  That mplayer error does look a little suspect to me, though it doesn't account for most of the other symptoms you've got, from my perspective.  Let's not deal with that unless we have to -- I get some video output errors in my log files, too, but mythtv has run flawlessly since I got it set up.  I hope we'll get you to that point soon! 

Good luck -- let me know if you need more help with #1, or the results of trying that out...  And of course, I hardly know what I'm doing anyway, so if others have insights, please jump in!  :D

---

### Post by NoahsMyBro on 2006-08-14
Dodongo - thanks for the advice. I sa the bit you quoted regarding depmod and modprobe, but haven't really comprehended it yet. I think I need to spend some time to actually focus and figure it out.

As for my specific problem, I haven't installed Myth yet. I wanted to verify ivtv is working properly first.

I think tonight I'm going to try and connect an old videogame cosnole to the Hauppauge and see if I can capture a signal from it, either on Channel 3 using "-tus-bcast", or the composite-in video input.

-- Steve

---

### Post by dodongo on 2006-08-14
> **NoahsMyBro said:**
> As for my specific problem, I haven't installed Myth yet. I wanted to verify ivtv is working properly first.

Oh, cheers.  Sorry I didn't pick up on that.  You still have to select the right frequency table, even when using the ivtv command-line tools.  I'm not at my Ubuntu box ATM, but if you do this

```
ivtv-tune --help
```

I think you'll find there is a command-line option for specifying which table you want, along with the channel, etc.  I don't know what all the us-cable variants are (there are several, like us-cable-hrc, I think) -- but try first using us-cable as your frequency table and see if that works / helps / makes things worse.

---

### Post by deba on 2006-08-15
I'm having problems with ivtv compile, and being new to linux need some help :)

[4294689.432000] ivtv:  ==================== START INIT IVTV ====================
[4294689.432000] ivtv:  version 0.4.4 (tagged release) loading
[4294689.432000] ivtv:  Linux version: 2.6.15-23-386 preempt 486 gcc-4.0
[4294689.432000] ivtv:  In case of problems please include the debug info between
[4294689.432000] ivtv:  the START INIT IVTV and END INIT IVTV lines, along with
[4294689.432000] ivtv:  any module options, when mailing the ivtv-users mailinglist.
[4294689.432000] ivtv0: Autodetected WinTV PVR 350 card (cx23415 based)
[4294689.433000] ACPI: PCI Interrupt 0000:02:09.0[A] -> GSI 16 (level, low) -> IRQ 185
[4294689.671000] usbcore: registered new driver hiddev
[4294689.715000] ACPI: PCI Interrupt 0000:00:14.5[B] -> GSI 17 (level, low) -> IRQ 209
[4294689.756000] tveeprom: ivtv version
[4294689.756000] tveeprom: Hauppauge: model = 48135, rev = J324, serial# = 7244836
[4294689.756000] tveeprom: tuner = Philips FM1246 (idx = 24, type = 1)
[4294689.756000] tveeprom: tuner fmt = PAL(I) (eeprom = 0x10, v4l2 = 0x00000010)
[4294689.756000] tveeprom: audio processor = MSP4418 (type = 19)
[4294689.756000] tveeprom: decoder processor = SAA7115 (type = 13)
[4294689.756000] ivtv0: i2c attach to card #0 ok [client=tveeprom, addr=50]
[4294689.957000] ACPI: PCI Interrupt 0000:02:08.0[A] -> GSI 18 (level, low) -> IRQ 201
[4294690.012000] tuner (ivtv): chip found at addr 0xc2 i2c-bus ivtv i2c driver #0
[4294690.012000] ivtv0: i2c attach to card #0 ok [client=(tuner unset), addr=61]
[4294690.249000] saa7115 0-0021: saa7115 found @ 0x42 (ivtv i2c driver #0)
[4294690.395000] ivtv0: i2c attach to card #0 ok [client=saa7115, addr=21]
[4294690.460000] saa7127 0-0044: saa7127 found @ 0x88 (ivtv i2c driver #0)
[4294690.460000] ivtv0: i2c attach to card #0 ok [client=saa7127, addr=44]
[4294690.493000] msp3400 0-0040: chip=MSP4418G-A2 +nicam +simple +simpler +radio mode=simpler
[4294690.493000] msp3400 0-0040: msp34xxg daemon started
[4294690.516000] ivtv0: i2c attach to card #0 ok [client=MSP4418G-A2, addr=40]
[4294691.018000] NET: Registered protocol family 17
[4294691.254000] ivtv0: loaded v4l-cx2341x-enc.fw firmware (262144 bytes)
[4294691.257000] ivtv0: unable to open firmware v4l-cx2341x-dec.fw
[4294691.257000] ivtv0: did you put the firmware in the hotplug firmware directory?
[4294691.257000] ivtv0 warning: failed loading decoder firmware
[4294691.257000] ivtv0 warning: Error loading firmware -1!
[4294691.257000] ivtv0: Error -1 initializing firmware.
[4294691.265000] ivtv0: Error -12 on initialization
[4294691.265000] ivtv: probe of 0000:02:09.0 failed with error -12
[4294691.269000] ivtv:  ====================  END INIT IVTV  ====================

---

### Post by dodongo on 2006-08-15
This part looks critical to me:

> 
[4294691.257000] ivtv0: unable to open firmware v4l-cx2341x-dec.fw
[4294691.257000] ivtv0: did you put the firmware in the hotplug firmware directory?
[4294691.257000] ivtv0 warning: failed loading decoder firmware

I would go back and do everything in section 5.2 of [the guide]("http://hyams.webhop.net/mythtv/myth_ubuntu.html") again (sorry!).  It looks like you missed or messed up on the steps that deal with extracting and symlinking this file in the right place.

In particular, this part:

```
mv /lib/modules/ivtv-fw-dec.bin /usr/lib/hotplug/firmware/
mv /lib/modules/ivtv-fw-enc.bin /usr/lib/hotplug/firmware/
cp ../v4l-cx2341x-init.mpg /usr/lib/hotplug/firmware
ln -s /usr/lib/hotplug/firmware/ivtv-fw-dec.bin /usr/lib/hotplug/firmware/v4l-cx2341x-dec.fw 
```

The first line there moves the decoder firmware to the proper location, and the last symlinks that file to another location.  I don't have any idea why, but I know if you do both those properly, the decoder firmware should load.  

You did some / all of it right up to that point though -- just above that line, the log mentions it did load the encoder firmware properly.  But to reiterate, I would redo all of section 5.2 just to be on the safe side.

---

### Post by deba on 2006-08-15
Thanks for reply Dodongo, I have re-done section 5.2 and get this same result how do un link symlinks? I think this is problem this is the dir structure and the end:-

drwxr-xr-x  3 root root   4096 May 31 01:53 2.6.15-23-386
drwxr-xr-x 19 root root   4096 Aug 14 22:56 ..
lrwxrwxrwx  1 root root     28 Aug 15 00:00 v4l-cx2341x-dec.fw -> lib/firmware/ivtv-fw-dec.bin
drwxr-xr-x  3 root root   4096 Aug 15 00:00 .
-rw-r--r--  1 root root 262144 Aug 15 21:42 ivtv-fw-enc.bin
-rw-r--r--  1 root root 262144 Aug 15 21:42 ivtv-fw-dec.bin
-r--r--r--  1 root root  14264 Aug 15 21:43 v4l-cx25840.fw
-r--r--r--  1 root root 376836 Aug 15 21:43 v4l-cx2341x-enc.fw
-rw-r--r--  1 root root 155648 Aug 15 21:43 v4l-cx2341x-init.mpg


Any one gotta clue ??, i'm sure someone has this problem before. I need to learn more linux comands and quick :)

---

### Post by dodongo on 2006-08-15
> **deba said:**
> Thanks for reply Dodongo, I have re-done section 5.2 and get this same result how do un link symlinks? I think this is problem this is the dir structure and the end:-

drwxr-xr-x  3 root root   4096 May 31 01:53 2.6.15-23-386
drwxr-xr-x 19 root root   4096 Aug 14 22:56 ..
lrwxrwxrwx  1 root root     28 Aug 15 00:00 v4l-cx2341x-dec.fw -> lib/firmware/ivtv-fw-dec.bin
drwxr-xr-x  3 root root   4096 Aug 15 00:00 .
-rw-r--r--  1 root root 262144 Aug 15 21:42 ivtv-fw-enc.bin
-rw-r--r--  1 root root 262144 Aug 15 21:42 ivtv-fw-dec.bin
-r--r--r--  1 root root  14264 Aug 15 21:43 v4l-cx25840.fw
-r--r--r--  1 root root 376836 Aug 15 21:43 v4l-cx2341x-enc.fw
-rw-r--r--  1 root root 155648 Aug 15 21:43 v4l-cx2341x-init.mpg


Any one gotta clue ??, i'm sure someone has this problem before. I need to learn more linux comands and quick :)
To "undo" a symlink, just delete it.  So in your case, you'd go to that directory and do

```
sudo rm v4l-cx2341x-dec.fw
```

then you can do

```
sudo ln -s /usr/lib/hotplug/firmware/ivtv-fw-dec.bin /usr/lib/hotplug/firmware/v4l-cx2341x-dec.fw
```

You'll notice your symlink above is pointing to the wrong file!  That may be the problem.  And yes, while setting up my system, I had a very similar problem.  You're not alone!

---

### Post by deba on 2006-08-15
Now i'm lost! ok i've deleted the link but how do you mean its pointing to the wrong file ? Is the HOWTO doc wrong?

---

### Post by dodongo on 2006-08-15
You'll notice in your output earlier that the file looked like this:

```
v4l-cx2341x-dec.fw -> lib/firmware/ivtv-fw-dec.bin
```

But /lib/firmware/iviv-fw-dec.bin isn't where the file should've been!  It's not pointing there anymore, of course, since you've deleted it.

If you followed the howto instructions precisely, your decoder firmware should be in /usr/lib/hotplug/firmware -- that's what this command does:

```
mv /lib/modules/ivtv-fw-dec.bin /usr/lib/hotplug/firmware/
```

If you followed those instructions exactly, and use the symlink command exactly, you should have all the right files in the right places, and your decoder firmware problems should be a thing of the past!  Again, I'd just encourage you to do all of sect. 5.2 over again, in the hopes of catching any other remaining problems.

---

### Post by deba on 2006-08-15
If you check the 1st page of this thread you will noitce the corrections that have been made for dapper install. This is what i'm following:-


When you get to this:
Quote:
cd utils
wget [ftp://ftp.shspvr.com/download/wintv-...0.24.23035.zip](ftp://ftp.shspvr.com/download/wintv-...0.24.23035.zip)
wget [ftp://ftp.shspvr.com/download/wintv-....22254_inf.zip](ftp://ftp.shspvr.com/download/wintv-....22254_inf.zip)
unzip pvr_2.0.24.23035.zip
./ivtvfwextract.pl pvr_1.18.21.22254_inf.zip
cp HcwMakoA.ROM /usr/lib/hotplug/firmware/v4l-cx25840.fw
cp HcwFalcn.rom /usr/lib/hotplug/firmware/v4l-cx2341x-enc.fw
mv /lib/modules/ivtv-fw-dec.bin /usr/lib/hotplug/firmware/
mv /lib/modules/ivtv-fw-enc.bin /usr/lib/hotplug/firmware/
cp ../v4l-cx2341x-init.mpg /usr/lib/hotplug/firmware
ln -s /usr/lib/hotplug/firmware/ivtv-fw-dec.bin /usr/lib/hotplug/firmware/v4l-cx2341x-dec.fw

Instead do this:
Code:

cd utils wget [ftp://ftp.shspvr.com/download/wintv-...0.24.23035.zip](ftp://ftp.shspvr.com/download/wintv-...0.24.23035.zip) wget [ftp://ftp.shspvr.com/download/wintv-....22254_inf.zip](ftp://ftp.shspvr.com/download/wintv-....22254_inf.zip) unzip pvr_2.0.24.23035.zip ./ivtvfwextract.pl pvr_1.18.21.22254_inf.zip cp HcwMakoA.ROM /lib/firmware/v4l-cx25840.fw cp HcwFalcn.rom /lib/firmware/v4l-cx2341x-enc.fw mv /lib/modules/ivtv-fw-dec.bin /lib/firmware/ mv /lib/modules/ivtv-fw-enc.bin /lib/firmware/ cp ../v4l-cx2341x-init.mpg /lib/firmware/ ln -s lib/firmware/ivtv-fw-dec.bin /lib/firmware/v4l-cx2341x-dec.fw

---

### Post by deba on 2006-08-15
There is no /hotplug directory

---

### Post by dodongo on 2006-08-15
> **deba said:**
> **If you check the 1st page of this thread you will noitce the corrections that have been made for dapper install.**

Ah!  That's right -- I'd forgotten there was an addendum on the first page.

---

### Post by backdoor on 2006-08-15
Hello,

This is a great post in showing the steps to get MythTv going.  And the many questions and answers helped clear up a lot of things.

I want to ask another question and hopefully its not too out of line with this post.

I have 2 tuners in my machine.  A PVR250 and a WinTV GO card.
Both work fine.  The only problem is after I've assinged them in MythTV using the dev/videoX device numbers, and I happen to reboot my machine afterwards, the device numbers get switched.  Needless to say, I can not watch TV (I get the menu page back) and only thing I can do to fix it is go to mythtv-setup again and remove/readd the cards back in and re-assign the current /dev/videoX numbers.

I believe the switching of the devices is happening because of udev and the order in which the cards get initialized.  The first to initialize gets /dev/video0 and the next /dev/video1.

My question is, is there any way I can nail up the devices so that they don't keep on changing on me after every reboot?

Thanks in advance.

---

### Post by NoahsMyBro on 2006-08-15
To Dodongo, and any others following my piece of this thread:
Thanks for all your help; I've gotten past the particular stumbling block I'd been facing.

To any others troubleshooting like I've been for the past week:
NEVER OVERLOOK THE OBVIOUS.

My problem was that I captured nothing but static, regardless of tuner-type, channel, frequency, etc... Turns out my #@$%*^&@ coax cable was defective! I swapped out the cable, and began capturing perfectly sharp and clear signals.   :mad: 

I'm now faced with the problem that my capture is in Black & White, but I'm pretty sure I've seen that addressed on various webpages, so hopefully I'll get it solved easily.

-- Steve

---

### Post by deba on 2006-08-16
Hi backdoor

> I believe the switching of the devices is happening because of udev and the order in which the cards get initialized. The first to initialize gets /dev/video0 and the next /dev/video1.


Maybe if swap the cards around in your machine, worth a try i think the system will init pci slot0 then pci slot1, etc. Did this with ethernet cards a long time ago seemed to work ok.

---

### Post by backdoor on 2006-08-16
Hi deba,

I can certainly try this, but I do believe that because of the almost random nature of which card intializes first using udev, this might not make a difference.

I still want to know if there is a way to assign (hard-code) the cards to the /dev/videoX devices so I don't have to worry about it anymore.  I have hard-coded ethernet devices like this before, but I just don't know how it could be done for these tuners.

Thanks.

---

### Post by phenolholic on 2006-08-17
Hello,
I followed Hyams guide in installing MythTV. Everything seems okay, as far as the setup and configuration. In mythfrontend, I select Watch TV and I get purple vertical lines and my computer freezes. I think it might have something to do with the display. The TV card works fine under XawTV. Any guidance is appreciated

---

### Post by NoahsMyBro on 2006-08-22
I'm stumped.

I've got a Ubuntu 6.06 PC, with an Hauppauge PVR-150.

I've followed the combination of the Hyams Home guide & the first post in this thread, and have almost achieved complete success.

However, I cannot get the MySQL database to work properly. If I launch mythfilldatabase, I receive a ton of the INSERT INTO dd_schedule errors that suggest I have MySQL 5, and MythTV 0.18. If I understand correctly, I can either downgrade MySQL, or upgrade MythTV, to solve the problem.

Here's the part I don't understand: I built this machine from scratch a couple of weeks ago specifically for this purpose. I started with a bare drive, and followed the HOWTOs As closely as I could. To the best of my knowledge, I have *NEVER* installed MythTV 0.18. From the very beginning, I downloaded the 0.19 .bz2 files, and used those, adhering to the Hyams page update (section 9.8).

SO, that doesn't jibe with the conclusion that my db errors are related to Myth being version 0.18. 

HOWEVER, if I look at Synaptic, and search for Myth, everything that comes up lists 18.1 in the 'installed version' column.

10 minutes ago I went back, and re-did the entire 9.8 section in the HOWTO, up until the section to add items to the startup programs tab (haven't done that step yet).

In a nutshell, I've followed the guide, using section 9.8 to install myth 0.19, and stopped just before adding anything to startup. I haven't bothered setting up the remote control yet, or anything else past section 6.

HOW do I have Myth 0.18, instead of 0.19, and how may I fix this so I can successfully run mythfilldatabase, have a program guide, and schedule recordings?

I've been losing a ton of sleep over this project, and most folks think I'm nuts, and ought to just get a Tivo or load up WinXP instead. But as I replied to someone about this last week, "Where's the fun in that?"

Thanks for any help,
Steve

---

### Post by NT4usB on 2006-08-22
I fought it for over a month...
Finally, I got it working by first getting my cards to work, and mysql, and the remote. Once those were stable, I installed MythTV.
Add these to your sources.list:
deb [http://knm.org/mythdebs/](http://knm.org/mythdebs/) binary/
deb-src [http://knm.org/mythdebs/](http://knm.org/mythdebs/) source/
Then install 19-5 via synaptic.
Fix the issue with mythmusic by installing libcdaudio0 from the 5.10 repos. Then pin it so it doesn't get updated.

---

### Post by xboxer21 on 2006-08-23
NT4usB,
when I use synaptic to install mythtv 19-5, there seems to be a lot of unresolved dependencies and therefore finally fails to install mythtv. Any Thoughts?

Thanks

---

### Post by NT4usB on 2006-08-23
Resolve the dependencies... I dunno?
Do you have everything else working? ivtv, mysql, apache2, etc?
iirc, once I had those dialed, I could add and remove mythtv at will.
The first time I installed 0.19 I used the repositories at:
deb [http://home.eng.iastate.edu/~superm1](http://home.eng.iastate.edu/~superm1) dapper main
deb-src [http://home.eng.iastate.edu/~superm1](http://home.eng.iastate.edu/~superm1) dapper main
but it only had the base install. 
iirc, I later found knm so I removed 0.19 and installed 0.19-5. (or, maybe I dumped 19-5 over the top. I don't remember)
May be that the 0.19 at iastate.edu left behind things that made 19-5 work. 
I'm no expert although I'm fairly proficient after several uninstalls, formats, reinstalls, etc. It does work!
My Mythbox has been running unattended for ~2 months now with only one myth lockup and one restart to update the kernel.

---

### Post by dillanlaughlin on 2006-08-23
Hey Everyone, I am stuck on these drivers, I've followed the guide 4 times now to no avail. As far as I can tell I've followed the directions right down to the letter. Right now this is as far as I get:

> dillan@ubuntu01:~$ sudo depmod
dillan@ubuntu01:~$ modprobe ivtv
FATAL: Module ivtv not found.

I am using the Hauppage 500 card and would greatly appreciate anyones help.
Thank You!

---

### Post by xboxer21 on 2006-08-23
> **NT4usB said:**
> Resolve the dependencies... I dunno?
Do you have everything else working? ivtv, mysql, apache2, etc?
iirc, once I had those dialed, I could add and remove mythtv at will.
The first time I installed 0.19 I used the repositories at:
deb [http://home.eng.iastate.edu/~superm1](http://home.eng.iastate.edu/~superm1) dapper main
deb-src [http://home.eng.iastate.edu/~superm1](http://home.eng.iastate.edu/~superm1) dapper main
but it only had the base install. 
iirc, I later found knm so I removed 0.19 and installed 0.19-5. (or, maybe I dumped 19-5 over the top. I don't remember)
May be that the 0.19 at iastate.edu left behind things that made 19-5 work. 
I'm no expert although I'm fairly proficient after several uninstalls, formats, reinstalls, etc. It does work!
My Mythbox has been running unattended for ~2 months now with only one myth lockup and one restart to update the kernel.

I will try in the same order as you did , Everything else is set up correctly.

Thanks Again

---

### Post by admiralawesome on 2006-08-24
dillanlaughlin,

I had the same problem.  Here's what I did.  I used the ivtv-0.4.6 drivers rather than 0.4.4.  During the make install, there were conflicts listed in the command's output.  They're easy to miss.  I fixed those by copying and pasting the exact commands listed in the make install output.  Things still didn't work after that; I wasn't getting an ivtv folder under /lib/modules/`uname -r`/ at all.  So I did a search and found that the ivtv folder was instead being created under /lib/modules/2.6.13.7-ubuntu1/ I think it was.  Copying the ivtv folder from there to /lib/modules/`uname -r`/ fixed the "Module ivtv not found" problem for me.  After fixing any conflicts during the make install of the ivtv drivers, do a search for the ivtv folder. It might have been created under the wrong folder.

---

### Post by xboxer21 on 2006-08-26
NT4usB,
I finally got mythtv installed except for mythflix which has an issue with overwriting some png file installed by mythnews. I have all drivers installed. I can capture and playback video with audio after following Hyam's how to ([http://hyams.webhop.net/mythtv/myth_ubuntu.html)](http://hyams.webhop.net/mythtv/myth_ubuntu.html)). However I have the following problems :(
[LIST]
[*]When I select Watch TV I hear sound for one second and the whole pc freezes.
[*]Mythweb does not work
[/LIST]
I have modifies the .htaccess file and have added the mysql username and password, I still continue to get the following error message
Database Setup Error

The database environment variables are not correctly set in the
included .htaccess file. Please read through the comments included
in the file and set up the db_* environment variables correctly.

iSome possible solutions are to make sure that mod_env is enabled
n httpd.conf, as well as having followed the instructions in the
README about the AllowOverride settings.

I would case less about the webmyth for now, but I'm not sure why my pc freezes after I select Watch TV.

Thanks

---

### Post by NT4usB on 2006-08-27
What version of ivtv did you install?
Mythtv locked up when I used 4.5 (or 4.6, I don't remember which...)
4.4 worked for me.
iirc, my computer wasn't locked up, just mythtv. If I Alt+Tab to bring the terminal to the front, then Ctrl+c to cancel Mythfrontend, I got my computer back.

I didn't install mythflix, saw no need for it. Mythweb didn't interest me (yet) It may work, I dunno.

---

### Post by xboxer21 on 2006-08-27
NT4usB,
MythTV works now, just had to reinstall Nvidia drivers and a few codecs to get it working. I have ivtv-0.4.4 installed, never tried 4.5 or 4.6, I will try messing with mythweb and post my results later
Thanks for all your help.

---

### Post by crispy_420 on 2006-08-29
ABLE TO WATCH TV!!! 

Basically it works for me but I do have a few questions:

Will my windows MCE remote work (was originally a Win MCE system I built, but hated the record format - MS-DVR)? More so has anyone tried and suceeded?

I have a mini-ATX mobo (asus) with built it 5.1 surround sound (RealTek), will that work with a reciever with multichannel in (eg. front right, front left, etc.)? Want this for DVD watching (in surround sound 5.1) and so the subwoofer will work?

What is the "good" repo for libcdaudio0? I know it is a breezy one but could someone post one here for me?

So far so good for me and I am trying this again for the first time in years. I originally bought this system to make a MythTV box (on FC3 - been a bit since I started this project). But after many attempts and failures, I gave up for a long time. For this time I used Win Media Center, which I was really happy with. But there was a catch: recorded to a format that many video editors at the time. So again I gave up and my system just sat there for months without a boot up. Then I came across posts like this and others and thought, why not. After many failures and reinstalls, I took my time and did a little bit at a time (install -> drivers -> ETC.). This time it worked, and for that I credit Ubuntu and it's loyal community.

So to those still having problems, DO NOT GIVE UP!!! In the long run it will be worth it to succeed. You may spend a long time getting it up and running, but you get a nice standard format. Just think of media center's format and the time it will cost to re-encode all those MS-DVR formatted videos to a functional format.

But as with any new project, only time will tell. For me this was just a project. If I really need to record, I have SageTV and [GB-PVR]("http://www.gbpvr.com/") to record. GB-PVR is a free project (to use) but is not open source. And it has many plugins too (ComSkip to name one).

Next up: [SageTV Linux OEM ]("http://www.sagetv.com/linuxOEMedition.html")

Maybe even a swappable drive system. One drive with Ubuntu/MythTV and Windows Media Center (dual boot). Another with SageTV Linux.

---

### Post by skattman83 on 2006-08-31
I can't get the ivtv driver working on my pvr 150 card.  Running the dmesg ends with these lines, which I think may be the problem:```
[17180164.692000] tuner: type set to 4 (NoTuner) by ivtv i2c driver #0
[17180164.988000] ivtv0: Initialized WinTV PVR 150, card #0
[17180164.988000] ivtv:  ====================  END INIT IVTV  ================== 
```

That line about type set to 4 (NoTuner), seems like it would be causing a problem.  Any ideas?

---

### Post by xboxer21 on 2006-08-31
> **skattman83 said:**
> I can't get the ivtv driver working on my pvr 150 card.  Running the dmesg ends with these lines, which I think may be the problem:```
[17180164.692000] tuner: type set to 4 (NoTuner) by ivtv i2c driver #0
[17180164.988000] ivtv0: Initialized WinTV PVR 150, card #0
[17180164.988000] ivtv:  ====================  END INIT IVTV  ================== 
```

That line about type set to 4 (NoTuner), seems like it would be causing a problem.  Any ideas?

What version of the ivtv drivers did you install and what kernel are you using?
Can you record any video by doing
cat /dev/video0 > /tmp/test.mpg
 (hit Ctrl+C to stop the capturing)
Use Mplayer to Play it back.


BTW I got my mythweb working after I did the following changes to the apache2.conf file

nano /etc/apache2/apache2.conf

<Directory /var/www/mythweb>
        AllowOverride All
        Options FollowSymLinks
</Directory>

---

### Post by skattman83 on 2006-08-31
@xboxer21:
I'm running IVTV driver version 4.4, and my kernel is 2.6.15-26-686.  If I try to run cat /dev/video0 > /tmp/test.mpg, all I get is static.

---

### Post by skattman83 on 2006-08-31
I just purchased the card in July.  Is it perhaps a new version that I need a newer driver for?

---

### Post by xboxer21 on 2006-09-01
> **skattman83 said:**
> @xboxer21:
I'm running IVTV driver version 4.4, and my kernel is 2.6.15-26-686.  If I try to run cat /dev/video0 > /tmp/test.mpg, all I get is static.

You probably are seeing static because the Tuner is not tuned to a viewable channel. Go to the bottom of section 5.3 in Hyams how to ([http://hyams.webhop.net/mythtv/myth_ubuntu.html](http://hyams.webhop.net/mythtv/myth_ubuntu.html)) and try to tune using command line.

I bought my PVR-250 2 weeks ago. The 4.4 drivers should work.
Did you follow althepcman's modifications to the howto to install the firmware at the beginning of this thread (1st post).

---

### Post by skattman83 on 2006-09-01
Yes, I followed the changes to the guide.  The section in the dmesg about ivtv does not list any errors loading the firmware, so I don't think that is the problem, unless the firmware isn't for my card.  What card do you have, if you run lspci?

---

### Post by xboxer21 on 2006-09-01
I have a PVR250, Dont have access to my home pc now but I vaguely remember seeing something about Hauppauge when I did lspci. I will confirm when i get a chance.

---

### Post by skattman83 on 2006-09-01
Mine listed some brand other brand name, I think it started with an N, but I'm not certain.

---

### Post by xboxer21 on 2006-09-02
> **skattman83 said:**
> Mine listed some brand other brand name, I think it started with an N, but I'm not certain.

Here's mine after I do lspci
0000:04:06.0 Multimedia video controller: Internext Compression Inc iTVC16 (CX23416) MPEG-2 Encoder (rev 01)

---

### Post by detectiveinspekta on 2006-09-02
Hi I think this line is wrong and craped people up.

ln -s lib/firmware/ivtv-fw-dec.bin /lib/firmware/v4l-cx2341x-dec.fw

should be
```

ln -s /lib/firmware/ivtv-fw-dec.bin /lib/firmware/v4l-cx2341x-dec.fw

```
I think...

I had a problem with the ivtv firmware decoder, the encoder would load but the decoder was missing. I did the above but ubuntu went to the shits when I tried to reboot.
I'm using dapper server install BTW, it uses some server kernel so I think it maybe the cause?

Also how long does it take to change channels? I had it running under windows and it takes maybe 1s to change using a bunny ears arial

---

### Post by detectiveinspekta on 2006-09-02
Alsome, you need to do a full power-down of the computer, take the plug out for a few minutes after you install ivtv. Seems to be loading correctly now. Worth putting in

---

### Post by NoahsMyBro on 2006-09-02
I've got a few different questions about my MythTV install. I'm not sure if they should be asked separately, each in it's own thread, or if it's proper to ask here in this thread. If they should be asked elsewhere, just say so and I'll happily do that.

System is:
 Ubuntu 6.06
 MySQL 5.0
 MythTV 19.5
 Motherboard is a Soyo K7VME - Integrated Unichrome graphics, no TV-Out.
 CPU = AMD Athlon XP 1Ghz. ACTUALLY PAID FOR SEMPRON 2300, a little PO'd about that.
 RAM = 512Mb.
 Hauppauge PVR-150 with Remote Control

I've got the fundamental functionality of my MythTV system working properly now. I can download the Program Guide, schedule recordings, watch live TV, and watch recordings, and use the Hauppauge Remote Control.

1) No TV-Out. If I pick up an inexpensive AGP videocard, what would I have to do to install it, and use it instead of the onboard graphics? How will this impact the currently installed and working MythTV install?

......1a) I'm seriously considering this card: [GIGABYTE GV-N52128DS Geforce FX5200 128MB DDR AGP 4X/8X Video Card]("http://www.newegg.com/Product/Product.asp?Item=N82E16814125191"). Once finished, the system will only be used for MythTV, and *maybe*, down the road, a little bit of MAME. No other gaming will be asked of the system. Any opinions on how well this card will work here? The only reason I'm looking to buy the card is to gain TV-Out, and watch the MythTV machine on a 27" JVC CRT, Standard Def TV.

2) Addition of a 2nd Tuner - The system has an Hauppauge PVR-150 tuner installed and working. The motherboard has only two PCI slots, with the Hauppauge occupying one. Now that I've got things working, I'd like to add a second tuner. I've got an Avermedia TV-M179 card waiting to be installed. Would it be fairly painless to install this second card and not break anything, using section 8.14 (adding a second PVR-150) of Hyams Home HOWTO as a guide?

3) During the install (using the first post of this thread, and the Hyams Home HOWTO), somewhere along the way I broke MyPHPAdmin. Should I bother trying to fix it, and does anybody have any good ideas as to how I could fix it? Regrettably I'm not prepared to give even the most basic info about *how* specifically it is broken.

4) MythGallery - I've copied a bunch of pictures from our home server to the directory I specified for MythGallery to use. Inadvertently, some of the files I copied were videos originally shot by my digital camera. (I think the digicam produces Quicktime format videos.) Whether a picture or a video, the thumbnails all display in MythGallery. If I view one of the videos, the video displays fine. If, however, I try to view a photo, all I see is a large white screen where the picture should display. I haven't found any reference at all to something like this via Google. Have any of you seen this, and do you know how I can fix it?

5) Multitasking - I'm not sure what I can or can't do on this box  while running Myth. Occasionally it seems Myth (Front or Backend) will crash when I do different things, with no apparent reason or warning. When this happens, nothing occurs to let me know; rather, Myth Frontend will stop responding, and/or programs simply won't record. This hasn't happened frequently enough for me to see a pattern, but has occured a few times. What CAN I do while using Myth, and what can't I do? I'm not trying to do anything terribly demanding on the system. 

...5a) One specific task I'm curious about - Can I watch one recorded program while recording a new program?

...5b) Can I rip CDs while recording a program?

6) Music - The first few times I tried to rip a CD, the job ended incredibly quickly, with no tracks ripped. I changed the encoding to .OGG and the ripping process took much longer, and actually worked. I'm now installing LAME. Is it likely I simply had no .mp3 encoder installed?

7) Program Guide - I'm in North America. I've registered an account with Zap2It, and am using the DataDirect Program Guide.

...7a) When running Mythfilldatabase I see a msg telling me my 
subscription will expire, I think sometime in November. Why is this? Does it auto-renew? Does the subscription begin to cost money after that?

...7b) A couple of nights ago I tried searching for a specific program, Veronica Mars. I could not find the program listed anywhere in the guide, whether using Find or doing a search. Is this a problem on my end, or does the guide sometimes just miss things?

I know that's a lot of questions. I hope some of you can help with some of them; sorry again if this is the wrong place for this.

Thanks for any help you can offer,
Steve

---

### Post by NT4usB on 2006-09-03
> **NoahsMyBro said:**
> ...
1) No TV-Out. If I pick up an inexpensive AGP videocard, what would I have to do to install it, and use it instead of the onboard graphics? How will this impact the currently installed and working MythTV install?

......1a) I'm seriously considering this card: [GIGABYTE GV-N52128DS Geforce FX5200 128MB DDR AGP 4X/8X Video Card]("http://www.newegg.com/Product/Product.asp?Item=N82E16814125191"). Once finished, the system will only be used for MythTV, and *maybe*, down the road, a little bit of MAME. No other gaming will be asked of the system. Any opinions on how well this card will work here? The only reason I'm looking to buy the card is to gain TV-Out, and watch the MythTV machine on a 27" JVC CRT, Standard Def TV.

TV out doesn't require much of a card. This one would work. 
(ed: this card doesn't have s-video or component out. Composite out is your only choice. Be sure it will work on your tv)
You'll have to install the Nvidia drivers (plenty of documentation on these boards.)
Shouldn't bother the Myth install... Don't know if your system can handle much multi tasking while Myth is running. If you really want your programs recorded (or whatever else you're working on) Probably should decide to do one or the other.

> **NoahsMyBro said:**
> 
2) Addition of a 2nd Tuner - The system has an Hauppauge PVR-150 tuner installed and working. The motherboard has only two PCI slots, with the Hauppauge occupying one. Now that I've got things working, I'd like to add a second tuner. I've got an Avermedia TV-M179 card waiting to be installed. Would it be fairly painless to install this second card and not break anything, using section 8.14 (adding a second PVR-150) of Hyams Home HOWTO as a guide?

Don't think Myth (or ivtv) supports Aver. Look it up. 
A second PVR-150 would require only a couple edits to files.

> **NoahsMyBro said:**
> ...
...5a) One specific task I'm curious about - Can I watch one recorded program while recording a new program?

Should be no problem. I record 2 programs and watch another.

> **NoahsMyBro said:**
> 
...5b) Can I rip CDs while recording a program?

Probably not. Ripping (specifically, encoding) requires a lot of resources.

> **NoahsMyBro said:**
> 
7) Program Guide - I'm in North America. I've registered an account with Zap2It, and am using the DataDirect Program Guide.

...7a) When running Mythfilldatabase I see a msg telling me my 
subscription will expire, I think sometime in November. Why is this? Does it auto-renew? Does the subscription begin to cost money after that?

they'll send an email to the address you signed up with to remind you. You simply go to your account there and click on a renew button.

> **NoahsMyBro said:**
> 
...7b) A couple of nights ago I tried searching for a specific program, Veronica Mars. I could not find the program listed anywhere in the guide, whether using Find or doing a search. Is this a problem on my end, or does the guide sometimes just miss things?

Lots of different ways to search. Did you try searching by keyword 'Veronica' or something?
The guide is not perfect. If you know it's playing and when, you can manually schedule it.

---

### Post by detectiveinspekta on 2006-09-03
Anyone know how to make the tv-out for the PVR-350?

So far I have this site [http://www.willmer.com/kb/2005/04/x-out-on-a-pvr-350/](http://www.willmer.com/kb/2005/04/x-out-on-a-pvr-350/) but there is no such location for /usr/X11R6/lib/modules/drivers/
Using a dapper install

---

### Post by skattman83 on 2006-09-04
When I run a lspci, my card comes up the same as xboxer21's.  Secondly, I saw this post below so I investigated it.

> **detectiveinspekta said:**
> Hi I think this line is wrong and craped people up.

ln -s lib/firmware/ivtv-fw-dec.bin /lib/firmware/v4l-cx2341x-dec.fw

should be
```

ln -s /lib/firmware/ivtv-fw-dec.bin /lib/firmware/v4l-cx2341x-dec.fw

```
I think...


I ran a ```
ls -l /lib/firmware/v41-cx2341x-dec.fw
``` which pointed to /lib/firmware/ivtv-fw-dec.bin.  The link was listed as red text on a black background, what does that mean?

---

### Post by detectiveinspekta on 2006-09-05
Red means its a broken link, look at /lib/firmware/ and check if ivtv-fw-dec.bin is there and v4l-cx2341x-dec.fw. I believe one of them is just a shorcut to the other, that what the ln -s does.

---

### Post by skattman83 on 2006-09-06
After running depmod, this is what my dmesg looks like:

```
[17180348.956000] ivtv:  ==================== START INIT IVTV ====================
[17180348.956000] ivtv:  version 0.4.4 (tagged release) loading
[17180348.956000] ivtv:  Linux version: 2.6.15-26-686 SMP preempt 686 gcc-4.0
[17180348.956000] ivtv:  In case of problems please include the debug info between
[17180348.956000] ivtv:  the START INIT IVTV and END INIT IVTV lines, along with[17180348.956000] ivtv:  any module options, when mailing the ivtv-users mailinglist.
[17180348.956000] ivtv0: Autodetected WinTV PVR 150 card (cx23416 based)
[17180348.956000] ACPI: PCI Interrupt 0000:01:01.0[A] -> GSI 17 (level, low) -> IRQ 201
[17180349.024000] tveeprom: ivtv version
[17180349.024000] tveeprom: Hauppauge: model = 26132, rev = G1B2, serial# = 9545814
[17180349.024000] tveeprom: tuner = <unknown> (idx = 112, type = 4)
[17180349.024000] tveeprom: tuner fmt = NTSC(M) (eeprom = 0x08, v4l2 = 0x00001000)
[17180349.024000] tveeprom: audio processor = CX25841 (type = 23)
[17180349.024000] tveeprom: decoder processor = CX25841 (type = 1c)
[17180349.024000] ivtv0: i2c attach to card #0 ok [client=tveeprom, addr=50]
[17180349.040000] tuner (ivtv): chip found at addr 0xc2 i2c-bus ivtv i2c driver #0
[17180349.040000] ivtv0: i2c attach to card #0 ok [client=(tuner unset), addr=61]
[17180349.212000] cx25840 2-0044: cx25841-23 found @ 0x88 (ivtv i2c driver #0)
[17180352.308000] cx25840 2-0044: loaded v4l-cx25840.fw firmware (14264 bytes)
[17180352.368000] ivtv0: i2c attach to card #0 ok [client=cx25840, addr=44]
[17180352.372000] wm8775 2-001b: chip found @ 0x36 (ivtv i2c driver #0)
[17180352.380000] ivtv0: i2c attach to card #0 ok [client=wm8775, addr=1b]
[17180353.104000] ivtv0: loaded v4l-cx2341x-enc.fw firmware (262144 bytes)
[17180353.312000] ivtv0: Encoder revision: 0x02050032
[17180353.312000] ivtv0: Allocate DMA encoder MPEG stream: 128 x 32768 buffers (4096KB total)
[17180353.312000] ivtv0: Allocate DMA encoder YUV stream: 194 x 10800 buffers (2048KB total)
[17180353.316000] ivtv0: Allocate DMA encoder VBI stream: 120 x 17472 buffers (2048KB total)
[17180353.316000] ivtv0: Allocate DMA encoder PCM audio stream: 455 x 4608 buffers (2048KB total)
[17180353.316000] tuner: type set to 4 (NoTuner) by ivtv i2c driver #0
[17180353.608000] ivtv0: Initialized WinTV PVR 150, card #0
[17180353.608000] ivtv:  ====================  END INIT IVTV  ====================

```

Where am I going wrong?  I'm still just getting static.  I checked the card on a windows machine, and it works great.

---

### Post by HellSpawn on 2006-09-06
I first tryed with ivtv 4.4 and get this:

```

[19061.488731] ivtv:  ==================== START INIT IVTV ====================
[19061.488734] ivtv:  [COLOR="Red"]version 0.4.4 (tagged release) loading[/COLOR]
[19061.488736] ivtv:  Linux version: 2.6.15-23-amd64-k8 SMP preempt gcc-4.0
[19061.488739] ivtv:  In case of problems please include the debug info between
[19061.488741] ivtv:  the START INIT IVTV and END INIT IVTV lines, along with
[19061.488743] ivtv:  any module options, when mailing the ivtv-users mailinglist.
[19061.491434] ivtv0: Autodetected WinTV PVR 250 card (cx23415 based)
[19061.491475] ACPI: PCI Interrupt 0000:02:09.0[A] -> Link [APC2] -> GSI 17 (level, low) -> IRQ 217
[19061.548872] tveeprom: ivtv version
[19061.548922] tveeprom: Hauppauge: model = 48012, rev = G310, serial# = 2601096
[19061.549005] tveeprom: tuner = Philips FI1236 MK2 (idx = 10, type = 2)
[19061.549079] tveeprom: tuner fmt = NTSC(M) (eeprom = 0x08, v4l2 = 0x00001000)
[19061.549161] tveeprom: audio processor = MSP3445 (type = c)
[19061.549229] tveeprom: decoder processor = Type 0x00 (type = 0)
[19061.549339] ivtv0: i2c attach to card #0 ok [client=tveeprom, addr=50]
[19061.578394] tuner (ivtv): chip found at addr 0xc2 i2c-bus ivtv i2c driver #0
[19061.578486] ivtv0: i2c attach to card #0 ok [client=(tuner unset), addr=61]
[19061.660510] saa7115 5-0021: saa7115 found @ 0x42 (ivtv i2c driver #0)
[19061.725225] ivtv0: i2c attach to card #0 ok [client=saa7115, addr=21]
[19061.738845] msp3400 5-0040: chip=MSP3445G-B8 +nicam +simple +simpler +radio mode=simpler
[19061.738981] msp3400 5-0040: msp34xxg daemon started
[19061.748195] ivtv0: i2c attach to card #0 ok [client=MSP3445G-B8, addr=40]
[COLOR="Blue"][19062.113038] ivtv0: loaded v4l-cx2341x-enc.fw firmware (262144 bytes)
[19062.128788] ivtv0: loaded v4l-cx2341x-dec.fw firmware (262144 bytes)[/COLOR]
[COLOR="Red"][19062.247698] ivtv0 warning: Encoder mailbox not found
[19062.269182] ivtv0 warning: Decoder mailbox not found
[19062.269249] ivtv0: Error locating firmware.
[19062.278128] msp3400 5-0040: chip reset failed
[19062.279379] ivtv0: Error -12 on initialization
[19062.279443] ivtv: probe of 0000:02:09.0 failed with error -12[/COLOR]
[19062.279520] ivtv:  ====================  END INIT IVTV  ====================

```


I read something about "patching" 4.1 for Ubuntu 64bits, so I tryed that and get the same result:

```

[19708.034415] Linux video capture interface: v1.00
[19708.065092] ivtv:  ==================== START INIT IVTV ====================
[19708.065185] ivtv:  [COLOR="Red"]version 0.4.1 (tagged release) loading[/COLOR]
[19708.065248] ivtv:  Linux version: 2.6.15-23-amd64-k8 SMP preempt gcc-4.0
[19708.065326] ivtv:  In case of problems please include the debug info between
[19708.065405] ivtv:  the START INIT IVTV and END INIT IVTV lines, along with
[19708.065507] ivtv:  any module options, when mailing the ivtv-users mailinglist.
[19708.065946] ivtv0: Autodetected WinTV PVR 250 card (cx23415 based)
[19708.066067] ACPI: PCI Interrupt 0000:02:09.0[A] -> Link [APC2] -> GSI 17 (level, low) -> IRQ 217
[19708.099549] tveeprom: ivtv version
[19708.099600] tveeprom: Hauppauge: model = 48012, rev = G310, serial# = 2601096
[19708.099683] tveeprom: tuner = Philips FI1236 MK2 (idx = 10, type = 2)
[19708.099757] tveeprom: tuner fmt = NTSC(M) (eeprom = 0x08, v4l2 = 0x00001000)
[19708.099838] tveeprom: audio processor = MSP3445 (type = c)
[19708.099901] tveeprom: decoder processor = Type 0x00 (type = 0)
[19708.099972] ivtv0: i2c attach to card #0 ok [client=tveeprom, addr=50]
[19708.101622] tuner (ivtv): chip found at addr 0xc2 i2c-bus ivtv i2c driver #0
[19708.101712] ivtv0: i2c attach to card #0 ok [client=(tuner unset), addr=61]
[19708.117838] saa7115 5-0021: saa7115 found @ 0x42 (ivtv i2c driver #0)
[19708.269965] ivtv0: i2c attach to card #0 ok [client=saa7115, addr=21]
[19708.282312] msp3400 5-0040: chip=MSP3445G-B8 +nicam +simple +simpler +radio mode=simpler
[19708.282445] msp3400 5-0040: msp34xxg daemon started
[19708.298667] ivtv0: i2c attach to card #0 ok [client=MSP3445G-B8, addr=40]
[[COLOR="Blue"]19708.673627] ivtv0: loaded v4l-cx2341x-enc.fw firmware (262144 bytes)
[19708.690163] ivtv0: loaded v4l-cx2341x-dec.fw firmware (262144 bytes)[/COLOR]
[COLOR="Red"][19708.809547] ivtv0 warning: Encoder mailbox not found
[19708.832795] ivtv0 warning: Decoder mailbox not found
[19708.832863] ivtv0: Error locating firmware.
[19708.836174] msp3400 5-0040: chip reset failed
[19708.837455] ivtv0: Error -12 on initialization
[19708.837520] ivtv: probe of 0000:02:09.0 failed with error -12[/COLOR]
[19708.837591] ivtv:  ====================  END INIT IVTV  ====================


```


this is my /lib/firmware

```

:~ # ll /lib/firmware/
total 1092
drwxr-xr-x 3 root root   4096 2006-06-04 00:26 2.6.15-23-amd64-generic
drwxr-xr-x 3 root root   4096 2006-06-04 00:26 2.6.15-23-amd64-k8
drwxr-xr-x 2 root root   4096 2006-06-20 21:53 2.6.15-25-amd64-generic
drwxr-xr-x 2 root root   4096 2006-06-20 21:53 2.6.15-25-amd64-k8
drwxr-xr-x 2 root root   4096 2006-08-03 21:33 2.6.15-26-amd64-generic
drwxr-xr-x 2 root root   4096 2006-08-03 21:33 2.6.15-26-amd64-k8
-rw-r--r-- 1 root root 262144 2006-09-06 09:00 ivtv-fw-dec.bin
-rw-r--r-- 1 root root 262144 2006-09-06 09:00 ivtv-fw-enc.bin
lrwxrwxrwx 1 root root     29 2006-09-06 09:02 v4l-cx2341x-dec.fw -> /lib/firmware/ivtv-fw-dec.bin
-r--r--r-- 1 root root 376836 2006-09-06 09:00 v4l-cx2341x-enc.fw
-rw-r--r-- 1 root root 155648 2006-09-06 09:00 v4l-cx2341x-init.mpg
-r--r--r-- 1 root root  14264 2006-09-06 09:00 v4l-cx25840.fw


```


My Kernel:
Linux igor 2.6.15-23-amd64-k8 #1 SMP PREEMPT Tue May 23 13:51:32 UTC 2006 x86_64 GNU/Linux

My lspci:

```

lspci
0000:00:00.0 Host bridge: nVidia Corporation nForce3 250Gb Host Bridge (rev a1)
0000:00:01.0 ISA bridge: nVidia Corporation nForce3 250Gb LPC Bridge (rev a2)
0000:00:01.1 SMBus: nVidia Corporation nForce 250Gb PCI System Management (rev a1)
0000:00:02.0 USB Controller: nVidia Corporation CK8S USB Controller (rev a1)
0000:00:02.1 USB Controller: nVidia Corporation CK8S USB Controller (rev a1)
0000:00:02.2 USB Controller: nVidia Corporation nForce3 EHCI USB 2.0 Controller (rev a2)
0000:00:05.0 Bridge: nVidia Corporation CK8S Ethernet Controller (rev a2)
0000:00:06.0 Multimedia audio controller: nVidia Corporation nForce3 250Gb AC'97 Audio Controller (rev a1)
0000:00:08.0 IDE interface: nVidia Corporation CK8S Parallel ATA Controller (v2.5) (rev a2)
0000:00:0a.0 IDE interface: nVidia Corporation CK8S Serial ATA Controller (v2.5) (rev a2)
0000:00:0b.0 PCI bridge: nVidia Corporation nForce3 250Gb AGP Host to PCI Bridge (rev a2)
0000:00:0e.0 PCI bridge: nVidia Corporation nForce3 250Gb PCI-to-PCI Bridge (rev a2)
0000:00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
0000:00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
0000:00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
0000:00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
0000:01:00.0 VGA compatible controller: nVidia Corporation GeForce 6200 (rev a1)
0000:02:07.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
[COLOR="Blue"]0000:02:09.0 Multimedia video controller: Internext Compression Inc iTVC15 MPEG-2 Encoder (rev 01)[/COLOR]

```

I'll appriciate any help!! ](*,)

---

### Post by xboxer21 on 2006-09-06
> **skattman83 said:**
> After running depmod, this is what my dmesg looks like:

```
[17180348.956000] ivtv:  ==================== START INIT IVTV ====================
[17180348.956000] ivtv:  version 0.4.4 (tagged release) loading
[17180348.956000] ivtv:  Linux version: 2.6.15-26-686 SMP preempt 686 gcc-4.0
[17180348.956000] ivtv:  In case of problems please include the debug info between
[17180348.956000] ivtv:  the START INIT IVTV and END INIT IVTV lines, along with[17180348.956000] ivtv:  any module options, when mailing the ivtv-users mailinglist.
[17180348.956000] ivtv0: Autodetected WinTV PVR 150 card (cx23416 based)
[17180348.956000] ACPI: PCI Interrupt 0000:01:01.0[A] -> GSI 17 (level, low) -> IRQ 201
[17180349.024000] tveeprom: ivtv version
[17180349.024000] tveeprom: Hauppauge: model = 26132, rev = G1B2, serial# = 9545814
[17180349.024000] tveeprom: tuner = <unknown> (idx = 112, type = 4)
[17180349.024000] tveeprom: tuner fmt = NTSC(M) (eeprom = 0x08, v4l2 = 0x00001000)
[17180349.024000] tveeprom: audio processor = CX25841 (type = 23)
[17180349.024000] tveeprom: decoder processor = CX25841 (type = 1c)
[17180349.024000] ivtv0: i2c attach to card #0 ok [client=tveeprom, addr=50]
[17180349.040000] tuner (ivtv): chip found at addr 0xc2 i2c-bus ivtv i2c driver #0
[17180349.040000] ivtv0: i2c attach to card #0 ok [client=(tuner unset), addr=61]
[17180349.212000] cx25840 2-0044: cx25841-23 found @ 0x88 (ivtv i2c driver #0)
[17180352.308000] cx25840 2-0044: loaded v4l-cx25840.fw firmware (14264 bytes)
[17180352.368000] ivtv0: i2c attach to card #0 ok [client=cx25840, addr=44]
[17180352.372000] wm8775 2-001b: chip found @ 0x36 (ivtv i2c driver #0)
[17180352.380000] ivtv0: i2c attach to card #0 ok [client=wm8775, addr=1b]
[17180353.104000] ivtv0: loaded v4l-cx2341x-enc.fw firmware (262144 bytes)
[17180353.312000] ivtv0: Encoder revision: 0x02050032
[17180353.312000] ivtv0: Allocate DMA encoder MPEG stream: 128 x 32768 buffers (4096KB total)
[17180353.312000] ivtv0: Allocate DMA encoder YUV stream: 194 x 10800 buffers (2048KB total)
[17180353.316000] ivtv0: Allocate DMA encoder VBI stream: 120 x 17472 buffers (2048KB total)
[17180353.316000] ivtv0: Allocate DMA encoder PCM audio stream: 455 x 4608 buffers (2048KB total)
[17180353.316000] tuner: type set to 4 (NoTuner) by ivtv i2c driver #0
[17180353.608000] ivtv0: Initialized WinTV PVR 150, card #0
[17180353.608000] ivtv:  ====================  END INIT IVTV  ====================

```

Where am I going wrong?  I'm still just getting static.  I checked the card on a windows machine, and it works great.

Have you tried using the command line tuner (ivtv-tune), or else go ahead and install mythtv and use the channel scanner in the mythtv-setup and verify if the card works or not.

---

### Post by skattman83 on 2006-09-06
> **xboxer21 said:**
> Have you tried using the command line tuner (ivtv-tune), or else go ahead and install mythtv and use the channel scanner in the mythtv-setup and verify if the card works or not.

I installed mythtv .19 from the repositories listed in the mythtv wiki.  It doesn't detect any channels when I try to do a channel scan.

---

### Post by xboxer21 on 2006-09-07
> **skattman83 said:**
> I installed mythtv .19 from the repositories listed in the mythtv wiki.  It doesn't detect any channels when I try to do a channel scan.

I Tried reinstalling my PVR250 with the .44 drivers and everything worked fine. Looks like you have followed everything mentioned in the howto's, but again did you make sure you have the environment set right before compiling the ivtv drivers? Have you followed every single step mentioned in section 5.1 of Hyams how to.

---

### Post by skattman83 on 2006-09-07
@xboxer21:
I'll redo that portion of the guide, and see if that fixes it.

---

### Post by skattman83 on 2006-09-07
Maybe this is my problem.  When I get to the command "make" for the ivtv drivers, it outputs this: ```
root@MythTV:/usr/src/ivtv-0.4.4# make
make -C driver all
make[1]: Entering directory `/usr/src/ivtv-0.4.4/driver'
make -C /lib/modules/2.6.15-26-686/build M=/usr/src/ivtv-0.4.4/driver modules
make[2]: Entering directory `/usr/src/linux-source-2.6.15'

  WARNING: Symbol version dump /usr/src/linux-source-2.6.15/Module.symvers
           is missing; modules will have no dependencies and modversions.

  Building modules, stage 2.
  MODPOST

```
But then it continues and appears to complete (I could be wrong).  How do I generate that Module.symvers file?

---

### Post by xboxer21 on 2006-09-07
Though i have an AMD64 processor , I'm using the 386 kernel. I use 2.6.15-25-386. I have always installed Mythtv on a fresh install of ubuntu.
I'm not sure why you get these errors. I have had absolutely no trouble compiling the ivtv drivers.

---

### Post by tytus on 2006-09-07
I am getting the following error when trying to install mythtv using Synaptic Package Manager:
```
E: mythtv-common: subprocess post-installation script returned error exit status 1
E: mythtv-frontend: dependency problems - leaving unconfigured
E: mythbrowser: dependency problems - leaving unconfigured
E: mythdvd: dependency problems - leaving unconfigured
E: mythgallery: dependency problems - leaving unconfigured
E: mythgame: dependency problems - leaving unconfigured
E: mythnews: dependency problems - leaving unconfigured
E: mythphone: dependency problems - leaving unconfigured
E: mythtv-database: dependency problems - leaving unconfigured
E: mythtv-backend: dependency problems - leaving unconfigured
E: mythtv: dependency problems - leaving unconfigured
E: mythvideo: dependency problems - leaving unconfigured
E: mythweather: dependency problems - leaving unconfigured
E: mythweb: dependency problems - leaving unconfigured
E: mythmusic: dependency problems - leaving unconfigured

```
Have anybody seen it? What does that mean?

I followed Hyams instructions (modified according to the first page of this thread).

thanks

---

### Post by jacrider on 2006-09-07
I am now up and running with Myth!  I have the Trailer Park Boys playing on the other screen right now (twinview).  

Two minor issues:

First, why do I have to login as the mythtv user?  How can I set up my normal  login as a mythtv-user?

Secondly, what is MythWeb?  Does it allow people on our in-the-house network to stream recorded content?  I haven't been able to find out much about it searching on either these forums or the web.

Thanks for all the help in this thread.  Without it, I never would have this working!

---

### Post by skattman83 on 2006-09-07
> **xboxer21 said:**
> Though i have an AMD64 processor , I'm using the 386 kernel. I use 2.6.15-25-386. I have always installed Mythtv on a fresh install of ubuntu.
I'm not sure why you get these errors. I have had absolutely no trouble compiling the ivtv drivers.
This was a fresh install as well.  Besides the steps taken in the guide, the only other thing I've done is compile ndiswrapper on this computer.

---

### Post by spirilis on 2006-09-07
Hit a fatal snag.

After mythtv's installed, mythfilldatabase bombs:
(several of these, not sure how many, it scrolls a lot)
```

DB Error (Inserting into dd_schedule):
Query was:
INSERT INTO dd_schedule (programid,stationid,scheduletime,duration,repeat,stereo,subtitled,hdtv,closecaptioned,tvrating,partnumber,parttotal,endtime) VALUES('EP8464790003','11782','2006-09-08T21:00:00','01:00:00',0,1,0,0,1,'TV-PG',0,0,'2006-09-08T22:00:00');
Driver error was [2/1064]:
QMYSQL3: Unable to execute query
Database error was:
You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near 'repeat,stereo,subtitled,hdtv,closecaptioned,tvrating,partnumber,parttotal,endtim' at line 1


```

---

### Post by spirilis on 2006-09-07
Also up above you have an "ln" statement using
```

ln -s lib/firmware/ivtv-fw-dec.bin /lib/firmware/v4l-cx2341x-dec.fw

```

Think there needs to be a leading slash in front of that "lib/" -- without it ivtv reports errors on load.  (bad symlink so it can't find the decoder firmware)

---

### Post by spirilis on 2006-09-07
Looks like the answer is to downgrade to mysql 4.1.  Seems to bomb though, and if I try to remove mysql-server, mythtv and mythtv-database have to go with it.
```

root@media:~# apt-get install mysql-server-4.1
Reading package lists... Done
Building dependency tree... Done
The following extra packages will be installed:
  mysql-client
The following packages will be REMOVED:
  mysql-server mysql-server-5.0
The following NEW packages will be installed:
  mysql-client mysql-server-4.1
0 upgraded, 2 newly installed, 2 to remove and 158 not upgraded.
Need to get 36.9kB/17.1MB of archives.
After unpacking 10.2MB disk space will be freed.
Do you want to continue [Y/n]? y
Get:1 http://archive.ubuntu.com dapper-security/main mysql-client 5.0.22-0ubuntu6.06.2 [36.9kB]
Fetched 36.9kB in 0s (49.6kB/s)   
Preconfiguring packages ...
(Reading database ... 93662 files and directories currently installed.)
Removing mysql-server ...
dpkg: mysql-server-5.0: dependency problems, but removing anyway as you request:
 mythtv-database depends on mysql-server; however:
  Package mysql-server is not installed.
  Package mysql-server-5.0 which provides mysql-server is to be removed.
Removing mysql-server-5.0 ...
Stopping MySQL database server: mysqld.
Selecting previously deselected package mysql-client.
(Reading database ... 93499 files and directories currently installed.)
Unpacking mysql-client (from .../mysql-client_5.0.22-0ubuntu6.06.2_all.deb) ...
Unpacking mysql-server-4.1 (from .../mysql-server-4.1_4.1.15-1ubuntu5_i386.deb) ...
Aborting downgrade from (at least) 5.0 to 4.1.
dpkg: error processing /var/cache/apt/archives/mysql-server-4.1_4.1.15-1ubuntu5_i386.deb (--unpack):
 subprocess pre-installation script returned error exit status 1
Errors were encountered while processing:
 /var/cache/apt/archives/mysql-server-4.1_4.1.15-1ubuntu5_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

I'mma attempt to rig it.  I'll keep ubuntu's mysql 5.0 installed but not running while I run mysql 4.1 built from source code.

---

### Post by spirilis on 2006-09-07
So far so good.  mythfilldatabase isn't bombing anymore.

---

### Post by skattman83 on 2006-09-08
My mythtv user cannot access mysql, how do I fix this?  I'm getting this:
```
sh-3.1$ mysql -u mythtv -p mythconverg
Enter password:
ERROR 1045 (28000): Access denied for user 'mythtv'@'localhost' (using password: YES)

```

---

### Post by jacrider on 2006-09-09
I have been researching on these forums and on the web and can't seem to figure out how to get MythWeb up and running.

If anyone has had success and could post a quick set of instructions, I would  really appreciate it.

Thanks.

---

### Post by skattman83 on 2006-09-10
I messed around with the mysql stuff and finally got it to let my mythtv user access the database.  I have a new issue now though.  When I did modprobe ivtv, it would come up as tuner type 4 (no tuner), which i got around by using "modprobe ivtv tuner=50".  When I reboot though, I get static, and when I check dmesg, it has the tuner type 4 message again.  How do I force it to use tuner=50 everytime I boot?

---

### Post by xboxer21 on 2006-09-10
Add it to startup Programs under System->Preferences->Sessions, I might be wrong there might be an easier way to do it by making a script with that modprobe line in it and placing it in the /etc/init.d folder. 
I'm glad you found a way to get aound the dmesg issue.

Thanks

---

### Post by ejslap on 2006-09-11
Hi,
I have been working on this for a few days now, and continually run into the problem of only being able to see static from either MythTv or with mplayer. 

Here is my dmesg output in the IVTV section

```

 ivtv:  ==================== START INIT IVTV ====================
[17179597.916000] ivtv:  version 0.4.6 (tagged release) loading
[17179597.916000] ivtv:  Linux version: 2.6.15-26-686 SMP preempt 686 gcc-4.0
[17179597.916000] ivtv:  In case of problems please include the debug info between
[17179597.916000] ivtv:  the START INIT IVTV and END INIT IVTV lines, along with
[17179597.916000] ivtv:  any module options, when mailing the ivtv-users mailinglist.
[17179597.916000] ivtv0: Autodetected WinTV PVR 150 card (cx23416 based)
[17179597.916000] **** SET: Misaligned resource pointer: dba08d02 Type 07 Len 0
[17179597.916000] ACPI: PCI Interrupt Link [LNKG] enabled at IRQ 11
[17179597.916000] ACPI: PCI Interrupt 0000:01:0a.0[A] -> Link [LNKG] -> GSI 11 (level, low) -> IRQ 11
[17179597.948000] input: ImPS/2 Generic Wheel Mouse as /class/input/input2
[17179597.972000] ivtv0: i2c attach to card #0 ok [client=tveeprom, addr=50]
[17179598.008000] tveeprom 0-0050: Hauppauge model 26132, rev G1B2, serial# 9543504
[17179598.008000] tveeprom 0-0050: tuner model is TCL M2523_5N_E (idx 112, type 4)
[17179598.008000] tveeprom 0-0050: TV standards NTSC(M) (eeprom 0x08)
[17179598.008000] tveeprom 0-0050: audio processor is CX25841 (idx 35)
[17179598.008000] tveeprom 0-0050: decoder processor is CX25841 (idx 28)
[17179598.008000] tveeprom 0-0050: has no radio, has IR remote
[17179598.088000] tuner 0-0061: chip found @ 0xc2 (ivtv i2c driver #0)
[17179598.088000] ivtv0: i2c attach to card #0 ok [client=(tuner unset), addr=61]
[17179598.288000] cx25840 0-0044: ivtv driver
[17179598.288000] cx25840 0-0044: cx25841-23 found @ 0x88 (ivtv i2c driver #0)
[17179598.540000] ath_hal: 0.9.14.9 (AR5210, AR5211, AR5212, RF5111, RF5112, RF2413)
[17179598.600000] wlan: 0.8.6.0 (EXPERIMENTAL)
[17179598.624000] ath_rate_sample: 1.2
[17179598.656000] ath_pci: 0.9.6.0 (EXPERIMENTAL)
[17179598.832000] Floppy drive(s): fd0 is 1.44M
[17179598.852000] FDC 0 is a post-1991 82077
[17179599.024000] ts: Compaq touchscreen protocol output
[17179602.116000] parport: PnPBIOS parport detected.
[17179602.116000] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
[17179602.160000] parport0: Printer, HEWLETT-PACKARD DESKJET 840C
[17179602.364000] cx25840 0-0044: loaded v4l-cx25840.fw firmware (14264 bytes)
[17179602.424000] ivtv0: i2c attach to card #0 ok [client=cx25840, addr=44]
[17179602.476000] wm8775 0-001b: chip found @ 0x36 (ivtv i2c driver #0)
[17179602.484000] ivtv0: i2c attach to card #0 ok [client=wm8775, addr=1b]
[17179603.332000] ivtv0: loaded v4l-cx2341x-enc.fw firmware (262144 bytes)
[17179603.548000] ivtv0: Encoder revision: 0x02050032
[17179603.548000] ivtv0: Allocate DMA encoder MPEG stream: 128 x 32768 buffers (4096KB total)
[17179603.548000] ivtv0: Allocate DMA encoder YUV stream: 194 x 10800 buffers (2048KB total)
[17179603.548000] ivtv0: Allocate DMA encoder VBI stream: 120 x 17472 buffers (2048KB total)
[17179603.548000] ivtv0: Allocate DMA encoder PCM audio stream: 455 x 4608 buffers (2048KB total)
[17179603.600000] tuner 0-0061: tuner type not set
[17179603.616000] tuner 0-0061: tuner type not set
[17179603.632000] ivtv0: Initialized WinTV PVR 150, card #0
[17179603.644000] gameport: EMU10K1 is pci0000:01:0b.1/gameport0, io 0xdff0, speed 1125kHz
[17179603.648000] ivtv:  ====================  END INIT IVTV  ====================

``` 

Also, here is an ls - of my /lib/firmware dir..

```

mythtv@bender:/lib/firmware$ ls -l
total 2052
drwxr-xr-x 2 root root   4096 2006-09-07 01:22 2.6.15-25-686
drwxr-xr-x 3 root root   4096 2006-08-05 18:22 2.6.15-26-386
drwxr-xr-x 3 root root   4096 2006-09-10 20:31 2.6.15-26-686
-rw-r--r-- 1 root root 119713 2006-07-01 16:22 firmware.tar.gz
-rw-r--r-- 1 root root 262144 2006-09-10 22:26 ivtv-fw-dec.bin
-rw-r--r-- 1 root root 262144 2006-09-10 22:26 ivtv-fw-enc.bin
-rw-r--r-- 1 root root 593441 2006-09-10 20:20 pvr_1.18.21.22254_inf.zip
-rw-r--r-- 1 root root 281620 2006-09-10 20:20 pvr_2.0.24.23035.zip
lrwxrwxrwx 1 root root     29 2006-09-10 22:28 v4l-cx2341x-dec.fw -> /lib/firmware/ivtv-fw-dec.bin
-r--r--r-- 1 root root 376836 2006-09-10 22:28 v4l-cx2341x-enc.fw
-rw-r--r-- 1 root root 155648 2006-09-10 22:28 v4l-cx2341x-init.mpg
-r--r--r-- 1 root root  14264 2006-09-10 22:28 v4l-cx25840.fw


```

As far as I can tell, the problem is with the last part of the dmesg output where it says the tuner is not set.  I have also tried "sudo modprobe ivtv tuner=50" as mentioned above, but that didn't work either, nor does a restart/unplug.

Could I have a hardware conflict?  I am running the PVR-150, with a some random wireless pci network card, and an old sound card.  Here is an lspci:

```

0000:00:00.0 Host bridge: Intel Corporation 82815 815 Chipset Host Bridge and Memory Controller Hub (rev 02)
0000:00:01.0 PCI bridge: Intel Corporation 82815 815 Chipset AGP Bridge (rev 02)
0000:00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 01)
0000:00:1f.0 ISA bridge: Intel Corporation 82801BA ISA Bridge (LPC) (rev 01)
0000:00:1f.1 IDE interface: Intel Corporation 82801BA IDE U100 (rev 01)
0000:00:1f.2 USB Controller: Intel Corporation 82801BA/BAM USB (Hub #1) (rev 01)
0000:00:1f.3 SMBus: Intel Corporation 82801BA/BAM SMBus (rev 01)
0000:00:1f.4 USB Controller: Intel Corporation 82801BA/BAM USB (Hub #2) (rev 01)
0000:01:0a.0 Multimedia video controller: Internext Compression Inc iTVC16 (CX23416) MPEG-2 Encoder (rev 01)
0000:01:0b.0 Multimedia audio controller: Creative Labs SB Live! EMU10k1 (rev 07)
0000:01:0b.1 Input device controller: Creative Labs SB Live! MIDI/Game Port (rev 07)
0000:01:0d.0 Ethernet controller: Atheros Communications, Inc.: Unknown device 001a (rev 01)
0000:02:00.0 VGA compatible controller: nVidia Corporation NV20 [GeForce3] (rev a3)

``` 

Any help would be greatly appreciated, I am getting really frustrated.

Thanks!

---

### Post by flotsam on 2006-09-11
re: the mythfilldatabase error:
DB Error (Inserting into dd_schedule):
Query was:
INSERT INTO dd_schedule (programid,stationid,scheduletime,duration,repeat,stereo,subtitled,hdtv,closecaptioned,tvrating,partnumber,parttotal,endtime) VALUES('SH6878270000','19283','2006-06-14T23:30:00','00:30:00',0,0,0,0,0,NULL,0,0,'2006-06-15T00:00:00');
Driver error was [2/1064]:
QMYSQL3: Unable to execute query
Database error was:
You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near 'repeat,stereo,subtitled,hdtv,closecaptioned,tvrating,partnumber,parttotal,endtim' at line 1


It seems to be caused by a Mythtv and mysql version problem.  The Mythtv packages are version 0.18.1 and the latest mysql server is version 5.  You need to use version 4x of mysql server (repository package is version 4.1 I think) with Mythtv 0.18.1. 

I had the same problem.  To fix I removed the Mythtv packages, installed mysql server 4x (it should remove all the mysql 5 components), and re-insalled the myth packages.  Make sure to do a complete removal of mysql server 5, otherwise you won't remove the database and it needs to be rebuilt from scratch.  The mythfilldatabase ran correctly after that.

Alternately, I'm told that mythtv version 0.19 fixes the problem so you could always compile mythtv yourself if you need mysql server 5 for some reason.

---

### Post by annk on 2006-09-12
I have a similar problem like the one stated above.  I followed Hyams instructions (with the Dapper modifications), and I think that I have ivtv driver installed correctly.  When I try to verify that the IVTV drivers work, then I just get a static picture.  Here's what I get for,

sudo depmod
sudo modprobe ivtv
dmesg

Here's what I get for INIT IVTV:
```

[17179596.796000] ivtv:  ==================== START INIT IVTV ====================
[17179596.796000] ivtv:  version 0.4.6 (tagged release) loading
[17179596.796000] ivtv:  Linux version: 2.6.15-26-686 SMP preempt 686 gcc-4.0
[17179596.796000] ivtv:  In case of problems please include the debug info between
[17179596.796000] ivtv:  the START INIT IVTV and END INIT IVTV lines, along with
[17179596.796000] ivtv:  any module options, when mailing the ivtv-users mailinglist.
[17179596.796000] ivtv0: Autodetected WinTV PVR 150 card (cx23416 based)
[17179596.796000] **** SET: Misaligned resource pointer: d877cde2 Type 07 Len 0
[17179596.796000] ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 18
[17179596.796000] ACPI: PCI Interrupt 0000:01:06.0[A] -> Link [LNKA] -> GSI 18 (level, high) -> IRQ 201
[17179596.796000] ivtv0: i2c attach to card #0 ok [client=tveeprom, addr=50]
[17179596.848000] tveeprom 2-0050: Hauppauge model 26582, rev F0B2, serial# 9439053
[17179596.848000] tveeprom 2-0050: tuner model is TCL M2523_5N_E (idx 112, type 4)
[17179596.848000] tveeprom 2-0050: TV standards NTSC(M) (eeprom 0x08)
[17179596.848000] tveeprom 2-0050: audio processor is CX25843 (idx 37)
[17179596.848000] tveeprom 2-0050: decoder processor is CX25843 (idx 30)
[17179596.848000] tveeprom 2-0050: has no radio, has no IR remote
[17179596.860000] tuner (ivtv): chip found at addr 0xc2 i2c-bus bt878 #0 [sw]
[17179596.860000] tuner: type set to 17 (Philips NTSC_M (MK2)) by bt878 #0 [sw]
[17179597.104000] tuner (ivtv): chip found at addr 0xc2 i2c-bus ivtv i2c driver #0
[17179597.104000] ivtv0: i2c attach to card #0 ok [client=(tuner unset), addr=61]
[17179597.332000] msp3400 1-0040: chip=MSP3451G-A2 +nicam +simple +simpler +radio mode=simpler
[17179597.332000] msp3400 1-0040: msp34xxg daemon started
[17179597.412000] bttv0: i2c: checking for TDA9875 @ 0xb0... not found
[17179597.412000] bttv0: i2c: checking for TDA7432 @ 0x8a... not found
[17179597.416000] bttv0: i2c: checking for TDA9887 @ 0x86... not found
[17179597.420000] bttv0: registered device video0
[17179597.420000] bttv0: registered device vbi0
[17179597.420000] bttv0: registered device radio0
[17179597.440000] cx25840 2-0044: ivtv driver
[17179597.440000] cx25840 2-0044: cx25843-23 found @ 0x88 (ivtv i2c driver #0)
[17179597.500000] bttv0: PLL: 28636363 => 35468950 ..eth0: no link during initialization.
[17179597.544000]  ok
[17179597.620000] bt878: AUDIO driver version 0.0.0 loaded
[17179598.720000] NET: Registered protocol family 17
[17179599.332000] eth1: link down
[17179601.376000] cx25840 2-0044: loaded v4l-cx25840.fw firmware (14264 bytes)
[17179601.456000] ivtv0: i2c attach to card #0 ok [client=cx25840, addr=44]
[17179601.500000] wm8775 2-001b: chip found @ 0x36 (ivtv i2c driver #0)
[17179601.512000] ivtv0: i2c attach to card #0 ok [client=wm8775, addr=1b]
[17179602.260000] ivtv0: loaded v4l-cx2341x-enc.fw firmware (262144 bytes)
[17179602.476000] ivtv0: Encoder revision: 0x02050032
[17179602.476000] ivtv0: Allocate DMA encoder MPEG stream: 128 x 32768 buffers (4096KB total)
[17179602.476000] ivtv0: Allocate DMA encoder YUV stream: 194 x 10800 buffers (2048KB total)
[17179602.476000] ivtv0: Allocate DMA encoder VBI stream: 120 x 17472 buffers (2048KB total)
[17179602.476000] ivtv0: Allocate DMA encoder PCM audio stream: 455 x 4608 buffers (2048KB total)
[17179602.476000] tuner: type set to 4 (NoTuner) by ivtv i2c driver #0
[17179602.588000] ivtv0: Initialized WinTV PVR 150, card #0
[17179602.588000] bt878: Bt878 AUDIO function found (0).
[17179602.588000] ACPI: PCI Interrupt 0000:01:08.1[A] -> Link [LNKC] -> GSI 16 (level, high) -> IRQ 217
[17179602.588000] bt878(0): Bt878 (rev 17) at 01:08.1, irq: 217, latency: 64, memory: 0xf2800000
[17179602.592000] ivtv:  ====================  END INIT IVTV  ====================

```

Furthermore, when I do the following command, I get:

ivtvctl -a -d /dev/video1
```

ioctl IVTV_IOC_G_CODEC ok
Codec parameters
aspect      : 2
audio       : 0x00e9
bframes     : 3
bitrate_mode: 0
bitrate     : 8000000
bitrate_peak: 9600000
dnr_mode    : 0
dnr_spatial : 0
dnr_temporal: 8
dnr_type    : 0
framerate   : 0
framespergop: 15
gop_closure : 1
pulldown    : 0
stream_type : 14
ioctl VIDIOC_G_FMT ok
        Type   : Video Capture
        Width  : 720
        Height : 480
ioctl VIDIOC_QUERYCAP ok
        Driver name   : ivtv
        Card type     : WinTV PVR 150
        Bus info      : 0000:01:06.0
        Driver version: 1030
        Capabilities  : 0x01030051
ioctl: VIDIOC_ENUMINPUT
        Input   : 0
        Name    : Tuner
        Type    : 0x00000001
        Audioset: 0x00000003
        Tuner   : 0x00000000
        Standard: 0x0000000000003000 ( NTSC )
        Status  : 0

        Input   : 1
        Name    : Composite 0
        Type    : 0x00000002
        Audioset: 0x00000003
        Tuner   : 0x00000000
        Standard: 0x00000000007F7FFF ( PAL NTSC SECAM )
        Status  : 0

        Input   : 2
        Name    : Composite 1
        Type    : 0x00000002
        Audioset: 0x00000003
        Tuner   : 0x00000000
        Standard: 0x00000000007F7FFF ( PAL NTSC SECAM )
        Status  : 0

        Input   : 3
        Name    : S-Video 0
        Type    : 0x00000002
        Audioset: 0x00000003
        Tuner   : 0x00000000
        Standard: 0x00000000007F7FFF ( PAL NTSC SECAM )
        Status  : 0

        Input   : 4
        Name    : S-Video 1
        Type    : 0x00000002
        Audioset: 0x00000003
        Tuner   : 0x00000000
        Standard: 0x00000000007F7FFF ( PAL NTSC SECAM )
        Status  : 0
ioctl VIDIOC_G_INPUT ok
Video input = 0
ioctl: VIDIOC_ENUMOUTPUT
ioctl VIDIOC_G_OUTPUT failed: Invalid argument
ioctl: VIDIOC_ENUMAUDIO
        Input   : 0
        Name    : Tuner Audio In

        Input   : 1
        Name    : Audio Line 1

        Input   : 2
        Name    : Audio Line 2

        Input   : 3
        Name    : Audio Line 3

        Input   : 4
        Name    : Audio Line 4
ioctl VIDIOC_G_AUDIO ok
Audio input = 0: Tuner Audio In
ioctl VIDIOC_G_FREQUENCY ok
Frequency = 884
ioctl: VIDIOC_ENUMSTD
        index       : 0
        ID          : 0x0000000000003000
        Name        : NTSC
        Frame period: 1001/30000
        Frame lines : 525

        index       : 1
        ID          : 0x00000000000000FF
        Name        : PAL
        Frame period: 1/25
        Frame lines : 625

        index       : 2
        ID          : 0x00000000007F0000
        Name        : SECAM
        Frame period: 1/25
        Frame lines : 625
ioctl VIDIOC_G_STD ok
Video standard = 0x00003000
ioctl: VIDIOC_QUERYCTRL
Brightness = 128
Contrast = 64
Saturation = 64
Hue = 0
Volume = 60928
Mute = 0

```

Is my Hauppauge PVR150 setup correctly?  Why can't I use mplayer to video the cable signal?  

mplayer -vo xv /dev/video1
ivtv-tune -c 3 -d /dev/video1

I just get static, even after trying to change the channel.  Please help this Linux newbie!!!!!

---

### Post by skattman83 on 2006-09-12
I was having a similar problem, I'm still trying to figure it out.  Try this: ```
sudo rmmod ivtv
sudo depmod
sudo modprobe ivtv tuner=50
dmesg
```

That will force ivtv to use a specific tuner.  If you check out /usr/src/ivtv*/driver/driver.h i think it is, you can see a listing of all of the choices for tuner numbers.  I have a newer pvr-150, and 50 worked for me.  The problem I'm running into is that you have to do this everytime you reboot though.

---

### Post by ckdvt on 2006-09-14
I have a PVR-500, and when I type dmesg I get:

(errors are towards the end of the file):confused: 
```
[17210363.284000] ivtv:  ==================== START INIT IVTV ====================
[17210363.284000] ivtv:  version 0.4.4 (tagged release) loading
[17210363.284000] ivtv:  Linux version: 2.6.15-26-386 preempt 486 gcc-4.0
[17210363.284000] ivtv:  In case of problems please include the debug info between
[17210363.284000] ivtv:  the START INIT IVTV and END INIT IVTV lines, along with
[17210363.284000] ivtv:  any module options, when mailing the ivtv-users mailinglist.
[17210363.284000] ivtv0: Autodetected WinTV PVR 150 card (cx23416 based)
[17210363.284000] ACPI: PCI Interrupt 0000:02:08.0[A] -> GSI 17 (level, low) -> IRQ 217
[17210363.284000] ivtv0: Unreasonably low latency timer, setting to 64 (was 32)
[17210363.332000] tveeprom: Second (radio) tuner idx 101
[17210363.332000] tveeprom: ivtv version
[17210363.332000] tveeprom: Hauppauge: model = 23552, rev = D592, serial# = 8320939
[17210363.332000] tveeprom: tuner = Philips FQ1236A MK4 (idx = 92, type = 57)
[17210363.332000] tveeprom: tuner fmt = NTSC(M) (eeprom = 0x08, v4l2 = 0x00001000)
[17210363.332000] tveeprom: audio processor = CX25843 (type = 25)
[17210363.332000] tveeprom: decoder processor = CX25843 (type = 1e)
[17210363.332000] ivtv0: i2c attach to card #0 ok [client=tveeprom, addr=50]
[17210363.380000] ivtv0: This is the first unit of a PVR500
[17210363.384000] tuner (ivtv): chip found at addr 0xc0 i2c-bus ivtv i2c driver #0
[17210363.384000] TEA5767 detected.
[17210363.384000] ivtv0: i2c attach to card #0 ok [client=(tuner unset), addr=60]
[17210363.384000] tuner: type set to 62 (Philips TEA5767HN FM Radio) by autodetect
[17210363.384000] type set to 62 (Philips TEA5767HN FM Radio)
[17210363.384000] tuner (ivtv): chip found at addr 0xc2 i2c-bus ivtv i2c driver #0
[17210363.384000] ivtv0: i2c attach to card #0 ok [client=(tuner unset), addr=61]
[17210363.584000] cx25840 1-0044: cx25843-23 found @ 0x88 (ivtv i2c driver #0)
[17210363.688000] cx25840 1-0044: unable to open firmware v4l-cx25840.fw
[17210363.748000] ivtv0: i2c attach to card #0 ok [client=cx25840, addr=44]
[17210363.780000] wm8775 1-001b: chip found @ 0x36 (ivtv i2c driver #0)
[17210363.788000] ivtv0: i2c attach to card #0 ok [client=wm8775, addr=1b]
[17210363.808000] tda9887 1-0043: (ivtv) chip found @ 0x86 (ivtv i2c driver #0)
[17210363.808000] ivtv0: i2c attach to card #0 ok [client=tda9887, addr=43]
[17210363.832000] ivtv0: Detected a TEA5767 radio tuner. Enabling radio support.
[17210364.444000] ivtv0: unable to open firmware v4l-cx2341x-enc.fw
[17210364.444000] ivtv0: did you put the firmware in the hotplug firmware directory?
[17210364.444000] ivtv0 warning: failed loading encoder firmware
[17210364.444000] ivtv0 warning: Error loading firmware -3!
[17210364.444000] ivtv0: Error -3 initializing firmware.
[17210364.448000] ivtv0: Error -12 on initialization
[17210364.448000] ivtv: probe of 0000:02:08.0 failed with error -12
[17210364.448000] ivtv0: Autodetected WinTV PVR 150 card (cx23416 based)
[17210364.448000] ACPI: PCI Interrupt 0000:02:09.0[A] -> GSI 18 (level, low) -> IRQ 193
[17210364.448000] ivtv0: Unreasonably low latency timer, setting to 64 (was 32)
[17210364.492000] tveeprom: Second (radio) tuner idx 101
[17210364.492000] tveeprom: ivtv version
[17210364.492000] tveeprom: Hauppauge: model = 23552, rev = D592, serial# = 8320939
[17210364.492000] tveeprom: tuner = Philips FQ1236A MK4 (idx = 92, type = 57)
[17210364.492000] tveeprom: tuner fmt = NTSC(M) (eeprom = 0x08, v4l2 = 0x00001000)
[17210364.492000] tveeprom: audio processor = CX25843 (type = 25)
[17210364.492000] tveeprom: decoder processor = CX25843 (type = 1e)
[17210364.492000] ivtv0: i2c attach to card #0 ok [client=tveeprom, addr=50]
[17210364.504000] tuner (ivtv): chip found at addr 0xc2 i2c-bus ivtv i2c driver #0
[17210364.504000] ivtv0: i2c attach to card #0 ok [client=(tuner unset), addr=61]
[17210364.668000] cx25840 1-0044: cx25843-23 found @ 0x88 (ivtv i2c driver #0)
[17210364.708000] cx25840 1-0044: unable to open firmware v4l-cx25840.fw
[17210364.768000] ivtv0: i2c attach to card #0 ok [client=cx25840, addr=44]
[17210364.768000] wm8775 1-001b: chip found @ 0x36 (ivtv i2c driver #0)
[17210364.776000] ivtv0: i2c attach to card #0 ok [client=wm8775, addr=1b]
[17210364.788000] tda9887 1-0043: (ivtv) chip found @ 0x86 (ivtv i2c driver #0)
[17210364.788000] ivtv0: i2c attach to card #0 ok [client=tda9887, addr=43]
[17210364.804000] ivtv0: This is the second unit of a PVR500
[17210364.804000] ivtv0: Correcting tveeprom data: no radio present on second unit
[17210365.464000] ivtv0: unable to open firmware v4l-cx2341x-enc.fw
[17210365.464000] ivtv0: did you put the firmware in the hotplug firmware directory?
[17210365.464000] ivtv0 warning: failed loading encoder firmware
[17210365.464000] ivtv0 warning: Error loading firmware -3!
[17210365.464000] ivtv0: Error -3 initializing firmware.
[17210365.464000] ivtv0: Error -12 on initialization
[17210365.468000] ivtv: probe of 0000:02:09.0 failed with error -12
[17210365.468000] ivtv:  ====================  END INIT IVTV  ====================

```

and ls -ltra /lib/firmware/

```
root@server:/usr/src/ivtv-0.4.4/utils# ls -ltra /lib/firmware/
total 1080
drwxr-xr-x  3 root root   4096 Aug  5 19:22 2.6.15-26-386
drwxr-xr-x 19 root root   4096 Sep 11 16:54 ..
-rw-r--r--  1 root root 262144 Sep 14 07:11 ivtv-fw-enc.bin
-rw-r--r--  1 root root 262144 Sep 14 07:11 ivtv-fw-dec.bin
-r--r--r--  1 root root  14264 Sep 14 07:11 v4l-cx25840.fw
-r--r--r--  1 root root 376836 Sep 14 07:11 v4l-cx2341x-enc.fw
-rw-r--r--  1 root root 155648 Sep 14 07:11 v4l-cx2341x-init.mpg
lrwxrwxrwx  1 root root     28 Sep 14 07:12 v4l-cx2341x-dec.fw -> lib/firmware/ivtv-fw-dec.bin
drwxr-xr-x  3 root root   4096 Sep 14 07:12 .

```

I believe my firmware is in the proper directory but am getting this error.  Any suggestions?

---

### Post by NoahsMyBro on 2006-09-15
According to the forum, I wrote this 1 week ago. (Seems longer than that to me, but I'm flaky, so I'm likely wrong.) I've got a few updates, one which may help somebody down the line.

> **NoahsMyBro said:**
> 

System is:
 Ubuntu 6.06
 MySQL 5.0
 MythTV 19.5
 Motherboard is a Soyo K7VME - Integrated Unichrome graphics, no TV-Out.
 CPU = AMD Athlon XP 1Ghz. ACTUALLY PAID FOR SEMPRON 2300, a little PO'd about that.

[COLOR="Blue"]{UPDATE = My idiocy - FSB jumper was wrong on motherboard. Moved it from 100mhz to 166mhz, and CPU now IDs as Athlon XP 1900. COuld be the BIOS doesn't know about Sempron; in any case, the machine runs peppier now, so things are good here.}[/COLOR]

 RAM = 512Mb.
 Hauppauge PVR-150 with Remote Control


1) No TV-Out. If I pick up an inexpensive AGP videocard, what would I have to do to install it, and use it instead of the onboard graphics? How will this impact the currently installed and working MythTV install?

......1a) I'm seriously considering this card: [GIGABYTE GV-N52128DS Geforce FX5200 128MB DDR AGP 4X/8X Video Card]("http://www.newegg.com/Product/Product.asp?Item=N82E16814125191"). Once finished, the system will only be used for MythTV, and *maybe*, down the road, a little bit of MAME. No other gaming will be asked of the system. Any opinions on how well this card will work here? The only reason I'm looking to buy the card is to gain TV-Out, and watch the MythTV machine on a 27" JVC CRT, Standard Def TV.

[COLOR="Blue"]{UPDATE = NT4USB pointed out the lack of S-Video. I'm now looking for a GeForce FX5200, AGP card, with S-Video. Would any card meeting those specs do, or do I need to be wary of anything in particular? }[/COLOR]

2) Addition of a 2nd Tuner - The system has an Hauppauge PVR-150 tuner installed and working. The motherboard has only two PCI slots, with the Hauppauge occupying one. Now that I've got things working, I'd like to add a second tuner. I've got an Avermedia TV-M179 card waiting to be installed. Would it be fairly painless to install this second card and not break anything, using section 8.14 (adding a second PVR-150) of Hyams Home HOWTO as a guide?

[COLOR="Blue"]{UPDATE = NT4USB suggested the AverMedia card won't work with Myth. However, this page - [http://www.mythtv.org/wiki/index.php/AVerMedia_M179](http://www.mythtv.org/wiki/index.php/AVerMedia_M179) - indicates the card will work. Of course, I can't get it to work myself.

My motherboard has 2 PCI slots. The Hauppauge was in PCI slot 1. I added the M179 to slot 2. Changing nothing software-wise, I powered the machine back up, and ran Myth. NOW, the reception on the Hauppauge was noticeably worse - lots of snow in the picture - looked like I had gone from cable to rabbit-ears. Tried swapping the two cards in the slots. After this, I could not capture at all - any time I selected 'Watch TV', the screen blinked and stayed on the Myth menu. Tried re-running mythtv-setup and configuring the M179 - tried the Analog V4L, and the MPEG *-50 choices - still no joy. Removed the M179, leaving the Hauppauge in slot 2. Re-ran mythtv-setup, removed all capture cards and reconfigured the Hauppauge, now I can watch TV again, using the Hauppauge.

I'd like to add the M179 so I can record 2 programs simultaneously. Has anybody here gotten the M179 to work, and how? Thx. }

[/COLOR]
3) During the install (using the first post of this thread, and the Hyams Home HOWTO), somewhere along the way I broke MyPHPAdmin. 

[COLOR="Blue"]{UPDATE = I suppose I'll just try to completely uninstall, and then reinstall, this, and hope for the best. )[/COLOR]

4) MythGallery - I've copied a bunch of pictures from our home server to the directory I specified for MythGallery to use. Inadvertently, some of the files I copied were videos originally shot by my digital camera. (I think the digicam produces Quicktime format videos.) Whether a picture or a video, the thumbnails all display in MythGallery. If I view one of the videos, the video displays fine. If, however, I try to view a photo, all I see is a large white screen where the picture should display. I haven't found any reference at all to something like this via Google. Have any of you seen this, and do you know how I can fix it?

[COLOR="Blue"]{UPDATE = SOLVED!!! - Within Image Settings, I deselected 'Use OpenGL Transitions', and the images show correctly now. I'd think transitions only have to do with the 'transition' when moving from one image to the next during a slideshow, but hey, what do I know? ;) }

One related question (haven't checked the manual yet, maybe this is a dumb question) - any way to listen to music while watching a slideshow?
[/COLOR]

Thanks for any help you can offer,
Steve

---

### Post by detectiveinspekta on 2006-09-15
> **spirilis said:**
> Also up above you have an "ln" statement using
```

ln -s lib/firmware/ivtv-fw-dec.bin /lib/firmware/v4l-cx2341x-dec.fw

```

Think there needs to be a leading slash in front of that "lib/" -- without it ivtv reports errors on load.  (bad symlink so it can't find the decoder firmware)

ie
```

ln -s /lib/firmware/ivtv-fw-dec.bin /lib/firmware/v4l-cx2341x-dec.fw

```

---------------
I still need X on tv-out on my pvr-350

---

### Post by detectiveinspekta on 2006-09-15
The above is a solution to the firmware directory errors, if the sim-link shows up red.

---

### Post by Sureshot324 on 2006-09-17
I installed mythtv 0.18.1 from source on Dapper using these commands:

apt-get build-dep mythtv
# apt-get source mythtv --compile

It installed ok and I can watch TV, but it doesn't work with mysql.  When I run mythfilldatabase it gives me a bunch of SQL errors.  I later learned that MythTV 0.18.1 is incompatible with MySQL 5.

What I want to do is uninstall 0.18.1 and the install 0.20 from source.  However, since I installed 0.18.1 from source, I have to idea how to uninstall it.  'apt-get remove mythtv' doesn't work becuase it thinks myth is not installed.

Can anyone help me out?

---

### Post by scifan on 2006-09-17
Just finished updating my 0.19.1 box to 0.20... 

If you have interest, you can install from here:

deb [http://home.eng.iastate.edu/~superm1](http://home.eng.iastate.edu/~superm1) dapper main
deb-src [http://home.eng.iastate.edu/~superm1](http://home.eng.iastate.edu/~superm1) dapper main

Remove the old version prior to installing the new version...

(I had issue's with the lcd server package causing problems when trying to do an upgrade).

I installed just about everything, but found that I was experiencing a segfault when launching the frontend that was related to the phone module - which is required for mythplugins... 

mythweb seems to be happy... I did have to update the password stored in /etc/mythtv/mysql.txt to match the password in mysql (I pretty much just changed the password for the mythtv user in mysql).

It seems to be relatively happy now... :)

(Oh, and I should note that these fine gent's have both i386 and amd64 versions on this site).

---

### Post by fortytwo on 2006-09-18
Hey guys, I'm having a problem similar to NoahsMyBro before, but where his fix was to change out the coax cable, I know that mine is good.

I do not have MythTV installed yet, I'm trying to test ivtv, and after doing a capture with:
cat /dev/video0 > /tmp/test.mpg

I try to view the mpg with:
mplayer -vo xv /tmp/test.mpg

But I get this error:
vo: couldn't open the X11 display ()!
Error opening/initializing the selected video_out (-vo) device.

I tried changing the channel with:
ivtv-tune -c 11

And get:
/dev/video0: 199.250 MHz  (Signal Detected)

So I don't think that's the problem.  If I try to open the file directly with mplayer, it tells me I do not have an encoder to handle the file, maybe I'm just missing a codec or something?

Thanks for the help

UPDATE:
I just tried doing:
mplayer -vo xv /dev/video0
And I saw the channel just fine, does this mean that the capture is encoding the mpeg in some format I can't read?  Any idea how to fix this?

---

### Post by xboxer21 on 2006-09-19
> **fortytwo said:**
> Hey guys, I'm having a problem similar to NoahsMyBro before, but where his fix was to change out the coax cable, I know that mine is good.

I do not have MythTV installed yet, I'm trying to test ivtv, and after doing a capture with:
cat /dev/video0 > /tmp/test.mpg

I try to view the mpg with:
mplayer -vo xv /tmp/test.mpg

But I get this error:
vo: couldn't open the X11 display ()!
Error opening/initializing the selected video_out (-vo) device.

I tried changing the channel with:
ivtv-tune -c 11

And get:
/dev/video0: 199.250 MHz  (Signal Detected)

So I don't think that's the problem.  If I try to open the file directly with mplayer, it tells me I do not have an encoder to handle the file, maybe I'm just missing a codec or something?

Thanks for the help

UPDATE:
I just tried doing:
mplayer -vo xv /dev/video0
And I saw the channel just fine, does this mean that the capture is encoding the mpeg in some format I can't read?  Any idea how to fix this?

fortytwo, 
I had the same issue when I installed ivtv on a fresh install of ubuntu. The solution is to install all multimedia codecs. What I did was installed automatix from [www.getautomatix.com](www.getautomatix.com) and with the help of the automatix installer I installed all available codecs, after which I had no trouble playing any kind of audio/video formats.

Thanks

---

### Post by skattman83 on 2006-09-19
> **skattman83 said:**
> I was having a similar problem, I'm still trying to figure it out.  Try this: ```
sudo rmmod ivtv
sudo depmod
sudo modprobe ivtv tuner=50
dmesg
```

That will force ivtv to use a specific tuner.  If you check out /usr/src/ivtv*/driver/driver.h i think it is, you can see a listing of all of the choices for tuner numbers.  I have a newer pvr-150, and 50 worked for me.  The problem I'm running into is that you have to do this everytime you reboot though.

I found how to make this permanent if anyone is interested.  In your /etc/modprobe.d/aliases file, add "Options ivtv tuner=50" after the line about ivtv.  This will pass the option to the module when it gets loaded.  I read that the problem is that the card simply doesn't autodetect.

---

### Post by fortytwo on 2006-09-19
> **xboxer21 said:**
> fortytwo, 
I had the same issue when I installed ivtv on a fresh install of ubuntu. The solution is to install all multimedia codecs. What I did was installed automatix from [www.getautomatix.com](www.getautomatix.com) and with the help of the automatix installer I installed all available codecs, after which I had no trouble playing any kind of audio/video formats.

Thanks

This fixed the problem, thanks!

---

### Post by skattman83 on 2006-09-20
Has anyone else used kernel 2.6.15-26 or -27 with mythtv yet?  I can't get lirc working on those kernels, and I saw another thread somewhere here that other people were having problems using it.

---

### Post by NT4usB on 2006-09-20
> **skattman83 said:**
> Has anyone else used kernel 2.6.15-26 or -27 with mythtv yet?
Yes.
What version ivtv you trying to install?
0.4.4 worked for me.

---

### Post by skattman83 on 2006-09-20
> **NT4usB said:**
> Yes.
What version ivtv you trying to install?
0.4.4 worked for me.

I'm trying to install ivtv 0.4.6, and it works fine.  My issue is with lirc not working.  I am trying to get 0.8.0 working, but 0.7.2 (the one from the guide) does not work either.

---

### Post by NT4usB on 2006-09-20
oops... you did type lirc. guess I have ivtv on the brain since that's what lots of folks have trouble with.
iirc, I grabbed both 8.0 and 7.2... one because I couldn't get the other to work. Just don't remember which one I have running atm.
I'll look it up tonight and try to recall what troubles I had.
How far have you got with it? irw show anything when you push the buttons?

---

### Post by skattman83 on 2006-09-20
That's my problem, I dont get anything when i run irw and press buttons.  I saw something about blacklisting bttv and cx8800, but that didn't work either.

---

### Post by Royle on 2006-09-21
I've followed the guide and the changes but I get this: ```
root@mike-basement:/usr/src/ivtv-0.4.6/utils# mv /lib/modules/ivtv-fw-dec.bin /lib/firmware/
mv: cannot stat `/lib/modules/ivtv-fw-dec.bin': No such file or directory
```

Anyone know what I might have done wrong?  Thanks in advance for your help.

---

### Post by DSK on 2006-09-21
Hello all,
I installed ver 0.20 as suggested in a previous thread.  All works well for the most part.  I can run myth-setup and do a mythfilldatabase.

But when i get run mythfront end it starts up then kicks me back to desktop.  I am using a computer and not a tv.  Here is what is displayed in terminal when I am booted back to desktop

 mythfrontend
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
2006-09-21 14:42:35.368 Using runtime prefix = /usr
2006-09-21 14:42:35.387 Gnome-Screensaver support enabled
2006-09-21 14:42:35.394 DPMS is active.
2006-09-21 14:42:35.425 New DB connection, total: 1
2006-09-21 14:42:35.432 Connected to database 'mythconverg' at host: localhost
2006-09-21 14:42:35.435 Total desktop dim: 1024x768, with 2 screen[s].
2006-09-21 14:42:35.440 Using screen 0, 1024x768 at 0,0
2006-09-21 14:42:35.531 Current Schema Version: 1158
2006-09-21 14:42:35.531 mythfrontend version: 0.20.20060828-3 [www.mythtv.org](www.mythtv.org)
2006-09-21 14:42:35.532 Enabled verbose msgs:  important general
2006-09-21 14:42:35.907 Total desktop dim: 1024x768, with 2 screen[s].
2006-09-21 14:42:35.909 Using screen 0, 1024x768 at 0,0
2006-09-21 14:42:35.910 Switching to square mode (G.A.N.T.)
2006-09-21 14:42:35.929 Using the Qt painter
mythtv: could not connect to socket
mythtv: No such file or directory
lirc_init failed for 2006-09-21 14:42:36.324 Joystick disabled.
mythtv, see preceding messages
2006-09-21 14:42:36.915 Loading from: /usr/share/mythtv/themes/G.A.N.T./base.xml2006-09-21 14:42:36.999 Loading from: /usr/share/mythtv/themes/default/base.xml
2006-09-21 14:42:37.042 Registering Internal as a media playback plugin.
2006-09-21 14:42:37.089 Registering MythDVD DVD Media Handler as a media handler ext()
2006-09-21 14:42:37.090 Registering MythDVD VCD Media Handler as a media handler ext()
2006-09-21 14:42:37.125 Registering MythGallery Media Handler 1/2 as a media handler ext()
2006-09-21 14:42:37.125 Registering MythGallery Media Handler 2/2 as a media handler ext(gif,jpg,png)
Failed to run 'cdrecord --scanbus'
adding: ATA:0,0,0 -- DVDR   PX-708A
adding: ATA:1,0,0 -- DVD-ROM LTD-166S
adding: ATAPI:0,0,0 -- DVDR   PX-708A
2006-09-21 14:42:38.813 Registering MythMusic Media Handler 1/2 as a media handler ext()
2006-09-21 14:42:38.814 Registering MythMusic Media Handler 2/2 as a media handler ext(ogg,mp3,aac,flac)
Failed to find network interface eth0
SIP listening on IP Address :5060 NAT address
SIP: Cannot register; proxy, username or password not set
Destroying SipFsm object
libpng error: Read Error
Segmentation fault


any help would be greatly appreciated.

---

### Post by fortytwo on 2006-09-21
Hey guys,
I'm having some trouble when hooking up the machine to my Dish network cable box.

If I plug the coax from the wall directly into the machine, I can get the basic local channels (about 5 or 6).  Obviously, I want to get the rest of my channels, which I need to use my cable box for.  I hooked the coax from the wall into the cable box, and then went from the cable box to the machine but get only a black screen.  Is there anyone who has had a similar problem that can point me in the right direction or even has a suggested fix?

Thanks

---

### Post by lokimon on 2006-09-21
had a working 19.5 system running on ubuntu 6.06.1, for a few weeks now,
after a recent reboot, i stopped being able to hear any sound for recorded programs (although sound works great for all the other elements of mythtv - music, videos, dvd... and for some reason live tv watching seems to be broken as well.)

here's the error message:

```
2006-09-21 21:47:30.308 TV: Changing from WatchingPreRecorded to None
2006-09-21 21:47:30.425 Enable DPMS
0: start_time: 0.036 duration: 161.579
stream: start_time: 0.400 duration: 1795.327 bitrate=4800 kb/s
2006-09-21 21:47:30.515 AFD: Opened codec 0x8e09230, id(MPEG2VIDEO) type(Video)
2006-09-21 21:47:30.516 NVP: Disabling Audio, params(-1,-1,-1)
2006-09-21 21:47:30.516 NVP: Disabling Audio, params(0,-1,-1)
0: start_time: 0.036 duration: 161.579
stream: start_time: 0.400 duration: 1795.327 bitrate=4800 kb/s
2006-09-21 21:47:31.056 AFD: Opened codec 0x8d57e60, id(MPEG2VIDEO) type(Video)
2006-09-21 21:47:31.056 NVP: Disabling Audio, params(-1,-1,-1)
2006-09-21 21:47:31.056 NVP: Disabling Audio, params(0,-1,-1)
2006-09-21 21:47:33.476 TV: Attempting to change from None to WatchingLiveTV
2006-09-21 21:47:33.484 Using protocol version 26
2006-09-21 21:47:33.562 GetEntryAt(-1) failed.
2006-09-21 21:47:33.564 EntryToProgram(0@Wed Dec 31 19:00:00 1969) failed to get pginfo
2006-09-21 21:47:33.564 TV Error: LiveTV not successfully started
2006-09-21 21:47:33.564 TV Error: LiveTV not successfully started
2006-09-21 21:47:33.573 TV: Deleting TV Chain in destructor
2006-09-21 21:47:33.581 Disable DPMS
2006-09-21 21:47:33.581 Enable DPMS

```

---

### Post by lokimon on 2006-09-22
so, i have been beating my head against this overnight. hoping someone can clarify this for me. i'm sort of at a loss right now

here's what i seem to be seeing:

yesterday after a reboot, audio stopped working on recorded tv programs (no problems hearing audio from video files, dvd, music etc.)  perhaps unrelated, live tv stopped working, and my system stopped recording new programs. as an added bonus my LIRC stopped working as well.

i have been digging into this and it seems that my pvr-350 card is no longer being recognized at startup (no idea if this is related to the audio problem, although it sure explains why the remote isn't working, as i use the remote that came with this card.)

lspci doesn't see the pvr-350 at all (still sees my soundcard just fine though.)

i ran dmesg | grep PCI to try to pare down the dmesg output to something i can post here:

```
lokke@media:~$ dmesg | grep PCI
[17179569.184000] Allocating PCI resources starting at 60000000 (gap: 50000000:aec00000)
[17179571.584000] PCI: PCI BIOS revision 2.10 entry at 0xfb4f0, last bus=2
[17179571.584000] PCI: Using configuration type 1
[17179571.596000] ACPI: PCI Root Bridge [PCI0] (0000:00)
[17179571.596000] PCI: Probing PCI hardware (bus 00)
[17179571.604000] PCI: nForce2 C1 Halt Disconnect fixup
[17179571.604000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[17179571.716000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.HUB0._PRT]
[17179571.716000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.AGPB._PRT]
[17179571.720000] ACPI: PCI Interrupt Link [LNK1] (IRQs 3 4 5 6 7 10 *11 12 14 15)
[17179571.720000] ACPI: PCI Interrupt Link [LNK2] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[17179571.720000] ACPI: PCI Interrupt Link [LNK3] (IRQs 3 4 5 6 7 10 *11 12 14 15)
[17179571.720000] ACPI: PCI Interrupt Link [LNK4] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[17179571.720000] ACPI: PCI Interrupt Link [LNK5] (IRQs 3 4 *5 6 7 10 11 12 14 15)
[17179571.720000] ACPI: PCI Interrupt Link [LUBA] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[17179571.720000] ACPI: PCI Interrupt Link [LUBB] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[17179571.724000] ACPI: PCI Interrupt Link [LMAC] (IRQs 3 4 5 6 7 10 *11 12 14 15)
[17179571.724000] ACPI: PCI Interrupt Link [LAPU] (IRQs 3 4 *5 6 7 10 11 12 14 15)
[17179571.724000] ACPI: PCI Interrupt Link [LACI] (IRQs 3 4 *5 6 7 10 11 12 14 15)
[17179571.724000] ACPI: PCI Interrupt Link [LMCI] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[17179571.724000] ACPI: PCI Interrupt Link [LSMB] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[17179571.724000] ACPI: PCI Interrupt Link [LUB2] (IRQs 3 4 *5 6 7 10 11 12 14 15)
[17179571.724000] ACPI: PCI Interrupt Link [LFIR] (IRQs 3 4 5 6 7 10 *11 12 14 15)
[17179571.728000] ACPI: PCI Interrupt Link [L3CM] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[17179571.728000] ACPI: PCI Interrupt Link [LIDE] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[17179571.728000] ACPI: PCI Interrupt Link [APC1] (IRQs *16), disabled.
[17179571.728000] ACPI: PCI Interrupt Link [APC2] (IRQs *17), disabled.
[17179571.728000] ACPI: PCI Interrupt Link [APC3] (IRQs *18), disabled.
[17179571.728000] ACPI: PCI Interrupt Link [APC4] (IRQs *19), disabled.
[17179571.728000] ACPI: PCI Interrupt Link [APC5] (IRQs *16), disabled.
[17179571.732000] ACPI: PCI Interrupt Link [APCF] (IRQs 20 21 22) *0, disabled.
[17179571.732000] ACPI: PCI Interrupt Link [APCG] (IRQs 20 21 22) *0, disabled.
[17179571.732000] ACPI: PCI Interrupt Link [APCH] (IRQs 20 21 22) *0, disabled.
[17179571.732000] ACPI: PCI Interrupt Link [APCI] (IRQs 20 21 22) *0, disabled.
[17179571.732000] ACPI: PCI Interrupt Link [APCJ] (IRQs 20 21 22) *0, disabled.
[17179571.732000] ACPI: PCI Interrupt Link [APCK] (IRQs 20 21 22) *0, disabled.
[17179571.732000] ACPI: PCI Interrupt Link [APCS] (IRQs *23), disabled.
[17179571.736000] ACPI: PCI Interrupt Link [APCL] (IRQs 20 21 22) *0, disabled.
[17179571.736000] ACPI: PCI Interrupt Link [APCM] (IRQs 20 21 22) *0, disabled.
[17179571.736000] ACPI: PCI Interrupt Link [AP3C] (IRQs 20 21 22) *0, disabled.
[17179571.736000] ACPI: PCI Interrupt Link [APCZ] (IRQs 20 21 22) *0, disabled.
[17179571.752000] PCI: Using ACPI for IRQ routing
[17179571.752000] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[17179571.816000] PCI: Bridge: 0000:00:08.0
[17179571.816000] PCI: Bridge: 0000:00:1e.0
[17179571.816000] PCI: Setting latency timer of device 0000:00:08.0 to 64
[17179574.792000] NFORCE2: IDE controller at PCI slot 0000:00:09.0
[17179577.208000] ohci_hcd: 2005 April 22 USB 1.1 'Open' Host Controller (OHCI) Driver (PCI)
[17179577.260000] ACPI: PCI Interrupt Link [APCF] enabled at IRQ 22
[17179577.260000] ACPI: PCI Interrupt 0000:00:02.0[A] -> Link [APCF] -> GSI 22 (level, high) -> IRQ 177
[17179577.260000] PCI: Setting latency timer of device 0000:00:02.0 to 64
[17179577.420000] ACPI: PCI Interrupt Link [APCG] enabled at IRQ 21
[17179577.420000] ACPI: PCI Interrupt 0000:00:02.1[B] -> Link [APCG] -> GSI 21 (level, high) -> IRQ 185
[17179577.420000] PCI: Setting latency timer of device 0000:00:02.1 to 64
[17179577.580000] ACPI: PCI Interrupt Link [APCM] enabled at IRQ 20
[17179577.580000] ACPI: PCI Interrupt 0000:00:0d.0[A] -> Link [APCM] -> GSI 20 (level, high) -> IRQ 193
[17179577.580000] PCI: Setting latency timer of device 0000:00:0d.0 to 64
[17179577.632000] ACPI: PCI Interrupt Link [APCL] enabled at IRQ 22
[17179577.632000] ACPI: PCI Interrupt 0000:00:02.2[C] -> Link [APCL] -> GSI 22 (level, high) -> IRQ 177
[17179577.632000] PCI: Setting latency timer of device 0000:00:02.2 to 64
[17179577.632000] PCI: cache line size of 64 is not supported by device 0000:00:02.2
[17179577.636000] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[193]  MMIO=[e3084000-e30847ff]  Max Packet=[2048]
[17179588.412000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[17179588.416000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[17179588.852000] ACPI: PCI Interrupt Link [APCH] enabled at IRQ 21
[17179588.852000] ACPI: PCI Interrupt 0000:00:04.0[A] -> Link [APCH] -> GSI 21 (level, high) -> IRQ 185
[17179588.852000] PCI: Setting latency timer of device 0000:00:04.0 to 64
[17179589.372000] ACPI: PCI Interrupt Link [APCJ] enabled at IRQ 20
[17179589.372000] ACPI: PCI Interrupt 0000:00:06.0[A] -> Link [APCJ] -> GSI 20 (level, high) -> IRQ 193
[17179589.372000] PCI: Setting latency timer of device 0000:00:06.0 to 64
[17179589.696000] ACPI: PCI Interrupt Link [APC4] enabled at IRQ 19
[17179589.696000] ACPI: PCI Interrupt 0000:02:00.0[A] -> Link [APC4] -> GSI 19 (level, high) -> IRQ 201
[17179589.720000] ACPI: PCI Interrupt Link [APC3] enabled at IRQ 18
[17179589.720000] ACPI: PCI Interrupt 0000:01:06.0[A] -> Link [APC3] -> GSI 18 (level, high) -> IRQ 209

```

---

### Post by lokimon on 2006-09-22
ok, so i managed to fix this, but am a bit perplexed.

the PCI card not being recognized was due to a IRQ collision as far as i could tell.

one thing i neglected to mention was that after the sound problem came up, i went ahead and updated the system, which updated the kernel.

in doing this i created the problem with the PCI card not being recognized.

once i went back to my old kernel version: 2.6.15-26-686 the card was seen just fine.

the sound thing was solved with adjusting the general mythv settings to use /dev/dsp1 (this seems to be weird, cause sometimes at startup it seems to switch which number it assigns each device)

i seem to remember people having this problem with multiple tuner cards as well.

to add to the confusion, one of the recorded shows i captured came in with no sound, so it was a flawed test file, and once i started using an older recording with a known working audio track, the problem became easier to troubleshoot.

i hope this helps someone else.

i still want to know a couple things:

1) is the new kernel going to cause this IRQ issue when i eventually upgrade, or is there a way to solve this?

2) how can i make ubuntu assign /dev/dsp1 to my soundcard every time at boot?

---

### Post by skattman83 on 2006-09-22
I'm getting an error message when I try to run "make" on lirc-0.8.0 and lirc-0.7.2.  They are both the same error messages:```
make  all-recursive
make[1]: Entering directory `/usr/src/lirc-0.7.2'
Making all in drivers
make[2]: Entering directory `/usr/src/lirc-0.7.2/drivers'
Making all in lirc_dev
make[3]: Entering directory `/usr/src/lirc-0.7.2/drivers/lirc_dev'
mv Makefile Makefile.automake
cp ../Makefile.kernel Makefile
make -C /lib/modules/2.6.15-23-686/build/ SUBDIRS=/usr/src/lirc-0.7.2/drivers/lirc_dev modules \
                KBUILD_VERBOSE=1
make[4]: Entering directory `/usr/src/linux-source-2.6.15'
mkdir -p /usr/src/lirc-0.7.2/drivers/lirc_dev/.tmp_versions

  WARNING: Symbol version dump /usr/src/linux-source-2.6.15/Module.symvers
           is missing; modules will have no dependencies and modversions.

make -f scripts/Makefile.build obj=/usr/src/lirc-0.7.2/drivers/lirc_dev
  gcc -m32 -Wp,-MD,/usr/src/lirc-0.7.2/drivers/lirc_dev/.lirc_dev.o.d  -nostdinc -isystem /usr/lib/gcc/i486-linux-gnu/4.0.3/include -D__KERNEL__ -Iinclude  -include include/linux/autoconf.h -Wall -Wundef -Wstrict-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -ffreestanding -O2     -fomit-frame-pointer -pipe -msoft-float -mpreferred-stack-boundary=2 -fno-unit-at-a-time -march=i686 -Iinclude/asm-i386/mach-default -Wdeclaration-after-statement -Wno-pointer-sign -DIRCTL_DEV_MAJOR=61 -DEXPORT_SYMTAB -DHAVE_CONFIG_H -I. -I. -I../.. -I /usr/src/lirc-0.7.2/drivers/lirc_dev/../.. -I /lib/modules/2.6.15-23-686/build//include/  -DMODULE -DKBUILD_BASENAME=lirc_dev -DKBUILD_MODNAME=lirc_dev -c -o /usr/src/lirc-0.7.2/drivers/lirc_dev/.tmp_lirc_dev.o /usr/src/lirc-0.7.2/drivers/lirc_dev/lirc_dev.c
/usr/src/lirc-0.7.2/drivers/lirc_dev/lirc_dev.c: In function ‘lirc_register_plugin’:
/usr/src/lirc-0.7.2/drivers/lirc_dev/lirc_dev.c:386: warning: passing argument 2 of ‘class_device_create’ makes pointer from integer without a cast
/usr/src/lirc-0.7.2/drivers/lirc_dev/lirc_dev.c:386: warning: passing argument 3 of ‘class_device_create’ makes integer from pointer without a cast
/usr/src/lirc-0.7.2/drivers/lirc_dev/lirc_dev.c:386: warning: passing argument 4 of ‘class_device_create’ from incompatible pointer type
/usr/src/lirc-0.7.2/drivers/lirc_dev/lirc_dev.c:386: warning: passing argument 5 of ‘class_device_create’ makes pointer from integer without a cast
  Building modules, stage 2.
make -rR -f /usr/src/linux-source-2.6.15/scripts/Makefile.modpost
  scripts/mod/modpost -m -a -i /usr/src/linux-source-2.6.15/Module.symvers /usr/src/lirc-0.7.2/drivers/lirc_dev/lirc_dev.o
  gcc -m32 -Wp,-MD,/usr/src/lirc-0.7.2/drivers/lirc_dev/.lirc_dev.mod.o.d  -nostdinc -isystem /usr/lib/gcc/i486-linux-gnu/4.0.3/include -D__KERNEL__ -Iinclude -include include/linux/autoconf.h -Wall -Wundef -Wstrict-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -ffreestanding -O2     -fomit-frame-pointer -pipe -msoft-float -mpreferred-stack-boundary=2 -fno-unit-at-a-time -march=i686 -Iinclude/asm-i386/mach-default -Wdeclaration-after-statement -Wno-pointer-sign    -DKBUILD_BASENAME=lirc_dev -DKBUILD_MODNAME=lirc_dev -DMODULE -c -o /usr/src/lirc-0.7.2/drivers/lirc_dev/lirc_dev.mod.o /usr/src/lirc-0.7.2/drivers/lirc_dev/lirc_dev.mod.c
  ld -m elf_i386 -m elf_i386 -r -o /usr/src/lirc-0.7.2/drivers/lirc_dev/lirc_dev.ko /usr/src/lirc-0.7.2/drivers/lirc_dev/lirc_dev.o /usr/src/lirc-0.7.2/drivers/lirc_dev/lirc_dev.mod.o
make[4]: Leaving directory `/usr/src/linux-source-2.6.15'
mv Makefile.automake Makefile
make[3]: Leaving directory `/usr/src/lirc-0.7.2/drivers/lirc_dev'
Making all in lirc_i2c
make[3]: Entering directory `/usr/src/lirc-0.7.2/drivers/lirc_i2c'
mv Makefile Makefile.automake
cp ../Makefile.kernel Makefile
make -C /lib/modules/2.6.15-23-686/build/ SUBDIRS=/usr/src/lirc-0.7.2/drivers/lirc_i2c modules \
                KBUILD_VERBOSE=1
make[4]: Entering directory `/usr/src/linux-source-2.6.15'
mkdir -p /usr/src/lirc-0.7.2/drivers/lirc_i2c/.tmp_versions

  WARNING: Symbol version dump /usr/src/linux-source-2.6.15/Module.symvers
           is missing; modules will have no dependencies and modversions.

make -f scripts/Makefile.build obj=/usr/src/lirc-0.7.2/drivers/lirc_i2c
  gcc -m32 -Wp,-MD,/usr/src/lirc-0.7.2/drivers/lirc_i2c/.lirc_i2c.o.d  -nostdinc -isystem /usr/lib/gcc/i486-linux-gnu/4.0.3/include -D__KERNEL__ -Iinclude  -include include/linux/autoconf.h -Wall -Wundef -Wstrict-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -ffreestanding -O2     -fomit-frame-pointer -pipe -msoft-float -mpreferred-stack-boundary=2 -fno-unit-at-a-time -march=i686 -Iinclude/asm-i386/mach-default -Wdeclaration-after-statement -Wno-pointer-sign -DIRCTL_DEV_MAJOR=61 -DEXPORT_SYMTAB -DHAVE_CONFIG_H -I. -I. -I../.. -I /usr/src/lirc-0.7.2/drivers/lirc_i2c/../.. -I /lib/modules/2.6.15-23-686/build//include/  -DMODULE -DKBUILD_BASENAME=lirc_i2c -DKBUILD_MODNAME=lirc_i2c -c -o /usr/src/lirc-0.7.2/drivers/lirc_i2c/.tmp_lirc_i2c.o /usr/src/lirc-0.7.2/drivers/lirc_i2c/lirc_i2c.c
In file included from include/linux/rcuref.h:36,
                 from include/linux/fs.h:12,
                 from /usr/src/lirc-0.7.2/drivers/lirc_i2c/../../drivers/lirc_dev/lirc_dev.h:24,
                 from /usr/src/lirc-0.7.2/drivers/lirc_i2c/lirc_i2c.c:58:
include/linux/interrupt.h:31: error: conflicting types for ‘irqreturn_t’
/usr/src/lirc-0.7.2/drivers/lirc_i2c/../../drivers/kcompat.h:166: error: previous declaration of ‘irqreturn_t’ was here
In file included from include/linux/rcuref.h:36,
                 from include/linux/fs.h:12,
                 from /usr/src/lirc-0.7.2/drivers/lirc_i2c/../../drivers/lirc_dev/lirc_dev.h:24,
                 from /usr/src/lirc-0.7.2/drivers/lirc_i2c/lirc_i2c.c:58:
include/linux/interrupt.h:33:1: warning: "IRQ_NONE" redefined
In file included from /usr/src/lirc-0.7.2/drivers/lirc_i2c/lirc_i2c.c:57:
/usr/src/lirc-0.7.2/drivers/lirc_i2c/../../drivers/kcompat.h:167:1: warning: this is the location of the previous definition
In file included from include/linux/rcuref.h:36,
                 from include/linux/fs.h:12,
                 from /usr/src/lirc-0.7.2/drivers/lirc_i2c/../../drivers/lirc_dev/lirc_dev.h:24,
                 from /usr/src/lirc-0.7.2/drivers/lirc_i2c/lirc_i2c.c:58:
include/linux/interrupt.h:34:1: warning: "IRQ_HANDLED" redefined
In file included from /usr/src/lirc-0.7.2/drivers/lirc_i2c/lirc_i2c.c:57:
/usr/src/lirc-0.7.2/drivers/lirc_i2c/../../drivers/kcompat.h:168:1: warning: this is the location of the previous definition
In file included from include/linux/rcuref.h:36,
                 from include/linux/fs.h:12,
                 from /usr/src/lirc-0.7.2/drivers/lirc_i2c/../../drivers/lirc_dev/lirc_dev.h:24,
                 from /usr/src/lirc-0.7.2/drivers/lirc_i2c/lirc_i2c.c:58:
include/linux/interrupt.h:35:1: warning: "IRQ_RETVAL" redefined
In file included from /usr/src/lirc-0.7.2/drivers/lirc_i2c/lirc_i2c.c:57:
/usr/src/lirc-0.7.2/drivers/lirc_i2c/../../drivers/kcompat.h:169:1: warning: this is the location of the previous definition
/usr/src/lirc-0.7.2/drivers/lirc_i2c/lirc_i2c.c: In function ‘ir_attach’:
/usr/src/lirc-0.7.2/drivers/lirc_i2c/lirc_i2c.c:426: error: ‘I2C_ALGO_BIT’ undeclared (first use in this function)
/usr/src/lirc-0.7.2/drivers/lirc_i2c/lirc_i2c.c:426: error: (Each undeclared identifier is reported only once
/usr/src/lirc-0.7.2/drivers/lirc_i2c/lirc_i2c.c:426: error: for each function it appears in.)
/usr/src/lirc-0.7.2/drivers/lirc_i2c/lirc_i2c.c: In function ‘ir_probe’:
/usr/src/lirc-0.7.2/drivers/lirc_i2c/lirc_i2c.c:506: error: ‘I2C_ALGO_BIT’ undeclared (first use in this function)
make[5]: *** [/usr/src/lirc-0.7.2/drivers/lirc_i2c/lirc_i2c.o] Error 1
make[4]: *** [_module_/usr/src/lirc-0.7.2/drivers/lirc_i2c] Error 2
make[4]: Leaving directory `/usr/src/linux-source-2.6.15'
make[3]: *** [lirc_i2c.o] Error 2
make[3]: Leaving directory `/usr/src/lirc-0.7.2/drivers/lirc_i2c'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/usr/src/lirc-0.7.2/drivers'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/usr/src/lirc-0.7.2'
make: *** [all] Error 2

```

I am trying to do this on a fresh dapper install.  I did all of the updates, and set up the build environment as listed in hyam's guide.  I did not install IVTV though.  Is it possible that is my problem?

---

### Post by GemaRastem on 2006-09-23
> **DSK said:**
> Hello all,
I installed ver 0.20 as suggested in a previous thread.  All works well for the most part.  I can run myth-setup and do a mythfilldatabase.

But when i get run mythfront end it starts up then kicks me back to desktop.  I am using a computer and not a tv.  Here is what is displayed in terminal when I am booted back to desktop

 mythfrontend
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
2006-09-21 14:42:35.368 Using runtime prefix = /usr
2006-09-21 14:42:35.387 Gnome-Screensaver support enabled
2006-09-21 14:42:35.394 DPMS is active.
2006-09-21 14:42:35.425 New DB connection, total: 1
2006-09-21 14:42:35.432 Connected to database 'mythconverg' at host: localhost
2006-09-21 14:42:35.435 Total desktop dim: 1024x768, with 2 screen[s].
2006-09-21 14:42:35.440 Using screen 0, 1024x768 at 0,0
2006-09-21 14:42:35.531 Current Schema Version: 1158
2006-09-21 14:42:35.531 mythfrontend version: 0.20.20060828-3 [www.mythtv.org](www.mythtv.org)
2006-09-21 14:42:35.532 Enabled verbose msgs:  important general
2006-09-21 14:42:35.907 Total desktop dim: 1024x768, with 2 screen[s].
2006-09-21 14:42:35.909 Using screen 0, 1024x768 at 0,0
2006-09-21 14:42:35.910 Switching to square mode (G.A.N.T.)
2006-09-21 14:42:35.929 Using the Qt painter
mythtv: could not connect to socket
mythtv: No such file or directory
lirc_init failed for 2006-09-21 14:42:36.324 Joystick disabled.
mythtv, see preceding messages
2006-09-21 14:42:36.915 Loading from: /usr/share/mythtv/themes/G.A.N.T./base.xml2006-09-21 14:42:36.999 Loading from: /usr/share/mythtv/themes/default/base.xml
2006-09-21 14:42:37.042 Registering Internal as a media playback plugin.
2006-09-21 14:42:37.089 Registering MythDVD DVD Media Handler as a media handler ext()
2006-09-21 14:42:37.090 Registering MythDVD VCD Media Handler as a media handler ext()
2006-09-21 14:42:37.125 Registering MythGallery Media Handler 1/2 as a media handler ext()
2006-09-21 14:42:37.125 Registering MythGallery Media Handler 2/2 as a media handler ext(gif,jpg,png)
Failed to run 'cdrecord --scanbus'
adding: ATA:0,0,0 -- DVDR   PX-708A
adding: ATA:1,0,0 -- DVD-ROM LTD-166S
adding: ATAPI:0,0,0 -- DVDR   PX-708A
2006-09-21 14:42:38.813 Registering MythMusic Media Handler 1/2 as a media handler ext()
2006-09-21 14:42:38.814 Registering MythMusic Media Handler 2/2 as a media handler ext(ogg,mp3,aac,flac)
Failed to find network interface eth0
SIP listening on IP Address :5060 NAT address
SIP: Cannot register; proxy, username or password not set
Destroying SipFsm object
libpng error: Read Error
Segmentation fault


any help would be greatly appreciated.


I am getting this same error, has anybody figured out why?

---

### Post by GemaRastem on 2006-09-23
> **DSK said:**
> Hello all,
I installed ver 0.20 as suggested in a previous thread.  All works well for the most part.  I can run myth-setup and do a mythfilldatabase.

But when i get run mythfront end it starts up then kicks me back to desktop.  I am using a computer and not a tv.  Here is what is displayed in terminal when I am booted back to desktop

 mythfrontend
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
2006-09-21 14:42:35.368 Using runtime prefix = /usr
2006-09-21 14:42:35.387 Gnome-Screensaver support enabled
2006-09-21 14:42:35.394 DPMS is active.
2006-09-21 14:42:35.425 New DB connection, total: 1
2006-09-21 14:42:35.432 Connected to database 'mythconverg' at host: localhost
2006-09-21 14:42:35.435 Total desktop dim: 1024x768, with 2 screen[s].
2006-09-21 14:42:35.440 Using screen 0, 1024x768 at 0,0
2006-09-21 14:42:35.531 Current Schema Version: 1158
2006-09-21 14:42:35.531 mythfrontend version: 0.20.20060828-3 [www.mythtv.org](www.mythtv.org)
2006-09-21 14:42:35.532 Enabled verbose msgs:  important general
2006-09-21 14:42:35.907 Total desktop dim: 1024x768, with 2 screen[s].
2006-09-21 14:42:35.909 Using screen 0, 1024x768 at 0,0
2006-09-21 14:42:35.910 Switching to square mode (G.A.N.T.)
2006-09-21 14:42:35.929 Using the Qt painter
mythtv: could not connect to socket
mythtv: No such file or directory
lirc_init failed for 2006-09-21 14:42:36.324 Joystick disabled.
mythtv, see preceding messages
2006-09-21 14:42:36.915 Loading from: /usr/share/mythtv/themes/G.A.N.T./base.xml2006-09-21 14:42:36.999 Loading from: /usr/share/mythtv/themes/default/base.xml
2006-09-21 14:42:37.042 Registering Internal as a media playback plugin.
2006-09-21 14:42:37.089 Registering MythDVD DVD Media Handler as a media handler ext()
2006-09-21 14:42:37.090 Registering MythDVD VCD Media Handler as a media handler ext()
2006-09-21 14:42:37.125 Registering MythGallery Media Handler 1/2 as a media handler ext()
2006-09-21 14:42:37.125 Registering MythGallery Media Handler 2/2 as a media handler ext(gif,jpg,png)
Failed to run 'cdrecord --scanbus'
adding: ATA:0,0,0 -- DVDR   PX-708A
adding: ATA:1,0,0 -- DVD-ROM LTD-166S
adding: ATAPI:0,0,0 -- DVDR   PX-708A
2006-09-21 14:42:38.813 Registering MythMusic Media Handler 1/2 as a media handler ext()
2006-09-21 14:42:38.814 Registering MythMusic Media Handler 2/2 as a media handler ext(ogg,mp3,aac,flac)
Failed to find network interface eth0
SIP listening on IP Address :5060 NAT address
SIP: Cannot register; proxy, username or password not set
Destroying SipFsm object
libpng error: Read Error
Segmentation fault


any help would be greatly appreciated.

> **GemaRastem said:**
> I am getting this same error, has anybody figured out why?


I just figured it out. you have to go into system>preferences>remote desktop and set a password to it, I used my mysql password

---

### Post by xolot1 on 2006-09-23
at the step at which i configure the database by visiting localhost with firefox, i can see that there are two directories
[DIR] apache2-default/        26-Jul-2006 13:50    -   
[DIR] phpmyadmin/             29-Aug-2006 21:05    -   

but when i click on phpmyadmin, firefox downloads a .phtml file, instead of browsing the directory. how can i fix this?


willi

---

### Post by zenkoanlife on 2006-09-23
> **xolot1 said:**
> at the step at which i configure the database by visiting localhost with firefox, i can see that there are two directories
[DIR] apache2-default/        26-Jul-2006 13:50    -   
[DIR] phpmyadmin/             29-Aug-2006 21:05    -   

but when i click on phpmyadmin, firefox downloads a .phtml file, instead of browsing the directory. how can i fix this?


willi

I had the same problem. Do you have this package installed... libapache2-mod-php5 ?  if not do this
```
apt-get install libapache2-mod-php5
```

hope this helps.

---

### Post by theolster on 2006-09-28
Hi - I'm trying to update my mythtv and [www.parker1.co.uk]("http://www.parker1.co.uk/mythtv_0.20.php") says to add:
> # Mythtv 0.19
deb [http://knm.org/mythdebs/](http://knm.org/mythdebs/) binary/
deb-src [http://knm.org/mythdebs/](http://knm.org/mythdebs/) source/
to the apt sources.list.  I've also noticed that others in the forum have been using this repo too.  However, this doesn't work and the stucture of the repo seems to have been changed, does anyone have any idea what the sources file should be amended to?

Cheers

---

### Post by neptune39 on 2006-09-28
So I have MythTV 0.2 running on my server and I am purely controlling it through Mythweb. After lots of messing around, especially with the uk radio time grab, I have it working and it is great.

I am not going to use the frontend, I want to use lots of frontends, e.g MCE2005, apple front row etc. I want anyone to be able to play the files while on my network. One problem I have is the filenames being the way they are, I would like to be able to see them as something more readable from say Windows. I have read about mythrename.py but cant find any useful info on its use or where to get it. I'm sure what I want to do is easy but I just can't seem to find it. Any Ideas?

Cheers

---

### Post by dodongo on 2006-09-29
> **neptune39 said:**
> So I have MythTV 0.2 running on my server and I am purely controlling it through Mythweb. After lots of messing around, especially with the uk radio time grab, I have it working and it is great.

I am not going to use the frontend, I want to use lots of frontends, e.g MCE2005, apple front row etc. I want anyone to be able to play the files while on my network. One problem I have is the filenames being the way they are, I would like to be able to see them as something more readable from say Windows. I have read about mythrename.py but cant find any useful info on its use or where to get it. I'm sure what I want to do is easy but I just can't seem to find it. Any Ideas?

Cheers

You can find it [here]("http://www.floppy.org.uk/stuff/mythtv/")!  At least, I think that's what you're looking for.

Also (and I apologize if this is totally pedantic), but you're actually using mythtv .20 in all likelihood.  That trailing zero indicates that it's the 20th revision of the 0 version of mythtv...  so the ordering goes .17, .18, .19, .20 which != .2 (which would've been only the second revision).

Happy renaming!

---

### Post by soaro77 on 2006-10-01
> **GemaRastem said:**
> I just figured it out. you have to go into system>preferences>remote desktop and set a password to it, I used my mysql password

> **DSK said:**
> Hello all,
I installed ver 0.20 as suggested in a previous thread.  All works well for the most part.  I can run myth-setup and do a mythfilldatabase.

But when i get run mythfront end it starts up then kicks me back to desktop.  I am using a computer and not a tv.  Here is what is displayed in terminal when I am booted back to desktop

 mythfrontend
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
2006-09-21 14:42:35.368 Using runtime prefix = /usr
2006-09-21 14:42:35.387 Gnome-Screensaver support enabled
2006-09-21 14:42:35.394 DPMS is active.
2006-09-21 14:42:35.425 New DB connection, total: 1
2006-09-21 14:42:35.432 Connected to database 'mythconverg' at host: localhost
2006-09-21 14:42:35.435 Total desktop dim: 1024x768, with 2 screen[s].
2006-09-21 14:42:35.440 Using screen 0, 1024x768 at 0,0
2006-09-21 14:42:35.531 Current Schema Version: 1158
2006-09-21 14:42:35.531 mythfrontend version: 0.20.20060828-3 [www.mythtv.org](www.mythtv.org)
2006-09-21 14:42:35.532 Enabled verbose msgs:  important general
2006-09-21 14:42:35.907 Total desktop dim: 1024x768, with 2 screen[s].
2006-09-21 14:42:35.909 Using screen 0, 1024x768 at 0,0
2006-09-21 14:42:35.910 Switching to square mode (G.A.N.T.)
2006-09-21 14:42:35.929 Using the Qt painter
mythtv: could not connect to socket
mythtv: No such file or directory
lirc_init failed for 2006-09-21 14:42:36.324 Joystick disabled.
mythtv, see preceding messages
2006-09-21 14:42:36.915 Loading from: /usr/share/mythtv/themes/G.A.N.T./base.xml2006-09-21 14:42:36.999 Loading from: /usr/share/mythtv/themes/default/base.xml
2006-09-21 14:42:37.042 Registering Internal as a media playback plugin.
2006-09-21 14:42:37.089 Registering MythDVD DVD Media Handler as a media handler ext()
2006-09-21 14:42:37.090 Registering MythDVD VCD Media Handler as a media handler ext()
2006-09-21 14:42:37.125 Registering MythGallery Media Handler 1/2 as a media handler ext()
2006-09-21 14:42:37.125 Registering MythGallery Media Handler 2/2 as a media handler ext(gif,jpg,png)
Failed to run 'cdrecord --scanbus'
adding: ATA:0,0,0 -- DVDR   PX-708A
adding: ATA:1,0,0 -- DVD-ROM LTD-166S
adding: ATAPI:0,0,0 -- DVDR   PX-708A
2006-09-21 14:42:38.813 Registering MythMusic Media Handler 1/2 as a media handler ext()
2006-09-21 14:42:38.814 Registering MythMusic Media Handler 2/2 as a media handler ext(ogg,mp3,aac,flac)
Failed to find network interface eth0
SIP listening on IP Address :5060 NAT address
SIP: Cannot register; proxy, username or password not set
Destroying SipFsm object
libpng error: Read Error
Segmentation fault


any help would be greatly appreciated.


Has anyone figured out an answer to this question? The suggestion about turning on remote desktop doesn't work. I am having this exact same problem and have been fighting getting MythTV setup now for 2 days and my patience is wearing very thin with it. It just really should not be this difficult. I would really appreciate any help anyone might have as to what is causing this.

---

### Post by soaro77 on 2006-10-01
> **soaro77 said:**
> Has anyone figured out an answer to this question? The suggestion about turning on remote desktop doesn't work. I am having this exact same problem and have been fighting getting MythTV setup now for 2 days and my patience is wearing very thin with it. It just really should not be this difficult. I would really appreciate any help anyone might have as to what is causing this.

For anyone who wants or needs to know, I found the answer to this. It appears there is some sort of bug or problem with MythPhone. If you remove that it fixes this problem. Once I removed MythPhone it started up just fine.

---

### Post by jr06compmaster on 2006-10-05
I used the step by step guide to install mythtv on Ubuntu 6.06 and everything seemed to work fine until it came time to fill the database. One of the first things in the guide was to setup mysql and make sure you can login by typing localhost in the address bar in firefox and going into phpmyadmin. That worked fine for me and I changed the password for root as instructed. Logged back in again and it was fine. Finished the guide down to filling the database and it came up with

"DB Error (Inserting into dd_schedule). Database error was: You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near 'repeat, stereo, subtitled, hdtv, closecaptioned, tvrating, partnumber, parttotal, endtim' at line 1."

I tried putting localhost into the address bar and sure enough, I can't get into phpmyadmin. It says "cannot load mysql extention. Please check your PHP configuration.

Anyone have any ideas?

---

### Post by NT4usB on 2006-10-05
> **jr06compmaster said:**
> I used the step by step guide to install mythtv on Ubuntu 6.06 and everything seemed to work fine until it came time to fill the database. One of the first things in the guide was to setup mysql and make sure you can login by typing localhost in the address bar in firefox and going into phpmyadmin. That worked fine for me and I changed the password for root as instructed. Logged back in again and it was fine. Finished the guide down to filling the database and it came up with

"DB Error (Inserting into dd_schedule). Database error was: You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near 'repeat, stereo, subtitled, hdtv, closecaptioned, tvrating, partnumber, parttotal, endtim' at line 1."

I tried putting localhost into the address bar and sure enough, I can't get into phpmyadmin. It says "cannot load mysql extention. Please check your PHP configuration.

Anyone have any ideas?

This looks to be the compatability issue with mysql (or was it phpmyadmin?) and mythtv.
myth 0.18 won't work with the current mysql. either install an older version or install myth 0.19.
search the forums. plenty discussion on the subject.
[http://www.google.com/search?hl=en&q=site%3Aubuntuforums.org+mysql+mythtv+repeat&btnG=Google+Search]("http://www.google.com/search?hl=en&q=site%3Aubuntuforums.org+mysql+mythtv+repeat&btnG=Google+Search")
[http://ubuntuforums.org/showpost.php?p=1553506&postcount=3]("http://ubuntuforums.org/showpost.php?p=1553506&postcount=3")
etc...

---

### Post by jr06compmaster on 2006-10-05
Ok i'm trying to use the guide to upgrade from .18 to .19 then; it says to unpack the 3 install files in /opt/src.  I didn't have an src file so I made one, but it won't let me extract the files there it says I don't have permissions and it won't let me change the permissions.  What is going on?

---

### Post by NT4usB on 2006-10-05
> **jr06compmaster said:**
> Ok i'm trying to use the guide to upgrade from .18 to .19 then; it says to unpack the 3 install files in /opt/src.  I didn't have an src file so I made one, but it won't let me extract the files there it says I don't have permissions and it won't let me change the permissions.  What is going on?

You can get 0.19 right from the repositories.

Add these to your sources.list:
deb [http://knm.org/mythdebs/](http://knm.org/mythdebs/) binary/
deb-src [http://knm.org/mythdebs/](http://knm.org/mythdebs/) source/
Then install 19-5 via synaptic.
Fix the issue with mythmusic by installing libcdaudio0 from the 5.10 repos. Then pin it so it doesn't get updated.

---

### Post by dannysauer on 2006-10-05
> **jr06compmaster said:**
> Ok i'm trying to use the guide to upgrade from .18 to .19 then; it says to unpack the 3 install files in /opt/src.  I didn't have an src file so I made one, but it won't let me extract the files there it says I don't have permissions and it won't let me change the permissions.  What is going on?

Man, that sounds like a pain.

0.20 is in edgy, which went beta recently.  Last night, I installed the 0.20 packages from edgy on my dapper boxes.  It's pretty easy, but I don't guarantee against any stability problems.  Here's what I did:

First, do an apt-get update; apt-get upgrade so you're up-to-date on dapper.

Then, edit /etc/apt/sources.list, adding these lines at the bottom:

```

#edgy stuff
deb http://us.archive.ubuntu.com/ubuntu edgy main restricted universe multiverse
deb http://security.ubuntu.com/ubuntu edgy-updates main restricted universe multiverse
deb http://security.ubuntu.com/ubuntu edgy-security main restricted universe multiverse
```

Run apt-get update again, to pull down the etch repository info.

Then, edit /etc/apt/preferences like so (you'll probably be creating the file):

```

Package: *
Pin: release a=dapper
Pin-Priority: 500

Package: *
Pin: release a=edgy
Pin-Priority: 1

Package: myth*
Pin: release a=edgy
Pin-Priority: 991
```

Look at man apt_preferences to explain that...

Anyway, now you can install the myth packages and it'll pull down the deps from etch as needed.  Install as normal, except add "-t edgy" to the apt-get line to make sure it pulls down from that repository.  To set up a bakckend machine, for example:

```
sudo apt-get -t edgy install mythtv-backend
```

Bang, pow!  You're sticking the "not guaranteed stable, but seems to work so far" edgy myth and a few other parts on your "used to be stable, but now, who knows" Dapper box, without going full-on Edgy.  You may want to change the edgy priority from 1 to -1 and/or the dapper priority from 500 to 990 so as to avoid accidentally getting more Edgy packages installed after you have myth set up, but that stuff *should* be pretty well tested at this point, AFAIK.  Like I said, I haven't had any problems in the few days since doing that, but that's no guarantee that will be true for you. :twisted:

---

### Post by jr06compmaster on 2006-10-05
ok you guys are awesome, im going to give the first one a try tomorrow and if it doesn't work try the .20.  Thanks guys!

---

### Post by jr06compmaster on 2006-10-06
0.19 did not work.  Those sources are bad i believe and they give me an error.  Wikipedia also confirms that these sources no longer work.  Unless I just typed them in wrong or something dumb but i don't think so.

---

### Post by NT4usB on 2006-10-06
> **jr06compmaster said:**
> 0.19 did not work.  Those sources are bad i believe and they give me an error.  Wikipedia also confirms that these sources no longer work.  Unless I just typed them in wrong or something dumb but i don't think so.

krap. it looks like they've been moved or deleted.
if I knew how to do it, I probably could post the ones I used to install... but I don't have a clue.

---

### Post by jr06compmaster on 2006-10-06
Ok 0.2 works, but I can't get my remote set up (I followed the setup [http://www.mythtv.org/wiki/index.php/Lirc_on_Ubuntu_Dapper](http://www.mythtv.org/wiki/index.php/Lirc_on_Ubuntu_Dapper).)  I got down through the testing, it registered me pressing buttons.  When I got to where it says mv /etc/lircmd.conf /etc/lirc/, I don't have a folder named /etc/lirc/ so it can't copy it.  Running irw gives me a permission error I believe, but not being able to move those files can't be good.  You guys have been so helpful I hope I can get this last problem resolved.

---

### Post by NT4usB on 2006-10-06
> **jr06compmaster said:**
> Ok 0.2 works, but I can't get my remote set up (I followed the setup [http://www.mythtv.org/wiki/index.php/Lirc_on_Ubuntu_Dapper](http://www.mythtv.org/wiki/index.php/Lirc_on_Ubuntu_Dapper).)  I got down through the testing, it registered me pressing buttons.  When I got to where it says mv /etc/lircmd.conf /etc/lirc/, I don't have a folder named /etc/lirc/ so it can't copy it.  Running irw gives me a permission error I believe, but not being able to move those files can't be good.  You guys have been so helpful I hope I can get this last problem resolved.

That guide is doing things I don't understand.
I used Hyam's guide and it worked perfectly. Just remember to type the version you have where the guide has lirc-0.7.2.
[http://hyams.webhop.net/mythtv/myth_ubuntu.htm](http://hyams.webhop.net/mythtv/myth_ubuntu.htm)

---

### Post by jr06compmaster on 2006-10-07
It doesn't let me save the file there, it says it could not be saved because you cannot change the contents of the folder.  I know its something with the permissions but I don't know what to do.  Thats why I tried that other guide.

---

### Post by NT4usB on 2006-10-07
> **jr06compmaster said:**
> It doesn't let me save the file there, it says it could not be saved because you cannot change the contents of the folder.  I know its something with the permissions but I don't know what to do.  Thats why I tried that other guide.

Were you logged in as root or using sudo with the commands?

Hyam has you log into root in the beginning of the guide:
```
sudo -i
```

Good and bad I think. 
I was never really sure how to get out of sudo -i and some of the things had to be done as mythtv or the permissions got jacked.

btw, found this guide. looks interesting...
[http://parker1.co.uk/mythtv_ubuntu.php](http://parker1.co.uk/mythtv_ubuntu.php)

---

### Post by jr06compmaster on 2006-10-08
I realize im suppose to log in as root, but thats only for the terminal window right?  The guide instructs to save the file in the usr/src folder or w/e which doesn't involve the terminal at all.  Or maybe im just missing something.

---

### Post by dodongo on 2006-10-09
I apologize if this is dreadfully offtopic, but I suspect a lot of people in this thread will be upgrading to Edgy over the next month or two.

I have upgraded to the Edgy beta, and I can confirm that the new Mythtv 0.20 packages + php5 + ivtv-0.7.x series drivers works just fine following the instructions early in this thread.  It doesn't appear that any changes have taken place which would affect the instructions for installing, other than version numbers (note the new ivtv version on account of the 2.6.17 kernel).

I used the upgrader software to move up, and I have to say when you're ready, come on in -- the water's fine!

---

### Post by NoahsMyBro on 2006-10-09
Over the last couple of months I've got a pretty good MythTV/Dapper system going, with much help from this forum/thread. (Thanks, BTW!) It's not perfect, but the remaining problmes are minor.

I'd like to be able to burn DVDs of recorded programs, though. I'd especially like it if I can do this on DVD-RWs, and re-use them after viewing the shows.

A) How easy/difficult/risky would it be to upgrade from Myth 0.19 to 0.20? The Mythtv wiki makes it sound brain-dead simple, but I'm still nervous and haven't made the move yet.

B) Assuming I took the plunge and leapt to 0.20, would I give anything up, functionality-wise?

---

### Post by dodongo on 2006-10-09
> **NoahsMyBro said:**
> A) How easy/difficult/risky would it be to upgrade from Myth 0.19 to 0.20? The Mythtv wiki makes it sound brain-dead simple, but I'm still nervous and haven't made the move yet.

B) Assuming I took the plunge and leapt to 0.20, would I give anything up, functionality-wise?

My upgrade to 0.20 included the transition to Edgy.  The *only* myth-related thing I had to change was recompiling the ivtv drivers against the new kernel source.  If you're grabbing mythtv 0.20 off a site that's got it compiled for Dapper, then I would imagine you're well within the "brain-dead simple" zone.

If there are any feature regressions in mythtv 0.20, I can't find 'em.

---

### Post by jr06compmaster on 2006-10-10
Could someone please tell me what im doing wrong?  When installing LIRC 0.8.0 i get down to the point in the guide where it tells me to chmod 666 /dev/lircd.  This gives me the message cannot access:  No such file or directory because it doesn't exist!  Why don't I have this file here where I need it?

---

### Post by NT4usB on 2006-10-10
> **jr06compmaster said:**
> Could someone please tell me what im doing wrong?  When installing LIRC 0.8.0 i get down to the point in the guide where it tells me to chmod 666 /dev/lircd.  This gives me the message cannot access:  No such file or directory because it doesn't exist!  Why don't I have this file here where I need it?

Do you know where the file/folder is? Is it even installed?
I can't tell you the correct way to solve it. I can tell you how I would go about it...
```
sudo updatedb
```
```
locate lirc*
```
Look at the paths and figure out where it's at.
```
cd /to/wherever/its/at/
```
```
sudo chmod 666 *
```
or some other variation on the theme. Not sure if I got the chmod syntax correct...
ymmv.

---

### Post by jr06compmaster on 2006-10-10
The lirc file is there, but the guide says to chmod into lircd.  That is the file that I can't find; its definately not there ive lsed and looked around for it.  When does that file get created?  If I knew that then I would know where the problem began.

---

### Post by NT4usB on 2006-10-10
> **jr06compmaster said:**
> The lirc file is there, but the guide says to chmod into lircd.  That is the file that I can't find; its definately not there ive lsed and looked around for it.  When does that file get created?  If I knew that then I would know where the problem began.
Not in front of my myth box to check it atm, but is lircd a file(s) not a folder..?
ed: so I looked it up. From man lircd:
OPTIONS
       The   --permission   option   gives  the  file  permission  of
       /dev/lircd if it has to be created  in  octal  representation.
       Read  the  documentation  for chmod for further details. If no
       --permission option is given when the socket is initially cre-
       ated  the  default is to give all users read and write permis-
       sions (0666 in octal representation).  If  /dev/lircd  already
       exists this option has no effect.

so, what is the permissions of your lircd?
```
ls -al lircd
```
I'll bet it's already srw-rw-rw- 1 root root 
If not, looks like you have to use the --permission   option

---

### Post by MonolithTMA on 2006-10-16
First of all, thanks for putting these instructions together.

I'm running into a problem.

OK, when I get to the point where I type:

```
depmod
```

I get:

```
WARNING: Module /lib/modules/2.6.15-27-powerpc-smp/madwifi-ng/new_ath_pci.ko ignored, due to loop
WARNING: Module /lib/modules/2.6.15-27-powerpc-smp/madwifi-ng/new_ath_rate_sample.ko ignored, due to loop
WARNING: Loop detected: /lib/modules/2.6.15-27-powerpc-smp/volatile/new_ath_hal.ko which needs new_ath_hal.ko again!
WARNING: Module /lib/modules/2.6.15-27-powerpc-smp/volatile/new_ath_hal.ko ignored, due to loop


```

I did lots of google searching, I even tried other search engines, which I seldom do, and I didn't find anything helpful.

I'm guessing it's some issue with my kernel version.

Any ideas? :-k

Thanks in advance! :)

Update: I installed Dapper from scratch last night and we'll see what happens when I try to install IVTV and MythTV again. After doing much searching, I'm pretty sure the above warnings have nothing to do with IVTV.

---

### Post by MonolithTMA on 2006-10-20
Did a total reinstall of Dapper and started from scratch. Exact same problems. I give up...for now.

In case someone is curious this is the total depmod IVTV output:

[ 6283.005194] ivtv:  ==================== START INIT IVTV ====================

[ 6283.005206] ivtv:  version 0.4.4 (tagged release) loading

[ 6283.005210] ivtv:  Linux version: 2.6.15-26-powerpc gcc-4.0

[ 6283.005213] ivtv:  In case of problems please include the debug info between

[ 6283.005217] ivtv:  the START INIT IVTV and END INIT IVTV lines, along with

[ 6283.005221] ivtv:  any module options, when mailing the ivtv-users mailinglis t.

[ 6283.006591] ivtv0: Autodetected WinTV PVR 250 card (cx23415 based)

[ 6283.006808] PCI: Enabling device 0001:10:12.0 (0004 -> 0006)

[ 6283.006928] ivtv0: Unreasonably low latency timer, setting to 64 (was 16)

[ 6283.041984] tveeprom: ivtv version

[ 6283.041993] tveeprom: Hauppauge: model = 48011, rev = G510, serial# = 2651099

[ 6283.041998] tveeprom: tuner = Philips FI1236 MK2 (idx = 10, type = 2)

[ 6283.042003] tveeprom: tuner fmt = NTSC(M) (eeprom = 0x08, v4l2 = 0x00001000)

[ 6283.042007] tveeprom: audio processor = MSP3435 (type = a)

[ 6283.042011] tveeprom: decoder processor = SAA7115 (type = 13)

[ 6283.042017] ivtv0: i2c attach to card #0 ok [client=tveeprom, addr=50]

[ 6283.072792] tuner (ivtv): chip found at addr 0xc2 i2c-bus ivtv i2c driver #0

[ 6283.072807] ivtv0: i2c attach to card #0 ok [client=(tuner unset), addr=61]

[ 6283.217010] saa7115 7-0021: saa7115 found @ 0x42 (ivtv i2c driver #0)

[ 6283.303407] ivtv0: i2c attach to card #0 ok [client=saa7115, addr=21]

[ 6283.362948] msp3400 7-0040: chip=MSP3435G-B6 +nicam +simple +simpler +radio m ode=simpler

[ 6283.363004] msp3400 7-0040: msp34xxg daemon started

[ 6283.376877] ivtv0: i2c attach to card #0 ok [client=MSP3435G-B6, addr=40]

[ 6284.122592] ivtv0: loaded v4l-cx2341x-enc.fw firmware (262144 bytes)

[ 6284.130119] ivtv0: unable to open firmware v4l-cx2341x-dec.fw

[ 6284.130130] ivtv0: did you put the firmware in the hotplug firmware directory ?

[ 6284.130135] ivtv0 warning: failed loading decoder firmware

[ 6284.130140] ivtv0 warning: Error loading firmware -1!

[ 6284.130144] ivtv0: Error -1 initializing firmware.

[ 6284.136219] ivtv0: Error -12 on initialization

[ 6284.136230] ivtv: probe of 0001:10:12.0 failed with error -12

[ 6284.137471] ivtv:  ====================  END INIT IVTV  ====================

---

### Post by Juzz on 2006-10-21
Where did you put the firmware?
Is it readable in the permissions?

From your output it seems that the firmware is either not readable or is placed in a wrong directory:

```
[ 6284.130119] ivtv0: unable to open firmware v4l-cx2341x-dec.fw

[ 6284.130130] ivtv0: did you put the firmware in the hotplug firmware directory ?
```

By the way, this:

```
WARNING: Module /lib/modules/2.6.15-27-powerpc-smp/madwifi-ng/new_ath_pci.ko ignored, due to loop
WARNING: Module /lib/modules/2.6.15-27-powerpc-smp/madwifi-ng/new_ath_rate_sample.ko ignored, due to loop
WARNING: Loop detected: /lib/modules/2.6.15-27-powerpc-smp/volatile/new_ath_hal.ko which needs new_ath_hal.ko again!
WARNING: Module /lib/modules/2.6.15-27-powerpc-smp/volatile/new_ath_hal.ko ignored, due to loop
```
Is related to the Atheros chipset code - AKA a wireless driver, which is delivered in the restricted modules.

---

### Post by MonolithTMA on 2006-10-21
Thanks for the reply. Yeah, I figured out that those warnings were about wireless.

Dapper Drake does not have a hotplug directory, so the firmware goes into /lib/firmware.

Here is the output of ls -ltra /lib/firmware/

drwxr-xr-x  3 root root   4096 2006-10-19 01:23 2.6.15-26-powerpc

drwxr-xr-x  3 root root   4096 2006-10-19 01:23 2.6.15-27-powerpc

drwxr-xr-x 17 root root   4096 2006-10-20 22:13 ..

-rw-r--r--  1 root root 262144 2006-10-20 23:45 ivtv-fw-enc.bin

-rw-r--r--  1 root root 262144 2006-10-20 23:45 ivtv-fw-dec.bin

-r--r--r--  1 root root  14264 2006-10-20 23:45 v4l-cx25840.fw

-r--r--r--  1 root root 376836 2006-10-20 23:45 v4l-cx2341x-enc.fw

-rw-r--r--  1 root root 155648 2006-10-20 23:46 v4l-cx2341x-init.mpg

lrwxrwxrwx  1 root root     28 2006-10-20 23:46 v4l-cx2341x-dec.fw -> lib/firmwa re/ivtv-fw-dec.bin

drwxr-xr-x  4 root root   4096 2006-10-20 23:46 .

All the permissions seem to be set properly.

I'm not sure why it shows the 2.6.15-26-powerpc and 2.6.15-27-powerpc directories. Hyams' output from [http://hyams.webhop.net/mythtv/myth_ubuntu.html](http://hyams.webhop.net/mythtv/myth_ubuntu.html) doesn't show that, but then he's using Breezy Badger in his example.

When I do uname -r I get 2.6.15-**26**-powerpc I'm not sure why it seems to have the 2.6.15-**27**-powerpc kernel too.

---

### Post by Juzz on 2006-10-23
Take a look at you /boot directory and check out which kernel is lying there.

My own Myth box is running dapper drake (however that's an 686), but I can check it's dirs in the afternoon when I get home from school.

---

### Post by MonolithTMA on 2006-10-23
Hmmm...it looks like both 26 and 27 are there.

ls /boot

abi-2.6.15-26-powerpc         initrd.img-2.6.15-27-powerpc

abi-2.6.15-27-powerpc         System.map-2.6.15-26-powerpc

config-2.6.15-26-powerpc      System.map-2.6.15-27-powerpc

config-2.6.15-27-powerpc      vmlinux

initrd.img                    vmlinux-2.6.15-26-powerpc

initrd.img-2.6.15-26-powerpc  vmlinux-2.6.15-27-powerpc

---

### Post by Juzz on 2006-10-23
What boot method are you using?

It's been a while since I have used PPC linux - is it yaboot or what?

---

### Post by MonolithTMA on 2006-10-23
It's yaboot.

I'm told in this thread:

[http://ubuntuforums.org/showthread.php?t=282725](http://ubuntuforums.org/showthread.php?t=282725)

that I can choose either kernel at the GRUB menu, so I'm guessing that the multiple kernels are not the problem.

---

### Post by Juzz on 2006-10-23
I honestly can't remember much from the time I ran PPC Linux, but I do remember that Yaboot boots the kernel not grub...

However it has been quite a while...

---

### Post by dodongo on 2006-10-23
I find when there's a problem with the decoder firmware like that, I've symlinked something into the wrong location.  Maybe double-check the instructions at the beginning of this thread, where it mentions how Dapper requires a different location than previous versions?  (Though, to be fair, it sounds like you're already aware of this change)

> Hmmm...it looks like both 26 and 27 are there.

So far as I know, which kernel you're running shouldn't be a problem, since you're dealing with a revision of a sub-minor release (e.g., 2.6.15.XX).  There should be no changes at that level which break drivers.

I would just go back to /lib/firmware and confirm that things are in the right places.

---

### Post by trubblemaker on 2006-11-01
> **MonolithTMA said:**
> 

[ 6284.130119] ivtv0: unable to open firmware v4l-cx2341x-dec.fw

[ 6284.130130] ivtv0: did you put the firmware in the hotplug firmware directory ?

[ 6284.130135] ivtv0 warning: failed loading decoder firmware

[ 6284.130140] ivtv0 warning: Error loading firmware -1!

[ 6284.130144] ivtv0: Error -1 initializing firmware.

[ 6284.136219] ivtv0: Error -12 on initialization

[ 6284.136230] ivtv: probe of 0001:10:12.0 failed with error -12

[ 6284.137471] ivtv:  ====================  END INIT IVTV  ====================

try this
```

cd /lib/firmware
cp ivtv-fw-dec.bin v4l-cx2341x-dec.fw

``` 
it got me farther down the line

---

### Post by sandy_m on 2006-11-05
Thanks for the great tutorial!
I'm trying to get my PVR-500 going on a clean Edgy install (6.06 would not install on my older machine for some reason).
I followed all tutorial steps, with two exceptions: I didn't install gcc3.4 (as more recent version installed) and I used ivtv 0.7 as my kernel is 2.6.17.

Everything went fine and I'm now stuck at step 5.3 (verification of ivtv drivers). Mplayer displays only a static blue screen (tested both videos on the PVR-500). The coax cable is fine. I'm in Australia and I tried althepcman's suggestion:

> ivtv-tune -t australia -c 40 -d /dev/video0

Channel 40 gets me Channel 9/Win tv

Without much luck. I'm hesitating to move on to Myth installation before this is fixed. I would appreciate and help.
Here is my dmesg:

```
...
[   68.142088] Linux video capture interface: v1.00
[   68.258650] ivtv: no version for "struct_module" found: kernel tainted.
[   68.274621] ivtv:  ==================== START INIT IVTV ====================
[   68.274643] ivtv:  version 0.7.1 (tagged release) loading
[   68.274656] ivtv:  Linux version: 2.6.17-10-generic SMP mod_unload 586 REGPARM gcc-4.1
[   68.274671] ivtv:  In case of problems please include the debug info between
[   68.274684] ivtv:  the START INIT IVTV and END INIT IVTV lines, along with
[   68.274698] ivtv:  any module options, when mailing the ivtv-users mailinglist.
[   68.275008] ivtv0: Autodetected Hauppauge WinTV PVR-150 card (cx23416 based)
[   68.275180] ivtv0: Unreasonably low latency timer, setting to 64 (was 32)
[   68.366684] tveeprom 1-0050: Hauppauge model 23559, rev D591, serial# 7964846
[   68.366708] tveeprom 1-0050: tuner model is Philips FQ1216AME MK4 (idx 91, type 56)
[   68.366729] tveeprom 1-0050: TV standards PAL(B/G) PAL(I) SECAM(L/L') PAL(D/D1/K) (eeprom 0x74)
[   68.366751] tveeprom 1-0050: second tuner model is Philips TEA5768HL FM Radio (idx 101, type 62)
[   68.366770] tveeprom 1-0050: audio processor is CX25843 (idx 37)
[   68.366786] tveeprom 1-0050: decoder processor is CX25843 (idx 30)
[   68.366801] tveeprom 1-0050: has radio, has no IR remote
[   68.366815] ivtv0: This is the first unit of a PVR500
[   68.514907] tuner 1-0060: TEA5767 detected.
[   68.514926] tuner 1-0060: chip found @ 0xc0 (ivtv i2c driver #0)
[   68.515046] tuner 1-0060: type set to 62 (Philips TEA5767HN FM Radio)
[   68.515304] tuner 1-0061: chip found @ 0xc2 (ivtv i2c driver #0)
[   68.756437] tda9887 1-0043: chip found @ 0x86 (ivtv i2c driver #0)
[   68.855383] cx25840 1-0044: cx25843-23 found @ 0x88 (ivtv i2c driver #0)
[   69.831245] pnp: Device 01:01.01 activated.
[   69.848425] gameport: NS558 PnP Gameport is pnp01:01.01/gameport0, io 0x200, speed 701kHz
[   70.127204] input: PC Speaker as /class/input/input2
[   71.234257] eth0: link down
[   74.221626] NET: Registered protocol family 17
[   74.992828] ts: Compaq touchscreen protocol output
[   75.141478] cx25840 1-0044: loaded v4l-cx25840.fw firmware (14264 bytes)
[   75.293479] wm8775 1-001b: chip found @ 0x36 (ivtv i2c driver #0)
[   76.593432] ivtv0: loaded v4l-cx2341x-enc.fw firmware (262144 bytes)
[   76.806218] ivtv0: Encoder revision: 0x02050032
[   76.807048] ivtv0: Allocate DMA encoder MPEG stream: 128 x 32768 buffers (4096KB total)
[   76.808663] ivtv0: Allocate DMA encoder YUV stream: 161 x 12960 buffers (2048KB total)
[   76.810150] ivtv0: Allocate DMA encoder VBI stream: 80 x 26208 buffers (2048KB total)
[   76.811368] ivtv0: Allocate DMA encoder PCM audio stream: 455 x 4608 buffers (2048KB total)
[   76.814252] ivtv0: Create encoder radio stream
[   76.814411] tuner 1-0061: type set to 56 (Philips PAL/SECAM multi (FQ1216AME MK4))
[   76.939829] ivtv0: Initialized WinTV PVR 500 (unit #1), card #0
[   76.940076] ivtv:  ======================  NEXT CARD  ======================
[   76.940100] ivtv1: Autodetected Hauppauge WinTV PVR-150 card (cx23416 based)
[   76.940305] ivtv1: Unreasonably low latency timer, setting to 64 (was 32)
[   76.990791] tuner 2-0061: chip found @ 0xc2 (ivtv i2c driver #1)
[   77.151732] tda9887 2-0043: chip found @ 0x86 (ivtv i2c driver #1)
[   77.167782] cx25840 2-0044: cx25843-23 found @ 0x88 (ivtv i2c driver #1)
[   80.208365] cx25840 2-0044: loaded v4l-cx25840.fw firmware (14264 bytes)
[   80.282292] wm8775 2-001b: chip found @ 0x36 (ivtv i2c driver #1)
[   80.388358] tveeprom 2-0050: Hauppauge model 23559, rev D591, serial# 7964846
[   80.388381] tveeprom 2-0050: tuner model is Philips FQ1216AME MK4 (idx 91, type 56)
[   80.388402] tveeprom 2-0050: TV standards PAL(B/G) PAL(I) SECAM(L/L') PAL(D/D1/K) (eeprom 0x74)
[   80.388424] tveeprom 2-0050: second tuner model is Philips TEA5768HL FM Radio (idx 101, type 62)
[   80.388443] tveeprom 2-0050: audio processor is CX25843 (idx 37)
[   80.388458] tveeprom 2-0050: decoder processor is CX25843 (idx 30)
[   80.388474] tveeprom 2-0050: has radio, has no IR remote
[   80.388487] ivtv1: This is the second unit of a PVR500
[   80.388500] ivtv1: Correcting tveeprom data: no radio present on second unit
[   81.388942] ivtv1: loaded v4l-cx2341x-enc.fw firmware (262144 bytes)
[   81.604720] ivtv1: Encoder revision: 0x02050032
[   81.605610] ivtv1: Allocate DMA encoder MPEG stream: 128 x 32768 buffers (4096KB total)
[   81.607290] ivtv1: Allocate DMA encoder YUV stream: 161 x 12960 buffers (2048KB total)
[   81.608975] ivtv1: Allocate DMA encoder VBI stream: 80 x 26208 buffers (2048KB total)
[   81.610236] ivtv1: Allocate DMA encoder PCM audio stream: 455 x 4608 buffers (2048KB total)
[   81.612524] tuner 2-0061: type set to 56 (Philips PAL/SECAM multi (FQ1216AME MK4))
[   81.736500] ivtv1: Initialized WinTV PVR 500 (unit #2), card #1
[   81.736556] ivtv:  ====================  END INIT IVTV  ====================
...
[  793.233056] ivtv-enc: page allocation failure. order:4, mode:0xd0
[  793.233115]  <c0151552> __alloc_pages+0x202/0x330  <c0166ec2> cache_alloc_refill+0x322/0x540
[  793.233242]  <c0167154> __kmalloc+0x74/0x90  <cca86344> ivtv_init_buffer+0x44/0x1e0 [ivtv]
[  793.233395]  <cca86d4c> enc_gather_free_buffers+0x9c/0x230 [ivtv]  <c011cdf8> __wake_up+0x38/0x50
[  793.233593]  <cca95530> ivtv_sched_DMA+0x480/0xa2a [ivtv]  <c01e0542> __next_cpu+0x12/0x20
[  793.233691]  <c011b22d> find_busiest_group+0xcd/0x2f0  <c011bde0> default_wake_function+0x0/0x10
[  793.233845]  <cca99dbf> ivtv_enc_thread+0x1af/0x220 [ivtv]  <c0102f06> ret_from_fork+0x6/0x20
[  793.233940]  <cca99c10> ivtv_enc_thread+0x0/0x220 [ivtv]  <c0136180> autoremove_wake_function+0x0/0x50
[  793.234083]  <cca99c10> ivtv_enc_thread+0x0/0x220 [ivtv]  <c0101005> kernel_thread_helper+0x5/0x10
[  793.234184] Mem-info:
[  793.234194] DMA per-cpu:
[  793.234208] cpu 0 hot: high 0, batch 1 used:0
[  793.234221] cpu 0 cold: high 0, batch 1 used:0
[  793.234233] DMA32 per-cpu: empty
[  793.234243] Normal per-cpu:
[  793.234257] cpu 0 hot: high 42, batch 7 used:40
[  793.234270] cpu 0 cold: high 14, batch 3 used:12
[  793.234281] HighMem per-cpu: empty
[  793.234299] Free pages:        4032kB (0kB HighMem)
[  793.234321] Active:28659 inactive:2995 dirty:1288 writeback:0 unstable:0 free:1008 slab:13520 mapped:28222 pagetables:413
[  793.234348] DMA free:868kB min:144kB low:180kB high:216kB active:9648kB inactive:96kB present:16384kB pages_scanned:67 all_unreclaimable? no
[  793.234367] lowmem_reserve[]: 0 0 175 175
[  793.234393] DMA32 free:0kB min:0kB low:0kB high:0kB active:0kB inactive:0kB present:0kB pages_scanned:0 all_unreclaimable? no
[  793.234410] lowmem_reserve[]: 0 0 175 175
[  793.234440] Normal free:3164kB min:1624kB low:2028kB high:2436kB active:104988kB inactive:11884kB present:180212kB pages_scanned:142 all_unreclaimable? no
[  793.234531] lowmem_reserve[]: 0 0 0 0
[  793.234556] HighMem free:0kB min:128kB low:128kB high:128kB active:0kB inactive:0kB present:0kB pages_scanned:0 all_unreclaimable? no
[  793.234574] lowmem_reserve[]: 0 0 0 0
[  793.234592] DMA: 63*4kB 13*8kB 0*16kB 0*32kB 0*64kB 0*128kB 0*256kB 1*512kB 0*1024kB 0*2048kB 0*4096kB = 868kB
[  793.234641] DMA32: empty
[  793.234651] Normal: 497*4kB 89*8kB 15*16kB 1*32kB 1*64kB 1*128kB 0*256kB 0*512kB 0*1024kB 0*2048kB 0*4096kB = 3164kB
[  793.234700] HighMem: empty
[  793.234717] Swap cache: add 16197, delete 15424, find 337/533, race 0+0
[  793.234731] Free swap  = 961616kB
[  793.234741] Total swap = 1020088kB
[  793.234752] Free swap:       961616kB
[  793.246982] 49149 pages of RAM
[  793.246996] 0 pages of HIGHMEM
[  793.247006] 1411 reserved pages
[  793.247016] 45767 pages shared
[  793.247025] 773 pages swap cached
[  793.247037] 1288 pages dirty
[  793.247046] 0 pages writeback
[  793.247056] 28222 pages mapped
[  793.247065] 13520 pages slab
[  793.247074] 413 pages pagetables
[  793.247091] ivtv0 warning: No memory on buffer alloc!
[  793.247112] ivtv0 warning: Needed 47104 bufs for encoder MPEG stream, received 32768 (buffers free 0, dma 0, full 153)
[ 1003.230124] ivtv-enc: page allocation failure. order:4, mode:0xd0
[ 1003.230251]  <c0151552> __alloc_pages+0x202/0x330  <c0166ec2> cache_alloc_refill+0x322/0x540
[ 1003.230379]  <c0167154> __kmalloc+0x74/0x90  <cca86344> ivtv_init_buffer+0x44/0x1e0 [ivtv]
[ 1003.230531]  <cca86d4c> enc_gather_free_buffers+0x9c/0x230 [ivtv]  <c011cdf8> __wake_up+0x38/0x50
[ 1003.230657]  <cca95530> ivtv_sched_DMA+0x480/0xa2a [ivtv]  <c01e0542> __next_cpu+0x12/0x20
[ 1003.230755]  <c011b22d> find_busiest_group+0xcd/0x2f0  <c011bde0> default_wake_function+0x0/0x10
[ 1003.230909]  <cca99dbf> ivtv_enc_thread+0x1af/0x220 [ivtv]  <c0102f06> ret_from_fork+0x6/0x20
[ 1003.231004]  <cca99c10> ivtv_enc_thread+0x0/0x220 [ivtv]  <c0136180> autoremove_wake_function+0x0/0x50
[ 1003.231117]  <cca99c10> ivtv_enc_thread+0x0/0x220 [ivtv]  <c0101005> kernel_thread_helper+0x5/0x10
[ 1003.231288] Mem-info:
[ 1003.231298] DMA per-cpu:
[ 1003.231312] cpu 0 hot: high 0, batch 1 used:0
[ 1003.231326] cpu 0 cold: high 0, batch 1 used:0
[ 1003.231337] DMA32 per-cpu: empty
[ 1003.231348] Normal per-cpu:
[ 1003.231362] cpu 0 hot: high 42, batch 7 used:38
[ 1003.231375] cpu 0 cold: high 14, batch 3 used:12
[ 1003.231387] HighMem per-cpu: empty
[ 1003.231404] Free pages:        9644kB (0kB HighMem)
[ 1003.231426] Active:28881 inactive:2320 dirty:1 writeback:0 unstable:0 free:2411 slab:12587 mapped:29018 pagetables:404
[ 1003.231454] DMA free:1744kB min:144kB low:180kB high:216kB active:8572kB inactive:488kB present:16384kB pages_scanned:37 all_unreclaimable? no
[ 1003.231473] lowmem_reserve[]: 0 0 175 175
[ 1003.231498] DMA32 free:0kB min:0kB low:0kB high:0kB active:0kB inactive:0kB present:0kB pages_scanned:0 all_unreclaimable? no
[ 1003.231516] lowmem_reserve[]: 0 0 175 175
[ 1003.231546] Normal free:7900kB min:1624kB low:2028kB high:2436kB active:106952kB inactive:8792kB present:180212kB pages_scanned:145 all_unreclaimable? no
[ 1003.231566] lowmem_reserve[]: 0 0 0 0
[ 1003.231591] HighMem free:0kB min:128kB low:128kB high:128kB active:0kB inactive:0kB present:0kB pages_scanned:0 all_unreclaimable? no
[ 1003.231609] lowmem_reserve[]: 0 0 0 0
[ 1003.231626] DMA: 252*4kB 50*8kB 9*16kB 4*32kB 1*64kB 0*128kB 0*256kB 0*512kB 0*1024kB 0*2048kB 0*4096kB = 1744kB
[ 1003.231676] DMA32: empty
[ 1003.231686] Normal: 581*4kB 453*8kB 98*16kB 8*32kB 0*64kB 1*128kB 0*256kB 0*512kB 0*1024kB 0*2048kB 0*4096kB = 7900kB
[ 1003.231736] HighMem: empty
[ 1003.231752] Swap cache: add 16926, delete 16052, find 506/804, race 0+0
[ 1003.231766] Free swap  = 961372kB
[ 1003.231777] Total swap = 1020088kB
[ 1003.231787] Free swap:       961372kB
[ 1003.243835] 49149 pages of RAM
[ 1003.243917] 0 pages of HIGHMEM
[ 1003.243927] 1411 reserved pages
[ 1003.243937] 46011 pages shared
[ 1003.243947] 874 pages swap cached
[ 1003.243958] 1 pages dirty
[ 1003.243967] 0 pages writeback
[ 1003.243976] 29018 pages mapped
[ 1003.243986] 12587 pages slab
[ 1003.243995] 404 pages pagetables
[ 1003.244011] ivtv1 warning: No memory on buffer alloc!
[ 1003.244032] ivtv1 warning: Needed 47104 bufs for encoder MPEG stream, received 32768 (buffers free 0, dma 0, full 135)
```

---

### Post by trubblemaker on 2006-11-05
Had a similar issue a while ago don't remeber if it's dont remember if it was the exact error but it's got something to due with allocating space for the kernel at boot time, I recall having to add something to  cat /boot/grub/menu.lst at the end of the line (boot paramerters) and it worked....

but know I used the wiki howto so I don't need that added to my boot, anymore and hence don't have an example to post, but I hope that I'm pointing you in the right direction.

---

### Post by lokimon on 2006-11-07
i don't know if anyone else has pointed this out in this thread, but if you update to a newer version of the kernel, you will have to re-install anything you had to compile specifically for the kernel.

in my case this was the full ivtv and lirc setups, but i imagine that on more complex systems this could be a big task.

am i wrong about this, could i have done this an easier way? or was this a "DUH, you should have known that" thing?

---

### Post by trubblemaker on 2006-11-07
nah your on the money a complete reinstall from source every time. next time yuo have to check for the howto on the ubuntu wiki, it's got an easy install and a script to make the recompile really easy.  sorry don't know where the link to the howto is I'm on my windows box.

---

### Post by sandy_m on 2006-11-08
Thanks trubblemaker, I followed your advice and found something to eliminate the memory problem. Just in case somebody else has the same issue: [http://ubuntuforums.org/showthread.php?t=181857]("http://ubuntuforums.org/showthread.php?t=181857")

Despite the error gone, I still only get a static blue when I try ivtv. Any ideas what I could check next?

Thanks,

Sandy

---

### Post by trubblemaker on 2006-11-08
I can't find the link now but you might need to tune you card depending if it's on pal or ntsc, their are some howto's on that I can' find any book marked ones kicking around but I saw them.... here check [this page ]("http://ivtv.writeme.ch/tiki-index.php?page=TvOutHowto")out might not solve it but help you out a bit it talks about tuning the card, for tvout, but might help you tune the card to your correct settings.

---

### Post by sandy_m on 2006-11-11
Thanks once again trubblemaker for pointing me in the right direction.
I eventually ended up with this very helpful site, which might be interesting for all Edgy users: [https://wiki.ubuntu.com/Install_IVTV_Edgy]("https://wiki.ubuntu.com/Install_IVTV_Edgy")

I still ended up with a static picture, but was finally able to resolve it. This was caused by wrong ivtv-tune parameters.

mplayer -vo xv /dev/video0   only gave me the static picture
mplayer -vo x11 /dev/video0  resulted in a random picture (similar to a TV that hasn't been tuned)

ivtv-tune -t australia -c XYZ -d /dev/video0
gave me a proper picture, where I substituted XYZ with 46, 49, 52, 55, 58, 61, 64 or 67 for Australian TV channels.

I'll now embark on installing MythTV.
Thanks once again,

Sandy

---

### Post by superm1 on 2006-11-12
> **sandy_m said:**
> Thanks once again trubblemaker for pointing me in the right direction.
I eventually ended up with this very helpful site, which might be interesting for all Edgy users: [https://wiki.ubuntu.com/Install_IVTV_Edgy](https://wiki.ubuntu.com/Install_IVTV_Edgy)

I still ended up with a static picture, but was finally able to resolve it. This was caused by wrong ivtv-tune parameters.

mplayer -vo xv /dev/video0   only gave me the static picture
mplayer -vo x11 /dev/video0  resulted in a random picture (similar to a TV that hasn't been tuned)

ivtv-tune -t australia -c XYZ -d /dev/video0
gave me a proper picture, where I substituted XYZ with 46, 49, 52, 55, 58, 61, 64 or 67 for Australian TV channels.

I'll now embark on installing MythTV.
Thanks once again,

Sandy
Sandy, if your on edgy and getting started with myth, checkout the wiki page for it for edgy.

[http://help.ubuntu.com/community/MythTV](http://help.ubuntu.com/community/MythTV)

---

### Post by trubblemaker on 2006-11-17
superm1 

I have to thank you for righting some awesome wiki. it's an all in one solution nicely made from soure!  you really made my life good. THanks.

Do you have any advice for getting X running on the pvr-350 out?  Do you have any resouces I could browse through to get it working?  All the ones I can find are outdated.

---

### Post by superm1 on 2006-11-17
> **trubblemaker said:**
> superm1 

I have to thank you for righting some awesome wiki. it's an all in one solution nicely made from soure!  you really made my life good. THanks.

Glad you like the wiki :)

Do you have any advice for getting X running on the pvr-350 out?  Do you have any resouces I could browse through to get it working?  All the ones I can find are outdated.

Unfortunately, I gave up on that a long time ago.  I bought a 350 two years ago because I read all about it's superb video output at 720x480, but I only had it working in gentoo.  It was highly unstable, and would freeze the myth box very often.  I eventually gave up on trying to get much out of it, and now just use it for recording (and that machine its sitting in isn't even used as a frontend anymore).

Your very best bet here is to check out the ivtv mailing list, and possibly send a message about getting it to work with xorg 7.1.  It's very possible thought too that the X driver that was written for it hasn't even been ported to 7.1.

---

### Post by trubblemaker on 2006-11-17
I've can playback recorded shows, so far, without issue using mythtv.  I've seen alot of people get it working on edgy but a howto isn't quite there yet.  I promise to write one if it ever does work out. (I'm really close just having issues playing back stuff manually on my tv-out card.)

---

### Post by superm1 on 2006-11-17
> **trubblemaker said:**
> I've can playback recorded shows, so far, without issue using mythtv.  I've seen alot of people get it working on edgy but a howto isn't quite there yet.  I promise to write one if it ever does work out. (I'm really close just having issues playing back stuff manually on my tv-out card.)
Yes if you do get it working, add your howto to the community mythtv pages and link to it from the hardware page.  Good luck :)

---

### Post by trubblemaker on 2006-11-18
ok I got it working so I owe one howto on the wiki.

As a note I did also grab the driver from the debian package and stick it in the proper xorg directory.  I don't have the exact instructoins with me be rest assured I will in my howto.

for those that want to see here's my xorg.conf file

```


# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the /etc/X11/xorg.conf manual page.
# (Type "man /etc/X11/xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
        FontPath        "/usr/share/X11/fonts/misc"
        FontPath        "/usr/share/X11/fonts/cyrillic"
        FontPath        "/usr/share/X11/fonts/100dpi/:unscaled"
        FontPath        "/usr/share/X11/fonts/75dpi/:unscaled"
        FontPath        "/usr/share/X11/fonts/Type1"
        FontPath        "/usr/share/X11/fonts/100dpi"
        FontPath        "/usr/share/X11/fonts/75dpi"
        FontPath        "/usr/share/fonts/X11/misc"
        # path to defoma fonts
        FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
        Load "dbe"
        Load "v4l"
        Load "extmod"
        Load "type1"
        Load "freetype"
EndSection

Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "CoreKeyboard"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "us"
        Option          "XkbOptions"    "lv3:ralt_switch"
EndSection

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"                "/dev/input/mice"
        Option          "Protocol"              "ExplorerPS/2"
        Option          "ZAxisMapping"          "4 5"
        Option          "Emulate3Buttons"       "true"
EndSection

Section "Device"
        Identifier "Hauppauge PVR 350 iTVC15 Framebuffer"
        Driver "ivtvdev"
        Option "fbdev" "/dev/fb0"  # /dev/fb? changes for depending on computer, usually fb0
        # Option "ivtv" "/dev/fb1" # for pal users I believe
        Option "TVStandard" "NTSC-M"
        Option "VideoOverlay" "on"
        Option "XVideo" "1"
        # this also changes for different users
        # 'lspci | grep Internext' will tell you the device number
        # just convert from hex or use hex encoding.

        BusID "PCI:1:13:0" # converted to decimal from hex
        # BusID "PCI:0x01:0x0d:0x00" # hex encoding (same as line above)
Screen 0

EndSection

Section "Monitor"
        Identifier "NTSC Monitor"
        HorizSync 30-68
        VertRefresh 50-120
        DisplaySize 183 122
        Mode "720x480"
        DotClock 34.564
        HTimings 720 752 840 928
        VTimings 480 484 488 504
        Flags "-HSync" "-VSync"
        EndMode


# for pal users:
        #Section "Monitor"
	#	Identifier  "PAL Television"
	#	HorizSync  30-68
	#	VertRefresh 50-120
	#	Mode "720x576"
		# D: 41.475 MHz, H: 44.693 kHz, V: 74.488 Hz
	#		DotClock 41.476
	#		HTimings 720 752 840 928
	#		VTimings 576 580 584 600
	#		Flags    "-HSync" "-VSync"
	#	EndMode
	#EndSection



EndSection

Section "Screen"
        Identifier "TV Screen"
        Device "Hauppauge PVR 350 iTVC15 Framebuffer"
        Monitor "NTSC Monitor"
        DefaultDepth 24
        DefaultFbbpp 32
        Subsection "Display"
        Depth 24
        FbBpp 32
        Modes "720x480"
EndSubsection
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "TV Screen"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"
EndSection

Section "DRI"
        Mode    0666
EndSection


```

---

### Post by trubblemaker on 2006-11-20
added howto on wiki with a little better instructions posted above.

[https://help.ubuntu.com/community/MythTV_Edgy_hardware_pvr-350_TV-out#preview](https://help.ubuntu.com/community/MythTV_Edgy_hardware_pvr-350_TV-out#preview)

---

### Post by superm1 on 2006-11-21
> **trubblemaker said:**
> added howto on wiki with a little better instructions posted above.

[https://help.ubuntu.com/community/MythTV_Edgy_hardware_pvr-350_TV-out#preview](https://help.ubuntu.com/community/MythTV_Edgy_hardware_pvr-350_TV-out#preview)


Awesome.  I'll get this linked to the correct pages and such in the style/fashion that I'm "attempting" (it's taking a lot longer then anticipated) to lay out.

Thanks a bunch for contributing! :)

---

### Post by trubblemaker on 2006-11-21
It's the only fee I ask of those I help.  Thanks for formatting that.  I noticed the complex underworkings when I tried to add some troubleshooting tips.  Beaware that I don't mind at all if you remove the current links I added to the wiki.  I just tried to add it where I thought it might be useful.  Thanks for all your hard work on making awesome documentation.  I really appreciate that.

---

### Post by sandy_m on 2006-11-28
Thanks superm1,

I've checked out [http://help.ubuntu.com/community/MythTV]("http://help.ubuntu.com/community/MythTV")
and was able to install MythTV (I opted for Backend/Desktop). 

When I enter 'sudo /etc/init.d/mythtv-backend restart' MythTV restarts without an error message, however when I start the front end and want to watch TV, I get a 'Could not connect to the master backend server - is it running? Is the IP address set for it in the setup program correct?'

Well the IP address is set to 'localhost' (I didn't change the value). Also, I might add, when doing the MythTV setup, I skipped the 'video sources' section (The MythTV machine is not connected to the Internet, so I won't download guide data). Could this be the source of my problem? Consequently I also skipped the 'Input Connections' section.
Again, any help would be appreciated.
Many thanks for the advice so far,

Sandy

---

### Post by trubblemaker on 2006-11-28
couple things check that it's running.
```
 ps aux | grep back 
```

check the bottom of that howto if it is running make sure the right password is entered for mysql

---

### Post by superm1 on 2006-11-28
> **sandy_m said:**
> Thanks superm1,

I've checked out [http://help.ubuntu.com/community/MythTV](http://help.ubuntu.com/community/MythTV)
and was able to install MythTV (I opted for Backend/Desktop). 

When I enter 'sudo /etc/init.d/mythtv-backend restart' MythTV restarts without an error message, however when I start the front end and want to watch TV, I get a 'Could not connect to the master backend server - is it running? Is the IP address set for it in the setup program correct?'

Well the IP address is set to 'localhost' (I didn't change the value). Also, I might add, when doing the MythTV setup, I skipped the 'video sources' section (The MythTV machine is not connected to the Internet, so I won't download guide data). Could this be the source of my problem? Consequently I also skipped the 'Input Connections' section.
Again, any help would be appreciated.
Many thanks for the advice so far,

Sandy

Check /var/log/mythtv/mythbackend.log

See if possibly it is giving you errors about the backend not running because of permissions or anything to that sort.

---

### Post by trubblemaker on 2006-11-28
oh and since your running both on the same computer.  Their is an issue if the frontend starts before the backend.  the front end grabs the ports and then the backend can't start as the ports are in use..  I don't know how to fix that. The boot order needs to be changed so I wish that someone would tell me how to change the order they start in.  for now I made a work around.

I added basically two lines to the restart script for mythbackend. "/etc/init.d/mythtv-backend"


(edited the restart function to something like


```
restart|force-reload)
        echo -n "Restarting $DESC: $NAME"
        start-stop-daemon --stop --oknodo --pidfile $RUNDIR/$NAME.pid \
                --chuid $USER --exec $DAEMON -- $ARGS
        echo "."
        [COLOR="Red"]killall mythfrontend
        echo "Killing mythfrontend"
        sleep 3[/COLOR]
        start-stop-daemon --start --pidfile $RUNDIR/$NAME.pid \
                --chuid $USER --nicelevel $NICE --exec $DAEMON -- $ARGS
        echo "."
        [COLOR="Red"]echo "Starting Mythfrontend"
        mythfrontend &[/COLOR]
        ;;
  *)
        N=/etc/init.d/$NAME
        echo "Usage: $N {start|stop|restart|force-reload}" >&2
        exit 1
        ;;
esac

```

then  you need to call the restart.  technically since the backend isn't running anyways, You shouldn't need to restart it. but I wanted it fixed in case I called restart.

---

### Post by superm1 on 2006-11-28
> **trubblemaker said:**
> oh and since your running both on the same computer.  Their is an issue if the frontend starts before the backend.  the front end grabs the ports and then the backend can't start as the ports are in use..  I don't know how to fix that. The boot order needs to be changed so I wish that someone would tell me how to change the order they start in.  for now I made a work around.

I added basically two lines to the restart script for mythbackend. "/etc/init.d/mythtv-backend"


(edited the restart function to something like


```
restart|force-reload)
        echo -n "Restarting $DESC: $NAME"
        start-stop-daemon --stop --oknodo --pidfile $RUNDIR/$NAME.pid \
                --chuid $USER --exec $DAEMON -- $ARGS
        echo "."
        [COLOR=Red]killall mythfrontend
        echo "Killing mythfrontend"
        sleep 3[/COLOR]
        start-stop-daemon --start --pidfile $RUNDIR/$NAME.pid \
                --chuid $USER --nicelevel $NICE --exec $DAEMON -- $ARGS
        echo "."
        [COLOR=Red]echo "Starting Mythfrontend"
        mythfrontend &[/COLOR]
        ;;
  *)
        N=/etc/init.d/$NAME
        echo "Usage: $N {start|stop|restart|force-reload}" >&2
        exit 1
        ;;
esac

```then  you need to call the restart.  technically since the backend isn't running anyways, You shouldn't need to restart it. but I wanted it fixed in case I called restart.

Well this shouldn't be happening if you haven't changed runlevels for gdm and mythtv-backend.  Mythtv-backend should be starting quite earlier in the boot process before gdm comes up.

---

### Post by trubblemaker on 2006-11-28
don't think I changed any run levels, is there a way to check that?

---

### Post by Karol_Pawlak on 2007-06-19
> **Vincent_Lin said:**
> I have a question.  well, a problem.  I must have done something wrong,

while I was doing mythfilldatabase, a number of errors came out:

DB Error (Inserting into programgenres table):
Query was:
INSERT IGNORE INTO programgenres (chanid, starttime, relevance, genre) SELECT chanid, starttime, relevance, class FROM dd_v_program, dd_genre WHERE (dd_v_program.programid = dd_genre.programid);
Driver error was [2/1146]:
QMYSQL3: Unable to execute query
Database error was:
Table 'mythconverg.dd_v_program' doesn't exist

Could someone help?

Thanks.

Vincent

Hi,

I got the same errors. It seems mythtv user doesn't have sufficient access to create tables in DB. Try altering those permissions, it helped for me.

Best regards,
Karol

---

### Post by krazyj on 2008-03-05
Hi all,
Can anyone post a WORKING xorg.conf for:

Fiesty w/ Mythbuntu
Dual Monitors (LCD + TV)
PVR-350

?

I cant get it to work and I think a working example would be all I need.

THANKS!

---

