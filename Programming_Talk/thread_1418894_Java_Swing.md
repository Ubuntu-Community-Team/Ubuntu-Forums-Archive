---
title: "Java Swing"
date: 2010-03-01
forum: Programming Talk
---

### Post by blazemore on 2010-03-01
Hi all,
I'm having some problems with a programming assignment on java Swing (flow layout) and I'd appreciate some guidance or a nudge in the right direction.

For some reason only the last item I add is displaying.
The code's here
[http://pastebin.com/VxukXeHq](http://pastebin.com/VxukXeHq)
Here, only the Jlabel displays, even if I resize the window.
I know I'm probably doing something obvious wrong, can anyone point me in the right direction?
Thanks.

---

### Post by ja660k on 2010-03-01
flow layouts arnt very good for displaying data and inputs like you want, look into a grid layout,

where you specify the number of cols, and rows and it will resize with your given panel hight and width

im taking a look at your code and ill see what i can come up with

---

### Post by blazemore on 2010-03-01
> **ja660k said:**
> resize your encrypt panel when you run it,
you should see it.

flow layouts arnt very good for displaying data and inputs like you want, look into a grid layout,

where you specify the number of cols, and rows and it will resize with your given panel hight and width
Even when I resize it, the label just grows to fill the whole window.
I have to use a flow layout, it's specified.

---

### Post by ja660k on 2010-03-01
yeah i read that sorry.
ahh the days of programming 2 :)
GUI programming is a right pain in the @$$

you need to add the JBUTTON etc to the panel. not the frame.

so where you have

```

panel.setLayout( new FlowLayout());
		
		
		this.add(panel);
		this.add(inputTextField);
		this.add(encryptButton);
		this.add(decryptButton);
		this.add(resultLabel);
		this.setVisible(true);

```
you want
```

		panel.setLayout( new FlowLayout());
				
		panel.add(inputTextField);
		panel.add(encryptButton);
		panel.add(decryptButton);
		panel.add(resultLabel);

		this.setVisible(true);
                this.add(panel);

```
you just need to tweak the width and hight to get it the way you want.
you could also just add blank JLabels to fill space in the layout

:-)

---

### Post by kahumba on 2010-03-01
I learned Swing mostly by reading this:
[http://java.sun.com/docs/books/tutorial/ui/index.html](http://java.sun.com/docs/books/tutorial/ui/index.html)
it's user friendly and with complete source code.

---

### Post by blazemore on 2010-03-01
Thanks all but I got it sorted on my own by building up from an earlier example. It looked like I was trying to add to the wrong thing, yes.

---

