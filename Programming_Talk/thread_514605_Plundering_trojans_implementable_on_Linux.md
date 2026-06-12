---
title: "Plundering trojans implementable on Linux?"
date: 2007-07-31
forum: Programming Talk
---

### Post by resander on 2007-07-31
I posted something similar to this in the Server & Security forum and got one reply. Maybe this forum is more suitable for this post.


ABOUT THE E-GOLD PLUNDERING TROJAN

The win32.grams trojan plunders e-gold accounts on Windows systems. It sits and waits for a user to enter the website address of egold and the password. Then it takes over (don't know how - maybe it spawns another browser process or hijacks the user's browser process) and opens an invisible 0 x 0 window and transfers the balance to another account (opened under false name with ATM card probably). When control returns to the user there is no money left 
in the account. As far as egold is concerned this is a normal user-initiated transaction, so there will be no refund. Similar techniques can be used for attacking PayPal accounts and Internet banking accounts.

On Windows there is no defense against this type of trojan other than not having it on the computer when you access your money or bullion account.

Here is more info about this trojan:

[www.secureworks.com/research/threats/grams/](www.secureworks.com/research/threats/grams/)



I am a Linux newbie and cannot figure this out myself:

1. assuming a trojan of this kind has found its way into a Linux system, e.g. downloaded as a trojan masquerading as hex calculator, jpg image etc, is there any way it can actually do the plundering on a Linux system?

2. are there ways to stop the trojan doing mischief if it is already on
the system, or phrased differently, can anything be done to completely snooker it?


AUTO RESTART ON LINUX?

Trojans need to be restarted on bootup. In Windows this is achieved by putting the program .exe name into a special place in the Registry. A Trojan sets this registry entry on initial infestation. Is there an equivalent auto restart mechanism in Linux?

KEYSTROKE LOGGERS POSSIBLE ON LINUX?

The e-gold plundering trojan in some way 'attaches' itself to the user 
browser process and then reads the content of the browser fields (I think) in order to synchronize itself for attack. This could be achieved by a keystroke logger too. In Windows there is a set of API functions that allows a process to spy on the key strokes sent to another process.Can anything equivalent be implemented on Linux?


FIREWALL LIKE ZONEALARM?

Slightly off topic...
On Windows I am configuring the ZoneAlarm firewall to allow browser and email clients to freely access Internet. ZoneAlarm pops up a confirm dialog if other processes try to access Internet, for example trojans trying to 'phone home'. Can Ubuntu provide something similar?

---

### Post by slavik on 2007-08-01
the first reason why it "may" possible in linux is if the process is run under root priveledges ... once that happens, all security bets are off, no matter the system.

---

### Post by Ramses de Norre on 2007-08-01
> **slavik said:**
> the first reason why it "may" possible in linux is if the process is run under root priveledges ... once that happens, all security bets are off, no matter the system.

That's you're own responsibility, be careful with root....

The big reasons why you wont see this trojan quickly are (IMO):

*you should only download and install software from the repo or from trusted sources, installing is done by root (requires password) and if you set "noexec" on /home no commands other than those installed by root can be executed.

*there are autostart mechanisms but they differ... Files like /etc/rc.local are system wide and on most linux systems but they require root access again. WMs provide autostart mechanisms too which are user accessible but they differ between WMs, there might be a solid system for gnome and kde but WMs like openbox and pekwm and such often require the user to execute his own script to autostart stuff, requiring root access to start the script from somewhere.

So the big difficulty in implementing such a trojan is the need for access to the root account...

---

### Post by pmasiar on 2007-08-01
I know you most likely know it, but maybe someone would like it, and I feel like writing it :-) , so here it goes:

Main (even philosophical) difference between Windows and Linux is .... history. 

Windows was born as pretty GUI on top of MS-DOS. MS-DOS was a single-user OS, way before computers were connected - [Sneakernet](http://en.wikipedia.org/wiki/Sneakernet) was state-of-the-art network back in old times, and it did not bother about security at all. All it bothered was convenience. Programmers found "convenient" to  access hardware directly, install memory-resident programs etc.

Since then, LANs and now internet forced MSFT to take security more seriously - even if it means less convenience, but it is hard for them - and hard for MSFT users, who would run as superuser all the time without thinking. And it was hard NOT be Admin even under win-XP, bacause even simple tasks were too complicated.

Vista is first serious attempt to do it half-right, and it is more pain to use as a result. See, it is "less convenient" :-)

Unix, precursor of Linux, was multi-user OS from very beginning, with obvious focus on protecting users from each other, and protecting system from "curious" users. Yes, I wrote my first trojan and worm on Unix back in times, too :-) and got it out of my system. Trick is how to make your friends to run a script. Solution is social engineering. So Unix has about 30 years lead on Vista on that :-)

Re questions: 

There are many ways to make your system more secure from different kinds of access. Each one involves some degrees of inconvenience, so it's up to you to decide what you prefer and can tolerate.

The only way to be 100% safe from viruses is never connect you computer with outside world (including no new programs). then again , you need to upgrade your virus checker... catch 22. :-) Solution: break that box and go play frisbie.

Firewall: [http://www.google.com/search?q=ubuntu+firewall](http://www.google.com/search?q=ubuntu+firewall)

---

