---
title: "I need some help with this Java code"
date: 2007-09-03
forum: Programming Talk
---

### Post by Xzallion on 2007-09-03
I started coding this 2D java game back in High School, which was about two years ago.  I had to code it in JBuilder (If my memory serves me), and it ran in that but wouldn't work outside of it, but I have messed it up since where it doesn't work anywhere.  I only worked on it for about a month out of high school and then let it sit until I could take a college intro to Java course, which I completed last semester.  But now I can't figure out what exactly I was doing with it or how to fix it and I don't have anyone to ask.  So If someone can help me fix, clean up, and get this working I would be very grateful.

Its a bare bones 2D rpg that plays like the Nintendo Entertainment Systems  Dragon Warrior (movement, character development, combat) but the maps are similar to the original zelda (you have a screen, then move to another screen, etc.)

Heres the code... Its a mess.

Square.java
```
package game;
/*Java Warrior 
 *
 *controls each individual square in the screen grid.
 */
 

public class Square
{
	//square variables
	private int i; //X coordinate of the world map
	private int j; //Y coordinate of the world map
	private int x; //X coordinate of the square.
	private int y; //Y coordinate of the square.
	private int graphic; //integer representing graphic file to load.
	private boolean stepOn; //determines if the player can step on this square.
	private boolean teleport; //determines if the square is a door or ground.
	private int teleportI; //Map location I to teleport to.
	private int teleportJ; //Map location J to teleport to.
	private int teleportX; //X location on the map represented by I, J to teleport to.
	private int teleportY; //Y location on the map represented by I, J to teleport to.
	private boolean characterThere;  //determines if a character is there or not
	
	public static void main(String[] args)
	{
		// For Testing purposes
		System.out.println("Square.java ran");
	}
	
	public Square(int newI, int newJ, int newX, int newY)
	{
		i = newI;
		j = newJ;
		x = newX;
		y = newY;
		stepOn = false;
		teleport = false;
		teleportI = 0;
		teleportJ = 0;
		teleportX = 0;
		teleportY = 0;
		graphic = 0;
	}

	public int getGraphic()
	{
		return graphic;
	}
	
	public boolean getCharacter()
	{
		return characterThere;
	}
	
	public boolean getStepOn()
	{
		return stepOn;
	}
	
	public int getX()
	{
		return x;
	}
	
	public int getY()
	{
		return y;
	}
	
	public void setGraphic(int newGraphic)
	{
		graphic = newGraphic;
	}
	
	public void setStepOn(boolean newStepOn)
	{
		stepOn = newStepOn;
	}
	
	public void setTeleport(boolean newTeleport)
	{
		teleport = newTeleport;
	}
	
	public void setCharacter(int newCharacter)
	{
		if(newCharacter == 1)
		{
			characterThere = true;
		}
		else if(newCharacter == 0)
		{
			characterThere = false;
		}
	}
	
	public void setTeleportCoordinates(int newTeleportI, int newTeleportJ, 
		int newTeleportX, int newTeleportY)
	{
		teleportI = newTeleportI;
		teleportJ = newTeleportJ;
		teleportX = newTeleportX;
		teleportY = newTeleportY;
	}
	
	public void setCharacterStart(boolean newThereNow)
	{
		characterThere = newThereNow;
	}
	
	
	
}
```

Dice.java (I completely redid this one)
```
package game;

/**
 * Dice generates a random number similiar to how varius dice do. It will be
 * used to generate any random number for the RPG Java Warrior.
 * 
 * @author kenneth
 */
public class Dice {

	/**
	 * Main Method: Used to test the Dice program.
	 * 
	 * @param args
	 */
	public static void main(String[] args) {
		System.out.println("Roll a 20 sided die!");
		int sides = 20;

		for (int rolls = 1; rolls < 5; rolls++) {
			System.out.println(rolls + "D" + sides);
			System.out.println(dieRoller(sides, rolls));
			System.out.println("");
		}
	}

	/**
	 * The dieRoller method rolls a dice with x many sides y many times and
	 * returns the result.
	 * 
	 */
	public static int dieRoller(int sides, int rolls) {
		int count = 0;// determines how many rolls have happened
		int dieTotal = 0;// the total of all dice rolls

		do {
			// generates the random number
			int dieRoll = (int) (sides * Math.random()) + 1;
			count++;
			dieTotal = dieTotal + dieRoll;// adds the roll to dieTotal
		} while (count < rolls);

		return dieTotal;
	}

}

```

