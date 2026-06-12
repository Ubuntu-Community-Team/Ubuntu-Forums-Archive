---
title: "Select default media player"
date: 2008-05-27
forum: New to Ubuntu
---

### Post by DestroyMicroshaft on 2008-05-27
Is there a way to select my default media player? See when I insert a dvd, I want mplayer to open up automatically not totem or movie player or whatever, cause they dont work right.

thanks

---

### Post by sayakb on 2008-05-27
Open Nautilus preferences (Edit->Preferences->Media tab)
You can set it from there.

---

### Post by DestroyMicroshaft on 2008-05-27
Yeah, that doesnt work, the only thing I can do is slect do nothing, ask what to do, and open folder, doenst let me pick a default player.

---

### Post by KingTermite on 2008-05-27
Just a guess, but maybe you need to open a folder and navigate to the program of choice.

> **DestroyMicroshaft said:**
> Yeah, that doesnt work, the only thing I can do is slect do nothing, ask what to do, and open folder, doenst let me pick a default player.

---

### Post by philinux on 2008-05-27
After reading this.

[http://ubuntuguide.org/wiki/Ubuntu:Hardy#How_to_make_VLC_open_when_you_insert_a_DVD](http://ubuntuguide.org/wiki/Ubuntu:Hardy#How_to_make_VLC_open_when_you_insert_a_DVD)

I'll put the dvd in kill totem then open VLC manually.

---

### Post by aikiwolfie on 2008-05-27
Having read that guide, why are you selecting VLC manually? The instructions couldn't be simpler to follow.

---

### Post by mc4man on 2008-05-27
For hardy (gnome) here's easy way for vlc. Any questions ask first!
[http://ubuntuforums.org/showthread.php?p=4986640#post4986640](http://ubuntuforums.org/showthread.php?p=4986640#post4986640)

---

### Post by philinux on 2008-05-27
I might want mplayer or totem or.....

I've set the option in nautilus to do nothing now.

---

### Post by mc4man on 2008-05-27
> I might want mplayer or totem or.....
I've set the option in nautilus to do nothing now. That's sort of a blanket statement that doesn't take into account that there are three actions here. 
You can have a player as a default choice, as the default player and have autoplay enabled or not.
Totem, gsteamer or xine is always a default choice
You can add an additional player as a choice thru defaults.list. Vlc works, others may not or don't
gxine when installed is automatically added as a choice
When a player is enabled as a choice it becomes part of the r. click menu on a mounted dvd icon.
When it's the default player double clicking on icon opens the disk in file mode with the default player listed in upper panel.
None of this has anything to do with autoplay.
Only totem, gxine and the  current player listed in defaults.list can be set to autoplay

There are some potential dangers of over editing any _one line_ in defaults .list  ie. if you add vlc, decide to try xxx player, it doesn't work or whatever and then re add vlc it may or may not work properly

---

