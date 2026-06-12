---
title: "C++ Timing Problem"
date: 2011-06-19
forum: Programming Talk
---

### Post by Ibrahim mufeed on 2011-06-19
Hi all,

I am facing a problem for the past two days, and it makes me sick. I am trying to make my C++ program to count number of goals my team score during one minute, and then write the result on an external file. And make the counter = zero again, and start counting number of goals for the next minute. etc.

The counter used to work just fine and I believe it is very logical, but once I added the timing, by subtracting the old time from the new time (TimeNew - TimeOld)and then the if(result%60 ==0) I write the goals counter to the file. The program always write ZERO and does not see the correct value for the goal counter.

```

int iGoalCounter = 0;
time_t tOut = time(0);//old time
while( WM->getPlayMode() != PM_TIME_OVER  && bContLoop )//while game running
{
      time_t t = time(0);//new time
      int seconds = t - tOut;          
      
      if(WM->getPlayMode() == PM_GOAL_LEFT)//we scored a goal
      {         
          iGoalCounter += 1;          
          while(WM->getPlayMode() == PM_GOAL_LEFT)
          {
              //Do nothing
          }
      }
      cout<<endl<<endl<<"IGOALCOUNTER AFTER ADDITION = "<<iGoalCounter<<endl<<endl;//this print the correct value of the counter!!
      int temp = iGoalCounter;
      if(seconds % 60 == 0)//if one minute passed, write data to file.
      {
        cout<<endl<<endl<<"iGoalCounter  = "<<iGoalCounter<<endl<<endl;//This prints ZERO always!! HERE IS THE PROBLEM
        ofstream outFile;
        char outputFilename[] = "input.txt";
        outFile.open(outputFilename, ios::out);
        if (!outFile)
        {
            cerr << "Can't open output file " << outputFilename << endl;
            exit(1);
        }        
        outFile<<temp;//iGoalCounter;
        outFile.close();
        iGoalCounter = 0;
        tOut = time(0);        
      }
}

```

It does not make any sense, I wish if anyone can help me.

Have a good time.
Ibrahim

---

### Post by dwhitney67 on 2011-06-19
In the future, I would suggest that you experiment with simpler code before plopping test code into your production code.  Not only will you be able to focus on the problem, but should you have any issues and decide to post on this forum, you can post minimal code.

Here's a trivial program that may help you:
```

#include <ctime>
#include <unistd.h>
#include <iostream>

int main(int argc, char** argv)
{
   int period = atoi(argv[1]); // should have better error checking; atoi() is not safe

   time_t start = time(0);

   while (true)
   {
      time_t now = time(0);

      if (now - start == (period - 1))
      {
         std::cout << period << " seconds have elapsed." << std::endl;
         start = now;
      }
      else
      {
         std::cout << "Delaying for 1 second..." << std::endl;
         sleep(1);
      }
   }
}

```
The period should be greater than 0, but I did not place any error checking in the code.

---

### Post by Ibrahim mufeed on 2011-06-19
Thank you for the advice. However, in my case I needed to show where the exact problem is because the timing was working just fine but the problem is; the variable iGoalCounter stores the count, let's say for one minute it we score 5 goals. So the iGoalCounter is 5, but when the current minute finishes and it is time to write the data to file, the value of the counter [iGoalCounter] is zero inside the [if(seconds % 60 == 0)] scope!!! 

This is the problem!

Thank you :)

---

### Post by dwhitney67 on 2011-06-19
> **Ibrahim mufeed said:**
> ... So the iGoalCounter is 5...

Have you verified this?  iGoalCounter is only incremented when a certain condition arises.  Please verify that you are incrementing the counter.

EDIT:  I just re-read your code (it is difficult to read).  I would have to guess that you are resetting iGoalCounter somewhere else within your code, or you are trampling on the data with some other operation.  It would be helpful to know what getPlayMode() is doing.

Also, simplify this code:
```

      int temp = iGoalCounter;
      if(seconds % 60 == 0)//if one minute passed, write data to file.
      {
        cout<<endl<<endl<<"iGoalCounter  = "<<iGoalCounter<<endl<<endl;//This prints ZERO always!! HERE IS THE PROBLEM
        ofstream outFile;
        char outputFilename[] = "input.txt";
        outFile.open(outputFilename, ios::out);
        if (!outFile)
        {
            cerr << "Can't open output file " << outputFilename << endl;
            exit(1);
        }        
        outFile<<temp;//iGoalCounter;
        outFile.close();
        iGoalCounter = 0;
        tOut = time(0);        
      }

```
Try something like:
```

      if(seconds % 60 == 0)  //if one minute passed, write data to file.
      {
        cout << endl<< endl << "iGoalCounter  = "<<iGoalCounter << endl <<endl;

        ofstream outFile("input.txt");

        if (!outFile)
        {
            cerr << "Can't open output file " << outputFilename << endl;
            exit(1);
        }

        outFile << iGoalCounter;

        iGoalCounter = 0;

        tOut = t;        
      }

```

