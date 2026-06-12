---
title: "Java Help (error with writes to external file)"
date: 2009-04-03
forum: Programming Talk
---

### Post by &#32 Greg on 2009-04-03
I'm a complete novice when it comes to programming Java. I've been trying to figure this out for a while because I've been bored, and, well, I failed.

```
//Greg
//craps.java
//A simple dice game

import java.util.Random;
import java.io.FileNotFoundException;
import java.io.*;
class craps
{
	
	static EasyReader io=new EasyReader();
	public static void main (String args[])
	{
		int money=250; //Money for nothing...
		int cont=0;
		int x=0;
		int bet;
		int a[]=new int[15];
		String b[]=new String[15];
		Random y=new Random();
		System.out.println("Hello. Welcome to the Craps table.");
		System.out.println("You start with $250 dollars. You may leave at any time.");
		System.out.println("Here are the rules... you win if you get a 7 or 11 the first roll, and lose if you get a 2, 3, or 12.");
		System.out.println("If you roll something besides those numbers, you roll again until you get that number again (for the win) or a 7 (for the loss)");
		while ((x!=1)&&(money>0))
		{
			System.out.println("Please enter a bet: ");
			bet=io.readInt();
			while (bet>money||bet<=0)
			{
				System.out.println("ERROR: ILLEGAL BET. ENTER A LEGAL BET");
				bet=io.readInt();
			}
			int die1=y.nextInt(6)+1;
			int die2=y.nextInt(6)+1;
			System.out.println("The first die showed a "+die1+" and the second showed a "+die2);
			int dietot=die1+die2;
			System.out.println("That means you rolled a... "+dietot);
			if ((dietot==7) || (dietot==11))
			{
				System.out.println("Congrats, you won.");
				money=money+bet;
				System.out.println("You now have $"+money);
			}
			else if ((dietot==2) || (dietot==3) || (dietot==12))
			{
				System.out.println("Sorry, you lost");
				money=money-bet;
				System.out.println("You now have $"+money);
			}
			else
			{
				int die3,die4,dietot2=0;
				while (dietot!=dietot2&&dietot2!=7)
				{
					die3=y.nextInt(6)+1;
					die4=y.nextInt(6)+1;
					System.out.println("The first die showed a "+die3+" and the second showed a "+die4);
					dietot2=die3+die4;
					System.out.println("That means you rolled a... "+dietot2);
				}
				if (dietot2==7)
				{
					System.out.println("Sorry, you lost");
					money=money-bet;
					System.out.println("You now have $"+money);
				}
				else
				{
					System.out.println("Congrats, you won.");
					money=money+bet;
					System.out.println("You now have $"+money);
				}
			}
			if (money>0)
			{
				System.out.println("Type 1 to walk, anything else to play again");
				x=io.readInt();
			}
		}
		String name;
		System.out.println("Enter your name");
		name=io.readLine();	
		name=io.readLine();	
		FileInputStream fin;
		try {
			fin = new FileInputStream (".top10");
			for (int qq=0;qq<10;qq++)
			{
				try {
					a[qq]=new DataInputStream(fin).readInt();
					}
				catch (IOException e)
				{
					System.out.println("ERROR 1");
				}
				try {
					b[qq]=new DataInputStream(fin).readLine();
					}
				catch (IOException e)
				{
					System.out.println("ERROR 2");
				}
			}
			a[11]=money;
			b[11]=name;		
			int i=0;
			int j;
			String k;
			while (i<11)
			{
				if (i==0||a[i-1]<=a[i]) {i++;} //If the two being compared are in order, it moves forward
				else
				{
					j=a[i];
					a[i]=a[i-1];
					a[i-1]=j; //Else, they switch...
					k=b[i];
					b[i]=b[i-1];
					b[i-1]=k;
					i--; //And the gnome steps back
				}
			}
			try {
				fin.close();
				}
			catch (IOException e)
			{
				System.out.println("ERROR 3");
			}
			}
		catch (FileNotFoundException ex) 
		{
			System.out.println("ERROR 4");
		}
      	FileOutputStream fout;		
		try
		{
		    // Open an output stream
		    fout = new FileOutputStream (".top10");
		    // Print a line of text
		    for (int ax=0;ax<10;ax++)
		    {
		    new PrintStream(fout).println (a[ax]);
		    new PrintStream(fout).println (b[ax]);
		    }
		    // Close our output stream
		    fout.close();		
		}
		// Catches any error conditions
		catch (IOException e)
		{
			System.err.println ("Unable to write to file");
			System.exit(-1);
		}
		System.out.println("Name Score");
  		for (int lm=0;lm<10;lm++)
  		{
  			System.out.println(b[lm]+" "+a[lm]);
		}
	}
}
```

This is my problem: The program runs, but the highscore doesn't work correctly.
The .top10 file starts with
0
null
0 
null
... (The pattern repeats so there are 10 scores and 10 names)
The output the first time is null 0 null 0 etc. without my (better) score in it. The output the next time it's run is null 0, ull 8061610006, ull 8061610006, etc... each time the letters drop, change to numbers, and the numbers expand. I get the feeling that this has something to do with the fact that when it writes to the text file, the number becomes a string. I'm not sure how to correct this though. Any possible help would be appreciated.

---

### Post by PaulM1985 on 2009-04-05
Hi Greg

I have taken you program and made some changes to it to try to get it working.  I think there may be a few things that you need to look at.

The first is that I don't think your program is finding your high score file.  I would recommend using the Scanner class from java.utils. to read the file and use

```
try
		{
		    fileReader = new Scanner(new File("Craps/top10.score"));
		}
	    catch (FileNotFoundException e)
		{
		    System.out.println("file not found");
		}
```
This way you can see if your file has been found.

Next, when you are reading the file to populate your arrays for score and scorer, I would use a while(fileReader.hasNext() && qq<10) rather than using a for-loop as this avoids problems when you come to the end of your file.

```
int qq = 0;
	    while (fileReader.hasNext() && qq<10)
		{
		    // This line takes the score
		    a[qq] = Integer.parseInt(fileReader.nextLine());
		    System.out.println(" score " + a[qq]);
		    // This line takes the scorer
		    b[qq] = fileReader.nextLine();
		    System.out.println("scorer file " + b[qq]);
		    qq++;
		}
```

There are still some other problems but I hope this starts you off.

Paul

---

