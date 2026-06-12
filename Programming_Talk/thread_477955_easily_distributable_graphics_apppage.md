---
title: "easily distributable graphics app/page?"
date: 2007-06-18
forum: Programming Talk
---

### Post by squirrelix on 2007-06-18
Uh, So, here is my problem.
  I have this great animation that I have written in OpenGL, both for C++ in Linux and C# in windows. I wanted to send this to lots of people so they could check it out and what not. However, there are libraries involved that the most tech savvy person probably doesn't have. 

  So, I thought a flash page would be good. However, I would really like to stick to my Linux box to do the development of this nice animation, and the only flash creation libraries I can find are ming. Which was working nicely until I wanted to add user input. Then, I had to write up this actionscript stuff to handle the user input. So, it was a C++ program with an ActionScript stored as a string that when executed creates a swf file. Sheesh what a pain. 

So, does anyone have any ideas for some way for me to easily distribute an animation that accepts user input from the keyboard and able to be developed on a Linux platform. (I am picky, I know :P

Thanks!
-- Squirrelix

---

### Post by hod139 on 2007-06-18
[jogl]("https://jogl.dev.java.net/") is developing nicely, and Java is pretty easy to install.  GLUT is another alternative, and you can include the GLUT library with your code.

---

### Post by squirrelix on 2007-06-19
I'll check out that jogl. 
The other problem I had with OpenGL/GLUT was the performance on various graphics cards. On one machine, I get a lot of flickering, on another the entire display gets a little slow. *shrug*.

Thanks for the info.
-- Squirrelix

---

### Post by HackingYodel on 2007-06-20
### Disclaimer ### You all are way out of my league.

I hope this isn't stupid, but have you considered [Proce55ing]("http://processing.org/reference/environment/index.html")?  It's so simple, even I can use it.
This code can automatically export an applet, embedded in HTML, of two translucent, perpendicular planes rotating (and you get OpenGL and jogl for free)
```
import processing.opengl.*;

float a; 

void setup() {
  size(800, 600, OPENGL);
  fill(0, 153);
  noStroke();
}

void draw() {
  background(255);
  translate(width/2, height/2);
  rotateX(a);
  rotateY(a*2);
  rect(-200, -200, 400, 400);
  rotateX(PI/2);
  rect(-200, -200, 400, 400);
  a += 0.01;
}
```

---

### Post by squirrelix on 2007-06-20
By Jove, I think the man is on to something! That looks pretty much exactly what I need. And it is so much better documented than ming is. HackingYodel, you are my hero :p. 
 Thanks!
-- Squirrelix

---

### Post by HackingYodel on 2007-06-21
Cool, I hope it works out well for you.  It's beta, so it can be a bit.... um.. quirky.

I read what you were doing, which was totally beyond me, and saw what was being done over at [WOW!!]("http://processing.org/exhibition/index.html")  Then, in a great thunder clap, both of my synapses fired and I made the connection.

I can't wait to see your work on the Proce55ing Exhibition page.

---

