---
title: "Help"
date: 2012-02-29
forum: New to Ubuntu
---

### Post by mk.alien.22 on 2012-02-29
please help me guys, i logged into my gnome 3.2 session earlier today and only the wallpaper is loading (unity works ok though), nothing else is on the screen, except for the mouse pointer. any suggestions?

---

### Post by mk.alien.22 on 2012-02-29
anyone? please?
will bump again tomorrow (respecting the once-in-24hours-bumping rule), but it is annoying as hell not having gnome.

---

### Post by MG&amp;TL on 2012-02-29
Have you tried reinstalling?

```
sudo apt-get remove --purge gnome-shell
```

(removes gnome-shell, and purges config files)

```
sudo apt-get install gnome-shell
```

(reinstalls gnome-shell)

---

### Post by coolman98 on 2012-02-29
you may have a corrupted hard drive get ubuntu live cd and run "fsck/dev/whateveryerpartionnameis

---

### Post by mk.alien.22 on 2012-03-01
hi and thank you for your answers!

@[MG&TL]("http://ubuntuforums.org/member.php?u=1320682"): will that return my gnome shell to its default (factory) settings? I ask because mine is heavily modified (I have Ubuntu 11.10 and it worked perfectly fine until yesterday); I wouldn't want to go to stock gnome and redo all my modifications, so if nothing else helps then I will wait for 12.04 :)

---

### Post by aeronutt on 2012-03-01
Did a kernel update happen prior to this problem?

---

### Post by mk.alien.22 on 2012-03-01
kernel updates require a computer restart, right? if so, no it didn't. I install all the regular updates, but none which required a reboot recently.

---

### Post by mastablasta on 2012-03-01
> **mk.alien.22 said:**
> I ask because mine is heavily modified (I have Ubuntu 11.10 and it worked perfectly fine until yesterday); 
 
seriously? i mean how do you expect people can help you if you run cusotm "heavilly modifiec" version
 
as suggested the easiest way is to reinstall it since we can't possibly know what aspects you modified. but obviously one of your modifications is not working as it should. maybe a log file will provide you with a clue. or not.

---

### Post by mk.alien.22 on 2012-03-01
well I am posting in the "Absolute beginner talk", right? That should give you a clue that for me heavily modified means a dozen extensions and a couple of visual changes and a few other settings. I haven't done anything extreme, but would hate to do it all over again.
edit: all modifications were done 2-3 months ago and worked great until yesterday

---

### Post by MG&amp;TL on 2012-03-01
> **mastablasta said:**
> seriously? i mean how do you expect people can help you if you run cusotm "heavilly modifiec" version


Hey, we can do our best for the OP, it's not like we're paid to do this or anything. :)

No, it will reset gnome and anything that depends on gnome, but your (I'm expecting hand-installed) themes should be OK. Backup anything you've installed if you're worried.

---

### Post by mk.alien.22 on 2012-03-01
Thank you for your understanding [MG&TL]("http://ubuntuforums.org/member.php?u=1320682"), I know that there could be thousands of reasons why this happened and my ignorance in this matter is not making things easier. I will try your first suggestion, I can't make things worse than they are now! 
Thanks again to all of you guys, will mark this as solved.

---

