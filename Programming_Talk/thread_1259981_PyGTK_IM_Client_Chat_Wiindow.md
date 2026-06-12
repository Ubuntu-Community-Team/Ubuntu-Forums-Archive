---
title: "PyGTK: IM Client Chat Wiindow"
date: 2009-09-07
forum: Programming Talk
---

### Post by loneowais on 2009-09-07
I'm trying to write something very similar to an IM client (for learning purposes only). I don't know how to write the Chat window. I want to display Users picture, name and message as any other IM client. The problem is that I don't know which gtk widget is best suited for it. Currently I use TextView and TextBuffers but I can't display Pictures and Links in the TextView. How does pidgin or empathy handle this?.

I'm using Glade with GtkBuilder

---

### Post by j7%&lt;RmUg on 2009-09-07
Can you post the code you currently have?

Also a gtk.TreeView is probably better than a textview.

---

### Post by loneowais on 2009-09-07
It's somewhat like this. Apparently I can't add pictures and links to it.
I would love to post output in html.

```

chat_buffer=self.gui.get_object('chat_buffer')		
chat_buffer.insert_at_cursor('User:')
chat_buffer.insert_at_cursor('Message\n\n')

```

---

### Post by j7%&lt;RmUg on 2009-09-07
I mean can you post your entire python script.

I cant tell you much from 3 lines of code.

---

### Post by ad_267 on 2009-09-07
You could have a look at the code for Emesene, which is an IM written in Python and GTK.

---

### Post by loneowais on 2009-09-07
> **nisshh said:**
> I mean can you post your entire python script.

I cant tell you much from 3 lines of code.

There is nothing much in the entire script. This is not a programing problem. I just want to know which widget in gtk will contain both Images and Text. That is all.

---

