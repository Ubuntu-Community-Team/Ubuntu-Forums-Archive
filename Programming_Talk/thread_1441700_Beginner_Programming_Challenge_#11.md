---
title: "Beginner Programming Challenge #11"
date: 2010-03-29
forum: Programming Talk
---

### Post by schauerlich on 2010-03-29
[size=5]Beginner Programming Challenge #11[/size]

[color=red]**This challenge is closed. You're welcome to submit an entry and ask for feedback, but [the winner](http://ubuntuforums.org/showpost.php?p=9135518&postcount=81) has already been selected.**[/color]

Welcome to the 11th Beginner Programming Challenge! Although I did not win [the 10th programming challenge](http://ubuntuforums.org/showthread.php?t=1424102), Bachstelze has graciously allowed me to host this one. 

If you need help, feel free to drop by on IRC on irc.freenode.net in #ubuntu-beginners-dev.

Let's get started.

[size=3]_Task:_[/size]

Implement a [Reverse Polish Notation](http://www.hpmuseum.org/rpn.htm) (RPN) calculator.

[size=2]_What is RPN?_[/size]
You're probably used to calculators using infix notation. With infix notation, you place an operator between two operands, and press enter to see the result. An example of infix notation:
```
3 + 4
```
Infix notation works well for basic expressions, but it is difficult to write complicated expressions without parentheses.

RPN, on the other hand, places operators *after* their operands. For example:
```
3 4 +
```
While this may seem odd at first, it has several convenient properties:
[list][*]It is possible to write arbitrarily long expressions in RPN which are unambiguous, and do not require parentheses.
[*]There is no need for an operator precedence hierarchy
[*]It is relatively easy for a computer to parse
[*]Calculations can be done as soon as an operator is specified - you do not need to consider the entire expression before beginning to evaluate it.[/list]

Here are a few more examples of RPN, with their infix notation counterparts
```
3 4 - 5 +
(3 - 4) + 5

3 4 5 * -
3 - (4 * 5)

5 1 2 + 4 * + 3 &#8722;
5 + ((1 + 2) * 4) &#8722; 3
```

[size=3]_Requirements:_[/size]
[list][*]Your program must be able to evaluate any valid RPN expression of reasonable length (~20 tokens) with the following operators: + - * / % ^ (division is true division. 10 3 / = 3.33)
[*]If the entered expression's syntax is invalid, your program should handle it gracefully (no segfaults or uncaught exceptions)
[*]Your program must handle divide by zero errors gracefully
[/list]

[size=3]_Extra Credit:_[/size]
[list][*]If interactive, allow users to quit without resorting to ^C.
[*]Plan for the future: make your code flexible so that it can be incorporated into other projects you may work on easily.
[*]Add more operators: anything that makes sense
[*]Gracefully handle all user input, from random characters to just a newline. 
[/list]

[size=3]_Extra Extra Credit:_[/size]
[list][*]Add support for an infix notation mode by converting the expression to RPN and evaluating it with your RPN code.[/list]

[size=3]_Example output, for testing:_[/size]
```
eric@river:~$ ./rpn
> 3 4 +
7.0
> 10 3 /
3.33333333333
> 2 5 ^
32.0
>  10 2 %
0.0
> 24 12 3 + 4 % / 6 - 4 * 3 ^
512.0
> 10 2 2 % /
Divided by Zero
// Incorrect inputs:
> 10 + 10
Not enough operands
> 10 10 10 +
Too many operands
> 
> aw4ojghsiu5esrgs56u7ikdyjdt drthisu 5 hrtgh 5 5 +
Unrecognized token
> 45 6 + / & 4
Unrecognized token
> q
eric@river:~$
```

[size=3]_Caveats:_[/size]
The wikipedia page has a good explanation of the algorithm for evaluating RPN, as well as a sample implementation in Python. Please try to think for yourself and only reference these if you're stuck. Submissions which are suspiciously similar probably won't win, and more importantly, you won't learn anything.

As always:
Any overly obfuscated code will be immediately disqualified without account for programmers skill. Please remember that these challenges are for beginners and therefore the code should be _easily readable and well commented_.

Any non-beginner entries will not be judged. Please use common sense when posting code examples. Please do not give beginners a copy paste solution before they have had a chance to try this for themselves.

Please provide instructions for how to run your program along with your submission.

And with that...
[size=4]Have fun![/size]

---

### Post by tooatw on 2010-03-29
hi, i am new to this forum and i would like to enter this challange, do i just write here when i'm done or something? are all programming languages accepted?

---

### Post by s.fox on 2010-03-29
> **tooatw said:**
> hi, i am new to this forum and i would like to enter this challange, do i just write here when i'm done or something? are all programming languages accepted?

Hello,

Provided you are a beginner then yes you can enter before the winner is announced.   To enter simply post your solution here.  Any language is allowed. 

-Silver Fox

---

### Post by tooatw on 2010-03-29
i'm almost done, it works fine for the first line, but if i enter the exact same thing on the second one, it doesnt work

alexander@amd64:~/1$ ./1
>24 12 3 + 4 % / 6 - 4 * 3 ^
512.0
>24 12 3 + 4 % / 6 - 4 * 3 ^
3.0

---

### Post by schauerlich on 2010-03-29
> **tooatw said:**
> i'm almost done, it works fine for the first line, but if i enter the exact same thing on the second one, it doesnt work

Without seeing your code, I'm guessing you don't reset your variables between runs.

---

### Post by tooatw on 2010-03-29
i thought it was the variables, however i only reset the counter to the arrays, i didn't reset all the elements in the array because i thought it didn't matter since it will just overwrite them anyway

here's a screenshot of it in action, i think it pretty much resembles with your post

p.s. i know it could be done faster / better but i'm a beginner and i think thats what this topic is about anyway

---

### Post by lavinog on 2010-03-29
```

for (i=0;i<99;++i) num[i]=zero=k[i]=0;

```
Are you setting zero to 0 99 times?

---

### Post by tooatw on 2010-03-29
> **lavinog said:**
> ```

for (i=0;i<99;++i) num[i]=zero=k[i]=0;

```
Are you setting zero to 0 99 times?
yes, i meant to put it to the other line actually, my mistake

---

### Post by tooatw on 2010-03-29
here i added comments to it now
```

//Alexander Constantin Bledea - Beginner Programming Challenge #11
#include <stdio.h> //standard for i/o
#include <stdlib.h> // standard again
#include <string.h> // string library
#include <math.h> // for the power function
int i,true=2,k[99],is,is2,w,iv,si,dubios,nc,number,zero,neo,num[99];
/*
 i is standard
 true is something that is always true since i don't know the c version of "while true"
 is is the empty spaces in the string counter
 is2 is the 'how much till the end' counter
 w is like a secondary i
 si counts how many words are between two spaces since operators can only use one space
 dubios seeks dubious behaviour
 nc is the number counter
 number is the temporary number
 zero alerts if someone wants to divide by 0
 neo is the not enough operators counter
 num is the number array 
 */
char x[100];
//the string
float n_to_f;
// for the dubious output
int main(){
	while (true){
		for (i=0;i<99;++i) num[i]=k[i]=0; // reset the arrays
		i=is=is2=w=iv=si=dubios=nc=zero=neo=number=0; // reset the variables
		printf("> ");
		gets(x);
		if (strcmp(x,"exit")== 0) break;
		for (i=0;i<strlen(x);++i){ //find empty spaces and keep track of them in k
			if (x[i]==' ') {
					k[is] = i; 
					++is;
			}
		}
		if (k[is] != strlen(x)) {k[is]=strlen(x);++is;} // add to the counter the last element
		iv=0;// needed later on
		for (w=0;w<is;++w){  // for all the empty spaces
			is2=k[w]-iv; //how many characters does the string fragment have
			number=0; //reset the number
			for (i=iv;i<k[w];++i){ //figure out what the number is
				si=is2;
				switch(x[i]){
					case '0'...'9': number += ((x[i] - '0') * pow( 10.0 , is2-1));
									--is2 ;
									if (is2==0) { //when is reaches 0 save the number 
										num[nc]=number;
										++nc;
									}
									break;	
					case  '+': if (si==1){ if(nc>1){ num[nc-2]=num[nc-2]+num[nc-1]; num[nc-1]=num[nc];--nc;} else ++neo;} else ++dubios;break;
					case  '-': if (si==1){ if(nc>1){ num[nc-2]=num[nc-2]-num[nc-1]; num[nc-1]=num[nc];--nc;} else ++neo;} else ++dubios;break;
					case  '/': if (si==1){ if(nc>1){ if (num[nc-1]!=0){ num[nc-2]=num[nc-2]/num[nc-1]; num[nc-1]=num[nc]; --nc;} else ++zero;}  else ++neo;} else ++dubios;break;
					case  '*': if (si==1){ if(nc>1){ num[nc-2]=num[nc-2]*num[nc-1]; num[nc-1]=num[nc]; --nc;} else ++neo;} else ++dubios;break;
					case  '^': if (si==1){ if(nc>1){ num[nc-2]=pow(num[nc-2],num[nc-1]); num[nc-1]=num[nc]; --nc;} else ++neo;} else ++dubios;break;
					case  '%': if (si==1){ if(nc>1){ num[nc-2]=num[nc-2]%num[nc-1]; num[nc-1]=num[nc]; --nc;} else ++neo;} else ++dubios;break;
					
					//for all cases of operands if the string fragment is wider than 1 caracter mark it as dubious behavior and if you dont have at least 2 operands mark it down
					default: ++dubios;break;
					//anything else goes to dubious behaviour
				}
			
			}
			iv=k[w];//we need this to find out the word size
			++iv;
		}
	n_to_f=num[nc-1];//transform it to float because thats what the post asks for
     if (dubios==0){//if nothing is dubious ... this should be obvious
		if (zero!=0) printf("Divided by Zero\n"); 
		else if (neo>0) printf("Not enough operands\n");
		else if (neo==0 &&nc>1) printf("Too many operands\n");
		else if (nc==0); //if empty string
		else printf("%.1f\n",n_to_f); }// if everything goes to plan print the number
     else printf("Unrecognized token\n");
    }
return 0;
}

```

---

### Post by Compyx on 2010-03-29
I would suggest breaking the code up into functions, adding some whitespace here and there and indenting properly. That would make the code easier to read, debug and extend.

The C idiom for `while (true)' is `while (1)' or (less common and less readable) `for ( ; ; )'.

You can define true if you want:
```

#define true 1
#define false 0

```
or:
```

typedef enum { false, true } bool;

```
will give you a boolean type should you need it.

---

### Post by tooatw on 2010-03-29
> **Compyx said:**
> I would suggest breaking the code up into functions, adding some whitespace here and there and indenting properly. That would make the code easier to read, debug and extend.

The C idiom for `while (true)' is `while (1)' or (less common and less readable) `for ( ; ; )'.

You can define true if you want:
```

#define true 1
#define false 0

```
or:
```

typedef enum { false, true } bool;

```
will give you a boolean type should you need it.
thanks the while (1) seams perfect
whats wrong with my indentation apart from the cases

---

### Post by tooatw on 2010-03-29
[PHP]//Beginner Programming Challenge #11
#include <stdio.h> //standard for i/o
#include <stdlib.h> // standard again
#include <string.h> // string library
#include <math.h> // for the power function
int i,true=2,k[99],is,is2,w,iv,si,dubios,nc,number,zero,neo,num[99];
/*
 i is standard
 true is something that is always true since i don't know the c version of "while true"
 is is the empty spaces in the string counter
 is2 is the 'how much till the end' counter
 w is like a secondary i
 si counts how many words are between two spaces since operators can only use one space
 dubios seeks dubious behaviour
 nc is the number counter
 number is the temporary number
 zero alerts if someone wants to divide by 0
 neo is the not enough operators counter
 num is the number array 
 */
char x[100];
//the string
float n_to_f;
// for the dubious output
int main(){
	while (true){
		for (i=0;i<99;++i) num[i]=k[i]=0; // reset the arrays
		i=is=is2=w=iv=si=dubios=nc=zero=neo=number=0; // reset the variables
		printf("> ");
		gets(x);
		if (strcmp(x,"exit")== 0) break;
		for (i=0;i<strlen(x);++i){ //find empty spaces and keep track of them in k
			if (x[i]==' ') {
					k[is] = i; 
					++is;
			}
		}
		if (k[is] != strlen(x)) {k[is]=strlen(x);++is;} // add to the counter the last element
		iv=0;// needed later on
		for (w=0;w<is;++w){  // for all the empty spaces
			is2=k[w]-iv; //how many characters does the string fragment have
			number=0; //reset the number
			for (i=iv;i<k[w];++i){ //figure out what the number is
				si=is2;
				switch(x[i]){
					case '0'...'9': number += ((x[i] - '0') * pow( 10.0 , is2-1));
									--is2 ;
									if (is2==0) { //when is reaches 0 save the number 
										num[nc]=number;
										++nc;
									}
									break;	
					case  '+':	if (si==1){ 
									if(nc>1){ 
										num[nc-2]=num[nc-2]+num[nc-1]; 
										num[nc-1]=num[nc];
										--nc;
									} 
									else ++neo;
								} 
								else ++dubios;break;
					case  '-':	if (si==1){ 
									if(nc>1){ 
										num[nc-2]=num[nc-2]-num[nc-1]; 
										num[nc-1]=num[nc];
										--nc;
									} 
									else ++neo;
								} 
								else ++dubios;break;
					case  '/':	if (si==1){ 
									if(nc>1){ 
										if (num[nc-1]!=0){ 
											num[nc-2]=num[nc-2]/num[nc-1]; 
											num[nc-1]=num[nc]; 
											--nc;
										} 
										else ++zero;
									}  
									else ++neo;
								} 
								else ++dubios;break;
					case  '*':	if (si==1){ 
									if(nc>1){ 
										num[nc-2]=num[nc-2]*num[nc-1]; 
										num[nc-1]=num[nc]; 
										--nc;
									} 
									else ++neo;
								} 
								else ++dubios;break;
					case  '^':	if (si==1){ 
									if(nc>1){ 
										num[nc-2]=pow(num[nc-2],num[nc-1]); 
										num[nc-1]=num[nc]; 
										--nc;
									} 
									else ++neo;
								} 
								else ++dubios;break;
					case  '%':	if (si==1){ 
									if(nc>1){ 
										num[nc-2]=num[nc-2]%num[nc-1]; 
										num[nc-1]=num[nc]; 
										--nc;
									} 
									else ++neo;
								} 
								else ++dubios;break;
					//for all cases of operands if the string fragment is wider than 1 caracter mark it as dubious behavior and if you dont have at least 2 operands mark it down
					default: ++dubios;break;
					//anything else goes to dubious behaviour
				}
			}
			iv=k[w];//we need this to find out the word size
			++iv;
		}
	n_to_f=num[nc-1];//transform it to float because thats what the post asks for
    if (dubios==0){//if nothing is dubious ... this should be obvious
		if (zero!=0) printf("Divided by Zero\n"); 
		else if (neo>0) printf("Not enough operands\n");
		else if (neo==0 &&nc>1) printf("Too many operands\n");
		else if (nc==0); //if empty string
		else printf("%.1f\n",n_to_f); }// if everything goes to plan print the number
     else printf("Unrecognized token\n");
    }
return 0;
}
[/PHP]

---

### Post by Compyx on 2010-03-29
> **tooatw said:**
> whats wrong with my indentation apart from the cases

Well, it's more a matter of too many indents, that's why I suggested breaking up the code into smaller pieces (functions), it'll make the code more readable and cut down on the number of variables needed.

For example the whole operator handling could be stored in a separate function:
```

int eval_operator(int operator, int operand1, int operand2)
{
    int result;

    switch (operator) {

        case '+':
            /* TODO: catch overflow before it happens */
            result = operand1 + operand2;
            break;

        case '-':
            result = operand1 - operand2;
            break;

        ...

        default:
            fprintf(stderr, "unsupported operator '%c'!\n", operator);
            result = SOME_ERROR_CODE;
            break;
    }
    return result;
}

```

Some people prefer to line up their cases with the switch statement, but that's just a matter of taste, as long as you're consistent.

Oh, and never use gets(), it's a buffer overflow waiting to happen, use fgets():
```

fgets(x, 100, stdin);

```

---

### Post by lavinog on 2010-03-29
Is it just me, or are these Beginner challenges more likely suited for the intermediate challenges?

---

### Post by schauerlich on 2010-03-29
> **lavinog said:**
> Is it just me, or are these Beginner challenges more likely suited for the intermediate challenges?

RPN is actually pretty simple to deal with. Every token is whitespace delimited, and evaluation can be implemented easily with a stack. The extra (extra) credit, though, it probably above beginner level - hence it's optional. These are supposed to be *challenges*, after all. :)

---

### Post by tooatw on 2010-03-29
> **lavinog said:**
> Is it just me, or are these Beginner challenges more likely suited for the intermediate challenges?
i'm a beginner
originally i wanted to get the elements with %s but i dropped it for some reason
like 
while (1)
scanf("%s",x)
and take every s separately with the same switch that i have now 
there are many ways that a beginner can think of 
just for the record, the first time i ever implemented something was about 3 months ago and i failed miserably 
i only started programming for the past 2-3 weeks

---

### Post by Compyx on 2010-03-29
Infix to postfix isn't that hard either, and it too can be implemented using a stack (and a queue).
The algorithm is a bit more complex than a postfix calculator, and increases when adding unary/ternary operators and function-calls. ;)

---

### Post by matmatmat on 2010-03-29
My python entry (now works for every input)
[PHP]
#!/usr/bin/env python
#-*- coding:utf-8 -*-
from sys import exit
import math

class Stack (object):                           #  stack class, allows pushing, popping
	def __init__(self):                         #+ could be used somewhere else ;)
		self.stack = []

	def push(self, val):
		self.stack = [val] + self.stack

	def pop(self):
		val = self.stack[0]
		self.stack.remove(self.stack[0])
		return val

	def __str__(self):                     # for the print stack bit below
		if(self.stack[0] % 1 == 0):
			return str(int(self.stack[0])) # if the number was whole
		return str(self.stack[0])          # else

def main():
	ans = 0
	print "Everything must be spaced seperated"
	while True:
		stack = Stack()
		try:
			string = raw_input("Enter your sum: ")
		except:
			print 
			exit()
		if(string == ""):
			pass
		elif(string != "Q"):
			split = string.split(" ")
			for token in split:
				try:
					if(token == "+"):
						stack.push(stack.pop()+stack.pop())
					elif(token == "-"):
						a = stack.pop()
						b = stack.pop()
						stack.push(b - a)					
					elif(token == "*"):
						stack.push(stack.pop()*stack.pop())
					elif(token == "/"):
						a = float(stack.pop())
						if(a == 0):
							print "Divide by 0 error"
							continue
						b = float(stack.pop())
						stack.push(b / a)		
					elif(token == "%"):
						a = float(stack.pop())
						b = float(stack.pop())
						stack.push(b % a)
					elif(token == "^"):
						a = float(stack.pop())
						b = float(stack.pop())
						stack.push(b ** a)		
					elif(token == "ans"):
						stack.push(ans)	
					elif(token == "sqrt"):
						stack.push(math.sqrt(stack.pop()))
					elif(token == "cos"):
						stack.push(math.cos(stack.pop()))	
					elif(token == "sin"):
						stack.push(math.sin(stack.pop()))
					elif(token == "fact"):
						stack.push(math.factorial(stack.pop()))	
					elif(token == "pi"):
						stack.push(math.pi)
					else:
						stack.push(int(token))
				except Exception as e:                        #  if there was an error
					print stack.stack                         #+ its probably the input
					print "Error in input: " + str(e)
					exit()

			print stack          # print result
			ans = stack.stack[0] # for recall later
		else:		       
			exit() # if it is Q to quit, quit

if __name__ == '__main__':
	main()
[/PHP]

Output:
```

matthew@matthew-desktop:~/Documents/Programming/Python$ python reverse_polish.py 
Everything must be spaced seperated
Enter your sum: 3 4 - 5 +
4
Enter your sum: 3 4 5 * -
-17
Enter your sum: 5 1 2 + 4 * + 3 -#
[3, 17]
Error in input: invalid literal for int() with base 10: '-#'
matthew@matthew-desktop:~/Documents/Programming/Python$ python reverse_polish.py 
Everything must be spaced seperated
Enter your sum: 5 2 ^
25
Enter your sum: 10 5 %
0
Enter your sum: 10 3 /
3.333333333333333
Enter your sum: 10 0 /
Divide by 0 error
10
Enter your sum: 10 sin
-0.544021110889
Enter your sum: 10 cos
-0.839071529076
Enter your sum: 10 sqrt
3.16227766017
Enter your sum: 10 fact
3628800
Enter your sum: pi
3.14159265359
Enter your sum: Q
matthew@matthew-desktop:~/Documents/Programming/Python$ 

```

---

### Post by lisati on 2010-03-29
> **lavinog said:**
> Is it just me, or are these Beginner challenges more likely suited for the intermediate challenges?

Interesting point. I vaguely recall a related programming task coming up in one of the courses available to second-year students at the University I attended, but one I don't think I took that subject (too much partying? wrong course? it was a long tima ago). If memory serves correctly it was related to converting regular algebraic expressions to RPN (a.k.a. infix to postfix)

---

### Post by tooatw on 2010-03-29
> **schauerlich said:**
> 
[SIZE=3]_Example output, for testing:_[/SIZE]
```
eric@river:~$ ./rpn
> 3 4 +
7.0
> 10 3 /
3.33333333333
> 2 5 ^
32.0
>  10 2 %
0.0
> 24 12 3 + 4 % / 6 - 4 * 3 ^
512.0
> 10 2 2 % /
Divided by Zero
// Incorrect inputs:
> 10 + 10
Not enough operands
> 10 10 10 +
Too many operands
> 
> aw4ojghsiu5esrgs56u7ikdyjdt drthisu 5 hrtgh 5 5 +
Unrecognized token
> 45 6 + / & 4
Unrecognized token
> q
eric@river:~$
```
i see that you modified it
so tell us exactly what happens
if the result is an integer only display one digit after the dot (why?) otherwise display 10?
why cant it be standard one digit after the , or standard 10

---

### Post by schauerlich on 2010-03-29
> **tooatw said:**
> i see that you modified it
so tell us exactly what happens
if the result is an integer only display one digit after the dot (why?) otherwise display 10?
why cant it be standard one digit after the , or standard 10

Yes I did modify it, sorry. I wanted to clarify that division should be true division - that means 10 3 / should be 3.333..., not 3.0. You should cast to a float *before* you do the division, not after.

---

### Post by blur xc on 2010-03-29
Just a quick fyi that would help all of us studying code posted here- edit your text editor's config files to enter spaces instead of tab characters when the tab key is pressed.  For example- in my .vimrc I have these lines-
```
set smartindent
set tabstop=4
set shiftwidth=4
set expandtab
```I don't recall exactly what each line does- I copied it off of some website with VIM information.  All that matters is that when I press the tab key - I get four spaces instead of a tab character.  

I copied and pasted the above code into vim, and I've got a huge mess to clean up before I can run or study it.

BM

edit- nevermind- I think I figured out what my problem was...

---

### Post by WillFerrellLuva on 2010-03-29
my messy c++ code that works for rpn:

```

#include <iostream>
#include <fstream>
#include <string>
#include <vector>
#include <cstdlib>
#include <cmath>
#include <iomanip>

using namespace std;

void rpn(const vector<string>& in)
{
	string out, temp;
	double answer = 0;
	double arguments[20] = {0};
	int arg_count = 0;
	unsigned int index = 0;
	bool error = false;
	
	do{
		temp = in[index];
		int int_temp = atoi(temp.c_str());	//used to check if word is a number
		char char_temp = temp[0];		//used to check if word is an operator
				
		if(int_temp > 0) 			//word is a non-zero number
		{
			arguments[arg_count] = int_temp;
			arg_count ++;
		}
		else if(char_temp == 48) 		//word is zero
		{
			arguments[arg_count] = 0;
			arg_count ++;
		}
		else if(index <= 1)		//encountered an operator/gibberish before having 2 arguments
		{
			error = true;
			index = in.size();
			cout << "Error in input." << endl;
		}
		else if(char_temp == 43) 		// + operator
		{
			if(arg_count > 1)
			{
				answer = arguments[arg_count-2] + arguments[arg_count-1];
				arguments[arg_count-2] = answer;
				arg_count--;
			}
			else if(arg_count <= 1)
			{
				answer += arguments[arg_count-1];
				arg_count--;
			}
		}
		else if(char_temp == 37) 		// % operator
		{
			if(arg_count > 1)
			{
				answer = static_cast<int>(arguments[arg_count-2]) % static_cast<int>(arguments[arg_count-1]);
				arguments[arg_count-2] = answer;
				arg_count--;
			}
			else if(arg_count <= 1)
			{
				answer = static_cast<int>(arguments[arg_count-1]) % static_cast<int>(answer);
				arg_count--;
			}
			 
		}
		else if(char_temp == 42)		 // * operator
		{
			if(arg_count > 1)
			{
				answer = arguments[arg_count-2] * arguments[arg_count-1];
				arguments[arg_count-2] = answer;
				arg_count--;
			}
			else if(arg_count <= 1)
			{
				answer *= arguments[arg_count-1];
				arg_count--;
			}
		}
		else if(char_temp == 45) 		// - operator
		{
			if(arg_count > 1)
			{
				answer = arguments[arg_count-2] - arguments[arg_count-1];
				arguments[arg_count-2] = answer;
				arg_count--;
			}
			else if(arg_count <= 1)
			{
				answer -= arguments[arg_count-1];
				arg_count--;
			}
		}
		else if(char_temp == 47) 		// / operator
		{
			if(arg_count > 1)
			{
				if(arguments[arg_count-1] == 0)
				{
					cout << "Dividing by zero!" << endl;
					error = true;
			 		index = in.size();
				}
				else
				{
					answer = arguments[arg_count-2] / arguments[arg_count-1];
					arguments[arg_count-2] = answer;
					arg_count--;
				}
			}
			else if(arg_count <= 1)
			{
				if(arguments[arg_count-1] == 0)
				{
					cout << "Dividing by zero!" << endl;
					error = true;
			 		index = in.size();
				}
				else
				{
					answer /= arguments[arg_count-1];
					arg_count--;
				}
			}
		}
		else if(char_temp == 94) 		// ^ operator
		{
			if(arg_count > 1)
			{
				answer = pow(arguments[arg_count-2], arguments[arg_count-1]);
				arguments[arg_count-2] = answer;
				arg_count--;
			}
			else if(arg_count <= 1)
			{
				answer = pow(arguments[arg_count-1], answer);
				arg_count--;
			}
		}
		else
		{
			cout << "Unrecognized token." << endl;
			error = true;
			index = in.size();
		}
		
		index++;

	}while(index < in.size());
	
	if(arg_count == 1 && !error)
	{
		cout << answer << endl;
	}
	else if(!error)
	{
		cout << "Error in input." << endl;
	}
}



int main(int argc, char* argv[])

{
	if(argc != 2)
	{
		cout << "Must enter a file to evaluate at the command line." << endl;
	}
	
	fstream in;
	in.open(argv[1], ios::in);
	string line, word;
	cout.precision(10);
	
	if(in.good())
	{
		while(getline(in, line))  //get lines
		{
			vector<string> words;
			cout << "> " << line << endl;
			
			while(line != "") //while line is non-empty, parse line into words
			{
				size_t found = 0;				//find space char
				found = line.find_first_of(" ");
				if(found < line.size())
				{
					word = line.substr(0,found);		//create word based on substring of line
					words.push_back(word);			//add word to the vector
					line = line.substr(found+1);		//remove word from line
				}
				else  						//no more whitespace - add last word
				{
					words.push_back(line);
					line = "";
				}
			}
			
			rpn(words);		//call rpn to process the words
			//cout << endl;
		}
	}
	else
	{
		cout << "Error opening file." << endl;
	}
	in.close();
	

	return 0;

}

```

output:
```

chris@chris-desktop:~/Code/Projects/Challenge 11$ ./driver test
> 3 4 +
7
> 10 3 /
3.333333333
> 2 5 ^
32
> 10 2 %
0
> 24 12 3 + 4 % / 6 - 4 * 3 ^
512
> 10 2 2 % /
Dividing by zero!
> 10 + 10
Error in input.
> aw4ojghsiu5esrgs56u7ikdyjdt drthisu 5 hrtgh 5 5 +
Error in input.
> 45 6 + / & 4
Unrecognized token.

```

---

### Post by WillFerrellLuva on 2010-03-29
Here is a little cleaner implementation.  rpn is a class now, and now the user has a choice to open a file or enter a rpn string of their own.

driver.cpp
```

#include "rpn.h"
#include <iostream>
#include <fstream>
#include <string>
#include <vector>
#include <cmath>
#include <iomanip>

using namespace std;


int main(int argc, char* argv[])

{
	string choose = "q";
	string rpn_eval = "";
	string filename = "";
	
	do{
		cout << "(O)pen a file, (E)nter a string, or (Q)uit: ";
		getline (cin, choose);
		
		if(choose == "O" || choose == "o")
		{
			cout << "Enter the name of the file to open: ";
			getline (cin, filename);
			fstream in;
			in.open(filename.c_str(), ios::in);
			if(in.good())
			{
				string line;
				while(getline(in, line))  //get lines
				{
					cout << "> " << line << endl;
					rpn one(line);
					cout << one << endl;
				}
				in.close();	
			}
			else
			{
				cout << "Error opening file." << endl;
			}
		}	
			
		else if(choose == "E" || choose == "e")
		{
			cout << "Enter a RPN string to be evaluated: ";
			getline (cin, rpn_eval);
			rpn one(rpn_eval);
			cout << one << endl;
		}
	}while(choose != "Q" && choose !="q");
		
	

	return 0;

}

```

rpn.h
```

#ifndef RPN_H
#define RPN_H
#include <string>
#include <vector>

class rpn

{
  private:
	std::string s_out;
	const std::string double_to_string(const double& input) const;
	

  public:

	rpn(std::string& line);
	friend std::ostream& operator<<(std::ostream& out, const rpn& show) {return out << show.s_out;}

};
#endif

```

and rpn.cpp
```

#include "rpn.h"
#include <string>
#include <vector>
#include <cmath>
#include <iostream>
#include <cstdlib>
#include <sstream>
using namespace std;

const string rpn::double_to_string(const double& input) const
{
	ostringstream oss;
	oss << input;
	return oss.str();
}

rpn::rpn(string& line)
{
	string word;
	vector<string> words;
	
	if(line == "")
	{
		s_out = "Empty string sent for evaluation!";
		return;
	}
			
	while(line != "") //while line is non-empty, p**** line into words
	{
		size_t found = 0;				//find space char
		found = line.find_first_of(" ");
		if(found < line.size())
		{
			word = line.substr(0,found);		//create word based on substring of line
			words.push_back(word);			//add word to the vector
			line = line.substr(found+1);		//remove word from line
		}
		else  						//no more whitespace - add last word
		{
			words.push_back(line);
			line = "";
		}
	}
	
	string temp;
	double arguments[20] = {0};
	int arg_count = 0;
	unsigned int index = 0;
	bool error = false;
	
	do{
		temp = words[index];
		int int_temp = atoi(temp.c_str());	//used to check if word is a number
		char char_temp = temp[0];		//used to check if word is an operator
				
		if(int_temp > 0) 			//word is a non-zero number
		{
			arguments[arg_count] = int_temp;
			arg_count ++;
		}
		else if(char_temp == 48) 		//word is zero
		{
			arguments[arg_count] = 0;
			arg_count ++;
		}
		else if(index <= 1)		//encountered an operator/gibberish before having 2 arguments
		{
			error = true;
			index = words.size();
			if(char_temp == 43 || char_temp == 37 || char_temp == 42 || char_temp == 45 || char_temp == 47 || char_temp == 94)
				s_out = "Encountered an operator before having at least two arguments.";
			else
				s_out = "Unrecognized token.";
		}
		else if(char_temp == 43) 		// + operator
		{
			arguments[arg_count-2] = arguments[arg_count-2] + arguments[arg_count-1];
			arg_count--;
			
		}
		else if(char_temp == 37) 		// % operator
		{
			arguments[arg_count-2] = static_cast<int>(arguments[arg_count-2]) % static_cast<int>(arguments[arg_count-1]);
			arg_count--;			 
		}
		else if(char_temp == 42)		 // * operator
		{
			arguments[arg_count-2] = arguments[arg_count-2] * arguments[arg_count-1];
			arg_count--;
		}
		else if(char_temp == 45) 		// - operator
		{
			arguments[arg_count-2] = arguments[arg_count-2] - arguments[arg_count-1];
			arg_count--;
		}
		else if(char_temp == 47) 		// / operator
		{
			if(arguments[arg_count-1] == 0)
			{
				s_out = "Divided by zero.";
				error = true;
			 	index = words.size();
			}
			else
			{
				arguments[arg_count-2] = arguments[arg_count-2] / arguments[arg_count-1];
				arg_count--;
			}
		}
		else if(char_temp == 94) 		// ^ operator
		{
			arguments[arg_count-2] = pow(arguments[arg_count-2], arguments[arg_count-1]);
			arg_count--;
		}
		else
		{
			s_out = "Unrecognized token.";
			error = true;
			index = words.size();
		}
		
		index++;

	}while(index < words.size());
	
	if(arg_count == 1 && !error)
	{
		s_out = double_to_string(arguments[arg_count-1]);
	}
	else if(!error)
	{
		s_out = "Incorrect number of arguments/operators.";
	}
}

```

---

### Post by schauerlich on 2010-03-29
> **WillFerrellLuva said:**
> I have an issue though.  I dont want to open the std namespace in rpn.h, however every time i try to compile without it i get the following error:
```

rpn.h:14: error: ISO C++ forbids declaration of ‘vector’ with no type

```
Anybody know how I can correctly declare that vector?

Just like anything else from the STL, prepend it with std::

```
rpn(const std::vector<std::string>& words);
```

---

### Post by WillFerrellLuva on 2010-03-29
tyvm, will edit my code.

---

### Post by tooatw on 2010-03-30
```
alexander@amd64:~/1$ ./rpn
> 3 4 +
7.0
> 10 3 /
3.3333333333
> 2 5 ^
32.0
> 10 2 %
0.0
> 24 12 3 + 4 % / 6 - 4 * 3 ^
512.0
> 10 2 2 % /
Divided by Zero
> 10 + 10
Not enough operands
> 10 10 10 +
Too many operands
>
> aw4ojghsiu5esrgs56u7ikdyjdt drthisu 5 hrtgh 5 5 +
Unrecognized token
> 45 6 + / & 4
Unrecognized token
> exit
alexander@amd64:~/1$ 
```[PHP]// Beginner Programming Challenge #11
#include <stdio.h> //standard for i/o
#include <stdlib.h> // standard again
#include <string.h> // string library
#include <math.h> // for the power function
int i,true=2,k[99],is,is2,w,iv,si,temp1,temp2,dubios,nc,zero,neo;
/*
 i is standard
 true is something that is always true since i don't know the c version of "while true"
 is is the empty spaces in the string counter
 is2 is the 'how much till the end' counter
 w is like a secondary i
 si counts how many words are between two spaces since operators can only use one space
 dubios seeks dubious behaviour
 nc is the number counter
 number is the temporary number
 zero alerts if someone wants to divide by 0
 neo is the not enough operators counter
 num is the number array 
 */
char x[100];
//the string
double number,num[99];
int main(){
    while (true){
        for (i=0;i<99;++i) num[i]=k[i]=0; // reset the arrays
        i=is=is2=w=iv=si=dubios=nc=zero=neo=number=0; // reset the variables
        printf("> ");
        gets(x);
        if (strcmp(x,"exit")== 0) break;
        for (i=0;i<strlen(x);++i){ //find empty spaces and keep track of them in k
            if (x[i]==' ') {
                    k[is] = i; 
                    ++is;
            }
        }
        if (k[is] != strlen(x)) {k[is]=strlen(x);++is;} // add to the counter the last element
        iv=0;// needed later on
        for (w=0;w<is;++w){  // for all the empty spaces
            is2=k[w]-iv; //how many characters does the string fragment have
            number=0; //reset the number
            for (i=iv;i<k[w];++i){ //figure out what the number is
                si=is2;
                switch(x[i]){
                    case '0'...'9': number += ((x[i] - '0') * pow( 10.0 , is2-1));
                                    --is2 ;
                                    if (is2==0) { //when is reaches 0 save the number 
                                        num[nc]=number;
                                        ++nc;
                                    }
                                    break;    
                    case  '+':    if (si==1){ 
                                    if(nc>1){ 
                                        num[nc-2]=num[nc-2]+num[nc-1]; 
                                        num[nc-1]=num[nc];
                                        --nc;
                                    } 
                                    else ++neo;
                                } 
                                else ++dubios;break;
                    case  '-':    if (si==1){ 
                                    if(nc>1){ 
                                        num[nc-2]=num[nc-2]-num[nc-1]; 
                                        num[nc-1]=num[nc];
                                        --nc;
                                    } 
                                    else ++neo;
                                } 
                                else ++dubios;break;
                    case  '/':    if (si==1){ 
                                    if(nc>1){ 
                                        if (num[nc-1]!=0){ 
                                            num[nc-2]=num[nc-2]/num[nc-1]; 
                                            num[nc-1]=num[nc]; 
                                            --nc;
                                        } 
                                        else ++zero;
                                    }  
                                    else ++neo;
                                } 
                                else ++dubios;break;
                    case  '*':    if (si==1){ 
                                    if(nc>1){ 
                                        num[nc-2]=num[nc-2]*num[nc-1]; 
                                        num[nc-1]=num[nc]; 
                                        --nc;
                                    } 
                                    else ++neo;
                                } 
                                else ++dubios;break;
                    case  '^':    if (si==1){ 
                                    if(nc>1){ 
                                        num[nc-2]=pow(num[nc-2],num[nc-1]); 
                                        num[nc-1]=num[nc]; 
                                        --nc;
                                    } 
                                    else ++neo;
                                } 
                                else ++dubios;break;
                    case  '%':    if (si==1){ 
                                    if(nc>1){ 
                                        temp1=num[nc-2];
                                        temp2=num[nc-1];
                                        num[nc-2]=temp1%temp2; 
                                        num[nc-1]=num[nc]; 
                                        --nc;
                                    } 
                                    else ++neo;
                                } 
                                else ++dubios;break;
                    //for all cases of operands if the string fragment is wider than 1 caracter mark it as dubious behavior and if you dont have at least 2 operands mark it down
                    default: ++dubios;break;
                    //anything else goes to dubious behaviour
                }
            }
            iv=k[w];//we need this to find out the word size
            ++iv;
        }
    if (dubios==0){//if nothing is dubious ... this should be obvious
        if (zero!=0) printf("Divided by Zero\n"); 
        else if (neo>0) printf("Not enough operands\n");
        else if (neo==0 &&nc>1) printf("Too many operands\n");
        else if (nc==0); //if empty string
        else {
            temp1=num[nc-1];
            if (temp1==num[nc-1])printf("%.1f\n",num[nc-1]);
            else printf("%.10f\n",num[nc-1]);
        }
        }// if everything goes to plan print the number
     else printf("Unrecognized token\n");
    }
return 0;
}
[/PHP]

---

### Post by Bodsda on 2010-03-30
> **lavinog said:**
> Is it just me, or are these Beginner challenges more likely suited for the intermediate challenges?
 
I think the very fact that you have to ask that means that your correct. Whilst these are supposed to be challenges, a beginner should be able to accomplish them. By beginner, I mean someone who started coding a few weeks ago, not someone who has been coding a while but does not consider themselves very good. 
 
I would like to remind all OP's of these challenges to please bear in mind the skillset of your audience. We do not want to alienate the very new programmers.
 
I would also like to remind beginners that although this task may seem way too difficult, it is not. With some research of rpn and algorithms, along with some active discussion, I believe anyone could accomplish this. If you need help, remember that the sponsors of these challenges are more then happy to give you a hand, we are on irc.freenode.net in #ubuntu-beginners-dev
 
Bodsda

---

### Post by WillFerrellLuva on 2010-03-30
edited my code a few posts up.  rpn now takes a string and writes a string with an overloaded << operator (parsing the string is now handled by rpn).

---

### Post by Coward on 2010-03-30
This is really limited, without using even standard input or implementing any error checking. Just for fun, a bit of scheme:

```
;I don't know how to easily do standard input, so please just change
;the inp list to represent the equation you want to test it with.
(define inp '(3 4 * 9.2 /))

;Immedialty call helper function with an empty stack
(define (pol expr) (pol-helper '() expr))

;Helper function. As you can see only +, -, *, and / have been defined.
(define (pol-helper stack expr) (
	if(eqv? expr '()) (car stack)
		(cond ((eqv? (car expr) '+)
			(pol-helper
(cons (+ (cadr stack) (car stack)) (cddr stack)) (cdr expr)))
			((eqv? (car expr) '-)
			 (pol-helper
(cons (- (cadr stack) (car stack)) (cddr stack)) (cdr expr)))
			((eqv? (car expr) '*)
			 (pol-helper
(cons (* (cadr stack) (car stack)) (cddr stack)) (cdr expr)))
			((eqv? (car expr) '/)
			 (pol-helper
(cons (/ (cadr stack) (car stack)) (cddr stack)) (cdr expr)))
		(else
			(pol-helper
(cons (car expr) stack) (cdr expr))))))

;Call the polish expression evaluator with the input. Display result.
(display (pol inp))
(newline)
```

---

### Post by Junkieman on 2010-03-30
Update: I rewrote my code, it now handles unrecognised tokens. See below for a curious result...

I'm learning Python and this is my first piece of code that actually tries to do something.

The results:
```
Enter your RPN expression, 'q' to quit
> 3 4 +
7.0
> 10 3 /
3.33333333333
> 2 5 ^
32.0
> 10 2 %
0.0
> 24 12 3 + 4 % / 6 - 4 * 3 ^
512.0
> 10 2 2 % /
Division by zero
> [COLOR="blue"]10 + 10
10.0
> 10 10 10 +
20.0[/COLOR]
> aw4ojghsiu5esrgs56u7ikdyjdt drthisu 5 hrtgh 5 5 +
Unrecognized token 'aw4ojghsiu5esrgs56u7ikdyjdt'
> 45 6 + / & 4
Unrecognized token '&'
> q
```

I have a question. Consider this expression breakdown:

```
> 45 6 + /
Input = 45    Stack = [45.0, None, None, None]
Input = 6     Stack = [6.0, 45.0, None, None]
Input = +     Stack = [51.0, None, None, None]
Input = /     Stack = [1.0, [COLOR="Blue"]None[/COLOR], None, None]
1.0

```

Is this correct, according to RPN rules? The divide operator copies X register into Y (if Y is None), then divides. So it divides the last result with itself. 

This is the same logic that applies to this expression, but the result I get is different than the expected result (Not enough operands):

```
> 10 + 10
Input = 10    Stack = [10.0, None, None, None]
Input = +     Stack = [20.0, None, None, None]
Input = 10    Stack = [10.0, 20.0, None, None]
10.0
```

For extras, I made it reusable as a python module:

```
# rpnlib.py
# Ubuntuforums Beginner Programming Challenge #11
import math

# Set true to view stack info during evaluation
DEBUG_INFO = True

# define our list of operators
operators = ("+", "-", "*", "/", "%", "^")


def calculate(a, b, operator):
    """ Calculates the value of a, b via the operator
    Returns the answer
    """
    try:
        if operator == "+":
            return b + a
        if operator == "-":
            return b - a
        if operator == "*":
            return b * a
        if operator == "/":
            return b / a
        if operator == "%":
            return b % a
        if operator == "^":
            return math.pow(b, a)
    except:
        return None


def shiftDown(stack, value):
    """ Shift the stack down, and insert the given value in the front
    Returns the modified stack
    """
    # duplicate the T register
    stack.append(stack[len(stack)-1])       # [X, Y, Z, T, T]
    # reverse the list, allowing us to pop items off the 'beginning' of the stack, ie X and Y
    stack.reverse()                         # [T, T, Z, Y, X] 
    # pop the X and Y registers, they're being replaced by the new calculated value
    stack.pop()                             # [T, Z, Y, X] 
    stack.pop()                             # [T, Z, Y] 
    # add the new value
    stack.append(value)                     # [T, Z, Y, X]
    # flip back to normality
    stack.reverse()                         # [X, Y, Z, T]
    return stack


def shiftUp(stack, value):
    """ Shift the stack up, insert the new value in front, push the old value out back
    """
    try:
        # test for a numeric value
        value = float(value)
    except:
        if DEBUG_INFO == True: print "Failed converting '{0}' to float".format(value)
        return ["Unrecognized token '%s'" % value]
    
    # insert the value in the stack
    stack.insert(0, value)
    
    # pop the last item off
    stack.pop()
    return stack


def addvalue(value, stack):
    """ Add the given value to the stack, operators calculate the value into the stack at X.
    The stack registers map to the list like so: [X, Y, Z, T]
    Returns the modified stack
    """
    
    # intialize the stack
    if stack == None:
        stack = [None, None, None, None]
    
    # define our register constants
    X = 0
    Y = 1
    Z = 2
    T = len(stack)-1
    
    # test if the value is an operator
    if value in operators:
        
        # clone the X register into Y, if Y is None
        if stack[Y] == None:
            stack = shiftUp(stack, stack[X])

        # calculate the new answer of registers X and Y. 'value' is our operator.
        a = float(stack[X])
        b = float(stack[Y])
        new_value = calculate(a, b, value)
        
        # do not process infinity problems
        if new_value == None:
            if DEBUG_INFO == True: print "Calculate failed on {0} {1} {2}".format(b, value, a)
            return ["Division by zero"]
        else:
            return shiftDown(stack, new_value)
        
    else:
        # Not an operator
        return shiftUp(stack, value)


def evaluate(expression):
    """ Evaluate the RPN expression.
    Returns the answer
    """
    stack = None
    tokens = expression.split(" ")
    
    # process each token in the expression
    for t in tokens:
        
        # process the current token
        stack = addvalue(t, stack)
        
        # print debug info
        if DEBUG_INFO == True: print "Input = {0:5} Stack = {1}".format(t, stack)
        
        # if the stack contains one item its an error message
        if len(stack) == 1: return stack[0]
    
    # return the first value in the stack, the answer
    return stack[0]


if __name__ == "__main__":
    print "Enter your RPN expression, 'q' to quit"
    key = ""
    while True:
        key = raw_input("> ")
        if key == "q" or key == "Q": break
        print evaluate(key)

```

---

### Post by vik_2010 on 2010-03-31
This is my code. I'm new to programming, so any advice would be warmly received.

[PHP]
#!/usr/bin/env python

from types import ListType
import sys

def RPNCalc():
    datainput=str(raw_input("> "))
    to_int = evaluate(datainput)
    result = compute(to_int)
    print result
    RPNCalc()

def is_num(inputdata):
    try:
        float(inputdata)
        return True
    except ValueError:
        return False

def evaluate(datainput):
    new_list=[]
    input_list = datainput.split(' ')
    for elem in input_list:
        if is_num(elem):
            new_list.append(int(elem))
        elif elem in ['+','-','%','*','^','/']:
            new_list.append(elem)
        else:
            print "Wrong Input. Exiting...."
            sys.exit(0)
    return new_list
            
def compute(inputlist):
    i = 0
    while len(inputlist)>1:
        if is_num(inputlist[i]):
            i += 1
        elif not is_num(inputlist[i]):
            if inputlist[i] is '+':
                inputlist[i-2] += inputlist[i-1]
            elif inputlist[i] is '-':
                inputlist[i-2] -= inputlist[i-1]
            elif inputlist[i] is '*':
                inputlist[i-2] *= inputlist[i-1]
            elif inputlist[i] is '/':
                inputlist[i-2] = float(inputlist[i-2]) / inputlist[i-1]
            elif inputlist[i] is '%':
                inputlist[i-2] %= inputlist[i-1]
            elif inputlist[i] is '^':
                inputlist[i-2] = pow(inputlist[i-2], inputlist[i-1])
            else:
                print "Invalid data. Exiting...."
                sys.exit(0)
            del inputlist[i-1:i+1]
            i = 0
        else:
            print "Invalid data. Will Exit...."
            sys.exit(0)
    return inputlist[0]
    
if __name__=="__main__":
    RPNCalc()
[/PHP]EDIT: My calc croaks on input like (10 + 10) - I recede through the list to compute values, and the index just goes to the back if an unusual input is provided. Will Correct.

---

### Post by matmatmat on 2010-03-31
Edited my code [here]("http://ubuntuforums.org/showpost.php?p=9046082&postcount=18").

---

### Post by WillFerrellLuva on 2010-03-31
Made the user input handling more forgiving, made some error messages a little more explicit, and made rpn able to handle empty strings w/o seg faulting.

I have a small issue in formatting the output.  All that stuff is in <iomanip> right?  Need some guidance in that department.

```

chris@chris-desktop:~/Code/Projects/Challenge 11$ ./driver
(O)pen a file, (E)nter a string, or (Q)uit: o
Enter the name of the file to open: test
> 3 4 +
7
> 10 3 /
3.33333
> 2 5 ^
32
> 10 2 %
0
> 24 12 3 + 4 % / 6 - 4 * 3 ^
512
> 10 2 2 % /
Divided by zero.
> 10 + 10
Encountered an operator before having at least two arguments.
> aw4ojghsiu5esrgs56u7ikdyjdt drthisu 5 hrtgh 5 5 +
Unrecognized token.
> 45 6 + / & 4
Unrecognized token.
(O)pen a file, (E)nter a string, or (Q)uit: e
Enter a RPN string to be evaluated: 
Empty string sent for evaluation!
(O)pen a file, (E)nter a string, or (Q)uit: 
(O)pen a file, (E)nter a string, or (Q)uit: e
Enter a RPN string to be evaluated: 10 10 10 +
Incorrect number of arguments/operators.
(O)pen a file, (E)nter a string, or (Q)uit: q

```

---

### Post by lavinog on 2010-03-31
Ok here is my go with python:
[php]
#! /usr/bin/env python
'''rpn_calc.py - Evaluates expressions in reverse polish notation format.
Created by: Greg Lavino for ubuntuforums beginner programming challenge #11
03.31.2010
'''


# Custom errors for error handling
class TooManyOperandsError(Exception):
    pass

class NotEnoughOperandsError(Exception):
    pass

class UnrecognizedTokenError(Exception):
    pass


class ReversePolishNotation:
    
    OPERATIONS={'+':lambda v1,v2 : v1 + v2,
                '-':lambda v1,v2 : v1 - v2,
                '*':lambda v1,v2 : v1 * v2,
                '/':lambda v1,v2 : v1 / v2,
                '%':lambda v1,v2 : v1 % v2,
                '^':lambda v1,v2 : v1 ** v2}

    
    def __init__(self):
        self.finalresult=None
        

    def evaluate(self,inputstr):
        '''evaluates inputstr as RPN'''
        
        # remove whitespace
        self.input = inputstr.strip()
        
        # split up arguments
        self.arg_list = self.input.split(' ')
        
        # preliminary checks
        self.check_tokens()
        
        while True:
            
            # get next operator
            self.operator_index = self.get_next_op()
            
            if not self.operator_index:
                break # no more operators, must be done
            
            # should have two values before operator
            if self.operator_index==1:
                raise NotEnoughOperandsError
            
            # grab next operator and operands
            self.operator = self.arg_list[ self.operator_index ]
            self.var1 = float(self.arg_list[ self.operator_index - 2 ])
            self.var2 = float(self.arg_list[ self.operator_index - 1 ])

            # evaluate
            self.do_operation()
            
            # substitute expression with result
            self.replace_sub_expression()
        
        # Old error check
        # This should be caught in the preliminary checks
        # Left in just in case
        if len(self.arg_list)>1:
            print 'SHOULD NOT GET THIS: TOO MANY OPERANDS'
            raise TooManyOperandsError
        
        # convert list item to value
        result = self.arg_list[0]

        #determine if result is int and return appropriate value
        if result==int(result):
            self.finalresult = int(result)
        else:
            self.finalresult = result
        
        return self.finalresult

    def check_tokens(self):
        '''Preliminary checks of arg_list'''
        op_count = 0
        num_count = 0
        
        for index,token in enumerate(self.arg_list):
            
            # Check if operator
            if token in self.OPERATIONS.keys() :
                op_count+=1
            
            # check if numeric
            elif self.isnumeric(token) :
                num_count+=1
            
            # replace ans with result from previous calculation
            elif token.lower()=='ans' and self.finalresult:
                self.arg_list[index]=self.finalresult
                num_count+=1
                
            else:
                raise UnrecognizedTokenError
        
        # Ensure we have correct number of operands and operators
        if op_count+1 < num_count:
            raise TooManyOperandsError
        
        elif op_count+1 > num_count:
            raise NotEnoughOperandsError



    def isnumeric(self,string):
        '''Determine if string is numeric'''
        try:
            float(string)
        except ValueError:
            return False
        return True
            

    def do_operation(self):
        '''Uses OPERATIONS dict to evaluate next operation'''
        if self.operator in self.OPERATIONS.keys():
            self.result = self.OPERATIONS[self.operator](self.var1,self.var2)
        
        
    def replace_sub_expression(self):
        ''' replaces the evaluated subexpression with result'''
        
        # clear out the two operands
        self.arg_list[ self.operator_index - 2] = None
        self.arg_list[ self.operator_index - 1] = None
        
        # replace operator with result
        self.arg_list[ self.operator_index ] = self.result
        
        # remove the cleared items
        self.arg_list = [ item for item in self.arg_list if item != None ]
        
    
    def get_next_op(self):
        '''Retuns index of next operator'''
        for index , chr in enumerate(self.arg_list):
            if chr in self.OPERATIONS.keys():
                return index
        


####### End of ReversePolishNotation Class ########


def show_help():
    print '''RPN Calculator - By Greg Lavino
    use load [filename] to load a file containing expressions to evaluate
    
    Last answer is stored in 'ans'
    
    For help type 'help'

    To exit type 'quit'
    '''
    

def exit_calc():
    '''Provides a custom exit'''
    print 'Have a nice day.'
    exit()


def main():
    rpn=ReversePolishNotation()
    
    show_help()
    
    while True:
    
        inputstr = raw_input('>')
        if not inputstr:
            continue        # Ignore blank lines
        
        # Check for exit
        elif inputstr.lower()=='quit' or inputstr.lower()=='exit' :
            exit_calc()
            
        # Check for help request
        elif inputstr.lower()=='help':
            show_help()
            
            
        # Load input from file
        elif inputstr.lower().startswith('load'):
            filename = inputstr.split(' ')[1]
            try:
                file = open(filename)
            except IOError:
                print 'File:%s could not be opened'% filename
                continue
            
            for line in file.readlines():
                line = line.strip()
                if line:
                    print '%s> %s' % ( filename, line )
                    evaluate(rpn,line)
            
        else:
            evaluate(rpn,inputstr)
    

def evaluate(rpn,inputstr):
    '''Evaluates inputstr with rpn object
       while handling errors that may occur.'''
       
    try:
        result = rpn.evaluate(inputstr)
    except ZeroDivisionError:
        print 'Divide by Zero'
        return
        
    except NotEnoughOperandsError:
        print 'Not enough operands'
        return
    
    except TooManyOperandsError:
        print 'Too many operands'
        return
    
    except UnrecognizedTokenError:
        print 'Unrecognized token'
        return

    
    print result
    

if __name__=='__main__':
    main()

[/php]

I was going to add a other operators, but I can only think of functions that take one value (sqrt, sin, cos...etc.) In which case I would need to modify some parts to recognize when only one value is needed.
I see that my approach could be simplified if I just use a stack...so I am going to try that now.

I did add a ans variable to allow recalling the previous answer

---

### Post by -grubby on 2010-03-31
Here's my version. Please tell me if it gives you any errors (it takes command line arguments.) It does not understand the % or ^ operators.

EDIT: now it does

```
[color=#008000]**from**[/color] [color=#0000FF]**sys**[/color] [color=#008000]**import**[/color] argv

[color=#008000]**def**[/color] [color=#0000FF]is_operator[/color](value):
    [color=#008000]**if**[/color] value [color=#AA22FF]**is**[/color] [color=#BA2121]"+"[/color] [color=#AA22FF]**or**[/color] value [color=#AA22FF]**is**[/color] [color=#BA2121]"-"[/color] [color=#AA22FF]**or**[/color] value [color=#AA22FF]**is**[/color] [color=#BA2121]"*"[/color] [color=#AA22FF]**or**[/color] value [color=#AA22FF]**is**[/color] [color=#BA2121]"/"[/color]\
    [color=#AA22FF]**or**[/color] value [color=#AA22FF]**is**[/color] [color=#BA2121]"%"[/color] [color=#AA22FF]**or**[/color] value [color=#AA22FF]**is**[/color] [color=#BA2121]"^"[/color]:
        [color=#008000]**return**[/color] [color=#008000]True[/color]
    [color=#008000]**return**[/color] [color=#008000]False[/color] 
                 
[color=#008000]**def**[/color] [color=#0000FF]main[/color]():
    stack [color=#666666]=[/color] []
    tokens [color=#666666]=[/color] argv[[color=#666666]1[/color]:]
    
    [color=#008000]**if**[/color] [color=#008000]len[/color](tokens) [color=#AA22FF]**is**[/color] [color=#666666]0[/color]:
        [color=#008000]exit[/color]()
    [color=#008000]**if**[/color] [color=#008000]len[/color](tokens) [color=#AA22FF]**is**[/color] [color=#666666]1[/color]:
        [color=#008000]**return**[/color] tokens[[color=#666666]0[/color]]

    [color=#008000]**for**[/color] token [color=#AA22FF]**in**[/color] tokens:
        [color=#008000]**if**[/color] [color=#AA22FF]**not**[/color] is_operator(token):
            [color=#008000]**try**[/color]:
                token [color=#666666]=[/color] [color=#008000]float[/color](token)
                stack[color=#666666].[/color]append(token)
            [color=#008000]**except**[/color] [color=#D2413A]**ValueError**[/color]:
                [color=#008000]**print**[/color] [color=#BA2121]"Invalid operand '[/color][color=#BB6688]**%s**[/color][color=#BA2121]'; must be a number"[/color] [color=#666666]%[/color] token
                [color=#008000]exit[/color]()
        [color=#008000]**else**[/color]:
            [color=#008000]**if**[/color] [color=#008000]len[/color](stack) [color=#666666]<[/color] [color=#666666]2[/color]:
                [color=#008000]**print**[/color] [color=#BA2121]"Error: Too little operands"[/color]
                [color=#008000]exit[/color]()
            [color=#008000]**elif**[/color] [color=#008000]len[/color](stack) [color=#666666]>[/color] [color=#666666]2[/color]:
                [color=#008000]**print**[/color] [color=#BA2121]"Error: Too many operands"[/color]
                [color=#008000]exit[/color]()
            
            operand1 [color=#666666]=[/color] stack[color=#666666].[/color]pop()
            operand2 [color=#666666]=[/color] stack[color=#666666].[/color]pop()
            
            [color=#008000]**if**[/color] token [color=#666666]==[/color] [color=#BA2121]"+"[/color]:
                stack[color=#666666].[/color]append(operand1 [color=#666666]+[/color] operand2)
            [color=#008000]**elif**[/color] token [color=#666666]==[/color] [color=#BA2121]"-"[/color]:
                stack[color=#666666].[/color]append(operand1 [color=#666666]-[/color] operand2)
            [color=#008000]**elif**[/color] token [color=#666666]==[/color] [color=#BA2121]"*"[/color]:
                stack[color=#666666].[/color]append(operand1 [color=#666666]*[/color] operand2)
            [color=#008000]**elif**[/color] token [color=#666666]==[/color] [color=#BA2121]"/"[/color]:
                [color=#008000]**try**[/color]:
                    stack[color=#666666].[/color]append(operand1 [color=#666666]/[/color] operand2)
                [color=#008000]**except**[/color] [color=#D2413A]**ZeroDivisionError**[/color]:
                    [color=#008000]**print**[/color] [color=#BA2121]"Error: Division by zero"[/color]
                    [color=#008000]exit[/color]()
            [color=#008000]**elif**[/color] token [color=#666666]==[/color] [color=#BA2121]"%"[/color]:
                stack[color=#666666].[/color]append(operand1 [color=#666666]%[/color] operand2)
            [color=#008000]**elif**[/color] token [color=#666666]==[/color] [color=#BA2121]"^"[/color]:
                stack[color=#666666].[/color]append([color=#008000]pow[/color](operand1, operand2))
            
    [color=#008000]**return**[/color] stack[[color=#666666]0[/color]]

[color=#008000]**if**[/color] __name__ [color=#666666]==[/color] [color=#BA2121]"__main__"[/color]:
    [color=#008000]**print**[/color] main()

```

---

### Post by lavinog on 2010-03-31
I rewrote mine to use the stack approach...It was much easier this way.
I added unary opererators, and demonstrated how to add new operations.
```
rpn.UNARY_OPERATIONS['!'] = lambda v: math.factorial(v)
```
Side note: lambda is making a lot more sense now...I don't know why I didn't understand it before.

[php]
#! /usr/bin/env python
'''rpn_calc.py - Evaluates expressions in reverse polish notation format.
Created by: Greg Lavino for ubuntuforums beginner programming challenge #11
03.31.2010
'''


import math

# Custom errors for error handling
class TooManyOperandsError(Exception):
    pass

class NotEnoughOperandsError(Exception):
    pass

class UnrecognizedTokenError(Exception):
    pass
#####  End of custom errors ######

class ReversePolishNotation:
    
    BINARY_OPERATIONS={ '+':lambda v1,v2 : v1 + v2,
                        '-':lambda v1,v2 : v1 - v2,
                        '*':lambda v1,v2 : v1 * v2,
                        '/':lambda v1,v2 : v1 / v2,
                        '%':lambda v1,v2 : v1 % v2,
                        '^':lambda v1,v2 : v1 ** v2}

    UNARY_OPERATIONS={  '-':lambda v : -v,
                        'sqrt':lambda v : math.sqrt(v),
                        'sin':lambda v:math.sin(v),
                        'cos':lambda v:math.sin(v)}
                        

    def __init__(self):
        self.finalresult=0
        

    def evaluate(self,inputstr):
        '''evaluates inputstr as RPN'''
        
        # remove whitespace
        self.input = inputstr.strip()
        
        # split up arguments
        arg_list = self.input.split(' ')
        
        # clear stack
        self.stack = []
        
        while arg_list:
            
            # Get next token
            token = arg_list.pop(0)
            
            # Replace ans keyword with last result
            if token == 'ans':
                token = self.finalresult
            
            
            # Test if token is an operator
            if self.isoperator(token):
                self.do_operation(token)
                
            # Test that token is a number
            elif self.isnumeric( token ):
                self.stack.append( float( token ) )
                
            # Token is not valid
            else:
                raise UnrecognizedTokenError
                
        if len(self.stack)>1:
            raise TooManyOperandsError

        
        # convert list item to value
        result = self.stack[0]

        #determine if result is int and return appropriate value
        if result==int(result):
            self.finalresult = int(result)
        else:
            self.finalresult = result
        
        return self.finalresult

        
    def isoperator(self,token):
        return self.isbinary_operator(token) or self.isunary_operator(token)
    
    def isbinary_operator(self,token):
        return token in self.BINARY_OPERATIONS.keys()
            
    def isunary_operator(self,token):
        return token in self.UNARY_OPERATIONS.keys()

    def isnumeric(self,string):
        '''Determine if string is numeric'''
        try:
            float(string)
        except ValueError:
            return False
        return True
            

    def do_operation(self,token):
        '''Uses OPERATIONS dict to evaluate next operation'''
        if self.isunary_operator(token):
            if len(self.stack)<1:
                raise NotEnoughOperandsError
                
            var = self.stack.pop()
            self.stack.append( self.UNARY_OPERATIONS[ token ]( var ) )
            
        else:
            if len(self.stack)<2:
                raise NotEnoughOperandsError
                
            var2 = self.stack.pop()
            var1 = self.stack.pop()
            
            self.stack.append( self.BINARY_OPERATIONS[ token ]( var1 , var2 ) )

####### End of ReversePolishNotation Class ########


def show_help():
    print '''RPN Calculator - By Greg Lavino
    use load [filename] to load a file containing expressions to evaluate
    
    Last answer is stored in 'ans'
    
    For help type 'help'

    To exit type 'quit'
    '''
    

def exit_calc():
    '''Provides a custom exit'''
    
    print 'Have a nice day.'
    exit()


def main():
    rpn=ReversePolishNotation()

    # Adding custom operation:
    rpn.UNARY_OPERATIONS['!'] = lambda v: math.factorial(v)

    show_help()
    
    while True:
    
        inputstr = raw_input('>')
        if not inputstr:
            continue        # Ignore blank lines
        
        # Check for exit
        elif inputstr.lower()=='quit' or inputstr.lower()=='exit' :
            exit_calc()
            
        # Check for help request
        elif inputstr.lower()=='help':
            show_help()
            
        # Load input from file
        elif inputstr.lower().startswith('load'):
            filename = inputstr.split(' ')[1]
            try:
                file = open(filename)
            except IOError:
                print 'File:%s could not be opened'% filename
                continue
            
            for line in file.readlines():
                line = line.strip()
                
                if line:
                    print '\n%s> %s' % ( filename, line )
                    evaluate(rpn,line)
            
        else:
            evaluate(rpn,inputstr)
    

def evaluate(rpn,inputstr):
    '''Evaluates inputstr with rpn object
       while handling errors that may occur.'''
       
    try:
        result = rpn.evaluate(inputstr)
    except ZeroDivisionError:
        print 'Divide by Zero'
        return
        
    except NotEnoughOperandsError:
        print 'Not enough operands'
        return
    
    except TooManyOperandsError:
        print 'Too many operands'
        return
    
    except UnrecognizedTokenError:
        print 'Unrecognized token'
        return
    
    print result

if __name__=='__main__':
    main()

[/php]

Could operator overloading be used for this project?  If so, would there be any benefit?

I might attempt the extra extra credit...It looks like I have to have a way to set operator precedence though...hmmm.

---

### Post by schauerlich on 2010-03-31
> **lavinog said:**
> Could operator overloading be used for this project?  If so, would there be any benefit?You're welcome to try anything you want, as long as beginners will be able to follow. Make sure to comment it well if you try anything fancy. It might be good to demonstrate to beginners how to overload operators in python.

---

### Post by Tony Flury on 2010-04-01
> **Junkieman said:**
> Update: I rewrote my code, it now handles unrecognised tokens. See below for a curious result...


I have a question. Consider this expression breakdown:

```
> 45 6 + /
Input = 45    Stack = [45.0, None, None, None]
Input = 6     Stack = [6.0, 45.0, None, None]
Input = +     Stack = [51.0, None, None, None]
Input = /     Stack = [1.0, [COLOR="Blue"]None[/COLOR], None, None]
1.0

```

Is this correct, according to RPN rules? The divide operator copies X register into Y (if Y is None), then divides. So it divides the last result with itself. 

I would say this is incorrect and that the "/" operator should result in an error as it is a binary operator and should have two operands on the staack for it to work.

> 
This is the same logic that applies to this expression, but the result I get is different than the expected result (Not enough operands):

```
> 10 + 10
Input = 10    Stack = [10.0, None, None, None]
Input = +     Stack = [20.0, None, None, None]
Input = 10    Stack = [10.0, 20.0, None, None]
10.0
```

Again in my view the "+" operand should fail - and not add the top operand to itself
All binary operators should pop two operands off the stack - note i say pop and not inspect - then do the operation and then push the result back, and therefore all binary operators should fail if there is not at least two values on the stack.

---

### Post by Marlonsm on 2010-04-01
I'm working on mine here is a work-in-progress version:
[php]import math
def calculate(operand1, operand2, operator):
	if operator == "+":
		return operand1 + operand2
	elif operator == "-":
		return operand1 - operand2
	elif operator == "*":
		return operand1 * operand2
	elif operator == "/":
		return operand1 / operand2
	elif operator == "%":
		return operand1 % operand2
	elif operator == "^":
		return math.pow(operand1,operand2)
raw_expression = raw_input()
expression = raw_expression.split(None)
operand1 = operand2 = "null"
while len(expression) > 1:
	for n in range (0, len(expression)):
		if not expression[n].isdigit():
			expression[n] = str(calculate(int(expression[n-2]),int(expression[n-1]),expression[n]))
			del expression[int(n-1)]
			del expression[int(n-2)]
			break
print expression[0][/php]
It still doesn't detect error in the input, doesn't divides with decimals and quits after every operation.
It basically imports the expression as a list and scans trough it, when it finds an operator, it calculates and updates the list with the result, looping it until the list has a single element.

---

### Post by Wybiral on 2010-04-01
I felt like playing around with this problem some, I'm not sure that I qualify as a beginner though :)

I'm whiting my code out just in case...

```

[color=#ffffff]
from operator import add, sub, mul, div, mod


class Evaluator:

  def __init__(self):
    self.operators = {'+':add, '-':sub, '*':mul, '/':div, '%':mod, '^':pow}

  def tokenize(self, expr):
    # Split string into tokens
    # otherwise return expr (assuming it's already a token list)
    if isinstance(expr, str):
      return [x.strip() for x in expr.split()]
    return expr

  def evaluate(self, expr, environment={}):
    # Evaluate RPN expression string or token list, return top of stack
    stack = []
    for token in self.tokenize(expr):
      if token in self.operators:
        b = stack.pop()
        a = stack.pop()
        stack.append(self.operators[token](a, b))
      elif token in environment:
        stack.append(environment[token])
      else:
        stack.append(float(token))
    return stack[-1]

  def make_function(self, expr, *arguments):
    # Return callable version of some expression, mapping args to "arguments"
    def callback(*args):
      return self.evaluate(expr, dict(zip(arguments, args)))
    return callback

  def infix_to_rpn(self, expr):
    # Convert infix expression or token list to rpn token list
    tokens = self.tokenize(expr)
    out = []
    stack = []
    prec_list = '^*/+-%('
    prec = prec_list.index
    for token in tokens:
      if token in prec_list:
        while stack and prec(token) > prec(stack[-1]):
          yield stack.pop()
        stack.append(token)
      elif token == '(':
        stack.append(token)
      elif token == ')':
        while stack[-1] != '(':
          yield stack.pop()
        stack.pop()
      else:
        yield token
    while stack:
      yield stack.pop()


ev = Evaluator()
infix_expr = '( x + x ) + y * 2'
rpn_expr = ev.infix_to_rpn(infix_expr)
x2_add_y2 = ev.make_function(rpn_expr, 'x', 'y')
print x2_add_y2(20, 30)
[/color]

```

(it can convert infix to postfix/rpn, also returns callable functions from an rpn expression and an argument list)

---

### Post by Marlonsm on 2010-04-01
Here is mine, now fully working (at least I hope so):
[php]import os
def listfiles():
	files = []
	for item in os.listdir("."):
		files.append(item)
	for item in range(0, len(files)):
		print item, "-", files[item]
	return files
def importfile(files):
	try:
		file = input("Choose a file - ")
		filedata = open(files[file], "r")
		for line in filedata:
			expression = line.strip()
		print "The expression is", expression
		return expression.split(None)
	except:
		print "Not a valid file"
		return []
def isnumber(number):
	try:
		float(number)
		return True
	except:
		return False
def calculate(operand1, operand2, operator):
	try:
		if operator == "+":
			return operand1 + operand2
		elif operator == "-":
			return operand1 - operand2
		elif operator == "*":
			return operand1 * operand2
		elif operator == "/" and operand2 != 0:
			return operand1 / operand2
		elif operator == "%" and operand2 != 0:
			return operand1 % operand2
		elif operator == "^":
			return pow(operand1,operand2)
		else:
			print "Divided by zero"
			expression = []
	except:
		expression = []
def main(expression):
	operators = ["+", "-", "*", "/", "%", "^"]
	while len(expression) > 1:
		for n in range (0, len(expression)):
			if expression[n] in operators:
				if n > 1:
					expression[n] = str(calculate(float(expression[n-2]),float(expression[n-1]),expression[n]))
					del expression[int(n-1)]
					del expression[int(n-2)]
					break
				else:
					print "Too few operands before operator"
					expression = []
					return
			elif not isnumber(expression[n]):
				print "Unrecognized token"
				expression = []
				return
			elif n == len(expression)-1:
				print "Too many operands"
				expression = []
				return
	if len(expression) == 1 and isnumber(expression[0]):
		print expression[0]
	else:
		print "Expression is not valid"
print "Enter your RPN expression, press o to open file or press q to quit"
quit = False
while quit == False:
	raw_expression = raw_input()
	if raw_expression == "q":
		quit = True
	elif raw_expression == "o":
		files = listfiles()
		expression = importfile(files)
		main(expression)
	else:
		expression = raw_expression.split(None)
		main(expression)[/php]
Might add more operations and features later, tho.

EDIT: Added a file importer.

EDIT2: Updated in post #49, now converts to infix.

---

### Post by StephenF on 2010-04-01
Not a beginner. Here is an importable module that makes rather heavy use of exceptions in the token classification process.
```

#! /usr/bin/env python

"""Stack based RPN calculator importable as a module."""


import operator
from collections import deque


__all__ = ["rpncalc", "StackError", "UnrecognizedTokenError"]


class StackError(RuntimeError):
    """Stack was unexpectedly empty or unexpectedly not."""
    pass

    
class UnrecognizedTokenError(RuntimeError):
    """Only numbers and +-*/%^ allowed."""
    pass


# Mapping of RPN symbols to the functions that perform the operation.
oplookup = {
    "+" : operator.add,
    "-" : operator.sub,
    "*" : operator.mul,
    "/" : operator.truediv,
    "%" : operator.mod,
    "^" : operator.pow }


def rpncalc(tokens):
    """Performs reverse polish notation calculations, returning the answer.
    
       tokens: A list or tuple of numbers and operators.

    """
    stack = deque() # Like list but optimized for stack operations.
    
    for token in tokens:
        try:
            # If it can cast to a float, it's a number.
            stack.append(float(token))
        except ValueError:
            try:
                op = oplookup[token]
            except KeyError:
                raise UnrecognizedTokenError("unrecognized token %s" % token)
            try:
                b, a = (stack.pop(), stack.pop())
            except IndexError:
                raise StackError("too few operands")
            # Result of computation is pushed onto the stack.
            stack.append(op(a, b))
            
    try:
        a = stack.pop()
    except IndexError:
        raise StackError("too many operators")
    if stack:
        raise StackError("too many operands")
   
    return a


# This code runs when not importing as a module.  
if __name__ == "__main__":
    print "Reverse polish notation calculator. Type 'exit' to finish."
    while 1:
        line = raw_input("> ").strip()
        if not line:
            continue
        if line.lower() == "exit":
            break
        try:
            result = rpncalc(line.split(" "))
        except (ZeroDivisionError, StackError, UnrecognizedTokenError), msg:
            print msg
        else:
            print result


```

---

### Post by lostinxlation on 2010-04-02
In Perl.

No need to judge mine...

Algorithm..
1. Put the whole input line into a variable, and convert the variable to the array(@x) with space(s) being a delimiter.
2. Shift out the 1st element of @x.
3. If shifted out data in #2 is a number, push it to the last element of another array(@op). If the said data is an operator(+.-,*,/,%,^), pop out the last 2 data from @op and run the specified calculation on them.
4. The result from #3 is pushed into the last element of @op.
5. Go to #2 until the data in @x runs out.


"Static" error check is done by subroutine "err_chk", and "dynamic" error check(divided by 0 and operand/operator sequence problem)  is done in sub "calc" along with the calculation.


```

#!/usr/bin/perl

use warnings;
use strict;

my (@x, $err);

print "> ";
while(<>){
  chomp;
  if($_ eq 'q'){                # Quit if 'q'.
    last;
  }
  s/^\s+//;                     # Removing the leading spaces
  s/\s+$//;                     # Removing the trailing spaces
  @x = split(/\s+/,$_);

  $err = err_chk(@x);        # call sub for error check. 
  
  ($err ne '') ? print "$err\n" : print calc(@x),"\n";  # if there is an error, print it, otherwise call calc sub for calculation. 

  print "> ";
}


sub err_chk {

my ($tmp, $operand, $operator) = ('', -1, 0);           # Legit operation has one more operands than operators.  

  foreach (@_){                                         # Error: Counting the operands and oparators to match each other 
    if(/^[0-9][0-9]*$/){                                #        as well as detecting unrecognized operators/operands.
       $operand++;
    }
    elsif(/^\+$/||/^\-$/||/^\*$/||/^\/$/||/^\%$/||/^\^$/){
       $operator++;
    }
    else{
       $tmp = "ERROR: Unrecognized operators/operands: $_";
    }
  }

  if( ($tmp eq '') && ($operand > $operator) ){
     $tmp = "ERROR: Too many operands";
  }
  elsif( ($tmp eq '') && ($operand < $operator)){
     $tmp = "ERROR: Too many operators";
  }


return $tmp; 
}


sub calc {

  my (@op, $a, $b);
  my $tmp = '';
  
  undef(@op);

  foreach (@_){ 

    if(/\+/||/\-/||/\*/||/\//||/\%/||/\^/ ){
      if(scalar(@op) < 2){
         $tmp = "ERROR: Operands or operators sequence may be wrong"; last;     # Error: Stack must have at least 2 data when the operation is performed.
      }
    }

    if(/\+/){                                           ### Addition
         $b = pop(@op); $a = pop(@op); $tmp=$a+$b;      # Add the last 2 elements in the array.
         push(@op, $tmp);                               # Push the result to the tail of the array. 
    }
    elsif(/\-/){                                        # Subtraction
         $b = pop(@op); $a = pop(@op); $tmp=$a-$b;
         push(@op, $tmp); 
    }
    elsif(/\*/){                                        ### Multiplication
         $b = pop(@op); $a = pop(@op); $tmp=$a*$b;
         push(@op, $tmp);
    }
    elsif(/\//){                                        ### Division
         $b = pop(@op); $a = pop(@op);
         if($b eq '0'){
           $tmp = "ERROR: Divide by 0"; last;           # Error: divide by 0 detected. Exit the loop.
         }
         $tmp=$a/$b;
         push(@op, $tmp);
    }
    elsif(/\%/){                                        ### Remainder
         $b = pop(@op); $a = pop(@op);
         if($b eq '0'){
           $tmp = "ERROR: Divide by 0"; last;           # Error: divide by 0 detected. Exit the loop.
         }
         $tmp=$a%$b;
         push(@op, $tmp); 
    }
    elsif(/\^/){                                        ### Power of ...
         $b = pop(@op); $a = pop(@op); $tmp=$a**$b;
         push(@op, $tmp); 
    }
    elsif(/[0-9][0-9]*/){
         push(@op, $_);                                 ### Pushing into the array if it's a number.
    }
 }

return $tmp;                                            # Return the result
}

``````

TPX30:~/perl> perl rpn
> 3 4 +
7
> 10 3 /
3.33333333333333
> 2 5 ^
32
> 10 2 %
0
> 24 12 3 + 4 % / 6 - 4 * 3 ^
512
>          6          5            4         *        -      2   8      /              +
-13.75
> 10 2 2 %
ERROR: Too many operands
> 10 2 2 % /
ERROR: Divide by 0
> 10 + 10
ERROR: Operands or operators sequence may be wrong
> 10 10 10 +
ERROR: Too many operands
> sdj fh 5 sej 4 5 +
ERROR: Unrecognized operators/operands: sej
> 45 6 + / & 4
ERROR: Unrecognized operators/operands: &
> + 4 1
ERROR: Operands or operators sequence may be wrong
> 4 5a +
ERROR: Unrecognized operators/operands: 5a
> 10 2 + -
ERROR: Too many operators
> 1 2 + hdf + itu -
ERROR: Unrecognized operators/operands: itu
> 2 4 + 1 4
ERROR: Too many operands
> 2 4 + - 4
ERROR: Operands or operators sequence may be wrong
> 3 4 9 * / % 8
ERROR: Operands or operators sequence may be wrong
> q
TPX30:~/perl> 



```

---

### Post by vik_2010 on 2010-04-02
OPEN QUESTION:

I, personally, think it's great that some more experienced coders are posting here. The best way to become a better coder is to look at other people's code, and I would prefer to look at good code than bad code.

Needless to say, I'm not interested in winning, but getting better. I think most people here would agree.

**That aside**, I have a question: Some of the coders are importing the operator module, including functions like pow, add, sub, etc. Why? pow is already in the __builtin__ module, so why import its cousin in operator? And the others? - how do you think they simplify the code?

Thanks :)

