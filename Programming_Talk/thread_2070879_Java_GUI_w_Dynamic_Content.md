---
title: "Java GUI w/ Dynamic Content"
date: 2012-10-13
forum: Programming Talk
---

### Post by kevinharper on 2012-10-13
First time really creating a GUI on my own and I'm excited. It took me most of the day to read tutorials and get something somewhat created. I will post the code and then a few questions. I am also fairly new to Object-oriented programming.

```

import javax.swing.*;        
import java.awt.*;
import java.awt.event.*;

public class FrontEnd {
    /**
     * Generate & Display GUI.
     */
	private static void GUI() {
        //window
        JFrame window = new JFrame("Kevin Harper's CSV Reader");
        window.setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
        window.setSize(1100, 650);
        window.setResizable(false);
        
        JPanel panel = new JPanel();
	    window.getContentPane().add(panel);

	    panel.setLayout(null);

        //TOP (open button, save button, & search)
	    JButton openButton = new JButton("Open CSV File");
	    openButton.setBounds(1,1,150,20);
	    openButton.addActionListener(new ActionListener() {
	    	public void actionPerformed(ActionEvent event) {
	    		System.exit(0);
	    	}
		});
	    
	    JButton saveButton = new JButton("Save Search Results");
	    saveButton.setBounds(157,1,200,20);
	    saveButton.addActionListener(new ActionListener() {
	    	public void actionPerformed(ActionEvent event) {
	    		System.exit(0);
	    	}
		});
	    
	    final JTextField searchField = new JTextField("Search ID or Description", 250);
		/***
		 * Code for clearing searchField on focus and replacing text when
		 * 	not in focus taken from:
		 * 	http://stackoverflow.com/questions/5382436/text-box-cleared-when-receives-focus
		 **/
	    searchField.addFocusListener(new FocusListener() {
            @Override
            public void focusLost(FocusEvent arg0) {
                searchField.setText("Search ID or Description");
            }
            @Override
            public void focusGained(FocusEvent arg0) {
                // TODO Auto-generated method stub
            	searchField.setText("");
            }
        });

	    searchField.setBounds(738, 1, 250, 20);
	    
	    JButton searchButton = new JButton("Search");
	    searchButton.setBounds(989,1,100,20);
	    searchButton.addActionListener(new ActionListener() {
	    	public void actionPerformed(ActionEvent event) {
	    		System.exit(0);
	    	}
		});
	    
	    //MIDDLE (data table)
	    String[] tableHeader = {"ID", "Description", "Color", "Qty.", "Price"};
	    Object[][] tableData = {
	    	{new Integer(1), "Screw", "Yellow", new Integer(10), new Float(0.50)},
	    	{new Integer(2), "Scres Driver", "Yellow", new Integer(4), new Float(10.50)},
	    	{new Integer(3), "TV", "Black", new Integer(100), new Float(1000)},
	    	{new Integer(4), "Screw", "Yellow", new Integer(10), new Float(0.50)},
	    	{new Integer(5), "Scres Driver", "Yellow", new Integer(4), new Float(10.50)},
	    	{new Integer(6), "TV", "Black", new Integer(100), new Float(1000)},
	    	{new Integer(7), "Screw", "Yellow", new Integer(10), new Float(0.50)},
	    	{new Integer(8), "Scres Driver", "Yellow", new Integer(4), new Float(10.50)},
	    	{new Integer(9), "TV", "Black", new Integer(100), new Float(1000)},
	    	{new Integer(10), "Screw", "Yellow", new Integer(10), new Float(0.50)},
	    	{new Integer(11), "Scres Driver", "Yellow", new Integer(4), new Float(10.50)},
	    	{new Integer(12), "TV", "Black", new Integer(100), new Float(1000)},
	    	{new Integer(13), "Screw", "Yellow", new Integer(10), new Float(0.50)},
	    	{new Integer(14), "Scres Driver", "Yellow", new Integer(4), new Float(10.50)},
	    	{new Integer(15), "TV", "Black", new Integer(100), new Float(1000)},
	    	{new Integer(16), "Screw", "Yellow", new Integer(10), new Float(0.50)},
	    	{new Integer(17), "Scres Driver", "Yellow", new Integer(4), new Float(10.50)},
	    	{new Integer(18), "TV", "Black", new Integer(100), new Float(1000)},
	    	{new Integer(19), "Screw", "Yellow", new Integer(10), new Float(0.50)},
	    	{new Integer(20), "Scres Driver", "Yellow", new Integer(4), new Float(10.50)},
	    	{new Integer(21), "TV", "Black", new Integer(100), new Float(1000)},
	    	{new Integer(22), "Screw", "Yellow", new Integer(10), new Float(0.50)},
	    	{new Integer(23), "Scres Driver", "Yellow", new Integer(4), new Float(10.50)},
	    	{new Integer(24), "TV", "Black", new Integer(100), new Float(1000)},
	    	{new Integer(25), "Screw", "Yellow", new Integer(10), new Float(0.50)},
	    	{new Integer(26), "TV", "Black", new Integer(100), new Float(1000)},
	    	{new Integer(27), "Screw", "Yellow", new Integer(10), new Float(0.50)},
	    	{new Integer(28), "Scres Driver", "Yellow", new Integer(4), new Float(10.50)},
	    	{new Integer(29), "TV", "Black", new Integer(100), new Float(1000)},
	    	{new Integer(30), "Screw", "Yellow", new Integer(10), new Float(0.50)}
		};
	    
	    JTable resultsTable = new JTable(tableData, tableHeader);
	    JScrollPane scrollPane = new JScrollPane(resultsTable);
	    resultsTable.setPreferredScrollableViewportSize(new Dimension(1000, 503));
	    resultsTable.setFillsViewportHeight(true);
	    scrollPane.setBounds(1, 40, 1090, 503);
	    
	    //BOTTOM (result tracker/count, page tracker)
	    JLabel totals = new JLabel("Total:");
	    totals.setBounds(570, 545, 100, 20);
	    JLabel qtyTotal = new JLabel("QTY_TOTAL");
	    qtyTotal.setBounds(661, 545, 100, 20);
	    JLabel priceTotal = new JLabel("PRICE_TOTAL");
	    priceTotal.setBounds(881, 545, 100, 20);
	    JLabel resultsString = new JLabel("Viewing Records 61 - 90 of 5,000");
	    resultsString.setBounds(300, 575, 200, 20);
	    JLabel pagesString = new JLabel("Pages: << 1 | 2 | 3 | 4 | 5 >>");
	    pagesString.setBounds(660,575,200,20);
	    
	    panel.add(openButton);
	    panel.add(saveButton);
	    panel.add(searchField);
	    panel.add(searchButton);
	    panel.add(scrollPane);
	    panel.add(totals);
	    panel.add(qtyTotal);
	    panel.add(priceTotal);
	    panel.add(resultsString);
	    panel.add(pagesString);
	    
        //center window
        window.setLocationRelativeTo(null);
        
        //view window
        window.setVisible(true);
    }
 
    public static void main(String[] args) {
        //Create & show GUI
        javax.swing.SwingUtilities.invokeLater(new Runnable() {
            public void run() {
                GUI();
            }
        });
    }
}
```

