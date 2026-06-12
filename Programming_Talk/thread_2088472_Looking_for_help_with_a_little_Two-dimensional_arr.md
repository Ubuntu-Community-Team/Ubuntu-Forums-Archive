---
title: "Looking for help with a little Two-dimensional array game in C#"
date: 2012-11-26
forum: Programming Talk
---

### Post by Egonosaur on 2012-11-26
Hello there!

I'm working on a simple little two-dimensional array game "Sink the boat" in C#,
it is a little console application based on a little 4x4 coordinate-system where you choose where you want to shoot "place the asterisk", the target will be a random generated coordinate, when hit you will get a message which tells you it was a hit and tells on how many tries it took. I want the game to look like this in the console window:

      ```

  
 |1|2|3|4|
1|*
2|
3|
4|    *

NEW SHOT
ENTER X-coordinate: 3
Enter Y-coordinate:


```[B]
But my problem is I can't manage to[/B] [B]print out the coordinate system like I showed above.

[/B]Here is what I've managed to code prior to this problem:
```

using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;

namespace SinkTheBoat
{
    class Game
    {
        int x;
        int y;
        int varCount = 1;
        string target;
        string[,] gameBoard = new string[5, 4];
                                                

        public void TheGame()
        {
            string choice;
            Random rnd = new Random();

            do
            {
                Console.Write("Do you wish to play the game? Y/N: ");
                choice = Console.ReadLine();

                //the game code
                if (choice == "Y" || choice == "y")
                {
                    do
                    {
                        Console.Clear();
                        
                        Console.WriteLine("===Sink the boat===");
                        int randomTargetX = rnd.Next(5);
                        int randomTargetY = rnd.Next(5);
                        target = gameBoard[randomTargetX, randomTargetY];

                        
                        for (int i = 0; i < gameBoard.GetLength(0); i++)
                        {
                            
                            
                            for (int j = 0; j < gameBoard.GetLength(1); j++)
                            {
                                
                                Console.Write(gameBoard[i, j]);

                            }
                            
                        }

                        Console.WriteLine("\nNEW SHOT");
                        Console.Write("Enter the X-coordinate: ");
                        x = Convert.ToInt32(Console.ReadLine());
                        Console.Write("Enter the Y-coordinate: ");
                        y = Convert.ToInt32(Console.ReadLine());

                        gameBoard[x, y] = "*"; //places an asterisk

                        if (gameBoard[x, y] == target) //if target is hit
                        {
                            Console.WriteLine("\nCongratulations you sunk the boat!");
                            Console.WriteLine("You managed to hit the target in " + varCount + " tries.");
                            Console.WriteLine("\nPress any key to continue.");
                            Console.ReadKey();
                            break;
                        }
                        varCount++; //counts the tries

                    } while (gameBoard[x, y] != target);

                }

                //if the user writes N/n the game will quit
            } while (choice != "n" && choice != "N");
        }

    }
    class Program
    {
        static void Main(string[] args)
        {
            Game game = new Game();

            game.TheGame();

            Console.WriteLine("Press any key to continue..");
            Console.ReadKey();
        }
    }
}


```I'm very thankful for any tips/ideas/solutions regarding this problem or my programming.


//Peace, -E

---

### Post by Vaphell on 2012-11-26
I'd suggest splitting the code into functional parts, eg
- function that accepts user input and checks it validity
- function that performs the game logic and checks the hit/miss based on the input
- function that prints the board

modularized code makes it much easier to see the overaching design and isolate potential bugs


aren't strings used to save the state a bit of overkill? table of ints, chars or bools would do just fine.

---

### Post by Egonosaur on 2012-11-26
> **Vaphell said:**
> I'd suggest splitting the code into functional parts, eg
- function that accepts user input and checks it validity
- function that performs the game logic and checks the hit/miss based on the input
- function that prints the board

modularized code makes it much easier to see the overaching design and isolate potential bugs


aren't strings used to save the state a bit of overkill? table of ints, chars or bools would do just fine.


Thank you very much for your feedback! :) 
I will take your thoughts into consideration.

---

