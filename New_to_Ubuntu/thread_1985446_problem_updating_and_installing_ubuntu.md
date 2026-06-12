---
title: "problem updating and installing ubuntu"
date: 2012-05-23
forum: New to Ubuntu
---

### Post by ubun123 on 2012-05-23
Hi,

I am new to ubuntu. Let me explain the problem in detail along with the steps taken :

-> created an new virtual machine on vm player
-> path given as the location of ubuntu iso file
-> after connecting the terminal, gave following command: (logged in as sudo/root)
->proxy connections set in browser as well as System settings-> network
-> Command: apt-get install update

Got following error:

```
 E: Unable to locate package update 
```

At one point, got following error:
```

Could not get lock /var/lib/apt/lists/lock - open (11: Resource temporarily unavailable)

```

To this, did following:

Command: sudo rm /var/lib/apt/lists/lock

But the update is not going through. It stucks at 16% or 17% or at times at 0% at following execution line:

[Connecting to us.archive.ubuntu.com (91.189.92.180)] [Connecting to security.ubuntu.com (91.189.92.181)]

-----------------------------------------------------

Please find below the entire console:

```

oot@ubuntu:~# apt-get install update
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package update
root@ubuntu:~# apt-get install update
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package update
root@ubuntu:~# ^C
root@ubuntu:~# apt-get update
E: Could not get lock /var/lib/apt/lists/lock - open (11: Resource temporarily unavailable)
E: Unable to lock directory /var/lib/apt/lists/
root@ubuntu:~# sudo rm /var/lib/apt/lists/lock
root@ubuntu:~# apt-get install update
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package update
root@ubuntu:~# sudo rm /var/lib/apt/lists
rm: cannot remove `/var/lib/apt/lists': Is a directory
root@ubuntu:~# apt-get install update
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package update
root@ubuntu:~# sudo apt-get update
Err http://extras.ubuntu.com oneiric InRelease                                 
  
Err http://extras.ubuntu.com oneiric Release.gpg                               
  Unable to connect to extras.ubuntu.com:http:
Err http://security.ubuntu.com oneiric-security InRelease                      
  
Err http://security.ubuntu.com oneiric-security Release.gpg                    
  Unable to connect to security.ubuntu.com:http: [IP: 91.189.92.181 80]
Err http://us.archive.ubuntu.com oneiric InRelease      
  
Err http://us.archive.ubuntu.com oneiric-updates InRelease
  
Err http://us.archive.ubuntu.com oneiric-backports InRelease
  
Err http://us.archive.ubuntu.com oneiric Release.gpg    
  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.92.151 80]
Err http://us.archive.ubuntu.com oneiric-updates Release.gpg
  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.92.151 80]
Err http://us.archive.ubuntu.com oneiric-backports Release.gpg
  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.92.151 80]
Reading package lists... Done
W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/oneiric/InRelease  

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/oneiric-updates/InRelease  

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/oneiric-backports/InRelease  

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/oneiric-security/InRelease  

W: Failed to fetch http://extras.ubuntu.com/ubuntu/dists/oneiric/InRelease  

W: Failed to fetch http://extras.ubuntu.com/ubuntu/dists/oneiric/Release.gpg  Unable to connect to extras.ubuntu.com:http:

W:  Failed to fetch  http://security.ubuntu.com/ubuntu/dists/oneiric-security/Release.gpg   Unable to connect to security.ubuntu.com:http: [IP: 91.189.92.181 80]

W:  Failed to fetch  http://us.archive.ubuntu.com/ubuntu/dists/oneiric/Release.gpg  Unable to  connect to us.archive.ubuntu.com:http: [IP: 91.189.92.151 80]

W:  Failed to fetch  http://us.archive.ubuntu.com/ubuntu/dists/oneiric-updates/Release.gpg   Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.92.151 80]

W:  Failed to fetch  http://us.archive.ubuntu.com/ubuntu/dists/oneiric-backports/Release.gpg   Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.92.151 80]

W: Some index files failed to download. They have been ignored, or old ones used instead.