I made the open, save, and search buttons close the window just to confirm that I had created them correctly.

My next step is to have the "Open" button pop up a file system navigation window and populate the table that way.

My questions:
1) Should the table and the text at the bottom each have it's own object class? This is information that gets generated dynamically and it needs to be repainted (right?).
2) Should I have my main program here? I will read a file and save the results to an arraylist. That array list will populate my first table. The user will then have the option to do a search. The search results will then populate the table.

I'm just not sure if this class should be my start class.

---

### Post by kevinharper on 2012-10-14
Maybe I didn't make my questions clear enough.

I have attached a picture of what the GUI looks like.

After the user selects a file for the program to read, the results are displayed in the table. A will then search and have only the results will be displayed.

---

### Post by KdotJ on 2012-10-14
Hi! Well done on creating your own GUI for the first time!

1) You are creating your table using a 2D array for the data. Take a deep look at Oracle's [Table Tutorial]("http://docs.oracle.com/javase/tutorial/uiswing/components/table.html") and read up on how to use a TableModel. If a JTable uses a TableModel for it's data, when the data in the model changes, the table will update to show these changes ("repaint" as you put it).

2) This falls into program design and is something that I believes takes a while to get into your head and understand the many different "design patterns" that are used in software. Each pattern serves different purposes. The one you should perhaps start of looking at is the Model-View-Controller pattern, which decouples to application logic from the GUI code.

