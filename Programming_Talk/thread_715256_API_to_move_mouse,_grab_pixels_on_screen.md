---
title: "API to move mouse, grab pixels on screen?"
date: 2008-03-04
forum: Programming Talk
---

### Post by solarwind on 2008-03-04
Hey all, is there a Linux API (preferably C++) to:
* Move the mouse to any coordinate on the screen.
* Get the position of the mouse on the screen.
* Get the colour value of a pixel on the screen at any given coordinate
?

---

### Post by mike_g on 2008-03-04
SDL maybe? I'm not 100% sure about setting the mouse co-ords but it does input so i imagine it should be able to do that.

---

### Post by solarwind on 2008-03-04
> **mike_g said:**
> SDL maybe? I'm not 100% sure about setting the mouse co-ords but it does input so i imagine it should be able to do that.

So SDL can work directly with X? Let's say I want to make a simple command line C++ program to get the current coordinates of the mouse and RGB values for that coordinate when run. Can SDL do that?

---

### Post by mike_g on 2008-03-04
Nah I don't think so. It will just set up a screen with double buffering to draw to, then you can get pixel values within it. Sorry, dident know that was what you were after.

---

### Post by solarwind on 2008-03-04
> **mike_g said:**
> Nah I don't think so. It will just set up a screen with double buffering to draw to, then you can get pixel values within it. Sorry, dident know that was what you were after.

It's ok, thanks for the reply anyway!

---

### Post by nanotube on 2008-03-04
well, for python, there's python-xlib ([http://python-xlib.sourceforge.net/](http://python-xlib.sourceforge.net/))

there's just plain xlib for c ([http://tronche.com/gui/x/xlib/](http://tronche.com/gui/x/xlib/))

both will be capable of doing what you say you want to do.

---

### Post by fuelnatchos on 2008-05-02
Here, try this code. It uses python-xlib and does exactly what you want ! (taken from python-linux implementation of wiiwhiteboard: sourceforge.net/project/wiiwhiteboard)

import Xlib.display
import Xlib.ext.xtest

class MouseControl:
        def __init__(self):
            self.display = Xlib.display.Display()
            self.screen = self.display.screen()
            self.root = self.screen.root

        def mouse_click(self, button):
            self.mouse_down(button)
            self.mouse_up(button)
            
        def mouse_down(self, button):   #button= 1 left, 2 middle, 3 right
            Xlib.ext.xtest.fake_input(self.display,Xlib.X.ButtonPress, button)
            self.display.sync()

        def mouse_up(self, button):
            Xlib.ext.xtest.fake_input(self.display,Xlib.X.ButtonRelease, button)
            self.display.sync() 

        def mouse_warp(self, x,y):
            self.root.warp_pointer(x,y)
            self.display.sync()
        
        def get_screen_resolution(self):
            return self.screen['width_in_pixels'], self.screen['height_in_pixels']

---

### Post by Wybiral on 2008-05-02
> **fuelnatchos said:**
>  ... 

Posting Python code...

[img]http://icanhascheezburger.files.wordpress.com/2007/04/wrong-mike.jpg[/img]

---

### Post by lapubell on 2008-05-02
hey wybiral, nice to see you again.  want to show me the right way?

---

### Post by Mr.Macdonald on 2008-05-03
If you're good with java, then the Robot class is perfect for you.

Java Doc:
[java.awt.Robot]("http://java.sun.com/j2se/1.4.2/docs/api/java/awt/Robot.html")

I have used it to do just what you want.
```

public class Robo {
	[INDENT]public static void main(String[] args) throws AWTException {
    		[INDENT]Robot robot = new Robot();
    		robot.mouseMove(100, 100);
    		robot.getPixelColor(100, 100);[/INDENT]
    	}[/INDENT]
}

```

---

### Post by LaRoza on 2008-05-03
> **lapubell said:**
> hey wybiral, nice to see you again.  want to show me the right way?

Use the tags for preserving formating. php and code are used. (There is more in the sticky on how to post)

---

### Post by solarwind on 2008-05-03
> **Mr.Macdonald said:**
> If you're good with java, then the Robot class is perfect for you.

Java Doc:
[java.awt.Robot]("http://java.sun.com/j2se/1.4.2/docs/api/java/awt/Robot.html")

I have used it to do just what you want.
```

public class Robo {
	[INDENT]public static void main(String[] args) throws AWTException {
    		[INDENT]Robot robot = new Robot();
    		robot.mouseMove(100, 100);
    		robot.getPixelColor(100, 100);[/INDENT]
    	}[/INDENT]
}

```
Java is my best language. Thanks a LOT!

---

### Post by solarwind on 2008-05-03
Hmm, this is very slow in Java though. Is there a way to do it in C++?

---

### Post by SuporteTecnicoID on 2008-11-30
Podem usar o programa:???

**movemouse**

[http://www.indexdata.com.br/Linux/Pacotes/AutoIT/movemouse](http://www.indexdata.com.br/Linux/Pacotes/AutoIT/movemouse)

atenciosamente...

SuporteTecnicoID
[www.indexdata.com.br](www.indexdata.com.br)
;-);-);-)

---

### Post by Aqlor on 2010-06-03
I know this post is basically dead but there still is a need for this.

Others and me have tried java too but this is really really and I mean **really** slow.

For example if I want to look for a red pixel on a 100 by 100 pixels square it will take just too much time.

Another thing is that with that xlib example you are just moving the mouse, that is just one of three objectives. Still missing getting the position of the mouse and getting the color value. I am not saying that with xlib it's impossible to do it, I have no clue.

It's weird how a scripting language like AutoIt can do it so much better on windows and on linux is basically impossible to get something similar to work.

SuporteTecnicoID nao me parece boa ideia deixar aqui replies em português e não me parece que movemouse faça mais do que mover o rato.

---

