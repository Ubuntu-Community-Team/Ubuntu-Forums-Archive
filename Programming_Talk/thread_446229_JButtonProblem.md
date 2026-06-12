---
title: "JButtonProblem"
date: 2007-05-16
forum: Programming Talk
---

### Post by Ameliorate on 2007-05-16
I know this is kind of a simple question but,
I haven't programmed for 2 years (I took java for 2 years in high school)

so help me here for just a sec

here is the source
package test;
import javax.swing.*;
import java.awt.*;
import java.awt.event.*;

public class PaneTester extends JFrame implements ActionListener
{
	/**
	 * 
	 */
	private static final long serialVersionUID = 1L;
	JButton quit;
	PopupMenu popup = new PopupMenu("try again");
	Graphics g;
	
	PaneTester()
	{
		JOptionPane.showMessageDialog(null, "Test", "this is a test",
				JOptionPane.INFORMATION_MESSAGE);
		setSize(800,800);
		setLocation(400,200);
		setBackground(Color.green);
		
		quit = new JButton("QUIT");
		quit.setBounds(50,50,10,35);
		quit.setForeground(Color.blue);
		quit.addActionListener(this);
		getContentPane().add(quit);

		setVisible(true);
	}//end main method
	
	public void actionPerformed(ActionEvent evt)
	{
		if(evt.getSource() == quit)
			System.exit(1);
	}
/*	
	public void paint(Graphics g)
	{
		
		
	}
*/	
	public static void main(String args[])
	{
		PaneTester pt = new PaneTester();
		pt.setDefaultCloseOperation(EXIT_ON_CLOSE);
	}

}//end class PaneTester


and i just get a frame with a big button
 why?


[IMG]file:///home/kent/Desktop/Screenshot1.png[/IMG]

---

### Post by JT673 on 2007-05-16
I'm assuming that you want to position stuff according to the call to setBounds(int, int, int , int), so you can just:

```
getContentPane().setLayout(null);
```

Before setVisible(true);

---

### Post by Ameliorate on 2007-05-17
thanks, it worked. I'll remember that setLayout method
should have already known it (hehe...)

---

