---
title: "&quot;Updates&quot; boxes in software sources cannot be unchecked"
date: 2013-06-05
forum: New to Ubuntu
---

### Post by monkeybrain2012 on 2013-06-05
Just noticed that the updates boxes in software sources cannot be unchecked (see the checked boxes in screenshot), try to say, uncheck "pre-relased ubdates" and you can click until your face turns blue and nothing happens.  boxes in other tabs such as "Other Software" are fine. This is Ubuntu 13.04

Any idea?

Thanks

---

### Post by houseworkshy on 2013-06-05
That doesn't sound right at all.  You could try putting in an alternative software manager, synaptic is still in the repositories.  You could also take a look at your sources and make sure that only the main repositories are enabled which might prevent things nearer to development status from going in.  You could also ( in order to make absolutely sure you are admin ) open the software centre from the command line with sudo.

---

### Post by monkeybrain2012 on 2013-06-05
> **houseworkshy said:**
> That doesn't sound right at all.  You could try putting in an alternative software manager, synaptic is still in the repositories.  You could also take a look at your sources and make sure that only the main repositories are enabled which might prevent things nearer to development status from going in.  You could also ( in order to make absolutely sure you are admin ) open the software centre from the command line with sudo.

That picture is from synaptic (but it doesn't really matter as the software sources window is is the same component in Updater and the USC). I know how to change it in the terminal, but just wondering if this is a bug or perhaps something in my setup,

Thanks for the reply though.

---

### Post by Frogs Hair on 2013-06-05
The sources can be changed from synaptic on my installation which is just another path to the software & updates GUI. The password prompt when opening synaptic should allow for making changes.

---

### Post by newb85 on 2013-06-05
You are using an administrator account, right?

---

### Post by Frogs Hair on 2013-06-05
I am  not sure whom you are asking, for me it makes no difference in user or administrative .  Both allow access after the password prompt.

---

### Post by newb85 on 2013-06-05
> **Frogs Hair said:**
> I am  not sure whom you are asking, for me it makes no difference in user or administrative .  Both allow access after the password prompt.
Oops! You're right.

---

### Post by monkeybrain2012 on 2013-06-05
Hmm.. then it looks like there is something wrong with my own setup then.. Will do more testings then report back.

---

### Post by monkeybrain2012 on 2013-06-05
> **Frogs Hair said:**
> The sources can be changed from synaptic on my installation which is just another path to the software & updates GUI. The password prompt when opening synaptic should allow for making changes.

The sources can be change except for those on the "updates" tab. On the other hand there is no problem say enabling or disabling a ppa with the checkboxes in the "other software" tab or enabling and disabling the partner's repo with the checkbox.

---

### Post by Frogs Hair on 2013-06-05
I can change all sources including Ubuntu software and  updates , so it may be a bug.

---

### Post by monkeybrain2012 on 2013-06-05
Ok, just did a bit more tests. This is weird. Actually some of the boxes in the "Other Software" tab cannot be changed either (checked on unchecked). But this is the pattern, the top 5 or 6 boxes on the page cannot be changed, all others can be. Since in the Updates tab there are only 4 update sources all on the top none of them can be changed.

Edited: it may be a side effect of some Compiz plugins..

---

### Post by houseworkshy on 2013-06-05
run rkhunter and chkrootkit

---