---

### Post by Wybiral on 2010-04-02
> **vik_2010 said:**
> **That aside**, I have a question: Some of the coders are importing the operator module, including functions like pow, add, sub, etc. Why? pow is already in the __builtin__ module, so why import its cousin in operator? And the others? - how do you think they simplify the code?

Thanks :)

Probably just for uniformity.

I usually just "from operator import ..." since those functions are so useful and it saves on having to use the '.' operation.

As far as importing the others, in general, because "add" is a lot less to type than "lambda x, y: x + y" and is visually easier to "parse" with your eyes.

---

### Post by StephenF on 2010-04-02
> **vik_2010 said:**
> I have a question: Some of the coders are importing the operator module, including functions like pow, add, sub, etc. Why? pow is already in the __builtin__ module, so why import its cousin in operator?

Consistency, although I don't like the idea of clobbering the version of pow residing in the module namespace. It is a separate entity from the ones in the math and operator modules.
> **vik_2010 said:**
> And the others? - how do you think they simplify the code?
By putting the mathematical operator functions in a lookup table (Python dictionary) they can be defined [once and only once]("http://c2.com/xp/OnceAndOnlyOnce.html"), making the code much easier to maintain.

From:
[INDENT]If the token is x, then you do y multiple times for where x and y have concrete definitions and lines of code have to be repeated with subtle variations (leading to a copy, paste, modify programming style where errors can creep in).[/INDENT]
To:
[INDENT]This token appears in the operator lookup table so look up its corresponding mathematical function and use it to perform a calculation using the numbers we have to hand.[/INDENT]

