---
title: "[SOLVED] VB6.0 style InputBox'es in wx"
date: 2007-12-01
forum: Programming Talk
---

### Post by Majorix on 2007-12-01
In VB6.0 (which I am learning at the college currently, what a shame) you could do this:
[PHP]For i = 1 To 100
a = InputBox("Please enter a number")
Next[/PHP]
Which would get 100 numbers from the user. As you would also agree, it's impossible to do this with textboxes. You could see the genius(!) of MS here, lol.

What is a way to do this under Linux, with wx?

---

### Post by NovaAesa on 2007-12-01
Well, I don't know much about wx, but I think it could be done with text boxes. I would probably only use one text box though. When the user presses enter, you could just store that number in a variable, and then set the text of the text box to a zero length string. You would also have a counter somewhere to tell the user to stop when 100 numbers have been entered.

Tell me if this sounds impossible (seeings I have no experience with wx), but I think it might work.

---

### Post by Majorix on 2007-12-01
A good idea. Even though I have never seen that kind of code in work, there is no reason for it not to work. I will use what you suggested from now on.

Thanks a lot.

---

