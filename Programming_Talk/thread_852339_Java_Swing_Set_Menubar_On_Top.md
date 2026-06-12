---
title: "Java Swing Set Menubar On Top"
date: 2008-07-07
forum: Programming Talk
---

### Post by mike_g on 2008-07-07
I started making a small swing app. It has a menu bar and a drawing surface. My problem is that when I click on the dropdown menu all the items are drawn behind the drawing surface. Is there any way to set the menu bar to be drawn on top? 

Heres my code:
```
package splineeditor;
import javax.swing.*;
import java.awt.*;
import java.awt.event.*;

public class Interface extends JFrame
{
    private MenuBar dropdown;
    private GraphicsArea graphics;
    
    
    public Interface() 
    {
        JPanel content = (JPanel)this.getContentPane();
        content.setLayout(new BoxLayout(content, BoxLayout.Y_AXIS));
        
        dropdown = new MenuBar();
        this.add(dropdown);
        
        graphics = new GraphicsArea();
        this.add(graphics);
          
        pack();        
        this.setVisible(true);
        this.setDefaultCloseOperation(WindowConstants.EXIT_ON_CLOSE);
    }
    
}
```
MenuBar extends JMenuBar and GraphicsArea extends Canvas.

---

### Post by Ruhe on 2008-07-07
Hi, mike_g!

Don't mix AWT components(Canvas) with swing components(JMenuBar).
Use swing for direct painting, JPanel for example.

good luck ;)

---

### Post by tinny on 2008-07-07
> **mike_g said:**
> I started making a small swing app. It has a menu bar and a drawing surface. My problem is that when I click on the dropdown menu all the items are drawn behind the drawing surface. Is there any way to set the menu bar to be drawn on top? 

Heres my code:
```
package splineeditor;
import javax.swing.*;
import java.awt.*;
import java.awt.event.*;

public class Interface extends JFrame
{
    private MenuBar dropdown;
    private GraphicsArea graphics;
    
    
    public Interface() 
    {
        JPanel content = (JPanel)this.getContentPane();
        content.setLayout(new BoxLayout(content, BoxLayout.Y_AXIS));
        
        dropdown = new MenuBar();
        this.add(dropdown);
        
        graphics = new GraphicsArea();
        this.add(graphics);
          
        pack();        
        this.setVisible(true);
        this.setDefaultCloseOperation(WindowConstants.EXIT_ON_CLOSE);
    }
    
}
```
MenuBar extends JMenuBar and GraphicsArea extends Canvas.

Hi

I notice that you are adding the menu bar as a standard component.

```

this.add(dropdown);

``` 

Here is a working example.

```

package javaapplication3;

import javax.swing.BoxLayout;
import javax.swing.JFrame;
import javax.swing.JMenu;
import javax.swing.JMenuBar;
import javax.swing.JMenuItem;
import javax.swing.JPanel;
import javax.swing.WindowConstants;


public class Interface extends JFrame
{
    private JMenuBar dropdown;
    private JPanel graphics;
    
    
    public Interface() 
    {
        JPanel content = (JPanel)this.getContentPane();
        content.setLayout(new BoxLayout(content, BoxLayout.Y_AXIS));
        
        dropdown = new JMenuBar();
        
        //Build menu
        JMenu menu = new JMenu("File");
        menu.add(new JMenuItem("Open"));
        
        //Add menu to menu drop down
        dropdown.add(menu);
        
        //IMPORTANT, add JMenuBar
        this.setJMenuBar(dropdown);
        
        graphics = new JPanel();
        
        this.add(graphics);
          
        pack();        
        this.setVisible(true);
        this.setDefaultCloseOperation(WindowConstants.EXIT_ON_CLOSE);
    }
    
}

```

Note that you need to use

```

this.setJMenuBar(dropdown);

```

Hope this helps :)

> 
Don't mix AWT components(Canvas) with swing components(JMenuBar).
Use swing for direct painting, JPanel for example.


Yeah, mixing AWT and Swing will be problematic.

---

### Post by mike_g on 2008-07-07
Ok cool, that sorted out that problem. But how do I draw to the JPanel. The code I was using uses AWT Graphics, when I call myJpanle.getGrpahics() it always returns null.

Can anyone tell me how I should go about it. I have been looking around on the net, but all the examples I have found seem to use AWT Graphics2D and I cant get it to work. I only want to draw some simple lines :'( 

```
package splineeditor;
import javax.swing.*;
import java.awt.*;
import java.awt.event.*;
import java.awt.geom.Line2D;

public class GraphicsArea extends JPanel
{
    private Styles styles;
    private Point offset;

    public GraphicsArea(Styles s) 
    {

        styles = s;
        offset = new Point();
        this.setBackground(styles.getBackgroundColor());
        this.setPreferredSize(new Dimension(800, 600));
        this.paint(this.getGraphics());
        
        System.out.println(this.getGraphics());
        //this.Redraw();
    }
    
    public void Redraw()
    {
        DrawGrid();
        
    }
    
    private void DrawGrid()
    {
        Graphics2D g = (Graphics2D) this.getGraphics(); 
        g.setColor(styles.getGridColor());
        for(int x=0; x<800; x+=10)
        {    
            g.drawLine(x, 0, x, 600);
        }
        for(int y=0; y<600; y+=10)
        {
            g.drawLine(0, y, 800, y); 
        }
        
    }   
}
```

---

### Post by tinny on 2008-07-07
You need to override the "paint" method of JPanel. (put your custom graphics in this method)

Then call "repaint" externally when you wish to refreash the view. (if your graphics change)


Put the below graphics code in the paint method.

> 
        Graphics2D g = (Graphics2D) this.getGraphics(); 
        g.setColor(styles.getGridColor());
        for(int x=0; x<800; x+=10)
        {    
            g.drawLine(x, 0, x, 600);
        }
        for(int y=0; y<600; y+=10)
        {
            g.drawLine(0, y, 800, y); 
        }



BTW don't call paint directly (not thread safe, you may crash swing). Just call "repaint"

---

### Post by mike_g on 2008-07-07
Cheers, it works now :)

---

### Post by tinny on 2008-07-07
> **mike_g said:**
> Cheers, it works now :)

Tip. If you have a tree of Swing components (JFrame > JPanel > etc....) you can call "validate" on the root component to recursively refresh all components.

Its not guaranteed to happen immediately (gets queued in the swing event dispatch thread), but it will happen :)

---

