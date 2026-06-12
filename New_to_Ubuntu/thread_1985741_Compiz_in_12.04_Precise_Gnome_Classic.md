---
title: "Compiz in 12.04 Precise Gnome Classic"
date: 2012-05-23
forum: New to Ubuntu
---

### Post by ibozzie on 2012-05-23
Just wondering if there was some sort of GUI for compiz in 12.04 with Gnome Classic - though I actually am not sure if I'm running metacity or compiz at this point, and not sure how to check. Assuming I am running compiz, how would I enable things like the rotating cube and wobbly windows?

---

### Post by MadmanRB on 2012-05-23
The compiz settings manager will do the same trick as it does for unity, install that if you dont have it already.
Also to get compiz running by default in gnome classic you have to manually add it into your session.
Its actually easier then that sounds, look for "startup applications" in your menu and add

> compiz --replace

in there

---

### Post by thomsebastin on 2012-05-23
and install compiz-fusion-icon from software centre which will help you determine if you're using compiz or metacity,emerald or gtk....this o that..whatever :-P

---

### Post by MadmanRB on 2012-05-23
> **thomsebastin said:**
> and install compiz-fusion-icon from software centre which will help you determine if you're using compiz or metacity,emerald or gtk....this o that..whatever :-P

Yeah installing the fusion icon isnt such a bad idea, you still may have to manually add in compiz though (had that issue with gnome classic)

---

### Post by ibozzie on 2012-05-25
Thanks, guys! I've got compiz working nicely and I've been tweaking through the compiz settings manager. However, the compiz fusion icon doesn't seem to start when I click it (it showed up under System Tools). Any idea why that might be?

---

### Post by ibozzie on 2012-05-26
OK, so weird sidenote: adding in compiz --replace to my startup applications locks my desktop, removes all icons from it, and removes my top sidebar (after a restart of course). I took out compiz --replace, restarted, and my desktop and sidebar are back to normal, and compiz still works.

---

### Post by thomsebastin on 2012-05-26
> **ibozzie said:**
> Thanks, guys! I've got compiz working nicely and I've been tweaking through the compiz settings manager. However, the compiz fusion icon doesn't seem to start when I click it (it showed up under System Tools). Any idea why that might be?
If you're using classic you should see a small icon on the top panel..did u check there..if you're still in unity u will have to change the panel settings from dconf editor..

---

### Post by ibozzie on 2012-05-26
Hm, no it's not there for some reason. It's supposed to be on the bar, right? Not inside a menu? It's also not in the "Add to panel..." list.

---

### Post by fabio.hipolito on 2012-05-28
Hi to all,

same problem here, using gnome classic.

Cheers.

---

### Post by codingman on 2012-05-28
> **ibozzie said:**
> OK, so weird sidenote: adding in compiz --replace to my startup applications locks my desktop, removes all icons from it, and removes my top sidebar (after a restart of course). I took out compiz --replace, restarted, and my desktop and sidebar are back to normal, and compiz still works.

Compiz is very unstable, does the same for me and has done ever since I started using ubuntu. It's not smart to mess with compiz a lot, unless you want a broken system :lolflag:

---

### Post by samitharansara on 2012-05-28
> **codingman said:**
> Compiz is very unstable, does the same for me and has done ever since I started using ubuntu. It's not smart to mess with compiz a lot, unless you want a broken system :lolflag:



Exactly :lolflag:

---

### Post by ibozzie on 2012-05-29
Hehehe, k, duly noted :D

---

### Post by traditionalist on 2012-05-29
Sometimes it works fine, other times it crashes as soon as you click on something. Once it is actually running with various settings it seems stable enough, but getting there can be a pain.

---

### Post by ibozzie on 2012-06-01
Yeah it's working great for me. The only issue I've noticed since I got it up and running is that now when I click a launcher on my toolbar, the icon expands normally and then turns into a black box just before it disappears and launches the program. Any clues as to what I should tweak to fix this? Like is there a file that manages that sort of thing?

---

### Post by inashdeen on 2012-06-02
just popping up here. does it mean that we can run compiz on gnome classic?

---

### Post by ibozzie on 2012-06-03
Absolutely! All you need to do is make sure you have compiz and the compiz settings manager installed, which I believe you can do from the software center.

---

### Post by traditionalist on 2012-06-03
Been working great for me since the last update, Very stable indeed;

[[IMG]http://img442.imageshack.us/img442/9255/compizconfigsettingsman.th.png[/IMG]](http://img442.imageshack.us/i/compizconfigsettingsman.png/)

---

### Post by inashdeen on 2012-06-04
Great! will try in this near future then. but, doesn't gnome classic run on mutter?

---

### Post by frogotronic on 2012-10-08
Hi All,

How can I delete all my compiz settings, or rather "restore" all the compiz settings to the default fresh install versions?

Thanks,
CH

---

### Post by zombifier25 on 2012-10-08
Run in command line:
```
gconftool-2 --recursive-unset /apps/compiz-1
```

---

### Post by frogotronic on 2012-10-08
Ok,  worked, but I also need to run the config reset

commands used:

```
$ gconftool-2 --recursive-unset /apps/compiz-1
$ gconftool-2 --recursive-unset /apps/compizconfig-1
```

Thanks,
CH

---

