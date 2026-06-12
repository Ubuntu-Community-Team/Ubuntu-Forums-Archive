---
title: "Animated GIF in Java GUI"
date: 2007-04-14
forum: Programming Talk
---

### Post by derby007 on 2007-04-14
Can I put an animated GIF onto my main screen/frame in my Java GUI. Is it complicated, thread-safe, etc, as I remember reading somewhere about a bug with GIF's and threads...

---

### Post by samjh on 2007-04-14
There was a bug where GIF icons could cause thread deadlocks.  But this was fixed for 1.4.

Just use the ImageIcon class, as usual for setting images into components.  You will need to use setImageObserver method for animated GIFs.  Refer to the JDK API documentation, under the ImageIcon class.

---

### Post by phossal on 2007-04-14
O'Reilly's book, "Java Swing", 2nd Ed by Loy, Marc et. al. has the following example:

```
//AnimationApplet.java
import javax.swing.*;

//A simple animation applet
public class AnimationApplet extends JApplet {
	public void init() {
		ImageIcon icon = new ImageIcon("images/rolling.gif"); //Animated gif
		getContentPane().add(new JLable(icon));
	}
}
```

All of the books examples are available online with source.

---

### Post by derby007 on 2007-04-14
Cheers for that, but if I'm not using applets do i still need to implement an applet in my JFrame to get GIFs to work?

---

### Post by phossal on 2007-04-14
No. ;) You should check out some of the other examples. [Java Swing, O'Reilly]("http://examples.oreilly.com/jswing2/code/")

---

### Post by derby007 on 2007-04-14
will do.... :)

---

