---
title: "Fear my c++ madness! beware!"
date: 2008-03-26
forum: Programming Talk
---

### Post by Rob-e on 2008-03-26
do not stare too long, you WILL go into a trance, muwhahaha

```

#include <iostream>
using std::cout;
using std::endl;

int main(int argc, char** argv)
{
	int i = 1;
	int i2 = 1;
	int i3;
	
	while(i < 100)
	{
		while (i2 < 75)
		{
			i3 = 0;
			while (i3 < i2)
			{
			cout << "*";
			i3 ++;
			}
			
		usleep(5000);
		cout << endl;
		i2 ++;		
		}

	i2 = 1;
	}
	return 0;
}

```

btw this is the best program in c++ ive ever written :)

---

### Post by pedro_orange on 2008-03-26
Charming......

---

### Post by Rob-e on 2008-03-26
i affected someone... my job here is done

---

### Post by pedro_orange on 2008-03-26
> i affected someone... my job here is done

Infected*

---

### Post by Joeb454 on 2008-03-26
I can't be bothered to compile it, what does it do?

---

### Post by Rob-e on 2008-03-26
it draws a star pattern like 
*
**
***
until 75 stars wide and repeats... FOREVER!!! hahahaha

---

### Post by fela on 2008-03-26
failed to compile; here is output: ```
me@aquabuntu:~/Desktop/rob-e-cplusplus$ g++ main.cc -o stars
main.cc:30: error: stray ‘#’ in program
main.cc:30: error: expected constructor, destructor, or type conversion before ‘<’ token
main.cc: In function ‘int main(int, char**)’:
main.cc:34: error: redefinition of ‘int main(int, char**)’
main.cc:5: error: ‘int main(int, char**)’ previously defined here
me@aquabuntu:~/Desktop/rob-e-cplusplus$
```

how did you compile it? is there a dependency/header i need?

---

### Post by zeller on 2008-03-26
This is so uncharacteristic of me, but, wtf?!

Er, good job. :|

---

### Post by Rob-e on 2008-03-26
i wrote it in geany and built it there, i assume that uses g++?

---

### Post by nitro_n2o on 2008-03-26
do you really need to say while(i < 100) :)

why don't you have a recursive version :) that will be fun

---

### Post by Rob-e on 2008-03-26
maybe dont name it main.cc mines named mezmorize.cpp

---

### Post by Rob-e on 2008-03-26
> **nitro_n2o said:**
> do you really need to say while(i < 100) :)

why don't you have a recursive version :) that will be fun

ah, yes, when i was testing the timer i had it only run 100 times and it would do that in like 5 seconds

and i dont know what a recursive version is

---

### Post by nitro_n2o on 2008-03-26
> **Rob-e said:**
> ah, yes, when i was testing the timer i had it only run 100 times and it would do that in like 5 seconds

and i dont know what a recursive version is

recursive is done by making a function call it self 
like this very simple code 

```
#include <iostream> 

using namespace std; 

void printStars(int n) 
{
  if(!n) {
    cout << endl; 
    return;
  }

  cout << "*";
  printStars(n-1); 
}


int main() 
{
  int i=1; 
  while(i++) {
    printStars(i);
    if(i >= 75) 
      i=1;
    usleep(5000);
  }

  return 0;
}
```

Actually you can replace the while(i++) with a recursive function :)

---

### Post by ibuclaw on 2008-03-26
A version that would call itself forever.

ie:
```

void recurse()
{
   recurse();
}

```

Now add some fancy stuff before the calling of recurse and you have yourself a never ending program that does something spectacular!

---

### Post by CptPicard on 2008-03-26
> **tinivole said:**
> 
Now add some fancy stuff before the calling of recurse and you have yourself a never ending program that does something spectacular!

... until it runs out of stack pretty quickly because we're not dealing with a tailcall optimizing compiler.

---

### Post by Rob-e on 2008-03-26
> **nitro_n2o said:**
> recursive is done by making a function call it self 
like this very simple code 



my god... that just blew my mind

---

### Post by Rob-e on 2008-03-26
> **nitro_n2o said:**
> 
```
#include <iostream> 

using namespace std; 

void printStars(int n) 
{
  if(!n) {
    cout << endl; 
    return;
  }

  cout << "*";
  printStars(n-1); 
}


int main() 
{
  int i=1; 
  while(i++) {
    printStars(i);
    if(i >= 75) 
      i=1;
    usleep(5000);
  }

  return 0;
}
```



