---
title: "The title bar or w/e doesnt appear!!"
date: 2008-07-10
forum: New to Ubuntu
---

### Post by Mocha_Latte on 2008-07-10
[FONT="Georgia"]I was doing some stuff on Compiz and i checked on of the boxes ( i forgot which one.. I'll have to look) but when i did the title bar with maximize minimize and close buttons dissapeared! I can still put my arrow on the button and use it, but its very inconvenient and ugly. I tried restarting my computer and changing the metacity app so the buttons appear on the left side, (i thought it would make the bar pop up magically) but it didn't work I posted an image for you guys to see. Thanks.[/FONT]

---

### Post by sayakb on 2008-07-10
Open CCSM (System->Preferences->Advanced Desktop Effects Settings), Click Preferences and click Restore to Defaults button.
If you dont have CCSM, at a terminal:
```
sudo apt-get install compizconfig-settings-manager
```

---

### Post by BDNiner on 2008-07-10
There is a "window decoration" option under Effects in Compiz Config Settings Manager. make sure that it is enabled. Are you using metacity or emerald for your window decorations?

---

### Post by LowSky on 2008-07-10
go back into compiz

make sure the option that I circled is checked off

If that doesn't work go go to terminal and type this command

```
metacity --replace
```
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=77191&d=1215725009[/IMG]

---

### Post by Mocha_Latte on 2008-07-10
> **LinuxIsInnovation said:**
> Open CCSM (System->Preferences->Advanced Desktop Effects Settings), Click Preferences and click Restore to Defaults button.
If you dont have CCSM, at a terminal:
```
sudo apt-get install compizconfig-settings-manager
```
Thank you very much, I would have never guessed there was a restore to default button!  PROBLEM SOLVED. Thank you for your consideration.

---

### Post by sayakb on 2008-07-10
Lol.. Glad I could help you!! :)

---

### Post by awidel on 2010-06-03
disabled Reflection.

---

