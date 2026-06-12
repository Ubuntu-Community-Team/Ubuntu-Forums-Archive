---
title: "Blackjack game that goes to 33 - Java"
date: 2014-04-17
forum: Programming Talk
---

### Post by Kuuga on 2014-04-17
So I am new to java, and for a project I have to make a blackjack game that goes up to 33 instead of 21. As of now I only have the deck class with what I think it should have it in. I am sort of lost. Normally I am good with writing my own code, but since this is a group project that I am doing alone; I am feeling the pressure. I was wondering if I could get any guidance. I also have to make this program using the methods my teacher has taught us so far. Those are **comments**, **if statements**, **while loops**, **sentential values**, **comparing data**, **methods**, **classes/objects**, **constructors**, **accessors/mutators**, and **arrays**. I've been browsing the forums and I see that people use an ArrayList. Problem is that I cannot use an ArrayList, because he has not talked about that in class. If I do use it, points are deducted from my grade. Sucks right? So far here is my Deck class:
```
public class Deck
{
    // Attributes
    private String[] suits = {"Spade", "Hearts", "Clubs", "Diamonds"};
    private String[] values = {"2","3","4","5","6","7","8","9","10","Jack","Queen","King","Ace"};
    private int quit = -1;
    
    public Deck(String[] s, String[] v)
    {
        suits = s;
        values = v;
    }

// Mutators

    public void setSuits(String[] s)
        {
            suits = s;
        }
    
    public void setValue(String[] v)
    {
        values = v;
    }

// Accessors
    
    public String[] getSuits()
    {
        return suits;
    }
    
    public String[] getValue()
    {
        return values;
    }
    
// Additonal
    
    public void quitGame()
    {
        quit = -1;
    }
}


```

I still have to create the main class which I am in the process of doing now. When I get somewhere with it I'll update this post. Does the deck class I have look alright? Or should I add more to it? Thanks for reading.

---

### Post by dwhitney67 on 2014-04-17
Looksie here... [http://math.hws.edu/eck/cs124/javanotes4/c5/ex-5-5-answer.html](http://math.hws.edu/eck/cs124/javanotes4/c5/ex-5-5-answer.html)

---

### Post by Kuuga on 2014-04-18
Thanks for the reply but unfortunately the program can only consist of two classes. A deck class that has all the deck information in it and the main class that runs the program :/

---

### Post by dwhitney67 on 2014-04-18
Look, nobody comes up with silly requirements such as what you have presented, unless of course it originated from some professor... and hence you are asking for help in doing homework.  This contravenes the rules of the forum, and thus you should steer elsewhere to find a solution.

---

### Post by Iowan on 2014-04-18
From the [Posting Guidelines]("http://ubuntuforums.org/showthread.php?t=2158945"):
> While we are happy to serve as a resource for hints and for asking questions when you get stuck and need a little help, the Ubuntu Forums is not a homework service. Please do not post your homework assignments expecting someone else to do it for you. Any such threads will either be jailed or closed, and warnings or infractions may be issued.
You're welcome to ask for assistance with a problem. The forum rule about homework is to discourage posting the question(s) and (essentially) asking "What's the answer".

---

