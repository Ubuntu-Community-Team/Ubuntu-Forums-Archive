---
title: "Gtk: adding to a pre-loaded menu"
date: 2009-12-01
forum: Programming Talk
---

### Post by kumoshk on 2009-12-01
How do I add MenuItems to a Menu *after* it has been constructed and displayed on the screen?

I have a bookmarks menu, but as it stands now, when I add a bookmark it only updates after I restart the program. I couldn't seem to find any documentation for this. The only option I saw was to destroy the whole menu and recreate it, but I don't think that's what I'm supposed to do.

---

### Post by Vadi on 2009-12-01
I think you're best asking that on the gtk app devel list.

---

### Post by kumoshk on 2009-12-01
> **Vadi said:**
> I think you're best asking that on the gtk app devel list.

Sorry, I didn't know there was such a place. Is that on these forums somewhere?

---

### Post by Vadi on 2009-12-02
[http://mail.gnome.org/mailman/listinfo/gtk-app-devel-list](http://mail.gnome.org/mailman/listinfo/gtk-app-devel-list)

---

### Post by kumoshk on 2009-12-02
> **Vadi said:**
> [http://mail.gnome.org/mailman/listinfo/gtk-app-devel-list](http://mail.gnome.org/mailman/listinfo/gtk-app-devel-list)

Is there a newsgroup option for that?

---

### Post by Vadi on 2009-12-03
?

Just subscribe or post to the list directly

---

### Post by kumoshk on 2009-12-03
> **Vadi said:**
> ?

Just subscribe or post to the list directly

I was just curious. Newsgroups are pretty nice, after all. :)

Really, I just want a way where I don't have to have a dedicated email address for each and every mailing list I subscribe to (each for the purpose of a different library). I mean, some of these lists get a ton of messages every day, and I have other things to look out for. To deal with all that just to get an answer to one question seems a little odd&#8212;although I've done it, several times (and not just with programming, but with things like LilyPond, too, although I have found a better way there). I wish they'd all just get Nabble forums instead of using these mailing lists (those will double as mailing lists, if desired, btw). That's what's so nice about this forum&#8212;it's for programming in general (my question was on topic here, even if it's true I might get a better response somewhere else&#8212;they might just tell me to read the documentation, which I have on the subject, or enough to know that it doesn't answer my question, or if it does, not directly, and the tutorial link is dead).

Posts here do get much better publicity on Google than any other forum I've tried, however.

If anyone has an answer, feel free to let me know.

---

### Post by ib.lundgren on 2009-12-03
A random thought, do you remember to use your_menu_item.show()?

---

### Post by kumoshk on 2009-12-03
> **ib.lundgren said:**
> A random thought, do you remember to use your_menu_item.show()?

Ah. :) You're amazing. Thanks. I faintly remember seeing stuff about that. I thought I didn't need to since it works fine in the constructor without it. But, yeah, that was the problem.

[The first time through, I suppose show_all() takes care of things.]

---

### Post by kumoshk on 2009-12-03
Hmm. Now that this works, I can't seem to get it to remove the old MenuItem.

I see several solutions that apparently work in other languages, according to people, but they give me runtime errors in Vala. Here are the solutions I found:

myMenuItem.destroy();
Menu.remove(myMenuItem);
myMenuItem.hide(); (hiding it would be a viable solution for me here, but it doesn't work)

Or, if I could empty my menu of all items, that would work instead for what I want.

---

### Post by kumoshk on 2009-12-04
I got it to work. I'm not sure why it originally didn't, but I still got weird run-time errors afterward (although it didn't crash the program, and it functioned properly). It took me a long time, but eventually I figured out it was because one of the items in my array of MenuItems was null, and it gave me those messages when it tried to perform those actions on the null ones.

Here are the errors, just in case other people who have them try to solve the problem through an Internet search:
```
(reader:5396): Gtk-CRITICAL **: gtk_container_remove: assertion `GTK_IS_WIDGET (widget)' failed
(reader:5425): Gtk-CRITICAL **: gtk_widget_hide: assertion `GTK_IS_WIDGET (widget)' failed
(reader:5455): Gtk-CRITICAL **: gtk_object_destroy: assertion `object != NULL' failed
```

Oh, and I think I found a Gtk forum that looks like it should work pretty well (anyone else who'd rather one over a mailing list take note):
[http://www.gtkforums.com/](http://www.gtkforums.com/)

It was the first thing that came up on Google. I should have thought to search for it sooner, instead of lamenting about how the official one didn't have a forum (though it might be archived on Nabble, I suppose).

---

