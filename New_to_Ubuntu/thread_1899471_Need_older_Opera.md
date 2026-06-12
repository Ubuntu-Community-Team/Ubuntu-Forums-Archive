---
title: "Need older Opera"
date: 2011-12-23
forum: New to Ubuntu
---

### Post by degarb on 2011-12-23
Made the mistake of trying to ugrade Opera 11.1 to 11.6 with Ubuntu 9.11.   Now, Opera is just hitting a restart screen and shuttig down.  Rebooted and same thing.  I only got 200k free on drive so ugrading OS is outofquestion.

Where can I get older working distro of Opera - the only smooth running browser on the old system?   11.1 or greater.

---

### Post by gandaran on 2011-12-23
> I only got 200k free on drive so ugrading OS is outofquestion
have you cleaned the system cache?
```
sudo apt-get clean
```

---

### Post by gandaran on 2011-12-23
all opera versions here
[http://ftp.opera.com/pub/opera/linux/](http://ftp.opera.com/pub/opera/linux/)

---

### Post by Karlchen on 2011-12-23
Hello, degarb.

I wonder which Ubuntu version you may be actually using. There was v9.04 and v9.10. There has never been v9.11. (minor inaccuracy, I guess)

Major problem: with just 200 KB free disk space left, the topmost priority task is not getting any Opera version to run, but to increase the amount of free disk space. Cf. gandaran's advice. Because with just 200 KB of free disk space you will not be able to make any software run reliably, new or old, not even your OS.

Kind regards,
Karl

---

### Post by degarb on 2011-12-23
Of course I do everything to keep space down.

I just lost my best browser, there is no roll back in Ubuntu, like windows, I cannot locate old deb via google to go down a notch.  Never had luck on new Opera boards.

I need the older deb, or solution as to why new deb is not compatible with older ubuntu.

Yes, of course, 9.11.  Works fine, no space to upgrade, and it takes me like 2 days to get wireless working, since never had luck with all the voodoo commands to get it running with broadcom.  I have no stomach to reinstall the os. Took too long to get to working condition.  And installing latest pinguy on a old laptop I found over a working xp with working wireless, gave me a dead wireless.  So, I threw it away.  No stomach for it.  I just want my Opera 11.xx back.

---

### Post by degarb on 2011-12-24
This thread isn't about cleaning cache or forcing a user to upgrade. Forced upgrades are only reason I don't use MS windows, etc. etc. They are relentlessly forcing costly upgrades, new hardware/sw programs, forcing machine downtime and maintenance time.  The thread is about a successful install of Opera on Ubuntu 9.11 on a machine that does everything I need.

Any idea down to what version will work on Ubuntu 9.11?  And, what is it about new version that is messing up with old version of OS; and possible workaround?

---

### Post by Zill on 2011-12-24
> **degarb said:**
> ...Yes, of course, 9.11...
Err... there really isn't a 9.11 release of Ubuntu. ;-)

[https://wiki.ubuntu.com/Releases]("https://wiki.ubuntu.com/Releases")

If you are using 9.10 (karmic) then this reached end-of-life on April 30, 2011 and so is no longer supported.

---

### Post by Frogs Hair on 2011-12-24
The link in post 3 has the old versions. If there are dependencies that need to be downloaded it may be a problem because the 9.10 repository is no longer available .

---

### Post by Karlchen on 2011-12-24
Hello, degarb.

Before it will be possible to give any helpful piece of advice we really need a few more reliable details about your system.

[LIST=1]
[*]Please, open a terminal session, run the command **cat /etc/lsb-release** and post the output here. - This will tell us which Ubuntu version you are using.
[*]Please, run the command **df -k** and post the output here. - This will tell us the sizes of your filesystems and how much disk space is available on each of them.
[*]Please, run the command **sudo apt-get check** and post the output here.
Note:
**sudo** will ask you to enter _your_ password. Please, do so when asked. The screen output will _not_ reveal your password.
The output of **sudo apt-get check** will hopefully give a hint on whether Opera is the only software package which has not been installed properly.
[/LIST]

Kind regards,
Karl

---

### Post by kerry_s on 2011-12-24
the new opera probably runs fine but has no space to run. suggest you make space.
clear cache
clear history
delete the man pages, that will give you at least a 100mb+ of space
delete logs
uninstall crap you don't need

---

### Post by gandaran on 2011-12-25
> Any idea down to what version will work on Ubuntu 9.11? And, what is it about new version that is messing up with old version of OS; and possible workaround?
new opera versions are not compatible with older opera user configuration files, the fix is simple delete the /home/user/.opera  folder but backup first as you will loose you favorite bookmarks then you can run the new opera without problems.

---

### Post by degarb on 2011-12-25
> **gandaran said:**
> new opera versions are not compatible with older opera user configuration files, the fix is simple delete the /home/user/.opera  folder but backup first as you will loose you favorite bookmarks then you can run the new opera without problems.

Cool, looks like a simple solution.   I did just get Opera 12 beta, next, installed!  Without using any workaround.


I wonder if this would work to get Spotify to install on this version of the OS.

================
aside:

If I knew newer version would install I might keep up.     Trying to get users to ugrade, when ugrades take gigs of free space, may take hours, may break a machine; this only drags off topic.  I will likely toss machine the very day I must upgrade, since new Ubuntu will likely be too large too memory intensive, and Likely I would never have ability to get the wireless card working again (no cable card on machine.)  Otherwise, this machine does video over network, music, office, surfing,kid educational games, etc.  All on a 2002 laptop.    ONly need 5-8 more laptops to serve all house hold needs.

---

### Post by gandaran on 2011-12-27
>  and Likely I would never have ability to get the wireless card working again
the wireless card may work out of the box on new ubuntu versions 
post the wirelss chip card brand and model, if it is working on older ubuntu I'm sure it will be easy.
or try run the live cd first then only if everything works you can do a install.
also for an old laptop I would recommend [lubuntu]("http://lubuntu.net/") instead of ubuntu download and burn the ISO to cd then run the live session, if you like it and works then try the install.

---

### Post by degarb on 2012-02-20
I don't think it is a matter of space, the opera next beta 12.13 ran well for about a month, then upgraded the beta, now it will not start, like Opera 11.  I removed unused kernels and got back up to 800 k.  Uninstalling and reinstalling Opera is no help.

I am using Epiphany, FF never ran smoothly on the machine.  Opera was more useable than Epiphany.

Hmm. opera runs fine on my 2001 xp machine.  No breakage there.  

Has to be something with some changing standard of folder (registry) convention between Ubuntu 10 and 11.

---

### Post by degarb on 2012-02-20
800 meg, I mean.  Obviously!

I deleted .opera and .opera-next, but still crashing on startup.

---

