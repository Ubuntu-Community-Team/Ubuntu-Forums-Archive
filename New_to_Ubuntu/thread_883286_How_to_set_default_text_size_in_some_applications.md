---
title: "How to set default text size in some applications?"
date: 2008-08-07
forum: New to Ubuntu
---

### Post by aridus on 2008-08-07
How can I set the default text and icon sizes in some applications? I have a dell laptop with a high res screen (1920 x 1200) and I can set the default font sizes for most things using System - Settings - Appearances. However some apps do not follow these settings (e.g. Skype, Zimbra) and are much too small on my screen. Is there a way to set the default size of everything for a single app (e.g. by adding a subcommand to the launcher)?

A subsidary question is how can I set the default text size in Firefox to be something than the standard setting. This is less of a bother because I can easily use Ctrl + to increase the text size - but it would be convenient if it could start up at a size that I prefer.

With grateful thanks for any help!

Martin

---

### Post by aridus on 2008-08-08
Hello folks - just asking again if anybody can help me with this? I have searched the forums and can't find any hint on this anywhere.

Thanks!

---

### Post by silkstone on 2008-08-08
In Firefox, Edit > Preferences > Content > Fonts & Colors > Advanced > and then set Minimum Font Size of 12 or whatever suits you.

Sorry I can't help with other apps.

---

### Post by aridus on 2008-08-08
> **silkstone said:**
> In Firefox, Edit > Preferences > Content > Fonts & Colors > Advanced > and then set Minimum Font Size of 12 or whatever suits you.

Sorry I can't help with other apps.

Thank you very much - that works perfectly! Now I just need to sort out the other apps, which seems to be more of a challenge!

---

### Post by mcduck on 2008-08-08
At least Skype uses Qt, instead of GTK, so Gnome's settings won't affect Skype's theme or fonts. 

If I remeber right "qt3-config" is the tool that can be used to configure the Qt theme in Gnome. You'll need to install it, and then start it from a terminal.

---

### Post by aridus on 2008-08-08
> **mcduck said:**
> At least Skype uses Qt, instead of GTK, so Gnome's settings won't affect Skype's theme or fonts. 

If I remeber right "qt3-config" is the tool that can be used to configure the Qt theme in Gnome. You'll need to install it, and then start it from a terminal.

Thanks - tried it - it changes the defalt font size in the qt config window but doesn't affect skype or zimbra.

---

### Post by sharma2008 on 2008-08-08
Thanks, its really Great..

---

### Post by mcduck on 2008-08-08
> **aridus said:**
> Thanks - tried it - it changes the defalt font size in the qt config window but doesn't affect skype or zimbra.

I just checked, and the latest Skype versions is already using Qt4.. I suppose you should find a configuration tool for that version instead of the qt3-config..

---

### Post by aridus on 2008-08-08
> **mcduck said:**
> I just checked, and the latest Skype versions is already using Qt4.. I suppose you should find a configuration tool for that version instead of the qt3-config..

Many thanks again - found qt4 config in the repository, set fonts to 12 pt and it works nicely. However, it doesn't affect all fonts in  skype. The text 'Call ordinary phones' for example, and other text, is still miniscule. In general this is definitely better though!

However, this doesn't affect Zimbra, the text of which is sooo tiny! Am still searching for a way to fix this as I want to use it instead of Evolution.

Thanks!

---

