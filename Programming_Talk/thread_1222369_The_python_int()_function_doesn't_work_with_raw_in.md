---
title: "The python int() function doesn't work with raw_input()"
date: 2009-07-24
forum: Programming Talk
---

### Post by l951b951 on 2009-07-24
I'm using the "Think Python" text to try to learn Python on my own.  I ran into a question yesterday and asked on this forum.  I've run into a question tonight.  I read through "Read before posting" post, but I also have a question:  Is this the right forum to ask basic beginner programming questions, or should I ask in a different forum (such as absolute beginner talk)?


My original question that I came here to ask is the following:

I'm having trouble understanding how to take user input in using raw_input() and converting that input into an integer (to use for comparison using >).  The exercise I'm doing >        &#8220;If any of the three lengths is greater than the sum of the other two, then you cannot
   form a triangle. Otherwise, you can .&#8221;
1. Write a function named is_triangle that takes three integers as arguments, and that prints
   either &#8220;Yes&#8221; or &#8220;No,&#8221; depending on whether you can or cannot form a triangle from sticks
   with the given lengths.
   

The code I'm using is ```
def is_triangle(a,b,c):
    if c>a+b or b>a+c or a>b+c:
        print 'No'
    else:
        print 'Yes'

def user_input():
    print 'Enter first value'
    user_a=raw_input()
    int(user_a)
    print 'Enter second value'
    user_b=raw_input()
    int(user_b)
    print 'Enter third value'
    user_c=raw_input()
    int(user_c)
    is_triangle(int(user_a),int(user_b),int(user_c))


is_triangle(3,4,5)
user_input()
```

In the last line of user_input, I only get correct returns if I encapsulate int(user_a), etc.  If I try to use user_a by itself, the returns come back incorrect because is_triangle takes them as strings, concatenates them and so the less than comparison comes back wrong. Also, "is_triangle(3,4,5)" is at the end as a comparison, I'm using those figures as my input.

Why can't I use int(user_a) immediately after I create user_a from raw_input()?  

type(user_a) comes back as a string.

---

### Post by Can+~ on 2009-07-24
int(variable_name) doesn't change the variable in place, you should do

[PHP]    print 'Enter first value'
    user_a = raw_input()
    user_a = int(user_a)[/PHP]

Or immediately make it an int:

[PHP]    print 'Enter first value'
    user_a = int(raw_input())[/PHP]

Also, you don't need that previous print, both raw_input() and input() accept an argument as question:

[PHP]    user_a = int(raw_input('Enter first value:'))[/PHP]

Rewriting the user_input() function as

[PHP]def user_input():
	user_a = int(raw_input("Enter the first value:"))
	user_b = int(raw_input("Enter the second value:"))
	user_c = int(raw_input("Enter the third value:"))
	
	is_triangle(user_a, user_b, user_c)[/PHP]

---

### Post by l951b951 on 2009-07-24
Ah, ok.  

Thanks both for the answer and the tip.  I'm learning stuff slowly but surely.

---

### Post by l951b951 on 2009-07-26
Ok, here's a question that was buried in my original question.  Is this the correct forum for someone who's learning python?  I read the stickies, but none said outright whether it's ok or not to ask beginner questions in this forum, or is there a better place to ask?

---

### Post by thornmastr on 2009-07-26
> **l951b951 said:**
> Ok, here's a question that was buried in my original question.  Is this the correct forum for someone who's learning python?  I read the stickies, but none said outright whether it's ok or not to ask beginner questions in this forum, or is there a better place to ask?

This is a forum about programming. Notice there is no set specifications as to language or skill level. You posted to the correct forum.

Robert

---

