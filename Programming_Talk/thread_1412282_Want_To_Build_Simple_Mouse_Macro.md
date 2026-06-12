---
title: "Want To Build Simple Mouse Macro"
date: 2010-02-21
forum: Programming Talk
---

### Post by azoundria on 2010-02-21
Okay, so I have this program, and you click an item, then a menu pops up, and you click an option on that menu. However, you have to use the same option hundreds of times (it's poorly designed), and I use it a lot and I am very tired of clicking.

What I would like is to make a simple macro program. When enabled, clicking the mouse causes the following:

1) A click at the present location.

2) A click at a location offset from the original location, which I guess means the mouse moves to that position.

3) The mouse returns to the original position.

I am using Ubuntu 9.10, so xmacro wont work, even if I can manage to understand it.

I'd much prefer to remain in the Linux environment, then switch back to Windows to use AutoHotKey or similar. Besides, I'm not completely sure this can be done with a simple Macro program.

Somebody said this:

> "There aren't many good Linux equivalents"

That's because Linux doesn't need any tools for it... you write a script and, assuming the hotkey is active either out of the box or through your own work, point the hotkey event through your DE's keyboard tool to it. It's not hard. Only Windows forces the user to use third-party software to configure something like this.

So I'm hoping someone can help me get started and build what should be a simple program to do those three things above when running.

---

### Post by jpkotta on 2010-02-21
xte and xmousepos (and some scripting) should solve your problem.  Both are in the xautomation package.

---

### Post by azoundria on 2010-02-21
Great,

Can you help me get started? I'm sorry but I've not found any good guide with steps that work on Ubuntu 9.10 as of yet.

---

### Post by jpkotta on 2010-02-22
Read the man pages for xmousepos and xte.  Then fire up a terminal and start playing with them.  You probably want something like
```

xte "mouseclick 1" "usleep 100000" "mousermove 0 100" "mouseclick 1" "usleep 100000" "mousermove 0 -100"

```

---

### Post by OgreProgrammer on 2010-02-23
_[U]how do i delete my posts?_
[/U][]("http://groups.csail.mit.edu/uid/sikuli/")

---

### Post by azoundria on 2010-02-23
Yay! I got a macro working that will do the proper clicking.

And after some work I figured out how to use xbindkeys to do things.

---

### Post by PaulM1985 on 2010-02-23
Hi

I was messing around with this problem myself yesterday at work investigating automated testing.  Here is simple Java program that I wrote using the Robot class to move about the screen clicking.  You could use some of the ideas and create a loop.  In some of the places where the clicking occurs more than once, it was to bring the window to the front of the screen.

Maybe if you are doing lots of clicks in one area you could use a while loop and then give the click positions.

It sounds like you may have solved your problem but here is something that may help...

```

/*
 * To change this template, choose Tools | Templates
 * and open the template in the editor.
 */

package robottest;

import java.awt.Robot;
import java.awt.event.InputEvent;

/**
 *
 * @author pmorgan
 */
public class Main {

    /**
     * @param args the command line arguments
     */
    public static void main(String[] args) {
        // TODO code application logic here

        try
        {
        Robot r = new Robot();

        // Moves to 100, 100
        r.mouseMove(100, 100);
        System.out.println("Moved to 100, 100");

        // Sleeps
        Thread.sleep(1000);

        // Moves to 400, 400 and clicks once
        r.mouseMove(400, 400);
        r.mousePress(InputEvent.BUTTON1_MASK);
        r.mouseRelease(InputEvent.BUTTON1_MASK);
        System.out.println("Moved to 400, 400");

        // Sleeps
        Thread.sleep(1000);

        // moves and clicks once
        r.mouseMove(1246, 198);
        r.mousePress(InputEvent.BUTTON1_MASK);
        r.mouseRelease(InputEvent.BUTTON1_MASK);

        // Sleeps
        Thread.sleep(1000);

        // Moves and clicks twice
        r.mouseMove(2000, 556);
        System.out.println("Moved to 1500, 600");
        r.mousePress(InputEvent.BUTTON1_MASK);
        r.mouseRelease(InputEvent.BUTTON1_MASK);
        r.mousePress(InputEvent.BUTTON1_MASK);
        r.mouseRelease(InputEvent.BUTTON1_MASK);

        // Sleeps
        Thread.sleep(2000);

        // Moves and clicks once (start button in windows xp) 
        r.mouseMove(50, 1012);
        System.out.println("Moved to 1500, 600");
        r.mousePress(InputEvent.BUTTON1_MASK);
        r.mouseRelease(InputEvent.BUTTON1_MASK);

        Thread.sleep(500);

        // Moves and clicks once (shutdown button in windows xp)
        r.mouseMove(333, 976);
        System.out.println("Moved to 1500, 600");
        r.mousePress(InputEvent.BUTTON1_MASK);
        r.mouseRelease(InputEvent.BUTTON1_MASK);
        }
        catch (Exception e)
        {
            System.out.println("Threw an exception");
        }

    }

}

```Paul

---

