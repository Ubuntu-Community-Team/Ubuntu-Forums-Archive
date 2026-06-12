---
title: "GUI Classes (Java)"
date: 2012-11-17
forum: Programming Talk
---

### Post by kevinharper on 2012-11-17
I want to go with JTabbedPanels for my next (and final) project for my Java class.

[http://docs.oracle.com/javase/tutorial/uiswing/components/tabbedpane.html](http://docs.oracle.com/javase/tutorial/uiswing/components/tabbedpane.html)

In my last project I used CardLayout and put ALL of the code for ALL of my panels on a single class. Is this how it is normally done? If I want 10 tabs do I have to place the code for all 10 content panels in a single class?

I think it would be more easily maintained if each had it's own class and somehow each class was called to be displayed when its corresponding tab was clicked.

---

### Post by slickymaster on 2012-11-18
Well, I normally use GridBagLayout, but that really doesn't have influence in the question. What is important and what you should always keep in mind, is to make your code easy and logic to read and understand.

Myself, I always have a class for each of the tabs, and always keep in mind the MVC (Model-View-Control) paradigm, regarding the way I design and code my projects.

---

### Post by Unterseeboot_234 on 2012-11-18
I usually have a class for the JPanel that inserts into the JTabbed. Let's say one of your tabs is 'Options'

public class Options extends JPanel {
vars

public Options() {
this.setLayout( new BorderLayout() );
...
}
/////////////
Then in the class that will be the JTabbedPane
public class JTabbedPanel extends JPanel {
// here you can have vars, or...(see below)
private Options options;
private JTabbedpane tabbedPane;

// constructor
public JTabbedPanel() {
this.setLayout( new BorderLayout() );
tabbedPane = new JTabbedpane();
this.add( tabbedPane); // default is Center location
options = new Options();
tabbedPane.add( "Options", options); // see javadoc
}

/////////////////////////////////
// the other way is inner classes
class OptionsTab extends Options {
}

The first choice of using vars like a horizontal structure is simple event-driven stuff.

The second choice of using inner class brings all of the public members as equal citizens of JTabbedPane. You would do this if, for example, you have two tabs [Options] [Colors].

If Options has radio buttons on its JPanel that change state based upon the color chosen in Colors, the single-dimension of everything included in JTabbedPanel class makes that interactivity more clear.

If we have to save selections done on Options tab when we close the application window, then we have a deeper discussion involving interface.

But, think in JPanels, set the Layout. Add other JPanels into the original JPanel, setLayout(). Each background JPanel is its own class.

---

### Post by kevinharper on 2012-11-18
Nice. Thanks for the replies and the suggestions.

---

