---
title: "Java: How to draw line?"
date: 2010-09-26
forum: Programming Talk
---

### Post by OVERPOWER8 on 2010-09-26
Hello.

I am trying to draw a line in java program, but it is not working...
How can I make this code to work?

```
main(){
     Graphics g = new Graphics();
     g.drawLine(10, 20, 30, 40); 
}
```

I just don't understand the principles of creating Graphics object and using it.

---

### Post by simeon87 on 2010-09-26
You can't do it like that because the Graphics object needs to come from an existing place (like a canvas to draw on), you can't use it by creating it with new. What you need to do, is to create a basic window with a canvas to draw on and then request the graphics object from there. Then you can use draw methods to draw on it. I recommend looking at tutorials for this and building on the example code they give you. For example, this one: [http://www.dgp.toronto.edu/~mjmcguff/learn/java/01-drawingLines/](http://www.dgp.toronto.edu/~mjmcguff/learn/java/01-drawingLines/) In that case, you get the Graphics object from the applet which calls the paint method when the applet needs to be painted. It's probably good to read some background details as well so you know what's going on.

---

### Post by OVERPOWER8 on 2010-09-26
>> [B]simeon87

[/B]Thanks 4 the reply, but maybe you can tell me how to make this code to work?

```
import java.awt.*;
import java.applet.*;
 
class Drawing extends Applet {
 
        private static final long serialVersionUID = 4902057285471885308L;
 
        public void paint(Graphics g) {
                test();
                
        }
        private void test()
        {
                Graphics g = getGraphics();
                g.drawLine(10, 20, 30, 40);
        }
}

class Program{
    public static void main(String[] args){
        
        Drawing d = new Drawing();
        d.paint();
    }
}
```

---

### Post by lykeion on 2010-09-26
GUI coding in Java isn't so intuitive at first. I'd also recommend doing some reading first to get a grip on the basics. 
The _[Sun Tutorials]("http://download.oracle.com/javase/tutorial/")_ is a good place to start, see for example _[Working with geometry]("http://download.oracle.com/javase/tutorial/2d/geometry/index.html")_.

Here's a working example to get you started:
[PHP]import javax.swing.*;
import java.awt.*;
import java.awt.event.*;
import java.awt.geom.Line2D;

class DrawingApplet extends JApplet {

    public void paint(Graphics g) {
        Graphics2D g2 = (Graphics2D) g;
        g2.draw(new Line2D.Double(10, 10, 250, 250));
    }
}

class StartApplet {
    public static void main(String[] args) {

        JFrame frame = new JFrame("Draw the line");
        frame.addWindowListener(new WindowAdapter() {
            public void windowClosing(WindowEvent e) {
                System.exit(0);
            }
        });
        JApplet applet = new DrawingApplet();
        frame.getContentPane().add(applet);
        applet.init();
        frame.pack();
        frame.setSize(new Dimension(300, 300));
        frame.setVisible(true);
    }
}[/PHP]

---

