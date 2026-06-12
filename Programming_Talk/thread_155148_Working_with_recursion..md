---
title: "Working with recursion."
date: 2006-04-04
forum: Programming Talk
---

### Post by DravenHavok on 2006-04-04
So I'm trying to learn recursion on the C language, and I found a cool mathematical problem, and I'm stuck. I think I understand the math part well, so I'm guessing it's my logic that's messed up. So if anyone has any comments or ideas as of why this program doesn't work I'd appreciate it. Thanks to all. 

```

#include <stdio.h>

int gcd (int);

int main()

{
	int divisor=0;
	
	divisor = gcd( divisor );
	
	printf("The greatest common divisor is %d.\n",&divisor);
	
return 0;
}

int gcd ( int divisor)
{
	int x = 0, y = 0, result = 0;

	printf("Please enter two integers.\n");
	scanf( "%d%d", &x, &y);
	
	if (y == 0)
		result = x;
	if (y != 0)
		result = x % y;
	
	return result;
} 


```

PS. I know I'm probably messing up on the parameters of the function, maybe that would help figure out what's wrong. Thanks y'all.

---

### Post by LordHunter317 on 2006-04-04
Well, you never recurse, for starters.  To recurse, the function must call itself.  None of your functions do that.

What you want to do is ask for hte numbers in main, and the have gcd() call itself until a correct result is found.  

Without giving it away, you should return the result of the recursive call, i.e.:```
return gcd(x, y);  /* inside gcd */
```and the value will just pass all the way up.

I'd post code but it's impossible to do without giving it away.

If you're having troubles, an algorithms book might be a very good purchase.

---

### Post by xenmax on 2006-04-04
i am sorry, but i can't see any recursion in your code?

---

### Post by tribaal on 2006-04-04
Hum... 

I'll try to give you as much help as I can.

First thing that struck me: your program is not recursive ;)
A recursive function should call itself from within itself. Might sound kinf of creepy, but it goes something like:

```
int recursive( int number){
    if number == 1{
          return 0;
    }else{
         return recursive(number--);
    }
}
```

Well of course, my example has absolutely no practical use. But it's recursive.
So your gdc() function should at some point call itself, for it to be a recursive function.

I can't remember the maths to get the largest comon divisor of two numbers, but if you explain it to me in maths, I can try to explain it in C :)

---

### Post by LordHunter317 on 2006-04-04
[QUOTE=tribaal]I can't remember the maths to get the largest comon divisor of two numbers, but if you explain it to me in maths, I can try to explain it in C :)[/QUOTE]For an algorithim that's this simple, doing this would net him nothing, which is why I didn't do it.

If he can't figure it out on his own, then he has more fundamental gaps in his knowledge (no offense) and really needs to go read an algorithms book.  This method for finding GCD and it's recursive implementation are covered in every algorithms book on the planet, in more detail, with more context.

---

### Post by hod139 on 2006-04-04
This is a correct non-recursive form of finding the GCD
```

int GCD(int a, int b)
{
    int r;

    while(b > 0){
      r = a % b;
      a = b;
      b = r;
    }

    return(a);
}

``` 
Hopefully you can see how to convert this into a recursive function.  

For another similar easy recursive function, finding the nth Fibonacci number is a common example (from wikipedia):
```

int fib(int n) {
  if (n < 2)
    return n;
  else
    return fib(n-1) + fib(n-2);
}
``` Here you can clearly see how the function calls itself.

If by tomorrow you still can't get a reursive form of GCD, post back and I will give you the answer. Often times struggling with a problem for a while helps you to remember and learn a lot more than just seeing an answer. As others have said it is hard to help you with your GCD example without simply giving you the answer. Hopefully another example and the non-recursive GCD shed some light for you.

---

### Post by DravenHavok on 2006-04-04
Yes, thank you. I don't want an answer, I want to learn. But I see what you mean. I knew the function had to call itself, I just didn't know if I was doing it right. Apparently not. But I don't quite see it yet, I'll sit here for a while and think about it. Thank you again.

---

