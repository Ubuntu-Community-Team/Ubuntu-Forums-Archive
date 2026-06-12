---
title: "Starting Firestarter on Boot"
date: 2008-06-15
forum: New to Ubuntu
---

### Post by idolguy on 2008-06-15
I've been able to figure out I need to put Firestarter under Sessions Preferences in Startup Programs.  I know that I'll click ADD.  However, it asks for the command to start Firestarter.  Would I use sudo firestarter or some other command?  I'm kind of stuck because I know that the sudo command asks for my password to "authenicate" the command.  

Any assistance would be greatly appreciated.

Thanks!

---

### Post by kansasnoob on 2008-06-15
What you need to understand first and foremost is that Ubuntu has a firewall running from the moment you install it.

That firewall is called iptables.

Beginning with Hardy ufw is installed which is a cli auditor for iptables.

But, most importantly, if you can do everything you want to do on the internet you're better off leaving everything alone! You are protected!

I heavily disputed this and I was wrong!

My one disappointment is that we can't log attempts to hack us without installing a front-end to iptables ................ but unless you're a super techie, I'd suggest leaving iptables alone!

---

### Post by frank002 on 2008-06-15
The only reason to use Firestarter is to change settings in the firewall(Ubuntu already comes with a firewall called iptables preinstalled). Are you trying to change iptables settings?

---

### Post by kansasnoob on 2008-06-15
I guess I should have added that it is possible to edit sudoers to make Firestarter run at start up, but I seriously discourage it. It's kind of like leaving the key to the front door under the doormat.

---

### Post by st33med on 2008-06-15
Firestarter, IMO, is not very good. You might want to use ufw instead.

[Tutorial for UFW]("http://www.ubuntugeek.com/ufw-uncomplicated-firewall-for-ubuntu-hardy.html")

---

### Post by idolguy on 2008-06-15
> **kansasnoob said:**
> What you need to understand first and foremost is that Ubuntu has a firewall running from the moment you install it.

That firewall is called iptables.

Beginning with Hardy ufw is installed which is a cli auditor for iptables.

But, most importantly, if you can do everything you want to do on the internet you're better off leaving everything alone! You are protected!

I heavily disputed this and I was wrong!

My one disappointment is that we can't log attempts to hack us without installing a front-end to iptables ................ but unless you're a super techie, I'd suggest leaving iptables alone!
 Okay, I have no need for firestarter then.  I was unaware that Hardy has a firewall.  I will leave it alone then.

Thanks!

---

### Post by idolguy on 2008-06-15
> **frank002 said:**
> The only reason to use Firestarter is to change settings in the firewall(Ubuntu already comes with a firewall called iptables preinstalled). Are you trying to change iptables settings?

No, I was unaware it came preinstalled with a firewall.  I'll content myself with learning about the iptables firewall in Ubuntu Hardy.


Thanks,

---

