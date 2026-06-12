---
title: "[SOLVED] Get gnome system font"
date: 2008-11-10
forum: Programming Talk
---

### Post by mihaiv on 2008-11-10
How do I get a gnome system font in C? I need to use a fixed width font in my application. I am interested to use the system fixed width font instead of just using pango_font_description_from_string("Monospace 10").

---

### Post by mihaiv on 2008-11-12
Use gconf and get the key "/desktop/gnome/interface/monospace_font_name".
```

    GConfClient *conf = gconf_client_get_default();
    char *font_name = gconf_client_get_string (conf, "/desktop/gnome/interface/monospace_font_name", NULL);
    PangoFontDescription *font_desc = pango_font_description_from_string(font_name);

```

---

