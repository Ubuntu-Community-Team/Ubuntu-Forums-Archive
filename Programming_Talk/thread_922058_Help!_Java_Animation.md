---
title: "Help! Java Animation"
date: 2008-09-16
forum: Programming Talk
---

### Post by Ultros88 on 2008-09-16
Hi all,
I'm trying to write a java application to simulate brownian motion but I'm stuck when it comes to implementing the animation. I've seen plenty of examples online for animations in applets but I am unable to translate that over to a stand-alone application. Any help would be greatly appreciated. Points to references, books, online, etc. simple code...

Thanks,
Ultros

---

### Post by monkeyking on 2008-09-16
I don't really understand what level of infomation you want,
but suns webpage is an excellent place for examples and api lookup.

[http://java.sun.com/docs/books/tutorial/2d/basic2d/index.html](http://java.sun.com/docs/books/tutorial/2d/basic2d/index.html)

---

### Post by Ultros88 on 2008-09-16
There is nothing about animation in the link you provided. Basically I just want to know how to animate a ball bouncing around in a JFrame. I need to know how to set up an animation thread (maybe a timer?) to take care of redrawing the ball at its computed location in successive intervals. Nothing fancy. I tried simply using repaint but that locked up my system and showed the path of the circle/ball.

---

### Post by mike_g on 2008-09-17
You can do it by setting the paint routine to repaint after a short delay. To you will also want to clear your drawing surface each time you repaint otherwise you get trails. Heres a crude example:
```
import java.awt.*;
import java.awt.event.*;
import javax.swing.*;

public class Window extends JFrame
{
    private Surface g;
    
    public Window()
    {        
        this.setPreferredSize(new Dimension(256, 256));
        this.setDefaultCloseOperation(WindowConstants.EXIT_ON_CLOSE);
        this.setVisible(true);
        g = new Surface();
        this.add(g);
        this.pack();
        
        for(int i=0; i<200; i++)
        {
            g.repaint();
            g.move();
            try{
                Thread.sleep(10);
            }catch(InterruptedException ex) {}
            
        }    
    }
 }
```
and:
```
import javax.swing.*;
import java.awt.*;
import java.awt.event.*;


public class Surface extends JPanel
{
    private int width, height;
    private Point pos;
    
    public Surface()
    {
        width = 256; height = 256;
        pos = new Point(10, 10);
    }
 
    public void paint(Graphics g)
    {
        Graphics2D g2 = (Graphics2D)g; 
        g2.setBackground(Color.WHITE);
        g2.setColor(Color.BLACK);
        g2.clearRect(0, 0, width, height);
        g2.drawOval(pos.x, pos.y, 5, 5);
    }
    
    public void move()
    {
        pos.x++; pos.y++;
    }
 
}
```

---

