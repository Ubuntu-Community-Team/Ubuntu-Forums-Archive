---
title: "Weekly Programming Challenge: Friday, Jan 19, 2007"
date: 2007-01-18
forum: Programming Talk
---

### Post by Wybiral on 2007-01-18
Hello everyone, I've been given the task of assigning the challenge this week...

This weeks challenge will be regressing a bit in skill level for any newbies looking for something to work on, but should still be interesting/flexible enough for all of you seasoned programmers too. The goal is to parse a mathematical expression that contains a mix of addition and subtraction. It must be able to handle varying lengths and a mixed order of operations.

Examples:

1+2+1-5+7
Should return: 6

1-10+14
Should return: 5

Rules:
1. You cannot use an existing expression parsing library (otherwise it would be boring)
2. It should be able to detect errors such that equations like "1+4++3" and "1+2-" will not be evaluated but will return an error.
3. It should handle more than single digit values.

Taking it further (bonus):
Try to make it handle multiplication and division, along with the
addition and subtraction, and remember that precedence matters!

Notes:
It does NOT have to handle floating point values, however that would be completely acceptable too.

Good luck, and have fun!

---

### Post by slash2314 on 2007-01-19
```

expression_string = str(raw_input("Enter your expression: "))
total = 0
number_list = []
curr_num_str = ""
operator_list = []
count=0
for character in expression_string:
    operand = False
    if character in ('+','-'):
        operand = True
        operator_list.append(character)
    else:
        curr_num_str+=character
    if operand == True or count==len(expression_string)-1 :
        number_list.append(curr_num_str)
        curr_num_str=""
    count+=1
if len(operator_list) == len(number_list)-1 and all(number_list):
    count = 0
    total= float(number_list[count])
    for operator in operator_list:
        second_number = float(number_list[count+1])
        if operator == "+":
            total= total +  second_number
        else:
            total = total - second_number
        count+=1
    print 'Answer: '+str(total)
else:
    print "expression error"

```

---

### Post by phossal on 2007-01-19
Removed. 56phil's python version is much better. :) Mine hangs on certain negative exponents, etc. After a lot of wasted time, I have to delete all the source so I don't piss away the rest of my life reinventing the wheel.

---

### Post by amo-ej1 on 2007-01-19
Supports + and -, doesn't use anything except a scanf() to read it char by char

```

#include <stdio.h>

typedef enum t_op operator;

enum t_op{
    PLUS,
    MINUS,
};

int main(int argc, char **argv)
{
    int res=0;        //!< Store the end result
    char curChar;     //!< Current char buffer
    int curVal=0;     //!< Buffer to construct the operand
    operator op=PLUS; //!< The current operator
    int gotOp=1;      //!< Flag to indicate and operator has already passed
    while(1)
    {
        scanf("%c",&curChar);
        if(curChar == '+')
        {
            if(gotOp==1)
            {
                printf("Unexpected operator found\n");
                return -1;
            }
            if(op==PLUS)
            {
                res+=curVal;
            }
            else
            {
                res-=curVal;
            }
            curVal=0;
            op=PLUS;
            gotOp=1;
        } 
        else if(curChar == '-')
        {
            if(gotOp==1)
            {
                printf("Unexpected operator found\n");
                return -1;
            }
            if(op==PLUS)
            {
                res+=curVal;
            }
            else
            {
                res-=curVal;
            }
            curVal=0;
            op=MINUS;
            gotOp=1;
        }
        else if(curChar >= '0' && curChar <= '9')
        {
            gotOp=0;
            curVal*=10;
            curVal+=curChar-'0';
        }
        else if(curChar == '\n' && gotOp==0)
        {
            if(op==PLUS)
            {
                res+=curVal;
            }
            else
            {
                res-=curVal;
            }
            printf("%d\n",res);
            return 0;
        }
        else
        {
            printf("Unexpected character: %c\n", curChar);
            return 1;
        }
    }
}

```

---

### Post by ghostdog74 on 2007-01-19
Is eval considered a parsing library? lol..
```

a = "1-10+14"
print eval(a)

```

---

### Post by jblebrun on 2007-01-19
Here's my playful python solution. It only implements adding and subtracting, with floating point numbers.

```

import sys
try:
    print reduce(float.__add__, [float(n) for n in [reduce(float.__sub__, [float(n) for n in x.split('-')]) for x in ("0"+sys.argv[1]).split('+')]])
except Exception:
    print "Error in expression!"

```

Here's the same thing, but using lambdas:
```

import sys
try:
    print reduce(lambda x,y: float(x)+float(y), [reduce(lambda x,y: float(x)-float(y), x.split('-')) for x in ("0"+sys.argv[1]).split('+')])
except Exception:
    print "Error in expression!"

```

---

### Post by jblebrun on 2007-01-19
> **ghostdog74 said:**
> Is eval considered a parsing library? lol..
```

a = "1-10+14"
print eval(a)

```

eval is a parser that is implemented for you in python, so it's basically a parsing library, yes :-P

---

### Post by jblebrun on 2007-01-19
I decided to do a C implementation, too.

Notable features: 
*Minimized the need for multiplies.
*Main parsing function uses only C keywords (no standard library functions)

```

//Challenge: use no libraries!

int parse(const char* input, long int* result) {

    char* p=(char*)input;
    int i=0,maxplace=0,place=0;
    unsigned char mode='+';
    long int places[64]={},temp[64]={0};

    //Move to end of string
    while(*(++p) != '\0');

    //Parse string backwards
    while(p-- >= input)
    {
	//When you hit an operator, add or subtract 
	if (*p=='+' || *p=='-' || p-input==-1) {
	    maxplace=(place>maxplace)?place:maxplace;
	    for(place; place >= 0; place--)
	    {
		places[place] += (p-input==-1 || *p=='+')?temp[place]:-temp[place];
		temp[place]=0;
	    }
	    place++; 
	    p--;
	    if(p<input)
		break;
	}
	
	//Put numbers in temporary placeholders
	if (*p < '0'  || *p > '9')
	    return -(p-input)+1;
	temp[place++] += *p-'0';
    }	    
    place = 1;

    //Compile number
    while(i <= maxplace) {
	*result += place*places[i++];  
	place *= 10;
    }

    return 0;
}

```

And code to test:
```



void helper(const char* s) {
    long int r=0;
    int b=0;
    printf("%s = ",s);
    b=parse(s, &r);
    if(b)
	printf("Error at position %d\n",-b);
    else
	printf("%d\n",r);
}

int main(int argc, char** argv) {
    int r;
    int b;
    helper("1+2+3");
    helper("+1+2+3");
    helper("-1+2+3");
    helper("-1+2-3");
    helper("10+20+30");
    helper("100+200+300");
    helper("1000+2000+3000");
    helper("-10+20+30");
    helper("-10+2+30");
    helper("-10+200+3000");
}

```

---

### Post by phossal on 2007-01-19
[Removed]

---

### Post by jblebrun on 2007-01-19
> **phossal said:**
> See my original post below. Supports all ops/floating point (in perl) :D

Your original post is above, for me ;-)

---

### Post by ghostdog74 on 2007-01-19
> **jblebrun said:**
> eval is a parser that is implemented for you in python, so it's basically a parsing library, yes :-P
oh ok.well here's a simple one (+ and -), no error checking
```

#!/usr/bin/python
import re,operator
input = "100+43+52213-442"
allnum = re.findall('[+-]\d+|\d+',input)
print "result : ", sum(map(float,allnum))

```

