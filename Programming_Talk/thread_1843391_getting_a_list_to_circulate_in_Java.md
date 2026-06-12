---
title: "getting a list to circulate in Java"
date: 2011-09-13
forum: Programming Talk
---

### Post by poodoopealeoaph on 2011-09-13
I've been trying to figure out this program for this week of my Java programming class and I can't seem to figure it out. I need to figure out how to get my next and previous buttons to go in a circular pattern. So, when I'm at the last listing and I hit next, it should show me the first listing and vise versa with the previous. here is the code... <code>
import javax.swing.*;
import java.awt.event.*;

//Stores and then gets info on a DVD
public class Application_DVD extends JFrame 
{

	private JTextArea txt;
	private Inventory inv;
	private int currentDisplay = 0;
	
	public Application_DVD() 
	{
		super("DVD Program");
		setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE); // quit if the window is closed
		init();
	}
	
	public void init() 
	{
		//make 3 objects
		ExtendedDVD p1 = new ExtendedDVD(1, "Carlito's Way", 3, 19.99, "Universal");
		ExtendedDVD p2 = new ExtendedDVD(2, "Archer Se#1", 1, 18.99, "Touchstone");
		ExtendedDVD p3 = new ExtendedDVD(3, "The Goonies", 4, 15.49, "Warner Brothers");

		// make an inventory and put in the objects
		inv = new Inventory();
		inv.add(p1);
		inv.add(p2);
		inv.add(p3);
		
		inv.sort();

//		output the info

		for (int i = 0; i < inv.size(); i++) 
		{
			System.out.println("Item number: " + inv.get(i).getItem());
			System.out.println("DVD name: " + inv.get(i).getName());
			System.out.println("Units in stock: " + inv.get(i).getUnits());
			System.out.println("Price: $" + String.format("%.2f",inv.get(i).getPrice()));
			System.out.println("Total value: $" + String.format("%.2f",inv.get(i).value()));
			System.out.println("Fee: $" + String.format("%.2f",inv.get(i).fee()));
			System.out.println();
		}

		//total val
		System.out.println("Total value: $" + String.format("%.2f",inv.value()));
		
		// setup the interface
		JPanel panel = new JPanel();
		txt = new JTextArea(15,40);
		txt.setEditable(false);//user shouldn't change it
		panel.add(txt);
		
		JButton next = new JButton("Next");
		next.addActionListener(new ActionListener() 
		{
			public void actionPerformed(ActionEvent e) 
			{
				if (currentDisplay < inv.size()-1) currentDisplay++; //advance to the end
				displayDVD();
			}
		});
		
		JButton previous = new JButton("Previous");
		previous.addActionListener(new ActionListener()
		{
			public void actionPerformed(ActionEvent a)
			{
				if (currentDisplay < inv.size()+1) currentDisplay--;
				displayDVD();
			}
		});
		
		JButton first = new JButton("First");
		first.addActionListener(new ActionListener()
		{
			public void actionPerformed(ActionEvent b)
			{
				if (currentDisplay < inv.size()+3) currentDisplay--;
				displayDVD();
			}
		});
		
		JButton last = new JButton("Last");
		last.addActionListener(new ActionListener()
		{
			public void actionPerformed(ActionEvent e)
			{
				if (currentDisplay < inv.size()+1) currentDisplay = 2;
				displayDVD();
			}
		});
		
		panel.add(first);
		panel.add(previous);
		panel.add(next);
		panel.add(last);
		
		getContentPane().add(panel);
		
		displayDVD();
	}
	
	// view software
	public void displayDVD() 
	{
		txt.setText("DVD Details:\n");
		txt.append("Item number: " + inv.get(currentDisplay).getItem() + "\n");
		txt.append("DVD name: " + inv.get(currentDisplay).getName() + "\n");
		txt.append("Units in stock: " + inv.get(currentDisplay).getUnits() + "\n");
		txt.append("Price: $" + String.format("%.2f",inv.get(currentDisplay).getPrice()) + "\n");
		txt.append("Total value: $" + String.format("%.2f",inv.get(currentDisplay).value()) + "\n");
		txt.append("Fee: $" + String.format("%.2f",inv.get(currentDisplay).fee()) + "\n\n");
	
		txt.append("Total value: $" + String.format("%.2f",inv.value()));

	}
	
	public static void main(String args[]) 
	{
		Application_DVD gui = new Application_DVD();
		gui.pack();
		gui.setVisible(true);
	}
//		
}
</code>

