---
title: "[SOLVED] Problem with FF3 and Google Toolbar"
date: 2008-06-18
forum: New to Ubuntu
---

### Post by slughappy1 on 2008-06-18
Is anyone else having the problem of google toolbar not downloading bookmarks? When I click on *Bookmars* it just says *Downloading bookmarks...* I had this problem with FF2. I was able to solve this problem by installing a certain file, but I don't remember what it was. Anyone know how to fix it?

---

### Post by KingTermite on 2008-06-18
I know I had a problem with google toolbar, and was able to overcome it by reinstalling.

The trick is to save your cookies and bookmarks (in your Fx profiles folder) if you have trouble exporting them manually. Then remove Fx (can use synaptic), delete Fx profile directory, reinstall and then copy your bookmarks/cookies back.

Then with a the fresh install (no plugin, flash or anything like that reinstalled), install google toolbar first. 

I had trouble installing and that was the process that fixed things for me.

---

### Post by kbchoi on 2008-06-18
Reinstall did not work for me on Hardy. Installing libstdc++5 did not work either, which worked for FF2. Hope someone find it out how to fix it really soon.

---

### Post by jon9314 on 2008-06-18
i have the same problem. is it a problem with ff, Google. or ubuntu?

---

### Post by Soundtrack Black on 2008-06-25
same here - running hardy. Tried reinstalling the toolbar, clearing cookies, logging in/out.

Anyone else?

---

### Post by mahiyar on 2008-06-25
Thats a problem. A round about way is to install a single bookmark button using FF add on from here, [https://addons.mozilla.org/en-US/firefox/addon/2453](https://addons.mozilla.org/en-US/firefox/addon/2453) , it works!

---

### Post by ominousluv on 2008-06-28
Same problem here.  I haven't been able to solve it.

---

### Post by rhomany on 2008-06-28
If it helps at all, I've found that [Gutil!]("https://addons.mozilla.org/en-US/firefox/addon/3755") + [Gmarks]("https://addons.mozilla.org/en-US/firefox/addon/2888"), together with the new built-in features of FF3, has removed the need for Google toolbar for me, now they fixed the spellchecker. 
Plus, Gutil! has a nice neat customiseable menu that doesn't periodically completely forget that you put customised buttons in it, unlike GT used to and GMarks gives you an optional bookmarks star mentioned above. Just right click on your toolbar and go to customise, then select it to add.

---

### Post by aBitLater on 2008-07-08
uninstalling adobe flashplayer 10 (beta) and reinstalling version 9 worked for me.  Also fixed crashes with Vuze

delete /home/your_account/.mozilla/plugins/libflashplayer.so (version 10) before running the install script for version 9.

---

### Post by ryukent on 2008-07-09
Open terminal. Type:

sudo apt-get install libxul-dev libstdc++5 gcc-4.1 libstdc++6

Then in firefox, go to tools, add-ons, disable google toolbar and let it restart firefox. Then do the same, but enable and restart firefox. Should now work.

---

### Post by slughappy1 on 2008-07-09
HOLY CRAP! IT WORKS! Thanks ryukent

---

