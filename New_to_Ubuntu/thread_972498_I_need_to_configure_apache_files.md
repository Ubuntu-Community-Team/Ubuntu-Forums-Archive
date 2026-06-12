---
title: "I need to configure apache files??"
date: 2008-11-05
forum: New to Ubuntu
---

### Post by Lakeside on 2008-11-05
I need to ask, is there some more work or configuring of files I need to do, in order to see my Joomla installation page at  [http://localhost/Joomla?](http://localhost/Joomla?) Because going there now, doesn`t load a page, and having just the localhost-  [http://127.0.0.1](http://127.0.0.1) just shows the Apache server directory, with the Joomla folder, and another test folder in it.  When I click on that folder, this is what occurs, according to someone else trying to help with this:  `If you are being asked to download the index.php when you try to access the "Joomla/" directory this tends to suggest that Apache and PHP are not correctly configured to run .php files. This would most likely be a missing "filetype" handler in the Apache configuration`  So far, I am just still trying to install Joomla, and haven`t configured any files I don`t think. Anyone think they know what I am missing? So far with help, I have managed to create a Joomla folder, give it proper permissions, put it in the var/www directory (webserver`s virtual directory). I just need to access the installation page. thanks for help in advance

---

### Post by Cypher on 2008-11-05
By default, if you install Apache2 on your machine, if you go to [http://localhost](http://localhost), you should get the message OK!. That means that Apache is working.

You will then want to install PHP and MySQL because Joomla needs those two. Then download Joomla and place it in the /var/www/joomla directory and now you can get to it from [http://localhost/joomla](http://localhost/joomla)..

---

### Post by Lakeside on 2008-11-05
Wow you`re quick! thanks :) Your were posting while I was editing. What`s weird is, when I first installed Apache, right after installing Hardy Heron on here, I did see that  `It Works!`message at localhost.
Then I started messing around I guess, and now I see the other thing.
I think I must have uninstalled the other things, so I will go check now.  thanks very much

---

### Post by Cypher on 2008-11-05
I would follow the instructions in [this guide]("https://help.ubuntu.com/community/ApacheMySQLPHP") to setup Apache, PHP and MySQL. Scroll down to the appropriate section. You can use the Hardy instructions if you're running Ibex (8.10)..

---

### Post by Lakeside on 2008-11-05
OMG...I`m so happy I might cry (just like last night) I just cleared my browser`s cache, went to localhost and JOOMLA INSTALLATION PAGE!  (only been trying to do this for like a week lol, but then that was installing hardy heron and learning linux and all from scratch). I was starting to think of giving upevenn after all the great (and I MEAN great) help from this forum.  I just read the guide in your link, did a few things (first I re-installed the php and mysql as u were right, they had gotten uninstalled somehow) followed their advice of clearing browser cache (which I always forget to do) and voila! Now I gotta go have fun getting confused with Joomla...so I can bug the people over on that forum :)  Oh, one last question please, this is just a `local server` for development purposes then? And if I actually want a web site `out there` I have to ftp the Joomla files up to my site? Have a good night Cypher (night here)

---

