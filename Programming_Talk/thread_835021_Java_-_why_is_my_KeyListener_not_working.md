---
title: "Java - why is my KeyListener not working?"
date: 2008-06-20
forum: Programming Talk
---

### Post by farrell2k on 2008-06-20
Does anyone know why my app is not responding properly to key presses? 

Thank you.
  

package game;
import javax.swing.*;
import java.awt.*;
import java.awt.event.KeyEvent;
import java.awt.event.KeyListener;

public class Game extends JPanel
{
    int up = 0, down = 1, left = 2, right = 3, still = 4;
    int p1Direction;
    int speed;
    
       Rectangle p1 = new Rectangle(100,100,30,30);
    
       public Game()
    {
        //start Thread
        MoveP1 moveP1 = new MoveP1();
        moveP1.start();
        
    }
    
    public void paintComponent(Graphics g)
    {
        super.paintComponent(g);
        g.setColor(Color.red);
        g.fillRect(p1.x,p1.y,p1.width,p1.height);
        
        
    }
    
    public class MoveP1 extends Thread implements KeyListener
    {
        public void run()
        {
            addKeyListener(this);
            
            while(true)
            {
                
                repaint();
                
                try
                {   
                    if (p1Direction == down)
                    {
                        p1.y++;
                        System.out.println(p1.x + " " + p1.y);
                    }
                    
                    Thread.sleep(60);
                
                
                }
                
                catch(Exception e)
                {
                    e.printStackTrace();
                }
            }
        }
        
        public void keyTyped(KeyEvent event)
        {
            
        }

        public void keyPressed(KeyEvent event)
        {
            if (event.getKeyChar() == 's')
            {
                p1Direction = down;
                System.out.println("You are pressing s.");
            }
        }

        public void keyReleased(KeyEvent event)
        {
            
        }
    }
    
    
    public static void main (String[]args)
    {
        Game game1 = new Game();
        
        JFrame frame = new JFrame("game test");
        frame.setSize(800,600);
        frame.setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
        frame.getContentPane().add(game1);
        frame.setVisible(true);
    }
    
}

---

### Post by xlinuks on 2008-06-20
One must explicitly tell Java that JPanel should receive focus and such types of events, thus your constructor should look like this:
```

	public Game() {
		//start Thread
		setFocusable( true ); //this line has been added
		MoveP1 moveP1 = new MoveP1();
		moveP1.start();

	}

```

btw, I would suggest using the code tags for the code to be readable for people who read your post(s).

---

### Post by reality1011 on 2008-06-20
> **farrell2k said:**
> Does anyone know why my app is not responding properly to key presses? 

Thank you.
  

package game;
import javax.swing.*;
import java.awt.*;
import java.awt.event.KeyEvent;
import java.awt.event.KeyListener;

public class Game extends JPanel
{
    int up = 0, down = 1, left = 2, right = 3, still = 4;
    int p1Direction;
    int speed;
    
       Rectangle p1 = new Rectangle(100,100,30,30);
    
       public Game()
    {
        //start Thread
        MoveP1 moveP1 = new MoveP1();
        moveP1.start();
        
    }
    
    public void paintComponent(Graphics g)
    {
        super.paintComponent(g);
        g.setColor(Color.red);
        g.fillRect(p1.x,p1.y,p1.width,p1.height);
        
        
    }
    
    public class MoveP1 extends Thread implements KeyListener  **[COLOR="Red"][SIZE="5"]==> this is the problem[/SIZE][/COLOR]**
    {
        public void run()
        {
            addKeyListener(this); [SIZE="5"][COLOR="Red"]**==> this is why ....Dont add actionlisteners to threads**[/COLOR][/SIZE]
            
            while(true)
            {
                
                repaint();
                
                try
                {   
                    if (p1Direction == down)
                    {
                        p1.y++;
                        System.out.println(p1.x + " " + p1.y);
                    }
                    
                    Thread.sleep(60);
                
                
                }
                
                catch(Exception e)
                {
                    e.printStackTrace();
                }
            }
        }
        
