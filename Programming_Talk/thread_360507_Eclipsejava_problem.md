---
title: "Eclipse/java problem"
date: 2007-02-13
forum: Programming Talk
---

### Post by falkenberg_cph on 2007-02-13
Hi
I have a problem with this program from Cay Horstmans "Java Concepts" - Project 2.2 (page. 62).
If i execute the program as mr. Horstman has written it, without "import java.awt.Color;" - i get a compiler error.
On the other hand, if i add "Import java.awt.Color;", i dont get a compile error, but eclipse gives me an error when i run the program. I am not at home right now, but when i am, i will post the eclipse error message.

Thanks
Carsten

> 
import javax.swing.JFrame;
import javax.swing.JTextField;

// This is what i have added to the program
import java.awt.Color;

public class FrameTester
{
   public static void main(String[] args)
   {
      JFrame frame = new JFrame();
      frame.setSize(200, 200);
      JTextField text = new JTextField("Hello, World!");

      text.setBackground(Color.PINK);
      frame.add(text);
      frame.setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
      frame.setVisible(true);
   }
}


---

### Post by SquatcHman on 2007-02-13
Ran fine for me in Eclipse, other than the typo in the code you posted on line 17.

---

### Post by phossal on 2007-02-13
Any chance your project is using incorrect compiler settings? Perhaps you're still using 1.4? Even if you open ecilpse using a newer JDK, it defaults to 1.4. That causes all kinds of errors. From the toolbar:
Window -> Preferences -> Java -> Compiler

---

### Post by falkenberg_cph on 2007-02-14
Yep. that was it, i was using 1.4 - i did what you said, and it almost helped.
For others having this problem, i also had to do the following:

Window -> preferences -> java - installed JREs
found JRE 1.5.0_10 (at the moment) - unchecked JRE 1.4

windows -> preferences -> compiler -> compiler compliance level 5.0
tried 6.0 at first, but that didnt work

Thanks for your help
/Carsten

---

### Post by phossal on 2007-02-14
Yeah, in the tutorial on Java in my sig, I mention the JRE settings, too. But you figured out *and most people do*. Glad you're up and running. Cheers.

---

