---
title: "Java JComboBox flakey in Hardy but not windows"
date: 2008-07-08
forum: Programming Talk
---

### Post by Ralph Boland on 2008-07-08
I am running Ubuntu Hardy on a dell optiplex 755.
If I create a JComboBox in Java using java-6-sun and select from the
menu the entry at the top of the JComboBox nothing happens.  I checked
with a debugger and the listener is not being called.
The same code on a windows machine (running Java-5-sun (jdk1.5.0_14) )
responds properly to the same selection.

If I switch to Java-5-sun (jdk1.5.0_14) then the selection is properly
recognized as in windows.  However the menu window for the JComboBox
stays in the same place when I move the window.
That is the menu shows up in the same place as before I moved the window.

Here is the code: (these problems happen in my real application as well).
You will see that if you select "Hello World" it will not be printed
even though it is printed in windows or java-5-sun. (.0_14). If you
select "Hi" though it will be printed.  But now if you select
"Hi" again it is not printed.  etc.


import java.awt.*;
import java.awt.event.*;
import javax.swing.JFrame;
import javax.swing.JComboBox;

public class ComboBoxBug {
	public static void main(String[] args) {
    	JComboBox buggyComboBox = new JComboBox();
        buggyComboBox.setAlignmentX(Component.LEFT_ALIGNMENT);
        buggyComboBox.addItem("Hello World");
        buggyComboBox.addItem("Hi");
        buggyComboBox.addItem("Good Bye Cruel World");
        buggyComboBox.setMaximumSize(new Dimension(120, 24));
		BugListener bugListener = new BugListener();
		buggyComboBox.addActionListener(bugListener);

		Panel panel= new Panel();
		panel.setLayout(new BorderLayout());
		panel.add(buggyComboBox);
	    JFrame frame = new JFrame();
		Container pane = frame.getContentPane();
		pane.add(panel);
		frame.setSize(200,70);
		frame.setVisible(true);
		frame.addWindowListener(new WindowAdapter(){
		    public void windowClosing(WindowEvent e){
		         System.exit(0);
		    }
		});
	}  
}


class BugListener implements ActionListener {
	public void actionPerformed(ActionEvent e) {
   		JComboBox cb = (JComboBox) e.getSource();
   		String type = (String) cb.getSelectedItem();
   		if(type.equals("Hello World")) {
			System.out.println("\nHello World\n");
   		} else if (type.equals("Good Bye Cruel World")) {
			System.out.println("\nGood Bye Cruel World\n");
   		} else if (type.equals("Hi")) {
			System.out.println("\nHi\n");
   		}
	}
}




Thanks for any help.  

Ralph Boland

[email]rpboland@gmail.com[/email]

---

### Post by tinny on 2008-07-08
This is really strange. This code works fine on my windows machine, I will try it on my Hardy box at home tonight.

