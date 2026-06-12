---
title: "Prepping for C++ Test Functions."
date: 2007-10-16
forum: Programming Talk
---

### Post by TreeFinger on 2007-10-16
Hey, all! I got a test in my C++ class tomorrow. I have a little study guide from the teacher. I am wondering if someone could verify that what I am thinking is correct for a few of the programming problems. I'll start out with the first one.

"Write a C++ function named sum1 that calculates and returns the value of the following expression:

1/1 + 1/3 + 1/5 + 1/7 + ... + 1/(2n - 1) + 1/(2n + 1)

n - parameter of the function, n>1, int data type.
Write a main function that calls the function sum1.

This problem confuses me a little. I wrote out what I thought would be the correct code in Notepad++ but I can't compile it because I have no compiler on my windows partition :( so there may be some syntax errors. Do you guys find this to be the solution for the problem?

```

#include <iostream>
using namespace std;

double sum1(int);

int main() {
	int n;
	cout << "enter n: ";
	cin >> n;
	cout << "Entering function sum1.\n";
	sum1(n);
	cout << "Back in main function.\n";
	return 0;
}

double sum1(int n) {
	double returnval = 0;
	for ( int i = 1; i <= n; i++ ) {
		returnval = returnval + ( 1 / ( ( 2 * i ) - 1 ) );
	}
	return returnval + ( 1 / ( ( 2 * n ) + 1 ) );
}

```

I am not sure about returning values from a function, so that is one thing that could be majorly wrong :x

---

### Post by xtacocorex on 2007-10-16
Crap, I'm not thinking right today
 
I thought you did it wrong, but I was incorrect.
 
You aren't printing the answer, you're calling the function, but not setting it equal to anything in main().

---

### Post by TreeFinger on 2007-10-16
So should I change the line in the main function where I call the sum1 function to..
```

cout << sum1(n); << endl;

```

---

### Post by xtacocorex on 2007-10-16
Instead of giving you the answer, I will pose a question.  Will that output the answer, if yes, then I'd say it'd be ok; if not, what could you do to get it to work. 
 
:)

---

### Post by TreeFinger on 2007-10-16
Well I know one way to output an answer would to put an output statement inside the function. I am thinking that using cout << functionname(); will output the return value, but I am not sure how the return object ( Is that what I should call it?) works. I think I am going to log onto ubuntu and try some compiling :)

---

### Post by aks44 on 2007-10-16
If you need a compiler just to check your syntax, one of the most standard-abiding C++ compilers out there (Comeau) allows you to [compile small snippets online]("http://www.comeaucomputing.com/tryitout/"). You won't be able to test the result though.


Back to your problem, the function works. Not the best solution though. Hint: use **for (int i=0; i<=n; ++i)** and adjust both your loop body and your return statement. :)

---

### Post by TreeFinger on 2007-10-16
aks44 - I don't see a difference between our two for statements. Just that I have post-increment and you have pre-increment. I don't see how that would make a difference. Please enlighten me :)

edit---

oh and you have i starting at 0. Let me think this through while I eat some lunch :)

---

### Post by TreeFinger on 2007-10-16
```

#include <iostream>
using namespace std;

double sum1(int);

int main() {
	int n;
	cout << "enter n: ";
	cin >> n;
	while ( n <= 1 ) {	//Input validation
		cout << "Enter integer greater than 1.\n";
		cin >> n;
	}
	cout << "Entering function sum1.\n";
	cout << sum1(n) << endl;
	cout << "Back in main function.\n";
	return 0;
}

double sum1(int n) {
	double returnval = 0;
	for ( int i = 1; i <= n; ++i ) {
		returnval = returnval + ( 1.0 / ( ( 2 * i ) - 1 ) );
		if ( i == n ) {
			returnval = returnval + ( 1.0 / ( ( 2 * n ) + 1 ) );
		}
	}
	return returnval;
}

```

This is the best I could come up with. I am not sure how I could make my function any more efficient? I hope you reply aks44 ! Anyone else see what I could do?

The change from my original code is I have input validation and I also added an if statement to add on the last value when i = n.

---

### Post by xtacocorex on 2007-10-16
Good work TreeFinger.  I only posed the question because I didn't want to give you the answer and from the look of it, you got it. :)

