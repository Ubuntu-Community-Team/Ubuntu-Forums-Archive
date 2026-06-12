---
title: "So I'm installed, and running...what next?"
date: 2008-11-26
forum: New to Ubuntu
---

### Post by 3dgimp on 2008-11-26
I've got intrepid running through wubi. I've got my gfx card set up along with compiz. And that's all fine and dandy, but now what do I do?

What are the cool things to do with ubuntu? Or cool games? Or, I dunno, anything. I just wanna play with it, and am overwhelmed with what to do.

Cheers

Ed

---

### Post by philinux on 2008-11-26
[GNOME-Look.org]("http://www.gnome-look.org/index.php?xcontentmode=170x171x172x173x174&PHPSESSID=7a9fb9d63cb13a3b004aad9c2c07180a")

Install alien-arena from synaptic

or 

sudo apt-get install alien-arena.

[GetDeb]("http://www.getdeb.net/")

---

### Post by Titan8990 on 2008-11-26
You should note that full screen games do not work well with Compiz (yet). I usually make a separate accnt with Compiz disabled for gaming.

---

### Post by jpoRS on 2008-11-26
Watch Star Wars in terminal:
[LINK]("http://www.macosxhints.com/article.php?story=20060406084728559&lsrc=osxh")
I know it says Mac, but we are all *nix, and it is the holidays, so lets just get along.

jim

---

### Post by nothingspecial on 2008-11-26
Make it look beautiful. Cubes and themes etc.
 Also start to play with the terminal, when you get used to it, it`s amazing how much you can get done easily with it.

Oh yeah, and have fun.

---

### Post by SunnyRabbiera on 2008-11-26
Theming is an essential part of the linux experience, the cool thing about linux is that you can make it look any way you want without installing dangerous software that could contain addware/spyware and be only workable for 30 days before having to pay money for a potentially harmful application.
Gaming is a little different, gaming in linux is not all there yet because of the lack of market linux has so if you want to play some major games they might not work under linux.
Now there are ways around this, you can try wine and crossover games.
Wine is a free application you can install via the repositories, it does a good job for the most part but for gaming its so so.
Crossover games is a commercial application so that means $$ but codeweavers contributes back to wine so its a good deal, but again not all games will work.

---

### Post by Persistence on 2008-11-26
Regarding the Compiz/graphics problem does it also affect games running through Wine such as World of Warcraft?

---

### Post by Keen101 on 2008-11-26
yeah, try you hand at themeing. I also recommend getting a good Linux book for you to go through. I recommend _**Beginning Ubuntu Linux: from novice to professional**_ by APRESS books.

I can recommend some games, but i don't know what kind of games your into.

Alien Arena
Urban Terror
Warzone21000
Glest

---

### Post by philinux on 2008-11-26
> **Titan8990 said:**
> You should note that full screen games do not work well with Compiz (yet). I usually make a separate accnt with Compiz disabled for gaming.

Some do but if some don't it's easier to install the fusion-icon and just disable compiz temporarily.

sudo apt-get install fusion-icon

The menu item for it appears in Apps>System Tools.
I add it to a panel.

---

### Post by DexterLB on 2008-11-26
> **Titan8990 said:**
> You should note that full screen games do not work well with Compiz (yet). I usually make a separate accnt with Compiz disabled for gaming.
I just have an on and off buttons on my panel, which turn compiz on/off. The on button executes ```
compiz --replace
``` and the off button executes ```
metacity --replace
```

---

### Post by Titan8990 on 2008-11-26
Last time I tried that, turning off Compiz also removed all my custom settings.

---

### Post by philinux on 2008-11-26
> **Titan8990 said:**
> Last time I tried that, turning off Compiz also removed all my custom settings.

fusion-icon retains settings.

---

