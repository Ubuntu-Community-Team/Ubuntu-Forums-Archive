---
title: "11,10 upgrade issues"
date: 2011-10-15
forum: New to Ubuntu
---

### Post by Trisket on 2011-10-15
I have two toshiba laptops one x86 and one amd64, both were running ubuntu 11.04. I first upgraded the 64 bit computer via the upgrade manager, i have a solid internet connection and no apparent reason for failure. All seemed to go well except when I tried to upgrade the ati driver it said the upgrade had failed and a partial upgrade was needed, so i did the partial and after restart it just said ubuntu and changed colors, never booted. Next i tried the update from a disk and the same thing happened, so i just went ahead and did a fresh install. The same thing happened with the other laptop, showing the ubuntu boot screen changing colors but never booting.  Has anyone else had this problem?

---

### Post by 23dornot23d on 2011-10-15
There are quite a few upgrade problems at the moment and the best thing to do is to
wait untill some of the issues are fixed before upgrading.

Partial upgrades are nearly always a problem .....

But why did you upgrade your second machine when the first failed .....

The thing now is to get them back up and running ...... but if a fresh install is not working
then go back to 11.04 and install that Fresh until such a time that the 11.10 works on your machines ...... you should always test from a liveCD/USB first ...... it gives you a good indication of whether the upgrade isgoing to be successful .......

See the link below as I am keeping track this time of the failed upgrades ...... I am just another user like you - but saw this happen last year and want to try to make it so the
same problems do not repeat next year .......

---

### Post by Trisket on 2011-10-15
> **23dornot23d said:**
> There are quite a few upgrade problems at the moment and the best thing to do is to
wait untill some of the issues are fixed before upgrading.

Partial upgrades are nearly always a problem .....

But why did you upgrade your second machine when the first failed .....

The thing now is to get them back up and running ...... but if a fresh install is not working
then go back to 11.04 and install that Fresh until such a time that the 11.10 works on your machines ...... you should always test from a liveCD/USB first ...... it gives you a good indication of whether the upgrade isgoing to be successful .......

See the link below as I am keeping track this time of the failed upgrades ...... I am just another user like you - but saw this happen last year and want to try to make it so the
same problems do not repeat next year .......

Clean installs worked on both machines, I continued with the second machine because i typically have more problems with the 64 bit version as apposed to x86, and had all files backed up.. I am very satisfied with 11.10 but wondered if anyone had similar issues...

---

### Post by wildmanne39 on 2011-10-15
Hi, in many cases upgrades fail especially since 11.04 came out, before 11.04 I did many upgrades with no problems but after they all end in failure, so I will only do a clean install from now on.
Thank you

---

### Post by alphacrucis2 on 2011-10-15
> **wildmanne39 said:**
> Hi, in many cases upgrades fail especially since 11.04 came out, before 11.04 I did many upgrades with no problems but after they all end in failure, so I will only do a clean install from now on.
Thank you

Upgrades have been kind to me. Currently running 11.10 which was reached by 10.04 -> 10.10 -> 11.04 -> 11.10. The process wasn't completely trouble free but the issues were easily fixed.

---

### Post by wildmanne39 on 2011-10-15
Hi alphacrucis2, you have been very lucky, I am glad it worked for you.

---

### Post by sandyd on 2011-10-16
Upgrades generally never work extremely well until they release the *.1 isos.

---

### Post by Prakhar Mishra on 2011-10-16
Hi Trisket, I am also having the same problem.
After upgrading to Ubuntu 11.10, Linux-3.0, I am stuck on the the screen saying &quot;Ubuntu&quot; and it takes me nowhere.
I am using nvidia driver for my graphics card.  
When I do start it in recovery mode, then I have to run fsck first. Then &quot;normal boot&quot; takes me to the tty1 with login prompt. No GUI gets started.  

If you have any solution, then please let me know

---

### Post by wildmanne39 on 2011-10-16
Hi Prakhar, it sounds like a nomodeset parameter might work for you to be able to boot ubuntu then uninstall the nvidia driver and try another one.
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
Thank you

