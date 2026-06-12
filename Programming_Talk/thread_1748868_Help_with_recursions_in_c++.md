---
title: "Help with recursions in c++"
date: 2011-05-04
forum: Programming Talk
---

### Post by Ashtarias on 2011-05-04
Hello guys, im new to programming in general and have just started learning C++ as my first programming language when i came across the topic of recursions and got awfully lost am am wondering if any kind soul can give me some help.
 
Now,google tells me that recursions are functions that call themselves,whether directly or indirectly, and showed my a few beginner examples of it which included the basic printing of numbers using a recursive function
 
```
 
void display(int n)
{ 
if ( n <= 0 ) return;
 cout << n << " ";
 display(n-1); //Will call display but with (n-1)
 return;}

```
 
and fibonacci number sequences which has got me stumped.
 
```
 
 
[COLOR=#0000ff]int[/COLOR] fibonacci[COLOR=#008000]([/COLOR][COLOR=#0000ff]int[/COLOR] n[COLOR=#008000])[/COLOR] 
[COLOR=#008000]{[/COLOR]     
[COLOR=#666666]// Base cases[/COLOR]   
 [COLOR=#0000ff]if[/COLOR] [COLOR=#008000]([/COLOR] n [COLOR=#000080]==[/COLOR] [COLOR=#0000dd]0[/COLOR] [COLOR=#008000])[/COLOR] [COLOR=#0000ff]return[/COLOR] [COLOR=#0000dd]0[/COLOR][COLOR=#008080];[/COLOR]   
 [COLOR=#0000ff]else[/COLOR] [COLOR=#0000ff]if[/COLOR] [COLOR=#008000]([/COLOR] n [COLOR=#000080]==[/COLOR] [COLOR=#0000dd]1[/COLOR] [COLOR=#008000])[/COLOR] [COLOR=#0000ff]return[/COLOR] [COLOR=#0000dd]1[/COLOR][COLOR=#008080];[/COLOR]     
[COLOR=#666666]//This is returning fibonacci(n) = fibonacci(n-1) + fibonacci(n-2)[/COLOR]    
[COLOR=#0000ff]else[/COLOR]          
[COLOR=#0000ff]return[/COLOR] fibonacci[COLOR=#008000]([/COLOR]n[COLOR=#000040]-[/COLOR][COLOR=#0000dd]1[/COLOR][COLOR=#008000])[/COLOR] [COLOR=#000040]+[/COLOR] fibonacci[COLOR=#008000]([/COLOR]n[COLOR=#000040]-[/COLOR][COLOR=#0000dd]2[/COLOR][COLOR=#008000])[/COLOR][COLOR=#008080];[/COLOR] [COLOR=#008000]}[/COLOR]

```
 
What do the base cases actually return?i've read that a return value of 0 in main.cpp means that the program executed without errors and that a return value of 1 shows that an error occurred.If this is the case, why does the function return 1(an error) when (n==1)?.Or do the values 0 and 1 returned mean nothing at all and simply terminate the function?
 
Also,i do not understand the line return fibonacci(n-1)+fibonacci(n-2).Assuming that i enter a value of 5, wouldnt the line become fibonacci(5-1)+fibonacci(5-2), which would give me a value of (4)+(3)=7 which is not a fibonacci number at all?
 
 
This is the fibonacci number sequence which i did iteratively
 
```
 
/*Generates the fibonacci sequence up to the nth number which the user inputs*/
 
#include <iostream>
using namespace std;
int Fibonacci(int &number)
{
 int counter;
 int firstnumber=0;
 int secondnumber=1;
 int total=0;
 int quit;
 cout<<"The fibonacci number sequence is : "<<endl;
 cout<<firstnumber<<" ";//entering it manually
 cout<<secondnumber<<" ";//entering it manually
 
 for(counter=0;total<number;counter++)
 {
       quit=total+firstnumber+secondnumber;
       total=firstnumber + secondnumber;
       cout<<total<<" ";
       firstnumber=secondnumber;
       secondnumber=total;
 
       if(quit>=number)
       {
             break;
       }
 }
}
int main()
{
    int input;
    cout<<"Enter a number"<<endl;
    cin>>input;
    cout<<endl;
 
    if(input==0)
    {
                cout<<"Please enter a number greater than 0"<<endl;
    }
    else if(input==1)
    {
         cout<<"Please enter a number greater than 1"<<endl;
    }
    else
    {
    Fibonacci(input);
    }
 
    system("PAUSE");
    return EXIT_SUCCESS;
}
 

```
 
and this is the fibonacci number sequence i did using recursions
 
```
 
#include <iostream>
using namespace std;
int Fibo(int n)
{
    int sum=0;
    while(sum<=n)
    {
                 sum=Fibo(n-1)+Fibo(n-2);
                 cout<<sum<<endl;
    }
}
int main()
{
    int input;
    cout<<"Please enter a number greater than 1"<<endl;
    cin>>input;
    if(input==1 || input==0)
    {
                         cout<<"Enter a number greater than 1 you dolt"<<endl;
    }
    else
    {
        Fibo(input);
    }
    system("PAUSE");
    return EXIT_SUCCESS;
}
 
 
 

```
 
My resursive fibonacci number sequence works, though i have no idea why it does LOL or how the line sum=Fibo(n-1)+Fibo(n-2); actually works.Also, can someone tell me why does my if loop in int main() of my recursive fibonacci sequence not work?Whenever i enter a number that is 1 or 0, i do not get the message i set "i.e Enter a number greater than 1 you dolt", but a message telling me to enter a number that is greater than 1(or 0 if i entered 0)
 
 
Sorry if i end up confusing anyone.
 