MapLoader.java (Loads the map from a save file)
```
package game;

/*Java Warrior 
 *
 *Loads the map for the game by setting the variables for every square.

 */

 

 

import java.io.*;

 

 public class MapLoader

 {

 	//counters

 	static int squareCounter = 0;  //counts the number of 

 									//squares in the map.

 	

 	//square coordinates

 	static int i;  //overworld maps x

 	static int j;  //overworld maps y

 	static int x;  //screen maps x

 	static int y;  //screen maps y

 	

 	//dummy variables

 	static int stepOnInt;  //dummy variable for later

 	static int teleportInt;  //dummy variable for later

 	

 	//teleport coordinates

 	static int teleportI;  //overworld maps x

 	static int teleportJ;  //overworld maps y

 	static int teleportX;  //screen maps x

 	static int teleportY;  //screen maps y

 	

 	//square interaction

 	static boolean stepOn;  //determines if you can step on the square

 	static boolean teleport;  //determines if the square is a door/stairs

 								//that would link to another map location

 	

 	//starting location for new game

 	static int charStartInt;

 	

 	//graphics

 	static int graphic;

 	 	

 	//read data from a file	

 	private static BufferedReader stdin;

 	private static String tempLine;

 	private static String[] tempArray = new String[11];

 	private static boolean stage = false;



// 	

 	public static void main(String[] args)

	{

		// for testing purposes only!

	}

//

	

	public static Square[][][][] MapLoader(Square[][][][] square, 

			String fileName) throws Exception

 	{

 		//Debugging aid to determine where errors occur

 		System.out.println("MapLoader has been Ran");

 		

 		stdin = new BufferedReader(new FileReader(new File(fileName)));

 		

 		//while the file has lines to be read

		while (stdin.ready())

 		{

 			reader();

	 		splitter();

	 		updateSquare(square);

	 		squareCounter++;

 		}

 		

 		System.out.println("MapLoader() finished completely");

 		

 		return square;

	}

	

	

		

	public static void reader() throws Exception

 	{

 		tempLine = stdin.readLine();

 	}

 	

 	public static void splitter()

 	{

 		tempArray = tempLine.split(",");

 	}

 	

 	public static void updateSquare(Square[][][][] square)

 	{

 		//parses the file into integers

 		i = Integer.parseInt(tempArray[0]);

 		j = Integer.parseInt(tempArray[1]);

 		x = Integer.parseInt(tempArray[2]);

 		y = Integer.parseInt(tempArray[3]);

 		stepOnInt = Integer.parseInt(tempArray[4]);

 		teleportInt = Integer.parseInt(tempArray[5]);

 		teleportI = Integer.parseInt(tempArray[6]);

 		teleportJ = Integer.parseInt(tempArray[7]);

 		teleportX = Integer.parseInt(tempArray[8]);

 		teleportY = Integer.parseInt(tempArray[9]);	

 		charStartInt = Integer.parseInt(tempArray[10]);

 		graphic = Integer.parseInt(tempArray[11]);

 					 		 		 		 		

 		//sets the stepOn boolean to true or false, 

 		//	or outputs a error message

 		if(stepOnInt == 0)

 		{

 			square[i][j][x][y].setStepOn(false);

 		}

 		else if(stepOnInt == 1)

 		{	

 			square[i][j][x][y].setStepOn(true);

 		}

 		else

 		{

 			System.out.println("Map File input Error on variable: stepOn");

 		}

 		

 		//sets the teleport boolean to true or false, 

 		//	or outputs a error message

 		if(teleportInt == 0)

 		{

 			square[i][j][x][y].setTeleport(false);

 		}

 		else if(teleportInt == 1)

 		{

 			square[i][j][x][y].setTeleport(true);

			square[i][j][x][y].setTeleportCoordinates(teleportI, teleportJ, 

			teleportX, teleportY);

 		}

 		else

		{

			System.out.println("Map File input Error on variable: teleport");

	 	}	

 		

 		//sets the characters starting location for a new game

 		if(charStartInt == 1)

 		{

 			square[i][j][x][y].setCharacterStart(true);

 		}

 		else if(charStartInt == 0)

 		{

 			//does nothing

 		}

 		else

 		{

 			System.out.println("Map File Input Error on variable: CharStart");

 		}

 		

 		//set that squares graphic

 		square[i][j][x][y].setGraphic(graphic);

 	}

 }
```

