---
title: "Netbeans displays Imgaes but Eclipse doesn't? (code included)"
date: 2009-11-04
forum: Programming Talk
---

### Post by wotsit on 2009-11-04
```
public class GameApplet extends JApplet {

    private PaintSurface canvas;

    @Override
    public void init() {
        this.setSize(650, 450);
        canvas = new PaintSurface();
        this.add(canvas);
        Thread t = new AnimationThread(this);
        t.start();
    }


}

public class PaintSurface extends JComponent {

    @Override
    public void paint(Graphics g) {
        Graphics2D g2d = (Graphics2D)g;


        Card janbright = new Card("Images/Kintengu_01c.png", 250, 10);
        Card janpoemscr = new Card("Images/Kintengu_01d.png", 84, 10);
        g2d.setColor(Color.BLACK);
        g2d.drawImage(janbright.img, 300, 10, null);
        g2d.drawImage(janpoemscr.img, 84, 10, null);
    }
}

public class Card {
    Image img;
    int xpos;
    int ypos;

    public Card(String img, int xpos, int ypos) {
        this.img = getImage(img);
        this.xpos = xpos;
        this.ypos = ypos;
    }
    
    public Image getImage(String img) {
        Toolkit toolkit = Toolkit.getDefaultToolkit();
        return toolkit.getImage(img);
    }

}

public class AnimationThread extends Thread {

    JApplet c;

    public AnimationThread(JApplet c) {
        this.c = c;
    }

    @Override
    public void run() {
        while(true) {
            c.repaint();
            try {
                Thread.sleep(20);
            } catch(InterruptedException e) {
            }
        }
    }
}
```

If you need any more info, please ask.

Thanks for your suggestions.

---

### Post by Zugzwang on 2009-12-01
For an applet to find the images, you should always:
[LIST]
[*]Include the images in the .jar file
[*]Load them using a relative path using the Class.getResource(...) functions.
[/LIST]
otherwise whether the images are found or not depends on the "current path" during execution, which your probably shouldn't rely on being set "correctly".

---

