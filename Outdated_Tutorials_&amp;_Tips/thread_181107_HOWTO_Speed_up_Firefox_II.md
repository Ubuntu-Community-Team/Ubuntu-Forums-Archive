---
title: "HOWTO: Speed up Firefox II"
date: 2006-05-23
forum: Outdated Tutorials &amp; Tips
---

### Post by Pjotor on 2006-05-23
You can speed up your Firefox browser by doing the following:

```
cd ~/.mozilla/firefox/*.default/
```
```
gedit user.js
```

Everyone should put there:

```
user_pref("network.http.pipelining", true);
user_pref("network.http.proxy.pipelining", true);
user_pref("network.http.pipelining.maxrequests", 8);
user_pref("content.notify.backoffcount", 5);
user_pref("plugin.expose_full_path", true);
user_pref("ui.submenuDelay", 0);
```

and after that one of the following depending on your computer and your connection:

FAST COMPUTER, FAST CONNECTION

```
user_pref("content.interrupt.parsing", true);
user_pref("content.max.tokenizing.time", 2250000);
user_pref("content.notify.interval", 750000);
user_pref("content.notify.ontimer", true);
user_pref("content.switch.threshold", 750000);
user_pref("nglayout.initialpaint.delay", 0);
user_pref("network.http.max-connections", 48);
user_pref("network.http.max-connections-per-server", 16);
user_pref("network.http.max-persistent-connections-per-proxy", 16);
user_pref("network.http.max-persistent-connections-per-server", 8);
user_pref("browser.cache.memory.capacity", 65536);

```

FAST COMPUTER, SLOWER CONNECTION

```
user_pref("content.max.tokenizing.time", 2250000);
user_pref("content.notify.interval", 750000);
user_pref("content.notify.ontimer", true);
user_pref("content.switch.threshold", 750000);
user_pref("network.http.max-connections", 48);
user_pref("network.http.max-connections-per-server", 16);
user_pref("network.http.max-persistent-connections-per-proxy", 16);
user_pref("network.http.max-persistent-connections-per-server", 8);
user_pref("nglayout.initialpaint.delay", 0);
user_pref("browser.cache.memory.capacity", 65536);
```

FAST COMPUTER, SLOW CONNECTION

```
user_pref("browser.xul.error_pages.enabled", true);
user_pref("content.interrupt.parsing", true);
user_pref("content.max.tokenizing.time", 3000000);
user_pref("content.maxtextrun" 8191);
user_pref("content.notify.interval", 750000);
user_pref("content.notify.ontimer", true);
user_pref("content.switch.threshold", 750000);
user_pref("network.http.max-connections", 32);
user_pref("network.http.max-connections-per-server", 8);
user_pref("network.http.max-persistent-connections-per-proxy", 8);
user_pref("network.http.max-persistent-connections-per-server", 4);
user_pref("nglayout.initialpaint.delay", 0);
user_pref("browser.cache.memory.capacity", 65536);
```

SLOW COMPUTER, FAST CONNECTION

```
user_pref("content.max.tokenizing.time", 3000000);
user_pref("content.notify.backoffcount", 5);
user_pref("content.notify.interval", 1000000);
user_pref("content.notify.ontimer", true);
user_pref("content.switch.threshold", 1000000);
user_pref("content.maxtextrun", 4095);
user_pref("nglayout.initialpaint.delay", 1000);
user_pref("network.http.max-connections", 48);
user_pref("network.http.max-connections-per-server", 16);
user_pref("network.http.max-persistent-connections-per-proxy", 16);
user_pref("network.http.max-persistent-connections-per-server", 8);
user_pref("dom.disable_window_status_change", true);
```

DIAL-UP

```
user_pref("content.max.tokenizing.time", 2250000);
user_pref("content.notify.interval", 750000);
user_pref("content.notify.ontimer", true);
user_pref("content.switch.threshold", 750000);
user_pref("nglayout.initialpaint.delay", 750);
user_pref("network.http.max-connections", 32);
user_pref("network.http.max-connections-per-server", 8);
user_pref("network.http.max-persistent-connections-per-proxy", 8);
user_pref("network.http.max-persistent-connections-per-server", 4);
user_pref("dom.disable_window_status_change", true);

```