wait, can i use  using namespace std insted of using every one i use? and its the same thing?

---

### Post by skeeterbug on 2008-03-26
Don't name variables with numbers in them like that. I swear I kept thinking it was 13 and not i3. Annoying!

---

### Post by lavinog on 2008-03-26
> **Rob-e said:**
> ah, yes, when i was testing the timer i had it only run 100 times and it would do that in like 5 seconds

and i dont know what a recursive version is

when will ( i >= 100 )?

Really what would be the advantage to a recursive function?
I don't think it would be more efficient.
wouldn't  a simple loop be just as good?

---

### Post by nitro_n2o on 2008-03-26
> **Rob-e said:**
> wait, can i use  using namespace std insted of using every one i use? and its the same thing?

absolutely .. we are lazy :)

---

### Post by nitro_n2o on 2008-03-26
> **lavinog said:**
> when will ( i >= 100 )?

Really what would be the advantage to a recursive function?
I don't think it would be more efficient.
wouldn't  a simple loop be just as good?

A simple loop is almost always better than recursion especially with compilers that don't exploit tail recursive functions and unwind them to loops 

the whole point is just to have fun ;)

---

### Post by drubin on 2008-03-26
I am also currently learning c++;

I am utterly confused at the whole point of this topic..... It makes no sense, there is no point to it.

I really started reading this hoping to be amazed - is there something i am missing? :)

---

### Post by LaRoza on 2008-03-26
> **rubinboy said:**
> 
I really started reading this hoping to be amazed - is there something i am missing? :)

No.

---

### Post by drubin on 2008-03-26
> no

```
Removed due to sense..... (People don't think before they run code)
```
This is the most beautiful  piece of code i have EVER seen, It is a simple bash script. 

> The following is arguably one of the most elegant examples of a fork bomb. It was created by Jaromil in 2002, and released as an open source piece of art. The fork bomb is executed by pasting the following 13 characters into a UNIX shell such as bash or zsh.[1]

DONT run it! (This is simply for looking and not touching) :)

While we are in the process of teaching about Recursion we might as well teach about this 
[http://en.wikipedia.org/wiki/Fork_bomb](http://en.wikipedia.org/wiki/Fork_bomb)

Great, now there is meaning, Code

---

### Post by danbuter on 2008-03-26
You should delete that. Someone will run it.

---

### Post by drubin on 2008-03-26
> **danbuter said:**
> You should delete that. Someone will run it.

Ye, after coming to my senses, people dont think before they run code! 

Thanks for the heads up. :) I really don't want to crash peoples computers.

---

### Post by nitro_n2o on 2008-03-26
hmm... the code posted thus far will not harm your computer.. unless you keep it running for days... 
it is just an infinite loop NOT a fork bomb :)

---

### Post by drubin on 2008-03-26
True,

But any one that runs code, that it explicitly says dont! well I don't have much sympathy for.

I included the url link, as to explain that running code you have no idea what it does, (No matter now cool and simple it looks) can be harmful!

I removed the code from the post, so people would have to actually go to the site read it, and do the exact opposite.

---

### Post by nitro_n2o on 2008-03-26
ohh ok.. but if someone is running code without knowing does that code do deserves and consequences  
I really like that sticky post about malicious commands

---

### Post by ibuclaw on 2008-03-26
Question!

Even if someone was stupid enough, wouldn't terminal shortcuts such as "Ctrl+C" or "Ctrl+Alt+C" stop the program in it's tracks? (unless the **&** command was used with the initiation of the program).

Regards
Iain

---

### Post by Jessehk on 2008-03-26
> **danbuter said:**
> You should delete that. Someone will run it.

As long as it comes with necessary warning, I don't think knowledge of a command should be censored.
Unix is not built on the idea of protecting the user from themselves. Why do you think commands like "rm" exist?

Just MHO.

---

### Post by LaRoza on 2008-03-26
> **Jessehk said:**
> As long as it comes with necessary warning, I don't think a command should be censored.

I don't think Unix is built on protecting the user from themselves. Why do you think commands like "rm" exist?

Just MHO.

Due to the posting of such commands in a very cruel manner (as advice, all such posts are in Jail, but they are most cruel), the forum has taken a very low tolerance for such commands, and they should never be posted, even with warnings.