or if sum() is not allowed:
```

#!/usr/bin/python
import re,operator
input = "100+43+52213-442"
accumulate = 0
for item in re.findall('[+-]\d+|\d+',input):
  accumulate = operator.add(float(item), accumulate)
print "result : ", accumulate

```

---

### Post by phossal on 2007-01-19
Oh yeah! I went for a run early this morning. It was cold and dark still. The temp was hanging around 10, and it was snowing. I'm going to try to run a my third marathon this year. Anyway, while I was running, it occurred to me that with just a little effort, I could hack in the rest of the details. Yeah, I know, it's *very* ugly, should be totally rewritten (probably in another language :) ), and then refactored to look *nothing* like the mess I've created. But! It does do *everything*. Add subtract, multiply, divide, floating point, negatives, exponents. You just can't use parentheses. :(

Time to go to work. Looking forward to seeing the rest of the candidates.

---

### Post by duff on 2007-01-19
Ah!  I actually like these simpler ones better.  The solutions are always more fun to read and vastly different than the others.  Here's mine, using Python iterators.

```
#!/usr/bin/env python
import sys

class Expr:
   def __init__(self, expr):
      self.expr = list('+' + expr)
   def __iter__(self):
      while self.expr:
         v = 0
         sign = {'+':1,'-':-1}[self.expr.pop(0)]
         assert self.expr[0].isdigit()
         while self.expr and self.expr[0].isdigit():
            v = v*10 + int(self.expr.pop(0))
         yield sign*v

print sum(Expr(sys.argv[1])) 
```

basic error checking  and no multiplication

quickd demo:```
# ./expr.py 2+26-31
-3

```

---

### Post by 56phil on 2007-01-19
superseded by entry posted 24Jan.

---

### Post by Wybiral on 2007-01-19
So many good ones, and it's only the first day... Whew! I'm going to have a lot source to try out! :lolflag: 

I'm also going to mention that I've also got a soft spot in my heart for compilers, so a stack based solution would be really cool... But, it mostly depends on how close it is to meeting the rules and how fast it is.

Once again, good luck everyone!

---

### Post by jblebrun on 2007-01-19
> **duff said:**
> Ah!  I actually like these simpler ones better.  The solutions are always more fun to read and vastly different than the others.  Here's mine, using Python iterators.

```
#!/usr/bin/env python
import sys

class Expr:
   def __init__(self, expr):
      self.expr = list('+' + expr)
   def __iter__(self):
      while self.expr:
         v = 0
         sign = {'+':1,'-':-1}[self.expr.pop(0)]
         assert self.expr[0].isdigit()
         while self.expr and self.expr[0].isdigit():
            v = v*10 + int(self.expr.pop(0))
         yield sign*v

print sum(Expr(sys.argv[1])) 
```

basic error checking  and no multiplication

quickd demo:```
# ./expr.py 2+26-31
-3

```

This breaks for a string starting with a negative number, like
-3+2+5

---

### Post by phossal on 2007-01-19
> **56phil said:**
> Multiplication, division, **exponentiation**, abutted multiplication supported. 


lol Sweet.

---

### Post by phossal on 2007-01-19
lol Wybiral, check out the updated perl version. *Negative exponents?* It does everything but parenthesis. Where is pmasair's 3-line Python version?

---

### Post by phossal on 2007-01-19
> **56phil said:**
> Multiplication, division, exponentiation, abutted multiplication supported. 


Failed with: -5^6-2*3   How do I do it?

[Edit] I remember reading a story about how, when the United States Gvt was considering a war with a country to the south, one of the weaknesses they noticed about their enemy after much observation was that they (the enemy) left all of their fighter jets packed on a single runway ready for immediate use. The US realized that a surprise attack on the runway would essentially eliminate their air power. Then some genius thought to check how the US avoided such a disaster. Of course, they found the US was doing *exactly the same thing*. lol So they immediately figured out a way to divide their planes so that a single attack wouldn't render them all useless. 

Anyway, -5^6-2*3 fails in 56phil's python program. But I noticed how well it handles almost everything else. It was just chance that I found the error. So, after checking mine...  lol In short, I fixed mine.

---

### Post by 56phil on 2007-01-20
Fixed mine, too. Thanks Phossal, that sequence never occured to me. -5^6-2*3 now yields -15631.

---

### Post by phossal on 2007-01-20
> **56phil said:**
> Fixed mine, too. Thanks Phossal, that sequence never occured to me. -5^6-2*3 now yields -15631.

Nice. Your version is obviously much better than mine. Nice job, really. It'll be interesting to see if Wybiral posts a version using a stack directly.

---

### Post by 56phil on 2007-01-20
:frown: Yes, but now 6^-5 fails! Such is life.](*,)

---

### Post by 56phil on 2007-01-20
Cleaned that little mess up. -2^2 yields -4 and -2^-2 yields -0.25. :biggrin:

---

### Post by phossal on 2007-01-20
lol I gave up after making the last correction. Did you see how I edited my code?

---

### Post by 56phil on 2007-01-20
No, Phossal. Now that you've removed your code, I suppose I never will. Oh, well.

---

### Post by phossal on 2007-01-20
Precisely. lol

---

### Post by public_void on 2007-01-20
My entry in C++, it can handle -, +, ints and doubles. I don't know if this is allowed, but I used the strtod(char*, char**) function. It converts a string to a double, returning a **signed double** (which my program just adds to the result), and changes the second parameter to where it finished. If its not allowed, I'll rewrite the strtod function and add that.

```
#include <iostream>
#include <cstring>
#include <cctype>

using namespace std;

int main (int argc, char *argv[]) {
  bool isSign(char sign);
  if (argc == 1) {
    cout << "Too few arguements" << endl;
    return 1;
  }
  for (char *check = argv[1]; *check != '\0';) {
    if (isdigit(*check)) {
      ++check;
    }
    else if (isSign(*check) && !isSign(*++check));
    else {
      cout << "Invalid string" << endl;
      return 1;
    }
  }
  double result = 0;
  char *line = argv[1];
  do {
    if (isspace(*line)) {
      continue;
    }
    else if (isdigit(*line) || isSign(*line)) {
      char *startOfNumber = line;
      double addition = strtod(startOfNumber, &line);
      result = result + addition;
    }
  } while (*line != '\0');
  cout << "Result = " << result << endl;
}

bool isSign(char sign) {
  switch (sign) {
    case '-':
    case '+':
    case '.': {
      return true;
    }
  }
  return false;
}

```

---

### Post by the_stranger on 2007-01-20
A while back for class I wrote a program in java that converted regular infix expressions to postfix (RPN) expressions. I dug up my old code and added a simple parser at the end that will go through the RPN expression and get the result. It's a bit more complicated then the other solutions posted but it works with addition, subtraction, multiplication, division, exponentiation and parenthesis. However it does not support the unary minus operator, so negative exponents and leading negative signs won't work. It also has no error checking. It works with ints and doubles and with or without spaces. I also used a custom deque (double ended queue) data structure. It's doable without one, but having it made my life easier. If anybody has an idea of how you can cleanly add support for unary minus operations then let me know.

