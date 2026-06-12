---
title: "Ruby problem"
date: 2010-01-23
forum: Programming Talk
---

### Post by danlthemanl on 2010-01-23
Hey, I'm making a text adventure game and I'm stumped. When i declare a variable inside of puts "#{var}" it creates a new line right after. Is there any way to avoid this?! Thanks

Here's a screenshot.

[IMG]http://i50.tinypic.com/2vn2jhc.png[/IMG]

---

### Post by denarced on 2010-01-23
puts creates the newline but print doesn't

---

### Post by BugenhagenXIII on 2010-01-23
> **denarced said:**
> puts creates the newline but print doesn't

danlthemanl's problem is that not only is 'puts' putting a new line at the end of the input, but also immediately after doing a variable substitution using #{...}.

I'm not sure what the problem is.  Variable substitution works fine for me (ruby 1.9.1p376).

It would help if you showed the code where you actually assign the variables values.

---