Some command have use, but do have a similiar format to those that are dangerous (rm can be most useful), but they should only be posted when required.

While some commands are common *nix jokes, this forum has many people yet to learn them.

---

### Post by Rob-e on 2008-03-27
how do i make a random number between 0 and 200?

---

### Post by Rob-e on 2008-03-27
thanks for all the tips and ... help :D 

heres v. 2

i used a function and it does something quite different

enjoy, i know i sure did/am

```
#include <iostream>
#include <cstdlib> 

using namespace std;

void makeLine(int width, int line, int time)
{
	width = 0;
	
	while (width < line)
		{
		cout << " ";
		width ++;
		}
	cout << "*";
	usleep(time);
	cout << endl;
}

int main(int argc, char** argv)
{
	int mainLoop = 1; //  doesnt change, loops foreaver
	int newLine = 1; //   adds 1 every line and tells lineWidth when to stop
	int lineWidth; //     counts up to star width in the given line
	int size = 75; //     max number of stars wide and height also
//	int insideSize = 20;
	int delay = 5000; //  delay of loop
/*	
	cout << "how big? ";
	cin >> size;
	cout << "time? ";
	cin >> delay;
*/
	while(mainLoop == 1)
	{
 	   srand((unsigned)time(0)); 
 	   size = rand() % 200; 
		
		while (newLine <= size)
		{
			makeLine(lineWidth, newLine, delay);
			newLine ++;		
		}
		
		while (newLine > 0)
		{
			makeLine(lineWidth, newLine, delay);
			newLine --;	
		}

	newLine = 1;
	}
	return 0;
}

```

---

### Post by WW on 2008-03-27
*Trapped... in an infinite loop!  Who will save us now?*

FYI: The two simplest ways to write an infinite loop in C are probably:
```

    while(1)
        do_this_forever...

```
or
```

    for (;;)
        do_this_forever...

```

---

### Post by Rob-e on 2008-03-27
nice, thats 1 less integer :popcorn:

---

### Post by Rob-e on 2008-03-27
k, i made it randomly go to a point between 1 and 200 from where it is, if you see anything that i did wrong, or that i could have done better, i appreciate the criticism so post away

this time i made the function much simpler, it just takes 1 integer and thats the number of spaces it makes

btw this may not be much to you but im veery new to this

here it is v.3


```

#include <iostream>
#include <cstdlib> 

using namespace std;

void makeLine(int size)
{
	int counter = 0;
	
	while (counter < size)
		{
		cout << " ";
		counter ++;
		}
	cout << "*" << endl;
}

int main(int argc, char** argv)
{

	int width = 1;
	int goToNum;
	
	while(1)
		{
		srand((unsigned)time(0)); 
		goToNum = rand() % 200; 
	
		if(goToNum > width)
			{
				while(goToNum != width)
				{
					width++;
					makeLine(width);
					usleep(10000);
				}
			}
		else
			{
				while(goToNum != width)
				{
					width--;
					makeLine(width);
					usleep(10000);
				}
			}
		}
			
return 0;
}

```

---

### Post by Wybiral on 2008-03-27
You realize you're making your own for-loop, right?

Why not replace this:

```

void makeLine(int size)
{
	int counter = 0;
	
	while (counter < size)
		{
		cout << " ";
		counter ++;
		}
	cout << "*" << endl;
}

```

With this:

```

void makeLine(int size)
{
	for(int i=0; i<size; ++i) cout << " ";
	cout << "*" << endl;
}

```

---

### Post by drubin on 2008-03-27
> **tinivole said:**
> Question!

Even if someone was stupid enough, wouldn't terminal shortcuts such as "Ctrl+C" or "Ctrl+Alt+C" stop the program in it's tracks? (unless the **&** command was used with the initiation of the program).

Regards
Iain

The point of that fork bomb, is that it creates so many proccess on your system you cant run ANY thing, not even the kill command.

Correct me if i am wrong, but  crtl+c  just runs the kill cmd on the current process id in that window. Therefore if some one had used the "&" on a standard infinite loop you could run something like.
```
ps -ef |grep commandname
kill proccessid  

```

---

### Post by drubin on 2008-03-27
> **WW said:**
> *Trapped... in an infinite loop!  Who will save us now?*

FYI: The two simplest ways to write an infinite loop in C are probably:
```

    for (;;)
        do_this_forever...

```

