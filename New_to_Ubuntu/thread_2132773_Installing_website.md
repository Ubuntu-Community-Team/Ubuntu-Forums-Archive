---
title: "Installing website"
date: 2013-04-05
forum: New to Ubuntu
---

### Post by Joe67 on 2013-04-05
Hey, first off bare with me :D am a newbie at this stuff.

Ive installed Ubuntu 11.04 64bit on my vps and now looking to install whats needed to run my website and later on arma 2 server and teamspeak.

First things first, whats needed to get the website runing, i was using centos before and knew a yum code that would install some things needed, but ubuntu doesnt use yum

Any help to get me started is appreciated,cheers

---

### Post by Nr90 on 2013-04-05
Ubuntu uses a packaging tool called apt, have a read somewhere (plenty of info out there).
You might want to search for LAMP server to get some information about setting up a webserver.

Good luck :)

---

### Post by lisati on 2013-04-05
*Thread moved to **Server Platforms**.*

If you are intending to run a website, you'll probably want to set up a *web server*. There are several alternatives, of which running "apache" is a commonly used choice. 

You might want to take a look here: [https://help.ubuntu.com/12.10/serverguide/httpd.html](https://help.ubuntu.com/12.10/serverguide/httpd.html)

---

### Post by Joe67 on 2013-04-05
thanks for the quick replys, ill have alook.

---

### Post by 3rdalbum on 2013-04-05
Ubuntu 11.04 is way out of date, and no longer supported. Install Ubuntu 12.04.

You can use Ubuntu Software Center to install Apache2, or the following apt-get command:

sudo apt-get install apache2

To copy files to the /var/www directory you need to use a file browser opened as root:

gksudo nautilus

or copy files across using sudo cp.

---

### Post by Cheesemill on 2013-04-05
First things first, you shouldn't be using 11.04.

11.04 was only supported for 18 months, so it reached end of life in October last year. This means it hasn't had any security updates or bug-fixes for 6 months now and may well have security vulnerabilities that won't ever get patched, meaning it could be a trivial task for anyone to hack into your server and take it over.

The recomendation is to only use LTS releases for production servers, which means installing 12.04 as it has five years of support.

Once you have 12.04 you can install the entire LAMP stack (Linux, Apache, MySQL and PHP) with the following command...
```
sudo apt-get install lamp-server^
```
This will configure Apache to server your website from the /var/www folder.

For more information your first port of call should be the official documentation...
[https://help.ubuntu.com/12.04/serverguide/index.html](https://help.ubuntu.com/12.04/serverguide/index.html)

---

### Post by Joe67 on 2013-04-05
ok thanks the reason i chose 11.04 was the next version up was  12.04 beta and it says use it at your own risk...(**Ubuntu 12.04 x64 bit (BETA)**
This is a beta OS for openVZ.  Use at your own risk)

---

### Post by Cheesemill on 2013-04-05
Your VPS provider isn't very up to date with their OS choices then. 12.04 was released in April last year.

---

### Post by Joe67 on 2013-04-05
lol ive just messaged them, hopfully they can help

---

### Post by sandyd on 2013-04-05
Tell them to do this.

Go to [http://wiki.openvz.org/Download/template/precreated](http://wiki.openvz.org/Download/template/precreated) , download 12.04.

On older openvz kernels, the VPS Provider _has_ to have the ppa:izx/ovz-libc PPA enabled inside the VPS in order to get a working libc

---

### Post by Joe67 on 2013-04-05
done :D

---

### Post by Joe67 on 2013-04-06
Heres what my host said, 2 replys

> I can't just install a new OS template on a whim.  It has to be tested  for functionality.  The other version of Ubuntu are not "out of date"  same as CentOS 5.x and CentOS 6.x are not upgrade version.  They are  completely separate versions from each other and plenty of people don't  go to new version.  I will look at getting the 12.04 loaded, but its not  going to be available for a little while

then

> I have update the 12.04 templates since I already had those loaded, and could just put the non-beta ones on.

You should be able to do a reinstall of the 12.04 64 bit and be on the non-beta version

my question now is, second message seem correct?


edit doesnt seem to be working, tryed to install says 0 out of 0 memory used.

dam i put this weekend aside to get all this done, i expected some set backs as a newbie but didnt expect this one

---

### Post by Joe67 on 2013-04-06
guys i have a problem i installed the 12.04 on the vps controll pannel like id with any other os. this time it says memory 0 of 0 Used / 0 Free  

after telling me 

> have update the 12.04 templates since I already had those loaded, and could just put the non-beta ones on.

You should be able to do a reinstall of the 12.04 64 bit and be on the non-beta version


they are now saying

> That's the 12.04 version you sent us a link to and wanted.....
You can always use another version, and run updates on it after its loaded.

i sent the link you guys said they should install

---

### Post by Joe67 on 2013-04-06
ok they removed the vps, made a new one and its working now i believe.


sudo apt-get install lamp-server^ doesnt work


sudo: apt-get: command not found

---

### Post by Joe67 on 2013-04-06
Ive split this from another thread as the thread got abit messed up, i hope the mods dont mind.

am trying to use 

sudo apt-get install lamp-server^  on putty but get the message sudo: apt-get: command not found

can anyone help? ive alot to do and little time :(

---

### Post by steeldriver on 2013-04-06
Hmm sounds like your apt package itself is messed up - what does 

```
 dpkg -l | grep -w apt
```

say? what about

```
echo $PATH
which apt-get
```

---

### Post by mörgæs on 2013-04-06
Merged

> **Joe67 said:**
> Ive split this from another thread as the thread got abit messed up, i hope the mods dont mind.


You had a hunch that this was not the preferred way, hadn't you?

---

### Post by Joe67 on 2013-04-06
> **steeldriver said:**
> Hmm sounds like your apt package itself is messed up - what does 

```
 dpkg -l | grep -w apt
```

say? what about

```
echo $PATH
which apt-get
```


root@vpsserver [~]# dpkg -l | grep -w apt
-bash: dpkg: command not found
root@vpsserver [~]# echo $PATH
/usr/local/jdk/bin:/usr/kerberos/sbin:/usr/kerberos/bin:/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin:/usr/local/bin:/usr/X11R6/bin:/root/bin
root@vpsserver [~]# which apt-get



yes mörgæs, sorry about that. am up against it and was looking for help asap

---

### Post by steeldriver on 2013-04-06
well that's not good - the PATH seems OK, so either the binaries are gone or not executable or maybe there's a library problem - let's see

```

ls -l /usr/bin/dpkg
ldd /usr/bin/dpkg
```

Let's also see what kind of system you are running

```
uname -a
```

---

### Post by Joe67 on 2013-04-06
> **steeldriver said:**
> well that's not good - the PATH seems OK, so either the binaries are gone or not executable or maybe there's a library problem - let's see

```

ls -l /usr/bin/dpkg
ldd /usr/bin/dpkg
```

Let's also see what kind of system you are running

```
uname -a
```


root@vpsserver [~]# ls -l /usr/bin/dpkg
/bin/ls: /usr/bin/dpkg: No such file or directory
root@vpsserver [~]# ldd /usr/bin/dpkg
ldd: /usr/bin/dpkg: No such file or directory
root@vpsserver [~]# uname -a
Linux .(removed).com 2.6.18-274.7.1.el5.028stab095.1 #1 SMP Mon Oct 24 20:49:24 MSD 2011 x86_64 x86_64 x86_64 GNU/Linux


could this problem be related to how host my host installed 12.04

> have update the 12.04 templates since I already had those loaded, and could just put the non-beta ones on.

You should be able to do a reinstall of the 12.04 64 bit and be on the non-beta version                      

---

### Post by Cheesemill on 2013-04-06
I'm not even sure if your using Ubuntu.

Even the oldest version of Ubuntu that should still be around uses a later kernel than the one you're using (8.04 uses 2.6.24 but that is being retired next month as it's 5 years old).
This along with the fact that you don't seem to have any of the Ubuntu/Debian package management tools installed makes me think you may be on a different OS.

What's the output of...
```
cat /etc/issue
lsb_release -a
```

---

### Post by sandyd on 2013-04-06
> **Cheesemill said:**
> I'm not even sure if your using Ubuntu.

**Even the oldest version of Ubuntu that should still be around uses a later kernel than the one you're using (8.04 uses 2.6.24 but that is being retired next month as it's 5 years old).**
This along with the fact that you don't seem to have any of the Ubuntu/Debian package management tools installed makes me think you may be on a different OS.

What's the output of...
```
cat /etc/issue
lsb_release -a
```

If your using openvz, the vps shares the kernel of the host machine. Only for OpenVZ tho, not with qemu/kvm, xen, .etc .etc

---

### Post by Cheesemill on 2013-04-06
> **sandyd said:**
> If your using openvz, the vps shares the kernel of the host machine. Only for OpenVZ tho, not with qemu/kvm, xen, .etc .etc

Your right :)
I'd forgotten all about that, I don't use OpenVZ myself.

I'm still wondering where all of the package management tools are though.

---

### Post by Joe67 on 2013-04-06
> **Cheesemill said:**
> I'm not even sure if your using Ubuntu.

Even the oldest version of Ubuntu that should still be around uses a later kernel than the one you're using (8.04 uses 2.6.24 but that is being retired next month as it's 5 years old).
This along with the fact that you don't seem to have any of the Ubuntu/Debian package management tools installed makes me think you may be on a different OS.

