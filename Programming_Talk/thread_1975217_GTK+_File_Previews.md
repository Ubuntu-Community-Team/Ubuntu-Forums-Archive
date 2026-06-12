---
title: "GTK+ File Previews"
date: 2012-05-07
forum: Programming Talk
---

### Post by MG&amp;TL on 2012-05-07
Greetings, programmers. :)

Got a bit of a problem implementing file previews in my app. 

While I can do it fine using gtk_file_chooser_get_preview_filename(), I also want to implement drag and drop. Is there a low-level GTK+ API that allows me to generate (preferably a GdkPixbuf*) a preview from a filename or URI? I'm assuming there is, as most file managers do it.

Currently I have to fallback to the default 'file', which doesn't look as good. See screenshot, the highlighted one is from the filechooserdialog, the one on the right is the un-previewed one from drag and drop.

I'm using C & GTK+3. Can easily post code samples, but didn't think it was necessary for this post.

---