---

### Post by schauerlich on 2010-04-02
> **vik_2010 said:**
> **That aside**, I have a question: Some of the coders are importing the operator module, including functions like pow, add, sub, etc. Why? pow is already in the __builtin__ module, so why import its cousin in operator? And the others? - how do you think they simplify the code?

Instead of having something like this:

```
if token is "+":
    result = lhs + rhs
elif token is "-":
    result = lhs - rhs
...
else:
    raise BadSyntax("Unrecognized token")
```

You can have something like this:

```

operators = { "+" : operator.add,
              "-" : operator.sub,
              ...
}
...
try:
    result = operators[token](lhs, rhs)
except KeyError:
    raise BadSyntax("Unrecognized token")

```

This makes it a lot easier to add new operators, as well as cut down on the lines of code and therefore opportunities to make mistakes.

---

### Post by Marlonsm on 2010-04-02
Added an infix converter to mine (in Python), the code is kind of big and messy, but I'm very proud of it:

The infix converter will assume any unrecognized token as a variable, for example, "x y +" will return "x+y".
[php]import os
def listfiles():   #List files in directory and gives each one a number
	files = []
	for item in os.listdir("."):
		files.append(item)
	for item in range(0, len(files)):
		print item, "-", files[item]
	return files
def importfile(files):  #Import file based on number chosen
	try:
		file = input("Choose a file - ")
		filedata = open(files[file], "r")
		for line in filedata:
			expression = line.strip()
		print "The expression is", expression
		return expression.split(None)
	except:
		print "Not a valid file"
		return []
