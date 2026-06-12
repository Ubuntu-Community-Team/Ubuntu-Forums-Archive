---
title: "MySQL problem over LAN"
date: 2005-06-28
forum: Programming Talk
---

### Post by ubunTux on 2005-06-28
Hi! Hope this is the right place for this post...

Recently I installed Ubuntu Hoary and MySQL Server 4.1. That being said, we at the office is planning to have our local DB Server and that's why I set it up. We use several platforms on our network's client PCs: WinXP, Ubuntu Hoary, Fedora Core2.

After I installed MySQL 4.1, I made a database,table and a user account on our server for our team so they won't need to install MySQL on their PC and instead use a single DB which will be on the server.

I did a GRANT this way:
**GRANT SELECT,INSERT,UPDATE,DELETE ON *our_db.** TO *'our_user'*@'%' IDENTIFIED BY *'our_password'*;**

And when I tried to test the connection to our MySQL Server (via my PC running Ubuntu Hoary using MySQLCC) it said ***"lost connection to MySQL server during query".***

I tried it on another machine using FC2 and still can't connect to it.

Being unaware what seems to be the problem, I tried telnet to check if the port 3306 on our Ubuntu/MySQL server is free via:
**telnet 192.168.0.54 3306** and displayed this message...
*telnet: Unable to connect to remote host: Connection refused*

Still being clueless, I was wondering til know what seems to be the problem. Hope someone here could help. TIA!



.ubunTux

---

### Post by Ride Jib on 2005-06-28
Well, first off you don't need tick marks around the user name, just the hostname. e.g. user@'%' instead of 'user'@'%'. 

Second... I have never actually gotten the % feature of the hostname to work in MySQL, and I have tried for HOURS. Try adding an entry for the specific hostname you are attempting to connect from and see if that doesn't fix your problem.

But, now that I think about it more, you aren't even connecting to the machine to attempt to log in.... are you running any sort of firewall? Do you have the MySQL services running?

---

### Post by deuce868 on 2005-06-28
Check out this part of your my.cnf in /etc/mysql

> 
# Instead of skip-networking the default is now to listen only on
# localhost which is more compatible and is not less secure.
bind-address            = 127.0.0.1


---

### Post by LordHunter317 on 2005-06-28
[QUOTE=Ride Jib]Well, first off you don't need tick marks around the user name, just the hostname. e.g. user@'%' instead of 'user'@'%'. [/quote]That won't change a thing, though.

The issue is that by default, Ubuntu ships the mysql server with TCP/IP networking turned off.

You need to edit /etc/mysql/my.cnf and remove the "skip-networking" directive.  

Also, unless your LAN is secure, you'll want to enable SSL before sending the passwords across the wire.

---

### Post by deuce868 on 2005-06-28
[QUOTE=LordHunter317]That won't change a thing, though.

The issue is that by default, Ubuntu ships the mysql server with TCP/IP networking turned off.

You need to edit /etc/mysql/my.cnf and remove the "skip-networking" directive.  

Also, unless your LAN is secure, you'll want to enable SSL before sending the passwords across the wire.[/QUOTE]

Read my post above. The comments seem to suggest that "skip-networking" is no longer used and he should instead bind to his public IP address on the machine. 

And definitely don't enable it unless you're securing the connection between the machines.

---

### Post by LordHunter317 on 2005-06-28
I don't know when they changed that (or why), but FWIW removing the directive will just force a bind to all interfaces.

---

### Post by Ninnghizidha on 2005-06-28
I got exatcly the same problem!!! Hooray!  "lost connection to MySQL server during query" after a 1-minute waiting time.

I'm trying to get a connection from my Webserver to my local MySQL-Server for testing purposes.

What has been done:
"skip-networking" and "bind-address" (which was never in the file btw)  is commented out.  
My Webserver got the IPadress "80.243.163.34", so the user which wants to connect from there must have this IP with the needed privileges added. Nevermind: The mysql-users have privileges from localhost, my publicIP, the webservers public IP and the webservers hostname. 

I tired to bind the mysql-server to 127.0.01 and to my publicIP, but i still can't connect. I cant get it to work properly ..  ](*,) 



Lets have a look at this:
(MySQL bound to 84.112.32.164, skipnetworking disabled.)
```
ninnghizidha@TimeFactory:~$ netstat -an | grep 3306
tcp        0      0 84.112.32.164:3306      0.0.0.0:*               LISTEN

```


and this one:
(bind-address commented out and skipnetworking disabled.)
```
ninnghizidha@TimeFactory:~$ netstat -an | grep 3306
tcp        0      0 0.0.0.0:3306            0.0.0.0:*               LISTEN

```



Whats to right thing to do that my webserver-user can connect from its IP to my local mysql-Database? How do we get rid of the "timed out during query"-Error?

Any advice or help would be greatly appreciated! 
Ninnghizidha.  :?

---

### Post by deuce868 on 2005-06-29
I'm confused. Do you have two seperate machines with internet IP addresses that you're using? Are they on the same network or do they have any firewalls between them that would need to have port forwarding enabled on port 3306?

---

### Post by Ninnghizidha on 2005-06-29
Yes. Two seperate machines, both with static IP-Adresses, reachable over the internet. Different machines, different location, different networks.

The MySQL-Server running on my Ubuntu-Installation doesn't have a firewall (i guess) - at least i deinstalled Firestarter.

I'm pretty shure that the Webserver has a firewall. If not, the company who hosts my webserver would be pretty untrustable. I guess i'll talk to them reguarding the 3306-port.

Thanks a lot for this hint, i'll write them a mail now and post the conclusio as soon as possible.

Ninnghizidha.

---

### Post by Ninnghizidha on 2005-06-29
I guess I located the problem now. It is a firewall in between, which is (still) blocking the connections between my webserver and my database-server. I didn't know there was another firewall until my ISP told me about it.

I tried my scripts from another external ( and unprotected) webserver, and the connection worked like a charm.

Thanks a lot for your help, deuce.

Ninnghizidha, (quite happy now  :-P )

---

### Post by ubunTux on 2005-06-30
To all of you! Thanks a lot! I really appreciate all of your help!

I got my server working now... :D



.ubunTux

---

