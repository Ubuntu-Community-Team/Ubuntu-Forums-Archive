---
title: "Compiled c++ program won't start"
date: 2007-06-03
forum: Programming Talk
---

### Post by Faytz on 2007-06-03
I recently took up C++ and when I programmed a terminal tax program in Anjuta.
But when I compiled it and checked for errors, it compiled sucessfully but when I run it,the executable will not run at all.Any help?
In case you need the source code here it is
```
#include <iostream>
using namespace std;

int main()
{
  double amount;
  double tax;
  double taxpercent;
  char again;
	
  do{
  cout<<"\nPlease Enter a Dollar Amount: ";
  cin>> amount;
  cout<<"Please Enter Tax Percentage: ";
  cin>> taxpercent;
  tax = taxpercent * 0.01 * amount;
  cin.ignore();
  cout<<"Tax is: "<< tax << "\n" << "Total is "<< tax + amount <<"\n";
  cin.get();
  cout<<"Would you like to play again? (y or n): ";
  cin>> again;
  } while ( again == 'y');
}


```

---

### Post by WW on 2007-06-03
How did you try to run the program?  If you are in a terminal, don't forget that you must put **./** in front of the executable name.  For example, if the executable is called **main**, you woud type **./main** to run it:
```

$ ./main

```

---

### Post by codesplice on 2007-06-03
Your code looks good, so I don't think that's the issue.  What compiler are you using, and how are you trying to execute it?

---

### Post by Faytz on 2007-06-03
> **WW said:**
> How did you try to run the program?  If you are in a terminal, don't forget that you must put **./** in front of the executable name.  For example, if the executable is called **main**, you woud type **./main** to run it:
```

$ ./main

```

Thanks I never knew that!
This was originally programmed in Dev-C++ but then i wanted to make a linux port.

---

### Post by PandaGoat on 2007-06-03
Not to be picky, and this is quite irrelevant, but it is best to not use do...while loops.  Just use a while loop. And your call to istream::ignore seems pointless.

---

### Post by Wim Sturkenboom on 2007-06-04
> **Faytz said:**
> Thanks I never knew that!The reason is that the current directory is not in the search path of the OS. The is a security 'feature', preventing you form accidently running a program with a name of a normal command. E.g. You can write a program that wipes the whole user directory and call it *ls*.
If your current directory is in the searchpath and you run ls, it will execute that one instead of the normal ls.

> **PandaGoat said:**
> Not to be picky, and this is quite irrelevant, but it is best to not use do...while loops.  Just use a while loop.Is there a reason for that ?
A *do/while* loop will always execute once while a *while* loop will execute 0 or mnore time

---

### Post by PandaGoat on 2007-06-04
There is no need for it to execute at least once.  What if you didn't want it to execute at all?  While loops are much more clean and we can predict how they will act better.  It may not matter in this simple program, but it can in more complicated ones.

```

char again = 'y'; // It's best to assign variables when you declare them too

while(again == 'y')
{
}

```

I do not have a good link, but I found this which sums it up pretty well: [clicky](http://www.geocities.com/learnprogramming123/Clesson10.htm)

---

### Post by Wim Sturkenboom on 2007-06-04
I do not really see their points as a problem.

Further I wonder how an endless loop is implemented. *for( ; ; )* can not be used and neither can *while(1)*. You have to waste a variable which will probably be removed by the compiler during optimization.

---

### Post by WW on 2007-06-04
I agree with Wim.  There is nothing wrong with do-while loops.
> **PandaGoat said:**
> There is no need for it to execute at least once.  What if you didn't want it to execute at all?
Then you would not use a do-while loop.  A do-while loop is a loop that always executes at least once, and has the test for repeating the loop at the end.
> **PandaGoat said:**
> 
  While loops are much more clean and we can predict how they will act better.

The behavior of a do-while loop is clearly defined; it is just as "predictable" as a while loop.
> **PandaGoat said:**
> 
I do not have a good link, but I found this which sums it up pretty well: [clicky](http://www.geocities.com/learnprogramming123/Clesson10.htm)
The phrase "lack of control" in that link is vacuous and makes no sense.  I am unconvinced.

---

### Post by PandaGoat on 2007-06-04
It is best to stick with one loop and have a constant understanding of your program's logic than have to understand multiple ways of how your program operates.  It is best to standardize yourself with one loop, and while loops tend to do what you want more often.  Sometimes in more advanced programs you may not want something to always execute, this is mostly always the case for it makes your program run more logically. 
If you use while loops you do not have to worry about variables being assigned.  

Yes, in this case it does not really matter, but it will ease your brain with much larger code.  I'm not sure how to explain it if what I have said is not good enough without showing huge amounts of code.

> Further I wonder how an endless loop is implemented. for( ; ; ) can not be used and neither can while(1). You have to waste a variable which will probably be removed by the compiler during optimization.
Why can't you use While(true)  or for( ; ; )?  That link is only talking about converting do...while loops to while loops.

---

### Post by aks44 on 2007-06-04
I don't mean to be picky either, but I can't agree on that. ;)

> **PandaGoat said:**
> It is best to stick with one loop and have a constant understanding of your program's logic than have to understand multiple ways of how your program operates.  It is best to standardize yourself with one loop, and while loops tend to do what you want more often.
Huh? I guess we shouldn't use switch() either, as they're just a fancy way of writing if/else... blocks? Not to speak about falling through different cases...

My point being: use whatever language construct that fits best what you're trying to express. Sometimes it's while(), sometimes do/while(), sometimes exotic for() loops...
It's all a matter of readability, and do/while() is much more expressive in this very case than a while() using a preinitialised variable.

> **PandaGoat said:**
> Yes, in this case it does not really matter, but it will ease your brain with much larger code.
What will ease your brain is having a readable and maintainable code. As I said, if a particular construct is more expressive then it is the way to go.

If one is not able to correctly grasp the difference between while() and do/while() loops at first glance, how can he even expect to work on serious projects?

---

### Post by Wim Sturkenboom on 2007-06-05
> **PandaGoat said:**
> Why can't you use While(true)  or for( ; ; )?  That link is only talking about converting do...while loops to while loops.No, they say that a do/while is improper. And enxt they convert it to a while.
Further,  there is a chance that you enter the loop with unintitialized variables when using while(1) or for( ; ; ) and that's not 'done'. But OK, uninitialized variables are bad anyway.

Last I do have a constant understanding of my program. If I see a do/while, I know it will be executed at least once and if I see a while, I know it might not be excuted at all; so for me, that's more clea. In my opinion, there is a place where you use the one and a place where you use the other.

---