MapDrawer.java (Draws the map)
```
package game;

/*Java Warrior 
 *
 *Draws the map for the game.
 */
 
 
 public class MapDrawer
{
	private Square[][][][] square;
	static int counter = 0;
//
	private int worldX;
	private int worldY;
//
			
	public static void main(String[] args)
	{
		//for testing purposes
		
	}
	
	//Default Constructor
	public MapDrawer() throws Exception
	{
		//Debugging aid to determine where errors occur
		System.out.println("MapDrawer Default Constructor start");
		
		square = new Square[1][1][20][15];
		worldX = 1;
		worldY = 1;
		
		//initialize the squares
		for(int i=0; i<worldX; i++)
		{
			for(int j = 0; j<worldY; j++)
			{
				for(int x=0; x<20; x++)
				{
					for(int y=0; y<15; y++)
					{
						square[i][j][x][y] = new Square(i, j, x, y);
					}
				}
			}
		}
		
			
		
		square = MapLoader.MapLoader(square, "Default.txt");

		//Debugging aid to determine where errors occur
		System.out.println("MapDrawer Default Constructor finish");
	}
	
	//Parameter Constructor
	public MapDrawer(String fileName) throws Exception
	{
		//Debugging aid to determine where errors occur
		System.out.println("MadDrawer Parameter Constructor Ran");
		
		square = MapLoader.MapLoader(square, fileName);
	}


	public int getSquareGraphic(int i, int j, int x, int y)
	{
		System.out.println("Square number: " + counter);
		counter++;
		
		if(counter%300==0)
		{
			System.out.println("************************");
		}
		
		return square[i][j][x][y].getGraphic();
	}
	
	public boolean getCharacterLocation(int i, int j, int x, int y)
	{
		return square[i][j][x][y].getCharacter();
	}
	
	public boolean getStepOnVariable(int i, int j, int x, int y)
	{
		return square[i][j][x][y].getStepOn();
	}

	public void setSquareGraphic(int i, int j, int x, int y, int newGraphic)
	{
		square[i][j][x][y].setGraphic(newGraphic);
	}
	
	public void setCharacterLocation(int i, int j, int x, int y, int character)
	{
		square[i][j][x][y].setCharacter(character);
	}
	
}
```

