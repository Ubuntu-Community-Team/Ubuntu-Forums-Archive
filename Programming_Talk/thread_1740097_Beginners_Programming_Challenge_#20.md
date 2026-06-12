---
title: "Beginners Programming Challenge #20"
date: 2011-04-26
forum: Programming Talk
---

### Post by schauerlich on 2011-04-26
[size="6"]Beginners Programming Challenge #20[/size]
I hope this wall of text doesn't scare you. I just want to make sure you have a few simple concepts down, and then the rest of the challenge should be fairly simple. Feel free to skip ahead if you think you've got the idea down.

[size="5"]Concepts[/size]
First-class functions are a very useful tool. When a language allows first-class functions, it lets you pass around a function just like any other piece of data. You can store a function in a variable, pass it in to some other function, evaluate it with parameters, and return some other function. You  can pass it around just like you would an integer or a character. This has some interesting benefits, and lets you describe common patterns in less code.

A common pattern is to take every element from a list, do something with it (say, add 5 to it, or square it, etc), and then make a list of the results. By sticking that "do something" into a function, we can hide the explicit iteration inside of a function we only have to write once. This is called 'mapping':
```
data = range(1, 11)
new_list = []

for i in data:
    new_list.append(i * i)
```
can be transformed into
```
def square(x):
    return x * x

def map(func, data):
    new_list = []

    for i in data:
        new_list.append( func(i) )

    return new_list

map(square, range(1, 11))

```
Now, this might look like MORE code, and that's true for this small example. But the benefit is that you only have to write 'map' once. Then, you can customize the behavior by writing a different function in place of 'square', and passing it in to 'map'.

Mapping is just one example of a common pattern that can be solved using first class functions. Your challenge is implement a couple more.

[size="5"]The Challenge[/size]
You must implement two functions, [filter](http://en.wikipedia.org/wiki/Filter_(higher-order_function)) and [reduce](http://en.wikipedia.org/wiki/Reduce_(higher-order_function)). 
[list][*]Filter will take two arguments, a function 'f' and a list 'x'. 
[list][*]'f' will be a function that returns True or False based on some input. For example, the function 'isOdd' should return True if it's given an odd number, and False otherwise.
[*]Filter will return a list that contains all of the elements of 'x' such that 'f' returns True.[/list][/list]
```
def isOdd(x):
    return x % 2 == 1

filter(isOdd, range(1, 11)) # returns [1, 3, 5, 7, 9]
```
[list][*]Reduce will take a function 'f', a list 'x', and an initial value 'i'. 
[list][*]'f' will take two parameters, combine them in some way, and return the result. 
[*]Reduce takes all of the elements of 'x', combines them one at a time using 'f', and uses the value 'i' as the starting value when doing the first combination.[/list][/list]
```
def add(x, y):
    return x + y

reduce(add, range(1, 6), 0) # returns (((((0 + 1) + 2) + 3) + 4) + 5), which is 15
```
[size="5"]Extra credit[/size]
A lot of things can be defined in terms of reduce, including map and filter. Other examples include: taking the sum or product of all elements in a list, concatenating a list of lists into one flat list, reversing a list, finding the minimum/maximum of a list, and so on. Implement anything else you feel like doing in terms of the functions presented here.

[size="5"]Help[/size]
For people who have never dealt with them before, first-class functions can be a little intimidating. If you're unclear on what filter and reduce should do or how first-class functions work, feel free to ask for a different explanation or more examples. Note that many languages already have map, filter and reduce built in or as part of the standard library under various names. You should experiment with those to get a better sense of what they do and what you can do with them.

[size="5"]Judging[/size]
Entries will be judged based on how well you seem to understand the applications of first class functions, as well as the basic criteria that you code must work and be readable. One way of demonstrating understanding is to at least attempt the extra credit, even if you can't get it working. The goal here is to make you think, not churn something out for a grade. :)

Have fun! Judging will commence in a few weeks, or when the entries stop coming in.

---

### Post by krazyd on 2011-04-27
Great challenge! :)
I like the idea of demonstrating understanding of a concept, rather than producing a result. Explaining something to someone else always aids your own understanding by making you think things through step-by-step.

Here's my entry, in Ruby. Two very helpful sites I used to aid my understanding are [here]("http://www.robertsosinski.com/2008/12/21/understanding-ruby-blocks-procs-and-lambdas/") and [here]("http://en.wikibooks.org/wiki/Ruby_Programming/Syntax/Method_Calls#Understanding_blocks.2C_Procs_and_methods") (both are good for further reading on functions in Ruby).

