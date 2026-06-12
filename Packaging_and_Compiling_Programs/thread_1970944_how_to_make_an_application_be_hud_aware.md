---
title: "how to make an application be hud aware"
date: 2012-05-01
forum: Packaging and Compiling Programs
---

### Post by botp on 2012-05-01
just install ubuntu 12.04 and just luv the hud ...

so my question is:

how could i make my application hud aware?
links of tutorials and simple howto would be great. 
thank you and best regards -botp

---

### Post by r-senior on 2012-05-02
What do mean by HUD aware?

HUD taps into the menu structures in Gnome as far as I can see and there's nothing special to do in your program. Mine seem to work with the HUD OK.

---

### Post by zombifier25 on 2012-05-02
As long as your software uses GTK+ or Qt (dunno if other toolkits supported, please add), then the HUD will recognize it.

---

### Post by r-senior on 2012-05-02
wx works OK.

---

### Post by randlieb on 2012-05-05
I can't get HUD to find anything. Had the same probem with the alpha and beta versions. And everything else works fine otherwise. Using a fresh install of 12.04.

For instance I type in firefox and get 4 entries all with 'fire' but does not show the firefox application. Tried gimp, inkscape and a handfull of other installed applications, all a bust! Not that I need this tool, but if it's there, it should work!

---

### Post by rg4w on 2012-05-05
> **zombifier25 said:**
> As long as your software uses GTK+ or Qt (dunno if other toolkits supported, please add), then the HUD will recognize it.
I use a tool (LiveCode) that doesn't use GTK or Qt for its menus.  Is there another way to inform HUD of what my app can do and provide triggers for its commands?

Also, HUD is ideally able to discern things beyond menu names, so I'm assuming there must be some mechanism by which a developer can provide such info to HUD.

Any guidance on this would be much appreciated. 

TIA -

---

### Post by randlieb on 2012-05-05
OOOOOPS!!! Sorry! Had come here from a search for HUD and didn't look to see what forum this thread was in. Will post my problem to the appropriate forum topic.

---

### Post by r-senior on 2012-05-05
> **randlieb said:**
> I can't get HUD to find anything. Had the same probem with the alpha and beta versions. And everything else works fine otherwise. Using a fresh install of 12.04.

For instance I type in firefox and get 4 entries all with 'fire' but does not show the firefox application. Tried gimp, inkscape and a handfull of other installed applications, all a bust! Not that I need this tool, but if it's there, it should work!
I think you misunderstand the distinction between the Dash and the HUD. The Dash (accessed via the super key or Ubuntu button) is for finding applications. The HUD is for accessing features within open applications via their menus.

So, you'd press the super key (to get the Dash) and type 'firefox' to find Firefox. Once open, you'd press alt (to get the HUD) and type 'pref' to activate the Edit-Preferences menu.

---

