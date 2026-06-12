---
title: "How can I work on phpbb3 forum in local?"
date: 2008-08-27
forum: Programming Talk
---

### Post by Roman10 on 2008-08-27
I have yet installed apache, php, mysql and downloaded phpbb3... but I don't know how I install and work on it.

:(

---

### Post by KIAaze on 2008-09-02
I just tried and managed to install phpbb2 and phpbb3 locally.

[SIZE="5"]_phpBB2 installation:_[/SIZE]
For phpbb2, the debian packages work well and all you need to do is follow this tutorial:
[https://help.ubuntu.com/community/PhpBB2](https://help.ubuntu.com/community/PhpBB2)

[SIZE="5"]_phpBB3 installation:_[/SIZE]
However, for phpbb3, it doesn't work at all.
But it's very easy to install it from source.

_before phpBB installation:_
1)The phpBB installation process will ask you for a database name, database user and password.
So you will need to set those up first.
The easiest way is to use phpMyAdmin.
```
sudo apt-get install phpmyadmin
```
2)Then go to [http://localhost/phpmyadmin/](http://localhost/phpmyadmin/) in your browser.
3)Go to "privileges"
4)Click on "Add a new user"
5)Enter a username and password (username could be "phpbb3" for example)
6)Select the option "Host: Local"
7)Select the option "Create database with same name and grant all privileges"
8 ) Click "Go"

_phpBB installation:_
1) Download latest release from [http://www.phpbb.com/](http://www.phpbb.com/)
2) Extract it to "/var/www" so that you have a "/var/www/phpBB3" directory.
3)
```
cd /var/www/phpBB3
sudo chmod 777 store/ cache/ files/ images/avatars/upload/
sudo chmod 666 config.php

```
4) Go to [http://127.0.0.1/phpBB3/install/](http://127.0.0.1/phpBB3/install/) in your browser.
5) Click on "Install" and follow the instructions.
6) Once you're done:
```
cd /var/www/phpBB3
sudo rm -rf install
sudo chmod 644 config.php

```
7) Now go to [http://127.0.0.1/phpBB3](http://127.0.0.1/phpBB3) in your browser and start administering. :)

_Notes for the database configuration step:_
You may leave everything by default.
The only necessary infos are:
-Database name
-Database username
-Database password

If you followed the instructions above with phpmyadmin, the database name and username are the same.

---

### Post by isterios on 2008-12-04
Thanks a lot KIAaze for your post.

After months of fighting, it finally works thanks to your post.

Great ;)

---