### Post by johnnymac on 2006-04-04
Draven...

Here's a quick how-to on working with recursion.  Now, one thing to think about is recursion is very educational and is avoided at all costs in the professional world because of it's high overhead.  So.......here's the how to

[http://personal.vsnl.com/erwin/recursion.htm](http://personal.vsnl.com/erwin/recursion.htm)

---

### Post by rplantz on 2006-04-04
Here's a way to think about recursion.

Say that you want to solve the problem for n and you know two things:
1. The result of the "base case", for example n = 0.
2. How to find the result for n if there is a "magic function" that will give you the result for n-1.

The algorithm is then
```

if base case
   then
      return with the result
   else
      call the "magic function" with n-1 as the argument
      compute the nth case from the (n-1)th result
      return the nth case result

```

Once you have figured out this algorithm, realize that you have yourself designed the "magic function." It is simply your recursive function called with n-1 instead of n.

Well, there is no magic here, just faith that your algorithm will work for n-1. But the "magic function" idea might help prevent a headache from thinking too much about recursion.

---

### Post by DravenHavok on 2006-04-04
OK, so the function has to call it self over and over and over again until it finds the GCD. OK...I'm getting it...little by little.

---

### Post by DravenHavok on 2006-04-04
[QUOTE=johnnymac]Draven...

Here's a quick how-to on working with recursion.  Now, one thing to think about is recursion is very educational and is avoided at all costs in the professional world because of it's high overhead.  So.......here's the how to

[http://personal.vsnl.com/erwin/recursion.htm](http://personal.vsnl.com/erwin/recursion.htm)[/QUOTE]


Thank you sir, I'll look at that.

---

### Post by johnnymac on 2006-04-05
Yes.....the function gets called over and over until the "magic" number is found.  Also some other common solutions that involve recursion are factorial, fibonacci, and the towers of hanoi (my favorite).

It's pretty fun when you start digging into it and if you want an interesting one - do the towers of hanoi - I've got an example somewhere of one I did in a java program when I was in school....gawd knows where it is now

---

### Post by DravenHavok on 2006-04-05
OK so I think I have the function part figured out. THe function calls itself everytime to do the modulus operation so that it finds the GCD, in accordance to Euclids Algorithm, HOWEVER, something isn't working right. This doesn't have anything to do with the algorithm part, but rather a logic error. I've highlighted in in red:

```

#include <stdio.h>

int gcd (int x, int y);

int main()

{
	int result;
	
	[COLOR="Red"]**_result = gcd();_**[/COLOR]
	
	printf("The greatest common divisor is %d.\n", &result);
	
return 0;
}

int gcd (int x, int y)

{
	int ans;

	printf("Please enter two integers.\n");
	scanf( "%d%d", &x, &y);
	
	if ((x % y) == 0)
		ans = y;
	else 
		ans = gcd(y, x % y );
	
	return (ans);
}


```


I know there's something supposed to go in there, and examples I've seen use something like number or int. It gives me a syntax error when I try to do that though...
I know it's probably something really simple, but I just can't see it.
Thank you SO very much for all the helpful hints. I'm enjoying this too much. ^_^

---

### Post by DravenHavok on 2006-04-05
[QUOTE=johnnymac]Yes.....the function gets called over and over until the "magic" number is found.  Also some other common solutions that involve recursion are factorial, fibonacci, and the towers of hanoi (my favorite).

It's pretty fun when you start digging into it and if you want an interesting one - do the towers of hanoi - I've got an example somewhere of one I did in a java program when I was in school....gawd knows where it is now[/QUOTE]


I used to play Towers of Hanoi when I was little. Ah the memories...I think I'l try that when I'm done with this one though...

---

### Post by sphinx on 2006-04-05
Disclaimer: I havent done anything in c for quite a while.

But I can see where your going wrong. Your attempting to call a function called gcd(), but you dont have a function called gcd(), you only have a function called gcd(int x,inty). They have diffrent signitures you see.

Also, as the gcd function you do have may be called miltiple time by itself, it would probably be a good idea to put the number prompting bit out of the gcd function and into the main function like this:
```

#include <stdio.h>

int gcd (int x, int y);

int main()

{
	int result;
	[COLOR="Red"][B]int x,y;
	printf("Please enter two integers.\n");
	scanf( "%d%d", &x, &y);
	
	result = gcd(x,y);[/B][/COLOR]
	
	printf("The greatest common divisor is %d.\n", &result);
	
return 0;
}

int gcd (int x, int y)

{
	int ans;
	
	if ((x % y) == 0)
		ans = y;
	else 
		ans = gcd(y, x % y );
	
	return (ans);
}


```

As per this disclaimer, I'm not sure if I've got the int x,y decleration correct in the main function. Hope this helps.

It might be a good excercise to put a printf in the gcd function to see what effect printing something within a recursive function has.

---

### Post by DravenHavok on 2006-04-05
Thank you sphinx, that solved my syntax problems, however, when I tried to run it it gave me a weird number. Weird like "-106957386756" kind of weird. So I'm guessing something's still wrong. Thank you though.

---

### Post by rplantz on 2006-04-05
[QUOTE=johnnymac]Draven...

Here's a quick how-to on working with recursion.  Now, one thing to think about is recursion is very educational and is avoided at all costs in the professional world because of it's high overhead.[/QUOTE]

I was a programmer in industry for ten years before switching to academia. I still find it weird that so many of my colleagues push recursion so much. Yes, the algorithms for certain types of problems look very clean. But I "grew up" as an electrical engineer, then became an assembly language programmer. So I know what's going on beneath those clean looking C programs. Yikes!

One of the assignments I used to give in my assembly language class was to trace through the stack in a recursive program. Doesn't look so clean from there.

Oh well, recursive programming is good for teaching about certain types of problems.

---

### Post by sphinx on 2006-04-05
It has to do with an address of (&) operator in the wrong spot. Have a look at how your refrencing and derefrencing your variables.

---

### Post by LordHunter317 on 2006-04-05
[QUOTE=rplantz]I was a programmer in industry for ten years before switching to academia. I still find it weird that so many of my colleagues push recursion so much. Yes, the algorithms for certain types of problems look very clean.[/quote]For most classes of software, writing easy to understand code is better than fast code.  The vast majority of software doesn't care, and when it does care, it's only small portions of code that care.

> So I know what's going on beneath those clean looking C programs. Yikes!It wouldn't be impossible, though perhaps painful, to implement a C-compiler that optimized away the tail call (at least for not C-args functions, varargs would be harder).  The code may not be as fast a tuned loop in all situations, but it would avoid all the practical negative limitations of recursive calls.  Frankly, if you're at the point you're hand-tuning loops, you wouldn't care anyway.

FWIW, MS' CIL does have a tail call instruction, .tail IIRC.  Unfortunately due to implementation details, it's much slower than regular calls.  Mono's doesn't have this limitation and it's tail calls are very fast.

> One of the assignments I used to give in my assembly language class was to trace through the stack in a recursive program. Doesn't look so clean from there.They should already know that because they should be drawing the stacks (or trees, for tree recursive programs) as a practical demonstration of both how they work and how they're called.  It's also crucial to understand how to convert a recursive program to an iterative one of any sort. Here I mean interative in the mathematical / functional sense: each step can be calculated independent of each other and the process can be stopped/restarted at any moment).

If they don't already understand that, they don't understand recursion correctly.

---

### Post by hod139 on 2006-04-05
[quote=DravenHavok]Thank you sphinx, that solved my syntax problems, however, when I tried to run it it gave me a weird number. Weird like "-106957386756" kind of weird. So I'm guessing something's still wrong. Thank you though.[/quote] 
Your printf statement is incorrect.  Since your question was about recursion, I'll just give you the answer to this problem.  
Here is your relevant code causing the problem:
```

result = gcd(x,y);
printf("The greatest common divisor is %d.\n", &result);

``` 
In the above code, you set the int result to the return value of your gcd(int, int) function, which also (correctly) happens to be an int. The problem is when you try to print the result. The argument you are giving printf is 
```
&result
``` which is the memory address of the variable result, not the value of the int. Since you are interested in the value, not the memory location, you should simply pass result as an argument, not &result. 

After making that minor change to printing, you should see that you basically have it. Good job. But, now it is time to nitpick 8)

The problem is that your method is not very robust to unexpected/bad input. There are 3 special cases to this algorithm that you have to handle:
1. x = y = 0
2. x < 0 or y < 0
3. x = 0 and y != 0 (and vice versa)

I was going to write the answer to handling this bad input, but I figured since this seems to be a learning thread I'll let you try and get it. If you need help with handling any of these special cases, let me know and I'll post my solution.

**Edit:** I should add that case 1 is really special.  The GCD is undefined for that input.  Your method should be able to say "Whoa, this input doesn't make any sense, what are you trying to do to me.  I'm not even going to try and run the algorithm on it!" (or something along those lines. :) )
For case 2, just make sure the result is always postive.  
For case 3, the result is the non-zero value.  So if x = 0. the result is y, and if y = 0, the result is x.

