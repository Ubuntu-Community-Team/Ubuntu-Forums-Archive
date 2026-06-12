---
title: "Python! Questions? and Answers. Tutors welcome!"
date: 2006-04-27
forum: Programming Talk
---

### Post by Omnios on 2006-04-27
Hi to start off I played around with programming back in the C 64 days and have read a few books on basic. I tryed learning C and C++ but found answeres to my questions lacking. Anyways now I am studying "How To Think Like a Computer Scientist, Python edition" I am learning a lot about python but find that I am learning allot just by trying to come up with little scripts on my own. 

 Anyways one of the lessons required me to do the following.

 ```
As an exercise, write a compare function that returns 1 if
x > y, 0 if x == y, and -1 if x < y.

``` 

 I achieved this with the following and added a print statement so I could see a result.

```
def compare1(x,y,z):
     if x > y:
         z = 1
         return z
     elif x == y:
         z = 0
         return z
         
     else:
         z = -1
         return z
z = 1
x = compare1(1,1,z)
print x
    
```

 Anyways my first question is I tryed to modify it to prompt for input and use the input to set x and y in the compare function. First I tryed
```
n1 = input ("input number one") 
```
and could not get the x value to pass into the function argument, I even played around with compar1(x = n1, ... but that did nto work either. ALso im using the SPE editor wich is a little screwy at times in that sometimes cut and past works sometimes it dont lol. Anyways any suggestions on what I am doing wrong.

---

### Post by LordHunter317 on 2006-04-27
For starters, why are you passing that unnecessary 'z' to the function compare1()?  A function's return value doesn't have to be declared as an input.

---

### Post by dabear on 2006-04-27
Try this:
```

def compare(x,y):
	if x == y: return 0
        if x > y: return 1
	if x < y: return -1


num = raw_input('Please type an x-value:')
val = compare(num,1)
print 'The value is', val

```

---

### Post by Omnios on 2006-04-27
GOt it to work which is kind of funny because it is almost identical what I was trying to do before which crapt out on me it seemed that raw_input did not want to work and it did not want to pass a inputed value to the function argument.

 ```
def compare1(x,y,):
     if x > y:
         z = 1
         return z
     elif x == y:
         z = 0
         return z
         
     else:
         z = -1
         return z
z = 1
a = raw_input (" input 1st number :")
b = raw_input (" input 2nd number :")
a = int(a)
b = int(b)
x = compare1(a,b,)
print x
```

---

### Post by engla on 2006-04-27
I have no problems with code that works, but:
This might be stylistic either way, but you don't need any else clauses after if .. : return X. Some people think else is clearer, some think it's clearer to skip it. I mostly think you shouln't have any elses if they are not needed, it might confuse you about the actual flow of the function.

---

### Post by unbuntu on 2006-04-27
You know, such simple branching can be easily written using ternary operator ?:, except that python doesn't have ?: as in C.  However, there's an _almost_ equivalent workaround in Python, which will reduce your code into one line:
```

def compare(x,y):
  return x>y and "1" or (x==y and "0" or "-1")

>>> compare(1,0)
'1'
>>> compare(1,1)
'0'
>>> compare(1,2)
'-1'
>>>

```

However, this [COLOR="Red"]wouldn't work[/COLOR] because of the nature of logic operators *and* and *or* and the fact that 0 is interpreted as false.
```

  return x>y and 1 or (x==y and 0 or -1)

```

---

### Post by dabear on 2006-04-28
Tell me, why do you use this shit? It for certain doesn't make the code more readable, especially when you start to nest them. I know the terminary-like operator can be useful, but I wouldn't sacrifice readability over a few lines of saved space.
```
def compare(x,y):
	if x == y: return 0
        if x > y: return 1
	if x < y: return -1

```
vs
```

def compare(x,y):
  return x>y and "1" or (x==y and "0" or "-1")

```

---

### Post by ow50 on 2006-04-28
[QUOTE=dabear]Tell me, why do you use this shit? It for certain doesn't make the code more readable, especially when you start to nest them. I know the terminary-like operator can be useful, but I wouldn't sacrifice readability over a few lines of saved space.[/QUOTE]

Exactly. Who needs one-liners? One of the Pythonic habits is to write readable code.
[quote=Zen of Python]Readability counts.[/quote]

With this example, I'd go further and put a newline after each colon.
[quote=PEP 8]Compound statements (multiple statements on the same line) are generally discouraged.[/quote]

```
def compare(x, y):
    if x > y:
        return 1
    if x < y:
        return -1
    return 0
```

---

### Post by Omnios on 2006-04-28
[QUOTE=ow50]Exactly. Who needs one-liners? One of the Pythonic habits is to write readable code.


With this example, I'd go further and put a newline after each colon.


```
def compare(x, y):
    if x > y:
        return 1
    if x < y:
        return -1
    return 0
```[/QUOTE]

 Actualy this is very helpfull,  made me think a bit different which will change the way I look at making code.

---

### Post by unbuntu on 2006-04-28
[QUOTE=dabear]Tell me, why do you use this shit?[/QUOTE]

I've no idea you guys are so against one-liners.  Maybe the code itself is not as readable as that junk, but you _have_ the method name up there right?  Who needs to look and figure out three months later what compare() function does by inspecting the code line by line???  You write it, test it, and know it works...as simple as that.  

One of the beauties(or ugliness in your opinion, and judging your preference, you guys must really hate Perl) of such scripting languages is that you can get a job done quickly and efficiently.  We are not talking about writing MS Windows here!  More often than not these are for system scripts that does things quick and dirty.  One-liner exhibits the power of these languages so why not?  (Give you guys a for example:  the python list comprehension feature actually performs faster than the regular for loop, because the list comprehension feature is implemented directly in native C code.)

---

### Post by LordHunter317 on 2006-04-28
[QUOTE=dabear]Tell me, why do you use this shit? It for certain doesn't make the code more readable, especially when you start to nest them.[/quote]The only reason it's less readable in python is because of Python's refusual to apply reasonable logic to conditional expressions.  They're not the same as conditional statements, and that's the problem.

The only reason is it's important at all in Python is because of their terribly broken lambda expressions.

---

### Post by Omnios on 2006-04-28
Hi again, One liners might actualy even be usefull but for newbies there very confusing and breaking it up as much as possible may aid in helping a newb understand. Even scafoldind helps newbs understand as they go through the process. Thank god there is no spegetti code, go to line 111 and stin yourself around.

 ANyways working on another problem.
 This function prints a variable number of lines. 

```
def nline(n):
  if n == 0:
     return
  else:
     print
     nline(n-1)
nline(2)
```

 Anyways this works but when I try it with while My compiler keeps spitting out errors about the function call or freezes up or other odd errors.
 
 This is what I tryed.
```

def nline(n):
  while n > 0:
     print
     nline(n-1)
  return
nline(3)

```

---

### Post by unbuntu on 2006-04-28
[QUOTE=Omnios]
```

def nline(n):
  while n > 0:
     print
     nline(n-1)
  return
nline(3)

```[/QUOTE]

It will freeze for sure because it's an infinite loop.  The loop termination condition (n<=0) is never reached.

Remember for every recursive call, the variables of the current executing method is saved on the stack, hence, not affected.  Therefore assuming your nline(n-1) does return, and now you're inside nline(n), but the value of n is still the original n, and since it's not decreased inside the loop, it will never terminate.

---

### Post by Omnios on 2006-04-28
[QUOTE=unbuntu]It will freeze for sure because it's an infinite loop.  The loop termination condition (n<=0) is never reached.

Remember for every recursive call, the variables of the current executing method is saved on the stack, hence, not affected.  Therefore assuming your nline(n-1) does return, and now you're inside nline(n), but the value of n is still the original n, and since it's not decreased inside the loop, it will never terminate.[/QUOTE]

 Duh whaps self got it solved with 

```
def nline(n):
     while n > 0:
         print
         n = n-1
     return
nline(4)
```

 Needless to say Im learning.

---

### Post by yaaarrrgg on 2006-04-28
course if you want obfuscated one liners, just map it to an equation :) 

