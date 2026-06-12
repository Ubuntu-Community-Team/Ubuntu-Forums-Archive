---
title: "Nasty little mouse icon set - Yuk!"
date: 2011-07-24
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by coffeecat on 2011-07-24
That's nasty little icons, not a nasty little mouse! :)

I've got this from both today's daily live and daily alternate installed to separate partitions on the same machine. They've defaulted to an ugly, nasty mouse cursor set that I haven't seen for some time. I think it's failed to use the usual whiteglass cursor theme. The ordinary pointer is black, the hand icon when you hover over a hyperlink is the ancient pointing-to-the-left one, but worst is the "wait" cursor. Instead of a swirly thing I'm getting the old static wristwatch icon which I've always disliked with a passion. Sorry that I haven't been able to post a screenshot - the cursors don't appear in screenshots for some reason.

I've just updated my older laptop Oneiric and the mouse cursors are still fine, so it must be some issue in today's daily builds. Anyone else seeing this? More to the point - how do I get the regular whiteglass set? I've forgotten how to do it from config files, and setting cursor themes doesn't seem to have made its way into System Settings yet.

Also - alt+ctrl+T doesn't work to open a terminal in either of the installs from today's dailies.

---

### Post by MacUntu on 2011-07-24
Ctrl+Alt shortcuts don't seem to work at all.

---

### Post by lucazade on 2011-07-24
about mouse cursor check if dmz-cursor-theme is installed and DMZ-White is selected as mouse pointer in gnome-tweak-tool or via dconf-editor.

---

### Post by coffeecat on 2011-07-24
> **lucazade said:**
> about mouse cursor check if dmz-cursor-theme is installed and DMZ-White is selected as mouse pointer in gnome-tweak-tool or via dconf-editor.

