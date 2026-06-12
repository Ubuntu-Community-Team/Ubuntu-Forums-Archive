---
title: "renaming trash bin"
date: 2008-08-28
forum: New to Ubuntu
---

### Post by anemptygun on 2008-08-28
Kind of a silly request, but how must one go about changing the trash bin's name. Possibly to "the rubbish bin".

thx

---

### Post by kpkeerthi on 2008-08-28
1. Open a terminal or press ALT+F2
2. Type gconf-editor
3. Go to the node apps/nautilus/desktop
4. Change trash_icon_name to whatever you'd like.

---

### Post by anemptygun on 2008-08-28
> **kpkeerthi said:**
> 1. Open a terminal or press ALT+F2
2. Type gconf-editor
3. Go to the node apps/nautilus/desktop
4. Change trash_icon_name to whatever you'd like.

It wont seem to let me change the name of trash_icon_name. When I choose edit the only thing that it lets me edit is the value. What am I missing?

---

### Post by Dougie187 on 2008-08-28
You want to edit the value. You don't want to change the key from trash_icon_name to something else. That would make the key not work for you.

---

### Post by anemptygun on 2008-08-28
> **Dougie187 said:**
> You want to edit the value. You don't want to change the key from trash_icon_name to something else. That would make the key not work for you.
 But the only options for the value are numerical, It doesnt seem to let me put in a name...

---

### Post by t0p on 2008-08-28
**from Configuration Editor when trash_icon_name is highlighted:**
> trash_icon_name <no value>

Key Documentation

Key name: /apps/nautilus/desktop/trash_icon_name
Key owner: nautilus
Short description: Desktop wastebasket icon name
Long description: This name can be set if you want a custom name for the wastebasket icon on the desktop

If you press the spacebar, an **edit key** box appears.  You can change value type between integer, boolean, string, float and list.  I imagine the one you'll want is string.

---

### Post by anemptygun on 2008-08-28
> **t0p said:**
> **from Configuration Editor when trash_icon_name is highlighted:**


If you press the spacebar, an **edit key** box appears.  You can change value type between integer, boolean, string, float and list.  I imagine the one you'll want is string.

Ok thanks, i will try this as soon as I get home tonite, I will post if there are any issues. Otherwise I will mark as solved. 

thx :)

---

### Post by anemptygun on 2008-08-28
Ok so, it worked. Not exactly as I was thinking, it just changed the name but on the desktop and not universally. If there is an obvious way to do this, great. If not no biggie.

Thanks guys! :KS

---

### Post by anemptygun on 2008-08-31
Ok, so I was messing around trying to change it back to the way it was, and now I can't access my desktop, or nautilus. When I try to open nautilus in terminal it gives me this error:```
Eel:ERROR:(eel-preferences.c:116):preferences_gconf_value_get_string: assertion failed: (value->type == GCONF_VALUE_STRING)
Aborted

```

I'm not sure how to fix this. Any suggestions?

---

