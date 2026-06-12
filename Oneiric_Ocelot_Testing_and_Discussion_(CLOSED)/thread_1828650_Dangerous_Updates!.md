---
title: "Dangerous Updates!"
date: 2011-08-19
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by sgage on 2011-08-19
As of 12:30 UTC there are updates for gjs and libnux in the repos, which if allowed to update will remove gnome-shell, unity, AND unity 2D. How cool is that! :KS

Not sure how long this state of affairs will last...

[Edit: There is now a new gnome-shell in the repos, so the gjs update is OK.]

---

### Post by mdhollis on 2011-08-19
The update only removed unity 2d for me.  Just upgraded 5 minutes ago.  The gjs upgrade is being held back even with dist-upgrade.

---

### Post by sgage on 2011-08-19
> **mdhollis said:**
> The update only removed unity 2d for me.  Just upgraded 5 minutes ago.  The gjs upgrade is being held back even with dist-upgrade.

Yes, there is now a new unity in the repos. I suspect a new unity-2d will be up soon.

I wonder why your gjs is being held back... maybe you have some other pkg installed that I don't that has that dependence.

---

### Post by 3rdalbum on 2011-08-19
Always check what's to be removed. I never do a "Partial Upgrade" in Update Manager - instead I use Synaptic as it's quicker to calculate the upgrade, and it gives more warnings about what's going to be removed - twice as many chances to turn chicken and decide to wait should something critical be marked for removal :-)

---

### Post by sgage on 2011-08-19
> **3rdalbum said:**
> Always check what's to be removed. I never do a "Partial Upgrade" in Update Manager - instead I use Synaptic as it's quicker to calculate the upgrade, and it gives more warnings about what's going to be removed - twice as many chances to turn chicken and decide to wait should something critical be marked for removal :-)

Yes, I always use Synaptic, and if something is marked for removal, I just wait until it resolves. Rarely I'll let it go ahead anyway, if I understand fully what's going on and know it's sensible.

---

### Post by mdhollis on 2011-08-19
You know I saw that unity 2d was going to be removed and I did it anyway.......lol.

I've been using gnome-shell for the past month.  I'm starting to really like it, but I still shouldn't have ran that update.

---

### Post by sgage on 2011-08-19
> **mdhollis said:**
> You know I saw that unity 2d was going to be removed and I did it anyway.......lol.

I've been using gnome-shell for the past month.  I'm starting to really like it, but I still shouldn't have ran that update.

Like I said, if the removal seems sensible, I let it go ;)

I am definitely leaning towards Gnome Shell, but I like to keep the other ones updated just in case. Ah, choice!

---

### Post by ratcheer on 2011-08-19
Hmmm...

I installed updates this morning and I still have Unity 2D. I know because I am running it, right now.

I will run another update and see what happens. I won't install it if it says it will remove Unity 2D, because that is the only way I can run Oneiric.

Tim

---

### Post by dino99 on 2011-08-19
2 packages are waiting for upgrading: mutter & clutter, & will not be ready till 8 days or so

so unity & gs have to wait, dont upgrade them or it breaks

---

### Post by ratcheer on 2011-08-19
> **ratcheer said:**
> Hmmm...

I installed updates this morning and I still have Unity 2D. I know because I am running it, right now.

I will run another update and see what happens. I won't install it if it says it will remove Unity 2D, because that is the only way I can run Oneiric.

Tim

No, it still does not offer to remove Unity 2D on my system. I do, however, have 23 "upgradable" packages that seem to be waiting for dependencies to be met.

Tim

---

### Post by sgage on 2011-08-19
I just did an update, and nothing is being held back any more - there's a new unity-2d, and bunches of other stuff.

---

### Post by Harry33 on 2011-08-19
> **sgage said:**
> As of 12:30 UTC there are updates for gjs and libnux in the repos, which if allowed to update will remove gnome-shell, unity, AND unity 2D. How cool is that! :KS

Not sure how long this state of affairs will last...

[Edit: There is now a new gnome-shell in the repos, so the gjs update is OK.]

Yes gnome-shell is OK.
This was only a switch from the library libgjs0b to a new one libgjs0c.
The old libgjs0b should be purged now.

---

### Post by jbicha on 2011-08-19
> **sgage said:**
> As of 12:30 UTC there are updates for gjs and libnux in the repos, which if allowed to update will remove gnome-shell, unity, AND unity 2D. How cool is that! :KS

Not sure how long this state of affairs will last...

[Edit: There is now a new gnome-shell in the repos, so the gjs update is OK.]

Holy inconsistent Ubuntu archive, Batman!

Seriously, could you use a less sensational title for your forum post? And mark this one SOLVED while you're at it.