Thanks

---

### Post by NovaAesa on 2011-05-04
> Assuming that i enter a value of 5, wouldnt the line become fibonacci(5-1)+fibonacci(5-2), which would give me a value of (4)+(3)=7 which is not a fibonacci number at all?

Yes, it would become fibonacci(5-1) + fibonacci(4-1). But then each fibonacci function must also be evaluated. I'll abbreviate 'fibonacci' to 'f'.

```

f(5) = f(5-1) + f(5-2)
     = f(4) + f(3)
     = f(4-1) + f(4-2) + f(3-1) + f(3-2)
     = f(3) + f(2) + f(2) + f(1)
     = f(3-1) + f(3-2) + f(2-1) + f(2-2) + f(2-1) + f(2-2) + 1
     = f(2) + f(1) + f(1) + f(0) + f(1) + f(0) + 1
     = f(2-1) + f(2-2) + 1 + 1 + 0 + 1 + 0 + 1
     = f(1) + f(0) + 1 + 1 + 0 + 1 + 0 + 1
     = 1 + 0 + 1 + 1 + 0 + 1 + 0 + 1
     = 5

```

With recursive functions like this, 0 and 1 don't really have anything to do with success or failure, that only has to do with which value is returned from main().

> 
how the line sum=Fibo(n-1)+Fibo(n-2); actually work