def isnumber(number):  #Check if an item is a number
	try:
		float(number)
		return True
	except:
		return False
def islist(list):     #Check if an item in a list
	try:
		list.append("")
		return True
	except:
		return False
def listtostring(list):   #Converts a list into a string
	string = str()
	for item in list:
		if islist(item): #If an item is a list, make it a string
			string += "( " + listtostring(item) + " )"
		else:
			string += item
	return string
def calculate(operand1, operand2, operator): #Calculate
	try:
		if operator == "+":
			return operand1 + operand2
		elif operator == "-":
			return operand1 - operand2
		elif operator == "*":
			return operand1 * operand2
		elif operator == "/" and operand2 != 0:
			return operand1 / operand2
		elif operator == "%" and operand2 != 0:
			return operand1 % operand2
		elif operator == "^":
			return pow(operand1,operand2)
		else:
			print "Divided by zero"
			expression = []
	except:
		expression = []
def solveRPN(expression):
	operators = ["+", "-", "*", "/", "%", "^"]
	m = 0 #This variable will hold the position reached by the program so it won't iterate numbers more than once
	while len(expression) > 1:
		for n in range (m, len(expression)):
			if expression[n] in operators:
				if n > 1: #If there are enough operands before operator, calculate
					expression[n] = str(calculate(float(expression[n-2]),float(expression[n-1]),expression[n]))
					del expression[int(n-1)]
					del expression[int(n-2)]
					m -= 2
					break
				else:
					print "Too few operands before operator"
					expression = []
					return
			elif not isnumber(expression[n]): #If a token is not an operator, neither a number, stop
				print "Unrecognized token"
				expression = []
				return
			elif n == len(expression)-1: #If there are no more operators but there is more then one number, stop
				print "Too many operands"
				expression = []
				return
			else:
				m += 1
	if len(expression) == 1 and isnumber(expression[0]): #When the result is found, print it
		print expression[0]
	else:
		print "Expression is not valid"
def converttoinfix(expression): #Same as "solveRPN()" but instead of calculate, just put in order
	operators = ["+", "-", "*", "/", "%", "^"]
	while len(expression) > 1:
		for n in range (0, len(expression)):
			if expression[n] in operators:
				if n > 1:
					expression[n] = [expression[n-2], " ", expression[n], " ", expression[n-1]]
					del expression[int(n-1)]
					del expression[int(n-2)]
					break
				else:
					print "Too few operands before operator"
					expression = []
					return
			elif n == len(expression)-1:
				print "Too many operands"
				expression = []
				return
	if len(expression) == 1:
		print listtostring(expression[0]) #Covert to string and print result
	else:
		print "Expression is not valid"
if __name__ == "__main__":
	print "Enter your RPN expression, press o to open file, i to convert to infix or q to quit"
	quit = False
	while quit == False:
		raw_expression = raw_input("RPN > ")
		if raw_expression == "q":
			quit = True
		elif raw_expression == "o":
			files = listfiles()
			expression = importfile(files)
			solveRPN(expression)
		elif raw_expression == "i":
			print "Enter an RPN expression or press o to open a file"
			raw_expression = raw_input("RPN to Infix > ")
			if raw_expression == "o":
				files = listfiles()
				expression = importfile(files)
				converttoinfix(expression)
			else:
				expression = raw_expression.split(None)
				converttoinfix(expression)
		else:
			expression = raw_expression.split(None)
			solveRPN(expression)[/php]

Example:
```
marlon@marlon-Ubuntu:~/Desktop$ python rpn.py
Enter your RPN expression, press o to open file, i to convert to infix or q to quit
RPN > 1 2 +
3.0
RPN > 1 2 3 + -
-4.0
RPN > o
0 - expression2.txt
1 - Screenshot.png
2 - rpn.py
3 - expression.txt
4 - Compartilhado.sh
Choose a file - 0
The expression is 24 12 3 + 4 % / 6 - 4 * 3 ^
512.0
RPN > i
Enter an RPN expression or press o to open a file
RPN to Infix > 1 2 +
1 + 2
RPN > i
Enter an RPN expression or press o to open a file
RPN to Infix > o
0 - expression2.txt
1 - Screenshot.png
2 - rpn.py
3 - expression.txt
4 - Compartilhado.sh
Choose a file - 3
The expression is 5 1 2 + 4 * + 3 -
( 5 + ( ( 1 + 2 ) * 4 ) ) - 3
RPN > i
Enter an RPN expression or press o to open a file
RPN to Infix > x y + z /
( x + y ) / z
RPN > 1 2 &
Unrecognized token
RPN > 1 2 3 +
Too many operands
RPN > 1 2 + -
Too few operands before operator
RPN > q
marlon@marlon-Ubuntu:~/Desktop$
```

