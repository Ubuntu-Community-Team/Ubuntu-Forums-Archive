---
title: "FAO Java Programmers: question..."
date: 2010-04-01
forum: Programming Talk
---

### Post by KdotJ on 2010-04-01
Hey all,
I have a question regarding java and using JFrames.

Let's say I have a JFrame called formA and another one named formB.
formA is my main form and formB is a kind of dialog form with some textfields on it.

Let's say that on formA there is a button which opens formB. Is there a way to open formB as if it were a message dialog? like when you do JOptionPane.showInuputDialog the form you called it from is 'locked' and you cannot do anything on that form until the dialog box has been closed.

Basically I want to use formB as a dialog box (which will allow the user to update some static Vector, declared in formA) and then when formB is closed, formA carry out some operation on the Vector.

I know what I just wrote isn't written too well and a bit confusing lol, but to anyone who understands what im after, I'd appreciate any help on it 

thanks

---

### Post by Reiger on 2010-04-01
If form B is a JDialog (rather than a JFrame) it is modal by default (you can configure that differently); and blocks other frames until it is closed.

---

### Post by KdotJ on 2010-04-01
Thats fantastic, thanks ever so much

---

