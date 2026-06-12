---
title: "Compiz still keeps crashing"
date: 2011-10-03
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by ubj on 2011-10-03
I have have been using Ubuntu since the very first release and Oneiric just might be first one to be too unstable for daily use. Only 9 days left for stable release and compiz just keep on crashing. According to bug [reports]("https://bugs.launchpad.net/ubuntu/+bugs?field.searchtext=compiz&orderby=-datecreated&search=Search&field.status%3Alist=NEW&field.status%3Alist=INCOMPLETE_WITH_RESPONSE&field.status%3Alist=INCOMPLETE_WITHOUT_RESPONSE&field.status%3Alist=CONFIRMED&field.status%3Alist=TRIAGED&field.status%3Alist=INPROGRESS&field.status%3Alist=FIXCOMMITTED&field.assignee=&field.bug_reporter=&field.omit_dupes=on&field.has_patch=&field.has_no_package=") i am not only one, many of those reports are very new.

---

### Post by alphacrucis2 on 2011-10-04
> **ubj said:**
> I have have been using Ubuntu since the very first release and Oneiric just might be first one to be too unstable for daily use. Only 9 days left for stable release and compiz just keep on crashing. According to bug [reports]("https://bugs.launchpad.net/ubuntu/+bugs?field.searchtext=compiz&orderby=-datecreated&search=Search&field.status%3Alist=NEW&field.status%3Alist=INCOMPLETE_WITH_RESPONSE&field.status%3Alist=INCOMPLETE_WITHOUT_RESPONSE&field.status%3Alist=CONFIRMED&field.status%3Alist=TRIAGED&field.status%3Alist=INPROGRESS&field.status%3Alist=FIXCOMMITTED&field.assignee=&field.bug_reporter=&field.omit_dupes=on&field.has_patch=&field.has_no_package=") i am not only one, many of those reports are very new.

Even the compiz settings manager crashes for me. With any luck there will be a raft of fixes before too long.

---

### Post by chipmonk on 2011-10-08
I have to agree. Just installed Oneiric few hours ago, and during that time (basic surfing in the net mostly) Compiz has crashed on me at least five times (two of those times brought Xorg server down as well) and compiz settings manager has crashed once (I have used it twice). Certainly step backwards in stability.

---

### Post by effenberg0x0 on 2011-10-08
Hey,

Compiz, Unity, ccsm, really are unstable, no question there. Things  we've doing for months to fix and help users get their launcher/panel on  screen, like resetting unity, deactivating/activating the Unity Plugin,  unsetting compiz-1/compizconfig-1 keys on gconf, removing xorg.conf,  ~/.Xauthority, .local, .cache, etc, restarting lightdm a couple times,  etc are not event that effective anymore with latest releases. 

I'm not sure where developers stand on that (I'm not following the  discussions), but they probably are putting really strong efforts on  fixing it now that we're so close to release date. It's not like its a  secondary or less relevant package / set of features that can be  disabled for release: It's the main thing about Oneiric. 

I wouldn't be surprised if a lot of the upcoming updates are related to  these packages.There's a strong community of developers and testers out  there. I believe it will get fixed in time.

Regards,
Effenberg

---

### Post by alphacrucis2 on 2011-10-08
Funnily enough for me, compiz has become much more stable over the last few days of updates. Even the crash I was getting in the compiz settings manager has gone.

---

