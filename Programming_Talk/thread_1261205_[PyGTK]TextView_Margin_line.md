---
title: "[PyGTK]TextView Margin line"
date: 2009-09-08
forum: Programming Talk
---

### Post by dom96 on 2009-09-08
Hello, i know i asked this question before, but i can't find an answer anywhere.
I looked xchats source code but C is just way too complicated.
So all i basically want is a movable margin line in a TextView(Like the one in xchat)
So that my text will look like this
[php]
Time         dom96|Message
Time SomeOtherNick|Message
Time         dom96|Message
[/php]

Is there anyway that i could accomplish this ?

---

### Post by days_of_ruin on 2009-09-08
You should have just bumped the old thread instead of starting a new one. You just need to calculate where the line should be based on the length of the text.

---

### Post by dom96 on 2009-09-08
My problem is that i can't get the text to be positioned properly.
btw sorry for making a new thread.

---

### Post by dom96 on 2009-09-09
bump...
Whatever i try the text is not aligned the way i want it to be aligned.
here is the code i am using.
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
sv.set_show_right_margin(True)

sb = gtksv.Buffer()
msgTag = sb.create_tag(None)
msgTag.set_property("justification",gtk.JUSTIFY_RIGHT)
sb.insert(sb.get_end_iter(),"dom96")
sb.insert_with_tags(sb.get_end_iter(),"Message",msgTag)

sv.set_buffer(sb)

vp.add(sv)

window.add(vp)

window.show_all()

