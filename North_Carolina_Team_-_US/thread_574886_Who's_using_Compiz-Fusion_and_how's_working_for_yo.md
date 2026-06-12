---
title: "Who's using Compiz-Fusion and how's working for you?"
date: 2007-10-13
forum: North Carolina Team - US
---

### Post by keithk on 2007-10-13
I've been using compiz fusion for 2 months now and it's been working great. The key for me was switching from an ATI card on my Ubuntu box to an Nvidia. Nvidia's  Linux support made it a breeze and I no longer have the headaches I had with Beryl and ATI. I'm also using Emerald Theme Manger with Compiz Fusion and haven't had a single issue. I'd like for some others to chime in with their experience. Thanks!

---

### Post by markthecarp on 2007-10-19
I switched to compiz-fusion about a month ago when I upgraded my test box to Gutsy. Previously I'd used Beryl. I apt-got removed beryl...and related prior to my upgrade. I left emerald alone.

I had to add two lines to my /e/X/xorg.conf to get compiz-fusion running on my hardware. I copied those lines from a backed up copy of /e/X/xorg.conf.

It's much better than my previous Beryl 3d desktop. 

I turned off FF's pop up blocker so I could kill popups and watch them go down in flames ;-)

-mark

---

### Post by keithk on 2007-10-19
Updated to Gutsy yesterday. Compiz and Emerald are working fine but I can't open Compiz Config Settings Manager. It's probably because of my previous install in Fiesty. I'd imagine the fix probably is one of those uninstall reinstall deals. But if anyone has a different fix for this let me know before I unleash some sort of mayhem upon my system.

---

### Post by markthecarp on 2007-10-20
Keithk,

Make sure you have the "compizconfig-settings-manager" package installed then the menu path should be "System > Preferences > Advanced Desktop Effects Settings". I had to remove the "gnome-compiz-manager" package.

-mark

---

### Post by Footer on 2007-10-20
> **markthecarp said:**
> Keithk,

Make sure you have the "compizconfig-settings-manager" package installed then the menu path should be "System > Preferences > Advanced Desktop Effects Settings". I had to remove the "gnome-compiz-manager" package.

-mark

Thanks Mark!  I just installed "compizconfig-settings-manager" package using Adept and now I can change all the compiz-fusion settings.  However, before I reinstalled Gutsy, I had a fusion-icon next to my clock.  I'd like that back for a one-click solution to bringing up the settings.  Any idea how to do that?

Thanks!

---

### Post by markthecarp on 2007-10-20
> **Footer said:**
> Thanks Mark!  I just installed "compizconfig-settings-manager" package using Adept and now I can change all the compiz-fusion settings.  However, before I reinstalled Gutsy, I had a fusion-icon next to my clock.  I'd like that back for a one-click solution to bringing up the settings.  Any idea how to do that?

Thanks!

Hum, I never had a fusion icon in the notification area; did have a beryl icon. One thing you can do is browse the menu to "System > Preferences" then right click on "Advanced Desktop Effects Settings"; that will bring up a dialog to add a launcher.

---

### Post by keithk on 2007-10-20
Mark thanks for the advice. I ended up removing settings manager and reinstalling and it worked so I'm back in biz

---

### Post by steveneddy on 2007-10-20
> **keithk said:**
> The key for me was switching from an ATI card on my Ubuntu box to an Nvidia. Nvidia's  Linux support made it a breeze

That is the key, I think, for a lot of people, that if you want/need this type of eye candy on your Linux Desktop, use nVidia products.

I have used Compiz before Quinnstorm wrote Beryl, so I am a long time user.

I like CF and use it on my gutsy 64 bit install.

Looks great and runs very well.

:popcorn:

---

### Post by Footer on 2007-10-20
> **markthecarp said:**
> Hum, I never had a fusion icon in the notification area; did have a beryl icon. One thing you can do is browse the menu to "System > Preferences" then right click on "Advanced Desktop Effects Settings"; that will bring up a dialog to add a launcher.

Yes, I had the beryl icon as well.  I've attached the fusion icon and a screenshot of what the icon I currently have looks like (when launching fusion-icon).  I do know you can go to the "Advanced Desktop Effects Settings" menu item to launch the settings but the fusion-icon is a little easier since it's sitting right there next to your clock!

---

### Post by markthecarp on 2007-10-22
> **Footer said:**
> Yes, I had the beryl icon as well.  I've attached the fusion icon and a screenshot of what the icon I currently have looks like (when launching fusion-icon).  I do know you can go to the "Advanced Desktop Effects Settings" menu item to launch the settings but the fusion-icon is a little easier since it's sitting right there next to your clock!

Ah, KDE; sorry I'm not much help with KDE. Hum, I wonder if it's a KDE package specific to compiz. That would explain my gnome system never having it (compiz-fusion icon).

That is a purrty icon ;-)

It is the NCLoCo forum.

-mark

---

