---
title: "Can't read some text in the web browser"
date: 2008-10-25
forum: New to Ubuntu
---

### Post by Axis on 2008-10-25
Ok, first things first, I understand the problem just not how to fix it the way I want it. I know that because I have a dark theme the text is white which is why I can't see my text sometimes, because its white.

My only thing is, how can I fix this shy of changing all of the text in ubuntu?

And it isn't all text in the web browser, IE I can read this text fine as it shows up black instead of white like many of the others.

Thanks,
Axis

---

### Post by mister_pink on 2008-10-25
Does edit -> Preferences -> Content -> Colours help you?

---

### Post by Pro-reason on 2008-10-25
There isn't a perfect solution to this.  The problem is bad web design.  People make assumptions about colours in browsers based on the colours in their browsers (typically IE, or at best Firefox on Windows).  So, they do stuff like setting the text colour to something dark, assuming that the background will be white.  Competent webmasters always make sure that they either set both foreground and background, or neither.

The workaround depends on what browser you are using.  Look at its settings.  You may be able to choose a custom theme that overrides the theme for your desktop.  You may be able to specify a custom stylesheet that overrides the stupid decisions of webmasters (although this will mess up the prettiness of some sites).

---

### Post by Axis on 2008-10-25
> **mister_pink said:**
> Does edit -> Preferences -> Content -> Colours help you?


That kinda helped, but the only way to fix it completely is force all webpages to have black backgrounds, and white text. it looks rather ugly.

---

### Post by nufros on 2008-11-13
I've got a Greasemonkey script that seemed to fix the problem for me [http://userscripts.org/scripts/show/36850]("http://userscripts.org/scripts/show/36850")

I hope it helps you out:)

---

