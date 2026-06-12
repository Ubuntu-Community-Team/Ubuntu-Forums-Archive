---
title: "Bulit Drop down combo"
date: 2009-08-08
forum: Programming Talk
---

### Post by denish_hp_6383 on 2009-08-08
I need one control which will **work as combo** box as it display list of text according to user's input....
so I had use **Entry and ListViewText** widget to full fill my requirement as combo box is not sufficient for that. 

now,i make visible and invisible listviewtext**(using .show() and .hide() method)** according to text entered in entry box by user.

its work fine....but when i make it visible and invisible,other widgets which are just below from listviewtext,change their position **up and down**.(which is obvious thing) as i had used HBox and VBox for arranging widgets.

but i dont want this...is there any way to overcome this problem....like creating layer or something...

plz help me
thanks.....

---

### Post by smartbei on 2009-08-08
What gui toolkit are you using?
Could you attach source code that displays the problem, so that I can play around with it and try to find a solution?
Why not use a ComboBox? Most of the gui toolkits have something of the sort I believe.

---

