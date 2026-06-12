---
title: "Java screen saver[school project]"
date: 2008-05-25
forum: Programming Talk
---

### Post by travist120 on 2008-05-25
Hey all, I'm having trouble, I'm wondering why the screensaver suddenly stops working when it hits a specific point on the screen. It's a school project so please bear with the noobness of the program.

```

//L7_ScreenSaver2 by Travis Moore

// Period 1

// This is a seperate project screensaver that draws lines that bounce off the edges of the screens. 

// and a second line follows up to cover it.





import javax.swing.*;

import java.awt.*;

import java.awt.event.*;

import java.text.*;

import java.util.*;





public class L7_ScreenSaver2 extends JFrame {

    public static final int NOTHING = 0;

    public static final int TOP = 1;

    public static final int RIGHT = 2;

    public static final int BOTTOM = 3;

    public static final int LEFT = 4;

    public static final int DRAW = 1;

    public static final int ERASE = 2;

    public L7_ScreenSaver2 () {   

        super("Graphics Window");

        Container container = getContentPane(); 

        

        // these numbers are the width and height of our window

        // if you want a bigger window, change the numbers

        setSize(1020, 720);   

        setVisible(true);

    }

    

    public void paint(Graphics g) {

        int across = 500, down = 500, secondAcross = 0, secondDown = 0, whichBall = NOTHING;

        int windowHorizantal = 0, windowVerticle = 0;

        int goDown = 1, goAcross = 1, areaHIT = NOTHING, randColor = 0, eraseDown = 1, eraseAcross = 1;

        Color currentColor = Color.blue;

        windowHorizantal = 1020;

        windowVerticle = 720;

        //Begin

        g.setColor(Color.black);

        g.fillRect(1, 1, windowHorizantal, windowVerticle);

        

        while (true) {

            if (whichBall == DRAW){

                randColor = (int)(Math.random() * 6) + 1;

            }

            if (randColor == 1){

                currentColor = Color.red;

            }

            if (randColor == 2){

                currentColor = Color.blue;

            }

            if (randColor == 3){

                currentColor = Color.green;

            }

            if (randColor == 4){

                currentColor = Color.white;

            }

            if (randColor == 5){

                currentColor = Color.yellow;

            }

            if (randColor == 6){

                currentColor = Color.magenta;

            }

            

            if (areaHIT == TOP){

                if (whichBall == DRAW){

                    goDown = 1;

                }

                if (whichBall == ERASE){

                    eraseDown = 1;

                }

            }

            if (areaHIT == RIGHT){

                if (whichBall == DRAW){

                    goAcross = -1;

                }

                if (whichBall == ERASE){

                    eraseAcross = -1;

                }

            }

            if (areaHIT == BOTTOM){

                if (whichBall == DRAW){

                    goDown = -1;

                }

                if (whichBall == ERASE){

                    eraseDown = -1;

                }

            }

            if (areaHIT == LEFT){

                if (whichBall == DRAW){

                    goAcross = 1;

                }

                if (whichBall == ERASE){

                    eraseAcross = 1;

                }

            }

            areaHIT = NOTHING;

            randColor = 0;

            while (areaHIT == NOTHING){

                if (across == 5){

                    areaHIT = LEFT;

                    whichBall = DRAW;

                }

                if (across == 1010){

                    areaHIT = RIGHT;

                    whichBall = DRAW;

                }

                if (down == 30){

                    areaHIT = TOP;

                    whichBall = DRAW;

                }

                if (down == 710){

                    areaHIT = BOTTOM;

                    whichBall = DRAW;

                }

                if (secondAcross == 5){

                    areaHIT = LEFT;

                    whichBall = ERASE;

                }

                if (secondAcross == 1010){

                    areaHIT = RIGHT;

                    whichBall = ERASE;

                }

                if (secondDown == 30){

                    areaHIT = TOP;

                    whichBall = ERASE;

                }

                if (secondDown == 710){

                    areaHIT = BOTTOM;

                    whichBall = ERASE;

                }

                across = across + goAcross;

                down = down + goDown;                

                secondAcross = secondAcross + eraseAcross;

                secondDown = secondDown + eraseDown;

                

                g.setColor(currentColor);

                g.fillOval(across, down, 5, 5);

                

                g.setColor(Color.black);

                g.fillOval(secondAcross, secondDown, 5, 5);

                

                delay(10);

            }

            

        }

    }   

    

    

    

    

    public void delay(int p) { 

        try { 

            Thread.sleep(p); 

        } 

        

        catch (InterruptedException e) { 

        } 

    }

    

    public static void main(String[] args) {

        L7_ScreenSaver2 prog = new L7_ScreenSaver2 ();

        prog.setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);

    }

}
```

---

### Post by NormR2 on 2008-05-25
I'm not sure what "stops working" means. Does the program exit or is it in an infinite loop?

You need to add some debugging code to your program to see what it is doing. Add some  ```
System.out.println("here I am x=" + x); 
```
statements in your code to see where it is and what values some variables have.

---

### Post by travist120 on 2008-05-25
my program is in an infinite loop, and what it does is it draws a line going over 1, and down 1, well when it hits the edge, it changes direction at a 90 degree angle and keeps going.It does this for a while, then inexplicably gets past the edge and keeps going (because of the infinite loop) at the same point every time. if you run and watch it for a while, you'll see what I mean.

---

