---
title: "Character count (python)"
date: 2008-11-07
forum: Programming Talk
---

### Post by ratmandall on 2008-11-07
Hey I can't quite work out how to count a character that repeats it self 2 or more times, for example.
Cinderella would return 2.
I'm not talking about just counting "l" but if a character is followed by the same character 2 times or more.
Thanks for any help.

---

### Post by WW on 2008-11-07
Your statement of the problem isn't clear to me.  When you say "Cinderella would return 2", you haven't mentioned which letter was referred to. So, for comparison, what would you expect from "Mississippi"? Or "bookkeeper"?

---

### Post by ratmandall on 2008-11-07
> **WW said:**
> Your statement of the problem isn't clear to me.  When you say "Cinderella would return 2", you haven't mentioned which letter was referred to. So, for comparison, what would you expect from "Mississippi"? Or "bookkeeper"?

Sorry I wasn't clear Well the user defines the letter,
Try and make sense of it from this because I have kind of confused myself.
```
If the user specified "s"
Miss issippi = 22
  ^^=2^^=2
If the user specified "k" 
bookkeeper = 2
   ^^=2
If the user specified "a" 
gaaaame = 4
 ^^^^=4
And a string that would return zero would be

Ubuntu = 0
```

---

### Post by Greyed on 2008-11-08
Gah, looks like a homework assignment.  :(

Simple for loop w/temp variable and a counter would do the trick.  There might be some deep-magic regex but my brain starts to explode around the problem of multiple, unknown matches.

---

### Post by ghostdog74 on 2008-11-08
hint: try count()

---

### Post by ratmandall on 2008-11-08
> **Greyed said:**
> Gah, looks like a homework assignment.  :(


No unfortunately I don't do any computer related courses/subject's at school.
:(
> **ghostdog74 said:**
> hint: try count()
All count does is count how many occurrences of the specified letter in a string, not what I want.

---

### Post by pp. on 2008-11-08
Writing a program is telling the computer how to proceed to do a particular task.

Since you don't appear to be overly clear about the task to be performed, why don't you start with writing instructions to yourself which describe how to perform that task with pencil and paper?

---

### Post by nvteighen on 2008-11-08
I understand this clearly: you want to detect groups of repeated letters and represent them by their length. Then the result for a given word will be the appending of all lengths found.

If this is not homework, I'll advice you to:
1. Change the "appended" result. Get yourself used to create programs that spit out manageable unambiguous information; I mean: if I get the result "123", that could mean "1-2-3", "12-3", "1-23" or even "123"... For example, using hyphens could be a solution.

2. Ok, to develop anything (and specially in high abstraction level languages like Python), first think what steps you have to take, always looking at the tools the language offers you.

3. As this is Python, please use the interactive shell to test things. It's a great learning/testing sandbox. Use it while designing your steps in "pencil & paper" (I wouldn't take that literally... the idea is "think before code").

Is there a purpose (besides learning) for this? I'm just curious.

---

### Post by stimpack on 2008-11-08
Sounds like a count of the length of a sequence of the same char, such as Run Length Encoding needs.

---

### Post by pmasiar on 2008-11-08
I assume you know the character you want to check for counts, and return a list of counts (how long are consecutive appearances)?

This is best researched in interactive shell, one of the reason Python is best for learning. Split the string on that character, and take a look at the results. Places with consecutive same character, split results are consecutive empty strings. Count them.

---

### Post by ratmandall on 2008-11-08
OK I sort of figured out how to do what I wanted, sort of as in I need to do other things with the string to actually make what I originally wanted but I'll do that by myself.
[php]
#!/bin/python
f = raw_input("blabla: ")
s = "guumom"#Wtf
print s
aa=s.rfind(f)
if aa >= 2:
    a = s.replace(f, "2" )#<<Would be 2 if "u" was entered, Meant to be how many times character specified appears, variable (aa) doesn't work??
    print a
else:
    print "naww"[/php]

---

### Post by Greyed on 2008-11-09
Er, ok, since you put up code, here is what I was alluding to in my first reply.  A for loop, a placeholder and a counter...

[php]
def letters(word=''):      
    count = 1 # Counter   
    prev = '' # Placeholder
    for c in word: # For loop
        if c != prev:
            if prev: # Prevents printing the empty prev.
                print prev, count
            count = 1
            prev = c
        elif c == prev:
            count = count + 1
    else: # needed to print out the final letter's count
        print c, count

while 1:
    letters(raw_input(': '))
[/php]Results in the following.
```

{grey@igbuntu:~} python foo.py
: mississippi                 
m 1                           
i 1                           
s 2                           
i 1                           
s 2                           
i 1                           
p 2                           
i 1                           
: ragoo                       
r 1                           
a 1                           
g 1                           
o 2                           
: Gooooooooooooooaaaaaaaallllll!!
G 1                              
o 14                             
a 8                              
l 6                              
! 2

```Since that accurately counts all letters it is simply a matter of adjusting the exact display logic with a few ifs.  Or, if you're getting really fancy, throwing it all into a dict of lists and extracting the information from that dict as needed.

---

### Post by ratmandall on 2008-11-09
> **Greyed said:**
> Er, ok, since you put up code, here is what I was alluding to in my first reply.  A for loop, a placeholder and a counter...

[php]
def letters(word=''):      
    count = 1 # Counter   
    prev = '' # Placeholder
    for c in word: # For loop
        if c != prev:
            if prev: # Prevents printing the empty prev.
                print prev, count
            count = 1
            prev = c
        elif c == prev:
            count = count + 1
    else: # needed to print out the final letter's count
        print c, count

while 1:
    letters(raw_input(': '))
[/php]Results in the following.
```

{grey@igbuntu:~} python foo.py
: mississippi                 
m 1                           
i 1                           
s 2                           
i 1                           
s 2                           
i 1                           
p 2                           
i 1                           
: ragoo                       
r 1                           
a 1                           
g 1                           
o 2                           
: Gooooooooooooooaaaaaaaallllll!!
G 1                              
o 14                             
a 8                              
l 6                              
! 2

```Since that accurately counts all letters it is simply a matter of adjusting the exact display logic with a few ifs.  Or, if you're getting really fancy, throwing it all into a dict of lists and extracting the information from that dict as needed.

Actually yea that's sort of what I wanted I just realised my code is wrong because I didn't fully test it, thanks :D

---