what am I doing wrong?!?

---

### Post by poodoopealeoaph on 2011-09-13
```

import javax.swing.*;
import java.awt.event.*;

//Stores and then gets info on a DVD
public class Application_DVD extends JFrame 
{

	private JTextArea txt;
	private Inventory inv;
	private int currentDisplay = 0;
	
	public Application_DVD() 
	{
		super("DVD Program");
		setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE); // quit if the window is closed
		init();
	}
	
	public void init() 
	{
		//make 3 objects
		ExtendedDVD p1 = new ExtendedDVD(1, "Carlito's Way", 3, 19.99, "Universal");
		ExtendedDVD p2 = new ExtendedDVD(2, "Archer Se#1", 1, 18.99, "Touchstone");
		ExtendedDVD p3 = new ExtendedDVD(3, "The Goonies", 4, 15.49, "Warner Brothers");

		// make an inventory and put in the objects
		inv = new Inventory();
		inv.add(p1);
		inv.add(p2);
		inv.add(p3);
		
		inv.sort();

//		output the info

		for (int i = 0; i < inv.size(); i++) 
		{
			System.out.println("Item number: " + inv.get(i).getItem());
			System.out.println("DVD name: " + inv.get(i).getName());
			System.out.println("Units in stock: " + inv.get(i).getUnits());
			System.out.println("Price: $" + String.format("%.2f",inv.get(i).getPrice()));
			System.out.println("Total value: $" + String.format("%.2f",inv.get(i).value()));
			System.out.println("Fee: $" + String.format("%.2f",inv.get(i).fee()));
			System.out.println();
		}

		//total val
		System.out.println("Total value: $" + String.format("%.2f",inv.value()));
		
		// setup the interface
		JPanel panel = new JPanel();
		txt = new JTextArea(15,40);
		txt.setEditable(false);//user shouldn't change it
		panel.add(txt);
		
		JButton next = new JButton("Next");
		next.addActionListener(new ActionListener() 
		{
			public void actionPerformed(ActionEvent e) 
			{
				if (currentDisplay < inv.size()-1) currentDisplay++; //advance to the end
				displayDVD();
			}
		});
		
		JButton previous = new JButton("Previous");
		previous.addActionListener(new ActionListener()
		{
			public void actionPerformed(ActionEvent a)
			{
				if (currentDisplay < inv.size()+1) currentDisplay--;
				displayDVD();
			}
		});
		
		JButton first = new JButton("First");
		first.addActionListener(new ActionListener()
		{
			public void actionPerformed(ActionEvent b)
			{
				if (currentDisplay < inv.size()+3) currentDisplay--;
				displayDVD();
			}
		});
		
		JButton last = new JButton("Last");
		last.addActionListener(new ActionListener()
		{
			public void actionPerformed(ActionEvent e)
			{
				if (currentDisplay < inv.size()+1) currentDisplay = 2;
				displayDVD();
			}
		});
		
		panel.add(first);
		panel.add(previous);
		panel.add(next);
		panel.add(last);
		
		getContentPane().add(panel);
		
		displayDVD();
	}
	
	// view software
	public void displayDVD() 
	{
		txt.setText("DVD Details:\n");
		txt.append("Item number: " + inv.get(currentDisplay).getItem() + "\n");
		txt.append("DVD name: " + inv.get(currentDisplay).getName() + "\n");
		txt.append("Units in stock: " + inv.get(currentDisplay).getUnits() + "\n");
		txt.append("Price: $" + String.format("%.2f",inv.get(currentDisplay).getPrice()) + "\n");
		txt.append("Total value: $" + String.format("%.2f",inv.get(currentDisplay).value()) + "\n");
		txt.append("Fee: $" + String.format("%.2f",inv.get(currentDisplay).fee()) + "\n\n");
	
		txt.append("Total value: $" + String.format("%.2f",inv.value()));

	}
	
	public static void main(String args[]) 
	{
		Application_DVD gui = new Application_DVD();
		gui.pack();
		gui.setVisible(true);
	}
//		
}

```
there it is... oh and just to clarify, the program is basically to list three movies. I have three other classes that are fine, I just need to figure out the buttons.

---

### Post by dethorpe on 2011-09-13
Think you just need a check in your next & prev action Listeners.
 
for next, check if  currentDisplay is allready at the end (i.e. equals size of inv -1), if so set to 0, otherwise increment.
 
For prev, check for currentDisplay being 0, if so set to last entry in inv (i.e. size of inv -1), otherwise decrement.

---

