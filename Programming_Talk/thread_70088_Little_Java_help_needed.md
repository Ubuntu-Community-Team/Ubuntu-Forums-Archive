---
title: "Little Java help needed"
date: 2005-09-28
forum: Programming Talk
---

### Post by NeoChaosX on 2005-09-28
Okay, doing some Java programming right now. I'm trying something new and defining my own ActionListener class, GreetingButtonListener. Here's how it looks right now:

```
import java.awt.*;
import java.awt.event.*;
import javax.swing.*;

public class GreetingButtonListener implements ActionListener
{
    /**
      Creates a new GreetingButtonListener
      @param message the Message that the listener will display
   */
   public GreetingButtonListener(String message)
   {
      buttonMessage = message;
   }

   /**
      The action that happens when the Listener is called
      @param event the event calling on the class
   */
   public void actionPerformed(ActionEvent event)
   {

   }
   private String buttonMessage;
}
```

Here's the program I'm using to test it: 

```
import java.awt.*;
import java.awt.event.*;
import javax.swing.*;

public class SampleProgram
{
   public static void main(String args[])
   {
      JFrame frame = new JFrame();

      final int FIELD_WIDTH = 20;
      final JTextField textField = new JTextField(FIELD_WIDTH);
      textField.setText("Click a button!");

      JButton helloButton = new JButton("Say Hello!");
      JButton goodbyeButton = new JButton("Say Goodbye!");

      helloButton.addActionListener(new GreetingButtonListener("Hello world!"));
      goodbyeButton.addActionListener(new GreetingButtonListener("Goodbye world!"));

      frame.setLayout(new FlowLayout());

      frame.add(helloButton);
      frame.add(goodbyeButton);
      frame.add(textField);

      frame.setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
      frame.pack();
      frame.setVisible(true);
   }
}
```

What I want the new Listener class to do is when the buttons in the program are pushed, it should change the JTextField in the original program to whatever it's set to. However, I'm stumped on how to access, much less modify the TextField from the listener. Does anybody have any suggestion on how to implement actionPerformed that allows me to do this?

---

### Post by blastus on 2005-09-28
You need access to the textField variable in the listener. There are lots of ways to do this, here's one way... 

```
import java.awt.*;
import java.awt.event.*;
import javax.swing.*;

public class SampleProgram extends JFrame implements ActionListener {

    final int FIELD_WIDTH = 20;
    final JTextField textField = new JTextField(FIELD_WIDTH);

    JButton helloButton = new JButton("Say Hello!");
    JButton goodbyeButton = new JButton("Say Goodbye!");

    public SampleProgram() {

        textField.setText("Click a button!");

        helloButton.addActionListener(this);
        goodbyeButton.addActionListener(this);

        setLayout(new FlowLayout());
        add(helloButton);
        add(goodbyeButton);
        add(textField);
        setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
        pack();
        setVisible(true);
    }

    public void actionPerformed(ActionEvent evt) {
        if (evt.getSource().equals(helloButton)) {
            textField.setText("Say Hello!");
        } 
        else if (evt.getSource().equals(goodbyeButton)) {
            textField.setText("Say Goodbye!");
        }
    }

    public static void main(String args[]) {
        new SampleProgram();
    }

}
```

Edit: Why doesn't the code tag on these forums retain spaces?

---

### Post by LordHunter317 on 2005-09-28
Blastus' solution is the eaisest way.  If you have more components that need different actions listeners, then use anonymous classes or inner classes (in your case, a inner class would be best).

---

### Post by NeoChaosX on 2005-09-28
To be honest, this problem was on a midterm for one of my classes, and since I got it back, I'm been looking over on how to do it. The problem required that I write it the way it is, with the ActionListener as a seperate class. I'd really like to know if there is a way to access the JTextField from a subclass like that, or if professor was giving us an impossible problem.

---

### Post by fakie_flip on 2005-09-28
You do not have to create a FlowLayout object. That is done by default if none other is chosen.

---

### Post by fakie_flip on 2005-09-28
A String object does not change. Find some example code that does the same thing you want.

---

### Post by LordHunter317 on 2005-09-28
[QUOTE=NeoChaosX]I'd really like to know if there is a way to access the JTextField from a subclass like that,[/quote]Unless I missed something, how is it a subclass?  It's a totally seperate class.  In which case, the quickest solution would be to pass a reference to the TextField in the listener's constructor.  Obviously, this defeats the whole purpose of decoupling the listener in the first place.  Not that there's much to gain by doing that, but that's what one would have to do.

