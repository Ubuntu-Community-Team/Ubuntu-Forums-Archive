---
title: "Update Manager Failed: Reporting the Bug"
date: 2012-06-03
forum: New to Ubuntu
---

### Post by namanmody on 2012-06-03
I tried installing the gnome 3 desktop environment my recently installed Ubuntu 12.04 LTS Unity, but couldn't. 

I got the same error message after the 'sudo get apt update' command in the same process as well as while I attempted to install the Adobe Acrobat Reader. 

Ubuntu tells me to report the bug. Here's the message:

> An unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Malformed line 6 in source list /etc/apt/sources.list (dist parse)'

---

### Post by raja.genupula on 2012-06-03
open your terminal and post the ouput of this command to here and wrap it between CODE tags 

```
cat /etc/apt/sources.list
```

---

### Post by namanmody on 2012-06-03
I'm new to ubuntu. Here's what I get: 

Now even the software manager's not working.  It's all going haywire. I'm having a disappointing start with ubuntu. :-(

```
deb http://archive.ubuntu.com/ubuntu/ precise main restricted universe multiverse
deb http://security.ubuntu.com/ubuntu/ precise-security main restricted universe multiverse
deb http://archive.ubuntu.com/ubuntu/ precise-updates main restricted universe multiverse
deb http://archive.canonical.com/precise partner
deb-src http://archive.canonical.com/precise partner

```

---

### Post by raja.genupula on 2012-06-04
ok now do as

```
sudo gedit /etc/apt/sources.list
```

and remove everything in that file and paste this code 
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

#### Gimp - https://launchpad.net/~otto-kesselgulasch/+archive/gimp
## Run this command: sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 614C4B38
deb http://ppa.launchpad.net/otto-kesselgulasch/gimp/ubuntu precise main

#### Google Linux Software Repositories - http://www.google.com/linuxrepositories/
## Run this command: wget -q https://dl-ssl.google.com/linux/linux_signing_key.pub -O- | sudo apt-key add -
deb http://dl.google.com/linux/deb/ stable non-free

#### Google Linux Software Repositories (Testing) - http://www.google.com/linuxrepositories/
## Run this command: wget -q -O - https://dl-ssl.google.com/linux/linux_signing_key.pub | sudo apt-key add  -
deb http://dl.google.com/linux/deb/ testing non-free

#### Gwibber (Daily) - https://launchpad.net/gwibber
## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 72D340A3
deb http://ppa.launchpad.net/gwibber-daily/ppa/ubuntu precise main

#### Medibuntu - http://www.medibuntu.org/ 
## Run this command: sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update 
deb http://packages.medibuntu.org/ precise free non-free 

#### Midori - https://launchpad.net/~midori/+archive/ppa
## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys A69241F1
deb http://ppa.launchpad.net/midori/ppa/ubuntu precise main

#### Mozilla Daily Build Team - http://edge.launchpad.net/~ubuntu-mozilla-daily/+archive/ppa
## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys  247510BE
deb http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu precise main

#### PlayOnLinux - http://www.playonlinux.com/en
## Run this command: wget -q "http://deb.playonlinux.com/public.gpg" -O- | sudo apt-key add -
deb http://deb.playonlinux.com/ precise main

#### Ubuntu Tweak - http://ubuntu-tweak.com/
## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 0624A220
deb http://ppa.launchpad.net/tualatrix/ubuntu precise main

#### UNetbootin - http://unetbootin.sourceforge.net/
## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys FC91AE7E
deb http://ppa.launchpad.net/gezakovacs/ppa/ubuntu precise main

#### VirtualBox - http://www.virtualbox.org
## Run this command: wget -q http://download.virtualbox.org/virtualbox/debian/oracle_vbox.asc -O- | sudo apt-key add -
deb http://download.virtualbox.org/virtualbox/debian precise contrib

#### Wine - https://launchpad.net/~ubuntu-wine/+archive/ppa/
## Run this command:  sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys F9CB8DB0
deb http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu precise main


####### 3rd Party Source Repos

#### Gimp (Source) - https://launchpad.net/~otto-kesselgulasch/+archive/gimp
## Run this command: sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 614C4B38
deb-src http://ppa.launchpad.net/otto-kesselgulasch/gimp/ubuntu precise main

#### Gwibber (Daily) (Source) - https://launchpad.net/gwibber
## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 72D340A3
deb-src http://ppa.launchpad.net/gwibber-daily/ppa/ubuntu precise main

#### Medibuntu (Source) - http://www.medibuntu.org/ 
## Run this command: sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update 
deb-src http://packages.medibuntu.org/ precise free non-free 

#### Midori (Source) - https://launchpad.net/~midori/+archive/ppa
## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys A69241F1
deb-src http://ppa.launchpad.net/midori/ppa/ubuntu precise main

#### Mozilla Daily Build Team (Source) - http://edge.launchpad.net/~ubuntu-mozilla-daily/+archive/ppa
## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys  247510BE
deb-src http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu precise main

#### Ubuntu Tweak (Source) - http://ubuntu-tweak.com/
## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 0624A220
deb-src http://ppa.launchpad.net/tualatrix/ubuntu precise main

#### UNetbootin (Source) - http://unetbootin.sourceforge.net/
## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys FC91AE7E
deb-src http://ppa.launchpad.net/gezakovacs/ppa/ubuntu precise main

#### Wine (Source) - https://launchpad.net/~ubuntu-wine/+archive/ppa/
## Run this command:  sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys F9CB8DB0
deb-src http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu precise main 



```

Then execute the following commands one bye one 

```
sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 614C4B38
wget -q https://dl-ssl.google.com/linux/linux_signing_key.pub -O- | sudo apt-key add -
wget -q -O - https://dl-ssl.google.com/linux/linux_signing_key.pub | sudo apt-key add  -
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 72D340A3
sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update 
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys A69241F1
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys  247510BE
wget -q "http://deb.playonlinux.com/public.gpg" -O- | sudo apt-key add -
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 0624A220
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys FC91AE7E
wget -q http://download.virtualbox.org/virtualbox/debian/oracle_vbox.asc -O- | sudo apt-key add -
 sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys F9CB8DB0
```

then try again . 

all the best :)

---

### Post by mörgæs on 2012-06-04
I'm not sure I would support this advice. 

Raja, you are recommending a very complicated setup with lots of PPA's that original poster probably does not need.

---

### Post by raja.genupula on 2012-06-04
@mörgæs +1 , but OP may be need them in future so i have given like that .

---

### Post by mörgæs on 2012-06-04
Namanmody, please restart the computer and run

```
sudo apt-get update
```

and post the complete output.

---

### Post by namanmody on 2012-06-06
Morgaes, 
I get this out put after sudo get-apt update. 

```

E: Malformed line 6 in source list /etc/apt/sources.list (dist parse)
E: The list of sources could not be read.

```

---

### Post by mörgæs on 2012-06-06
Then I'm out of ideas. Let's try moving it to another forum.

---

### Post by namanmody on 2012-06-09
Running the commands given by Raja seems to have got back the Software Manager to normal functioning! 

Now I am left with the task of installing the update manager. ? 

Please help.

---