EDIT: Now it can also be used as a module and I added an optimization that it won't iterate the whole expression again after making an operation.

---

### Post by Canis familiaris on 2010-04-03
[SIZE="7"]C[/SIZE]

[SIZE="5"]OUTPUT[/SIZE]
**Compiled with gcc -Wall -Wextra -pedantic -ansi -lm revpolish.c**
```
amd@amita-pc:~/Programming$ ./a.out 
Welcome to Post Fix Interpreter. Press q to quit

postfix> 3 4 +
7.000000
postfix> 10 3 /
3.333333
postfix> 2 5 ^
32.000000
postfix> 24 12 3 + 4 % / 6 - 4 * 3 ^
512.000000
postfix> 10 + 10
ERROR: Too less operands
postfix> 10 10 10 +
ERROR: Too many operands
postfix> sald;kas;dk;asdk;as
ERROR: Invalid Token
postfix> 45 6 + / & 4 
ERROR: Too less operands
postfix> 2 & 4
ERROR: Invalid Token
postfix> q   

amd@amita-pc:~/Programming$ 
```


[SIZE="5"]SOURCE CODE[/SIZE]
[ [http://pastebin.fosspowered.com/view/35147988](http://pastebin.fosspowered.com/view/35147988) ] (For easier Reading)

[PHP]#include<stdlib.h>
#include<string.h>
#include<stdio.h>
#include<math.h>

#define LEN 100

/* Enumerated Data type to determine whether we are in process of getting a number or decimal or new operand/operator */
enum State	{OUT, IN, DECIMAL}; 
enum Sign	{POSITIVE, NEGATIVE};

/************************************************LIFO Data Structure using Linked Lists********************************/
typedef struct Node {
	double num;
	struct Node *ptr;
} Node;

typedef struct Stack	{
	Node *top;
} Stack;

/* Initialize a stack to NULL */
void Stack_Initialize(Stack *s)	{
	s->top = NULL;
}

/* Push an element on to a stack. No need to check for bounds, as the nodes are dynamically created */
void Stack_Push(Stack *s, double n)	{
	/* Create a new node to store the new value */
	Node *prevtop = s->top; 
	Node *newnode;
	newnode = (Node*)malloc(sizeof(Node));
	newnode->num = n;
	newnode->ptr = prevtop; /* Point the pointer in the node to the current top of the stack */
	
	s->top = newnode;	/* Point the top of the stack to the new node */
}

/* Pop an element from stack and store it in retnum, if successful return 1, if not return 0 */
int Stack_Pop(Stack *s, double *retnum)	{
	Node *p = s->top;
	
	/* If the stack top is NULL, that means no data is there in the stack*/
	if(s->top == NULL)	{
		return 0;	/* Failure to Pop */
	}
	
	*retnum = p->num; /* Store the number on top node of srack in retnum */
	s->top = p->ptr;  /* Now set the new stack top the stack to the node below the top */
	free(p); /* Clean up the top node */
	
	return 1;	/* Successful */
}
/************************************************End of Data Structure********************************/

/* Safely get a string, and put space in the end of the input string as sentinel element */
void get_string(char str[])
{
	char *newline;
	fgets(str, LEN, stdin);
	newline = strchr(str, '\n');
	*newline = ' ';
}

/* Compute the postfix expression string */
void compute(char postinp[])	{
	int i; 
	double num; /* Variable for storing the extracted decimal number */
	char ch; /* Variable to store each character */
	int len; /* Length of the string */
	enum State n = OUT; /* Set initial state of whether reading a decimal or not as OUT */
	enum Sign sign = POSITIVE;
	int count_decplaces = 0; /* Variable to determine number of decimal places, in case of . is detected in string for floating point numbers parsing */
	Stack pfstack; /* Stack to store operands for postfix evaluation */
	double op1, op2, res; /* Variables to hold the operands which are popped out and res is the result stored which is pushed to the stack */
	int count_operands = 0; /* Count number of operands, if zero then output nothing */
	
	Stack_Initialize(&pfstack); 
	
	len = strlen(postinp); 
	
	for(i=0; i<len; ++i)	{
		ch = postinp[i];	
		
		/* Detect use of - as a negative sign */
		if(postinp[i]=='-' && (postinp[i+1] >= '0' && postinp[i+1] <= '9') && sign == POSITIVE && n==OUT)	{
			sign = NEGATIVE;
			continue;			
		}
		
		/* If the character is a numeric type, put it into the current or set as new number */	
		if((ch>='0' && ch<='9'))	{
			/* If it's a new number in case n is OUT, and not IN or DECIMAL; set the number's first digit place */
			if(n==OUT)	{
				num = (int)ch-(int)'0';			
				n=IN;	
			}
			/* If in process of reading a number, multiply the current number by 10 and add the new digit */
			/* eg. if we read 123, and now read 4, then 123*10=1230 then 1230+4=1234 */
			else if(n==IN)	{
				num *= 10;
				num += (int)ch-(int)'0';			
			}
			/* If we are in n = DECIMAL, that is reading a decimal */
			else	{
				count_decplaces++; /* Moving in to next decimal place, increment the number of decimal places */
				
				/* Divide the digit to the 10th power of the number of decimal places eg. 2 in 3rd decimal place then 0.002 would be added */
				num += ((int)ch-(int)'0')/pow(10, count_decplaces); 
			}
		}
		
		/* In case a decimal point is detected and it's not illegaly used period(.), i.e. double(.) or so */
		else if(ch=='.' && n != DECIMAL)	{
			if(n==OUT)	{
				num = 0.0; /* In case if user inputs, .23, then sets num = 0.0 */
			}
			n=DECIMAL; /* Set n as DECIMAL, i.e. it will read as decimal state */
		}
		/* If we detect ch as any other character which is neither numeric nor single period */
		else	{
			/* If we are reading the current number, then we finish reading it here */
			if(n==IN || n==DECIMAL)	{
				if(sign == NEGATIVE)	{
					num *= -1;
				}
				sign = POSITIVE;
				Stack_Push(&pfstack, num);	 
				count_operands++; 
			}
			/* Stop reading the number which was being read */
			n = OUT; 
			count_decplaces=0;
			
			/* If an operator is detected */
			if(ch=='+' || ch=='-' || ch=='*' || ch=='/' || ch=='^')	{
				/*Pop top two elements, from the stack, if successfully popped, then move further */
				if(Stack_Pop(&pfstack, &op1) && Stack_Pop(&pfstack,&op2))	{
					switch(ch)	{
						/* Perform appropraite operation */
						case '+':
							res = op2 + op1;
							break;
						case '-':
							res = op2 - op1;
							break;
						case '*':
							res = op2 * op1;
							break;
						case '/':
							if(op1 == 0)	{
								printf("ERROR: Divide by zero\n");
								return;
							}
							res = op2 / op1;
							break;
						case '^':
							res = pow(op2, op1);
							break;
					}
					Stack_Push(&pfstack, res); /* Push the result onto the stack */
				}
				/* In case there is underflow in the stack, that means there were too many operators for current number of operands */
				else	{
					printf("ERROR: Too less operands\n");
					return;
				}
			}
				
			/* ' ' is the seperator between numbers, it has to be noted operators can acts as separators too */
			else if(ch==' ')
				continue;
			/* Any other character other than numeric, operator, or ' ' is invalid */
			else	{
				printf("ERROR: Invalid Token\n");
				return;
				}
			}
			
		}

		
	Stack_Pop(&pfstack, &res); /* Pop the (hopefully) last element, this is the result */
	
	/* If an element still remains after the previous popping operations it means, there were excess of operands */
	/* In case of failure of popping, which means successful parsing, res does not change its values during this code */
	if(Stack_Pop(&pfstack, &res))	{
		printf("ERROR: Too many operands\n");
		return;
	}
	
	/* Output nothing if the number of operands is zero */
	if(count_operands==0)	{
		return;
	}
	
	/* Show the result */
	printf("%f\n", res);
	
}

int main()
{
	char inp[LEN];
	
	printf("Welcome to Post Fix Interpreter. Press q to quit\n\n");
	
	while(1)	{
		printf("postfix> ");	/* Prompt */
		get_string(inp);
		if(inp[0] == 'q')
			break;
		compute(inp);	/* Evaluate */
	}

	printf("\n");
	return 0;
}
[/PHP]





The only "problem" is that if an invalid token if AFTER say lack of operands I mean like 45 6 + / & 4, this would exit at the point of that '/' with the too less operands error rather than invalid token as shown to be done, but I dont think it's much of a problem; No?

EDIT: ~SNIPPED~

EDIT#2: Added support for Negative numbers, and also works with Decimals. Removed %

EDIT#3: Please separate tokens by space. There seems to be ambiguity if ane expression such as -2-2+ is used, -2 -2 + works though

---

### Post by Marlonsm on 2010-04-03
> **Canis familiaris said:**
> 

The only "problem" is that if an invalid token if AFTER say lack of operands I mean like 45 6 + / & 4, this would exit at the point of that '/' with the too less operands error rather than invalid token as shown to be done, but I dont think it's much of a problem; No?


I don't think it's a problem, it also happens in mine, it prints the first error it finds.

---

### Post by SledgeHammer_999 on 2010-04-03
Hello. 
I am a hobbyist C++ programmer, but I don't consider myself a beginner. Nevertheless I was highly intrigued by this particular exercise. I tried to use as many C++ facilities as I could, but at the end I had to use 2-3 C functions...

I don't know if my code should enter the competition but I want others to comment on my code. Especially for things that I should avoid or for things I should do differently.

Some notes:
1. Doesn't detect trailing whitespace. If I coded this ability I think it would make the code less readable by beginers.
2. I don't have much comments. I think the vars' names describe pretty much everything.
3. It handles everything in "double" type except when you do a modulo operation. It implicity casts the double to an integer in that case.
4. The way it is structured I can easily add more operations.(like square)
5. It stops on the first problem of the entered expression.
6. It doesn't output the same error messages as the OP dispayed in his example.
7. I have already thought of a way to add infix support but I didn't have time. Maybe I'll add it later.

[php]
#include <iostream>
#include <string>
#include <vector>
#include <sstream>
#include <cmath>
#include <cctype>

bool isoperand(std::string &operand)
{
	if (operand == "+" || operand == "-" || operand == "*" ||  operand == "/" || operand == "%" || operand == "^")
	{
		return true;		
	}
	else return false;
	
}

double convert_to_double(std::string &operand) throw(std::string)
{
	std::stringstream ss;
	ss << operand;
	
	double a;
		
	ss >> a;
	if (!ss.good() && !ss.eof())
	{
		std::string ex = "Could not convert \'" + operand + "\' to a number.";
		throw ex;
	}
	
	return a;
}

double addition(std::string &first_operand, std::string &second_operand) throw(std::string)
{	
	double a, b;
	
	try
	{
		a = convert_to_double(first_operand);
		b = convert_to_double(second_operand);
	}
	catch (std::string e)
	{
		throw e;
	}
	
		
	return a+b;
}

double subtraction(std::string &first_operand, std::string &second_operand) throw(std::string)
{
	double a, b;
	
	try
	{
		a = convert_to_double(first_operand);
		b = convert_to_double(second_operand);
	}
	catch (std::string e)
	{
		throw e;
	}
	
		
	return a-b;
}

double multiplication(std::string &first_operand, std::string &second_operand) throw(std::string)
{
	double a, b;
	
	try
	{
		a = convert_to_double(first_operand);
		b = convert_to_double(second_operand);
	}
	catch (std::string e)
	{
		throw e;
	}
	
		
	return a*b;
}

double division(std::string &first_operand, std::string &second_operand) throw(std::string)
{
	double a, b;
	
	try
	{
		a = convert_to_double(first_operand);
		b = convert_to_double(second_operand);
	}
	catch (std::string e)
	{
		throw e;
	}
	
	if (b==0.0)
	{
		std::string ex = "Division by zero in: " + first_operand + " " + second_operand + " /";
		throw ex;
	}
	
		
	return a/b;
}

int modulo(std::string &first_operand, std::string &second_operand) throw(std::string)
{
	int a, b;
	
	try
	{
		a = convert_to_double(first_operand);
		b = convert_to_double(second_operand);
	}
	catch (std::string e)
	{
		throw e;
	}
	
		
	return a%b;
}

int power(std::string &first_operand, std::string &second_operand) throw(std::string)
{
	double a, b;
	
	try
	{
		a = convert_to_double(first_operand);
		b = convert_to_double(second_operand);
	}
	catch (std::string e)
	{
		throw e;
	}
	
		
	return pow(a, b);
}

void parse_expression(std::string &input_rpn, std::vector<std::string> &parsed_list)
{
	int prev_pos = 0;

  while (true)
    {
      unsigned int next_pos = input_rpn.find(" ", prev_pos);
      int size = next_pos - prev_pos;

      parsed_list.resize(parsed_list.size()+1);

      if (next_pos != std::string::npos)
        {
          parsed_list.back() = input_rpn.substr(prev_pos, size);

          prev_pos = next_pos + 1;
        }
      else
        {
          //here we grab the last element and we break the loop
          parsed_list.back() = input_rpn.substr(prev_pos);
          break;
        }
    }	
}

void remove_calculated_elements(std::vector<std::string> &parsed_list, unsigned int &operator_pos)
{
	//start removing the end, so the pos don't change
	parsed_list.erase(parsed_list.begin() + operator_pos); //the operator
	parsed_list.erase(parsed_list.begin() + (operator_pos-1)); //the second operand
	parsed_list.erase(parsed_list.begin() + (operator_pos-2)); //the first operand
}

void insert_result(std::vector<std::string> &parsed_list, double &result, unsigned int &prev_operator_pos)
{
	std::stringstream ss;
	ss << std::fixed << result;
	parsed_list.insert(parsed_list.begin() + (prev_operator_pos-2), ss.str());
}

void calculate_result(std::vector<std::string> &parsed_list) throw(std::string)
{
	while(parsed_list.size() > 1)
	{
		if (!isoperand(parsed_list.back()))
		{
			std::string ex = "There isn't an operator at the end of this expression:";
			for (unsigned int i=0; i<parsed_list.size(); i++)
			{
				ex += " " + parsed_list[i];
			}
			throw ex;
		}
		
		for (unsigned int i=0; i<parsed_list.size(); i++)
		{
			if (isoperand(parsed_list[i]))
			{
				if (i <= 1)
				{
					std::string ex = "Operand missing in:";
					for (unsigned int t=0; t <= i; t++)
					{
						ex += " " + parsed_list[t];
					}
					throw ex;
				}
				
				double result = 0.0;
				try
				{
					if (parsed_list[i] == "+") result = addition(parsed_list[i-2], parsed_list[i-1]);
					else if (parsed_list[i] == "-") result = subtraction(parsed_list[i-2], parsed_list[i-1]);
					else if (parsed_list[i] == "*") result = multiplication(parsed_list[i-2], parsed_list[i-1]);
					else if (parsed_list[i] == "/") result = division(parsed_list[i-2], parsed_list[i-1]);
					else if (parsed_list[i] == "%") result = modulo(parsed_list[i-2], parsed_list[i-1]);
					else if (parsed_list[i] == "^") result = power(parsed_list[i-2], parsed_list[i-1]);
				}
				catch (std::string e)
				{
					throw e;
				}
				
				remove_calculated_elements(parsed_list, i);
				insert_result(parsed_list, result, i);			
				break;
			}
		}
	}
	
	//this detects if you had an extra operand in the expression
	if (isoperand(parsed_list.front()))
	{
		std::string ex = "You had this extra " + parsed_list.front() + " at the end of the expression";
		throw ex;
	} 
	
}

int main(int argc, char *argv[])
{
	while (true)
	{
		std::string input_rpn;
		std::vector<std::string> parsed_list;
		bool print_result = true;

		std::cout << "Please enter your RPN expression or type \'quit\' to quit the program" << std::endl;
		std::getline(std::cin, input_rpn);
		
		for (unsigned int i=0; i<input_rpn.size(); i++)
		{
			input_rpn[i] = tolower(input_rpn[i]);
		}

		parse_expression(input_rpn, parsed_list);
		
		//check if only one element exists and if it is "quit"
		if (parsed_list.size() == 1 && parsed_list.front() == "quit") break;
  
		try
		{
			calculate_result(parsed_list);
		}
		catch (std::string e)
		{
			std::cout << e << std::endl;
			print_result = false;
			//I don't quit here. I let the user enter a new expression			
		}
  
		if (print_result) std::cout << "The result is: " << parsed_list.front() << std::endl;
	}  
  
	return 0;	
}
[/php]

---

### Post by Froodolt on 2010-04-03
Hello,

I want to post a first try in python too.
Its not a perfect piece of code, but its functional (for as far as I tested it).

[PHP]#! /usr/bin/env python

# RPN.py
# Beginner programming challange 11
# Froodolt

import sys

def inp():                          # get userinput
  inp = str(raw_input('Enter : '))
  ilist=inp.split(' ')              # make the string format input a list
  if len(ilist) > 2:                # if list is smaler than 3, the input is wrong
    return ilist
  else:
    print 'input to short'
    sys.exit(0)

def lookup(ilist):
  j=[]
  for element in ilist:             # look at the elements in list from left to right
    try:
      float(element)                # if element can be casted to float than pass
      pass
    except:                         # when it isnt a number:
     i=ilist.index(element)         # look for the place of the element in the list
     j.append(ilist.pop(i))         # put the element in list j
     j.append(float(ilist.pop(i-1)))# take the two numbers in front of it
     j.append(float(ilist.pop(i-2)))
     k=calc(j)                      # calculate the list j 
     ilist.insert(2-i, k)           # insert the answer of list j in the original list
  return ilist
    
def calc(stack1):
  stack=stack1.reverse()            # dont know why I reversed the list here XD
  x=stack1.pop()                    # pop the symbol
  if x=='+':                        
    z=stack1.pop(1)+stack1.pop()
  elif x=='-':
    z=stack1.pop(1)-stack1.pop()
  elif x=='*':
    z=stack1.pop(1)*stack1.pop()
  elif x=='/':
    z=stack1.pop(1)/stack1.pop()
  elif x=='^':
    z=pow(stack1.pop(1), stack1.pop())
  else:
    print 'Error: Unknown opperant.'
    print 'Opperants must be +, -, *, / or ^.'
    sys.exit(0)
  if len(stack1)==0:              # check if the stack is really empty
    return z
  else:
    print 'Error: Stack must be empty at this point, the programmer must have made a big mistake'
    sys.exit(0)

def main():                       # main function
  q=1
  while q!=0:                     # dirty way to keep the program running
    a=inp()
    b=lookup(a) 
    print b                       # spit out the answer

main()
[/PHP]

Please review and comment as much as possible!

By the way, it took me a while to find out that python doesn't come with a switch statement. :lolflag:

---

### Post by HellBoz on 2010-04-04
> **Froodolt said:**
> Hello,

I want to post a first try in python too.
Its not a perfect piece of code, but its functional (for as far as I tested it).

[PHP]#! /usr/bin/env python

# RPN.py
# Beginner programming challange 11
# Froodolt

import sys

def inp():                          # get userinput
  inp = str(raw_input('Enter : '))
  ilist=inp.split(' ')              # make the string format input a list
  if len(ilist) > 2:                # if list is smaler than 3, the input is wrong
    return ilist
  else:
    print 'input to short'
    sys.exit(0)

def lookup(ilist):
  j=[]
  for element in ilist:             # look at the elements in list from left to right
    try:
      float(element)                # if element can be casted to float than pass
      pass
    except:                         # when it isnt a number:
     i=ilist.index(element)         # look for the place of the element in the list
     j.append(ilist.pop(i))         # put the element in list j
     j.append(float(ilist.pop(i-1)))# take the two numbers in front of it
     j.append(float(ilist.pop(i-2)))
     k=calc(j)                      # calculate the list j 
     ilist.insert(2-i, k)           # insert the answer of list j in the original list
  return ilist
    
def calc(stack1):
  stack=stack1.reverse()            # dont know why I reversed the list here XD
  x=stack1.pop()                    # pop the symbol
  if x=='+':                        
    z=stack1.pop(1)+stack1.pop()
  elif x=='-':
    z=stack1.pop(1)-stack1.pop()
  elif x=='*':
    z=stack1.pop(1)*stack1.pop()
  elif x=='/':
    z=stack1.pop(1)/stack1.pop()
  elif x=='^':
    z=pow(stack1.pop(1), stack1.pop())
  else:
    print 'Error: Unknown opperant.'
    print 'Opperants must be +, -, *, / or ^.'
    sys.exit(0)
  if len(stack1)==0:              # check if the stack is really empty
    return z
  else:
    print 'Error: Stack must be empty at this point, the programmer must have made a big mistake'
    sys.exit(0)

def main():                       # main function
  q=1
  while q!=0:                     # dirty way to keep the program running
    a=inp()
    b=lookup(a) 
    print b                       # spit out the answer

main()
[/PHP]Please review and comment as much as possible!

By the way, it took me a while to find out that python doesn't come with a switch statement. :lolflag:
```
[COLOR=Green]Enter : 5 2 +
[7.0][/COLOR]

[COLOR=Red]Enter : 4 + 2
[6.0][/COLOR]

[COLOR=Red]Enter : 2 5 5
['2', '5', '5'][/COLOR]

[B][COLOR=Red]Enter : 9 0 -
[-9.0][/COLOR][/B]
```

You should test it before publishing or at least mention that it does weird things ;)

---

### Post by Canis familiaris on 2010-04-04
[SIZE="7"]Python[/SIZE]
I have made an Infix calculator with Python now. It seems to work. However, I feel I have not done coding enough in Pythonic style :/. Kindly comment, and report bugs if any

[SIZE="5"]Output[/SIZE]
```

Welcome to Infix Evaluator. Separate tokens by space. Press q to quit

infix> ( 3 ) + ( 4 * 5 - ( 6 / 7 ^ 8 ) * 9 ) * 10
   infix = 3 4 5 * 6 7 8 ^ / 9 * - 10 * +
   answer = 202.999906328
infix> 9 + 2
   infix = 9 2 +
   answer = 11.0
infix> 14.0 % 3
   infix = 14.0 3 %
   answer = 2.0
infix> 

```

[SIZE="5"]SOURCE CODE[/SIZE]
[ [http://pastebin.fosspowered.com/view/91970775](http://pastebin.fosspowered.com/view/91970775) ] for better reading
[PHP]
#!/usr/bin/env python

def main():
	print "Welcome to Infix Evaluator. Separate tokens by space. Press q to quit"
	print
	while True:
		inpstr = raw_input('infix> ')		
		if(inpstr in ['q', 'quit', 'exit', 'close']):
			exit()
		try:
			pf_result = infix_to_postfix(inpstr)
			result = evaluate_rpn(pf_result)
			print "   infix = %s" %pf_result
			print "   answer = %s" %result
		except IndexError:
			print "ERROR: Too few operands"
		except ValueError:
			print "ERROR: Invalid Token"
		except ArithmeticError:
			print "ERROR: Too few operators or bad operation"
		except:
			pass

operators = ('+','-','*','/','%', '^')

def perform(v1, v2, oper):
	if oper == '+':
		res = v1 + v2
	elif oper == '-':
		res = v1 - v2
	elif oper == '*':
		res = v1 * v2
	elif oper == '/':
		if v2 == 0:
			raise ArithmeticError("Invalid Operation")
		res = v1 / v2
	elif oper == '%':
		if v2 == 0:
			raise ArithmeticError("Invalid Operation")
		res = v1 % v2
	elif oper == '^':
		res = v1 ** v2
	
	return res

def evaluate_rpn(inpstr):
	stack = []
	tokens = inpstr.split()
	
	if not tokens:
		raise Exception("Too many operands")
	
	for i in range(0, len(tokens)):
		t = tokens[i]
	
		if t in operators:
			try:
				op1 = stack.pop()
				op2 = stack.pop()
			except IndexError:
				raise IndexError("Too few operands")
			r = perform(op2, op1, t)
			stack.append(r)
		else:	
			try:	
				num = float(t)
				stack.append(num)
			except ValueError:
				raise ValueError("Invalid token for evaluation: %s" %t)
		
	if len(stack)>1:
		raise ArithmeticError("Too many operands")
	else:
		return stack.pop()

def infix_to_postfix(pstr):
	stack = []
	expression = []
	
	inpstr = '( ' + pstr + ' )'

	def pop_out_brackets():
		while stack and stack[-1] != '(':
			k = stack.pop()
			expression.append(k)
		
	def pop_out_higher_precedence(current_operator):
		new_operators = ('(',) + operators
		while True:
			k = stack.pop()
			expression.append(k)
			if not stack or new_operators.index(current_operator) > new_operators.index(stack[-1]):
				break

	tokens = inpstr.split()
	
	for i in range(0, len(tokens)):
		t = tokens[i]
		if t in operators:			
			if not stack or stack[-1] == '(':
				stack.append(t)
			elif operators.index(t) > operators.index(stack[-1]):
				stack.append(t)
			else:
				pop_out_higher_precedence(current_operator=t)
				stack.append(t)
		elif t == '(':
			stack.append(t)
		elif t == ')':
			pop_out_brackets()
			stack.pop()
		else:
			if tokens[i-1] not in operators + ('(',) and tokens[i+1] not in operators + (')',):
				raise ArithmeticError("Too many operands")
			expression.append(t)
	else:
		pop_out_brackets()
		
	return ' '.join(expression)

if __name__ == '__main__':
	main()

[/PHP]

EDIT: Error found for second number as zero :/
EDIT: Error fixed

---

### Post by Froodolt on 2010-04-04
> **HellBoz said:**
> ```
[COLOR=Green]Enter : 5 2 +
[7.0][/COLOR]

[COLOR=Red]Enter : 4 + 2
[6.0][/COLOR]

[COLOR=Red]Enter : 2 5 5
['2', '5', '5'][/COLOR]

[B][COLOR=Red]Enter : 9 0 -
[-9.0][/COLOR][/B]
```

You should test it before publishing or at least mention that it does weird things ;)

#-o
Oke...:-s
Good one... ill take a second look at it than:-\"... 
Sorry. :oops:

EDIT:
Sorry, forgot the 'while len(ilist) >1 :' part in above version too.:oops:
It only does the first calculation.

---

### Post by cprofitt on 2010-04-04
Nice code this run through... I have to find some time to work on this... but things are busy right now. Keep up the good work everyone.

---

### Post by Junkieman on 2010-04-05
Thanks for clearing that up Tony!

Okay here is my third try, it handles the sample expressions well. and the code is reusable via Python module imports.

The calculator part is pretty much done, I realized an easier way of handling the stack. 

I added two extra boolean operators for fun, < returns the lower of the two stack values as the answer, and > return the larger.

```
Enter your RPN expression, 'q' to quit
> 3 4 +
7.0
> 10 3 /
3.33333333333
> 2 5 ^
32.0
> 10 2 %
0.0
> 24 12 3 + 4 % / 6 - 4 * 3 ^
512.0
> 10 2 2 % /
Division by zero
> 10 + 10
Not enough operands
> 10 10 10 +
Too many operands
> aw4ojghsiu5esrgs56u7ikdyjdt drthisu 5 hrtgh 5 5 +
Unrecognized token
> 45 6 + / & 4
Not enough operands

> 1 2 + 5 >
5.0
> 1 2 + 5 <
3.0
> q
```

```
# rpnlib.py
# Ubuntuforums Beginner Programming Challenge #11
import math

# define our list of operators
operators = ("+", "-", "*", "/", "%", "^", ">", "<")

def calc(a, b, operator):
    """ Calculates and returns the value of a and b
    """
    if operator == "+": return a + b
    if operator == "-": return a - b
    if operator == "*": return a * b
    if operator == "/": return a / b
    if operator == "%": return a % b
    if operator == "^": return math.pow(a, b)
    if operator == ">":
        if a > b: return a
        else: return b
    if operator == "<":
        if a < b: return a
        else: return b

def evaluate(expression):
    """ Evaluate the expression.
    Returns the answer (float), or an error message (string)
    """
    stack = []
    for token in expression.split():
        if token in operators:
            # need two stack values to operate together
            if len(stack) < 2: return "Not enough operands"
            b = float(stack.pop())
            a = float(stack.pop())
            # test for infinity problems
            if b == 0 and token == '/': return "Division by zero"
            stack.append(calc(a, b, token))
        else:
            try:
                # add the number on to the stack
                stack.append(float(token))
            except:
                return "Unrecognized token"
    
    # the end result should have one stack value
    if len(stack) > 1:
        return "Too many operands"
    else:
        return stack[0]

if __name__ == "__main__":
    print "Enter your RPN expression, or 'q' to quit"
    while True:
        input = raw_input("> ")
        if input == "q" or input == "Q": break
        print evaluate(input)
```

---

### Post by Froodolt on 2010-04-06
Another try, think this is much better.
Sorry for my contribution earlier.

[PHP]#! /usr/bin/env python

# RPN.py
# Beginner programming challange 11
# Froodolt

import sys

def inp():
  print 'type exit to exit'                       
  inp = str(raw_input('Enter : '))
  if inp == 'exit':
    sys.exit(0)
  ilist=inp.split(' ')
  if len(ilist) > 2:
    for element in ilist:
      i=ilist.index(element)
      try:
        ilist[i]=float(element)
      except:
        pass
    return ilist
  else:
    print 'error: input to short, minimal input must be 2 operands and an operator'
    main()

def lookup(ilist):
  j=[]
  while len(ilist) >2 :
    for element in ilist:
      if type(element) is str and ilist.index(element) > 1:
        i=ilist.index(element)
        j.append(ilist.pop(i))
        j.append(ilist.pop(i-1))
        j.append(ilist.pop(i-2))
        k=calc(j)
        ilist.insert(2-i, k)
      elif type(element) is float and ilist.index(element) < len(ilist)-1:
        pass
      else:
        print 'error: first two elements must be operands or to many operands'
        main()
  return ilist

def check(ch):
  if type(ch[0])==float and type(ch[1])==float and type(ch[2])==str:
    pass
  else:
    print 'error: to many operators'
    main()
    
def calc(stack1):
  stack=stack1.reverse()
  check(stack1)
  x=stack1.pop()
  if x=='+':                      
    z=stack1.pop(0)+stack1.pop()
  elif x=='-':
    z=stack1.pop(0)-stack1.pop()
  elif x=='*':
    z=stack1.pop(0)*stack1.pop()
  elif x=='/':
    z=stack1.pop(0)/stack1.pop()
  elif x=='^':
    z=pow(stack1.pop(0), stack1.pop())
  else:
    print 'error: Unknown operator'
    print 'Operator must be +, -, *, / or ^'
    main()
  return z

def main():
  q=1
  while q!=0:
    a=inp()
    b=lookup(a)
    print "the answer is: " 
    print b.pop()
    print ""

main()
[/PHP]

---

### Post by Junkieman on 2010-04-06
> **Froodolt said:**
> Another try, think this is much better.

```
Enter : 24 12 3 + 4 % / 6 - 4 * 3 ^
error: to many operators
```

It seems like you handle the stack, expecting the third token to be an operator, but as I also discovered, this isn't always true.

If we look at the stack as we calc the expression 24 12 3 +

```

[24.0]             # push 24 onto stack
[24.0, 12.0]       # push 12 onto stack
[24.0, 12.0, 3.0]  # push 3 onto stack
op: +              # add operator
[24.0, 15.0]       # pop last two values, add them and push the answer onto stack

```

All throughout the 24 stays in the stack, waiting for some operator to come along and use it. So by the end of your expression, you should only have one value on the stack, the final answer for the expression.

Hope this helps :)

Oh and talking of stacks, a little tip: programs keep an internal stack of which functions are called, so that when a function returns, execution flows back to where the function was called from, with me? 

So your flow from main() calls inp(), and if the user enters invalid text, it calls main() again, you now have made two calls to main(), when the first call hasn't even returned yet. If the user now enters invalid input again, a third call to main() will be put in your program's stack.

Try code so that functions you call unwind naturally. Otherwise your program can cause stack overflows!

In this case it won't matter, but there is a limit of calls you can make. It's just good practice :)