---

### Post by proxygeek on 2011-10-16
[QUOTE=Prakhar Mishra;11350665]Hi Trisket, I am also having the same problem.
After upgrading to Ubuntu 11.10, Linux-3.0, I am stuck on the the screen saying &quot;Ubuntu&quot; and it takes me nowhere.
I am using nvidia driver for my graphics card.  
When I do start it in recovery mode, then I have to run fsck first. Then &quot;normal boot&quot; takes me to the tty1 with login prompt. No GUI gets started.  /QUOTE]

I have the exact same problem. Was running 11.04.
Tried upgrading to 11.10 via update-manager. 

Problems: 
1) Failed Upgrade message
2) Rebooting gets me to tty login; startx and GUI does not work because nvidia modules not loaded
3) Can't connect to wi-fi; 

This is the first time since Ubuntu 8.04 that I have faced so many issues. 

Any Suggestions on 
1) How to fix the GUI issue?  OR/AND
2) How to get back my network connection? OR/AND
3) How to roll back to 11.04 at least?

Thanks in advance,

---

### Post by mglennpooh on 2011-10-16
I wanted to install 11.10 Wubi but downloaded 11.04 Wubi the day before as contingeny. 11.10 failed three times due to tar.xz based OS files which are incompatible for Windows. 11.04 initially succeeded but then failed due to 5 hour download of 11.10 Upgrade causing missing or corrupt files due to the overwhelming demand on the Server following the new release. I finally succeeded - 23 mins total - by downloading the iso image to the same download folder as the 11.10 Wubi which then utilized the iso instead of downloading the tar.xz files( which are the 64bit version appropriate for Non-Windows Primary OS).

One of the moderators with the username " bcbc " gave me similar advice two days ago. Pass it along. 
 
I would add I would've been wise to wait a week or two or three after the release date to try 11.10 Install or Upgrade as the many inevitable problems we're all experiencing right now will have been resolved by then.
But then again I had waited already since May when I first read about Linux & Ubuntu and wasn't
about let any problems like this get in my way.

:popcorn:

---

### Post by Prakhar Mishra on 2011-10-17
Hi wildmanne39,
I have tried nomodeset option at startup but still I am stuck over screen saying Ubuntu.
One more thing I would like to tell you that I can enter recovery mode and then I can select normal boot which takes me to the tty1 with login prompt.
When I login, I can issue startx command and my NVidia driver is also working. But my networking is not ON and nm-applet is not shown. Further, when I start nm-applet, it says D-Bus is not responding.

Please, anybody help me out....

---

### Post by wildmanne39 on 2011-10-17
Hi, it sounds like a failed upgrade, it is best to do a clean install but back up your data first.
Thank you

---

### Post by Prakhar Mishra on 2011-10-18
Looks like a clean install is the only option left................

Thank you to all of you

---

### Post by wildmanne39 on 2011-10-18
Hi, your welcome!

---

### Post by Prakhar Mishra on 2011-10-20
Hi wildmanne39,
I was just wandering that what are the permissions required by linux kernel to show login screen(GUI).
(Please forgive me if I am asking stupidly).
Or more precisely, the kernal have to start X-server first to enable login prompt in GUI.
From whom account, the kernel (or ubuntu) initiates the X-server?
Is there anything I can do to grant/revoke that permission from ubuntu?

Because my login prompt is not loading..... I was thinking if I could  grant ubuntu(or to the user which ubuntu uses) the permission to invoke  the X-server.
(Please forgive me if I asked something wrong) 

Thank you.

---

### Post by wildmanne39 on 2011-10-20
Hi, I still believe with all the issues you are having it would be best and quicker to do a clean install, you could spend days trying to fix your issues when you could reinstall and update in about an hour.

These are the other issues:
> nm-applet is not shown. Further, when I start nm-applet, it says D-Bus is not responding.
and this is just the issues you know about.
Thank you

---

