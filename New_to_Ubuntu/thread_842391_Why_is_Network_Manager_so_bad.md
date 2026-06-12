---
title: "Why is Network Manager so bad?"
date: 2008-06-27
forum: New to Ubuntu
---

### Post by jlhs1971 on 2008-06-27
Hi

I cannot understand why Network Manager is so poor?  I have a windows box and a Mac box and the wireless networking on both of these machines is very good with little configuration necessary. With Network Manager, on the other hand, I often spend hours trying to log into my own network! It is the one thing that prevents me from wholehartedly recommending Ubuntu to all of my family and friends. Furthermore, it is the one application where, I am afraid to say, Ubuntu just fails miserably to live up to its commercial peers.

Here's the problem: Network Manager often fails to connect to my hone network. I need to delete the passkey and then change the SSID of the network and disable WPA security to log back into it. I can then change the SSID back to its original name together with the original WPA password and (usually) successfully log back in.

I have tried WICD and Knetwork Manager but they are no better.

Does anyone know a solution or a better network manager?

thanks

---

### Post by phidia on 2008-06-27
There are many topics [here]("https://help.ubuntu.com/community/NetworkDevices") to check out.
It seems like the problem might be the WPA security. Can you open your network (run without security) long enough to test whether the security is causing the problem?
If the wpa settings are causing the problems there are [threads]("http://ubuntuforums.org/search.php?searchid=43697151") in the networking & wireless section on that including [this one]("http://ubuntuforums.org/showthread.php?t=837566&highlight=wpa").

---

### Post by maestrobwh1 on 2008-06-27
Another package that replaces network manager is called WICD and you can add the repository to your apt list.

Check it out:
[http://wicd.sourceforge.net/](http://wicd.sourceforge.net/)

On one machine, network manager does fine with the wireless.  On my  other laptop, it is annoying and I have similar issues.  I have WICD installed there.  It us just "better" and anyone who uses it will attest to that.

You may also need to edit a network config file, but that info is on their website.

If you use KDE, there is a trick to getting the tray icon to load, but you don't mention that you do.

---

### Post by phidia on 2008-06-27
> **jlhs1971 said:**
> 

I have tried WICD and Knetwork Manager but they are no better.



o)(o

---

### Post by bumanie on 2008-06-27
Agreed that wireless is not brilliant. For what it's worth, Mark Shuttleworth is adamant that there will be big improvements in wireless for intrepid ibex - one can only hope that the October release lives up to these expectations. I know that doesn't help now.

---

### Post by imdano on 2008-06-27
This thread should be called "Why is my wireless driver so bad?".  If you're having problems with every wireless management app you've tried, odds are they're not at fault, its probably that your driver is no good.

---

