---
title: "Unity has grown too large , want's to remove K-desktop from Kubuntu Oneiric ..."
date: 2011-07-08
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by xeizo on 2011-07-08
Yes, that's true with todays updates, Synaptic want's to remove the KDE-desktop and replace it with lot's of Compiz/Unity and it's Gnome 3-depencencies. I hope it's a casual bug as I've grown fond of Kubuntu and it would be real sad if one can't be able to have a clean KDE-desktop anymore.

Unity and Gnome-shell sucks in usability so far imho.

One extra problem with the above is if one allows Unity/Compiz/Gnome 3-anything to be installed they will currently start a ghost desktop behind the KDE-desktop even if one uses KDM, so they really have to be kept at bay!

I hope the Kubuntu-crowd can workaround this development so it will still be possible to run a clean KDE Kubuntu. 

Otherwise, well, the other desktop dists have even worse problems so I set my hope to Ubuntu/Kubuntu as a viable Windows-alternative!

---

### Post by kaldor on 2011-07-08
Kubuntu is not going anywhere, nor is KDE. Remember that this is still a very Alpha version of 11.10 and I am certain that this is just a testing mistake.

---

### Post by lucazade on 2011-07-08
> **kaldor said:**
> Kubuntu is not going anywhere, nor is KDE. Remember that this is still a very Alpha version of 11.10 and I am certain that this is just a testing mistake.

this.. and we are here to figure out if there are this kind of issues and report them in launchpad. This way we can contribute during alpha testing.
Just FYI indicators updates want to remove unity-2d here, so it is not about unity growing.

---

### Post by xeizo on 2011-07-08
> **lucazade said:**
> this.. and we are here to figure out if there are this kind of issues and report them in launchpad. This way we can contribute during alpha testing.
Just FYI indicators updates want to remove unity-2d here, so it is not about unity growing.

I didn't exactly mean Unity in itself but it's list of dependencies, sort of in the same way as Plymouth nowadays is impossible to fully remove only hide.

Of course I hope it's a normal bug during development, but if I have choosen Kubuntu in all possible ways I don't wan't even the smell of Unity on my system. Not when doing a normal upgrade. Even if it's under the development stage, Unity should not install itself unless I choose so. And I will not choose it until it has improved in multiple ways, which is likely to occur some time.

---

### Post by lucazade on 2011-07-08
> **xeizo said:**
> I didn't exactly mean Unity in itself but it's list of dependencies, sort of in the same way as Plymouth nowadays is impossible to fully remove only hide.

Of course I hope it's a normal bug during development, but if I have choosen Kubuntu in all possible ways I don't wan't even the smell of Unity on my system. Not when doing a normal upgrade. Even if it's under the development stage, Unity should not install itself unless I choose so. And I will not choose it until it has improved in multiple ways, which is likely to occur some time.

Plymouth depends on mountall because of fsck check at boot-time and cannot be easily removed. Only recompiling and modifying deps. 
Anyway plymouth could be disabled in a simple way, so no great problem for me.

About Unity I can understand that for a Kde user is not interesting, but this time I believe it is not related with the issue you got. Sometime seems to me that unity is the "aunt sally" for a lot of recents glitches, when in reality is not strictly related to it.

---

### Post by fjgaude on 2011-07-08
> About Unity I can understand that for a Kde user is not interesting, but this time I believe it is not related with the issue you got. Sometime seems to me that unity is the "aunt sally" for a lot of recents glitches, when in reality is not strictly related to it.

My understanding is Unity is a GUI shell over Gnome2/3, just as Gnome-shell is over Gnome2/3. KDE is a shell over Gnome2/3?

---

### Post by cariboo on 2011-07-08
KDE is a stand alone OS that depends on QT libraries, it has nothing to do with gnome.

---

### Post by fjgaude on 2011-07-08
> **cariboo907 said:**
> KDE is a stand alone OS that depends on QT libraries, it has nothing to do with gnome.

Thanks for the insight. So why the talk of Unity getting too big?

---

### Post by IanW on 2011-07-09
> **fjgaude said:**
> Thanks for the insight. So why the talk of Unity getting too big?

I think the OP was referring to ego not size?

---

### Post by xeizo on 2011-07-10
> **IanW said:**
> I think the OP was referring to ego not size?

Indeed I was. And with the upcoming/now ongoing KDE 4.7 RC1 breakage I gave up and switched to Unity again while KDE/Kubuntu sorts out it's stuff. 

It's(Unity) actually working, but with the same bugs as KDE had before ie no keyboard and mouse at login - removing/inserting USB activates them - and no sound after login. The dreaded "dummy output". sudo alsa force-reload activates sound, but why I still have to keep doing that after almost a week is beyond me ....

I saw another thread about changing ownersship of /dev/snd, I will try that too as I've noticed along the way that permissions regularly gets messed up in Oneiric. Don't know yet if it will work, but apparently it did in the other thread.

---

### Post by hexsel on 2011-07-15
> **cariboo907 said:**
> KDE is a stand alone OS that depends on QT libraries, it has nothing to do with gnome.

KDE is a stand-alone DESKTOP ENVIRONMENT (K Desktop Environment), not an OS.

---

### Post by MAFoElffen on 2011-07-15
> **cariboo907 said:**
> KDE is a stand alone OS that depends on QT libraries, it has nothing to do with gnome.
And just as this is said... This wasn't just a Kubuntu 11.10 issue.  I had to help Kubuntu 11.04 users on the Ubuntu Installations and Updates Forum last week after an update hit.  Seems that while updating xserver-xorg-core, it wanted to remove the kubuntu-desktop.  Reinstalling Kubuntu 11.04 fresh brought it back to the same error after updates... until a couple days went by and it seemed to resolve itself in updates(???)

---

### Post by cariboo on 2011-07-15
It seems to me that if an update was going to remove a major part of my install, I'd ignore the update, until it was fixed. Here in this sub-froum most of us know what we are doing, but the regular users, seem to want to blindly do updates, without investigating what is going to happen if and when they run the update.

This is more a matter of education, most of our users are still Windows users, and they have been conditioned to run updates whenever they show up without checking to see what they do. My hope is that eventually our users become better computer users, not just Windows or Ubuntu users.

BTW my comment was for someone who assumed KDE was just another shell on top of gnome.

---

### Post by MAFoElffen on 2011-07-15
> **cariboo907 said:**
> It seems to me that if an update was going to remove a major part of my install, I'd ignore the update, until it was fixed. Here in this sub-froum most of us know what we are doing, but the regular users, seem to want to blindly do updates, without investigating what is going to happen if and when they run the update.
Was exactly my conclusion on that... Fixed some broken packages associated with that fiasco.  They kept on eye on what packages were being added, replaced and removed for a couple days... And I haven't heard from them since.  3 users where Kubuntu 11.04 and one said he was Xubuntu 11.04, but not verified on that user. (One post and then silence.)  No activity on that thread since.  One user logged that "that" update wanted to remove 20 plus packages!

---

### Post by cariboo on 2011-07-15
Yes unfortunately many of our members just disappear after their problem is solved, with no feedback.

---

