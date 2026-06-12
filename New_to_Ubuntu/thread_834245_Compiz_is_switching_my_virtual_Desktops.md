---
title: "Compiz is switching my virtual Desktops"
date: 2008-06-19
forum: New to Ubuntu
---

### Post by jbrown96 on 2008-06-19
The title is slightly misleading but it was the best way that I could think to word it. I use a laptop and it has the feature that allows scrolling if you drag your finger on the right edge. I love it and don't know what I would do without it. However, Compiz completely ruins it. If I so much as touch the right side of the pad, Compiz switches the Desktop. It does the fancy animation where it flips the screen. I can't stand it. 
I don't use compiz much because it kills my battery, but I'm not using the battery at all this summer (student), so I would like to use Compiz.

Is there a way to disable the screen flipping, but not scrolling all-together?

Thanks for the help

---

### Post by golgo13 on 2008-06-20
can you not get rid of compiz and set the system --> preferences --> appearence --> visual effects setting?
I got rid of compiz as it does tend to do some 'weird' stuff to other settings
what the reason you want to keep it?

---

### Post by issih on 2008-06-20
First install ccsm if you haven't already:

```
sudo apt-get install compizconfig-settings-manager
```

I think that is the right package name.

Then open ccsm from System->Preferences->Advanced Desktop Effects

go to the Viewport Switcher plugin and disable the flipping on scroll (it will say something like button4 and button 5) alternatively just disable the whole plugin.

That ought to get you sorted, you will still be able to switch from the keyboard or the little panel applet, but the trackpad will be disabled.

Hope that helps..

N.B. I think you need to be on "extra" in the visual effects tab for ccsm to be active.

---

