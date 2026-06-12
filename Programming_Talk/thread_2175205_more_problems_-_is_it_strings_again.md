---
title: "more problems - is it strings again?"
date: 2013-09-18
forum: Programming Talk
---

### Post by linuxonbute on 2013-09-18
Hi guys,
i posted earlier about strings here:  [http://ubuntuforums.org/showthread.php?t=2174873](http://ubuntuforums.org/showthread.php?t=2174873)
But since then my wife has been playing 4 pics 1 word on her android phone and sometimes it's hard for us to guess the right word.
Anyone who has played it knows you cannot move on until you do.
Well as it's a similar problem to what I was going to tackle i have started on that annd now I have what is, to me, a very strange problem. Here is some code to let to see what I mean'
```


#!/usr/bin/python

from time import sleep

def three(wl):
    for a in range(0, tot - wl) :
        for b in range (a + 1, tot + 1 - wl) :
            for c in range(b + 1, tot + 2 - wl) :
                print  str(a) + " " + str(b) + " " + str(c)
                print  word1[a] + word1[b] + word1[c]
    return 



def five(wl):
    for a in range(0, tot - wl) :
        for b in range (a + 1, tot + 1 - wl) :
            for c in range(b + 1, tot + 2 - wl) :
                for d in range (c + 1, tot + 3 - wl) :
                    for e in range(d + 1, tot + 4 - wl) :
                         print str(a) + " " + str(b) + " " + str(c) + " " + str(d) + " " + str(e)
                         print word1[a] + word1[b] + word1[c] + word1[d] + word1[e]
    return


word1 = 'abcdefghijkl'
wl = 4
tot = len(word1) + 1
counter = 0
thisVar = "~"
newVar = ""
q = len(word1)
r = 0
three(3)
#sleep(2)
#four(wl)
#sleep(2)
#five(5)



```

IF I run it so it calls the function three it works as expected:
> 

 0 1 2
abc
0 1 3
abd
0 1 4
abe
0 1 5
abf
0 1 6
abg
0 1 7
abh
0 1 8
abi
0 1 9




If I run it with the call to five uncommented I get this:
> 
egijl
4 6 8 10 11
egikl
4 6 9 10 11
egjkl
4 7 8 9 10
4 7 8 9 11
ehijl
4 7 8 10 11
ehikl
4 7 9 10 11
ehjkl
4 8 9 10 11
eijkl
5 6 7 8 9
5 6 7 8 10
5 6 7 8 11
fghil
5 6 7 9 10
5 6 7 9 11
fghjl
5 6 7 10 11
fghkl
5 6 8 9 10
5 6 8 9 11
fgijl




Now I have actually functions which cover word 3, 4, 5, 6 and seven characters long
but only calls to three and four work correctly. The others exhibit the same problems as shown for the call to five.
Last time I did miss something obvious - I am only a beginner - but I cannot spot it this time.
Any ideas please.

---

### Post by r-senior on 2013-09-18
Is it just that it is generating so much output that you can't scroll back to the beginning? If I run it with the five function uncommented, the first lines look as I think you expect:

```
$ ./words.py | head -10
0 1 2 3 4
abcde
0 1 2 3 5
abcdf
0 1 2 3 6
abcdg
0 1 2 3 7
abcdh
0 1 2 3 8
abcdi
```

Did you know there is a function called permutations in the Python itertools library:

[http://docs.python.org/2/library/itertools.html#itertools.permutations](http://docs.python.org/2/library/itertools.html#itertools.permutations)

```
#!/usr/bin/env python

import itertools
import string
import sys

input = sys.argv[1]
length = int(sys.argv[2])

for permutation in itertools.permutations(input, length):
    print string.join(permutation, '')
```

Example:

```
$ ./words.py 'abc' 2
ab
ac
ba
bc
ca
cb
$ ./words.py 'abcdef' 3
abc
abd
abe
abf
acb
acd
ace
acf
...
```

---

### Post by linuxonbute on 2013-09-18
Hi,
No I didn't know about the function.
But the problem isn't about fast scrolling.
If I feed the output through less I can see it all.
The problem is that each iteration through the loops should be like this:
> 
fgijl
5 6 8 10 11



with one line of characters and one line of numbers but randomly I am getting:
> 

eijkl
5 6 7 8 9
5 6 7 8 10
5 6 7 8 11
fghil
5 6 7 9 10
5 6 7 9 11
fghjl
5 6 7 10 11
fghkl
5 6 8 9 10
5 6 8 9 11
fgijl
5 6 8 10 11
fgikl
5 6 9 10 11
fgjkl
5 7 8 9 10
5 7 8 9 11

So it's not printing the characters relating to each set of numbers which, of course relate to the original string.

If I just say what I ultimately want to do it might give everyone a better idea.
The game offers 4 pictures, a set of 12 characters and a set of blank spaces.
You tap each character in turn that you think fits the spaces, to end up the the word which links the 4 pictures.

I will input the 12 characters to the program and a number representing the number of letters in the word.
I have a text file with around 400,000 words in it.
Each iteration of the loop will also read in 1 word from the file, store a copy in another variable,re-arrange the letters in it alphabetically 
and compare it to the string I have generated in the loop. If they match then I will print out the stored word.

I think this will be a simpler way of getting a list of viable words although I am usually wrong:(
This should, I believe, give us a list of words and we should then be able to feed the correct one into the game.

---

### Post by linuxonbute on 2013-09-18
Well I can't believe this!!!
I have been using gedit to type in the program and it has been wrapping round  on line length on screen which, in part, was due to tabs being set to 8 characters.
So I changed it in the editor preferences to 3 characters. i also changed the font size from 18 to 14.
I did absolutely nothing else but when I ran the program it dropped out with an error in 'seven' relating to indentation on the character printing line.
I corrected it and then got the same error for 'six' which I corrected and then the same for 'five'
Now it does run as it should so what on earth is happening???

---

### Post by spjackson on 2013-09-18
> **linuxonbute said:**
> 
with one line of characters and one line of numbers but randomly I am getting:
```

eijkl
5 6 7 8 9
5 6 7 8 10
5 6 7 8 11
fghil
5 6 7 9 10
5 6 7 9 11
fghjl
5 6 7 10 11
fghkl
5 6 8 9 10
5 6 8 9 11
fgijl
5 6 8 10 11
fgikl
5 6 9 10 11
fgjkl
5 7 8 9 10
5 7 8 9 11                      

```
So it's not printing the characters relating to each set of numbers which, of course relate to the original string.

I am not seeing that at all. For me the five function prints a line of letters then a line of numbers throughout.
```

$ ./words.py > words.out
$ wc -l words.out
1584 words.out
$ egrep '^[0-9]' words.out | wc -l
792
$ egrep '^[a-z]' words.out | wc -l
792

```
i.e. 1584 lines of output, half of which begin with a letter, and half of which begin with a number. Looking at the output file, I don't spot any erroneous patterns either.

What you are seeing would appear to relate to terminal display rather than the output of your program.

---

### Post by linuxonbute on 2013-09-18
Well thanks for the idea but i think it was related somehow to do with something the editor was doing when the text from a line ( as displayed ) wrapped round to the next line because The output was run in the same instance of the terminal program before and after the change. Unfortunately since the problem was occurring update manager has done an automatic update and now I can't reproduce the problem. Once again the same instance of the terminal has been running, in fact it is the same one as was running yesterday as I left the laptop on all night as I was doing a backup. I tried setting the font back to the original size and tabs to 8 characters but it still runs without problems.
Ah well at least it works.
Thanks for the support guys.

---

### Post by trent.josephsen on 2013-09-18
Ok, so I don't know how gedit works, but it's obvious to me that some combination of spaces and tabs, in your original file, led Python to be confused about the intended indentation of your code. Changing the tab size wouldn't have done anything in $preferred_editor, but maybe gedit did some magical retabbing for you when you changed it to 3, or perhaps you forgot to save just before that and so were running a different version of the code until afterwards.

Regardless, this is why [PEP 8](http://www.python.org/dev/peps/pep-0008/) recommends using only spaces for indentation. Using tabs is fine too, but in Python you're asking for trouble if you mix them up, which is the default behavior for many editors (and can happen when you change indentation manually, too). I suggest turning off tabs, or setting gedit to use tabs exclusively, if such an option exists.

Finally, putting an empty 'return' at the end of a function that doesn't return anything is a little weird for Python. I'd leave it off.

---

### Post by spjackson on 2013-09-18
> **trent.josephsen said:**
> Ok, so I don't know how gedit works, but it's obvious to me that some combination of spaces and tabs, in your original file, led Python to be confused about the intended indentation of your code
That's a tempting theory, because it is often a cause of bugs in Python code, but... out of the possible permutations of the indentation of the two print lines, I am pretty sure that none of these could produce the example output.

I don't disagree with your recommendations, but I don't think that indentation errors can explain the evidence given.

---

### Post by linuxonbute on 2013-09-18
Okay thanks for the info. In gedit it is possible to set tab to issue a number of spaces rather than tab characters.
I made a backup of what I have got and tried it. It seems to work so I will stick to that.
Thanks again.

---

### Post by trent.josephsen on 2013-09-18
> **spjackson said:**
> That's a tempting theory, because it is often a cause of bugs in Python code, but... out of the possible permutations of the indentation of the two print lines, I am pretty sure that none of these could produce the example output.

I don't disagree with your recommendations, but I don't think that indentation errors can explain the evidence given.

Hrm, yeah, on reflection you may be right... hard to say for sure. My mistake, if so. In any case, the code as posted does not exhibit such behavior, so I'm still inclined to blame some kind of formatting problem.

---

### Post by trent.josephsen on 2013-09-19
Nope, I was right the first time:
```
def five(wl):
    for a in range(0, tot - wl) :
        for b in range (a + 1, tot + 1 - wl) :
            for c in range(b + 1, tot + 2 - wl) :
                for d in range (c + 1, tot + 3 - wl) :
                    for e in range(d + 1, tot + 4 - wl) :
                         print str(a) + " " + str(b) + " " + str(c) + " " + str(d) + " " + str(e)
                    print word1[a] + word1[b] + word1[c] + word1[d] + word1[e] # this line unindented one level
    return
```
This code does print that sequence, near the end. It wasn't clear in the OP whether or not the posted output was all the output, so I imagine this was probably the mistake.

Significant indentation is definitely one of Python's few real "gotchas" for newbies. It's easy to let your editor handle the indentation, but some editor settings will break it and in some cases silently change the semantics of the code. (And silent bugs are the worst bugs.)

---