Good luck on the test!

---

### Post by Wybiral on 2007-10-16
> **aks44 said:**
> ... ++i ...

aks44, I'm curious what you think about pre and post increment operators. I've always thought the existence of both is a sloppy design decision so I used to use pre increment for everything, but recently I've started using post again just to make my code more familiar to other developers. IMO, pre is the only one that makes sense to use (because it has a clearly defined precedence), but post seems more popular (like in the classic "for(int i = 0; i < size; i++)"). You seem to have been developing in C++ for a while now, which do you prefer and why?

---

### Post by dwhitney67 on 2007-10-17
I generally use the pre-increment in loops, for both integers and iterators.  You can't use the post-increment on iterators.

Long ago when I programmed in C for the MC68030 using a derivative of Microware's OS-9 C compiler, it was more efficient to perform the pre-increment than the post-increment.  I was responsible for porting Microware's dis-assembler and C debugger to work on a diskless system, so I spent many days staring at 68030 opcodes.  The post-increment operation required one more instruction than the pre-increment.

Nowadays with better compilers and optimizers, it probably wouldn't make a difference which method you use.  If you have peers that are unfamiliar with pre-increment (or pre-decrement), educate them!

---

### Post by TreeFinger on 2007-10-17
Figure I'll share the other preparation question.

Write a C++ function named prod2 that calculates and returns the value of the following expression:

1/n * 1/(n-2) * 1/(n-2) * ... * 1/(n-k)

n, k - parameters of the function, n > k > 1, int data types.
Write a main function that calls the function prod2.

```

#include <iostream>

using namespace std;

double prod2(int n, int k);

int main() {
	int n, k;
	cout << "Enter 2 integers: ";
	cin >> n;
	cin >> k;
	while ( k <= 1 || n <= k ) {
		cout << "first number must be greater than second, both must be greater than 0.\n";
		cin >> n;
		cin >> k;
	}
	cout << prod2(n, k) << endl;

	return 0;
}

double prod2(int n, int k) {
	double returnResult = 1.0;
	for ( int i = 0; i <= k; ++i ) {
		returnResult = returnResult * ( 1.0 / ( n - i ) );
	}
	return returnResult;
}

```

Check it out. Hopefully I can do it tomorrow on a piece of paper :)

Any problems? I insist you inform me!

Took me a while to figure out why I kept getting 0 for the return result haha. Kept thinking it was a problem with the loop. I had returnResult initialized to 0! Duh!

---

### Post by mjwood0 on 2007-10-17
> **Wybiral said:**
> aks44, I'm curious what you think about pre and post increment operators. I've always thought the existence of both is a sloppy design decision so I used to use pre increment for everything, but recently I've started using post again just to make my code more familiar to other developers. IMO, pre is the only one that makes sense to use (because it has a clearly defined precedence), but post seems more popular (like in the classic "for(int i = 0; i < size; i++)"). You seem to have been developing in C++ for a while now, which do you prefer and why?

I'm not aks44, but I'll give my insight.  I too would be curious to their response.

Due to the nature of what I do, all code must be rigorously unit tested.  So, for the expression:
```
i < 7
```
we'd have to run a unit test for i = 6 and i = 7.  Basically, verify the -1 and equal conditions.

For the expression 
```
i <= 7
```
we'd have to run a unit test on i = 6, i = 7 and i = 8 to get full coverage.  Therefore, you'll often see code such as this:
```
for (i = 0; i < (SIZE + 1); i++)
```

While I agree that often times the pre-increment makes sense in loops, there is sometimes a hidden cost to the software such as this testing.  Using post increment gives us one less test to write and saves cost in the long run.  Also, to keep things more consistent throughout the code, we tend to use post increment universally.  

Just an oddball point of view.

---

### Post by Wybiral on 2007-10-17
> **dwhitney67 said:**
> I generally use the pre-increment in loops, for both integers and iterators.  You can't use the post-increment on iterators.

Long ago when I programmed in C for the MC68030 using a derivative of Microware's OS-9 C compiler, it was more efficient to perform the pre-increment than the post-increment.  I was responsible for porting Microware's dis-assembler and C debugger to work on a diskless system, so I spent many days staring at 68030 opcodes.  The post-increment operation required one more instruction than the pre-increment.

