---
title: "[SOLVED] Java question: updating values with JSlider"
date: 2008-02-08
forum: Programming Talk
---

### Post by tbranham on 2008-02-08
I've got a question for all you Java programmers:

I was given some Java code as part of an assignment, and I'm supposed to input the code with my line-drawing algorithm and make the thing run. I've got this taken care of...

...except for 1 nagging detail. So, this is my first *real* attempt at serious programming in Java (I come from a C++ background, mostly, but I am well versed in several other languages). Anyway, the project we're building has a set of JSlider objects to manipulate the input values to out line-drawing method. The problem is that the code provided does not work as expected; the value in the JTextField next to the slider changes, but the change does not propagate to the custom Canvas object.

OK, so here is the code I was provided with:
```
import java.awt.*;
import java.awt.event.*;
import javax.swing.*;
import javax.swing.border.*;
import javax.swing.event.*;

public class LineDraw extends JFrame{
    DrawingCanvas canvas;
    JSlider mSlider;
    JSlider bSlider;
    JTextField mValueField;
    JTextField bValueField;
    
    public LineDraw() {
        super("LineDraw -- Bresenham's Algorithm");
        Container container = getContentPane();
        
        canvas = new DrawingCanvas();
        container.add(canvas);
        
        JPanel controlPanel = new JPanel();
        GridLayout layout = new GridLayout(2,3);
        controlPanel.setLayout(layout);
        container.add(controlPanel, BorderLayout.SOUTH);
        
        TitledBorder border = new TitledBorder("SET INPUT PARAMS");
        controlPanel.setBorder(border);
        
        JLabel mLabel = new JLabel("m:  ", JLabel.RIGHT);
        mSlider = new JSlider(JSlider.HORIZONTAL, -100, 100, 0);
        mValueField = new JTextField("0", 4);
        mSlider.addChangeListener(new SliderListener(canvas.mValue, mValueField));
        controlPanel.add(mLabel);
        controlPanel.add(mValueField);
        controlPanel.add(mSlider);
        
        JLabel bLabel = new JLabel("b:  ", JLabel.RIGHT);
        bSlider = new JSlider(JSlider.HORIZONTAL, -100, 100, 0);
        bValueField = new JTextField("0", 4);
        bSlider.addChangeListener(new SliderListener(canvas.bValue, bValueField));
        controlPanel.add(bLabel);
        controlPanel.add(bValueField);
        controlPanel.add(bSlider);
        
        addWindowListener(new WindowEventHandler());
    }
    
    class DrawingCanvas extends Canvas {
        Double mValue;
        Double bValue;
        
        DrawingCanvas() {
            setSize(600, 400);
            setBackground(Color.WHITE);
        }
        
        public void paint(Graphics g) {
            Graphics2D g2D = (Graphics2D)g;
            // I added the followng println statements so you can see what I mean...
            System.out.println(mValue);
            System.out.println(bValue);
            drawPoint(200, 250, g2D);
        }
        
        private void drawPoint(int x, int y, Graphics2D g2D) {
            g2D.drawLine(x, y, x, y);
        }
    }
    
    class SliderListener implements ChangeListener {
        private Double value;
        private JTextField textField;
        
        public SliderListener(Double value, JTextField textField) {
            this.value = value;
            this.textField = textField;
        }
        
        public void stateChanged(ChangeEvent e) {
            JSlider slider = (JSlider) e.getSource();
            int sValue = slider.getValue();
            textField.setText(Double.toString(sValue));
            value = Double.valueOf(sValue);
            canvas.repaint();
        }
    }
    
    static class WindowEventHandler extends WindowAdapter {
        public void windowClosing(WindowEvent e) {
            System.exit(0);
        }
    }
    
    public static void main(String[] args) {
        LineDraw lineDraw = new LineDraw();
        lineDraw.setLocation(200, 200);
        lineDraw.pack();
        lineDraw.setVisible(true);
    }
}

```
If you run that, you'll see that the 'println' statements show that the changes from the JSliders are not making it into the customized canvas object. Now, my Professor swears that this code should work. Apparently, he believes that by using Double objects in the DrawingCanvas class, the references to those objects should make it through the SliderListener class.

Anyway, I did come up with a version that works, but I went about it by changing the Double objects in DrawingCanvas to primatives, then using some ugly code in the SliderListener to see which JSlider was changing, then updating the value in canvas directly. Obviously, this works, but I'd still like to find out the best way to do this.

OK, have I confused you enough? Essentially what I'm looking for is the "right way (tm)" to update these values. Any thoughts?

Thanks for your insight.

---

### Post by Ragazzo on 2008-02-08
The class Double is an immutable wrapper so when you write **value = Double.valueOf(sValue);** in SliderListener, you're making the variable point to a new object but those in DrawingCanvas still point to the old object. 

One solution is to write your own mutable wrapper for the primitive double:

```

public class MutableDouble {
 private double value;

 public double getValue() {
  return value;
 }

 public void setValue(double d) {
  this.value = d;
 }
}

```

---

### Post by tbranham on 2008-02-08
Thanks Ragazzo!

This works like a champ. I'm one of those programmers that doesn't like to settle for "well, it works, but it's ugly." This is far more clear than the solution I had previously come up with.

---

