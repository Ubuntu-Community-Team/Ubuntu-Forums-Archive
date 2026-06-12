---
title: "php"
date: 2008-07-27
forum: New to Ubuntu
---

### Post by sudeepk on 2008-07-27
When i open php file from my monzila it is asking me wheather to download or open with.. but i need to see my files in my browser . what should i do?

---

### Post by hansdown on 2008-07-27
> **sudeepk said:**
> When i open php file from my monzila it is asking me wheather to download or open with.. but i need to see my files in my browser . what should i do?

Hi sudeepk. If you click on "open with" ,and choose one of the options, you will be able to look at it in the browser.

---

### Post by sudeepk on 2008-07-27
actually how can i see the php files in the browser like i see the html files,.

---

### Post by freak42 on 2008-07-27
does it happen with all php files everywhere on the net or just with php files on one web-site?

---

### Post by sudeepk on 2008-07-27
it happens to all the php files which are in my hard drive . i use apache2

---

### Post by Ryadt on 2008-07-27
You will have to install something like LAMP or XAMPP.

---

### Post by Samhain13 on 2008-07-27
Does opening mean doing File > Open > thefile.php?
Or does it mean going to the address bar and typing [http://localhost/thefile.php?](http://localhost/thefile.php?)
In the former, the behaviour you describe is expected.

---

### Post by sudeepk on 2008-07-27
i have tried both ways but still its asking me wheather to download or open.

---

### Post by Samhain13 on 2008-07-27
Right. Apart from Apache2, do you have libapache2-mod-php5 and php5-common installed? You can check that through System > Administration > Synaptic Package Manager and do a search for "php".

If you already have those packages, try restarting Apache2. This might be helpful:
[http://ubuntuguide.org/wiki/Ubuntu:Hardy#Install_a_LAMP_server_on_a_Desktop](http://ubuntuguide.org/wiki/Ubuntu:Hardy#Install_a_LAMP_server_on_a_Desktop)

---

### Post by sudeepk on 2008-07-27
i already installed the above files but when i tried to restart apache its saying 

"apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName"

---

### Post by Samhain13 on 2008-07-27
Ah, that message is normal if you don't have a qualified domain name.
But now I'm out of suggestions. :(

---

### Post by sudeepk on 2008-07-27
actually how do u see your php output?

---

### Post by lordadi on 2008-07-27
change [http://localhost/XYZ/](http://localhost/XYZ/) to [http://127.0.1.1/XYZ/](http://127.0.1.1/XYZ/) and it should work.

---

### Post by Samhain13 on 2008-07-27
How do you see your PHP output? Well, for starters, if you have

[php]
<?php
echo "<p>Hello, world.</p>" ;
?>
[/php]

in a file called file.php in the /var/www/ directory; then you open it in your browser using [http://localhost/file.php](http://localhost/file.php), your browser should say "Hello, world.".

---

### Post by Ryadt on 2008-07-27
I can only see my php output if I start XAMPP ( in my case). I still have to save my php files in /opt/lamp/xampp/htdocs directory for me to be able to view them.

---

### Post by sudeepk on 2008-07-27
is this correct way to view a php file?
1. Write the code and save as a php file in /var/www
2. To view the php file, go to monzilla and type localhost/filename.php

if that is the correct procedure, then why i am i getting the option to save it or to open it?

---

### Post by Samhain13 on 2008-07-27
Yup, it's supposed to be that simple (with [http://](http://) in #2).
And that is why we have a problem.

---

### Post by sudeepk on 2008-07-27
can any one please suggest me gui tool for working with php and mysql to develop a website?

---

### Post by Ryadt on 2008-07-27
> **sudeepk said:**
> can any one please suggest me gui tool for working with php and mysql to develop a website?

I use xampp cause I find it real easy. [http://www.apachefriends.org/en/xampp-linux.html](http://www.apachefriends.org/en/xampp-linux.html)
You can try LAMP which is in repos if you prefer.

---

### Post by Samhain13 on 2008-07-27
^But isn't sudeepk already on LAMP?

---

### Post by sudeepk on 2008-07-27
thanx a lot i will try those . but please any one help me out how to manually see the php files from the browser.

---

### Post by Ryadt on 2008-07-27
I am pretty sure that you will have to install one of these webservers to be able to view a php file.

---

### Post by RuleMaker on 2008-07-27
Download LAMPP, install it by:
```
sudo tar xvfz file_name -C /opt
```
Then any php file you have need to be placed in /opt/lamp/htdocs to be able to show it in browser.
Server must be started, you can do it by:
```
sudo /opt/lampp/lampp start
```

If you dont plan to use LAMPP as a web server you can chmod the htdocs directory to enable any user to write and read from it:
```
sudo chmod a+x+w+r /opt/lampp/htdocs
```

Also, I recommend you tu use "Quanta" as your php editor, you can install it from Synaptic.

---

### Post by ceclauson on 2008-07-27
I had the same problem myself.  It means that you don't have apache set up correctly.

Check this out:
[http://ubuntuforums.org/showthread.php?t=845916](http://ubuntuforums.org/showthread.php?t=845916)

---

### Post by forger on 2008-07-27
> **sudeepk said:**
> thanx a lot i will try those . but please any one help me out how to manually see the php files from the browser.

you could try my proposal without apache2 installed, if it's a simple php:
[http://medigeek.blogspot.com/2008/07/how-to-run-simple-local-php-script.html](http://medigeek.blogspot.com/2008/07/how-to-run-simple-local-php-script.html)

---

### Post by halitech on 2008-07-27
if you simply type in [http://localhost](http://localhost) or [http://127.0.0.1](http://127.0.0.1) do you get the default apache page? if you do, you don't need to install apache and you are looking at an issue where php files are not associated in apache as a valid file so it will not send the correct info to firefox and thus will ask you to save the file.

---

### Post by lordadi on 2008-07-28
Hi Sudeepk,

If you want to parse php files (for example the hello world example above) you will have to save the file (for example: test.php) to /var/www/ then in mozilla firefox type in [http://127.0.1.1/test.php](http://127.0.1.1/test.php) and it should work.

This is because your computer now uses 127.0.1.1 as the server address instead of 127.0.0.1 (remember the message you posted?)

A good gui text editor with php centric features is geany (if you use gnome) or quanta for KDE.

Let me know if there are issues.

Cheers,


Lordadi.

---

### Post by halitech on 2008-07-28
> **sudeepk said:**
> i already installed the above files but when i tried to restart apache its saying 

"apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName"

Simply add this line anywhere to your /etc/apache2/apache2.conf file:

```

ServerName  localhost
```
you'll also need to restart apache
```
sudo /etc/init.d/apache2 restart
```

---

### Post by halitech on 2008-07-28
also, did y ou follow a guide like this to make sure everything was installed?

[http://ubuntuguide.org/wiki/Ubuntu:Hardy#Simple_LAMP_server_Setup](http://ubuntuguide.org/wiki/Ubuntu:Hardy#Simple_LAMP_server_Setup)

---

### Post by sujoy on 2008-07-28
see the "Configure PHP" section [here]("http://wiki.archlinux.org/index.php/LAMP"), hope it helps.

---