```


pls suggest

---

### Post by ubun123 on 2012-05-23
Hi,

I am new to ubuntu. Let me explain the problem in detail along with the steps taken :

-> created an new virtual machine on vm player
-> path given as the location of ubuntu iso file
-> after connecting the terminal, gave following command: (logged in as sudo/root)
->proxy connections set in browser as well as System settings-> network
-> Command: apt-get install update

Got following error:

```
 E: Unable to locate package update 
```

At one point, got following error:
```

Could not get lock /var/lib/apt/lists/lock - open (11: Resource temporarily unavailable)

```

To this, did following:

Command: sudo rm /var/lib/apt/lists/lock

But the update is not going through. It stucks at 16% or 17% or at times at 0% at following execution line:

[Connecting to us.archive.ubuntu.com (91.189.92.180)] [Connecting to security.ubuntu.com (91.189.92.181)]

-----------------------------------------------------

Please find below the entire console:

```

oot@ubuntu:~# apt-get install update
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package update
root@ubuntu:~# apt-get install update
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package update
root@ubuntu:~# ^C
root@ubuntu:~# apt-get update
E: Could not get lock /var/lib/apt/lists/lock - open (11: Resource temporarily unavailable)
E: Unable to lock directory /var/lib/apt/lists/
root@ubuntu:~# sudo rm /var/lib/apt/lists/lock
root@ubuntu:~# apt-get install update
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package update
root@ubuntu:~# sudo rm /var/lib/apt/lists
rm: cannot remove `/var/lib/apt/lists': Is a directory
root@ubuntu:~# apt-get install update
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package update
root@ubuntu:~# sudo apt-get update
Err http://extras.ubuntu.com oneiric InRelease                                 
  
Err http://extras.ubuntu.com oneiric Release.gpg                               
  Unable to connect to extras.ubuntu.com:http:
Err http://security.ubuntu.com oneiric-security InRelease                      
  
Err http://security.ubuntu.com oneiric-security Release.gpg                    
  Unable to connect to security.ubuntu.com:http: [IP: 91.189.92.181 80]
Err http://us.archive.ubuntu.com oneiric InRelease      
  
Err http://us.archive.ubuntu.com oneiric-updates InRelease
  
Err http://us.archive.ubuntu.com oneiric-backports InRelease
  
Err http://us.archive.ubuntu.com oneiric Release.gpg    
  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.92.151 80]
Err http://us.archive.ubuntu.com oneiric-updates Release.gpg
  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.92.151 80]
Err http://us.archive.ubuntu.com oneiric-backports Release.gpg
  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.92.151 80]
Reading package lists... Done
W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/oneiric/InRelease  

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/oneiric-updates/InRelease  

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/oneiric-backports/InRelease  

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/oneiric-security/InRelease  

W: Failed to fetch http://extras.ubuntu.com/ubuntu/dists/oneiric/InRelease  

W: Failed to fetch http://extras.ubuntu.com/ubuntu/dists/oneiric/Release.gpg  Unable to connect to extras.ubuntu.com:http:

W:  Failed to fetch  http://security.ubuntu.com/ubuntu/dists/oneiric-security/Release.gpg   Unable to connect to security.ubuntu.com:http: [IP: 91.189.92.181 80]

W:  Failed to fetch  http://us.archive.ubuntu.com/ubuntu/dists/oneiric/Release.gpg  Unable to  connect to us.archive.ubuntu.com:http: [IP: 91.189.92.151 80]

W:  Failed to fetch  http://us.archive.ubuntu.com/ubuntu/dists/oneiric-updates/Release.gpg   Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.92.151 80]

W:  Failed to fetch  http://us.archive.ubuntu.com/ubuntu/dists/oneiric-backports/Release.gpg   Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.92.151 80]

W: Some index files failed to download. They have been ignored, or old ones used instead.


```


pls suggest

---

### Post by NikTh on 2012-05-23
If you want to update your system , the proper command is ```
sudo apt-get update ; sudo apt-get upgrade
``` **and not** ```
sudo apt-get [COLOR=Red]install[/COLOR] update
``` when you give the install command then Ubuntu search for the appropriate package after install , in your case **update**. So the result is 
"Unable to locate package update"

For the second message 

