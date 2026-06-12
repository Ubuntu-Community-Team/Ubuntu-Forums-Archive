---
title: "XAMPP: MySQL connection problem"
date: 2007-05-21
forum: Programming Talk
---

### Post by jingo811 on 2007-05-21
I'm still learning how to use WAMP in a course. So I don't really know what needs to be done the LAMP way? Since XAMPP is kind of set in stone regarding certain behaviours I know even less what to do in order to make it work in Linux?

In the course I just follow instructions how to install MySQL then the part where you test the Database with **Windows CMD** you're supposed to check these things.

To see if the server is running.
```
c:\> mysqladmin -u root -p ping
```


To print out the version number for MySQL server.
```
c:\> mysqladmin -u root -p version
```


To check how long the server has been online.
```
c:\> mysqladmin -u root -p status
```


None of those simple commands seem to work with XAMPP on Linux
```


mike@sanka:~$** lamp_start**
Starting XAMPP for Linux 1.6.1...
XAMPP: Another web server daemon is already running.
XAMPP: XAMPP-MySQL is already running.
XAMPP: XAMPP-ProFTPD is already running.
XAMPP for Linux started.

mike@sanka:~$ **mysqladmin -u root -p ping**
Enter password:
[COLOR="Red"]mysqladmin: connect to server at 'localhost' failed
error: 'Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)'
Check that mysqld is running and that the socket: '/var/run/mysqld/mysqld.sock' exists![/COLOR]
mike@sanka:~$



```


```

mike@sanka:~$ **lamp_stop**
Stopping XAMPP for Linux 1.6.1...
XAMPP: XAMPP-Apache is not running.
XAMPP: Stopping MySQL...
XAMPP: Stopping ProFTPD...
XAMPP stopped.

mike@sanka:~$ **mysqladmin -u root -p ping**
Enter password:
[COLOR="Red"]mysqladmin: connect to server at 'localhost' failed
error: 'Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)'
Check that mysqld is running and that the socket: '/var/run/mysqld/mysqld.sock' exists![/COLOR]
mike@sanka:~$


```





What am I doing wrong?
The password is supposed to be empty it says on the webpage but still it won't work?

---

### Post by jingo811 on 2007-05-21
hmm... it seems I've broken XAMPP from earlier experimentations with a malfunction Drupal install and removal via Synaptic.
Just as well, XAMPP support is really bad.  Guess I should install LAMP like a real man now instead.

Does anybody have any Aptitude or Apt-get instructions for installing: Apache+ PHP+ MySQL?
I only know how to install those 3 packages on Windows XP don't know where to begin with Linux?
Help plz.

---

### Post by DouglasAWh on 2008-03-17
I'm sure this is resolved or given up on, but using apt-get is real easy:

```

sudo apt-get install $nameOfProgram

```

maybe there's some weird tag like php-lib or something...well, just search apt-cache first

```

sudo apt-cache search $whatever

```

---

