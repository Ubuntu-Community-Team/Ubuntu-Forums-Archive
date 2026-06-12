---
title: "Java: Clicking inside a moved shape."
date: 2009-09-01
forum: Programming Talk
---

### Post by spadewarrior on 2009-09-01
Hello everyone. I've been trying to register when a point is inside of a Shape created from a GeneralPath in Java. 

The problem I'm having is that I want to translate() my shape to arbitrary co-ordinates, but the shape still acts like it's in the top left of the screen (the original place of the GeneralPath).

Can anybody suggest a way of moving my shape to anywhere on my panel that moves the whole path as well?


Here is my code:

[PHP]import java.awt.*;
import javax.swing.*;
import java.awt.geom.*;
 
/*
 * Represents a Hexagon shape.
 */
public class Hexagon
{
    private  GeneralPath path;

    AffineTransform aff;
    private Double sideLength;
    private double hexOffset;
    
    private Shape hexShape;
    
    /*
     * Hexagon
     */
    public Hexagon(Double size)
    {
        super();
        sideLength = size;
        setUp();
        
    }
    
    private void setUp()
    {
        hexOffset = sideLength * Math.sqrt(3);
        
        path = new GeneralPath();
        path.moveTo(1, 0);
        path.setWindingRule(GeneralPath.WIND_EVEN_ODD);
        
        for(int i = 1; i < 6; i++)
        {
            path.lineTo(Math.cos(i * Math.PI/3), Math.sin(i * Math.PI/3));
        }
        
        path.closePath();
        
        aff = new AffineTransform();

        aff.scale(sideLength, sideLength);
        aff.rotate(Math.PI / 6);
        hexShape = aff.createTransformedShape(path);
        
    }
    
    public GeneralPath getPath()
    {
        return path;
    }
   
    public Double getSize()
    {
        return sideLength;
    }
    
    public Shape getShape()
    {
        return hexShape;
    }
    
    
    
}

[/PHP]

[PHP]import java.awt.*;
import javax.swing.*;
import java.awt.geom.*;
import java.awt.event.*;
/*
 * Represents a Hexagon-shape panel.
 */
public class HexPanel extends JPanel 
{
    private final Hexagon hexagon;
    
    public HexPanel(double hexSize)
    {
        super();
        hexagon = new Hexagon(hexSize);
        setMouseListener();
    }
    
    private void setMouseListener()
    {
        this.addMouseListener(
        new MouseAdapter() {
            public void mousePressed( MouseEvent e )
            {
                if(hexagon.getShape().contains(e.getPoint()))
                {
                    System.out.println("mouse pressed inside hexagon");
                }
                repaint();
            }

            public void mouseReleased( MouseEvent e )
            {
                

                repaint();
            }
         }
      );
    }
    
    public void paintComponent(Graphics g)
    {
        super.paintComponent(g);
        Graphics2D g2 = (Graphics2D)g;
        g2.setRenderingHint(RenderingHints.KEY_ANTIALIASING, 
            RenderingHints.VALUE_ANTIALIAS_ON);
        
        g2.setStroke(new BasicStroke(0.89f));
        g2.setPaint(new Color(0, 0, 0));
        
        g2.translate(200, 100);
        
        g2.draw(hexagon.getShape());
    }
    
    

    public static void main(String[] args)
    {
        
        SwingUtilities.invokeLater(new Runnable() 
        {
            public void run() 
            {
                
                JFrame f = new JFrame("Hexagon");
                Dimension d = new Dimension(800, 600);
                f.setPreferredSize(d);
                HexPanel panel = new HexPanel(60);
                panel.setPreferredSize(d);
                f.getContentPane().add(panel);
                f.setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
                
                f.pack();
                f.setVisible(true);
    
                
               
            }
        });

        
    }
        
    
    
    
    
    
    
}[/PHP]

Many thanks. :)

---

