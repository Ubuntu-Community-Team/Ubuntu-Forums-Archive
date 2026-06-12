---
title: "what is meant by gethostname()"
date: 2008-09-17
forum: New to Ubuntu
---

### Post by redhue on 2008-09-17
While attempting to fix a problem with "Add and remove" as well as what i assumed was an related problem with retrieving the software updates. I had switched to the terminal and typed: "sudo apt-get install" and then "enter". And I get "sudo: unable to look up via gethostname()". I just installed Ubuntu 6.06 from the DVD and was attempting to start updates and whatnot and .....well here I am.any asistance would be appreciated.

---

### Post by halitech on 2008-09-17
what were you trying to install? normally you use apt-get install in conjunction with telling it a program to install.

```
sudo apt-get install amsn
```

---

### Post by aeiah on 2008-09-17
gethostname() is a functional call from within the problem. its probably struggling because as was mentioned, you didnt supply it with a package to try to install. it could be another problem though since gethostname() tends to suggest its stuggling to find the host name. 

as well as add/remove and apt-get, there's also synaptic, which is a gui front end that'll let you view the software in the repositories, update, install, search etc

---

### Post by redhue on 2008-09-17
> **halitech said:**
> what were you trying to install? normally you use apt-get install in conjunction with telling it a program to install.

```
sudo apt-get install amsn
```
I was acting on advice i had found in "The Ubuntu Book" having to do with the conflict I mentioned in my post. I only have these 2 fingers to type with so I try to not repeat myself if I can help it. So can you offer any help.

---

### Post by halitech on 2008-09-17
there is information here that may help

[http://ubuntuforums.org/showthread.php?t=390469](http://ubuntuforums.org/showthread.php?t=390469)

can you post the output of```
cat /etc/hosts
```

---

### Post by redhue on 2008-09-17
> **halitech said:**
> there is information here that may help

[http://ubuntuforums.org/showthread.php?t=390469](http://ubuntuforums.org/showthread.php?t=390469)

can you post the output of```
cat /etc/hosts
```

I did as you suggested and I got this : onthe line immediatly below "127.0.1.1 AlbertEmc2" (AlbertEmc2 is the name of my PC). And the it skips a line and there is the following"# The following lines are desirable for IPv6 capable hosts". next line"::1 ip6-localhost ip6 loopback" next line "fe00::0ip6-localnet". next line  all the same except after the -"masterprefix" next line same except "allnodes" next "allrouters" and last allthe same then "allhosts" I'm sorry also after the "fe00;; 0 its ff00;; 0 ,ff00;; 1 and so on I hope this sheds some light on and doesn't confuse I'll try that link you suggested now and let you know howq it goes thanx

---

### Post by redhue on 2008-09-17
> **halitech said:**
> there is information here that may help

[http://ubuntuforums.org/showthread.php?t=390469](http://ubuntuforums.org/showthread.php?t=390469)

can you post the output of```
cat /etc/hosts
```
yeah I got the same basic out put as in that post so should I just go ahead and try to reload Ubuntu again seeing as I am not that far into it and already having this problem as well as not being able to get "Add and remove" or "Updates" and now I can't seem to get it to reboot so I'm kind of stuck in the terminal "yikes" what now !?

---

### Post by halitech on 2008-09-17
ok, if I'm reading your information right, you have

127.0.0.1 AlbertEmc2

and then it goes to the IPv6 info.

here is a copy of mine
```
daryl@ubuntu:~$ cat /etc/hosts
127.0.0.1 localhost
127.0.1.1 ubuntu

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

127.0.0.1 doubleclick.net
127.0.0.1 ad.doubleclick.net
127.0.0.1 ad.ca.doubleclick.net
127.0.0.1 adremote.timeinc.net
127.0.0.1 adsremote.scripps.net
127.0.0.1 a.as-us.falkag.net
127.0.0.1 interclick.com
127.0.0.1 a1.interclick.com
127.0.0.1 media.fastclick.net
127.0.0.1 network.realmedia.com
```

I think the problem is you are missing the localhost. try this
```
nano /etc/hosts
```
then add localhost after the 127.0.0.1 and before AlbertEmc2
then to save the file, press CTRL O and CTRL X to exit. then
```
sudo reboot
```

---

