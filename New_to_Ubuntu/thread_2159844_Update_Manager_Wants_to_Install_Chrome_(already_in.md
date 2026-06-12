---
title: "Update Manager Wants to Install Chrome (already installed) Constantly"
date: 2013-07-04
forum: New to Ubuntu
---

### Post by Wadcutter on 2013-07-04
[Solved] I just recently caught on that my Update Manger lists a suggested 43.2 MB installation of Chrome every time ( or almost) it runs. But I already have Chrome installed and I use it occasionally. I have a hard time believing that Google is updating their browser once or twice per week. I realize I can uncheck it to run in Update, but it made me wonder if to do so I would be missing some security update. Now today, it has decided that I should install Mozilla Firefox (again) for another 26.7 MB and Opera for 13+ MB more. All of these browsers cannot be issuing updates on a daily basis. What is going on with Update mgr? Cut out the browser updates and everything else loads in about 3 minutes.

I'm running Ubuntu 12.04 on a desktop and have all 3 browsers installed but use FF about 95% of the time, Chrome 5% and Opera almost never although 6 months ago it was my default browser.

---

### Post by JKyleOKC on 2013-07-04
Firefox did have an update, to version 22, today; I don't know about the other two. However it's probable that there's been an update sometime since you installed or last updated those other browsers, and you have unchecked it before installing other updates. The Update Manager will keep reminding you until you DO install it -- unlike Windows Update on XP, which lets me choose to ignore an unchecked update if I so desire.

The Firefox update replaces the previous version, so it doesn't increase your disk usage. They update approximately once a month, and will be doing it again on August 6 according to a schedule I saw...

EDIT: If you install the Synaptic package manager (available in the Software Center) and set it to show "installed" packages only, it will show you the version you have installed, and the current version, for every software package on your system that was installed via the package managers (including Update Manager). You can use this feature to determine whether you actually have the version that's triggering the notification.

---

### Post by Dennis N on 2013-07-04
Update manager will not propose the same version as you have installed. Use the "technical description" dropdown to see the difference in version. See attachment for an example.

---

### Post by craig10x on 2013-07-04
I use Google Chrome very actively (it's my main used browser on ubuntu) and what it is is that Google added a PPA updater to the software sources in your software updater so that each time a new version is released you get it in your updates and you should allow it to be installed....i doubt if you are getting it twice every week but Chrome does often make very frequent release...not new versions so quick but updated versions with either bug fixes or security updates....It just so happens they did send 2 new updated versions within the last week....

That doesn't happen that fast all the time... but it CAN....so don't think it's just trying to re-install the same one again...and it's REPLACING the one you got on there now with the newer one...it isn't installing another one separately...

You can see for yourself....Just look in "about chrome" in the system settings and just write down the version that's installed...let us say it is 28.100.17 (just a made up number) well, after the updater installs the new version , check it again and then you might see, say 28.100.35 (also made up)...that would have either bug fixes, security updates or both...

Get the picture? :D

---

### Post by su:bhatta on 2013-07-04
Thanks wadcutter for posting this thread, I was also using Chrome and got 3 updates in a week. I didn't like it and thought something fishy was going on and uninstalled it. Now within the last 2 weeks I got 2 firefox updates, which is now my only browser, and had to install both times... 

Wonder if Chromium is more, if i may use the term, stable. I have got a ISP plan where my Download speed drops after 6GB download and i dont wanna install so much Chrome/firefox and add to my download gigs...
I will keep a lookout at your post to find out more...

---

### Post by Cheesehead on 2013-07-04
> **Wadcutter said:**
> Update Manger lists a suggested 43.2 MB installation of Chrome every time ( or almost) it runs. But I already have Chrome installed and I use it occasionally.

You misunderstand. It's recommending an **update** to Chrome. Updating means removing the old package and downloading and installing the new.

> **Wadcutter said:**
>  I have a hard time believing that Google is updating their browser once or twice per week. I realize I can uncheck it to run in Update, but it made me wonder if to do so I would be missing some security update.

Update Manager naturally assumes that you want to run the latest stable and secure version. You should let Update Manager install **everything** unless you are on a slow or expensive connection. It does **not** remember an uncheck, and will continue to offer you the same updated version that you previously refused.

If you are using PPAs or want to pin versions or do by-package updates or otherwise make your system needlessly complicated, then you should use Synaptic instead of Update Manager.


Yeah, if you have three big-binary browsers installed, and each send out a security update or two each month, then you will indeed get a lot of big-download updates. The behaviour you describe seems normal for the setup you describe.

---

### Post by craig10x on 2013-07-04
Exactly...what you should do is re-check it....let it update your current version which will give you the latest...there was 2 new updates for it this past week but that is not something i have seen every week...
With Firefox you are depending on Canonical to update you which can be a slower process....Google is more "on the ball" with this things and updates promptly when there is a new release...

Also, Chrome is transitioning to the new "blink" engine from webkit so perhaps that might generate a little more frequent updated versions too...don't know why you guys are making such a fuss about it...Chrome is not unstable (unless you run the testing unstable channel) in fact, if anything Chrome is MORE stable then chromium because they do refinements on the Chromium packages before they make their releases...
Just let the darn thing update...

One thing that irks me a bit since getting involved with Linux is that i seem to run across a lot of unnecessary paranoia about certain things...windows and mac users of Chrome are getting the same updates on this...you can relax...

---

### Post by vasa1 on 2013-07-04
@craig10x, I think what gets some people worried is the download sizes. In Windows, unless there's been some major change, updates for Firefox and Chrome are differential. In other words, they're not the size of a clean install. In Linux, each conventional update of Firefox or Chrome (and most other software) isn't differential. So it's like doing a fresh install with each update.

Some people don't have access to reliable or cheap internet. And keeping Linux and it's software updated can prove pretty heavy for such people. Even I held off installing Linux until I could get a suitable internet plan ;)

---

### Post by Cheesehead on 2013-07-05
> **vasa1 said:**
> Some people don't have access to reliable or cheap internet. And keeping Linux and it's software updated can prove pretty heavy for such people. Even I held off installing Linux until I could get a suitable internet plan ;)

