---
title: "php not working on 8.04"
date: 2008-07-27
forum: Programming Talk
---

### Post by TorchlightJay on 2008-07-27
Hello,
   So I have apache2, libapache2-mod-php5, php5 installed on my system. I am trying to do PHP development and then I will try to open my files on Firefox and I get nothing. This the code I entered:

--------------------------
<html>
  <head>
    <title>Look Out World</title>
  </head>

  <body>
    <?php echo "Hello, world!" ?>
  </body>
</html>
--------------------------

and when I open it in firefox as an html, it's blank. If I do it as a php, it asks me to download it. sudo a2emod says that php5 is loaded. I am not sure what's wrong. Any ideas?

---

### Post by Kadrus on 2008-07-27
Have you place your php file in the directory /var/www/
You should go to [http://localhost/](http://localhost/)
and your php files will appear there.
Edit:
And if you the installation is missing
```
sudo tasksel
```
Choose LAMP
or
read the guide [here]("http://ubuntuguide.org/wiki/Ubuntu:Hardy#Install_a_LAMP_server_on_a_Desktop").

---

### Post by BRUUUCE on 2008-07-27
did it work in previous versions? or is this your first time with the OS?

when i first switched to ubuntu, i made the mistake assuming my php scripts would work anywhere. Put them in /var/www/. Another mistake i made was double clicking them there - i would get the same result/prompt. go to brower and type in: localhost

---

### Post by RuleMaker on 2008-07-27
You cant run your php scripts from any location, because not every directory on your computer is affected by the server.
You must put your php script in servers directory, im not sure which it is in your case because I use lampp, in my case it's /opt/lampp/htdocs.
In your case it could be /var/www but I'm really not sure, try it.

---

### Post by TorchlightJay on 2008-07-27
i see. makes sense. This is the first time I've done PHP development on this system. I guess I need to move stuff to the server portion.  Any other possible issues?

---

### Post by TorchlightJay on 2008-07-27
Hey, i just moved it to my server and php is not workig still. LAMP is installed. Any ideas?

---

### Post by slavik on 2008-07-27
make sure the apache config knows about the php type (search google for "addtype php", you should get something). Also for the root directory, you might want to enable ExecCGI option.

---

### Post by TorchlightJay on 2008-07-28
Hello,
   So how do I do the ExecCGI thing?

---

### Post by slavik on 2008-07-28
try google and apache docs :)

---

### Post by ceclauson on 2008-07-28
I might be able to help. I'm running Gutsy, but I just spent a good part of the afternoon getting this to work.

I'll just copy in my configuration file:
```

User ceclauson

ServerName ceclauson
ServerRoot /home/ceclauson/Desktop/website
DocumentRoot /home/ceclauson/Desktop/website/htdocs

Listen localhost:80

IndexOptions FancyIndexing

LoadModule php5_module "/usr/lib/apache2/modules/libphp5.so"

AddType application/x-httpd-php .php

```

In fact, here's a link you can use to just download the whole site:
[http://edison.seattlecentral.edu/~cclaus01/website.zip](http://edison.seattlecentral.edu/~cclaus01/website.zip)

Just unzip it in your desktop, replace all instances of "ceclauson" in conf/httpd.conf with your username, and you should be good.  Run the start.sh and stop.sh scripts in the terminal to start and stop the server.

(P.S., Even though I know I'm trustworthy, you don't.  You probably want to check these scripts first to make sure they don't contain malicious commands)

---

### Post by TorchlightJay on 2008-07-28
Cool, I'll try it. My httpd.conf file is empty, do you guys mean apache2.conf or do I have something screwed up pretty bad?

---

### Post by ceclauson on 2008-07-28
To the best of my knowledge, Apache always looks for a file called httpd.conf for the configuration.

Cooper

---

### Post by mssever on 2008-07-29
Ubuntu's Apache conf is in /etc/apache2/apache2.conf. You can ignore httpd.conf--it's only there for compatibility. Also, if you installed via the normal Ubuntu packages, I can guarantee that the default configuration works--no need to mess with it. Your problem is something else. Have you looked in Apache's logs? Have you examined the response headers?

If you have messed with Apache's configuration, the only relevant lines from ceclauson's config are the LoadModule and AddType lines--both of which should be in /etc/apache2/mods-enabled/php5.*

Also, there's no need to enable ExecCGI if you're using the PHP Apache module, which doesn't use CGI.

---