---

### Post by Ibrahim mufeed on 2011-06-19
Yes, I verified it by using cout statements and the counter works fine. Before it enters the if(1 min passed) scope it prints let's say 2, and once it is inside the new scope it prints zero!!

---

### Post by dwhitney67 on 2011-06-19
> **Ibrahim mufeed said:**
> Yes, I verified it by using cout statements and the counter works fine. Before it enters the if(1 min passed) scope it prints let's say 2, and once it is inside the new scope it prints zero!!

I edited my previous post; can you please answer what getPlayMode() is doing?

---

### Post by dwhitney67 on 2011-06-19
I bet I know what the problem is... you are pounding the CPU with your while-loop.  The condition "seconds % 60 == 0" is probably true quite often, and thus the iGoalCounter is repeatedly (re)set to zero.

You should avoid checking if 60 seconds has elapsed at every opportunity.  Setup a timer, such that when it expires, you can be notified to perform a certain task (ie. capture the goal counter).

---

### Post by Ibrahim mufeed on 2011-06-19
First of all, I would like to thank you for your help :) . 

This is a soccer game, and this code snippet is from the coach of my team. WM->getPlayMode(), here the coach is asking the World Model about the current situation of the running match. So when:
```
if(WM->getPlayMode() == PM_GOAL_LEFT)
``` 
it means that my team scored a goal. And the:
```
while(WM->getPlayMode() == PM_GOAL_LEFT)//Do nothing
```
it is added to force the coach NOT to increment the iGoalCounter more than once each goal we score at a time.

But let me CONFIRM to you, that the iGoalCounter works fine and it is NOT USED at all any elsewhere. 

This is why I am saying it does not make any sense!

To overcome this problem, I made a new counter k = 0 out of the loop. and every time k +=1; and if(k%600)//one minute passed and it worked fine!! [at least so far].

```

int k = 0;
int iGoalCounter = 0;
while(game not finished)
{
   k++;
   if(we scored)
   {
      iGoalCounter += 1;
   }
   if(k % 600 == 0)
   {
      write to file iGoalCounter;
      k+=30;//to compensates the time spent while writing the file.
      iGoalCounter = 0;
   }
}

```

I wish if we can find an explanation for that problem!

Have a good time :-)

---

### Post by dwhitney67 on 2011-06-19
EDIT.  The code I posted will not work.  I will look into an alternate solution.

---

### Post by Ibrahim mufeed on 2011-06-19
My new method, using the k counter without the time, it does not work fine since it is not accurate at all. I'm still looking for a solution. 

Thank you.

---

### Post by Petrolea on 2011-06-19
> **Ibrahim mufeed said:**
> My new method, using the k counter without the time, it does not work fine since it is not accurate at all. I'm still looking for a solution. 

Thank you.

Of course it isn't accurate, the execution time of a loop depends on computer speed. You are forced to use time (k will be 600 within a microsecond).

---

### Post by Ibrahim mufeed on 2011-06-19
@Petrolea: Yes you are right, but in my case; it used to take 1 minute till the k is equal to 600. But after a period of time that changes.

@All: I guess that comment number 7 helped me to figure out the reason behind this problem. I tried to use [sleep()] inside the IF statement and outside it, this way it does write the correct value of iGoalCounter, but the new problem is; it keeps updating the file very often [in less than one minute] so overwrites the correct value. Currently I am trying to use different sleep values to see if anyone would work correctly.

Thanks.

---

### Post by Ibrahim mufeed on 2011-06-19
Finally it is solved. I think I solved it by adding one sleep statement in the beginning of the big while loop [while(match not finished)].

```

int iGoalCounter = 0;
time_t tOut = time(NULL);
while( WM->getPlayMode() != PM_TIME_OVER  && bContLoop )
{
   sleep(1);
   time_t t = time(NULL);
   int seconds = t - tOut;          
    ....

```

I made it in the production version now for test, by tomorrow I will confirm if it is working fine. Hope so!

Thanks all.

---

### Post by dwhitney67 on 2011-06-19
That won't necessarily do the trick; now your game engine will suffer (unless it is in a separate thread).

---

### Post by Ibrahim mufeed on 2011-06-20
Hi, left the match running since last night and I am happy to confirm that it is running correctly till now. The timing is just perfect and no delays happen at the mean time the correct counter iGoalCounter value is being written to the file.

@dwhitney67: Thank you so much for your help and suggestions. Regarding your last comment; every player is running on a separate thread and so the coach. I noticed no changes/problems happened [at least so far].

Have a good time :-)

---

