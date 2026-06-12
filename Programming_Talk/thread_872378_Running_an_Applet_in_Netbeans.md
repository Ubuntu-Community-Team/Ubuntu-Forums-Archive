---
title: "Running an Applet in Netbeans"
date: 2008-07-27
forum: Programming Talk
---

### Post by ceclauson on 2008-07-27
Hello!

I'm trying to run a Java applet in Netbeans.  All the sources I can find say that you simply right click the file and choose "Run File" from the pop-up menu, but when I do this I get an error that says "Class [class name] does not have a main method".

Thanks,
Cooper

---

### Post by tinny on 2008-07-27
I just created an empty Applet in NetBeans right clicked it > "Run File" and it worked. NetBeans detected that the class extends "JApplet", does yours extend JApplet?

Maybe you could do a "Clean and Build" on your project to try and get it to refresh

Failing this perhaps you could post your code...

---

### Post by ceclauson on 2008-07-28
Thanks for your reply :-)

I tried creating a new project with a new applet, copied the old code in, and it ran, oddly enough. Not sure why it didn't run the original.  It still won't. Here's the code for reference:
```

package miscellaneous;

import javax.swing.*;
import java.awt.*;
        
/**
 *
 * @author ceclauson
 */
class FocusTester extends JApplet {
    
    @Override
    public void init() {
        this.setLayout(new FlowLayout());
        JTextField tf1 = new JTextField();
        JTextField tf2 = new JTextField();
        JTextField tf3 = new JTextField();
        
        this.add(tf1);
        this.add(tf2);
        this.add(tf3);
    }
    
}

```
I'm pretty happy with this, but I still have no idea why it won't run the original.

Thanks again,
Cooper

---

### Post by tinny on 2008-07-28
:confused:

What was the original project type? "Java Class Library" or "Java Application"?

What version of NetBeans?

---

### Post by ceclauson on 2008-07-28
The project type is "Java Application," but I created two new projects, one a Java application and the other a Class Library, and in both I was able to create and run a working applet.

My Netbeans version is 6.1.

---

### Post by miki4242 on 2009-11-16
The class FocusTester needs to be public. Then NetBeans will run it as an applet.

---