Spot on! dmz-cursor-theme was not installed (and this in a fresh installation from today's daily-live). I installed it and then installed gnome-tweak-tool which immediately told me that DMZ-White was set as the icon theme even though it wasn't showing. Logged out and in again and mouse cursors are now as they should be.

My guess about whiteglass was wrong. It was DMZ-White that I needed - thanks. I guess the dmz-cursor-theme has mistakenly been omitted from the daily image. I hope this is not a deliberate decision, because those other cursors are quite ghastly, and have no style at all.

---

### Post by ranch hand on 2011-07-24
That is probably being slapped in from Debian Sid as the devs are busy with other things.  That is exactly what you are getting now under Sid.   I have some other cursors that all seem to work fine but I am getting the wristwatch from before the login screen up to the desktop.

New installs are exactly as you describe.  Really ugly.

---

### Post by mc4man on 2011-07-24
> Also - alt+ctrl+T doesn't work to open a terminal in either of the installs from today's dailies. 
The gnome capability plugin isn't enabled by default anymore - you can just create a binding in settings > keyboard and if desired use Ctrl+Alt+T
(working here after creating on todays iso

Edit: meant to say the binding isn't enabled in the plugin (or non-functional if it is

---

### Post by coffeecat on 2011-07-24
Aha! It was useful that I did two side-by-side installs, the one from the daily-live, the other from the daily-alternate. Rebooted into the install from today's alternate ISO, which is absolutely fresh - nothing added, no tweaks, no updates. Installed the package dmz-cursor-theme only, logged out and in again and cursors are back to what they should be. I guess therefore it really is a simple package omission and without it the system is defaulting to something that looks as if it belongs in 1981 - or is that 1781? :?

Actually, I couldn't log out and in again - not from the System button. I just get a purple screen. I had to use AltGr+PrtScr+k to kill the xserver and get to the login screen.

And the restart option has disappeared from the system menu. Suspend, hibernate and shutdown, but no restart. Have to use sudo reboot in the terminal which I can't start with ctrl-alt-T.

Happy days! :)

**EDIT**: just saw mc4man's post about ctrl-alt-T. I'll try that.

---

### Post by coffeecat on 2011-07-25
Package dmz-cursor-theme missing from today's (25th July) daily-live as well according to the manifest. I've opened a bug:

[https://bugs.launchpad.net/ubuntu/+source/dmz-cursor-theme/+bug/815555](https://bugs.launchpad.net/ubuntu/+source/dmz-cursor-theme/+bug/815555)

Could I trouble people to do me-toos? Also, I'd like to research when the package went awol so that I can add that to the bug report. Does anyone have a link to where I can find all the earlier dailies, hopefully with their manifest files? I would hope they are archived rather than just being deleted.

---

### Post by dino99 on 2011-07-25
only found that one:

[http://cdimage.ubuntu.com/daily-live/](http://cdimage.ubuntu.com/daily-live/)

---

### Post by lucazade on 2011-07-25
added me-too to bug report, I had the same issue with latest daily-images.

about old manifests file I wasn't able to find them before 24 July.. also using google cache or waybackmachine. no idea.

---

### Post by coffeecat on 2011-07-25
Thanks for the me-toos.

> **lucazade said:**
> about old manifests file I wasn't able to find them before 24 July.. also using google cache or waybackmachine. no idea.

Did a bit more googling - still can't find any either. But I checked the manifest on the alpha 2 amd-64 image. Package dmz-cursor-theme is included in alpha2 as I suspected, so it must have dropped out sometime between early July and yesterday.

---

### Post by mc4man on 2011-07-25
Started noticing last week on live sessions, maybe mid week
(07/17 was good, that was my previous install till redoing yesterday

---

### Post by coffeecat on 2011-08-01
Is it just me that's the kiss of death to launchpad bugs? :(

[https://bugs.launchpad.net/ubuntu/+source/dmz-cursor-theme/+bug/815555](https://bugs.launchpad.net/ubuntu/+source/dmz-cursor-theme/+bug/815555)

Confirmed but unassigned. And dmz-cursor-theme still missing from dailies as of 31st July build.

---

### Post by kansasnoob on 2011-08-01
> **coffeecat said:**
> Is it just me that's the kiss of death to launchpad bugs? :(

[https://bugs.launchpad.net/ubuntu/+source/dmz-cursor-theme/+bug/815555](https://bugs.launchpad.net/ubuntu/+source/dmz-cursor-theme/+bug/815555)

Confirmed but unassigned. And dmz-cursor-theme still missing from dailies as of 31st July build.

While performing Alpha3 iso-testing I'll try to report that using your bug report, unless it's been fixed by then. That should get us an answer.

BTW that looks like the standard Lubuntu cursor theme (or darn close) and I always change that almost immediately :)

---

### Post by kansasnoob on 2011-08-02
I reported that so hopefully we'll know soon if this is the new normal ............. I hope not.

---

### Post by coffeecat on 2011-08-02
Thanks kansasnoob.

It's still missing from today's (2nd August) dailies. I see that the feature freeze is on 15th August, so there won't be much time to include this in the ISO before then.

I really, really, really hope this mouse cursor set is not intended as the default for Oneiric. If it is, it would make a mockery of the design team's efforts to make Unity elegant. It truly is an abomination. (The mouse cursor set, that is. :))

---

### Post by lucazade on 2011-08-02
> **coffeecat said:**
> Thanks kansasnoob.

It's still missing from today's (2nd August) dailies. I see that the feature freeze is on 15th August, so there won't be much time to include this in the ISO before then.

I really, really, really hope this mouse cursor set is not intended as the default for Oneiric. If it is, it would make a mockery of the design team's efforts to make Unity elegant. It truly is an abomination. (The mouse cursor set, that is. :))

it is not inteded to be default, you can bet on it.
anyway still present also on latest daily iso image.

---

### Post by G0B1!N on 2011-08-03
I went and manually installed the package but I noticed that the DMZ cursor only appears when i'm in applications like firefox. Is this supposed to happen? :/

---

### Post by coffeecat on 2011-08-03
I don't think so. When I installed the package dmz-cursor-theme I got the proper cursor set for the whole desktop. I get the swirly thing as should be when Synaptic is doing a recalculation.

---

### Post by coffeecat on 2011-08-16
Breaking news!

Fix committed:

[https://bugs.launchpad.net/ubuntu/+source/ubuntu-meta/+bug/815555](https://bugs.launchpad.net/ubuntu/+source/ubuntu-meta/+bug/815555)

More breaking news!

Package dmz-cursor-theme has been included in the 16th August live dailies.

Even more breaking news!

As this is the first time any notice has ever been taken of anything I've posted in a bug report, you're all invited round to my place for a glass of champagne. :wink:

Don't forget to wipe your shoes on your way in!

---

### Post by lucazade on 2011-08-16
> **coffeecat said:**
> Breaking news!

Fix committed:

[https://bugs.launchpad.net/ubuntu/+source/ubuntu-meta/+bug/815555](https://bugs.launchpad.net/ubuntu/+source/ubuntu-meta/+bug/815555)

More breaking news!

Package dmz-cursor-theme has been included in the 16th August live dailies.

Even more breaking news!

As this is the first time any notice has ever been taken of anything I've posted in a bug report, you're all invited round to my place for a glass of champagne. :wink:

Don't forget to wipe your shoes on your way in!

LOL!
thanks for heads up.

---

