---
title: "Java help with drawing a circle in drafts game"
date: 2009-11-19
forum: Programming Talk
---

### Post by Shpongle on 2009-11-19
ok so iv an assignment to do and im flying through it,  i have to make the game checkers / drafts . iv got my board class  extending a JPanel . it that class an 8 by 8 array of colored panels are constructed and initialised to redpanels or blackpanels. iv then logic to set up properly and display the board in my game class. i add the board to my game class in the content pane and set that in the games constructor. i can access any board panel by array index. ie myboard.boardpanels[5][1] .

i have a pieces class  shown below but i cant seem to get the pieces to show up on the board , since the pieces will be drawn on colored panels which extend jpanels i overloaded the paint method in the colored panel class.

in my game im trying to draw the pieces like this



mypiece = new DraftsPiece(10,10,100,Color.WHITE);
myBoard.boardpanels[5][1].add(mypiece);
myBoard.boardpanels[5][1].repaint();

please if anyone can help id greatly appreciate it , its driving me mad , and iv been at it for two days straight! all over javadocs and the web! , and still cant get it working , im gettin no compilation errors or runtime errors,  

thanks 

---------------------------------------------------------------------

/**
* to fill in!
* 
* DraftsPieces class
*  .
**/



package draftspkg;

import java.awt.Component;
import java.awt.Color;
import java.awt.Graphics;


public class DraftsPiece extends Component{
	
	
 	boolean isking;
	int x, y, radius;
	Color colour;



    

 
	public DraftsPiece(int x, int y, int radius, Color colour){
		
		this.x = x;

        	this.y = y;

        	this.radius = radius;

        	this.colour = colour;
        	
		isking = false;
		
	}
	
	
	//class functions

	
	// draw the piece

    	public void draw(Graphics g) {

        g.setColor(colour);

        g.fillOval(x, y, 2 * radius, 2 * radius);

    }
	
	
	
	public void setKing( ){
	
		isking = true;
	
	}
}
 

-------------------------------------------------------------------

/**
*
* Colored Panel class
* 
*
**/


package draftspkg;
import javax.swing.JPanel;
import javax.swing.JComponent;
import java.awt.Color;
import java.awt.Dimension;
import java.awt.Graphics;



public class ColoredPanel extends JPanel{

	public ColoredPanel(Color c){
		super();
		setBackground(c);
	}
	
	public ColoredPanel(Color c, int h , int w){
		super();
		setBackground(c);
		setPreferredSize(new Dimension(h,w));
	}


	public void changeColor(Color c){
	
		setBackground(c);
	}
	
	
	// override paint method to paint shapes on the panel

        public void paint(Graphics g) {



            super.paint(g);

            // draw the shape

            g.setColor(Color.WHITE);

            g.fillOval(150, 150, 100, 100);



        }


}

-------------------------------------------------------------------------

---

### Post by Shpongle on 2009-11-19
or if anyone can explain how i draw a circle / oval on a jpanel that i can specify its color . i just cant do anything else until i get this bit done . il be making the game open source too when i finish  , if anyone is interested

---

### Post by myrtle1908 on 2009-11-19
```
import javax.swing.JFrame;
import java.awt.Color;
import java.awt.Graphics;
import java.awt.event.WindowEvent;
import java.awt.event.WindowAdapter;

public class Test extends JFrame {
	public void paint(Graphics g) {
		g.drawOval(50, 50, 50, 50);
		g.setColor(Color.BLUE);
		g.fillOval(50, 50, 50, 50);
	}
	public static void main(String args[]) {
		JFrame frame = new Test();
		frame.addWindowListener(new WindowAdapter() {
			public void windowClosing(WindowEvent we) {
				System.exit(0);
			}
		});
		frame.setBackground(Color.BLACK);
		frame.setSize(200, 200);
		frame.setVisible(true);
	}
}
```

---

### Post by Shpongle on 2009-11-21
thanks but i need to be able to create a circle on an already existing jpanel in a separate class. I have to be able to put a piece on any panel on the board, i wish to be able to add a piece as a component to a panel eg myboard.boardpanels[2][1].add(mypiece);
 and i want to have it so the pieces constructor or a method will draw / create it on the panel , please if anyone can help me with this id greatly appreciate it! thanks

---

### Post by Shpongle on 2009-11-22
i tried the getGraphics method but it doesnt work how i want , i was reading that i have to use the paint method to keep the changes persistent!!

any ideas?

---

### Post by issih on 2009-11-22
If you want to do it like that you could try making a Piece class that extends from JPanel,and override that classes paint method to draw a circle. You can then just add an instance of that piece class to your panels that represent your squares.

Be warned, that I haven't really played with java graphics for about 5 years..so this is probably outdated/just plain wrong :)

Hope that helps

---