and the main class RPG.java
```
package game;

/* Java Warrior 
 *
 *version started:04/08/2006
 * This is the main class for the program.  It is the one that utilizes
 *the others to run the game.
 */

 

import java.awt.*;

import javax.swing.*;

import java.awt.event.*;

 

public class RPG extends JApplet implements KeyListener

{	

	int stage = 0;  //determines the flow of the game.

	int titleSelect = 192;  //y location of the title screen selection icon.

	

	//map coordinates

	int i = 0;

	int j = 0;

	int x = 0;

	int y = 0;

	

	//character coordinates

	int cI = 0;

	int cJ = 0;

	int cX = 0;

	int cY = 0;

	

	//for movement

	boolean up = false;

	boolean down = false;

	boolean left = false;

	boolean right = false;	

	

	private MapDrawer game;

	

	String filename;

	

	Toolkit kit = Toolkit.getDefaultToolkit();

	

			//Game Graphics

	//Character

	Image character = Toolkit.getDefaultToolkit().createImage(

		"Java_Warrior_Sprites/char_down.png");

	//Water

	Image water = Toolkit.getDefaultToolkit().createImage(

		"Java_Warrior_Sprites/blue_water.png");

	//Rock

	Image rock = Toolkit.getDefaultToolkit().createImage(

		"Java_Warrior_Sprites/brown_rock.png");

	//Bush

	Image bush = Toolkit.getDefaultToolkit().createImage(

		"Java_Warrior_Sprites/green_bush.png");

	//Sand

	Image sand = Toolkit.getDefaultToolkit().createImage(

		"Java_Warrior_Sprites/yellow_sand.png");	

	

	public void init()

	{

		Toolkit kit = Toolkit.getDefaultToolkit();

		addKeyListener(this);

	}

	

	public void main(String[] args)

	{

		

	}

	

	

	//draws the graphics inside the applet

		public void paint(Graphics g)

	{

		//Title Screen Stage

		if(stage==0)

		{

			//Debugging aid to determine where errors occur

			System.out.println("MapDrawer paint() Title Screen has been drawn");

			

			//draws the title screen

			g.setColor(Color.BLACK);

			g.fillRect(0,0,640,512);

			

			g.setColor(Color.RED);

			g.drawString("Java Warrior", 300,20);

			g.drawString("New Game", 320, 192);

			g.drawString("Load Game", 320, 224);

			g.drawString("*", 310, titleSelect);

		}

		else if(stage==1)

		{

			//debugging message

			System.out.println("stage one reached");

			

			//draws the black background

			g.setColor(Color.BLACK);

			g.fillRect(0,0,640,512);

			

			//draws the game board

			for(int x=0; x<20; x++)

			{

				for(int y=0; y<15; y++)

				{

					if(game.getSquareGraphic(i, j, x, y) == 0)

					{

						g.drawImage(sand, x*32, (y+1)*32, null);

					}

					else if(game.getSquareGraphic(i, j, x, y) == 1)

					{

						g.drawImage(bush, x*32, (y+1)*32, null);

					}

					else if(game.getSquareGraphic(i, j, x, y) == 2)

					{

						g.drawImage(rock, x*32, (y+1)*32, null);

					}

					else if(game.getSquareGraphic(i, j, x, y) == 3)

					{

						g.drawImage(water, x*32, (y+1)*32, null);

					}

					else if(game.getSquareGraphic(i, j, x, y) == 4)

					{

						g.drawImage(character, x*32, (y+1)*32, null);

					}

					

						

				}

			}

			

			//determines the character location

			for(int x=0; x<20; x++)

			{

				for(int y=0; y<15; y++)

				{

					if(game.getCharacterLocation(i, j, x, y) == true)

					{	

					 	cI = i;

					 	cJ = j;

					 	cX = x;

					 	cY = y;

						

						up = game.getStepOnVariable(i, j, x, y-1);

						down = game.getStepOnVariable(i, j, x, y+1);

						left = game.getStepOnVariable(i, j, x-1, y);

						right = game.getStepOnVariable(i, j, x+1, y);

					}

				}	

			}

		}

	}

	

	public void keyTyped(KeyEvent e)

	{

		//empty

	}

	

	public void keyPressed(KeyEvent e)

	{

		//empty currently, will need stuff added for movement

		int key = e.getKeyCode();

		

		if(key==e.VK_LEFT)

		{

			if(stage==0)

			{

				//does nothing in this stage

			}

			else if(stage==1)

			{

				if(left==true)

				{

					game.setSquareGraphic(cI, cJ, cX, cY, 0);

					game.setSquareGraphic(cI, cJ, cX-1, cY, 4);

					game.setCharacterLocation(cI, cJ, cX, cY, 0);

					game.setCharacterLocation(cI, cJ, cX-1, cY, 1);

					cX = cX-1;

					repaint();

				}

			}

		}

		

		else if(key==e.VK_RIGHT)

		{

			if(stage==0)

			{

				//does nothing in this stage

			}

			else if(stage==1)

			{

				if(right==true)

				{

					game.setSquareGraphic(cI, cJ, cX, cY, 0);

					game.setSquareGraphic(cI, cJ, cX+1, cY, 4);

					game.setCharacterLocation(cI, cJ, cX, cY, 0);

					game.setCharacterLocation(cI, cJ, cX+1, cY, 1);

					cX = cX+1;

					repaint();

				}

			}

		}

		

		if(key==e.VK_DOWN)

		{

			if(stage==0)

			{

				titleSelect = 224;

				repaint();

			}

			else if(stage==1)

			{

				if(down==true)

				{

					game.setSquareGraphic(cI, cJ, cX, cY, 0);

					game.setSquareGraphic(cI, cJ, cX, cY+1, 4);

					game.setCharacterLocation(cI, cJ, cX, cY, 0);

					game.setCharacterLocation(cI, cJ, cX, cY+1, 1);

					cY = cY+1;

					repaint();

				}

			}

		}

		

		if(key==e.VK_UP)

		{

			if(stage==0)

			{

				titleSelect = 192;

				repaint();

			}

			else if(stage==1)

			{

				if(up==true)

				{

					game.setSquareGraphic(cI, cJ, cX, cY, 0);

					game.setSquareGraphic(cI, cJ, cX, cY-1, 4);

					game.setCharacterLocation(cI, cJ, cX, cY, 0);

					game.setCharacterLocation(cI, cJ, cX, cY-1, 1);

					cY = cY-1;

					repaint();

				}

			}

		}

		

		if (key==e.VK_SPACE)

		{

			if(stage==0)

			{

				if(titleSelect==192)

				{

					try

					{

						game = new MapDrawer();

						stage++;

						repaint();

					}

					catch(Exception error)

					{

						System.out.println(error);

					}

				}

				else if(titleSelect==224)

				{

//					// implement file open dialog

				}

			}

			else if(stage==1)

			{

				//call menu

			}

			else if(stage==2)

			{

				

			}

		}

	}

	

	public void keyReleased(KeyEvent e)

	{

		//empty currently, will need stuff added for movement

	}

	

	

}
```


