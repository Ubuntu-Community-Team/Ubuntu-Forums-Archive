---
title: "[SOLVED] Running Java with FontStruct problem"
date: 2007-08-12
forum: Programming Talk
---

### Post by slamdunk12 on 2007-08-12
Hey there,

This is my first post in ubuntu forum, hooray...

Anyway back to business, when I tried to run my compiled java application in java i got these 2 error showing up:

```
Warning: Cannot convert string "-b&h-luxi sans-medium-r-normal--*-140-*-*-p-*-iso8859-1" to type FontStruct

Warning: Cannot convert string "-misc-ar pl shanheisun uni-medium-r-normal--*-*-*-*-p-*-iso10646-1" to type FontStruct
```

It didn't break my code, its just annoying to look at. I've search the forum for similar problems and so far I got nothing :mad:

Suggestion anyone?

---

### Post by nitro_n2o on 2007-08-12
This isn't a java specific problem... it seems that your application can't find the fonts you want to use in the system.... try to change the font and use something normal to see if this warning goes away.. if not i think you need to install the needed fonts and direct your application to find them

---

### Post by slamdunk12 on 2007-08-12
I didn't use any special fonts for my application nitro_n2o, thats why I am puzzled to see those error :confused:. For your reference I copy paste my very simple application that can reproduce the problem on my machine:

```
import javax.swing.*;
import java.awt.Dimension;

public class jTank extends JFrame{

	JButton bttTank = new JButton("x");

	public jTank(){
		super("Welcome to jTank");
		setSize(300, 300);
		setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
		JPanel pane = new JPanel();
		bttTank.setPreferredSize(new Dimension(100, 30));
		pane.add(bttTank);
		add(pane);
		//pack();
		setVisible(true);
	}

	public static void main(String[] Arguments){
		jTank showFrame = new jTank();
	}
}
```

Any help will be much a preciated :rolleyes:

---

### Post by slamdunk12 on 2007-08-12
By the can, can you show me where do I find those fonts and how do i install them... thank you...

---

### Post by slamdunk12 on 2007-08-12
Problem Solved!

Java has an issue with my Beryl Window Manager,  I revert back to Metacity (Gnome Windows Manager) and remove this line:

export AWT_TOOLKIT=MToolkit
at
gksudo gedit ~/.bashrc

and this line

gksudo gedit /etc/environment
at
export AWT_TOOLKIT="MToolkit"

Now my java runs with no complain what so ever!

---

### Post by Balazs_noob on 2007-08-13
yeah it runs , but you can not use beryl while you program in Java.
because you deleted the line that makes it work under beryl and compiz.
i had the same problem and i decided to ignore that error message because it didn't cause any problems.

---

### Post by slamdunk12 on 2007-08-13
Yeah I realize that, I am just beginning to learn Java so these kind of warning sign irritates me a little... :)

---

