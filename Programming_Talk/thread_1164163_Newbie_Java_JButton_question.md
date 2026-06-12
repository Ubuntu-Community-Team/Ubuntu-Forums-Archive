---
title: "Newbie Java JButton question"
date: 2009-05-19
forum: Programming Talk
---

### Post by PaulTR on 2009-05-19
I'm working my way through a Java programming book, and have just started where they're introducing graphics with the JFrame. I can get the frame to appear and title it, but when I try to add buttons they're not showing up. Here's an example of the code I'm using to display the buttons, copied right out of the book. Is there something specific about Ubuntu that I'm missing as to why they wouldn't be displayed? I'm using Hardy and Java 5


> 
import javax.swing.*;
import java.awt.*;

public class Playback extends JFrame
{
	public Playback()
	{
		super("Playback");
		setSize(225, 80);
		setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
		setVisible(true);
		FlowLayout flo = new FlowLayout();
		setLayout(flo);
		JButton play = new JButton("Play");
		JButton stop = new JButton("Stop");
		JButton pause = new JButton("Pause");
		add(play);
		add(stop);
		add(pause);
		setVisible(true);
	}

	public static void main(String[] arguments)
	{
		Playback pb = new Playback();
	}
}




Sorry that there's no tabs, I just used the quote tags to add it in there and it didn't keep it in the same format as I have it in my editor.

---

### Post by baizon on 2009-05-19
You need a JPanel, and then put the JButtons on the JPanel.

---

### Post by cl333r on 2009-05-19
Java 5 was released several years ago when composite managers on Linux were not taken into account. Disable compiz and try again, worked for me.

Also you might wanna add components transparently, to a JPanel and make the JPanel the content pane of the JFrame.

```

import javax.swing.*;
import java.awt.*;

class Playback extends JFrame {

	public Playback() {
		super("Playback");
		setSize(225, 80);
		setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);

		JPanel contentPane = new JPanel(new FlowLayout());
		setContentPane(contentPane);

		JButton play = new JButton("Play");
		JButton stop = new JButton("Stop");
		JButton pause = new JButton("Pause");
		
		contentPane.add(play);
		contentPane.add(stop);
		contentPane.add(pause);
		
		setVisible(true);
	}

	public static void main(String[] arguments) {
		Playback pb = new Playback();
	}
}

```

---

### Post by PaulTR on 2009-05-19
Awesome, thanks for the help. I'll give that a shot real quick. How do I disable Compiz, other than killall compiz in the terminal?

Edit: Did a killall on compiz and used your code to try it out. Still not displaying any sort of buttons.

---

### Post by PaulTR on 2009-05-19
Got help from someone else, who gave me this code that works :)

```

import javax.swing.*;
import java.awt.*;
 
public class Playback {
    public static void main(String[] args) {
        EventQueue.invokeLater(new Runnable(){
            public void run() {
                JFrame f = new JFrame("Playback");
                f.setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
                Container cp = f.getContentPane();
                cp.setLayout(new FlowLayout());
                cp.add(new JButton("Play"));
                cp.add(new JButton("Stop"));
                cp.add(new JButton("Pause"));
                f.pack();
                f.setVisible(true);
            }
        });
    }
}

```

Going to monkey around with that for a bit and see if I can't figure out what all of it does and how it does it. Thanks for all the help :) Still couldn't get the other code to work, even after sudo apt-get remove --purge compiz*

---

### Post by cl333r on 2009-05-19
hehehe to disable compiz go to:
System->Preferences->Appearance->"Visual Effects" tab-> choose "None" (the 1st option).
Restart your java application.

---

### Post by PaulTR on 2009-05-19
Ah! Very awesome, thanks. The code I was using before, and your code work fine now that I have that disabled. Thanks a ton :) Trying to work my way through a ton of programming books for summer entertainment, and little details like that always screw me up <.<

---

### Post by cl333r on 2009-05-19
Glad the issue is solved, now, unless using Java 5 is a must, consider using Java 6, it works fine with compiz (at least with nvidia cards) and is faster. To install:

```

sudo apt-get install sun-java6-jre sun-java6-jdk sun-java6-plugin

```

Now, to make sure that Java 6 is the default Java (JRE and JDK) on your system:
```

sudo update-alternatives --config java

```

---

