---
title: "seems to be endless loop on trying to boot - HELP !"
date: 2008-11-23
forum: New to Ubuntu
---

### Post by RLuck on 2008-11-23
On a full install everything was working fine till it said I needed to load 247 updates - and overnight about 200 were downloaded before my dialup connection was dropped - at this point I think if I had just gotten back on line and finished with the other 40+ I would have been OK - but I noticed an alert in upper right corner saying it needed a reboot. When I rebooted it got into an endless loop with a message of about four lines - last line said 'Running local boot scripts (/etc/rc.loacl)' 

Using the 8.04 install disc I was able to open a terminal and read these scripts. posted here:
---------------------
root@ubuntu:/etc/rc0.d# cat README 
The scripts in this directory are executed once when entering 
runlevel 0.

The scripts are all symbolic links whose targets are located in
/etc/init.d/ .

Generally it is not necessary to alter the scripts in this directory.
Their purpose is to stop all services and to make the system ready
for shutdown.
---------------------

I'm not real quick and sure (a real babe in the woods really) using a terminal - 

Can anyone help here seems if I can break the loop - how I don't know - then maybe I could finish the other 40+ updates and the system would reboot.

HOPE !  

Bob:):):)

---

### Post by RealPSL on 2008-11-23
Rluck,

Have you tried booting the system in recovery mode? You can do this by hitting ESC in the initial boot sequence you only have 2-3 seconds so you have to be quick. Once you are there I do not believe that rc.local gets run during the recovery but I am not 100% sure. Can you also send all 4 lines of the loop sometimes the last line is not indicative of the problem. rc.local in a default installation has nothing in it.

Let us know if after selecting recovery it still loops. In recovery you can still run an update but I have a broadband connection I am not sure how your dialup works.

Note booting recovery will not fix the problem but it will to some extent help isolate the source of the problem.

---

### Post by RLuck on 2008-11-23
Thanks for the reply RealPSL  

More information:
Continuing to go thru the README files this is the one for rc1.d
-----------------------
root@ubuntu:/etc/rc1.d# cat README 
The scripts in this directory are executed each time the system enters
this runlevel.

The scripts are all symbolic links whose targets are located in
/etc/init.d/ .

Generally it is not necessary to alter the scripts in this directory.
Their purpose is to stop all services and thus to put the system in
single-user mode.
----------------------
I would think - if I only knew how to feed the correct seed I could pull this out of it's problem and get it to boot.

I'll go now - reboot and try to post the four lines that come up -  and try also the Esc during boot initial boot . Be back soon  

Bob

If nothing works out  I can go back and install again  -  sure hate to though it took all afternnon yesterday setting up the cube in compiz-fusion  -  I bearly got to try it out and use it.  It was working GREAT when I decided to install the updates.  

Oh, Well stuff happens  ;)

---

### Post by kelean on 2008-11-23
If you are able to boot in recovery mode trhen you should be able to finish update.  I have run into somthing close to that before.  Once booted into recorvery mode run:

```
sudo apt-get -f install
```

If memory serves that will attemp to fix whats broken or tell you what the problems are.

I hope that helps, Kelean.

---

### Post by RLuck on 2008-11-23
Many Thanks to both kelean and RealPSL - 

I am back up and online downloading the remaining 69 updates it says I need.  After I hit Esc it gave me four choices and I choose fix X  -  must have been the problem  - next thing I knew it booted up correctly.  compiz-fusion doesn't appear to be there and it dropped me back to two desktops.  So I'll wait till the updates complete then set it up again.  At 5000+ B/s I'll be most of the day finishing with the updates.  

Sure miss DSL :confused:

Bob

---

