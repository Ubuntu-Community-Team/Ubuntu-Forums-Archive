---
title: "How to change themes with Emerald?"
date: 2008-04-29
forum: New to Ubuntu
---

### Post by leotemp on 2008-04-29
So i installed emerald and its dependents via the PM and downloaded a nice looking theme (kore) and now i would like to see it in action, problem is I am to pants on the head retarded to figure out how to activate it once its imported into the Emerald Theme Manager, I can click on the new theme and highlight it but after that I am out of ideas, clicking close just closes the manager and i still have the default hardy theme, any ideas?

---

### Post by z0mbie on 2008-04-29
Install the compiz-fusion-icon package. 

Then launch it from Applications > System Tools > Compiz Fusion Icon. 

You'll notice it in the tray, click and Select Window Decorator as Emerald.

To load it automatically during login, just add it to Sessions from System > Preference > Sessions.

---

### Post by skymera on 2008-04-29
Or for compiz-fusion.
If you want it loaded by default when you boot do this:

System -> Prefs -> Advanced Desktop Settings -> Window Decorator. Tick that.

Once its ticked, click it to configure its settings. There should be a box around the middle that says "Command" in there type

```
 emerald --replace 
```

Thats what i did, it seemed to work seamless.

---

### Post by leotemp on 2008-04-29
I dont have an "Applications > System Tools" or a "System -> Prefs -> Advanced Desktop Settings ->" do i need to perhaps install something?

---

### Post by skymera on 2008-04-29
o compizconfig-settings-manager from the repos.
Sorry i shoulda' said :)

---

### Post by leotemp on 2008-04-29
well i have the advanced desktop settings now which is pretty cool but I still don't see a way of switching the themes, selecting a new one still doesn't do anything and I dont have a "system tools" under my applications menu to select.

---

### Post by bilal.17 on 2008-04-29
System -> Prefs -> Advanced Desktop Settings  instead of system tools
as for changing theme, i was perplexed with it to originally but normally you just click on the theme and it should change, but only if you window decorator is set as emerald

---

### Post by leotemp on 2008-04-29
I don't see where under the options i would set the decorator to use Emerald
under command i have:
"/usr/bin/compiz-decorator/ emerald --replace"

---

### Post by Helios1276 on 2008-04-29
the Fusion-Icon might prove handy for ya too

---

### Post by leotemp on 2008-04-29
okay, that did it, thanks!

---

### Post by Shadius on 2008-05-05
Umm...I'm confused. I'm new to Ubuntu and need help installing a theme. What do I need to install a theme. I have Compiz-Fusion set up already. What's Emerald? How do I get it?

---

