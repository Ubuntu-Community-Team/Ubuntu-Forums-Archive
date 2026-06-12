---
title: "java repaint() method not calling paintComponent()"
date: 2011-04-15
forum: Programming Talk
---

### Post by orrymr on 2011-04-15
So basically I'm trying to create little grid in java. For now, all I'm trying to do is change the colour of the lines which split the screen up into said grid. Code is posted below, but basically all I'm trying to do is call the method performEpisode() from my constructor. perforEpisode() should then draw the game, using green lines, onto a temporary BufferedImage. I then call the repaint() method so that the game gets painted onto the screen. Next, I was 2 seconds, paint the game, using red lines this time, onto the temporary image, and call repaint() so that the new red game gets painted onto the screen. What actually happens is that nothing happens for 2 seconds, then the red game is painted. Green is completely ignored. Why doesn't java see the green game?

```

//O Messer 2011
import java.awt.Color;
import java.awt.Graphics;
import java.awt.image.BufferedImage;
import java.io.IOException;
import java.util.Random;

import javax.imageio.ImageIO;
import javax.swing.JFrame;
import javax.swing.JPanel;


public class GW extends JPanel {
        
        /**
     * 
     */
    private static final long serialVersionUID = 1L;
        static final int height = 600;
        static final int width = 600;
    
        BufferedImage gWorld;
    
    
    public GW() throws InterruptedException, IOException {
        setBackground(Color.black);
        performEpisode();
        
    }
    
    public void performEpisode() throws InterruptedException{
            drawGame(Color.green);
            repaint();
         Thread.sleep(2000);
         drawGame(Color.red);
         repaint();
    }
    
    public void update(Graphics g){
        paintComponent(g);        
    }
    
    public void drawGame(Color col){
        BufferedImage bim = new BufferedImage(width, height, BufferedImage.TYPE_INT_RGB);
        Graphics b = bim.getGraphics();
        b.setColor(col);
        for(int i = 1; i <= 3; i++){
            b.drawLine(i*600/4, 0, i*600/4, 600);
            b.drawLine(0, i*600/4, 600, i*600/4);
        }

        gWorld = bim;
    }
    
    
    public void paintComponent(Graphics g){
        g.drawImage(gWorld, 0, 0, this);
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
}

```

---

### Post by PaulM1985 on 2011-04-15
Hi

You are calling performEpisode in the constructor of the GW object.  This means that the green drawing is happening before it is added to the JFrame and also before the JFrame is even visible (since the constructor is called before the setVisible call).  If you remove your performEpisode() call from your GW contructor and then in your main method, if you did:

```

GW g = new GW();
f.add(g);
f.setVisible(true);
g.performEpisode();

```

You will see the green lines.

Paul

---

### Post by orrymr on 2011-04-16
Awesome, it works, thanks

---

