---
title: "[SOLVED] problem with firefox add-ons"
date: 2008-05-24
forum: New to Ubuntu
---

### Post by pranayama on 2008-05-24
I recently installed Hardy Heron. I don't like Firefox 3 beta 5 for various reasons, so I have tried to go back to stable Firefox 2 numerous times but there's always a problem. Tonight I've become unable to install or uninstall add-ons from both 3 and 2. I've tried purging them both completely twice, on both my administrator profiles, with all the flash plugins and the ubufox extension too. Then I reinstalled Firefox 2 with Synaptic, but it "reinstalls" within seconds, which makes me suspicious that Synaptic hasn't really purged it in the first place. I have cable, but it's not that fast. After reinstallation it comes up with my old homepage and bookmarks unchanged, and I'm still unable to add or remove extensions. I found a residual directory /etc/firefox-3.0 after the complete removal of version 3 with Synaptic, and I deleted that, but it hasn't solved the problem.

Now trying to install e.g.Adblock Plus on Firefox 2 gives this message on the error console:

installLocation has no properties
file:///usr/lib/firefox/components/nsExtensionManager.js

I'd be grateful for any advice on how to just uninstall *all* Firefox packages completely (preferably using a GUI application) so I can just start again from scratch.

Mark

---

### Post by saj0577 on 2008-05-24
As for your home page staying the same that will because the settings are still in your home folder. Look at the hidden folders and look for firefox, delete that and it will all go back to default.

As for totally removing all plugins, the only way i know is tools/add-ons but im sure you will have already tried this.

Saj

---

### Post by Hossie on 2008-05-24
Create a new profile with the [Profile manager](http://support.mozilla.com/en-US/kb/Managing+profiles).

---

### Post by pranayama on 2008-05-24
Saj when I search with Nautilus I find 7 folders called tools which is too many for my brain. I have already looked for hidden folders in /home/myprofile but there's nothing called firefox still left in there. Hossie I'll try that.

---

### Post by pranayama on 2008-05-24
In the directory /home/myprofile I found a hidden folder called .mozilla.

In all 4 of my profiles I deleted this with sudo rm -r .mozilla

Thanks, now Firefox 2 works OK again.

---

### Post by saj0577 on 2008-05-24
Thought it would, as I remember doing it myself along time ago.

Saj

Please mark as solved. :)

---

