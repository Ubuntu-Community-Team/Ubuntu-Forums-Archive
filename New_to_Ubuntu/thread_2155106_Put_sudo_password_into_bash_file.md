---
title: "Put sudo password into bash file"
date: 2013-06-17
forum: New to Ubuntu
---

### Post by kamrava on 2013-06-17
Hi there

I would like to run below command into `.sh` file :
```
#! /bin/sh -e
sleep 20
sudo /opt/lampp/lampp start
123456  #it's sudo password
exit 0



```
It's doesn't start `lampp`.
I think, i have put sudo password in wrong place.

Thank You

---

### Post by Cheesemill on 2013-06-17
Is this script going to be run every time the system boots?

Also do you have a good reason to be using lampp instead of the standard lamp stack that's in the Ubuntu repositories?

---

### Post by matt_symes on 2013-06-17
Hi

Please, please, please don't put your password in a script. 

It's such a huge security risk and, from looking at your script, i suspect there are other ways to achive what you want.

Kind regards

---

### Post by kamrava on 2013-06-17
> **Cheesemill said:**
> Is this script going to be run every time the system boots?
Yes.

> **Cheesemill said:**
> Also do you have a good reason to be using lampp instead of the standard lamp stack that's in the Ubuntu repositories?
Lampp is not in Ubuntu repositories by default.

> **matt_symes said:**
> [COLOR=#000000]It's such a huge security risk and, from looking at your script, i suspect there are other ways to achive what you want.[/COLOR]
What i must to do?

Regards

---

### Post by Cheesemill on 2013-06-17
If you want a command to be run every time the system boots then you can add it to the /etc/rc.local file. All commands in this file are run with root privileges.
> Lampp is not in Ubuntu repositories by default.
No it isn't, but the industry standard lamp stack is, you can install it by doing...
```
sudo apt-get install lamp-server^
```
Installing the proper version from the repositories instead of the version that you have installed will mean that all of the packages will get updated along with the rest of your system.
Also when you install the version in the repositories it automatically sets up the services to be started when the machine boots, so you don't need to fudge together a startup script like you are trying to do.

---

### Post by matt_symes on 2013-06-17
Hi

> What i must to do?

Follow Cheesemill's sage advice.

I run an apache server on my servers and on my notebook. 

One thing you should look into after installing it is how how harden it and we have the security sub forum with some good advice on how to do this.

Kind regards

---

### Post by ikt on 2013-06-17
Just a note that you don't usually put sudo in a script, you make the script run using sudo. Which is usually via cron (running as root if necessary).

---

