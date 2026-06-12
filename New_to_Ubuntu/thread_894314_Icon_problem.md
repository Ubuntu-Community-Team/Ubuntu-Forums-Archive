---
title: "Icon problem"
date: 2008-08-19
forum: New to Ubuntu
---

### Post by Troll_the_Great on 2008-08-19
Hy all!
I have a weird problem with my icons (or items) on the top panel.When I restart, the icons are all messed up (for example, the shutdown button, instead of being in the top right corner is in the middle of the panel, and so on).All icons are messed up.
Any ideas why?

---

### Post by mike1821 on 2008-08-19
Have you tried to use the "lock panel option"?

Right click in one of the icons on your bar and select the option "Lock To Panel"

I hope this helps!

---

### Post by Troll_the_Great on 2008-08-19
> **mike1821 said:**
> Have you tried to use the "lock panel option"?

Right click in one of the icons on your bar and select the option "Lock To Panel"

I hope this helps!

Yes, all the icon are looked to the panel.Is weird, it didn't happen before...

---

### Post by Troll_the_Great on 2008-08-20
Nobody?It's really annoying to rearrange my icons every time I restart...

---

### Post by Troll_the_Great on 2008-08-22
Bump!

---

### Post by Troll_the_Great on 2008-08-24
Bump!

---

### Post by Troll_the_Great on 2008-08-29
Bump...again!

---

### Post by adrien214 on 2008-08-29
> **Troll_the_Great said:**
> Bump...again!

ah! I got the same recurrent problem, I did a lot of installation and testing different ubuntu versions (x,k...) but I could never figure out why the icons would move and it would just make me insane.

anyway, [this thread]("http://ubuntuforums.org/showthread.php?t=276105") proposes to delete you gnome config file, but there was not reply or guarantee it would work...

[COLOR="Silver"]it's funny how people accumulate posts by bumping, isn't that cheating ? :P[/COLOR]

---

### Post by Troll_the_Great on 2008-08-29
> **adrien214 said:**
> ah! I got the same recurrent problem, I did a lot of installation and testing different ubuntu versions (x,k...) but I could never figure out why the icons would move and it would just make me insane.

anyway, [this thread]("http://ubuntuforums.org/showthread.php?t=276105") proposes to delete you gnome config file, but there was not reply or guarantee it would work...

[COLOR="Silver"]it's funny how people accumulate posts by bumping, isn't that cheating ? :P[/COLOR]

It's a little dramatic to delete my gnome configuration...I think I will wait until someone confirms it works.I don't want to nuke my installation for such a little thing.

---

### Post by adrien214 on 2008-08-30
okay, 

My icons got messed up again this morning when I started up, so I think that just talking about it brings about the problem... anyway I locked my icons to the panel and they didn't move.

now, I'm going to reset the gnome configuration just for your good eyes...
let's see what happens...:)

**edit** : if you have tweaked you desktop to the last snippet, forget about this method. Now it's hard to tell if this actually works because I have the feeling the full moon might mess up the icons again. The fact is that I reseted the gnome configuration, then I added a few more icons to the panel, I moved some of them with the mouse to other part of the panel (usually these should then move to another position, if any do) and none of the icons changed place afterwards.

that was on 8.04.

**edit** : I went to the launcher folder (icons) in my gnome conf folder (~/.gnome*/panel*.d/default/launchers) and I changed the organization of the icons (e.g. by size, date...) but the icons in the panel didn't move...

I suggest you launch the *gconf-editor* (type this command in the shell) and you navigate to the folder _/apps/panel/default_setup/global_ and there you look for  the option "locked_down" and you tick it. this way, you panel will be entirely locked. And post back here if your icons still move.

---

### Post by gmxgeek on 2008-08-30
This seems to happen whenever i change from a really small resolution to a really large one. I simply unlock my icons, move them, then lock them again, and they stay put. Try that and see if they behave. :)

---

### Post by Troll_the_Great on 2008-08-30
> **adrien214 said:**
> 
I suggest you launch the *gconf-editor* (type this command in the shell) and you navigate to the folder _/apps/panel/default_setup/global_ and there you look for  the option "locked_down" and you tick it. this way, you panel will be entirely locked. And post back here if your icons still move.

Nope, I tried and doesn't work.When I restart, my icons are still screwed up...

---

### Post by Troll_the_Great on 2008-08-30
> **gmxgeek said:**
> This seems to happen whenever i change from a really small resolution to a really large one. I simply unlock my icons, move them, then lock them again, and they stay put. Try that and see if they behave. :)

My problem have nothing to do with the resolution.They screw up when I restart.I've tried locking them, but no use...

---

### Post by Canuckelhead on 2008-08-30
Is your monitor on when you restart?

I had some problems similar a while back.. they were solved by turning the monitor on first...

I also had some problems with my EEE...  I had to unlock everything to solved it...

I switch between a 7 inch and 22 inch screen on the same system.

---

### Post by Troll_the_Great on 2008-08-30
> **Canuckelhead said:**
> Is your monitor on when you restart?.

I have a laptop, so my monitor turns on automatically when I power up the PC....

---

### Post by Troll_the_Great on 2008-08-31
Nobody?The strange thing is that the icons don't mess up at every restart, just now and then in a random manner.Where are the desktop settings stored?

---

### Post by Troll_the_Great on 2008-09-03
I hate to do this but...BUMP!

---

### Post by Troll_the_Great on 2008-09-04
Has this anything to do with compiz?I play Warcraft, so when I start the game I replace compiz with metacity (metacity --replace) and when I finish playing I switch to compiz (compiz --replace).Could this be the problem?

---

### Post by Troll_the_Great on 2008-09-05
Come on you linux gurus!We need you!

---

### Post by Troll_the_Great on 2008-09-08
Is there any use in bumping :(

---

### Post by Troll_the_Great on 2008-09-10
I think compiz definitely has something to do with it because it only happens when I replace compiz with metacity and vice versa.Can somebody tell me how to correct this?

---

### Post by Troll_the_Great on 2008-10-01
Bump!

---

### Post by allanlewis on 2008-11-11
Bump!

---

