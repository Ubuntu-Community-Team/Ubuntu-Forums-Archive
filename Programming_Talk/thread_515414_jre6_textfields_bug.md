---
title: "jre6 textfields bug?"
date: 2007-08-01
forum: Programming Talk
---

### Post by obiwan on 2007-08-01
I've just installed the jdk6 but I'm having trouble with textfields. I can't edit  them when the window that contains it has opened another jframe or dialog. 

Is much easier to see it in the example I attach: The Main class is a JFrame with a textfield and a button. The button opens another instance of the main window, but when I try to edit the textfield of a previously opened frame I just can't.

This only happens using jre6 and jre7, with jre5 everything works fine. I have this problem with NetBeans too, so I can't use it because I can't write in it! (in fact in every swing application running in jre6).

I use Beryl, but I have the same problems when I switch to Metacity. 

Someone knows how to solve this? I want antialias in my swing applications!

The example: 
```
import java.awt.FlowLayout;
import java.awt.event.ActionEvent;
import java.awt.event.ActionListener;

import javax.swing.JButton;
import javax.swing.JFrame;
import javax.swing.JTextField;

public class Main extends JFrame {
	JTextField txt = new JTextField(10);

	public Main() {
		super();
		setLayout(new FlowLayout());
		add(txt);
		JButton btn = new JButton("Damn Bug!");
		btn.addActionListener(new ActionListener() {
			public void actionPerformed(ActionEvent e) {
				new Main().setVisible(true);
			}
		});
		add(btn);
		setSize(200, 100);
	}

	/**
	 * @param args
	 */
	public static void main(String[] args) {
		Main m = new Main();
		m.setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
		m.setVisible(true);
	}

}

```

---

### Post by kknd on 2007-08-01
I had this problem when using XGL too.

---

### Post by nitro_n2o on 2007-08-02
try to create the new window in a new Thread... that might solve it. 
I don't know just an idea

---

### Post by samjh on 2007-08-02
Java Swing is not compatible with Beryl.  That would be the cause of your problem.

[http://bugs.sun.com/bugdatabase/view_bug.do?bug_id=6509038](http://bugs.sun.com/bugdatabase/view_bug.do?bug_id=6509038)

Hopefully the recent Beryl/Compiz merge, and pressure  from the Java community itself, will result in a fix soon.

---

### Post by kknd on 2007-08-02
> **nitro_n2o said:**
> try to create the new window in a new Thread... that might solve it. 
I don't know just an idea

It's a Beryl / Compiz bug. As my ss shows, the bug didn't appear with Metacity.

Creating new threads would be a bad idea, since you're not supposed to use Swing out of the AWT-Event-Thread.

---