```
>>> print sys.getrecursionlimit()
1000
[COLOR="Gray"]# wow I learned something new![/COLOR]
```

---

### Post by schauerlich on 2010-04-08
Just a bump to see if we have any more entries on the way.

---

### Post by whiteychs on 2010-04-09
I'm submitting for fun. I'm opting-out of the competition.

I used Lua, which doesn't have the core library or features of other more prominent languages like Python. Makes it a little longer usually - that and I just hacked it as I went so I'm sure it's no as condensed as it can be.

Everything should work.  I only left out infix notation converting because it's already 2am.

Let me know of any problems if you would, please. :)

```
#!/usr/bin/lua
--[[ 
whiteychs  4/8/10
Ubuntu forums - Programming Challenge #11
Reverse Polish Notation
http://ubuntuforums.org/showthread.php?t=1441700
--]]

--############# LIST
function list()
-- simply lists contents of 'go' array
-- Lua does not have an array list method builtin
	q = 2
	done = "" .. go[1]
	while q <= (# go) do
		done = "" .. done .. " " .. go[q]
		q = q + 1
	end
	return(done)
end
--############# CALC
function calc(numone,numtwo,opp)
-- crawls through the given 2 numbers and opperation 
-- and, if valid, returns their combination.

	if (string.find(tostring(numtwo), '[^%d]')) ~= nil then
		print("!ERROR! Check input. Equation is not valid.")
		return("exit")
	end
	if (string.find(tostring(numone), '[^%d]')) ~= nil then
		print("!ERROR! Check input. Equation is not valid.")
		return("exit")
	end
	if opp == "+" then
		return(numone + numtwo)
	elseif opp == "-" then
		return(numone - numtwo)
	elseif opp == "*" then
		return(numone * numtwo)
	elseif opp == "/" then
		if (numtwo == '0') then
			print("Divided by 0. Your answer will be infinite.")
			return("exit")
		end
		return(numone / numtwo)
	elseif opp == "^" then
		return(numone ^ numtwo)
	elseif opp == "%" then
		return(numone % numtwo)
	else
		return("invalid")
	end
end

--############# SPLIT
function split(foo) -- splits expression into table 'go'
	count = 1
	for id in foo:gmatch("%S+") do
		go[count] = id
		count = count + 1
	end
end

--############## ERRORCHECK
-- Checks to make sure all input is valid. (number or opperator)
function errorcheck(statement)
	if statement == "" then
		print("No input given. 'q' to quit.")
		exiter = true
	end
	if statement == 'q' then
		print("Goodbye.")
		os.exit()
	end
	if string.find(statement, '[^%d%%%s+*%^/%-]') ~= nil then
		print("!ERROR! Bad input found. A non-valid character.")
		exiter = true
	else
		return("k")
	end
end

--######### MEAT ('n Potatoes)
function meat()
	i = 1
	while((# go) >= 2 and exiter == false) do -- Main loop.
		passme = (calc(go[i],go[i+1],go[i+2]))
		if (passme) == "exit" then
			exiter = true
		elseif (passme) ~= "invalid" then
			go[i+2] = passme -- vvvv
			table.remove(go,i) --   replacing the 2 calced numbers
			table.remove(go,i) --   with their equal
			if (# go) ~= 1 then print(list()) end
			i = 1
		else
			i = i + 1
		end
	end
	
	if exiter == false then
		print("\nANSWER:")
		print(go[1])
	end
end

--#################################
--########### MAIN ################
function main()
	exiter = false
	go = {} -- main array we will work with
	print("\n>> Enter your RPN expression (q to quit):")
	state = io.stdin:read() -- reading equation
	state = state:gsub("^%s*", "") -- remove leading whitespace 
	errorcheck(tostring(state)) -- checks for errors
	split(state) -- parse equation into the 'go' array

	meat()
end

repeat main() until false
```

---

### Post by Junkieman on 2010-04-10
> **whiteychs said:**
> I'm submitting for fun. I'm opting-out of the competition.

I used Lua, which doesn't have the core library or features of other more prominent languages like Python. Makes it a little longer usually - that and I just hacked it as I went so I'm sure it's no as condensed as it can be.

I have no lua experience, I installed lua and gave it a go, nice one!

---

### Post by mo.reina on 2010-04-10
haven't put this through excessive testing but it should work, my python skills are very basic so the code is a little encumbering.

```
#!/usr/bin/python
import sys

data = raw_input("enter notation: ") 
rpn = data.split()     # input split into separate elements, delimited by a space
ln = len(rpn)
li = []         # secondary list, used for computing elements that have the same operator
counter = 0
total = 0

while counter < ln:               # loops through the items found in the list rpn
  try:
    li.append(int(rpn[counter]))   # digits are passed to the secondary list
  except:
    if total == 0 and len(li) < 2:              # error if there are not enough digits
	print "not enough operands"
	sys.exit()
    elif rpn[counter] == "+":   # if the operator is "+"
	ln2 = len(li)        # takes the length of the secondary list 
	counter2 = 0
	while counter2 < ln2:   # loops through the secondary list, adding the items found in the list to the total
	  total += li[counter2]
	  counter2 += 1
	li = []             # clears the secondary list, digits using another operator can then be added to the list
    elif rpn[counter] == "-": 
	ln2 = len(li)
	counter2 = 0
	while counter2 < ln2:
	  if total == 0:       # in case the "-" operator is the first one encountered, computation will be correct
		total = li[counter2]
		counter2 += 1
	  total -= li[counter2]
	  counter2 += 1
  	li = []
    elif rpn[counter] == "*":
	ln2 = len(li)
	counter2 = 0
	while counter2 < ln2:
	  if total == 0:
		total = li[counter2]
		counter2 += 1
	  total *= li[counter2]
	  counter2 += 1
	li = []
    elif rpn[counter] == "/":
	ln2 = len(li)
	counter2 = 0
	while counter2 < ln2:
	  if total == 0:
		total = li[counter2]
		counter2 += 1
	  if li[counter2] == 0:    # prevents interpreter error in the case of division by 0
		print "zero division"
		sys.exit()
	  total /= float(li[counter2])  # true division
	  counter2 += 1
	li = []
    elif rpn[counter] == "%":
	ln2 = len(li)
	counter2 = 0
	while counter2 < ln2:
	  if total == 0:
		total = li[counter2]
		counter2 += 1
	  total %= li[counter2]
	  counter2 += 1
	li = []
    elif rpn[counter] == "^":
	ln2 = len(li)
	counter2 = 0
	while counter2 < ln2:
	  if total == 0:
		total = li[counter2]
		counter2 += 1
	  total = total ** li[counter2]
	  counter2 += 1
	li = []
    else:
	print "unrecognized token"    # in case input contains non mathematical elements
	sys.exit()
  counter += 1
print "the total is %0.2f" % (total)
```

would really appreciate feedback to tighten the code up.  

also if anyone has a good resource for python.  i've started and stopped so many tutorials it's ridiculous, i'm looking for something with good exercises/applications for the code that's being taught.  something like the bash tutorial found in tldp.org, that was an awesome book.

---

### Post by Marlonsm on 2010-04-10
> **mo.reina said:**
> haven't put this through excessive testing but it should work, my python skills are very basic so the code is a little encumbering.

(CODE)

would really appreciate feedback to tighten the code up.  

also if anyone has a good resource for python.  i've started and stopped so many tutorials it's ridiculous, i'm looking for something with good exercises/applications for the code that's being taught.  something like the bash tutorial found in tldp.org, that was an awesome book.

Nice to see more people learning Python.

But instead of using
```
while counter < len(rpn):
    ---code with rpn[counter]---
    counter += 1
```
you could use
```
for item in rpn:
    -code with item instead of rpn[counter]
```
The "for item in list" statement repeats the code for every item in the list.

I'm also new in programming, started in the beginners challenge 9, so there might be other things that could get better.

---

### Post by mo.reina on 2010-04-10
> **Marlonsm said:**
> Nice to see more people learning Python.

But instead of using
```
while counter < len(rpn):
    ---code with rpn[counter]---
    counter += 1
```
you could use
```
for item in rpn:
    -code with item instead of rpn[counter]
```
The "for item in list" statement repeats the code for every item in the list.

I'm also new in programming, started in the beginners challenge 9, so there might be other things that could get better.

hey thanks, same syntax that you use in bash, i'll edit it now

---

### Post by Marlonsm on 2010-04-11
Added a infix-to-RPN converter that solves the infix expression, even if it has parenthesis.
[php]import os
def listfiles():   #List files in directory and gives each one a number
	files = []
	for item in os.listdir("."):
		files.append(item)
	for item in range(0, len(files)):
		print item, "-", files[item]
	return files
def importfile(files):  #Import file based on number chosen
	try:
		file = input("Choose a file - ")
		filedata = open(files[file], "r")
		for line in filedata:
			expression = line.strip()
		print "The expression is", expression
		return expression.split(None)
	except:
		print "Not a valid file"
		return []
def isnumber(number):  #Check if an item is a number
	try:
		float(number)
		return True
	except:
		return False
def islist(list):     #Check if an item is a list
	try:
		list.append("")
		return True
	except:
		return False
def haserror(expression):
	operators = ["+", "-", "*", "/", "%", "^", "(", ")"]
	for item in expression:
		if item not in operators and not isnumber(item):
			return True
	return False
def listtoinfixstring(list):   #Converts a list into a string
	string = str()
	for item in list:
		if islist(item): #If an item is a list, make it a string
			string += "( " + listtoinfixstring(item) + " )"
		else:
			string += item
	return string
def listtoRPNstring(list):   #Converts a list into a string
	string = str()
	for item in list:
		string += item + " "
	return string
def infixlisttoRPN(list):
	operators = ["+", "-", "*", "/", "%", "^"]
	RPN = []
	for item in list:
		if islist(item):
			newlist = infixlisttoRPN(item)
			for item in newlist:
				RPN.append(item)
		else:
			RPN.append(item)
	while haserror(RPN):
		for n in range(0, len(RPN)):
			if RPN[n] not in operators and not isnumber(RPN[n]):
				del RPN[n]
				break
	return RPN
def calculate(operand1, operand2, operator): #Calculate
	try:
		if operator == "+":
			return operand1 + operand2
		elif operator == "-":
			return operand1 - operand2
		elif operator == "*":
			return operand1 * operand2
		elif operator == "/" and operand2 != 0:
			return operand1 / operand2
		elif operator == "%" and operand2 != 0:
			return operand1 % operand2
		elif operator == "^":
			return pow(operand1,operand2)
		else:
			print "Divided by zero"
			expression = []
	except:
		expression = []
def infixtoRPN(expression):
	if haserror(expression):
		return
	def hasoperator(expression):
		operators = ["+", "-", "*", "/", "%", "^"]
		for item in expression:
			if item in operators:
				return True
		return False
	while "(" in expression and ")" in expression: #if there are parenthesis solve them
		for n in range(0, len(expression)):
			if expression[n] == "(":
				count = 0
				for m in range (n, len(expression)):
					if expression[m] == "(":
						count += 1
					elif expression[m] == ")" and count > 1:
						count -= 1
					elif expression[m] == ")" and count == 1:
						newexpression = []
						for k in range (n+1, m): #find what is inside the parenthesis
							newexpression.append(expression[k])
						expression[m] = infixtoRPN(newexpression)
						for k in range (n, m): #get the result and remove everything else
							del expression[n]
						break
					if m == len(expression) - 1: #if the parenthesis do not match, return an error
						return
				break
			if n == len(expression) - 1:
				return
	while hasoperator(expression): #while there are operators
		while "^" in expression: #solve the expression in order
			for m in range(0, len(expression)):
				if expression[m] == "^":
					expression[m] = [expression[m-1],expression[m+1],expression[m]]
					del expression[m+1]
					del expression[m-1]
					break
		while "*" in expression or "/" in expression or "%" in expression:
			for m in range(0, len(expression)):
				if expression[m] in ["*","/","%"]:
					expression[m] = [expression[m-1],expression[m+1],expression[m]]
					del expression[m+1]
					del expression[m-1]
					break
		while "+" in expression or "-" in expression:
			for m in range(0, len(expression)):
				if expression[m] in ["+","-"]:
					expression[m] = [expression[m-1],expression[m+1],expression[m]]
					del expression[m+1]
					del expression[m-1]
					break
	if len(expression) == 1:
		return expression[0]
	else:
		return
