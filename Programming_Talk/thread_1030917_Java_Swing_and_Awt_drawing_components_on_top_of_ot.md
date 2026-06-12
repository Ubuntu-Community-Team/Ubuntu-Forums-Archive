---
title: "Java Swing and Awt: drawing components on top of other components"
date: 2009-01-04
forum: Programming Talk
---

### Post by zizzdude on 2009-01-04
I'm wondering if there was a way you can draw components on an already drawn "big" component. for example:

```

public class Canvas extends JPanel
{
    public void paintComponent(Graphics g)
    {
        // draw the canvas...
    }
}

public class Ball extends JComponent
{
    public void paintComponent(Graphics g)
    {
        // draw the ball...
    }
}

public class MainClass
{
    public static void main(String[] args)
    {
        Canvas panel = new Canvas();
        panel.add(new Ball());
    }
}

```

I tried something like this, but I just see the "Canvas", not the "Ball" on the "Canvas"
Any other methods I should use?

---

### Post by lordikyiky on 2009-01-04
Make a draw method for the ball that takes in a Graphics object. Then pass in "g" from the canvas paintComponent method to that draw method.  Then both objects will be drawn onto the same graphics object.

---

