---
title: "how to uninstall POSTGRE in my system by force or any process.."
date: 2008-10-02
forum: New to Ubuntu
---

### Post by rybaxs on 2008-10-02
everything i've installed and download postgre error occur, system found some crash reports. I think postgre is crash.. 

this is what happen every time Im installing, accessing, starting and uninstalling.

Installing Postgre by force
```

user@user-desktop:/$ sudo apt-get install -f postgresql-8.3
Reading package lists... Done
Building dependency tree       
Reading state information... Done
postgresql-8.3 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
2 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up postgresql-8.3 (8.3.3-0ubuntu0.8.04) ...
 * Starting PostgreSQL 8.3 database server                                       * pg_controldata: could not open file "/var/lib/postgresql/8.3/main/global/pg_control" for reading: Permission denied
Error: Could not parse locale out of pg_controldata output
                                                                         [fail]
invoke-rc.d: initscript postgresql-8.3, action "start" failed.
dpkg: error processing postgresql-8.3 (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of postgresql:
 postgresql depends on postgresql-8.3; however:
  Package postgresql-8.3 is not configured yet.
dpkg: error processing postgresql (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 postgresql-8.3
 postgresql
E: Sub-process /usr/bin/dpkg returned an error code (1)

```


Starting the crash postgre
```

user@user-desktop:/$ sudo /etc/init.d/postgresql-8.3 start
 * Starting PostgreSQL 8.3 database server                                       * pg_controldata: could not open file "/var/lib/postgresql/8.3/main/global/pg_control" for reading: Permission denied
Error: Could not parse locale out of pg_controldata output
                                                                         [fail]
user@user-desktop:/$ 


```

Running Postgre
```

user@user-desktop:/$ psql
psql: could not connect to server: No such file or directory
	Is the server running locally and accepting
	connections on Unix domain socket "/var/run/postgresql/.s.PGSQL.5432"?
user@user-desktop:/$ 

```


Help.. its my 4th day solving this simple unsolvable problem.

---

### Post by rybaxs on 2008-10-02
more crashes on my System.. Is it good to upgrade your Ubuntu 7.10 to 8.04?

---

### Post by rybaxs on 2008-10-02
I would try navigating to something like /etc/postgres or something similar. Somewhere in this folder should be a file called server.key.

The error is telling you that the permissions on the file are wrong. Try a

```

sudo chmod 700 server.key

```
This should change the permissions of the file to what the postgres daemon expects.

If you can't find the file...

```


sudo updatedb
locate server.key

```

Perform the chmod on that file and you should be in business.

To see if the above worked, do a
HTML 

```

sudo /etc/init.d/postgresql start

```

I'm not sure of the postgresql part, but if you type post and then hit tab a few times it should get you going.


from: ifeldt

---

### Post by rybaxs on 2008-10-02
```

user@user-desktop:/opt/lampp/etc/ssl.key$ sudo /etc/init.d/postgresql-8.3 start
 * Starting PostgreSQL 8.3 database server                                                                    * pg_controldata: could not open file "/var/lib/postgresql/8.3/main/global/pg_control" for reading: Permission denied
Error: Could not parse locale out of pg_controldata output
                                                                                                      [fail]
user@user-desktop:/opt/lampp/etc/ssl.key$ 

```

---

### Post by hansdown on 2008-10-02
Hi rybaxs.

Without knowingb what version you are using, I could only do a wide search.

[http://www.google.ca/search?q=acidlab-+pgsql&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:unofficial&client=firefox-a](http://www.google.ca/search?q=acidlab-+pgsql&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:unofficial&client=firefox-a)

---

### Post by rybaxs on 2008-10-08
> **hansdown said:**
> Hi rybaxs.

Without knowingb what version you are using, I could only do a wide search.

[http://www.google.ca/search?q=acidlab-+pgsql&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:unofficial&client=firefox-a](http://www.google.ca/search?q=acidlab-+pgsql&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:unofficial&client=firefox-a)

version of psql? 8.2 8.1 and 8.3

thanks, I've already solve the problem.. 
syntax error.. :mad:

---

### Post by ibert on 2008-11-17
Can you share how you solved the problem?

thanx
ibert

---