[PHP]#!/usr/bin/ruby

# Ruby has several kinds first-class functions, but I'm only going to look at
# two: Procs and Lambdas.
# First, Procs:

is_odd = Proc.new{ |n| !(n%2).zero? }

def filter(function, range)
    values = []
    range.each do |i|
        values << i if function.call(i)
    end
    values
end

p filter(is_odd, (1..10))

# Procs also have a shorthand syntax.

add = ->(n,m){ n+m }

def reduce(function, range, initial)
    range.each do |i|
        initial = function.call(i, initial)
    end
    initial
end

p reduce(add, (1..10), 0)


# Ruby also has Lambdas, which are similar to Procs but have different rules
# for flow control, and behave more like methods in other languages. For
# example, you can return from a Lambda back *to* the calling function, but
# returning from a Proc is the same as returning *from* the calling function.

def test
    my_lambda = lambda{ return "returning from Lambda" }
    my_proc = Proc.new{ return "returning from Proc" }

    puts "starting test.."
    puts my_lambda.call     # the lambda returns to here.
    my_proc.call            # the Proc does *not* return to here.
    "returning from test.." # control does *not* get here.
end

puts test                   # the Proc returns to here!
[/PHP]

Edit: This code is written in a more functional style than I'm used to; it's not very Rubyish, and is not the technique I would normally use for code re-use. However, this was the format requested in the challenge. :)

Edit 2: This is the output:
```
[1, 3, 5, 7, 9]
55
starting test..
returning from Lambda
returning from Proc
```

---

### Post by JupiterV2 on 2011-04-27
For a lark, I thought I'd do this one in ANSI C. I decided to break the rules by adding additional arguments to the required functions to make the test more friendly to C:

func_callback.h
[PHP]/* Programming Challenge 20
 * Due to the difficulty of implementing generalized arguments in C, 
 * only an integer compatible version of the functions exist. */

#ifndef FUNC_CALLBACK_H
#define FUNC_CALLBACK_H 1

#define TRUE  1
#define FALSE 0

typedef unsigned char boolean;

typedef boolean (*TestFunc) (int);
typedef int (*CombineFunc) (int, int);

/* remove entries which do not match criteria specified by user supplied
 * function 'f' and return an array containing only those matches. */
int *filter (const TestFunc f, int *arr, const int sz, int *result_sz);

/* reduce array 'arr' by applying user supplied function 'f' into one result,
 * starting with value 'start' */
int reduce (const CombineFunc f, int *arr, const int sz, const int start);

#endif /* FUNC_CALLBACK_H */[/PHP]

func_callback.c
[PHP]#include "func_callback.h"
#include <stdlib.h>

int *
filter (const TestFunc f, int *arr, const int sz, int *result_sz)
{
    int i;
    int x = 0;
    int *tmp = malloc (sizeof (int) * sz);
    
    if (!tmp) return NULL;
    
    for (i = 0; i < sz; i++)
      if (f (arr[i])) 
            tmp[x++] = arr[i++];
    
    tmp = realloc (tmp, sizeof (int) * x);
    
    *result_sz = !tmp ? 0 : x;
    
    return tmp;
}

int 
reduce (const CombineFunc f, int *arr, const int sz, const int start)
{
    int i;
    int result = start;
    
    for (i = 0; i < sz; i++)
        result = f (result, arr[i]);
    
    return result;
}[/PHP]

The following is the code used to test the above:

func_cb_main.c
[PHP]#include "func_callback.h"
#include <stdio.h>
#include <stdlib.h>

/* "user" defined functions for use with filter and reduce */
static boolean 
isOdd (const int num)
{
    return (num % 2);
}

static boolean 
isEven (const int num)
{
    return !(num % 2) && num != 0;
}

static int
add (const int x, const int y)
{
    return x + y;
}

static int
sub (const int x, const int y)
{
    return x - y;
}