The other solution is to get the parent component from the event, but this will force you to cast and leave back where you started.

Were you not allowed to use inner classes?

**fakie_flip:**
How is anything you posted vaugely relevant?

---

### Post by NeoChaosX on 2005-09-29
[QUOTE=LordHunter317]Were you not allowed to use inner classes?[/QUOTE]

Yeah, the instructions explictly said not to use inner classes. I wonder if there is a way to do it without them. There has to be, but looking over what I've learned so far hasn't made this clear to me.

---

### Post by roccos111 on 2005-09-29
Hi,

The best way to do this would be to implement the listener as an INNER class. I have bolded the important parts. This should compile but i wont make promises, i havn't compiled it.


import java.awt.event.ActionEvent;
import java.awt.event.ActionListener;

public class SampleProgram extends javax.swing.JFrame {
	
    private javax.swing.JButton jbButton;
    private javax.swing.JTextField tfTextField;

    **private ActionListener buttonListener = new CustomListener();**

    public SampleProgram() {
        java.awt.GridBagConstraints gridBagConstraints;

        jbButton = new javax.swing.JButton();
        tfTextField = new javax.swing.JTextField();

        **jbButton.addActionListener(customListener);**

        getContentPane().setLayout(new java.awt.GridBagLayout());

        gridBagConstraints = new java.awt.GridBagConstraints();
        gridBagConstraints.gridx = 1;
        gridBagConstraints.gridy = 0;
        gridBagConstraints.insets = new java.awt.Insets(4, 4, 4, 4);
        getContentPane().add(jbButton, gridBagConstraints);

        gridBagConstraints = new java.awt.GridBagConstraints();
        gridBagConstraints.gridx = 0;
        gridBagConstraints.gridy = 0;
        gridBagConstraints.fill = java.awt.GridBagConstraints.BOTH;
        gridBagConstraints.weightx = 1.0;
        gridBagConstraints.insets = new java.awt.Insets(4, 4, 4, 4);
        getContentPane().add(tfTextField, gridBagConstraints);

        pack();
    }
	
	
	public static void main(String args[]) {
		java.awt.EventQueue.invokeLater(new Runnable() {
			public void run() {
				new SampleProgram().setVisible(true);
			}
		});
	}
	
    [B]private class CustonListener implements ActionListener {
        public void actionPerformed(ActionEvent e) {
            tfTextField.setText("");
        }
    }  [/B]
	
}

---

### Post by roccos111 on 2005-09-29
Sorry, i missed your last comment about not being able to use inner classes.

In that case, you write a response like 'You ask a question like this when you are teaching software engineering? Seems like you need to LEARN software engineering.' but that probably wouldn't go down to well.

It is possible by using a separate class, and then passing that class a reference to the JTextField for example, but that is stupid. There are times when external listeners are handy, this is certainly not on of them.

---

### Post by LordHunter317 on 2005-09-29
[QUOTE=NeoChaosX]Yeah, the instructions explictly said not to use inner classes. I wonder if there is a way to do it without them. There has to be, but looking over what I've learned so far hasn't made this clear to me.[/QUOTE]The eaisest way would be to modify your class like so:```
public class GreetingButtonListener implements ActionListener
{
     private JTextField fieldToEdit;
    /**
      Creates a new GreetingButtonListener
      @param message the Message that the listener will display
   */
   public GreetingButtonListener(String message, JTextField field)
   {
      buttonMessage = message;
      fieldToEdit = field;
   }
```Or similiar.

---

### Post by blastus on 2005-09-29
I think it's a matter of preference as everyone has different coding styles. I (as my example shows) prefer NOT to use inner classes though it reallys depends on the situation. I generally steer away from inner classes or creating separate listener classes because it requires the instantiation of another object in your program. But if you implement whatever listener interface you need where your need it, you don't add the overhead of another class file.

But again, it reallys depends on the situation. Sometimes it is more useful or practical to use an inner class, or an adapter, or an external listener class. In this example, having a separate listener class was the requirement...even though its not the *best* way to do it.

---

### Post by LordHunter317 on 2005-09-29
[QUOTE=blastus]I think it's a matter of preference as everyone has different coding styles.[/quote]No, there's clear maintance and encaspulation differences here.  Sometimes fundamental, sometimes not.

> I (as my example shows) prefer NOT to use inner classes though it reallys depends on the situation.The problem is, you end up with spaghetti code if you have multiple objects needing different actions.  

Basically, if your action listener has to do dispatch, there's a problem.  A major entire point of OOP is to avoid those sorts of situations.

