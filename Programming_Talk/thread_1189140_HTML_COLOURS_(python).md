---
title: "HTML COLOURS (python?)"
date: 2009-06-16
forum: Programming Talk
---

### Post by matmatmat on 2009-06-16
I have these colours:
```

#000
#FFEBCD
#fff
#56554e
#ffffff
#fff
#888
#FFEBCD
#888
#FFEBCD

```
are they HTML colours and, if so, does anyone know where I can get a list of all HTML colours (in some format that will be easy to put in a list)?
Thanks in advanced

---

### Post by Zugzwang on 2009-06-16
> **matmatmat said:**
> I have these colours:
are they HTML colours and, if so, does anyone know where I can get a list of all HTML colours (in some format that will be easy to put in a list)?


There are ~ 16.8 million different "HTML colours". You don't want to put them all in a list.

Basically, everything is a HTML colour which starts with a "#" and then has 1-6 hexadecimal digits in it (which are 0,1,2,3,4,5,6,7,8,9,A,B,C,D,E,and F, provided that you convert the string to upper-case beforehand). Leading Zeros might be missing, so "#fff" should be equivalent to "#000fff".

EDIT: If you want to have a list of "common colours", look here: [http://en.wikipedia.org/wiki/X11_color_names](http://en.wikipedia.org/wiki/X11_color_names)

---

### Post by matmatmat on 2009-06-16
Thanks for the reply, which ones should I put in & is there a way to sort the fff problem?

---

### Post by Zugzwang on 2009-06-16
> **matmatmat said:**
> Thanks for the reply, which ones should I put in & is there a way to sort the fff problem?

This is not really a problem. If your application just outputs these codes, just output only 6 digit codes. For reading code, reformat them to fit into the 6-digit scheme.

I've already linked to a colour list in my last post.

---

### Post by matmatmat on 2009-06-16
I'm wanting to check if the codes (which will be read from a file) are valid.

---

### Post by Zugzwang on 2009-06-16
> **matmatmat said:**
> I'm wanting to check if the codes (which will be read from a file) are valid.

Then check if the first character is a "#" and the other characters are hexadecimal digits and that the number of digits is >= 1 and <= 6 (good HTML pages should only have 6-digit numbers). Note that there are also some colour names that can be used instead of these codes. Google them up if you need them.

---

### Post by matmatmat on 2009-06-16
...

---

### Post by markux^Hs on 2009-06-16
> **Zugzwang said:**
> There are ~ 16.8 million different "HTML colours". You don't want to put them all in a list.

Basically, everything is a HTML colour which starts with a "#" and then has 1-6 hexadecimal digits in it (which are 0,1,2,3,4,5,6,7,8,9,A,B,C,D,E,and F, provided that you convert the string to upper-case beforehand). Leading Zeros might be missing, so "#fff" should be equivalent to "#000fff".

EDIT: If you want to have a list of "common colours", look here: [http://en.wikipedia.org/wiki/X11_color_names](http://en.wikipedia.org/wiki/X11_color_names)

Huh? #-o

I thought #FFF equated to #FFFFFF, #000 to #000000, etc.

---

### Post by markux^Hs on 2009-06-16
> **matmatmat said:**
> I'm wanting to check if the codes (which will be read from a file) are valid.

*^#[a-zA-Z0-9]{6}$*

---

### Post by days_of_ruin on 2009-06-16
```
try:
 int(color_code, 16)
except ValueError:
 return False
else:
 return True

```

Be sure to remove the '#' in color_code before hand.

---

### Post by Can+~ on 2009-06-16
6 hexadecimal digit code:

#[color=#ff0000]rr[/color][color=#00ff00]gg[/color][color=#0000ff]bb[/color]

And actually, the other 3-digit codes:

#[color=#ff0000]r[/color][color=#00ff00]g[/color][color=#0000ff]b[/color]

Example 1 (6-digit):
[INDENT][color=#FA00C9]#FA00C9[/color]

FA = 250
00 = 0
C9 = 201
[/INDENT]

Example 2 (3-digit):
[INDENT][color=#C09]#C09[/color]

C(C) = 204
0(0) = 0
9(9) = 153

Which is equivalent to [color=#CC0099]#CC0099[/color]
[/INDENT]

[http://www.w3.org/TR/2001/WD-css3-color-20010305#colorunits](http://www.w3.org/TR/2001/WD-css3-color-20010305#colorunits)
[http://en.wikipedia.org/wiki/Web_colors](http://en.wikipedia.org/wiki/Web_colors)

Btw, CSS has also other valid color notations:

[<property>-]color: [<color_name> | rgb(<int>, <int>, <int>) | rgb(<r%>, <g%>, <b%>) | #<RRGGBB> | #<RGB> ]

---

