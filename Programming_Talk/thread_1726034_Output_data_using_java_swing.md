---
title: "Output data using java swing"
date: 2011-04-10
forum: Programming Talk
---

### Post by raac on 2011-04-10
Hello guys I've got a question. I already have a panel setup so it would display data.

How can I display all the data in case it does not fit in the panel? If there is a different approach to do this please let me know.

I tried 
```


JPanel panel = new JPanel();
JScrollPane sp = new JScrollPane(panel);

for(int i = 0; i < 1000; i++){
   JLabel test = new JLabel("Something ");
   panel.add(test);
}

```

I was expecting a scroll pane aside from the panel so I would be able to see all the 1000 different "Something " strings by scrolling down, but there is no scroll pane.

What can I do?

---

### Post by r-senior on 2011-04-10
What layout manager is your panel using?

I think the default will be to lay out left to right. Do you have a horizontal scrollbar?

[http://download.oracle.com/javase/tutorial/uiswing/layout/visual.html](http://download.oracle.com/javase/tutorial/uiswing/layout/visual.html)

---

### Post by raac on 2011-04-10
I think the default is flow layout, and yes from left to right. But it does not show any of the scroll bars

---

### Post by simeon87 on 2011-04-10
A JLabel is for displaying text in graphical interfaces, it's not really intended to be used for large amounts of text. If you wish to display text you should look into a component for displaying text. Those type of controls also support scrollbars and related functionality.

---

### Post by r-senior on 2011-04-10
I fleshed out your little snippet of code:

```
import java.awt.*;
import javax.swing.*;

public class Test extends JFrame {

	public Test() {
		JPanel panel = new JPanel();
		JScrollPane sp = new JScrollPane(panel);
		for(int i = 0; i < 1000; i++){
   			JLabel test = new JLabel("Something ");
   			panel.add(test);
		}
		this.add(sp);
		this.setSize(400, 300);
		this.setVisible(true);
	}

	public static void main(String ...args) {
		Test test = new Test();
	}

}

```

And it gave me a horizontal scroll. You must be doing something else in your code somewhere. Are you setting preferredSize or something like that?

I got the second screenshot simply by setting the layout manager of the panel to GridLayout.

EDIT: And yes, I would agree, this is not the best way to deal with large amounts of text.

---

### Post by raac on 2011-04-10
Wow that'll work. THANKS

---

### Post by raac on 2011-04-10
Ok what I had done before was

```

JPanel panel = new JPanel();
panel.setPreferredSize(new Dimension(100,100));
JScrollPane sp = new JScrollPane(panel);

for(int i = 0; i < 1000; i++){
   JLabel test = new JLabel("Something ");
   panel.add(test);
}
this.add(panel);

```

Obviously it is wrong, so I changed it to

```

JPanel panel = new JPanel();
JScrollPane sp = new JScrollPane(panel);
sp.setPreferredSize(new Dimension(100,100));

for(int i = 0; i < 1000; i++){
   JLabel test = new JLabel("Something ");
   panel.add(test);
}
this.add(sp);

```

And it worked. Thanks everyone

---

