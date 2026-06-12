---
title: "Proper Event Handling in Java"
date: 2012-11-22
forum: Programming Talk
---

### Post by kevinharper on 2012-11-22
My StartProgram class sets MainFrame class visible.

The MainFrame class contains a couple of JPanels, one for MyMenuBar object and another for MyTabbedPanel.

The MyTabbedPanel class includes a TrainingPanel object.

The TrainingPanel class extends JPanel and uses CardLayout so I can switch viewable content.

"card 1" for TrainingPanel is the SouthboundPanel object.

SouthboundPanel only has buttons. Clicking one of these should switch the "card" being displayed on TrainingPanel.

I tried to create a Training.Panel.switchCard() method but I am getting an error about making a reference to a static ... I looked up the error and I understand WHY I'm getting it.

I know that I need to set up a listener class but am really getting confused with how to do this. I haven't had much luck following online examples. I have attached all of the classes I mentioned above (w/ my last attempt to add a listener class).

---

### Post by Unterseeboot_234 on 2012-11-22
I looked at your attached files and I can't tell what's going on. Usually, a problem with 'static' means you don't have an Object. Only Objects can have [1] states [2] values [3] behaviors (methods). You can't have an Object on the heap without the keyword 'new' and a pointer (var).

A class file can be chalked text on a blackboard.

in code when java encounters 'static' the single copy is immediately configured in RAM before going on to read the rest of your program.

So, if you could draw a picture of your GUI, scan it and upload the .jpg. You could even use a pencil sketch. Swing code is bulky, so I'm willing to slam the code and then upload on pastebin.com.

The forums work best with direct Q&A. I really think some navigation through the Swing APIs is what you're asking.

---

### Post by kevinharper on 2012-11-22
:S It looks like I attached one incorrect file. TrainingListener wasn't intended to be there.

The class that I am posting here only contains buttons. When someone clicks on one of the buttons, I want TrainingPanel to change the panel currently shown (according to the button clicked).
```
import java.awt.BorderLayout;
import java.awt.Dimension;
import java.awt.FlowLayout;
import java.awt.event.ActionEvent;
import java.awt.event.ActionListener;

import javax.swing.JButton;
import javax.swing.JLabel;
import javax.swing.JPanel;

public class TrainingMainPanel extends JPanel{
	private JLabel lblTitle;
	
/***
 * START: Dynamic content
 **/
	JButton btnSouthbound;
	JButton btnNorthbound;
	JButton btnVirtualTransfers;
//END: Dynamic content
	
	public TrainingMainPanel(){
		this.setLayout(new FlowLayout(FlowLayout.CENTER, 0, 0));
		
		JPanel pnlTitle = new JPanel();
		pnlTitle.setPreferredSize(new Dimension(TabbedFrame.F_WIDTH, 30));

		JPanel pnlTrainingModules = new JPanel();
		
		lblTitle = new JLabel();
		lblTitle.setText("Training Modules");
		
/***
 * START: Dynamic content
 **/
		btnSouthbound = new JButton();
		btnSouthbound.setText("Southbound");
		btnSouthbound.setPreferredSize(new Dimension(150, 150));
		btnSouthbound.addActionListener(new ButtonClicked());
		
		btnNorthbound = new JButton();
		btnNorthbound.setText("Northbound");
		btnNorthbound.setPreferredSize(new Dimension(150, 150));
		btnNorthbound.addActionListener(new ButtonClicked());
		
		btnVirtualTransfers = new JButton();
		btnVirtualTransfers.setText("Virtual Transfers");
		btnVirtualTransfers.setPreferredSize(new Dimension(150, 150));
		btnVirtualTransfers.addActionListener(new ButtonClicked());
//END: Dynamic content
		
		pnlTitle.add(lblTitle);
/***
 * START: Dynamic content
 **/
		pnlTrainingModules.add(btnSouthbound);
		pnlTrainingModules.add(btnNorthbound);
		pnlTrainingModules.add(btnVirtualTransfers);
//END: Dynamic content
		
		this.add(pnlTitle, BorderLayout.NORTH);
		this.add(pnlTrainingModules, BorderLayout.CENTER);
	}
	
	private class ButtonClicked implements ActionListener{
		@Override
		public void addActionListener(TrainingMainListener listener){

			this.lstListeners.add(CarListener.class, listener);

		}
	}
}
```

That is where I think I need a listener and where I am getting stuck. Not sure how to link the three classes together (the one with the buttons, the listener, and the one displaying the panels).

---

### Post by slickymaster on 2012-11-23
**_In TrainingMainPanel.java:_**

```
private class ButtonClicked implements ActionListener {

        @Override
        public void addActionListener(TrainingMainListener listener) {

            this.lstListeners.add(CarListener.class, listener);

      }
    }
```

