---
title: "hostname mailname"
date: 2013-04-08
forum: New to Ubuntu
---

### Post by kgamble on 2013-04-08
I am struggling setting up our mailserver and I have a question I don’t seem to be able to answer from the internet.
The original server name was something like server88.456.xxx.xx.famail.co.uk
 
We are trying to change it to jack.ourname.com – there is an A record for jack.ourname.com and also for ourname.com, and Fasthosts have done whatever their thing is to make jack.ourname.com a reverse lookup.  There is an mx record for mail.ourname.com
 
 
In main.cf (and in etc/hostname and etc/hosts) the hostname = jack.ourname.com.  I have read that this should be just jack in some places and jack.ourname.com in others.  what should it be?
 
 
Sudo hostname  gives  jack.ourname.com   and sudo hostname –f gives exactly the same i.e. jack.ourname.com
Postconf –n gives myhostname = jack.ourname.com
It also gives mydomain = ourname.com


 
Now here comes the DUMB question….. what should be in /etc/mailname? Should it be mail.ourname.com or jack.ourname.com or just ourname.com
 
 
I have a lot of other things to sort out, so it is not as simple as trying each of the above in turn.
 
I can send mail to external addresses quite happily, but not to [EMAIL="windy@climatz.com"]m[/EMAIL]ailaddress1@ourname.com OR to ourothername.com which is a virtual domain and mail account on this server. 
Before we tried to change the servername – we could send to ourname.com and ourothername.com but NOT outside.
 
I have done postmaps for every file that has ever changed, restarted postfix, and rebooted the whole server.
 
Is the mailname the problem, or is it hostname that should only be jack or is there something else all together?
 
I have read and printed out a lot of postfix.org stuff and it is useful, but doesn’t nail these.
Thanks

---

### Post by smtp on 2013-04-11
The **mailname** in the "/etc/mailname" file is usually a fully qualified domain name (FQDN) that resolves to one of the host's IP addresses.

---

