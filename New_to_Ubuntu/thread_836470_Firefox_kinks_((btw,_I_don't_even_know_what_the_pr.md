---
title: "Firefox kinks? ((btw, I don't even know what the prefix thing means.. lo siento))"
date: 2008-06-21
forum: New to Ubuntu
---

### Post by cnzabel on 2008-06-21
Soo. I don't really know much about anything with computers. But here I am, using Hardy Heron. Huzzah, eh? So I'm going to try to explain this the best I can..

I just ..installed.. downloaded.. updated? Upgraded? I don't know. I went from one Firefox thingy to the new one. Firefox 3, I guess. And since that.. which was about a couple days ago.. Firefox has been doing some strange things.

1. The screen randomly goes grey.
2. Firefox randomly closes. With no message about crashing or anything. Just disappears.
3. I click on links, and they don't ..load? They just sit there and pretend like they're loading. The bottom of the page always says it's loading whatever, but they never load. And the little Stop Action red X button goes grey (so I can't click it..).
4. The ..bar at the top with the title of the page and the minimize, maximize and close buttons disappears sometimes. And then it won't let me type in the address bar.. So I can't get away from Firefox. :  \

I don't know if these are problems that my computer is having (I have only had Hardy Heron for about two weeks and have had a LOT of problems thus far), or if they're problems with certain websites, or if all people with Firefox 3 are experiencing these ..technical difficulties..

Perhaps my comp just hates Hardy Heron? Help? Does any one know what's going on?

---

### Post by seuzy13 on 2008-06-21
Have you tried reinstalling Firefox?

Go to System>Administration>Synaptic Package Manager.
Scroll down the list or do a search for firefox-3.0.
Right click it and select "mark for reinstall."
Click Apply and it should walk you through the rest.

Hopefully, this would take care of the problem. I have not heard of such a thing happening, so this is about all I can suggest. If you want to use Firefox 2 instead, you can go in synaptic and mark 3 for uninstall and 2 for install. I don't know if any of this will help, but I certainly hope so.

I understand what it's like to have a lot of problems, just push through it and post when you need help! :-)

By the way, the prefix is to let every one know what variant of ubuntu you have. There are several (xubuntu, kubuntu, edubuntu, ubuntu, etc.), and if you don't know which one you have it is probably ubuntu. Just look at the splash screen when your computer boots, and it should tell you.

---

### Post by Sarah L on 2008-06-21
I've had some difficulties with FF3 on Hardy, but they stemmed from running SCIM and the Flash plugin at the same time; not sure if this is your problem. But let's try to troubleshoot.

Have you installed any addons or plugins?
Try disabling any ones that you've installed.

Does this behavior only occur at certain sites?
If so, avoid those sites or view them with a different browser.

What sort of internet connection do you have?
If your connection is unreliable, websites might fail to load.

Have you installed some sort of window manager decoration (such as compiz-fusion)?
That might sometimes interfere with the appearance of your windows (such as getting rid of the borders so you can't close them anymore)

If you still haven't found the problem, then reinstall firefox. Maybe try deleting the package and installing firefox 2.0.

If none of these are the case, I suggest that you try an alternate browser, such as Opera (you can download an Ubuntu package from their webpage) or Konqueror (you can install that through aptitude: sudo apt-get install konqueror). You might even want to try Internet Explorer through Wine!

Hope you can get your browser working!
-Sarah

---

### Post by cnzabel on 2008-06-21
> **Sarah L said:**
> I've had some difficulties with FF3 on Hardy, but they stemmed from running SCIM and the Flash plugin at the same time; not sure if this is your problem. But let's try to troubleshoot.

Have you installed any addons or plugins?
Try disabling any ones that you've installed.

Does this behavior only occur at certain sites?
If so, avoid those sites or view them with a different browser.

What sort of internet connection do you have?
If your connection is unreliable, websites might fail to load.

Have you installed some sort of window manager decoration (such as compiz-fusion)?
That might sometimes interfere with the appearance of your windows (such as getting rid of the borders so you can't close them anymore)

If you still haven't found the problem, then reinstall firefox. Maybe try deleting the package and installing firefox 2.0.

If none of these are the case, I suggest that you try an alternate browser, such as Opera (you can download an Ubuntu package from their webpage) or Konqueror (you can install that through aptitude: sudo apt-get install konqueror). You might even want to try Internet Explorer through Wine!

Hope you can get your browser working!
-Sarah

I have the official Sun Java and flash plugins. And ..Adblock Plus, a couple language dictionaries, Download them all.. and stuff.

The title ..bar thing doesn't disappear anymore. I think it must've just been that website? I don't know.. And the link thing mostly screws up on Facebook, but that's really the only website I use with lots of link clicking.

I have a pretty reliable wireless connection--that is, nothing else seems to have problems with ..the internet.

I'm just using the default window decorations with extra effects.

I will just try reinstalling Firefox, je suppose. But thanks for the help. I appreciate it.

---

### Post by acidsolution on 2008-06-21
Try disabling your addons because some addons installed for firefox 2 may not be compatible with firefox 3.0

---