```
E: Could not get lock /var/lib/apt/lists/lock - open (11: Resource temporarily unavailable)
```

Just make sure that you have not open anything like Update Manager at the same time that you execute the update command.

---

### Post by roelforg on 2012-05-23
The command should be:
```

apt-get update

```
 
EDIT:
Do you use a proxy?

---

### Post by coffeecat on 2012-05-23
Duplicate threads merged.

---

### Post by cortman on 2012-05-23
It looks as though the proxy isn't configured correctly. I assume you're using Firefox for a browser; set the proxy connection there to "use system proxy" and see if you can connect to Google or any other website.

---

### Post by ubun123 on 2012-05-24
yes , m using firefox and proxy is set there to system proxy only. I am able to connect to Google or any other website from there.

---

### Post by roelforg on 2012-05-24
This article'll tell you a setting for apt-get for proxies (it sometimes won't play nice with sys proxy):
[http://askubuntu.com/questions/89437/how-to-install-packages-with-apt-get-on-a-system-connected-via-proxy](http://askubuntu.com/questions/89437/how-to-install-packages-with-apt-get-on-a-system-connected-via-proxy)

---

### Post by cortman on 2012-05-24
I've had success using apt with sys proxy, but I can easily see it being a kind of hit-or-miss thing. Good link roelforg.

---

### Post by ubun123 on 2012-05-25
Thanks lot! it was issue with providing username along with proxy. that link really helped! :)

---

### Post by ubun123 on 2012-05-25
I tried the following :

```
root@ubuntu:/etc/apt# tasksel install lamp-server 
```

And got error as:

```

The program 'tasksel' is currently not installed.  You can install it by typing:
apt-get install tasksel

```

Now, am trying the following:

```
root@ubuntu:/etc/apt# apt-get install tasksel 
```

And getting the  following console and error:

```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package tasksel

```

Pls suggest a solution.

---

### Post by roelforg on 2012-05-25
> **ubun123 said:**
> I tried the following :
 
```
root@ubuntu:/etc/apt# tasksel install lamp-server 
```
 
And got error as:
 
```

The program 'tasksel' is currently not installed.  You can install it by typing:
apt-get install tasksel

```
 
Now, am trying the following:
 
```
root@ubuntu:/etc/apt# apt-get install tasksel 
```
 
And getting the following console and error:
 
```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package tasksel

```
 
Pls suggest a solution.
 
Try: 
```

sudo apt-get update
sudo apt-get install tasksel
sudo tasksel install lamp-server

```
 
Or install all the packages manually (lamp-server is a meta package):
```

sudo apt-get install apache2 apache2-mpm-prefork apache2-utils apache2.2-common libapache2-mod-php5 libapr1 libaprutil1 libdbd-mysql-perl libdbi-perl libmysqlclient15off libnet-daemon-perl libplrpc-perl libpq5 mysql-client-5.0 mysql-common mysql-server mysql-server-5.0 php5-common php5-mysql

```

---

### Post by ubun123 on 2012-05-25
```
sudo apt-get update
sudo apt-get install tasksel

```
 
The above lines give me following err:
 
```
Unable to locate package tasksel  
```

---

### Post by roelforg on 2012-05-25
Post the contents of /etc/apt/sources.list

---

### Post by ubun123 on 2012-05-29
PFB contents of etc/apt/sources.list

```


#deb cdrom:[Ubuntu 11.10 _Oneiric Ocelot_ - Release i386 (20111012)]/ oneiric main restricted

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

deb http://security.ubuntu.com/ubuntu oneiric-security main restricted
deb-src http://security.ubuntu.com/ubuntu oneiric-security main restricted
deb http://security.ubuntu.com/ubuntu oneiric-security universe
deb-src http://security.ubuntu.com/ubuntu oneiric-security universe
deb http://security.ubuntu.com/ubuntu oneiric-security multiverse
deb-src http://security.ubuntu.com/ubuntu oneiric-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu oneiric partner
# deb-src http://archive.canonical.com/ubuntu oneiric partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb http://extras.ubuntu.com/ubuntu oneiric main
deb-src http://extras.ubuntu.com/ubuntu oneiric main


```

---

