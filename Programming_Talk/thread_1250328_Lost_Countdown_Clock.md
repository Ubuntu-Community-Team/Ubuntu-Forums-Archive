---
title: "Lost_Countdown_Clock"
date: 2009-08-26
forum: Programming Talk
---

### Post by NielsAMD on 2009-08-26
Hello,

You might have seen the TV show: LOST.
Now i wanted to make a clock that counted down from 108 to zero, just like in the series. 

I already tried to make a script in python but i had some problems, see the code below.
First problem, I don't know how to make the program wait for user input when n =< 4 and larger than 0. Second I don't know how to make the program check the code entered with the code that has to be entered (4 8 15 16 23 42).
Another problem is that because of the many print commands make it impossible to enter the code without pasting.
Any help / ideas on making this clock are appreciated. I also have Visual C++ for MS Windows.
Below i have typed some requirements the program has to have, and some ideas for improvement.


```
#Lost numbers countdown

import time


n=108


While n => 1:
    print n
    n -= 1
    time.sleep(60)  #Displays time left, substracts 1 from n every minute

While n < 1 and n > 0:
    print (n/60.0)
    n -= (1/60.0)
    time.sleep(1)   #Displays time left in seconds, when under one minute.
                    #Substracs 1/60th of a minute every second.
While n =< 4 >0:

                    #This would be the time when the numbers should be entered.
                    #Explained at post.
While n == 0:
    print "SYSTEM FAILURE"
    time.sleep(3)


```

Here are the requirements for the program:
- The clock has to count down from 108 to zero in exactly 108 minutes.
- The clock has to display the time left. Under a minute the time has to be displayed in seconds.
- The code (4 8 15 16 23 42) has to be entered to reset the clock back to 108, when timer hits 4 minutes remaining.
- When timer hits zero,  entering the code will no longer reset the timer and "SYSTEM FAILURE" must be displayed on the screen.

Ideas for improvement
- Adding sound
- Visual output, no command line showing time left, but a timer.

Remember, ALL ideas are welcome, even if it means using another programming language.

---

