---
title: "Messed up my PHP, please help"
date: 2012-03-27
forum: New to Ubuntu
---

### Post by CamChev on 2012-03-27
Hi, I hope someone can help me here, I have made a mess of my php installation and I think I need to remove it completely and start again, here's what happened.
Using Ubuntu 10.4 via putty on a dedicated server. fresh install, installed mono, mysql, nano, and went for php.....

I am using a process which doesnt like PHP5.3 and the makers say it must be run with PHP 5.2, but I could not find 5.2 in the rep, so I compiled my own 5.2.9 (yeah ambitious I know) I have compiled many programs before in Windows using visual studio so I thought I could handle it, but I havent had a lot of experience with Linux, sooo
it compiles ok, make and install, but wont run, restart of apache fails, phpinfo() wants to download instead of display, google search found this..
# cd /etc/apache2/mods-available
Create a new file called php5.load and paste the following line into it:
# LoadModule php5_module /usr/lib/apache2/modules/libphp5.so
and
Now create another file called php5.conf and paste the following into it: AddType application/x-httpd-php .php .phtml .php3
 AddType application/x-httpd-php-source .phps
save that
# a2enmod php5
 Enabling module php5.

 Run ‘/etc/init.d/apache2 restart’ to activate new configuration!
 # /etc/init.d/apache2 restart
 * Restarting web server apache2
computer says nooooo, no such file as libphp5.so

so to cut what could be a really long post short, (something I read said to purge and reinstall libapache2-mod-php5) but it says libapache2-mod-php5 is not installed, so I installed it, and something broke, now restarting apache results in...

(13)Permission denied: make_sock: could not bind to address 0.0.0.0:80
no listening sockets available, shutting down
Unable to open logs

I have no idea where to go from here,
I feel sick, can somebody pleeeease help.
Cam

---

### Post by shubham1 on 2012-03-27
completely purge php this can be done using synapathic package manager mark it for complete removal
here is the php downloads archive for ubuntu [http://packages.ubuntu.com/lucid/php/](http://packages.ubuntu.com/lucid/php/)
what about upgrading your php to latest version by using synapathic package manager

---

### Post by SeijiSensei on 2012-03-27
> **CamChev said:**
> 
Create a new file called php5.load and paste the following line into it:
# LoadModule php5_module /usr/lib/apache2/modules/libphp5.so

That module was probably not installed to /usr/lib/apache2/modules if you built PHP from scratch.  Chances are it is somewhere in /usr/local.

Try running the commands

```

sudo updatedb
[wait until it finishes]
locate libphp5.so

```

The locate command should report the complete path name for libphp5.so.  Use that in the LoadModule directive instead.

---

### Post by CamChev on 2012-03-27
Thank you both for the replies,
After server restart that file mysteriously appeared in the right place, some changes to the php5.conf and apache restart, and ....drumroll.... apache starts with no errors and php is running, I really dont know what I did but its working, only problem is it is version 5.3.2 and I really needed 5.2.X
I think it was when I ran apt-get install  [FONT=Verdana]libapache2-mod-php5
I really need to downgrade unless my software devs sort out this issue, or php5.4 has fixed the issue that 5.3 broke from 5.2 (if that makes any sense) but there seems to be lots of stuff on forums about downgrading from 5.3 to 5.2 so I am not alone here.
But this issue of completely messed up PHP is solved.
Again Thank you
Cam
[/FONT]

---

