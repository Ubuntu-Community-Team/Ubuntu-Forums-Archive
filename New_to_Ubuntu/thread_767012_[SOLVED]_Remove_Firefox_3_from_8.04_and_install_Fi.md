---
title: "[SOLVED] Remove Firefox 3 from 8.04 and install Firefox 2"
date: 2008-04-25
forum: New to Ubuntu
---

### Post by H.Callahan on 2008-04-25
How the heck do I get rid of Firefox 3 Beta from 8.04?  Nothing I do will really get rid of FF3.  I tried installing FF2, but it does not seem to work correctly when FF3 is installed (when I tried to add an extension that is not compatible with FF3 in FF2, it wouldn't install.  When I shut down FF2 and accidentally restarted FF3, the configuration box for the extension showed up and told me that it wasn't compatible with FF3).  I suspect that the two versions are using some common areas.

At any rate I want FF3 off until it is a released version.  When I use Add/Remove..., it tells me I can't uninstall it--that I have to use the Synaptic Package Manager.  When I remove it from there, it SAYS that it is removed, but it still appears under Applications and on the launch panel.  How do I REALLY, REALLY, REALLY, REALLY delete the %$^%*)&%^ thing?

---

### Post by mrazster on 2008-04-25
Try this:

1. Open synaptic and search for ***firefox***

2. Right klick and choose ***Mark for Complete Removal*** on the following packages: *_firefox, firefox-2, firefox-3.0, firefox-3.0-gnome-support, ubufox_*. Klick apply e.t.c for removal.

3. Open nautilus and tick */view/show hidden files*.

4. Then remove the *.mozilla* folder

5. Then in synaptic search for *firefox-2* and any other additional packages you might need and install.

If you are going to use mplayer and mozilla-mplayer plugin then it will automaticly install the package *firefox* and firefox-3.0. 
So my suggestion is to install any addons and plugins you need and lastly install mozilla-mplayer.
And then what ever you do, **DO NOT START FIREFOX-3.0**
Remove it from your start menu or what ever.

God luck

---

### Post by Gulyan on 2008-04-25
FF 3 is much better then 2 :KS

---

### Post by H.Callahan on 2008-04-25
Ok, I will give it a try.

Why is FF3 so hard to get rid of (and stay rid of)?  I think it is ridiculous to include a beta browser in what is supposedly a released version of Ubuntu.  I don't have anything against using beta software when I choose to do so, but I don't think it should be required of me, if I prefer a released version.  And it particularly should not hang on by teeth and nails when I try to remove it.

---

### Post by H.Callahan on 2008-04-25
> **Gulyan said:**
> FF 3 is much better then 2 :KS
It isn't if I can not load the add-ons that I want to use because they do not yet support FF3.  Also it is not, if I have problems in rendering pages that do not have problems rendering in FF2.

FF3 has POTENTIAL for being better than FF2, but right at the minute, **FOR ME**, it is not.

---

### Post by asgard_command on 2008-04-25
I'm sure Firefox 3 will be a great improvement when it is finished, but getting it removed was my first job with hardy. 
Hardly any of my extensions are ready for version 3 yet and I had major issues in Firefox 3, it crashed every time I clicked a link to a multimedia file such as mp3.
It took me a few attempts to get back to version 2 properly, eventually having to completely remove my profile and start from a fresh install.
Does seem a bit strange to have beta software in a supposedly super stable LTS release.

---

### Post by DerGeist on 2008-04-25
I upgraded and so far everything has be phenomenal except that Swiftfox/FF2 won't load my addons properly (it was working before the upgrade).

I took quite some time getting FF customized just the way I like it, and I really don't want to start all over from scratch...virtually everything is customized...isn't there a way to get rid of FF3 so my addons will work like before?

---

### Post by stchman on 2008-04-25
> **H.Callahan said:**
> How the heck do I get rid of Firefox 3 Beta from 8.04?  Nothing I do will really get rid of FF3.  I tried installing FF2, but it does not seem to work correctly when FF3 is installed (when I tried to add an extension that is not compatible with FF3 in FF2, it wouldn't install.  When I shut down FF2 and accidentally restarted FF3, the configuration box for the extension showed up and told me that it wasn't compatible with FF3).  I suspect that the two versions are using some common areas.

At any rate I want FF3 off until it is a released version.  When I use Add/Remove..., it tells me I can't uninstall it--that I have to use the Synaptic Package Manager.  When I remove it from there, it SAYS that it is removed, but it still appears under Applications and on the launch panel.  How do I REALLY, REALLY, REALLY, REALLY delete the %$^%*)&%^ thing?

First uninstall Firefox 3 completely.

```
sudo apt-get autoremove firefox-3.0
```

Then remove the residual config in Synaptic.  After that remove your ~/.mozilla folder but remember to save your bookmark.htm file before that.

Then install Firefox 2

