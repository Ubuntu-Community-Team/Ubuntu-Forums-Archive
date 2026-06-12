---
title: "creating a rainbow in java"
date: 2006-04-05
forum: Programming Talk
---

### Post by sublime on 2006-04-05
im having a little difficulty using an array to create a rainbow out of randomize colors in an array.  its a little hard to explain, but ill give it a try anyways.  we were given a set of code to use to create a method that would sort out randomized colors in an array.  there were about 300 colors in the array, red, orange, yellow, green, violet and indigo, with each color being an index.  we were also given a gui to go with it to visualize the sorting.  so i started out by writing a for loop that would go through each index of the array finding the color red.  then it would use the swap method given to swap that index into the first available index.  however i seem to be having some trouble with it because it doesnt do taht at all.  if anyone can provide some help, i think i just need some fresh eyes on it.  sometimes thats all it takes.  yes it is homework btw, no im not asking for someone to do it, just a few hints maybe.

here's the code with my method:
```

// Author By Drew Davidson, 1-April-2005

// Modified by Rick Mercer, 3-April-2006

import java.awt.Color;

import java.util.Observable;

import java.util.Observer;

import java.util.Random;



public class Rainbow extends Observable {



  // All 7 of these (RED, ORANGE, ... , INDIGO) can be stored as a Color

  public static final Color RED = Color.RED;

  public static final Color ORANGE = Color.ORANGE;

  public static final Color YELLOW = Color.YELLOW;

  public static final Color GREEN = Color.GREEN;

  public static final Color BLUE = Color.BLUE;

  public static final Color VIOLET = new Color(138, 43, 226); // Not with Java

  public static final Color INDIGO = new Color(75, 0, 130);   // Not with Java



  // Instance variables you'll need (you may need another)

  private Color[] colors; // The random array that needs to be arranged

  private int n; // The number of Color objects to arrange (set elsewhere, do not change n)

  private int j;

  

  // COMPLETE THIS METHOD TO arrange the array in the colors of the rainbow

  public void arrange() {

     //THIS IS WHERE IM STUCK

     // TODO Complete this arrange method, call swap to see animation

	  for( int i = 0; i <= n; i++)

	  {

		  if( colors[i] == RED);

		  {

			  swap(i, j);

			  j++;

		  }

		  /*else if( colors[i] == ORANGE);

		  {

			  swap(i, a);

			  a++;			  

		  }

		  else if( colors[i] == YELLOW);

		  {

			  swap(i, a);

			  a++;

		  }

		  else if( colors[i] == GREEN);

		  */

	  }





     // SOME OTHER CODE WILL CALL randomizeArray BEFORE CALLING THIS ARRANGE METHOD







     // YOU MUST CALL swap BELOW TO SEE THE ANIMATION REDRAW FOR EVERY SWAP



  }



/************** ** DO NOT CHANGE THE CODE BELOW THIS LINE! ** *********************/





  // Swap colors[i] with colors[j]

  private void swap(int i, int j) {

    Color temp = colors[i];

    colors[i] = colors[j];

    colors[j] = temp;







    // This code allows the GUI to show your algorithm in action

    this.setChanged();

    this.notifyObservers();

    sleep();

  }



  // randomizes the array

  public void randomizeArray() {

    Random rnd = new Random();

    //    insert random color (r,w,b) into array

    for (int i = 0; i < colors.length; i++) {

      int num = rnd.nextInt(7);

      if (num == 0)

        colors[i] = Color.RED;

      else if (num == 1)

        colors[i] = Color.ORANGE;

      else if (num == 2)

        colors[i] = Color.YELLOW;

      else if (num == 3)

        colors[i] = Color.GREEN;

      else if (num == 4)

        colors[i] = Color.BLUE;

      else if (num == 5)

        colors[i] = VIOLET;

      else

        colors[i] = INDIGO;

    }

  }



  // Other instance variables

  private Color purple;

  private long speed;

  private Observer view;



  // Constructor place low

  public Rainbow(int size, Observer theView) {

    //initialize some instance vars

    speed = 300;

    n = size;

    colors = new Color[size];

    purple = new Color(120, 0, 120);

    view = theView;

    // add Observers

    this.addObserver(view);



    // Randomize the array

    randomizeArray();

  } //complete this method



  /*

   * This method will make the current thread sleep for the *

   * specified ammount of time. This enables the GUI to display the *

   * animation in real-time.

   */

  private void sleep() {

    try {

      Thread.sleep(speed);

    } catch (InterruptedException e) {

    }

  }



  // updates the speed based on the slider bar.

  public void updateSpeed(long newSpeed) {

    speed = newSpeed;

  }



  //for the GUI

  public Color[] getArray() {

    return colors;

  }



}

```

