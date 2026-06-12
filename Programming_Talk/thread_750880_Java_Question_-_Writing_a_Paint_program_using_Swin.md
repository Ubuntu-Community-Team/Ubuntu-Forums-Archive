---
title: "Java Question - Writing a Paint program using Swing"
date: 2008-04-10
forum: Programming Talk
---

### Post by dolgion1 on 2008-04-10
hello folks,

I'm writing a simple paint program for a school assignment using Swing.
I can already choose colors and draw simple lines on my JPanel component that I use for canvas.
Problem is now, that anytime the JPanel has to repaint itself, the drawings dissappear.
For example, if I resize my JFrame, and therefore the canvas, or if I drag another window on top, or minimize the program window. 
It is obvious that everytime the canvas has to update and repaint itself, 
the drawings that fall under the "dirty" part of the window are discarded.
How can I make the JPanel remember what was drawn on it and not have it discard it everytime it has to repaint?

Btw, I use a Graphics object to draw lines, and am planning to include other brush-modes using the methods of the Graphics class.

here is my code for reference:

import javax.swing.*;
import java.awt.*;
import java.awt.event.*;
import java.awt.image.BufferedImage;
import java.awt.Color;
import java.awt.Graphics;
import java.awt.GraphicsEnvironment;
import java.awt.Point;

public class Paint extends JFrame {
	public BufferedImage image = new BufferedImage(500,500,BufferedImage.TYPE_INT_RGB);
	private JPanel canvas = new JPanel();
	private Point lastPos = null;
	private JPanel colorPanel = new JPanel();
	private JMenuBar menuBar = new JMenuBar();
	private JMenu file = new JMenu("File");
	private JMenuItem colorItem = new JMenuItem("Color");
	private Graphics gc;
	public Paint () {
		setTitle("pSaiko Paint");
		setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
		setSize(600,400);
		colorPanel.setLayout(new GridLayout(2,7));
		file.add(colorItem);
		menuBar.add(file);
		canvas.setBackground(Color.WHITE);
		canvas.setSize(400,400);

		getContentPane().add(canvas, BorderLayout.CENTER);
		getContentPane().add(menuBar, BorderLayout.NORTH);
		setVisible(true);
		// get the Graphics Context
		
		gc = canvas.getGraphics();
		gc.setColor(Color.BLACK);
		gc.drawRect(0, 0, 100, 100);
				
		colorItem.addActionListener(new ActionListener () {
			public void actionPerformed (ActionEvent a) {
				ColorDialog c = new ColorDialog ();
			}
		});
		
		canvas.addMouseMotionListener(new MouseMotionListener () {
			public void mouseDragged (MouseEvent m) {
				// the mouse(pen) was dragged, so the pixels at coords found in
				// MouseEvent m must be updated with current color
				Point p = m.getPoint() ;
				gc.drawLine(lastPos.x, lastPos.y, p.x, p.y) ;
				lastPos = p ;
			}
			public void mouseMoved (MouseEvent m) {}
		});
		canvas.addMouseListener(new MouseListener () {
			public void mouseClicked(MouseEvent e) {}
			public void mousePressed(MouseEvent e) {lastPos = e.getPoint();}
			public void mouseReleased(MouseEvent e) {lastPos = null;}
			public void mouseEntered(MouseEvent e) {}
			public void mouseExited(MouseEvent e) {}
		});
	}
	
	public void captureCanvasImage (){
		System.out.println("1");
		Graphics g = image.createGraphics();
		canvas.paint(g);
	}
	class ColorDialog extends JDialog{
		private JColorChooser colorChooser = new JColorChooser ();
		private JButton okButton = new JButton ("OK");
		private JButton cancelButton = new JButton ("Cancel");
		public ColorDialog() {
			setLayout(new FlowLayout());
			setTitle("Color Dialog");
			add(colorChooser);
			add(okButton);
			add(cancelButton);
			pack();
			setVisible(true);
			okButton.addActionListener(new ActionListener () {
				public void actionPerformed(ActionEvent a) {
					gc.setColor(colorChooser.getColor());
					setVisible(false);
				}
			});
		}
	}
	
	public static void main (String [] args) {
		Paint p = new Paint();
	}
}


thanks in advance for all replies

---

### Post by heikaman on 2008-04-10
hi...
each time an event happens : you move the window, resize, ... the JPanel repaints it self  (which clears your drawings)  so here's what you need to do.


1- don't draw directly on the JPanel, instead draw on a BufferedImage.

2- subclass JPanel and override "paintComponent(Graphics g)" this method is called when the JPanel needs to repaint.

3- In paintComponent(Graphics g) draw the BufferedImage to the JPanel.

if this isn't clear here's an example from a paint program i wrote a couple of years ago:

[PHP]

//draw on this
BufferedImage image = new BufferedImage(800, 600, BufferedImage.TYPE_INT_RGB);

//get the image Graphics object
Graphics2D imageG = image.createGraphics();

//draw something
imageG.fillRect(0, 0, 100, 100);

//dispose the Graphics object when you're finished.
imageG.dispose();


//finally the JPanel subclass:

	private class paintPanel extends JPanel {

		public void paintComponent(Graphics g) {
			//call super paintComponent
			super.paintComponent(g);

			//cast to Graphics2D
			Graphics2D tempg = (Graphics2D) g;

			//Draw BufferedImage
			tempg.drawImage(image, 0, 0, null);

		}



	}


[/PHP]

---

### Post by themusicwave on 2008-04-10
Just out of curiosity are you taking Object Oriented programming at Behrend in Erie?

We had the exact assignment when I took it....

I think heikaman's advice on super.paint(g) will help you.  Forgetting that line can cause a lot of issues with swing.

---

