---
title: "Help with JAVA collison detection problem."
date: 2008-06-18
forum: Programming Talk
---

### Post by farrell2k on 2008-06-18
I have been racking my brain trying to figure out what is wrong with my collision detection, and I know it is something extremely simple that I am just not seeing, so maybe someone here can shed some light on it for me.

I have created this app that generates two rectangles, then checks for collision.  When a collision occurs, the moving rectangle bounces off the other.   Everything works great if I am moving around by only pressing one key at a time, but if I am holding down two opposite movement keys (w and s, or a and d) at the point where the two rectangle collide, the rectangles pass through one another.  

I hope I've made myself clear.   Thanks for any help :)




// ***** code
/*
 * To change this template, choose Tools | Templates
 * and open the template in the editor.
 */

package collide;
import javax.swing.*;
import java.awt.*;
import java.awt.event.KeyEvent;
import java.awt.event.KeyListener;

/**
 *
 * @author tj
 */
public class Collide extends JFrame
{
    final int WIDTH=800, HEIGHT=600, UP =0, DOWN =1, LEFT =2, RIGHT =3, STOP = 4;
    int speed = 5;    
    int p1Direction = STOP;
    
    Rectangle box1 = new Rectangle(350,250,100,100);
    Rectangle box2 = new Rectangle(400,400,20,20);
    
    public Collide()
    {
        super("Collision Detection Test");
        setSize(WIDTH,HEIGHT);
        setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
        setVisible(true);
        
        Box2Go bx2 =new Box2Go();
        bx2.start();
        
       
    }
    
    @Override
    public void paint(Graphics g)
    {
        super.paint(g);
        g.fillRect(box1.x,box1.y,box1.width,box1.height);
        g.fillRect(box2.x,box2.y,box2.width,box2.height);
        
    }
    
    private class Box2Go extends Thread implements KeyListener
    {
        public void run()
        {
            addKeyListener(this);
            
            while(true)
            {
                try
                {
                    
                    if (box2.intersects(box1))
                    {
                        System.out.println("HIT");
                        speed = -5;
                    }
                    
                    repaint();
                    
                    if (speed <5)
                       speed++;    
                    
                    if (p1Direction == STOP)
                    {
                        box2.x = 400;
                        box2.y = 400;
                        box2.width = 20;
                        box2.height = 20;
                    }
                            
                    if (p1Direction == UP)
                    {
                        box2.y -= speed;
                    }
                    
                    if (p1Direction == DOWN)
                    {
                        box2.y += speed;
                    }
                    
                    if (p1Direction == LEFT)
                    {
                        box2.x -= speed;
                    }
                    
                    if (p1Direction == RIGHT)
                    {
                        box2.x += speed;    
                    }
                    
                    System.out.println(box2.y + " " + speed);
                    Thread.sleep(100);
                    
                }
                
                catch (Exception e)
                {
                    break;
                }
            }
        }
        public void keyTyped(KeyEvent event)
        {
             if (event.getKeyChar() == 'a')
             {
                p1Direction = LEFT;
             }
            if (event.getKeyChar() == 's')
            {
                p1Direction =  DOWN;
            }   
            if (event.getKeyChar() == 'd')
            {
                p1Direction = RIGHT;
            }
            if (event.getKeyChar() == 'w')
            {
                p1Direction = UP;
            }
             
            
        }

        public void keyPressed(KeyEvent event)
        {
            
        }

        public void keyReleased(KeyEvent event)
        {
           
        }
    }
    
    
        
    public static void main(String[] args)
    {
        Collide collide1 = new Collide();
        
    }

}

---

### Post by NormR2 on 2008-06-18
Not sure what it's supposed to do. I'm not able to get the small box to travel over the large one. Perhaps if you added somemore println() statements you could see what is happening.
Some other ideas: 
1)make the small box a different color.
2)if (p1Direction == STOP) etc
why do this code in run()? p1Direction is never set to STOP
3) add some text to the println() in run(): "y=" ... ", speed="
4) show keypress   System.out.println("got char=" + event.getKeyChar());   
5) use if...else if... in keyTyped(). Only one of the the if tests will be true, so once you've found the char, the others will always be false

---

### Post by xlinuks on 2008-06-18
If bouncing back and forward after collision is not a must then this might help:
```

		public void run() {
			addKeyListener( this );

			while( true ) {
				try {
					if( speed < 5 ) {
						speed++;
					}

					if( p1Direction == STOP ) {
						box2.x = 400;
						box2.y = 400;
						box2.width = 20;
						box2.height = 20;
					}

					switch( p1Direction ) {
						case UP:
							box2.y -= speed;
							break;
						case DOWN:
							box2.y += speed;
							break;
						case LEFT:
							box2.x -= speed;
							break;
						case RIGHT:
							box2.x += speed;
							break;
					}

					if( box2.intersects( box1 ) ) {
						System.out.println( "HIT" );

						//just cancel
						switch( p1Direction ) {
							case UP:
								box2.y += speed;
								break;
							case DOWN:
								box2.y -= speed;
								break;
							case LEFT:
								box2.x += speed;
								break;
							case RIGHT:
								box2.x -= speed;
								break;
						}
					}

					repaint();

					System.out.println( box2.y + " " + speed );
					Thread.sleep( 100 );

				} catch( Exception e ) {
					break;
				}
			}
		}

```

---

### Post by Mr.Macdonald on 2008-06-18
You'll want to make a class for a moving box. and in that class also have a thread that you can start and stop. you should extend the Rectangle class and have a thread object. you can look a movement engine i have yet to finish. But it still has good info.

if you extend the rectangle class then you won't need the contains functions (i was attempting a whole rewrite of the shapes in awt).

---

### Post by farrell2k on 2008-06-18
> **xlinuks said:**
> If bouncing back and forward after collision is not a must then this might help:
```

		public void run() {
			addKeyListener( this );

			while( true ) {
				try {
					if( speed < 5 ) {
						speed++;
					}

					if( p1Direction == STOP ) {
						box2.x = 400;
						box2.y = 400;
						box2.width = 20;
						box2.height = 20;
					}

					switch( p1Direction ) {
						case UP:
							box2.y -= speed;
							break;
						case DOWN:
							box2.y += speed;
							break;
						case LEFT:
							box2.x -= speed;
							break;
						case RIGHT:
							box2.x += speed;
							break;
					}

					if( box2.intersects( box1 ) ) {
						System.out.println( "HIT" );

						//just cancel
						switch( p1Direction ) {
							case UP:
								box2.y += speed;
								break;
							case DOWN:
								box2.y -= speed;
								break;
							case LEFT:
								box2.x += speed;
								break;
							case RIGHT:
								box2.x -= speed;
								break;
						}
					}

					repaint();

					System.out.println( box2.y + " " + speed );
					Thread.sleep( 100 );

				} catch( Exception e ) {
					break;
				}
			}
		}

```


Yes!  This is perfect.   I'm too new to java, so I have to review it and figure out everything.   It appears as if you removed my speed = -5, and reversed the direction of the keys when a collison occurs?

---

### Post by xlinuks on 2008-06-19
What I did is a generally a stopgap implementation to the following idea:
if the box detects that it intersects the other box then it should "cancel the move", that's exactly what the second "switch" block does.
BTW: I would suggest for the animation to use double buffering, cause the app is flickering and your/the eyes will start hurting after a few minutes/hours working with it.

---