Nowadays with better compilers and optimizers, it probably wouldn't make a difference which method you use.  If you have peers that are unfamiliar with pre-increment (or pre-decrement), educate them!

Weird, I would think at the assembly level it would be the same (the "inc"/"dec" instructions). I guess it depends how the compiler handles them. But I have read that other languages, such as PHP, are slightly faster (by an operation or two) using pre-increment.

IMO, post-increment just doesn't make sense. Why would you ever need to post-increment? It would make more sense to explicitly define the precedence using parenthesis if you need it to increment afterward.

---

### Post by LaRoza on 2007-10-17
Get a portable compiler, [http://sourceforge.net/projects/devcpp-portable](http://sourceforge.net/projects/devcpp-portable), great for school or other random computers. Uses G++.

---

### Post by dwhitney67 on 2007-10-17
> **mjwood0 said:**
> I'm not aks44, but I'll give my insight.  I too would be curious to their response.

Due to the nature of what I do, all code must be rigorously unit tested.  So, for the expression:
```
i < 7
```
we'd have to run a unit test for i = 6 and i = 7.  Basically, verify the -1 and equal conditions.

For the expression 
```
i <= 7
```
we'd have to run a unit test on i = 6, i = 7 and i = 8 to get full coverage.  Therefore, you'll often see code such as this:
```
for (i = 0; i < (SIZE + 1); i++)
```

While I agree that often times the pre-increment makes sense in loops, there is sometimes a hidden cost to the software such as this testing.  Using post increment gives us one less test to write and saves cost in the long run.  Also, to keep things more consistent throughout the code, we tend to use post increment universally.  

Just an oddball point of view.
I don't quite understand your point?  The loops shown below exhibit the same result:

[PHP]#include <iostream>

using namespace std;

int main()
{
  int SIZE = 4;

  for ( int i = 0; i < (SIZE + 1); i++ )
  {
    cout << "i = " << i << endl;
  }

  for ( int i = 0; i < (SIZE + 1); ++i )
  {
    cout << "i = " << i << endl;
  }
}[/PHP]

A for-loop works like this:

1) initialize local value(s), if any
2) inspect conditional, and if 'false' exit loop
3) perform actions in body of for-loop
4) pre- or post-increment iterator(s)
5) return to step 2

Note that steps 4 and 5 (or should I say 2) are independent.  It doesn't matter if pre- or post-increment is used.  Now in a case like this, it would matter:

```
int i = 5;
int j = ++i;
```

Here, j would equal the value i, which is 6.

In this case,

```
int i = 5;
int j = i++;
```

j would equal 5, whereas i would equal 6.

---

### Post by hod139 on 2007-10-17
> **Wybiral said:**
> aks44, I'm curious what you think about pre and post increment operators. I've always thought the existence of both is a sloppy design decision so I used to use pre increment for everything, but recently I've started using post again just to make my code more familiar to other developers. IMO, pre is the only one that makes sense to use (because it has a clearly defined precedence), but post seems more popular (like in the classic "for(int i = 0; i < size; i++)"). You seem to have been developing in C++ for a while now, which do you prefer and why?

I'm not aks44, but I can answer this question.  Pre-increment and post-increment are different.
```

i++

```will copy i, increment i and return the copy (i not i+1)
```

++i

```increments i and returns i+1.

If "i" is a primitive type, the distinction is not really important.  However, if "i" is a more complex type (e.g. a complex class ) then the extra copy needed in the post-increment can become very expensive (cost of the copy constructor call).

> **dwhitney67 said:**
>   You can't use the post-increment on iterators.
This isn't true, you can do both pre and post.  However, as noted above, post-increment may be noticeable slower since you must copy the old iterator to return.

**Edit:** I should add, a good rule of thumb is to always use pre-increment or pre-decrement unless you explicitly want the copying behavior of the post-increment and post-decrement.

---

### Post by aks44 on 2007-10-17
> **hod139 said:**
> If "i" is a primitive type, the distinction is not really important.  However, if "i" is a more complex type (e.g. a complex class ) then the extra copy needed in the post-increment can become very expensive (cost of the copy constructor call).

