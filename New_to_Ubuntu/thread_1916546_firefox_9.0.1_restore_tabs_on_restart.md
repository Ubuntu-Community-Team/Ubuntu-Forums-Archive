---
title: "firefox 9.0.1 restore tabs on restart"
date: 2012-01-28
forum: New to Ubuntu
---

### Post by JamButty on 2012-01-28
Starting I think with the upgrade to 9.0.1 (for Ubunutu), FF always restores  the last tabs I had open when I restart it, regardless of whether I closed normally or forced it closed (e.g. crash). It does not ask, as was a possibility on prior versions, it just does it every time, or apologizes for not being able to. I'd rather it gave me the option on this, but I can't find a way to turn that tabs restore function off.
Anyone familiar with this? Running Oneiric if that matters.
Thanks.

---

### Post by raja.genupula on 2012-01-28
open your firefox

click at edit -> preferences ->general 
there at the start up make the selection as home page  , i think for you it might be show my last pages  .


All the best man .

---

### Post by JamButty on 2012-01-28
I've been through all the preferences with a fine-toothed comb. Found nothing about restoring tabs.
Homepage was set and defined. In previous versions of FF there was a preferences option for restoring/not restoring/ ask or similar, but not now.
"Don't load tabs until selected" is blank and grayed-out

---

### Post by Dave_L on 2012-01-28
[http://support.mozilla.org/en-US/kb/common-questions-after-upgrading-firefox-36#w_why-werent-my-tabs-and-windows-restored](http://support.mozilla.org/en-US/kb/common-questions-after-upgrading-firefox-36#w_why-werent-my-tabs-and-windows-restored)

Does that help?

---

### Post by raja.genupula on 2012-01-28
Hi man before posting here i have seen those options in my firefox too . I have tried and posted . and i am also using same FF 9 .

ope preference and at 1st TAB(named as general ) in that look for start up . that first line . ok
look at this image . 

Let me know if something wrong .

---

### Post by Cavsfan on 2012-01-28
There is an addon called "Tab Control" that lets you decide if you want to keep the tabs you have open saved for the next time
you open Firefox.
You can choose to "save and quit" or just "quit".

---

### Post by Cavsfan on 2012-01-28
Once you install it, just click on preferences and put a checkmark by "show save and quit dialogue".
Then it will be just like it was on earlier versions.

---

### Post by JamButty on 2012-01-28
[raja.genupula]("http://ubuntuforums.org/member.php?u=1184528") - thanks for taking the time to post a screen shot, but your and my startup section look the same, apart from a different homepage. I even tried going counterintuitive by using the "show my window and tabs from last time" temporarily so that the "Don't load tabs until selected" box became available, checked that, then went back to normal homepage setting. It did not affect the behavior.

Dave L - that guide says FF should not restore tabs automatically but only upon using the restore button on the default FF homepage (which I don't use) or by intentionally restoring the tabs via the history function. But my installation automatically restores old tabs on restart. I'll de/re-install FF.

---

### Post by Newton2525 on 2012-01-28
I have the drop-down menu like raja.genupula's image shows. Using FF 9.0.1 in Lucid.

Edit - Just read your latest post JamButty, nevermind

---

### Post by Frogs Hair on 2012-01-28
If  cookies and history are cleared at browser close tabs from the previous session won't be saved . If this is not the case I don't know what's happening there .

---

### Post by JamButty on 2012-01-28
Added the "Tab control". This works (need to check the "save and quit warning" box on preferences) when I close each FF window, so that is progress, but not a total solution.
Deinstalling/reinstalling did not change behavior. If I have multiple FF windows open, only the most recently opened FF window (and any associated tabs) are automatically restored the next time I start FF after shutting down (or crashing) with FF up. It is pretty common at night that I would just shut down without addressing every program open and it is not uncommon to force a crash after a lockup (powering down or thru terminal "shutdown now" if the system will give me a terminal) as Oneiric is buggy.

---

### Post by ajgreeny on 2012-01-28
I use **tab-mix-plus** add on for FF 9.01 in Lucid and that gives the option of saving then sessions if you want, and then reloading them at next start-up of FF, or starting with your own home-page, along with other options.  See screenshots for details.

---

### Post by Karlchen on 2012-01-28
Hello, JamButty.
> **JamButty said:**
> I'll de/re-install FF.Personally, I would try to launch Firefox with a fresh profile:

[LIST]
[*]terminate Firefox
[*]go to ~/.mozilla/firefox
[*]there will be a subfolder having weird looking name like e.g. vw9o29p4.default.
[*]rename this subfolder to something else: mv vw9o29p4.default vw9o29p4.prev
[*]restart Firefox
[*]Firefox should re-create the folder vw9o29p4.default and a new profile in it
[*]use Firefox, creating and removing browser tabs
[*]terminate and relaunch Firefox several times in order to determine whether problem has vanished.
[*]In case everything is all right, you may start restoring settings which you may have lost by starting with an empty profile by comparing your new profile to the renamed profile
[/LIST]
Only in case the new profile attempt fails, too, I would assume that the Firefox main program may be the culprit and re-install it.

HTH,
Karl

---

### Post by Cavsfan on 2012-01-28
> **JamButty said:**
> Added the "Tab control". This works (need to check the "save and quit warning" box on preferences) when I close each FF window, so that is progress, but not a total solution.
Deinstalling/reinstalling did not change behavior. If I have multiple FF windows open, only the most recently opened FF window (and any associated tabs) are automatically restored the next time I start FF after shutting down (or crashing) with FF up. It is pretty common at night that I would just shut down without addressing every program open and it is not uncommon to force a crash after a lockup (powering down or thru terminal "shutdown now" if the system will give me a terminal) as Oneiric is buggy.

Tab Control works great on Lucid. Just like FF version 3.6 did.

---

### Post by lovinglinux on 2012-01-28
Get [Session Manager](https://addons.mozilla.org/en-US/firefox/addon/session-manager/) add-on. It has many options and it is great for customizing your sessions. It can even save multiple sessions, like Opera does.

---

### Post by JamButty on 2012-01-28
Session-Manager sounds interesting and I may try it for other reasons, but it is meant for saving sessions, and my aim is to stop FF saving windows and restoring without my asking.
Karlchen - hob's jemocht - deinstalled, let Bleachbit wipe everything FF and deleted /.mozilla/.firefox, then reinstalled. Behavior is the same.   Tab-mix-plus looks very complete and it ostensibly turned off FF default session restore function (it claimed to have done so), but behavior remains after specifying /don't restore/ on /browser starts/ and /don't save/ on /browser exits/.

---

