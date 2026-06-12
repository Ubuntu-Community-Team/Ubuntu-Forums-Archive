---
title: "Java memory leak"
date: 2011-06-01
forum: Programming Talk
---

### Post by Petrolea on 2011-06-01
Hi everyone!

I was just starting creating an app when I for some unknown reason started observing its memory usage. It is a simple program with 2 buttons, nothing else.

If I keep pressing buttons, memory usage starts to increase rapidly (about 0.01 MiB per 4-5 clicks which isn't a small amount). Is this normal for a program to do?

If not, this is the code, hopefully someone can find a place where memory keeps leaking:

[PHP]
import java.awt.*;
import java.awt.event.*;
import javax.swing.*;

@SuppressWarnings("serial")
class Panel extends JPanel implements ActionListener
{
	public void paintComponent(Graphics g)
	{
		super.paintComponent(g);
		gumb1 = new JButton("Gumbek 1");
		gumb2 = new JButton(new ImageIcon("slika.jpg"));
		gumb1.setActionCommand("gumb1");
		gumb2.setActionCommand("gumb2");
		add(gumb1);
		add(gumb2);
		gumb1.addActionListener(this);
		gumb2.addActionListener(this); 
	}
	
	public void actionPerformed(ActionEvent event)
	{
			
	}
	
	JButton gumb1;
	JButton gumb2;
	
}

@SuppressWarnings("serial")
class Okno extends JFrame
{
	public void Exitaj()
	{
		addWindowListener(new WindowAdapter()
		{
			public void windowClosing(WindowEvent e)
			{
				System.exit(0);
			}
		});
	}
	
	public Okno()
	{
		Exitaj();
		Toolkit toolkit = Toolkit.getDefaultToolkit();
		Dimension dimension = toolkit.getScreenSize();
		Container vsebinaPanela = getContentPane();
		Image slika = toolkit.getImage("slika.jpg");
		
		setTitle("Program");
		int x_screen = dimension.width;
		int y_screen = dimension.height;
		setSize(x_screen / 2, y_screen / 2);
		setLocation(x_screen / 4, y_screen / 4);		
		setIconImage(slika);
		setResizable(false);
		vsebinaPanela.add(new Panel());
	}
			
}

public class Glavni 
{
	public static void main(String[] args)
	{
		JFrame okno = new Okno();
		okno.setVisible(true);
		
	}
}
[/PHP]

I didn't change the language because the code is pretty straightforward.

Thanks in advance!

---

### Post by Zugzwang on 2011-06-01
You shouldn't add buttons in the paintComponent() function of a Panel. This way, every time paintComponent() is called, more and more buttons are added. Rather do that in its constructor.

Other than that, note that Java's memory management is kind of non-deterministic. The JVM decides when to collect unused objects and when to increase the memory footprint. Just make sure that you don't keep references to objects that you don't need any longer.

---

### Post by Petrolea on 2011-06-01
> **Zugzwang said:**
> You shouldn't add buttons in the paintComponent() function of a Panel. This way, every time paintComponent() is called, more and more buttons are added. Rather do that in its constructor.


Ah, I see, don't know why I didn't remember that. Thanks for help, will mark as solved.

---

