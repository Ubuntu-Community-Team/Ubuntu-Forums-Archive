---
title: "Tricky to get my head round (Python)"
date: 2010-01-13
forum: Programming Talk
---

### Post by blazemore on 2010-01-13
I'm trying to do one thing in Python, and I'm finding it difficult to get my head around.

What I want to do is have an arbitrarily sized "grid" (2 dimenional array) of '0's
What I then want to do is repeatedly add 1 to the first "cell" until it reaches 9.
Then it resets, and 1 is added to the next "cell" and the first cell loops 0 through 9 again.
This would carry on in this fashion until *every combination possible has been printed*.

So if it was just a 1 dimensional list of 2 it would go:
00
10
20
30
40
50
60
70
80
90
01
11
21
31
...

and so on.

Can anyone please help me with this thought process? The language is irrelevant, I just can't think of the logic to do this.

---

### Post by CptPicard on 2010-01-13
```

def count(li, n):

  def recurse(stack):
    if len(stack) == n:
      print "".join([str(i) for i in stack])
    else:
      for x in li:
	stack.append(x)
	recurse(stack)
	stack.pop()
  
  recurse([])
  
count([0,1,2,3], 3)

```

Simple recursive "counting". If you're on Python, look at the "product" iterator in functools. This implementation actually counts in reverse to what you want, but the modification is simple... for example don't push to the "top" of stack but to the "front" of it.

---

### Post by blazemore on 2010-01-13
That looks great, let me write it as a flowchart to work it out. Then I'll rewrite it.
I may use this for commercial purposes with your permission; will you release your snippet under the GPL if I opt for a straight copy+paste?
I don't mind which way it counts, as long as every possible combination is looped through.

---

### Post by blazemore on 2010-01-13
That is absolutely brilliant thanks a lot.
Would it be straightforward to expand this to include 2 dimensional arrays?

Or would it be easy to use a display hack to "wrap" long outputs over multiple lines, so a list like this:
[x,x,x,x,x,x,x,x,x,x,x,x,x,x,x,x]

would be displayed like this
[FONT="Courier New"]xxxx
xxxx
xxxx
xxxx[/FONT]

---

### Post by doas777 on 2010-01-13
> **blazemore said:**
> That is absolutely brilliant thanks a lot.
Would it be straightforward to expand this to include 2 dimensional arrays?

Or would it be easy to use a display hack to "wrap" long outputs over multiple lines, so a list like this:
[x,x,x,x,x,x,x,x,x,x,x,x,x,x,x,x]

would be displayed like this
[FONT=Courier New]xxxx
xxxx
xxxx
xxxx[/FONT]

just add a '\n' every couple loops (looks like you would prefer 4 iterations per line).

---

### Post by blazemore on 2010-01-13
lol you are clearly a better programmer than me.
I can't see where to put the newline character.

I'd like the "width" and "height" of this rectangle to be user-set and I have two integer variables just ready (width I am passing to 'n' in your lovely function)

---

### Post by CptPicard on 2010-01-13
> **blazemore said:**
> 
I may use this for commercial purposes with your permission; will you release your snippet under the GPL if I opt for a straight copy+paste?


Do whatever you want with it, the implementation is trivial and I don't own the idea :)

> I don't mind which way it counts, as long as every possible combination is looped through.

In a real implementation I would go for itertools.product instead of my code -- I just wanted to show you the idea (product is not in functools as I said before, sorry).


> **blazemore said:**
> 
Would it be straightforward to expand this to include 2 dimensional arrays?

Not sure what you mean...? You can put anything in the recursion termination condition... (the first if branch)

---

### Post by doas777 on 2010-01-13
> **blazemore said:**
> lol you are clearly a better programmer than me.
I can't see where to put the newline character.

I'd like the "width" and "height" of this rectangle to be user-set and I have two integer variables just ready (width I am passing to 'n' in your lovely function)


well, you will need a counter, and code to increment and monitor it. starting with the captians code I would do it as:
```
def recurse(stack, outcount, max):
    if outcount == max:
        print "\n"
        outcount = 0
    if len(stack) == n:
      print "".join([str(i) for i in stack])
      outcount += 1
    else:
      for x in li:
    stack.append(x)
    recurse(stack)
    stack.pop()
  
recurse([], 0, 3)
```

---

### Post by blazemore on 2010-01-13
Unfortunately that doesn't work. The value of "outcount" seems to keep getting reset to 1.

---

### Post by doas777 on 2010-01-13
> **blazemore said:**
> Unfortunately that doesn't work. The value of "outcount" seems to keep getting reset to 1.

ahh, yeah, your right. the printing is at the end, not incremental.

---

### Post by blazemore on 2010-01-13
I did that and that's not the problem.
The problem is the second time the recursion method is called, "outcount" needs to be passed to it, not 0.

However, it still doesn't work.

---

### Post by doas777 on 2010-01-13
> **blazemore said:**
> I did that and that's not the problem.
The problem is the second time the recursion method is called, "outcount" needs to be passed to it, not 0.
However, it still doesn't work.

well, it's recursive so it saves up all the entries until the length of the stack is equal to the number of elements passed in. as a result, you either need to break up the print statement, or accumulate the \n's on the stack (which would wreak havok if you tried to add it to a number). I would seperate out your processing from your output (put it in a function that gets called after all the math is done) which prints out each line.

---

### Post by blazemore on 2010-01-13
To tell the truth, I don't really understand the function.
I didn't do well on the recursive section of my Computer Systems Architecture module, although that was written in assembler.

It seems you understand it perfectly and think it's really simple.
Could you please try and explain it in step by step terms, exactly what the program is doing?

I'll let you know where I'm going with this.
I want a GUI with a grid of pixels, and the program will cycle through all combinations, assigning each one a number.

I've got a friend studying maths who thinks he could write an algorithm to generate the picture, given the number, if he can see a flowchart of how the program cycles through them.

So I'm mocking it up in Python now to generate in a compiled language later.

---

### Post by blazemore on 2010-01-16
Ack, can't get it to work with a 2 dimensional array.
Tried to hack it by inserting newline characters into the list, but that was seriously ugly. and slow.

---

