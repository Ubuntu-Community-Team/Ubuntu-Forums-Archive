---
title: "GtkWarning and Segmentaion Fault problems"
date: 2009-07-01
forum: Programming Talk
---

### Post by dom96 on 2009-07-01
Hello this is my first post on this forum regarding python development.
Well i'm trying to add colored text to a TextBuffer, and so far it was going well, but now i get errors randomly when i'm adding the text, sometimes it's Segmentation Fault and sometimes it's
```

GtkWarning: Invalid text buffer iterator: either the iterator is uninitialized, or the characters/pixbufs/widgets in the buffer have been modified since the iterator was created. You must use marks, character numbers, or line numbers to preserve a position across buffer modifications. You can apply tags and insert marks without invalidating your iterators, but any mutation that affects 'indexable' buffer contents (contents that can be referred to by character offset) will invalidate all outstanding iterators   gtk.main()

```

And sometimes it's

```

GtkWarning: gtk_text_layout_real_invalidate: assertion `layout->wrap_loop_count == 0' failed   cServer.cTextBuffer.insert_with_tags_by_name(cServer.cTextBuffer.get_end_iter(),strftime("[%H:%M:%S]", localtime()),"timeTag")

```
for each of my insert_with_tags_by_name that i call.

[PHP]
            cServer.cTextBuffer.insert_with_tags_by_name(cServer.cTextBuffer.get_end_iter(),strftime("[%H:%M:%S]", localtime()),"timeTag")
            cServer.cTextBuffer.insert_with_tags_by_name(cServer.cTextBuffer.get_end_iter()," >","highlightTag")
            cServer.cTextBuffer.insert_with_tags_by_name(cServer.cTextBuffer.get_end_iter(),cResp.nick,"nickTag")  
            cServer.cTextBuffer.insert_with_tags_by_name(cServer.cTextBuffer.get_end_iter(),"<" + " ","highlightTag")   
            cServer.cTextBuffer.insert(cServer.cTextBuffer.get_end_iter(),cResp.msg + "\n")
            #Scroll the TextView to the bottom...                                   
            endMark = cServer.cTextBuffer.create_mark(None, cServer.cTextBuffer.get_end_iter(), True)
            chatTextView.scroll_to_mark(endMark,0)
[/PHP]
And that's my code.
I would be really grateful if someone could tell me how i can fix this very random error.

---

### Post by monraaf on 2009-07-01
Are you doing this from a different thread than the one which is running the mainloop?

---

### Post by dom96 on 2009-07-01
Yes i am, so is that the issue, i can't access objects from another thread ?
Any ideas how i could access them ?
Thanks for the reply

---

### Post by monraaf on 2009-07-01
You could put the code in a function/method and schedule it to run by the 'gui' thread with gobject.idle_add(), but see the PyGTK Faq for more on how to deal with threading (section 20).

[http://faq.pygtk.org/index.py?req=index](http://faq.pygtk.org/index.py?req=index)

---

### Post by dom96 on 2009-07-01
ok, thanks a lot, i'll try that tommorow it's a bit too late for programming now.

---

### Post by dom96 on 2009-07-02
Thanks a lot using gobject.idle_add worked perfectly.Tested it 10 times :P

---

