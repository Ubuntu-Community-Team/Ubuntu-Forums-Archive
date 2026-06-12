---
title: "Installing and updating software &quot;fatal error&quot;"
date: 2012-05-26
forum: New to Ubuntu
---

### Post by drewbird on 2012-05-26
I was trying to install Synaptic Package Manager through Ubuntu Software Center, and I am getting an error message, "Package operation failed." Looking at the details from the error, this is what it outputs.

installArchives() failed: Selecting previously unselected package sgml-data.
(Reading database ... 
(Reading database ... 5%
(Reading database ... 10%
(Reading database ... 15%
(Reading database ... 20%
(Reading database ... 25%
(Reading database ... 30%
(Reading database ... 35%
(Reading database ... 40%
(Reading database ... 45%
(Reading database ... 50%
(Reading database ... 55%
(Reading database ... 60%
(Reading database ... 65%
(Reading database ... 70%
(Reading database ... 75%
(Reading database ... 80%
(Reading database ... 85%
(Reading database ... 90%
(Reading database ... 95%dpkg: unrecoverable fatal error, aborting:
 files list file for package `ubuntu-docs' contains empty filename
Error in function: 

Note: I also get a similar error when trying to update software using the Update Manager. The first line is different though:

installArchives() failed: Preconfiguring packages ...
Preconfiguring packages ...
Preconfiguring packages ...
Preconfiguring packages ...

The rest is the same as the previous error.

Thanks for replying if you do!

---

### Post by fantab on 2012-05-26
Welcome to the forum!

Run the following in the Terminal:

```
$ sudo rm /var/lib/apt/lists/* -vf
$ sudo apt-get update
```If you still get errors then post the output of the following in code #:

```
$ cat /etc/apt/sources.list
```

---

### Post by drewbird on 2012-05-26
Thanks for the quick reply.

After doing the update, I still got the error when trying to install Synaptic.

Error in function:
SystemError: E:Sub-process /usr/bin/dpkg returned an error code (2)

And still no luck with Update Manager.

---

### Post by fantab on 2012-05-26
Were there any errors during "sudo apt-get update"?

$ sudo apt-get clean all
$ sudo apt-get update

If yes, post the output and also post the output of the second command in post #2

---

### Post by drewbird on 2012-05-27
No error with the "sudo apt-get update"

Here is the output for the second command though.


# /etc/apt/sources.list

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise main restricted universe multiverse
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) precise-security main restricted universe multiverse
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise-updates main restricted universe multiverse

---

### Post by fantab on 2012-05-27
Post the output of 

$ cat /usr/bin/dpkg

---

### Post by drewbird on 2012-05-27
It output a lot of unreadable characters.

---

### Post by fantab on 2012-05-27
My bad.

Try this:
$ su
# apt-get update
# apt-get upgrade

Then try to install Synaptic.

---

### Post by drewbird on 2012-05-27
I entered my Password in correctly but it says, "su: Authentication failure" after using the $ su command.

---

### Post by raja.genupula on 2012-05-27
[http://repogen.simplylinux.ch/](http://repogen.simplylinux.ch/)

by using the link generate source list for your distro and place them in  /etc/apt/sources.list by 

```
sudo gedit /etc/apt/sources.list
``` save and close the window then do ```
sudo apt-get update
```

---

### Post by fantab on 2012-05-27
There seems to be an authentication problem. Try again.

---

### Post by raja.genupula on 2012-05-27
> **drewbird said:**
> I entered my Password in correctly but it says, "su: Authentication failure" after using the $ su command.

su for Debian
sudo for Ubuntu

---

### Post by drewbird on 2012-05-27
Raja, would you mind helping me out with the simplylinux site? I am completely new to Ubuntu, so I'm not sure what to check for my source list.

---

### Post by fantab on 2012-05-27
> **raja.genupula said:**
> su for Debian
sudo for Ubuntu


ok... still hung up :)

```
$ sudo -i
# apt-get update
# apt-get upgrade
```

then install synaptic.

---

### Post by drewbird on 2012-05-27
Okay, so I am getting an error when I try to upgrade using those commands.

root@ubuntu:~# apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be upgraded:
  at-spi2-core gir1.2-atspi-2.0 libasound2 libatspi2.0-0
  libnautilus-extension1a libssl1.0.0 nautilus nautilus-data
  nvidia-current-updates openssl python-gi python-gi-cairo python-gobject
  software-center xserver-common xserver-xorg-core
  xserver-xorg-input-synaptics
17 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0 B/64.3 MB of archives.
After this operation, 343 kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Preconfiguring packages ...
(Reading database ... 95%dpkg: unrecoverable fatal error, aborting:
 files list file for package `ubuntu-docs' contains empty filename
E: Sub-process /usr/bin/dpkg returned an error code (2)

---

### Post by raja.genupula on 2012-05-27
```
#############################################################
################### OFFICIAL UBUNTU REPOS ###################
#############################################################

###### Ubuntu Main Repos
deb http://us.archive.ubuntu.com/ubuntu/ precise main restricted universe multiverse 
deb-src http://us.archive.ubuntu.com/ubuntu/ precise main restricted universe multiverse 

###### Ubuntu Update Repos
deb http://us.archive.ubuntu.com/ubuntu/ precise-security main restricted universe multiverse 
deb http://us.archive.ubuntu.com/ubuntu/ precise-updates main restricted universe multiverse 
deb http://us.archive.ubuntu.com/ubuntu/ precise-proposed main restricted universe multiverse 
deb http://us.archive.ubuntu.com/ubuntu/ precise-backports main restricted universe multiverse 
deb-src http://us.archive.ubuntu.com/ubuntu/ precise-security main restricted universe multiverse 
deb-src http://us.archive.ubuntu.com/ubuntu/ precise-updates main restricted universe multiverse 
deb-src http://us.archive.ubuntu.com/ubuntu/ precise-proposed main restricted universe multiverse 
deb-src http://us.archive.ubuntu.com/ubuntu/ precise-backports main restricted universe multiverse 

###### Ubuntu Partner Repo
deb http://archive.canonical.com/ubuntu precise partner
deb-src http://archive.canonical.com/ubuntu precise partner

###### Ubuntu Extras Repo
deb http://extras.ubuntu.com/ubuntu precise main
deb-src http://extras.ubuntu.com/ubuntu precise main

##############################################################
##################### UNOFFICIAL  REPOS ######################
##############################################################

###### 3rd Party Binary Repos

#### Audacity - http://audacity.sourceforge.net/
## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys     1024R/BB901940
deb http://ppa.launchpad.net/audacity-team/daily/ubuntu precise main 

#### Banshee - https://edge.launchpad.net/~banshee-team
## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 6E80C6B7
deb http://ppa.launchpad.net/banshee-team/ppa/ubuntu precise main

#### Gimp SVN - https://launchpad.net/~matthaeus123/+archive/mrw-gimp-svn
## Run this command: sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 405A15CB
deb http://ppa.launchpad.net/matthaeus123/mrw-gimp-svn/ubuntu precise main 

#### Glx-Dock / Cairo-Dock - http://www.glx-dock.org
## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys E80D6BF5
deb http://ppa.launchpad.net/cairo-dock-team/weekly/ubuntu precise  main

#### Gwibber (Daily) - https://launchpad.net/gwibber
## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 72D340A3
deb http://ppa.launchpad.net/gwibber-daily/ppa/ubuntu precise main

#### Ironhide - https://launchpad.net/~mj-casalogic/+archive/ironhide/
## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys ECF7E0B3
deb http://ppa.launchpad.net/mj-casalogic/ironhide/ubuntu precise main

#### LibreOffice - http://www.documentfoundation.org/download/
## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 1378B444
deb http://ppa.launchpad.net/libreoffice/ppa/ubuntu precise main

#### Mozilla Daily Build Team - http://edge.launchpad.net/~ubuntu-mozilla-daily/+archive/ppa
## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys  247510BE
deb http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu precise main

#### Pidgin - http://pidgin.im
## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys A1F196A8
deb http://ppa.launchpad.net/pidgin-developers/ppa/ubuntu precise main

#### VirtualBox - http://www.virtualbox.org
## Run this command: wget -q http://download.virtualbox.org/virtualbox/debian/oracle_vbox.asc -O- | sudo apt-key add -
deb http://download.virtualbox.org/virtualbox/debian precise contrib


####### 3rd Party Source Repos

#### Audacity (Source) - http://audacity.sourceforge.net/
## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys     1024R/BB901940
deb-src http://ppa.launchpad.net/audacity-team/daily/ubuntu precise main 

#### Banshee (Source) - https://edge.launchpad.net/~banshee-team
## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 6E80C6B7
deb-src http://ppa.launchpad.net/banshee-team/ppa/ubuntu precise main

#### Gimp SVN (Source) - https://launchpad.net/~matthaeus123/+archive/mrw-gimp-svn
## Run this command: sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 405A15CB
deb-src http://ppa.launchpad.net/matthaeus123/mrw-gimp-svn/ubuntu precise main 

#### Glx-Dock / Cairo-Dock (Source) - http://www.glx-dock.org
## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys E80D6BF5
deb-src http://ppa.launchpad.net/cairo-dock-team/weekly/ubuntu precise main

#### Gwibber (Daily) (Source) - https://launchpad.net/gwibber
## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 72D340A3
deb-src http://ppa.launchpad.net/gwibber-daily/ppa/ubuntu precise main

#### Ironhide (Source) - https://launchpad.net/~mj-casalogic/+archive/ironhide/
## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys ECF7E0B3
deb-src http://ppa.launchpad.net/mj-casalogic/ironhide/ubuntu precise main

#### LibreOffice (Source) - http://www.documentfoundation.org/download/
## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 1378B444
deb-src http://ppa.launchpad.net/libreoffice/ppa/ubuntu precise main

#### Mozilla Daily Build Team (Source) - http://edge.launchpad.net/~ubuntu-mozilla-daily/+archive/ppa
## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys  247510BE
deb-src http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu precise main

#### Pidgin (Source) - http://pidgin.im
## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys A1F196A8
deb-src http://ppa.launchpad.net/pidgin-developers/ppa/ubuntu precise main


```

copy above text into your source.list file with the gedit command i have given and do update again . 
dont forget doing sudo apt-key adv --keyserver keyserver.ubuntu.com for the unofficial repos .

---

### Post by fantab on 2012-05-27
@Raja: I think his issue is not with Sources.list but with an empty file name in ubuntu-docs.

ALT + F2 - then type "gksu nautilus" (without quotes)

Search - ubuntu-docs 

open the folder and see what files you've got there: specifically look if there is an empty file... or list all the files you've got there and we'll see.

---

### Post by drewbird on 2012-05-27
Thanks for the responses so far.

Raja:
I did everything you said, but after updating I tried to upgrade and I got the same error as before.

fantab:
I don't seem to have an "ubuntu-docs" folder... Any idea why that might be?

---

### Post by fantab on 2012-05-27
Search for in the File System. or use this path File System/usr/share/doc/ubuntu-docs (This is where I've got it.)

---

### Post by drewbird on 2012-05-27
Thanks, that worked.

Files in folder include:

AUTHORS, changelog.gz, copyright, NEWS.gz, README, and TODO

---

### Post by fantab on 2012-05-27
Try opening the flies by double clicking on them and see if any is empty.

---

### Post by drewbird on 2012-05-27
They all have some text in them.

---

### Post by fantab on 2012-05-27
Good. Using Terminal open:

```
$ sudo gedit /var/lib/dpkg/info/ubuntu-docs.list
```Scroll to the bottom of the list and see if there are any empty lines, to make sure see that the cursor is at the end last word ("page") of the last line and press delete until there are no more empty lines under last written line. Also check if there are any empty lines in between, if there are then delete them. Then Save the file and

```
$ sudo apt-get update
$ sudo apt-get upgrade 
$ sudo apt-get install synaptic
```

---

### Post by drewbird on 2012-05-27
It says most of the file is invalid characters. Is this normal using "Current Locale (UTF-8)" for the character encoding?

---

### Post by fantab on 2012-05-27
> **drewbird said:**
> It says most of the file is invalid characters. Is this normal using "Current Locale (UTF-8)" for the character encoding?

Okay... UTF- 8 is what it should be.

recheck

```
$ locale
```more info**[ HERE]("https://help.ubuntu.com/community/Locale")** and **[HERE]("https://help.ubuntu.com/community/LocaleConf")**

Make sure it is all correct... if not then use the links to correct it. Reconfigure Locale.

Then try instructions in my post **#23**

---

### Post by drewbird on 2012-05-27
Thanks for all the help fantab. I wasn't having any luck with the locale stuff, so I just reinstalled it and now it is working perfectly fine.

Thanks again! Cheers!

---

