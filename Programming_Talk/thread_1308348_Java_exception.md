---
title: "Java exception"
date: 2009-10-31
forum: Programming Talk
---

### Post by hyperAura on 2009-10-31
hi guys.. im writing a small board game but im gettin an exception which i cannot understand..

i have three classes disc, board and test..

board is an array of disc objects.. the classes are as follows

public class Disc {

    int colour =0;
    
}//disc class



public class Board {

     Disc [][] board = new Disc[8][8];
     
    void initialize()
    {
        //Clear all positions
        for (int x=0; x<8; x++)
            for (int y=0; y<8; y++)
                board[x][y].colour = 0;

        //Set starting positions for white
        board[3][3].colour = 2;
        board[4][4].colour = 2;

        //Set staring positions for black
        board[4][3].colour = 1;
        board[3][4].colour = 1;
    }//initialise

    void printBoard()
    {
        for (int x=0; x<8; x++)
        {
            for (int y=0; y<8; y++)
            {
                System.out.print(" ");
                System.out.print(board[x][y].colour);
            }
         System.out.println();
        }
    }//print

}//Board class


public class test {

    public static void main (String [] args)
    {
     Board Game;

     Game = new Board();

     Game.initialize();

     Game.printBoard();
    
    }

}//test class



The exception i get is the following:

"Exception in thread "main" java.lang.NullPointerException
        at Board.initialize(Board.java:19)
        at test.main(test.java:18)
Java Result: 1
BUILD SUCCESSFUL (total time: 0 seconds)"

Btw im using Netbeans IDE..

---

### Post by 0cton on 2009-10-31
the problem is that disc is a class
when you do Disc [][] board = new Disc[8][8];
it makes an disc array board for 8*8
but it does not create a new Disc class
why you are using a disc class when it has only an int color (you could do
int[][] color=new int[8][8]
anyway to fix it you must create a new Disc for each index
in other words before line 19
for(int i1=0;i1<board.length;i1++){
   for(int i2=0;i2<board[i1].length;i2++){
      board[i1][i2]=new Disc();
   }
}
You need to understand the difference primitive types and objects
when you do int i;
i will be by default 0; or in some cases a random value (even though java forces you to initialize it before using it)
when you do
Disc c;
c is by default null; (a null reference) so i you do c.color it doesn't exist since is null
you must do c=new Disc(); first to create a new disc object and return it's reference address.
if you don't create a constructor a default one will be created.
edit using my code above you don't need to initialize they would be by default 0 . still why you use a class i don't see since your class has only a primitive value use directly the int. (an int array)
also you made int color=0 inside disc. why you need initialize to set them again at 0? <.<
an int[][] board=new int[8][8] will suit you perfectly!

---

### Post by hyperAura on 2009-10-31
thnx a lot this helped me get the point of my problem..
this code here is just the beginning thus why there are no methods in the disc class.. i assumed that it is going to be a bit complicated and inefficient if i just write one class for the whole thing.. :)
thnx again..

---

### Post by 0cton on 2009-10-31
You are welcome also do edit the title to [Solved] It will help people who try to help know not to come in this thread, also maybe people who search for help to find answers :P
I once went to page 2 and found a thread and when i opened it it was solved just saying better if you could add it in the title (not only you all people but nobody seems to follow this :P)
Also you can come on irc on freenode.net (sudo apt-get xchat) there is already freenode in the servers list register a nick and join ##java many people online most of the time and can help you :P
Good luck programming!

---

### Post by hyperAura on 2009-10-31
thnx for the tip again..:)

---