I'm looking for constructive criticism and once again any and all help is appreciated.  If I can get this up and going again I'm going to try to make it a open source game and see where it goes.

---

### Post by dwhitney67 on 2007-09-03
What's the problem you are having?  If you are looking for a peer review of your code, then sorry, I have better things to do.

---

### Post by Xzallion on 2007-09-03
It won't compile, I have various problems with the way files reference one another, and It needs some help.  I understand if you don't have the time, I was hoping someone with some free time would help me on it, pointing out things here and there or just give me some examples of what I did wrong and help me fix them.

---

### Post by dwhitney67 on 2007-09-03
Ok, it won't compile.  It would be extremely helpful if you would post the output generated when you compile using javac, and how you are compiling.

---

### Post by Xzallion on 2007-09-03
OK, I feel really stupid on this but I realized that it wasn't compiling in Eclipse becuase I hadn't set it to compile using JDK 6.0.  Now it compiles and loads up to the main menu screen I had set up for it, but won't accept input. So now its just mistakes in the programming logic I'm trying to track down.

but in case it helps, I am using Eclipse 3.2.2 and am running the program by selecting the RPG file and right clicking, and selecting run as>java applet.  It originally was designed to run in an applet and I never got it to work outside of JBuilder.


Edit:  Okay to clarify I really don't know what all is wrong with it, and am just looking for help.  But I'm going to get off here for a while and fiddle with it , and will check back later.

---

### Post by Tomosaur on 2007-09-03
> **Xzallion said:**
> OK, I feel really stupid on this but I realized that it wasn't compiling in Eclipse becuase I hadn't set it to compile using JDK 6.0.  Now it compiles and loads up to the main menu screen I had set up for it, but won't accept input. So now its just mistakes in the programming logic I'm trying to track down.

