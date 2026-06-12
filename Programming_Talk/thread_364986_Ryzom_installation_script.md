---
title: "Ryzom installation script"
date: 2007-02-18
forum: Programming Talk
---

### Post by Jiraiya_sama on 2007-02-18
I was wondering if anyone here would be interested in testing a bash script made to configure wine to run the saga of ryzom (online game). I'll post a tarball with it in a second.

---

### Post by Jiraiya_sama on 2007-02-19
[ATTACH]25656[/ATTACH]

here it is. I would appreciate if someone would test this for me.

this program downloads a 1.7GB installer and the installer unpacks about 6.7GB of data so be ready for it. It works best (for me so far anyway) with wine v0.9.30, and a trial account for ryzom is helpful to test how the game runs and patching. 3d Acceleration is needed.

---

### Post by po0f on 2007-02-19
Jiraiya_sama,

Your script might get more exposure if you post this in Gaming & Leisure.

---

### Post by justin whitaker on 2007-02-19
> **Jiraiya_sama said:**
> [ATTACH]25656[/ATTACH]

here it is. I would appreciate if someone would test this for me.

this program downloads a 1.7GB installer and the installer unpacks about 6.7GB of data so be ready for it. It works best (for me so far anyway) with wine v0.9.30, and a trial account for ryzom is helpful to test how the game runs and patching. 3d Acceleration is needed.

Nice! I will try this.

---

### Post by Jiraiya_sama on 2007-02-19
> Nice! I will try this.

great to hear. If the program works (and you'll know by the client loading,) three scripts will be put onto your desktop: Ryzom_Fullscreen.sh, Ryzom_Windowed.sh, and Patch_Ryzom.sh. After the client runs the first time and patches your game, you have to click the Patch_Ryzom script before you can load the game again. This will be the same with any patch, as the game doesn't patch itself properly in wine. After that, to start the game, click either Ryzom_Fullscreen or Ryzom_Windowed (windowed works best, and both versions run in a window to be honest; I'm still working on this>)

also, if you have problems with the mouse disappearing on you, switch wine's compatibility mode to windows 98 (enter winecfg in the terminal)

if anyone knows how to alter wine's compatibility mode through the registry, that info would be much appreciated.

> Jiraiya_sama,

Your script might get more exposure if you post this in Gaming & Leisure.

Well, I would post it in gaming, but I'm not entirely sure if it will work on other computers (I'm afraid the registry setting that are supposed to add to wine's registry won't apply on other computers because of some stuff in wine)

after I know if it works on other people's computers I'll move to gaming & leisure.

---

### Post by po0f on 2007-02-19
Jiraiya_sama,

So, PT forum dwellers are to be guinea pigs for other users?  ;)

---

### Post by Jiraiya_sama on 2007-02-19
> **po0f said:**
> Jiraiya_sama,

So, PT forum dwellers are to be guinea pigs for other users?  ;)

:lolflag: 

i thought you guys would be more willing to test something than a normal user.

---

