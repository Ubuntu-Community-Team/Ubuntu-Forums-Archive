---
title: "CompizConfig Settings Manager Unity settings are being ignored"
date: 2011-09-02
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by ZequeZ on 2011-09-02
Well, when I try to change any Unity settings in the CompizConfig they don't make any change, the Unity launcher keeps autohiding, doesn't matter what timeout do I use it doesn't apply... etc

Even if I disable Unity through CompizConfig, it keeps working like nothing happened...

It's just me? How could I solve it?

EDIT: Seems like restarting Unity with `unity --replace`  solved it. Though I don't know if it will come back when I restart.

EDIT2: Broken again, and didn't even restarted. Something is wrong with the CompizConfig, because is not only Unity, it's most of the settings.

---

### Post by raw_knee on 2011-09-03
I just changed the settings for Panel Opacity and the Launcher Icon Size. It seemed like the transparency was not working, but the transparency effect was not obvious until I switched the theme from Radiance to Ambiance.

---

### Post by cariboo on 2011-09-03
I've found for some settings, I have to log out, then back in again.

---

### Post by lucazade on 2011-09-04
> **ZequeZ said:**
> Well, when I try to change any Unity settings in the CompizConfig they don't make any change, the Unity launcher keeps autohiding, doesn't matter what timeout do I use it doesn't apply... etc

Even if I disable Unity through CompizConfig, it keeps working like nothing happened...

It's just me? How could I solve it?

EDIT: Seems like restarting Unity with `unity --replace`  solved it. Though I don't know if it will come back when I restart.

EDIT2: Broken again, and didn't even restarted. Something is wrong with the CompizConfig, because is not only Unity, it's most of the settings.

Get the same here

---

### Post by karmila on 2011-09-04
I use desktop edge for compiz scale and show desktop, but oneiric will not remember this settings after logout/reboot.
I have to resetting things for each session.

---

### Post by rbrick49 on 2011-09-04
> **cariboo907 said:**
> I've found for some settings, I have to log out, then back in again.
yes I do the same as you but sometimes it doesnt work just jumps around, and then unity launcher jumps out goes back.I didnt give it much of a chance as I installed fglrx straight away and I have a strange feeling this might be some of the problem but  not sure as I have gone back to 86x64 system i386 seemed ok before the beta.

---

### Post by sparker256 on 2011-09-04
> **cariboo907 said:**
> I've found for some settings, I have to log out, then back in again.
That is a change because the icon size used to be immediate. I have also found that the title-bar buttons are the same way. From a usability standpoint this sure seems to be going backwards. It would be nice to know where these kind of changes are coming from and if it is a bug or a expected behavior.  

Bill

---

### Post by cariboo on 2011-09-04
> **sparker256 said:**
> That is a change because the icon size used to be immediate. I have also found that the title-bar buttons are the same way. From a usability standpoint this sure seems to be going backwards. It would be nice to know where these kind of changes are coming from and if it is a bug or a expected behavior.  

Bill

You could always ask on the Ayatana mailing list.

---

### Post by Martin Marshalek on 2011-09-04
I don't know if it makes a difference, but I installed compizconfig without the plugins (I set synaptic to not treat recommends as dependencies) and now it updates whenever I change a setting. With the main plugins installed it would be hit and miss. It could just be a coincidence though...

---

