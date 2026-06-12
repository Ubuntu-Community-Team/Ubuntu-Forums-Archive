---
title: "Help with BASIC ... Prime Numbers"
date: 2015-07-09
forum: Programming Talk
---

### Post by antoine11 on 2015-07-09
Hello. I've recently started learning BASIC programming language on my ubuntu laptop. I am running on the latest ubuntu, I use gedit (with plugins), and I use freeBASIC to run my commands. I have been trying this program out trying to find the highest prime number my computer could handle, but my running gives me errors and i can't find a tutorial online seeing as BASIC is not very thouroughly explained on the internet :sad:](*,):?:. Please help. I will put program and terminal output for you to see. If you have any suggestions or questions for me please tell me (constructive criticism helpful). I'm not very skilled so try not to use complicated terms when explaining. Thank You!


```
Rem All "dim's"
dim numtype3 as double
DIM num as integer
DIM length1 as integer
dim numtype as integer
DIM lastnum as integer
DIM amount as integer
DIM last as integer
DIM numfiltertwo as integer
dim numtype2 as double
REM All under until do is equalities
numtype3 = numfiltertwo/7
numtype2 = numfiltertwo/3
length1 = len(num)
 num = num + 1
length1 = len(num)
lastnum = length1 - 1
dim lastnum1(lastnum)
lastnum1 = num


do
 goto 30


print "Number is not prime number."
goto 30


Rem IF you want to have it run from where you left off, check the text file for the last prime number you found, and instead of num = num + 1 type num = [number] + 1 and add this command ABOVE it: 
Rem num = num + 1
Rem goto 37


IF amount = 0 then 
print "Finished" 
else 
goto 21
end if
cls
input "How many prime numbers would you like to find?" ; amount
IF amount = 0 then
print "Machine must run at least one time."
elseif amount = 0 then
goto 37
if length1 < 2 then
num = num + 1
goto 37
elseIF num < 23 then
goto 37
end if


last = num:ToString:ToCharArray () (lastnum)
if last = 2 then 
goto 24
elseIF last = 4 then 
goto 24
elseIF last = 5 then 
goto 24
elseIF last = 6 then 
goto 24
elseIF last = 8 then 
goto 24
elseIF last = 0 then 
goto 24
END IF


Rem The second filter is because the number cannot be a multiple of 3, or 7.


IF length1 = 5 then
numfiltertwo :ToString:ToCharArray ( ) (1) (2) (3)
END IF
IF length1 = 4 then
numfiltertwo :ToString:ToCharArray ( ) (1) (2)
END IF
IF length1 = 3 then
numfiltertwo :ToString:ToCharArray ( ) (1)
END IF
IF length1 = 2 then
numfilter :ToString:ToCharArray ( )
END IF
IF numtype2 = integer then 
goto 24
IF numtype3 = integer then 
goto 24
END IF


numtype = num/11
numtype1 = num/13
IF numtype = integer then
goto 24
sleep
END IF
IF numtype1 = integer then
goto 24
END IF
else
open #1: name highest_prime.txt, access output, create newold
print #1: num
close #1
goto 21
loop
```

---

### Post by PaulW2U on 2015-07-09
*Thread moved to **Programming Talk**.* 

Welcome to the forums antoine11.

You might want to repost your terminal output between code tags as the screenshots are far too small to be readable.

If you are using New Reply button - highlight text and use the # button in the text box header.

If you are using Quick Reply then add [noparse]```
 at the beginning of the section and 
```[/noparse] at the end.

---

### Post by QIII on 2015-07-09
I have removed the images because they were hardly viewable.  Please follow the instructions above for posting the actual code.

I have also changed the title to something more meaningful.

---

### Post by antoine11 on 2015-07-09
thanks for the info

---

### Post by trent.josephsen on 2015-07-10
You may find it difficult to find (recent) tutorials and help for BASIC, for a couple reasons. BASIC isn't just one language: there are many different "dialects". When I first began programming, I used a dialect called XBasic. FreeBASIC, on the other hand, looks like it's based on Microsoft's QBasic dialect. In any case, I didn't stick with it very long, and that was so long ago that I don't really remember any of it, so any help I can offer will be on a very, um, *basic* level.

That said, maybe there are a few things I can help with.

