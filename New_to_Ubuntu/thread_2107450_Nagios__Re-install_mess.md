---
title: "Nagios:  Re-install mess?"
date: 2013-01-21
forum: New to Ubuntu
---

### Post by Roskow on 2013-01-21
Okay I ran the typical sudo apt-get install -y nagios3 to try this program.

It's installing as normal then the prompt comes up to give it a password. So I go to type and bumped the enter key.  :shock: So either it accepted an empty field as the password or maybe I bumped the " key next to it. Well I tried to sign in with "nagiosadmin" and nothing for the password and it gave me an error. 

So I figured I should try to strip off everything Nagios and start over.  As a noob I followed different commands from Google like Apt-Get Remove, AutoRemove, or Purge.  I also manually searched and removed Nagios or Nagios-Plugins directories.  

Anyway I'm getting "Errors in Config" message or dependency problems when I try to install Nagios3 again. 

I may say the hell with it and start over.  This is my student project computer I'm learning on by installing Ubuntu than breaking it and then reinstalling the whole server.



[EDIT]:  I'm going to start over.  I just tried to install Bind9 for another project and got errors. But any feedback that keeps me from messing things up like this in the future would really help me out.  Noob-Thnx.

---

### Post by cariboo on 2013-01-24
The first thing to do is to check and see if nagios3 is still running, to do so use the following command:

```
ps ax | grep nagios3
```

If it is still running , you should see something like this:

```
ps ax | grep nagios3
 1429 ?        SNs    0:41 /usr/sbin/nagios3 -d /etc/nagios3/nagios.cfg
 5010 pts/1    S+     0:00 grep --color=auto nagios3
```

if you get something similar to the first line, you need to stop nagios3, to do so use this command:

```
sudo kill 1429
```

of course substitute the number (PID) at the start of the line for the one on your system. Once you have killed the process, you should be able to completely remove nagios3, using:

```
apt-get purge nagios3
```

**Note:** You may run into more problems, if you didn't use apt-get to remove the plugin packages you installed.

---

