---
title: "Java swing layout"
date: 2011-10-19
forum: Programming Talk
---

### Post by raac on 2011-10-19
[ATTACH]204826[/ATTACH]I have a main panel which contains three panels (place, date, and description columns). Each of those panels' layout is BoxLayout (Y.Axis). I know place and date will not be long strings so a set setPreferredSize, setMinimumSize, and setMaximumSize to the same size. However, description might be longer so I want to expand the column when the user resize the window, but I want it to resize only on the X-Axis, is it possible to set a fixed sized for Y-Axis only????
 
Because If I don't have a fixed size for Y, it will occupy the whole column (you can see it on the attached pic).
 
 
Thanks in advance

---

### Post by raac on 2011-10-19
Any ideas???

---

### Post by HotCupOfJava on 2011-10-19
You might want to investigate the Box class - it is a lightweight container that uses the BoxLayout. It contains methods that are designed to make the sort of thing you are doing easier.

---

### Post by ballantony on 2011-10-20
I wouldn't do it this way, but this gives a quick example:
 
public class MyFrame extends JFrame {
JLabel lblFirst, lblSecond;
JButton ok, cancel;
JTextField txt;

MyFrame()
{
this.setSize(250,150);
this.setLocationRelativeTo(null);
this.setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
lblFirst = new JLabel("First Label");
lblSecond = new JLabel("Second Label");
ok = new JButton("OK");
cancel = new JButton("Cancel");
txt = new JTextField("Enter Text Here...");
Container vert = Box.createVerticalBox();
Container horiz = Box.createHorizontalBox();
horiz.add(ok);
horiz.add(cancel);
vert.add(lblFirst);
vert.add(lblSecond);
vert.add(txt);
vert.add(horiz);
this.add(vert);
}
}

---

### Post by ofnuts on 2011-10-20
> **raac said:**
> [ATTACH]204826[/ATTACH]I have a main panel which contains three panels (place, date, and description columns). Each of those panels' layout is BoxLayout (Y.Axis). I know place and date will not be long strings so a set setPreferredSize, setMinimumSize, and setMaximumSize to the same size. However, description might be longer so I want to expand the column when the user resize the window, but I want it to resize only on the X-Axis, is it possible to set a fixed sized for Y-Axis only????
 
Because If I don't have a fixed size for Y, it will occupy the whole column (you can see it on the attached pic).
 
 
Thanks in advanceWhat is wrong with JTable?

---

### Post by karlson on 2011-10-20
OT rant.  After working for a few months with Swing I miss QT....

I am actually with ofnuts on this one.  JTable seems to be a better solution for you.  But on top of this I suggest using a GridBagLayout rather then BoxLayout.

---

### Post by ofnuts on 2011-10-21
> **karlson said:**
> OT rant.  After working for a few months with Swing I miss QT....
You could be writing IE6-compatible HTML/js, so don't complain :)

---

### Post by karlson on 2011-10-21
> **ofnuts said:**
> You could be writing IE6-compatible HTML/js, so don't complain :)

Judging by what where things are going with this project it may be the next step. :(

---

### Post by raac on 2011-10-21
Thanks alot guys!!! JTable is exactly what I wanted, I just didn't know it existed.

---

