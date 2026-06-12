---
title: "Custom Theme for a gtk app?"
date: 2008-10-05
forum: Programming Talk
---

### Post by earobinson on 2008-10-05
I'm playing with pygtk and I want to write an app that has a black background, buttons, etc and white text. Is there any way to do this at all? (can I set the color for each button manually or can I set the theme for the whole app?)

Cheers.

---

### Post by days_of_ruin on 2008-10-05
To set the gtk theme for the entire application:
```
settings = gtk.settings_get_default()
settings.set_property("gtk-theme-name",gtk_theme_name)
```

---

### Post by earobinson on 2008-10-05
Cheers, Ill test this as soon as I have the chance.

---

### Post by earobinson on 2008-10-07
Hum It did not seem to work, any idea why
```
gtk_settings = gtk.settings_get_default()
gtk_settings.set_property('gtk-theme-name', 'UbuntuStudio')
```
would not work?

---

