---
title: "ssh pre-login banner help"
date: 2008-09-30
forum: New to Ubuntu
---

### Post by Born-Thirsty on 2008-09-30
Hi there,

I know that it is possible to display a banner *before* the login prompt when ssh'ing to a server... using **/etc/ssh/sshd_config**

However, is it possible to somehow display the ip address or other information of the person trying to connect, *before* the login prompt as well ?

-------------------------
***Edit:***
Or to even be able to specify a certain banner for certain ip's that are trying to connect to the machine ?

-------------------------

Regards

---

### Post by Dr Small on 2008-09-30
Not that I know of, but there may be someone else here with a solution. By the way, why would you want to do this anyhow?

---

### Post by opscure on 2008-09-30
You can write a little script that checks for incoming connections to port 22 and then updates your /etc/issue.net file with the message you want to send to the incoming connection.  This will display all remote IPs connected to port 22:
```

#####Begin mysshscript.sh
#!/bin/sh
while [ 1 ]; do
Msg=`netstat -an --inet |grep :22 |cut -c 45-60`
echo "Welcome.  Follow ip's are connected: $Msg">/etc/issue.net
sleep 2
done

```
This will have to be ran at startup as a background process (sh mysshscript.sh) that will continually update your issue.net message.  This file (issue.net) will have to be writable by the user running the script and the file must be enabled in your sshd_config file.

Hope this helps.

---

### Post by Born-Thirsty on 2008-09-30
> **opscure said:**
> You can write a little script that checks for incoming connections to port 22 and then updates your /etc/issue.net file with the message you want to send to the incoming connection.  This will display all remote IPs connected to port 22:
```

#####Begin mysshscript.sh
#!/bin/sh
while [ 1 ]; do
Msg=`netstat -an --inet |grep :22 |cut -c 45-60`
echo "Welcome.  Follow ip's are connected: $Msg">/etc/issue.net
sleep 2
done

```
This will have to be ran at startup as a background process (sh mysshscript.sh) that will continually update your issue.net message.  This file (issue.net) will have to be writable by the user running the script and the file must be enabled in your sshd_config file.

Hope this helps.

--------------------------------------
**Dr Small**

I would just like to use it to scare of noob script kiddies that are trying anything and possibly use it to create my own log of who is accessing my machine while I am away... And just for the fun of being able to get it to work :)

--------------------------------------

**opscure**

Thanks. That is great as a start, but I would like it to be more specific and display the user's ip that is currently trying to connect and not all the current connections.

*`netstat -an --inet |grep ':22 ' |cut -c 45-65 |cut -d ":" -f1`*
(works better for getting the exact address without the port)

Regards

---

### Post by opscure on 2008-09-30
Alright, how about this:
```
#!/bin/sh
netstat -an --inet |grep ':22 ' |cut -c 45-65 |cut -d ":" -f1 >/home/user/initList
while [ 1 ]; do
        netstat -an --inet |grep ':22 ' |cut -c 45-65 |cut -d ":" -f1 >/home/user/newList
        diff -EbB /home/user/newList /home/user/initList >/home/user/changes
        change=`awk '{ save=$0 }END{ print save }' /home/user/changes |cut -c 2-20`
        if [ "$change" != "" ]; then
                echo "You are connecting through IP address: $change" >/etc/issue.net
                mv -f /home/user/newList /home/user/initList
        fi
        sleep 2
done
```
This will grab the latest IP address to connect to port 22 and assign it to the issue.net file.  It will update when the next connection is present for the next user....


You may want to remove the sleep to prevent this from capturing two changes at once.  Assuming two users connect within a two second range of one another.

---

### Post by Born-Thirsty on 2008-09-30
Thank you, I will try this and see how it goes.

God Bless.

---

### Post by opscure on 2008-10-01
No problem.

---

