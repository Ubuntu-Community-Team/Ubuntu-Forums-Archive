---
title: "[SOLVED] [PyGTK] gtk.Entry set cursor position"
date: 2008-12-18
forum: Programming Talk
---

### Post by mssever on 2008-12-18
A utility I'm writing includes a gtk.Entry whose default value is the clipboard contents. Since the clipboard contents won't always fit in the Entry without scrolling, and since the most important information is at the beginning of the string, I want the first character to be visible (plus whatever other characters fit).

My approach to this has been to try to set the cursor to position 0 (the Entry has input focus by default). However, this test code produces weird results:
```
# self.text_entry is an instance of gtk.Entry
        self.text_entry.paste_clipboard()
        print self.text_entry.get_position()
        self.text_entry.set_position(0)
        self.text_entry.insert_text('test',0)
        print self.text_entry.get_position()
```The printed results are: ```
0
0
```Furthermore, the word "test" appears *after* the pasted text, but the cursor is immediately before the word "test". So not only is the cursor *not* getting moved, but get_position() is reporting incorrect values. What's wrong?


EDIT: I've attached a screenshot showing the state after the code snippets above have run.

---

### Post by mssever on 2008-12-18
I've done some more testing, and the mystery deepens. Consider this code snippet: ```
self.text_entry.paste_clipboard()
txt = self.text_entry.get_text()
print 'txt =', repr(txt)
self.text_entry.set_text('this is a test')
```I expect this code to store the current value of self.text_entry (which is the same as the clipboard contents) in txt, then change the value of self.text_entry to "this is a test".

What actually happens, though, is that txt is equal to "" and self.text_entry still contains the clipboard contents. No methods that operate on the text entry that I've tried do anything.

What confuses me is that later in the program (in a signal handler) I'm able to successfully change the text and set it all to selected. What gives?

EDIT: Correction: The string "this is a test" shows up at the very end of the current contents, being appended, rather than replacing the clipboard contents. The string "test" (see post 1) also shows up, immediately before "this is a test", even though it appears later in the source.

---

### Post by mssever on 2008-12-19
I managed to work around this problem by replacing ```
self.text_entry.paste_clipboard()
```with ```
self.text_entry.set_text(gtk.Clipboard().wait_for_text())
```However, I think that paste_clipboard() is a bit cleaner, and I still don't understand why it didn't work. Any ideas?

---

### Post by tadeboro on 2008-12-21
Hello.

I posted an explanatory post at [http://gtkforums.com/viewtopic.php?p=6454#6454](http://gtkforums.com/viewtopic.php?p=6454#6454)

---

