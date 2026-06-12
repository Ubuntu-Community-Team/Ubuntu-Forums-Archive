---
title: "Python: Pull text and set it as default typed text for raw_input"
date: 2010-06-26
forum: Programming Talk
---

### Post by slooksterpsv on 2010-06-26
Ok this may seem difficult, but I'm making a simple text editor for myself and here's how it works:
```


1: $: =op test.html[enter]
10: $: =out[enter]
1: <HTML>[enter]
2: <head>[enter]
3: <title>Hello World</title>[enter]
4: </head>[enter]
5: <body>[enter]
6: Hello World, this is a program made in python by me[enter]
7: This program actually creates files[enter]
8: </body>[enter]
9: </html>[enter]
10: $: 

```

What I want to be able to do is this:

When I type in =ed 6 I can edit line 6 so if I type in this:
```

10: $: =ed 6
6: $: Hello World, this is a program made in python by me[]

```
Where [] is my cursor and I can press backspace to delete all the way to $:_ (_ being space).
I'm pulling input in via raw_input - so I'm not sure if there is a way. Pretty much I want to pull text and set it as what's typed for the raw_input, but where I can modify it. So I can press the back arrow key and go to: program and change it to html page - like you would in gedit or a regular editor or that.

I hope that makes sense, if not let me know.

---

### Post by wmcbrine on 2010-06-26
That's way beyond the scope of raw_input(). You might want to look into the "curses" module. Although, you seem to be reinventing the line-based editor (ugh), which doesn't really make sense when you have full cursor control, which curses provides.

---

### Post by slooksterpsv on 2010-06-26
> **wmcbrine said:**
> That's way beyond the scope of raw_input(). You might want to look into the "curses" module. Although, you seem to be reinventing the line-based editor (ugh), which doesn't really make sense when you have full cursor control, which curses provides.

I understand yeah it's kind of archaic, but it was just something fun that I wanted to try out and work on today just as personal project. So I'm just trying thing out with Python as I've been diving into it the past 3 days.

---