From: [http://www.tweakfactor.com/articles/tweaks/firefoxtweak/4.html](http://www.tweakfactor.com/articles/tweaks/firefoxtweak/4.html)

---

### Post by Toxicity999 on 2006-06-05
sounds Identical to faster fox of winows

---

### Post by kingsidy on 2006-06-07
exactly what i was thinking. that extension is often overlooked.

---

### Post by wwood on 2006-06-07
Minor correction. 

Shouldn't there be a starting double quotes in line 7 of the 

FAST COMPUTER, FAST CONNECTION

So it should read

user_pref("content.interrupt.parsing", true);
user_pref("content.max.tokenizing.time", 2250000);
user_pref("content.notify.interval", 750000);
user_pref("content.notify.ontimer", true);
user_pref("content.switch.threshold", 750000);
user_pref("nglayout.initialpaint.delay", 0);
user_pref("network.http.max-connections", 48);
user_pref("network.http.max-connections-per-server", 16);
user_pref("network.http.max-persistent-connections-per-proxy", 16);
user_pref("network.http.max-persistent-connections-per-server", 8);
user_pref("browser.cache.memory.capacity", 65536);



Correct?

---

### Post by simplyw00x on 2006-06-07
Most of these settings are available in FasterFox, and many of them are irresponsible and cause excess traffic on websites, thus pushing up bandwidth bills. Re-posting this by telling people to edit user.js instead of the usual about:config doesn't change how old and bad these 'improvements' are.

---

### Post by M4LFUNCT10N on 2006-06-07
Not sure if i'm the only one, but doing those changes actually slowed down firefox for me.

---

### Post by dr_d on 2006-06-08
I think it would be nice if you would provide more detailed info about the connection speed these mods are optimized for.

For example, I have 512KB broadband. I know it's not a slow connection, but does it count as a fast connection or a slower connection?

much appreciated.

---

### Post by dagr8tim on 2006-06-08
How about just typing "about:config" in the address bar?  

I know I've done this in other distro's.

---

### Post by xXx 0wn3d xXx on 2006-06-08
[QUOTE=dr_d]I think it would be nice if you would provide more detailed info about the connection speed these mods are optimized for.

For example, I have 512KB broadband. I know it's not a slow connection, but does it count as a fast connection or a slower connection?

much appreciated.[/QUOTE]
I would think that it would be a faster connection. That's just my optinion since it generally is a fairly fast connection and slow connections means dial-uo or isdn.

---

### Post by TuxCrafter on 2006-07-18
Thx for the info is there a big diffrence in using fasterfox?

also i thing this is wrong
```
gedit user.js
```

it should be
```
gedit prefs.js
```

Thx again 8)

Ps this is wrong info prefs.js gets overwriten i have made a new file called user.js and used it

---

### Post by aeto on 2006-07-20
tuxcrafter: prefs.js gets overwritten after u exit firefox. it is already stated in there.

---

### Post by TuxCrafter on 2006-07-20
I see it thanks for the info i will make a new file user.js

---

### Post by barbarian on 2006-07-20
Thanx for howto, me, personally, beleive, that firefox is the best tweakable browser ever.
One think I'm doubting about..- could I consider my machine specs as a 'fast computer'?
I have Athlon 2500 XP(32bit) with 512 Mb RAM

---

### Post by Iyatos on 2006-07-25
Thx for the guide very useful.

---

### Post by deizel on 2006-08-01
Instead of doing:
```
gedit ~/.mozilla/firefox/*.default/user.js
```
you can go to the URL
```
about:config
```
d.

---

### Post by Gimikk on 2006-08-11
Yes, it's prefs.js !

---

### Post by dancavs on 2006-08-12
i have found firefox to be slower on ubuntu than on winxp, and opera browser on ubuntu to be quicker than firefox on ubuntu ... ?

