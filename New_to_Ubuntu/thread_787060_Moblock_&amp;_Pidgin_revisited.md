---
title: "Moblock &amp; Pidgin revisited"
date: 2008-05-08
forum: New to Ubuntu
---

### Post by siretfel on 2008-05-08
Hi all,

Strange things happens with moblock in my laptop.
I have configured moblock in order to make pidgin work when running moblock but whatever i try i cant connect to my msn account.

First I whitelisted the ip range i could see in moblock to be blocked:
WHITE_IP_IN="xxx.xxx.xx.0/24"
WHITE_IP_OUT="xxx.xxx.xx.0/24"

No change.

Then i added port 1863 to 
WHITE_TCP_OUT="80 443 1863"

Still nothing.

Then i tried only with port and then again both port and ip range, and then only ip range.All combinations failed. I even stoped using Microsoft blacklist from the blocklists.

Any ideas on what's going on? Everything else seems to work fine with moblock so far.

thanks

---

### Post by MrWES on 2008-05-08
I had the same problems with MoBlock, so I uninstalled it and put in IPblock, and I've had no issues since.

Bill

---

### Post by gnivler on 2008-05-08
You might want to install mobloquer, a/the GUI for moblock, that will illustrate clearly if you are still getting blocked connections.  I had many with MSN and unblocked them tediously by hand, there is probably a better way.

---

### Post by siretfel on 2008-05-08
> **gnivler said:**
> You might want to install mobloquer, a/the GUI for moblock, that will illustrate clearly if you are still getting blocked connections.  I had many with MSN and unblocked them tediously by hand, there is probably a better way.

that's exactly what i tried to do.I did use the GUI and tried to unblock what was block but that's just not the way.it is frustrating.Anyway i'll give ipblock a try now and see what happens.

Thanks for your answers guys

---

### Post by BorisDBlade on 2008-05-08
where do you get IPblock? can't find in repos or in add/remove. I'm also on mobloquer but have to stop it to get msn on pidgin to work.

---

### Post by siretfel on 2008-05-08
> **BorisDBlade said:**
> where do you get IPblock? can't find in repos or in add/remove. I'm also on mobloquer but have to stop it to get msn on pidgin to work.

You dont find it in repos. Follow instructions here:
[http://ubuntuforums.org/showthread.php?t=530183](http://ubuntuforums.org/showthread.php?t=530183)

Basically you donwload it from sourceforge and install it (just doubleclick on it).Then after it is installed you find it under Applications/Internet menu.

That's it.Any questions please ask.

---

### Post by BorisDBlade on 2008-05-08
thank you.

---

### Post by jre on 2008-05-09
Did you restart MoBlock after the configuration changes? The whitelisting works with iptables rules so you can verify if it worked with e.g. "moblock-control status".
I can't verify if 1863 is the correct port - otherwise your settings seem to be correct.

---

### Post by jimtb on 2008-05-10
The easiest and safest way to use MSN while running moblock is to enable the **http method** in pidgin's options. 

Just open pidgin, go to Accounts->Manage, select your MSN account, click Modify and check the "Use http method" in the "Advanced" tab. If you already have port 80(http) whitelisted everything should work just fine.

**Edit:** You may also have to whitelist the http method server which for me is **gateway.messenger.hotmail.com**. This can be easily done using mobloquer. Just click "Whitelist IPs" in the settings tab, paste your http method server, click resolve and then add it to the whitelist. 

Hope I helped.

:-)

---

### Post by BorisDBlade on 2008-05-10
thanks for the info about msn on pidgin, I was stopping moblock when I used it. that makes it easier to keep pidgin up without opening up to needless ip's.

---

### Post by gnivler on 2008-05-10
> **jimtb said:**
> The easiest and safest way to use MSN while running moblock is to enable the **http method** in pidgin's options. 

Just open pidgin, go to Accounts->Manage, select your MSN account, click Modify and check the "Use http method" in the "Advanced" tab. If you already have port 80(http) whitelisted everything should work just fine.

**Edit:** You may also have to whitelist the http method server which for me is **gateway.messenger.hotmail.com**. This can be easily done using mobloquer. Just click "Whitelist IPs" in the settings tab, paste your http method server, click resolve and then add it to the whitelist. 

Hope I helped.

:-)

Very good to know.. also figured out my mobloquer wasn't the newest because I didn't even have the buttons you mentioned :)  Double-win.  Thank you.

---

