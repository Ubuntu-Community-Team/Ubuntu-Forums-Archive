---
title: "Java JLabel not being found"
date: 2009-05-02
forum: Programming Talk
---

### Post by mikemcleanuk on 2009-05-02
Hey im doing some basic tutorials and ive come across a problem part of my code seems to be shielded from being able to see my lable but i dont know why. It looks like the code inside an if statement make it unable to see the lable but that doesnt make any sense to me.

If you guys could take a look and point out my mistake im sure it will be a rookie error as allways :P

If someone could try explain the problem in simplistic terms so i can try avoid it in the future that would be great also.

The aim of the program is to simply have 2 buttons that will grow and shrink a square box by 10 in each dimention, with the limitation of not going smaller than 10 by 10 or bigger than the window.

```

import java.awt.*;
import javax.swing.*;
import java.awt.event.*;
import java.awt.Color;

class GrowBox extends JPanel implements ActionListener
{
	private JButton growButton;
	private JButton shrinkButton;
	JLabel box1;

	GrowBox()
	{
		Dimension mLSize = new Dimension(20,20);

		growButton = new JButton("Grow");
		shrinkButton  = new JButton("Shrink");

		this.add(growButton);
		this.add(shrinkButton);

		growButton.addActionListener(this);
		shrinkButton.addActionListener(this);

		box1 = new JLabel();
		box1.setOpaque(true);
		box1.setBackground(Color.green);
		box1.setPreferredSize(mLSize);
		this.add(box1);
    }
	
	public void actionPerformed(ActionEvent e)
	{
		if(e.getSource() == growButton)
		{
		int tmpH = box1.getHeight() + 10;
		int tmpW = box1.getWidth() + 10; 
		int frameH = getHeight();
		int frameW = getWidth();

		if(!(tmpH >= frameH || tmpW >= frameW))
		{
			box1.setPreferedSize(tmpH, tmpW);
		}
		}
		if(e.getSource() == shrinkButton)
		{
		int tmpH = box1.getHeight() - 10;
		int tmpW = box1.getWidth() - 10; 
		if(!(tmpH == 0 || tmpW == 0))
		{
			box1.setPreferedSize(tmpH, tmpW);
		}
		}
	}
}

```

All help even regarding cleaning up working areas of my code is apprechiated.

```
C:\JPR\Lab17>javac TestGrowBox.java
.\GrowBox.java:43: cannot find symbol
symbol  : method setPreferedSize(int,int)
location: class javax.swing.JLabel
                        box1.setPreferedSize(tmpH, tmpW);
                            ^
.\GrowBox.java:52: cannot find symbol
symbol  : method setPreferedSize(int,int)
location: class javax.swing.JLabel
                        box1.setPreferedSize(tmpH, tmpW);
                            ^
2 errors
```

Mike

---

### Post by jespdj on 2009-05-02
The method "setPreferedSize" that you typed isn't found, and that's because you made a typo.

The method is called setPrefe**rr**edSize with rr instead of setPreferedSize.

---

### Post by mikemcleanuk on 2009-05-02
thanks for pointing that out as true as it was however it has not fixed the problem

any more ideas?

---

### Post by MeLight on 2009-05-02
Change setPreferredSize to setSize. And get yourself a descent IDE with auto-complete, will save you tons of headache ;)
[Download NetBeans IDE]("http://www.netbeans.org/downloads/index.html")

---

### Post by mikemcleanuk on 2009-05-02
> **MeLight said:**
> Change setPreferredSize to setSize. And get yourself a descent IDE with auto-complete, will save you tons of headache ;)
[Download NetBeans IDE]("http://www.netbeans.org/downloads/index.html")

i use notepad++ and it doesnt autocomplete i dont know where i got setprefferedsize from probably some tutorial website i guess.

thanks that fixed it

---

