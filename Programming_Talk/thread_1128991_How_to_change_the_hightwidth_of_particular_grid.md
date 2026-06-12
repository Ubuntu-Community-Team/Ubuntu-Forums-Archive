---
title: "How to change the hight/width of particular grid ?"
date: 2009-04-18
forum: Programming Talk
---

### Post by tusharv on 2009-04-18
Hi All,

How can I change the height/width of particular grid ?

```
button .btn1 -text "Button1"
button .btn2 -text "Button2"

grid .btn1 -row 0 -column 0
grid .btn2 -row 2 -column 2
```

In above code there will not be any space between two button though I have skipped row and column 1. and If I make same size of 0 1 and 2 using grid rowconfigure I will get the space between them.
But this space will be fixed and depends on the size of buttons. can I make them fixed irrespective of button size ?

Thanks,
Tusharv

---

### Post by cabalas on 2009-04-18
Ok I think you might need to produce a little bit more information before people will be able to answer your question.  If you could supply the following it would help.

1) What language are you coding in?
2) What UI toolkit are you using?

---

### Post by tusharv on 2009-04-18
Ooops !!! I forgot to write that.:P
I am using TCL/TK.

---

