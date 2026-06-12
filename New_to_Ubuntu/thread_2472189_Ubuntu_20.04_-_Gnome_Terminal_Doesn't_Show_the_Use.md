---
title: "Ubuntu 20.04 - Gnome Terminal Doesn't Show the User Spesific Fonts"
date: 2022-02-20
forum: New to Ubuntu
---

### Post by hulusidemir on 2022-02-20
Hello all.
I'm using Ubuntu 20.04, and making some personalizations. I installed gnome-tweaks and I installed SF UI Display Regular fonts and changed Interface Text, Document Text, Monospace Text and Legacay Window Titles.
My gnome-terminal doesn't show my font, why ? How can i install my font to gnome-terminal?

---

### Post by Impavidus on 2022-02-20
Have you tried the settings in gnome-terminal itself? Maybe it doesn't properly import gnome settings. Or at least not automatically.

I don't use gnome myself, but on xfce, the terminal can either use the system default or a setting for its own.

---

### Post by Dennis N on 2022-02-20
You need to set the terminal font in the terminal itself.
Open Preferences and select the active profile. In the dialog, you can change the font. See the screenshot.

---

### Post by MAFoElffen on 2022-03-01
> **Dennis N said:**
> You need to set the terminal font in the terminal itself.
Open Preferences and select the active profile. In the dialog, you can change the font. See the screenshot.
But... In your own ScreenShot, if you uncheck the checkbox for "Custom Font", then it should use what the system font is set to, similar to what Impavidus answered in his post. So you two are actually saying the same thing.

I am a bit confused by the OP's wording, as some of what he has said, about some of the changes he made in Gnome Tweak would be UI Theming changes (not just with the font), which I change the theme on my system, and Gnome terminal does inherit all those system theme changes... That would confirm to Impavidus, that Gnome-Terminal should inherit those system theme changes normally.

I have multiple named profiles setup in Gnome-Terminal to help me do different things in Terminal. I spend a lot of time in terminal and Console. Might as well make it feel like home.

---

