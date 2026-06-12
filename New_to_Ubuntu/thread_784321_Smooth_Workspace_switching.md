---
title: "Smooth Workspace switching ?"
date: 2008-05-06
forum: New to Ubuntu
---

### Post by Crossroads on 2008-05-06
Switching from one workspace to another is rather abrupt here.

Can I configure it to "glide" from one workspace to another?
Or "fade" from one to the other?
Or...?

---

### Post by mister_pink on 2008-05-06
Do you have other desktop effects enabled (ie compiz). I cant remember what the different settings give you, but try right clicking your desktop, change wallpaper. Go on the visual effects tab and try selecting normal or extra. 
If this works, but still doesnt give you the desired effect, then you need to install compizconfig-settings-manager, and turn on the "desktop wall" effect in System -> Prefs ->  Advanced Desktop effects settings.

---

### Post by Paqman on 2008-05-06
Definitely recommend CCSM if you want to tweak the animations on your desktop effects. You can use it to customise them to a ridiculous level.

---

### Post by prshah on 2008-05-06
> **Crossroads said:**
> 
Can I configure it to "glide" from one workspace to another?
Or...?

If you have compiz running, you can enable the "Desktop Wall" to"glide" from one desktop to another, or "Desktop Cube" to "rotate" from one desktop to another.

To check if you have compiz active: Open a terminal (Applications-Accessories-Terminal) and give the following command```
ps -e | grep compiz
```; if it shows anything with "compiz" then compiz is active. Options for "desktop wall" etc are in System-Preferences-Advanced Desktop Settings.

If it's not active, you can (attempt) to activate it by pressing Alt+F2 and giving the command ```
compiz --replace
``` your screen should flicker/blank out for a few seconds and then come back. If it doesn't come back, press Ctrl+Alt+F1, and login in normally, then give the command ```
metacity --replace
``` and go back using Ctrl+Alt+F7.

Post here with details for above steps if facing difficulties.

---

### Post by Crossroads on 2008-05-07
Thanks guys,

I have just been running the default 7.10 LiveCD. I haven't twiddled any display settings yet.  

I'll see if compiz is running and try out your suggestions.

Absolute Ubuntu Noob!

---

### Post by Crossroads on 2008-05-07
Well, I've got compiz running.:) But I have not yet found "Desktop Wall" or "Desktop Cube". I'll have another look later.

In Visual Effects, the selection was Normal, I could not select "Extra" - graphics card not powerful enough (well, it is a bit old).

What I am looking for is some mechanism to make the transition from one workspace to another smoother. At the moment it's a jump from one screen to the next.

[I may be using the wrong term - when I say workspace I mean the screens available in the icon in the bottom-right corner]

---

### Post by mister_pink on 2008-05-07
You'll need to install compizconfig-settings-manager (Applications -> Add/Remove, search for compiz) as I said, but beware if you're on the live CD it'll forget all this when you reboot. Also bear in mind that performance isn't likely to be anywhere near as good running from the CD, so it might struggle with simple effects.

---

### Post by Golem XIV on 2008-05-07
What video card exactly do you have?  Most (very) old models are simply too weak to run Compiz.

---

### Post by Crossroads on 2008-05-07
Compiz is running here, but I do not have "Advanced Desktop Settings" in my System >> Preferences. There is an "Appearance" choice which takes me to the config window - themes, fonts, background, visual effects etc.

Is compizconfig-settings-manager" something different? If so, I'll keep on looking.

I don't mind about the LiveCD performance or "forgetfulness" as I am just exploring Ubuntu at the moment.

The graphic card is a Sapphire Radeon 9500 (not Pro)

---

