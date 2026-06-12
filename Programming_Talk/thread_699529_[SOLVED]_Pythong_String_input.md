---
title: "[SOLVED] Pythong String input"
date: 2008-02-17
forum: Programming Talk
---

### Post by Strike&gt;&gt; on 2008-02-17
Hi

I just started learning python, and as my second program i decided to make a really simple calculator. Since it only works in the terminal I made the program ask for the operations and input them as string. like a = raw_input("Operation: "). The problem is the operation entered must be exact or else it wouldn't work. for example can't type Add,ADD,AdD.... Is there a way  to fix that problem without making if statements for every possible combination?

---

### Post by LaRoza on 2008-02-17
Convert the input to all uppercase, that is what I do usually.

[php]
oper = raw_input("Operation: ").upper()
print oper
[/php]

---

### Post by a9bejo on 2008-02-17
> **LaRoza said:**
> Convert the input to all uppercase, that is what I do usually.

Hmm I always convert to lowercase. Maybe this could become the subject of a new kind of flamewar. ;)

---

### Post by Strike&gt;&gt; on 2008-02-17
I tried that and it didn't work. I don't know what I did wrong. I didn't want to post the program since I was embarrassed by how stupid it looks :oops:

```
from math import sqrt



a = input("First Number: ")

b = input("Second Number: ")

o = raw_input("Operation: ")



if o == 'add': 
    c = a + b
elif o == 'multiply':
    c = a * b
elif o == 'divide':
    c=  a / b
elif o ==  'subtract':
    c = a - b
elif o == 'exponent':
    c = a ** b
elif o == 'square root':
    d = 0
    d = sqrt(a)
    c = sqrt(b)
    print "Result: ", d
else:
    c= 0
    
    
    
    
print "Result: ", c
```

so i added .upper() to raw_input and gave me 0 for my results.

---

### Post by LaRoza on 2008-02-17
Use lower() instead then.

You are converting the input to all uppercase, and then testing against lowercase conditions.

I typically convert to uppercase, although it doesn't matter.

---

### Post by a9bejo on 2008-02-17
> 
so i added .upper() to raw_input and gave me 0 for my results.


if you add upper(), the result will be uppercase, thus "ADD" ;)

---

### Post by Strike&gt;&gt; on 2008-02-17
W00t, it worked! Thanks for your help guys :D

---

### Post by LaRoza on 2008-02-17
> **Strike>> said:**
> W00t, it worked! Thanks for your help guys :D

User input, the worst part of programming. 

Read this: [http://linuxgazette.net/issue83/evans.html](http://linuxgazette.net/issue83/evans.html)

---

### Post by Strike&gt;&gt; on 2008-02-17
Thanks for the link LaRoza. i am trying to learn from it, although it can be a little confusing. It seems input() can be a dangerous thing to do and i should try to use raw_input() instead. I changed my input() to int(input()), Does that fix the security and other potential damages problem? I tried raw_input() for getting the integer part but I don't know how to 'process' the integer inputs I get.

---

### Post by Jessehk on 2008-02-17
*raw_input()* will return a string. *int()* takes a variable and will attempt to turn it into an integer.

Thus, to get an integer from a string (like *raw_input()*):
```

number = int(raw_input("Enter a number: "))

```

---

### Post by pmasiar on 2008-02-18
> **Strike>> said:**
> It seems input() can be a dangerous thing to do and i should try to use raw_input() instead. I changed my input() to int(input()),  

This is wrong way to think about it. You cannot rely on using recipes and copy-paste snippets of code. You need to understand the differences, and know from your own understanding where to use what.

Just copying snippets without real understanding what every statement or function does is [Cargo cult programming](http://en.wikipedia.org/wiki/Cargo_cult_programming). You cannot become competent hacker if you don't have patience to read the docs, and compare the two definitions word by word to find the difference.

Ie you copied .upper() as LaRoza suggested, but without the understanding consequences: typical cargo cult. Because o is now uppercase, you obviously need to  compare o == 'ADD'. If you adapt any advice, you need to track and fix consequences for other parts of your code - it is your job, not the advisor's.

BTW don't get upset - I am trying to help you and show you meta-errors, so you can avoid them next time. If I did not care about you and did not want to help you, much easier for me would be to ignore question completely - it takes less time than writing the answer :-)

Free bonus hint: Get used to longer, more descriptive variable names. 'oper' instead of 'o' (if you are too lazy to write 'operation'. Good variable name is real life saver later, when your code grows.

---

### Post by ssam on 2008-02-18
to make it more robust you may also want to use strip. this removes surrounding whitespace.

```

>>> "  abc  ".strip()
'abc'

```

---

### Post by LaRoza on 2008-02-18
> **Strike>> said:**
> Thanks for the link LaRoza. i am trying to learn from it, although it can be a little confusing. It seems input() can be a dangerous thing to do and i should try to use raw_input() instead. I changed my input() to int(input()), Does that fix the security and other potential damages problem? I tried raw_input() for getting the integer part but I don't know how to 'process' the integer inputs I get.

Always get input as strings, and then try to convert them to ints. If the conversion fails, you can handle it gracefully.

Right now, user input (which confounds experienced programmers) isn't the most important thing for you. Learn the basics first, and don't worry about it. (You will have plenty of time later)

To convert a string to an int use the int() method.

---

### Post by LaRoza on 2008-02-18
> **pmasiar said:**
> 
Free bonus hint: Get used to longer, more descriptive variable names. 'oper' instead of 'o' (if you are too lazy to write 'operation'. Good variable name is real life saver later, when your code grows.

I wrote that...

It is my habit to use weird variable names and truncations of real words. 

If you use the following against me later, I understand. I do it because I use ECMAScript and PHP which have large global namespaces and I don't want to have to worry about conflicts.

---

### Post by pedro_orange on 2008-02-18
...Am I the only one that Lol'd at the title of this thread? ^^

---

### Post by Strike&gt;&gt; on 2008-02-18
Thanks everyone for your comments and tips.
> BTW don't get upset - I am trying to help you and show you meta-errors, so you can avoid them next time. If I did not care about you and did not want to help you, much easier for me would be to ignore question completely - it takes less time than writing the answer 
Sniff* Man i am touched. You are absolutely right, i should take more responsibility to learn things thoroughly. It;s just that i am so impatience and I can't concentrate on something for that long, I just go to another tab and start reading something else, then after 1 min. I  quit and start playing something like tetris or w/e. Maybe i have ADD, i don't know. But I am going to try harder to understand before posting. 

ssam thank you for that wonderful tip, I was wondering how to do that. 

LaRoza thank you for the tips:guitar:And yeah, right now the input is more complex than the main code.


pedro_orange are you thinking of something naughty ;)?

Found a good website for manipulating inputs in many ways 
[HTML]http://docs.python.org/lib/string-methods.html[/HTML]

---

