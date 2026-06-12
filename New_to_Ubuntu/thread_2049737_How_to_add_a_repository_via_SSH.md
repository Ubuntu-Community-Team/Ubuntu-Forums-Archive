---
title: "How to add a repository via SSH"
date: 2012-08-29
forum: New to Ubuntu
---

### Post by Matsaki on 2012-08-29
Having Ubuntu 10.04.4 LTS on my server I'm now looking for a tutorial what and how to put in Repositories, such as MySQL, PHP etc. via SSH.

Thanks!

---

### Post by Lars Noodén on 2012-08-29
PHP, MySQL, Postgresql, etc. are all already available via Ubuntu's repositories. Do you mean working with the repositories via the shell?  It's the same then whether you are working locally using the console or terminal or remotely using SSH. The tool you need then would be [apt-get](http://manpages.ubuntu.com/manpages/precise/en/man8/apt-get.8.html) and maybe [apt-cache](http://manpages.ubuntu.com/manpages/precise/en/man8/apt-cache.8.html).

```

sudo apt-get update
sudo apt-get install apache2
apt-cache policy apache2

```


Or do you mean getting access to a [repository that is restricted access behind an SSH login](http://www.debian-administration.org/articles/513)?

---

### Post by Matsaki on 2012-08-29
Great so when I do the:

> sudo apt-get update
&
> sudo apt-get upgrade

All the essentials are upgraded without having to add them in repositories?

---

### Post by Lars Noodén on 2012-08-29
That will update the programs you already have installed to the latest versions.  The source of that update will be from the repositories listed in [/etc/apt/sources.list](http://manpages.ubuntu.com/manpages/precise/en/man5/sources.list.5.html) and [font=Courier New]/etc/apt/sources.list.d/*[/font]

---

### Post by Matsaki on 2012-08-29
How can I check i.e. the version I have of MySQL and what is the newest working with Ubuntu to compare and see that MySQL is upgraded correctly?

Your help is much appreciated Lars!

---

### Post by Lars Noodén on 2012-08-29
You can check the version that you have using [dpkg](http://manpages.ubuntu.com/manpages/precise/en/man1/dpkg.1.html) and check the version that the Ubuntu repository has using [apt-cache](http://manpages.ubuntu.com/manpages/precise/en/man8/apt-cache.8.html)

```

dpkg -s mysql-server
[s]apt-cache mysql-server[/s]
apt-cache search mysql-server

```

---

### Post by Matsaki on 2012-08-29
Not working for me. Maybe my Ubuntu installation is made different?

> root@server:~# dpkg -s mysql-server
Package `mysql-server' is not installed and no info is available.
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.

> root@server:~# apt-cache mysql-server
E: Invalid operation mysql-server

---

### Post by Lars Noodén on 2012-08-29
The error in apt-cache was my mistake, I've corrected the post above to show the right way.

The output you have from dpkg seems to show that mysql-server is not installed.  You could check with the option --get-selections to get another view of the status.

```

dpkg --get-selections mysql-server
dpkg --get-selections | grep mysql

```

---

### Post by Matsaki on 2012-08-29
I have mysql running on the server, and when I tried "dpkg --get-selections mysql-server"

> root@server:~# dpkg --get-selections mysql-server
No packages found matching mysql-server.

And running "dpkg --get-selections | grep mysql" I get nothing.

Shall I ask the guy who made the installation whats going on?

---

### Post by Lars Noodén on 2012-08-29
Yes, you should ask him what's going on.  It appears that mysql server is not installed from the repositories.

One final check could be to look for the server binary itself.  If it's there the program itself can tell you the version.  Check the help or manual page for the right option, but to report version, it is usually -V or -v

```

/usr/sbin/mysqld -V

```

If it is there but not from the repositories, it would be a very good idea to uninstall it and then reinstall using the repository's version.

---

### Post by Matsaki on 2012-08-29
He said mysql comes with the DA. Should I change it?

---

### Post by Lars Noodén on 2012-08-29
What is meant by "DA" in that context?   

Again if mysql wasn't installed using the package manager, then it would be *very highly recommended* to uninstall it and then reinstall using the package manager.  Getting programs from outside the existing repositories is often a recipe for trouble and extra work, sooner or later.  It cannot be overstated how much of a help the repositories are in *easily* keeping the software up to date.

---

### Post by Matsaki on 2012-08-29
With DA he means DirectAdmin which is used on the machine. Would that be ok you think?

---

### Post by Lars Noodén on 2012-08-29
I haven't seen DirectAdmin before.  I've always used the plain shell instead.  If it's bypassing the Ubuntu repositories, then I'll state again that it is best not to do that.  

I'm not finding much mention of Ubuntu on the [DirectAdmin](http://www.directadmin.com/install.html) site, not mention of DirectAdmin in the repository.  Are you sure that you have Ubuntu?  What is the output from these:

```

uname -a
lsb_release -rd

```

The DirectAdmin website does mention that it includes mysql, but how and whether it is kept up to date is another question.  Did [font=Courier New]/usr/sbin/mysqld -V[/font] give you info?  That should work if DirectAdmin put the [files in the right place](http://manpages.ubuntu.com/manpages/precise/en/man7/hier.7.html).  Anyway, I guess that is between him and you.  You could save ~ $29 per month by learning to use a plain shell.

---

### Post by Matsaki on 2012-08-29
I'm trying to find out why he did the installation through DA. I'm not happy with that either. Or using webmin in that case too.

These is the output I get:

> root@server:~# uname -a
Linux server.mydomain.com 2.6.32-38-server #83-Ubuntu SMP Wed Jan 4 11:26:59 UTC 2012 x86_64 GNU/Linux
root@server:~# 

> root@server:~# lsb_release -rd
/usr/bin/python: /usr/local/lib/libz.so.1: no version information available (required by /usr/bin/python)
Description:	Ubuntu 10.04.4 LTS
Release:	10.04

---

### Post by Lars Noodén on 2012-08-29
That's good.  You have the server edition of Ubuntu 10.04 and no worries about support until 2015.  I do hope he comes around to using the package manager, though.  I can say that mixing and matching packages from outside the package manager will eventually lead to problems.  Been there, done that.  

It might be worth noting that there is a web interface for 10.04 called [ebox](https://help.ubuntu.com/10.04/serverguide/ebox.html).

If [font=Courier New]/usr/sbin/mysqld -V[/font] did not work, then mysqld must be in a non-standard location.  You can find it with [locate](http://linux.die.net/man/1/locate)

```

locate mysqld

```

---

### Post by Matsaki on 2012-08-29
All applications such as PHP, MySQL, Mail etc. is installed via DA. I have to install scripts in order for DA to make upgrades. I think I will look for another solution than DA. The result of locate is:

> root@server:~# locate mysqld
/etc/init.d/mysqld
/etc/rc0.d/K20mysqld
/etc/rc1.d/K20mysqld
/etc/rc2.d/S20mysqld
/etc/rc3.d/S20mysqld
/etc/rc4.d/S20mysqld
/etc/rc5.d/S20mysqld
/etc/rc6.d/K20mysqld
/usr/local/directadmin/scripts/mysqld
/usr/local/mysql-5.5.9-linux2.6-x86_64/bin/mysqld
/usr/local/mysql-5.5.9-linux2.6-x86_64/bin/mysqld-debug
/usr/local/mysql-5.5.9-linux2.6-x86_64/bin/mysqld_multi
/usr/local/mysql-5.5.9-linux2.6-x86_64/bin/mysqld_safe
/usr/local/mysql-5.5.9-linux2.6-x86_64/bin/mysqldump
/usr/local/mysql-5.5.9-linux2.6-x86_64/bin/mysqldumpslow
/usr/local/mysql-5.5.9-linux2.6-x86_64/include/mysqld_ername.h
/usr/local/mysql-5.5.9-linux2.6-x86_64/include/mysqld_error.h
/usr/local/mysql-5.5.9-linux2.6-x86_64/lib/libmysqld-debug.a
/usr/local/mysql-5.5.9-linux2.6-x86_64/lib/libmysqld.a
/usr/local/mysql-5.5.9-linux2.6-x86_64/man/man1/mysqld_multi.1
/usr/local/mysql-5.5.9-linux2.6-x86_64/man/man1/mysqld_safe.1
/usr/local/mysql-5.5.9-linux2.6-x86_64/man/man1/mysqldump.1
/usr/local/mysql-5.5.9-linux2.6-x86_64/man/man1/mysqldumpslow.1
/usr/local/mysql-5.5.9-linux2.6-x86_64/man/man8/mysqld.8
/usr/local/mysql-5.5.9-linux2.6-x86_64/mysql-test/include/default_mysqld.cnf
/usr/local/mysql-5.5.9-linux2.6-x86_64/mysql-test/include/mysqld--help.inc
/usr/local/mysql-5.5.9-linux2.6-x86_64/mysql-test/include/mysqldump.inc
/usr/local/mysql-5.5.9-linux2.6-x86_64/mysql-test/include/restart_mysqld.inc
/usr/local/mysql-5.5.9-linux2.6-x86_64/mysql-test/r/mysqld--help-notwin.result
/usr/local/mysql-5.5.9-linux2.6-x86_64/mysql-test/r/mysqld--help-win.result
/usr/local/mysql-5.5.9-linux2.6-x86_64/mysql-test/r/mysqldump-compat.result
/usr/local/mysql-5.5.9-linux2.6-x86_64/mysql-test/r/mysqldump-max.result
/usr/local/mysql-5.5.9-linux2.6-x86_64/mysql-test/r/mysqldump-no-binlog.result
/usr/local/mysql-5.5.9-linux2.6-x86_64/mysql-test/r/mysqldump.result
/usr/local/mysql-5.5.9-linux2.6-x86_64/mysql-test/r/mysqldump_restore.result
/usr/local/mysql-5.5.9-linux2.6-x86_64/mysql-test/r/rpl_mysqldump_slave.result
/usr/local/mysql-5.5.9-linux2.6-x86_64/mysql-test/t/mysqld--help-notwin.test
/usr/local/mysql-5.5.9-linux2.6-x86_64/mysql-test/t/mysqld--help-win.test
/usr/local/mysql-5.5.9-linux2.6-x86_64/mysql-test/t/mysqldump-compat.opt
/usr/local/mysql-5.5.9-linux2.6-x86_64/mysql-test/t/mysqldump-compat.test
/usr/local/mysql-5.5.9-linux2.6-x86_64/mysql-test/t/mysqldump-max-master.opt
/usr/local/mysql-5.5.9-linux2.6-x86_64/mysql-test/t/mysqldump-max.test
/usr/local/mysql-5.5.9-linux2.6-x86_64/mysql-test/t/mysqldump-no-binlog-master.opt
/usr/local/mysql-5.5.9-linux2.6-x86_64/mysql-test/t/mysqldump-no-binlog.test
/usr/local/mysql-5.5.9-linux2.6-x86_64/mysql-test/t/mysqldump.test
/usr/local/mysql-5.5.9-linux2.6-x86_64/mysql-test/t/mysqldump_restore.test
/usr/local/mysql-5.5.9-linux2.6-x86_64/mysql-test/t/rpl_mysqldump_slave.test
/usr/local/mysql-5.5.9-linux2.6-x86_64/support-files/mysqld_multi.server
/var/lib/update-rc.d/mysqld
root@server:~# 

---

### Post by saphil on 2012-08-29
You might want to make sure that the repositories are all available.
```
sudo gedit /etc/apt/sources.list
```or if you have CLI only,
```
sudo nano /etc/apt/sources.list
```
wherever there is a "#" sign in front of a line that starts "deb..." you can safely delete the "#" and then run 
```
sudo apt-get update
```A default install does not make available all of the repositories.

---

### Post by Matsaki on 2012-08-29
I would like to show you the repositories file as it is now. But how do I copy all text in the file? 

I was also told that mysql should be updated manually as there might be cases of updates that calls for i.e. rebuilding tables etc. that one would not like to do.

---

### Post by Matsaki on 2012-09-03
With the help from very helpful guys at DirectAdmin, all the applications are now up to date :)

But when I run update for Ubuntu now:

> sudo apt-get update
sudo apt-get upgrade

I get the message that 3 packages is not updated?

> The following packages have been kept back:
  linux-headers-server linux-image-server linux-server
0 upgraded, 0 newly installed, 0 to remove and 3 not upgraded.

What does that mean?

---

### Post by Lars Noodén on 2012-09-03
From what I gather it is because you are adding new packages, each kernel is in a separate package.  So to update kernels you have to add the new kernel packages.  To do that, use dist-upgrade.

```

sudo apt-get dist-upgrade

```

Along the same lines the extra old kernels have to be removed manually.  In general it is good practice to leave at least one old one in case it turns out that there is something wrong with the new one.

You can see what you have using [dpkg](http://manpages.ubuntu.com/manpages/precise/en/man1/dpkg.1.html).
```

dpkg --get-selections linux-image-*

```

---

### Post by Matsaki on 2012-09-03
I run the:

> sudo apt-get dist-upgrade

and the took care of the problem

When I run:

> dpkg --get-selections linux-image-*

I get:

> root@server:~# dpkg --get-selections linux-image-*
linux-image-2.6.32-33-server			install
linux-image-2.6.32-38-server			install
linux-image-2.6.32-42-server			install
linux-image-server				install

So what and how should I remove?

---

### Post by Lars Noodén on 2012-09-04
You can remove the oldest one.  You can use apt-get to remove it. That leaves you with the latest kernel plus the next most recent one as a spare.  

```

sudo apt-get remove linux-image-2.6.32-33-server

```

---

