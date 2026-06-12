---
title: "Adding Composer Support to Rhythmbox - Stuck!"
date: 2013-03-31
forum: Programming Talk
---

### Post by theexternvoid on 2013-03-31
The fact that Rhythmbox does not support the composer tag drives me nuts, and I see web forums where people have been complaining about it for 9 years. So I figured there's an easy way to fix this: write the code. Problem is I don't know Linux Gnome programming at all. Nonetheless, seems easy enough: find everywhere some other tag is used (like "Album Artist") and mimic that.

I got the UI working. Problem is when it tries to save the update to the file then it crashes. I'm at a loss for what to do. Error is this:
(rhythmbox:4930): GLib-ERROR **: g_variant_new: expected array GVariantBuilder but the built value has type `(null)'

Occurs in rb_metadata_save() of rb-metadata-dbus-client.c. My guess is that rb_metadata_dbus_get_variant_builder() is returning something junk to g_variant_new(). I did notice that when I don't change anything in the MP3 file properties window that every property in rb_metadata_dbus_get_variant_builder() is skipped due to rb_metadata_get() returning 0...except my new composer tag. But I can't figure out why the composer tag would be any different than any other tag.

I'm looking for someone who would be willing to help with this bug. If you are willing or if you know someone who is then please let me know!

---

### Post by tehcavil on 2013-04-03
would be better to talk to the authors of rhythmbox, on mailing lists or irc or however they coordinate their development. they would know more about the internal specifics of that program than randoms on the ubuntu forums.

---