heres the gui for testing, it doesnt need any editing, just copy and paste:
```

//Written by Drew Davidson

//April 11th and April 12th



import java.awt.BorderLayout;

import java.awt.Color;

import java.awt.Container;

import java.awt.Graphics;

import java.awt.GridLayout;

import java.awt.event.ActionEvent;

import java.awt.event.ActionListener;

import java.util.Observable;

import java.util.Observer;



import javax.swing.JButton;

import javax.swing.JFrame;

import javax.swing.JPanel;

import javax.swing.JSlider;

import javax.swing.event.ChangeEvent;

import javax.swing.event.ChangeListener;



public final class RainbowGUI extends JFrame implements Observer {

  private Color[] myUnsortedColors;

  private Color[] mySortedColors;

  private Color[] myCurrentColors;

  private int myWidth, myHeight;

  private DrawPanel thePanel;

  private ButtonPanel buttonPanel;

  private Rainbow theRainbow;

  public static final int SIZE = 300;



  public static void main(String[] args) {

    RainbowGUI fg = new RainbowGUI();

    fg.setVisible(true);

  }



  public RainbowGUI() {

    //create a rainbow with 300 strands

    theRainbow = new Rainbow(SIZE, this);



    myCurrentColors = theRainbow.getArray();

    myUnsortedColors = new Color[myCurrentColors.length];



    //Make a value copy of the array

    for (int i = 0; i < myCurrentColors.length; i++) {

      myUnsortedColors[i] = myCurrentColors[i];

    }



    //Format the frame

    this.setTitle("Watch the actions of the... rainbow");

    this.setSize(900, 600);

    this.setLocation(100, 100);

    this.setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);



    //Format and manage the content pane

    Container contentPane = this.getContentPane();



    this.setBackground(Color.WHITE);



    //Format and add the buttonPanel

    buttonPanel = new ButtonPanel(Color.WHITE);

    JButton randomize = new JButton("Randomize");

    JButton sorted = new JButton("Sorted");

    JButton rainbowizeButton = new JButton("Rainbowize");



    // Slider bar to change speed

    JSlider speedBar = new JSlider(JSlider.HORIZONTAL);

    speedBar.addChangeListener(new ChangeListener() {

      public void stateChanged(ChangeEvent e) {

        JSlider source = (JSlider) e.getSource();

        if (!source.getValueIsAdjusting())

          theRainbow.updateSpeed((int) source.getValue() * 10);

      }

    });



    theRainbow.updateSpeed((int) speedBar.getValue() * 10);



    buttonPanel.add(randomize);

    buttonPanel.add(rainbowizeButton);

    // buttonPanel.add(sorted);

    JPanel control = new JPanel();

    GridLayout g = new GridLayout(2, 1);

    control.setLayout(g);

    control.add(buttonPanel);

    control.add(speedBar);



    contentPane.add(BorderLayout.SOUTH, control);



    //Format and add drawPanel

    myWidth = this.getWidth();

    myHeight = this.getHeight();

    thePanel = new DrawPanel();

    thePanel.setSize(myWidth, myHeight);

    contentPane.add(BorderLayout.CENTER, thePanel);



    //Create and register the button listeners

    RainbowizeListener rainbowListener = new RainbowizeListener();

    SortListener sortListener = new SortListener();



    sorted.addActionListener(rainbowListener);

    rainbowizeButton.addActionListener(sortListener);



    RandomListener randomListener = new RandomListener();

    randomize.addActionListener(randomListener);



    //show the rainbow frame

    this.setVisible(true);



  }



  private class DrawPanel extends JPanel {



    int myColumnWidth;

    int myPosition;

    int num;



    public DrawPanel() {

      myColumnWidth = myWidth / myCurrentColors.length;

      myPosition = 0;

      num = 0;

    }



    public void paintComponent(Graphics g) {

      this.drawStripe(g);

    }



    public void drawStripe(Graphics g) {

      for (int i = 0; i < myCurrentColors.length; i++) {

        g.setColor(myCurrentColors[i]);

        g.fillRect(myPosition, 0, myColumnWidth, myHeight);

        myPosition += myColumnWidth;

      }

      myPosition = 0;

    }



  }



  private class ButtonPanel extends JPanel {

    Color myColor;



    public ButtonPanel(Color colorIn) {

      myColor = colorIn;

    }



    public void paintComponent(Graphics g) {

      g.setColor(myColor);

      g.fill3DRect(0, 0, this.getWidth(), this.getHeight(), false);

    }



  }



  private class RainbowizeListener implements ActionListener {

    public void actionPerformed(ActionEvent arg0) {

      theRainbow.arrange();

      thePanel.repaint();

    }

  }



  private class SortListener implements ActionListener {



    public void actionPerformed(ActionEvent arg0) {

      Thread sortThread = new Thread() {

        public void run() {

          theRainbow.arrange();

        }

      };

      sortThread.start();

    }

  }



  private class RandomListener implements ActionListener {

    public void actionPerformed(ActionEvent arg0) {

      theRainbow.randomizeArray();

      myCurrentColors = theRainbow.getArray();

      thePanel.repaint();

    }

  }



  public void update(Observable arg0, Object arg1) {

    myCurrentColors = theRainbow.getArray();

    thePanel.repaint();

  }

}

```

