---
title: "Noobish Gambas Question!"
date: 2005-05-08
forum: Programming Talk
---

### Post by Gnobody on 2005-05-08
[[IMG]http://img235.echo.cx/img235/4048/screenshot2ky.th.jpg[/IMG]](http://img235.echo.cx/my.php?image=screenshot2ky.jpg)

I am using my knowledge of VB5 to help me with Gambas, I am trying to create a simple program to test for a triangle.  But I get syntax error on line 14.  What am I doing wrong?  :-?

---

### Post by JonahRowley on 2005-05-08
It would be better to post the actual code, and not a screenshot..  I can't read that at all.

Edit:  oops, it was scaled down, I can read it now, but still, code > screenshot.

I don't know VB-style basic, so I can't be sure, but that looks OK.  I'd like to see what's above it.  Or even the whole program, it doesn't look long.

---

### Post by Kimm on 2005-05-08
If you change this line:

```

Dim A As Integer, B As Integer, C As Integer

```

To:

```

Dim A As Integer
Dim B As Integer
Dim C As Integer

```

That should work.

---

### Post by Gnobody on 2005-05-08
OK, thank that works now but it won't let me take the val of a textbox?

---

### Post by Kimm on 2005-05-09
I'm not very used to Gambas, I've only realy used VB6
I doubt that Gambas is exactly like VB, but perhaps you can be mroe exact to what your problem is? i.e. lets see the code that does not work

---

### Post by Gnobody on 2005-05-10
I get "Type mismatch: Wanted string; Got textbox instead"  whenever I try to convert a string entered in a textbox.  

Ex: weight = Val(txtweight)

---

