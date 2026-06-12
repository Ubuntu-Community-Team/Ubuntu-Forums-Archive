---
title: "Kubuntu 6. 10 - Making Konsole Semi-Opaque without any patching"
date: 2006-11-18
forum: Outdated Tutorials &amp; Tips
---

### Post by underdog on 2006-11-18
Want to have a neat Semi-opaque konsole so you can read commands through it, etc? KDE provides and option to make it 'transparent', but this only shows the wallpaper and not the contents of any window, etc.

After struggling with a patch I found on KDE-look, I found a much simpler way, so I thought I would share it.

This is my first how-to, so bare with me as I struggle through it:D 

Right click on the Title bar of a Konsole window -> Configure Window Behavior

First, we must enable translucency, but turn it off in all standard cases.
On the selection menu to the left choose 'Translucency'.
Make sure all of the 'windows' check boxes are unchecked.

Now, back on the menu to the left, choose 'Window-Specific Settings'
Click 'new' to the right.

In the dialog, click 'detect', then click within your open Konsole window.
Choose 'use window class (whole application)' to ensure our settings apply every time Konsole is started.
Type something descriptive in the 'discription' field, like 'konsole opacity', and hit 'OK'.

Now, back at the 'Window-Specific Settings' dialog, choose your new setting and click 'modify'.

Under the 'Preferences' tab, set active and inactive opacity to whatever you wish (I use 65). The higher this percentage is, the more visible the Konsole will be. Hit OK on everything, and close and reopen Konsole. 

Nifty, ain't it?

Please post comments / corrections.

---

