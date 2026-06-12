---
title: "gtkmm problems"
date: 2008-03-23
forum: Programming Talk
---

### Post by libwilliam on 2008-03-23
I am trying to get gtkmm set up and when I make my project, I get this error...

/usr/include/cairomm-1.0/cairomm/enums.h:195: error: ‘CAIRO_FONT_TYPE_ATSUI_replaced_by_CAIRO_FONT_TYPE_QUARTZ’ was not declared in this scope

When I look at the cairomm code this is what is there...
typedef enum
{
    FONT_TYPE_TOY = CAIRO_FONT_TYPE_TOY,
    FONT_TYPE_FT = CAIRO_FONT_TYPE_FT,
    FONT_TYPE_WIN32 = CAIRO_FONT_TYPE_WIN32,
    FONT_TYPE_ATSUI = CAIRO_FONT_TYPE_ATSUI
} FontType;

Anyone have any ideas on how I can fix this?

---

### Post by libwilliam on 2008-03-23
Nevermind, it's a bug in the latest cairomm in Hardy.

---