def solveRPN(expression):
	operators = ["+", "-", "*", "/", "%", "^"]
	m = 0 #This variable will hold the position reached by the program so it won't iterate numbers more than once
	while len(expression) > 1:
		for n in range (m, len(expression)):
			if expression[n] in operators:
				if n > 1: #If there are enough operands before operator, calculate
					expression[n] = str(calculate(float(expression[n-2]),float(expression[n-1]),expression[n]))
					del expression[int(n-1)]
					del expression[int(n-2)]
					m -= 2
					break
				else:
					print "Too few operands before operator"
					expression = []
					return
			elif not isnumber(expression[n]): #If a token is not an operator, neither a number, stop
				print "Unrecognized token"
				expression = []
				return
			elif n == len(expression)-1: #If there are no more operators but there is more then one number, stop
				print "Too many operands"
				expression = []
				return
			else:
				m += 1
	if len(expression) == 1 and isnumber(expression[0]): #When the result is found, print it
		print expression[0]
	else:
		print "Expression is not valid"
def converttoinfix(expression): #Same as "solveRPN()" but instead of calculate, just put in order
	operators = ["+", "-", "*", "/", "%", "^"]
	while len(expression) > 1:
		for n in range (0, len(expression)):
			if expression[n] in operators:
				if n > 1:
					expression[n] = [expression[n-2], " ", expression[n], " ", expression[n-1]]
					del expression[int(n-1)]
					del expression[int(n-2)]
					break
				else:
					print "Too few operands before operator"
					expression = []
					return
			elif n == len(expression)-1:
				print "Too many operands"
				expression = []
				return
	if len(expression) == 1:
		print listtoinfixstring(expression[0]) #Covert to string and print result
	else:
		print "Expression is not valid"
if __name__ == "__main__":
	print "Enter your RPN expression, press o to open file, c to convert to infix, i to solve infix or q to quit"
	quit = False
	while quit == False:
		raw_expression = raw_input("RPN > ")
		if raw_expression == "q":
			quit = True
		elif raw_expression == "o":
			files = listfiles()
			expression = importfile(files)
			solveRPN(expression)
		elif raw_expression == "c":
			print "Enter an RPN expression or press o to open a file"
			raw_expression = raw_input("RPN to Infix > ")
			if raw_expression == "o":
				files = listfiles()
				expression = importfile(files)
				converttoinfix(expression)
			else:
				expression = raw_expression.split(None)
				converttoinfix(expression)
		elif raw_expression == "i":
			print "Enter an infix expression or press o to open a file"
			raw_expression = raw_input("Infix > ")
			if raw_expression == "o":
				files = listfiles()
				expression = importfile(files)
				try:
					RPN = infixlisttoRPN(infixtoRPN(expression))
					print "RPN >", listtoRPNstring(RPN)
					solveRPN(RPN)
				except:
					print "Expression is not valid"
			else:
				expression = raw_expression.split(None)
				try:
					RPN = infixlisttoRPN(infixtoRPN(expression))
					print "RPN >", listtoRPNstring(RPN)
					solveRPN(RPN)
				except:
					print "Expression is not valid"
		else:
			expression = raw_expression.split(None)
			solveRPN(expression)[/php]

---

### Post by texaswriter on 2010-04-12
Hi, I've been working my way through all the previous Beginner Challenges. If you wait a couple more days, I will have post a C program. 

I'll try to start writing it tonight and post something if I do. 

Thanks,

EDIT: I am writing mine right now. Will have it uploaded sometime tonight.

---

### Post by schauerlich on 2010-04-13
I'm going to judge entries this weekend, hopefully, so this is a last call for any entries.

---

### Post by Junkieman on 2010-04-15
I have updated my Python entry it now includes a Infix to RPN converter, and a test function to automate a whole bunch of expressions.

I'm not sure if I should edit my original post, or repost the code again... So I went for pastebin, the URL is [uf-challenge11.pastebin.com](http://uf-challenge11.pastebin.com) (Ubuntu Forums Challenge #11)

The title of your post is your forum username, the 'subdomain posts' to the top-left on the page is where you want to look.

[Direct link to my post is here]("http://uf-challenge11.pastebin.com/8pNtXJFh") :)

---

### Post by patrickaupperle on 2010-04-15
Here is my C++ entry. I wrote it with the help of google, but without looking at any code related to this challenge. I know it is horribly done, but this is a learning experience. I just started learning c++. 
Please comment on my code (or make fun of it mercilessly).

[PHP]#include <iostream>
#include <vector>
#include <string>
#include <sstream>
#include <cmath>
using namespace std;

int main()
{
    string exp = " ";
    vector<double> evalExp;
    double result;
    double num;
    char c;
    bool print;
    cout << "Enter an equation to be evaluated (q to quit)" << endl;
    while  (true) {
        print = true;
        result = 0;
        num = 0;
        evalExp.clear();
        c = ' ';
        cout << "> ";
        while (c != '\n')
         {
            cin >> exp;
            istringstream myStream(exp);
            if (myStream >> num) //if the string in myStream succesfully becomes a double, true.
                evalExp.push_back(num);
            else if (exp == "+" || exp == "-" || exp == "*" || exp == "/" ||
                    exp == "^" || exp == "%") {
                if (evalExp.size() < 2) { //evalExp has to have at least 2 numbers in it to calculate an answer
                    print = false;
                    break;
                } else {
                    result = evalExp.back();
                    evalExp.pop_back();
                    if (exp == "+")
                        result += evalExp.back();
                    else if (exp == "-")
                        result = evalExp.back() - result;
                    else if (exp == "*")
                        result *= evalExp.back();
                    else if (exp == "/")
                        result = evalExp.back() / result;
                    else if (exp == "^")
                        result = pow(evalExp.back(),result);
                    else if (exp == "%")
                        result = fmod(evalExp.back(),result);
                    evalExp.pop_back();
                    evalExp.push_back(result);
                }
            } else if (exp == "q") {
                return 0;
            } else {
                print = false;
                break;
            }
            cin.get(c); //this should get a \n at the end of the line, ending the loop.
        }
        if (evalExp.size() == 1 && print) { //if there is more than one value left, the input contained too many numbers.
            cout << evalExp[0] << endl;
        } else {
            cout << "Error, Unrecognized Input" << endl;
            cin.ignore(512, '\n');
        }
    }
}
[/PHP]

edit: added %
edit: changed to use double instead of int to allow proper division. Also changed variable "sum" to a name that makes more sense.
edit: condensed the code.
edit: removed unnecessary #include statements
edit: tried to fix bugs below, but it still behaves badly (better, though)
edit: Added some comments and changed to use == instead of .compare == 0.
edit: Though a bit late for the competition, I fixed the bug. Turns out cin.clear() does not do what i thought it did.
edit: made % except doubles

---

### Post by Marlonsm on 2010-04-15
> **patrickaupperle said:**
> Here is my C++ entry. I wrote it with the help of google, but without looking at any code related to this challenge. I know it is horribly done, but this is a learning experience. I just started learning c++. 
Please comment on my code (or make fun of it mercilessly).



I don't understand much about C++, but I think you can use something like functions to replace all those:
[PHP]       else if (exp.compare("+") == 0) {
                sum = evalExp.back();
                evalExp.pop_back();
                sum += evalExp.back();
                evalExp.pop_back();
                evalExp.push_back(sum);
            }[/PHP]

---

### Post by patrickaupperle on 2010-04-15
> **Marlonsm said:**
> I don't understand much about C++, but I think you can use something like functions to replace all those:
[PHP]       else if (exp.compare("+") == 0) {
                sum = evalExp.back();
                evalExp.pop_back();
                sum += evalExp.back();
                evalExp.pop_back();
                evalExp.push_back(sum);
            }[/PHP]

Thanks, I was just thinking about that. I am trying to come up with a way.

Edit: I condensed it, but not through the use of functions. I am sure there is a better way, but that is what I came up with.

---

### Post by falconindy on 2010-04-15
Late entry in C. I didn't do the advertised extra credit, but I added the ability to change the precision of the output by entering :N as a token, where N is the number of decimal places shown. Default is 3 places.

'./posty' to run interactively. use the -v flag to show stack dumps on an error. Sending Ctrl-C, Ctrl-D, or a blank line will exit.

You can also pipe it an expression if you'd like, but the output is a little messy.

```
#include <ctype.h>
#include <math.h>
#include <stdio.h>
#include <string.h>
#include <stdlib.h>

#define CONTINUE 1
#define BREAK 0

/* stack declaration */
typedef struct __stack_t {
  double data;
  struct __stack_t *next;
} stack_t;

stack_t *opstack = NULL;
int stack_size = 0;

/* default runtime options */
int verbose = 0;
int precision = 3;

/* protos */
int parse_expression(char*);
int parse_operand(char*, double*);
int parse_operator(char);
stack_t *push(stack_t*, double);
stack_t *pop(stack_t*);
stack_t *poptop(stack_t*, double*);
double top(stack_t*);

static char *strtrim(char *str) {
  char *pch = str;

  if (str == NULL || *str == '\0')
    return str;

  while (isspace(*pch)) pch++;

  if (pch != str)
    memmove(str, pch, (strlen(pch) + 1));

  if (*str == '\0')
    return str;

  pch = (str + strlen(str) - 1);

  while (isspace(*pch))
    pch--;

  *++pch = '\0';

  return str;
}

/** stack operations */
static void clearstack() {
  if (opstack == NULL)
    return;

  if (verbose)
    printf(":: Stack Dump :: ");
  while (opstack) {
    if (verbose)
      printf("%.*f ", precision, top(opstack));
    opstack = pop(opstack);
  }
  if (verbose)
    putchar('\n');
}

stack_t *push(stack_t *stack, double data) {
  stack_t *newnode = malloc(sizeof(stack_t));
  newnode->data = data;
  stack_size++;

  if (stack == NULL)
    newnode->next = NULL;
  else
    newnode->next = stack;

  return newnode;
}

stack_t *pop(stack_t *stack) {
  stack_t *tmpnode = stack->next;

  free(stack);
  stack_size--;

  return tmpnode;
}

stack_t *poptop(stack_t *stack, double *op) {
  *op = top(stack);
  return pop(stack);
}

double top(stack_t *stack) {
  return stack->data;
}


/** parse operations */
int parse_operand(char *token, double *operand) {
  char *endPtr;

  *operand = strtod(token, &endPtr);
  if (*operand == HUGE_VAL) {
    fprintf(stderr, "!! Input overflow.\n");
    return 1;
  }
  if (token + strlen(token) != endPtr) {
    fprintf(stderr, "!! Bad input: %s\n", token);
    return 1;
  }

  return 0;
}

int parse_operator(char operator) {
  double op1, op2;

  opstack = poptop(opstack, &op2);
  opstack = poptop(opstack, &op1);

  if (verbose)
    printf(":: %.*f ", precision, op1);

  switch (operator) {
    case '+': op1 += op2; break;
    case '-': op1 -= op2; break;
    case '*': op1 *= op2; break;
    case '^': op1 = pow(op1, op2); break;
    case '/': if (! op2) {
                fprintf(stderr, "!! Divide by zero\n");
                return 1;
              }
              op1 /= op2; 
              break;
    case '%': if (! op2) {
                fprintf(stderr, "!! Divide by zero\n");
                return 1;
              }
              op1 = (int)op1 % (int)op2; 
              break;
  }

  if (verbose)
    printf("%c %.*f = %.*f\n", operator, precision, op2, precision, op1);

  if (op1 == HUGE_VAL) {
    fprintf(stderr, "!! Result overflow\n");
    return 1;
  }

  opstack = push(opstack, op1); /* push result back onto stack */

  return 0;
}

int parse_precision(char *p) {
  char *endPtr;
  int pre = (int)strtol(p, &endPtr, 10);
  if (endPtr != p + strlen(p)) {
    fprintf(stderr, "!! Bad precision specified\n");
    return 1;
  } else {
    precision = pre;
    if (precision < 0) /* clamp negative numbers to 0 */
      precision ^= precision;
    printf(":: Precision set to %d decimal places.\n", precision);
  }

  return 0;

}

int parse_expression(char *expr) {

  if (strlen(strtrim(expr)) == 0)
    return BREAK;

  char *token;
  static const char *operators = "+/*-%^";
  double operand;

  while ((token = strsep(&expr, " \n"))) {
    if (strlen(token) == 0) continue;

    if (strchr(operators, *token) && strlen(token) == 1) { /* Caught an operator */
      if (stack_size < 2) {
        fprintf(stderr, "!! Malformed expression -- insufficient operands.\n");
        return CONTINUE;
      }
      if (parse_operator(*token) > 0) {
        return CONTINUE;
      }
    } else if (*token == ':') {
      parse_precision(++token);
    } else { /* Hope this is an operand */
      if (parse_operand(token, &operand) > 0)
        return CONTINUE;

      opstack = push(opstack, operand);
    }
  }

  if (stack_size > 1)
    fprintf(stderr, "!! Malformed expression -- excess operands.\n");
  else if (stack_size == 1) {
    printf(" = %.*f\n", precision, top(opstack));
    opstack = pop(opstack);
  }

  return CONTINUE;
}


int main(int argc, char *argv[]) {
  if (argc > 1 && strcmp(argv[1], "-v") == 0) {
    fprintf(stderr, "::Stack dumps enabled::\n");
    verbose = 1;
  }

  char *buf;
  buf = calloc(sizeof(char), BUFSIZ);

  do {
    clearstack();
    printf("> ");
    *buf = '\0';
    fgets(buf, BUFSIZ, stdin);
  } while (parse_expression(buf));

  free(buf);

  return 0;
}
```

And here's a Makefile:
```
CC=gcc -std=c99 -Wall -pedantic
CFLAGS=-pipe -O2 -D_GNU_SOURCE
LDFLAGS=-lm

all: posty

posty: posty.c $(OBJ)
	$(CC) $(CFLAGS) $(LDFLAGS) $< $(OBJ) -o $@

clean:
	@rm posty

.PHONY: all posty clean
```

edit: throw error on divide by zero rather than answering with infinity.
edit2: separate operand parsing off to its own function.

---

### Post by texaswriter on 2010-04-15
EDIT: I posted new code, please find my post after this. Thanks!!

OK, hope it is not too late. But as promised, it is my version in C. 

Please note, this WILL NOT compile on Windows by all means because you can't plug a constant into an array... It will generate an error [last time I tried in Visual Studio anyways]. This is not a problem in GCC. 

I compiled with the following options ```
gcc -lm -x c texaswriter_challenge11.txt -o texaswriter_challenge11
``` **Please note: you have to link modules manually for the #include <math.h>** *Just copy the above command and you'll be fine unless you rename the file. *

Just some caveats: any negative numbers have to manually made negative. It's not hard at all to program this in, I just didn't want to mess up my code by programming in a bunch of exceptions [like 1E-12 or what have you]... It gives the correct answer for all the RPN that were input.

It is commented as well as I believe is necessary. 

My code is attached as a file.

---

### Post by falconindy on 2010-04-15
> **texaswriter said:**
> OK, hope it is not too late. But as promised, it is my version in C. 

Please note, this WILL NOT compile on Windows by all means because you can't plug a constant into an array... It will generate an error [last time I tried in Visual Studio anyways]. This is not a problem in GCC. 

I compiled with the following options ```
gcc -lm -x c texaswriter_challenge11.txt -o texaswriter_challenge11
``` **Please note: you have to link modules manually for the #include <math.h>** *Just copy the above command and you'll be fine unless you rename the file. *

Just some caveats: any negative numbers have to manually made negative. It's not hard at all to program this in, I just didn't want to mess up my code by programming in a bunch of exceptions [like 1E-12 or what have you]... It gives the correct answer for all the RPN that were input.

It is commented as well as I believe is necessary. 

My code is attached as a file.
Your entry exits as soon as its starts. Changing your while loop in main() to a do/while fixes that.

Two cents: While commenting is valuable, I believe that comments should answer the question 'why', and not 'what'. If the intention of your code isn't obvious from reading it, perhaps there's a simpler way.

---

### Post by texaswriter on 2010-04-15
> **falconindy said:**
> Your entry exits as soon as its starts. Changing your while loop in main() to a do/while fixes that.

Two cents: While commenting is valuable, I believe that comments should answer the question 'why', and not 'what'. If the intention of your code isn't obvious from reading it, perhaps there's a simpler way.

Thanks, I changed it and uploaded a new file containing the changes. Was your reply on commenting related to the comments in the code or just my general statement that I put in my post?

Please let me know if any other problems remain. Should work without further problems, excepting lack of negative numbers [can't input them] and no exponential numbers. There can be negative numbers by arithmetic. 

[php]//texaswriter
//Ubuntu Forums Programming Challenge 11
//Reverse Polish Notation Calculator
//NOTE: compile like gcc -lm -x c challenge11.c -o challenge11 

#include <stdio.h>
#include <stdlib.h>
#include <string.h>
#include <math.h>

const int MAX_BUFFER_LENGTH = 1024; //NOTE: this will change the size if the input buffer AND the max number allowed in input. 
const char OPERATOR_SEARCH_STRING[]="+-*/%^"; //NOTE: this will be searched to determine and could hypothetically used to simplify the case. By subtracting the pointer returned by the strchr [later on] and the pointer of the string, an integer could be returned that would  drastically simplify cases. 
const int MAX_MISDIRECTION = 100; //this sets the maximum number of consecutive stacks [numbers]

void getInput(char *refString); //retreive input

double rpnCalculator(char *rpnExpression); //calculate expression //NOTE: For rpnCalculator, to maximize future expandability will include ALL variables locally so it can be called recursively by itself or anybody else. 

//double fetchNumber(char *relString); //

int main(void)
{
  char inputBuffer[MAX_BUFFER_LENGTH]; //an oversized buffer
  double printAnswer=0; //holds answer
  
  printf("\n\nWelcome to the Reverse Polish Notation Calculator.","\n\nCurrent Buffer size is: %d",MAX_BUFFER_LENGTH);
  
  do     //Will continue inputting until a null, q, Q, or CR is returned. 
  {
    getInput(inputBuffer); //inputs expression
    printAnswer=rpnCalculator(inputBuffer); //IMPORTANT NOTE: probably a structure containing an error int value and the double answer will be required, this way an answer isn't mistaken when in fact an error was returned or thrown somewhere .... 
    printf("\n\nYour answer: %4.10f",printAnswer);
  } while((inputBuffer[0]!='\n')&&(inputBuffer[0]!='q')&&(inputBuffer[0]!='Q')&&(inputBuffer[0]!='\0'));
  return 1;
}

void getInput(char *refString) //Inputs RPN Expression
{
  printf("\n\nPlease enter a valid RPN express ?\t");
  fgets(refString, MAX_BUFFER_LENGTH-1, stdin);
}

double rpnCalculator(char *rpnExpression) //Processes Reverse Polish Notation Expression and returns final value. PLEASE NOTE: This function prints ALL of its own error messages. In reality, I'd rather create a struct that included an int and the double. I would pass back this structure in ALL cases instead of printing error messages here. This way the calling function could deal with input error. 
{
  double rpnStack[MAX_MISDIRECTION]; //~20 levels of indirection provided for //otherwise holds the numbers [aka the stack]
  int rpnSP=0; //is the stack pointer for the numbers
  int rpnStrSP=0; //is the expression "stack" pointer
  int maxStack=0; //holds the number of STACK locations to ensure operator/number balance
  
  //This while loop will proceed through the string and is the "workhorse" loop here
  //Basically, the whole string will be processed to detect numbers and operators. If an operator is detected
  while((rpnExpression[rpnStrSP]!='\0')&&(rpnExpression[rpnStrSP]!='\n')&&(rpnStrSP<strlen(rpnExpression)))
  {
    if(isdigit(rpnExpression[rpnStrSP])!=0) //checks to see if the current expression "stack pointer" is a number.. If so, converts the number to a float and increments stack pointer
    {
      rpnStack[rpnSP]=atof(rpnExpression+rpnStrSP); //fetches a number and puts it on the stack      
      //printf("\n\n***** DEBUG MESSAGE: Your double entered was: %4.2f",rpnStack[rpnSP]);
      rpnSP++;
      maxStack++;
      
      while((isdigit(rpnExpression[rpnStrSP])!=0)||(rpnExpression[rpnStrSP]=='.')) //hard way to advance the String pointer or express SP... 
      {
    rpnStrSP++;
      }
      
    }
    else
    if(rpnExpression[rpnStrSP]==' ') //clear blanks
    {
      rpnStrSP++;
    }
    else //catch all ... mostly for operators
    if((strchr(OPERATOR_SEARCH_STRING, rpnExpression[rpnStrSP])!=NULL)&&(rpnSP>1)) //This strchr might seem weird, but it is to ensure some expandability to special cases. Right now it just does the basic operators. 
    {
      switch(rpnExpression[rpnStrSP]) //decrement rpnSP by 2 and perform arithmetic
      {
    case '+':
    {
      rpnSP=rpnSP-2; 
      rpnStack[rpnSP]=rpnStack[rpnSP]+rpnStack[rpnSP+1];
      rpnStrSP++;
      rpnSP++;
      maxStack--;
    } break;
    case '-':
    {
      rpnSP=rpnSP-2; 
      rpnStack[rpnSP]=rpnStack[rpnSP]-rpnStack[rpnSP+1];
      rpnStrSP++;
      rpnSP++;
      maxStack--;
    } break;
    case '*':
    {
        rpnSP=rpnSP-2; 
      rpnStack[rpnSP]=rpnStack[rpnSP]*rpnStack[rpnSP+1];

      rpnStrSP++;
      rpnSP++;
      maxStack--;
    } break;
    case '/':
    {
      rpnSP=rpnSP-2; 
      if(rpnStack[rpnSP+1]!=0)
      {
        rpnStack[rpnSP]=(double)rpnStack[rpnSP]/(double)rpnStack[rpnSP+1];
      }
      else
      {
        printf("\n\n***** Division by zero: YOU HAVE DOOMED US ALL!! *****\n");
        return -1;
      }
      rpnStrSP++;
      rpnSP++;
      maxStack--;
    } break;
    case '%':
    {
      rpnSP=rpnSP-2; 
      if(rpnStack[rpnSP+1]!=0)
      {
        rpnStack[rpnSP]=fmod((double) rpnStack[rpnSP], (double) rpnStack[rpnSP+1]);
      }
      else
      {
        printf("\n\n***** Division by zero: YOU HAVE DOOMED US ALL!! *****\n");
        return -1;
      }
        
      rpnStrSP++;
      rpnSP++;
      maxStack--;
    } break;
    case '^':
    {
      rpnSP=rpnSP-2; 
      rpnStack[rpnSP]=pow((double)rpnStack[rpnSP], (double)rpnStack[rpnSP+1]);
      rpnStrSP++;
      rpnSP++;
      maxStack--;
    } break;
      }
    }
    else //this is the catch all and also where future expansion will go. 
    {
      printf("\n\n***** Invalid Operator Detected OR Invalid operator/number balance *****\n");
      return -1;
    }
  }
  
  if(maxStack==1) //These two if statements ensure that there were not too many numbers on the stack per the number of operators. 
  {
    return rpnStack[rpnSP-1];
  }
  else
  if(rpnExpression[0]=='\0'||rpnExpression[0]=='\n')
  {
    printf("\n\nExiting...\n\n");
    return -1;
  }
  else
  {
      printf("\n\n***** Invalid Operator Detected OR Invalid operator/number balance *****\n");
      return -1;
  }
}

[/php]

---

### Post by slavik on 2010-04-16
I, of course, have to post some Perl code. :)

