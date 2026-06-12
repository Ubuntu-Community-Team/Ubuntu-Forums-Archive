---
title: "Bandwidth Monitor"
date: 2008-09-16
forum: New to Ubuntu
---

### Post by AurolacKid on 2008-09-16
Hello.
I recently switched from Windows to Ubuntu and I'm trying to find a bandwidth monitor that will keep track of bandwidth usage on a monthly basis. The ones I've used reset after I restart my computer, I need one that will track bandwidth from when I log on to when I log off so I can see the total usage by the end of the month.

Any suggestions or help is greatly appreciate. Thanks.

---

### Post by zephyrcat on 2008-09-16
Well, it is a CLI (command line interface) application, but I would recommend vnstat.

Just type this into a terminal (Applications > Accessories > Terminal):

sudo apt-get install vnstat

This will install vnstat. Now, type in this command if you are using a wired internet connection:

vnstat -u -i eth0

Or this if you are using a wireless connection:

vnstat -u -i wlan0

Go do some web surfing for an hour or so, then open up a terminal again and type in this:

vnstat -m

This will tell you how much bandwidth you have used this month.

Hope that helps!

---

### Post by AurolacKid on 2008-09-16
Doesn't seem to be working:

danniy@Heartside-Home:~$ vnstat -u -i eth0
Error:
Unable to read database "/var/lib/vnstat/eth0".
Error:
Unable to write database "/var/lib/vnstat/eth0".
Make sure it's write enabled for this user.
Database not updated.

---

### Post by karlr42 on 2008-09-16
> **AurolacKid said:**
> Doesn't seem to be working:

danniy@Heartside-Home:~$ vnstat -u -i eth0
Error:
Unable to read database "/var/lib/vnstat/eth0".
Error:
Unable to write database "/var/lib/vnstat/eth0".
Make sure it's write enabled for this user.
Database not updated.
Just put sudo at the start of the command, like this:
```
sudo vnstat -u -i eth0
```
The password is whatever you log in with.
Sudo lets you br root for the duration of the command- root is allowed access important system files, you, the default user are not- makes things safer!

---

### Post by AurolacKid on 2008-09-16
danniy@Heartside-Home:~$ sudo vnstat -u -i eth0
[sudo] password for danniy: 
Error:
Unable to read database "/var/lib/vnstat/eth0".
-> A new database has been created.
danniy@Heartside-Home:~$

hmm?

---

### Post by shaggy999 on 2008-09-16
It looks like your installation went well, although the output is VERY confusing. I just installed it a few days ago and was perplexed by the message. First it says "can't read database" because one doesn't exist. Then it says "creating database", which means there is now a database that exists. So now just type vnstat -m to get monthly statistics. You should also check the man page ('man vnstat') for other options. This is a great little program!

---

### Post by AurolacKid on 2008-09-17
Got it. Thanks guys.

Anyone know of any others?

---

### Post by roscal on 2008-09-17
> **AurolacKid said:**
> Got it. Thanks guys.

Anyone know of any others?

Your Isp likely has a monitor (on a secure website),
for you to view your modem usage.
You could check that out.

---

