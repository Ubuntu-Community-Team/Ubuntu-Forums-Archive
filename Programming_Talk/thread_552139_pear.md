---
title: "pear"
date: 2007-09-16
forum: Programming Talk
---

### Post by fascigo1618 on 2007-09-16
I am running ubuntu 7.04 with lampp 1.6.3b
i require MDB2 and the mysql driver for mdb2, but i have no internet connection on that pc. so i downloaded the files and wrote the following command:
>>pear install /media/memorycard/MDB2.tgz
it gives the following error:
>>bash: pear: command not found
i tried it with both starting and stoppiing xampp
same error please help

---

### Post by Compyx on 2007-09-16
Looks like you don't have 'php-pear' installed:
```

compyx@gutsy:~$ apt-file search pear | grep 'pear$'
dh-make-php: usr/bin/dh-make-pear
dh-make-php: usr/bin/dh-make-pear
dh-make-php: usr/bin/dh-make-pear
php-pear: usr/bin/pear
php-pear: usr/bin/pear
php-pear: usr/bin/pear
php-pear: usr/share/doc/php-pear
php-pear: usr/share/doc/php-pear
php-pear: usr/share/doc/php-pear
compyx@gutsy:~$ 

```

So perhaps a simple:
```

sudo apt-get install php-pear

```
would solve your problem.

But then again you mention you don't have an internet connection, which also kind of defeats the purpose of a web-server ;)

---

### Post by fascigo1618 on 2007-09-16
I solved the problem.
i had to use the following
Step 1:
>>cd /
>>find / -name "pear"
>>sudo ln /path/to/pear /usr/bin/pear
:guitar:

---

### Post by mizar001 on 2008-11-19
I want to clarify some things. 

Using lampp implies that all software (apache, php, mysql) are under a specific directory. Usually the most used folder is /opt/lampp. 

So the php,mysql,httpd,pear commands are all under /opt/lampp/bin

Linking in /usr/bin without knowing that can lead to wrong programs to be executed, probably by some other applications. Sometimes these softwares are installed as package from the repositories, so their binaries are in /usr/bin. Be carefully conscious of what you do.

---