(So you are saying the code you posted here doesn't run on your Ubuntu machine right?)

What does this command give you?

```

java -version

```

---

### Post by HotCupOfJava on 2008-07-08
It is worth noting that there are some portability issues with Java GUIs on different platforms. For example - a JButton that has focus will generate an ActionEvent when you hit the spacebar on some OSes, but not on others. You may be experiencing something like this. Two other suggestions I might make (that may or may not help you):

Try using "import javax.swing.*;" instead - it will grab the JFrame and the Combo box and maybe something you are missing to make this work. Second - Try using JComboBox.getSelectedIndex() instead of getSelectedItem(). It will return an integer rather than a Object. I know you are casting it to a String but who knows what it is returning? If it is ANY different from the other Strings the equals method will return false and your code will not execute. Perhaps it is returning a memory reference that is then being cast to a String? You might try outputting whatever it is returning as a String type to see if that is your problem. BUT - with the getSelectedIndex() method you can compare by what position the Strings hold in the JComboBox. The first is at 0, the second at 1, etc.....

---

### Post by tinny on 2008-07-08
> 
Try using "import javax.swing.*;" instead - it will grab the JFrame and the Combo box and maybe something you are missing to make this work.

:confused:

Are you saying that java dynamic linking is broken? Id be very surprised if this were true.

> 
Try using JComboBox.getSelectedIndex() instead of getSelectedItem(). It will return an integer rather than a Object. I know you are casting it to a String but who knows what it is returning?


Yeah good spotting, this would be a better way of doing it.

---

### Post by kavon89 on 2008-07-08
I have no problems with it. See picture here for version and test:

[http://i34.tinypic.com/2i8vk13.png](http://i34.tinypic.com/2i8vk13.png)

To compile properly I had to correct this line,, which had a random space in it:

```
buggyComboBox.setAlignmentX(Component.LEFT_ALIGNMENT);
```

I don't know if that was just a copy & paste typo or what, I'm just saying. :D

---

### Post by tinny on 2008-07-08
> **kavon89 said:**
> I have no problems with it. See picture here for version and test:

[http://i34.tinypic.com/2i8vk13.png](http://i34.tinypic.com/2i8vk13.png)

To compile properly I had to correct this line,, which had a random space in it:

```
buggyComboBox.setAlignmentX(Component.LEFT_ALIGNMENT);
```

I don't know if that was just a copy & paste typo or what, I'm just saying. :D

I see your using the Sun version of the JRE. Id be interested to know what version the OP is using.

---

### Post by HotCupOfJava on 2008-07-08
> **tinny said:**
> :confused:

Are you saying that java dynamic linking is broken? Id be very surprised if this were true.

Nah - I didn't figure that was happening, but I find I will occasionally leave a class I need out on accident. It is easier for me to use the wildcard and play it safe. But since his code is working on the other platform, that is very likely not the problem. It is more likely to be one of portability issues, which can be fixed by a little recoding.

---

### Post by tinny on 2008-07-08
> 
Nah - I didn't figure that was happening, but I find I will occasionally leave a class I need out on accident. It is easier for me to use the wildcard and play it safe.


Computers don't make mistakes!

Wildcard imports are generally considered bad form. Wildcard imports might make your job easier, but they make your code harder for another developer to interpret.

If you haven't done your imports correctly you will get a compile time error.

---

### Post by Ralph Boland on 2008-07-09
Here are my  responses to the comments on my original post:

   > **tinny said:**
> I see your using the Sun version of the JRE. 
   Id  be interested to know what version the OP is using.

I don't know what you mean by "what version the OP is using".
If I run java -version I get:

java -version
java version "1.6.0_06"
Java(TM) SE Runtime Environment (build 1.6.0_06-b02)
Java HotSpot(TM) Server VM (build 10.0-b22, mixed mode)

java5 -version
java version "1.5.0_14"
Java(TM) 2 Runtime Environment, Standard Edition (build 1.5.0_14-b03)
Java HotSpot(TM) Server VM (build 1.5.0_14-b03, mixed mode)

I added the line import javax.swing.*
which, not suprisingly, had no affect.
I also tried using getSelectedIndex
which also did not help.
This also was no suprise since,
as I noted earlier,
I verified with a debugger that the problem occurs 
because the  method "actionPerformed" does not
get invoked when I select the value at the top of the 
ComboBox.

So far no one has reported actually seeing either of 
the two problems that I see.
If someone can report seeing them then at least I would know
that neither I nor my machine are flakey.

Thanks for the help so far but I don't seem to be any closer to
a solution.


Ralph Boland

---

### Post by HotCupOfJava on 2008-07-09
One other suggestion I can make is to try using a different event handler, such as ItemListener, and place your handling code in an itemStateChanged. JComboBoxes inherit from class JComponent, which will generate ItemEvents.

---

### Post by tinny on 2008-07-09
> 
I don't know what you mean by "what version the OP is using".


What version of Java is the Original Poster (OP) using. (You have now answered this)

---