---

### Post by sphinx on 2006-04-05
Yeah, you have just made 2 "Tired eyes" mistakes in the same area. I've highlighted the two characters you should remove.

```
     
	  // TODO Complete this arrange method, call swap to see animation
	  for( int i = 0; i <[COLOR="Red"]**=**[/COLOR] n; i++)
	  {
		  if( colors[i] == RED)[COLOR="Red"]**; <- error**[/COLOR]
		  {
			  swap(i, j);
			  j++;
		  }

```

The <= in the for loop should be just < as when you are iterating through an array you only ever want to go to array[length-1] because aray[length] will always give you an ArrayOutOfBoundsException. This is because the last index of an array with a length of 5 is array[4]. I recommend you run the program without fixing this first to see what happens, or play around with looping over an array with a length of 3 just so you can see what the i value is dooing each loop.

The second mistake is at the end of you if statment. An if statment expects a { character to follow, if not then the next line is executed untill the ;. What this means is the if statment you have written is logically the same as the following:

```
if( colors[i] == RED) 
{
  // do nothing
}

swap(i, j);
j++;
```

So you can see that the ';' character has, in effect, removed the if statment from having any effect whatsoever, causing the swap(i,j) and the j++ to be run every loop regardless of the color.

You may have already known about both of these error but failed to see them because you have been staring at the code for hours. That happens to us all at some point.

---

### Post by sublime on 2006-04-06
```

if( colors[i] == RED); <- error
		  {
			  swap(i, j);
			  j++;
		  }

```
[img]http://forums.clubsi.com/images/graemlins/suicide-santa.gif[/img]

thanks man.  i knew it was something stupid like that.  works like a charm now.

---

