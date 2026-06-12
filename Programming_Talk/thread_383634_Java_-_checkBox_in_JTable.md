---
title: "Java - checkBox in JTable"
date: 2007-03-13
forum: Programming Talk
---

### Post by serlex on 2007-03-13
I like to place a checkbox in a JTable, i got some sort of idea to use getColumnClass(int x), but dont know how you specify a column. here is the code
```
// Imports
import java.awt.*;
import java.awt.event.*;
import javax.swing.*;

class historyPane extends JPanel
 {
	// Instance attributes used in this example
	private	JPanel		topPanel;
	private	JTable		table;
	private	JScrollPane scrollPane;

	// Constructor of main frame
	public historyPane()
	{
		// Create columns names
		String columnNames[] = { "Order No", "Amount", "Payment type", "Paid","Status"};

		// Create some data
		String dataValues[][] =
		{
			{ "12", "234", "67", "43", "853"  },
			{ "-123", "43", "853" , "43", "853" },
			{ "93", "89.2", "109" , "43", "853" },
			{ "279", "9033", "3092", "43", "853"  }
		};
		
		// Create a new table instance
		table = new JTable( dataValues, columnNames );
		
		// Add the table to a scrolling pane
		scrollPane = new JScrollPane( table );
		table.setPreferredScrollableViewportSize(new Dimension(638, 450));
		add( scrollPane, BorderLayout.CENTER );
	}

}
```

I wanna turn Status column into checkbox

---

### Post by phossal on 2007-03-13
You're probably going to want to use an abstract table model. In Java Swing (O'Reilly), chapter 15 includes a simple example. Example 5-5, among others, includes simple checkbox values.

O'Reilly typically makes the source/example code from their books available for download. You can find the Swing examples here: [http://examples.oreilly.com/jswing2/code/](http://examples.oreilly.com/jswing2/code/)

---

