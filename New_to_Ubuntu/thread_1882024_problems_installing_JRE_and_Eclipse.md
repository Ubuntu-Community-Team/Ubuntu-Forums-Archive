---
title: "problems installing JRE and Eclipse"
date: 2011-11-16
forum: New to Ubuntu
---

### Post by ub1922 on 2011-11-16
I just installed UBUNTU 11.10 on my laptop.
Have connection to the Internet.

I am trying to install Java and Eclipse. 
There are few problem I have encountered.

1.  Eclipse does not find Java

2.  While trying to install Java JRE the  sudo apt-get update - could not connect to any of the servers.
More when I tried to Find best server, it gave me a message, no Internet connection. I have no problem finding packages in Mozilla. Am I missing some settings for Software Center or what?

3. I downloaded jre1.6.0_29, unpacked and now I have a folder with some files in it. How to I know that this Java JRE is installed?

Thank you for your help.

---

### Post by thatguruguy on 2011-11-16
Where did you download the jre from?

Have you tried installing the openjdk from the Ubuntu Software Center?

---

### Post by ub1922 on 2011-11-16
ubuntu software center cannot download anything

it gets stuck during download

---

### Post by thatguruguy on 2011-11-16
Well, that seems like the first problem to solve.

Open a terminal and type: 
```
software-center
```

Let's see if we can get that problem solved.

---

### Post by ub1922 on 2011-11-16
[FONT=Courier New]2011-11-16 10:49:53,976 - softwarecenter.ui.gtk3.em - INFO - EM's: 17 15 21[/FONT]

---

### Post by ub1922 on 2011-11-16
as you said I tried openjdk again.

in the progress tab I can see [INDENT]```
Updating Cache 
Downloaded 0 B of 14 B 
``` [/INDENT]it could stay like this forever

---

### Post by thatguruguy on 2011-11-16
So far, so good.

Actually, close the software center, and type the following into a terminal:
```
sudo apt-get update
```
It will prompt you for your password.  Post the terminal output here.

Also, please wrap the output in code tags.

---

### Post by ub1922 on 2011-11-16
```
ub1922@ub1922:~$ sudo apt-get update
[sudo] password for ub1922: 
E: Could not get lock /var/lib/apt/lists/lock - open (11: Resource temporarily unavailable)
E: Unable to lock directory /var/lib/apt/lists/
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
ub1922@ub1922:~$ 
```

 I tried this as well

sometimes it gives me this
sometimes it gives me Err Unable to ....

---

### Post by frncz on 2011-11-16
you must close the software centre before running apt-get

---

### Post by ub1922 on 2011-11-16
I just restarted Ubuntu

this is a typical output

```
Err http://ftp.de.debian.org sid InRelease                                                                                         
  
Err http://ftp.de.debian.org sid Release.gpg                                                                                       
  Unable to connect to ftp.de.debian.org:http:
Err http://archive.canonical.com oneiric InRelease                                                                                 
  
Err http://extras.ubuntu.com oneiric InRelease                                                                                     
  
Err http://my.archive.ubuntu.com hardy/main InRelease                                                                              
  
Err http://my.archive.ubuntu.com hardy/multiverse InRelease                                                                        
  
Err http://archive.canonical.com oneiric Release.gpg                                                                               
  Unable to connect to archive.canonical.com:http:
Err http://extras.ubuntu.com oneiric Release.gpg       
  Unable to connect to extras.ubuntu.com:http:
Err http://my.archive.ubuntu.com hardy/main Release.gpg
  Unable to connect to my.archive.ubuntu.com:http:
Err http://my.archive.ubuntu.com hardy/multiverse Release.gpg
  Unable to connect to my.archive.ubuntu.com:http:
0% [Connecting to us.archive.ubuntu.com (91.189.88.45)]



```it take way too long to go through all the sources...

all of them give me error messages

---

### Post by Gremlinzzz on 2011-11-16
The "sun-java6" package is no longer available in the official Ubuntu 11.10 Oneiric Ocelot repositories due to the removal of the JDL license. Java 7 won't be in Oneiric either, but you still have 3 options:

- Install OpenJDK:

sudo apt-get install openjdk-7-jre


- Or Oracle (previously Sun) Java 6 from the LFFL PPA:

sudo add-apt-repository ppa:ferramroberto/java
sudo apt-get update
sudo apt-get install sun-java6-jdk sun-java6-plugin

:popcorn:

---

### Post by thatguruguy on 2011-11-16
Obviously, this is not a clean install.

You need to clear out your software sources.  You have a lot of things in there that aren't supported (for instance, all of the Hardy entries).  Also, why all the debian sources?

---

### Post by thatguruguy on 2011-11-16
> **Gremlinzzz said:**
> The "sun-java6" package is no longer available in the official Ubuntu 11.10 Oneiric Ocelot repositories due to the removal of the JDL license. Java 7 won't be in Oneiric either, but you still have 3 options:

- Install OpenJDK:

sudo apt-get install openjdk-7-jre


- Or Oracle (previously Sun) Java 6 from the LFFL PPA:

sudo add-apt-repository ppa:ferramroberto/java
sudo apt-get update
sudo apt-get install sun-java6-jdk sun-java6-plugin



Yeah, but java 7 will be based on openjdk 7.  And seriously, before adding another ppa he needs to get the ones he has under control.

---

### Post by ub1922 on 2011-11-16
ok, lets clean them out

this is a clean install. Just did it this morning.

I feel like there is a problem with proxy settings or something.
but lets first clean the sources:

this is my source list:
```

# deb cdrom:[Ubuntu 11.10 _Oneiric Ocelot_ - Release i386 (20111012)]/ oneiric main restricted

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://us.archive.ubuntu.com/ubuntu/ oneiric main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ oneiric main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ oneiric-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ oneiric-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ oneiric universe
deb-src http://us.archive.ubuntu.com/ubuntu/ oneiric universe
deb http://us.archive.ubuntu.com/ubuntu/ oneiric-updates universe
deb-src http://us.archive.ubuntu.com/ubuntu/ oneiric-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ oneiric multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ oneiric multiverse
deb http://us.archive.ubuntu.com/ubuntu/ oneiric-updates multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ oneiric-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ oneiric-backports main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ oneiric-backports main restricted universe multiverse

deb http://us.archive.ubuntu.com/ubuntu/ oneiric-security main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ oneiric-security main restricted
deb http://us.archive.ubuntu.com/ubuntu/ oneiric-security universe
deb-src http://us.archive.ubuntu.com/ubuntu/ oneiric-security universe
deb http://us.archive.ubuntu.com/ubuntu/ oneiric-security multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ oneiric-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu oneiric partner
deb-src http://archive.canonical.com/ubuntu oneiric partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb http://extras.ubuntu.com/ubuntu oneiric main
deb-src http://extras.ubuntu.com/ubuntu oneiric main
deb-src http://ftp.de.debian.org/debian sid main
deb http://my.archive.ubuntu.com hardy/main java-common
deb-src http://my.archive.ubuntu.com hardy/main java-common
deb http://my.archive.ubuntu.com hardy/multiverse sun-java6-jre
deb-src http://my.archive.ubuntu.com hardy/multiverse sun-java6-jre
deb http://my.archive.ubuntu.com hardy/main odbcinstldebianl
deb-src http://my.archive.ubuntu.com hardy/main odbcinstldebianl
deb http://my.archive.ubuntu.com hardy/main unixodbc
deb-src http://my.archive.ubuntu.com hardy/main unixodbc
deb http://my.archive.ubuntu.com hardy/multiverse sun-java6-bin
deb-src http://my.archive.ubuntu.com hardy/multiverse sun-java6-bin
deb http://my.archive.ubuntu.com hardy/multiverse sun-java6-jdk
deb-src http://my.archive.ubuntu.com hardy/multiverse sun-java6-jdk

```

---

### Post by ub1922 on 2011-11-16
what shall I keep?

---

### Post by thatguruguy on 2011-11-16
It is inconceivable that it is a "clean install" and yet shows the hardy repositories.  Perhaps you are using the expression "clean install" in a way that I don't.  Unless you added the hardy and debian repositories by hand.  Is that what happened?

Moreover, not all ppas are listed in the sources.list file.  Now, they'll be individual files in /etc/apt/sources.list.d

The easiest way to deal with repositories is to use the Software Sources tool available in system settings.  If you truly have a clean install, you should have an icon which looks like a wrench over a large gear in your launcher (the sidebar).  If not, click on the icon which looks like a gear in the right-hand corner of the top unity bar, and choose "System Settings...", and then choose "Software Sources."

Go to the second tab of Software Sources and clear out anything that is not an Oneiric repository.  In your case, anything relating to Debian Sid and/or Ubuntu Hardy.

---

### Post by ub1922 on 2011-11-16
done.

This is a new look.

```

# deb cdrom:[Ubuntu 11.10 _Oneiric Ocelot_ - Release i386 (20111012)]/ oneiric main restricted

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://us.archive.ubuntu.com/ubuntu/ oneiric restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ oneiric restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ oneiric-updates restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ oneiric-updates restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ oneiric multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ oneiric multiverse
deb http://us.archive.ubuntu.com/ubuntu/ oneiric-updates multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ oneiric-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ oneiric-backports restricted multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ oneiric-backports restricted multiverse

deb http://us.archive.ubuntu.com/ubuntu/ oneiric-security restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ oneiric-security restricted
deb http://us.archive.ubuntu.com/ubuntu/ oneiric-security multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ oneiric-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu oneiric partner
deb-src http://archive.canonical.com/ubuntu oneiric partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb http://extras.ubuntu.com/ubuntu oneiric main
deb-src http://extras.ubuntu.com/ubuntu oneiric main

```

---

### Post by thatguruguy on 2011-11-16
Try:
```
sudo apt-get update
```
... again, and let's see if your results make more sense.

---

### Post by ub1922 on 2011-11-16
nope,

same thing... :-(

 I had done this 100 times today...

I wonder how to configure proxy on this software center

Are there any global variables I must set?

---

### Post by thatguruguy on 2011-11-16
Could you post the results here, by any chance?

---

### Post by ub1922 on 2011-11-16
absolutely!
I really appreciate any help I can get. 
it takes a while to run. This is what I got so far. When it will finish I will edit to paste the whole thing
```

ub1922@ub1922:~$ sudo apt-get update
[sudo] password for ub1922: 
Err http://extras.ubuntu.com oneiric InRelease                                 
  
Err http://extras.ubuntu.com oneiric Release.gpg                               
  Unable to connect to extras.ubuntu.com:http:
Err http://archive.canonical.com oneiric InRelease                             
  
Err http://archive.canonical.com oneiric Release.gpg                           
  Unable to connect to archive.canonical.com:http:
0% [Connecting to us.archive.ubuntu.com (91.189.92.169)]



```

---

### Post by ub1922 on 2011-11-16
I have to give up on the[FONT=Courier New][SIZE=2] sudo apt-get update[/SIZE][/FONT] now.

Meanwhile I managed to download bins and installed Eclipse and JDK manually.

many thanks to everybody who helped!!!

---