---

### Post by rplantz on 2006-04-05
[QUOTE=LordHunter317]For most classes of software, writing easy to understand code is better than fast code.  The vast majority of software doesn't care, and when it does care, it's only small portions of code that care.[/quote]
Very true. The example I often use is error handling code. One assumes that it will seldom, if ever, be executed.

If I may brag a bit, I had a friend who was a manager at two places where I worked. He remained at each company for several months after I left. He said that I was the only programmer he knew that other programmers didn't complain about my code after I left. One of the biggest compliments I ever got.

> 
They should already know that because they should be drawing the stacks (or trees, for tree recursive programs) as a practical demonstration of both how they work and how they're called.  It's also crucial to understand how to convert a recursive program to an iterative one of any sort. Here I mean interative in the mathematical / functional sense: each step can be calculated independent of each other and the process can be stopped/restarted at any moment).

If they don't already understand that, they don't understand recursion correctly.

"If I had a nickel for everytime I've said the same thing to students..." I always drew pictures on the board. I handed out worksheets in class and had students work through the pictures with me as I walked through the code on the board. In lab, I would bring up the code in a debugger (using an overhead projector) and walk through it while maintaining a drawing on the board. (I taught at a university where we had no teaching assistants, so I taught the labs myself.)

Would you care to guess how many students have drawn a picture when they came to my office or called me over for help in the lab? Decades of working with this stuff, and I can't figure it out without drawing a picture. Yet at least 95% of students seem to think they can. ](*,) (One more reason to be thankful for my retirement. :))

