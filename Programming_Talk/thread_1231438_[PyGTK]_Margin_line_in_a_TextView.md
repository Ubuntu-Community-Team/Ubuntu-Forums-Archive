---
title: "[PyGTK] Margin line in a TextView"
date: 2009-08-04
forum: Programming Talk
---

### Post by dom96 on 2009-08-04
Hello, i'm not sure if this is possible, but it should since xchat has it.
I'm not even sure what it's called, I'm talking about the margin line(which is grey by default) which separates the user names and messages in xchat.

So my question is how do I implement a line like that in a PyGTK TextView ?

Thanks in advance for any replies

---

### Post by days_of_ruin on 2009-08-04
You need to use gtkSourceView: ```
sudo apt-get install python-gtksourceview2
```

Docs are here: [http://www.pygtk.org/pygtksourceview/index.html]("http://www.pygtk.org/pygtksourceview/index.html")

Here is a quick and dirty example:```
#!/usr/bin/env python

import gtk
import gtksourceview2 as gtksv

window = gtk.Window()
window.set_default_size(400, 400)
window.connect("destroy", gtk.main_quit)

vp = gtk.Viewport()
sv = gtksv.View()

sv.set_right_margin_position(10)
sv.set_show_right_margin(True)

sb = gtksv.Buffer()
sb.set_text("aaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa")

sv.set_buffer(sb)

vp.add(sv)

print type(sv)
window.add(vp)

window.show_all()

gtk.main()
```

You will have to figure out how make text not run over the line, gtk.TextIter would be a good place to start: [http://www.pygtk.org/pygtk2tutorial/sec-TextIters.html]("http://www.pygtk.org/pygtk2tutorial/sec-TextIters.html")

---

### Post by dom96 on 2009-08-05
Hey, thanks for this awesome example.
I am already using TextTags, so i tried doing this with TextTags instead of TextIters.
```

#!/usr/bin/env python

import gtk
import gtksourceview2 as gtksv

window = gtk.Window()
window.set_default_size(400, 400)
window.connect("destroy", gtk.main_quit)

vp = gtk.Viewport()
sv = gtksv.View()

sv.set_right_margin_position(10)
#sv.set_left_margin_position(10)
dir(sv)
sv.set_show_right_margin(True)
#sv.set_show_left_margin(True)

sb = gtksv.Buffer()
msgTag = sb.create_tag(None)
msgTag.set_property("justification",gtk.JUSTIFY_RIGHT)
sb.insert_with_tags(sb.get_end_iter(),"Message",msgTag)

sv.set_buffer(sb)

vp.add(sv)

print type(sv)
window.add(vp)

window.show_all()

gtk.main()

```
It doesn't give me the result that I want, "Message" is on the far right, I presumed it was gonna be before the margin line but it's not, I need a way to have text before the margin line, and after it, something like in the attached image.
Would the TextIters make it work correctly ? Could you tell me how i can get it to work like shown in the image ?

---

### Post by dom96 on 2009-08-07
anybody ?

---

### Post by smartbei on 2009-08-08
The reason it is in the far right is because of the JUSTIFTY_RIGHT - change that to JUSTIFY_LEFT and it'll be before the margin line.

I haven't been able to get text to show up after the margin though.

---

### Post by dom96 on 2009-08-08
yeah that's my problem i don't know how to get the text to be before the margin line so it doesn't get over it, and i don't know how to get text after the margin, does anybody know ?

---

### Post by dom96 on 2009-08-10
anybody ?

---

