---
title: "timing problem"
date: 2009-07-21
forum: Programming Talk
---

### Post by freakinjonathan on 2009-07-21
Hello I write code for robots using c code. I have a program that is suppose to, based on sensor input, do either of two things. 

```
while(1)
		{
			sleep(0.1);
			if(sensor==success)
			{successful();break;}

			if(sensor==fail)
			{
				for (x=1;x<9999;x=x+1)//every 15 counts is about 2 seconds on the processor(yes the same processor is always used!)
				{
					if(x/15<x)
					{failure();break;}

				}
			}	
			
		}
```

It is suppose to count a timer that counts up to a user specified amount, and if the sensor doesn't equal a certain value by the end of the countdown it should be able to "know" that and continue the program. 

assume successful(), failure(), and success fail are declared. Also assume I'm not the most experienced coder.

---

### Post by dwhitney67 on 2009-07-21
I assume you are programming under Linux vs. M$.  Thus one thing that sticks out is the sleep() parameter.  You are passing a floating point number, where instead, the C Library API indicates that it should be an integer that represents the number of seconds.

Perhaps you meant to use usleep()??

If 'sensor' can only have two states, 'success' or 'fail', then there really is no need to have the if-conditional checking for 'fail'.  If you determine that 'sensor' is not equal to 'success', just implement your delay.

And as for this statement:
```

if(x/15<x)

```
when do you think it will ever be false?  I believe it will always be true.  The left hand side will always be 0 for x=[1,15), 1 for x=[15,30), 2 for x=[30,45), etc., whereas the right hand side 'x' will be 1,2,3,... .  Thus what is the point of having the conditional statement?

P.S.  Try to be consistent with your use of the {} brackets and indentation.  Using tab-spaces to indent, IMO, blows.


P.S.S.
Perhaps something like this would work for you:
```

const unsigned int MAX_FAILURES_ALLOWED = 15;

unsigned int failureCount = 0;

while (sensor == FAIL && failureCount < MAX_FAILURES_ALLOWED)
{
   ++failureCount;
   sleep(2);
   failure();
}

if (failureCount == MAX_FAILURES_ALLOWED)
{
   /* grave error */
}
else
{
   /* all ok */
   successful();
}

```

---

### Post by freakinjonathan on 2009-07-21
Thank you. That simplifies things. If you want to know more We are using a modified version of C. It's called Interactive C. Though pretty much any C code will compile and run. The sleep function is included and extra methods ex. "ao()" will turn off all motors. The 15 was suppose to divide the number since every 15 counts is about 2 seconds and you would be able to just put the amount of seconds you want. I didn't really think about it as long as it had the basic functionality. I am 16 and I program the robots and participate/compete in botball. More info is on botball.org.

---

