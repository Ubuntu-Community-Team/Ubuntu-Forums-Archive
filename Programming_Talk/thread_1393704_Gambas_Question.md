---
title: "Gambas Question"
date: 2010-01-29
forum: Programming Talk
---

### Post by ve3tru on 2010-01-29
I'm a newbe playing with gambas and I'm a little stumped
I want a button to do 3 things in this order.
1 close the form (or close it later)
2 open a new form.
3 do a shell command.
sounds simple, but for some reason it jumps to number three if i take out the shell command it open and closes the forms ok

example

PUBLIC SUB Button1_Click()

IF ToggleButton1.Value = TRUE THEN 
Form3.Show 
Form1.close
SHELL " blah blah blah blah" WAIT 
message.Info("done")
ENDIF 
END

---

### Post by kalaharix on 2010-01-30
hi

1. If Form1 is your main start up form then closing it closes the whole program

2. Opening Form2 passes focus to it. The shell and message commands need to be in (for example) a _gotfocus() on Form2. e.g.if you have an exit button on form2 that receives focus when the form opens, then within btnExit_gotfocus(). You control what gets focus when with the hierarchy tab.

rgds

---

### Post by ve3tru on 2010-02-01
Ok thanks for the help but I'm not getting anywhere.
form 3 is  just  pictures that i use throughout my program, so im trying not put code there.
I even tried to make new forms copys of form 3 but no luck, for some reason it jumps to my shell before doing anything else. Even if the shell is in a new form. gotfocus sounds cool but i don't know how to use it. I googled it  found some info but im not sure if it even works on a new form and anyway it's not working for me. Way back when you would number the lines so you don't run into this.
thanks for the help
Peter

---

### Post by kalaharix on 2010-02-07
Hi,

Well there are (at least!) two ways of proceeding.

1.	Use a formless class as your startup class. This loads Form1 which in turn loads Form2 which then closes Form1.

2.	I suspect you do not even have to use multiple forms. Gambas is very flexible and you can layer objects in depth on a form. So for example you could have a panel (containing the photos) on the top of the form but invisible (panel1.visible=false). At the required time, panel1.visible=true then shows the photos.

rgds

---

