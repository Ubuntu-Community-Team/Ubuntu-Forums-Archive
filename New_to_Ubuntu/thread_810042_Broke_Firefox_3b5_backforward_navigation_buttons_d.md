---
title: "Broke Firefox 3b5 back/forward navigation buttons don't work"
date: 2008-05-27
forum: New to Ubuntu
---

### Post by marcelo danico on 2008-05-27
I've been trying to fix ff3b5 crashes from youtube like web pages, but now my back/forward buttons don't work(greyed out) and the address bar doesn't remember the webpages that I've typed in.  Funny thing is the random crashes seem to have been fixed.

I was looking at several how-tos and my modifications were:

> sudo apt-get purge flashplugin-nonfree gnash gnash-common mozilla-plugin-gnash swfdec-mozilla && sudo apt-get install flashplugin-nonfree libflashsupport

> sudo apt-get remove kaffeine-mozilla mozilla-helix-player mozilla-mplayer mozilla-plugin-vlc totem-mozilla xine-plugin


> sudo apt-get install gnome-mplayer gecko-mediaplayer

> sudo aptitude remove gxine

> sudo aptitude install vlc

> sudo gedit /etc/gnome/defaults.list

In defaults.list I used replace function to change totem to vlc, saved and closed. Then rebooted system.

Anyone recognize were I made a big mistake? Or know a quick fix? Epiphany navigation buttons etc work fine and is now also loading faster and not crashing (so far).

I'll keep testing to see if the sudden crashes are really gone and post back.

---

### Post by marcelo danico on 2008-05-27
Crash problem definitely not fixed. But pages do load faster.

---

### Post by Sarah L on 2008-05-27
I believe that the firefox plugin packages are designed for the "firefox" package in the repositories, which is version 2 point something. They may not be compatible with the beta version of firefox 3.

Do you have the normal firefox package installed? I suggest that you stick with that if you're going to use the plugin packages from the repos.

---

### Post by marcelo danico on 2008-05-27
I still have the default firefox for 8.04 ff3 beta 5.

---

### Post by marcelo danico on 2008-05-27
I just upgraded ff3.0RC1
Using following

> You just need to add the following to your /etc/apt/sources.list:

    deb [http://ppa.launchpad.net/fta/ubuntu](http://ppa.launchpad.net/fta/ubuntu) hardy main

Then you only need to update (with apt-get update) and then upgrade (with apt-get dist-upgrade) or to install the firefox-3.0 package if you haven’t do it before.

But same problem: Navigation buttons and refresh, stop are dead (greyed out) and address bar stays same--doesn't change when I open a link or change between tabs.

---

### Post by Bubba64 on 2008-05-27
> **marcelo danico said:**
> I still have the default firefox for 8.04 ff3 beta 5.

If you want the latest FF release not in Hardy here is a link, this will over write the Hardy version and save all the bookmarks add ons and plugins.
[http://www.ubuntugeek.com/how-to-install-firefox-3-rc1-in-ubuntu-hardy.html](http://www.ubuntugeek.com/how-to-install-firefox-3-rc1-in-ubuntu-hardy.html)
If you ave any plugins that are not enabled install nightly tester tools this will force them to work with a button on the bottom right of the add on window.
[https://addons.mozilla.org/en-US/firefox/search?q=nightly%20tester%20tools](https://addons.mozilla.org/en-US/firefox/search?q=nightly%20tester%20tools)

---

### Post by marcelo danico on 2008-05-28
Okay I installed ff3.0RC1, problem still not fixed. Removed ff3.0 using synaptic, then reinstalled using Synaptic.  But problem remains--my settings like cookies, psswds also remain.

So I figure some extension or configuration from my profile settings is creating my problem.

So how do I wipe out my firefox user profile (in /home ?) and re-create it like new.

Is it safe to erase /home/marcelo/.mozilla? Does launching firefox re-create it automatically?

---

### Post by Bubba64 on 2008-05-28
> **marcelo danico said:**
> Okay I installed ff3.0RC1, problem still not fixed. Removed ff3.0 using synaptic, then reinstalled using Synaptic.  But problem remains--my settings like cookies, psswds also remain.

So I figure some extension or configuration from my profile settings is creating my problem.

So how do I wipe out my firefox user profile (in /home ?) and re-create it like new.

Is it safe to erase /home/marcelo/.mozilla? Does launching firefox re-create it automatically?

 In what order did you remove and install FF 3 in synaptic and install the updated version. Is your only problem the back and forth buttons. and the history in the browser window. have you looked in preferences for the days to remember history for FF.

---

### Post by marcelo danico on 2008-05-28
broken buttons forward/back, refresh, stop, address bar.

I had 3.5beta then I added the launchpad repo and installed RC1 with just update&dist-upgrade.  But the button issue didn't change, so I opened Synaptic searched firefox, removed ff3.0. Restarted and reinstalled ff3.0 w Synaptic again.  But again the same buttons are broken.

---

### Post by Bubba64 on 2008-05-28
> **marcelo danico said:**
> broken buttons forward/back, refresh, stop, address bar.

I had 3.5beta then I added the launchpad repo and installed RC1 with just update&dist-upgrade.  But the button issue didn't change, so I opened Synaptic searched firefox, removed ff3.0. Restarted and reinstalled ff3.0 w Synaptic again.  But again the same buttons are broken.

Toolbar buttons has reload and other button which may be usable. personally I never use any history of the address bar.
[https://addons.mozilla.org/en-US/firefox/search?q=toolbar%20buttons](https://addons.mozilla.org/en-US/firefox/search?q=toolbar%20buttons)
I really do not know any answers to fix what you want. you might wait for more posts for help.

---

### Post by marcelo danico on 2008-05-28
Well I used Synaptic to remove ff3.0 plus mplayer, acroread, flash-nonfree plugins. Then installed **ff2.0**, buttons all working.

---

### Post by 8086 on 2008-06-01
Removing firefox doesn't fix a thing. You need to fix your profile. Just move the .mozilla directory to .mozilla.old, and start up firefox. I have the same problem (with my old profile) as well. Only a fresh new profile fix it.

I suspect it might have to do with one of my many plugins ..

---

### Post by Joeb454 on 2008-06-01
To do that - from a terminal you can simply run ```
mv ~/.mozilla ~/.mozilla.old
```

Then you just need to start Firefox again :)

---

### Post by Saghaulor on 2008-10-28
I ran out of space on my filesystem. Consequently several things went awry, but I did not notice until firefox went on the fritz. Things started corrupting and whatnot. 

It may not be your problem, but I think my problem may help others out, hence my post.

---

