---
title: "[SOLVED] phpMyAdmin problem - Ubuntu Desktop LAMP"
date: 2008-10-06
forum: New to Ubuntu
---

### Post by dESAI on 2008-10-06
Hi all,

Situation
I'm a noob, not good with terminal :(
New install of Ubuntu.
LAMP pakage installed.
localhost directed to : /home/username/www/
phpinfo.php test successful :)

Now I need to get phpMyAdmin working.

when I enter
[http://localhost/phpMyAdmin/scripts/setup.php](http://localhost/phpMyAdmin/scripts/setup.php) in Firefox I get:


"Can not load or save configuration
Please create web server writable folder config in phpMyAdmin toplevel
directory as described in documentation. Otherwise you will be only able
to download or display it.

I'm stuck. 

I think I need to change user rights, but I have no idea how. 

I have already changed the root and my password to the same, in the hope it might help. But I think that was the wrong path to take.

I await your wisdom.

Thanks all :)

D

---

### Post by zephyrcat on 2008-10-06
It sounds like you can just create a folder called "config" in the phpmyadmin folder.

---

### Post by dESAI on 2008-10-06
> **zephyrcat said:**
> It sounds like you can just create a folder called "config" in the phpmyadmin folder.

I did, no change :(

---

### Post by zephyrcat on 2008-10-06
Oops. Sorry, I missed the writable part. Find the config folder you created (you may have to do this as root by typing "gksudo nautilus" into the Terminal), right click on it and chose properties. Then go to permissions and change them so that all groups can read and write to the folder. If you are setting up a real server, you may want to be more careful with permission than that, but you would have to ask someone else about that.

---

### Post by dESAI on 2008-10-06
> **zephyrcat said:**
> Oops. Sorry, I missed the writable part. Find the config folder you created (you may have to do this as root by typing "gksudo nautilus" into the Terminal), right click on it and chose properties. Then go to permissions and change them so that all groups can read and write to the folder. If you are setting up a real server, you may want to be more careful with permission than that, but you would have to ask someone else about that.

That did the trick :D

1,000,000 thanks!!

---

