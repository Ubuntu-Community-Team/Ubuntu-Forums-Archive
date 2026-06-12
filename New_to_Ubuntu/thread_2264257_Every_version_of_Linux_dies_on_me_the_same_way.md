---
title: "Every version of Linux dies on me the same way"
date: 2015-02-06
forum: New to Ubuntu
---

### Post by Ben_Muircroft on 2015-02-06
I have a very odd experience for the last two days, I am new  to using Linux. First I tried Linux Mint Cinnamon then I tried Linux  Mint with the Mate desktop now Ubuntu 14. I switched each time because I  have had the same problem with each one after a couple of hours of use  (maybe not exactly but same - identical results).
  I am now typing in the try Unbutu from CD mode. When I boot normally I  am no longer greeted by my user login screen, it just goes straight to  the desktop where I see my desktop icons but, no user interface. The top  panel showing time date volume and power is gone. The launcher is also  gone.
  The other day also that happened with Mint (Mate) except I had not  yet added any desktop icons so I could not even get to a file browser  and find a terminal.
  As I mentioned before the situations were not exactly the same; in  the case of my first use of Linux Mint Cinnamon edition.. I accidentally  removed Nemo thinking that I had replaced it with another desktop  environment. So when I restarted I had no desktop UI.
  It is also interesting to note that in all three cases I installed  successfully from USB but when each one lost its UI, then, they would no  longer boot from USB in 'try Linux/Ubuntu' mode, they instead get stuck  on there loading icons indefinitely.[INDENT]   As explained above I am infact typing through 'Try Ubuntu', but  this time I am on a friends CD from 3 years ago (version 12.04) not USB.
 [/INDENT]
Another point of interest is that the second and third times the last  thing I was doing before this terrible glitch was installing Virtualbox  4.3.20. The very last time I was half way through installing it with  the Application Manager when the Internet dropped due to bad snow. The  next thing I noticed was that no search would even find the Application  Manager, so I restarted. And now I am here again.
  If I try to reinstall Ubuntu over the top of an existing  installation, I don't have the option to reinstall (thus leaving my  documents intact), but only the option to install a new copy of Ubuntu  alongside the old one.
  What could I do now? I would appreciate some expert advice very much, thank you.

---

### Post by tgalati4 on 2015-02-06
Welcome to the forums.  You might have a power supply problem.  How old is the machine?  What is the make and model?  How much RAM?  Installing linux can be a frustrating experience if the hardware is defective.

---

### Post by grahammechanical on 2015-02-06
Please make a decision as to which Linux distribution you want to use. I have no experience with Linux Mint and so I cannot give advice regarding Linux Mint. I do have much more experience with Ubuntu. And that is where I give my attention. We have a section of this forum specifically for Linux Mint users

[http://ubuntuforums.org/forumdisplay.php?f=453](http://ubuntuforums.org/forumdisplay.php?f=453)

My advice would be to use the Live session to copy your files and documents to a safe place. Then either fresh install or re-install. With Ubuntu we can re-install without formatting the partition and that should protect our files in the /home partition. We use the Something Else option. It may also fail to clear out any system configuration files that are causing conflicts.

My next advice would be to make a record of all the modifications that you do to the user interface so that you know what to revert if the modifications break something. Do one modification at a time and test by restarting.

If a live session fails to load it may mean that you need to use some of the F6 options. In this link go down to Changing the CD,s boot options and look at section 6 - F6.

[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

From your post it is clear to me that you do not have a recurring problem. Different things have happened for different reasons. We can use the terminal to update the system. These two commands are useful. For fault finding any error messages are very useful to us.

```
sudo apt-get update
sudo apt-get upgrade
```

Regards.

---

### Post by Habitual on 2015-02-06
Open a terminal and issue
```
inxi -S
``` and show us the output please.

---

### Post by mooreted on 2015-02-06
When installing Ubuntu, make sure you have a stable Internet connection. Ubuntu pulls packages from a repository server over the Internet. If you loose your connection during installation it will cause problems. I recommend a wired rather than wireless connection.

---

### Post by lotharmat on 2015-02-07
Or you can disconnect completely and just install from the image with no updates!

Then install updates when it is stable!

---

### Post by mooreted on 2015-02-07
That's true, a little more work after bootup, but at least you have a bootup.

---

### Post by kingdominsight on 2015-02-08
> **lotharmat said:**
> Or you can disconnect completely and just install from the image with no updates!

Then install updates when it is stable!

^ this ^   Although being new to linux , i have toyed with a few different distros, and reinstalled all of them probably at least twice, and i am finding what Lothar said there to often be true. In my limited experience, not connecting to the Internet and just installing the basic OS (if current) seems to yield the most stable results.  Then adding applications and libraries one at a time.  Oh and i have learned that a system restore program like Timeshift to be very useful. being able to restore to a point prior to a certain app or driver install is really nice.

---

### Post by HermanAB on 2015-02-09
Bear in mind that uninstalling things is somewhat like trying to unscramble an egg.  Life will be better if you don't uninstall random stuff.

---

### Post by mastablasta on 2015-02-09
> **Ben_Muircroft said:**
> 
  I am now typing in the try Unbutu from CD mode. When I boot normally I  am no longer greeted by my user login screen, it just goes straight to  the desktop where I see my desktop icons but, no user interface. The top  panel showing time date volume and power is gone. The launcher is also  gone.
  The other day also that happened with Mint (Mate) except I had not  yet added any desktop icons so I could not even get to a file browser  and find a terminal.
  As I mentioned before the situations were not exactly the same; in  the case of my first use of Linux Mint Cinnamon edition.. I accidentally  removed Nemo thinking that I had replaced it with another desktop  environment. So when I restarted I had no desktop UI.

it is more interesting to note you did osme operation requiring admin password without you knowing what the consequences might be. that passwrod not only protects your system from outside interfernce but also from the user. so when it pops up asking for your permission, you better be sure what you are doing as it means that main system files are to be changed or removed.

> 
 Another point of interest is that the second and third times the last  thing I was doing before this terrible glitch was installing Virtualbox  4.3.20. The very last time I was half way through installing it with  the Application Manager when the Internet dropped due to bad snow. The  next thing I noticed was that no search would even find the Application  Manager, so I restarted. And now I am here again.
  .
it could be it did an update/upgrade first and connection fell during that time. this can occasionally make you loss the desktop. we had same thing happen to thousands of PC running windows 8. boy that must have been fun recovering all those PC. although this is more likely to happen if power goes out (which is why faults PSU was suggested.

Anyway it is recoverable. might need a few tried in command line to start recovery procedure.

[https://wiki.ubuntu.com/RecoveryMode](https://wiki.ubuntu.com/RecoveryMode)
[https://help.ubuntu.com/community/LiveCdRecovery](https://help.ubuntu.com/community/LiveCdRecovery)

you might be able to finish update/upgrade or you might need to force the upgrade or to fix it.

you might get this working to fix it without the liveDVD/USB

---

