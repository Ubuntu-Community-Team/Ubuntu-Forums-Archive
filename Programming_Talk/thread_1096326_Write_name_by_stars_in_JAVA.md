---
title: "Write name by stars in JAVA"
date: 2009-03-14
forum: Programming Talk
---

### Post by aRTx on 2009-03-14
Write a Java program with a text field, a button, and a text area as shown in Figure 4.12. A user may enter a string in the text field. When the button "Print" is clicked, the text area will display the pattern of the string formed with the character '*'. 

Figure 4.12. ASCII art.


[IMG]http://www.tupanat.com/fotoartx/fig.JPG[/IMG]

---

### Post by kavon89 on 2009-03-14
What have you done thus far? Do you have any ideas you've come up with to tackle this problem?

I would personally just brute force it and store each letter & number in its own String[]. All the letters will need to have the same number of spaces/stars, and you'll need to set the text box to Monospace. Then just concatenate each String[]'s same indexes together for one whole horizontal line of stars and spaces.

---

### Post by Reiger on 2009-03-14
A text can be written to a buffered image or similar objects. You could use black text on a white background for this purpose and thereby obtain a model which merely need to be scaled so that each black pixel may be properly represented by an asterisk. This neatly deals with multiple fonts, styles, and even character sets.

---

### Post by myrtle1908 on 2009-03-15
> **Reiger said:**
> A text can be written to a buffered image or similar objects. You could use black text on a white background for this purpose and thereby obtain a model which merely need to be scaled so that each black pixel may be properly represented by an asterisk. This neatly deals with multiple fonts, styles, and even character sets.

Yes.  This is the best way.  Clean and simple.

---

### Post by drubin on 2009-03-15
> **kavon89 said:**
> What have you done thus far? Do you have any ideas you've come up with to tackle this problem?

+1 Please don't provide support for home work assignments. The OP isn't going to learn any thing by us just giving out our solutions. 

Rather wait for him/her to come back and explain what they have done and maybe where they are stuck on.

---

### Post by vlearner on 2009-03-15
@kavon89 : thanks a lot for the idea, seems like a fun problem so I decided to give it a shot (I m not the thread creator). String[][] would be the better choice
btw, seriously, what does OP stand for? :)

---

### Post by Joeb454 on 2009-03-15
> **vlearner said:**
> btw, seriously, what does OP stand for? :)

Original Poster.

And drubin is correct - if this is homework the thread is likely to be closed.

[quote=Code of Conduct]# While we are happy to serve as a resource for hints and for asking questions when you get stuck and need a little help, **the Ubuntu Forums should not be thought of as a homework service. Please do not post your homework assignments expecting someone else to do it for you. **Any such threads will be taken offline and warnings or infractions may be issued.[/quote]

(emphasis mine :))

---

### Post by aRTx on 2009-03-15
Thank you very much for your ideas. I have learned a lof from your comments but finally I have found the source code and I want to share with you ;)

```

import javax.swing.*;
import java.awt.event.*;
import java.awt.*;
import java.awt.image.*;

public class Ex6 extends JApplet implements ActionListener {
    public static void main(String[] args) {
        JFrame frame = new JFrame();
        frame.setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
        JApplet applet = new Ex6();
        frame.getContentPane().add(applet);
        applet.init();
        applet.start();
        frame.setSize(600,400);
        frame.show();
    }
    
    JTextField text = new JTextField("Artan Potera");
    JTextArea ta = new JTextArea(20, 80);
    
    public void init() {
        ta.setFont(new Font("Monospaced", Font.PLAIN, 10));
        JPanel p = new JPanel();
        p.setLayout(new BorderLayout());
        p.add(text, BorderLayout.CENTER);
        JButton b = new JButton("Print");
        b.addActionListener(this);
        p.add(b, BorderLayout.EAST);
        this.getContentPane().setLayout(new BorderLayout());
        this.getContentPane().add(p, BorderLayout.NORTH);
        this.getContentPane().add(ta, BorderLayout.CENTER);
    }
    
    public void actionPerformed(ActionEvent e) {
        String s = text.getText();
        if (s != null) {
            BufferedImage bi = new BufferedImage(80,20,BufferedImage.TYPE_INT_BGR);
            Graphics2D g2 = (Graphics2D)bi.getGraphics();
            g2.setFont(new Font("Serif", Font.BOLD, 20));
            g2.drawString(s, 0, 16);
            Raster ras = bi.getData();
            ta.setText("");
            for (int row = 0; row < 20; row++) {
                String line = "";
                for (int col = 0; col < 80; col++) {
                    if (ras.getSample(col,row,1) > 128) {
                        line += "*";
                    } else {
                        line += " ";
                    }
                }
                System.out.println(line);
                ta.append(line+"\n");
            }
        }
    }
}

```

---

### Post by drubin on 2009-03-15
> **aRTx said:**
> Thank you very much for your ideas. I have learned a lof from your comments but finally I have found the source code and I want to share with you ;)


Found or wrote your self...

---

### Post by CptPicard on 2009-03-15
> **drubin said:**
> Found or wrote your self...

The funny thing about this OP is that he doesn't even make an attempt to disguise that this is homework -- it's just word by word copypaste, even with this "see figure (that does not exist in post)" stuff kept :D

---

### Post by bapoumba on 2009-03-15
Closing here, sorry, please see post #7 for the CoC quote. Thanks.

---