int
main (void)
{
    int test_arr[] = {0, 1, 2, 3, 4, 5, 6, 7, 8, 9};
    int *result_arr;
    int result = 0;
    int i;
    int sz;
    
    result_arr = filter (isEven, test_arr, sizeof(test_arr) / sizeof (int), &sz);
    printf ("Printing even numbers from array:\n");
    for (i = 0; i < sz; i++)
        printf ("%d ", result_arr[i]);
    printf ("\n");
    free(result_arr);
    
    result_arr = filter (isOdd, test_arr, sizeof(test_arr) / sizeof (int), &sz);
    printf ("Printing odd numbers from array:\n");
    for (i = 0; i < sz; i++)
        printf ("%d ", result_arr[i]);
    printf ("\n");
    free(result_arr);
    result_arr = NULL;
    
    result = reduce (add, test_arr, 10, 0);
    printf ("reduce (add) returned a result of %d\n", result);
    
    result = reduce (sub, test_arr, 10, 20);
    printf ("reduce (sub) returned a result of %d\n", result);
    
    return 0;
}[/PHP]

Use whatever compile flags you want. I tested with:
```
gcc -Wall -Wextra -ansi -pedantic func_callback.c func_cb_main.c && ./a.out
```

Results:
```
Printing even numbers from array:
2 4 6 8 
Printing odd numbers from array:
1 3 5 7 9 
reduce (add) returned a result of 45
reduce (sub) returned a result of -25

```

---

### Post by schauerlich on 2011-04-27
> **JupiterV2 said:**
> For a lark, I thought I'd do this one in ANSI C. I decided to break the rules by adding additional arguments to the required functions to make the test more friendly to C:

I was waiting for someone to try it in C. :) The idea for this challenge actually came from a discussion on how to make a generic version of map in C. There's no good way to do it. One method is to force the function you hand in to be of the type void foo(void *), and then make the user take care of casting the void * properly. Ugly.

If someone made a generic reduce in C, I'd be very impressed. After all, the value it accumulates should be able to be ANY type, including an array.

---

### Post by jwbrase on 2011-04-28
Interesting. I think I had an assignment a year or so ago where implementing filter in terms of reduce (in Haskell) was not just extra credit but actually required. It's been a while, though, the course was in German, and I seem to remember pulling my hair out over the problem.

EDIT: In fact, I seem to have found it so difficult that I used a loophole in the way the assignment was written to not implement filter in terms of reduce. I'll have to try again.

---

### Post by andrew1992 on 2011-04-28
I figured reduce lends itself nicely to a recursive approach. Here's a concise Python example:

```

def filter(function, list_):
    return [i for i in list_ if function(i)]

def reduce(function, list_):
    if len(list_) > 1:
        list_ = [reduce(function, [function(list_[0], list_[1])] + list_[2:])]
    return list_[0]

```

---

### Post by andrew1992 on 2011-04-28
> **schauerlich said:**
> I was waiting for someone to try it in C. :) The idea for this challenge actually came from a discussion on how to make a generic version of map in C. There's no good way to do it. One method is to force the function you hand in to be of the type void foo(void *), and then make the user take care of casting the void * properly. Ugly.

If someone made a generic reduce in C, I'd be very impressed. After all, the value it accumulates should be able to be ANY type, including an array.

I've never touched C before, though I'm aware it has no support for function overloading as far as I know. I'm going to give this a shot though, just for kicks ;)

---

### Post by simeon87 on 2011-04-28
> **andrew1992 said:**
> I figured reduce lends itself nicely to a recursive approach. Here's a concise Python example:

```

def filter(function, list_):
    return [i for i in list_ if function(i)]

def reduce(function, list_):
    if len(list_) > 1:
        list_ = [reduce(function, [function(list_[0], list_[1])] + list_[2:])]
    return list_[0]

```

Your reduce function does not have an initial value (see opening post). The initial value is needed to perform certain tricks with reduce. For example, when calculating the sum or the product of a list then the initial value should be 0 and 1 respectively. You can also have a different value to do something like computing the sum of a list plus a value n > 0 or multiplying all elements of a list with each other and a value n > 1.

---

### Post by andrew1992 on 2011-04-28
Your example doesn't help me see why those initial values are needed.  Let's say you want to take the product of all the values in a list [1, 2, 3, 4, 5].  With my algorithm, an initial value isn't necessary.

[1, 2, 3, 4, 5]
[2, 3, 4, 5]
[6, 4, 5]
[24, 5]
120

---

### Post by simeon87 on 2011-04-28
> **andrew1992 said:**
> Your example doesn't help me see why those initial values are needed.  Let's say you want to take the product of all the values in a list [1, 2, 3, 4, 5].  With my algorithm, an initial value isn't necessary.

[1, 2, 3, 4, 5]
[2, 3, 4, 5]
[6, 4, 5]
[24, 5]
120

In my examples the initial values indeed cancel out. But the initial value is nonetheless part of reduce and foldr/foldl functions in languages such as Haskell.