This is simply the recursive definition of the fibonacci numbers. Take a look at [http://en.wikipedia.org/wiki/Fibonacci_number](http://en.wikipedia.org/wiki/Fibonacci_number) or any entry level algebra or number theory textbook, they will explain it pretty well.

---

### Post by Arndt on 2011-05-04
> **Ashtarias said:**
> 
What do the base cases actually return?i've read that a return value of 0 in main.cpp means that the program executed without errors and that a return value of 1 shows that an error occurred.If this is the case, why does the function return 1(an error) when (n==1)?.Or do the values 0 and 1 returned mean nothing at all and simply terminate the function?


The language doesn't impose any interpretation on what the result of a function you've written means, except in the case you mention, where the return value from main (not main.cpp, we're talking about functions, not files, and the file could be named anything) signals success or error.

In this case, the function corresponds well to the mathematical concept of a function, which maps input value(s) to a return value, with no signalling of errors. f(0) = 0, so the function call f(0) returns 0, that's all. The function cos(x) returns 1 when called as cos(0) (it's not recursive, but we were talking about the base case anyway).

Returning terminates the function, if you like to express it like that, because the result is known and is now given back to the caller. But "terminate" more often means stopping the program for good, which is another thing.

In C++, you can write functions for many other purposes than implementing a mathematical function, and you're free to let them return some value or other to signal error, not necessarily the same way main does. They don't have to be functions in the mathematical sense, either, and can have side-effects (changing a file, for example), which a mathematical function doesn't have.

---

### Post by Ashtarias on 2011-05-04
Thanks for your help Nova, i understand the fibonacci sequences better now.I searched math and algebra in google instead of recursive fibonacci and came up with a math book that explained it to me.I looked in wikipedia before posting here and only felt dumb after loking at all the wierd and squiggly symbols listed there O_O.
 
@Arndt: What do you mean by the function cos(x)? I dont see any function cos(x) anywhere? 
 
PS:Do i need a strong foundation in math to be a good programmer? I dont have a strong mathemathical background so i ws wondering if that would hinder my programming progress.BTW can anyone help me with the debugging messages i get? I'm currently using microsoft visual studio 2010 C++ express on a 64bit windows 7 OS but dont understand why i am getting messages in the debugger that says that they can't find a pdb file?
 
```
 
'Resursive Fibonacci.exe': Loaded 'C:\Users\Kenneth\Documents\Visual Studio 2010\Projects\Resursive Fibonacci\Debug\Resursive Fibonacci.exe', Symbols loaded.
'Resursive Fibonacci.exe': Loaded 'C:\Windows\SysWOW64\ntdll.dll', Cannot find or open the PDB file
'Resursive Fibonacci.exe': Loaded 'C:\Windows\SysWOW64\kernel32.dll', Cannot find or open the PDB file
'Resursive Fibonacci.exe': Loaded 'C:\Windows\SysWOW64\KernelBase.dll', Cannot find or open the PDB file
'Resursive Fibonacci.exe': Loaded 'C:\Windows\SysWOW64\msvcp100d.dll', Symbols loaded.
'Resursive Fibonacci.exe': Loaded 'C:\Windows\SysWOW64\msvcr100d.dll', Symbols loaded.
'Resursive Fibonacci.exe': Loaded 'C:\Windows\SysWOW64\apphelp.dll', Cannot find or open the PDB file
'Resursive Fibonacci.exe': Loaded 'ImageAtBase0x4a840000', Loading disabled by Include/Exclude setting.
'Resursive Fibonacci.exe': Unloaded 'ImageAtBase0x4a840000'
The program '[3044] Resursive Fibonacci.exe: Native' has exited with code 0 (0x0).

```

---

### Post by NovaAesa on 2011-05-04
> **Ashtarias said:**
> What do you mean by the function cos(x)? I dont see any function cos(x) anywhere?

It was a reference to the trigonometric function cosine. [http://en.wikipedia.org/wiki/Cosine#Sine.2C_cosine.2C_and_tangent](http://en.wikipedia.org/wiki/Cosine#Sine.2C_cosine.2C_and_tangent)


 
>  
PS:Do i need a strong foundation in math to be a good programmer? I dont have a strong mathemathical background so i ws wondering if that would hinder my programming progress.
It really depends on what kind of programming you want to do. If you want to just stick to application programming, basic high school maths should be fine.

---

### Post by simeon87 on 2011-05-04
> **Ashtarias said:**
> PS:Do i need a strong foundation in math to be a good programmer? I dont have a strong mathemathical background so i ws wondering if that would hinder my programming progress.BTW can anyone help me with the debugging messages i get? I'm currently using microsoft visual studio 2010 C++ express on a 64bit windows 7 OS but dont understand why i am getting messages in the debugger that says that they can't find a pdb file?

Math is good to have but it depends on what you're creating. If you're creating 3D video games then you'll need linear algebra and similar maths. You always need good knowledge of logic to do well in computer programming but many other types of maths can be learned when you need it.

---

### Post by Arndt on 2011-05-04
> **Ashtarias said:**
> 
 
@Arndt: What do you mean by the function cos(x)? I dont see any function cos(x) anywhere? 


It was just meant as an example of a mathematical function. If you haven't learned trigonometry, I apologize.

---

### Post by heyandy889 on 2011-05-05
Another cool illustration of recursion is the Towers of Hanoi. This guy does an okay job of explaining the game in this video [http://www.youtube.com/watch?v=uZaHTmOuqJI&feature=fvst](http://www.youtube.com/watch?v=uZaHTmOuqJI&feature=fvst)

The game is a bit like the Fibonacci sequence, because you can rely on simpler cases to solve harder cases.

Also interesting are factorial numbers

---

### Post by Ashtarias on 2011-05-05
Thanks for the replies guys i have learnt trigonometry before, though it was a few years ago .
 
I've read a book that explains recursion and understand how a recursive function calls itself.However, i still do not understand how a recursive function works and outputs the result.
 
```

f(5) = f(5-1) + f(5-2)
     = f(4) + f(3)
     = f(4-1) + f(4-2) + f(3-1) + f(3-2)
     = f(3) + f(2) + f(2) + f(1)
     = f(3-1) + f(3-2) + f(2-1) + f(2-2) + f(2-1) + f(2-2) + 1
     = f(2) + f(1) + f(1) + f(0) + f(1) + f(0) + 1
     = f(2-1) + f(2-2) + 1 + 1 + 0 + 1 + 0 + 1
     = f(1) + f(0) + 1 + 1 + 0 + 1 + 0 + 1
     = 1 + 0 + 1 + 1 + 0 + 1 + 0 + 1
     = 5
```
 
in this case, isnt this the same as simply declaring 5=5? If so, while i understand the process of the recursive function calling itself as shown above in nova's example, i do not understand how the recursive actually comes out with an output for the fibonacci sequence when the end result of the function is simply the value passed into the function.
 
Am i correct in guessing that the stack memory somehow comes into play here,seeing as we are dealing with functions?
 
```

#include <iostream>
 using namespace std;
 
int fibo(int n)
{
int sum=0;
if(n==0)
{
cout<<"Please enter a number greater than 0"<<endl;
return 0;
}
 
else if(n==1)
{
cout<<"Please enter a number greater than 1"<<endl;
return 1;
}
 
else
{
sum=fibo(n-1)+fibo(n-2);
cout<<sum<<endl;
}
return sum;
}
 
int main()
{
int input;
cout<<"Please enter a number: ";
cin>>input;
fibo(input);
system"PAUSE";
return EXIT_SUCCESS;

```
 
Also, can someone just kindly point out why this code doesn't work and the solution? i've tried it out and everything works except the line sum=fibo(n-1)+fibo(n-2)
? I've been trying since yesterday night and still cant see what's the problem =(
 
Ashtarias

---

### Post by NovaAesa on 2011-05-05
It's just a coincidence that the 5th Fibonacci number is 5, i.e. f(5)=5.

Think about the first few terms of the Fibonacci sequence and how they relate to each other.

0, 1, 1, 2, 3, 5, 8, 13, 21, ...

You can see that each Fibonacci number is the sum of the two previous Fibonacci numbers. But then how do we calculate the first two Fibonacci numbers? The first two numbers in the sequence don't have two entries before them (the first number (or zeroth number counting from 0) has zero entries before it, and the second number (first number, counting from zero) has only one entry before it). So we just arbitrarily say that the first Fibonacci number is 0 and the second is 1.

Using the notation f(n) is the nth Fibonacci number:

f(0) = 0 //the zeroth fibonacci number
f(1) = 1 //the first fibonacci number
f(n) = f(n-1) + f(n-2) //the nth fibonacci number is the sum of the n-1th fibonacci number and the n-2th fibonacci number

Does that help? There's really no point trying to understand any recursive code until you understand the underlying recursive relationship between the numbers.

---

### Post by Ashtarias on 2011-05-05
Yea that did help. i tried out different values with the recursive fibonacci and got the value
 
```

f(7)=f(7-1)+f(7-2)
=f(6) + f(5)
={f(6-1)+f(6-2)} + {f(5-1)+f(5-2)}
={f(5)+f(4)} + {f(4) + f(3)}
={f(5-1)+f(5-2)} + {f(4-1)+f(4-2)} + {f(4-1) + f(4-2)}+{f(3-1) + f(3-2)}
={f(4)+f(3)} + {f(3)+f(2)} + {f(3)+f(2)} + {f(2)+f(1)}
={f(4-1)+f(4-2)} + {f(3-1)+f(3-2)} + {f(3-1)+f(3-2)} + {f(2-1)+f(2-2)} + {f(3-1)+f(3-2)} + {f(2-1)+f(2-2)} + {f(2-1)+f(2-2)}+1
={f(3)+f(2)}+{f(2)+1}+{f(2)+1}+{1+0}+{f(2)+1}+{1+0}+{1+0}+1
=f(3)+f(2)+f(2)+f(2)+f(2)+7
={f(3-1)+f(3-2)} + {f(2-1)+f(2-2)}+{f(2-1)+f(2-2)}+{f(2-1)+f(2-2)}+{f(2-1)+f(2-2)}+7
={f(2)+1}+{1+0}+{1+0}+{1+0}+{1+0}+7
={f(2)}+12
={f(2-1)+f(2-2)}+12
=1+0+12
=13

```
 
If this is the case, am i right in saying that the computer calculates all of the above for the value passed into the function and stores it in the stack memory.It then goes on to a smaller number and again caluculates all the above and stores it again in the stack memory, and continues till it reaches the base case where the function will end.Then, upon ending the function, the function will take the top value in the stack(I.e the newest value, which would be the first fibonacci number) and outputs it,and slowly descends down the stack till all the numbers are shown?
 
In that case, all i have to do to make my code work would be to simply add a loop in int main(), which counts down the number entered to the user and calls the fibo function with every cycle of the loop?

---

### Post by Tony Flury on 2011-05-05
> **Ashtarias said:**
> Yea that did help. i tried out different values with the recursive fibonacci and got the value
 
```

f(7)=f(7-1)+f(7-2)
=f(6) + f(5)
={f(6-1)+f(6-2)} + {f(5-1)+f(5-2)}
={f(5)+f(4)} + {f(4) + f(3)}
={f(5-1)+f(5-2)} + {f(4-1)+f(4-2)} + {f(4-1) + f(4-2)}+{f(3-1) + f(3-2)}
={f(4)+f(3)} + {f(3)+f(2)} + {f(3)+f(2)} + {f(2)+f(1)}
={f(4-1)+f(4-2)} + {f(3-1)+f(3-2)} + {f(3-1)+f(3-2)} + {f(2-1)+f(2-2)} + {f(3-1)+f(3-2)} + {f(2-1)+f(2-2)} + {f(2-1)+f(2-2)}+1
={f(3)+f(2)}+{f(2)+1}+{f(2)+1}+{1+0}+{f(2)+1}+{1+0}+{1+0}+1
=f(3)+f(2)+f(2)+f(2)+f(2)+7
={f(3-1)+f(3-2)} + {f(2-1)+f(2-2)}+{f(2-1)+f(2-2)}+{f(2-1)+f(2-2)}+{f(2-1)+f(2-2)}+7
={f(2)+1}+{1+0}+{1+0}+{1+0}+{1+0}+7
={f(2)}+12
={f(2-1)+f(2-2)}+12
=1+0+12
=13

```
 
If this is the case, am i right in saying that the computer calculates all of the above for the value passed into the function and stores it in the stack memory.It then goes on to a smaller number and again caluculates all the above and stores it again in the stack memory, and continues till it reaches the base case where the function will end.Then, upon ending the function, the function will take the top value in the stack(I.e the newest value, which would be the first fibonacci number) and outputs it,and slowly descends down the stack till all the numbers are shown?
 
In that case, all i have to do to make my code work would be to simply add a loop in int main(), which counts down the number entered to the user and calls the fibo function with every cycle of the loop?

No - it does not recalculate everything each time round - although depending on your algorithm some things might get re-calculated more than once.

You are right in your assumption that in some cases (like this) you can convert a recursive solution to a loop (and vice versa)- these are so called Tail recursion - howvere not all recursive algorithms can be easily converted - for istance traversing a binary tree can be implemented as a loop, but you end up needing to build your own stack to keep track of where you have been, and where you are going to next, so why not use the stack you already have.

---

### Post by NovaAesa on 2011-05-05
> **Ashtarias said:**
> 
In that case, all i have to do to make my code work would be to simply add a loop in int main(), which counts down the number entered to the user and calls the fibo function with every cycle of the loop?
That is a valid way to approach the problem, and probably the most straightforward (although not the most computationally efficient).

---

### Post by Ashtarias on 2011-05-05
```
[FONT=Consolas][SIZE=2][COLOR=#0000ff][FONT=Consolas][SIZE=2][COLOR=#0000ff]
[SIZE=2][FONT=Consolas][COLOR=#0000ff]#include[/COLOR][/FONT][/SIZE][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#a31515][FONT=Consolas][SIZE=2][COLOR=#a31515][FONT=Consolas][SIZE=2][COLOR=#a31515]<iostream>[/COLOR][/SIZE][/FONT]
[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#0000ff][FONT=Consolas][SIZE=2][COLOR=#0000ff][FONT=Consolas][SIZE=2][COLOR=#0000ff]using[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#0000ff][FONT=Consolas][SIZE=2][COLOR=#0000ff][FONT=Consolas][SIZE=2][COLOR=#0000ff]namespace[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2] std;[/SIZE][/FONT]
[/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#0000ff][FONT=Consolas][SIZE=2][COLOR=#0000ff][FONT=Consolas][SIZE=2][COLOR=#0000ff]int[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2] fibo([/SIZE][/FONT][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#0000ff][FONT=Consolas][SIZE=2][COLOR=#0000ff][FONT=Consolas][SIZE=2][COLOR=#0000ff]int[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2] n)[/SIZE][/FONT]
[SIZE=2][FONT=Consolas]{[/FONT][/SIZE]
 
[/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#0000ff][FONT=Consolas][SIZE=2][COLOR=#0000ff][FONT=Consolas][SIZE=2][COLOR=#0000ff]int[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2] sum=n;[/SIZE][/FONT]
[/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#0000ff][FONT=Consolas][SIZE=2][COLOR=#0000ff][FONT=Consolas][SIZE=2][COLOR=#0000ff]if[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2](n==0)[/SIZE][/FONT]
[SIZE=2][FONT=Consolas]{[/FONT][/SIZE]
[/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#0000ff][FONT=Consolas][SIZE=2][COLOR=#0000ff][FONT=Consolas][SIZE=2][COLOR=#0000ff]return[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2] 0;[/SIZE][/FONT]
[SIZE=2][FONT=Consolas]}[/FONT][/SIZE]
[/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#0000ff][FONT=Consolas][SIZE=2][COLOR=#0000ff][FONT=Consolas][SIZE=2][COLOR=#0000ff]else[/COLOR][/SIZE][/FONT]
[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2]{[/SIZE][/FONT]
[SIZE=2][FONT=Consolas]sum=fibo(n-1)+fibo(n-2);[/FONT][/SIZE]
[SIZE=2][FONT=Consolas]cout<<sum<<[/FONT][/SIZE][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#a31515][FONT=Consolas][SIZE=2][COLOR=#a31515][FONT=Consolas][SIZE=2][COLOR=#a31515]" "[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2];[/SIZE][/FONT][/SIZE][/FONT]
[FONT=Consolas][SIZE=2]return sum;
[SIZE=2][FONT=Consolas]}[/FONT][/SIZE]
[/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#0000ff][FONT=Consolas][SIZE=2][COLOR=#0000ff][FONT=Consolas][SIZE=2][COLOR=#0000ff][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2] 
[SIZE=2][FONT=Consolas]}[/FONT][/SIZE]
 
 
[/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#0000ff][FONT=Consolas][SIZE=2][COLOR=#0000ff][FONT=Consolas][SIZE=2][COLOR=#0000ff]int[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2] main()[/SIZE][/FONT]
[SIZE=2][FONT=Consolas]{[/FONT][/SIZE]
[/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#0000ff][FONT=Consolas][SIZE=2][COLOR=#0000ff][FONT=Consolas][SIZE=2][COLOR=#0000ff]int[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2] i;[/SIZE][/FONT]
[/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#0000ff][FONT=Consolas][SIZE=2][COLOR=#0000ff][FONT=Consolas][SIZE=2][COLOR=#0000ff]int[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2] num;[/SIZE][/FONT]
[SIZE=2][FONT=Consolas]cout<<[/FONT][/SIZE][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#a31515][FONT=Consolas][SIZE=2][COLOR=#a31515][FONT=Consolas][SIZE=2][COLOR=#a31515]"Enter a number: "[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2];[/SIZE][/FONT]
[SIZE=2][FONT=Consolas]cin>>num;[/FONT][/SIZE]
[/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#0000ff][FONT=Consolas][SIZE=2][COLOR=#0000ff][FONT=Consolas][SIZE=2][COLOR=#0000ff]for[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2](i=num;i!=0;i--)[/SIZE][/FONT]
[SIZE=2][FONT=Consolas]{[/FONT][/SIZE]
[SIZE=2][FONT=Consolas]fibo(num);[/FONT][/SIZE]
[SIZE=2][FONT=Consolas]}[/FONT][/SIZE]
[SIZE=2][FONT=Consolas]system([/FONT][/SIZE][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#a31515][FONT=Consolas][SIZE=2][COLOR=#a31515][FONT=Consolas][SIZE=2][COLOR=#a31515]"PAUSE"[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2]);[/SIZE][/FONT]
[/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#0000ff][FONT=Consolas][SIZE=2][COLOR=#0000ff][FONT=Consolas][SIZE=2][COLOR=#0000ff]return[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2] EXIT_SUCCESS;[/SIZE][/FONT]
[SIZE=2][FONT=Consolas]}[/FONT][/SIZE]
[/SIZE][/FONT]
```
 
can someone tell me what am i doing wrong? I've added a loop to my code but now im getting a stack overflow?! O_O
Recursions are giving me a major headache.

---

### Post by Arndt on 2011-05-05
> **Ashtarias said:**
> ```
[FONT=Consolas][SIZE=2][COLOR=#0000ff][FONT=Consolas][SIZE=2][COLOR=#0000ff]
[SIZE=2][FONT=Consolas][COLOR=#0000ff]#include[/COLOR][/FONT][/SIZE][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#a31515][FONT=Consolas][SIZE=2][COLOR=#a31515][FONT=Consolas][SIZE=2][COLOR=#a31515]<iostream>[/COLOR][/SIZE][/FONT]
[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#0000ff][FONT=Consolas][SIZE=2][COLOR=#0000ff][FONT=Consolas][SIZE=2][COLOR=#0000ff]using[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#0000ff][FONT=Consolas][SIZE=2][COLOR=#0000ff][FONT=Consolas][SIZE=2][COLOR=#0000ff]namespace[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2] std;[/SIZE][/FONT]
[/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#0000ff][FONT=Consolas][SIZE=2][COLOR=#0000ff][FONT=Consolas][SIZE=2][COLOR=#0000ff]int[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2] fibo([/SIZE][/FONT][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#0000ff][FONT=Consolas][SIZE=2][COLOR=#0000ff][FONT=Consolas][SIZE=2][COLOR=#0000ff]int[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2] n)[/SIZE][/FONT]
[SIZE=2][FONT=Consolas]{[/FONT][/SIZE]
 
[/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#0000ff][FONT=Consolas][SIZE=2][COLOR=#0000ff][FONT=Consolas][SIZE=2][COLOR=#0000ff]int[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2] sum=n;[/SIZE][/FONT]
[/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#0000ff][FONT=Consolas][SIZE=2][COLOR=#0000ff][FONT=Consolas][SIZE=2][COLOR=#0000ff]if[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2](n==0)[/SIZE][/FONT]
[SIZE=2][FONT=Consolas]{[/FONT][/SIZE]
[/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#0000ff][FONT=Consolas][SIZE=2][COLOR=#0000ff][FONT=Consolas][SIZE=2][COLOR=#0000ff]return[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2] 0;[/SIZE][/FONT]
[SIZE=2][FONT=Consolas]}[/FONT][/SIZE]
[/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#0000ff][FONT=Consolas][SIZE=2][COLOR=#0000ff][FONT=Consolas][SIZE=2][COLOR=#0000ff]else[/COLOR][/SIZE][/FONT]
[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2]{[/SIZE][/FONT]
[SIZE=2][FONT=Consolas]sum=fibo(n-1)+fibo(n-2);[/FONT][/SIZE]
[SIZE=2][FONT=Consolas]cout<<sum<<[/FONT][/SIZE][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#a31515][FONT=Consolas][SIZE=2][COLOR=#a31515][FONT=Consolas][SIZE=2][COLOR=#a31515]" "[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2];[/SIZE][/FONT][/SIZE][/FONT]
[FONT=Consolas][SIZE=2]return sum;
[SIZE=2][FONT=Consolas]}[/FONT][/SIZE]
[/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#0000ff][FONT=Consolas][SIZE=2][COLOR=#0000ff][FONT=Consolas][SIZE=2][COLOR=#0000ff][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2] 
[SIZE=2][FONT=Consolas]}[/FONT][/SIZE]
 
 
[/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#0000ff][FONT=Consolas][SIZE=2][COLOR=#0000ff][FONT=Consolas][SIZE=2][COLOR=#0000ff]int[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2] main()[/SIZE][/FONT]
[SIZE=2][FONT=Consolas]{[/FONT][/SIZE]
[/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#0000ff][FONT=Consolas][SIZE=2][COLOR=#0000ff][FONT=Consolas][SIZE=2][COLOR=#0000ff]int[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2] i;[/SIZE][/FONT]
[/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#0000ff][FONT=Consolas][SIZE=2][COLOR=#0000ff][FONT=Consolas][SIZE=2][COLOR=#0000ff]int[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2] num;[/SIZE][/FONT]
[SIZE=2][FONT=Consolas]cout<<[/FONT][/SIZE][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#a31515][FONT=Consolas][SIZE=2][COLOR=#a31515][FONT=Consolas][SIZE=2][COLOR=#a31515]"Enter a number: "[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2];[/SIZE][/FONT]
[SIZE=2][FONT=Consolas]cin>>num;[/FONT][/SIZE]
[/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#0000ff][FONT=Consolas][SIZE=2][COLOR=#0000ff][FONT=Consolas][SIZE=2][COLOR=#0000ff]for[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2](i=num;i!=0;i--)[/SIZE][/FONT]
[SIZE=2][FONT=Consolas]{[/FONT][/SIZE]
[SIZE=2][FONT=Consolas]fibo(num);[/FONT][/SIZE]
[SIZE=2][FONT=Consolas]}[/FONT][/SIZE]
[SIZE=2][FONT=Consolas]system([/FONT][/SIZE][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#a31515][FONT=Consolas][SIZE=2][COLOR=#a31515][FONT=Consolas][SIZE=2][COLOR=#a31515]"PAUSE"[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2]);[/SIZE][/FONT]
[/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#0000ff][FONT=Consolas][SIZE=2][COLOR=#0000ff][FONT=Consolas][SIZE=2][COLOR=#0000ff]return[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2] EXIT_SUCCESS;[/SIZE][/FONT]
[SIZE=2][FONT=Consolas]}[/FONT][/SIZE]
[/SIZE][/FONT]
```
 
can someone tell me what am i doing wrong? I've added a loop to my code but now im getting a stack overflow?! O_O
Recursions are giving me a major headache.

The base case for n = 1 seems to have disappeared.

And please indent your source code; it's hard to read when left adjusted.

---

### Post by Ashtarias on 2011-05-05
```
 
#include <iostream>
using namespace std;
int fibo(int n)
{
[INDENT]int sum=n;
if(n==0)
{
[INDENT]return 0;
[/INDENT]}
else if(n==1)
{
[INDENT]return 1;
[/INDENT]}
else
{
[INDENT]sum=fibo(n-1)+fibo(n-2);
cout<<sum<<" ";
[/INDENT]}
return sum;
[/INDENT]}
 
 
int main()
{
[INDENT]int i;
int num;
cout<<"Enter a number: ";
cin>>num;
for(i=num;i!=0;i-=1)
{
[INDENT]fibo(num);
[/INDENT]}
system("PAUSE");
return EXIT_SUCCESS;
[/INDENT]}

```
 
My apologies about the source code, i just copied and pasted it into the reply box.
 
I've added in the base case and while i do not get a stackoverflow anymore, i get a very wierd output that seems to show the fibonacci number sequence seperated by 1 and 2s. E.g **1 2 **1 **3** 1 2 5 1 2 1 3 8 1 2 1 3 1 2 5 1 3 1 2 1 3 1 2 5 1 2 1 3 8 **21 ......**ending with 89.(i entered the number 11, so the answer is technically correct, just intersparsed with lots of random digits)
 
Also, why do i actually need a base case for n==1? Wouldn't the function end when end ==0? if i add a base case that states n==1, the function will end when n==1 and will never actually go down to n==0?
 
Sorry about my endless questions, but this recursion thing has really got me stumped.

---

### Post by simeon87 on 2011-05-05
> **Ashtarias said:**
> ```
 
#include <iostream>
using namespace std;
int fibo(int n)
{
[INDENT]int sum=n;
if(n==0)
{
[INDENT]return 0;
[/INDENT]}
else if(n==1)
{
[INDENT]return 1;
[/INDENT]}
else
{
[INDENT]sum=fibo(n-1)+fibo(n-2);
cout<<sum<<" ";
[/INDENT]}
return sum;
[/INDENT]}
 
 
int main()
{
[INDENT]int i;
int num;
cout<<"Enter a number: ";
cin>>num;
for(i=num;i!=0;i-=1)
{
[INDENT]fibo(num);
[/INDENT]}
system("PAUSE");
return EXIT_SUCCESS;
[/INDENT]}

```
 
My apologies about the source code, i just copied and pasted it into the reply box.
 
I've added in the base case and while i do not get a stackoverflow anymore, i get a very wierd output that seems to show the fibonacci number sequence seperated by 1 and 2s. E.g **1 2 **1 **3** 1 2 5 1 2 1 3 8 1 2 1 3 1 2 5 1 3 1 2 1 3 1 2 5 1 2 1 3 8 **21 ......**ending with 89.(i entered the number 11, so the answer is technically correct, just intersparsed with lots of random digits)

You are now printing output in your fibo function but you're also calling the function multiple times. That means you'll be calling the function many times and you'll be getting many partial results while the fibo function is computing. A better way would be to let fibo compute the number and then to print the value in main(). So you'd get:

- Compute fibo(0) and print it.
- Compute fibo(1) and print it.
- Compute fibo(2) and print it.
- ...
- Compute fibo(n) and print it.

So you don't print the values while it's computing but only the final values. That way you'll get the Fib. sequence as you'd expect.
 
> **Ashtarias said:**
> Also, why do i actually need a base case for n==1? Wouldn't the function end when end ==0? if i add a base case that states n==1, the function will end when n==1 and will never actually go down to n==0?

The reason is that you have two base cases in the sequence: for fibo(0) the value is 0 (predefined) and for fibo(1) the value is 1 (predefined). You can see this when you're calculating fibo(2). You do a recursive call for fibo(n - 1) and for fibo(n - 2). When n = 2 this means you're doing a fibo(1) and a fibo(0) call. The Fibonacci sequence is defined as starting with the number 0 and 1. So those two values are your base cases.

The function will go to 0 but only when fibo(0) is called. And as you can see, that does happen. The function will also be called with fibo(1) and then you have to return the value 1 (because that's how the sequence is defined).

---

### Post by dwhitney67 on 2011-05-05
> **simeon87 said:**
> You are now printing output in your fibo function but you're also calling the function multiple times. That means you'll be calling the function many times and you'll be getting many partial results while the fibo function is computing. A better way would be to let fibo compute the number and then to print the value in main().

Correct.

Just in case partial results are desirable, I threw this together:
```

#include <iostream>
#include <string>

#ifdef DEBUG
        #define PRT_DBG(n)   std::cout << (n) << " "
#else
        #define PRT_DBG(n)
#endif


int fibo(const int n)
{
   if (n == 0)
   {
      PRT_DBG(0);
      return 0;
   }
   else if (n == 1)
   {
      PRT_DBG(1);
      return 1;
   }

   int sum = fibo(n - 1) + fibo(n - 2);

   PRT_DBG(sum);

   return sum;
}


int main()
{
   int num;

   std::cout << "Enter a number: ";
   std::cin  >> num;
   std::cin.ignore(1024, '\n');

   for (int i = 0; i <= num; ++i)
   {
      std::cout << fibo(i) << " ";
   }
   std::cout << std::endl;

   std::string nl;
   std::cout << "\nPress <return> to continue...";
   std::getline(std::cin, nl);

   return EXIT_SUCCESS;
}

```

To display partial results:
```

g++ -DDEBUG fibo.cpp -o fibo

```

---

### Post by Ashtarias on 2011-05-05
I pretty much understand recursions now but i just need a quick clarification on the base cases.
 
```

f(7)=f(7-1)+f(7-2)
=f(6) + f(5)
={f(6-1)+f(6-2)} + {f(5-1)+f(5-2)}
={f(5)+f(4)} + {f(4) + f(3)}
={f(5-1)+f(5-2)} + {f(4-1)+f(4-2)} + {f(4-1) + f(4-2)}+{f(3-1) + f(3-2)}
={f(4)+f(3)} + {f(3)+f(2)} + {f(3)+f(2)} + {f(2)+f(1)}
={f(4-1)+f(4-2)} + {f(3-1)+f(3-2)} + {f(3-1)+f(3-2)} + {f(2-1)+f(2-2)} + {f(3-1)+f(3-2)} + {f(2-1)+f(2-2)} + {f(2-1)+f(2-2)}+1
={f(3)+f(2)}+{f(2)+1}+{f(2)+1}+{1+0}+{f(2)+1}+{1+0}+{1+0}+1
=f(3)+f(2)+f(2)+f(2)+f(2)+7
={f(3-1)+f(3-2)} + {f(2-1)+f(2-2)}+{f(2-1)+f(2-2)}+{f(2-1)+f(2-2)}+{f(2-1)+f(2-2)}+7
={f(2)+1}+{1+0}+{1+0}+{1+0}+{1+0}+7
={f(2)}+12
={f(2-1)+f(2-2)}+12
=1+0+12
=13

```
 
While i understand what simeon 87 says about having to set the base cases for n==0 and n==1, what do the base cases actually do with the value returned?I've read that the return value simply returns the value stated back to the calling function.
 
So in the case of the code above,am i right in saying that whenever the calculations come across f(1) and f(0), it will return the value 1 and 0 respectively to the calling function [i.e f(7) for the 7th fibonacci number] where the values will be stored and used to calculate the final value?

---

### Post by simeon87 on 2011-05-05
> **Ashtarias said:**
> I pretty much understand recursions now but i just need a quick clarification on the base cases.
 
```

f(7)=f(7-1)+f(7-2)
=f(6) + f(5)
={f(6-1)+f(6-2)} + {f(5-1)+f(5-2)}
={f(5)+f(4)} + {f(4) + f(3)}
={f(5-1)+f(5-2)} + {f(4-1)+f(4-2)} + {f(4-1) + f(4-2)}+{f(3-1) + f(3-2)}
={f(4)+f(3)} + {f(3)+f(2)} + {f(3)+f(2)} + {f(2)+f(1)}
={f(4-1)+f(4-2)} + {f(3-1)+f(3-2)} + {f(3-1)+f(3-2)} + {f(2-1)+f(2-2)} + {f(3-1)+f(3-2)} + {f(2-1)+f(2-2)} + {f(2-1)+f(2-2)}+1
={f(3)+f(2)}+{f(2)+1}+{f(2)+1}+{1+0}+{f(2)+1}+{1+0}+{1+0}+1
=f(3)+f(2)+f(2)+f(2)+f(2)+7
={f(3-1)+f(3-2)} + {f(2-1)+f(2-2)}+{f(2-1)+f(2-2)}+{f(2-1)+f(2-2)}+{f(2-1)+f(2-2)}+7
={f(2)+1}+{1+0}+{1+0}+{1+0}+{1+0}+7
={f(2)}+12
={f(2-1)+f(2-2)}+12
=1+0+12
=13

```
 
While i understand what simeon 87 says about having to set the base cases for n==0 and n==1, what do the base cases actually do with the value returned?I've read that the return value simply returns the value stated back to the calling function.
 
That is correct. The base cases serve to stop the recursion. As you can see fibo(n) is calling fibo(..) again with a smaller value of n. At some point the recusion has to end, otherwise fibo would keep calling itself. So when fibo(0) or fibo(1) is called, it returns the value 0 or 1 and then that value is given back to the earlier call of fibo(..).

> **Ashtarias said:**
> So in the case of the code above,am i right in saying that whenever the calculations come across f(1) and f(0), it will return the value 1 and 0 respectively to the calling function [i.e f(7) for the 7th fibonacci number] where the values will be stored and used to calculate the final value?

They won't return it to the call of f(7) but to the call just before that. So when you call f(2), it will call f(1) and f(0). Both of these will return a value to f(2) which it will use in computing the value of f(2). So f(7) calls f(6) and f(5), and f(5) will call f(4) and f(3) until you eventually reach the base cases of f(1) and f(0). That's where the recursion will end and then the values are returned to the earlier calls of f(...). Each call then returns a value to the previous call of f(..) until ultimately the value of f(7) can be computed. The computation then ends and the final value of f(7) is returned.

---

### Post by Ashtarias on 2011-05-05
```
 
#include <iostream>
 
using namespace std;
 
string thanks(int thk)
{
[INDENT]cout<<" THANK YOU SO MUCH!!"<<endl;
thanks(thk-1);//Infinite loop ftw =)
return 0;
[/INDENT]}
 
int main()
{
[INDENT]cout<<"YAY I UNDERSTAND RECURSIVE FIBONACCI SEQUENCES NOW!!!";
thanks(1);
system("PAUSE");
return EXIT_SUCCESS;
[/INDENT]}
&#12288;

```
 
 
Thanks for all your help guys i've finally gotten a grasp on this tricky recursive concept.Couldn't have done it without ya'll.=)

---

### Post by vishalaprasad on 2011-05-13
the same way as the fibonacci sequence, can anyone write a program that calculates the factorial of a number, eg, 2 files, one with main.cpp   and the other factorial.cpp  . the main is the parent and the factorial will be the child process, use pipes method to link. please help, dont know where to start

---

### Post by lisati on 2011-05-13
> **vishalaprasad said:**
> the same way as the fibonacci sequence, can anyone write a program that calculates the factorial of a number, eg, 2 files, one with main.cpp   and the other factorial.cpp  . the main is the parent and the factorial will be the child process, use pipes method to link. please help, dont know where to start

There are many people here who could probably do this, but keep in mind that we won't actually do your homework for you. I'm not sufficiently competent in C++ to start the ball rolling beyond suggesting that you make sure you understand the question.

Thread closed with the suggestion that vishalaprasad does what they can, and start a new thread asking for help when they get stuck.

---

