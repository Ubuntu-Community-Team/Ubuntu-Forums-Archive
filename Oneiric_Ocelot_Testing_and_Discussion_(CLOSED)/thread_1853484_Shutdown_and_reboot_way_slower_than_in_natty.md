---
title: "Shutdown and reboot way slower than in natty"
date: 2011-10-02
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by lucazade on 2011-10-02
Any clue why this is happenning?
Once the session is closed it takes double of the time to shutdown or reboot.. annoying!

There is also a bug for unity-2d that hooks the session for at least 30sec.. hope this at least will be solved in time.

maybe i have to improve my personal uptime record :)

---

### Post by wgarcia on 2011-10-02
I have noticed the same in two quite different systems. It takes a while to close the desktop (I'm using Unity) and another while to close the system completely once the desktop is closed. 

In one of the systems it does not close down at all, it stays at the splash screen where it says "Ubuntu" and has the dots below it.

I've been trying to diagnose this but I haven't been able to get rid of the splash screen. I tried to boot the system by erasing "quite splash" in the grub menu before booting, but the splash screen is still there when starting and closing down. Why doesn't it go away? I thought that by editing the appropriate line and erasing those parameters I would get a one time boot without splash and more verbosity...

---

### Post by lucazade on 2011-10-02
> **wgarcia said:**
> I have noticed the same in two quite different systems. It takes a while to close the desktop (I'm using Unity) and another while to close the system completely once the desktop is closed. 

In one of the systems it does not close down at all, it stays at the splash screen where it says "Ubuntu" and has the dots below it.

I've been trying to diagnose this but I haven't been able to get rid of the splash screen. I tried to boot the system by erasing "quite splash" in the grub menu before booting, but the splash screen is still there when starting and closing down. Why doesn't it go away? I thought that by editing the appropriate line and erasing those parameters I would get a one time boot without splash and more verbosity...

also removing splash from kernel params doesn't seem to kill plymouth completely.
saw this when trying to make the gma500 kms driver working.. it conflicted with plymouth resulting in a splitted screen. the only way i've found to avoid plymouth was to remove its init script.. probably there is a better way but i'm not aware of it.

sudo mv /etc/init/plymouth.conf /etc/init/plymouth.conf.disabled

---

### Post by mc4man on 2011-10-02
> **lucazade said:**
> 
There is also a bug for unity-2d that hooks the session for at least 30sec.. hope this at least will be solved in time.

I'd hope so  - the 1st few times I'd thought the system had hung up.
The only other annoying thing in 2d here is that while the 1st unmaxed window opens in screen center the 2nd one always opens upper left corner & hides the launcher (using whatever the default settings are

---

### Post by lucazade on 2011-10-03
> **mc4man said:**
> I'd hope so  - the 1st few times I'd thought the system had hung up.
The only other annoying thing in 2d here is that while the 1st unmaxed window opens in screen center the 2nd one always opens upper left corner & hides the launcher (using whatever the default settings are

I'm following the hangup bug from unity-2d birth :)
tried everything to debug and to provide better info to devs but it seems hard to catch.

about window placement i disable the launcher autohide so I don't see that issue but I imagine it could be annoying.

---

### Post by Harry33 on 2011-10-03
> **lucazade said:**
> also removing splash from kernel params doesn't seem to kill plymouth completely.
saw this when trying to make the gma500 kms driver working.. it conflicted with plymouth resulting in a splitted screen. the only way i've found to avoid plymouth was to remove its init script.. probably there is a better way but i'm not aware of it.

sudo mv /etc/init/plymouth.conf /etc/init/plymouth.conf.disabled

How about removing the theme packages, leaving only the ones that mountall depends on:
- plymouth
- libplymouth2 (dependant of plymouth)

After that (and with the text "quiet splash" in grub) you can see messages and nothing about plymouth.

---

### Post by lucazade on 2011-10-03
> **Harry33 said:**
> How about removing the theme packages, leaving only the ones that mountall depends on:
- plymouth
- libplymouth2 (dependant of plymouth)

After that (and with the text "quiet splash" in grub) you can see messages and nothing about plymouth.

I believe it is correct.. it should be more or less like passing 'text' to gfxpayload in grub menu.
Also 'vt.handoff=7' keeps alive the resolution of grub until plymouth (or lightdm if the splashscreen is disabled) comes up.

---

### Post by tista on 2011-10-03
> **lucazade said:**
> I believe it is correct.. it should be more or less like passing 'text' to gfxpayload in grub menu.
Also 'vt.handoff=7' keeps alive the resolution of grub until plymouth (or lightdm if the splashscreen is disabled) comes up.

Hi Luca. ;)

I suppose "modem manager" seeoms to waste to be killed...
Actually when I purged modem-manager makes shutdown quickly... :P
(Around 12 sec to 6 sec...)

cheers.

---

### Post by lucazade on 2011-10-03
> **tista said:**
> Hi Luca. ;)

I suppose "modem manager" seeoms to waste to be killed...
Actually when I purged modem-manager makes shutdown quickly... :P
(Around 12 sec to 6 sec...)

cheers.

Hi Tista

I've tried to purge modemmanager but it seems only a little bit faster, not really noticeable here.
Sometimes I use also a 3G dongle with the netbook so I can't purge it completely.
thanks anyway :)

---

### Post by lucazade on 2011-10-03
unity-2d bug is in progress (long delay at session shutdown)
[https://bugs.launchpad.net/unity-2d/+bug/812104](https://bugs.launchpad.net/unity-2d/+bug/812104)

---

### Post by mc4man on 2011-10-03
> **lucazade said:**
> unity-2d bug is in progress (long delay at session shutdown)
[https://bugs.launchpad.net/unity-2d/+bug/812104](https://bugs.launchpad.net/unity-2d/+bug/812104)
Thanks for link
side note - whats odd here is if I start the logout helper from a terminal than most times, (not all) I get a quick logout

```
/usr/lib/indicator-session/gtk-logout-helper --logout
```

---

### Post by TuxIsAwesome on 2011-10-03
Thats very odd, because I am experiencing the exact opposite in Natty > Onieric

-Logout time has been halved
-Shutdown takes 1/4 of the time it used to
-Reboot is more or less the same as shutdown


I have an 

Acer Aspire 7551-7422
RAM: 4GB DDR3 @ 1066MHz (Not Overclocked)
CPU: AMD Phenom II X4 N970 @ 2.2GHz (Not Overclocked)
HDD: 750GB WD SATA3 HDD (Using recommended settings for Advanced Format Drives)
Graphics: ATI Mobility Radeon HD 4250 (FGLXR Driver)
Using radeon.modeset=0 and nomodeset in /etc/default/grub as well as a blacklist radeon entry in /etc/modprobe.d/blacklist.conf to disable and prevent the radeon module from loading, which totally foobars my suspend/hibernate abilitys up the wall and back

Granted my machine is a bit of a beast, but it that isn't the cause of why mine is faster to shutdown/reboot/etc faster than yours is, then it might be having something to do with the way yours is configured.

Oh and you mentioned that you removed the quiet splash entry from GRUB_CMDLINE_LINUX_DEFAULT="" in /etc/default/grub. 

I know why it's still displaying, and it's a very easy fix.

Run this command, and your grub2 menu will update, and will parse those changes so that you can boot without any splash screen, just lovely, charming, verbose output

sudo update-grub

Reboot and log into whichever kernel you happen to like using, and it should no longer give you a splash screen.

Albiet the splash screen is pretty and all that, I too find that it's inherently useless in terms of how the machine boots. I just wish I knew how to make all the text look pretty, and maybe at least have a background to the verbose screen.

---

### Post by lucazade on 2011-10-03
I can say I see slower shutdowns in Oneiric from first builds using 5 different machines. Fresh installs, stock stuff, no 3rd parties apps.
So I'd say it is not related to configurations or caused by machines' performances.

about 'quiet splash' removed from grub, this disables only plymouth but a large part of log messages are not displayed this way.
You need to remove also the plymouth init script to see the rest.

---

### Post by lucazade on 2011-10-03
> **mc4man said:**
> Thanks for link
side note - whats odd here is if I start the logout helper from a terminal than most times, (not all) I get a quick logout

```
/usr/lib/indicator-session/gtk-logout-helper --logout
```

nice.. going to try it :)

---

### Post by Rasa1111 on 2011-10-03
I find the opposite in 11.10.
it boots up and shuts down quite a bit faster than natty.

---

### Post by lucazade on 2011-10-03
> **mc4man said:**
> Thanks for link
side note - whats odd here is if I start the logout helper from a terminal than most times, (not all) I get a quick logout

```
/usr/lib/indicator-session/gtk-logout-helper --logout
```

great.. session logout is fast.
going to add this to the bugreport :)

---

### Post by wgarcia on 2011-10-03
I tried it in Unity 3D in one of my systems and the logout is still slow.

---

### Post by wgarcia on 2011-10-03
I reported a bug for Unity 3D if anybody else is affected:

[https://bugs.launchpad.net/ubuntu/+source/unity/+bug/865612](https://bugs.launchpad.net/ubuntu/+source/unity/+bug/865612)

---

### Post by kaldor on 2011-10-03
I can confirm this. 

I used Ubuntu 11.10 briefly yesterday (was in a distro hopping mood) and noticed that everything was much slower. When I shut down on Fedora 15 it takes maybe 15 seconds whereas I stared for about 40 seconds at the moving dots on Plymouth before it shut off.

---

### Post by mc4man on 2011-10-03
I'd guess if anyone is saying their shutdown/reboot times are faster in 11.10 should put it in reference. I'd expecpt most find it significantly increased
For Ex. here
10.04 > 11.04 , sd/rb is generally 2-3 sec
11.10,  10-13 sec

---

### Post by mc4man on 2011-10-04
On the topic of the unity-2d logout hang - 
Due to some increasing issues here, both with crashers & just poor behavior (hopefully fixed with the fix release on xsession bug which does involve more than just the root owned file), went ahead & installed gdm & switched to it
Also purged lightdm which I believe should be done atm if switching

Not only has all the bad stuff stopped with  unity 3d,  but a quick test (4 attempts) of a unity-2d logout thru the indicator shows no hang at all

edit:
one of the reasons for not having 2 dm's installed has been fixed in latest upstart - more a graphical issue, plymouth over text on shutdown/restart

---

### Post by lucazade on 2011-10-04
> **mc4man said:**
> I'd guess if anyone is saying their shutdown/reboot times are faster in 11.10 should put it in reference. I'd expecpt most find it significantly increased
For Ex. here
10.04 > 11.04 , sd/rb is generally 2-3 sec
11.10,  10-13 sec

exactly, same here... 
it was blazing fast in previous releases and slow as hell in Oneiric.

> **mc4man said:**
> On the topic of the unity-2d logout hang - 
Due to some increasing issues here, both with crashers & just poor behavior (hopefully fixed with the fix release on xsession bug which does involve more than just the root owned file), went ahead & installed gdm & switched to it
Also purged lightdm which I believe should be done atm if switching

Not only has all the bad stuff stopped with  unity 3d,  but a quick test (4 attempts) of a unity-2d logout thru the indicator shows no hang at all

this is interesting, going to try here as well.. 
thanks for sharing. i'll report back my experiences.

---

### Post by robert shearer on 2011-10-04
> **lucazade said:**
> exactly, same here... 
it was blazing fast in previous releases and slow as hell in Oneiric.

Agreed.!

Though a week or so ago when there was the glitch with the loss of networking...
[http://ubuntuforums.org/showthread.php?t=1846185](http://ubuntuforums.org/showthread.php?t=1846185)

for a day or so the shutdown was **as fast as in Natty** then reverted to the previous (and current) slothful state.

"I don't really want to shutdown, please just wait a moment or two, not so fast, don't be impatient, oh all right, if you insist, here we go, now how does it go again.....etc,etc,etc." :)

---

### Post by mc4man on 2011-10-04
The new lightdm seems to be helpful in a unity-2d logout though at least here the log out can hang on black text screen once & a while

(though for the moment I have a slightly different libgnome-desktop-3-2 installed, not sure if involved, likely not
Probably going to try a new install tomorrow & then this weekend

---

### Post by lucazade on 2011-10-06
Found why sd and rb are slow... network-manager doesn't shutdown properly and it adds 5/10 sec to the closing routine.

a fix for karmic does the trick:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/418509/comments/105](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/418509/comments/105)

```
--- /etc/init/network-manager.conf.orig 2010-05-03 14:56:09.745071317 +0200
+++ /etc/init/network-manager.conf 2010-05-03 14:56:43.075152939 +0200
@@ -8,6 +8,7 @@
 start on (local-filesystems
          and started dbus)
 stop on stopping dbus
+stop on runlevel [06]

 expect fork
 respawn
```

before applying this I've seen in VT these:
* Asking all remaining processes to terminate... [OK]
* Killing all remaining processes... [fail]

now this is no more present :)
[https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/869635](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/869635)


..now it is time to iron out unity-2d delay at session closing...

---

### Post by Harry33 on 2011-10-07
Confirmed this bug.

I can see this message too right after the "killing all remaining processes":
"nmdispatcher.action caught signal 15 shutting down ..."

---

### Post by Harry33 on 2011-10-07
And yes, Lucazade
adding the line
stop on runlevel [6]
into the file /ect/init/network-manager.conf
really fixed the issue.

Now all my setups are restarting immediately.
Thanks.

---

### Post by lucazade on 2011-10-07
> **Harry33 said:**
> And yes, Lucazade
adding the line
stop on runlevel [6]
into the file /ect/init/network-manager.conf
really fixed the issue.

Now all my setups are shutting down immediately.
Thanks.

thanks for the feedback :D

---

### Post by robert shearer on 2011-10-07
Confirmed. Works here too ! Thanks lucazade :D

@Harry33....  took me a while to decipher it too. Your clarification should be a good pointer for others to follow.

---

### Post by lucazade on 2011-10-07
Probably I've found why there is a long delay with Unity-2D when closing session.
If I don't open the dash the session closes fast, If I open it the delay is always reproducible (at least here after a ton of trials!)

[https://bugs.launchpad.net/unity-2d/+bug/812104](https://bugs.launchpad.net/unity-2d/+bug/812104)

---

### Post by mc4man on 2011-10-07
> **lucazade said:**
> Probably I've found why there is a long delay with Unity-2D when closing session.
If I don't open the dash the session closes fast, If I open it the delay is always reproducible (at least here after a ton of trials!)

[https://bugs.launchpad.net/unity-2d/+bug/812104](https://bugs.launchpad.net/unity-2d/+bug/812104)
For something else I've probably done a couple of hundred+ log in/outs in last few days, many with unity-2d. Every time I thought there was a pattern to the hang occurring or not it turned out to just be happenstance.

Probably a 60-40 thing here that it occurs. (currently back to gdm

( have also been getting cursor spin on opening nautilus from home-folder launcher icon when no other nautilus instance is open...

---

### Post by lucazade on 2011-10-08
> **mc4man said:**
> For something else I've probably done a couple of hundred+ log in/outs in last few days, many with unity-2d. Every time I thought there was a pattern to the hang occurring or not it turned out to just be happenstance.

Probably a 60-40 thing here that it occurs. (currently back to gdm

( have also been getting cursor spin on opening nautilus from home-folder launcher icon when no other nautilus instance is open...

I've tried gdm (and also slim dm) to see if lightdm has some negative impact on session and check startup time. I've to say lightdm is quite mature and stable lately.

I've seen also the spinning cursor for nautilus during other checks but I wasn't able to find any clue about it.

---

### Post by mc4man on 2011-10-08
The main issue I see with lightdm may only affect certain hardware, who knows, but it is a bit of a pita
[https://bugs.launchpad.net/ubuntu/+source/lightdm/+bug/863054](https://bugs.launchpad.net/ubuntu/+source/lightdm/+bug/863054)

Otherwise it's ok other then an occasional log out freeze on the black text screen that usually only appears for a split second (fairly rare

Still overall I see some 'out of the blue' weird happenings on 11.10, like this one, first time just now - 

Opened thunderbird on another Ws to retrieve & open the above bug - currently on that Ws there is TB & a new FF window open.
The spread (l. click on FF icon) shows that  FF & TB which shouldn't happen, not in same window group
And it is not seeing this FF window on different Ws that I'm posting in. but is finding the attachment window

(Hard to describe clearly - I see what's gone wrong, more the point that this shouldn't be happening 
I think the release of 11.10 will prove to be quite interesting..

---

### Post by lucazade on 2011-10-08
> **mc4man said:**
> The main issue I see with lightdm may only affect certain hardware, who knows, but it is a bit of a pita
[https://bugs.launchpad.net/ubuntu/+source/lightdm/+bug/863054](https://bugs.launchpad.net/ubuntu/+source/lightdm/+bug/863054)

Otherwise it's ok other then an occasional log out freeze on the black text screen that usually only appears for a split second (fairly rare

Still overall I see some 'out of the blue' weird happenings on 11.10, like this one, first time just now - 

Opened thunderbird on another Ws to retrieve & open the above bug - currently on that Ws there is TB & a new FF window open.
The spread (l. click on FF icon) shows that  FF & TB which shouldn't happen, not in same window group
And it is not seeing this FF window on different Ws that I'm posting in. but is finding the attachment window

(Hard to describe clearly - I see what's gone wrong, more the point that this shouldn't be happening 
I think the release of 11.10 will prove to be quite interesting..

I'll follow the bug report about lightdm, didn't noticed all the session is owned by root.. thought only .xsessionerrors.

About the wrong window pick haven't seen here, I'll try to reproduce it to understand it better.

---

### Post by mc4man on 2011-10-08
> About the wrong window pick haven't seen here, I'll try to reproduce it to understand it better.
I would think it would be almost impossible to recreate, I'd never had that happen before & maybe never again.
Even though this install is only 3 days old at this point don't have 100% trust in it, maybe 1 more test install this weekend & then 'one for real' to use in place of 11.04

(the change you suggested to restarts has been working out fine here, a couple of sec.'s & done..

---

### Post by Harry33 on 2011-10-08
> **mc4man said:**
> 
...
(the change you suggested to restarts has been working out fine here, a couple of sec.'s & done..

Here too.
But mc4man, did that have any effect on power down (halt)?

Lucazade, I still get the "killing all remainig processes - fail" error when shutting down. Restarts work fine.

---

### Post by mc4man on 2011-10-08
> **Harry33 said:**
> Here too.
But mc4man, did that have any effect on power down (halt)?

Lucazade, I still get the "killing all remainig processes - fail" error when shutting down. Restarts work fine.
It appears so  - though still a bit slower than 11.04
In 11.04 it was usually 2 secs & done for both
Now (with change) its generally 3 sec for restart, 5 for shutdown
What's going on can't see - trying to keep this install close to default as provided
( have gotten rid of the 1.7.4 sudo because it's a pita in dev, & am using gdm instead of lightdm

Maybe I'll go to a no plymouth splash, non quiet & see what it says..

---

### Post by Rasa1111 on 2011-10-08
Ive booted into my 11.04 partition 3 times since my last post in this thread..
and still have to say that my 11.10 boots up faster than 11.04. 
a good 10+ seconds faster.

---

### Post by Harry33 on 2011-10-08
> **mc4man said:**
> It appears so  - though still a bit slower than 11.04
In 11.04 it was usually 2 secs & done for both
Now (with change) its generally 3 sec for restart, 5 for shutdown
What's going on can't see - trying to keep this install close to default as provided
( have gotten rid of the 1.7.4 sudo because it's a pita in dev, & am using gdm instead of lightdm

Maybe I'll go to a no plymouth splash, non quiet & see what it says..

Yes please do that.
It is the only way to see the messages as there are no logs generated about it.

---

### Post by mc4man on 2011-10-08
> **Harry33 said:**
> Yes please do that.
It is the only way to see the messages as there are no logs generated about it.
Interesting - 
with all the plymouth splash packages removed (3), & grub adjusted am now seeing a quicker shutdown - 2-3 sec
The output is larger than a restart, but definitely no "killing all remainig processes - fail" or any other fail.

As mentioned only real changes here were sudo (irrelevant), & I am using gdm

---

### Post by lucazade on 2011-10-12
The delay present when closing the Unity-2D session (specially when using the application dash) is logged in .xsessionerrors file.
I have enabled '--debug' for gnome-settings-daemon in /usr/share/xsessions/ubuntu-2d.desktop to get more verbosity and looked at logs after the session is completely closed (switched from lightdm to vt).

```
(process:3926): libunity-CRITICAL **: unity_inspector_on_unity_vanished: assertion `conn != NULL' failed
g_dbus_connection_real_closed: Remote peer vanished with error: Underlying GIOStream returned 0 bytes on an async read (g-io-error-quark, 0). Exiting.
```

going to add these notes to [bug-report]("https://bugs.launchpad.net/unity-2d/+bug/812104")

---