Edit: 

With regards to searching etc, Java offers that kind of stuff with filtering and sorting for free (outlined [here]("http://docs.oracle.com/javase/tutorial/uiswing/components/table.html#sorting") in the Table Tutorial I linked). Again, this is another reason to use TableModel.

---

### Post by kevinharper on 2012-10-14
KdotJ, thank you for taking the time to reply to my post. And thank you for the positive feedback.

I used the term "repaint" because of the repaint() method. The table tutorial you make reference to is one of the many documents that I read prior to building the GUI. I re-read it and got a better idea of how data tables work. It did, however, generate another question - if I update the data will the new data automatically display within the table or do I have to somehow 'refresh'/repaint() the table so that the new information is displayed?

What about the text at the bottom? I do have to repaint that, right?

PS: I have decided to get rid of the "Open CSV File" button because there was I was running into a problem importing javax.jnlp.*;

Instead, I will look for rawData.csv in the current directory and read it as the program starts.

---

### Post by KdotJ on 2012-10-14
Hi Kevin, no need to say thanks!

Firstly in answer to your new question... If a JTable is linked to a TableModel then it will automatically update the table to reflect changes to the model. No need to refresh anything manually :D

As for the text at the bottom, yes this will need to be updated to show the right text... but this could be done by calling setText() on it... e.g.

```
resultsString.setText("blah blah blah...");
```

and this will update it on the GUI.

Lastly, not sure how you were trying things but there is no reason to import **javax.jnlp.*;** to read files from the local system.

---

