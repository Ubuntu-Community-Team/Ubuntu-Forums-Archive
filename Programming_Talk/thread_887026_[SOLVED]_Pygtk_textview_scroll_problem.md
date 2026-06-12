---
title: "[SOLVED] Pygtk textview scroll problem"
date: 2008-08-11
forum: Programming Talk
---

### Post by bubba_169 on 2008-08-11
Hello again, a new question... In pygtk, Im having problems with a textview packed into a scrolledwindow. When I first draw the textview and load text into it using the textbuffer.set_text() method, the top portion of text is displayed in the scrolledwindow. However as soon as I click on this or the textview gains keyboard focus, it automatically scrolls right to the bottom of the text. The cursor remains flashing at the right place where I clicked, up at the top of the text - I have to scroll up to see it.

Is this a "feature" of gtk or is it a bug? I have written a little example to show what I mean...(see attachment). If you run it, it will display numbers 1 through 12 but as soon as I click it it scrolls to show numbers 10 through 20. I dont personally think this is normal? Anyone know of a workaround?


EDIT:
Its OK its fixed :) All I had to do was add the following line after I inserted my text
```
buf.place_cursor(buf.get_start_iter())
```

Thats the third time I've fixed something within ten minutes of asking for help now!

---

