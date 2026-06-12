---
title: "Script to start server"
date: 2008-05-29
forum: Programming Talk
---

### Post by ramasdf123 on 2008-05-29
Hi,

I am would like to learn how to create a script in ubuntu that would let me start ZOPE and Plone when the computer starts.  Is this possible with bash or python scripts?

where would be a good place to start?

---

### Post by Go_Bucks on 2008-06-21
+1. I am searching for the same thing.

---

### Post by geirha on 2008-06-21
```
gksudo gedit /etc/rc.local
```
If you put the commands necessary to start your apps there, they should start up each boot.

---

### Post by Go_Bucks on 2008-06-21
> **geirha said:**
> ```
gksudo gedit /etc/rc.local
```
If you put the commands necessary to start your apps there, they should start up each boot.

Woops... I thanked you, and then it occurred to me as I started to do that it would not work. Zope/Plone is initiated with sudo, so putting the command in rc.local won't work. It will require a start-up script, but I am not certain how to do that. I looked at the start-up script for hamachi (which also requires sudo), but could not make sense of how it might be altered for this case.

---

### Post by geirha on 2008-06-22
/etc/rc.local is run as the root user just before the login-screen opens, so sudo would just be redundant. I do not know how these programs work though. Do you need to run it when you log in, rather than when you computer starts/boots?

---

### Post by Go_Bucks on 2008-06-22
> **geirha said:**
> /etc/rc.local is run as the root user just before the login-screen opens, so sudo would just be redundant. I do not know how these programs work though. Do you need to run it when you log in, rather than when you computer starts/boots?

Thanks... I wasn't aware of that. I tried it and it worked. 

A similar but unrelated issue is that I am running GeoNetwork, which is service that creates a website that stores metadata for geographic data. I have deployed this on four computers so far. The service does not require sudo to start, and I have always placed an entry for it in "sessions" to start at login. Well, on this computer it just stopped working. Based on the rc.local advice for Plone you just gave I placed the command for GeoNetwork in there to and it is not working. The script to start it is /home/user/geonetwork/bin/start-geonetwork.sh. If I execute it manually after the computer is up and running it works fine. Any ideas?

---

### Post by geirha on 2008-06-22
I don't have any experience with geonetwork, but I would try something like this in /etc/rc.local:
```

sudo -u *user* /home/*user*/geonetwork/bin/start-geonetwork.sh &> /var/log/geonetwork.log

```

The root user can run any program with sudo, without being prompted for a password. In this case, sudo is used to run the program as the user *user*. If a program can run as a regular user, then run it as a regular user.

The "&> /var/log/geonetwork.log" will redirect any output from the command to a file. So if it doesn't start, check that file for clues.

---

