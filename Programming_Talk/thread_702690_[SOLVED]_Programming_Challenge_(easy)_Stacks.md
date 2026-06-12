---
title: "[SOLVED] Programming Challenge (easy): Stacks"
date: 2008-02-20
forum: Programming Talk
---

### Post by Wybiral on 2008-02-20
We haven't had a good programming challenge for a while, so I figured I would start a simple one and we'll see if we can't revive them. This challenge is an easy one, you have to implement the [stack ADT]("http://en.wikipedia.org/wiki/Stack_%28data_structure%29") in your language of choice. You will be judged on creativity, efficiency, and elegance (in terms of whatever language you use, I won't be prejudice for this challenge).

The rules:
[LIST=1]
[*]You can't use any preexisting list / stack-like structure. So Python programmers are prohibited from using lists and C++ programmers are prohibited from using the STL stack. [COLOR="Red"](Clarification: you are prohibited from using them directly as the stack, not from simply using them in your code)[/COLOR]
[*]You must implement ALL of the following routines: [COLOR="Blue"]push[/COLOR] (push value onto stack), [COLOR="Blue"]pop[/COLOR] (pop value from stack, AND return it), [COLOR="Blue"]top/tos[/COLOR] (return top value on stack, but DON'T pop it)
[/LIST]

Bonus points (for those who like extra credit)
[list=1]
[*]If your stack implementation is generic (capable of being used for more than one type) [COLOR="Red"](Clarification: it doesn't have to hold multiple types at once, just the ability to create multiple stack types. An int stack, a string stack, etc (without writing completely new implementations). Although a truly dynamic stack would also work)[/COLOR]
[/list]

You have until Wednesday (next week) to complete it and have it posted here. The author of my favorite entry will get to choose next weeks challenge (where he/she will then get to choose the person to follow them).

Let the challenge begin!

---

### Post by Siph0n on 2008-02-20
Awesome! :) I can't wait to get back into these! good idea!!!

---

### Post by LaRoza on 2008-02-20
This should be interesting to try to write in Forth or Lisp...

---

### Post by CptPicard on 2008-02-20
Oh man, this is going to be [so much work]("http://ubuntuforums.org/showthread.php?t=548096&highlight=cubytes+stacks"). :(

@LaRoza: well, Lisp's lists are a natural, it's almost too easy. Stack top is (car list) and rest of stack is (cdr list), pushing is returning (cons new_item list). Popping is peeking first and replacing list with rest of list.

Scheme, without testing in any way:

```

(define (makestack) '())

(define (peek stack) (car stack))
(define (popped stack) (cdr stack))
(define (pushed_stack stack item) (cons item stack))

```

In a pure-functional style, it's difficult to define "pop" in terms of both returning top item and mangling the structure underneath as we do it, so one needs to peek first and then do something with the popped stack, if one needs it.

By the way... This Is Homework.

---

### Post by aks44 on 2008-02-20
> **Wybiral said:**
> You must implement ALL of the following routines: [COLOR="Blue"]push[/COLOR] (push value onto stack), [COLOR="Blue"]pop[/COLOR] (pop value from stack, AND return it), [COLOR="Blue"]top/tos[/COLOR] (return top value on stack, but DON'T pop it)

As far as C++ goes, pop() just can't be made exception-safe (strong guarantee) for templated stacks.

I'd suggest that the people submitting a C++ template implement remove() instead (which removes the topmost value from the stack, but does NOT return it).
Of course if you allow it and people choose to follow that way, strong exception-safety would be a basic requirement.

Just my 0.02 (I can provide more in-depth explanations if needed).

---

### Post by Wybiral on 2008-02-20
> **CptPicard said:**
> Oh man, this is going to be [so much work]("http://ubuntuforums.org/showthread.php?t=548096&highlight=cubytes+stacks"). :(

lol, I forgot all about that...

---

### Post by LaRoza on 2008-02-20
I idly started making one in Python, not using Lists or anything. I got along with the basics, then looked "Stack" up on Wikipedia to get an overview of the data structure, then I saw one given as an example on that page...in Python. It looked too similar to mine, so I scrapped it. Don't want to do something could easily be mistaken for cheating.

Might do it in another language.

---

### Post by Jessehk on 2008-02-20
I'm trying to learn Haskell, so I attempted to use Monad Transformers to write a Stack type. I don't know if it's "correct" (and I'd be happy to be corrected), but it definitely works.

Keep in mind that the code for the actuall ADT ends at the marker. All the rest of the code consists of examples and of a main function that prints the state of the stack and the resulting value following every example.

Because of the ErrorT monad, there is built-in exception handling.

EDIT: I should also mention that it is a generic type. In my examples, I happened to fill it with **Int**'s.
EDIT2: I misread the rules, and I missed the bit about not using built-in lists. I'll leave the code as-is just because
I enjoyed writing it, but I don't expect to be "eligible" for the contest. :)
EDIT3: I've changed my mind based on the other entries. I use a list to keep track of the stack, but there is no built-in stack type. I would like to be considered for the contest. :)
```

-- By Jessehk
-- Feb. 20, 2008
--
-- Newbie at Haskell hopefully utilizing monad transformers correctly
-- to write a Stack class.

module Main where

import Control.Monad.State
import Control.Monad.Error

data Stack a = Stack [a]
             | Empty
             deriving (Eq, Show)

-- Get the raw contents of a stack.
raw :: Stack a -> [a]
raw Empty = []
raw (Stack list) = list

type StackMonad a = ErrorT String (StateT (Stack a) IO)

-- Execuate a series of stack actions given an
-- initial Stack.
runStack m s = runStateT (runErrorT m) s

-- Push an element on to a Stack.
-- Returns the new size of the Stack.
push :: a -> (StackMonad a) Int
push obj = do
    stack <- get
    put $ Stack (obj : raw stack)
    return $ (length $ raw stack) + 1


-- Remove the top element of the stack
-- and return it.
pop :: (StackMonad a) a
pop = do
    stack <- get

    case stack of
        Empty -> throwError "Stack.pop: Empty Stack"
        Stack [e] -> do
            put Empty
            return e
        Stack list -> do
            let top = head list
            put $ Stack (tail list)
            return top

-- Return the top element of a stack.
-- Does NOT remove it.
top :: (StackMonad a) a
top = do
    stack <- get
    case stack of
        Empty -> throwError "Stack.top: Empty Stack"
        Stack list -> return $ head list

-- END ACTUAL STACK CODE. ALL THAT FOLLOWS ARE EXAMPLES --

pushExample = do
    push 3
    push 2
    push 1

popExample = do
    push 1
    push 2
    pop
    pop

topExample = do
    push 3
    push 2
    top

-- This will fail once there are
-- no elements to pop
errorHandlingExample = do
    push 5
    push 6
    pop
    pop
    pop

reportResult :: (Show a) => (Either String a, Stack a) -> IO ()
reportResult ((Left msg, _)) = putStrLn $ "Error: " ++ msg
reportResult ((Right val, s)) = putStrLn $ (show s) ++ ", value: " ++ (show val)

main :: IO ()
main = do
    -- Send in an empty stack
    result <- runStack pushExample Empty
    reportResult result

    -- Start with an existing stack
    result <- runStack popExample (Stack [10, 9, 8])
    reportResult result

    result <- runStack topExample Empty
    reportResult result

    result <- runStack errorHandlingExample Empty
    reportResult result

```

**Output**
```

Stack [1,2,3], value: 3
Stack [10,9,8], value: 1
Stack [2,3], value: 2
Error: Stack.pop: Empty Stack

```

---

### Post by themusicwave on 2008-02-20
I'm going to give it a shot in Python.

I've done this exercise before for courses in C, C++ and Java.  I am currently learning python so it will be interesting to try.

The no list thing definitely makes it a bit more diffucult.  I know python has arrays, but they are static typed.  So making a stack class to except all types with them seems impossible.

I'll have to think about it.

---

### Post by pedro_orange on 2008-02-21
If these challenges take off, you should host the winning/best of each language as parts of your tutorial sections on your respective wikis.

Free wiki updates! :)

I might have a go when I get home from work. (If I can bare looking at a computer screen after doing it from 9-5!)

---

### Post by LaRoza on 2008-02-21
> **themusicwave said:**
> I'm going to give it a shot in Python.

I've done this exercise before for courses in C, C++ and Java.  I am currently learning python so it will be interesting to try.

The no list thing definitely makes it a bit more diffucult.  I know python has arrays, but they are static typed.  So making a stack class to except all types with them seems impossible.

I'll have to think about it.

It is very easy and straight forward in Python. You only need two classes. See wikipedia if you don't mind seeing a possible answer.

---

### Post by Tuna-Fish on 2008-02-21
So, I needed a stack. That got me thinking, my computer already has a stack, right, so why not use that?

Behold:
[php]
#! /usr/bin/env python
# encoding=utf-8
######################
#Author: Antti-Ville Tuunainen (tuna)
#The Mighty Recursive-Execution-Stack-Based-Stack
#No, I don't usually program like this.
import Queue, thread
def _stack(qin,qout,o):
    while True:
        task = qin.get()
        if task == "push":
            oo = qin.get()
            call = True
        elif task == "pop":
            qout.put(o)
            return
        elif task == "peek":
            qout.put(o)
            call = False
        if (call):
            _stack(qin,qout,oo)
def _stackstart(qin,qout):
    while True:
        _stack(qin,qout,None)
            
class RESBStack():
    def __init__(self):
        self.qin = Queue.Queue()
        self.qout = Queue.Queue()
        self.t = thread.start_new_thread(_stackstart,(self.qin,self.qout))
    def push(self,o):
        self.qin.put("push")
        self.qin.put(o)
    def pop(self):
        self.qin.put("pop")
        return self.qout.get()
    def peek(self):
        self.qin.put("peek")
        return self.qout.get()

if __name__ == "__main__":
    stack = RESBStack()
    stack.push(1)
    stack.push("moi")
    stack.push(True)
    stack.push(3.14)
    print stack.peek()
    print stack.peek()
    print stack.pop()
    print stack.pop()
    stack.push(42)
    print stack.peek()
    print stack.pop()
    
    print stack.pop()
    print stack.pop()
    print stack.pop()
[/php]

You know that it's empty when it returns none. Only, 'cos you can push a None, you don't. Ain't life fun?

Oh, and the thread keeps on living until someone calls system.exit.

But hey, why gloss over minor details?

---

### Post by Lster on 2008-02-21
Tuna-Fish, that looks nice! I need to learn a little more Python first to understand it entirely!

---

### Post by Tuna-Fish on 2008-02-21
> **Lster said:**
> Tuna-Fish, that looks nice!
It's not, it's horrible on purpose :)

>  I need to learn a little more Python first to understand it entirely!

Well, it might work as a basic primer on threads.

---

### Post by bobbocanfly on 2008-02-21
Here is mine. It calls sys.exit() and prints to screen if the stack is empty or the limit is exceeded and isnt threaded so that will probably count against it.

stack.py class:
```
#General Purpose Stack Class
#Copyright (C) David Futcher (bobbo) 2007 - 2008
#bobbocanfly@gmail.com

#To init:
#myStack = Stack(int limit)
#To invoke a class without a limit use limit use:
#myStack = Stack(0)

import sys

class Stack:

    def __init__(self, limit):
        self.STACK = [] #This is the actual Stack Array
        self.itemIndex = 0
        if limit == 0:
            self.limitUsed = 0
        else:
            self.limitUsed = 1
            self.itemLimit = limit

    #Push data onto the stack
    def push(self, data):
        if self.limitUsed:
            if self.itemIndex == self.itemLimit:
                print "Stack full, cant push anything onto it"
                sys.exit(1)
        self.STACK.insert(self.itemIndex + 1, str(data))
        self.itemIndex += 1

    #Pop data from the stack
    def pop(self):
        if self.itemIndex == 0:
            print "Stack empty, exiting"
            sys.exit(1)

        self.itemIndex -= 1

        return self.STACK.pop()

    def peek(self):
        return self.STACK[self.itemIndex - 1]

    #Remove all data from stack
    def flush(self):
        if self.itemIndex == 0:
            print "Stack empty, exiting"
            sys.exit(1)

        for i in self.STACK:
            self.STACK.remove(i)

        self.itemIndex = 0

    #Check if stack is empty
    def isEmpty(self):
        if self.itemIndex == 0:
            return True
        else:
            return False
```

How to use the class:
```
from stack import Stack
myStack = Stack(5) #Stack with item limit of 5
myStack2 = Stack(0) #Stack without a limit (0 == no limit)

```

---

### Post by lnostdal on 2008-02-21
here is one in Common Lisp

```

;; http://ubuntuforums.org/showthread.php?t=702690

(defpackage :stack
  (:use cl)
  (:shadow :pop :push))
(in-package :stack)


(defmacro with-gensyms (syms &body body)
  `(let ,(mapcar (lambda (s)
                   `(,s (gensym ,(concatenate 'string (princ-to-string s) "-"))))
                 syms)
     ,@body))


(defmacro push (value stack)
  "Push `value' onto `stack'."
  (with-gensyms (mstack)
    `(let ((,mstack ,stack))
       (setq ,stack (cons ,value ,mstack)))))


(defmacro pop (stack)
  "Pop value from stack and return the popped value."
  (with-gensyms (mstack)
    `(let ((,mstack ,stack))
       (prog1 (first ,mstack)
         (setq ,stack (rest ,mstack))))))


(defun top (stack)
  "Return top value from stack. Does not pop it."
  (first stack))



#|

STACK> (let ((stack (list 2 3)))
         (push 1 stack)
         (values (list (pop stack) stack)
                 (top stack)))
(1 (2 3))
2

STACK> (macroexpand-1 '(push 1 stack))
(LET ((#:MSTACK-2036 STACK))
  (SETQ STACK (CONS 1 #:MSTACK-2036)))
T

STACK> (macroexpand-1 '(pop stack))
(LET ((#:MSTACK-2037 STACK))
  (PROG1 (FIRST #:MSTACK-2037) (SETQ STACK (REST #:MSTACK-2037))))
T
|#

```

---

### Post by sznurek on 2008-02-21
Here is one in C++:
[PHP]
#include <vector>
#include <iostream>
#include <cstdlib>

using namespace std;

template <class T> 
class Stack;

template <class T> 
ostream& operator<<(ostream&, const Stack<T>&); 

template <class T>
struct Node {
    T object;
    struct Node* next;
};

template <class T>
class Stack {
    public:
        Stack();
        ~Stack();
        Stack<T>& push(T);
        T pop();
        T peek();
        int length();
        friend ostream& operator<< <>(ostream&, const Stack<T>&);
    private:
        struct Node<T>* top;
        int _length; 
};

template <class T>
Stack<T>::Stack() {
    this->top = NULL;
    this->_length = 0;
}

template <class T>
Stack<T>::~Stack() {
    struct Node<T>* current = this->top;
    struct Node<T>* next = this->top;
    while(current != NULL) {
        next = current->next;
        delete current;
        current = next;
    }
}

template <class T>
Stack<T>& Stack<T>::push(T what) {
    struct Node<T>* _new = new struct Node<T>;
    _new->object = what;
    _new->next = this->top;
    this->top = _new;
    this->_length++;
    return *this;
}

template <class T>
T Stack<T>::pop() {
    if(this->_length == 0) throw "Empty";
    struct Node<T>* object = this->top;
    this->top = this->top->next;
    T copy = object->object;
    delete [] object;
    this->_length--;
    return copy;
}

template <class T>
T Stack<T>::peek() {
    return this->top->object;
}

template <class T>
int Stack<T>::length() {
    return this->_length;
}

template <class T>
ostream& operator<<(ostream& os, const Stack<T>& s) {
    os << "[";
    struct Node<T>* current = s.top;
    while(current != NULL) {
        os << current->object << ", ";
        current = current->next;
    }
    os << "\b\b]";
    return os;
}

int main(void) {
    Stack<int> stos;
    stos.push(10).push(20).push(30);
    cout << stos << endl;
    int poped = stos.pop();
    cout << stos << endl;
    cout << "Poped value: " << poped << endl;
    cout << "Length: " << stos.length() << endl;
}

[/PHP]

---

### Post by aks44 on 2008-02-21
> **sznurek said:**
> Here is one in C++

A few remarks:

[list][*]**Correctness:** in pop() you delete[] a new'ed object (not a new[]'ed one, mind you).
[*]**Correctness:** both peek() and pop() will segfault if called on an empty stack.
[*]**Correctness:** both push() and pop() will memleak if T's operator=() throws (push) or if T's copy constructor throws (pop).
[*]**Style:** typically, template classes are defined in header files, but you use **using namespace std;**...
[*]**Style:** for better encapsulation, Node should be a private sub-class of Stack.[/list]

I'm sorry to put it bluntly, but this class is not usable as-is.

---

### Post by sznurek on 2008-02-21
> **aks44 said:**
> A few remarks:

[list][*]**Correctness:** in pop() you delete[] a new'ed object (not a new[]'ed one, mind you).
[*]**Correctness:** both peek() and pop() will segfault if called on an empty stack.
[*]**Correctness:** both push() and pop() will memleak if T's operator=() throws (push) or if T's copy constructor throws (pop).
[*]**Style:** typically, template classes are defined in header files, but you use **using namespace std;**...
[*]**Style:** for better encapsulation, Node should be a private sub-class of Stack.[/list]

I'm sorry to put it bluntly, but this class is not usable as-is.

OK, I'm a beginner in C++ :)

But:
For first point: Before I create a copy of cargo(Node->object) - is this correct?
Second: Edited.
Third: Ouh, I cannot correct it now (i must read for this) :)
Style-point: To be corrected too.

Can I please You to correct my code? I will be thankful.

Ps. Sorry for my English :(

---

### Post by aks44 on 2008-02-21
> **sznurek said:**
> I'm a beginner in C++ :)
No problem, let's review my remarks a bit more in detail then... :)

1) Read about new / delete vs. new[] / delete[]. The fact that delete[] seems to work correctly with a new'ed object is only chance.
2) You corrected pop() but not peek()... By the way it is usually better to throw an object rather than a scalar type. See eg. std::runtime_error.
3) This is a problem of exception-safety. "Funnily" enough, this challenge is labelled "easy" but a well known C++ guru's equivalent article has a difficulty of 9/10. If you're a beginner, don't expect to understand that too quickly. When the challenge is over I'll give you interesting links. ;)


> **sznurek said:**
> Can I please You to correct my code? I will be thankful.
I'm sorry but I won't tell you here how to correct those errors, as this is a Challenge (kind of a contest)... That would be unfair to other people.
The hints I gave you should be enough to keep you busy for a moment. Just don't feel bad if you can't make sense of everything right now, C++ is a complex language that requires much practice.

Again, when this challenge is over we can discuss those topics more in-depth if you're still interested. :)

---

### Post by ruy_lopez on 2008-02-21
A Obj-C version. Obj-C is not my strong suit, so you'll have to endure my clumsiness. I thought it might make a nice alternative.

Stack.h
```

#import <objc/Object.h>
#import <stdio.h>
#import <stdlib.h>

#define STACKDEPTH 1024
#define MXLEN 1024

@interface Stack : Object
{
	id oarray[STACKDEPTH];
	int refcount;
}
- (Stack *) initWith;
- (int) getRef;
- (id) getTop;
- (void) push: (id) object;
- (id) pop;
@end

@interface ObjInt: Stack
{
	int value;
}
- (id) setVal: (int) val;
- (int) getVal;
- (void) print;
@end

@interface ObjStr: Stack
{
	char value[MXLEN];
}

- (id) setVal: (char *) val;
- (char *) getVal;
- (void) print;
@end

@interface ObjDouble: Stack
{
	double value;
}
- (id) setVal: (double) val;
- (double) getVal;
- (void) print;
@end

```

Stack.m
```

#import "Stack.h"

@implementation Stack

- (Stack *) initWith
{
	self = [super init];
	if (self)
		refcount = 0;
	return self;
}

- (int) getRef
{
	return refcount;
}

- (id) getTop
{
        return oarray[refcount - 1];
}

- (void) push: (id) object
{
	if (refcount < STACKDEPTH)
		oarray[refcount++] = [object copy];
	else {
		printf("stack busted\n");
		exit(1);
	}
}

- (id) pop
{
        id object;
        object = [oarray[--refcount] copy];
	[oarray[refcount] free];
        return object;
}
@end

@implementation ObjInt
- (id) setVal: (int) val
{
	value = val;
	return self;
}

- (int) getVal
{
	return (value);
}

- (void) print
{
	printf("%d\n", [self getVal]);
}
@end

@implementation ObjStr
- (id) setVal: (char *) val
{
        memset(value, 0, sizeof(value));
        if ((strlen(val)) < MXLEN)
                strncpy(value, val, strlen(val));
        else /* truncate */
                strncpy(value, val, MXLEN);
	return self;
}

- (char *) getVal
{
	return (value);
}

- (void) print
{
	printf("%s\n", [self getVal]);
}
@end

@implementation ObjDouble
- (id) setVal: (double) val
{
	value = val;
	return self;
}

- (double) getVal
{
	return (value);
}

- (void) print
{
	printf("%f\n", [self getVal]);
}
@end

```

main.m
```

#include "Stack.h"

int main(int argc, char *argv[])
{
	ObjInt		*oInt;
	ObjStr		*oStr;
	ObjDouble	*oDble;
	Stack		*oStack;
        id thing;
        char buf[1024];
	int i;
        double d = 0;

	oStack 	= [[Stack alloc] initWith];
	oInt	= [[ObjInt alloc] init];
	oStr	= [[ObjStr alloc] init];
	oDble = [[ObjDouble alloc] init];
	

	for (i = 1; i < 5; i++) {
		[ oStack push: [ oInt setVal: i ]];
	}

	[ oStack push: [ oStr setVal: "(integers)" ]];

	for (i = 5; i < 10; i++) {
		snprintf(buf, sizeof(buf), "'%d string'", i);
		[ oStack push: [ oStr setVal: buf ]];
	}


	[ oStack push: [ oStr setVal: "(strings)" ]];

	while ([ oStack getRef ] > 0)
		[[ oStack pop ] print ];


	for (d = 0; d < 1; d += .1) {
		[ oStack push: [ oDble setVal: d ]];
	}

	[ oStack push: [ oStr setVal: "(doubles)" ]];

	d = 0;
	while ([ oStack getRef ] > 0) {
		thing = [ oStack getTop ];
		if ([ thing isKindOf: [ ObjDouble class ]]) {
			oDble = [ oStack pop ];
			d += [ oDble getVal ];
			[ oDble print ];
		}
		else
			[[ oStack pop ] print ];	
	}

	[ oStack push: [ oDble setVal: d ]];
	[ oStack push: [ oStr setVal: "========" ]];
	[ oStack push: [ oStr setVal: "double sum" ]];

	[[ oStack pop ] print ];
       	[[ oStack pop ] print ];	
	[[ oStack pop ] print ];

	[ oInt free ];
	[ oStr free ];
        [ oDble free ];
	[ oStack free ];

	return 0;
}

```

---

### Post by Wybiral on 2008-02-21
> **aks44 said:**
> 3) This is a problem of exception-safety. "Funnily" enough, this challenge is labelled "easy" but a well known C++ guru's equivalent article has a difficulty of 9/10. If you're a beginner, don't expect to understand that too quickly. When the challenge is over I'll give you interesting links. ;)

The stack ADT plays a vital role in a number of algorithms, knowing how to implement them yourself helps new programmers to grasp the concept better. It's "easy" depending on the language you choose, IMO very few worth-while problems have an "easy" solution in C++ (that is, if you want to do them generically, safely, and correctly). Before that's interpreted as bait, I'm not saying C++ is an inevitably hard language (I'm thinking that, but I'm not saying that :) ), just that it usually requires more thought and time than some other languages.

> **aks44 said:**
> I'm sorry but I won't tell you here how to correct those errors, as this is a Challenge (kind of a contest)... That would be unfair to other people.

It is a challenge, but it's also an opportunity to learn new things. So I agree that giving the source code is cheating, but definitely do post any further info you have when the challenge is over.

---

### Post by aks44 on 2008-02-21
> **Wybiral said:**
> I agree that giving the source code is cheating, but definitely do post any further info you have when the challenge is over.

That was my intention. :)

I have tons of links at hand on that topic, and a very straightforward implementation that is not *that much* different from sznurek's. The difference is only a few details, but they matter a lot. ;)

We'll see that next Thursday...

---

### Post by happysmileman on 2008-02-21
How long do these challenges last, and will they still be kept here after they're finished, as ideas for people to program?

It'd be nice to have a thread with just the past challenges if these continue.

---

### Post by Wybiral on 2008-02-21
> **happysmileman said:**
> How long do these challenges last, and will they still be kept here after they're finished, as ideas for people to program?

It'd be nice to have a thread with just the past challenges if these continue.

The thread will stay open for discussion, but I'm going to pick a winner on Wednesday (the 27th), then that person gets to decide next weeks challenge (and so on).

---

### Post by Lux Perpetua on 2008-02-21
It's unclear whether it's really useful to implement a stack in PostScript, since if you're already in PostScript, you might as well just use the operand stack, right? I did it anyway: ```
%!

% - stack <stack>
/Stack { [] } bind def

% <stack> empty bool
/Empty { length 0 eq } bind def

% <stack> <item> push <stack>
/Push { [3 1 roll exch aload pop] } bind def

% <stack> pop <stack> <item>
/Pop { [exch aload pop counttomark 1 sub array astore
    exch 3 -1 roll pop } bind def

% <stack> top <item>
/Top { 0 get } bind def
```Notes:
[list][*]This stack can hold anything that PostScript can represent. 
[*]In this implementation, updating a stack via Push or Pop is *nondestructive*; i. e., operations that "change" a stack actually do so by returning a modified stack. 
[*]I don't normally capitalize the names of functions, but PostScript already has an operator named **pop**, which I definitely do not want to redefine, so I had to name my "pop" function something else. I capitalized the rest of the names for consistency.
[*]There is no error checking; if you Top or Pop an empty stack, the interpreter will unceremoniously generate a **rangecheck** error.
[*]My code uses the PostScript operand stack, which no PostScript code can avoid. However, that stack is independent of the stack implemented here. 
[/list]

---

### Post by themusicwave on 2008-02-21
After some thought I realized python does have pointers in a way.  Basically references are pointers in a sense, so I exploited that to make my solution.

I took and object Oriented approach, first I implemented a Node class with data and previous and next pointers.  

Once I had the nodes I then built a LinkedList class that is essentially a doubly linked list.  Items can be added, removed or viewed from either the head or tail.  The linked list is essentially a bunch of nodes linked together.

Finally I implemented a Stack class using my LinkedList.  It has push, pop, and peak(view top). It can store values of any type.

Just for fun I also implemented a Queue with enqueue, dequeue, and front(look at front of queue).  It can store values of any type.

The thing I like about this design is all the elements are reusable.  The node class could be used to build a Binary tree for instance(although next and prev would need to be renamed left and right).  
Also, The linkedlist was used twice to make both a stack and a queue.  It also is valuable on it's own.  

Node.py:
[PHP]
#Node.py
#Author Jon Paris
#Created On: 2/21/08
#Description:  A generic node object that contains data
#and a pointer next and prev to another node.  A basic building block for
#linked lists, trees, etc.

class Node:
    
    #create a blank Node
    def __init__(self):
        self._data = None
        self._next = None
        self._prev = None
    
    #Set the value this node holds
    def setData(self,value):
        self._data = value
       
    #retrieve the value this node holds 
    def getData(self):
        return self._data
    
    #Get a pointer to the node before this one
    def getPrev(self):
        return self._prev
    
    #Set the pointer to the node before this one
    def setPrev(self,node):
        self._prev = node
    
    #Get a pointer to the node after this one
    def getNext(self):
        return self._next
    
    #Set the pointer to the node after this one
    def setNext(self,node):
        self._next = node
[/PHP]

LinkedList.py:
[PHP]
#LinkedList.py
#Author Jon Paris
#Created On: 2/21/08
#Description: A doubly linked list.  Values can be added/removed
#From both the head and tail.

from Node import Node

class LinkedList:
    
    #Create and empty LinkedList
    def __init__(self):
        self._size=0
        self._headPointer = Node()
        self._tailPointer = self._headPointer
        
    #Adds to the head or front of the LinkedList    
    def addHead(self,value):
        toAdd = Node()
        toAdd.setData(value)
        toAdd.setNext(self._headPointer)
        toAdd.setPrev(None)
        self._tailPointer = self._headPointer
        self._headPointer = toAdd
        
        #First item, it is both head and tail
        if(self._size == 0):
            self._tailPointer = toAdd
        
        self._size+=1
        
    #Adds to the tail or end of the LinkedList        
    def addTail(self,value):
        
        toAdd = Node()
        toAdd.setData(value)
        toAdd.setNext(None)
        toAdd.setPrev(self._tailPointer)
        self._tailPointer.setNext(toAdd)
        
        self._tailPointer = toAdd
        
         #First item, it is both head and tail
        if(self._size == 0):
            self._headPointer = toAdd
        
        self._size+=1
    
    #Remove from the head, returns None if the list is empty          
    def removeHead(self):

        #Don't fall off the end of the list
        if (not self._headPointer == None) and (self._size >0):
            next = self._headPointer.getNext()
            val = self._headPointer.getData()
            self._headPointer = next
            self._size-=1
        else:
            val = None
        
        return val
    
    #Remove from the tail, returns None if the list is empty          
    def removeTail(self):
           #Don't fall off the start of the list
           if (not self._size == None) and (self._size >0) :
               prev = self._tailPointer.getPrev()
               val = self._tailPointer.getData()
               self._tailPointer = prev
               self._size-=1
           else:
               val = None
               
           return val
       
    #simply return the value at the head, don't change/remove it       
    def getHeadValue(self):   
        
        if(not self._headPointer == None):
            val = self._headPointer.getData()
        else:
            val = None
        
        return val
    
     #simply return the value at the tail, don't change/remove it       
    def getTailValue(self):
        
        if(not self._tailPointer == None):
            val =self._tailPointer.getData()
        else:
            val = None
            
        return val
    
    #Returns the number of elements in the list
    def getSize(self):
        return self._size
[/PHP]


Stack.py:
[PHP]
#Stack.py
#Author Jon Paris
#Created On: 2/21/08
#Description: A simple FILO Stack

from LinkedList import LinkedList

class Stack:
    
    def __init__(self):
        self._linkedList = LinkedList()
    
    def push(self,value):
        self._linkedList.addHead(value)
        
    def pop(self):
        return self._linkedList.removeHead()
    
    def peak(self):
        return self._linkedList.getHeadValue()
    
    def getSize(self):
        return self._linkedList.getSize()
[/PHP]

Queue.py
[PHP]
#Queue.py
#Author Jon Paris
#Created On: 2/21/08
#Description: A simple FIFO queu.

from LinkedList import LinkedList

class Queue:
    
    def __init__(self):
        self._linkedList = LinkedList()
    
    def enqueue(self,value):
        self._linkedList.addTail(value)
        
    def dequeue(self):
        return self._linkedList.removeHead()
    
    def front(self):
        return self._linkedList.getHeadValue()
    
    def getSize(self):
        return self._linkedList.getSize()
[/PHP]

Test.py:
[PHP]
#Test.py
#Author Jon Paris
#Created On: 2/21/08
#Description: Simply demonstrates that Test and Queue Work.

from Queue import Queue
from Stack import Stack


q = Queue()

q.enqueue(1)
q.enqueue(2.5)
q.enqueue("I Work")
q.enqueue([1,2,3])

print "Queue"
print "Front ", q.front()
print q.dequeue()
print q.dequeue()
print q.dequeue()
#enqueue in the middle of the dequeues to show it works
q.enqueue(99)
print q.dequeue()
print q.dequeue()
print q.dequeue()

print "Stack"

s = Stack()

s.push(1.5)
s.push(2)
s.push("I Work")
s.push([1,2,3])

print "Peak: ", s.peak()
print s.pop()
print s.pop()

#push in the middle of the pops to show it works
s.push(99)
print s.pop()
print s.pop()
print s.pop()
print s.pop()
[/PHP]

Output from test.py:
> 
Queue
Front  1
1
2.5
I Work
[1, 2, 3]
99
None

Stack
Peak:  [1, 2, 3]
[1, 2, 3]
I Work
99
2
1.5
None
Peak  100
100



---

### Post by foo-bar on 2008-02-21
Here's a ruby stack class implementing push, pop, and top.  It is also independent of the type of data being stored.

```

class Stack
  # for testing, allow access to the @stack member
  attr_accessor :stack

  # Allow a stack with an arbitrary number of items
  def initialize(limit)
    @top = 0
    @limit = limit
    @stack = []
  end
  
  def push(item)
    @top = @top + 1
    if @top > @limit
      raise "Too many items on the stack!"
    end
    @stack[@top] = item
  end
  
  def pop()
    if @top == 0
      raise "There are no items on the stack!"
    end
    ret = @stack[@top]
    @stack[@top] = nil
    @top = @top - 1
    ret
  end
  
  def top()
    @stack[@top]
  end
end

```

It may not be perfect ruby style but it should work :)

---

### Post by sznurek on 2008-02-23
Corrected(?) C++ version:
Stack.h:
[PHP]
#ifndef STACK_H_
#define STACK_H_

#include <iostream>

template <class T> 
class Stack;

template <class T> 
std::ostream& operator<<(std::ostream&, const Stack<T>&); 

template <class T>
class Stack {
    public:
        Stack();
        ~Stack();
        Stack<T>& push(T);
        T pop();
        T peek();
        int length();
        friend std::ostream& operator<< <>(std::ostream&, const Stack<T>&);
        struct Node {
            T object;
            struct Stack<T>::Node* next;
        };
    private:
        struct Stack<T>::Node* top;
        int _length;
};

#endif
[/PHP]

Stack.cpp:
[PHP]

#include <iostream>
#include <stdexcept>
#include <cstdlib>

#include "stack.h"

template <class T>
Stack<T>::Stack() {
    this->top = NULL;
    this->_length = 0;
}

template <class T>
Stack<T>::~Stack() {
    struct Stack<T>::Node* current = this->top;
    struct Stack<T>::Node* next = this->top;
    while(current != NULL) {
        next = current->next;
        delete current;
        current = next;
    }
}

template <class T>
Stack<T>& Stack<T>::push(T what) {
    struct Stack<T>::Node* _new = new struct Stack<T>::Node;
    try {
        _new->object = what;
    } catch(...) {
        delete _new;
        throw;
    }
    _new->next = this->top;
    this->top = _new;
    this->_length++;
    return *this;
}

template <class T>
T Stack<T>::pop() {
    if(this->_length == 0) throw std::runtime_error("Empty stack");
    struct Stack<T>::Node* object = this->top;
    /* When below instruction throws exception, function returns, right? */
    T copy = object->object;
    this->top = this->top->next;
    delete object;
    this->_length--;
    return copy;
}

template <class T>
T Stack<T>::peek() {
    if(this->_length == 0) throw std::runtime_error("Empty stack");
    return this->top->object;
}

template <class T>
int Stack<T>::length() {
    return this->_length;
}

template <class T>
std::ostream& operator<<(std::ostream& os, const Stack<T>& s) {
    os << "[";
    struct Stack<T>::Node* current = s.top;
    while(current != NULL) {
        os << current->object << ", ";
        current = current->next;
    }
    if(s._length > 0)
        os << "\b\b]";
    return os;
}

int main(void) {
    Stack<int> stos;
    stos.push(10).push(20).push(30);
    std::cout << stos << std::endl;
    int poped = stos.pop();
    std::cout << stos << std::endl;
    std::cout << "Poped value: " << poped << std::endl;
    std::cout << "Length: " << stos.length() << std::endl;
    try {
        stos.pop();
        stos.pop();
        stos.pop();
    } catch(std::runtime_error& err) {
        std::cerr << "Error - " << err.what() << std::endl;
    }
    Stack<int*> stos2;
    int* one = new int(1);
    int* two = new int(2);
    stos2.push(one).push(two);
    std::cout << "Peek(): " << *(stos2.peek()) << std::endl;
    *two = 123;
    std::cout << "Peek() when modified: " << *(stos2.peek()) << std::endl;
}
[/PHP]

---*** EDIT ***---
Last change:
[PHP]
#ifndef STACK_H_
#define STACK_H_

#include <iostream>
#include <cstdlib>
#include <stdexcept>

template <class T> 
class Stack;

template <class T> 
std::ostream& operator<<(std::ostream&, const Stack<T>&); 

template <class T>
class Stack {
    public:
        Stack() : _length(0), top(NULL) {}
        
        ~Stack() {
            struct Stack<T>::Node* current = this->top;
            struct Stack<T>::Node* next = this->top;
                while(current != NULL) {
                    next = current->next;
                    delete current;
                    current = next;
            }
        }
        
        Stack<T>& push(T what) {
            struct Stack<T>::Node* _new = new struct Stack<T>::Node;
            try {
                _new->object = what;
            } catch(...) {
                delete _new;
                throw;
            }
            _new->next = this->top;
            this->top = _new;
            this->_length++;
            return *this;
        }
        
        T pop() {
            if(this->_length == 0) throw std::runtime_error("Empty stack");
            struct Stack<T>::Node* object = this->top;
            T copy = object->object;
            this->top = this->top->next;
            delete object;
            this->_length--;
            return copy;
        }
        
        T peek() {
            if(this->_length == 0) throw std::runtime_error("Empty stack");
            return this->top->object;
        }
        
        int length() {
            return this->_length;
        }
        
        friend std::ostream& operator<< <>(std::ostream&, const Stack<T>&);
        
        struct Node {
            T object;
            struct Stack<T>::Node* next;
        };
        
    private:
        struct Stack<T>::Node* top;
        int _length;
};

template <class T>
std::ostream& operator<<(std::ostream& os, const Stack<T>& s) {
    os << "[";
    struct Stack<T>::Node* current = s.top;
    while(current != NULL) {
        os << current->object << ", ";
        current = current->next;
    }
    if(s._length > 0)
        os << "\b\b]";
    return os;
}

#endif
[/PHP]

---

### Post by Lster on 2008-02-23
Here is my solution in C:

[PHP]

/*
	Stack.c
	By Lster
	
    This program is free software: you can redistribute it and/or modify
    it under the terms of the GNU General Public License as published by
    the Free Software Foundation, either version 3 of the License, or
    (at your option) any later version.

    This program is distributed in the hope that it will be useful,
    but WITHOUT ANY WARRANTY; without even the implied warranty of
    MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
    GNU General Public License for more details.

    You should have received a copy of the GNU General Public License
    along with this program.  If not, see <http://www.gnu.org/licenses/>.
*/

// Required libraries.
#include "stdlib.h"
#include "string.h"

// Tests Stack!
#define TEST_STACK
#define STACK_LIBRARY

#ifdef TEST_STACK
#include "stdio.h"
#endif

// Stack elements should generally be changed with the Stack_* methods, but you
// can easily access other information using the following structure variables.
// For example, Stack -> Top is the length of the stack...
typedef struct Stack
{
	void * Memory;				// The memory that is used to store the stack's
								// data.
	unsigned int Length;		// The current number of elements in the stack.
	unsigned int ElementSize;	// The size (in bytes) of each element.
	unsigned int Increment;		// The amount to increase the length if all of
								// currently allocated memory is used.
	unsigned int Top;			// A relative pointer to the top of the stack.
} Stack;

// Creates a new stack with the element size (b), number of elements, and the
// of elements to increment if space is ran out of.
Stack * Stack_Create ( unsigned int ElementSize , unsigned int InitialElements
					   , unsigned int Increment )
{
	if ( Increment == 0 || InitialElements == 0 || ElementSize == 0 )
		return 0;
	
	Stack * Struct = ( Stack * ) malloc ( sizeof ( Stack ) );
	
	if ( Struct == 0 )
		return 0;
	
	Struct -> Length = InitialElements;
	Struct -> ElementSize = ElementSize;
	Struct -> Memory = malloc ( InitialElements * ElementSize );
	Struct -> Top = 0;
	
	if ( Struct -> Memory == 0 )
	{
		free ( Struct );
		return 0;
	}
	
	return Struct;
}

// Frees the stack and all memory it currently holds.
void Stack_Free ( Stack * Struct )
{
	if ( Struct == 0 )
		return;
	
	if ( Struct -> Memory != 0 )
		free ( Struct -> Memory );
	free ( Struct );
}

// Pushes data into a stuct assuming that Data is a pointer to a block of memory
// at least as long as the stack's element size.
int Stack_Push ( Stack * Struct , void * Data )
{
	if ( Struct == 0 )
		return 0;
	
	if ( Struct -> Top >= Struct -> ElementSize )
	{
		Struct -> ElementSize += Struct -> Increment;
		Struct -> Memory = realloc ( Struct -> Memory , Struct -> ElementSize );
		
		if ( Struct -> Memory == 0 )
		{
			// Kill the stack off - there is not enough memory.
			free ( Struct );
			return 0;
		}
	}
	
	memcpy ( Struct -> Memory + Struct -> Top * Struct -> ElementSize ,
			 Data , Struct -> ElementSize );
	Struct -> Top ++;
	
	return 1;
}

// Pops an element off the stack and copies it to the memory pointed to by
// Return. Return should be at least as long as the stack's element size. This
// removes the last element.
int Stack_Pop ( Stack * Struct , void * Return )
{
	if ( Struct == 0 || Struct -> Top == 0 )
		return 0;
	
	Struct -> Top --;
	memcpy ( Return , Struct -> Memory + Struct -> Top * Struct -> ElementSize ,
			 Struct -> ElementSize );
	
	return 1;
}

// Identical to Stack_Pop except it does not remove the last element from the
// stack.
int Stack_Top ( Stack * Struct , void * Return )
{
	if ( Struct == 0 || Struct -> Top == 0 )
		return 0;
	
	memcpy ( Return ,
			 Struct -> Memory + ( Struct -> Top - 1 ) * Struct -> ElementSize ,
			 Struct -> ElementSize );
	
	return 1;
}


#ifdef TEST_STACK

// Quick test!
int main ( void )
{
	Stack * Test = Stack_Create ( sizeof ( int ) , 10 , 5 );
	
	int * A = malloc ( sizeof ( int ) );
	int * B = malloc ( sizeof ( int ) );
	
	* A = 6;
	printf ( "\nPushing %i.\n" , * A );
	Stack_Push ( Test , A );
	
	* A = 7;
	printf ( "Pushing %i.\n" , * A );
	Stack_Push ( Test , A );
	
	Stack_Pop ( Test , B );
	printf ( "Pop received %i.\n" , * B );
	
	Stack_Top ( Test , B );
	printf ( "Top found %i.\n" , * B );
	
	Stack_Pop ( Test , B );
	printf ( "Pop received %i.\n" , * B );
	
	if ( Stack_Pop ( Test , B ) == 0 )
		printf ( "Pop failed!\n\n" );
	else
		printf ( "Pop received %i.\n\n" , * B );
	
	Stack_Free ( Test );
	
	return 0;
}

#endif
[/PHP]

It is fully generic and has all the functions specified. I haven't tested it a lot, but it should be *reasonably* stable. ;)

EDIT: OK. I added some extra checks for safety. It is a bit better now - but probably not perfect!

---

### Post by andrewjoy on 2008-02-23
Nice work guys, my knowlage is not realy up to this level yet but i would be realy intrested in seeing a sollution to this problem in java

---

### Post by Lster on 2008-02-23
You might be interested in this:

[http://java.sun.com/javase/6/docs/api/java/util/Stack.html](http://java.sun.com/javase/6/docs/api/java/util/Stack.html)

Although it's use is disallowed in this challenge!

---

### Post by andrewjoy on 2008-02-23
Yes i know about the stack class as i have just used it in my last program to create an in tray.

I was wondering how it would be implimented in java without the use of the stack class.

As its not part of the challange to use a pre build class :D. I asume that it would be ok in the challange to extend vector

```

import java.util.Vector

class myclass extends Vector
{
//code//
}

```

---

### Post by aks44 on 2008-02-24
Here's my submission. Thanks to [Strike>>]("http://ubuntuforums.org/member.php?u=63133") for the suggestion of doing it in ASM. ;)

[LIST][*] **gas_stack_asm.s**: native ASM library (x86 32-bits)
[*] **gas_stack_c.c/h**: C bindings
[*] **gas_stack_example.c**: usage example in C
[*] **test.sh**: compile and run the C example[/LIST]
I know the C bindings are a mess, but I hacked them just for the sake of it (plus it's my first try at Linux / AT&T ASM, so please bear with me).

:)

---

### Post by LaRoza on 2008-02-24
> **aks44 said:**
> Here's my submission. Thanks to [Strike>>]("http://ubuntuforums.org/member.php?u=63133") for the suggestion of doing it in ASM. ;)

[LIST][*] **gas_stack_asm.s**: native ASM library (x86 32-bits)
[*] **gas_stack_c.c/h**: C bindings
[*] **gas_stack_example.c**: usage example in C
[*] **test.sh**: compile and run the C example[/LIST]
I know the C bindings are a mess, but I hacked them just for the sake of it.

:)

Good work.

---

### Post by aks44 on 2008-02-24
> **sznurek said:**
> Corrected(?) C++ version:

Congrats, you got it right, save for a few minor details. Your new code is correct and exception-safe, as far as I can tell. :D

**But**, definition of the template members should be in the header file, not in the cpp file. What if you create another .cpp and include stack.h? Ideally it should work, but here it doesn't.

There are also other points that could be enhanced (mainly style details) but let's save that discussion for when the challenge is over, OK?

Anyway, good work in so little time for a self admitted beginner. :D


And to answer your question in the comments:
**/* When below instruction throws exception, function returns, right? */**
"Return" wouldn't be the exact word. The rest of the function isn't executed, and neither is any other code until the exception is caught in a catch() handler.



EDIT:
> **LaRoza said:**
> Good work.
Better see the messy code before blindly congratulating me... ;) Thanks anyway. :)

---

### Post by Wybiral on 2008-02-24
lol, being the judge makes me feel left out :(

Is it legal for me to submit something if I vow not to choose my own submission? How about a language I don't use, like Java?

---

### Post by LaRoza on 2008-02-24
> **Wybiral said:**
> lol, being the judge makes me feel left out :(

Is it legal for me to submit something if I vow not to choose my own submission? How about a language I don't use, like Java?

You can have the community vote (publically) and I can add the poll for you if you want.

I don't know if you want that, but it is an option.

---

### Post by Wybiral on 2008-02-24
> **LaRoza said:**
> You can have the community vote (publically) and I can add the poll for you if you want.

I don't know if you want that, but it is an option.

I mostly just don't want to take away anyones idea (there's only so many ways you can make a stack, so me posting would remove an option for someone). But I have a better idea... I know a way they nobody would possibly use, so I'm going to hack that out :)

I don't want to win because I want to participate in the next challenge, so I wont count my submission.

---

### Post by aks44 on 2008-02-24
> **Wybiral said:**
> Is it legal for me to submit something if I vow not to choose my own submission?
Seems fair, why wouldn't you have the right to have fun too? :p

> **Wybiral said:**
> How about a language I don't use, like Java?
Suggestion for more spice: use generics... ;)

---

### Post by sznurek on 2008-02-24
> **aks44 said:**
> Congrats, you got it right, save for a few minor details. Your new code is correct and exception-safe, as far as I can tell. :D

**But**, definition of the template members should be in the header file, not in the cpp file. What if you create another .cpp and include stack.h? Ideally it should work, but here it doesn't.

There are also other points that could be enhanced (mainly style details) but let's save that discussion for when the challenge is over, OK?

Anyway, good work in so little time for a self admitted beginner. :D


Thanks, but I had some experience in other programming languages before (Java, some scripting(Python, Ruby, Php, Bash)) ;)

Currently I'm waiting for [Professional C++]("http://www.amazon.com/Professional-C-Programmer-Nicholas-Solter/dp/0764574841") book - I hope I'll learn a lot :) C++ is confusing language :confused:

I'm waiting for next challenge too :)

BTW - is there any official C++ reference (keywords, STL, I/O)? I already know [www.cppreference.com](www.cppreference.com) and [www.cplusplus.com](www.cplusplus.com) but I have not find, for example, std::numerical_limits on these sites.

---

### Post by Lster on 2008-02-24
[QUOTE=sznurek]I'm waiting for next challenge too :)[/QUOTE]

Once you learn C++, check out this site:

[http://www.cprogramming.com/helpfree.html](http://www.cprogramming.com/helpfree.html)

---

### Post by seventhc on 2008-02-24
> **Tuna-Fish said:**
> So, I needed a stack. That got me thinking, my computer already has a stack, right, so why not use that?

Behold:
[php]
#! /usr/bin/env python
# encoding=utf-8
######################
#Author: Antti-Ville Tuunainen (tuna)
#The Mighty Recursive-Execution-Stack-Based-Stack
#No, I don't usually program like this.
import Queue, thread
def _stack(qin,qout,o):
    while True:
        task = qin.get()
        if task == "push":
            oo = qin.get()
            call = True
        elif task == "pop":
            qout.put(o)
            return
        elif task == "peek":
            qout.put(o)
            call = False
        if (call):
            _stack(qin,qout,oo)
def _stackstart(qin,qout):
    while True:
        _stack(qin,qout,None)
            
class RESBStack():
    def __init__(self):
        self.qin = Queue.Queue()
        self.qout = Queue.Queue()
        self.t = thread.start_new_thread(_stackstart,(self.qin,self.qout))
    def push(self,o):
        self.qin.put("push")
        self.qin.put(o)
    def pop(self):
        self.qin.put("pop")
        return self.qout.get()
    def peek(self):
        self.qin.put("peek")
        return self.qout.get()

if __name__ == "__main__":
    stack = RESBStack()
    stack.push(1)
    stack.push("moi")
    stack.push(True)
    stack.push(3.14)
    print stack.peek()
    print stack.peek()
    print stack.pop()
    print stack.pop()
    stack.push(42)
    print stack.peek()
    print stack.pop()
    
    print stack.pop()
    print stack.pop()
    print stack.pop()
[/php]You know that it's empty when it returns none. Only, 'cos you can push a None, you don't. Ain't life fun?

Oh, and the thread keeps on living until someone calls system.exit.

But hey, why gloss over minor details?
I ran this code, and well,  I have a threading.py script in my home directory and it sort of interfered with this script. lol
I had to move mine to another folder. Otherwise I get errors.

---

### Post by aks44 on 2008-02-24
> **sznurek said:**
> is there any official C++ reference (keywords, STL, I/O)?
THE C++ reference is the [INCITS/ISO/IEC 14882-2003 standard]("http://webstore.ansi.org/RecordDetail.aspx?sku=INCITS/ISO/IEC%2014882-2003"), but it is definitely *not* a learning tool. Just don't bother buying it until you already know a good deal about C++, it is mainly useful for triple-checking specific language & library details.

As far as I'm concerned, I usually use my compiler's STL documentation ([here]("http://gcc.gnu.org/onlinedocs/libstdc++/documentation.html") for G++, see also the "Source-Level Documentation" section near the bottom of that page)

> **sznurek said:**
> I have not find, for example, std::numerical_limits on these sites
It's std::numeric_limits (easily finding such info is where the standard can be useful after all :p) but you're right, it doesn't seem to be on cppreference.com anyway. :)

---

### Post by Jessehk on 2008-02-24
I use [this](http://www.sgi.com/tech/stl/table_of_contents.html) reference for the STL. :)

---

### Post by Wybiral on 2008-02-26
Get your submissions in ASAP, the contest ends tomorrow!

I had a more elaborate system planned that was pretty "off the wall" (I was using some of my JIT compiling routines to create a stack "class" in C, but I got sidetracked with a project I had been working on recently). It was something similar to [this]("http://ubuntuforums.org/showpost.php?p=4227466") (that I posted as a joke) but more elaborate.

Anyway, I decided to go through with the Java as a learning exercise (I'm not a Java programming, in fact, I'm not a big fan of Java at all). Here it is (with generics as suggested):

Stack.java
```
class Node<T> {
	Node<T> parent;
	T value;
	
	Node(Node<T> newParent, T newValue) {
		parent = newParent;
		value = newValue;
	}
}

public class Stack<T> {
	Node<T> node;
		
	void push(T value) {
		node = new Node<T>(node, value);
	}

	T pop() {
		if(node == null) {
			throw new Error("Empty stack operation (pop)");
		} else {
			T value = node.value;
			node = node.parent;
			return value;
		}
	}

	T top() {
		if(node == null) {
			throw new Error("Empty stack operation (top)");
		} else {
			return node.value;
		}
	}
}

```

Test.java
```

public class Test {
	public static void main(String[] args) {
		Stack<String> stack = new Stack<String>();

		stack.push("Hello");
		stack.push("Testing");
		System.out.println(stack.pop());
		System.out.println(stack.pop());

		try {
			System.out.println(stack.pop());
		} catch (Throwable e) {
			System.out.println("Error caught: " + e.getMessage());
		}
	}
}

```

It's a straight-forward nested object implementation. Nothing special here.

---

### Post by pedro_orange on 2008-02-27
Argh where does the time go? It's Wednesday already & I did nothing! 

I am eagrely awaiting the next challenge.

---

### Post by Lster on 2008-02-27
[QUOTE=pedro_orange]Argh where does the time go? It's Wednesday already & I did nothing!

I am eagrely awaiting the next challenge.[/QUOTE]

Tell me about it. I'm glad I got mine done before going back to college - I definitely wouldn't have had time to do it if I had left it any later. Life's such a rush... :)

---

### Post by moma on 2008-02-27
Hello all,

Here is my contribution to this "make a stack" competition. It is written in C. It contains abstract datatypes for Array, List and Red-Black balanced Tree.

[[img]http://bildr.no/thumb/161510.jpeg[/img]](http://bildr.no/view/161510)

0) Browse to [http://www.futuredesktop.org/adt/]("http://www.futuredesktop.org/adt/")  and download [adt-0.1.tar.gz]("http://home.online.no/~osmoma//adt/adt-0.1.tar.gz"). 

1) Unpack the files 

2) Konfigurer og kompiler 
$ cd adt-0.1
$ configure 
$ make 

3) Test  (all three datatypes)
$ cd adt-0.1/test 
$ ./parray_test
$ ./plist_test
$ ./ptree_test

The ptree_test generates some SVG files that illustrate how the tree crows.   (requires the "imagemagick" package")
$ display tree??.svg

Think it as a stack. Use the insert time (yes time) as a key.  Is it possible? 
-------------------------

BTW: Stack in PIR language is rather easy to do.
See: [http://linux1.no/blogg/moma/3231/perl6-boken-ankom-i-dag-holder-meg-opptatt](http://linux1.no/blogg/moma/3231/perl6-boken-ankom-i-dag-holder-meg-opptatt)
[http://www.parrotcode.org/examples/pir.html](http://www.parrotcode.org/examples/pir.html)

---

### Post by Wybiral on 2008-02-27
Well, it's that time and unfortunately I have to pick one of these. And the winner is... [Lsters C implementation]("http://ubuntuforums.org/showpost.php?p=4387723").

Why: The code is well commented, to-the-point (it did exactly what was asked of the challenge), and the use of incremental overallocation is an efficient way to avoid costly memory allocation on each operation.

Python programmers might be interested to know that Pythons list data-type uses a similar method of overallocation to avoid those nasty calls to malloc (which can get quite costly on some systems).

It's up to Lster to pick the next challenge!

Now we can get to the educational side and share links / tips on stack implementation.

---

### Post by Lster on 2008-02-27
You are very kind, Wybiral. Thanks! :) Many of the other implementations were very good though!

Now for a challenge! I'll keep it simple enough for all to attempt it, but with some additions that are a bit more challenging. Expect a challenge in about 20 minutes!

---

### Post by Wybiral on 2008-02-27
> **Lster said:**
>  Expect a challenge in about 20 minutes!

Great! Count me in (it's much funner to participate than to judge).

If I could solve this challenge in my native language, it probably would have looked something like this:

```
class Stack:

    def __init__(self):
        self._node = None

    def push(self, value):
        self._node = (value, self._node)

    def pop(self):
        try:
            value, self._node = self._node
            return value
        except:
            raise IndexError("Empty stack")

    def top(self):
        try:
            return self._node[0]
        except:
            raise IndexError("Empty stack")
```

Essentially the nested object approach (which is common for stacks), but using Pythons tuple so that the first object is the data and the second is the next tuple. The tuple assignment / unpacking syntax of Python makes this incredibly small and readable.

---

### Post by pedro_orange on 2008-02-27
Gz on winning by the way; hope I actually get time to do this new challenge!

Edit: 
Should keep a listing of these in a sticky as a reference. Would be a good set of tasks for new programmers.

---

### Post by Lster on 2008-02-27
[QUOTE=pedro_orange]Should keep a listing of these in a sticky as a reference. Would be a good set of tasks for new programmers.[/QUOTE]

That would be nice if a moderator agrees. :)

---

### Post by Jessehk on 2008-02-27
Congrats on the win. :)

I point this out only so you can improve your program, but you have memory leaks.

```

$ gcc -Wall -Wextra stack.c -o stack
$ ./stack

Pushing 6.
Pushing 7.
Pop received 7.
Top found 6.
Pop received 6.
Pop failed!

$ valgrind ./stack
==5850== Memcheck, a memory error detector.
==5850== Copyright (C) 2002-2007, and GNU GPL'd, by Julian Seward et al.
==5850== Using LibVEX rev 1732, a library for dynamic binary translation.
==5850== Copyright (C) 2004-2007, and GNU GPL'd, by OpenWorks LLP.
==5850== Using valgrind-3.2.3-Debian, a dynamic binary instrumentation framework.
==5850== Copyright (C) 2000-2007, and GNU GPL'd, by Julian Seward et al.
==5850== For more details, rerun with: -v
==5850== 

Pushing 6.
Pushing 7.
Pop received 7.
Top found 6.
Pop received 6.
Pop failed!

==5850== 
==5850== ERROR SUMMARY: 0 errors from 0 contexts (suppressed: 11 from 1)
==5850== malloc/free: in use at exit: 8 bytes in 2 blocks.
==5850== malloc/free: 4 allocs, 2 frees, 68 bytes allocated.
==5850== For counts of detected errors, rerun with: -v
==5850== searching for pointers to 2 not-freed blocks.
==5850== checked 59,164 bytes.
==5850== 
==5850== LEAK SUMMARY:
==5850==    definitely lost: 8 bytes in 2 blocks.
==5850==      possibly lost: 0 bytes in 0 blocks.
==5850==    still reachable: 0 bytes in 0 blocks.
==5850==         suppressed: 0 bytes in 0 blocks.
==5850== Rerun with --leak-check=full to see details of leaked memory.

```

You should either explicitly **free()** *A* and *B*, or add in code to Stack_Free to do it for you, maybe based on a function pointer that can be supplied to the function.

---

### Post by Lster on 2008-02-27
If you look at the LibC Manual, here's what it says about free:

[QUOTE=LibC Manual]Occasionally, free can actually return memory to the operating system and make the process smaller. Usually, all it can do is allow a later call to malloc to reuse the space. In the meantime, the space remains in your program as part of a free-list used internally by malloc.

**There is no point in freeing blocks at the end of a program, because all of the program's space is given back to the system when the process terminates.**[/QUOTE]

Source:
[http://www.gnu.org/software/libc/manual/html_node/Freeing-after-Malloc.html#Freeing-after-Malloc](http://www.gnu.org/software/libc/manual/html_node/Freeing-after-Malloc.html#Freeing-after-Malloc)

---

### Post by ruy_lopez on 2008-02-27
> **Wybiral said:**
> Well, it's that time and unfortunately I have to pick one of these. And the winner is... [Lsters C implementation]("http://ubuntuforums.org/showpost.php?p=4387723").


Good choice. Well documented, nice dynamic implementation, and plenty of whitespace (joke). Congratulations Lster.

---

### Post by LaRoza on 2008-02-27
> **Lster said:**
> That would be nice if a moderator agrees. :)

If there is going to be a series of such challenges, it would be good to have a section in the sticky.

---

### Post by JupiterV2 on 2008-05-19
I know this contest is long over but I decided to noodle around a little bit and see if I could hack something together. I may submit a more complex C++ version later but I wanted to create a minimalist stack implementation that used a simple/traditional linked-list. My aim was more for simple elegance rather than mind-blowing awesome. =)

I can't call it type safe as it relies on the 'user' to properly cast the pointer to the type they desire. I took an approach that would allow someone to store any type of data they want within the stack but leave it up to them to handle the data itself.

stack.h (actual stack code):

[PHP]#ifndef STACK_H
#define STACK_H

#include <assert.h>
#include <stdlib.h>

//*****************************************************************************
// Type Definitions
//*****************************************************************************

typedef void* data_t;

typedef struct Node
{
	data_t data;
	struct Node* next;
} node_t;

typedef struct Stack
{
	node_t* head;
} stack_t;


//*****************************************************************************
// Function Definitions
//*****************************************************************************

void init_stack(stack_t* s)
{
	// initialize head pointer to NULL
	s->head = NULL;
}

void push_stack(stack_t* s, data_t d) 
{
	// constant time: push a new element onto the stack
	node_t* n = (node_t*) malloc( sizeof(node_t) );
	
	assert(n);
		
	n->data = d;
	n->next = s->head;
	s->head = n;
}

data_t pop_stack(stack_t* s)
{
	// constant time: pop (remove) element off the stack and return result
	node_t* n = s->head;
	data_t d;
	
	if( n == NULL ) return NULL;
	
	d = n->data;
	s->head = n->next;
	free(n);
	
	return d;	
}

data_t top_stack(stack_t* s) 
{
	if( s->head == NULL ) return NULL;
	else return s->head->data;
}

unsigned int size_stack(stack_t* s)
{
	// linear time: return size (length) of stack
	node_t* n = s->head;
	int size = 0;
	
	while( n != NULL )
	{
		size++;
		n = n->next;
	}
	
	return size;
}

#endif[/PHP]

main.c (test suite) :
[PHP]#include "stack.h"
#include <stdio.h>

int main()
{
	stack_t s1, s2;
	data_t d;
	
	int x = 0, size = 0;
	char c = 'a';
	
	init_stack(&s1);
	init_stack(&s2);
	
	while( x < 5 )
	{
		d = malloc( sizeof(int) );
		*(int*)d = x++;
		push_stack(&s1, d);
		
		d = malloc( sizeof(char) );
		*(char*)d = c++;
		push_stack(&s2, d);
	}
	
	printf("top = %d\n", *(int*)top_stack(&s1));
	printf("top = %c\n", *(char*)top_stack(&s2));
		
	printf("\nPrinting stack #1:\n");
	x = 0;
	size = size_stack(&s1);
	
	while( x < size ) 
	{
		d = pop_stack(&s1);
		printf("elem = %d\n", *(int*)d);
		free(d);
		
		x++;
	}
	
	printf("\nPrinting stack #2:\n");
	x = 0;
	size = size_stack(&s2);
	
	while( x < size ) 
	{
		d = pop_stack(&s2);
		printf("elem = %c\n", *(char*)d);
		free(d);
		
		x++;
	}
	
	return 0;
}[/PHP]

For fun I thought I would include the valgrind report:
```
==8039== 
top = 4
top = e

Printing stack #1:
elem = 4
elem = 3
elem = 2
elem = 1
elem = 0

Printing stack #2:
elem = e
elem = d
elem = c
elem = b
elem = a
==8039== 
==8039== ERROR SUMMARY: 0 errors from 0 contexts (suppressed: 11 from 1)
==8039== malloc/free: in use at exit: 0 bytes in 0 blocks.
==8039== malloc/free: 20 allocs, 20 frees, 105 bytes allocated.
==8039== For counts of detected errors, rerun with: -v
==8039== All heap blocks were freed -- no leaks are possible.

```

---

### Post by bobbocanfly on 2008-05-19
Was trying to learn object orientation in Python so here is a stupidly OO stack class:

```
#Stupidly Object-Oriented Stack Class
#Copyright (C) David Futcher (bobbo) 2008
#bobbocanfly@gmail.com
#Benefits of doing it this way:
#-Multiple stacks in one controller
#-Easier to add stuff to each stored node like data lengths etc.
#Yes I know raising string exceptions is deprecated but i wanted
#to keep this simple

#Actual stack class
class Stack:
 
    def __init__(self):
        self.stack = [] 

    def addNode(self, data):
        self.stack.insert(len(self.stack) + 1, Node(str(data)))

    def popNode(self):
        try:
            return self.stack.pop().data
        except IndexError:
            return "ERROR: Cannot pop from empty stack"

#Low level data node class, this is a waste of time
class Node:

    def __init__(self, data):
        self.data = data

#Main stack controller class
class StackController:

    def __init__(self):
        self.stacks = {}

    def createStack(self, name):
        if not self.stacks.has_key(name):
            self.stacks[name] = Stack()
            return True
        else:
            raise "StackError", "Stack already exists"           

    def deleteStack(self, name):
        if self.stacks.has_key(name):
            del self.stacks[name]
            return True
        else:
            raise "StackError", "Stack does not exist"     

    def push(self, stack, data):
        if self.stacks.has_key(stack):
            self.stacks[stack].addNode(data)
        else:
            raise "StackError", "Stack does not exist"

    def pop(self, stack):
        if self.stacks.has_key(stack):
            return self.stacks[stack].popNode()
        else:
            raise "StackError", "Stack does not exist"

#Test!
if __name__ == "__main__":
    s = StackController()
    s.createStack("test")
    s.createStack("test2")
    s.push("test", "hello world")
    s.push("test2", "hey!")
    print s.pop("test2")
    print s.pop("test")
```

---

### Post by geirha on 2008-05-19
A simple implementation using arrays in bash:
[php]
#!/bin/bash

declare -a stack

function push() # $1=value
{
    stack=( $1 "${stack[@]}" )
}

function top()
{
    echo "${stack[0]}"
}

function pop()
{
    top
    stack=( "${stack[@]:1}" )
}

function print_stack()
{
    echo "${stack[@]}"
}

#test
push k
push c
push s
pop         # s
top         # c
push a
push t
push s
print_stack # s t a c k
[/php]

---

### Post by AaronMT on 2008-05-19
> **geirha said:**
> A simple implementation using arrays in bash:
[php]
#!/bin/bash

declare -a stack

function push() # $1=value
{
    stack=( $1 "${stack[@]}" )
}

function top()
{
    echo "${stack[0]}"
}

function pop()
{
    top
    stack=( "${stack[@]:1}" )
}

function print_stack()
{
    echo "${stack[@]}"
}

#test
push k
push c
push s
pop         # s
top         # c
push a
push t
push s
print_stack # s t a c k
[/php]

That's cute, I like that one. Good old bash. :)

---

### Post by NathanB on 2008-05-19
I know, Foo-Bar already showed a Ruby stack, but here is a leaner version (I'm forcing myself to learn Ruby).

{ Save as 'something.rb' then type 'ruby something.rb' at the prompt. }
[php]class Mystack

    def initialize

        @items = Array.new
        @count = 0

    end

    def push( item )

        @items[@count] = item
        @count = @count + 1

    end

    def pop

        @count = @count - 1
        temp = @items[@count]
        @items[@count] = nil
        temp

    end

    def top

        @items[@count - 1]

    end

end

numbers = Mystack.new
numbers.push( 90 )
numbers.push( 21 )
numbers.push( 15 )
numbers.push( 96 )
numbers.push( 38 )

i = 1
while i < 6

    puts numbers.pop
    i += 1

end
puts "\n"

strings = Mystack.new
strings.push( "for Ruby!" )
strings.push( "clap" )
strings.push( "Let us" )

puts strings.pop
puts strings.top
puts strings.pop
puts strings.pop
[/php]

Almost makes it look _too_ easy, huh?

Well, what are we gonna use these "home-made" stacks for??  Can we build something useful (er... slightly non-trivial) from these components? One possibility is an Expression Evaluator using the Shunt Algorithm -- you know, given a string such as "8 + 45 * ( 7 / ( 14 - 8 ) ) - 3" return the correct result.

---

### Post by pavel989 on 2008-07-18
i still don't get what a stack is, all i see is either an array or like C++ pointers stuff... 

can anyone englishify this?

---

### Post by lisati on 2008-07-18
It's like a pile of letters (or files or whatever) on your desk - you PUSH the latest letter to arrive onto the top of the stack. When you're ready, you POP the topmost letter off to deal with it.

---

### Post by LaRoza on 2008-07-18
> **pavel989 said:**
> i still don't get what a stack is, all i see is either an array or like C++ pointers stuff... 

can anyone englishify this?

[http://en.wikipedia.org/wiki/Stack_(data_structure)](http://en.wikipedia.org/wiki/Stack_(data_structure))

---

### Post by pavel989 on 2008-07-18
well i got that its like a pile of stuff, but i guess my question shouldlve been, "whys it special?"

the link Loraza, btw somehow got messed up, the last parenthesis isn't included. After lisati, the article made a bit more sense. 

But again, why wouldn't the computer just do stuff in the order its given? And whats the point of a stack?

---

### Post by LaRoza on 2008-07-18
> **pavel989 said:**
> well i got that its like a pile of stuff, but i guess my question shouldlve been, "whys it special?"
It isn't special. 

> 
the link Loraza, btw somehow got messed up, the last parenthesis isn't included. After lisati, the article made a bit more sense. 
The forum software does that when a URI contains a ().

> 
But again, why wouldn't the computer just do stuff in the order its given? And whats the point of a stack?

The stack is how a computer works. It is a way of representing data. See my site and the RPN calculator. Try to program that without a stack!

---

### Post by pavel989 on 2008-07-19
> **LaRoza said:**
> 
The stack is how a computer works. It is a way of representing data. See my site and the RPN calculator. Try to program that without a stack!

are you saying that a computer does math through RPN? if so, I now see the idea and usefullness behind it

---

### Post by LaRoza on 2008-07-19
> **pavel989 said:**
> are you saying that a computer does math through RPN? if so, I now see the idea and usefullness behind it

Most calculators (and such apps) use RPN internally.

Look at the code for it, and you'll see how it works.

---

### Post by pavel989 on 2008-07-19
LaRoza saves the day again

---

### Post by Sinkingships7 on 2008-07-19
> **pavel989 said:**
> are you saying that a computer does math through RPN? if so, I now see the idea and usefullness behind it

Imagine a calculator. The one provided with Ubuntu by default, perhaps (gcalctool). When you enter a number, you just "pushed" that number onto the stack (which is programmed into the calculator). Then you enter a arithmetic symbol, like * for multiply. That's added to the stack. Next, you add another number to the stack. When you press enter, the answer is stored into a variable, the stack is flushed (cleared of all data), and the answer is pushed onto the stack. Now you may add to that stack (push), or take away from it (pop). You'll notice that when you press backspace, you only erase one number or symbol at a time. That's because the data that you enter is stored in a stack, otherwise known as a last-in first-out data structure. You can't get rid of something in the middle of the stack without first popping the data on top of it. 

Of course, there's work arounds to that. Like when the user backspaces, copy the stack, delete the number from the original, then add the copied stack back to the original. Viola, fixed stack.

Not completely sure if that's how that specific calculator works, but you get the general idea.

---

### Post by pavel989 on 2008-07-19
well it isn't RPN as LaRoza said, but a varient, interesting stuff. thnx Sinkingships7

---

### Post by Wybiral on 2008-07-19
> **pavel989 said:**
> well it isn't RPN as LaRoza said, but a varient, interesting stuff. thnx Sinkingships7

Most infix expression evaluation is done by converting it to postfix, then evaluating it (using a stack).

---