### Post by kevinharper on 2012-10-14
I've spent the last few hours reading:
[http://www.javaworld.com/javaworld/jw-07-1999/jw-07-toolbox.html](http://www.javaworld.com/javaworld/jw-07-1999/jw-07-toolbox.html)
[http://www.javaworld.com/javaworld/jw-08-2003/jw-0801-toolbox.html](http://www.javaworld.com/javaworld/jw-08-2003/jw-0801-toolbox.html)
[http://www.javaworld.com/javaworld/jw-09-2003/jw-0905-toolbox.html?page=1](http://www.javaworld.com/javaworld/jw-09-2003/jw-0905-toolbox.html?page=1)

AWESOME! I didn't quite understand objects. These tutorials have cleared that up! I am going to toss what I have done so far and go at it differently.

> If a JTable is linked to a TableModel then it will automatically update the table to reflect changes to the model. No need to refresh anything manually
Nice! I had missed this point the first time I read the tutorial, and noticed something to that extent the last time I went through it. Which is why I asked. This makes things A LOT EASIER for me.

> but this could be done by calling setText() on it.
Nice! I will definitely incorporate this into my new design. I have a few more pages left to read, but am confident I will have most of this done tonight.

As for javax.jnlp.*, I was attempting to use it for a file browser-type frame where the user can navigate through his/her directories looking for files for the program to read. Several FileChooser examples I've seen use it, including [this Java tutorial example]("http://docs.oracle.com/javase/tutorial/uiswing/components/filechooser.html").

I would REALLY like to have it but, honestly, haven't really looked into this too much. I was hoping to find a segment of code online that I could cp and paste for this so I wouldn't be distracted from the development of the rest of the program (the real meat of it all).

---

### Post by 1clue on 2012-10-14
I guess somebody should ask a couple questions I haven't seen yet.

If you're looking for how to do things the "java" way, then what people have been saying is good advice.

If you want to know how to build all the mechanics behind these tables, then you probably want to do things differently just so you can figure out how much effort these classes (JTable etc) are saving you.  I recommend doing that much later, after you figure out how everyone else does it.

You probably want to get an overview of event handlers and event listeners, if you're planning on making an interactive Java app.

There's a couple things I've started doing that really help make the application maintainable.

First, I use what is called ubiquitous language.  This means that you use the same names for objects and methods that the user would use.  If you're making an accounting app then use accounting terms for the specific things you're coding.  If you see something that is a recognizable concept which can do things or have things done to it, then you should consider making it an object.  The things it can do or have done to it are verbs, so methods are verbs.  The properties the object has are nouns, and so properties (variables, etc) are nouns.

Most IDEs have automatic completion now.  So if you have a method that returns a variable, use a getter.  For example, your window has a frame, so window.getFrame() should return the frame. 

Second, I try to keep my classes strictly simple.  If it doesn't fit your ubiquitous language paradigm consider moving it to a utility class or find some other class for it.

---

### Post by kevinharper on 2012-10-14
Thanks for the advice 1clue! Great analogy using accounting, verbs and nouns.

Not sure what you meant by, "consider moving it to a utility class or find some other class for it", though.

I hope I can get this done in the next few days. Will keep you all posted as I progress through to completion. Besides, I'm sure I'll run into some issues along the way. :)

---

### Post by ofnuts on 2012-10-15
> **kevinharper said:**
> Thanks for the advice 1clue! Great analogy using accounting, verbs and nouns.

Not sure what you meant by, "consider moving it to a utility class or find some other class for it", though.

[LEFT] I hope I can get this done in the next few days. Will keep you all posted as I progress through to completion. Besides, I'm sure I'll run into some issues along the way. :)A "utility class" is a class that doesn't really represent objects but is is just use to gather together common functions (usually "static" ones). See for instance java.lang.StrictMath**.**[/LEFT]

---

### Post by 1clue on 2012-10-15
Exactly.

Java doesn't really have a 'function' type, a non-object-oriented functionality mechanism.  Everything you do needs to be attached to an object.

Because of that, Java programmers tend to make a utility class (StringUtils, ArrayUtils, FileUtils, ...) for functionality that doesn't really belong in a class, or belongs to a class you don't own.  As mentioned by ofnuts, usually all the methods in a utility class are static so you don't have to create the class first.

Technically the '...belongs to a class you don't own' situation calls for you to create a new class which extends the original, but if the original is a 'final' class then you can't do that.

---

### Post by kevinharper on 2012-10-15
Thank you. I'll have to read up on that because as of right now I'm interpreting it as a class with various "orphan" functions/methods?

Almost to serve as functions in a procedural program? :S
I ask because I've taken a look at a few examples and they seem to contain somewhat random methods just thrown into a class.

And I don't think that's completely accurate.

---

### Post by 1clue on 2012-10-15
Not really orphan, but your second statement about functions is right on the money.  Some functionality doesn't really fit into the object oriented paradigm very well.  There will inevitably be one or more utility functions in any application.

Another thing, try to avoid a single "god class" which knows all about everything.  One common mistake is to have all functionality go through a single interface which is sometimes called a 'god class.'  This is an example of model-view-controller (MVC) gone wrong.  The controller is a god class of sorts because it can know whatever it needs to know about another part of the app.  It is, as it were, the thing that controls the flow of the app in an MVC design.

Realistically if you're using that approach, the controller knows how to set up all the screens (views) in its area of focus.  It knows how to map the clicks from those views to the service layer and how to display the results.  But it doesn't need to be much more than glue, and it doesn't need to know about the entire application unless you have a really small application.

If you find yourself calling through a single class all the time which then delegates responsibility to any other part of the app, then that's a red flag.

---

### Post by kevinharper on 2012-10-15
Very glad you mentioned the God class, 1clue.

So then the user would interact with a controller. That controller tells an object to act like the object it represents. That object then returns an object, right?

So in my example, the searches through the data. The search string is passed from the controller to the search object. The search object internally searches through the data, and posts the data back to the JTable object. This Jtable object (with the data) is returned to the controller. It, in turn, acts like glue (as you put it) to display the returned object as part of the GUI seen by the user.

Right?

---

