---
title: "i lost my network connection in ubuntu"
date: 2008-08-21
forum: New to Ubuntu
---

### Post by imgkg on 2008-08-21
i have lost my network connection in ubuntu anyone please help how to repair it i have to use xp to post this please help

---

### Post by Het Irv on 2008-08-21
Do you know what happened to cause your computer to lose internet?  

I don't know the exact command in bash, but resetting the computer should have the same affect.

---

### Post by Titan8990 on 2008-08-21
Did you change any settings? Is your router giving you an IP address? Did you enable the default policies for ucw? Can you ping your router?


No such thing as too much info when asking for help.


Edit: I believe the command that the user above me is looking for is this:

sudo ifconfig eth0 down

sudo ifconfig eth0 up

OR for wireless:

sudo ifconfig wlan0 down

sudo ifconfig wlan0 up

---

### Post by imgkg on 2008-08-21
can you please tell how to reset my network connection

---

### Post by imgkg on 2008-08-21
i used this command sudo apt-get install ubuntu-desktop it removed something like network manager i cant remember

---

### Post by Titan8990 on 2008-08-21
This would be the equivalent of a "repair" connection in Windows:

sudo ifconfig eth0 down

sudo ifconfig eth0 up

OR for wireless:

sudo ifconfig wlan0 down

sudo ifconfig wlan0 up

THEN:

sudo /etc/init.d/networking restart


Edit: The network manager is nothing more than a GUI thus not needed for connectivity.

---

### Post by imgkg on 2008-08-21
the output of that command is > desktop:~$ sudo ifconfig eth0 down
 
-desktop:~$ sudo ifconfig eth0 up
-desktop:~$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                          RTNETLINK answers: No such process
SIOCDELRT: No such process
                                                                         [ OK ]
-desktop:~$  * Stopping NTP server ntpd
   ...done.
 * Starting NTP server ntpd
   ...done.

---

### Post by imgkg on 2008-08-21
the output of that command is > desktop:~$ sudo ifconfig eth0 down
 
-desktop:~$ sudo ifconfig eth0 up
-desktop:~$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                          RTNETLINK answers: No such process
SIOCDELRT: No such process
                                                                         [ OK ]
-desktop:~$  * Stopping NTP server ntpd
   ...done.
 * Starting NTP server ntpd
   ...done.

---

### Post by Titan8990 on 2008-08-21
See if this is helpful: [http://bugs.archlinux.org/task/9960?string=network+restart&project=1&type%5B0%5D=&sev%5B0%5D=&pri%5B0%5D=&due%5B0%5D=&reported%5B0%5D=&cat%5B0%5D=&status%5B0%5D=open&percent%5B0%5D=&opened=&dev=&closed=&duedatefrom=&duedateto=&changedfrom=&changedto=&openedfrom=&openedto=&closedfrom=&closedto=](http://bugs.archlinux.org/task/9960?string=network+restart&project=1&type%5B0%5D=&sev%5B0%5D=&pri%5B0%5D=&due%5B0%5D=&reported%5B0%5D=&cat%5B0%5D=&status%5B0%5D=open&percent%5B0%5D=&opened=&dev=&closed=&duedatefrom=&duedateto=&changedfrom=&changedto=&openedfrom=&openedto=&closedfrom=&closedto=)

There are suggestions in the comments below the thread.

---

### Post by imgkg on 2008-08-21
if this isnt solved i have to completly remove ubuntu and reinstall it

---

### Post by Titan8990 on 2008-08-21
If that is easy for you then go for it. Linux is not Windows though. Linux does not run in to "unfixable" problems. You may have to wait a while and do lots of research/fiddling but it is not often a reinstallation is necessary. 

The few example I can think where it would be necessary are a direct result of user error (such as changing permissions on the entire filesystem).

---

### Post by imgkg on 2008-08-21
it not easy its last resort i guess

---

### Post by Het Irv on 2008-08-21
By any chance were you trying to install WICD?  All of the things I can find though Google seem to be related to WICD.

---

### Post by imgkg on 2008-08-21
no no i wasnt installing WICD all the things i did just before network went of is in my previous thread [http://ubuntuforums.org/showthread.php?t=896352](http://ubuntuforums.org/showthread.php?t=896352)

---

