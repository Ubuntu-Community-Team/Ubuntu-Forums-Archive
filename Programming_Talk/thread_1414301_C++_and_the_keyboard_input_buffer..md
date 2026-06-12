---
title: "C++ and the keyboard input buffer."
date: 2010-02-23
forum: Programming Talk
---

### Post by Jonas thomas on 2010-02-23
I'm studying for my midterm for my begineers C++ and I'm know I'm still having issues with this stupid input buffer stuff.

Conceptually, I understand whats going on in the book/class, but I'm still feeling real real uncomfortable with when to cin.ignore and when not to.  (My practise code is taking longer to debug than it should, so I feel I need to focus on this stuff a little more, before the test)

I guess what I'm looking for is the ultimately tutorial link that delves into the nuances of the keyboard input buffer of C++ and how you can screw it up. 

There is a huge amount hits to sift throw when you google, I thought someone my have a favorite link that helped them out with this topic.

What would also be interesting would be some sort of tie-in as to of how the hardware ties into the software(Way beyond what I need for the class, but I'm very curious about this stuff.)

Thanks,

JT

---

### Post by dwhitney67 on 2010-02-23
> **Jonas thomas said:**
> 
I guess what I'm looking for is the ultimately tutorial link that delves into the nuances of the keyboard input buffer of C++ and how 

You have to program defensively when accepting user input from the command line.  If you request a number, then the user enters a string, what are you going to do about it?  Similarly, if the user enters a mix of number and characters (eg. 123abc).

When reading in multiple values, the best bet is to use getline().  From there you can tokenize the values into their respective components, such as an int and a string, which hopefully are separated by a white-space.

The getline() also assists you in guarding against excessive data input; for instance, if the user decides to enter 4000+ characters, followed by a newline, then your application will be safe from buffer overruns (a lot of C++ programmers on this forum like to use C-style arrays!).

Anyhow, once you have gotten the input from the user, it can be tokenized using the stringstream buffer.  You can verify the stringstream at every stage to ensure that it got the correct data type you seek.

Of course, if you want to stick to using cin only, it also offers the capability to check for valid input.  If you detect bad input, then you want to clear the flags and then the input buffer.  Typically, the input buffer is terminated with a newline, thus you want to bleed all characters in the input buffer up to, and including, the newline.  Hence the ignore() function.  Give it a reasonable int value for the number of characters you want to gobble up, or the max size_t as provided by numeric limits.

General usage is:
```

while (true)
{
   // prompt for input

   // get input

   if (cin.good()) break;

   // error w/ user's input; clear stream, and try again
   cin.clear();
   cin.ignore(1024, '\n');
}

```
I've never tried it, but perhaps cin.ignore(1024) might work as well.  This version uses the default value of EOF when searching through the stream.

---

### Post by Jonas thomas on 2010-02-23
> **dwhitney67 said:**
> You have to program defensively when accepting user input from the command line.  If you request a number, then the user enters a string, what are you going to do about it?  Similarly, if the user enters a mix of number and characters (eg. 123abc).

No kidding.. The class hasn't reached a point where input requirements are totally bullet proofed.  It drives me nuts, dealing with stuff like
int a;
cin>>a;
I don't think I ever use anything like that outside of a class room setting.

My current preference in my homework assignments is to do something like this to bullet proof:

```


bool canLeaveNow=false;
int daysoff=0;
do
{
   cout<<"Please enter days off for employee#"<<employeeNum<<": ";
   cin.getline(inputLine2,255);
   if(1 != sscanf(inputLine2, "%d", &daysoff))	   
   {
       cout<< "Was expecting a numeric input!!\n Not >"<<inputLine<<"<"<<endl;
   }
   else
   {
       if (daysoff>=0)
       {
	  canLeaveNow=true;
       }
       else
	  cout<<"Please end a positive number"<<endl;
    }
}
while(canLeaveNow==false);
daysOffForEmployee[employeeNum]=daysoff;

```
I just worried that I'm going to brain lock on something really elemental, only having a pencil and paper in front of me..
Anyway... I went to look research cin.clear() that you mentioned and I stumbled on something that will help me prep for my exam.
[URL="http://augustcouncil.com/~tgibson/tutorial/iotips.html"]
http://augustcouncil.com/~tgibson/tutorial/iotips.html[/URL]

Anyway... Thanks...

---

### Post by dwhitney67 on 2010-02-23
It appears as if you took a C programming class before you took the C++ class.  sscanf()???

As for the link you posted, I'm not impressed.  The author of that 'stuff' made some errors... err, assumptions, that fails to make the code bullet proof.  For example (and I realize this is a snip of code):
```

  #include<limits> //for numeric_limits
  float fl;
  int bad_input;
  do{
    bad_input=0;
    std::cin >> fl;
    if(!std::cin)
    {
      bad_input=1;
      std::cin.clear();
      std::cin.ignore(std::numeric_limits<streamsize>::max(),'\n');
    }

  }while(bad_input);

```
This code would allow the user to enter "123abc", whereas one would think that this would be deemed to be erroneous input when expecting a float.

I wrote this code a while back (and tweaked it a bit this evening), which I hope is as close to being bullet-proof as possible:
```

#include <string>
#include <iostream>
#include <limits>

// helper function for getting input
//
template <typename T>
T getInput(const char* prompt)
{
   using namespace std;

   T input;

   while (true) {
      // prompt user and attempt to read input
      cout << prompt;
      cin  >> input;

      // check if valid input given; break from loop if so.
      if (cin.peek() == '\n' && cin.good()) break;

      // damn user gave bad input; let them know about it.
      cout << "Invalid input!  Try again...\n" << endl;
      cin.clear();
      do { cin.ignore(numeric_limits<streamsize>::max(), '\n'); } while (!cin);
   }

   return input;
}

// test code
//
int main(void)
{
   double      num  = getInput<double>("Enter a double number: ");
   std::string word = getInput<std::string>("Enter a single word: ");

   std::cout << "Your double num: " << num  << std::endl;
   std::cout << "Your word is   : " << word << std::endl;
}

```


P.S.  If you don't already have it bookmarked, this is one of the best sites for referencing the C++ API:
[http://www.cplusplus.com/reference/stl/](http://www.cplusplus.com/reference/stl/)

---

### Post by Jonas thomas on 2010-02-24
> **dwhitney67 said:**
> It appears as if you took a C programming class before you took the C++ class.  sscanf()??? 
[/code]  Actually, many many moons ago I did.. To be honest.. I did some surfing for what made sense to me and I used it.  I think I like your solution better. Btw.. The class hasn't reached templated functions but they sure are cool.

> 
P.S.  If you don't already have it bookmarked, this is one of the best sites for referencing the C++ API:
[http://www.cplusplus.com/reference/stl/](http://www.cplusplus.com/reference/stl/)

I think that's probably one of the greenest tree's in the forest of information out there. My googling probably lands me there 70%+ of the time.  (Sometimes I find that site a little too concise.) If you don't already sort of understand it, it can be a bit overwhelming.

Just curious, I noticed you used "using namespace std" in your template but chose the "std::" within the main().  I understand what's going on, I'm just curious why you didn't go with using namespace std within the main().  Preference or a reason?

---

### Post by MindSz on 2010-02-24
> P.S. If you don't already have it bookmarked, this is one of the best sites for referencing the C++ API:
[http://www.cplusplus.com/reference/stl/](http://www.cplusplus.com/reference/stl/)

+1 ... good site for C too!

---

### Post by dwhitney67 on 2010-02-24
> **Jonas thomas said:**
> 
Just curious, I noticed you used "using namespace std" in your template but chose the "std::" within the main().  I understand what's going on, I'm just curious why you didn't go with using namespace std within the main().  Preference or a reason?

I added an additional query for input in the post I provided; earlier, with just the one query for a double value, I only needed to use std:: twice, for the cout and endl.  It wasn't worth importing the entire namespace for just that.  Basically, it boils down to one's preference.

---

### Post by Jonas thomas on 2010-02-27
I like your templated bullet proof solution. I like to understand what's going on before I adapt it.
regarding:
```

do { cin.ignore(numeric_limits<streamsize>::max(), '\n'); } while (!cin);

```
prior to this there was bad input. 
clear was invoked to get rid of the error to accept future cin
We're entering a loop that will clear out the input buffer to the max width of the buffer as defind in <limits> while (!cin)
It's the while (!cin) that I'm a little fuzzy on as to whats  going on.
I think what happening is that cin returns true when something is read from the key board buffer.
So...
I think whats going on here is:
Stay in the loop and clear the keyboard buffer as long as nothing is happening.
Is that it? Or am I missing something... 
What type of bad user input would make this necessary?

---

### Post by dwhitney67 on 2010-02-27
When evaluating a stream as a conditional, the stream's "operator bool()" method is called.

Many books do not discuss data conversion operators, and oftentimes it is not necessary to have.  Typically, accessor methods are discussed, and hence many programmers implements such (which is fine).

Here's an example of the usage of an accessor method and the operator bool method.
```

#include <iostream>

class Foo
{
public:
   Foo(bool flag) : myFlag(flag) {}

   bool getFlag() const { return myFlag; }

   operator bool() const { return myFlag; }

private:
   bool myFlag;
};

int main()
{
   Foo foo(true);

   // here, Foo's accessor method is called
   //
   std::cout << "flag = " << (foo.getFlag() ? "true" : "false") << std::endl;

   // here, Foo's operator bool() method is called
   //
   std::cout << "flag = " << (foo ? "true" : "false") << std::endl;
}

```

Anyhow, back to your question... cin is being evaluated as a bool in the while-loop conditional.  When cin's operator bool() method is called, it is equivalent to calling cin's good() method.

In the code I presented earlier, including <limits> was probably overkill.  Simply using a numeric value, say 256, in the cin.ignore() method would have sufficed to clear the cin stream of unwanted data up to, and including, the newline character.

---

### Post by Jonas thomas on 2010-02-27
```

Anyhow, back to your question... cin is being evaluated as a bool in the while-loop conditional. When cin's operator bool() method is called, it is equivalent to calling cin's good() method.

```
Thank you for explaining that. Mentally !cin.good() works for me..
Looking at...
```

      cin.clear();
      do { cin.ignore(numeric_limits<streamsize>::max(), '\n'); } while (!cin);

```
Originally I was wondering why you didn't just get rid of the '\n' in the cin.ignore(numeric_limits<streamsize>::max(), '\n') and just clear the whole buffer. (I was thinking like of an error event such as me pounding my keyboard in utter disgust or the cat jumping up on my desk to say hello) Then it occurred to me if someone was a really fast typist (who knew the questions that where going to be asked) the input buffer would stay ahead of the program with the algorithm... I think that's what going on right??

Also I seem to remember reading somewhere that that once a you are cin.good() ==false you need a cin.clear to reset everything before everything  works properly again.  Is this correct? (Probably should test this before asking this question, but I think I'm correct on this)

If so, is the"do while" really required?  

I'm assuming that cin.ignore can never generate a failure, because if it did wouldn't you be trapped in the do while, since there is nothing to clear the error? Right?

Ok.. One other question..
```

      // check if valid input given; break from loop if so.
      if (cin.peek() == '\n' && cin.good()) break;

```
I'm just curious why didn't you do this to strip off the '\n' since it's a nuisance at this point.
```

      // check if valid input given; break from loop if so.
      if (cin.peek() == '\n' && cin.good())
      {
          cin.ignore();
          break;
       }

```
I suppose I might be thinking more like a vb programmer than a c++ programmer here.
Was this just preference, or am I missing something here.

---