The reason for the intial value is that the types can differ. Your reduce function can only handle functions that take two values of the same type. It's a function that takes two int values and returns an int.

More abstractly we can say that it takes two values of type a and it returns a value of type a.

But we can also think of functions that take a value of type a, a value of type b and return a value of type a. This allows us to reduce a list of values of type b by starting with a value of type a.

The following example shows how this can be used:

```
def f(a, b):
    if b in a[1]:
        return (a[0] + [b], a[1])
    return a
    
def contains(my_words):
    return reduce(f, my_words, ([], ["aaa", "bbb", "ccc"]))[0]

print contains(["aaa", "ddd", "bbb"])
```

which will print:

```
['aaa', 'bbb']
```

In other words, we have a function called contains that shows all words from my_words that are also in the predefined list of words ["aaa", "bbb", "ccc"]. Note that we can only do this because the types of a and b in function f differ.

---

### Post by andrew1992 on 2011-04-28
I see that there, but to me that seems really quite unnecessary - why not just use filter, in that case?

---

### Post by simeon87 on 2011-04-28
> **andrew1992 said:**
> I see that there, but to me that seems really quite unnecessary - why not just use filter, in that case?

This is an example that I just came up with and yes you can write in a more simple way. I wouldn't write it like that in a real-world application but the example does highlight the need of an initial value to keep the function as generic as possible. It would be an unnecessary restriction of the reduce function if it could only handle functions of the same type.

---

### Post by andrew1992 on 2011-04-28
> **simeon87 said:**
> This is an example that I just came up with and yes you can write in a more simple way. I wouldn't write it like that in a real-world application but the example does highlight the need of an initial value to keep the function as generic as possible. It would be an unnecessary restriction of the reduce function if it could only handle functions of the same type.

I guess my current understanding of reduce is that it should take a function, apply it to pairs of entries in a list and returning a result, and stop after it has reduced to a single result.  Could you help me understand why it would be beneficial to allow genericness with reduce (that is, reduce a list of different types)? Because I'm finding it hard to see any case where that would be necessary (although I'm still learning, haha). Thanks, I appreciate the help.

---

### Post by andrew1992 on 2011-04-28
To add, your first example really did reduce a list of a single type, so could you show me an example of reducing a list of different types?

---

### Post by simeon87 on 2011-04-28
> **andrew1992 said:**
> I guess my current understanding of reduce is that it should take a function, apply it to pairs of entries in a list and returning a result, and stop after it has reduced to a single result.  Could you help me understand why it would be beneficial to allow genericness with reduce (that is, reduce a list of different types)? Because I'm finding it hard to see any case where that would be necessary (although I'm still learning, haha). Thanks, I appreciate the help.

It happens quite often in data processing that you have some list of values [a, a, a, a, a] and some object B that you wish to use to compute something using an 'a'. This object B could be a file or a database or some complex mathematical thing.

For example, you could have a list of people and a database in which you can lookup their salaries and other information. The value that reduce returns does not have to be 1 value, it can also be a list or some more complex object. So you walk along the list, you look at a value 'a' and you perform some calculation with that object B.

You can then think of functions that can do:

- Given a list of people, reduce it to a list of people that earn at least $50,000 annually.
- Given a list of people, reduce it to the total salary of these people.
- Given a list of people, reduce it to a list of managers with a salary of at least $70,000.
- Given a list of people, reduce it to the average salary of these people.
- Given a list of people, reduce it to the lowest / highest salary of these people.

You don't need to write all these things with reduce but it's nonetheless possible. You can think of the inital value as a helper value or helper object that you can use in your computations using the values of the list.

---

### Post by simeon87 on 2011-04-28
> **andrew1992 said:**
> To add, your first example really did reduce a list of a single type, so could you show me an example of reducing a list of different types?

It's not the types of the values in the list, it's about the types of the parameters of function f. In my latest example, the types are different. In function f, the type of parameter a is a tuple of two lists and the type of parameter b is a string. That's why I have [0] at the end to return the correct list of the tuple that reduce returns. If you take that away, you'll see that reduce actually returns:

```
(['aaa', 'bbb'], ['aaa', 'bbb', 'ccc'])
```

A tuple where the first of these is the final result of my computation and the second is the list from which we are checking. Effectively I'm building up my final result in the first list while using the second list during my calculations.

---

### Post by schauerlich on 2011-04-28
> **andrew1992 said:**
> Your example doesn't help me see why those initial values are needed.

