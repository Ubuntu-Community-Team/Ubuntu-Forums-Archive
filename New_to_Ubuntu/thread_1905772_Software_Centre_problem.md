---
title: "Software Centre problem"
date: 2012-01-07
forum: New to Ubuntu
---

### Post by johnupatree on 2012-01-07
Software Centre fails to open. Opening in Terminal elicits following error message, suggestions please.
CAUTION NEWBIE!!
john@Baby-Linux:~$ software-center
2012-01-07 21:02:22,028 - softwarecenter.ui.gtk3.em - INFO - EM's: 17 15 21
2012-01-07 21:02:53,021 - softwarecenter.fixme - WARNING - logs to the root logger: '('/usr/lib/python2.7/dist-packages/dbus/proxies.py', 406, '_introspect_error_handler')'
2012-01-07 21:02:53,021 - dbus.proxies - ERROR - Introspect error on :1.106:/com/ubuntu/Softwarecenter: dbus.exceptions.DBusException: org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

Thanks

---

### Post by MG&amp;TL on 2012-01-07
> **johnupatree said:**
> Software Centre fails to open. Opening in Terminal elicits following error message, suggestions please.
CAUTION NEWBIE!!
john@Baby-Linux:~$ software-center
2012-01-07 21:02:22,028 - softwarecenter.ui.gtk3.em - INFO - EM's: 17 15 21
2012-01-07 21:02:53,021 - softwarecenter.fixme - WARNING - logs to the root logger: '('/usr/lib/python2.7/dist-packages/dbus/proxies.py', 406, '_introspect_error_handler')'
2012-01-07 21:02:53,021 - dbus.proxies - ERROR - Introspect error on :1.106:/com/ubuntu/Softwarecenter: dbus.exceptions.DBusException: org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

Thanks

ouch.

What version of Ubuntu are you running?

---

### Post by johnupatree on 2012-01-07
Ooops, forgot that vital bit of info. Version 11.10
The ouch does not fill me with a happy feeling!
:(

---

### Post by wildmanne39 on 2012-01-07
Hi, here is a bug report on it and a few things you can try are listed.
[https://answers.launchpad.net/ubuntu/+source/software-center/+question/177062](https://answers.launchpad.net/ubuntu/+source/software-center/+question/177062)

The person who filed the report ended up reinstalling ubuntu but I would try the other things at that link first.
Thanks

---

### Post by d3v1150m471c on 2012-01-07
have you tried using aptitude or apt-get? synaptic == GUI btw.

---

### Post by bluexrider on 2012-01-07
Might want to try

```
sudo apt-get clean; sudo apt-get update; sudo apt-get -y --reinstall install software-center
```

---

### Post by johnupatree on 2012-01-09
Thanks for the help, suggestions and information.  I have tried all the ideas suggested and had no success, so have reinstalled.  Not as bad as it sounds, as I am a relative newbie to Ubuntu and mainly use the machine as a test bed.  

Find the help and advice offered here is excellent

Appreciate your help, enjoy 2012!

John

---

### Post by wildmanne39 on 2012-01-09
Hi, your welcome!

---

### Post by johnupatree on 2012-01-10
Just as a follow on to the original post. I have reinstalled 11.04 from disc, absolutely fine, works without problem. However I decided to upgrade again to 11.10, all went well until after I rebooted. Same problem re occurs, Software Centre opens, greyed out and just hangs. 

As the whole point of me setting up this old laptop is to get used to using Ubuntu and discovering its potential, I will re install 11.04 tonight and stick to that for the time being.
Frustrating to say the least, as I don't want to spend all my time trying to get something to work, when there is a simple solution!

Once again thanks for the help

John

---

### Post by Bartender on 2012-01-10
> **johnupatree said:**
> Frustrating to say the least, as I don't want to spend all my time trying to get something to work...John

Look at it as an opportunity.  Tonight you could try installing manually, setting up separate partitions for linux-swap & /home.  Installing from scratch 3 or 4 times within a short period of time, as you're doing, is an excellent way to get comfortable with the process and help memorize the steps.

---

### Post by wildmanne39 on 2012-01-10
Hi, upgrading instead of doing a clean install may be the problem, there has been a lot of issues with upgrading to 11.10 because it has a lot of major changes compared to 11.04.
Thanks

---

### Post by Rex Bouwense on 2012-01-10
I have always been hesitant about upgrading because of the horror stories I read about.  One of these days I will try it, although fresh installs do not take very long.  We never read about the upgrades that work flawlessly.  No one writes about them.

---

### Post by johnupatree on 2012-01-18
Installed 11.04, created three partitions, all works flawlessly. Will stick where I am for now, at least if I upgrade I wont lose anything I have created.  Now I have the partitions I am happier to start using and saving work, its certainly been a worthwhile experience :)
Thanks to everyone for your input.

---

### Post by wildmanne39 on 2012-01-18
Hi, your welcome! I am glad you got it sorted.

---

