---
title: "Backend code for GUI created in NetBeans"
date: 2007-02-03
forum: Programming Talk
---

### Post by phossal on 2007-02-03
I recently installed NetBeans, and I've only been able to spend a few minutes checking it out. I've been able to duplicate the very simple form GUI per its tutorial, and I've managed to run it as a .jar file externally. However, without having done my research, how do you tie the GUI to the rest of the code base? Once I've created a form, for example, how do I connect it to the code that manages a database, or anything else?

---

### Post by Tomosaur on 2007-02-03
Do you mean 'connect' in the sense you allow the various parts of the program to talk to each other, or 'connect' in the sense that you just want your program to launch the GUI in the first place?

If the former, your GUI is going to need some event listeners and such. If the latter, you just create an instance of your gui and, provided the constructor of your GUI code sets up and displays it, you should be all done:

```

public class myProgram{
  public static void main(String argv[]){
    gui myGui = new gui();
  }
}

```
Something like that^ should do it.

---

### Post by phossal on 2007-02-03
I do mean *connect* in terms of responding to events. I know I need some action and event listeners, but it isn't immediately obvious to me how I *add* them. I'm not very familiar with NetBeans. I have nearly every book on Java produced by O'Reilly, but I don't have the outdated "NetBeans". I want to learn more about it, and I may start by returning to an old love, Learning Java, to read the chapter on Java Beans. I'm sure after I do that I'll figure out what I need and be able to ask better questions.

C'est la vie. It seems like when I need the most help, I'm totally without a way to *ask* for it. I appreciate the response, too, Tomosaur. Thank you.

---

### Post by samjh on 2007-02-07
Go to Design view of a particular form.  Click on any of the controls (eg. button, textfield, etc.), then right-click on it, and you will find a menu item for adding events and action handlers.  Choose them, and you will be directed to the part of the auto-generated code where you can insert your own code.

---

### Post by Tomosaur on 2007-02-07
Adding actionevents and such isn't too complicated. Here's how you add an ActionEvent to a button, for example:
```

import java.awt.event.*; //You'll need to import this for GUI events.

//To add an event listener to a button, use this syntax
my_button.addActionListener(
  new ActionListener(){
    public void actionPerformed(ActionEvent e){
      System.out.println("Hello world!");
    }
  }
);

```
That's the basic approach, and it looks a little ugly. You may want to implement your own ActionListener (since ActionListener itself is an interface), so you can cut down on the lines of code for each different event, but at the same time, this may mean you'll end up with lots of different class files. I find it's easier to just implement the ActionListener as and when I'm adding one to a button, but it's your choice :)

---

