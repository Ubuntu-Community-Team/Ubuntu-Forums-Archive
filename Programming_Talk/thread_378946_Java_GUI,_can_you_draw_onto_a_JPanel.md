---
title: "Java GUI, can you draw onto a JPanel?"
date: 2007-03-07
forum: Programming Talk
---

### Post by CrazyTn on 2007-03-07
I am trying to make a Tetris game in java

I have a window borderlayout 
West : button Panel
Center: board
  
board is a JPanel, and I want to add JTetris to it. Which will draw the board.
board.add(new JTetris());
contentPane(board, BorderLayout.CENTER);
But it is not being drawn.

Works when I do contentPane.add( new JTetris(), BorderLayout.CENTER);
But I want to have a border around the board. So I want to put the board into a Panel of some sort.

any help would be appreciated.

```
import java.awt.*;
import java.awt.event.ActionEvent;
import java.awt.event.ActionListener;
import java.awt.event.WindowAdapter;
import java.awt.event.WindowEvent;
import java.awt.geom.*;
import javax.swing.*;

public class JTetris extends JPanel{
	public void  paintComponent(Graphics g){
		super.paintComponent(g);
		Graphics2D g2d = (Graphics2D)g;
		
		JTShapes block = new JTShapes(1);	
		Rectangle2D.Double[] outBlock = block.getFigure();

		for(int i=0;i<block.getNumBlock(); i++){
			g2d.fill(outBlock[i]);	
		}
	}

public static void main(String[] args){
		//set up the Window
		JFrame frame = new JFrame();
		frame.setTitle("Java Tetris");
		frame.setSize(550, 670);
		frame.addWindowListener(new WindowAdapter(){
			public void windowClosing(WindowEvent e){
				System.exit(0);	
			}
		});

		Container contentPane = frame.getContentPane();
		contentPane.setLayout(new BorderLayout());		

		//Buttons
		btnPanel = new JPanel(new GridLayout(3,1));
	   btnPanel.setPreferredSize(new Dimension(80,100));
		btnPanel.setBackground(Color.green);

		newGameBtn = new JButton("New");
		pauseBtn =   new JButton("Pause");
		quitBtn =    new JButton("Quit");
		btnPanel.add(newGameBtn);
		btnPanel.add(pauseBtn);
		btnPanel.add(quitBtn);

		JPanel left = new JPanel();
		left.setPreferredSize(new Dimension(100, 670));
		left.add(btnPanel);
		contentPane.add(left, BorderLayout.WEST);	

		JPanel board = new JPanel();
		board.add(new JTetris());	
		contentPane.add(board, BorderLayout.CENTER);

		//set border
		left.setBorder(BorderFactory.createLineBorder(Color.black));	

		frame.show();
	}
//Private variables
	static private JPanel btnPanel;
	static private JPanel rPanel;
	static private JButton newGameBtn;
	static private JButton pauseBtn;
	static private JButton quitBtn;
}


```

```
import java.awt.*;
import java.awt.geom.*;
import javax.swing.*;


public class JTShapes extends Rectangle2D.Double{
	//constructor
	public JTShapes(int tFigure){
		shape = tFigure;
		createFigure();
	}

	public void createFigure(){
		switch(shape){
			case 1: //square
				figure[0] = new Rectangle2D.Double(80.0,0.0,HEIGHT,HEIGHT); 
				figure[1] = new Rectangle2D.Double(20.0,0.0,HEIGHT,HEIGHT);
				figure[2] = new Rectangle2D.Double(80.0,40.0,HEIGHT,HEIGHT); 
				figure[3] = new Rectangle2D.Double(20.0,40.0,HEIGHT,HEIGHT);
		}
	}

	public Rectangle2D.Double[] getFigure(){
		return figure;	
	}

	public int getNumBlock(){
		return numBlock;	
	}
	//public JTShapes move(int position){
	
	//}
	private final int numBlock = 4;	
	private final double HEIGHT = 40.0;
	private int shape;
	private Rectangle2D.Double[] figure = new Rectangle2D.Double[numBlock];
	/*
   private Rectangle2D.Double piece1; 
   private Rectangle2D.Double piece2;
   private Rectangle2D.Double piece3;
   private Rectangle2D.Double piece4;
	*/
}

```

---

### Post by CrazyTn on 2007-03-08
nm problem solved

---

### Post by 1asian2 on 2009-07-14
Hi,
Im having a similar problem adding 2D drawing to a panel. Please could you explame how you solved yours and maybe show some final code??
Thanks

---

### Post by drubin on 2009-07-14
> **1asian2 said:**
> Hi,
Im having a similar problem adding 2D drawing to a panel. Please could you explame how you solved yours and maybe show some final code??
Thanks

You can draw onto a Jpannel but this isn't the best way of drawing onto the screen. I would personally look into Canvas objects. Or creating a custom Component. (Yes I know they are similar but drawing onto JPannel just feels dirty to me)

---

