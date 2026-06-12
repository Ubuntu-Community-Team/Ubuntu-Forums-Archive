---
title: "Java Question - Starting an app as maximized?"
date: 2007-09-07
forum: Programming Talk
---

### Post by Fireblend on 2007-09-07
Hello, I'm currenlty working on an university assignment which has to be made on Java, and I'd like the app to start as a maximized window. I tried using the method [setExtendedState]("http://java.sun.com/javase/6/docs/api/java/awt/Frame.html#setExtendedState(int)") but it isn't working at all. 

I'm guessing this should be possible, but I just can't find the correct method or the way I should be using the above one.

Any help is appreciated! :)

---

### Post by tenmillionmilesaway on 2007-09-07
Not sure about maximised but you can find the resolution of the screen by Toolkit.getDefaultToolkit and then its one of the methods of the toolkit to get the bounds (can remember it off hand, look in javadocs)  You can then set the size of your window to the screen size and its almost as good.
Hope this helps

---

### Post by pbrockway2 on 2007-09-07
> Not sure about maximised but you can find the resolution of
> the screen by Toolkit.getDefaultToolkit and then its one of the
> methods of the toolkit to get the bounds

Using the Toolkitkit method getScreenSize() is one way.  It is discussed in Real's HowTo.  [http://http://www.rgagnon.com/javadetails/java-0222.html]("http://http://www.rgagnon.com/javadetails/java-0222.html")

setExtendedState() is another - but make sure the frame is packed first.  Something like this:```
import java.awt.BorderLayout;
import java.awt.Frame;
import java.awt.Toolkit;

import javax.swing.JFrame;
import javax.swing.JLabel;
import javax.swing.SwingUtilities;

public class MaxWin extends JFrame {

    MaxWin() {
        setTitle("Maximised!");
        add(new JLabel("Content here"), BorderLayout.CENTER);
    }
	
    public static void main(String args[]) {
        boolean supported = Toolkit.getDefaultToolkit().isFrameStateSupported(Frame.MAXIMIZED_BOTH);
        System.out.printf("Supported: " + supported);
        SwingUtilities.invokeLater(new Runnable() {
            public void run() {
                JFrame test = new MaxWin();
                test.setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
                
                test.pack();
                test.setExtendedState(Frame.MAXIMIZED_BOTH);
                test.setVisible(true);
            }
        });
    }
}
```

---

