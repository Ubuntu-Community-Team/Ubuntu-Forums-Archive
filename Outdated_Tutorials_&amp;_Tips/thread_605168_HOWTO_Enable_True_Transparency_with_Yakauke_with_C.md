---
title: "HOWTO: Enable True Transparency with Yakauke with Compiz Fusion in KDE"
date: 2007-11-06
forum: Outdated Tutorials &amp; Tips
---

### Post by sunexplodes on 2007-11-06
After switching to KDE from the default GNOME desktop, I found I was really missing the true transparency of Gnome-Terminal when using the otherwise fantastic Yakuake drop-down terminal emulator.

[ATTACH]49364[/ATTACH]

1. Open the CompizConfig Settings Manager by typing Alt+F2 and entering "ccsm". If you don't have it installed, install it by typing "sudo apt-get install compizconfig-settings-manager" in a terminal.

2. Click on General Options, then navigate to the Opacity Settings tab. Click the "Add" button. 

3. Enter the following in the opacity windows box: "class=Yakuake", and whatever transparancy level you'd like (I used 85) under Opacity Window Values. Click OK.


And that's it! This also works for any other application you'd like to make permanently Opaque.

---

### Post by indiix2 on 2007-11-09
You've mispelt Yakuake, you have Yakauke. :)

---

### Post by sunexplodes on 2007-11-09
Blarg, and I can't edit the title. Oh well.

---

### Post by maumorales28 on 2007-11-15
Thanks men, works perfect!!

---

### Post by Cresho on 2008-01-21
This one worked for me!  I found out that you should use the well, i can't take the credit and cannot remember where I got this one from but The ^ in title=^Yakuake is a regular expression meaning »begins with«. If you use title=Yakuake instead, the opacity settings will apply to every window that has »Yakuake« anywhere in its title, like a browser window after a Google search for »Yakuake« for instance."

so use "title=^Yakuake" without parenthesis.

---

### Post by LordIshamael on 2008-12-30
hey thanks this was really useful!
a quick note: opacity is no longer under general options, but in opacity, brightness and saturation, and can be configured from there

---