but according to [http://www.skattertech.com/2006/02/how-to-block-fasterfox-requests/#]("http://www.skattertech.com/2006/02/how-to-block-fasterfox-requests/#") the fasterfox extension is a problem for webmasters who are low on bandwidth by causing premature overload, as it were ...

anyway speeds not everything, its what you use it for that counts :p

---

### Post by VCSkier on 2006-09-05
how would this be different for swiftfox users.  i have it installed in /opt/swiftfox/

---

### Post by ~LoKe on 2006-09-06
> **VCSkier said:**
> how would this be different for swiftfox users.  i have it installed in /opt/swiftfox/

Just install the FasterFox extension.

---

### Post by VCSkier on 2006-09-06
i try to minimize my use of extensions.

---

### Post by Karail on 2006-10-01
As far as i am aware it is not possible to install faster fox on Firebird Version 2 yet. Also using about:config in the address bar is much easier.

---

### Post by TSP on 2006-10-29
```
user_pref(network.http.max-connections", 48);
```

Fix that line is Fast Cimputer Fast connection, there is a missing " is the start.

Thanks for this :D

---

### Post by zek725 on 2007-04-10
> **deizel said:**
> Instead of doing:
```
gedit ~/.mozilla/firefox/*.default/user.js
```
you can go to the URL
```
about:config
```
d.

I've edited it using about:config. How do you delete a preference key? I accidentally assigned **nglayout.initialpaint.delay** as **string** and I want to undo it.

---

### Post by dazzpj on 2007-05-15
Does anyone have any tips for improving Firefox response in Ubuntu ?  I'm not looking for fasterfox or any of the settings that supposedly improve performance of page retrieval, I am actually trying to improve the responsiveness of the application itself.

I have used Fx for quite some time on Windows XP and it was great, now switching to Ubuntu as my OS of choice i find that Firefox performs terribly, switching from one tab to another seems to take about 2 seconds, something that should be instant and is instant on Windows XP, does anyone else see this type of sluggish performance from Fx in Ubuntu or am i simply going mad ?

---

### Post by TuxCrafter on 2007-05-17
> **dazzpj said:**
> Does anyone have any tips for improving Firefox response in Ubuntu ?  I'm not looking for fasterfox or any of the settings that supposedly improve performance of page retrieval, I am actually trying to improve the responsiveness of the application itself.

I have used Fx for quite some time on Windows XP and it was great, now switching to Ubuntu as my OS of choice i find that Firefox performs terribly, switching from one tab to another seems to take about 2 seconds, something that should be instant and is instant on Windows XP, does anyone else see this type of sluggish performance from Fx in Ubuntu or am i simply going mad ?

I think you have a 2D/3D video driver problem, are your video drivers installed correctly. The only thing I know of is disabling ipv6 functions to speed-up the GUI. Let us know when you find something.

---

### Post by Diabolis on 2007-08-01
I find forefox slower on ubuntu  too and I think my video drivers are ok. Would it have to deal with the size of my RAM?

---

### Post by Ubuntiac on 2007-09-29
I'm finding FF incredibly slower on this latest pre-release of Ubuntu (Gutsy Beta). I know my video drivers are fine, as performance in Compiz Fusion is silky smooth. Try changing between tabs in FF though, and as previous poster put it, it can take over a second.

Another post about a very slow firefox actually was resolved by the user changing from an Intel Motherboard and CPU to an Asus/AMD combo. Given that I'm also on an Intel/Intel pair, I'd be curious to hear what anyone else having this problem is running as what I'm seeing is far more than just a speed of internet thing. It seems more to do with speed of redraw (IE tabswitching and scrolling). Xorg CPU usage (only when using FF) also seems strangely high whether using compiz or not.

I'm honestly thinking this needs a bug report, but am info gathering first... :)

---

### Post by twright on 2007-10-29
try swiftweasel:)

---

### Post by cthulhu.hpl on 2007-11-02
Well, I'm using Gutsy final release and I do notice sluggish performance with firefox...everything else (including Compiz-Fusion) works as expected.

I'm using a 2.8 Ghz Athlon, 1GB of Ram and a Radeon 9800 XT (with the last closed source, nonfree drivers from ati).

¿Any ideas?

---

### Post by crimesaucer on 2007-12-10
> **zek725 said:**
> I've edited it using about:config. How do you delete a preference key? I accidentally assigned **nglayout.initialpaint.delay** as **string** and I want to undo it.

You right click on the one you want to delete, and the select "Reset".


If you created the preference like nglayout.initialpaint.delay, then resetting it will erase it after a restart.


If it already existed, it will go back to default setting.

---

### Post by warbread on 2007-12-11
> **Ubuntiac said:**
> I'm finding FF incredibly slower on this latest pre-release of Ubuntu (Gutsy Beta). I know my video drivers are fine, as performance in Compiz Fusion is silky smooth. Try changing between tabs in FF though, and as previous poster put it, it can take over a second.

