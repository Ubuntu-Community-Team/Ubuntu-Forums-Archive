---
title: "Fire an event with a custom component in java"
date: 2009-10-05
forum: Programming Talk
---

### Post by kirbyboy on 2009-10-05
Hi, i'm making a custom component(it's only a JPanel with some squares draw at hand), but i don't know how to launch a ActionEvent from there.
An example(my english is not very good):
My custom component names GridCard.
If i made a simple gui program with a JPanel called panel1 and i do:
panel1.add(button1)           //a generic button.
panel1.add(text1)            //a generic text box/label, doesn't mind.
panel1.add(grid1)           //an instance of my custom component GridCard.

when i put the next code:
	public void actionPerformed(ActionEvent e)
  	{
		
    	    if (e.getSource() == button1)
		{
			text1.setText("hi");
		} 
	    else if (e.getSource() == grid1)
		{
			text1.setText("goodbye");
		} 
  	}

When i click in the button(or press space when the focus is in the button), the actionPerformed is launched.  How do i do so all the code works(that actionPerformed is launched when i click in grid1)?, thanks.

---

### Post by dwhitney67 on 2009-10-05
Consider defining your GridCard as a subclass of AbstractButton.

```

import javax.swing.*;
import java.awt.event.*;

class GridCard extends AbstractButton
{
   ...
}


public class MyClass extends JFrame implements ActionListener
{
   public MyClass()
   {
      JPanel   panel = new JPanel();
      GridCard gc    = new GridCard();

      gc.addActionListener(this);

      panel.add(gc);

      // ...
   }

   public void actionPerformed(ActionEvent event)
   {
      ...
   }
}

```

---

### Post by kirbyboy on 2009-10-06
Hi, i read the documentation about AbstractButton, but i think it's not what i need.
I draw some squares in a JPanel, the ActionEvent should fire only when i clicked inside one of those squares, if i use an AbstractButton the event launchs when i click in the button, not in the squares draw by me.
I read something in:
[http://www.j2ee.me/j2ee/1.4/docs/tutorial-update2/doc/JSFCustom7.html#wp114206](http://www.j2ee.me/j2ee/1.4/docs/tutorial-update2/doc/JSFCustom7.html#wp114206)
but it's overcomplicated and i would like to use only java standard, so i don't have to learn j2ee for now.

Reading the documentation, it doesn't like that i can choose one or some areas that launch the ActionEvent, if i'm wrong, please, tell me how to choose the "clickable" areas.

---

### Post by Reiger on 2009-10-06
You could (a) override the paint method of buttons to look like squares and paint buttons instead of squares; (b) add a mouse listener (consider a subclass of MouseAdapter) to the panel which in turn notifies the buttons.

The benefit of (a) is that it is more flexible (you can incorporate keyboard navigation) and can be made to work rather better in the case the user is able to resize the panel... Once the visuals become more complex/unique per card you can easily move to external PNG files for icons too.

The benefit of (b) is that it is easier to do: simply create your own custom ActionEvent objects and call actionPerformed() on the various AbstractActions when you have found the right one to call based on x/y coordinate comparisons.

---

### Post by kirbyboy on 2009-10-07
Hi, i choose b), it's exactly what i was doing(at least what i was trying).
I tried to make it a subclass of AbstractButton, but the ActionPerformed didn't launch, so i tried another test and make it directly a subclass of JButton.  The control acted like a button(it visually clicked, but it's not what i want), but the ActionPerformed didn't launch, so it must be some method that must be overwritten to launch the ActionPerformed, so if i make it a subclass of AbstractButton and i discover how to launch the ActionPerformed, all will be done.  Can you tell me which method i must overwrite to fire the ActionPerformed?.
I think this should be, but i'm not sure:
[http://java.sun.com/j2se/1.4.2/docs/api/javax/swing/AbstractButton.html#fireActionPerformed(java.awt.event.ActionEvent](http://java.sun.com/j2se/1.4.2/docs/api/javax/swing/AbstractButton.html#fireActionPerformed(java.awt.event.ActionEvent))

edit: Making it a subclass of JButton it launchs the ActionPerformed(i had forget to add the actionListener with the "grid1.addActionListner(this)" command), but not making it a subclass of AbstractButton.

---

### Post by kirbyboy on 2009-10-12
It was easier than i thought, i was looking at "Thinking in Java" when i found an example of what i needed.
At the end i used a JPanel(i suppose it works too with an AbstractButton), and when i receive a click in the dessired area i only have to launch the next code:
actionListener.actionPerformed(new ActionEvent(CardGrid.this, ActionEvent.ACTION_PERFORMED, null));

With this, i can get the actionPerformed when i want.  Thanks for all the help.

---

