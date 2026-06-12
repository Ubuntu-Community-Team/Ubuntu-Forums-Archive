---
title: "code for a friend"
date: 2007-12-18
forum: Programming Talk
---

### Post by PToros on 2007-12-18
Code for a friend

//Dan Sanchez
//Bowling.java
//Object class for bowling.
//
import java.util.Random;
public class Bowling
{
    public int score = 0, throwsleft = 0, hit = 0, left = 0, number =
 0, 
frame = 0;
    /*Constructor.
     *pre: none
     *post: A bowling object is created.*/
    public Bowling(int pnumber)
    {
        score = 0;
        number = pnumber;
    }
    /*Allows bowler to play the frame.
     *pre: Bowling object initialized.
     *post: Player gets points based on performance.*/
    public void playFrame(int framenum)
    {
        frame = framenum;
        System.out.println("Frame "+frame+", Player "+number+"'s
 turn.");
        Random rand = new Random();
        throwsleft = 2;
        hit = 0;
        left = 10;
        while(throwsleft>0)
        {
            hit = rand.nextInt(left+1);
            left = left - hit;
            System.out.println("Player "+number+" hit "+hit+" pins!");
            if(hit==0)
                System.out.println("Gutterball!");
            if(left==0)
            {
                if(throwsleft==2)
                {
                    System.out.println("Strike! Player "+number+" gets
 20 points!");
                    score = score + 20;
                    throwsleft = 0;
                }
                else
                {
                    System.out.println("Spare! Player "+number+" gets
 15 points!");
                    score = score + 15;
                    throwsleft = 0;
                }
            }
            else
            {
                if(throwsleft==2)
                    System.out.println("Player "+number+" has "+left+"
 pins left.");
                else
                {
                    hit = 10 - left;
                    score = score + hit;
                    System.out.println("Player "+number+" gets "+hit+"
 points.");
                }
                throwsleft = throwsleft - 1;
            }
        }
        System.out.println("Player "+number+"'s current score:
 "+score);
        System.out.println();
    }
    /* Returns player's score.
     *pre: player object is initialized
     *post: score is returned*/
     public int returnScore()
     {
        return(score);
     }
}


//Dan Sanchez
//RunBowling.java
//Client code for bowling.
import java.util.Scanner;
public class BowlingClient
{
    public static void main(String[]args)
    {
        int players = 0, framenum = 1, pnumber = 1, loop = 0, max = 0,
 maxp = 
1, score = 0;
        Scanner scan = new Scanner(System.in);
        while(loop==0)
        {
            System.out.println("It's time to bowl! How many will be
 bowling 
today? (max 4)");
            players = scan.nextInt();
            if(players>0&&players<5)
                loop = 1;
            else
                System.out.println("That is an invalid entry.");
        }
        Bowling p1 = new Bowling(1);
        Bowling p2 = new Bowling(2);
        Bowling p3 = new Bowling(3);
        Bowling p4 = new Bowling(4);
        System.out.println(players+" player(s), huh? Well, let's
 bowl!");
        while(framenum<=10)
        {
            if(pnumber==1)
            {
                p1.playFrame(framenum);
                if(players>1)
                    pnumber=2;
            }
            if(pnumber==2)
            {
                p2.playFrame(framenum);
                if(players>2)
                    pnumber=3;
                else
                    pnumber = 1;
            }
            if(pnumber==3)
            {
                p3.playFrame(framenum);
                if(players>3)
                    pnumber=4;
                else
                    pnumber = 1;
            }
            if(pnumber==4)
            {
                p4.playFrame(framenum);
                pnumber = 1;
            }
            framenum = framenum + 1;
        }
        score = p1.returnScore();
        max = score;
        System.out.println("Player 1's score: "+score);
        if(players>1)
        {
            score = p2.returnScore();
            if(score>max)
            {
                max = score;
                maxp = 2;
            }
            else if(score==max)
                maxp = 0;
            System.out.println("Player 2's score: "+score);
        }
        if(players>2)
        {
            score = p3.returnScore();
            if(score>max)
            {
                max = score;
                maxp = 3;
            }
            else if(score==max)
                maxp = 0;
            System.out.println("Player 3's score: "+score);
        }
        if(players>3)
        {
            score = p4.returnScore();
            if(score>max)
            {
                max = score;
                maxp = 4;
            }
            else if(score==max)
                maxp = 0;
            System.out.println("Player 4's score: "+score);
        }
        if(maxp==0)
            System.out.println("It's a tie!");
        else
            System.out.println("Player "+maxp+" is the winner!");
    }
}

---

### Post by AZzKikR on 2007-12-18
There is something called Pastebin, you know?

---

