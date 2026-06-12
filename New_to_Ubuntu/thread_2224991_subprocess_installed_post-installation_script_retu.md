---
title: "subprocess installed post-installation script returned error exit status 127"
date: 2014-05-19
forum: New to Ubuntu
---

### Post by ryan85 on 2014-05-19
I am having a little problem. Relatively new to Ubuntu and am trying to get Solr installed in my local environment. I was able to install solr-tomcat without issue using apt-get, but this was the wrong distro for solr that I was looking for. So I purged solr-tomcat and all config. Then install solr-jetty and found this to be wrong as well, so puged that install as well. I then decided to install tomcat6 as standalone and then download solr version pakage that I wanted and configure. I thought this was successful until I tried to restart tomcat. Now if I try to restart tomcat or run apt-get upgrade, or install any other pakage I am getting errors. here is my output for commands:

```
sudo aptitude install tomcat6


The following partially installed packages will be configured:
  tomcat6 
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0 B of archives. After unpacking 0 B will be used.
Setting up tomcat6 (6.0.39-1) ...        
/var/lib/dpkg/info/tomcat6.config: 1: /etc/default/tomcat6: TOMCAT6: not found
dpkg: error processing package tomcat6 (--configure):
 subprocess installed post-installation script returned error exit status 127
Errors were encountered while processing:
 tomcat6
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
```

Then ran:
```
sudo aptitude install -f

The following NEW packages will be installed:
  authbind libservlet3.0-java libtomcat7-java tomcat7 tomcat7-common 
The following packages will be REMOVED:
  libtomcat6-java{u} tomcat6-common{u} 
The following partially installed packages will be configured:
  tomcat6{b} 
0 packages upgraded, 5 newly installed, 2 to remove and 0 not upgraded.
Need to get 0 B/4,043 kB of archives. After unpacking 1,681 kB will be used.
The following packages have unmet dependencies:
 tomcat6 : Depends: tomcat6-common (>= 6.0.39-1) but it is not going to be installed.
The following actions will resolve these dependencies:

     Remove the following packages:
1)     tomcat6                     



Accept this solution? [Y/n/q/?] y
The following NEW packages will be installed:
  authbind libservlet3.0-java libtomcat7-java tomcat7 tomcat7-common 
The following packages will be REMOVED:
  libtomcat6-java{u} tomcat6{a} tomcat6-common{u} 
0 packages upgraded, 5 newly installed, 3 to remove and 0 not upgraded.
Need to get 0 B/4,043 kB of archives. After unpacking 1,311 kB will be used.
Do you want to continue? [Y/n/?] y
Preconfiguring packages ...              
(Reading database ... 173922 files and directories currently installed.)
Removing tomcat6 (6.0.39-1) ...
/var/lib/dpkg/info/tomcat6.prerm: 1: /etc/default/tomcat6: TOMCAT6: not found
dpkg: error processing package tomcat6 (--remove):
 subprocess installed pre-removal script returned error exit status 127
/var/lib/dpkg/info/tomcat6.config: 1: /etc/default/tomcat6: TOMCAT6: not found
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 127
Removing tomcat6-common (6.0.39-1) ...
Removing libtomcat6-java (6.0.39-1) ...
Errors were encountered while processing:
 tomcat6
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
                                         
Current status: 1 broken [+1].
```

I have tried searching the forums, and all of Google for that matter, and I just can't figure this one out. At this point I just want to remove all of Tomcat6 so I have a clean slate. Then I will try it again, but am just stuck for right now. Any suggestions are greatly appreciated.

---

### Post by matt_symes on 2014-05-19
Hi

Installation is failing due to a missing file.

Quite why this file is missing, i`m not sure.

What i would do first is try to reinstall tomcat to see if that fixes it.

sudo dpkg install --reinstall PACKAGE_NAME

and then run

sudo apt-get install -f

If that does not work then create the missing file manually

sudo touch /etc/default/FILENAME

And then run the apt-get command again.

Change PACKAGD_NAME and FILENAME as required.

If your still having problems i will next login on wednesday but in the meantime, i`m sure others can help you

Kind regarda

---

### Post by Danger_Monkey on 2014-05-19
I'm with Matt, it looks like tomcat6 was only partially installed.  It might be able to remove it if you:

```

touch /etc/default/tomcat6

```
and try removing again.  I have quite a few Solr servers, I would just download the packages you want to use from Apache, and extract them in /opt/  Then install openjdk-jre7, and away you go.  It's surprisingly easy to do.

---

