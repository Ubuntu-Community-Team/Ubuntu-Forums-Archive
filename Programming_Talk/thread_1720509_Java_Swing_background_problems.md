---
title: "Java Swing background problems"
date: 2011-04-03
forum: Programming Talk
---

### Post by orrymr on 2011-04-03
Hi guys, not really sure why the following code isn't generating a black background for me. Any help would be gladly appreciated, thanks :)

```

//relevant imports
public class Shooter extends JPanel {
    private static final long serialVersionUID = 1L;

    public Shooter(){
        setBackground(Color.black);
    }
    
    public void paint(Graphics g){
        g.setColor(Color.green);
        g.drawString("Hi...", 200, 300);
    }
   
    public static void main(String[] args){
        JFrame f = new JFrame();
        f.setSize(600,600);
        f.setLocation(300,150);
        f.setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
        f.add(new Shooter());
        f.setVisible(true);
    }    
}

```

---

### Post by Minimal Hank on 2011-04-03
Add it to the main function as f.setBackground(Color.black) and it'll work.

---

### Post by Reiger on 2011-04-04
Since you override paint, it is now *your* job to make sure that the background is painted. Since your paint() method doesn't fill the widget with a black background, you don't see one.

That's why if you override paint of a GUI component you almost always do it like this:
```

public void paint(Graphics g) {
  super.paint(g); // make sure the base widget is drawn
  
  // draw your additions to the widget here.
}

```

---

### Post by dazman19 on 2011-04-04
try calling this as the first line of paintComponent
super.paintComponent(g);


public void paintComponent( Graphics g ){
		super.paintComponent(g);


...
}

EDIT: didnt realise the dude before me said the same thing and that I used paintComponent instead of paint lolz.

---

### Post by orrymr on 2011-04-04
Thanks for the replies, the suggestions work. I've been reading about paint() and paintComponent() but I still don't really understand why I should use one over the other.

---

### Post by dazman19 on 2011-04-04
paintComponent seems to be another way of calling the paint method.
When you call super, you are calling the super class's paint method. 

I believe paint is an interface. PaintComponent is a sub-component of JComponent,

I just check the AWT before i paint to see what i need, but if either work for you then go for it.

---

### Post by orrymr on 2011-04-04
I think (if someone could confirm, that would be great) that what happens when you call paint() is that paintComponent(), paintBorder() and paintChildren() get called. Since I've only got a single component, my JPanel which I'm adding to my JFrame I only really need to call the paintComponent() method, although Java doesn't seem to mind if I simply call paint().

---

### Post by VernonA on 2011-04-05
In the old days of AWT, you used to override the paint() method to put your graphics on components. When Swing came along, components had borders, multiple layers, children etc, so the paint() method became more complicated, and overriding it properly got tougher. You have two choices, invoke the super() call to get the bulk of the redraw done, then add your own custom drawing, or leave paint alone and just override the paintComponent() method instead which is the sub-function which redraws the main area of the component. In practice, in normal Swing apps, you should use the latter. Painting dynamic things is tough enough on Swing as it is, so if you want to avoid a number of problems just (i) override paintComponent(), and (ii) don't invoke its super() but instead draw the whole panel yourself.

Once you have this basic structure in your app, I'm guessing you're going to want to draw something dynamic. This moves us on to double-buffering and flicker-reduction. That can be another thread!

---

### Post by orrymr on 2011-04-05
Thanks for the great reply VernonA, but if I don't invoke paintComponent()'s super(), my background colour doesn't show up.

---

### Post by VernonA on 2011-04-05
That's right, you have to do it yourself. Draw a big black block on the panel using gc.fillRect(0,0,width,height), or whatever. I am assuming you are writing something like a game which uses sprites on a backdrop image. You have to keep the panel up-to-date as dynamic things move about. You can't keep calling super() or the whole panel will redraw each time, which is going to flicker horribly. If you are not doing anything dynamic then calling super() may be OK, so let me know where you are headed with this and I can tune my advice.

---

### Post by orrymr on 2011-04-05
Well, it's not exactly going to be a game, but it will have a sprite that's going to move around a lot (dozens of times a second, possibly).

---

### Post by VernonA on 2011-04-05
Fine, my advice stands. I assume there will be some sort of backdrop behind the sprite. That is the "background" of the panel, and a call to super() isn't going to draw that. Let's take a concrete example, your app is a picture of the Mona Lisa with a fly buzzing around in front of it. You need to load the background with constructor code like:
    BufferedImage backdrop = ImageIO.read("MonaLisa.jpg");
Then the first line of the paintComponent(gc) function will be
    gc.drawImage( backdrop, 0,0, null );
The next line would be a call to draw the fly sprite.

The first issue you will find with this code is that as you resize your app window, Mona will stay glued to the top left corner. You need to decide what behaviour you actually want (either this is fine, the image should scale to fill the window or the image should move to stay centred in the window). You need to write appropriate code to get what you want and there are quite a few ways available so think it through. In particular. note how this affects the fly. Does it scale too? If Mona shifts does his coordinate system shift equally? If a border appears around Mona can he fly onto it? Programing sprites is not trivial!

---

### Post by orrymr on 2011-04-05
Yes, essentially what I want to do is create a 4x4 grid and allow my sprite to move from cell to cell in the grid. In order to implement the grid, (as well as know the sprite's position) I have a 2d boolean array (4x4). All entries are false except for the one which corresponds to the sprite's position in the grid, which will obviously be true. In order to visually represent this I've drawn 3 green horizontal and vertical lines (that is, 6 lines in total) over a black background -> this will split the window into the appropriate cells. This grid doesn't need to change. All that needs to change is which cell the sprite is currently occupying. 
My code for doing this:
```

    public GW() throws InterruptedException, IOException {
        setBackground(Color.black);
        a = new Agent();
    }
    
    public void drawLines(Graphics g){
        g.setColor(Color.green);
        for(int i = 1; i <= 3; i++){
            g.drawLine(i*600/4, 0, i*600/4, 600);
            g.drawLine(0, i*600/4, 600, i*600/4);
        }
    }
    
    
    public void paintComponent(Graphics g){
        super.paintComponent(g);
        drawLines(g);

    }
    
    
    public static void main(String[] args) throws InterruptedException, IOException {
        JFrame f = new JFrame();
        f.setSize(600,600);
        f.setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
        f.setResizable(false);
        f.setLocation(400,100);
        f.add(new GW());
        f.setVisible(true);
    }

```
works fine

---

### Post by VernonA on 2011-04-05
I'm glad its working well. Adding the sprite looks straightforward too - change where it is in the grid and call repaint(); to get all the graphics redrawn. Nice.

---

