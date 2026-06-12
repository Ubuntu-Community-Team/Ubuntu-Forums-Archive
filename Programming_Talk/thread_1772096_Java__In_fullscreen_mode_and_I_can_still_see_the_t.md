---
title: "Java:  In fullscreen mode and I can still see the top panel"
date: 2011-05-31
forum: Programming Talk
---

### Post by jarl-haggerty on 2011-05-31
I'm running Xubuntu and this is my program.(Press any key to stop the program)

```
import javax.swing.JFrame;
import javax.swing.JPanel;
import java.awt.Graphics;
import java.awt.Graphics2D;
import java.awt.geom.AffineTransform;
import javax.swing.Timer;
import java.awt.event.ActionListener;
import java.awt.event.ActionEvent;
import java.awt.event.KeyAdapter;
import java.awt.event.KeyEvent;
import java.awt.GraphicsEnvironment;
import java.awt.DisplayMode;

public class Java2D{
    private static class TestKeyListener extends KeyAdapter{
    private JFrame frame;
    private DisplayMode displayMode;

    public TestKeyListener(JFrame frame, DisplayMode displayMode){
        this.displayMode = displayMode;
        this.frame = frame;
    }
    public void keyPressed(KeyEvent event){
        GraphicsEnvironment.getLocalGraphicsEnvironment().getScreenDevices()[0].setDisplayMode(displayMode);
        System.exit(0);
    }
    }

    public static void main(String[] args){
    DisplayMode[] displayModes = GraphicsEnvironment.getLocalGraphicsEnvironment().getScreenDevices()[0].getDisplayModes();
    DisplayMode original = GraphicsEnvironment.getLocalGraphicsEnvironment().getScreenDevices()[0].getDisplayMode();
    DisplayMode t = null;
    for(int i = 0;i < displayModes.length;i++){
        if(displayModes[i].getWidth() == 800 && displayModes[i].getHeight() == 600){
        t = displayModes[i];
        }
    }
    final DisplayMode displayMode = t;
    

    final long start = System.currentTimeMillis();
    final JFrame frame = new JFrame("Java2D");
    frame.setSize(displayMode.getWidth()+frame.getInsets().left+frame.getInsets().right, 
              displayMode.getHeight()+frame.getInsets().bottom+frame.getInsets().top);
    frame.setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
    frame.setLocationRelativeTo(null);
    frame.setContentPane(new JPanel(){
        public void paintComponent(Graphics g){
            Graphics2D graphics = (Graphics2D)g;
            AffineTransform transform = new AffineTransform();
            transform.scale(1, -1);
            transform.translate(0, -displayMode.getHeight());
            transform.rotate(Math.PI/4 + (System.currentTimeMillis()-start)/1000f, displayMode.getWidth()/2, displayMode.getHeight()/2);
            graphics.setTransform(transform);
            graphics.fillRect(displayMode.getWidth()/4, displayMode.getHeight()/4, displayMode.getWidth()/2, displayMode.getHeight()/2);
        }});
    frame.addKeyListener(new TestKeyListener(frame, original));
    frame.setUndecorated(true);
    frame.setResizable(false);

    GraphicsEnvironment.getLocalGraphicsEnvironment().getScreenDevices()[0].setFullScreenWindow(frame);
    GraphicsEnvironment.getLocalGraphicsEnvironment().getScreenDevices()[0].setDisplayMode(displayMode);
    frame.setVisible(true);    
    
    Timer timer = new Timer(16, new ActionListener(){
        public void actionPerformed(ActionEvent event){
            frame.repaint();
        }
        });
    
    timer.start();
    }
}


```

When I run it I see the attached screenshot.  If it's not obvious what my problem is, I don't want any part of the desktop visible.  I once found an obscure solution to this problem but it's lost to me now.

---

### Post by unknownPoster on 2011-05-31
Just as an FYI, the code posted above ran full screen on OSX. Perhaps there is a Linux full-screen function or something similar.

---

### Post by VernonA on 2011-05-31
Are you using Sun's JVM or the OpenJDK? Can you swap to use the alternative? The code looks OK and works correctly on my Windows box at work. I will try it on Ubuntu 10.10 when I get home.

---

