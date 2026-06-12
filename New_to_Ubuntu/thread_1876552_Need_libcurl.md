---
title: "Need libcurl"
date: 2011-11-06
forum: New to Ubuntu
---

### Post by ericstrom on 2011-11-06
Using Lucid Lynx and trying into install a package into R but getting an error that curl-config can't be found.

* installing *source* package ‘RCurl’ ... 
> checking for curl-config... no 
> Cannot find curl-config 
> ERROR: configuration failed for package ‘RCurl’ 

I went to the R help formum and am being advised that I need to install libcurl-dev:

First Response:
I think you are on Linux and missing the library headers to build 
against the curl.  On Fedora or RedHat you would do something like 
'sudo yum -y install curl-devel' and on Ubuntu it may be  'sudo 
apt-get install curl-dev' 

Second response:
This is something missing from your (unstated) Linux installation. 

curl-config is part of the original libcurl sources, but Linux 
distributors tend to separte it out.  *How* they do so is 
non-standard: 

Fedora and other RPM-based distributions tend to use libcurl-devel 
Debian and related tend to use libcurl-dev 

So I tried the following command and it didn't work:

eric@desktop:~$ apt-get install curl-dev
E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
eric@desktop:~$ 

Next I tried tried apt-get install libcurl-dev .... getting the following message:

eric@desktop:~$ sudo apt-get install libcurl-dev 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package libcurl-dev is a virtual package provided by:
  libcurl4-openssl-dev 7.19.7-1ubuntu1.1
  libcurl4-gnutls-dev 7.19.7-1ubuntu1.1
You should explicitly select one to install.
E: Package libcurl-dev has no installation candidate

What is the correct command to get this done ?

---

### Post by ubudog on 2011-11-06
Here, try this:
```
sudo apt-get install curl-dev
```
You will have to enter your password, which will be totally invisible.

You may also want to open up Synaptic, it's easier to use, and you can install multiple packages at a time. 

Enjoy!  :)

---

### Post by ericstrom on 2011-11-06
I tried the command that was suggested. Here is the output:


eric@desktop:~$ sudo apt-get install curl-dev
[sudo] password for eric: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package curl-dev

What should I try now ?

---

### Post by beew on 2011-11-06
To install things with the "sudo apt-get install" command you need to know the exact name of the package. If you are not sure it is better to use the Synaptic package manager which has a search function. Synaptic appears under System > Administration in Lucid Lynx. 

I am on Natty and just did a search in Synaptic. There is no package called curl-dev or libcurl-dev, however, there are three packages with names libcurl4-xxx-dev. The description is that "these files allow to build software with libcurl". You may try install these and see if it works. In Lucid the version number may be different (so instead of libcurl4 you may have some other number)

---

### Post by ubudog on 2011-11-06
> **beew said:**
> to install things with the "sudo apt-get install" command you need to know the exact name of the package. If you are not sure it is better to use the synaptic package manager which has a search function. Synaptic appears under system > administration in lucid lynx. 

I am on natty and just did a search in synaptic. There is no package called curl-dev or libcurl-dev, however, there are three packages with names libcurl4-xxx-dev. The description is that "these files allow to build software with libcurl". You may try install these and see if it works. In lucid the version number may be different (so instead of libcurl4 you may have some other number)

+1!

---

