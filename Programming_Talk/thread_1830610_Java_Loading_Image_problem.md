---
title: "Java Loading Image problem?"
date: 2011-08-22
forum: Programming Talk
---

### Post by kensclark15 on 2011-08-22
How do I enter the class path in Java to make an image load right? Here is the line of code. I don't know if it's right: ```
bg = new ImageIcon("\\home\\kenneth\\Desktop\\back.png").getImage();
        pic = new ImageIcon("\\home\\kenneth\\Desktop\\bam.png").getImage();
``` I'll give you my code so far.
Images.class:
```
package main;
import java.awt.*;
import javax.swing.JFrame;
import javax.swing.ImageIcon;
@SuppressWarnings("serial")
public class Images extends JFrame {
    public static void main(String[] args) {
        DisplayMode dm = new DisplayMode(800, 600, 16, DisplayMode.REFRESH_RATE_UNKNOWN);
        Images mm = new Images();
        mm.run(dm);
    }
    
    private Screen s;
    private Image bg;
    private Image pic;
    private boolean loaded;
    
    //run method
    
    public void run(DisplayMode dm) {
        setBackground(Color.BLUE);
        setForeground(Color.WHITE);
        setFont(new Font("Arial", Font.PLAIN, 24));
        loaded = false;
        
        s = new Screen();
        try {
            s.setFullScreen(dm, this);
            loadpics();
            try {
                Thread.sleep(5000);
            } catch (Exception ex) {}
        } finally {
            s.restoreScreen();
            }
    }
    
    //loads pics
    
    public void loadpics() {
        bg = new ImageIcon("\\home\\kenneth\\Desktop\\back.png").getImage();
        pic = new ImageIcon("\\home\\kenneth\\Desktop\\bam.png").getImage();
        loaded = true;
        repaint();
    }
    
    public void paint(Graphics g) {
        if(g instanceof Graphics2D) {
            Graphics2D g2 = (Graphics2D) g;
            g2.setRenderingHint(RenderingHints.KEY_TEXT_ANTIALIASING, RenderingHints.VALUE_TEXT_ANTIALIAS_ON);
        }
        if(loaded) {
            g.drawImage(bg,0,0,null);
            g.drawImage(pic,170,180,null);
        }
    }
}
```
Screen.class:
```
package main;
import java.awt.*;
import javax.swing.JFrame;

public class Screen {
    
    private GraphicsDevice vc;
    
    public Screen() {
        GraphicsEnvironment env = GraphicsEnvironment.getLocalGraphicsEnvironment();
        vc = env.getDefaultScreenDevice();
    }
    
    public void setFullScreen(DisplayMode dm, JFrame window) {
        window.setUndecorated(true);
        window.setResizable(false);
        vc.setFullScreenWindow(window);
        
        if(dm != null && vc.isDisplayChangeSupported()) {
            try {
                vc.setDisplayMode(dm);
            } catch (Exception e) {}
        }
    }
        
        public Window getFullScreenWindow() {
            return vc.getFullScreenWindow();
        }
        
        public void restoreScreen() {
            Window w = vc.getFullScreenWindow();
            if(w != null) {
                w.dispose();
            }
            
            vc.setFullScreenWindow(null);
        }
    
    
    

}

```

---

### Post by lykeion on 2011-08-24
I guess you mean your image paths, ([classpath]("http://en.wikipedia.org/wiki/Classpath") is something different in Java):

"\\home\\kenneth\\Desktop\\back.png"

The double backslashes in your paths are wrong. On Linux the forward slash (/) is used as a file separator:

"/home/kenneth/Desktop/back.png"


I'd use relative paths and place the images in same dir as the java files:
"back.png"

EDIT
The Oracle Swing tutorial is really good. I found I used that a lot when I was learning Java GUI development:
[http://download.oracle.com/javase/tutorial/uiswing/components/](http://download.oracle.com/javase/tutorial/uiswing/components/)

---

### Post by The Cog on 2011-08-24
Moved to Programming Talk.

---

### Post by PaulM1985 on 2011-08-24
I agree with lykeion, try and use relative paths where possible.  I tend to keep my images in the same jar file as my project and load through the jar file using getResource() and ImageIO.read():

[http://download.oracle.com/javase/1,5.0/docs/api/java/lang/Class.html#getResource(java.lang.String](http://download.oracle.com/javase/1,5.0/docs/api/java/lang/Class.html#getResource(java.lang.String))

[http://download.oracle.com/javase/6/docs/api/javax/imageio/ImageIO.html#read(java.net.URL](http://download.oracle.com/javase/6/docs/api/javax/imageio/ImageIO.html#read(java.net.URL))

Paul

---