### Post by Footer on 2007-10-23
Sorry to barge in on your forum but I found this subject while doing a search trying to get the compiz-fusion settings installed.

Anyway, I did fix the compiz-fusion icon thing.  The details are posted in a thread I started here:

[http://forum.compiz-fusion.org/showthread.php?t=4871](http://forum.compiz-fusion.org/showthread.php?t=4871)

Thanks!  :)

---

### Post by markthecarp on 2007-10-23
My apologies. I did not intend to be uninviting or rude; I intended a joke on some NC native's accents. For the last two days I've worked with a gentleman from Stokes County that has a _very strong accent.

Thanks for the heads up with the compiz-fusion linkage.

-mark

---

### Post by Footer on 2007-10-24
Ahh, I see!  I didn't take it that way to be honest.  But I did kind of jump in here.  It did help me to find the forum from my home state however:  MN.  How'd you guess I was from 'up north'.

:)

---

### Post by jfrorie on 2007-10-24
I was using Beryl under feisty with good results.  Some occasional issues after hibernate (HP zd8000 laptop).

After I switched to gusty and fusion, I was seeing artifacts, particularly with the screen savers.  I changed the driver to use the restricted ATI version and all has been well.

---

### Post by keithk on 2007-10-24
my own experience with an ati card and Beryl was awesome at first but then one magic day I updated from Dapper to Edgy and BOOM!!!!!! It was like hitting an IED with a HUMMVEE. Never got it to work with the ATI card again. popped in the Nvidia and presto good to go. That's not to say that you can't have a good compiz-ati experience it was just more labor intensive for myself.

---

### Post by keithk on 2007-10-24
I added a launcher using this icon from gnome-look

---

### Post by markthecarp on 2007-10-25
> **Footer said:**
> Ahh, I see!  I didn't take it that way to be honest.  But I did kind of jump in here.  It did help me to find the forum from my home state however:  MN.  How'd you guess I was from 'up north'.

:)

You're from "up north"! I had no idea. You don't write with an accent ;-)

MN and NC, don't we both have unique accents? I live about 30 miles south of the fictional town of Mayberry. Uhm, the town Mayberry was based on, Mt. Airy, NC. 

Neither the Andy Griffith Show or the Mary Tyler Moore Show give our fair states accurate representations.

-mark

---

### Post by melm2 on 2008-04-16
I never got Compiz-Fusion running correctly under Gutsy.  I decided to run the Hardy Beta and after adding in the programs all is working beautifully now.  I even got AWN to work which I'm still getting used to.  I've also never have figured out how to get the Icon to Stay after reboots.  I can get it to show during a session but logout or reboot and it goes away.  I'm just working on getting the cylinders stuff now.  It's all eye candy but so much sweeter that that other OS vendor.

---

### Post by Event_Horizon on 2008-04-20
I've had mixed experiences with compiz. When I first installed Gusty, I had many problems with Firefox locking up and OpenOffice just quiting which I attributed to Compiz (as these problems were not ever seen in Dapper, which was stable as a rock IMO), but now the stability issues seem to be mostly taken care of thanks to updates. Now compiz works MOST of the time; I say "most" because Firefox will still sometimes freeze up randomly when I try to open a link. Personally I think the Vista like fade away effects are really cool, but if it comes at the price of stability than I think it should be left out. Just my two cents.

---

### Post by jfrorie on 2008-04-25
> **melm2 said:**
> I never got Compiz-Fusion running correctly under Gutsy.  I decided to run the Hardy Beta and after adding in the programs all is working beautifully now.  I even got AWN to work which I'm still getting used to.  I've also never have figured out how to get the Icon to Stay after reboots.  I can get it to show during a session but logout or reboot and it goes away.  

Just add the command to System->Preferences->Session ( or maybe System->Administration->Session).  It should start after that.

---

### Post by UbuntuNerd on 2009-02-22
I love compiz so much I wrote some guides on it but I don't use it that much anymore, only when other people are around so I can see their faces drop to the floor.
check [HERE](http://my.opera.com/ubuntunerd1/blog/how-to-install-compiz-fusion-in-ubuntu-hardy) and [HERE](http://my.opera.com/ubuntunerd1/blog/how-to-use-compiz-settings-manager)

---

### Post by Jesus.9.04 on 2009-07-30
I recently switched to Ubuntu 9.04 and compiz is working just perfectly. Everything is much more simple than windows. I just have a question, I've seen videos that show compiz effects on the menu items? Does anyone know how to do that? 			  	Smilies 	 	 :KS   :popcorn:   :grin:   :eek:   :smile:

---

### Post by jfrorie on 2009-07-30
> **Jesus.9.04 said:**
> I recently switched to Ubuntu 9.04 and compiz is working just perfectly. Everything is much more simple than windows. I just have a question, I've seen videos that show compiz effects on the menu items? Does anyone know how to do that? 			  	Smilies 	 	 :KS   :popcorn:   :grin:   :eek:   :smile:


How do you mean?  Do you have a youtube example?

---

