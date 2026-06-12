---
title: "Strange PHP Error in Breezy After Upgrade"
date: 2005-11-24
forum: Programming Talk
---

### Post by SuperMike on 2005-11-24
After upgrading from Hoaring to Breezy, my PHP4 is acting very strange. I was getting "what do you want me to do with this file?" type Firefox popups whenever I hit a PHP page. So, I thought something was botched with my PHP4, so I tried first upgrading to PHP5. I did this and it worked. I was able to view my test.php file just fine in Firefox. So then I downgraded to PHP4 and rebooted. (At least, I think I rebooted, but am not 100% certain.) I found the test.php file worked just fine.

Well, this morning, I rebooted again so that I could show a friend the new Ubuntu boot screen, which is different. Unfortunately, however, PHP4 or Apache is broke again. I cannot view my test.php file. However, I see Apache running in memory because I can hit the default Apache website.

I tried PHP command line and it works just fine, so something's up with the binding between Apache or PHP4, or perhaps I have my directory security incorrect?

In Ubuntu, in order to add a new PHP website, I just create a symbolic link to my web folder inside /var/www. And even though I do this under the root ID, it seems to work just fine. Well, at least it /used/ to work.

Please help? :confused:

---

### Post by SuperMike on 2005-11-25
It's like libapache2-mod-php5 or libapache2-mod-php4 is not being properly installed or something. That's what it seems like.

What is up with Breezy and PHP? Is there a known bug here?

---

### Post by oskude on 2005-11-25
[QUOTE=SuperMike]I was getting "what do you want me to do with this file?" type Firefox popups whenever I hit a PHP page.[/QUOTE]sounds like this is missing```
AddType application/x-httpd-php .php
```in your apache configs...

---

### Post by SuperMike on 2005-11-25
What a bunch of weirdness I just experienced! I've been out of this forum for like 3-4 hours fighting with this. I wanted to let you PHPers know what I had to do to get it to work in case you encounter this. I got PHP4, Apache2, and PostgreSQL to work well together again in Breezy.

1. I had to use Synaptic and tell it to "Mark for full removal" all my PHP4 and Apache2 stuff.
2. I had to ensure 100% it properly deleted anything PHP4 or Apache2 off my hard drive. 
3. I deleted and recreated my www-data user and group, just in case. Note that you can go with defaults on this, but you don't need to give it any rights or home directories in the Users and Groups Control Panel. Note also that if you delete this, the re-installation of Apache will *NOT* put it back. You have to do it yourself.
4. I deleted /var/www just in case -- the install would recreate it.
5. I used Synaptic and merely checked off PHP4. It prompted me that it needed to install the rest and I let it. I didn't push it though -- I left behind a bunch of other necessary stuff because I didn't trust this to go through smoothly.
6. This didn't work the first time I did this. I had to repeat this process in steps 1 and 5 multiple times until it worked in Firefox. But at least I finally got it to work. The downside, oddly enough, was that my Images subfolder had some kind of security problem and it wouldn't read the images. And all I did on the Images folder to fix it was remove and reapply the existing u, g, o security attributes that were there previously. Go figure. Anyway, my images came back to life after that.
7. Using Synaptic, I added back in the other php4 extensions, one by one, bouncing the Apache2 server in between, just in case.
8. When I got to php4-pgsql, it would install and say it was installed, but didn't work when you tested it in a web page.
9. I had to uninstall and reinstall it about 5 times through Synaptic before it finally just went through properly and I could execute PostgreSQL code.

So I'm dumbfounded why, using apt or Synaptic, I got different results each time I did this. My only hunch is that Canonical has some sort of web farm with the PHP4 and Apache2 software on it, and that perhaps some of these servers are suspect?? I really have no idea at this point and that's the only thing that makes some kind of sense.

---

### Post by SuperMike on 2005-11-25
[QUOTE=oskude]sounds like this is missing```
AddType application/x-httpd-php .php
```in your apache configs...[/QUOTE]

Yep. However, when "apt" works great, it fixes this for you. And that's just what happened after I repeated the process of uninstalling and reinstalling, over and over, until I got this to work.

---

### Post by Tuxbee on 2005-11-25
Same here.
Been working 2 hours on this now. No joy yet :(

---

### Post by SuperMike on 2005-11-25
[QUOTE=Tuxbee]Same here.
Been working 2 hours on this now. No joy yet :([/QUOTE]

Ah, so it's not me going crazy. Okay, something is up. I can't say it's a bugzilla thing with Ubuntu's install because we all finally manage to get it working EVENTUALLY if we keep playing with it, redoing the order, etc. I think it has to do with some sort of problem in the Canonical web farm that we pull the install images from -- they're likely not consistent. And that's if I'm a bettin' man.

---

### Post by SuperMike on 2005-11-25
[QUOTE=Tuxbee]Same here.
Been working 2 hours on this now. No joy yet :([/QUOTE]

Another note. Someone in the Usenet newsgroups said that if we uninstall PHP5 and go to PHP4, but don't reboot between sessions, even if we bounce Apache, we *might* have the PHP INI file cached in RAM. That's her theory, at least. Don't know if she's right or not.

Anyway, that was option # 2 for why we're seeing this ghost-in-the-machine kind of random effect here where if you run the same uninstall / reinstall steps multiple times it finally just "takes" and works.

Good luck, Tuxbee. I'm rooting for you.

---

