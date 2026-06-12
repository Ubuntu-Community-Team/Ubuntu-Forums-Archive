---
title: "Can I install and play starcraft with ubuntu?"
date: 2008-06-13
forum: New to Ubuntu
---

### Post by swimm3r137@gmail.com on 2008-06-13
If so, how would I go about installing it? (I have no idea)  It worked perfect when I ran it on windows, so hopefully it will on linux too.  =)  thanks

---

### Post by gr4nf on 2008-06-13
Ha! i love that game too.

From my experience, Starcraft is one of the few games that runs very well under wine.

To get wine, use:
```

sudo apt-get install wine

```

---

### Post by swimm3r137@gmail.com on 2008-06-13
> **gr4nf said:**
> Ha! i love that game too.

From my experience, Starcraft is one of the few games that runs very well under wine.

To get wine, use:
```

sudo apt-get install wine

```

Really?  Cuz I heard it works like ****; slow, lots of freezing, etc.  GUess I'll see :)

---

### Post by Afkpuz on 2008-06-13
Make sure you have the latest video driver.
System>Administration>Hardware Drivers

Make sure the driver is installed.  Then, when launching starcraft, you can add the -opengl when launching wine.  I think that's the command, but there's one you can use that invokes opengl which I needed to play warcraft.

---

### Post by Xiong Chiamiov on 2008-06-13
I would use Wine's repos for installing Wine.  Instructions are [here]("http://www.winehq.org/site/download-deb").

I don't have any special tweaks for Starcraft.  It runs flawlessly for me, which it never did in XP.

[Here's]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=149") the page on the Wine AppDB for Broodwar.

---

### Post by swimm3r137@gmail.com on 2008-06-13
Yea, I dunno guys..  When I click multiplayer, then battlenet, it freezes and won't get past that screen.

---

### Post by Xiong Chiamiov on 2008-06-13
Have you tried looking through what others have said on the Wine AppDB?  There are usually quite a bit of useful tidbits.  I'd check the page for the original Starcraft as well.

Mm, btw, I wouldn't use an email address as your username.  These forums are extremely high trafficked, and that email will be unusable very soon.

---

### Post by RiceMonster on 2008-06-13
> **swimm3r137@gmail.com said:**
> Yea, I dunno guys..  When I click multiplayer, then battlenet, it freezes and won't get past that screen.

In my experience, everything but battle.net works. I can play it on LAN with my friends, and single player. I've never tried to get battle.net working though.

---