+1


> **hod139 said:**
> a good rule of thumb is to always use pre-increment or pre-decrement unless you explicitly want the copying behavior of the post-increment and post-decrement.

+1

Not much to add to this. :D Those are the very reasons why by default I always use pre-in/de-crements (even on scalar types where it doesn't matter, I use them because of consistance with the rest of the code). Plus in templates, you don't know what the actual type will be so better play safe on the performance side.



> **Wybiral said:**
> recently I've started using post again just to make my code more familiar to other developers

As hod139 put it, there are very good reasons to prefer the "pre" version. The "post" being more popular only shows one thing IMO: most C++ programmers are clueless about these details. Again, I'll rant against C, where it actually doesn't matter which operator you use (since you can only use them on scalars). One more reason not to learn C before C++. (the never-ending crusade :p)

---

### Post by dwhitney67 on 2007-10-17
> **hod139 said:**
> 

[QUOTE=dwhitney67;3550720]Originally Posted by dwhitney67 View Post
You can't use the post-increment on iterators.

This isn't true, you can do both pre and post.
[/QUOTE]
You're right.  It must have been a previous experience I had with a non-conforming C++ compiler (on Solaris) back in the late '90s that lead me to believe that the post-increment could not be done.  But I do remember distinctly that it could not be done (at least back then).

---

### Post by Wybiral on 2007-10-17
Well that settles it, I'm switching back to pre-incrementing whether my fellow developers like it or not. It is really weird that I see post-increment used 90% of the time though (even in books and stuff).

BTW, Python doesn't have this problem :)

---

### Post by aks44 on 2007-10-17
> **Wybiral said:**
> I'm switching back to pre-incrementing whether my fellow developers like it or not.

If they're not aware of the problem at hand, educate them!
And if they are too stubborn to hear & understand your arguments, send them back to hell. :p


> **Wybiral said:**
> It is really weird that I see post-increment used 90% of the time though (even in books and stuff).

Again, in C code it doesn't matter since any decent compiler can optimize it out every time. The real problem is that most people think that C is *just* a subset of C++, and that what works for C also works for C++ (which is plain false of course).

[Herb Sutter's work]("http://gotw.ca/") is what "enlightened" me (and I really mean it!), way back in '98-99 on c.l.c++.m. He is one of the few who *understood* what C++ is all about (and IMHO way farther than what Bjarne Stroustrup ever dreamed) and made it available to the masses. If you're serious about C++, read *all* his books, you won't regret it. :) FWIW even after all those years this guy is still my *guru* (no pun intended), I still don't get everything he says.

Unfortunately not many people are as insightful as Herb Sutter, that's why crappy examples are the "norm". :(

---

### Post by mjwood0 on 2007-10-17
I think the real confusion here is that the fundamental difference in how they operate is often obscured by their most common usage.

For example, if you are simply incrementing the same value, they make no difference:
```
i++;
++i;
```

Both will increment i by 1.

However, if you are using them in an assignment statement, there is a vast difference in the underlying assembly.  However, as far as C is concerned, there is no difference in cost.

Pre-incrementing something is really acting on the direct operand.
```
j = ++i;
```
is actually equal to the following:
```
i += 1;
j = i;
```

On the other hand, post incrementing is not changing the direct operand.
```
j = i++;
```
is really the following:
```
j = i;
j += 1;
```

---

### Post by aks44 on 2007-10-17
> **mjwood0 said:**
> I think the real confusion here

Which confusion? The whole point is about "which one should you use when BOTH are correct?"... so there's no possible confusion IMHO.

> **mjwood0 said:**
> On the other hand, post incrementing is not changing the direct operand.
```
j = i++;
```
is really the following:
```
j = i;
j += 1;
```

You meant```
j = i;
i +=1;
```
Right? :p

(I really hope this was a typo, but that would explain your previous post about unit tests...)

---

### Post by j_g on 2007-10-17
Former posters have already pointed out the advantages of using pre, versus post, inc/dec. I concur 100% and see no need to repeat what they've already said. I'll just add a little more detail for anyone who may still be confused about the point being made.

I always use pre, except in the case where I really want to use the value _before_ inc/dec.

For example, assume an integer variable "i" has a value of 10. I want to use i's current value (10) in an expression, and _then_ increment i. In this case, I of course would use a post inc as so:

```
i = 10;
sum = i++ * somethingElse;
```

But if I'm not actually using the value of i in an expression, but instead, simply incrementing (or decrementing) its value, then I always use pre inc.

The reason has to do with my experience with the output of compilers (which concurs with what previous posters have reported). I've also noted that many compilers produce smaller code when compiling:

```
++i;
--i;
```

versus:

```
i++;
i--;
```

In the former (pre) case, the compiler thinks "Ok, first I increment i, and then I use i. So, first let me write out an inc opcode that works directly on the address where i's value is stored. Done. Now let me 'use' i. Wait a minute... i's value isn't really being used for anything. So let me skip doing something like writing out an opcode to load the contents of that address into a CPU register. I've used only one inc opcode to compile this instruction.".

In the latter (post) case, the compiler thinks "Ok, I can't increment i before I get its current value. So let me load that current value into a CPU register first. Ok, done. Now I can use that inc opcode to work directly on the address where i's value is stored. It's ok because I already have a copy of i's current value in a CPU register. Done. Ok, now let me use the value of i (which is already in a CPU register). Wait a minute... i's value isn't really being used for anything. Ok, I don't need any more opcodes to do anything with that CPU register. I've used two opcodes to compile this instruction. One load opcode to move the current value into a register, and a second inc opcode. Sure, that load opcode turned out to be totally unnecessary, but I already wrote it out. C'est la vie.".

And that's why typically a pre-increment produces more efficient asm output from a compiler.

---

### Post by hod139 on 2007-10-17
> **j_g said:**
> 
<snip>
And that's why typically a pre-increment produces more efficient asm output from a compiler.

That's far lower level than I would ever think.  I think like this: (code from a basic list iterator class)


```

//pre-increment
list_iterator<T> & operator++() { 
    ptr_ = ptr_->next_; 
    return *this;
  }
  
//post-increment
list_iterator<T> operator++(int) {
    list_iterator<T> temp(*this);
    ptr_ = ptr_->next_;
    return temp;
  }
```

We clearly see the extra work needed in the post-increment method, the copy constructor call.
 
It's good having low level asm people around too, but I don't think that level of analysis is needed to analyze this problem.  Hopefully the above code is obvious in why post increment/decrement can be slower.

---

### Post by slavik on 2007-10-17
> **j_g said:**
> Former posters have already pointed out the advantages of using pre, versus post, inc/dec. I concur 100% and see no need to repeat what they've already said. I'll just add a little more detail for anyone who may still be confused about the point being made.

I always use pre, except in the case where I really want to use the value _before_ inc/dec.

For example, assume an integer variable "i" has a value of 10. I want to use i's current value (10) in an expression, and _then_ increment i. In this case, I of course would use a post inc as so:

```
i = 10;
sum = i++ * somethingElse;
```

But if I'm not actually using the value of i in an expression, but instead, simply incrementing (or decrementing) its value, then I always use pre inc.

The reason has to do with my experience with the output of compilers (which concurs with what previous posters have reported). I've also noted that many compilers produce smaller code when compiling:

```
++i;
--i;
```

versus:

```
i++;
i--;
```

In the former (pre) case, the compiler thinks "Ok, first I increment i, and then I use i. So, first let me write out an inc opcode that works directly on the address where i's value is stored. Done. Now let me 'use' i. Wait a minute... i's value isn't really being used for anything. So let me skip doing something like writing out an opcode to load the contents of that address into a CPU register. I've used only one inc opcode to compile this instruction.".

In the latter (post) case, the compiler thinks "Ok, I can't increment i before I get its current value. So let me load that current value into a CPU register first. Ok, done. Now I can use that inc opcode to work directly on the address where i's value is stored. It's ok because I already have a copy of i's current value in a CPU register. Done. Ok, now let me use the value of i (which is already in a CPU register). Wait a minute... i's value isn't really being used for anything. Ok, I don't need any more opcodes to do anything with that CPU register. I've used two opcodes to compile this instruction. One load opcode to move the current value into a register, and a second inc opcode. Sure, that load opcode turned out to be totally unnecessary, but I already wrote it out. C'est la vie.".

And that's why typically a pre-increment produces more efficient asm output from a compiler.

usually, I don't say this to anyone, but YOU ARE WRONG! :)

attached, are two C files, two asm files produced by running gcc -S on them and a diff file. :)

