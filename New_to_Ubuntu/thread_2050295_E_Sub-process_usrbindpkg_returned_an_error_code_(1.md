---
title: "E: Sub-process /usr/bin/dpkg returned an error code (1)"
date: 2012-08-30
forum: New to Ubuntu
---

### Post by ubigix on 2012-08-30
Hi!
I'm trying to install MySQL through the command 

# aptitude install mysql-server mysql-client

but I think to encounter a problem with dependencies (that I do not know indeed what they are).

This is the error report:
> 
Setting up mysql-server-5.5 (5.5.24-0ubuntu0.12.04.1) ...
start: Job failed to start
invoke-rc.d: initscript mysql, action "start" failed.
dpkg: error processing mysql-server-5.5 (--configure):
 subprocess installed post-installation script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of mysql-server:
 mysql-server depends on mysql-server-5.5; however:
  Package mysql-server-5.5 is not configured yet.
dpkg: error processing mysql-server (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing:
 mysql-server-5.5
 mysql-server
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up mysql-server-5.5 (5.5.24-0ubuntu0.12.04.1) ...
start: Job failed to start
invoke-rc.d: initscript mysql, action "start" failed.
dpkg: error processing mysql-server-5.5 (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of mysql-server:
 mysql-server depends on mysql-server-5.5; however:
  Package mysql-server-5.5 is not configured yet.
dpkg: error processing mysql-server (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 mysql-server-5.5
 mysql-server


From that you can see that I use Ubuntu 12.04 and I'm trying to install MySQL 5.5.

Thanks a lot for help.

---

### Post by drmrgd on 2012-08-30
Try this and report any errors you get if this doesn't work:

```
sudo dpkg --configure -a
```

---

### Post by ubigix on 2012-08-30
```

Setting up mysql-server-5.5 (5.5.24-0ubuntu0.12.04.1) ...
start: Job failed to start
invoke-rc.d: initscript mysql, action "start" failed.
dpkg: error processing mysql-server-5.5 (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of mysql-server:
 mysql-server depends on mysql-server-5.5; however:
  Package mysql-server-5.5 is not configured yet.
dpkg: error processing mysql-server (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 mysql-server-5.5
 mysql-server

```

Thanks

---

### Post by drmrgd on 2012-08-30
I'm not a mysql expert by any stretch, so I'm shooting in the dark here a little.  It looks like it's trying run the post-installation script before the package is configured for some reason.  Let's try to configure it directly:

```
sudo dpkg --configure mysql-server-5.5
```

---

### Post by ubigix on 2012-08-30
The same error...

```

Setting up mysql-server-5.5 (5.5.24-0ubuntu0.12.04.1) ...
start: Job failed to start
invoke-rc.d: initscript mysql, action "start" failed.
dpkg: error processing mysql-server-5.5 (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 mysql-server-5.5

```

---

### Post by drmrgd on 2012-08-30
Hmmm...you have me a little baffled.  I did a quick Google search, and this seems to have come up before.  Again, not knowing much about mysql, I'm not quite sure the best approach.  Seems there is a system configuration of a mysql.cnf file problem, that prevents dpkg from configuring it correctly.  Here are a couple links I found that might be relevant:

[http://stackoverflow.com/questions/9972611/not-able-to-install-mysql-on-ubuntu-11](http://stackoverflow.com/questions/9972611/not-able-to-install-mysql-on-ubuntu-11)

[http://ubuntuforums.org/showthread.php?t=1763604](http://ubuntuforums.org/showthread.php?t=1763604)

[http://ubuntuforums.org/showpost.php?p=11872291&postcount=3](http://ubuntuforums.org/showpost.php?p=11872291&postcount=3)

Hope those help!

---

### Post by ubigix on 2012-08-30
Nothing to do!
I receive messages like the following ones

```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 libmysqlclient18 : Depends: mysql-common (>= 5.5.24-0ubuntu0.12.04.1) but it is not going to be installed
 mysql-client-5.5 : Depends: mysql-common (>= 5.5.24-0ubuntu0.12.04.1) but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

```

```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
mysql-common is already the newest version.
mysql-common set to manually installed.
mysql-server is already the newest version.
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 mysql-server : Depends: mysql-server-5.5 but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

```

---

