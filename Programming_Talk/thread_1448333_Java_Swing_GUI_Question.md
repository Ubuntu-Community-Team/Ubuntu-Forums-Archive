---
title: "Java Swing GUI Question"
date: 2010-04-06
forum: Programming Talk
---

### Post by SNYP40A1 on 2010-04-06
I have an application which produces a JFrame that contains several JPanels.  I would like to have a way to configure / add / remove different JPanels to the JFrame after the application is launched.  So I can add a menu bar which produces a pop-up window with the configuration info.  Problem is that each JPanel requires different parameters.  What would be the best way to handle this?

---

### Post by PaulM1985 on 2010-04-06
I am guessing that you only want to be showing one JPanel at any one time and you want to show/hide them.  Is this the case?

If so, I would create objects extending the JPanel class for each of the panels you want so each panel can be customised.

I think you should be able to add them all to the JFrame using a flow layout and use setVisible(true/false) to display the panel that you want.

Hope this is what you wanted to do.

Paul

---

### Post by hyperAura on 2010-04-06
Pop-up window to insert the parameters should be easy.. You can change visibility of your panels as Paul says so you can control that through the parameters you feed to the program..

---

### Post by SNYP40A1 on 2010-04-06
Actually, I do want to add multiple JPanels to a JFrame and I'm already doing that.  Currently, I instantiate each class that extends JPanel one at a time and then add them onto the JFrame.  The JPanels all scale nicely thanks to the layout manager.

What I want to do is add/remove the panels, but in order to create a new panel, the panel needs some parameters...the constructor requires parameters.  I want these parameters to be user-configurable, so yes, having a pop-up window come up for parameter entry would be ideal.  I know how to generate such a pop-up window, but what's the best way to fill out the parameters on the window?  That code should probably go in each class because each class knows best...I am thinking something like this:

```

class myPanel extends JPanel
{

    public myPanel(int parameter1, double parameter2, Mode parameter3...);

    public myPanel()
    {
         JFrame paramFrame = new JFrame();
         JPanel paramPanel = new JPanel();
         paramPanel.add(new JLabel("Parameter 1"));
         paramPanel.add(new JTextField(...
         /*more code to setup panel here
               ...
         */
         paramFrame.add(paramPanel);
         paramFrame.setVisible(true);
    }
}

```

So I could make a parameter-less constructor for each panel class that I want to display.  The constructor would pop up a new window, user enters parameters, then the information is passed to the other constructor to generate the panel.  Problem is that that's a lot of work and repeated code for the several panel types that I plan to create.  I figured there would probably be a library for generating option parameter windows.

A better way to do this would be to make one generic options display class.  Each Panel class that I want to display has a default constructor which generates an instance of the options window.  It passes the options window a map of <string, string>.  The first string is the parameter names.  The second string will store the values that the user entered in the window.  The options window display class simply adds one JLabel and JTextbox to itself per parameter.  The user enters values for each parameter, then presses update.  At which time, the option window stores the values entered into the map and passes it back to the class which called it.  Anyone got a better idea?

---

### Post by PaulM1985 on 2010-04-07
What sort of parameters are you storing for the panel?  Things like size or is it something to do with state or values in textboxes etc.  Could really do with knowing what these are..

Having a stab in the dark...
I think I would give each of the panels an Id and create a new parameter store class (ParamStore maybe).  In the constructor for the param store, all of the default values for each of the panels can be defined.  This is assuming that there is a fixed number of panels.  The default values could be read in from some text file maybe.

The parameter store would be an ArrayList of ArrayLists of strings.  (ArrayList<ArrayList<String>>, I think this is allowed).

Each id for you panels is an index in the ArrayList.  You can get your arraylist for the panel, then iterate through the strings in the arraylist that is returned to get the parameters out.

When calling the constructor for each of your panels, you would pass in the appropriate index of the ParamStore, so all of the values from the paramstore are passed in.  Then you can update the values in the param store in the panel class after you have closed the popup window.

When closing the program, all of the values in the param store could be saved out to file.

Strings in the paramstore array could be in the form "Some Parameter - SomeValue" so that it doesn't necessarily matter on the index in the arraylist, you could parse the string, find out which parameter it refers to and set the appropriate value.

Paul

PS.
The JFrame would own the ParamStore and pass into each constructor the appropriate Array of parameter strings.  This way each panel has a reference to its parameters, but the frame has overall ownership of all of the objects.

---

