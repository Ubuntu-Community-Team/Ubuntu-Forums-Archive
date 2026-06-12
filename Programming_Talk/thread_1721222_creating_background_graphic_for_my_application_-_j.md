---
title: "creating background graphic for my application - java swing"
date: 2011-04-04
forum: Programming Talk
---

### Post by orrymr on 2011-04-04
Hi guys. So what I'm trying to do is set up a 4x4 grid. On this grid I will eventually have a sprite that moves from one cell in the grid to another, but for now I just want to set up the grid. What I want is a black background and thereafter to have 3 horizontal and 3 vertical lines which will split up the world into the 4x4 grid.
The following code attempts to accomplish this:
```

import java.awt.Color;
import java.awt.Graphics;
import java.awt.image.BufferedImage;

import javax.swing.JFrame;
import javax.swing.JPanel;


public class GW extends JPanel {
        
        static final int height = 600;
        static final int width = 600;
 
        BufferedImage backgroundImage;
    
    
    public GW() {
        setBackground(Color.black);
        backgroundImage = new BufferedImage(width, height, BufferedImage.TYPE_INT_RGB);
        Graphics g = backgroundImage.getGraphics();
        g.setColor(Color.green);
        for(int i = 1; i <= 3; i++){
            g.drawLine(i*600/4, 0, i*600/4, 600);
            g.drawLine(0, i*600/4, 600, i*600/4);
        }
    }  
    
    public static void main(String[] args){
        JFrame f = new JFrame();
        f.setSize(600,600);
        f.setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
        f.setResizable(false);
        f.setLocation(400,100);
        f.add(new GW());
        f.setVisible(true);
    }
}

```

To reiterate, all I want this code to do is to draw a black background, 3 horizontal and 3 vertical lines (these must be green). I can't figure out why it only draws the black background but not the green lines.
Any help would be much appreciated :D

---

### Post by PaulM1985 on 2011-04-04
You should be doing this in an overriden paint() or paintComponent() method rather than in the constructor.  Everytime the paint() method gets called (which you have not yet overriden) it is setting the background and not re-drawing your green lines.

Paul

---

### Post by orrymr on 2011-04-04
Thanks Paul, it works when I put it in an overridden paint method. One last question, why would I use paint( as opposed to paintComponent( ? my zero key isn't working:/

---

### Post by PaulM1985 on 2011-04-04
I am not 100% sure of the difference.  I tend to always override the paint method because I only ever want to use the panel as a canvas for drawing on.

I think if you wanted to change the look and feel of a UI control, for example making your own special button, then override the appropriate paintComponent/paintBorder method.

Hopefully this clarifies it a bit

Paul

---

### Post by orrymr on 2011-04-04
Well, it doesn't make a difference whether I use paint() or paintComponent(), but I guess that's because I've only got a JPanel on my JFrame.

---