```

def c(x,y):
    return (x-y)^0

print c(3,2)    # 1
print c(2,2)    # 0
print c(1,2)    #-1

```

---

### Post by xenmax on 2006-04-29
[quote=yaaarrrgg]
```

def c(x,y):
    return (x-y)^0

```[/quote]
what about c(1,-1)? your code will return 2. The function is supposed to return 1 if x>y, 0 if x==y and -1 if x<y, not the difference b/w x and y.

---

### Post by yaaarrrgg on 2006-04-29
[QUOTE=xenmax]what about c(1,-1)? your code will return 2. The function is supposed to return 1 if x>y, 0 if x==y and -1 if x<y, not the difference b/w x and y.[/QUOTE]

oops... you're right.  it actually should be somthing more like:

```

def c(x,y):
    return (x-y)/max(abs(x-y),1)

```

---

### Post by Omnios on 2006-04-29
```
 As an exercise, write a function that takes a string as an argument
and outputs the letters backward, one per line.
```

Well I tryed to make this one work with if but could not get it to run properly learn't a lot playing around with it today, I finaly got it to work with a while loop.

```

def word():
  word = raw_input("Enter a word : ")
  i = len(word)
  n = 1
  while n < i+1:
     last = word[i-n] 
     n = n+1
     print last,
  else:
     return
word()

The output
>>> Running '/home/tom/tutor/revers.3' ...
Enter a word : I won
n o w   I Script '<source>' returned exit code 0
>>> got a chuckle from that one.

```

 Anyways im starting to get the fealing that either there are large differences in the usage of "if" and "while" or my SPE python editor is borked. Whats the best python editor to play with scripting? Also there a way to get this to work properly with a if loop?](*,)

