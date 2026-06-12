---
title: "Software issue regarding JFrames"
date: 2010-04-24
forum: Programming Talk
---

### Post by Ravenshade on 2010-04-24
Subject changed. Thread recycling. (Mainly due to the fact I screwed up and instead of hitting new topic, hit reply instead *sigh*)

---

### Post by Ravenshade on 2010-04-24
....why why does the title sound like middle aged orgy in an exotic country, with an air of black mail on the side? 

No matter... 

```
//This is the main 'frame' class to the overall program. 
import java.awt.*;
import java.awt.event.*;
import javax.swing.*;

public class CelsiusConverterGUI extends javax.swing.JFrame {
    //*Create new form*//
    public static void createAndShowGUI() {
        //Create it!
        JFrame frame = new JFrame("FrameDemo");
        frame.setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
        //name it!
        JLabel title = new JLabel("Celsius Converter App");
        title.setPreferredSize(new Dimension(175, 100));
        frame.getContentPane().add(title, BorderLayout.CENTER);
        
        //Display it!
        frame.pack();
        frame.setVisible(true);
    }
    
    public static void main(String[] args) {
        //Do something
        javax.swing.SwingUtilities.invokeLater(new Runnable() {
                public void run() {
                    createAndShowGUI();
                }
            }
        
        );
    }
}
```

Now, I believe from this code, I should be getting a relatively small box, however what I get is just a huge gray sprawl, with the title half way down the left hand of my screen. :confused: What gives. The demonstration on Java Tuts show that I should be getting a very small box.

---

