---
title: "Problem setting up Zend in Ubuntu"
date: 2009-09-22
forum: Programming Talk
---

### Post by mindaslab on 2009-09-22
Hi,

I am new to Zend, and want to install it on Ubuntu. When I did install I got the following error (I ran the quick start project described in [http://framework.zend.com/docs/quickstart/create-your-project](http://framework.zend.com/docs/quickstart/create-your-project) )


Warning: require_once(Zend/Application.php) [function.require-once]: failed to open stream: No such file or directory in /var/www/quickstart/public/index.php on line 18

Fatal error: require_once() [function.require]: Failed opening required 'Zend/Application.php' (include_path='/var/www/quickstart/library:.:/usr/share/php:/usr/share/pear') in /var/www/quickstart/public/index.php on line 18

I was following the quick start tutorial given in quick start section of getting started with Zend.

Extra Info (what I did):

   1. I downloaded ZF 1.9.2, extracted it to  **/usr.share/php5/zend/ZendFramework-1.9.2**
   2. In php.ini-dist changed line **;include_path = ".:/usr/share/php"** to **;include_path = ".:/usr/share/zend/ZendFramework-1.9.2/library:/usr/share/php"**
   3. In php.ini-dist.cli changed line **;include_path = ".:/usr/share/php" **to **;include_path = ".:/usr/share/zend/ZendFramework-1.9.2/library:/usr/share/php"**

Could any one tell what I have done wrong?

Regards
A.K.Karthikeyan

---

### Post by CyberJack on 2009-09-23
The error message doesn't show your added include path.
Try restarting apache to make sure your changed php.ini is used.

---

### Post by Ascenti0n on 2009-09-23
Wow, that seems like overkill. When I want to install a PHP framework, I merely download and extract the folder within my web folder, ie within /var/www (you will need to use SUDO and/or change owner to yourself). 

Once extracted in your web folder, there isn't anything else to do other than rename the folder to whatever you will call your project, ie 'testpproj', so then you can view through browser using: localhost/testproj/

---

### Post by infallible on 2009-10-03
BUMP!

I'm having issues with this, too. 

IMO, dropping the framework library into the root directory of every subdomain using it is a crap solution.

I just installed zend-framework and libzend-framework from the repositories.

The Zend test script shows the libraries were not added to php.ini's include_path section. Easy enough to do manually, but where did it all go?

I can't find, or 'locate', anything called "zend" on my system. Where did the package from the repos put it all?

---

### Post by CyberJack on 2009-10-05
Have you update the locate database after installing Zend Framework?
After installing the version from the repository, `locate` shows that the framework is located in: /usr/share/php/libzend-framework-php/Zend/

The version installed is very old though (1.5.3 from 2008-07-28 ).
It might be better to download the latest version manually (currently 1.9.3PL1). Unpack somewhere and add the library/ directory to your php.ini's include_path setting. This should be enough to make the framework system wide available.

---

### Post by infallible on 2009-10-05
I tried 'locate zend' and 'locate Zend' after repo install to look for the library directory, in order to add to php.ini, with no results. 

I have installed manually.

Then, you posted :rolleyes:=D>

---

