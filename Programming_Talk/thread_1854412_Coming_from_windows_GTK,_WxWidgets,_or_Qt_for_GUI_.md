---
title: "Coming from windows: GTK, WxWidgets, or Qt for GUI development?"
date: 2011-10-04
forum: Programming Talk
---

### Post by Noble Bell on 2011-10-04
Which of the following tool kits give the best results:

1) WxWidgets
2) Qt
3) GTK

I use C++ and I want to be able to write my software one time on my Linux box and be able to use it on Windows and Mac as well as Linux. I know all three are able to do this but I may want to sell some of my applications on Windows/Mac and that kinda leaves out Qt doesn't it? 

Anyone have any advice to offer?

Thanks in advance.

---

### Post by karlson on 2011-10-04
> **Noble Bell said:**
> Which of the following tool kits give the best results:

1) WxWidgets
2) Qt
3) GTK

I use C++ and I want to be able to write my software one time on my Linux box and be able to use it on Windows and Mac as well as Linux. I know all three are able to do this but I may want to sell some of my applications on Windows/Mac and that kinda leaves out Qt doesn't it? 


It actually doesn't leave out QT at all you may need to get Commercial license to get All possible features of QT but the LGPL version is pretty extensive.

I would suggest trying all 3 and deciding what you like better.  In either case the software you distribute will have to have components of these libraries distributed with them.

---

### Post by SledgeHammer_999 on 2011-10-04
"leaves out Qt doesn't it"---> No it doesn't. If you use the LGPL license then you can distribute closed-source programs(and payware). Just don't modify the qt sources themselves.

In Linux I have used [GTKmm](www.gtk.org)(a C++ gtk binding/wrapper) extensively. For cross-platform apps I have used wxWidgets and Qt. Both work great. And I suppose so does Gtkmm, never tried it though. 

You could try all 3 of them, and then decide on what you feel more comfortable with.(api wise and style wise)

---

### Post by Noble Bell on 2011-10-04
I really like what Qt has. I was concerned about the licensing stuff. I never really understood the LGPL model that well. I guess I am challenged in that area. LOL.

---

### Post by KdotJ on 2011-10-04
I've only had real actual experience with wxWidget, and I think its really good. Its simple to pick up and has great documentation. I have had a play with Qt but not enough to make a full judgement.

---

### Post by juancarlospaco on 2011-10-04
> **Noble Bell said:**
> I want to be able to write my software one time on my Linux box and be able to use it on Windows and Mac as well as Linux. 

Anyone have any advice to offer?

Then add **HTML5** to your List, and i Suggest using it, 
more if you like C++ google for HTML5 Native Client,
which its a C++ extension, and everything can work Offline.

---

### Post by SledgeHammer_999 on 2011-10-04
> **Noble Bell said:**
> I really like what Qt has. I was concerned about the licensing stuff. I never really understood the LGPL model that well. I guess I am challenged in that area. LOL.

I think LGPL boils down to this:
Use our code in any way you want. If you modify it then you have to publish the changes. (seek a lawyer if you're going commercial though)

---

### Post by cgroza on 2011-10-04
I for one use wxWidgets.

---

### Post by LinTux on 2011-10-04
While this is not an answer to the asked question, i also want to ask which is better for me to start GUI programming with C. Which one is easier, which one is better for Linux, which one is easier to code with, which framework is more extensive, etc.

---

### Post by SledgeHammer_999 on 2011-10-04
If you want to use C then, your only option is Gtk+. wxWidgets and Qt use C++

---

### Post by hakermania on 2011-10-05
[FONT=Impact][SIZE=4][COLOR=Red][U][I][COLOR=Black]Qt for sure[/COLOR]
[/I][/U][/COLOR][/SIZE][/FONT]

---

