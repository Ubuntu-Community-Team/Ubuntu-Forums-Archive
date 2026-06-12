---
title: "Desktop renaming problem"
date: 2008-04-28
forum: New to Ubuntu
---

### Post by jasex on 2008-04-28
How come I can no longer assign a blank name to icons on the desktop... trash lets me do it... but shortcuts added from the menu to the desktop no longer let me put a blank name... example they now say firefox.desktop and terminal.desktop as the names

I just upgraded from 7.10 to 8.04 last night for reference

Of course if I add a new one it retains the menu name, but I want to be able to set blank names.

---

### Post by jasex on 2008-04-29
Also... along with that issue, I cannot search in synaptic... it just hangs =(

---

### Post by jasex on 2008-05-20
No responses... What the hey.

And it's not solved... bumping shouldn't be a representation of that... that's what the Thread Solved tool is for... =(

---

### Post by iaculallad on 2008-05-20
> **jasex said:**
> Also... along with that issue, I cannot search in synaptic... it just hangs =(

Remove Synaptics first: **sudo apt-get remove synaptic**

then try reinstalling the Synaptics Package Manager

**sudo apt-get install synaptic**

For the update: **sudo apt-get install apt-utils**

---

### Post by bluefrog on 2008-05-21
you cannot "blank" names for files, you will always need at least one character.

---

### Post by El Lance-O on 2008-05-21
Yes, but it used to work. I have made several threads on multiple boards about this with no response.

I filed the bug here:

[http://bugzilla.gnome.org/show_bug.cgi?id=531237](http://bugzilla.gnome.org/show_bug.cgi?id=531237)

No progress from there either, but it wouldn't hurt to post something there.

I miss my wonderful desktop too. :(
It looked wonderful with JUST icons. I miss it oh so much..

---

### Post by El Lance-O on 2008-05-21
See, notice how NO ONE has responded whatsoever.

Everyone acts like it doesn't exist, so it never gets fixed.

---

