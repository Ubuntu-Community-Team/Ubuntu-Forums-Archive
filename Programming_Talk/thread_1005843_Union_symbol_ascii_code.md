---
title: "Union symbol ascii code"
date: 2008-12-08
forum: Programming Talk
---

### Post by Mr.Macdonald on 2008-12-08
I need the ascii value for the union symbol in math. I need to parse a list in python and replace the _U with union symbols. either in python or do it in abiword

---

### Post by mssever on 2008-12-08
ASCII doesn't include the union symbol. But it you pull up the character map, you can find the Unicode code point and use that.

---

### Post by s.fox on 2008-12-08
Have a look [HERE]("http://htmlhelp.com/reference/html40/entities/symbols.html")

If I understand you correctly then I think you need to use "& #8746;"

(without the space)

---

### Post by mssever on 2008-12-08
> **Ash R said:**
> Have a look [HERE]("http://htmlhelp.com/reference/html40/entities/symbols.html")

If I understand you correctly then I think you need to use "&#8746;"

(without the space)
If you're using HTML or XML, yes. In Python, it's ```
u'\u222a'
```because you have to use hex.

---

### Post by s.fox on 2008-12-08
Ahhh,  HEX.... I copied the wrong set of codes.  My bad.  LOL

---

### Post by Mr.Macdonald on 2008-12-08
Sorry I can't tell you why, but I need to be able to copy it into Abiword. But having Union symbols in Abiword is mandatory, and it prints blank in the terminal

---

### Post by mssever on 2008-12-08
> **Mr.Macdonald said:**
> Sorry I can't tell you why, but I need to be able to copy it into Abiword. But having Union symbols in Abiword is mandatory, and it prints blank in the terminal
You can copy from the character map (or some other source), or you can find documentation for whatever file format Abiword uses and programatically modify the file. The last time I used Abiword was years ago, and it didn't cut the mustard for me then. I'm sure it's changed quite a bit since then, and I don't know whether it has some sort of scripting interface.

On the other hand, if Abiword doesn't support Unicode (I have no idea whether it does), you're probably out of luck.

---

