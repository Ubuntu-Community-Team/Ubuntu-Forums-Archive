---
title: "Is updating GVFS safe now?"
date: 2008-09-02
forum: New to Ubuntu
---

### Post by Halibutt on 2008-09-02
Hello all. Some time ago I installed all the suggested updates for my Hardy Heron. Among them was the GVFS update which caused [this]("http://ubuntuforums.org/showthread.php?t=801597&highlight=Halibutt"), then [this]("http://ubuntuforums.org/showthread.php?t=901245"), and in the end my Ubuntu machine was nothing more than a pile of electronic garbage. 

I reinstalled ubuntu from the scratch and now I'm wondering. The autoupdate wizard (or whatever that star's name is) is suggesting me to update GVFS every time I start Ubuntu. Is it safe now? Or will it crash my computer the way Windows viruses never did - and the way it did before? Finally, is there a way to, say, unmark the gvfs to never appear in auto-update? Every time I install something I'm afraid I might accidently click a wrong icon and install the gvfs update, cause it's always there...
Cheers and thanks for your help.

---

### Post by drs305 on 2008-09-02
I have never had problems with gvfs, so my saying that the updates have not caused any problems probably doesn't mean much.

As to your question, you can go into synaptic and highlight "gvfs". Then in the top menu, select Package and 'Lock version'. It will prevent further updates. 

I would personally allow the updates, but that is how you would do it should you decide to do so.

Note that Synaptic locks are not respected by command-line updates. The aptitude command has a *hold* option for command-line updates using aptitude.

---

### Post by Halibutt on 2008-09-02
> **drs305 said:**
> I have never had problems with gvfs, so my saying that the updates have not caused any problems probably doesn't mean much.Well, the problems with my first Ubuntu installation started when I updated an almost-clean installation. This time I reinstalled the system and updated all packages - except for gvfs. No crash this time, all goes smooth and fine, so I guess the gvfs update was the reason for all my problems, as others suggested in one of the threads I linked. 

Now, I wonder if there's a way to check whether the gvfs will run havoc once again, or was it a one-time crime.

---

### Post by arpanaut on 2008-09-02
I just checked here: [https://bugs.launchpad.net/ubuntu/hardy/+bugs?field.searchtext=GVFS&orderby=-importance&search=Search&field.status%3Alist=NEW&field.status%3Alist=INCOMPLETE_WITH_RESPONSE&field.status%3Alist=INCOMPLETE_WITHOUT_RESPONSE&field.status%3Alist=CONFIRMED&field.status%3Alist=TRIAGED&field.status%3Alist=INPROGRESS&field.status%3Alist=FIXCOMMITTED&field.assignee=&field.bug_reporter=&field.omit_dupes=on&field.has_patch=&field.has_no_package=](https://bugs.launchpad.net/ubuntu/hardy/+bugs?field.searchtext=GVFS&orderby=-importance&search=Search&field.status%3Alist=NEW&field.status%3Alist=INCOMPLETE_WITH_RESPONSE&field.status%3Alist=INCOMPLETE_WITHOUT_RESPONSE&field.status%3Alist=CONFIRMED&field.status%3Alist=TRIAGED&field.status%3Alist=INPROGRESS&field.status%3Alist=FIXCOMMITTED&field.assignee=&field.bug_reporter=&field.omit_dupes=on&field.has_patch=&field.has_no_package=)
which gives the open GVFS bugs in hardy... I don't know if any relate to your problems but it seems to me that if there was a prevailing problem from updates it would have been reported?

To Update is always is always a tricky question especially after being burned once.  It could be localized to your machine/setup or Not!

Hope you find your answer.

---

### Post by Halibutt on 2008-09-11
Just for the record, with my fresh install I waited a bit with updating it for fear of having to reinstall once again, but I finally made the step and... all worked fine this time. Thanks for your help.
Cheers

---