        public void keyTyped(KeyEvent event)
        {
            
        }

        public void keyPressed(KeyEvent event)
        {
            if (event.getKeyChar() == 's')
            {
                p1Direction = down;
                System.out.println("You are pressing s.");
            }
        }

        public void keyReleased(KeyEvent event)
        {
            
        }
    }
    
    
    public static void main (String[]args)
    {
        Game game1 = new Game();
        
        JFrame frame = new JFrame("game test");
        frame.setSize(800,600);
        frame.setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
        frame.getContentPane().add(game1);
        frame.setVisible(true);
    }
    
}



Actionlisteners are for Components not Classes which extend threads.  Try creating a textfield, adding an actionlistener....

Here I did it for you... type some text and then press enter....


> 

import javax.swing.*;
import java.awt.*;
import java.awt.event.KeyEvent;
import java.awt.event.KeyListener;

public class Game extends JPanel
{
    int up = 0, down = 1, left = 2, right = 3, still = 4;
    int p1Direction;
    int speed;
    
       Rectangle p1 = new Rectangle(100,100,30,30);
    
       public Game()
    {
        //start Thread
        MoveP1 moveP1 = new MoveP1(20); // NOW EXTENDS JTEXTFIELD not Thread
        //moveP1.start();
	add(moveP1);
        
    }
    
    public void paintComponent(Graphics g)
    {
        super.paintComponent(g);
        g.setColor(Color.red);
        g.fillRect(p1.x,p1.y,p1.width,p1.height);
        
        
    }
    
    public class [SIZE="5"]**[COLOR="Red"]MoveP1 extends JTextField [/COLOR]**[/SIZE] implements KeyListener
    {


	public MoveP1(int i){
	    super(i);
	     addKeyListener(this); //==> this is why ....
	 
	}
    
        public void keyTyped(KeyEvent event){}
        

        public void keyPressed(KeyEvent event)
        {
            if (event.getKeyText(event.getKeyCode()).equals("Enter")) 
            {

System.out.println("Getting the current value of this field:" + this.getText());
            }
    }

        public void keyReleased(KeyEvent event){}
    }
    
    
    public static void main (String[]args)
    {
        Game game1 = new Game();
        
        JFrame frame = new JFrame("game test");
        frame.setSize(800,600);
        frame.setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
        frame.getContentPane().add(game1);
        frame.setVisible(true);
    }
    
}

---

