---
title: "Help with some color code"
date: 2008-02-22
forum: Programming Talk
---

### Post by Muscar on 2008-02-22
GUI.Component.App.waterColor = [0.1000000014901161, 0.1000000014901161, 1.0, 0.699999988079071];

I know that's blue, how do i get red?

:confused:

---

### Post by Soybean on 2008-02-22
Without any sort of context, it's hard to say... but if a colour is defined by four numbers, it's usually (red, green, blue, alpha). If that set of numbers gives blue, I'd guess it's a scale of 0.0-1.0 for each number. 

In that case, red is probably:
[1.0, 0.1000000014901161, 0.1000000014901161, 0.699999988079071];

Just try changing the numbers around and see what happens.

---

### Post by Muscar on 2008-02-22
Nothing happens, Here is the download for the application:

[http://www.acc.umu.se/~emilk/downloads.html](http://www.acc.umu.se/~emilk/downloads.html)

I just want to change the water color to red, so it looks like blood :lolflag:

It's in the config.cfg file

---

### Post by Muscar on 2008-02-22
Anyone!?

---

### Post by Soybean on 2008-02-25
I think the problem here may be that this isn't a programming question -- you're using a closed-source program, and it appears to be behaving strangely. You might have better luck on a forum dedicated to this program, or perhaps contacting the author directly.

---