Transitions happen all the time in the Ubuntu development cycle. Inconsistencies are usually resolved within a few hours; sometimes it takes a few days if something wasn't quite right. People who want to run the development release need to look before they dist-upgrade (or partial upgrade) unless they enjoy reinstalling. The partial upgrade thread is stickied so people don't waste their time reading supposedly urgent forum threads that really aren't that important.

---

### Post by rbrick49 on 2011-08-19
> **jbicha said:**
> Holy inconsistent Ubuntu archive, Batman!

Seriously, could you use a less sensational title for your forum post? And mark this one SOLVED while you're at it.

Transitions happen all the time in the Ubuntu development cycle. Inconsistencies are usually resolved within a few hours; sometimes it takes a few days if something wasn't quite right. People who want to run the development release need to look before they dist-upgrade (or partial upgrade) unless they enjoy reinstalling. The partial upgrade thread is stickied so people don't waste their time reading supposedly urgent forum threads that really aren't that important. steady eddie he was only warning of the dangers

---

### Post by VinDSL on 2011-08-20
> **sgage said:**
> I just did an update, and nothing is being held back[...] 
Dittos!

> **sgage said:**
> There's a new unity-2d, and bunches of other stuff.
This is the smoothest, fastest, and best that Unity has run, since the pre-alpha.

Plus, the LightDM Greeter is back.  Surprise, surprise.

Gotta go try 2D now.  Thanks, for reminding me.  ;)

---

### Post by sgage on 2011-08-20
> **jbicha said:**
> Holy inconsistent Ubuntu archive, Batman!

Seriously, could you use a less sensational title for your forum post? And mark this one SOLVED while you're at it.

Transitions happen all the time in the Ubuntu development cycle. Inconsistencies are usually resolved within a few hours; sometimes it takes a few days if something wasn't quite right. People who want to run the development release need to look before they dist-upgrade (or partial upgrade) unless they enjoy reinstalling. The partial upgrade thread is stickied so people don't waste their time reading supposedly urgent forum threads that really aren't that important.

Look, every time the repos get that inconsistent, especially with major fundamental stuff, there are people that don't pay that close attention. And then we have a raft of posts like "I did a partial upgrade and now my system is borked". I was trying to preempt some of that.

It also enabled people to see when things were resolved, so they could go back and update.

I thought it was important, I suspect it saved some people some grief, and I really didn't care for the tone of your lecture.

---

### Post by tingxyu1996 on 2011-08-20
Yea... Last night I updated then restart, the Gnome shell has been removed and I forced to use Unity....
I re-installed Ubuntu and I won't update the Ubuntu again!

---

### Post by dummy910 on 2011-08-20
I posted a very similar situation a few days ago, whereas jockey-gtk **deleted my entire unbuntu-desktop** whilst **activating** what it detected as the **correct video drivers**(you guessed it, ATI). 

**11.04 Desktop go kaboom!**
 [http://ubuntuforums.org/showpost.php?p=11158961&postcount=1](http://ubuntuforums.org/showpost.php?p=11158961&postcount=1)

---

### Post by cariboo on 2011-08-20
@dummy910 & tingxyu1996

This is the Oneiric testing and discussion sub-forum, if you have problems with released versions please post your questions and comments in General Help. Your problems aren't relevant unless you are running 11.10.

---

### Post by jbicha on 2011-08-20
> **sgage said:**
> Look, every time the repos get that inconsistent, especially with major fundamental stuff, there are people that don't pay that close attention. And then we have a raft of posts like "I did a partial upgrade and now my system is borked". I was trying to preempt some of that.

It also enabled people to see when things were resolved, so they could go back and update.

I thought it was important, I suspect it saved some people some grief, and I really didn't care for the tone of your lecture.

I apologize for being rude. I believe we all want to help more or less.

I think that if you try to post a warning every time there is a partial upgrade that affects core parts of the system, you'll be posting quite a bit.

---

### Post by sgage on 2011-08-20
> **jbicha said:**
> I apologize for being rude. I believe we all want to help more or less.

I think that if you try to post a warning every time there is a partial upgrade that affects core parts of the system, you'll be posting quite a bit.

Your point is taken. It just seemed like I was seeing a lot of folks with messed up system lately, and this one affecting so many things at once, I thought it worth the head's up. If only everyone would read the sticky up top!

And thanks for the apology - I was feeling a bit grumpy myself this morning...

---

### Post by dummy910 on 2011-08-20
> **cariboo907 said:**
> @dummy910 & tingxyu1996

This is the Oneiric testing and discussion sub-forum, if you have problems with released versions please post your questions and comments in General Help. Your problems aren't relevant unless you are running 11.10.
I stand corrected cariboo, sorry to all to whom confusion may have occured as I am a dummy after all.

peace out!

---