Great point. And there are several other ways to address that problem.
For example, a user can delay non-security updates in Software Sources (software-properties-gtk)
Or reduce the frequency of update checks.
Alternately, a user can significantly reduce update volume by uninstalling unused or rarely-used applications.
Alternately, some users use cron to update during low-cost hours.
Alternately, some users use Upstart to update when they connect to low-cost networks.
There are many flexible solutions.

There is no reason Ubuntu cannot use delta-based binary updates. Quite a bit of work by Canonical was done back in 2010-2011, if I recall correctly. But the developers abandoned that project before release, and nobody has been interested enough to pick it up since.

---

### Post by vasa1 on 2013-07-05
> **Cheesehead said:**
> ... And there are several other ways to address that problem.
....
@Cheesehead, could you point to a resource where the more technical tips are laid out in detail? It would be of great use. I'm pretty sure that bandwidth limitation is one factor holding back the spread of Linux (desktop), at least where I come from.

My compromise has been to go for an unlimited plan but with pathetic speed ... which is one reason why I stay away from "Ubuntu+1 testing".

---

### Post by su:bhatta on 2013-07-05
That was my point too... I hav a unlimited plan but after a certain download size the download speed craps up... getting things deffered is not a solution is it? Sooner or later I have to get that 26 odd mb downloaded.... right!

and vasa, yes internet ain't cheap from where we come from;)

Thats y i hav been on & off Ubuntu(which i like very much, thank u) from 2010,  finally made the plunge this May !

---

### Post by Cheesehead on 2013-07-05
> **vasa1 said:**
> @Cheesehead, could you point to a resource where the more technical tips are laid out in detail? It would be of great use.

First the user must decide how they want to balance. More applications? More frequent updates?
Obviously, you already know this stuff.

I usually send users with these issues to Software Sources (software-properties-gtk).
Change the 'Updates' tab settings to something more realistic for their needs.

For example, most users (unlike you) are more interested in stability and simplicity, and less interested in the bleeding edge. If they don't understand -updates, -proposed, and -backports, then I tell them they can safely uncheck them. If they find Update Manager to be stressful, then they can turn off the update display ("when there are other updates") while keeping security updates in the background.

Obviously, you are a more technical sort, so I would point you more toward Synaptic and per-package control of updates.

---

### Post by slickymaster on 2013-07-05
> **craig10x said:**
> I use Google Chrome very actively (it's my main used browser on ubuntu) and what it is is that Google added a PPA updater to the software sources in your software updater so that each time a new version is released you get it in your updates and you should allow it to be installed....i doubt if you are getting it twice every week but Chrome does often make very frequent release...not new versions so quick but updated versions with either bug fixes or security updates....It just so happens they did send 2 new updated versions within the last week....

That doesn't happen that fast all the time... but it CAN....so don't think it's just trying to re-install the same one again...and it's REPLACING the one you got on there now with the newer one...it isn't installing another one separately...

You can see for yourself....Just look in "about chrome" in the system settings and just write down the version that's installed...let us say it is 28.100.17 (just a made up number) well, after the updater installs the new version , check it again and then you might see, say 28.100.35 (also made up)...that would have either bug fixes, security updates or both...

Get the picture? :D

Can speak for FF and Opera, but in what Chrome is concerned, craig10x's explanation is absolutely correct and accurate.

---

### Post by Wadcutter on 2013-07-05
What a bunch of great answers to my concern! I appreciate the info. I probably could have figured it out by looking for version numbers, but I was certain someone else would have a ready answer if I asked. I do have rather slow internet, so I don't want to be downloading 43.2 MB of updates if not necessary.  Thanks again.

---