---

### Post by LordHunter317 on 2006-04-05
[QUOTE=rplantz]Would you care to guess how many students have drawn a picture when they came to my office or called me over for help in the lab?[/quote]The circuit schematic is always worth 10-25% of the grade in my EE classes, I don't see why CS should be any different.

---

### Post by rplantz on 2006-04-05
[QUOTE=LordHunter317]The circuit schematic is always worth 10-25% of the grade in my EE classes, I don't see why CS should be any different.[/QUOTE]

Again, I totally agree with you. Unfortunately, I worked at a university where we were overworked and not given a budget for hiring graders or teaching assistants. It often came down to a time issue (my time).

In addition, CS attracts many students who are not prepared to work hard. Everybody knows that engineering, math, physics, etc. require lots of hard work. CS is a new discipline, and lots of people don't know what it involves.

I finally learned to tell students that I would not help them until they drew a diagram. And when I graded programming projects, the **first** 10 - 20% of the grade was based on documentation. I would not continue unless the documentation was at least adequate. (The next thing it had to do was compile without errors.)

And (sorta) back to the topic of this thread. The message here is that you should not be trying to write code until you can draw a diagram and/or explain in a natural language what your code is supposed to do.

---

### Post by DravenHavok on 2006-04-11
Hey, thanks for the help. I'm sorry if I haven't replied, but I'm uber busy with making a web page that I've left my c programing for later. Thanks you all who helped me learn.

---