This code works, but won't win due to it not satisfying the gracefulness parameters. It does do a quick sanity check though.

Can be exited via ^D instead of ^C :P (if there is no input typed in on current prompt)

[PHP]#!/usr/bin/perl

# rule of three
use strict;
use warnings;
use diagnostics;

# some place to store input
my $input;
my @terms;

# operator mapping from real world to perl world
my %OP_MAP = (
	'+' => '+',
	'-' => '-',
	'*' => '*',
	'/' => '/',
	'^' => '**',
	'%' => '%',
);

# build our "valid" regex
my $regex = " 0-9" . join "", keys %OP_MAP;

while ($input = <>) {
	chomp $input;
	
	# skip line if we don't like it
	if ($input =~ /[^$regex]/) {
		print STDERR "Invalid characters found, good bye!\n";
		next;
	}

	# turn input into an array of terms by splitting on space
	@terms = split /\s+/, $input;

	# now to build the tree, this is what makes RPN easy/awesome
	my %tree;
	parse(\%tree);
	print calc(\%tree) . "\n";
}

# it is 12:53AM ... there is some kind of logic here that works ... I think
# btw, this is almost funcational programming. :)
sub parse {
	my $tree_ref = shift;

	while ($#terms > -1) {
		my $term = pop @terms;
		if (defined $OP_MAP{$term}) {
			if (defined $tree_ref->{'n'}) {
				# read an op for a child, traverse down
				if (defined $tree_ref->{'r'}) {
					$tree_ref->{'l'}->{'n'} = $term;
					parse($tree_ref->{'l'});
				} else {
					$tree_ref->{'r'}->{'n'} = $term;
					parse($tree_ref->{'r'});
				}
			} else {
				$tree_ref->{'n'} = $term;
			}
		} elsif (defined $tree_ref->{'r'}) {
			$tree_ref->{'l'} = $term;
		} else {
			$tree_ref->{'r'} = $term;
		}
		return if (defined $tree_ref->{'r'} and defined $tree_ref->{'l'} and !defined $OP_MAP{$tree_ref->{'r'}} and !defined $OP_MAP{$tree_ref->{'l'}});
	}
}

# eval the tree ...
# btw, this is very funcational programming. :)
sub calc { # because eval is a reserved bareword
	my $tree_ref = shift; # I've seen this somewhere ...

	# figure out what needs to be calced, calc it and eval and return
	if (ref($tree_ref->{'r'}) eq "HASH") {
		if (ref($tree_ref->{'l'}) eq "HASH") {
			# both are ops
			return eval(calc($tree_ref->{'l'}) . $OP_MAP{$tree_ref->{'n'}} . calc($tree_ref->{'r'}));
		} else {
			# only right is op
			return eval($tree_ref->{'l'} . $OP_MAP{$tree_ref->{'n'}} . calc($tree_ref->{'r'}));
		}
	} elsif (ref($tree_ref->{'l'}) eq "HASH") {
		# only left is op
		return eval(calc($tree_ref->{'l'}) . $OP_MAP{$tree_ref->{'n'}} . $tree_ref->{'r'});
	} else {
		# neither is an op, eval and return the value
		return eval($tree_ref->{'l'} . $OP_MAP{$tree_ref->{'n'}} . $tree_ref->{'r'});
	}
}
[/PHP]

---

### Post by SledgeHammer_999 on 2010-04-16
> **patrickaupperle said:**
> Here is my C++ entry. I wrote it with the help of google, but without looking at any code related to this challenge. I know it is horribly done, but this is a learning experience. I just started learning c++. 
Please comment on my code (or make fun of it mercilessly).

Since your entry was much smaller in code size than my own([link](http://ubuntuforums.org/showpost.php?p=9070986&postcount=52)) I gave it a try. It doesn't handle correctly this input:
```
10 + 10
```
And it crashes with these inputs:
```
>aw4ojghsiu5esrgs56u7ikdyjdt drthisu 5 hrtgh 5 5 +
>45 6 + / & 4

```

---

### Post by patrickaupperle on 2010-04-16
> **SledgeHammer_999 said:**
> Since your entry was much smaller in code size than my own([link](http://ubuntuforums.org/showpost.php?p=9070986&postcount=52)) I gave it a try. It doesn't handle correctly this input:
```
10 + 10
```
And it crashes with these inputs:
```
>aw4ojghsiu5esrgs56u7ikdyjdt drthisu 5 hrtgh 5 5 +
>45 6 + / & 4

```

This is odd. It handled 10 + 10 correctly earlier. I'll look into that.

It seems to handle aw4ojghsiu5esrgs56u7ikdyjdt drthisu 5 hrtgh 5 5 + fine (at least it works as I intended it to).

```
[patrick@arch RPN]$ ./a.out  
Enter an equation to be evaluated (q to quit)
> aw4ojghsiu5esrgs56u7ikdyjdt drthisu 5 hrtgh 5 5 +
Error. Unrecognized Input
[patrick@arch RPN]$
```

The last is probably the same problem as the first, I'll look into that too.

Thank you for pointing out these bugs, I really can not believe I did not find them when I was testing.

Edit: modified so that my program does not quit on error. I also fixed (well, sort of) those other bugs. The error message just seems to print multiple time in some cases as well as the last entered number. I can't seem to figure this out, maybe a fresh look later will help.
Edit2: Here is a sample of the new output:
```
[patrick@arch GNU-Linux-x86]$ ./rpn 
Enter an equation to be evaluated (q to quit)
> 10 + 10
Error, Unrecognized Input
> 10
> aw4ojghsiu5esrgs56u7ikdyjdt drthisu 5 hrtgh 5 5 +
Error, Unrecognized Input
> Error, Unrecognized Input
> Error, Unrecognized Input
> 10
> 45 6 + / & 4
Error, Unrecognized Input
> Error, Unrecognized Input
> 4
> q
[patrick@arch GNU-Linux-x86]$ 

```

---

### Post by falconindy on 2010-04-17
Submitting a partial rewrite that uses only stack allocated memory and has some mild improvements/fixes. I don't really consider myself a beginner in programming, but I'm still pretty green when it comes to C. Same Makefile as from my last entry can be used here.

```
#include <ctype.h>
#include <math.h>
#include <stdio.h>
#include <string.h>
#include <stdlib.h>

#define CONTINUE 1
#define BREAK 0

#define STACK_SIZE 64

/* operand stack */
static double opstack[STACK_SIZE];
static double *stackptr;

/* default runtime options */
static int verbose = 0;
static int precision = 3;

/* protos */
static char *strtrim(char*);
static int parse_expression(char*);
static int parse_operand(char*, double*);
static int parse_operator(char);
static void resetstack();

char *strtrim(char *str) {
  char *pch = str;

  if (str == NULL || *str == '\0')
    return str;

  while (isspace(*pch)) pch++;

  if (pch != str)
    memmove(str, pch, (strlen(pch) + 1));

  if (*str == '\0')
    return str;

  pch = (str + strlen(str) - 1);

  while (isspace(*pch))
    pch--;

  *++pch = '\0';

  return str;
}

void resetstack() {
  if (stackptr == &opstack[0])
    return;

  if (verbose) { /* Dump individual items on the stack */
    printf(":: Stack Dump :: ");
    while (stackptr != &opstack[0])
      printf("%.*f ", precision, *--stackptr);
    putchar('\n');
  } else /* Just reset the pointer */
    stackptr = &opstack[0];

}

/** parse operations */
int parse_operand(char *token, double *operand) {
  char *endPtr;

  *operand = strtod(token, &endPtr);
  if (*operand == HUGE_VAL) {
    fprintf(stderr, "!! Input overflow.\n");
    return 1;
  }
  if (token + strlen(token) != endPtr) {
    fprintf(stderr, "!! Bad input: %s\n", token);
    return 1;
  }

  return 0;
}

int parse_operator(char operator) {
  double op1, op2;

  op2 = *--stackptr;
  op1 = *--stackptr;

  if (verbose)
    printf(":: %.*f ", precision, op1);

  switch (operator) {
    case '+': op1 += op2; break;
    case '-': op1 -= op2; break;
    case '*': op1 *= op2; break;
    case '^': op1 = pow(op1, op2); break;
    case '/': if (op2 == 0) {
                fprintf(stderr, "!! Divide by zero\n");
                return 1;
              }
              op1 /= op2; 
              break;
    case '%': if (op2 == 0) {
                fprintf(stderr, "!! Divide by zero\n");
                return 1;
              }
              op1 = (int)op1 % (int)op2;
              break;
  }

  if (verbose)
    printf("%c %.*f = %.*f\n", operator, precision, op2, precision, op1);

  if (op1 == HUGE_VAL) {
    fprintf(stderr, "!! Result overflow\n");
    return 1;
  }

  *stackptr++ = op1;

  return 0;
}

int parse_precision(char *p) {
  char *endPtr;
  int pre;

  pre = (int)strtol(p, &endPtr, 10);
  if (endPtr != p + strlen(p)) {
    fprintf(stderr, "!! Bad precision specified\n");
    return 1;
  } else {
    precision = pre;

    if (precision < 0) /* clamp negative numbers to 0 */
      precision ^= precision;
    printf(":: Precision set to %d decimal places.\n", precision);
  }

  return 0;

}

int parse_expression(char *expr) {
  if (strlen(strtrim(expr)) == 0) /* empty string passed, we're done */
    return BREAK;

  char *token;
  static const char *operators = "+/*-%^";
  double operand;

  while ((token = strsep(&expr, " \n"))) {
    if (strlen(token) == 0) continue;

    if (*token == ':') /* precision specified */
      parse_precision(++token);
    else if (strchr(operators, *token) && strlen(token) == 1) { /* operator */
      if (stackptr - opstack < 2) {
        fprintf(stderr, "!! Malformed expression -- too few operands.\n");
        return CONTINUE;
      }

      if (parse_operator(*token) > 0) {
        return CONTINUE;
      }
    } else { /* it's an operand, or it's bad input */
      if (parse_operand(token, &operand) > 0) /* parsing failed on bad input */
        return CONTINUE;

      if (stackptr == &opstack[STACK_SIZE]) { /* stack overflow */
        fprintf(stderr, "!! Stack overflow. Expression too large.\n");
        return CONTINUE;
      }

      *stackptr++ = operand;
    }
  }

  if (stackptr - opstack > 1)
    fprintf(stderr, "!! Malformed expression -- too many operands.\n");
  else if (stackptr - opstack == 1) {
    printf(" = %.*f\n", precision, *--stackptr);
  }

  return CONTINUE;
}

int main(int argc, char *argv[]) {
  char buf[BUFSIZ + 1];

  if (argc > 1 && strcmp(argv[1], "-v") == 0) {
    fprintf(stderr, "::Stack dumps enabled::\n");
    verbose = 1;
  }

  stackptr = &opstack[0]; /* initialize stack */

  do {
    resetstack();
    printf("> ");
    buf[0] = '\0';
    fgets(buf, BUFSIZ, stdin);
  } while (parse_expression(buf));

  return 0;
}
```

---

### Post by schauerlich on 2010-04-18
Alright, the time has come to announce the winner. Drum roll please...

Our winner is...
[size=5]falconindy![/size]

[His entry](http://ubuntuforums.org/showpost.php?p=9135518&postcount=81) may have come in late, but it's a well-done, functional entry, written in C to boot! A refreshing change from what seems to be a python-dominated challenge. Not that that's a bad thing, per se, but variety is the spice of life. :) 

Congratulations! It's your turn to host the challenge. Once you've got an idea, make a thread and let the fun begin all over again!

---

### Post by patrickaupperle on 2010-04-18
Congratulations falconindy! When can we expect the next challenge?

---

### Post by texaswriter on 2010-04-18
Congratulations FalconIndy. I did like how concise and short yours was. :popcorn::KS:):P

---

### Post by falconindy on 2010-04-18
Fun fun. I'll poke around and see if I can't find something fitting by the end of the day.

edit: it's up! [Enjoy!](http://ubuntuforums.org/showthread.php?t=1457404)

---

### Post by Junkieman on 2010-04-18
Well done falconindy! :guitar:

---

### Post by thepopasmurf on 2010-08-05
Here's a late entry. I am not a beginner programmer in general but I am only just learning Ocaml (and functional languages in general).

```

(* Reverse Polish Notation *)
exception Stack_error of string;;

(* Required for % operation because built in % works for ints *)
let floatMod a b =
	let ai = int_of_float a in
	let bi = int_of_float b in
	float_of_int (ai mod bi);;

let rec execute commList stack =
	match commList with
	| [] -> (
		match stack with
		| x::[] -> x
		| _ -> raise (Stack_error "Invalid answer" );
			)
	| "+"::rest -> begin
		match stack with
	    | x::y::xys -> execute rest ((x+.y)::xys);
		| _ -> raise (Stack_error "Not enough arguments");
			end
	| "-"::rest -> begin
		match stack with
		|x::y::xys -> execute rest ((y-.x)::xys);
		| _ -> raise (Stack_error "Not enough arguments");
			end
	| "*"::rest -> begin
		match stack with 
		|x::y::xys ->	execute rest ((x*.y)::xys);
		| _ -> raise (Stack_error "Not enough arguments");
			end
	| "/"::rest -> begin
		match stack with
		|x::y::xys -> execute rest ((y/.x)::xys);
		|_ -> raise (Stack_error "Not enough arguments");
			end
	| "%"::rest -> begin
		match stack with
		|x::y::xys -> execute rest ((floatMod y x)::xys);
		|_ -> raise (Stack_error "Not enough arguments");
		end
	| "^"::rest -> begin
		match stack with
		|x::y::xys -> execute rest ((y**x)::xys);
		|_ -> raise (Stack_error "Not enough arguments");
		end
		
	| str::rest -> let re = Str.regexp "[0-9]+\\.?[0-9]*$" in
		if Str.string_match re str 0 then 
			execute rest ((float_of_string str)::stack)
	        else (raise (Stack_error "Invalid input"));;
		
(* Runs the program in the terminal *)
let rec go value = 
	if value then begin
	try
		print_string " -> ";
		let input = read_line() in
		if input="q" then go false else
		let commandList = Str.split (Str.regexp " ") input in
		print_float (execute commandList []);
		print_string "\n";
		go true;
	with Stack_error s -> print_endline s; go true;
	end
	else ();;
		
print_endline "Type 'q' (lowercase) to quit the program";
go true;;

```

This program uses regular expressions. If anyone wants compile this program they need to include the str.cma / str.cmxa modules.

```
ocamlc -o output str.cma file.ml
```
```
ocamlopt -o output str.cmxa file.ml
```

---

### Post by schauerlich on 2010-09-21
Well, when I made this challenge, I did it in python... but as I'm learning ruby I decided to reimplement it in that. Enjoy.

```
[color=#008000]**class**[/color] [color=#0000FF]**Calculator**[/color]
    [color=#008000]**def**[/color] [color=#0000FF]eval[/color](exp)
        tokens [color=#666666]=[/color] exp[color=#666666].[/color]gsub([color=#BA2121]'^'[/color], [color=#BA2121]'**'[/color])[color=#666666].[/color]split[color=#666666].[/color]map [color=#008000]**do**[/color] [color=#666666]|[/color]token[color=#666666]|[/color]
            [color=#008000]**begin**[/color]
                [color=#008000]Float[/color](token)
            [color=#008000]**rescue**[/color] [color=#880000]ArgumentError[/color]
                [color=#008000]**if**[/color] [color=#008000]%w{+ - / * % **}[/color][color=#666666].[/color]include? token
                    token
                [color=#008000]**else**[/color]
                    [color=#008000]**raise**[/color] [color=#880000]ArgumentError[/color][color=#666666].[/color]new [color=#BA2121]"Unrecognized token"[/color]
                [color=#008000]**end**[/color]
            [color=#008000]**end**[/color]
        [color=#008000]**end**[/color]
        
        stack [color=#666666]=[/color] [color=#666666][][/color]

        tokens[color=#666666].[/color]each [color=#008000]**do**[/color] [color=#666666]|[/color]token[color=#666666]|[/color]
            [color=#008000]**if**[/color] token[color=#666666].[/color]class [color=#666666]==[/color] [color=#008000]Float[/color]
                stack[color=#666666].[/color]push( token )
            [color=#008000]**else**[/color]
                right, left [color=#666666]=[/color] stack[color=#666666].[/color]pop, stack[color=#666666].[/color]pop

                [color=#008000]**if**[/color] right [color=#666666]==[/color] [color=#008000]nil[/color] [color=#AA22FF]**or**[/color] left [color=#666666]==[/color] [color=#008000]nil[/color]
                    [color=#008000]**raise**[/color] [color=#880000]ArgumentError[/color][color=#666666].[/color]new [color=#BA2121]"Not enough operands"[/color]
                [color=#008000]**end**[/color]

                [color=#008000]**begin**[/color]
                    stack[color=#666666].[/color]push( left[color=#666666].[/color]send(token, right) )
                [color=#008000]**rescue**[/color] [color=#880000]ZeroDivisionError[/color]
                    [color=#008000]**raise**[/color] [color=#880000]ArgumentError[/color][color=#666666].[/color]new [color=#BA2121]"Division by zero"[/color]
                [color=#008000]**end**[/color]
            [color=#008000]**end**[/color]
        [color=#008000]**end**[/color]
        [color=#008000]**if**[/color] stack[color=#666666].[/color]length [color=#666666]==[/color] [color=#666666]1[/color]
            stack[color=#666666].[/color]pop
        [color=#008000]**else**[/color]
            [color=#008000]**raise**[/color] [color=#880000]ArgumentError[/color][color=#666666].[/color]new [color=#BA2121]"Too many operands"[/color]
        [color=#008000]**end**[/color]
    [color=#008000]**end**[/color]
[color=#008000]**end**[/color]


[color=#008000]**if**[/color] [color=#008000]__FILE__[/color] [color=#666666]==[/color] [color=#19177C]$0[/color]
    calc [color=#666666]=[/color] [color=#880000]Calculator[/color][color=#666666].[/color]new

    [color=#008000]**while**[/color] [color=#008000]true[/color]
        [color=#008000]print[/color] [color=#BA2121]"> "[/color] 
        input [color=#666666]=[/color] [color=#008000]gets[/color][color=#666666].[/color]strip[color=#666666].[/color]downcase

        [color=#880000]Process[/color][color=#666666].[/color]exit! [color=#008000]**if**[/color] input [color=#666666]==[/color] [color=#BA2121]'q'[/color]
        [color=#008000]**next**[/color] [color=#008000]**if**[/color] input[color=#666666].[/color]empty?

        [color=#008000]**begin**[/color]
            [color=#008000]puts[/color] calc[color=#666666].[/color]eval( input )
        [color=#008000]**rescue**[/color] [color=#880000]ArgumentError[/color] [color=#666666]=>[/color] err
            [color=#008000]puts[/color] err
        [color=#008000]**end**[/color]
    [color=#008000]**end**[/color]
[color=#008000]**end**[/color]
```

---

### Post by Coalwater on 2011-06-26
> **schauerlich said:**
> 
```

> 45 6 + / & 4
Unrecognized token

```
In my code this case generated not enough operands, because it tries to do the division before noticing the "&" , is this considered correct ? or do i need to scan the whole string first?

---

### Post by schauerlich on 2011-06-26
> **Coalwater said:**
> In my code this case generated not enough operands, because it tries to do the division before noticing the "&" , is this considered correct ? or do i need to scan the whole string first?

As long as it doesn't segfault or have an uncaught exception, it's fine. What happens on the input "5 10 &" ?

---

### Post by Coalwater on 2011-06-27
> **schauerlich said:**
> As long as it doesn't segfault or have an uncaught exception, it's fine. What happens on the input "5 10 &" ?
It generates the 'Unrecognized token', i could post the code but i need to modify it to make it work in a loop untill it reads the 'q' input

---