Main program:
```
public class Expression
{
    public static void main(String[] args)
    {
        Deque<String> output = new Deque<String>();
        Deque<String> operators = new Deque<String>();
        Deque<Double> result = new Deque<Double>();  
        char[] expression = args[0].toCharArray();
        String number = "";
        
        System.out.println("Original expression: " + args[0]);
        
        for(char c : expression)
        {
        	if(c == ' ') continue;
        	else if(c == '+' || c == '-' || c == '*' || c == '/' || 
        		c == '^' || c == '(' || c == ')')
        	{
        		if(!number.equals(""))
        		{
        			output.append(number);
        			number = "";
        		}
        		
        		if(c == '(') operators.push(String.valueOf(c));
        		else if(c == ')')
        		{
        			while(!operators.checkFirst().equals("("))
        			{
        				output.append(operators.pop());
        			}
        			operators.pop();
        		}
        		else
        		{
        			if(operators.checkFirst() == null) operators.push(String.valueOf(c));
        			else
        			{
        				if(c == '^') operators.push(String.valueOf(c));
        				else
        				{
        					if(c == '*' || c == '/')
        					{
        						if(operators.checkFirst().equals("+") || 
        							operators.checkFirst().equals("-"))
        								operators.push(String.valueOf(c));
        						else
        						{
        							while(!(operators.checkFirst().equals("+") || 
        								operators.checkFirst().equals("-")))
        							{
        								if(operators.isEmpty() || 
        									operators.checkFirst().equals("(")) break;
        								output.append(operators.pop());
        							}
        							operators.push(String.valueOf(c));
        						}	
        					}
        					else
        					{
        						while(!operators.isEmpty())
        						{
        							if(operators.checkFirst().equals("(")) break;
        							output.append(operators.pop());
        						}
        						operators.push(String.valueOf(c));
        					}
        				}
        			}
        		}
        	}
        	else
        	{
        		number += String.valueOf(c);
        	}
        	
        }
        if(!number.equals(""))
	{
		output.append(number);
		number = "";
	}
        while(!operators.isEmpty())
        	output.append(operators.pop());
       	
       	System.out.print("RPN equivalent: ");
       	
       	for(String s : output)
       	{
       		System.out.print(s + " ");
       	}
       	System.out.println("");
       	
       	double v1;
       	double v2;
       	
       	for(String s : output)
       	{
       		if(s.equals("+"))
       		{
       			v2 = result.pop().doubleValue();
       			v1 = result.pop().doubleValue();
       			result.push(new Double(v1 + v2));
       		}
       		else if(s.equals("-"))
       		{
       			v2 = result.pop().doubleValue();
       			v1 = result.pop().doubleValue();
       			result.push(new Double(v1 - v2));
       		}
       		else if(s.equals("/"))
       		{
       			v2 = result.pop().doubleValue();
       			v1 = result.pop().doubleValue();
       			result.push(new Double(v1 / v2));
       		}
       		else if(s.equals("*"))
       		{
       			v2 = result.pop().doubleValue();
       			v1 = result.pop().doubleValue();
       			result.push(new Double(v1 * v2));
       		}
       		else if(s.equals("^"))
       		{
       			v2 = result.pop().doubleValue();
       			v1 = result.pop().doubleValue();
       			result.push(new Double(Math.pow(v1,v2)));
       		}
       		else
       		{
       			result.push(new Double(s));
       		}
       	}
       	System.out.println("Result: " + result.pop());
    }
}
```

Deque data structure:
```
import java.util.Iterator;

public class Deque<E> implements Iterable<E>
{
	private Node<E> head;
	private Node<E> tail;
	
	public Deque()
	{
		head = null;
		tail = null;
	}
	
	public boolean isEmpty()
	{
		return head == null;
	}
	
	public Iterator<E> iterator()
	{
		return new NodeIterator<E>(head);
	}
	
	public void push(E element)
	{
		Node<E> n = new Node<E>(element);
		
		if(isEmpty())
		{
			head = n;
			tail = n;
		}
		else
		{
			n.setNext(head);
			head = n;
		}
	}
	
	public E pop()
	{
		if(isEmpty()) return null;
		Node<E> n = head;
		head = head.next();
		return n.element();
	}
	
	public void append(E element)
	{
		Node<E> n = new Node<E>(element);
		
		if(isEmpty())
		{
			head = n;
			tail = n;
		}
		else
		{
			tail.setNext(n);
			tail = n;
		}
	}
	
	public E checkFirst()
	{
		if(isEmpty()) return null;
		return head.element();
	}
	
	private class Node<E>
	{
		private E element;
		private Node<E> next;
		
		public Node(E e)
		{
			element = e;
			next = null;
		}
		
		public E element()
		{
			return element;
		}
		
		public Node<E> next()
		{
			return next;
		}
		
		public void setNext(Node<E> node)
		{
			next = node;
		}
	}
	
	private class NodeIterator<E> implements Iterator<E>
	{
		Node<E> current;
		Node<E> last;
	
		public NodeIterator(Node<E> n)
		{
			current = n;
			last = null;
		}
		
		public E next()
		{
			last = current;
			current = current.next();
			return last.element();
		}
		
		public boolean hasNext()
		{
			return current != null;
		}
		
		public void remove()
		{
			//Not Supported
		}
	}
}

```

Testing:
```
java Expression "5 + ((1 + 2) * 4) - 3"
Original expression: 5 + ((1 + 2) * 4) - 3
RPN equivalent: 5 1 2 + 4 * + 3 - 
Result: 14.0

java Expression "3+4*2/(1-5)^2^3"
Original expression: 3+4*2/(1-5)^2^3
RPN equivalent: 3 4 2 * 1 5 - 2 3 ^ ^ / + 
Result: 3.0001220703125

```

---

### Post by Note360 on 2007-01-20
Sorry, you are right. I just re read what you said.

---

### Post by Wybiral on 2007-01-20
public_void:
"strtod" is OK... I just don't want people using "eval" or "exec" or any expression parsing libraries... Simply reading the values is fine.

