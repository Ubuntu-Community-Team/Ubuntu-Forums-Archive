---
title: "changing the login manager"
date: 2013-12-08
forum: New to Ubuntu
---

### Post by codenine75a on 2013-12-08
I installed Kubuntu 13.10 and I did not like the login manager because kdm did not have a default login user by default.  Now I know it probably can be configured but I ventured forward with my instinct.  I used the google search engine for login managers and found one called "slim".  

I installed it with
>sudo apt-get install slim
It asks for what default login manager I wanted to use so I chose slim.
I rebooted it and up came the new login manager but I had to type in my user name in the input field so I had to look in the docs
reference: [http://slim.berlios.de/manual.php](http://slim.berlios.de/manual.php)

I found out the configuration file is not under /usr.  It is under /etc/slim.conf
so I used my favorite text editor and typed this in
>sudo kate /etc/slim.conf

I edited the config file like this example by taking out the hash or pound symbol ('#')
..
# default user, leave blank or remove this line
# for avoid pre-loading the username.
default_user        babsbunny
..

I then rebooted and it filled out the input user name field so all I have to do is enter the user password.

If you do this and want to revert back to kdm just reinstall it.

---

### Post by oldos2er on 2013-12-08
Kubuntu uses lightdm by default. Also you don't need to reinstall a display (i.e. login) manager to revert to it, assuming you didn't uninstall it; you can run ```
sudo dpkg-reconfigure lightdm
```

---

