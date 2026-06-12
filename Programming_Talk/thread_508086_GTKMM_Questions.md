---
title: "GTKMM Questions"
date: 2007-07-23
forum: Programming Talk
---

### Post by azan00 on 2007-07-23
Hello not sure if this is the best forum, but I could not find a forum dedicated to GTKMM... I just had a couple questions about the TextBuffer and TextView class.

First is there any way to easily append a ustring onto the end of a text buffer? So far I have been doing it like this...
```

Glib::ustring in = textBuffer->get_text();
in = in + "theString";
textBuffer->set_text(in);

```
But that seems somewhat inefficient... so after looking around in the documentation I found this.

```

textBuffer->insert_at_cursor("theString");

```

But that doesn't work well because the cursor can change... 

Then my next question which ties into the above question... when I append text how do I set a scroll window to auto scroll with the text being added on?

---

### Post by AlexThomson_NZ on 2007-07-23
Sorry I can't specifcally answer your question, but here is the API reference for a TextBuffer with GTKMM

[http://www.gtkmm.org/docs/gtkmm-2.4/docs/reference/html/classGtk_1_1TextBuffer.html](http://www.gtkmm.org/docs/gtkmm-2.4/docs/reference/html/classGtk_1_1TextBuffer.html)

I think you should be able to use 'insert' and specify an arbitary position.

You can also try asking on the official gtkmm mailing list (very few people here seem to use gtkmm)

[http://mail.gnome.org/archives/gtkmm-list/](http://mail.gnome.org/archives/gtkmm-list/)

I ended up giving up with gtkmm- too broken, too unsupported and too undocumented, and going back to gtk+, which is still a dog, but slightly less frustrating...

---

### Post by azan00 on 2007-07-23
Thanks for the reply. :)

Looks like I might have to give GTK+ a look.

---

