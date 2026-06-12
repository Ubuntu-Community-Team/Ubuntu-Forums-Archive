---
title: "Java window resizing problems (but not in windows)"
date: 2008-07-08
forum: Programming Talk
---

### Post by Ralph Boland on 2008-07-08
I am running Ubuntu Hardy on a Dell optiplex 755.
The attached Java code (32 lines) when run creates a window the contents of which should resize to fill the window if you change the window's size.
It actually works in Java-6-sun but not Java-5-sun (jdk1.5.0_14).
It also works on windows with jkd1.5.0_14).

Can anyone explain what the problem is and what to do about it?
Unfortunately, I cannot upgrade to Java-6 at this time.

Does anybody know if this problem occurs in a recent version of Redhat?
Some of our customers will run Redhat; others Windows.


Thanks

Ralph Boland

[email]rpboland@gmail.com[/email]

---

### Post by tinny on 2008-07-08
Did you forget to attach the code??? Or am I blind? :)

---

### Post by Ralph Boland on 2008-07-09
Here is the attached code again.
I don't why it didn't attach the first time.  
Perhaps I didn't click  "upload".  (I am used to firefox which has no upload button.)
Just to be sure is a a pasted version of the code.

import java.awt.*;
import java.awt.event.*;
import javax.swing.JFrame;

public class Border {

	public static void main(String[] args) {
	    JFrame frame = new JFrame();
		Container pane = frame.getContentPane();
		Panel pa= new Panel();
	    Button ba1= new Button();
		Button ba2=new Button();
		Button ba3=new Button();
		Button ba4=new Button();
		Button ba5=new Button();
		pane.add(pa);
		pa.setLayout(new BorderLayout());
		pa.add(new Button("Wel"), BorderLayout.NORTH);
		pa.add(new Button("Come"), BorderLayout.SOUTH);
		pa.add(new Button("Rose"), BorderLayout.EAST);
		pa.add(new Button("India"), BorderLayout.WEST);
		pa.add(new Button("RoseIndia"), BorderLayout.CENTER);
		frame.setSize(300,300);
		// frame.setPreferredSize(new Dimension(300,300));
		frame.setVisible(true);
		frame.addWindowListener(new WindowAdapter(){
		    public void windowClosing(WindowEvent e){
		         System.exit(0);
		    }
		});
	}  
}



Sorry for all the confusion.

Ralph Boland

---

### Post by HotCupOfJava on 2008-07-09
You may have to tell it to recalculate the layout of the content pane. You will have to instantiate the BorderLayout to do it. Example: private BorderLayout layout; layout = new BorderLayout(<arguments>); then when you resize - layout.layoutContainer(getContentPane());

hope that helps

---

### Post by Ruhe on 2008-07-09
Of course, you can agree or disagree with me,
but after hours of writing such gui initialization code I decided, that [**matisse**]("http://www.netbeans.org/kb/articles/matisse.html") is the best solution. Code isn't clean but you can visually build your gui, without compiling and running again and again and checking that everything is ok.

---

### Post by tinny on 2008-07-09
> 
Of course, you can agree or disagree with me,
but after hours of writing such gui initialization code I decided, that matisse is the best solution. Code isn't clean but you can visually build your gui, without compiling and running again and again and checking that everything is ok.


:evil:  Hahaha

> 
You may have to tell it to recalculate the layout of the content pane. You will have to instantiate the BorderLayout to do it. Example: private BorderLayout layout; layout = new BorderLayout(<arguments>); then when you resize - layout.layoutContainer(getContentPane());

hope that helps 


In these sort of re-layout circumstances you really only want to call the "validate" method (There is alot of stuff that Swing is doing under the hood that you don't want to muscle in on).

Try the code I have posted below. This is a hack and far from ideal, but if it works...

```

public class Border {

    public static void main(String[] args) {
        final JFrame frame = new JFrame();
        Container pane = frame.getContentPane();
        Panel pa = new Panel();
        Button ba1 = new Button();
        Button ba2 = new Button();
        Button ba3 = new Button();
        Button ba4 = new Button();
        Button ba5 = new Button();
        pane.add(pa);
        pa.setLayout(new BorderLayout());
        pa.add(new Button("Wel"), BorderLayout.NORTH);
        pa.add(new Button("Come"), BorderLayout.SOUTH);
        pa.add(new Button("Rose"), BorderLayout.EAST);
        pa.add(new Button("India"), BorderLayout.WEST);
        pa.add(new Button("RoseIndia"), BorderLayout.CENTER);
        frame.setSize(300, 300);
        frame.setVisible(true);
        frame.addComponentListener(new ComponentListener() {

            public void componentResized(ComponentEvent e) {
                System.out.println("Component resized");
                frame.validate();
            }

            public void componentMoved(ComponentEvent e) {
                
            }

            public void componentShown(ComponentEvent e) {
                
            }

            public void componentHidden(ComponentEvent e) {
                
            }
        });
        
        
        frame.addWindowListener(new WindowAdapter() {

            public void windowClosing(WindowEvent e) {
                System.exit(0);
            }
        });
    }
}

```

> 
Does anybody know if this problem occurs in a recent version of Redhat?


Why dont you install Red hat (or Fedora) in a VM?

---

### Post by Phristen on 2008-07-10
I couldn't replicate the problem, but just to add to tinny's comment, it is better to use ComponentAdapter helper class rather than ComponentListener, unless you really need all those empty methods in your code...

But really, the layout manager should take care of everything automatically, that's its purpose.

Also, JFrame has a shortcut to that window adapter you use to exit the app.
Just call frame.setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);

---

### Post by tinny on 2008-07-11
> **Phristen said:**
> I couldn't replicate the problem, but just to add to tinny's comment, it is better to use ComponentAdapter helper class rather than ComponentListener, unless you really need all those empty methods in your code...

But really, the layout manager should take care of everything automatically, that's its purpose.

Also, JFrame has a shortcut to that window adapter you use to exit the app.
Just call frame.setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);

Im pretty sure the OP isnt looking for "real" code, just pointers on how to find a solution.

> 
 Java window resizing problems (but not in windows)


Note: The whole application the in a main method, there are several unused JButton's and my code doesnt have any class imports.

---

