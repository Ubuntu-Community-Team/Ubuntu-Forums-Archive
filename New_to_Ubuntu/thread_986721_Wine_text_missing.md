---
title: "Wine text missing"
date: 2008-11-18
forum: New to Ubuntu
---

### Post by joruscbaoth on 2008-11-18
**What I did**
I installed Ubuntu 8.10 and added Wine 1.0.1 from the add/remove programs.

**What I see**
When I run winecfg, I receive the following message:

fixme:mixer:ALSA_MixerInit No master control found on USB Device 0x46d:0x8d7, disabling mixer

and the Wine Configuration dialog box contains zero text.  I also get zero text displayed if I run Notepad.  Text does not display even if I highlight text typed into Notepad.

Having no text makes it difficult to install/configure/run apps in Wine.

**What I've tried**
I've searched the forums and web and tried what was suggested, but I have yet to find the proverbial needle.  It appears that the Tahoma font was not included in previous versions of Wine.  This version does include it, but to be safe...

Added Tahoma font to /usr/share/wine/fonts/ overwriting what was there.
Didn't work - still no text.
Added Tahoma font to /usr/share/fonts/truetype and ran mkfontdir
Didn't work - still no text.
Added the following to regedit (as suggested over at winehq.org):
[HKEY_CURRENT_USER\Software\Wine\X11 Driver]
"ClientSideWithRender"="N"

Finally, used add/remove programs to remove Wine altogether.  Also removed the ~/.wine directory.

Reinstalled Wine from add/remove programs.  Didn't work - still no text.  

I'm sure it's something basic, but this poor noob can't seem to find it.

Any help would be generously appreciated.

- joruscbaoth

---

### Post by Farmer of Bricks on 2009-03-31
Look at ChesterBR's solution in [this thread]("http://ubuntuforums.org/showthread.php?t=244623#8"). It solved my problem.

---

### Post by nineowls on 2010-03-16
> **Farmer of Bricks said:**
> Look at ChesterBR's solution in [this thread]("http://ubuntuforums.org/showthread.php?t=244623#8"). It solved my problem.

Thank you VERY much! This solved my problem too.

---