The class ButtonClicked is implementing ActionListener but is not abstract nor it is implementing the abstrac methods of the ActionListener interface.
You have two options, either you make it abstract or you implement the method actionPerformed(ActionEvent e) in it.

---

### Post by kevinharper on 2012-11-23
Okay... Will try that and repost this class in a few hours.

---

### Post by kevinharper on 2012-11-23
So I did as slickymaster suggested and I'm getting errors in other classes. Mainly because of being unable to instantiate an abstract class, which I get.

I think I am over-thinking what I want to do. Here is the gist of what I need:

User sees an options menu. I have decided to display JButtons as the options. User clicks a button and depending on which button is clicked, a new JPanel is displayed. This newly displayed JPanel has another options menu. And so on.

Am I on the right track of is there a simpler way to do this? Have I explained my objective clearly enough?

---

### Post by kevinharper on 2012-11-23
[http://www.oracle.com/technetwork/articles/javase/wizard-136789.html](http://www.oracle.com/technetwork/articles/javase/wizard-136789.html)

Seems to suggest that objects, which change the panel currently being displayed, be placed within the class that contains the CardLayout. Yes. I have done this before.

How do I manipulate the CardLayout-containing class when the controlling object is in another class? Or is this my error? Am I not supposed to separate the buttons from the CardLayout?

---

### Post by Unterseeboot_234 on 2012-11-23
For what it's worth, here is a NetBeans Project as a zipped. NetBeans because it enforces package. I don't see any package statements in your code examples. package is sanity with namespace

---

### Post by ofnuts on 2012-11-23
> **kevinharper said:**
> My StartProgram class sets MainFrame class visible.

The MainFrame class contains a couple of JPanels, one for MyMenuBar object and another for MyTabbedPanel.

The MyTabbedPanel class includes a TrainingPanel object.

The TrainingPanel class extends JPanel and uses CardLayout so I can switch viewable content.

"card 1" for TrainingPanel is the SouthboundPanel object.

SouthboundPanel only has buttons. Clicking one of these should switch the "card" being displayed on TrainingPanel.

I tried to create a Training.Panel.switchCard() method but I am getting an error about making a reference to a static ... I looked up the error and I understand WHY I'm getting it.

I know that I need to set up a listener class but am really getting confused with how to do this. I haven't had much luck following online examples. I have attached all of the classes I mentioned above (w/ my last attempt to add a listener class).

Without looking too much at your code.... you don't need a specific Listener class.... The simpler solution is to have your Training panel implement ActionListener and be the listener for the buttons, and have its actionPerformed() method switch on the "actionCommand" from the ActionEvent to select the proper panel.

Or you have a controller class above everything, that acts at the action Listener and dispatches the "orders" to the right part of the UI.

---

### Post by kevinharper on 2012-11-23
> The simpler solution is to have your Training panel implement ActionListener and be the listener for the buttons, and have its actionPerformed() method switch on the "actionCommand" from the ActionEvent to select the proper panel.

Or you have a controller class above everything, that acts at the action Listener and dispatches the "orders" to the right part of the UI.
And that's precisely where I am stuck. I have tried both ways and ridiculously broke my code.

I have a ButtonListener class.. But am not sure how to link it all together. The professor put up 4 classes the other day. One was a car, another a police officer. When the car went over 100 it alerted a listener class that prompted the officer class to give the car a ticket.

I know this is what I am looking for. But for the life of me, I haven't been able to implement it into my project.

I know I'm close. I know that I am missing something dumb. Maybe I have read the answer already but haven't recognized it.

---

### Post by kevinharper on 2012-11-23
Thank you Unterseeboot_234 for the code.

I looked through it and like how you segregated the various objects. I am not doing packages because we never really covered them in class. I read about it on the Java tutorial but didn't really get a full understanding of its importance. I'm sure it is very important. But I will have to revisit that information (and much more) once the semester is over.

---

### Post by Unterseeboot_234 on 2012-11-24
If I knew the purpose of the program we have been discussing I could tell you whether your shortest path is an interface or an extends.

All the package statement does is group names, which lends itself to Objects. e.g. instead of varnames like: primeNo_training, tabbedPane_primeNo, we can use logical varnames over and over. 

e.g. com.vcbrad.training.gui.primeNo and com.vcbrad.training.gui.constants.primeNo and the short version of both is:

import com.vcbrad.training.gui;
...
private int primeNo;

import com.vcbrad.training.constants;
static final int primeNo;

You will see professional code using the long form of varnames, not so reliant on the import statement, so that editing is considered line by line. But, take my word for it, import makes Objects easier. Shout back if you need to connect anything.

---

### Post by kevinharper on 2012-11-24
It is supposed to be a training tool where an instructor can create new lesson plans and students can view these lesson plans.

All that I have posted so far is from the student side. He/She sees a window with the various lessons. Each lesson title is contained within a JButton. The student clicks the lesson he/she would like to start and the student is directed to a page that has an outline of the lesson. This outline is a column of JButtons, each with a section title contained within. When the student clicks a button he/she is directed to a page with the corresponding content/lesson.

There is a "Back to main page" button at the bottom of each screen. When clicked, the user should see the various lessons. I have all of these layouts completed. I also have a separate JPanel class with CardLayout. I am having an issue changing the shown content in the CardLayout, depending on which buttons are clicked on the other screens.

---

### Post by Unterseeboot_234 on 2012-11-24
Thanks, I can scaffold something for you. As an aside, the program really should be a database with persistence. And SE includes Apache Derby. I think we all want to see interface in action.

I must tell you to learn programming BEFORE you get married. I will show you how to write the central Controller.java, MainProgram creates an instance and interface on any class will interact to the methods() of Controller.

Check back later and I would have amended this thread. BTW, 3.5 years wasted in Tempe thinking Motorola would give me a chance. Lived right next door to ASU.

---

### Post by kevinharper on 2012-11-24
Content will be generated using a database.

I have it all mapped out. I am comfortable using DBs but will have to figure out later how it is all put together in Java.

I wanted to start with the shells that would house the dynamic content.

I'm in Tucson, about 2hr drive from ASU.

Thank you for your time.

---

### Post by Unterseeboot_234 on 2012-11-24
First, you want:

[FONT="Courier New"]public interface IEvent {}[/FONT]

in a file all by itself.

Then, you have class files which implement that. Here is an example. All class names here begin with EventBlahBlah:

[FONT="Courier New"]public class EventChangeClassData implements IEvent {

private ClassData data;

// const
public EventChangeClassData( ClassData data ) {
this.data = data;
}
// getter / setters
public ClassData getData() {
return data;
}
public void setData( ClassData c ) {
data = c;
}
}
[/FONT]

Now, for the über_events class:

[FONT="Courier New"]public class EventDispatcher {

private MainFrame mainFrame;

// const
public EventDispatcher( MainFrame mainFrame ) {
this.mainFrame = mainFrame;
}

// where the rubber meets the road...
public void dispatchEvent( IEvent incomingEvent ) {

// could use a try{ the following code's logic-tree
// } catch(Throwable t){ new ErrorDialog()}

if( incomingEvent instanceof ChangeClassData ) {
ChangeClassData event = (ChangeClassData)incomingEvent;
String classD = event.getClassData();
}

else if( incomingEvent instanceof [/FONT]

MainFrame would have as a member:

[FONT="Courier New"]public EventDispatcher eventDispatcher = new EventDispatcher( this );[/FONT]

in MainFrame should you wish to attach your extended WindowAdapter for windowClosing, the call looks like:

[FONT="Courier New"]eventDispatcher.dispatchEvent( new EventShutdownMainFrame() );
shootOffRockets();
formatDriveC();
}[/FONT]

And, in the JPanels, because the constructor had...
public WidgetPanel( MainFrame mainFrame ) {
...

the call might look like this:
[FONT="Courier New"]public String getTabPaneText() {
String selectedTabText = mainFrame.eventDispatcher.dispatchEvent( new EventGetTabPaneText( this ) );
return selectedTabText;[/FONT]

===================
I hope this helps and is of use for you. Perhaps you can see it is incremental and expandable.

========================

One place could be in JButton. No need to extend JButton unless they have special properties such as size or color.

JButton button = new JButton();
button.addActionListener(new ActionListener() {

 
    public void actionPerformed(ActionEvent arg0) {
        
        mainFrame.eventDispatcher.dispatchEvent( new EventImadeAclassFor() );
    }
    
});

---

### Post by kevinharper on 2012-11-24
It did help, thank you.

Using your sample code and that I got from a custom event handler example the professor provided us w/, I have come to the conclusion that the logic I'm using is all-sorts-of-jacked-up.

Going to redo the navigation flow logic. I think I have to create a custom class that extends JButton so I can add these event handlers to it. It is what would interact with the interface. I've spent the last 4 hours trying to cram these solutions into what I have and, sadly, haven't gotten anywhere. I do have a much better idea of what I need to do. I will see if it can be more easily implemented once I revisit the program logic.

Again, thank you for all of your time. All responses have been very helpful.

---

### Post by kevinharper on 2012-11-24
Seriously, I have never had this great of an urge to transform my laptop into a Frisbee. And all because I know the answer is right in front of me. I'll change the status to solved because I really understand where you are going and what I need to do.

---

