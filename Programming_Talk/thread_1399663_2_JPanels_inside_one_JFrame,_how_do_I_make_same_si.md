---
title: "2 JPanels inside one JFrame, how do I make same size?"
date: 2010-02-06
forum: Programming Talk
---

### Post by SNYP40A1 on 2010-02-06
The following code is a simple example which creates 2 JPanels (each set to a different background color) and adds them to a JFrame.  How do I make both panels the same size, even during resizing?

[PHP]import java.awt.*;
import javax.swing.*;

public class Example extends JFrame {

	public Example()
	{
		try {
			UIManager.setLookAndFeel(UIManager.getSystemLookAndFeelClassName());
		} catch (Exception ignored) { }
		setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
		setLayout(new BorderLayout());
		
		JPanel panel1 = new JPanel();
		panel1.setBackground(Color.RED);
		JPanel panel2 = new JPanel();
		panel2.setBackground(Color.GREEN);
		this.add(panel1, BorderLayout.CENTER);
		this.add(panel2, BorderLayout.SOUTH);		
		
		pack();
		setVisible(true);			
	}

	public static void main(String args[])
	{
		Example example = new Example();		
	}
}[/PHP]

Note, adding these two lines:
[PHP]
		panel1.setPreferredSize(new Dimension(400,400));
		panel2.setPreferredSize(new Dimension(400,400));[/PHP]

Comes close to the solution...but not quite.

---

### Post by kahumba on 2010-02-06
```

import java.awt.*;
import javax.swing.*;

public class Example extends JFrame {

    public static void main(String args[]) {
        new Example();
    }

    public Example() {
        setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
        setLayout(new BorderLayout());

        JPanel p = new JPanel();
        setContentPane(p);
        p.setLayout(new BoxLayout(p, BoxLayout.PAGE_AXIS));

        JPanel panel1 = new JPanel();
        panel1.setBackground(Color.RED);
        JPanel panel2 = new JPanel();
        panel2.setBackground(Color.GREEN);
        p.add(panel1);
        p.add(panel2);
        setSize(200, 200);
        setVisible(true);
    }
}

```

---

### Post by SNYP40A1 on 2010-02-06
That works.  I tried using BoxLayout, but it didn't work.  I was trying to add the two JPanels directly to the JFrame.  Got some error about BoxLayout cannot be shared.  

If I want one window to be larger than the other, say a 4:1 size ratio, is the best way to do that by adding setPreferredSize(width, height * ratio) to the paintComponent method?  Only issue I see with that is that's it called everytime even when the window has not resized.  There's probably a resizeEventListener, I'll look for something like that if performance becomes a problem.

---

### Post by PaulM1985 on 2010-02-06
I think that instead of using BorderLayout.CENTER and BorderLayout.SOUTH as you were, if you used NORTH and SOUTH it should work.

Paul

Try using GridBagLayout for different ratios of sizes.  There is a GridBagConstraints class that you pass in as an argument and this sets the weighting.  Look it up on the Java API.

---

### Post by Shpongle on 2010-02-06
yea BorderLayout() will work or else GridLayou(2,0)

---

### Post by kahumba on 2010-02-07
```

import java.awt.*;
import javax.swing.*;

class P extends JPanel {
    private int percent;
    public P(int percent) {
        this.percent = percent;
    }

    @Override
    public Dimension getPreferredSize() {
        Dimension d = getParent().getSize();
        int w = d.width * percent / 100;
        int h = d.height * percent / 100;
        return new Dimension(w,h);
    }
}

public class Example extends JFrame {

    public static void main(String args[]) {
        new Example();
    }

    public Example() {
        setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
        JPanel p = new JPanel();
        setContentPane(p);
        p.setLayout(new BoxLayout(p, BoxLayout.PAGE_AXIS));

        JPanel panel1 = new P(80);
        panel1.setBackground(Color.RED);
        JPanel panel2 = new P(20);
        panel2.setBackground(Color.GREEN);
        p.add(panel1);
        p.add(panel2);
        setSize(200, 200);
        setVisible(true);
    }
}

```In this example the 1st panel here is 80% and second 20%.

Note: One can't add multiple panes to a JFrame, but people did this (mistake) so often that in a later release of the JRE Sun changed swing to propagate multiple add() calls to the underlying default content pane.
Note2: BoxLayout is special compared to former layout managers in that it actually honors the children's preferred size and the way it's constructed and attached to the container. Of course writing the GUI by hand is usually daunting by it's worth it.
[http://java.sun.com/docs/books/tutorial/uiswing/layout/box.html](http://java.sun.com/docs/books/tutorial/uiswing/layout/box.html)

---

### Post by SNYP40A1 on 2010-02-10
Thanks for your help.  Very clean solution, I like it.

---

