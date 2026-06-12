---
title: "When will the network be ready during the booting?"
date: 2008-01-20
forum: Programming Talk
---

### Post by chenxing on 2008-01-20
I am writing a script. It should be run during the boot process and because it queries a webpage, it must run after the network is ready. 

I put the script in /etc/init.d/ and make a symbol link to it in /etc/rc2.d/S80ipgw . This trick works in almost all other distributions, but fails in ubuntu, it complains that the network is not ready. but if add a "sleep 20" at the begining of the script, it works ( and consume 20 seconds... ).

How can I ensure the script run right after the initialization of network?

---

### Post by naugiedoggie on 2008-01-20
> **chenxing said:**
> I am writing a script. It should be run during the boot process and because it queries a webpage, it must run after the network is ready. 

I put the script in /etc/init.d/ and make a symbol link to it in /etc/rc2.d/S80ipgw . This trick works in almost all other distributions, but fails in ubuntu, it complains that the network is not ready. but if add a "sleep 20" at the begining of the script, it works ( and consume 20 seconds... ).

How can I ensure the script run right after the initialization of network?

Hello,

The proper place to run your own scripts during boot is /etc/rc.local.  This script is always the last script run during the boot process.

Thanks.

mp

---

### Post by chenxing on 2008-01-20
I have tried it and it doesn't work. The network may not be ready even when the rc.local is to be run. (You may write a simple script: rm index.html -f; wget [http://ubuntuforums.org/](http://ubuntuforums.org/) . and let rc.local call it. The wget here always fails during the boot process.)

Besides, I also need to run my script when the system is going down or someone is trying to stop a network interface. Is rc.local called when the system is shutting down?

Another question is that can I put the script into the scripts controling a network interface?

---

### Post by naugiedoggie on 2008-01-20
> **chenxing said:**
> I have tried it and it doesn't work. The network may not be ready even when the rc.local is to be run. (You may write a simple script: rm index.html -f; wget [http://ubuntuforums.org/](http://ubuntuforums.org/) . and let rc.local call it. The wget here always fails during the boot process.)

Besides, I also need to run my script when the system is going down or someone is trying to stop a network interface. Is rc.local called when the system is shutting down?

Another question is that can I put the script into the scripts controling a network interface?

Hello,

The network interface certainly is up by then.  If the system is on dhcp, then it is possible that the interface doesn't have an address by then.  In which case, you have to wait out the dhcp configuration process.  Indeed, that appears to be the case when I test a system here.

Of course, you can put anything anywhere you want, it's your system and you are root.  It's just not best practice to modify boot scripts.   That is the reason that /etc/rc.local exists.

There is always a time when changes have to be implemented in the boot process, because there is no reasonable alternative.  The question is, is this one of them?  

There are several tools available that may be of use if you are going to play with the boot scripts.

```
man update-rc.d
sudo apt-get install sysv-rc-conf
sudo apt-get install bum

```
Thanks.

mp

---

### Post by chenxing on 2008-01-20
Thanks for your answer, but it still doesn't work. Maybe just as you say, it is acquiring a IP address. It seems that ubuntu is different from other distributions, other distributions don't run the following scripts until the network is ready.

I edit /etc/network/interfaces , and make my script run after the network is ready, it works~

---

### Post by naugiedoggie on 2008-01-21
> **chenxing said:**
> Thanks for your answer, but it still doesn't work. Maybe just as you say, it is acquiring a IP address. It seems that ubuntu is different from other distributions, other distributions don't run the following scripts until the network is ready.

I edit /etc/network/interfaces , and make my script run after the network is ready, it works~

Hello,

It's easy enough to test.  Redirect the output of ifconfig into a text file from rc.local.

```

/sbin/ifconfig eth0 > /root/status.txt

```

For your purposes, you just modify this concept to execute your script after the 'inet addr' entry appears in the output.

Or, simply give the system a static IP address. Then the interface will get its IP at the time it's brought up.

I have to say that I don't think you can make that argument about "other distributions."  I used Slackware for nearly 10 years, and I've used Gentoo and Red Hat as well.  They don't "wait" for the network, if you're using DHCP -- they bring up the interface, start the DHCP daemon and keep going.  Once the interface is up, the boot process  doesn't care when or even if it gets an address.  As a practical matter, it would not make sense to not boot the system because the DHCP server was unavailable or otherwise not assigning an address to the network card.

Thanks.

mp

---

### Post by chenxing on 2008-01-21
> **naugiedoggie said:**
> Hello,

It's easy enough to test.  Redirect the output of ifconfig into a text file from rc.local.

```

/sbin/ifconfig eth0 > /root/status.txt

```

For your purposes, you just modify this concept to execute your script after the 'inet addr' entry appears in the output.

Or, simply give the system a static IP address. Then the interface will get its IP at the time it's brought up.

I have to say that I don't think you can make that argument about "other distributions."  I used Slackware for nearly 10 years, and I've used Gentoo and Red Hat as well.  They don't "wait" for the network, if you're using DHCP -- they bring up the interface, start the DHCP daemon and keep going.  Once the interface is up, the boot process  doesn't care when or even if it gets an address.  As a practical matter, it would not make sense to not boot the system because the DHCP server was unavailable or otherwise not assigning an address to the network card.

Thanks.

mp

That's a good idea. But my script really works on gentoo, debian, fedora and openSUSE.

---

### Post by mssever on 2008-01-22
For Ubuntu, check out Upstart, Ubuntu's new event-based boot system. You should be able to tie your script to a network up event. I've never mucked around with Upstart, but there's some documentation on either ubuntu.com or launchpad.net -- I forget which.

---

