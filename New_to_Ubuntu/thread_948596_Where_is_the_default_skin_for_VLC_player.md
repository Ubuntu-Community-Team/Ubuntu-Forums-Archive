---
title: "Where is the default skin for VLC player?"
date: 2008-10-15
forum: New to Ubuntu
---

### Post by bwallum on 2008-10-15
Hi, I was getting on so well with the Intrepid beta that I thought I would try and change the skin of vlc. It crashed and now I am being asked to select a skin.

Where is the default vlc skin file in Ubuntu please?

---

### Post by iKonaK on 2008-10-15
Delete your "/home/you/[COLOR=Red].vlc[/COLOR]" folder, this will reset your vlc settings.

---

### Post by bwallum on 2008-10-15
> **iKonaK said:**
> Delete your "/home/you/[COLOR=Red].vlc[/COLOR]" folder, this will reset your vlc settings.

Didn't solve it unfortunately. I've appended a screen shot to show the error messages. Does that give any more clues?

---

### Post by LowSky on 2008-10-15
when in doubt why not just reinstall vlc from synaptic

---

### Post by iKonaK on 2008-10-15
> **LowSky said:**
> when in doubt why not just reinstall vlc from synaptic
+1
try reinstall it or completely remove an then install again...

---

### Post by bwallum on 2008-10-15
> **LowSky said:**
> when in doubt why not just reinstall vlc from synaptic

Tried that 'completely remove' and everything that was loaded with vlc in it. Then restarted, then reinstalled vlc from Add/Remove (just to make sure I got all the files back that were needed). Result...no change, same error windows as posted above.

---

### Post by fooman on 2008-10-15
i had a similar issue with a new skin i added...then could not get rid of.

i opened synaptic, searched for vlc,  uninstalled vlc, vlc-nox, libvlc and vlc-plugin-pulse *by right clicking and choosing "mark for complete removal"*.

then find and delete /home/<username>/.vlc

then reinstall vlc (which should install libvlc, lvlc-nox and vlc-plugin-pulse as dependencies).

after that all was good here.

---

### Post by bwallum on 2008-10-15
> **fooman said:**
> i had a similar issue with a new skin i added...then could not get rid of.

i opened synaptic, searched for vlc,  uninstalled vlc, vlc-nox, libvlc and vlc-plugin-pulse *by right clicking and choosing "mark for complete removal"*.

then find and delete /home/<username>/.vlc

then reinstall vlc (which should install libvlc, lvlc-nox and vlc-plugin-pulse as dependencies).

after that all was good here.

Tried all the above but it did not work...however, I recalled something about config file changes and found the config files at /home/<username>/.config/vlc

So deleted all the files you recommended namely vlc, vlc-nox, libvlc and vlc-plugin-pulse (if you have it) by right clicking and choosing "mark for complete removal", then deleted /home/<username>/.config/vlc, then reinstalled vlc and now back to default with vlc working. 

I'm using Intrepid so think the .config bit may not be appropriate for hardy, gutsy, fiesty etc.

Thanks everybody!

---

### Post by darkazurka on 2008-12-28
Whatever you do. Don't touch synaptic when you've done something wrong in the settings. They're either in /etc/ or in your home directory!

I deleted
```
/home/linuxaiz/.config/vlc
```
the vlc directory containing 2 files. After that I started up vlc. Guess what.

It's not asking for the damn skin files again! It made the setup from the beginning. I felt so relieved! :popcorn:

---

### Post by InsaneNoob on 2010-10-31
BUMP... last post does the trick

---

### Post by jfreak_ on 2010-10-31
talk about reviving old threads.....

---

