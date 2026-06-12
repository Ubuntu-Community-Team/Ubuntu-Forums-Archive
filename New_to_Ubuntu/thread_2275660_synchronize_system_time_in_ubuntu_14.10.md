---
title: "synchronize system time in ubuntu 14.10"
date: 2015-04-27
forum: New to Ubuntu
---

### Post by thaniyarasu-gmail on 2015-04-27
recently i installed ubuntu 14.10
i followed 
=>System Setting =>Time & Date =>Set the time O Manually


i manually changed  time by mistake (by pressing "Manually" Radio button)


now my system time is changed 


even [https://github.com](https://github.com)  is not working in browser


getting this error
 
SSL connection error
ERR_SSL_PROTOCOL_ERROR
Hide details
Unable to make a secure connection to the server. This may be a problem with the server, or it may be requiring a client authentication certificate that you don't have.




How can i resolve this ?

---

### Post by thaniyarasu-gmail on 2015-04-27
my country is india
my timezone is Asia/Kolkata
i installed ntp
here is what i tried , but still github.com is not working 

user@ubuntu:~$ sudo service ntp stop
[sudo] password for dev: 
 * Stopping NTP server ntpd                                              [ OK ] 
user@ubuntu:~$ sudo ntpdate pool.ntp.org
28 Apr 13:11:31 ntpdate[1538]: no server suitable for synchronization found
user@ubuntu:~$ 

Help me

---

### Post by ian-weisser on 2015-04-27
> **thaniyarasu-gmail said:**
> i installed ntp
Why? NTP is included with the default install. Had you uninstalled it?

> **thaniyarasu-gmail said:**
> but still github.com is not working
Are you sure you have network connectivity?

I have not needed to use ntpdate in years - NTP is very good.
Back in the old days, here is how I did it:
I don't stop/start NTP
```
$ sudo ntpdate-debian
[sudo] password for ian: 
27 Apr 15:35:06 ntpdate[27813]: adjust time server 38.229.71.1 offset 0.010308 sec
```

---

### Post by ajgreeny on 2015-04-27
Are you sure ntp is part of the default install?  It is not in my Xubuntu 14.04 which has ntpdate instead.

I have not removed ntp, nor added ntpdate.  Is this a difference between 14.04 and 14.10, or perhaps between Ubuntu and Xubuntu?

---

### Post by ian-weisser on 2015-04-27
Ha! You're totally right. More importantly, I was so wrong.
NTP is no longer part of ubuntu-standard, so it's not part of the default install of most flavors.
I don't have NTP installed either.

Instead, an if-up hook runs ntpdate to sync the time whenever a network interface comes up.
I dimly remember discussion on the ubuntu-devel mailing list to try this approach a few cycles back.

So back to the OP's issue: Is there real connectivity on that network connection?

---

### Post by thaniyarasu-gmail on 2015-04-28
i connect internet through corporate proxy "http://mycorporateproxy.com:8080  . i have dual boot , windows 7 & ubuntu 14.10.
i logged into windows , [https://github.com](https://github.com) is working fine in windows. but not working in ubuntu. 
my ubuntu time show 17 seconds behind my real localtime "Asia/Kolkata"

---