but in case it helps, I am using Eclipse 3.2.2 and am running the program by selecting the RPG file and right clicking, and selecting run as>java applet.  It originally was designed to run in an applet and I never got it to work outside of JBuilder.


Edit:  Okay to clarify I really don't know what all is wrong with it, and am just looking for help.  But I'm going to get off here for a while and fiddle with it , and will check back later.

As someone else said - we'll be better able to help you if you just paste the output of the javac command - OR, since you're using Eclipse, select the 'problems' tab for each source file, and copy and paste them here. Eclipse can also sometimes fix your problems - just right-click the problem and select quick-fix. Be careful though, because Eclipse is stupid and sometimes does something unexpected when you use this method.

The best way by far (in my opinion anyway) is to create debugging lines in your code (I usually just print stuff to the terminal if I'm trying to isolate weird behaviour - like 'This is line 540 in MyClass.java', or print a stack-trace or something. This helps you find non-fatal bugs which will help you track down the points of failure in the program logic. For example, if you suspect some if-statement is failiing when you know it should be passing, then just stick a System.out.println("Passed!") line immediately inside the if-block, and you'll know if it's working or not, and thus whether the problem lies elsewhere. Once you've tracked it down, you can fix the problem. For small projects like this game, however - you may not find this necessary - I only use this technique when I'm working on something with lots of different source files and thousands of lines of code - because it can be a pain in the backside trying to find the exact portion of code you suspect is causing the issue.

Of course, if you use that technique, you have to remember to clean the code up to remove such lines.

So anyway - post any errors or whatever you're getting - we should  be able to interpret the errors and help you fix them.

Also, people may be more willing to download and compile your code if you just create a .tar.gz archive file - you should be able to attach it to your post. Copying and pasting source code is just annoying.

---

### Post by samjh on 2007-09-03
> **Xzallion said:**
> Now it compiles and loads up to the main menu screen I had set up for it, but won't accept input. So now its just mistakes in the programming logic I'm trying to track down.

So it doesn't accept input?

In the portion of your code that deals with inputs, put some lines like ```
System.out.println(key)
```so you can see if it is actually detecting your keyboard inputs, and whether it is detecting the correct input.

That will be your best starting point, if you don't know how to use the debugger.

---

### Post by nitro_n2o on 2007-09-03
ok great, in terms of formatting your code is a big mess. If you've uploaded some well formatted readable files that would've helped greatly. 
I'd say don't wait for someone to solve your homework, because it's unlikely that someone will solve it for you! 
But, everybody can help.. try to get to a point where you can ask specific questions and you'll get solutions. Especially that we don't know what exactly what is that you trying to do 

have fun

---

### Post by Xzallion on 2007-09-03
Thanks for the help Tomosaur and Samjh, I will try adding some debugging lines and try to determine if its accepting input, and post my problem messages from eclipse here in a little bit.  I actually managed to finally track down and fix the errors in the square file last night after staring at my old code for three weeks trying to figure it out.  I will edit the first post and change it to a .tar.gz file here in a few minutes.

nitro_n20, this isn't my homework.  It was a homework assignment in my high school class that I wanted to continue working on.  But your right I do need to clean up the code, but every time I have tried I have caused more errors then when I started just trying to clean up the code.  I have let this code sit around too long and while I know more about correct formating and better ways to implement things in the code, I need to fix some of whats there and well I got in over my head back in high school and now I'm just so lost in it that I don't know exactly where to begin working on it again.

It would take a lengthy post to explain what each part of the program is trying to do, but if that would help I can go through my old design documents and see if I can explain the logic of this mess.

Edit: Due to a mess up on my end, I just lost what work I did last night and today, so It will be sometime tomorrow before I can post my .tar.gz file and I have found some specific problems, which I will be asking how to fix when I get it back to where it was.

---

