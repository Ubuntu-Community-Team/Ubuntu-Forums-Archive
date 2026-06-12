---
title: "Google Chrome installation query"
date: 2012-10-04
forum: New to Ubuntu
---

### Post by arejet on 2012-10-04
Hi,

I am a new user of Ubuntu 12.04 LTS. This is my first Linux experience. 
I have read a few of the commands. So I thought of installing chrome through the command line. I downloaded google-chrome-stable_current_amd64.deb on my computer and started to install using the sudo apt-get install command. But I get a message saying: E: Unable to locate package google-chrome-stable_current_amd64. 

It is located in the desktop and also in the Downloads folder in Home.

How should I proceed to install this package?

---

### Post by 2F4U on 2012-10-04
To install the .deb file, follow these instructions:

[http://www.howopensource.com/2012/05/install-google-chrome-in-ubuntu-12-04-precise-with-debain/](http://www.howopensource.com/2012/05/install-google-chrome-in-ubuntu-12-04-precise-with-debain/)

However, there is also a repository available for Chrome. To install from the repository, follow these instructions:

[http://www.howopensource.com/2011/10/install-google-chrome-in-ubuntu-11-10-11-04-10-10-10-04/](http://www.howopensource.com/2011/10/install-google-chrome-in-ubuntu-11-10-11-04-10-10-10-04/)

---

### Post by albandy on 2012-10-04
> **arejet said:**
> Hi,

I am a new user of Ubuntu 12.04 LTS. This is my first Linux experience. 
I have read a few of the commands. So I thought of installing chrome through the command line. I downloaded google-chrome-stable_current_amd64.deb on my computer and started to install using the sudo apt-get install command. But I get a message saying: E: Unable to locate package google-chrome-stable_current_amd64. 

It is located in the desktop and also in the Downloads folder in Home.

How should I proceed to install this package?

Double-click the package and will be installed.
If you want to install it throught console type: sudo dpkg -i google-chrome-stable_current_amd64.deb

---

### Post by arejet on 2012-10-04
> **albandy said:**
> Double-click the package and will be installed.
If you want to install it throught console type: sudo dpkg -i google-chrome-stable_current_amd64.deb

Thank you so much !
I tried it. I first changed the directory to Desktop (that`s where the deb file is). But I get the following message:


arejet@ubuntu:~$ cd Desktop
arejet@ubuntu:~/Desktop$ ls
Getting Started with Ubuntu 12.04.pdf   intro-linux.pdf
google-chrome-stable_current_amd64.deb
arejet@ubuntu:~/Desktop$ sudo dpkg -i google-chrome-stable_current_amd64.deb
Selecting previously unselected package google-chrome-stable.
(Reading database ... 165627 files and directories currently installed.)
Unpacking google-chrome-stable (from google-chrome-stable_current_amd64.deb) ...
dpkg: dependency problems prevent configuration of google-chrome-stable:
 google-chrome-stable depends on libxss1; however:
  Package libxss1 is not installed.
dpkg: error processing google-chrome-stable (--install):
 dependency problems - leaving unconfigured
Processing triggers for man-db ...
Processing triggers for desktop-file-utils ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for gnome-menus ...
Errors were encountered while processing:
 google-chrome-stable

---

### Post by albandy on 2012-10-04
> **arejet said:**
> Thank you so much !
I tried it. I first changed the directory to Desktop (that`s where the deb file is). But I get the following message:


arejet@ubuntu:~$ cd Desktop
arejet@ubuntu:~/Desktop$ ls
Getting Started with Ubuntu 12.04.pdf   intro-linux.pdf
google-chrome-stable_current_amd64.deb
arejet@ubuntu:~/Desktop$ sudo dpkg -i google-chrome-stable_current_amd64.deb
Selecting previously unselected package google-chrome-stable.
(Reading database ... 165627 files and directories currently installed.)
Unpacking google-chrome-stable (from google-chrome-stable_current_amd64.deb) ...
dpkg: dependency problems prevent configuration of google-chrome-stable:
 google-chrome-stable depends on libxss1; however:
  Package libxss1 is not installed.
dpkg: error processing google-chrome-stable (--install):
 dependency problems - leaving unconfigured
Processing triggers for man-db ...
Processing triggers for desktop-file-utils ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for gnome-menus ...
Errors were encountered while processing:
 google-chrome-stable

Now type:
sudo apt-get install -f

---

### Post by arejet on 2012-10-04
> **albandy said:**
> Now type:
sudo apt-get install -f

Hey thank you so much Albandy !
It worked like magic .... 
I am starting to like linux ... :)

BTW, where in the file system is chrome installed?

---

### Post by NikTh on 2012-10-04
> **arejet said:**
> BTW, where in the file system is chrome installed?

Search under /usr/bin or /usr/sbin 

example
```
ls /usr/bin/ | grep -i chrome
``` 

Thanks

---