In first passing through the code, I noticed that there are 12 places where you wrote "IF" but only 10 "END IF"s. There must be an END IF for every IF. I'm not sure where those extra END IFs belong, so you should look back through your program and see where you forgot to write it.

It is tremendously helpful to indent everything between THEN and the associated END IF. [Here's an example of a program with correct indentation that makes the code more readable.](http://www.99-bottles-of-beer.net/language-freebasic-980.html)

These:
```
numtype3 = numfiltertwo/7
numtype2 = numfiltertwo/3
length1 = len(num)
num = num + 1
length1 = len(num)
lastnum = length1 - 1
lastnum1 = num
```
aren't "equalities" -- they are assignment statements. There is an important difference. An equality is something that's either true or not. "1 = 2" is a false equality; "2 + 2 = 4" is a true one. "x = 5" is true only when the variable x has the value 5. But assignment statements are a different story. "x = 5" as an assignment statement should be understood as "x **gets** the value 5". As the CPU is running your code, before it gets to the assignment statement, x could have any value; but afterwards, x will definitely have the value 5.

"num = num + 1" doesn't make sense as an equality -- there is no number that is equal to one more than itself. But as an assignment statement, it means that num **gets** the value one greater than whatever its value was before. Assignments are sequential statements: they change the state of the program when run.

This brings me to another point, which is that all these assignment statements are at the top of your file, which means they only get run once at the beginning of the program. It seems like what you want to do is run them somewhere in the loop. An essential skill you absolutely must have as a programmer is the ability to look through your program line-by-line and pretend you are the CPU. If you do this, you should notice a problem:
```
dim numtype3 as double
>>> CPU thinks: Ok, "numtype3" is a name that refers to a double. Let's give it the initial value 0.
...
dim numfiltertwo as integer
>>> CPU thinks: Ok, "numfiltertwo" is a name that refers to an integer. Let's give it the initial value 0.
...
numtype3 = numfiltertwo/7
>>> CPU thinks: What value does numfiltertwo refer to? Oh, it's 0.
>>> CPU thinks: What's 0 divided by 7? Oh, it's 0.
>>> CPU thinks: Ok, let's give numtype3 the new value 0.
```
Which is not what you wanted. You probably wanted numfiltertwo to have some value other than zero. But you didn't ever give it a value, so you got what the CPU decided to put in it.

This program may be a bit too ambitious for you at the moment. Don't worry, it won't take long to get up to speed; you just need to start smaller. How about a program that reads a number from the user and tells whether it is even or not? That's super simple. Then change it so it tells whether the number is divisible by 3, then 5, and at that point, if you understand the pattern, take a stab at telling primes from non-primes. Then you'll be well on your way to writing a program that generates all primes.

There's a [famous programming interview question](famous programming interview question) that would be a good exercise with loops, assignments, and ifs, and don't be intimidated -- it's simpler than a program that tests primality. You can read about it at the linked blog, but here's the problem if you want to take a stab at it:
> Write a program that prints the numbers from 1 to 100. But for multiples of three print "Fizz" instead of the number and for the multiples of five print "Buzz". For numbers which are multiples of both three and five print "FizzBuzz".

---

### Post by raydeen on 2015-07-30
I think the biggest problem here is that it seems you are mixing 'old' and 'new' BASIC. You have quite a few GOTO statements that look like they're pointing to line number references but the line numbers don't seem to be present in your code. Like 'goto 30', 'goto 24', etc. Originally BASIC did everything with line numbers. A typical 'Hello World' program would look like:

10 PRINT "HELLO WORLD"
20 GOTO 10

The interpreter would first print HELLO WORLD on the screen and then loop back to do it again, over and over until the user broke out of the program. Newer BASIC dialects did away with line numbers in favor of Labels. So a newer BASIC Hello World program might look like:

Hello:
    print "Hello World"

goto Hello

In any case, unless you really have a need or desire to learn BASIC, and as one of the other posters have stated, there are MANY different dialects, I'd recommend going with Python. It's the BASIC of the 21st Century and A LOT more flexible and powerful. Just to give you an idea of what your prime number program would look like in Python, check out this link:

[http://www.programiz.com/python-programming/examples/prime-number-intervals](http://www.programiz.com/python-programming/examples/prime-number-intervals)

Much easier to read, much less code to type, and all around more efficient.

---

