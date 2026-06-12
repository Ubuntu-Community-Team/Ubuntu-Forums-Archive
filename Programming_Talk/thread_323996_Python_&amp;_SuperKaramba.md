---
title: "Python &amp; SuperKaramba"
date: 2006-12-23
forum: Programming Talk
---

### Post by Mithrilhall on 2006-12-23
I've downloaded [http://netdragon.sourceforge.net/example.py](http://netdragon.sourceforge.net/example.py) and renamed it cool.py. I then created a cool.theme. 
 
At the bottom of the cool.py file is this: 
 
# This will be printed when the widget loads. 
print "Loaded my python extension!" 
 
 
How do I get the text "Loaded my python extension!" visible on the desktop? I'm not sure what I need to put in my cool.theme file.

---

### Post by Mithrilhall on 2006-12-27
I'm having some issues adding text to my SuparKaramba theme. If someone could point out what I'm doing wrong I would appreciate it.



Section of my test.py file:

```

def widgetClicked(widget, x, y, button):
	karamba.redrawWidget(widget)
	myText = karamba.createText(widget, 12, 50, 20, 20, "TESTING")
	karamba.toggleWidgetRedraw(widget, 1)
    pass

```


Here is my test.theme file:
```

KARAMBA x=0 BOTTOM=true w=200 h=400 LOCKED=false INTERVAL=1000
DEFAULT font="Sans" fontsize=10 shadow=2 color=255,255,255

<GROUP>
	TEXT x=12 y=0 sensor=time fontsize=12 format="hh:mm:ss" INTERVAL=1000
	TEXT x=12 y=15 sensor=time format="ddd dd.MM.yyyy"
</GROUP>

<GROUP>
	TEXT NAME=ARG x=12 y=30 value="HELLO"
</GROUP>

```

---

### Post by Mithrilhall on 2006-12-27
Nevermind...I got it working.

---