diff file reposted here for my purpose.

```
--- test.s	2007-10-17 20:36:32.000000000 -0400
+++ test2.s	2007-10-17 20:36:33.000000000 -0400
@@ -1,2 +1,2 @@
-	.file	"test.c"
+	.file	"test2.c"
 	.section	.rodata
@@ -18,4 +18,4 @@
 	movl	$0, -4(%rbp)
-	movl	-4(%rbp), %esi
 	addl	$1, -4(%rbp)
+	movl	-4(%rbp), %esi
 	movl	$.LC0, %edi
```

The compiler things more along the lines of "Hey, I need to put this somewhere else in memory. I will move it to CPU first (there is no `mov mem/mem` instruction in x86). Ooh, it needs to be incremented before/after I send it somewhere else in memory ..."

the ondly difference is that there is an extra memory write to save the original variable, but with todays write back caching, you probably won't see any difference (since CPU moves data in and out of memory in chunks anyway, possibly rewriting memory with same copies).

edit: surprisingly it's not an inc instruction, but an add ... maybe the assembler changes it?
edit2: disassembled compiled object files and it's still an addl :)

---

### Post by mjwood0 on 2007-10-17
> **aks44 said:**
> Which confusion? The whole point is about "which one should you use when BOTH are correct?"... so there's no possible confusion IMHO.



