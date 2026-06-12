---
title: "Mysterious Gtk threads w/ Poppler"
date: 2007-12-28
forum: Programming Talk
---

### Post by kripkenstein on 2007-12-28
I'm trying to write an app which uses threading, and I just can't figure something out... any help is welcome.

I have a document-showing app. It uses Poppler to render PDFs on the screen. I want the rendering to be in a background thread, so that's how I wrote it. However, things don't work quite right.

If I create the thread using Gtk.timeout_add, then it renders perfectly. However, this doesn't really work as a 'background' thread, the GUI becomes nonresponsive. So, not good.

If I create the thread using GLib's thread_create function, then I get a true background thread - the GUI is responsive. And I see that the thread functions normally (I have some debug statements that show it goes through the same steps). **However**, Poppler gives me NO output in this case. It receives the same input... but gives empty pixbufs.

Why should a library's behavior change when it is run inside a timeout_add thread or a thread_create thread? Is there some fundamental difference between the two?

Help :)

---