gtk.main()
```

it ends up being:
[PHP]
dom96Mes|sage
[/PHP]

i want it to be
[PHP]
dom96|Message
[/PHP]

---

### Post by dom96 on 2009-09-09
Anybody know why that happens ?
I want the nick to be right aligned to the margin and the message to be left aligned to the margin, which should give me this...
[PHP]
        dom96|Message
     SomeNick|Message
SomeOtherNick|Message
         Nick|Message
[/PHP]
| = Margin line

It just seems to ignore the margin even if i make a TextTag with the property "justification" set to gtk.JUSTIFY_RIGHT, and then insert text with that tag.
It just puts the text to the far right.
Could someone please help me?

---

### Post by days_of_ruin on 2009-09-09
> **dom96 said:**
> Anybody know why that happens ?
I want the nick to be right aligned to the margin and the message to be left aligned to the margin, which should give me this...
[PHP]
        dom96|Message
     SomeNick|Message
SomeOtherNick|Message
         Nick|Message
[/PHP]
| = Margin line

It just seems to ignore the margin even if i make a TextTag with the property "justification" set to gtk.JUSTIFY_RIGHT, and then insert text with that tag.
It just puts the text to the far right.
Could someone please help me?

I figured out a way to do this using two gtk.TextViews, see the attached tarball.

---

### Post by dom96 on 2009-09-10
yeah i thought about doing that and thanks for giving me an example.
But how would this work with word wrap ?

---

### Post by dom96 on 2009-09-11
bump

---

### Post by dom96 on 2009-09-11
bump again, please anybody ?:(

---

### Post by dom96 on 2009-09-12
days_of_ruin, would your example work with word wrap ?

---

### Post by days_of_ruin on 2009-09-12
> **dom96 said:**
> days_of_ruin, would your example work with word wrap ?

What do you mean by word wrap?

---

### Post by dom96 on 2009-09-13
bump
EDIT: oops i didn't see the second page...
you know word wrap..if a line is bigger then the width of the TextView it wraps the line.
[http://www.pygtk.org/docs/pygtk/class-gtktextview.html#method-gtktextview--set-wrap-mode](http://www.pygtk.org/docs/pygtk/class-gtktextview.html#method-gtktextview--set-wrap-mode)

---

### Post by dom96 on 2009-09-14
bump ^^

---

### Post by linkmaster03 on 2009-09-14
I see you already found the docs, so what exactly do you need help with? All you would need to do is add the line:

```
self.fb2.set_wrap_mode(gtk.WRAP_WORD)
```

after the line:

```
self.tb2 = get("textbuffer2")
```

---

### Post by dom96 on 2009-09-15
....
I know how to do it, all i'm saying is two textviews wouldn't share the same word wrap, it would be like this.
[PHP]
_________________________________
|        dom96|messagessss.s..s..|
|Someothernick|s.s..s.s..s..s    |
|             |Another Message   |
|________________________________|
[/PHP]

When it should be like this...
[PHP]
_________________________________
|        dom96|messagessss.s..s..|
|             |s.s..s.s..s..s    |
|Someothernick|Another Message   |
|________________________________|
[/PHP]
i.e the two TextViews wouldn't share the same word wrap.
Just like this...

---

### Post by dom96 on 2009-09-15
bump

---

### Post by dom96 on 2009-09-16
bump again...

---

### Post by dom96 on 2009-09-17
anybody ?

---

### Post by BloGTK on 2009-09-18
I'm not sure how I'd do that with a textview widget... to be honest, I'd maybe consider using a liststore instead... then you'd create a list store with three columns, and you could customize the divider between the two as well as the formatting.

It might be possible to do what you're thinking of with a standard textview, but it might be easier to rethink your approach and try using a treeview and a list store.

---

### Post by smartbei on 2009-09-18
@dom96 - This thread has been out there for a while, and previous one even longer. It could be that none of the people that frequent the forum have anything new to tell you. I suggest taking a look at a program that uses it as you want, and figuring out from its source code how have the margin line behave as you want it.

---

### Post by dom96 on 2009-09-18
@BloGTK using a liststore would be way harder, using colors... and how would word wrap work with that?

@smartbei i looked at xchats source code, but it's really hard to understand, i's written in C and there is so many files.

---

### Post by BloGTK on 2009-09-18
I decided that this was an intriguing enough challenge to see if I could do what you want to do with a list store. Here's some sample code that demonstrates how this work.

Now, the problem is that the width of the cell is a fixed size. If that works for you, great. If not, [then here's a quick HOWTO on how to let the wrap width change as the column size changes]("http://aggregat4.net/2008/08/multiline-text-in-pygtk-treeview-mini-howto/").

You can change the font formatting by setting other properties in the cellrenderer.

Feel free to steal this code if it helps you.

I hope this helps!

---

### Post by dom96 on 2009-09-19
Thanks a lot for taking the time to put this together!
This is a solution but a lot of the features that the TextView has aren't there for example, you can't select and copy text and i'm sure there is more that i would need, images in text, links in text.

Would there be anyway to make it act just like the TextView?
If not then is there anyone who knows C and could easily look at xchats source code to check how they do it ? i would really appreciate it.

---

### Post by BloGTK on 2009-09-19
I'm not sure exactly how flexible that would be.

The other solution is to completely cheat and use python-webkit and do the interface in HTML. That would give you tons of flexibility. The downside is that part of your interface would have to be programmed in HTML, CSS, and JavaScript. But, I believe that the WebKit bindings let you go between JavaScript and Python objects.

---

### Post by dom96 on 2009-09-19
Yeah that's an option too, but that would propably waste way too many resources.
And anyway xchat does it, there must be a way to do it.

---

### Post by dom96 on 2009-09-20
Is there anyone who could take a look at xchats source to see how xchat does it ?

---

### Post by dom96 on 2009-09-21
anyone ?

---

### Post by alzaf on 2009-09-22
dom96, have you thought of using a number of gtk.ListStore's packed in  a table rather using a textView as it looks like you are only displaying data?

---

### Post by dom96 on 2009-09-24
Yes, BloGTK suggested that

---

### Post by dom96 on 2009-09-26
By the way i understand it, this should work.
[PHP]
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

msgTag = sb.create_tag(None)
msgTag.set_property("justification",gtk.JUSTIFY_RIGHT)

msgTag1 = sb.create_tag(None)
msgTag1.set_property("justification",gtk.JUSTIFY_LEFT)

sb.insert_with_tags(sb.get_end_iter(),"dom96",msgTag1)
sb.insert_with_tags(sb.get_end_iter(),"Message",msgTag)

sv.set_buffer(sb)

vp.add(sv)

window.add(vp)

window.show_all()

gtk.main()
[/PHP]
but doesn't "dom96" and "Message" is just LEFT ALIGNED!
Could someone tell me why ?

---

### Post by alzaf on 2009-09-26
I don't know anything about gtksourceview but if you are looking for a quick hack then pad each name with space.

> 
#!/usr/bin/env python
import gtk
import gtksourceview2 as gtksv
import string

window = gtk.Window()
window.set_default_size(400, 400)
window.connect("destroy", gtk.main_quit)

vp = gtk.Viewport()
sv = gtksv.View()

sv.set_right_margin_position(10)
sv.set_show_right_margin(True)

sb = gtksv.Buffer()

msgTag = sb.create_tag(None)


msgTag1 = sb.create_tag(None)


name = string.rjust("dom96", 9)
sb.insert_with_tags(sb.get_end_iter(),name,msgTag1)
sb.insert_with_tags(sb.get_end_iter(),"Message",msgTag)


sv.set_buffer(sb)

vp.add(sv)

window.add(vp)

window.show_all()

gtk.main()


---

### Post by dom96 on 2009-09-27
Well i **finally** found an answer to my question, all i had to do is get the left GdkWindow of a TextView and paint text in it...

---

