---
title: "Issues downloading / updating / connecting"
date: 2012-08-10
forum: New to Ubuntu
---

### Post by Shweebz on 2012-08-10
Hello experts,

New Linux user here.  I did a full installation of Ubuntu 12.04LTS, but have encountered several issues:

Preface: I have Internet connection, but am connecting through a work VPN.  I use Cisco AnyConnect VPN Client, and use an "Automatic proxy configuration URL": [http://wpad/wpad.dat](http://wpad/wpad.dat) to connect using firefox. 

Yesterday I tried to install GASP using: sudo apt-get python-gasp.  I got this in response:

jfujimoto@ubuntu:~$ sudo apt-get install python-gasp
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package python-gasp

After some digging, I added repositories.  Here is my /etc/apt/sources.list file:

#############################################################
################### OFFICIAL UBUNTU REPOS ###################
#############################################################

###### Ubuntu Main Repos
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise main restricted universe multiverse 
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise main restricted universe multiverse 
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise main universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise main universe

###### Ubuntu Update Repos
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-security main restricted universe multiverse 
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates main restricted universe multiverse 
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-proposed main restricted universe multiverse 
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-backports main restricted universe multiverse 
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-security main restricted universe multiverse 
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates main restricted universe multiverse 
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-proposed main restricted universe multiverse 
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-backports main restricted universe multiverse 
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-security main universe
deb [http://us.archive.ubuntu.com/](http://us.archive.ubuntu.com/) precise-updates main universe

Then I tried doing a sudo apt-get update and got the following:

jfujimoto@ubuntu:~$ sudo apt-get update
0% [Connecting to us.archive.ubuntu.com (91.189.91.25)]

...Stays at this for a while (10 minutes+) before I ultimately shut it down.  So I then tried to change servers using "find best server".  The response I got back was "No suitable download server was found.  Please check your Internet Connection".  

I thought it could be the proxy or vpn, but when I tried doing this at home, I encountered the exact same issues.  Any thoughts?  If it is an issue with the proxy/vpn is there a workaround?  Any help, guidance would be greatly appreciate.d

Thank you!

---

### Post by cortman on 2012-08-10
The reason GASP didn't install is because the command was slightly off- it should be

```
sudo apt-get **install** python-gasp
```

As far as not downloading updates... That looks like a proxy issue.
Do you have the System proxy set, or just Firefox? You can set the automatic configuration url in the System Settings as well.

EDIT: Plus, it looks like your sources.list has duplicates:

```

################################################## ###########
################### OFFICIAL UBUNTU REPOS ###################
################################################## ###########

###### Ubuntu Main Repos
deb http://us.archive.ubuntu.com/ubuntu/ precise main restricted universe multiverse 
deb-src http://us.archive.ubuntu.com/ubuntu/ precise main restricted universe multiverse 
[B]deb http://us.archive.ubuntu.com/ubuntu/ precise main universe
deb-src http://us.archive.ubuntu.com/ubuntu/ precise main universe[/B]

###### Ubuntu Update Repos
deb http://us.archive.ubuntu.com/ubuntu/ precise-security main restricted universe multiverse 
deb http://us.archive.ubuntu.com/ubuntu/ precise-updates main restricted universe multiverse 
deb http://us.archive.ubuntu.com/ubuntu/ precise-proposed main restricted universe multiverse 
deb http://us.archive.ubuntu.com/ubuntu/ precise-backports main restricted universe multiverse 
deb-src http://us.archive.ubuntu.com/ubuntu/ precise-security main restricted universe multiverse 
deb-src http://us.archive.ubuntu.com/ubuntu/ precise-updates main restricted universe multiverse 
deb-src http://us.archive.ubuntu.com/ubuntu/ precise-proposed main restricted universe multiverse 
deb-src http://us.archive.ubuntu.com/ubuntu/ precise-backports main restricted universe multiverse 
[B]deb http://us.archive.ubuntu.com/ubuntu/ precise-security main universe
deb http://us.archive.ubuntu.com/ precise-updates main universe
[/B]

```

The lines in bold should be removed.

---

### Post by Shweebz on 2012-08-10
Thanks for the response.  I corrected the command, but still got the same error.  I also deleted the duplicate repositories without any luck.

I only had the proxy configured in firefox, but I just added the proxy in network settings (system wide), restarted, and still can't update or download anything.

---

### Post by cortman on 2012-08-10
Do you know the details of the proxy enough to manually configure it?
That would be the next step.

---

### Post by Shweebz on 2012-08-10
I unfortunately do not.  Meh...I guess I might just have to stick to limited access (solely internet browsing) while at work.  Thanks for the help cortman!

---

### Post by cortman on 2012-08-10
> **Shweebz said:**
> I unfortunately do not.  Meh...I guess I might just have to stick to limited access (solely internet browsing) while at work.  Thanks for the help cortman!

I wonder if something like [this]("http://mihirknows.blogspot.com/2010/02/ubuntu-910-setting-up-auto-detect-proxy.html") isn't what you're dealing with... Hope it helps.
You're quite welcome for the help; sorry it's not more effective. :?

---

