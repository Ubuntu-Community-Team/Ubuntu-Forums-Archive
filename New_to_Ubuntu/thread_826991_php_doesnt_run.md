---
title: "php doesnt run"
date: 2008-06-12
forum: New to Ubuntu
---

### Post by witash on 2008-06-12
I tried to reinstall apache2 and php5. apache2 works, but now, when i try to  run php bash tells me command not found! I tired installing just php5 by itself, but this does nothing. Any help?

---

### Post by Cypher on 2008-06-12
Install the PHP5 Module for Apache with
```

sudo apt-get install libapache2-mod-php5

```
This will now install the correct module for Apache, then create your test PHP file with the following
```

cd /var/www
sudo cat "<? phpinfo.php ?>" > test.php

```
Now point your browser to [http://localhost](http://localhost) and you should get "It Works", then point it to [http://localhost/test.php](http://localhost/test.php) and you should get info about the PHP version installed plus additional info.

PHP is a web-based scripting language, you do not execute it from the BASH command line like Python/Perl or something..

---

### Post by witash on 2008-06-12
I have already done all that. when i go to the test page, the browes asks if i want to download the file (like i would expect if php is npt working). And i may be mistaken, but i thought that although running php form the command line is not the USUAL way it is used, it is still possible.

---

### Post by hyper_ch on 2008-06-12
```

sudo a2enmod php5

```

---

### Post by Titan8990 on 2008-06-12
Check this thread: [http://ubuntuforums.org/showthread.php?t=796407](http://ubuntuforums.org/showthread.php?t=796407).

I had a similar issue and the problem turned out to be my /etc/hosts file.

If you input your local ip address instead of localhost can you view that php page?

---

### Post by witash on 2008-06-12
okay, so a2enmod php5 was apparently what i needed, since the test page now works. HOWEVER bash still tells me the command php is not found. This is a problem, since i need to run a php script. i did this the ther day, and im pretty sure that the command i used was php [name-of-script].php and this worked

---

### Post by forger on 2008-06-12
you could try installing php5-cli
> $ php -a
Interactive shell

php > echo "Hello!\n";
Hello!
php > exit


---

### Post by hyper_ch on 2008-06-12
yeah, to run php scripts from the cli you need the php5-cli packages and then you can just:

```

php file.php

```

---

### Post by witash on 2008-06-12
ok, the problem was i did not install the php5-cli package. Thank you for your help!

---

