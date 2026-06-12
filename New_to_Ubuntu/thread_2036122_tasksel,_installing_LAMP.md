---
title: "tasksel, installing LAMP"
date: 2012-08-01
forum: New to Ubuntu
---

### Post by Hamidjon on 2012-08-01
Hi,
My tasksel is not working properly. In a site ([http://www.unixmen.com/install-lamp-with-1-command-in-ubuntu-1010-maverick-meerkat/](http://www.unixmen.com/install-lamp-with-1-command-in-ubuntu-1010-maverick-meerkat/)) the steps about installing the LAMP by one command (sudo tasksel) is explained. I'm having trouble in a first step: when I enter ```
sudo tasksel
``` to a command line, the tasksel shows only one line at Software selection:
______________________________________________________
Choose software to install:
   [ ] Manual package selection
        <ok>
______________________________________________________

Just one, no more available selections. According to site, here, must be ([ ] LAMP), but there is no such line. Can somebody help to solve this problem? Thanks.

At first time, when I used 'sudo tasksel' there were 3 selection-lines (first and second already checked and third one not unchecked). I unchecked first and second and selected the third one and hit <ok>... Maybe, here, I made a mistake ...

Commands (such as ```
lsb_release -a; echo; apt-cache policy tasksel
```) give:
No LSB modules are available.
Distributor ID: Ubuntu
Description:	Ubuntu 12.04 LTS
Release:	12.04
Codename: precise

tasksel:
  Installed: 2.88ubuntu9
  Candidate: 2.88ubuntu9
  Version table:
 *** 2.88ubuntu9 0
        100 /var/lib/dpkg/status

---

### Post by Lars Noodén on 2012-08-01
I would just use the package manager to install the packages.  There are only a few needed. I've never had good luck with tasksel at any time over the years.  

For LAMP, you've already got Linux and Perl installed, you just need to install Apache and MySQL (or alternately nginx and Postgresql).  The packages [apache2](http://packages.ubuntu.com/precise/apache2), [mysql-client](http://packages.ubuntu.com/precise/mysql-client) and [mysql-server](http://packages.ubuntu.com/precise/mysql-server) should do the trick. Like  Perl, Python is also already included by default if that's what you want.  The package php5 will give you PHP.

---

### Post by Cheesemill on 2012-08-01
You can use apt-get instead of tasksel:
```
 
sudo apt-get install lamp-server^

```(don't forget the caret)

---

### Post by Hamidjon on 2012-08-01
Here, for apache there are 4 types of packages. I can't decide which one is suitable for my OS, because I don't have any knowledge about servers. I work both with Perl and PHP, so which type of server I should select among them: apache2-mpm-event, apache2-mpm-itk, apache2-mpm-prefork, apache2-mpm-worker?
And do I need to install both MySQL types (server and client)?
Thanks

---

### Post by Hamidjon on 2012-08-01
The result is:
hamidjon@hamidjon-desktop:~$ sudo apt-get install lamp-server^
[sudo] password for hamidjon: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package lamp-server^
E: Couldn't find task 'lamp-server'
E: Couldn't find any package by regex 'lamp-server^'

---

### Post by Lars Noodén on 2012-08-01
> **Hamidjon said:**
> Here, for apache there are 4 types of packages. I can't decide which one is suitable for my OS, because I don't have any knowledge about servers. I work both with Perl and PHP, so which type of server I should select among them: apache2-mpm-event, apache2-mpm-itk, apache2-mpm-prefork, apache2-mpm-worker?
And do I need to install both MySQL types (server and client)?
Thanks

There is only one Apache server.  Just install the package [apache2](apt://apache2).  That will give you the base web server.  Later you can worry about adding other modules.  

You might not need the mysql client.  Though, I guess for perl, you'll also need the package [libdbd-mysql-perl](apt://libdbd-mysql-perl)

---

### Post by Hamidjon on 2012-08-01
Link to apt://apache2 gives such result: There isn&#8217;t a software package called &#8220;apache2&#8221; in your current software sources.
How can I get apache2 from another source?
How about this source -- [http://packages.ubuntu.com/precise/i386/apache2.2-bin/download](http://packages.ubuntu.com/precise/i386/apache2.2-bin/download)
Is it package apache2?

---

### Post by Lars Noodén on 2012-08-01
Yes, it's the package 'apache2'  That's actually a metapackage that will install a handful of programs, modules and libraries.  It should be available in your repository, whatever version of Ubuntu you are running.  It's there for me in Precise and in Quantal-alpha3.

What happens when you try [apt-get](http://manpages.ubuntu.com/manpages/precise/en/man8/apt-get.8.html)?

```

sudo apt-get update
sudo apt-get install apache2

```

---

### Post by Hamidjon on 2012-08-01
for **sudo apt-get update**:

hamidjon@hamidjon-desktop:~/LAMP/Linux/soft/tasksel$ sudo apt-get update
[sudo] password for hamidjon: 
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise InRelease     
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise Release.gpg   
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise Release
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Sources
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main i386 Packages
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main TranslationIndex
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Translation-en_US
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Translation-en
Reading package lists... Done


and for **sudo apt-get install apache2**:

hamidjon@hamidjon-desktop:~/LAMP/Linux/soft/tasksel$ sudo apt-get install apache2
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package apache2

---

### Post by Lars Noodén on 2012-08-01
The output from apt-get update seems to suggest that you are not pointed at any regular [repository](https://help.ubuntu.com/community/Repositories).  Check to make sure that your package manager can use at least the main and universe repositories.  By default restricted and multiverse are usually included, too, but not necessary in this particular case.

[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

---

### Post by Hamidjon on 2012-08-01
Yes, finally it's worked... :) 
I made changes in a repository of Ubuntu Software Center (some unchecked lines, at edit menu, were checked by me)
When I enter the sudo apt-get install lamp-server^ everything worked I'm now installing LAMP :)
Thank you very much Lars Noodén!

---

