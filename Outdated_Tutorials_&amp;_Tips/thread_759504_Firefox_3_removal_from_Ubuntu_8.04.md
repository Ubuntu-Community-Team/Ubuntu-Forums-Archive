---
title: "Firefox 3 removal from Ubuntu 8.04"
date: 2008-04-19
forum: Outdated Tutorials &amp; Tips
---

### Post by gn2 on 2008-04-19
**15 June 08 EDIT: This thread largely irrelevant now, as most FF add-ons updated and now working OK with FF3** 

If like me you have Firefox extensions that will not work with Firefox 3 Beta4, or you simply don't like FF3 you can replace it with Firefox 2.

First close any Firefox windows then open Synaptic and search for firefox.

Mark firefox-3.0 for complete removal and click apply.

Then in your Home folder, locate the hidden .mozilla folder.
(either by pressing Ctrl+h or View>Show Hidden Files)
Inside the .mozilla folder is the firefox folder.
Move the firefox folder to the trash, then empty the trash..

Next search Synaptic again for firefox and click on the firefox-3.0 line to highlight it, then in the top menu bar click "Package" then select "Lock Version"
This will prevent Firefox 3 from being re-installed.
**EDIT:** *Also completely remove then lock all the other firefox-3 entries and the firefox (metapackage) there are reports that Firefox 3 can reappear unless all the firefox-3 entries are removed and locked.*


Next, check that the /home/<username>/.mozilla/firefox folder is still deleted.

Search again for firefox in Synaptic then mark firefox-2 for installation and click apply.

You will now be able to use a much wider range of add-ons and your Home button won't be in the Bookmarks Toolbar. Why was it moved there? Grrr!
EDIT: Home button now back in it's rightful place with Beta5

---

### Post by fedex1993 on 2008-04-19
funny thing is that there is a plugin that you can run firefox 2 plugins with firefox 3 also you can just install firefox 2 and use that instead of firefox 3 b 5

---

### Post by gn2 on 2008-04-19
> **fedex1993 said:**
> funny thing is that there is a plugin that you can run firefox 2 plugins with firefox 3 

You wouldn't happen to know what it's called or have a link for it?

---

### Post by ratanx on 2008-04-24
> **gn2 said:**
> You wouldn't happen to know what it's called or have a link for it?


Bump.

I'd like to know this as well.

---

### Post by psyke83 on 2008-04-24
[https://addons.mozilla.org/en-US/firefox/addon/6543](https://addons.mozilla.org/en-US/firefox/addon/6543)

---

### Post by PinkFloyd102489 on 2008-04-24
Only problem is that mozilla-mplayer does not work with FF3 and that's the only video plugin I will use.

---

### Post by Chipesh on 2008-04-25
> **PinkFloyd102489 said:**
> Only problem is that mozilla-mplayer does not work with FF3 and that's the only video plugin I will use.
.
I am using FF3 with Mplayer plug in in 8.04 ?
.
Bob

---

### Post by SunnyRabbiera on 2008-04-26
well I had stability issues with firefox 3, so I already did all this...
I am still going to check the progress of firefox 3 from time to time, as I know currently its a beta so its meant to be buggy.

---

### Post by zambizzi on 2008-04-27
I'd like to keep both so I can experiment with FF3, however when I run FF2, my important add-ons are all disabled and can't be re-enabled.

Is there a way that I can re-enable my FF2 add-ons in FF2 while keeping FF3 installed?

---

### Post by fooman on 2008-04-27
> **zambizzi said:**
> 
Is there a way that I can re-enable my FF2 add-ons in FF2 while keeping FF3 installed?

go to /home/<user name>/.mozilla/firefox/*****.default (where ***** can be any series of numbers & letters)

delete the *extensions.rdf* file and restart firefox.

you should then be able to install and use any firefox-2 extensions.

only trouble is if/when you do use firefox3 again,  it will reset and you will have to delete that file once more in order to install/use any those extensions in FF2 again.

---

### Post by zambizzi on 2008-04-27
I'll try it, thanks!

---

### Post by Theo148 on 2008-05-01
You can also disable add-on compatibility checking with the [Nightly Tester Tools extension]("https://addons.mozilla.org/en-US/firefox/addon/6543"), but do remember that not all add-ons will actually work properly in FF3.

---

### Post by JohnLM_the_Ghost on 2008-05-11
A quick note:
Don't forget to make Launcher on Main Menu Bar point to **firefox-2 %u** instead of just **firefox %u**

---

### Post by squidmaster on 2008-05-13
There are nice things about FF3 but FF2 > FF3 for now.

Good tutorial mate, I didn't even think about locking the version, good idea!

---

### Post by gmatt on 2008-05-15
I've  installed ff2 on my setup again and this is a really minor issue, but I notice that when I launch it I get two icons in my window list (in default ubuntu gnome setup this would be at the bottom) one says "Starting FireFox 2 Web Browser" and the other says whatever my homepage is set to. I wouldn't mind it much if the "Starting FireFox 2 Web Browser" lasted only 1 or 2 seconds, but it lasts close to 30-40 seconds, its quite annoying cause it serves no function as FireFox is already loaded and usable. Must be a bug with 8.04 cause in 7.10 no such thing happened.

---

