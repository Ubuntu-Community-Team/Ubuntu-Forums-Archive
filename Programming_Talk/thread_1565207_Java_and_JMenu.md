---
title: "Java and JMenu"
date: 2010-08-31
forum: Programming Talk
---

### Post by Ravenshade on 2010-08-31
Hi folks, 

Delving into swing here since I think I understand enough to actually start learning syntax >_< 

```
blueMenuBar.setPrefferedSize(blah blah blah);
```

This bit is causing problems, if there's a setPreferredSize (this appears to mean something along the lines of %'s in CSS speak) is there a static way? So if I want to say that my menu bar is 20px high (I know I know, java doesn't appear to understand pixels...).... what's the appropriate syntax for...

```
blueMenuBar.setActualSize(20, 600);
``` ?

I'm currently looking all over but I think it's something that's inherited from somewhere and I can't find where >.<

Thanks!

---

### Post by KdotJ on 2010-08-31
Hey,
Actually, you're kind of there with the preferredSize, but there's a bit more to it. As you're working with swing, I'm guessing you're familiar with [Layout Managers]("http://download.oracle.com/javase/tutorial/uiswing/layout/visual.html"). There are many to choose from, and each have their strengths. However, an important note is that some Layout Managers honour the component's PreferredSize (if you have explicitly set it), while others do not and will over write it. The reasoning for over writing it, is that it works better regarding resizing components when the size of a window is changed.

For example, if you have a FlowLayout, it will honour the preferredSize...
> The FlowLayout class puts components in a row, sized at their preferred size

---

### Post by Ravenshade on 2010-08-31
Ah, I see... yeah, I've been playing around with the layout managers.

It seems that I asked a dumb question, after all, dynamic interfaces are more flexible than absolute ones. >_<;

---