If I had to solve this problem in C++, I would probably use a state machine. Add when I found the "+" and subtract when I found the "-"... I would use a string as a number buffer, and an integer as an accumulator and simply iterate over the input, concatenating the read character to the number buffer (unless it's + or -) and then when a + or - are found, add the number buffer to the integer (I would use atoi for this) and clear the number buffer and start over until it's gone.

As far as whether or not I would use a stack... Probably not, there are more effective ways. It's just that's how a lot of compilers create the opcodes for evaluating the expression in assembly. If I get some more free time this week, I *might* attempt and assembly submission, but I have a few other projects to work on (and I'll be gone the next 2 days)

---

### Post by jblebrun on 2007-01-20
> **Wybiral said:**
> public_void:
"strtod" is OK... I just don't want people using "eval" or "exec" or any expression parsing libraries... Simply reading the values is fine.

If I had to solve this problem in C++, I would probably use a state machine. Add when I found the "+" and subtract when I found the "-"... I would use a string as a number buffer, and an integer as an accumulator and simply iterate over the input, concatenating the read character to the number buffer (unless it's + or -) and then when a + or - are found, add the number buffer to the integer (I would use atoi for this) and clear the number buffer and start over until it's gone.

As far as whether or not I would use a stack... Probably not, there are more effective ways. It's just that's how a lot of compilers create the opcodes for evaluating the expression in assembly. If I get some more free time this week, I *might* attempt and assembly submission, but I have a few other projects to work on (and I'll be gone the next 2 days)

A stack-based approach makes sense if you want full expression parsing with precedence concerns. Infix notation gets converted to pre or postfix notation, which is inherently quite easy to evaluate using a stack based method. 

In my approach, I was trying to be as tight and efficient as possible for a case using only add and subtract. My main concern was avoiding multiplications during the main parsing loop, since that would be the biggest hit to scalability as input size increases. I chose to parse the expression backwards, but parsing it forwards would be an option too, if I kept an additional state variable to indicate whether to add or subtract. In fact, I might update my submission to do it that way, instead. 

i'm trying to come up with a one-line split/map/reduce solution in python like the one I already submitted, but also handling * and /, but it's making my head hurt.

---

### Post by Alasdair on 2007-01-20
Here's one written in Common Lisp. I'm kinda new to CL (and programming in general) so it may not be 100% perfect ;) 

[html](defun ^ (x y)
  (expt x y))

(defun evaluate (expr)
  (let ((value 1)
	(opr '*))
    (loop for i from 0 to (- (length expr) 1) do
	  (let ((item (nth i expr)))
	    (cond ((numberp item)
		   (progn (setq value (funcall opr value item))
			  (setq opr nil)))
		  ((listp item)
		   (progn (setq value (funcall opr value (evaluate item)))
			  (setq opr nil)))
		  (t
		   (if (null opr)
		       (setq opr item)
		       (error "Invalid sequence of operators"))))))
    value))[/html]

Output:

```
>(evaluate '(2 + 2))
4

>(evaluate '(5 ^ 2))
25

>(evaluate '(((5 ^ 2) * 2) - 10 + (100 * 4) + 4))
444

>(evaluate '((25 ^ 0.5) / 2))
2.5
```

It doesn't have any kind of operator precedence, although it does have brackets, and the expressions are made up of lists rather than strings which I hope is legal, also why does the [code] tag on this forum use a non monospaced font? (maybe it's just my strange browser settings :D)

---

### Post by Lux Perpetua on 2007-01-20
Here's (mostly) x86 assembly code for this task:```
[FONT="Courier New"]        .data
        .align 4
        
        .global parse_error
parse_error:
        .skip 1
        
        .global overflow
overflow:
        .skip 1
        
        .text
        
        /* parse_int routine */
        .local parse_int
parse_int:
        
        /* find sign */
        movb    $-1, %dl
        xorl    %eax, %eax
        call    advance
        cmpb    $0X2D, %al
        sete    %al
        decl    %eax
        xorb    %al, %dl
        addl    %eax, %esi

        xorl    %ecx, %ecx

        /* check first proper character */
        movb    (%esi), %al
        subb    $0X30, %al
        setl    %ah
        cmpb    $10, %al
        setge   %al
        orb     %ah, %al
        movb    %al, parse_error

parsing_loop:
        lodsb
        subb    $0X30, %al
        jl      the_end
        cmpb    $10, %al
        jge     the_end

        imul    $10, %ecx
        seto    %ah
        orb     %ah, %dh

        xorb    %dl, %al
        subb    %dl, %al
        cbtw
        cwtl

        addl    %eax, %ecx
        seto    %ah
        orb     %ah, %dh

        jmp     parsing_loop
the_end:
        decl    %esi
        movl    %ecx, %eax
	ret

        /* advance routine */
        .local  advance
advance:        
        lodsb
        cmpb    $0X20, %al
        je      advance
        ret

        .global parse_input
        /* int parse_input(const char *s); */
parse_input:
        pushl   %ebp
        movl    %esp, %ebp
        subl    $12, %esp
        movl    %ebx, -4(%ebp)
        movl    %esi, -8(%ebp)
        movl    %edi, -12(%ebp)

        movl    8(%ebp), %esi

        cld

        movb    $0, parse_error
        xorb    %dh, %dh
        
        call    parse_int
        movl    %eax, %ebx
read_loop:
        movb    parse_error, %cl
        cmpb    $0, %cl
        jne     done
        
        call    advance
        cmpb    $0, %al
        je      done
        cmpb    $0X2B, %al
        je      add_it
        cmpb    $0X2D, %al
        je      subtract_it

        /* unrecognized character */
        movb    $1, parse_error
        jmp     done
add_it: 
        call    parse_int
        addl    %eax, %ebx
        seto    %ah
        orb     %ah, %dh
        jmp     read_loop

subtract_it:    
        call    parse_int
        subl    %eax, %ebx
        seto    %ah
        orb     %ah, %dh
        jmp     read_loop
        
done:
        movl    %ebx, %eax
        movb    %dh, overflow

        movl    -4(%ebp), %ebx
        movl    -8(%ebp), %esi
        movl    -12(%ebp), %edi

        movl    %ebp, %esp
        popl    %ebp
	ret
[/font]
```Driver C program:```
[font="Courier New"]#include <stdio.h>

extern unsigned char parse_error;
extern unsigned char overflow;

int parse_input(const char *s);

int main(int argc, char **argv) {
    int a = parse_input(argv[1]);

    if (parse_error) {
        printf("Parse error\n");
    } else {
        printf("%d\n", a);
    }

    if (overflow) {
        printf("Overflow occurred\n");
    }

    return 0;
}[/font]
```The input string should be the first argument on the command line. (You can have spaces between integers and operators, but then you must enclose the input in quotes to ensure that the whole thing is parsed.) I didn't attempt to handle multiplication, floating-point input, or parentheses. > also why does the [****code] tag on this forum use a non monospaced font?When you find out, be sure to tell us.

---

### Post by runningwithscissors on 2007-01-21
```
#include <stdio.h>
#include <string.h>
#include <stdlib.h>

double eval_div(const char* expr, int expr_len)
{
	char* delimiters = "+-/*";
	char* delim_ptr = NULL;
	delim_ptr = strchr(expr, '/');
	if(delim_ptr == NULL || (strlen(expr) - strlen(delim_ptr)) >= expr_len)
		return strtod(strtok(expr, delimiters), NULL);
	else
		return eval_div(expr, (strlen(expr) - strlen(delim_ptr))) / \
				eval_div(delim_ptr, strlen(++delim_ptr));
}

double eval_mult(const char* expr, int expr_len)
{
	char* delim_ptr = NULL;
	delim_ptr = strchr(expr, '*');
	if(delim_ptr == NULL || (strlen(expr) - strlen(delim_ptr)) >= expr_len)
		return eval_div(expr, expr_len);
	else
		return eval_mult(expr, (strlen(expr) - strlen(delim_ptr))) * \
				eval_mult(delim_ptr, strlen(++delim_ptr));
}

double eval_minus(const char* expr, int expr_len)
{
	char* delim_ptr = NULL;
	delim_ptr = strchr(expr, '-');
	if(delim_ptr == NULL || (strlen(expr) - strlen(delim_ptr)) >= expr_len)
		return eval_mult(expr, expr_len);
	else
		if(strlen(delim_ptr) == strlen(expr))
			return -1 * eval_minus(delim_ptr, strlen(++delim_ptr));
		else
			return eval_minus(expr, (strlen(expr) - strlen(delim_ptr))) - \
				eval_minus(delim_ptr, strlen(++delim_ptr));
}

double eval_add(const char* expr, int expr_len)
{
	char* delim_ptr = NULL;
	delim_ptr = strchr(expr, '+');
	if(delim_ptr == NULL || (strlen(expr) - strlen(delim_ptr)) >= expr_len)
		return eval_minus(expr, expr_len);
	else
		return eval_add(expr, (strlen(expr) - strlen(delim_ptr))) + \
				eval_add(delim_ptr, strlen(++delim_ptr));
}

int check_expr(const char* expr)
{
	int i = 0;
	int flag = 0;
	for(i = 0; i < strlen(expr); ++i) {
		if(expr[i] == '+' || expr[i] == '-' || expr[i] == '*' || expr[i] == '/')
			if(flag == 0 && i < strlen(expr) - 1)
				flag = 1;
			else
				return 1;
		else
			flag = 0;
	}
	return 0;
}

int main(int argc, char** argv)
{
	if(check_expr(argv[1]) == 0)
		printf("%lg\n", eval_add(argv[1], strlen(argv[1])));
	else
		printf("expr error\n");

        return 0;
}

```

This ought to work. It seems to do multiplication and division okay too. Also accepts a negative sign on the first number. Maybe a bit cycle heavy, though. :(

---

### Post by jblebrun on 2007-01-21
> **Alasdair said:**
> Here's one written in Common Lisp. I'm kinda new to CL (and programming in general) so it may not be 100% perfect ;) 

[html](defun ^ (x y)
  (expt x y))

(defun evaluate (expr)
  (let ((value 1)
	(opr '*))
    (loop for i from 0 to (- (length expr) 1) do
	  (let ((item (nth i expr)))
	    (cond ((numberp item)
		   (progn (setq value (funcall opr value item))
			  (setq opr nil)))
		  ((listp item)
		   (progn (setq value (funcall opr value (evaluate item)))
			  (setq opr nil)))
		  (t
		   (if (null opr)
		       (setq opr item)
		       (error "Invalid sequence of operators"))))))
    value))[/html]

Output:

```
>(evaluate '(2 + 2))
4

>(evaluate '(5 ^ 2))
25

>(evaluate '(((5 ^ 2) * 2) - 10 + (100 * 4) + 4))
444

>(evaluate '((25 ^ 0.5) / 2))
2.5
```

It doesn't have any kind of operator precedence, although it does have brackets, and the expressions are made up of lists rather than strings which I hope is legal, also why does the [code] tag on this forum use a non monospaced font? (maybe it's just my strange browser settings :D)

You could probably make this work with strings pretty easily, right? I'm not familiar with Common lisp, but it should be trivial to add something that turns a string into a list of numbers and operators, right?

---

### Post by Alasdair on 2007-01-21
> **jblebrun said:**
> You could probably make this work with strings pretty easily, right? I'm not familiar with Common lisp, but it should be trivial to add something that turns a string into a list of numbers and operators, right?

Yes, all you have to do is slap parentheses on either end of the string and read it as a lisp expression.

 I also removed the progn statements from my code as they were unnecessary (no idea why I even put them there in the first place).

[HTML](defun ^ (x y)
  (expt x y))

(defun evaluate-string (expr)
  (evaluate (read-from-string (concatenate 'string "(" expr ")"))))

(defun evaluate (expr)
  (let ((value 1)
	(opr '*))
    (loop for i from 0 to (- (length expr) 1) do
	  (let ((item (nth i expr)))
	    (cond ((numberp item)
		   (setq value (funcall opr value item))
		   (setq opr nil))
		  ((listp item)
		   (setq value (funcall opr value (evaluate item)))
		   (setq opr nil))
		  (t
		   (if (null opr)
		       (setq opr item)
		       (error "Invalid sequence of operators"))))))
    value))[/HTML]

Output:

```
>(evaluate-string "2 + 2")
4

>(evaluate-string "5 ^ 2")
25

>(evaluate-string "((5 ^ 2) * 2) - 10 + (100 * 4) + 4")
444

>(evaluate-string "(25 ^ 0.5) / 2")
2.5
```

---

### Post by Mba7eth on 2007-01-22
Or you can do 
```
$echo $[ur expresion here]
```
  :lolflag: 


Cheers, 
          Ma7eth

---

### Post by Wybiral on 2007-01-22
> **Mba7eth said:**
> Or you can do 
```
$echo $[ur expresion here]
```
  :lolflag: 


Cheers, 
          Ma7eth

No... that breaks the rules... That's what we call using an expression parsing library.

---

### Post by cocteau on 2007-01-23
Alright, I'm going to post my best shot here. I fairly new to this whole thing but I have managed to make this in C++.

It does will not parse parentheses and only accepts ints. However it has got fail check so I should not be possible to crash it, and it works with +-* and / so far with precedence working correctly. It is heavily commented at the moment as it is still a work in progress, but I'm posting now because, I would really appreciate some comments on how I'm doing this.

```
#include <iostream>
#include <string>

using std::cout;			using std::cin;
using std::endl;			using std::string;
using std::getline;	

//global constant with char rules. Only declare one of these.
struct Rules
{
	char* numerics[12];
	char* operators[6];
	char* firstOrderOperators[2];
	char* secondOrderOperators[3];
	char* thirdOrderOperators[3];

	Rules() {
		*numerics = "0123456789-";
		*operators = "*/+-";
		*firstOrderOperators = "^";
		*secondOrderOperators = "*/";
		*thirdOrderOperators = "+-";
	}
};
const Rules rules;

//used for containing error messages.
struct Exception {
	Exception(string e) {
		err = e;
	}
	
	string err;
};
	
//isOperator returnes a bool to tell wether the pointer is
//an operator.
bool isOperator(const string::const_iterator& iter)
{
	const char* pOpr = *rules.operators;
		
	while (*pOpr) {
		if (*iter == *pOpr) {
			return true;
		} else {
			pOpr++;
		}
	}
	
	return false;
}

//isNumeric returns a bool to tell wether pointer as a numeric.
bool isNumeric(const string::const_iterator& iter)
{
	const char* pNum = *rules.numerics;
	
	while (*pNum) {
		if (*iter == *pNum) {
			return true;
		} else {
			pNum++;
		}
	}
	
	return false;
}

//test sequence to see if its legal.
//Input is valid if, and only if, the first part of the
//input is a numeric value or a '-' followed by either end of input
//or a single operator which must be followed by another numeric value.
string testSequence(const string& in)
{
	bool isNum = false;
	bool isOpr = true;
	string::const_iterator iter = in.begin();
	
	while (iter != in.end()) {
		//advance to first number or end.
		while (iter != in.end() && *iter == ' ') {
			iter++;
		}
		
		if (!isNum && isNumeric(iter)) {
			isNum = true;
			isOpr = false;
		}
		
		if (isOpr) {
			break;
		}
		
		if (isNum && !isOpr && isOperator(iter)) {
			isOpr = true;
			isNum = false;
		}
		
		iter++;
	}
	
	if (isOpr) {
		return "Invalid sequence.";
	} else {
		return "";
	}
}

//TestInput	- test to see if input contains any illegal value.
//An illegal value is one that is not defined as a numeric or an
//operator in the Rules struct.
string testInput(const string& in)
{
	string ret;
	bool isFound = false;
	string::const_iterator iter = in.begin();
	
	//test for invalid characters.
	while (iter != in.end()) {
		if (isNumeric(iter) || isOperator(iter)) {
			isFound = true;
		}
		
		if (!isFound) {
			if (ret.empty()) {
				ret = "Invalid char(s): ";
			}
	
			ret += *iter;
		}
		
		iter++;
		isFound = false;
	}
	
	if (ret.empty()) {
		return testSequence(in);
	} else {
		return ret;
	}
}

//sanitiseInput - Splits the input into sentenses (not implemented yet)
//and removes spaces.
void sanitiseInput(string& in)
{
	string::iterator iter = in.begin();
	while (iter != in.end()) {
		if (*iter == ' ') {
			iter = in.erase(iter);
		} else {
			iter++;
		}
	}
	
	return;
}

//takes two pointers and returns the numbers between them as an int
int stringToInt(string::iterator lIter, string::iterator rIter)
{
	int ret = 0;
	int count = 1;
	bool isNegative = false;
	
	if (*lIter == '-') {
		isNegative = true;
		lIter++;
	}

	while (rIter-- != lIter) {
		ret += (*rIter - 48) * count;
		count *= 10;
	}
	
	if (isNegative) {
		ret *= -1;
	}
	
	//cout << "returning (int): " << ret << endl;
	
	return ret;
}

//pow - simple power function
int pow(int x, int y)
{
	if (y < 1 || x == 0) {
		return 1;
	}
	
	int ret = x;
	
	while ( --y != 0 ) {
		ret *= x;
	}
	
	return ret;
}

//converts an int back to a string
string intToString(int x)
{
	string ret;
	
	//cout << "x: " << x << endl;
	
	if (x < 0) {
		ret += '-';
		x *= -1;
	} else if (x == 0) {
		return "0";
	}
	
	int temp = x;
	int count = 0;
	
	while (temp > 0) {
		count++;
		temp /= 10;
	}
	
	while (count-- != 0) {
		temp = x / pow(10, count);
		ret += (temp + 48);
		x -= temp * pow(10, count);
	}
	
	//cout << "intToString: " << ret << endl;

	return ret;
}

//findlValue returns the l-value as an int.
int findlValue(string& in, string::iterator& it)
{
	string::iterator iter = it;
	bool isFirstOpr = false;
	--iter;
		
	while (iter > in.begin()) {
		if (*iter == '-' && !isFirstOpr) {
			isFirstOpr = true;
			iter--;
			continue;
		}
		
		if (isFirstOpr && !isOperator(iter)) {
			iter++;
			iter++;
			break;
		}
			
		if (isOperator(iter)) {
			iter++;
			break;
		}
		
		iter--;
	}
		
	//cout << "iter: " << *iter << endl;
	int ret = stringToInt(iter, it);
	it = in.erase(iter, it);
	return ret;
}

//findrValue returns the r-value as an int.
int findrValue(string& in, string::iterator it)
{
	string::iterator iter = ++it;
	//bool isFirstOpr = false;
	
	while (iter != in.end()) {
		iter++;
		if (isOperator(iter)) {
			break;
		}
	}
	
	int ret = stringToInt(it, iter);
	in.erase(it, iter);
	return ret;
}

//add - addition
int add(const int left, const int right) {
	return left + right;
}

//sub - subtraction
int sub(const int left, const int right) {
	return left - right;
}

//multi - multiplication
int multi(const int left, const int right) {
	return left * right;
}

//divi - division
int divi(const int left, const int right) {
	if (right == 0) {
		throw Exception("Division by zero!");
	} else {
		return left / right;
	}
}


//calculate - takes a pointer to an operator and translates values on
//either side to numbers.
void calculate(string& in)
{
	bool isRunning = true;
	bool isOpr = false;
	int nlValue = 0;
	int nrValue = 0;
	string buffer;
	string::iterator szIter = in.begin() + 1;
	char* pOpr = *rules.firstOrderOperators;
	
	while (isRunning) {
		buffer.clear();
		isOpr = false;
		szIter = in.begin() + 1;
		//cout << "input is: " << in << endl;
		//cout << *szIter << endl;
		
		while (!isOpr && szIter != in.end()) {
			if (*szIter == *pOpr) {
				isOpr = true;
			} else {
				szIter++;
			}
		}
		
		if (!isOpr) {
			pOpr = *rules.secondOrderOperators;
			szIter = in.begin() + 1;
		}
		
		while (!isOpr && szIter != in.end()) {
			if (*szIter == *pOpr || *szIter == *(pOpr + 1)) {
				//cout << "3" << *szIter << "first: " << *pOpr << ", second: " << *(pOpr + 1) << endl;
				isOpr = true;
			} else {
				szIter++;
			}
		}
		
		if (!isOpr) {
			pOpr = *rules.thirdOrderOperators;
			szIter = in.begin() + 1;
		}
		
		while (!isOpr && szIter != in.end()) {
			if (*szIter == *pOpr || *szIter == *(pOpr + 1)) {
				isOpr = true;
			} else {
				szIter++;
			}
		}
		
		//cout << "isOpr: " << isOpr << endl;
		
		if (!isOpr) {
			//cout << "returning: " << ret << endl;
			break;
		}
		
		//cout << "szIter: " << *szIter << endl;
		
		//cout << "In: '" << in << "'" << endl;
		nlValue = findlValue(in, szIter);
		//cout << "In: '" << in << "'" << endl;
		nrValue = findrValue(in, szIter);
		//cout << "In: '" << in << "'" << endl;
		
		//cout << "l-value: " << nlValue << ", r-value: " << nrValue << endl;

		switch (*szIter) {
			case '+':
				buffer = intToString(add(nlValue, nrValue));
				szIter = in.erase(szIter);
				in.insert(szIter, buffer.begin(), buffer.end());
				break;
			case '-':
				buffer = intToString(sub(nlValue, nrValue));
				szIter = in.erase(szIter);
				in.insert(szIter, buffer.begin(), buffer.end());
				break;
			case '*':
				buffer = intToString(multi(nlValue, nrValue));
				szIter = in.erase(szIter);
				in.insert(szIter, buffer.begin(), buffer.end());
				break;
			case '/':
				buffer = intToString(divi(nlValue, nrValue));
				szIter = in.erase(szIter);
				in.insert(szIter, buffer.begin(), buffer.end());
				break;
			default:
				throw Exception("Invalid operator");
				break;
		}
	}
	
	return;
}

int main()
{
	string input, buffer;
	
	while ( true ) {
		cout << ":";
		getline(cin, input);
		
		if (input == "exit" || input == "Exit") {
			break;
		}
		
		buffer = testInput(input);
		
		if (!buffer.empty()) {
			cout << "Error: " << buffer << endl;
			continue;
		}
		
		buffer = input;
		sanitiseInput(input);
		
		try {
		calculate(input);
		cout << buffer << " = " << input << endl;
		} catch (Exception e) {
			cout << "Error: " << e.err << endl;
		}
	}
	
	return 0;
}
```

Examples of output (input is the lines prefixed with a colon).
:1+3*4
1+3*4 = 13
:-10+4
-10+4 = -6
:10+5*-2
10+5*-2 = 0
:10/0
Error: Division by zero!

---

### Post by 56phil on 2007-01-24
Here's my entry. It supports:[LIST]
[*]addition
[*]subtraction
[*]multiplication
[*]division
[*]exponentiation
[*]parentheses
[*]factorials
[/LIST]

```

#!/usr/bin/python


""" Weekly Programming Challenge: Friday, Jan 19, 2007 """


i_type = type(1)
f_type = type(1.0)
ops = '+-*/^!'
grp = '()'
white_space = ' \t'


def make_num(a):
    if '.' in a:
        return float(a)
    else:
        return int(a)
    
    
def factorial(a):
    if a < 0 or int(a) != a:
        print 'invalid argument for factorial'
        return -1
    elif a < 2:
        return 1
    else:
        return a * factorial(a-1)

def do_list(my_list):
    x = str(my_list[-1])
    if x in ops and x != '!':
        print 'Operator Error', x
        my_list.pop()

    x = str(my_list[0])
    if x in ops:
        print 'Operator Error', x
        my_list.pop(0)

    while '(' in my_list:
        openers = my_list.count('(')
        n = i = 0
        while n < len(my_list):
            if my_list[n] == '(':
                i += 1
                if i == openers:
                    m = n + 1
                    while m < len(my_list):
                        if my_list[m] == ')':
                            my_list.pop(m)
                            x = do_list(my_list[n+1:m])
                            for i in range(m - n):
                                my_list.pop(n)
                            for i, element in enumerate(x):
                                my_list.insert(n+i, element)
                            break
                        m += 1
                    break
            n += 1

    i = 1;
    while i < len(my_list):
        if my_list[i] == '!':
            my_list.pop(i)
            my_list.insert(i-1, factorial(my_list.pop(i-1)))
        else:
            i += 1

    i = 0
    while i < len(my_list):
        if my_list[i] == '^':
            my_list.pop(i)
            my_list.insert(i-1, my_list.pop(i-1) ** my_list.pop(i-1))
        else:
            i += 1

    i = 0;
    while i < len(my_list):
        x = my_list[i]
        x_type = type(x)
        y_type = None
        if i+1 < len(my_list):
            y_type = type(my_list[i+1])
        if x == '*':
            my_list.pop(i)
            my_list.insert(i-1, my_list.pop(i-1) * my_list.pop(i-1))
        elif x == '/':
            my_list.pop(i)
            my_list.insert(i-1, my_list.pop(i-1) / my_list.pop(i-1))
        elif (x_type == f_type or x_type == i_type) and \
             (y_type == f_type or y_type == i_type):
            my_list.insert(i, my_list.pop(i) * my_list.pop(i))
        else:
            i += 1

    i = 0;
    while i < len(my_list):
        x =  my_list[i]
        if x == '+':
            my_list.pop(i)
            my_list.insert(i-1, my_list.pop(i-1) + my_list.pop(i-1))
        elif x == '-':
            my_list.pop(i)
            my_list.insert(i-1, my_list.pop(i-1) - my_list.pop(i-1))
        else:
            i += 1

    return my_list


def get_input():
    in_str = raw_input('Enter your expression: ')
    fmt_err = False
    digit_str = ''
    my_list = []
    for char in in_str:
        if char.isdigit():
            digit_str += char
        elif char == '.':
            digit_str += char
        elif char in ops + grp:
            if digit_str:
                my_list.append(make_num(digit_str))
                digit_str = ''
            my_list.append(char)
        elif char in white_space:
            pass
        else:
            print 'format error'
            fmt_err = True
            break

    if digit_str:
        my_list.append(make_num(digit_str))

    if my_list.count('(') != my_list.count(')'):
        print 'Unbalenced Parentheses'
        fmt_err = True

    if str(my_list[-1]) in ops and my_list[-1] != '!':
        print 'Expression may not end with an operator'
        fmt_err = True

    if str(my_list[0]) in ops and my_list[0] != '-':
        print 'Expression must begin with a number, (, or -'
        fmt_err = True

    i = 0
    while i + 1 < len(my_list):
        if my_list[i] == '-' :
            a = ''
            if i > 0:
                a = my_list[i-1]
            if i == 0 or str(a) in ops or a == '(' or my_list[i+1] == '(':
                my_list.pop(i)
                my_list.insert(i, -1)
                my_list.insert(i+1, '*')
                if a == '^':
                    my_list.insert(i, '(')
                    my_list.insert(i+4, ')')
        i += 1

    i = 1
    while i < len(my_list):
        if (str(my_list[i]) in ops and str(my_list[i-1]) in ops and my_list[i-1] != '!') or \
           (my_list[i] == '!' and my_list[i-1] == '!'):
            print 'contiguous operators'
            fmt_err = True
        i += 1

    if not fmt_err:
        my_list = do_list(my_list)
        print my_list[0]


if __name__ == '__main__':
    while True:
        get_input()
        in_str = raw_input('Do you have another expression to try? (y/n): ')
        if in_str.lower().strip() != 'y':
            break

```

---

### Post by Note360 on 2007-01-24
Here is my really bad one 
it supports
addition and subtraction with no room for scalability

```

#!/usr/bin/ruby

=begin
Christopher Woodall
Expression Handling Program
=end

red = "\033[31m"
standard = "\033[0m"

class Expression
    
    def initialize( values )    # values should be an array
        @values = values        
        @results = 0
    end
    
    def evaluate_expression()     
        for value in @values
            value = value.to_f
            @results = @results + value
        end
        return @results
    end
    
    attr_reader :results, :values
end

def prepare_string( input )
    input = input.chomp
    input = input.sub( '-', '+-' )
    input = input.split( '+' )
    return input
end

def scan_for_errors( input )
    if input =~ /([0-9]*\+\+[0-9]*)|([0-9]*\-\+[0-9]*)|(^[\+|\-][0-9]*)|([0-9]*[\+|\-]$)/
        puts red + "ERROR" + standard
        return true
    else
        return false
    end
end

print "Input Expression: "

input = gets
if scan_for_errors( input ) == true
    exit
else
    list_of_values = prepare_string( input )
    expression = Expression.new( list_of_values )
    expression.evaluate_expression
end

puts "Results: #{expression.results}"

```

Oh well I know it is bad, lol I couldnt get it though so I just posted what I had so far.

---

### Post by ghostdog74 on 2007-01-24
```

# no support for parenthesis
# there will be bugs.
import re,operator,sys
temp = []
s = "10.112*3423432/433/3.32323+294*38*7.2+40.1/2-432-3+323-3.2/4.3+34*23123-32*2.7/2+5523+383+4*12+3"
pat_d = re.compile(r"((?:\d+\.\d+|\d+)(?:\/(?:\d+\.\d+|\d+))+)")
pat_m = re.compile(r"((?:\d+\.\d+|\d+)(?:\*(?:\d+\.\d+|\d+))+)")
def findmatch(s,pat,op):
        oper = { "/" : operator.div , "*": operator.mul}
        for match in pat.finditer(s):
                span = match.span()
                grp = match.group()
                s = s.replace(grp,str(reduce( oper[op], [float(f) for f in grp.split(op)])))
        return s
s = findmatch(s,pat_d,"/")
s = findmatch(s,pat_m,"*")
addtotal = reduce(operator.add, [float(f) for f in s.split("+") if "-" not in f])
for i in [f for f in s.split("+") if "-" in f]:
        temp.append(reduce(operator.sub, [float(k) for k in i.split("-")]))
print "Result: " , addtotal + reduce(operator.add , temp)


```

---

### Post by derjames on 2007-01-25
yet another not elegant solution ... in Ruby

```


def check_for_errors(my_qty)
	if my_qty.include?("++") or my_qty.include?("--") or my_qty.include?("+-") or my_qty.include?("-+")
		raise "Error, multiple operand detected"
	elsif my_qty.include?("*") or my_qty.include?("/") or my_qty.include?("^") or my_qty.include?("%")
		raise "Multiplication, divison, exponentiation and module are yet to be supported"
	end
end

def split_of_quantities(my_qty)
	prep_qty = my_qty.gsub("-","+-").split("+")
	index = 0
	sum = 0
	(prep_qty.length).times {
		sum += prep_qty[index].to_s.to_f
		index += 1
	}
	puts sum
end

print"Quantities? "
qty=gets()
check_for_errors(qty)
split_of_quantities(qty)
```

---

### Post by Note360 on 2007-01-25
we ysed the same principle for our Ruby solutions. THebad thing about our solutions is that they cannot really be easily expanded.

---

### Post by derjames on 2007-01-25
> **Note360 said:**
> we ysed the same principle for our Ruby solutions. 

Actually I took your code and removed some lines ...


> **Note360 said:**
>  THebad thing about our solutions is that they cannot really be easily expanded.



 I am working trying to incorporate all the features suggested by Wybiral....

Cheers

---

### Post by Note360 on 2007-01-25
Lol, sorry about the spelling, I typed it up fast before going to take a Regents.

I understand, and it makes sense. I am glad you used my code. I originally had what you had, but I decided to implement a class.

Oh, and thanks I learned from your code I now now how to not use regexp (include?) and how to raise errors.

---

### Post by Bluetech on 2007-01-25
Since I'm learning recursion right now I decided to attempt a recursive solution in c++ (that means I don't pay much attention to the performance), and see what you think.
It doesn't do error checking or precedence, but it handles doubles fine I think.
Any criticism would be welcome!
(I belive the code is pretty simple so I didn't comment it)
```

#include <iostream>
#include <string>
#include <cctype>
using namespace std;

double parse_expr(const string& expr);
bool is_atofable(const string& str);

int main(int argc, char **argv)
{
	if (argc == 1) {
		cerr << "Usage: parse [math expression]" << endl;
		exit(EXIT_FAILURE);
	}
		
	cout << parse_expr(argv[1]) << endl;
	exit(EXIT_SUCCESS);
}

double parse_expr(const string& expr)
{
	if (is_atofable(expr)) return atof(expr.c_str());
	
	int pos = expr.find_last_of("*/+-");
	double left = parse_expr(expr.substr(0, pos));
	double right = parse_expr(expr.substr(pos+1));
	
	switch (expr[pos]) {
		case '+': return left + right;
		case '-': return left - right;
		case '*': return left * right;
		case '/': return left / right;
		default : return 0; // don't know what to do here
	}
}

bool is_atofable(const string& str)
{
	for (unsigned int i=0; i < str.size(); i++)
		if (!isdigit(str[i]) && !isblank(str[i]) && str[i] != '.')
			return false;
	return true;
}

```

---

### Post by jblebrun on 2007-01-25
> **Bluetech said:**
> Since I'm learning recursion right now I decided to attempt a recursive solution in c++ (that means I don't pay much attention to the performance), and see what you think.
It doesn't do error checking or precedence, but it handles doubles fine I think.
Any criticism would be welcome!
(I belive the code is pretty simple so I didn't comment it)
```

#include <iostream>
#include <string>
#include <cctype>
using namespace std;

double parse_expr(const string& expr);
bool is_atofable(const string& str);

int main(int argc, char **argv)
{
	if (argc == 1) {
		cerr << "Usage: parse [math expression]" << endl;
		exit(EXIT_FAILURE);
	}
		
	cout << parse_expr(argv[1]) << endl;
	exit(EXIT_SUCCESS);
}

double parse_expr(const string& expr)
{
	if (is_atofable(expr)) return atof(expr.c_str());
	
	int pos = expr.find_last_of("*/+-");
	double left = parse_expr(expr.substr(0, pos));
	double right = parse_expr(expr.substr(pos+1));
	
	switch (expr[pos]) {
		case '+': return left + right;
		case '-': return left - right;
		case '*': return left * right;
		case '/': return left / right;
		default : return 0; // don't know what to do here
	}
}

bool is_atofable(const string& str)
{
	for (unsigned int i=0; i < str.size(); i++)
		if (!isdigit(str[i]) && !isblank(str[i]) && str[i] != '.')
			return false;
	return true;
}

```

It's a nice start of a submission: but there is a functional error related to operator precedence. For example, try:

./parse "1+2+3*4"
./parse "3*4+1+2"

There's some ambiguity, here!

---

### Post by Bluetech on 2007-01-26
I probably shouldn't be keeping this thread up, but here is a somewhat improved attempt with precedence and exponents. The rest of the program is the same.

```

double parse_expr(const string& expr)
{
	if (is_atofable(expr)) return atof(expr.c_str());
	
	string::size_type pos = expr.find_last_of("+-");
	if (pos == string::npos) pos = expr.find_last_of("*/");
	if (pos == string::npos) pos = expr.find_last_of("^");
	if (pos == string::npos) {
		cerr << "malformed expression" << endl; 
		exit(EXIT_FAILURE);
	}
	
	double left = parse_expr(expr.substr(0, pos));
	double right = parse_expr(expr.substr(pos+1));
	
	switch (expr[pos]) {
		case '+': return left + right;
		case '-': return left - right;
		case '*': return left * right;
		case '/': return left / right;
		case '^': return powf(left, right);
		default : return 0;
	}
}

```

---

### Post by Wybiral on 2007-01-26
I don't see any reason not to be able to keep up an old challenge... They are supposed to be for fun and education anyway.

---

### Post by rune_kg on 2008-12-28
**_PHP_**
Tried to make it as short as possible.

[PHP]
<?
function calc($s) {
	if (!preg_match_all('/(?P<k>[0-9.]+)(?P<v>([+-])|)/', $s, $m)) return false;
	extract($m);
	$r=array_shift($k);
	for ($i=0;$i<count($k);$i++) {
		if ($v[$i]=='+') $r+=$k[$i];
		if ($v[$i]=='-') $r-=$k[$i]; 
	}
	return $r;
}

var_dump (calc('200-50+80-5'))."\n<br />";
var_dump (calc('98-50+40'))."\n<br />";
var_dump (calc('98--50+40'))."\n<br />";
var_dump (calc('98-50+40-'))."\n<br />";[/PHP]

---

### Post by rune_kg on 2008-12-29
**_PHP_**
LOL...even shorter and will as an extra bonus generate notices.
[PHP]
<?
function calc($s){
	preg_match_all('/(?P<k>[0-9.]+)(?P<v>([+-])|)/',$s,$m);
	for ($i=1;$i<count($m['k']);$i++) $r+=($m['v'][$i-1].'1')*$m['k'][$i];
	return $r+$m['k'][0];
}

var_dump (calc('200-50+80-5'))."\n<br />";
var_dump (calc('98-50+40'))."\n<br />";
var_dump (calc('98--50+40'))."\n<br />";
var_dump (calc('98-50+40-'))."\n<br />";[/PHP]

---

### Post by snova on 2008-12-29
(Thanks to rune_kg for bumping this thread into my attention zone.)

I recently started learning a little Ruby, so rather than my usual Python, here's my entry in the aforementioned language:

[PHP]#!/usr/bin/ruby

C = ARGV[0].gsub(/\s/,"").split(/(\d+|[\+\-\*\/\^])/).delete_if{|x|x==""}
C.each_index { |x| C[x] = C[x].to_i if C[x] =~ /\d+/ }

def rf(op)
    C.each_index { |x| C[x-1..x+1] = yield C[x-1], C[x+1] if op == C[x] }
end

rf("^") { |x,y| x**y }
rf("*") { |x,y| x*y }
rf("/") { |x,y| x/y }
rf("+") { |x,y| x+y }
rf("-") { |x,y| x-y }

puts C[0]
[/PHP]

Usage:

```
$ ruby eval.rb "1+2^2*3
```

It features the whole range of operations. No negative numbers or floats, sadly.

Error handling consists of a stack trace when the exception goes off. :P

Comments welcome. I'm not very good at this yet...

Edit: Whoops! There's a bug regarding precedence. I'll see if I can fix it.

Namely, addition and subtraction are supposed to be done at the same time. Instead, it does one, then the other. Likewise for multiplication and division.

---