There's three solutions:[list=1][*](Anonymous) Inner Classes[*]Extending each Widget[*]Creating seperate listener classes[/list]The second one isn't a viable solution over the first for a project of any size, as it's more LOC and complication for zero gain.

The third is a valid solution IFF you have multiple objects that respond the same way to an action.  In fact, Swing has an class design to do this: Action.  Extending action for common actions is quite useful.   However for one-offs, it's just added overhead again, and the (anonymous) inner class wins out in simple less LOC, less tedious naming, and smaller exposed namespace.

>  I generally steer away from inner classes or creating separate listener classes because it requires the instantiation of another object in your program.And for the former case, how's it a big deal?  Instaniation occurs with definition: RAII, which is ideal.

> But if you implement whatever listener interface you need where your need it, you don't add the overhead of another class file.And the trade off is spahgetti code whenever you have more than one widget.

---

### Post by blastus on 2005-09-29
> No, there's clear maintance and encaspulation differences here.  Sometimes fundamental, sometimes not. The problem is, you end up with spaghetti code if you have multiple objects needing different actions. Basically, if your action listener has to do dispatch, there's a problem.  A major entire point of OOP is to avoid those sorts of situations.

It's called event demultiplexing. If you want to call it "spaghetti code" then that's your opinion. The entire AWT/Swing framework is based on the delegate event model. There is going to be dispatching involved one way or another. If you are insistent on avoiding any kind of dispatch in your listener implementation then you must instantiate a separate listener for each event source. I suppose you would call calling a method in an event a dispatch also--because technically that may also be considered a "dispatch."

> And for the former case, how's it a big deal?  Instaniation occurs with definition: RAII, which is ideal. And the trade off is spahgetti code whenever you have more than one widget.

It's not. I simply prefer to avoid inner classes for listeners where possible to avoid the overhead of the instantiation of another object. I also tend to avoid inner classes in general, because IMO, if you use a lot of them they can make your code *harder* to read. If you have a large project with hundreds or thousands and source files, I can't help but think that the elimination of a couple hundred class files *may* make a difference. But there are certainly situations where inner classes are very useful and can make your code *easier* to read.

I'm not arguing, but like I said, it really has a lot to do with the way your system is designed and personal preference. There's always going to be some tradeoffs here so there are no hard core rules, just guidelines and design patterns. There's not always a clearcut *best* way to do things in every situation.

---

