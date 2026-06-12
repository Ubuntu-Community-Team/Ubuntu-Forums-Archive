---
title: "Cookies, how to delete ?"
date: 2020-11-10
forum: New to Ubuntu
---

### Post by Innernet on 2020-11-10
Greetings.

I would like to have ALL the cookies deleted after exiting a web site that forces or not to accept them in order to visit such site.

What command will list the cookies currently stored; to confirm they do got deleted since last time ?
This is only to confirm or not the slowing down of the browser or system obeys to a overdose of cookies.
Your guidance worded for a beginner, please ?

I see I can select at Settings ---> Privacy ---> Temporary files ---> Purge now / every xx days.   Are cookies considered temporary files ?

---

### Post by TheFu on 2020-11-10
Cookies are controlled by the web browser.
Or
You can just wipe the profile directory after every use.
Or
You can run the browser inside a light sandbox tool like **firejail** in a mode that doesn't let the browser see or safe anything.  Each run of the browser under firejail in "private" mode will seem like the very first time the browser was ever run.

There are some other techniques too.

Honestly, first-party cookies aren't all that big a problem.  Most browsers can block 3rd party cookies, which you should configure. There are "local objects" from HTML5 and Flash that are worse for tracking and there are other ways we can be tracked using normal javascript.  I'm most afraid of Javascript when it comes to my privacy.
[https://panopticlick.eff.org/](https://panopticlick.eff.org/) is a tester from the EFF for how much you can be tracked.

---

### Post by Innernet on 2020-11-10
Thank you.
_Am not concerned at all about being tracked or to reveal some personal preferences or data_. Most cookies seem not hazardous, can live with them.
Am after finding **what**, if cookies slow down the browser.

Recently am not turning power off the laptop between sessions but put to sleep.  In few days everything slowly chokes to crawling speed.  Turning power off between sessions restores speed.  Closing Firefox and using Opera equally restores speed.  When happens under Opera, closing it and opening Firefox also restores speed.

I just want to know **what **clogs the browser/system, if it is cookies or is it something else.

If cookies become the choking suspect; then will ask for proper action to periodically**_ truly _**delete them.  If cookies presence do not choke the browser; will ask for some other kind of hunting.

Seems every web site now wants to control user equipment.  Starting with Google - which I rarely use now.

---

### Post by TheFu on 2020-11-10
I can't see any reason why cookies would slow anything down. It isn't the cookie. It is the extra code and javascript that is run based on the state of selected cookies which can cause problems.  There are many more ways too.  

In general, addons are the worse way to slow down a browser.

If you are a software developer, we can go much deeper, but if you aren't, that background knowledge would greatly help with understanding.

---

### Post by ActionParsnip on 2020-11-11
If you make a folder in /tmp at boot and make a folder for your browser cache in that folder you can then symlink cache the folder in your user's home to this folder. When you reboot the data is lost as it resides in tempfs. I used to do this with Google Chrome. It also slightly speeds up your Web access as the cache is in RAM rather than the slower permanent storage.
I did this because I had a small 4Gb SSD and wanted to save space. Great days

---

### Post by TheFu on 2020-11-11
```
$ cd /tmp/
$ df .
Filesystem                  Size  Used Avail Use% Mounted on
/dev/mapper/hadar--vg-root   22G   16G  5.4G  75% /
```
/tmp isn't always in RAM.  You can make it that way, if you like.

Also, waiting until reboot could be problematic for some people.
```
$ uptime 
 17:37:26 up 11 days, 14:29,
$ uptime
 17:37:38 up 13 days,  4:23,
$ uptime 
 17:37:55 up 11 days,  7:00,
```

But if you shutdown your browser daily, there are browser settings to delete all local objects, including cookies, daily.
But Cookies have very little to do with browser performance.  Javascript and the fact that 40% of the web is advertising matters much more. Judicious use of NoScript and a Pi-Hole DNS blocker would help much more.  OTOH, both of those techniques also can break some websites to the point of being unusable.  It is for this reason I have multiple browsers that run in different environments, based on the believed risks involved.  That doesn't help Grandma, since anything too complex just isn't high on her priority list (thank god!).  I'd much rather have grandma worrying about the things that matter most to her than how to safely use a computer for speed or privacy.

---

