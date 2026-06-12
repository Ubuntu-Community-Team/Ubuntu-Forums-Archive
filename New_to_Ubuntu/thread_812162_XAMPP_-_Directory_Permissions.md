---
title: "XAMPP - Directory Permissions"
date: 2008-05-29
forum: New to Ubuntu
---

### Post by garyedwardjohnston on 2008-05-29
OMG!!!

I've done this before. but for the life of me I can't get through it this time.

Everything seems to be working ok (XAMMPP, Joomla install, etc.) except that I cannot use my Joomla Admin to upload anything to my site!!!.

I type sudo nautilus in terminal and right click my htdocs folder to change the permissions and it won't stick.  I need to change the permissions of the folders to the correct settings.  Please help.  Thanks.

---

### Post by Dr Small on 2008-05-29
Try:
```
gksudo nautilus
```

And browsing to /opt/lampp/htdocs/**joomla_directory**/ and finding the admin directory. Right click on it, and change the permissions of it. It will need write permissions.

Alternately, you can use the command line:
```
sudo chmod 777 /opt/lampp/htdocs/path/to/joomla/admin
```

---

### Post by garyedwardjohnston on 2008-05-29
Thanks for the try but NOTHING STICKS.

I need a screenprint of what the directory permissions window should look like.

I change the permissions to what I think they should be then it AUTOMATICALLY changes back.  It won't accept my changes.

---

### Post by Dr Small on 2008-05-29
Could you please specify the full path to the joomla/admin directory, so I can give you a few commands to see what the problem is?

Dr Small

---

### Post by garyedwardjohnston on 2008-05-29
/opt/lampp/htdocs/joomla/....

It's something different than what youre thinking.

I cannot change the directory permissions via sudo nautilus.

---

### Post by Dr Small on 2008-05-29
Ok, please show me the results of this command:
```
ls -l /opt/lampp/htdocs/joomla/
```

Then I'll see how to correctly set the permissions for the directory.

Dr Small

---

### Post by garyedwardjohnston on 2008-05-29
total 264
drwxrwxrwx  9 gary gary   4096 2008-02-21 11:32 administrator
drwxrwxrwx  2 gary gary   4096 2008-02-21 11:32 cache
-rwxrwxrwx  1 gary gary 104874 2008-02-21 11:31 CHANGELOG.php
drwxrwxrwx 16 gary gary   4096 2008-02-21 11:32 components
-rwxrwxrwx  1 gary gary   4372 2008-02-21 11:31 configuration.php-dist
-rwxrwxrwx  1 gary gary   3429 2008-02-21 11:31 COPYRIGHT.php
drwxrwxrwx  2 gary gary   4096 2008-02-21 11:32 editor
-rwxrwxrwx  1 gary gary   3745 2008-02-21 11:31 globals.php
drwxrwxrwx  3 gary gary  12288 2008-02-21 11:32 help
-rwxrwxrwx  1 gary gary   4829 2008-02-21 11:31 htaccess.txt
drwxrwxrwx  6 gary gary   4096 2008-02-21 11:32 images
drwxrwxrwx 10 gary gary   4096 2008-02-21 11:32 includes
-rwxrwxrwx  1 gary gary   5216 2008-02-21 11:32 index2.php
-rwxrwxrwx  1 gary gary   8481 2008-02-21 11:32 index.php
drwxrwxrwx  3 gary gary   4096 2008-02-21 11:32 installation
-rwxrwxrwx  1 gary gary   4376 2008-02-21 11:32 INSTALL.php
drwxrwxrwx  2 gary gary   4096 2008-02-21 11:32 language
-rwxrwxrwx  1 gary gary  17977 2008-02-21 11:32 LICENSE.php
-rwxrwxrwx  1 gary gary    710 2008-02-21 11:32 mainbody.php
drwxrwxrwx  7 gary gary   4096 2008-02-21 11:32 mambots
drwxrwxrwx  2 gary gary   4096 2008-02-21 11:32 media
drwxrwxrwx  2 gary gary   4096 2008-02-21 11:32 modules
-rwxrwxrwx  1 gary gary   2474 2008-02-21 11:32 offlinebar.php
-rwxrwxrwx  1 gary gary   4929 2008-02-21 11:32 offline.php
-rwxrwxrwx  1 gary gary    709 2008-02-21 11:32 pathway.php
-rwxrwxrwx  1 gary gary    286 2008-02-21 11:32 robots.txt
drwxrwxrwx  5 gary gary   4096 2008-02-21 11:32 templates

---

### Post by Dr Small on 2008-05-29
Well /opt/lampp/htdocs/joomla/administrator seems to have rwx for all (read, write and execute), so I really don't see where the problem is.

---

### Post by garyedwardjohnston on 2008-05-29
Well things have changed...they continue to change because I continue to try to install this damn thing with instructions I find in every corner of the net.

None of them work, most of them are totally outdated and eventually I have to reinstall the operating system OVER AND OVER again.

I have seen your posts regarding this in numerous places elsewhere in these forums and like the other posts, NOTHING WORKS.

I can't help but think something has changed with Ubuntu (Hardy or the new kernel or something) that is making everyone's instructions totally mess things up.

If you really do know a lot about this, might I suggest a run a fresh through yourself using a totally up to date EVERYTHING (Hardy, XAMPP, and Joomla!) and updating the Joomla! install instructions in the community documentation.

[https://help.ubuntu.com/community/Joomla?highlight=(joomla](https://help.ubuntu.com/community/Joomla?highlight=(joomla))

I bet you are in for a surprise.

---

### Post by Dr Small on 2008-05-29
Tha guide was writen for Dapper and doesn't even use Xampp. I have installed joomla before and Xampp and never had a problem.

It seems there is some misconfiguration for permissions somewhere, is all.

Oh, and what should I be surprised about on that Wiki page? I know you are frustrated, but don't let that show in your posting attitude, please.

Dr Small

---

### Post by garyedwardjohnston on 2008-05-29
Thanks for your help but I'm giving up on Ubuntu.

[http://ubuntuforums.org/showthread.php?t=812469](http://ubuntuforums.org/showthread.php?t=812469)

PS.  I am still giving you a thanks to add to your collection.

---

### Post by VitalBodies on 2008-07-14
**XAMPP - Directory Permissions or better:**
I have 10-15 websites with thousands of files and hundreds of folders that I would like to have permission to edit. 
They are in /opt/lampp/htdocs/

Using sudo nautilus would take hours...

I was using XAMPP portable on a portable Windows hard drive then switched to 64-bit Ubuntu. 

Ideally I would (or think I would) like to switch to some form of:
sudo aptitude install lamp-server
or the like...

**Would this be the answer?:** [https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

I am not running a live online server only a server to test build sites locally. 

XAMPP seems like an external set of applications, when Ubuntu has full support for roughly all the same things.

---

