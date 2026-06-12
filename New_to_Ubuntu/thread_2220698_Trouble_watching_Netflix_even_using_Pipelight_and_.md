---
title: "Trouble watching Netflix even using Pipelight and User Agent Switcher"
date: 2014-04-29
forum: New to Ubuntu
---

### Post by LizzyJean on 2014-04-29
Okay.  I finally actually installed Ubuntu 14.04 alongside XP on my laptop yesterday. It's bumpier than I expected (the real install of Ubuntu is different from the test version), but I'm working through it.

Tonight I learned that Netflix Instant Movies blocks Linux systems.  (Aaargh!)  I installed Pipeplight to run Silverlight (the plugin that Netflix uses to stream media) [using these instructions]("http://www.makeuseof.com/tag/easily-enable-silverlight-watch-netflix-linux/") and then realized that I *also* needed to trick Netflix into thinking that I was running Windows, using an Add-On for firefox called User Agent Switcher.  So I got the addon and [imported profiles]("http://www.ghacks.net/2009/04/10/extend-firefoxs-user-agent-switcher/") for Windows versions of Firefox into the addon.  (Phfew!)

This got me past Netflix's page telling me that I had the wrong system.  But now I get an error code when i try to play a movie.  I tried all six Windows-Firefox profiles, but they all fail.

Any sugestions of how to more reliably work around Netflix's barrier?

---

### Post by monkeybrain20122 on 2014-04-29
The user agent switcher addon apparently never works on netflix. Get the user agent overrider addon and set it to Firefox/Windows, that should work. But don't set it to IE as netflix will then look for ActiveX and won't play without finding it.

---

### Post by LizzyJean on 2014-04-29
> **monkeybrain20122 said:**
> The user agent switcher addon apparently never works on netflix. Get the user agent overrider addon and set it to Firefox/Windows, that should work. But don't set it to IE as netflix will then look for ActiveX and won't play without finding it.

This worked perfectly!  Thanks for your help :)

---

### Post by migs73 on 2014-04-29
And if you use Chrome try the 'Chrome UA Spoofer' works for me on Amazon and BT Sport with Pipelight.

Also could please mark the thread as 'Solved' (got tot he top of the thread and click on the thread tool menu and select 'Mark as Solved'.

Cheers

Mike :)

---

### Post by monkeybrain20122 on 2014-04-29
> **migs73 said:**
> And if you use Chrome try the 'Chrome UA Spoofer' works for me on Amazon and BT Sport with Pipelight.

Also could please mark the thread as 'Solved' (got tot he top of the thread and click on the thread tool menu and select 'Mark as Solved'.

Cheers

Mike :)

Forget about Chrome. Pipelight will stop working on Chrome comes Chrome 35 in May as google has dropped support for all NPAPI plugins including pipelight (and all media plugins)

Chromium may work if it is built with certain patches.
[https://answers.launchpad.net/pipelight/+question/247081](https://answers.launchpad.net/pipelight/+question/247081)

---

### Post by migs73 on 2014-04-30
I'll bear that in mind thanks.

---

### Post by LizzyJean on 2014-05-09
> **migs73 said:**
> Also could please mark the thread as 'Solved' (got tot he top of the thread and click on the thread tool menu and select 'Mark as Solved'.:)

Thanks for that tip, Mike.  But now I'm adding another question to this (hope that's okay).  Can I safely use User Agent Overrider to log into a website where I pay a bill?  It says it doesn't support linux.  Here's the site:  [https://secure.anchorgeneral.com/AGLogin.aspx?M=0&PageType=4](https://secure.anchorgeneral.com/AGLogin.aspx?M=0&PageType=4)

Thanks!

---

### Post by monkeybrain20122 on 2014-05-09
user agent overrider doesn't seem to work, I still got Linux not supported when I turned on uao, but a fast google search shows a few links that basically say it is a horrible company bordering on fraud, maybe that is a good enough reason to consider stop dealing with them if not for the lack of  Linux support. :)

---

### Post by LizzyJean on 2014-05-09
> **monkeybrain20122 said:**
> user agent overrider doesn't seem to work, I still got Linux not supported when I turned on uao, but a fast google search shows a few links that basically say it is a horrible company bordering on fraud, maybe that is a good enough reason to consider stop dealing with them if not for the lack of  Linux support. :)

yeah. that totally corroborates my own experience.  maybe this will be the final straw.;)

---

### Post by SeijiSensei on 2014-05-10
I'm using [UAControl]("https://addons.mozilla.org/en-us/firefox/addon/uacontrol/") and just ran Netflix via pipelight.  This one lets you specify user-agent strings by domain.  For netflix.com I'm using:
```
Mozilla/5.0 (Windows NT 6.1; rv:29.0) Gecko/20131011 Firefox/29.0
```

---

### Post by Habitual on 2014-05-10
Fri May 09, 2014 -  4:17:17 PM EDT

User Agent Switcher 0.7.3 for Firefox is useless or broken on Firefox 17.0.11
so I switched to User Agent Overrider 0.22.3 using the agent string of
# Netflix
NetFlix / Firefox 15: Mozilla/5.0 (Windows NT 6.1; WOW64; rv:15.0) Gecko/20120427 Firefox/15.0a1

NOTE: You MUST disable and re-enable the addon after editing Preferences as the drop-down list gets weird.

---

### Post by monkeybrain20122 on 2014-05-10
> **Habitual said:**
> Fri May 09, 2014 -  4:17:17 PM EDT

User Agent Switcher 0.7.3 for Firefox is useless or broken on Firefox 17.0.11
so I switched to User Agent Overrider 0.22.3 using the agent string of
# Netflix
NetFlix / Firefox 15: Mozilla/5.0 (Windows NT 6.1; WOW64; rv:15.0) Gecko/20120427 Firefox/15.0a1

NOTE: You MUST disable and re-enable the addon after editing Preferences as the drop-down list gets weird.

The netflix problem is already solved. :) Now OP wants to know if there is a way tp access [https://secure.anchorgeneral.com/AGLogin.aspx?M=0&PageType=4](https://secure.anchorgeneral.com/AGLogin.aspx?M=0&PageType=4) with a user agent switcher like addon.

---

### Post by Habitual on 2014-05-11
> **monkeybrain20122 said:**
> The netflix problem is already solved. :) Now OP wants to know if there is a way tp access [https://secure.anchorgeneral.com/AGLogin.aspx?M=0&PageType=4](https://secure.anchorgeneral.com/AGLogin.aspx?M=0&PageType=4) with a user agent switcher like addon.

Without an account there, **we** will never know.

Have a good day.

---