What's the output of...
```
cat /etc/issue
lsb_release -a
```



root@vpsserver [~]# cat /etc/issue
This computer system is for authorized users only. Individuals using this
system without authority or in excess of their authority are subject to
having all their activities on this system monitored and recorded or
examined by any authorized person, including law enforcement, as system
personnel deem appropriate. In the course of monitoring individuals
improperly using the system or in the course of system maintenance, the
activities of authorized users may also be monitored and recorded. Any
material so recorded may be disclosed as appropriate. Anyone using this
system consents to these terms.

root@vpsserver [~]# lsb_release -a
-bash: lsb_release: command not found

yes it uses openvz

---

### Post by sandyd on 2013-04-06
they used the wrong template on the page....
the correct link should be [http://download.openvz.org/template/precreated/ubuntu-12.04-x86_64.tar.gz](http://download.openvz.org/template/precreated/ubuntu-12.04-x86_64.tar.gz)

---

### Post by Joe67 on 2013-04-06
my host is asking will 12.10 be ok?

---

### Post by Cheesemill on 2013-04-06
That's up to you.

Personally I'd want to use an LTS release such as 12.04 on a server, and I know that a lot of people think the same way.

You can do everything you need to on either version but support ends for 12.10 in a years time, so you'll have to either upgrade to a newer release or do a fresh installation quite soon if you want to keep getting updates (vitally important for a server on the internet). As 12.04 is LTS it's supported until 2017 giving you a server that will hopefully run for several years without any issues. Also because 12.04 has been out longer then more of its bugs will have been fixed.

At the end of the day it's up to you (and your VPS host), but I always use 12.04 on my servers at the moment.

---

### Post by Joe67 on 2013-04-06
ok mate thanks for the help, 12.04 it is :D

---

### Post by Joe67 on 2013-04-06
gutted, i took our clan website, ts server etc down to do this, really disapointed with my host at the moment one support guy says one thing and the other says different... they offer to install proper 12.10 and 12.04 and now am told > If its not what you want, then you will have to pick anther version  while we spend the time testing that needs to be done.  This is all we  can do.
they have been good untill now, will see what happens. just incase though anyone know of a good vps host with good prices?

---

### Post by Cheesemill on 2013-04-06
I always use [Linode]("http://www.linode.com/") whenever I need a VPS. There not the cheapest but their customer service, infrastructure and control panel are second to none.
Even if you don't choose them its worth bookmarking the site just for their excellent [documentation library]("http://library.linode.com/").

If you are looking for something cheaper then take a look at [Digital Ocean]("https://www.digitalocean.com/") although I haven't used them personally, their prices start at $5.

---

### Post by Joe67 on 2013-04-07
ok any ideas on:

sudo apt-get install lamp-server^
Reading package lists... Done
Building dependency tree... Done
E: Unable to locate package lamp-server^
E: Couldn't find task 'lamp-server'
E: Couldn't find any package by regex 'lamp-server^'

---

### Post by Cheesemill on 2013-04-07
Have you updating your package list? You need to do this before you can install any software...
```
sudo apt-get update
```

---

### Post by Joe67 on 2013-04-07
ok thanks for the help, getting somewhere now

---

### Post by Joe67 on 2013-04-08
anyone know of a good guide for newbies setting up a webserver/site? so far lamp server installed.. now ive got time to try get rest done

---

### Post by mörgæs on 2013-04-08
What exactly do you need? A guide for learning HTML / CSS / PHP ...?

---

### Post by Joe67 on 2013-04-08
it was to get everything setup for my website to run on, i think am slowly getting there now, google, google, google lol.

---

### Post by Joe67 on 2013-04-09
ok am very slowly making progress, i have the webserver etc set and displaying a default html file when i enter website ip but i still cant get my website to show. i edited the website config file and have made sure db details are correct, for now am stuck.. any ideas?

---

### Post by mörgæs on 2013-04-10
You are still not describing exactly what you need. 

Can you show static HTML from your web site? 
Can you show static HTML and PHP? 
Can you show static HTML and PHP with database connection?

---

### Post by Joe67 on 2013-04-10
I think so, if you can point me in the right direction how to test would be appreciated

Am not sure the website is connecting to database,  db name/user/password/ are correct

---

### Post by mörgæs on 2013-04-10
Sorry, I don't think there's more I can do. It's too difficult to give advice without seeing the screen.

---

### Post by Joe67 on 2013-04-11
as per pm, you are happy with php info

am now sure its a db issue, my website runs on a cms called nuke evolution. ive edited the config file to match the database but for some reason its not connecting. the db has been uploaded, username/password are correct. it should work.

is there anyway i can test connection to db?

---

### Post by Joe67 on 2013-04-12
I asked someone to have a look over server for me, give me second opinion on the setup,heres what he said
> 
I went in and looked. I did check to see if the  user he had set up in phpmyadmin had all the permissions, and when I was  in there, I did notice it was saying that the DB was called, as an  example, **example\_xtreme**, where when looking at the DB names you see it as **example_xtreme**.  So I went into the config and changed it to what it was saying under  the users and it ended up showing that the phpMyadmin version was out  dated and evo did not support it and phpmyadmin does not support it. And  when I put it back to what he had, he saw a blank white page and on  Chrome, for me it is showing a 500 error.  
 
I also uploaded a test site into a sub folder to see if it might of been  a corrupt file somewhere and it spit out the same thing. To me, it  seems like its not connecting to the DB or something is messing with the  connection between the two. Hopefully someone here that know something  about this can solve his issue.

Am sure mysql version is ok, i know  of someone runing the same version

---

### Post by Joe67 on 2013-04-12
EDIT:

from log:

```
[Fri Apr 12 23:28:30 2013] [error] [client 66.249.76.95] PHP Fatal error:  Uncaught exception 'Zend_Cache_Exception' with message 'cache_dir is not writable' in /home/ca/public_html/Zend/Cache.php:208
Stack trace:
#0 /home/ca/public_html/Zend/Cache/Backend/File.php(157): Zend_Cache::throwException('cache_dir is no...')
#1 /home/ca/public_html/Zend/Cache/Backend/File.php(121): Zend_Cache_Backend_File->setCacheDir('/home/ca/public...')
#2 /home/ca/public_html/Zend/Cache.php(152): Zend_Cache_Backend_File->__construct(Array)
#3 /home/ca/public_html/Zend/Cache.php(93): Zend_Cache::_makeBackend('File', Array, false, false)
#4 /home/ca/public_html/includes/classes/class.cache.php(58): Zend_Cache::factory('Core', 'File', Array, Array)
#5 /home/ca/public_html/includes/classes/class.cache.php(162): cache->cache(1)
#6 /home/ca/public_html/mainfile.php(204): require_once('/home/ca/public...')
#7 /home/ca/public_html/modules.php(43): require_once('/home/ca/public...')
#8 {main}
  thrown in /home/ca/public_html/Zend/Cache.php on line 208
[Fri Apr 12 23:28:40 2013] [error] [client 66.249.76.177] PHP Fatal error:  Uncaught exception 'Zend_Cache_Exception' with message 'cache_dir is not writable' in /home/ca/public_html/Zend/Cache.php:208
Stack trace:
#0 /home/ca/public_html/Zend/Cache/Backend/File.php(157): Zend_Cache::throwException('cache_dir is no...')
#1 /home/ca/public_html/Zend/Cache/Backend/File.php(121): Zend_Cache_Backend_File->setCacheDir('/home/ca/public...')
#2 /home/ca/public_html/Zend/Cache.php(152): Zend_Cache_Backend_File->__construct(Array)
#3 /home/ca/public_html/Zend/Cache.php(93): Zend_Cache::_makeBackend('File', Array, false, false)
#4 /home/ca/public_html/includes/classes/class.cache.php(58): Zend_Cache::factory('Core', 'File', Array, Array)
#5 /home/ca/public_html/includes/classes/class.cache.php(162): cache->cache(1)
#6 /home/ca/public_html/mainfile.php(204): require_once('/home/ca/public...')
#7 /home/ca/public_html/modules.php(43): require_once('/home/ca/public...')
#8 {main}
  thrown in /home/ca/public_html/Zend/Cache.php on line 208
[Fri Apr 12 23:29:16 2013] [error] [client 66.249.76.95] PHP Fatal error:  Uncaught exception 'Zend_Cache_Exception' with message 'cache_dir is not writable' in /home/ca/public_html/Zend/Cache.php:208
Stack trace:
#0 /home/ca/public_html/Zend/Cache/Backend/File.php(157): Zend_Cache::throwException('cache_dir is no...')
#1 /home/ca/public_html/Zend/Cache/Backend/File.php(121): Zend_Cache_Backend_File->setCacheDir('/home/ca/public...')
#2 /home/ca/public_html/Zend/Cache.php(152): Zend_Cache_Backend_File->__construct(Array)
#3 /home/ca/public_html/Zend/Cache.php(93): Zend_Cache::_makeBackend('File', Array, false, false)
#4 /home/ca/public_html/includes/classes/class.cache.php(58): Zend_Cache::factory('Core', 'File', Array, Array)
#5 /home/ca/public_html/includes/classes/class.cache.php(162): cache->cache(1)
#6 /home/ca/public_html/mainfile.php(204): require_once('/home/ca/public...')
#7 /home/ca/public_html/modules.php(43): require_once('/home/ca/public...')
#8 {main}
  thrown in /home/ca/public_html/Zend/Cache.php on line 208
[Fri Apr 12 23:29:27 2013] [error] [client 66.249.76.177] PHP Fatal error:  Uncaught exception 'Zend_Cache_Exception' with message 'cache_dir is not writable' in /home/ca/public_html/Zend/Cache.php:208
Stack trace:
#0 /home/ca/public_html/Zend/Cache/Backend/File.php(157): Zend_Cache::throwException('cache_dir is no...')
#1 /home/ca/public_html/Zend/Cache/Backend/File.php(121): Zend_Cache_Backend_File->setCacheDir('/home/ca/public...')
#2 /home/ca/public_html/Zend/Cache.php(152): Zend_Cache_Backend_File->__construct(Array)
#3 /home/ca/public_html/Zend/Cache.php(93): Zend_Cache::_makeBackend('File', Array, false, false)
#4 /home/ca/public_html/includes/classes/class.cache.php(58): Zend_Cache::factory('Core', 'File', Array, Array)
#5 /home/ca/public_html/includes/classes/class.cache.php(162): cache->cache(1)
#6 /home/ca/public_html/mainfile.php(204): require_once('/home/ca/public...')
#7 /home/ca/public_html/modules.php(43): require_once('/home/ca/public...')
#8 {main}
  thrown in /home/ca/public_html/Zend/Cache.php on line 208
[Fri Apr 12 23:29:30 2013] [error] [client 86.162.89.134] PHP Fatal error:  Uncaught exception 'Zend_Cache_Exception' with message 'cache_dir is not writable' in /home/ca/public_html/Zend/Cache.php:208
Stack trace:
#0 /home/ca/public_html/Zend/Cache/Backend/File.php(157): Zend_Cache::throwException('cache_dir is no...')
#1 /home/ca/public_html/Zend/Cache/Backend/File.php(121): Zend_Cache_Backend_File->setCacheDir('/home/ca/public...')
#2 /home/ca/public_html/Zend/Cache.php(152): Zend_Cache_Backend_File->__construct(Array)
#3 /home/ca/public_html/Zend/Cache.php(93): Zend_Cache::_makeBackend('File', Array, false, false)
#4 /home/ca/public_html/includes/classes/class.cache.php(58): Zend_Cache::factory('Core', 'File', Array, Array)
#5 /home/ca/public_html/includes/classes/class.cache.php(162): cache->cache(1)
#6 /home/ca/public_html/mainfile.php(204): require_once('/home/ca/public...')
#7 /home/ca/public_html/index.php(39): require_once('/home/ca/public...')
#8 {main}
  thrown in /home/ca/public_html/Zend/Cache.php on line 208
[Fri Apr 12 23:29:32 2013] [error] [client 86.162.89.134] PHP Fatal error:  Uncaught exception 'Zend_Cache_Exception' with message 'cache_dir is not writable' in /home/ca/public_html/Zend/Cache.php:208
Stack trace:
#0 /home/ca/public_html/Zend/Cache/Backend/File.php(157): Zend_Cache::throwException('cache_dir is no...')
#1 /home/ca/public_html/Zend/Cache/Backend/File.php(121): Zend_Cache_Backend_File->setCacheDir('/home/ca/public...')
#2 /home/ca/public_html/Zend/Cache.php(152): Zend_Cache_Backend_File->__construct(Array)
#3 /home/ca/public_html/Zend/Cache.php(93): Zend_Cache::_makeBackend('File', Array, false, false)
#4 /home/ca/public_html/includes/classes/class.cache.php(58): Zend_Cache::factory('Core', 'File', Array, Array)
#5 /home/ca/public_html/includes/classes/class.cache.php(162): cache->cache(1)
#6 /home/ca/public_html/mainfile.php(204): require_once('/home/ca/public...')
#7 /home/ca/public_html/index.php(39): require_once('/home/ca/public...')
#8 {main}
  thrown in /home/ca/public_html/Zend/Cache.php on line 208
[Fri Apr 12 23:29:33 2013] [error] [client 86.162.89.134] PHP Fatal error:  Uncaught exception 'Zend_Cache_Exception' with message 'cache_dir is not writable' in /home/ca/public_html/Zend/Cache.php:208
Stack trace:
#0 /home/ca/public_html/Zend/Cache/Backend/File.php(157): Zend_Cache::throwException('cache_dir is no...')
#1 /home/ca/public_html/Zend/Cache/Backend/File.php(121): Zend_Cache_Backend_File->setCacheDir('/home/ca/public...')
#2 /home/ca/public_html/Zend/Cache.php(152): Zend_Cache_Backend_File->__construct(Array)
#3 /home/ca/public_html/Zend/Cache.php(93): Zend_Cache::_makeBackend('File', Array, false, false)
#4 /home/ca/public_html/includes/classes/class.cache.php(58): Zend_Cache::factory('Core', 'File', Array, Array)
#5 /home/ca/public_html/includes/classes/class.cache.php(162): cache->cache(1)
#6 /home/ca/public_html/mainfile.php(204): require_once('/home/ca/public...')
#7 /home/ca/public_html/index.php(39): require_once('/home/ca/public...')
#8 {main}
  thrown in /home/ca/public_html/Zend/Cache.php on line 208
[Fri Apr 12 23:29:55 2013] [error] [client 66.249.76.95] File does not exist: /home/ca/public_html/Evo-Calendar_-_m_-_05_-_d_-_02_-_y_-_2018_-_op_-_day.html
[Fri Apr 12 23:30:04 2013] [error] [client 66.249.76.95] PHP Fatal error:  Uncaught exception 'Zend_Cache_Exception' with message 'cache_dir is not writable' in /home/ca/public_html/Zend/Cache.php:208
Stack trace:
#0 /home/ca/public_html/Zend/Cache/Backend/File.php(157): Zend_Cache::throwException('cache_dir is no...')
#1 /home/ca/public_html/Zend/Cache/Backend/File.php(121): Zend_Cache_Backend_File->setCacheDir('/home/ca/public...')
#2 /home/ca/public_html/Zend/Cache.php(152): Zend_Cache_Backend_File->__construct(Array)
#3 /home/ca/public_html/Zend/Cache.php(93): Zend_Cache::_makeBackend('File', Array, false, false)
#4 /home/ca/public_html/includes/classes/class.cache.php(58): Zend_Cache::factory('Core', 'File', Array, Array)
#5 /home/ca/public_html/includes/classes/class.cache.php(162): cache->cache(1)
#6 /home/ca/public_html/mainfile.php(204): require_once('/home/ca/public...')
#7 /home/ca/public_html/modules.php(43): require_once('/home/ca/public...')
#8 {main}
  thrown in /home/ca/public_html/Zend/Cache.php on line 208
[Fri Apr 12 23:30:33 2013] [error] [client 66.249.76.177] PHP Fatal error:  Uncaught exception 'Zend_Cache_Exception' with message 'cache_dir is not writable' in /home/ca/public_html/Zend/Cache.php:208
Stack trace:
#0 /home/ca/public_html/Zend/Cache/Backend/File.php(157): Zend_Cache::throwException('cache_dir is no...')
#1 /home/ca/public_html/Zend/Cache/Backend/File.php(121): Zend_Cache_Backend_File->setCacheDir('/home/ca/public...')
#2 /home/ca/public_html/Zend/Cache.php(152): Zend_Cache_Backend_File->__construct(Array)
#3 /home/ca/public_html/Zend/Cache.php(93): Zend_Cache::_makeBackend('File', Array, false, false)
#4 /home/ca/public_html/includes/classes/class.cache.php(58): Zend_Cache::factory('Core', 'File', Array, Array)
#5 /home/ca/public_html/includes/classes/class.cache.php(162): cache->cache(1)
#6 /home/ca/public_html/mainfile.php(204): require_once('/home/ca/public...')
#7 /home/ca/public_html/modules.php(43): require_once('/home/ca/public...')
#8 {main}
  thrown in /home/ca/public_html/Zend/Cache.php on line 208
[Fri Apr 12 23:30:51 2013] [error] [client 66.249.76.95] PHP Fatal error:  Uncaught exception 'Zend_Cache_Exception' with message 'cache_dir is not writable' in /home/ca/public_html/Zend/Cache.php:208
Stack trace:
#0 /home/ca/public_html/Zend/Cache/Backend/File.php(157): Zend_Cache::throwException('cache_dir is no...')
#1 /home/ca/public_html/Zend/Cache/Backend/File.php(121): Zend_Cache_Backend_File->setCacheDir('/home/ca/public...')
#2 /home/ca/public_html/Zend/Cache.php(152): Zend_Cache_Backend_File->__construct(Array)
#3 /home/ca/public_html/Zend/Cache.php(93): Zend_Cache::_makeBackend('File', Array, false, false)
#4 /home/ca/public_html/includes/classes/class.cache.php(58): Zend_Cache::factory('Core', 'File', Array, Array)
#5 /home/ca/public_html/includes/classes/class.cache.php(162): cache->cache(1)
#6 /home/ca/public_html/mainfile.php(204): require_once('/home/ca/public...')
#7 /home/ca/public_html/modules.php(43): require_once('/home/ca/public...')
#8 {main}
  thrown in /home/ca/public_html/Zend/Cache.php on line 208
[Fri Apr 12 23:31:11 2013] [error] [client 66.249.76.95] PHP Fatal error:  Uncaught exception 'Zend_Cache_Exception' with message 'cache_dir is not writable' in /home/ca/public_html/Zend/Cache.php:208
Stack trace:
#0 /home/ca/public_html/Zend/Cache/Backend/File.php(157): Zend_Cache::throwException('cache_dir is no...')
#1 /home/ca/public_html/Zend/Cache/Backend/File.php(121): Zend_Cache_Backend_File->setCacheDir('/home/ca/public...')
#2 /home/ca/public_html/Zend/Cache.php(152): Zend_Cache_Backend_File->__construct(Array)
#3 /home/ca/public_html/Zend/Cache.php(93): Zend_Cache::_makeBackend('File', Array, false, false)
#4 /home/ca/public_html/includes/classes/class.cache.php(58): Zend_Cache::factory('Core', 'File', Array, Array)
#5 /home/ca/public_html/includes/classes/class.cache.php(162): cache->cache(1)
#6 /home/ca/public_html/mainfile.php(204): require_once('/home/ca/public...')
#7 /home/ca/public_html/modules.php(43): require_once('/home/ca/public...')
#8 {main}
  thrown in /home/ca/public_html/Zend/Cache.php on line 208
[Fri Apr 12 23:31:11 2013] [error] [client 66.249.76.177] PHP Fatal error:  Uncaught exception 'Zend_Cache_Exception' with message 'cache_dir is not writable' in /home/ca/public_html/Zend/Cache.php:208
Stack trace:
#0 /home/ca/public_html/Zend/Cache/Backend/File.php(157): Zend_Cache::throwException('cache_dir is no...')
#1 /home/ca/public_html/Zend/Cache/Backend/File.php(121): Zend_Cache_Backend_File->setCacheDir('/home/ca/public...')
#2 /home/ca/public_html/Zend/Cache.php(152): Zend_Cache_Backend_File->__construct(Array)
#3 /home/ca/public_html/Zend/Cache.php(93): Zend_Cache::_makeBackend('File', Array, false, false)
#4 /home/ca/public_html/includes/classes/class.cache.php(58): Zend_Cache::factory('Core', 'File', Array, Array)
#5 /home/ca/public_html/includes/classes/class.cache.php(162): cache->cache(1)
#6 /home/ca/public_html/mainfile.php(204): require_once('/home/ca/public...')
#7 /home/ca/public_html/modules.php(43): require_once('/home/ca/public...')
#8 {main}
  thrown in /home/ca/public_html/Zend/Cache.php on line 208
[Fri Apr 12 23:31:38 2013] [error] [client 66.249.76.177] File does not exist: /home/ca/public_html/Evo-Calendar_-_m_-_08_-_d_-_15_-_y_-_-0026_-_op_-_month.html
[Fri Apr 12 23:31:38 2013] [error] [client 66.249.76.177] PHP Fatal error:  Uncaught exception 'Zend_Cache_Exception' with message 'cache_dir is not writable' in /home/ca/public_html/Zend/Cache.php:208
Stack trace:
#0 /home/ca/public_html/Zend/Cache/Backend/File.php(157): Zend_Cache::throwException('cache_dir is no...')
#1 /home/ca/public_html/Zend/Cache/Backend/File.php(121): Zend_Cache_Backend_File->setCacheDir('/home/ca/public...')
#2 /home/ca/public_html/Zend/Cache.php(152): Zend_Cache_Backend_File->__construct(Array)
#3 /home/ca/public_html/Zend/Cache.php(93): Zend_Cache::_makeBackend('File', Array, false, false)
#4 /home/ca/public_html/includes/classes/class.cache.php(58): Zend_Cache::factory('Core', 'File', Array, Array)
#5 /home/ca/public_html/includes/classes/class.cache.php(162): cache->cache(1)
#6 /home/ca/public_html/mainfile.php(204): require_once('/home/ca/public...')
#7 /home/ca/public_html/modules.php(43): require_once('/home/ca/public...')
#8 {main}
  thrown in /home/ca/public_html/Zend/Cache.php on line 208
[Fri Apr 12 23:31:49 2013] [error] [client 66.249.76.177] PHP Fatal error:  Uncaught exception 'Zend_Cache_Exception' with message 'cache_dir is not writable' in /home/ca/public_html/Zend/Cache.php:208
Stack trace:
#0 /home/ca/public_html/Zend/Cache/Backend/File.php(157): Zend_Cache::throwException('cache_dir is no...')
#1 /home/ca/public_html/Zend/Cache/Backend/File.php(121): Zend_Cache_Backend_File->setCacheDir('/home/ca/public...')
#2 /home/ca/public_html/Zend/Cache.php(152): Zend_Cache_Backend_File->__construct(Array)
#3 /home/ca/public_html/Zend/Cache.php(93): Zend_Cache::_makeBackend('File', Array, false, false)
#4 /home/ca/public_html/includes/classes/class.cache.php(58): Zend_Cache::factory('Core', 'File', Array, Array)
#5 /home/ca/public_html/includes/classes/class.cache.php(162): cache->cache(1)
#6 /home/ca/public_html/mainfile.php(204): require_once('/home/ca/public...')
#7 /home/ca/public_html/modules.php(43): require_once('/home/ca/public...')
#8 {main}
  thrown in /home/ca/public_html/Zend/Cache.php on line 208

```

---