```
sudo apt-get install firefox-2
```

That should do it.

---

### Post by FredB on 2008-04-25
> **asgard_command said:**
> I'm sure Firefox 3 will be a great improvement when it is finished, but getting it removed was my first job with hardy.

Big mistake...
 
> Hardly any of my extensions are ready for version 3 yet and I had major issues in Firefox 3, it crashed every time I clicked a link to a multimedia file such as mp3.

Extension coders will use RC1 - API are frozen at this time - to adapt their work.

> It took me a few attempts to get back to version 2 properly, eventually having to completely remove my profile and start from a fresh install.
Does seem a bit strange to have beta software in a supposedly super stable LTS release.

Just use your brain for 5 minutes. When Firefox 3 is released, firefox 2 will have only 6 more months to live. Let's say it will lose all technical support by next december. Kinda annoying for the next 2 years of support of Ubuntu Hardy...

---

### Post by H.Callahan on 2008-04-25
That seems to have done the trick.  Hopefully it will not pop back up on me again.

Thanks!

> **mrazster said:**
> Try this:

1. Open synaptic and search for ***firefox***

2. Right klick and choose ***Mark for Complete Removal*** on the following packages: *_firefox, firefox-2, firefox-3.0, firefox-3.0-gnome-support, ubufox_*. Klick apply e.t.c for removal.

3. Open nautilus and tick */view/show hidden files*.

4. Then remove the *.mozilla* folder

5. Then in synaptic search for *firefox-2* and any other additional packages you might need and install.

If you are going to use mplayer and mozilla-mplayer plugin then it will automaticly install the package *firefox* and firefox-3.0. 
So my suggestion is to install any addons and plugins you need and lastly install mozilla-mplayer.
And then what ever you do, **DO NOT START FIREFOX-3.0**
Remove it from your start menu or what ever.

God luck

---

### Post by Bubba64 on 2008-04-25
> **DerGeist said:**
> I upgraded and so far everything has be phenomenal except that Swiftfox/FF2 won't load my addons properly (it was working before the upgrade).

I took quite some time getting FF customized just the way I like it, and I really don't want to start all over from scratch...virtually everything is customized...isn't there a way to get rid of FF3 so my addons will work like before?

Nightly tester tools in Mozilla add ons will get the add ons working in FF3.

Personally I like FF 3 beta even before downloading Hardy I installed FF3 on gutsy also keeping FF2 and had no problems using either one, but that is my personal experience.

---

### Post by asgard_command on 2008-04-25
> **FredB said:**
> Big mistake...
 


Extension coders will use RC1 - API are frozen at this time - to adapt their work.



Just use your brain for 5 minutes. When Firefox 3 is released, firefox 2 will have only 6 more months to live. Let's say it will lose all technical support by next december. Kinda annoying for the next 2 years of support of Ubuntu Hardy...

I'm sorry I don't understand the 'Big Mistake'
A mistake to think Firefox 3 is going to be an improvement? It can't possibly be a mistake to remove something that isn't working for you.

Obviously Firefox 2 would have to be updated and it would be best to have version 3 at the release of a new Ubuntu version. Just seems to me that inexperienced users are going to be put off by software that isn't quite ready. I'd rather have a working browser now and update in a few months. My parents ran Gutsy for 6 months without a hitch but wouldn't have had a clue how to get Firefox back playing their media links and working the way it had. If I hadn't rolled it back to version 2 they wouldn't have stuck with Hardy then it becomes pretty irrelevant how many more months of support Firefox 2 has left.

My hiccup with Firefox did make me use Seamonkey for a day which I thought  was great seemed fast and simple, I may just give up my useful extension and start to use that.

---

### Post by Martin Aulbach on 2008-04-25
Personally I can't complain about FF3. The most important extensions for me, Adblock und Noscript, automagically installed without a glitch. Flash installed fine, too. :)

---

### Post by asgard_command on 2008-04-25
Some of my extensions worked and many that didn't were not at all essential. My favorite is Wizz which didn't work, keeps me so organized with my news feeds and podcasts would hate to be without it.

---

### Post by Bubba64 on 2008-04-25
If you imagine the developers putting together Hardy, it only makes sense that they would put out a browser with it that works for the most people. We have to remember that this and other forums are to find out how to fix a glitch in your system. So it looks as though more people are having problems than not,  this is called a correlation and not considered as an actual data analysis.

---

### Post by adwallum on 2008-04-25
I'm new so forgive me if I'm talking out of line here. Firefox 3 is much more stable than Firefox 2 for me. FF3 streams beautifully now especially the trickier sites like BBC news and iPlayer. I have no issues with Hardy and FF3 other than some sites (usually government ones) are so locked into MS that no version of FF works their forms correctly. 

If you look past the beta tag you might save yourself a headache. Good luck anyway and I hope you find a solution you can relax with.

---

