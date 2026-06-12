---
title: "GameLand Java Code"
date: 2011-12-19
forum: New to Ubuntu
---

### Post by KittyExpresso on 2011-12-19
Alright, I am completely new to the java code and recently all my files have been deleted so I had to start this lab assignment from scratch again >.<
 
Here's my code:
 
import java.util.*;
import java.io.*;
 
public class game3 {
 
    private int dice1, dice2, spot1, spot2, dicetotal, turn = 1;//declares ints
    String name1, name2;//declares strings
    Scanner fred = new Scanner(System.in);//makes scanner
 
    public void Begin() {//makes method to take names and such, basically sued to start the game.
        System.out.println("game time");
        System.out.println("name 1");
        name1 = fred.next();
        System.out.println("name 2");
        name2 = fred.next();
    }
 
    public void roll() {
        int dice1, dice2;//initializes dice 1 2 
        Random number = new Random();//makes new number generator
        dice1 = number.nextInt(6) + 1;//creates random number
        dice2 = number.nextInt(6) + 1;//creates random number
        dicetotal = dice1 + dice2;
    }
 
    public void Moving() {//the method that runs the game
        while (spot1 < 100 && spot2 < 100) {//while the players are still playign it runs
            if (spot1 >= 0 && turn == 1) {//this while is a bunch of cases for the dice roll, and whatever one applies to it it does.
                this.roll();
                if (dicetotal == 2 || dicetotal == 12 && turn ==1) {//stops turn
                    turn = 2;
                } else 
                    if (dicetotal == 7 && turn == 1) {
                        spot1 = spot1 - 7;
                        if(spot1 <= 0){
                            spot1 = 0;
                            turn = 2;
                        }
 
                    } else 
                        if ((spot1 + dicetotal) >= 100 && turn == 1) {//determines a winner
                            System.out.println("player one wins");
                            spot1 = spot1 + dicetotal;
                            turn = 2;
 
                        } else 
                            if ((spot1 + dicetotal) == spot2 && turn == 1) {//determines if someone goes back
                                spot2 = 0;
                                spot1 = (spot1 + dicetotal);
                                turn = 2;
 
                            } else 
                                if (dicetotal != 2 && dicetotal != 7 && dicetotal != 12 && turn == 1) {//moves normally
                                    spot1 = spot1 + dicetotal;
                                    turn = 2;
                                }
 
System.out.println("player 1 is now at " + spot1);//prints out where the player is back at the end of the turn
turn = 2;
         if (spot2 >= 0 && turn == 1) {//this while is a bunch of cases for the dice roll, and whatever one applies to it it does.
                this.roll();
                if (dicetotal == 2 || dicetotal == 12 && turn ==1) {//stops turn
                    turn = 1;
                } else 
                    if (dicetotal == 7 && turn == 1) {
                        spot2 = spot2 - 7;
                        if(spot2 <= 0){
                            spot2 = 0;
                            turn = 1;
                        }
 
                    } else 
                        if ((spot2 + dicetotal) >= 100 && turn == 1) {//determines a winner
                            System.out.println("player two wins");
                            spot2 = spot2 + dicetotal;
                            turn = 1;
 
                        } else 
                            if ((spot2 + dicetotal) == spot2 && turn == 1) {//determines if someone goes back
                                spot2 = 0;
                                spot2 = (spot2 + dicetotal);
                                turn = 1;
 
                            } else 
                                if (dicetotal != 2 && dicetotal != 7 && dicetotal != 12 && turn == 1) {//moves normally
                                    spot2 = spot2 + dicetotal;
                                    turn = 1;
                                }
 
}
System.out.println("player 2 is now at " + spot2);//prints out where the player is back at the end of the turn
turn = 1;
} 
}
}
}
 
 
My friend went in and added the comments, pardon if they bug you. I can honestly say that I have no idea how to get the game to run and print out feedback and results, I know that it compiles in BlueJ but i don't know how to get results. Thanks for any help ^-^

---

### Post by oldos2er on 2011-12-19
> **KittyExpresso said:**
>  I had to start this lab assignment from scratch again 

Good luck with your homework, sorry we can't help you with it. Closed.

---

