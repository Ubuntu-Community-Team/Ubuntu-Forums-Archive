---
title: "Java JLabel setOpaque() method"
date: 2011-06-05
forum: Programming Talk
---

### Post by tornadof3 on 2011-06-05
Hello

I have read the help and googled for several examples. I am using a JLabel object which I've set as JLabel with no text but an assigned background colour and I'm going to use the opaque property to make it appear and disappear. If I set the opaque property before running program it is OK, I tried using the setOpaque(false) method whilst the program is running to make it hide again; this doesn't work. I think this method may only be for defining the shape before it gets drawn the first time. How do I get round this?

```
    private void jButton1MouseClicked(java.awt.event.MouseEvent evt) {                                      
        System.out.println("button clicked");
        jLabelRed.setOpaque(false);
        $notify_engine.issueMsg("Opaque status", "Status of red light being opaque: " + jLabelRed.isOpaque());
    }  
```

this returns the status of the JLabel "correctly" according to what I have just used the setOpaque method to achieve, but the appearance of the JLabel does not actually change.

---

### Post by t1497f35 on 2011-06-05
Have you tried setVisible(boolean)?

---

### Post by tornadof3 on 2011-06-05
Hmml the setVisible(false) method did successfully hide the shape, but it also moved other objects around within the frame (it moved a button and two other labels up and over where the shape had been. Is that normal?

---

### Post by t1497f35 on 2011-06-05
That's normal, but it's probably not what you want, you might like this solution though:

[PHP]
package test;

import java.awt.*;
import java.awt.event.*;
import javax.swing.*;

public class Main extends JFrame implements ActionListener {

    private TLabel label;
    private boolean toggle = false;

    public static void main(String[] args) {
        new Main();
    }

    public Main() {

        JPanel cp = new JPanel(new FlowLayout(FlowLayout.LEFT));
        setContentPane(cp);

        label = new TLabel();
        label.setText("hide me");
        label.setBackground(Color.yellow);
        cp.add(label);

        JButton btn = new JButton("toggle view");
        btn.addActionListener(this);
        cp.add(btn);

        setDefaultCloseOperation(EXIT_ON_CLOSE);
        setSize(500, 500);
        setVisible(true);
    }

    @Override
    public void actionPerformed(ActionEvent ae) {
        label.labelShow(toggle);
        toggle = !toggle;
    }
}

class TLabel extends JLabel {

    private boolean show = true;

    public TLabel() {
    }

    public void labelShow(boolean flag) {
        show = flag;
        repaint();
    }

    @Override
    public void paintComponent(Graphics gr) {
        if (!show) {
            return;
        }
        gr.setColor(getBackground());
        gr.fillRect(0, 0, getWidth(), getHeight());
        super.paintComponent(gr);
    }
}
[/PHP]

---

