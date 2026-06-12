---
title: "Python, pygtk, clipboard, rich text?"
date: 2006-12-23
forum: Programming Talk
---

### Post by sethmahoney on 2006-12-23
Does anyone have any experience working with rich text in the pygtk clipboard dealey?  What I want to do, to copy some text, formatting included, onto the clipboard, should be totally straightforward, but, of course, it isn't (plain text is, but that doesn't really help me).

---

### Post by sethmahoney on 2006-12-23
Okay, I've got a roundabout method going: copying all my text into a gtk.TextBuffer and then using TextBuffer's clipboard-handling facilities (which is supposed to include rich text, isn't it?) to copy to the clipboard, like so:

```
citation_buffer = gtk.TextBuffer()
...
clipboard = gtk.clipboard_get("CLIPBOARD")
citation_buffer.select_range(citation_buffer.get_start_iter(), citation_buffer.get_end_iter())
citation_buffer.copy_clipboard(clipboard)

```

Only problem is, all it will paste is plain text.  So, next question: Am I maybe going about this all wrong?  What I'd like to do is construct a text string that includes formatting for pasting into an openoffice, abiword, etc. document.  And if I'm not going about it all wrong, why isn't my app actually including the formatting information?

---

### Post by sethmahoney on 2006-12-23
Update number two (in case anyone's counting): attaching the text buffer to a gtk.TextView shows everything correctly (including formatting), but I still can't paste the text as anything but plain text.  Even more bizarre, if I copy and paste directly from the TextView, it *still* pastes as plain text...

---