### Post by asgard_command on 2008-04-26
> **adwallum said:**
> I'm new so forgive me if I'm talking out of line here. Firefox 3 is much more stable than Firefox 2 for me. FF3 streams beautifully now especially the trickier sites like BBC news and iPlayer. I have no issues with Hardy and FF3 other than some sites (usually government ones) are so locked into MS that no version of FF works their forms correctly. 

If you look past the beta tag you might save yourself a headache. Good luck anyway and I hope you find a solution you can relax with.

I don't think many are put of by the beta tag most will just try it for themselves. The only ones that might be put of would be ones like my parents but they wouldn't even understand what a beta is.

Incidentally I have fixed most of the issues I had with Firefox 3 on my desktop and it's running great on there now.

---

### Post by Freeper on 2008-05-03
Don't forget to changed preferred applications from firefox %s to firefox-2 %s otherwise it breaks things like deskbar's websearch.

---

### Post by Krieg on 2008-05-06
> **FredB said:**
> Big mistake...
 


Extension coders will use RC1 - API are frozen at this time - to adapt their work.



Just use your brain for 5 minutes. When Firefox 3 is released, firefox 2 will have only 6 more months to live. Let's say it will lose all technical support by next december. Kinda annoying for the next 2 years of support of Ubuntu Hardy...

Better YOU use YOUR brain.  Not everybody uses their PCs just to browse the net for fun and chat with the cyberfriends.   Some people can't afford to use beta/unfinished software.

Hardy has FF2 and if some people think it is better for their needs who are you to tell them you know better?

---

### Post by hman469 on 2008-05-07
> **FredB said:**
> Big mistake...
 
Just use your brain for 5 minutes. When Firefox 3 is released, firefox 2 will have only 6 more months to live. Let's say it will lose all technical support by next december. Kinda annoying for the next 2 years of support of Ubuntu Hardy...


Wont Ubuntu put out a new version in 6 months as well?

---

### Post by florinn on 2008-05-08
I solved the problem of having add-ons disabled in FF2 by removing extensions.cache extensions.log and extensions.rdf files from profile directory 
rm /home/_user_name_/.mozilla/firefox/_profile_name_/extensions.*

I accidentally started FF3 and the add-ons have been disabled in FF2 and I needed my session back and all the other settings for the add-ons, I could not delete profile directory.

---

### Post by kansasnoob on 2008-05-08
Mrazter has the procedure exactly right, but I've been trying FF3 beta every few days, and it has gotten much better, still not perfect ........ but I've been using it for 3 days on my "toy" and  NO crashes!

I'm not sure, but maybe the "complete" removal followed by a "complete" reinstall are necessary to bring in the most recent updates when available.

To those who are disappointed ................. did you try Vista the day it went on sale? Still to this day if you buy a Vista puter and want to downgrade to XP what does that cost? Gates sure doesn't just send you a free version of XP!

---

### Post by juje on 2008-05-09
hey! i've been having problems with both FF2 and 3...i gave a shot to the uninstall (both) and re install (only the third one) and now i can't even use it...i have no lanuchers (thats not a big problem, but's strange) and when i launch it thru the terminal it appears with out menus and without any function...any clue how to reinstall FF3 with all it's functionalities?

i've unisntalled it (both of them) and reinstalled it thru synaptic (also delete the .mozilla files in home folder, just to avoid previous profiles)

thankz

---

### Post by salefish on 2008-05-26
The question originally asked was how to remove Firefox 3 and install Firefox 2. The question was not do you agree with his decision, or whether you think he should do it. 
  I also need some extensions that are not ready for Firefox 3. I also have a job and a life that does not afford me the time to force them to work. The easiest solution is to install Firefox 2. Thanks again for the easy, no back talk, answer to the question.

---

### Post by ShadowSystems on 2008-05-27
To all that helped instruct us how to remove FF3 & install FF2, *Thank You*.
To those who resorted to name calling, shame on you.
FF3 may be an improvement over FF2, but the fact that it IS beta and that a LOT of the Plug-In's don't work with it, is a BIG deal-breaker for some of us.

The best way to handle it would have been to keep FF2 as the default browser.
Then *give the user the choice* of if THEY wanted to go to FF3 or not.
You tell them the pro's & con's of each version, & why you think it'd be a good idea to go with 3, but the fact that it doesn't work with FF2 PI's is a definite "needs to be disclosed" issue.

At this point, I'm going back to FF2 because there are too many PI's that I "have" to have.
The utility of NoScript + Remove It Permanently + GreaseMonkey is just too important in making my work day a productive one.
The fact that there are only SIX (6) FF3 compatible PI's out of the twenty I typically use, means FF3 isn't an option for me at the moment.
Once the PI writers have recoded their PI's to work under FF3, THEN I'll give it another look.

Until then, I downloaded a "stable" OS, I'd like a *stable* (not Beta) browser to go along with it.
=)

---