### Post by xlinuks on 2008-05-26
I watched for several minutes and everything seems to work fine.
Perhaps it's a bug in your JVM and you should consider updating to the last one?
I tested it on Linux/Ubuntu with JDK 6 update 6.

---

### Post by Zugzwang on 2008-05-26
I don't know if that causes the problem, but you shouldn't have an infinite loop in your paint() method. 

I don't know for sure how to do this correctly, but it might be ok to call invokeLater() with some thread that causes repainting at the end of the paint() function. Another possibility is to put rendering into a seperate thread.

The reason is that an infinite loop in the paint() method will cause the GUI handling thread of Java to block, so for example it can't process the message that the program receives when someone closes the window. This might also cause painting programs as there might be other components involved in actually getting the stuff onto the screen. Similiary, the OS/window manager might think that the program has hung and stop rendering correctly.

---

### Post by achelis on 2008-05-26
InvokeLater is the way to go.

the paint-method should exit as quickly as possible as it blocks the thread listening for events* - therefore you can't close your application properly until the paint() function exits.

You can force a repaint using code similar to this in your paint() method (note you would have to change your code to remember what it should draw + you might want to use some sort of timer to control the speed - Thread.sleep(x) is not good for timing - use System.nanotime()):

```

	SwingUtilities.invokeLater(new Runnable() {
		@Override
		public void run()
		{
			L7_ScreenSaver2.this.repaint();
		}
	});

```

*I'm not entirely sure how this works - I'm sure you can read about in one of Sun's tutorials or in the javadoc.

---

### Post by xlinuks on 2008-05-26
Yet the best way is for your main class to implement the Runnable interface to do everything in a different thread, that would also require rewriting some of the rendering code.

---

### Post by achelis on 2008-05-26
Swing isn't thread-safe though, so couldn't it be messy if he doesn't use the invoke later for scheduling ?

---

### Post by xlinuks on 2008-05-26
He's got a simple task of drawing something onto the canvas of the content pane (or frame), there's nothing computing intensively, thus it's enough drawing from a separate thread onto the canvas (generally implemented through the Runnable interface unless he wants for some reason to directly extend Thread).
To avoid flickering one has to draw everything onto a java.awt.image.BufferedImage and then draw that image onto the canvas - it comes out pretty nice and smooth.
The threads issue: the following pseudo code doesn't mess the swing threads:
```

frame.setSize( 200, 200 );
frame.setDefaultCloseOperation( JFrame.EXIT_ON_CLOSE );
paintingThread.start();//a thread is launched that will paint in a neverending
//loop upon the canvas of a BufferedImage which in turn will be painted
//upon the canvas of the content pane.
//the current thread goes on running in parallel (without stopping)
//so it has nothing to do with the paintingThread we lauched.
frame.setVisible( true );

```

---

### Post by travist120 on 2008-05-26
Okay, well I'm only in Intro to Computer Science.  So when you guys say "threads" I don't know quiet exactly what it means. I'm assuming that by threads, it is classes? IDK. I put in the ```
frame.setSize( 200, 200 );
frame.setDefaultCloseOperation( JFrame.EXIT_ON_CLOSE );
paintingThread.start();//a thread is launched that will paint in a neverending
//loop upon the canvas of a BufferedImage which in turn will be painted
//upon the canvas of the content pane.
//the current thread goes on running in parallel (without stopping)
//so it has nothing to do with the paintingThread we lauched.
frame.setVisible( true );
``` but I get an error. I assume that I have to have a class or something with a frame cause I get this error ```
ymbol  : variable frame
location: class L7_ScreenSaver2
        frame.setSize( 1020, 720 );
        ^
L7_ScreenSaver2.java:30: cannot find symbol
symbol  : variable frame
location: class L7_ScreenSaver2
frame.setDefaultCloseOperation( JFrame.EXIT_ON_CLOSE );
^
L7_ScreenSaver2.java:31: cannot find symbol
symbol  : variable paintingThread
location: class L7_ScreenSaver2
paintingThread.start();//a thread is launched that will paint in a neverending
^
L7_ScreenSaver2.java:36: cannot find symbol
symbol  : variable frame
location: class L7_ScreenSaver2
frame.setVisible( true );
^
4 errors

```

Thanks for all your help.

---

### Post by achelis on 2008-05-26
1) Threads are not classes. If you're only on a beginner course I wouldn't worry about it just yet - surely your teacher will get to it.

2) As for your code you should have a variable called frame which is an instance of a JFrame for this to work. What your code does is calling a method on the object ie.

```

frame.setVisible( true );

```
calls the method setVisible on the object frame.

Hope that makes sense, I'll stop talking about threads as it seems to be out the scope of your task..

---

### Post by xlinuks on 2008-05-26
Ok, I'll create a little demo and post the source code as a NetBeans 6.1 project so that you can see in action what it's all about, ok, please wait a bit.
Threads are.. threads :) and are represented in Java by the class called java.lang.Thread

---

### Post by xlinuks on 2008-05-26
Ok, here's a short video showing how a Thread and animation in general works (ogg video of only about 700KB):
[http://xlinuks.googlepages.com/test.ogg](http://xlinuks.googlepages.com/test.ogg)

There's a bit of flickering on the video but only
because the frame rate isn't good enough, in reality
it is pretty smooth.

And the source code as a NetBeans project is attached.
Between the source code lines I made some random comments, hope they help.

---