Here's an example: Say you want to determine if a list of boolean values has an even or an odd number of Trues. We can write functions to test for both of these with reduce, using the same function, but different starting values:

```
def f(acc, b):
    if b:
        return not acc
    else:
        return acc

def oddBools(x):
    return reduce(f, x, False)

def evenBools(x):
    return reduce(f, x, True)

even = [True, True, False, True, True,  False]
odd  = [True, True, False, True, False, False]

print "evenBools(" + str(even) + "): " + str(evenBools(even))
print "oddBools("  + str(even) + "): " + str(oddBools(even))
print "evenBools(" + str(odd)  + "): " + str(evenBools(odd))
print "oddBools("  + str(odd)  + "): " + str(oddBools(odd))

```

Of course, this is just one (fairly trivial) example.

---

### Post by andrew1992 on 2011-04-28
I understand that it's possible, it just seems unnecessary.  

```

true_list = filter(lambda x: x, [False, True, True, False, True])
if len(true_list) % 2 == 0:
    print "Even number of trues"
else:
    print "Odd number of trues"

```

I know that you're just trying to illustrate the benefit of genericness, but it's hard for me to find a case where that would be useful.

---

### Post by andrew1992 on 2011-04-28
Also, your example doesn't have any genericness, the function takes in and returns the same type.

---

### Post by simeon87 on 2011-04-28
> **andrew1992 said:**
> I understand that it's possible, it just seems unnecessary.  

```

true_list = filter(lambda x: x, [False, True, True, False, True])
if len(true_list) % 2 == 0:
    print "Even number of trues"
else:
    print "Odd number of trues"

```

I know that you're just trying to illustrate the benefit of genericness, but it's hard for me to find a case where that would be useful.

