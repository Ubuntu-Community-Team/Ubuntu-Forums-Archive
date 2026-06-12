---
title: "Drawing Swing Components in an arbritrary place?"
date: 2009-08-31
forum: Programming Talk
---

### Post by Fallen_Demon on 2009-08-31
Hey people,

Having a damn hard time trying to draw a JTextArea onto what is essentially a JPanel. My code is something like:
```

SwingUtilities.paintComponent(textareaWidget, xCoord,yCoord);

```

This, however, throws a null pointer exception, complaining about a non existing CellRendererPane.

I also went the other way, and tried instantiating a CellRendererPane and doing the same thing, but it just refused to draw. No errors, no nothing (it worked for regular drawing activities, though. I drew a rectangle in the right spot)

Anyone got some sample code for me to look at? I'm hard pressed finding jack on Google

---

### Post by Ragazzo on 2009-08-31
Here's an example that draws a JTextArea on a JList

```

import javax.swing.*;
import java.awt.*;

public class Test {
	public static void main(String...args) {
		SwingUtilities.invokeLater(new Runnable() {
			public void run() {
				JFrame frame = new JFrame();
				frame.setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
				final JTextArea area = new JTextArea("hello\nworld");
				final Container container = new Container();
				JList list = new JList(new String[]{ "one", "two", "three", "four", "five"}) {
					protected void paintComponent(Graphics g) {
						super.paintComponent(g);
						SwingUtilities.paintComponent(g, area, container, 20, 20, 60, 60);
					}
				};
				frame.add(list);
				frame.setSize(200, 200);
				frame.setVisible(true);
			}
		});
	}
}

```

Hope it helps

---

### Post by Fallen_Demon on 2009-08-31
Ah, I understand :) It has to keep painting it in order to keep the graphics up to date :) Thanks, that helps a lot

---

