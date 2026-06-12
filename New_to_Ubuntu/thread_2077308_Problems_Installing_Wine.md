---
title: "Problems Installing Wine?"
date: 2012-10-28
forum: New to Ubuntu
---

### Post by Pokemon3DS on 2012-10-28
Hi all, I have just moved from Windows to Ubuntu and I am trying to install Wine, but it won't work. Can I have some help please?

---

### Post by howefield on 2012-10-28
Some errors or an idea of where you are getting stuck might help anyone who wants to offer some assistance.

---

### Post by Pokemon3DS on 2012-10-28
> **howefield said:**
> Some errors or an idea of where you are getting stuck might help anyone who wants to offer some assistance.

It's as soon as I install it, it just comes up with an error

---

### Post by critin on 2012-10-28
> **Pokemon3DS said:**
> It's as soon as I install it, it just comes up with an error

What does the error say?

---

### Post by Pokemon3DS on 2012-10-28
That it can conflict with other apps, but all I have installed is Google Chromium and VLC Media Player

---

### Post by critin on 2012-10-28
> **Pokemon3DS said:**
> That it can conflict with other apps, but all I have installed is Google Chromium and VLC Media Player

I've never installed wine so can't help with that, but if it's only warning you,  you can reinstall those two if a problem arises.  Go ahead and install it.  If it refuses to install, uninstall the two apps, then install again after installing wine.

If it doesn't name the apps, you're guessing it's these two.

---

### Post by Mark Phelps on 2012-10-28
Since you're probably installing Wine to run Windows apps, before you go any further, you need to go to the WineHQ website, the application compatibilty page -- and look up the apps (and versions) you want to run under Wine.

Anything you need to use daily, that either (1) is not listed or (2) has a rating lower than GOLD, is not going to work well enough to be useful to you.

In that case, you then need to come back here and ask about Linux alternatives -- as trying to install the Windows apps is largely going to be a waste of your time and effort.

---

### Post by monkeybrain2012 on 2012-10-28
Well if you expect help you should be more specific, like exactly what the conflict is. I don't know how anyone can help you if all you tell us is "it doesn't work", "I get error message", "it says there is some conflict" and only give these vage answers after other people's prompting. Do you go to the doctor to just say "Doc, I don't feel well" and expect him to be able to diagnose your problem? :)

---

### Post by Spyderkid on 2012-10-28
try running these in terminal...

sudo apt-get update
sudo apt-get upgrade
sudo apt-get install wine

---

