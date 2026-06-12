---
title: "Java Form Help"
date: 2012-08-28
forum: Programming Talk
---

### Post by shadhin on 2012-08-28
[COLOR=#204a87]** **[/COLOR]I have two jFrames one is called MainMenu and the other is called  SubMenu
i want to open the SubMenu jFrame from a button which is located in MainMenu and if i close SubMenu i need MainMenu still exist.	

How can i do this by java at NetBeans?

---

### Post by prismctg on 2012-08-28
No reply from anyone !!! I m also facing the problem   :mad:

---

### Post by PaulM1985 on 2012-08-28
This is likely to be something that is setting the default close operation for your JFrames.  There is a function called setDefaultCloseOperation and something is probably calling it passing in the parameter EXIT_ON_CLOSE.  For your main window you probably want EXIT_ON_CLOSE and the child window will probably want either HIDE_ON_CLOSE or DISPOSE_ON_CLOSE.

See the Java API for more details.
[http://docs.oracle.com/javase/6/docs/api/javax/swing/JFrame.html#setDefaultCloseOperation(int](http://docs.oracle.com/javase/6/docs/api/javax/swing/JFrame.html#setDefaultCloseOperation(int))

Paul

---

### Post by ofnuts on 2012-08-28
> **prismctg said:**
> No reply from anyone !!! I m also facing the problem   :mad:Same homework?

---

### Post by shadhin on 2012-08-28
Thank you "PaulM1985" for reply.

**Easy way:**
just go to Form properties and change the value of defaultCloseOperation as Dispose.


:guitar:

---

### Post by prismctg on 2012-08-29
> **ofnuts said:**
> Same homework?
  of course :D

---