### Post by LordHunter317 on 2005-09-29
> **blastus]It's called event demultiplexing. If you want to call it "spaghetti code" then that's your opinion.[/quote]It is.  Having an actionListener with code like:```
public void actionPerformed(ActionEvent event) {
    if (event.getSource().equals(Object1) {
       actionPerformedOnObject1() said:**
> The entire AWT/Swing framework is based on the delegate event model. There is going to be dispatching involved one way or another.Yes, so why not let **someone else** handle it?  Especially since Swing goes out of it's way to handle it for you anyway.

>  If you are insistent on avoiding any kind of dispatch in your listener implementation then you must instantiate a separate listener for each event source.And as I said, **what's the problem with that**?  It's RAII, and it's a good thing.  

> It's not. I simply prefer to avoid inner classes for listeners where possible to avoid the overhead of the instantiation of another object.The overhead of initalizing a class that has no private data and descends from one Interface is absolutely minimal.

Certainly it's not high enough to justify messy, error-prone conditional code in any case.

 > If you have a large project with hundreds or thousands and source files, I can't help but think that the elimination of a couple hundred class files *may* make a difference.Inner classes don't add source files, so this is a non-sequitur.

> But there are certainly situations where inner classes are very useful and can make your code *easier* to read.Eventing being the most common and useful example in Java.

[quoyr]There's always going to be some tradeoffs here[/quote]Perhaps, but you've failed to demonstrate any real positive tradoffs with embedding the listener in the parent class, for any case where there are unique response to an event type.  And, you've demonstrated marked negatives.

> not always a clearcut *best* way to do things in every situation.In this case, it's pretty clear that inner classing of some sort is generally a better solution, exception the Action case I originally noted.

---

### Post by blastus on 2005-09-29
> Inner classes don't add source files, so this is a non-sequitur.

I said "If you have a large project with hundreds or thousands and source files, I can't help but think that the elimination of a couple hundred **class files** *may* make a difference."

Anyway, I do agree with you that demultiplexing code should probably be kept to a minimum. But like I said a lot of this has to do with what you want to do. However, the only other solution you propose is to create and instantiate TWO inner classes, not only adding more code, but also adding TWO more .class files to the project. Even if you do it that way, you could mix up the listeners just as easy as you can mix up the event sources.

Like I said a lot of this is a matter of opinion. I am open to learning new things and there's definitely always going to be better ways to do things. But the example you quote about demultiplexing an event that only has two possible event sources being "spaghetti code" is an **extreme** position. If you need a prime example of event multiplexing and demultiplexing take a look at the JMF.

---

### Post by LordHunter317 on 2005-09-29
[QUOTE=blastus]I said "If you have a large project with hundreds or thousands and source files, I can't help but think that the elimination of a couple hundred **class files** *may* make a difference."[/quote]Sorry, I thought you meant source files.  However, class files  (like most binary code) is a minor inconvience at best.  Unless you had a package with literally tens of thousands, they're not an issue.

Number of source files is far more important as an CM issue.

> However, the only other solution you propose is to create and instantiate TWO inner classes, not only adding more code, Only because the declaration for anonyomous inner classes is retarded.  But it's certainly better encapsulation, even if it comes at cost of syntax.

More importantly, there are cases where it **must** done (e.g., any case where you want to use an Adapter) because of the weakness in Java's multiple inheritence.  Your only solutions at that point are to create a second class, be it an external helper or an inner class.  And encapsulation says it shouldn't be external unless something else needs to use it.

So in Java, the case for using distinct classes for events is even stronger, because at some point, you likely will have to.

> But the example you quote about demultiplexing an event that only has two possible event sources being "spaghetti code" is an **extreme** position.Perhaps for two cases.  But what about 3?  Or 4?  or 20?  It's also prone to fall-through logic errors (i.e., else covering cases it shouldn't).  

Using distinct classes isn't prone to that.

---

### Post by blastus on 2005-09-30
> Only because the declaration for anonyomous inner classes is retarded. But it's certainly better encapsulation, even if it comes at cost of syntax...Perhaps for two cases. But what about 3? Or 4? or 20? It's also prone to fall-through logic errors (i.e., else covering cases it shouldn't).

The advantage of demultiplexing in this case is that event handling is less verbose and it is **centralized**. Since it is centralized, it is easier to read and if it is easier to read, it is easier to maintain. If you have 20 buttons and one listener then your event handling is centralized in one place. 

However, if you have 20 buttons and 20 listeners then your event handling is NOT centralized and you require the instantiation of 20 objects and 20 .class files on your hard drive. Now if the syntax of specifying 20 inner classes was simpler and it did NOT require the instantiation of 20 objects and require 20 .class files, then it would be more appealing to me. Each one of those 20 .class files has to be read from the hard drive you know.

> More importantly, there are cases where it must done (e.g., any case where you want to use an Adapter) because of the weakness in Java's multiple inheritence. Your only solutions at that point are to create a second class, be it an external helper or an inner class. And encapsulation says it shouldn't be external unless something else needs to use it.

I sometimes use adaptors for listeners but usually only where the listener has tons of methods that I do not need to implement. Of course, in that case, an inner class is simpler and works best. Listeners should not be in separate classes unless they are shared.

You should take a look at the JMF. There's lots of event multiplexing and demultiplexing going on there and yet it is a well-designed framework.

---

### Post by LordHunter317 on 2005-09-30
[QUOTE=blastus]Since it is centralized, it is easier to read and if it is easier to read, it is easier to maintain.[/quote]It's not clear that centralized code is actually eaiser to read in this case, because the centralized code is a far more complicated conditional block, while the class solution has **no conditionals whatsoever**.

Given the choice between picking out the inner classes (which somethign like Eclipse can pin-point for me, plus they have distinctive syntax) or writing a huge if/else block, I know which one I'm picking if I have more than one distinct response to an event.

>  Now if the syntax of specifying 20 inner classes was simpler and it did NOT require the instantiation of 20 objects and require 20 .class files, then it would be more appealing to me.Of those, only the first is valid.  You've yet to demonstrated that the instantiation overhead is a problem (because it isn't, there's really nothing to initalize), and that having the extra files is a legtimitate problem.  Mainly because neither are.  

>  Each one of those 20 .class files has to be read from the hard drive you know.And?  Your conditional code does too, and it's not like the overhead of .class file is substantial.  Not a valid reason to do it.

> I sometimes use adaptors for listeners but usually only where the listener has tons of methods that I do not need to implement.Which is quite the common case in Java, all over the place.  JFC has several examples (WindowAdapter being probably the most common).  SAX being another awesome one.

---

