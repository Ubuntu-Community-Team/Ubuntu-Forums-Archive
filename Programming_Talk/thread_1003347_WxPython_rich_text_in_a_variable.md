---
title: "WxPython rich text in a variable"
date: 2008-12-06
forum: Programming Talk
---

### Post by kumoshk on 2008-12-06
In WxPython, how do I put rich text in a variable?

I know how to make a rich text control, but that's not what I want.

I want to be able to manipulate the styled text in variables outside of my GUI and then pass it in later. I can't set the styles as I pass it as things are now.

Pseudo example of what I want:
s = RichString("<b>This</b> is <color>a</color> test.")

OR

s = RichString("This is a test.")
theStyle=TextAttrEx(…)
s.append_TextAttrEx(theStyle)

---