### Post by benjamin123 on 2009-01-31
Hello everybody! I'm new to these forums, and i have a question about a KeyListener too.
```
/*
 * To change this template, choose Tools | Templates
 * and open the template in the editor.
 */

/**
 *
 * @author Beni
 */
import java.awt.*;
import java.awt.event.*;
import javax.swing.*;
import java.awt.event.KeyAdapter;


public class test {
    public static void main(String[] args) {
        JFrame f = new JFrame("Tetris v0.01");
		f.setBounds(300,300,500,700);
        f.setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
        Container panel = new TetrisPanel();
        panel.setFocusable(true);
        f.getContentPane().add(panel, BorderLayout.CENTER);
        f.setVisible(true);
    }

    
}

class TetrisPanel extends JPanel implements KeyListener, MouseListener {
	static final long serialVersionUID=5L;
	int x_poz = 100;
	int y_poz = 100;
	int a = 30;
	private Image dbImage;
	private Graphics dbg;
	int[][] tab1 = {{0,0,0,0,0},
				    {0,0,0,0,0},	
				    {0,1,1,1,0},
				    {0,0,0,1,0},
				    {0,0,0,0,0}};
	int[][] tab2=new int[5][5];
	int[][] temp=new int[5][5];				
	
    public TetrisPanel() {
        super();
        setLayout(new BorderLayout());
        setBorder(BorderFactory.createLineBorder(Color.black));
    }

    /*@Override
    public Dimension getPreferredSize() {
        // Figure out what the layout manager needs and
        // then add 100 to the largest of the dimensions
        // in order to enforce a 'round' bullseye 
        Dimension layoutSize = super.getPreferredSize();
        int max = Math.max(layoutSize.width,layoutSize.height);
        return new Dimension(max+100,max+100);
    }
*/
    protected void paintComponent(Graphics g) {
        for(int i=0;i<tab1.length;i++)
			for(int j=0;j<tab1[i].length;j++)
				if(tab1[i][j]==1) {
					g.setColor(Color.red);
					g.fillRect(x_poz+(a*j),y_poz+(a*i),a,a);
				}	
    }
	
    public void update (Graphics g) {
	if (dbImage == null) {
        dbImage = createImage (this.getSize().width, this.getSize().height);
        dbg = dbImage.getGraphics ();
	}

	dbg.setColor(getBackground ());
	dbg.fillRect(0, 0, this.getSize().width, this.getSize().height);
        dbg.setColor(getForeground());
	paint(dbg);
	g.drawImage (dbImage, 0, 0, this);
	}
	
    public void obrni(int[][] tab1, int[][] tab2) {
	for(int i=0;i<5;i++) 
            for(int j=0;j<5;j++) 
		tab2[i][5-1-j]=temp[j][i];//algoritem za rotacijo//rotation
	for(int i=0;i<5;i++) 
            for(int j=0;j<5;j++)
		temp[i][j]=tab2[i][j];
    }

    public void keyTyped(KeyEvent e) {
    }

    public void keyPressed(KeyEvent e) {
		int c=e.getKeyCode();
		if (c==KeyEvent.VK_RIGHT) {
			//obrni(tab1,tab2);
			x_poz++;
            System.out.println("pritisk");
			repaint();
			e.consume();
		}
    }

    public void keyReleased(KeyEvent e) {
    }

    public void mouseClicked(MouseEvent e) {
    }

    public void mousePressed(MouseEvent e) {
    }

    public void mouseReleased(MouseEvent e) {
    }

    public void mouseEntered(MouseEvent e) {
    }

    public void mouseExited(MouseEvent e) {
    }
	
	
}

```
I keep pressing the right arrow key, but it wont do a thing. What could be the problem?
My programming skills in java are not very good, still learning.
Greetings, Benjamin

---

### Post by cl333r on 2009-01-31
```

    public TetrisPanel() {
        super();
	addKeyListener( this );
        setLayout(new BorderLayout());
        setBorder(BorderFactory.createLineBorder(Color.black));
    }

```

---

### Post by benjamin123 on 2009-01-31
Thank you very much for your help, sir. 
Have a nice day!
Greetings, Benjamin

---

### Post by benjamin123 on 2009-02-01
Well, the KeyListener works, but now, everytime the Tetris figure moves, it leaves behind the old trail. How could i do that, so the old figure would be deleted, and only the new one would appear?
Greetings, Benjamin

---

### Post by benjamin123 on 2009-02-02
Anyone?

---

### Post by dutyandcourage@gmail.com on 2012-05-16
Generally the way key listeners work is you first Implement the KeyListener. 

```

class vernaKeyListener implements KeyListener {

        public void keyTyped(KeyEvent e) {
            throw new UnsupportedOperationException("Not supported yet.");
        }

        public void keyPressed(KeyEvent e) {
            throw new UnsupportedOperationException("Not supported yet.");
        }

        public void keyReleased(KeyEvent e) {
            throw new UnsupportedOperationException("Not supported yet.");
        }
        
    };

```

Then you declare an object of the type of KeyListener you implemented in your JFrame. (It doesn't have to be a JFrame though, it can be any class that inherits from Component.) Then when you want your JFrame to start using your KeyListener you call addKeyListener(yourKeyListener).

```

class rawr extends JFrame{
    vernaKeyListener aKeyListener;
    rawr(){
        aKeyListener = new vernaKeyListener();
        this.addKeyListener(aKeyListener);
    }
}

```

Thereafter whenever your JFrame recieves a Keystroke it will call the functions defined in your KeyBoardListener class to handle the event.

---