To appreciate reduce (or foldr//foldl) you'd need to study algebraic data types as fold functions can be generalized to also "reduce/fold" other data structures into a result, such as trees. An example of that (in Haskell) can be found here: [http://en.wikipedia.org/wiki/Catamorphism#Example](http://en.wikipedia.org/wiki/Catamorphism#Example) This is often used in parsers to reduce a tree data structure into a single value. Lists are a simple case of that: [http://en.wikipedia.org/wiki/Fold_%28higher-order_function%29#List_folds_as_structural_transformations](http://en.wikipedia.org/wiki/Fold_%28higher-order_function%29#List_folds_as_structural_transformations)

It's not easy to come up with a straightforward example that demonstrates the usefulness of foldr/reduce because you can, in Python, always write something else that does the same. However, the general theory behind it can be applied to various data structures. In a language such as Haskell the fold functions can make complex operations quite easy to do. Python implements these concepts from functional programming but you don't need to use them rigorously.

---

### Post by andrew1992 on 2011-04-28
That's very interesting.  I've been starting to look at Haskell a little bit, and this gives me all the more reason to progress with it. Thanks for the time guys.

---

### Post by schauerlich on 2011-04-28
> **andrew1992 said:**
> That's very interesting.  I've been starting to look at Haskell a little bit, and this gives me all the more reason to progress with it. Thanks for the time guys.

Haskell is a very interesting language. Check out [Learn You a Haskell for Great Good!](http://learnyouahaskell.com/chapters) for a pretty straightforward introduction.

---

### Post by jwbrase on 2011-04-29
> **andrew1992 said:**
> Your example doesn't help me see why those initial values are needed.  Let's say you want to take the product of all the values in a list [1, 2, 3, 4, 5].  With my algorithm, an initial value isn't necessary.

[1, 2, 3, 4, 5]
[2, 3, 4, 5]
[6, 4, 5]
[24, 5]
120

In addition to what others have said, what happens if the list passed to your function is the empty list?

Reduce functions that specify an initial value just return the initial value in that case.

---

### Post by jwbrase on 2011-04-30
Here's an implementation in Haskell with filter, map, reverse (returns the list passed to it in opposite order), and a factorial function all implemented in terms of reduce.

(filter, map, and reverse are all already functions in Haskell Prelude, so I've added ' to the function names to distinguish them from the native versions).

```
main = do
        print (reduce (+) 0 [1..5]) {-add the numbers from 1 to 5-}
        print (filter' odd [1..10]) {-print the odd numbers 1<=n<=10-}
        print (map' (\x -> x*x) [1..10]) {-Print the squares of 1 to 10-}
        print (reverse' [1..10]) {-Print 1 to 10 in reverse order-}
        print (map' fac [0..9]) {-Print n factorial for 0<=n<=9-}

reduce :: (a -> b -> a) -> a -> [b] -> a
reduce _ i [] = i
reduce f i (x:xs) = reduce f (f i x) xs

filter' :: (a -> Bool) -> [a] -> [a]
filter' f xs = reduce (\ys y -> if f y then ys ++ [y] else ys) [] xs

map' :: (a -> b) -> [a] -> [b]
map' f xs = reduce (\ys y -> ys ++ [(f y)]) [] xs

reverse' :: [a] -> [a]
reverse' xs = reduce (\ys y -> y:ys) [] xs

fac :: Integer -> Integer
fac x = reduce (*) 1 [1..x]

```

---

### Post by schauerlich on 2011-05-12
A bump for more entries. Would anyone who's already made an entry like to try the extra credit? :)

---

### Post by red_Marvin on 2011-05-12
gforth implementation, gforth does not have a list type, so I had to implement
one.

Most list operations are done through maps, but note that there are
more than one type of map. Those that modifies the list, and those
that leave the list unmodified, like the map used for printing the
contents of a list.
Reduce is also done with a non-modifying map, but where the function that is applied takes two values from the stack* and leaves one.
In this way the first application of the function will operate on the
initial value and the first element, and leave the result on the stack
for the next iteration which will consume the previous result and the second
value in the list ...and so on...

*Forth is a stack-based language

```
\ create a new node and pop the stack top
\ into the payload cell
: +>node ( n -- a )
    3 cells allocate throw
    ( n a )
    0 over cell+ !
    0 over 2 cells + !
    dup -rot !
;

\ get the previous node address
: node- ( a[i] -- a[i-1] )
    dup if cell+ @ then
;

\ get the next node address
: node+ ( a[i] -- a[i+1] )
    dup if 2 cells + @ then
;

\ link two nodes together so that they point at each other
: cons ( a[i] a[i+1] -- a[i+1] )
    dup if 2dup cell+ ! then
    over if 2dup swap 2 cells + ! then
    nip
;

\ break the link between two nodes
: uncons ( a[i] -- a[i-1] a[i] )
    dup node-
    dup if
        dup 2 cells + 0 swap !
    then
    swap
    dup if
        dup cell+ 0 swap !
    then
;

\ loop node- until the first node is found
: find-first ( a[i] -- a[0] )
    dup ( ai ai )
    begin
        nip dup ( ai ai )
        node- dup 0= ( ai ai-1 tf )
    until
    drop
;

\ loop node+ until the last node is found
: find-last ( a[i] -- a[N] )
    dup
    begin
        nip dup
        node+ dup 0=
    until
    drop
;

\ uncons node from prev and next and free the node
: -node ( a[i] -- a[i+1] )
    uncons node+ uncons ( a[i-1] a[i] a[i+1] )
    swap free throw ( a[i-1] a[i+1] )
    cons ( a[i+1] )
;

\ apply an xt to all nodes in a list
: map \ ( a xt( a -- a ) -- )
    begin
        dup >r ( a[i] xt / xt)
        execute ( a[i+1] / xt )
        r> over ( a[i+1] xt a[i+1] )
    0= until
    2drop
;

\ Takes an xt (xti) with the stack effect ( n0 -- n1 )
\ and return an xt (xto) with the stack effect ( a0 -- a1 )
\ where a are node addresses.
\ The xti is included in xto so that the xti is applied to
\ the payload of a0 and the result (n1) is written back to a0
\ then a node+ is executed yielding a1
: rw-iter \ ( xt( n -- n ) -- xt( a -- a ) )
    >r :noname r>
        postpone dup postpone >r postpone @
        ( ... n ) compile, ( ... n )
        postpone r@ postpone !
        postpone r> postpone node+
    postpone ; postpone immediate
;

\ same as rw-iter, but the expected stack effect of xti
\ is ( n -- ) and no data is written back to the node
\ good for printing the content of a list and such
: ro-iter \ ( xt( n -- ) -- xt( a -- a ) )
    >r :noname r>
        postpone dup postpone >r postpone @
        ( ... n ) compile, ( ... )
        postpone r> postpone node+
    postpone ; postpone immediate
;

\ also an iterator, but also expects another list node
\ on the stack, if the xt returns nonzero, 
\ creates a new node with the data of the examined one
\ and conses the it onto this one
: cons-filter-iter
    >r :noname r>
        postpone dup postpone >r postpone @
        ( ... n ) compile, ( ... n )
        postpone if
            postpone r@ postpone @
            postpone +>node
            postpone cons
        postpone then
        postpone r> postpone node+
    postpone ; postpone immediate
;

\ print a list
: .list ['] . [compile] ro-iter map ;

\ add 1 to all the elements of a list
: 1+list ['] 1+ [compile] rw-iter map ;

\ delete a list
: -list ['] -node map ;

\ copies the elements for which the xt returns nonzero
\ onto a new list
: filter
    0 -rot [compile] cons-filter-iter map find-first
;

\ applies the xt onto the initial argument and the
\ first member of the list
\ the xt on the result of the above and the second element
\ ...
: reduce ( a n xt -- n )
    [compile] ro-iter map
;

: even 2 mod 0= ;

: odd 2 mod 0<> ;

\ creates a list
: simple-list
    1 +>node
    26 2 do
        i +>node cons
    loop
    find-first
;

\ creates a list of lists
: list-of-lists
    11 +>node
    10 2 do
        10 i + +>node cons
    loop
    find-first
    +>node
    10 2 do
        10 i * 1 + +>node
        10 2 do
            10 j * i + +>node cons
        loop
        find-first +>node cons
    loop
    find-first
;
    

\ examples


simple-list
." the contents of the test list:" cr
dup .list cr cr

." the even elements in the list:" cr
dup ' even filter
dup .list -list \ the result list is also freed from memory
cr cr

." the even elements in the list:" cr
dup ' odd filter
dup .list -list
cr cr

." the sum of the elements of the list:" cr
0 over ' + reduce . cr cr

." the product of the elements of the list:" cr
1 over ' * reduce . cr cr

." mapping a function that increases the values in the list" cr
dup ' 1+ rw-iter map
dup .list cr cr

-list


list-of-lists

\ the same as .list but with a carriage return on the end
: .row .list cr ;

." look! here we map another map on a list of lists :)" cr
dup ' .row ro-iter map cr

\ freeing the data is a question of first deleting the inner lists
dup ' -list ro-iter map
-list
```

Shell/Output:
```
leo@patternmaker:~/prog/forth
$ gforth challenge20.fs
the contents of the test list:
1 2 3 4 5 6 7 8 9 10 11 12 13 14 15 16 17 18 19 20 21 22 23 24 25 

the even elements in the list:
2 4 6 8 10 12 14 16 18 20 22 24 

the even elements in the list:
1 3 5 7 9 11 13 15 17 19 21 23 25 

the sum of the elements of the list:
325 

the product of the elements of the list:
2076180480 

mapping a function that increases the values in the list
2 3 4 5 6 7 8 9 10 11 12 13 14 15 16 17 18 19 20 21 22 23 24 25 26 

look! here we map another map on a list of lists :)
11 12 13 14 15 16 17 18 19 
21 22 23 24 25 26 27 28 29 
31 32 33 34 35 36 37 38 39 
41 42 43 44 45 46 47 48 49 
51 52 53 54 55 56 57 58 59 
61 62 63 64 65 66 67 68 69 
71 72 73 74 75 76 77 78 79 
81 82 83 84 85 86 87 88 89 
91 92 93 94 95 96 97 98 99 

Gforth 0.7.0, Copyright (C) 1995-2008 Free Software Foundation, Inc.
Gforth comes with ABSOLUTELY NO WARRANTY; for details type `license'
Type `bye' to exit


```

---

### Post by schauerlich on 2011-05-14
> **red_Marvin said:**
> gforth implementation, gforth does not have a list type, so I had to implement
one.

I don't know forth myself, but I've got a friend whose opinion I trust that I'll ask to take a look at this when judging comes around.

---

### Post by red_Marvin on 2011-05-14
He will probably say it is very horrible! :p

---

### Post by schauerlich on 2011-05-16
> **red_Marvin said:**
> He will probably say it is very horrible! :p

If you won again, they'd probably think we're colluding. :)

---

### Post by mo.reina on 2011-06-20
common lisp has remove-if-not,

my own implementation

```
(defun filter (fn lst)
  (cond ((null (car lst)) nil)
        (t (cons (if (funcall fn (car lst))
                     (car lst))
                 (filter fn (cdr lst))))))
```

another way of doing it (longer but more correct output)

```
(defun filter (fn lst)
  (let ((final nil))
    (labels ((main-loop (lst2)
                        (cond ((null (car lst2)) nil)
                              ((funcall fn (car lst2))
                               (push (car lst2) final)
                               (main-loop (cdr lst2)))
                              (t (main-loop (cdr lst2))))))
      (main-loop lst))
    (reverse final)))
```

reduce (must have a start value):

```
(defun reduc (fn lst start)
  (funcall fn (subseq lst start))
```

extra credit:
```
(defun sum (lst)
  (cond ((null (car lst)) 0)
        (t (+ (car lst)
              (sum (cdr lst))))))

(defun cat (lsts)
  (let ((final-list nil))
    (mapcar (lambda (lst)
              (mapcar (lambda (item)
                        (push item final-list))
                      lst))
            lsts)
    (reverse final-list)))

(defun rev (lst)
  (let ((final-list nil))
    (mapcar (lambda (item)
              (push item final-list))
            lst)
    final-list))
```

```
* (reduc #'sum '(1 2 3 4 5) 0)

15
* (reduc #'sum '(1 2 3 4 5) 2)

12
* (filter #'oddp '(1 2 3 4 5))

(1 3 5)

* (sum '(1 2 3 4 5))

15
* (cat '((1 2 3 4 5) (6 7 8 9 0)))

(1 2 3 4 5 6 7 8 9 0)

* (rev '(1 2 3 4 5))

(5 4 3 2 1)


```

---

### Post by schauerlich on 2011-06-21
Huh, I should probably pick a winner. I'll wait for mo.reina to finish, though.

---

### Post by mo.reina on 2011-06-21
all done.

---

### Post by schauerlich on 2011-06-21
Alright! Sorry it's taken so long to pick a winner for this, school tends to be distracting.

Anyways, the winning entry belong to [jwbrase](http://ubuntuforums.org/showpost.php?p=10746907&postcount=24)! His Haskell entry was concise, functional (in both senses of the word), and implemented the other functions in terms of reduce. Thank you to all of the participants, and congratulations jwbrase! We'll be looking out for the next challenge.

---

### Post by schauerlich on 2011-06-22
jwbrase has let me know he can't run the next challenge at the moment - is there anyone else interested in hosting it?

---

### Post by Queue29 on 2011-06-24
> **schauerlich said:**
> jwbrase has let me know he can't run the next challenge at the moment - is there anyone else interested in hosting it?

I'd be happy to do it

---

### Post by schauerlich on 2011-06-24
> **Queue29 said:**
> I'd be happy to do it

Alright. Unless someone from the beginner's team objects, go ahead and make the next one!

---

### Post by ziekfiguur on 2011-06-24
I know the challenge is officially over, but i saw noone gave a C++ solution, so i thought i should give it a try (and refresh my template skills which i haven't used for a long time).

```
#include <iostream>
#include <vector>

template <typename Function, typename T>
std::vector<T> map(Function f, std::vector<T> const &data)
{
    std::vector<T> result;
    for (typename std::vector<T>::const_iterator it = data.begin();
            it != data.end();
                ++it)
        result.push_back(f(*it));
    return result;
}

template <typename T>
class Square
{
    public:
        T operator()(T const &x)
        {
            return x * x;
        }
};

template <typename Function, typename T>
std::vector<T> filter(Function f, std::vector<T> const &data)
{
    std::vector<T> result;
    for (typename std::vector<T>::const_iterator it = data.begin();
            it != data.end();
                ++it)
        if (f(*it))
            result.push_back(*it);
    return result;
}

class isOdd
{
    public:
        int operator()(int x)
        {
            return x & 1;
        }
};

template <typename Function, typename T>
T reduce(Function f, std::vector<T> const & data, T const &i)
{
    T value = i;
    for (typename std::vector<T>::const_iterator it = data.begin();
            it != data.end();
                ++it)
            value = f(value, *it);
    return value;
}

template <typename T>
class add
{
    public:
        T operator()(T const &v1, T const &v2)
        {
            return v1 + v2;
        }
};

template <typename T>
void print(std::vector<T> const &data)
{
    for (typename std::vector<T>::const_iterator it = data.begin();
            it != data.end();
                ++it)
        std::cout << *it << ' ';
    std::cout << '\n';
}

int main()
{
    int array[] = {1, 2, 3, 4, 5, 6, 7, 8, 9, 10};
    std::vector<int> vec(array, array + 10);

    std::vector<int> squares = map(Square<int>(), vec);
    print(squares);

    std::vector<int> odds = filter(isOdd(), vec);
    print(odds);

    std::vector<int> vec2(array, array + 5);
    int sum = reduce(add<int>(), vec2, 0);
    std::cout << sum << std::endl;
    return 0;
}

```

---

