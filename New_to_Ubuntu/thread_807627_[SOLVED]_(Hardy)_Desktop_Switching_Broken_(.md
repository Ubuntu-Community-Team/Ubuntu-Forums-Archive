---
title: "[SOLVED] (Hardy) Desktop Switching Broken :("
date: 2008-05-26
forum: New to Ubuntu
---

### Post by BassKozz on 2008-05-26
Just upgraded from Feisty (7.10) to Hardy (8.04) and for some reason my keyboard shortcuts are no longer working, specifically the desktop switching shortcut (Ctrl+Alt+ left/right/up/down)...
I checked _S_ystem->Preferences->Keyboard Shortcuts, and they are all setup properly, but for some reason when I try and use them, NOTHING HAPPENS :(
Any idea's?:confused:
Thanks in advance,
-BassKozz

---

### Post by ingrid_ozikem on 2008-05-26
Is Compiz enabled? The location of the Keyboard Shortcuts you mentioned isn't where Compiz gets its info... at least for me, the desktop switching shortcut is handled by Compiz and I need to set it in ccsm. (I think you find it under Sys -> Pref -> desktop handling / appearance or something like that... or just run ccsm)

---

### Post by BassKozz on 2008-05-26
> **ingrid_ozikem said:**
> Is Compiz enabled? The location of the Keyboard Shortcuts you mentioned isn't where Compiz gets its info... at least for me, the desktop switching shortcut is handled by Compiz and I need to set it in ccsm. (I think you find it under Sys -> Pref -> desktop handling / appearance or something like that... or just run ccsm)

That was it, I had enabled compiz, and then I disabled compiz, and the keyboard shortcuts didn't reset back to the non-compiz settings (for some reason), so after I rebooted, keyboard shortcuts are back to normal.

Thanks ingrid :D

---

