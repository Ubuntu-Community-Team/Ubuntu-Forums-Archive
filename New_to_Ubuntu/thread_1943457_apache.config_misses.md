---
title: "apache.config misses"
date: 2012-03-19
forum: New to Ubuntu
---

### Post by crowz on 2012-03-19
Hi everybody!

I need you to install Lamp on my Ubuntu 10.10 system. 
Since the beginning, I had a problem with phpmyadmin which asks me a password I couldn't understand, so that I wasn't able to open php files with chrome or mozilla. 
After I tried some "solutions", I got worse than before: I can't run apache2: error 232 /etc/phpmyadmin/apache.conf: no such file or directory. 
I've just to install apache2 two times but it doesn't work!!! same error

---

### Post by TeoBigusGeekus on 2012-03-19
> **crowz said:**
> Hi everybody!

I need you to install Lamp on my Ubuntu 10.10 system. 
Since the beginning, I had a problem with phpmyadmin which asks me a password I couldn't understand, so that I wasn't able to open php files with chrome or mozilla. 
After I tried some "solutions", I got worse than before: I can't run apache2: error 232 /etc/phpmyadmin/apache.conf: no such file or directory. 
I've just to install apache2 two times but it doesn't work!!! same error

The password it asks you should be the password for the mysql account you're trying to access.

---

### Post by crowz on 2012-03-19
Mysql password is blank... anyway in a second time: now is apache my first problem

---

### Post by crowz on 2012-03-19
Found, now I have "It works!" on my localhost.
I did "sudo apt-get remove --purge apache2 apache2-utils"

to remove correctly

and then " sudo apt-get install apache2 "

But I still have to resolve phpmyadmin

---

### Post by crowz on 2012-03-20
What is the best way to install PhpMyAdmin? Synaptic?

---

### Post by raja.genupula on 2012-03-20
[https://help.ubuntu.com/community/phpMyAdmin](https://help.ubuntu.com/community/phpMyAdmin)

---

### Post by crowz on 2012-03-21
When I tried to install phpmyadmin with mysql already installed, I coudln't understand if I had to install the program manually as an advanced database administrator or automatically so that during the process I closed console. In a second time, When I decided to try one way, I realized maybe a nasty bug.
At the moment I am not able to use console with sudo apt-get install phpmyadmin

E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem.

and Synaptic at all:

E: _cache->open() failedsudo apt-get install phpmyadmin
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem., please report.

Well...dio...
:guitar:

---

### Post by mcduck on 2012-03-21
> **crowz said:**
> Mysql password is blank... anyway in a second time: now is apache my first problem

based on the error, it#s not Apapche that;s the problem but phpMyAdmin instead.

(note that the config file mentioned in the error is in phpMyAdmin's directory, no Apache's. )

---

### Post by lisati on 2012-03-21
What happens when you run the following on the command line, as suggested by the error message?
```
sudo dpkg --configure -a
```

---

### Post by crowz on 2012-03-23
Done: "sudo dpkg --configure -a"

I got the phpmyadmin processing installation again. Finished installation I could read:

"Setting up phpmyadmin (4:3.3.7-5build0.10.10.1) ...
dbconfig-common: writing config to /etc/dbconfig-common/phpmyadmin.conf

Creating config file /etc/dbconfig-common/phpmyadmin.conf with new version

Creating config file /etc/phpmyadmin/config-db.php with new version
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place"

Now Synaptic is well, mysql and apache2 are running and phpmyadmin's been installed. Well, how can run the last one?

---

### Post by mcduck on 2012-03-24
Just open a web browser, and go to [http://localhost/phpmyadmin]("http://localhost/phpmyadmin"). :)

---

### Post by crowz on 2012-03-25
I've already tried, but I got:

"Not Found

The requested URL /phpmyadmin/ was not found on this server.

Apache/2.2.16 (Ubuntu) Server at localhost Port 80"

---

