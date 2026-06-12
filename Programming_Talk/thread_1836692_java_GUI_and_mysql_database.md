---
title: "java GUI and mysql database"
date: 2011-08-31
forum: Programming Talk
---

### Post by vineeth v s on 2011-08-31
hi,

  i am trying to create a GUI that interact with mysql database in java,
i know till applets in java and bit more than basics in JDBC and mysql throughly .
can anyone help me with some kind of tutorial links???
it will be a great help ,am being googling it for a while.. :(

thanks in advance,

v

---

### Post by howefield on 2011-08-31
Thread moved to "*Programming Talk*"

Not sure if this is the best place for your query, but better than "Tutorials and Tips" where you posted to.

---

### Post by t1497f35 on 2011-08-31
That's CRUD (create read update delete). There's many ways to do this.
You can do it manually by creating your own (Swing) window with a JTable and then using it for CRUD operations through JDBC.
Or you can google for something like "crud java gui" and see other solutions.

---

### Post by dazman19 on 2011-09-01
I have only used swing to make gui apps in java. But its quite a easy library to use, not the prettyest in my opinion, but i see elements of it in netbeans IDE so you can make thing look good if you devote time. 

I take it you have used mysql with java but not with a gui before.. 
I think the part you will find hardest if you have not used java to make a gui before is working with the event handler. And understanding how the jframe/jpanel/(j(whateverelse)) stack up. 

Its basic inheritance you can find in the java online manuals. you are just extending off what you need. Then adding things like jbuttons or jsliders or jtextfields. 

You will need to implement an interface most probably a changelistener/actionlistener of some sort.

here is an example of something i had a while back.
```

import java.awt.*; // required by swing
import java.awt.event.*; //actionlisteners
import java.awt.image.*;
import javax.imageio.*;
import javax.swing.*;  //import swing
//import javax.swing.event.*; //forjslider

public class MyClass extends JPanel implements ActionListener, MouseListener, MouseMotionListener, ChangeListener {

	//JPanel's (additional).
	JPanel jpControls, jpImage;
	
	// Menu items
	JMenuItem openItem, closeItem, quitItem;

//impliment stuff here for interfaces and override abstract methods here

	//required for mouselistener etc.... 
	public void mouseClicked(MouseEvent mevent) {
    }
	public void mousePressed(MouseEvent mevent) {
    }
	 public void mouseReleased(MouseEvent mevent) {
    }
	public void mouseEntered(MouseEvent mevent) {    
    }	
	public void mouseExited(MouseEvent mevent) { 
    }
	public void mouseDragged(MouseEvent mevent) {
	
		//some code here... 
		int x = mevent.getX();
		int y = mevent.getY();
		calcRGB(x,y);
		repaint();
    }
	public void mouseMoved(MouseEvent mevent) {
	}
	
	public void stateChanged(ChangeEvent e) {
		//code for JSlider
		JSlider source = (JSlider)e.getSource();
		if (source.getValueIsAdjusting()) {
			//No code to be processed until mouse is released.
		}		

		if (!source.getValueIsAdjusting()) { 
			//othter stuff
		}
	}
	
	public void actionPerformed(ActionEvent event) {

		JComponent source = (JComponent)event.getSource(); 
	}
	
	//make sure you impliment this aswell
	public void paintComponent( Graphics g ) {
		super.paintComponent(g);
	}


}


```


by all means this probably wont compile, i have just taken snippets out of a project. to show you what you will need. But if you google "java swing tutorials" and try make a simple file/help menu with jmenu and jmenuitems and jmenubars it might be a good start.

If you dont want to use swing there are other library's someone here is bound to point you in the right direction.

---

### Post by vineeth v s on 2011-09-03
hi,

   thanks to all......

nywy ur program shows error.... :)...bt it was helpful..

---

