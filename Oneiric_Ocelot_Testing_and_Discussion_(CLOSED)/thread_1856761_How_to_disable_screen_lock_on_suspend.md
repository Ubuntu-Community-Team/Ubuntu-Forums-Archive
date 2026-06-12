---
title: "How to disable screen lock on suspend???"
date: 2011-10-08
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by christoph411 on 2011-10-08
Does anybody know how to disable the screen lock prompt after you suspend? :confused:

---

### Post by tista on 2011-10-08
> **christoph411 said:**
> Does anybody know how to disable the screen lock prompt after you suspend? :confused:

@christoph411,

"System Settings" -> "Screen" -> "Lock"?

cheers.

---

### Post by christoph411 on 2011-10-09
Thanks, but I already have it set to off under screen lock and it still is locked when coming back from suspend?

---

### Post by Toz on 2011-10-09
How about running gconf-editor, going to apps -> gnome-power-manager -> lock, and unchecking the suspend option. This has worked in the past.

---

### Post by bbrg548 on 2011-10-09
I think you have to install Ubuntu-Tweak. Once you have it installed, in the left panel scroll down to "Power Management", and you'll see a "Lock screen on suspend" option. Unchecking that *should* do it, I think.

---

### Post by christoph411 on 2011-10-09
The setting mentioned in the gconf-editor has no effect anymore (most likely due to the switch to Gnome 3) and in ubuntu-tweak lock on suspend is already disabled... Has the capability to disable this been removed with Gnome 3? :confused:

Also, thanks for all of the suggestions that everybody has made so far! :D

---

### Post by nrundy on 2011-10-09
> **christoph411 said:**
> The setting mentioned in the gconf-editor has no effect anymore (most likely due to the switch to Gnome 3) and in ubuntu-tweak lock on suspend is already disabled... Has the capability to disable this been removed with Gnome 3? :confused:

Also, thanks for all of the suggestions that everybody has made so far! :D

maybe you should file a bug report on it.

---

### Post by christoph411 on 2011-10-09
[COLOR="Red"][/COLOR]Thanks for the suggestion nrundy! I went ahead and filed my first bug report, so if anybody has any suggestions on how to make it better, just tell me. :D

Here's the link to it. please mark it as "This bug affects me too."
[https://bugs.launchpad.net/ubuntu/+source/gnome-power-manager/+bug/871560](https://bugs.launchpad.net/ubuntu/+source/gnome-power-manager/+bug/871560)

---

### Post by christoph411 on 2011-10-10
*bump*

---

### Post by bbrg548 on 2011-10-11
> **christoph411 said:**
> The setting mentioned in the gconf-editor has no effect anymore (most likely due to the switch to Gnome 3) and in ubuntu-tweak lock on suspend is already disabled... Has the capability to disable this been removed with Gnome 3? :confused:

Also, thanks for all of the suggestions that everybody has made so far! :D

Odd, ubuntu-tweak did the trick for me. :-k

The only other thing I can think of is to double check and make sure it's still set to "off" under the regular Settings->Screen->Lock dialog (that you hadn't flipped it back on for some testing reason and forgot to switch it back, or something), and to make sure you restart after making sure it's turned off everywhere. Basically, the stuff I would assume you already did but could have lost track of in the course of "try this and try that" that's normally involved in figuring out something like this.

---

### Post by christoph411 on 2011-10-11
Thanks for the suggestion. I went back and checked that I had the option unchecked everywhere. I checked "settings, lock," the gconf-editor, and Ubuntu-tweak to make sure it wasn't checked and did a restart and the screen still locks on suspend. :mad:

---

### Post by christoph411 on 2011-10-11
I have started a new thread since it appears that my issue is a bug and not a settings issue so Im going to mark this tread as solved.

---

