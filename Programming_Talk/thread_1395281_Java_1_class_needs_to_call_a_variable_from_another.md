---
title: "Java 1 class needs to call a variable from another class"
date: 2010-01-31
forum: Programming Talk
---

### Post by l951b951 on 2010-01-31
Let me begin by saying, this is for a school assignment, so please please teach me to fish rather than give me one.

The assignment is to create a simple GUI calculator, 2 text fields to input data and 4 buttons to correspond with add/subtract/multiply/divide, and a JLabel to display results.  Our programming goal is to be modular, so I have created 3 sources (i think that's the word - 3 documents that end in .java).  I created these 2 other classes to make my main class have as much abstraction as possible.

1. Mycalc.java Includes my main class, creates the frame, panels, and sets up layouts.
2.  AutoButton.java - is a class that creates a new button with an action listener receiving its title and tooltip text from creation.  Currently (just for testing) my buttons simply do a print line so I can make sure they work.
3. Autotextfield.java - creates a textfield and creates an action listener for each.  

The trouble I am having now is that within my AutoButtons I need them to use gettext() on the textfields which are defined in autotext.java and instantiated in mycalc.java.  I think the solution is to make each autobutton click create 2 variables (one for each textfield), use those 2 variables for the calculation, output the results into a 3rd variable, and update my JLabel to show the results (the 3rd variable).  

I only know how to do 1 of these 4 things (use the variables for calculations).  I need help figuring out how to:
1. make a button click in an instance of autobutton.java create 2 variables using gettext() for the textfield.
2. have that same button click create and assign a value to a 3rd variable.
3. have that same button click refresh and redraw a JLabel to display its value.


These all seem to be accomplish-able if I could just figure out how to have one class call methods from another class.

---

### Post by Reiger on 2010-01-31
You mean you want to export the textual symbol on the button (e.g. &#8216;6&#8217;) to the label/calculation &#8216;window&#8217; that displays the calculation as it is being entered?

Consider then to use *one* action listener to listen for/control application state via events among multiple components; you can use the getSource() method on the ActionEvent object to obtain the source which fired to event -- and get obtain the model/data from there.

---

### Post by l951b951 on 2010-01-31
> **Reiger said:**
> You mean you want to export the textual symbol on the button (e.g. ‘6’) to the label/calculation ‘window’ that displays the calculation as it is being entered?

Consider then to use *one* action listener to listen for/control application state via events among multiple components; you can use the getSource() method on the ActionEvent object to obtain the source which fired to event -- and get obtain the model/data from there.

Not exactly.  I want to get the numbers entered into the textfield for the calculations.  So, for example, you enter 2 and 3 into the text fields, when you press the addition button, it will get the those two items, parse them to float, and then perform var1 + var2 where var1 is from textfield1.getText() and var2 is from textfield2.getText().

---

### Post by Reiger on 2010-01-31
That is possible too with the central ActionListener design. You merely have to ensure that the text field is visible to the ActionListener to do that; e.g. pass the text field to the constructor of the ActionListener object to keep a reference to it.
```

JTextfield field =new JTextfield();
MyCustomActionListener mcal = new MyCustomActionListener(field);

```

---