You meant```
j = i;
i +=1;
```
Right? :p

(I really hope this was a typo, but that would explain your previous post about unit tests...)

No.  On my compiler, the following is what I got -- and I tested this multiple times to ensure that I was posting correctly.

```

j = i++;

```

This statement does NOT update i.  Instead, j gets the value of i + 1 while i remains unchanged.

This is with a very well known embedded systems compiler targeted to a PowerPC processor.

I just attempted the same thing using XCode on my Mac and get the result you expected (but in C++).

Hmm...  I'll have to mess with the compiler at work and see what's going on.  Perhaps I'll dump the assembly and see where that takes me. 

No wonder I've always thought this stuff made no sense when I read other people's take on it...:confused:

---

### Post by mjwood0 on 2007-10-17
Okay.  Now I'm really confused.

I did the same thing using gcc on my Mac and got the expected results (what aks44 said).  But I have the output here and my PPC compiler definitely didn't work this way.

Come to think of it, I never really understood the whole dilemma until now...  This actually makes me feel a lot better as I was starting to question my sanity when people kept extolling the features of pre vs. post incrementing.  

I really do need to check what that compiler is doing though.  It wouldn't be the first time it had an odd idea of what's needed where...

---

### Post by j_g on 2007-10-18
> **slavik said:**
> you're wrong...

No, no. Don't use i in an expression. The compiler has to fetch the value in both cases anyway. Just do a pre, versus a post, increment. See if the compiler generates an unnecessary fetch of the variable's value in the latter case.

```
int main(int argc, char** argv)
{
  int i = 0;
  i++;
  return 0;
}

int main(int argc, char** argv)
{
  int i = 0;
  ++i;
  return 0;
}
```


You may also want to perform the test with a global variable, and perhaps a pointer to something, etc, because sometimes certain opcodes can be used in particular address modes and with particular operands, and the compiler may optimize things differently in these cases.

I (and other posters who have reported such) have in fact seen compilers do extra unnecessary fetches for post inc/dec, versus pre inc/dec (regardless of what gcc in particular does). We didn't just make that up.

---

### Post by aks44 on 2007-10-18
> **mjwood0 said:**
> Okay.  Now I'm really confused.

I did the same thing using gcc on my Mac and got the expected results (what aks44 said).  But I have the output here and my PPC compiler definitely didn't work this way.

FWIW, either in C or C++ the standard behaviour of **j = i++;** really is
[B]j = i;
i += 1;[/B]


If your PPC compiler goes wrong on such basic operations, better dump it as you never know what else it could mess up... ](*,)

---