---

### Post by LordHunter317 on 2006-04-29
[QUOTE=Omnios]Also there a way to get this to work properly with a if loop?](*,)[/QUOTE]There is no such thing, an if is an conditional block.

---

### Post by Omnios on 2006-04-29
[QUOTE=LordHunter317]There is no such thing, an if is an conditional block.[/QUOTE]

 Da whap! rewrites faulty memory and shakes out decades of dust. 

 Anyways finaly figured out the only way Im going to learn is actualy playing around and writing scripts, reading books just do not seem to work 100% for me. Why today I thought I could make a loop from a if statement escapes me. Your help is greatly apreciated and Thank you so little helps so much.

---

### Post by Omnios on 2006-04-30
[QUOTE=Omnios]Hi again, One liners might actualy even be usefull but for newbies there very confusing and breaking it up as much as possible may aid in helping a newb understand. Even scafoldind helps newbs understand as they go through the process. Thank god there is no spegetti code, go to line 111 and stin yourself around.

 ANyways working on another problem.
 This function prints a variable number of lines. 

```
def nline(n):
  if n == 0:
     return
  else:
     print
     nline(n-1)
nline(2)
```

 Anyways this works but when I try it with while My compiler keeps spitting out errors about the function call or freezes up or other odd errors.
 
 This is what I tryed.
```

def nline(n):
  while n > 0:
     print
     nline(n-1)
  return
nline(3)

```[/QUOTE]

 K figured this out, I managed to make it so that the function calls itself with a different value which worked, then half asleep I thought for some crazy reason to try making a loop with "if" which looped me lol. Anyways managed to also correct this one though I learnt something about functions from this.

 New Code 
```

def nline(n):
     while n > 0:
         print
         n=n-1
nline(3)

```
 Actualy playing around with the code and doing the lessons makes for a mean learning curve. Before I was just copying code and didn't realy learn much.

---

### Post by Omnios on 2006-04-30
I have a question this is a modified example from "How To Think Like a Computer Sientist" 

```

def find(str,ch):
  index = 0
  while index < len(str):
     if str[index] == ch:
         return index
     index = index + 1
  return -1
find("toomb","o")
print index,
```

 And it seems my returns are not returning properly as I I tryed.

```

def find(str,ch):
  index = 0
  while index < len(str):
     if str[index] == ch:
         print index
         return index
     index = index + 1
  return -1
find("toomb","o")
print index,
``` 

 and it printed out the proper return, Now this is where it get funky, I tryed the example before and gave me a global error that index was not defined. Anyways I defined index and found it just punched out the numbers that I declared it as. Then for the hell of it I punched in 9 as there where no where neer 9 len's in it. Then I took out the Global and it still kind of worked buy no matter how I changed the input string It would punch out

```

1
9 Script '<source>' returned exit code 0
>>> >>> 9 Script '<source>' returned exit code 0
>>> 
``` 
Now where did it get 9 from? 
Is my Python editor Flakey?

---

### Post by ow50 on 2006-04-30
Here's a fixed version
```
def find(string, char):
  index = 0
  while index < len(string):
     if string[index] == char:
         return index
     index += 1
  return -1
print find("toomb", "o")
```

1. Don't end your script with "print [...],", because the comma holds up the printing until the script reaches the next print statement that is not followed by a comma.
2. Don't use str as a variable name since it's a built-in function.
3. The variable "index" is not available outside the function "find".
4. You'll want to print the return value of the "find" function, not the inaccesible "index" variable. You can also do
```
index = find("toomb", "o")
print index
```

---

### Post by TheGrudge on 2006-05-04
another version:
```

def find(str,ch):
        for index in range(len(str)):
                if str[index] == ch: return index
        return -1



print find("hello","l")
>> 2

```

The nice thing about Python "strings","lists","dictionaries"... is that you can iterate over them.
So this solution is shorter (and maybe better to understand)....

---

### Post by Omnios on 2006-07-18
I have been taking a break from learning python for a few months, im on medication and have just had a magore med change. Anyways am planning to continue my python studies as my concintration seems to be much better now than what it was before. 

 Anyways anyone have any suggestion for quick reads on syntax?

---