Another post about a very slow firefox actually was resolved by the user changing from an Intel Motherboard and CPU to an Asus/AMD combo. Given that I'm also on an Intel/Intel pair, I'd be curious to hear what anyone else having this problem is running as what I'm seeing is far more than just a speed of internet thing. It seems more to do with speed of redraw (IE tabswitching and scrolling). Xorg CPU usage (only when using FF) also seems strangely high whether using compiz or not.

I'm honestly thinking this needs a bug report, but am info gathering first... :)

I'm having the exact same problem.  Guess what?  I've got an Intel Core2 Duo and nVidia 8600m GT.  Has anyone else tried [this?]("http://onlinedev.blogspot.com/2007/09/compiz-fusion-slow-on-nvidia.html")

---

### Post by Pelonchas on 2007-12-16
> **warbread said:**
> I'm having the exact same problem.  Guess what?  I've got an Intel Core2 Duo and nVidia 8600m GT.  Has anyone else tried [this?]("http://onlinedev.blogspot.com/2007/09/compiz-fusion-slow-on-nvidia.html")

I had the same problem with Gutsy Release Candidate, tryed to fix it many times reading and trying many guides, upgrading nm-applet and removing it. In some point i did something bad and i had to reinstall Gutsy from my brand new Gutsy CD's from Netherland. I was impress about all the problems were not there. Not 100% CPU all the time, nm-applet were working ok this time, and all the firefox problems were gone. :guitar:

---

### Post by MarilenCorciovei on 2007-12-16
For me what it gave a boost to Firefox was [disabling ipv6]("http://www.len.ro/work/tools/ubuntu-gutsy-on-a-dell-latitude-d820/what-was-killing-my-gutsy"). It seems there where a lot of people complaining about slow firefox related to this issue but I would never have thought about it.

---

### Post by Muscar on 2007-12-17
So, if ive got a 8 mb/sec connection and a nVidia geforce 7300 with a 0.8 gHz CPU and 1.5 gig ram, that would count as? slow computer fast connection? :confused:

---

### Post by Sk1nnyMan on 2008-03-05
Can someone please give me an example of what a "Fast computer" is?

Thanks

---

### Post by Diabolis on 2008-03-05
I don't think that this is the right thread for your question. And how fast a computer is depends on what you want to do. A fast pc opens files faster if you got lots of ram, but it would not be fast enough to encrypt a password if it has a 20mhz processor. Usually the more the better, so I would say that a fast pc is the playstation 3. Graphics are the heaviest stuff you can do with a pc, so videogames require very powerful computers.

---

### Post by warbread on 2008-03-06
> **Sk1nnyMan said:**
> Can someone please give me an example of what a "Fast computer" is?

Thanks

[IMG]http://www.tvscoop.tv/knight-rider.jpg[/IMG]

---

### Post by Oldest Bob on 2008-03-08
I put in the mods and firefox went supersonic for me. Load time from click to home page dropped from 40-60secs to 3-5 secs. As noted by someone my file is in /firefox/383utfif.default/prefs.js. there is no "user.js" file in my version which came on a Gutsey CD. Firefox is still slow on my Windows and I sure notice the difference.By the way I think there is a typo in line 13.** initialpaint** should probably be **initialpoint** - right? At least that's what I used. Thanks for a great boost to my Firefox.

---

### Post by davidgutu on 2008-04-20
I don't see any difference? Maybe mine already had that tweak.

:)

---

### Post by xMoDx on 2008-06-24
> **~LoKe said:**
> Just install the FasterFox extension.

fasterfox is still not available for FF3 :(

---

### Post by abhinav.p on 2009-03-31
ok heres a scenario.i use wireless network provided by university and hence my speed at anytime dependa on how many of the users are sharing a router.so fastness is unpredictable.so what settings do i do for
my laptop?my laptop is fast with 2 Gb ram and its dell 1520 bought 2 months back.so i can assure its fast.



also with the default settings in firefox,i have found that it is way slower than a windows firefox next to my laptop.so i guess some changes have to be made...

---

### Post by vijayy on 2010-04-16
It's nice information...I check my speed test here [http://www.ip-details.com/](http://www.ip-details.com/)

---