(My c++/c are a bit well lacking, but in all other programming langs you would at least need a condition )
so?```
  for (;true;)
        do_this_forever...
```

---

### Post by Lusst on 2008-03-27
[img]http://ballastexistenz.autistics.org/images/oncouch2.jpg[/img]

---

### Post by POW R TOC H on 2008-03-27
:confused:
What was that all about ?:lolflag:

---

### Post by drubin on 2008-03-27
Explain the pic?

relevance

---

### Post by pedro_orange on 2008-03-27
This thread has certainly disturbed me. I have no idea what its about now!

---

### Post by drubin on 2008-03-27
I like your sig. A tpedro_orange.

Goes with the current state of this thread

---

### Post by WW on 2008-03-27
> **rubinboy said:**
> (My c++/c are a bit well lacking, but in all other programming langs you would at least need a condition )
so?```
  for (;true;)
        do_this_forever...
```

Did you try it?  If the second expression is missing, it is assumed to be 1 (i.e. true).  (Your example wouldn't compile as it is, because **true** is not predefined in C.)

---

### Post by drubin on 2008-03-27
Thanks. :) 
Always good to learn new things

---

### Post by Nemooo on 2008-03-27
Indeed, I learned quite a few things going through this thread.

---

### Post by Rob-e on 2008-03-27
> **Wybiral said:**
> You realize you're making your own for-loop, right?
```

void makeLine(int size)
{
	for(int i=0; i<size; ++i) cout << " ";
	cout << "*" << endl;
}

```

wow, i dont know why i did that, i think for loops with the 3 things in parentheses, it never quite works right, why is it ++i instead of i++ or is there no difference?

---

### Post by Rob-e on 2008-03-27
what does the for loop do? does it repeat while it is true? or does it repeat until its true?

btw nice gas/liquid program, thats cool

---

### Post by drubin on 2008-03-27
> wow, i dont know why i did that, i think for loops with the 3 things in parentheses, it never quite works right, why is it ++i instead of i++ or is there no difference?

There is no difference in a for loop. 

But take this code for instance. (Should explain the difference)

```

int x=0;
int a=x++;  //a now have a value of 0, x has a value of 1

int y =0;
int b= ++y;  //b now has a value of 1, y has a value of 1

```

The first returns the value, then increments its value 
The second one  increments its value, and then returns it. 

> what does the for loop do? does it repeat while it is true? or does it repeat until its true?

For loop repeats while it is true,

so if at the first run the condition is false, it will never run.

---

### Post by baumgc on 2008-03-27
btw this is the best program in c++ ive ever written :)[/QUOTE]

```

#include <iostream>

using namespace std;

int main()
{
	int newLine;
	int star;
	int blank;


	for(newLine = 1; newLine < 25; newLine++)
	{
		for(blank = 24; blank > newLine; blank--)
		{
			cout << " ";
		}
		for(star = 0; star < (newLine * 2) - 1; star++)
		{
			cout << "*";
		}
		
		
	cout << endl;
	}
	return 0;
}

```
I did a similar thinger in my programming class. A christmas tree for the holiday season.

---

### Post by slashank on 2008-03-27
Also, ++x is faster than x++.

---

### Post by baumgc on 2008-03-27
What if I execute this code on an SSH client with my schools UNIX server?

Will it crash that or my computer?

---

### Post by drubin on 2008-03-27
> **slashank said:**
> Also, ++x is faster than x++.

Is there a reason, or is it just c++ implementation? (This thread has taken of a bit of most langs :) )

---

### Post by drubin on 2008-03-27
> **baumgc said:**
> What if I execute this code on an SSH client with my schools UNIX server?

Will it crash that or my computer?

Firstly, Why would you want to crash any thing? Would you really like to break your schools server? Would you like to get into trouble for a boring not worth while "joke". You might end up loosing all the data and corrupting the hard drive(improper shutdown).


Secondly what answer do I have to give for you not to run it ?

---

### Post by Rob-e on 2008-03-27
> **rubinboy said:**
> There is no difference in a for loop. 

But take this code for instance. (Should explain the difference)

```

int x=0;
int a=x++;  //a now have a value of 0, x has a value of 1

int y =0;
int b= ++y;  //b now has a value of 1, y has a value of 1

```

The first returns the value, then increments its value 
The second one  increments its value, and then returns it. 


