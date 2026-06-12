---
title: "Java Keylisteners"
date: 2011-07-30
forum: Programming Talk
---

### Post by orrymr on 2011-07-30
Hi all - I have the following code. All I want it to do is to output "Hello" to standard output when I hit a key. I'm not sure why the code doesn't work... any ideas? Thanks!
```

import javax.swing.*;
import java.awt.*;
import java.awt.event.KeyEvent;
import java.awt.event.KeyListener;

public class Lines extends JPanel implements KeyListener{
    public static void main(String[] args){
        JFrame frame = new JFrame ("Lines");
        frame.setSize(600,600);
        frame.setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
        frame.setLocation(400,100);
        Lines l = new Lines();
        frame.add(l);
        
        frame.setVisible(true);
    }
    
    Lines(){
        this.setBackground(Color.black);
    }
    
    public void keyPressed(KeyEvent e){
        System.out.println("Hello");
    }
    public void keyReleased(KeyEvent e){}
    public void keyTyped(KeyEvent e){}
}
```

---

### Post by Reiger on 2011-07-31
The short answer: because your key listener isn't receiving any events, because your listener was never added to the list of listeners to notify. The tutorials are a good place to start:

[http://download.oracle.com/javase/tutorial/uiswing/events/keylistener.html](http://download.oracle.com/javase/tutorial/uiswing/events/keylistener.html)

---

### Post by orrymr on 2011-07-31
Thanks - I see I was going about this the complete wrong way...

---

