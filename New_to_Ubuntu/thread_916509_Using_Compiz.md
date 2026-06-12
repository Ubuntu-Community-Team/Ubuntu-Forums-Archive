---
title: "Using Compiz"
date: 2008-09-11
forum: New to Ubuntu
---

### Post by Frogbarf on 2008-09-11
What do I have to do to get the famous "cube" display? I have been unable to find a simple step by step guide; all the how-to pages seem to assume you already understand Advanced Desktop Effects.

I know to go into System>Preferences>Appearance>Visual Effects and mark "Normal" or "Extra", and I know there's a gazillion settings under System>Preferences>Advanced Desktop Effects Settings, but what to click and what to key where I cannot figure out.

For the sake of discussion, I'd like a cube with Firefox on one face, a file browser window on another face, Abiword on a third face, and character map on a fourth face. (Can you have all six faces going at one?)

Anybody willing to take me through this step by step?

---

### Post by Tatty on 2008-09-11
You need to install the compiz config settings manager (CCSM), which will let you customise your compiz settings.

```
sudo apt-get install compizconfig-settings-manager
```

EDIT: sorry i just realised you have already installed this, But ill leave it up incase someone else needing it surfs in to this thread

EDIT EDIT: You need to go to General Options->Desktop Size and increase the number of desktops to 4 (or however many you want)

Then turn on the Desktop Cube and Rotate Cube plugins.  To see the keys to use them, click on the plugins and go to the "bindings" tab

---

### Post by Zzl1xndd on 2008-09-11
You need the "Advanced Desktop Effect Settings" if you type compiz into the add/remove programs it should be the first on the list. This will give you the extra settings you need.

---

### Post by Perfect Storm on 2008-09-11
System>Preferences>Advanced Desktop Effects Settings

Click on Desktop Cube and rotate Desktop

Remember to set how many desktop you want in "general options" ---> "Desktop Size" tab.

---

### Post by Frogbarf on 2008-09-11
Yikes! It works! Amazing!

Another extremely basic question: in the bindings for Rotate Cube it says **initiate** is bound to <Control><Alt><Button1>. What is Button1? Where is a list of what the keys are named?

A slightly more advanced question (now I'm inching my way up to the intellectual level of an ordinary garden slug): how can I get the cube display in perspective?

---

### Post by Perfect Storm on 2008-09-11
Click on it ---> Grab key Combination.

Then you can set which key(s).
With middle mouse button you can also rotate the Desktop.

---

### Post by Tatty on 2008-09-11
> **Frogbarf said:**
> Another extremely basic question: in the bindings for Rotate Cube it says **initiate** is bound to <Control><Alt><Button1>. What is Button1?

Button1 means your first mouse button - usually the left mouse button.

---

### Post by Guilden_NL on 2008-09-11
Just what the doctor ordered, Many thanks, this is one of those functions where it would be nice to have working, but not one where I dropped everything to get it going.

I happened to have a wallpaper using a nice photo of two big Red Kangaroos that I took with a setting sun behind them.  When I turn the cube flattened out, it appears that the Roos are running.

---