did you actually know that or do you have like 5 books and you searched each one to find the smallest thing, just to look smart?

---

### Post by drubin on 2008-03-27
> **Rob-e said:**
> wow, i dont know why i did that, i think for loops with the 3 things in parentheses, it never quite works right, why is it ++i instead of i++ or is there no difference?

> **Rob-e said:**
> did you actually know that or do you have like 5 books and you searched each one to find the smallest thing, just to look smart?

You asked the question! I assumed you would have liked an answer? But guess not.

No I did not search for hours trying to find that. 

But if some one did take the time to search around/google things just to help you (and learn something in the process) you should just thank them and then ask why didn't I think of that.

---

### Post by Rob-e on 2008-03-27
i think its awesome that you know that, i was very surprised you knew such a small thing, thats why i made a funny joke

anyway, its time to do my VB homework for class tonight, so i may/may not reply again

---

### Post by drubin on 2008-03-27
jokes :)

Ye, been coding for a while (Not as long as these Cobol, machine code boys) but a few years, you tend to pick things up... 

Because at some point in time you are bound to be fixing/working with/correcting/maintaining some other persons code and well you need to know what they are doing.

VB is a dirty lang.. :) but enjoy

---

### Post by nvteighen on 2008-03-27
> **rubinboy said:**
> VB is a dirty lang.. :) but enjoy

A very smart way to describe it! I remember when I coded a word processor in VB... and yes, I felt my code to be just dirty.

---

### Post by drubin on 2008-03-27
> **nvteighen said:**
> A very smart way to describe it! I remember when I coded a word processor in VB... and yes, I felt my code to be just dirty.

Your code, I felt dirty after coding in it :)

Only did it once and never again

---

### Post by Wybiral on 2008-03-27
> **Rob-e said:**
> i think its awesome that you know that, i was very surprised you knew such a small thing, thats why i made a funny joke

anyway, its time to do my VB homework for class tonight, so i may/may not reply again

It's not a small thing. It makes a HUGE difference if you use them incorrectly. If something that you expect to be 10 ends up being 9, your entire program is probably going to crash.

---

### Post by nvteighen on 2008-03-27
> **rubinboy said:**
> Your code, I felt dirty after coding in it :)

Only did it once and never again
I was lucky, then! ;)

It was dissappointing to see how a program meant to be a small RTF-processor ended up eating lots of memory just because of all auxiliary modules that had to be loaded in background only to keep the thing running properly.

---

### Post by ibuclaw on 2008-03-27
> **rubinboy said:**
> VB is a dirty lang.. :) but enjoy

Yes! C# is a better language for the "new to programming" students.
It has an equally decent standard for easy learning, but keeps to other language standards in terms of format.

Though, that said. I did have a lot of fun crashing computers at school.

Since our computing lessons were 2 hours long, we'd all have a 15 minute break inbetween. 
By the end of the first year we'd all got into the habit of locking our PCs before leaving them as everyone started using this very popular prank on everyone else while they weren't looking.

```

int a = 1
while (a != 2)
x = shell(calc.exe)
loop

```
Which would open a million instances of MS's calculator app. (until the OS crashed).
There were other variations such as a number of apps in loop, or as one smart spark made one that "searched" every folder accessible on the network for executables and launched them.

Those were good old times!

Forgive me if my VB6 code is wrong, it has been ages since I last used the language.

Iain

---

### Post by drubin on 2008-03-28
> **tinivole said:**
> Yes! C# is a better language for the "new to programming" students.
It has an equally decent standard for easy learning, but keeps to other language standards in terms of format.

I personally think Java is the best lang to start programming with. It  might not be as Fast as c++/c but it has standards and makes learning the lang very easy.

It also is a completely OO lang  and therefore explains alot for students learning things for the first time.

---

### Post by patbuntu on 2008-03-28
> **rubinboy said:**
> Is there a reason, or is it just c++ implementation? (This thread has taken of a bit of most langs :) )


The postfix operator ( x++ ) normally requires making a copy of an object, while the prefix operator ( ++x ) does not.

With regards to primitive types like int or char, there is probably no real difference, but when applied to objects which overload these operators, it can be significantly more efficient to use prefix.

---

### Post by drubin on 2008-03-28
> **patbuntu said:**
> The postfix operator ( x++ ) normally requires making a copy of an object, while the prefix operator ( ++x ) does not.

Makes sense.

---

