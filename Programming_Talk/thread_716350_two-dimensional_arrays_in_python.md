---
title: "two-dimensional arrays in python"
date: 2008-03-05
forum: Programming Talk
---

### Post by pytheas22 on 2008-03-05
I'm an absolute beginner in python (but a dedicated Ubuntu user!) and am stuck.  I want to create a two-dimensional array to represent the following data, which represents a scrabble board:

```
G..BLEEP......Q
I..A........C.U
BUNT........O.I
E..E...J....RAX
.UNDERDOG.NO.NO
OP.....U.ZA...T
.......SCAMSTER
F......T......Y
LADYLIKE.......
AW....ADO......
TA...ES.MITE..V
F..........HAIR
I...........I.O
S..........VROW
HEIR..........S
```

Each character of each line should be put into an array, and then those arrays should be combined, so that arr[0][0] = G, arr [1][0] = ., arr [0][1] = I and son.

I have written the following code to try to do this but it's not working.  It seems to add each line to a separate array, but each of those arrays is empty, and I can't figure out what's wrong:

```
import sys
from itertools import izip

#define files to open
dictfile = open('sowpods.txt','r')
startfile = open(sys.argv[1],'r')

#create dict from dictfile
k = range(1,9999999)
d = dict(izip(k,dictfile))

#create two-dimensional array
arr = []
for line in startfile.readlines():
    arr.append([])
    for square in startfile.readline():
        arr[line].append(line+square)
```


('startfile' is the variable name given to the file containing the scrabble board layout, given as a command-line argument.)

I don't understand why the "for square in startfile.readline()" line does not appear to be doing anything.  Any hints would be greatly appreciated.

---

### Post by imdano on 2008-03-05
My guess is that after running startfile.readlines() python has reached the EOF, so calling readline() won't return anything.  You have to reset your position in the file (using seek() or closing/opening the fil again) before calling readline().

edit: There are a few other problems with your code, though.  Something like this would be more efficient.
[php]#create two-dimensional array
arr = []
for line in startfile.readlines():
    littlearr = []
    for letter in line.strip():
        littlearr.append(letter)
    arr.append(littlearr)
[/php]

---

### Post by pmasiar on 2008-03-05
You don't have to use readlines() when iterating, ```
for line in startfile:
``` is enough.

You can also use dictionary with keys - tuples, to get multi-dimensional arrays.

[PHP]board = {}
board[1,2] = 'A'[/PHP]

Check also setdefault(), it is intended to be used in such situations, instead of your's arr.append([])

> I don't understand why the "for square in startfile.readline()" line does not appear to be doing anything. 

You should not read from the same file inside loop where you already read the line. Internal loop will read up all file, external loop will iterate only once. And you cannot use 'line' as index in array[] -- you need some integer counter, or just append.


This is brute force, not tested :-)
[PHP]board = {}
row = 0
for line in open(sys.argv[1]):
   column = 0
   row += 1
   for cc in line:
      board[row, column] = cc
      column +=1[/PHP]

---

### Post by slavik on 2008-03-05
Are you building up every row by appending a single letter on every iteration inside a loop?

---

### Post by pytheas22 on 2008-03-05
Thanks so much for all of the replies.

> Are you building up every row by appending a single letter on every iteration inside a loop?

I guess that's what I was trying to do, but I realize now that there are much better ways to go about this.

```

board = {}
row = 0
for line in startfile:
   column = 0
   row += 1
   for cc in line:
      board[row, column] = cc
      column +=1
```

This code works well, and I understand why it's such a better way to do this.  I guess there's still more that I need to learn about arrays in python.  Thanks for the help with the basics of the language; I will see if now I can finish the rest of what I need to do.

---

### Post by Wybiral on 2008-03-05
You could always just use a list comprehension...
```

board = []
for line in open(sys.argv[1]):
    board.append([x for x in line])

```

Heck, since this is so small, you could even use list comp for both:
```

board = [[x for x in line] for line in open(sys.argv[1])]

```

---

### Post by slavik on 2008-03-05
at least you're not doing it with strings in Java (are strings immutable in Python?)

---

### Post by Wybiral on 2008-03-05
> **slavik said:**
> at least you're not doing it with strings in Java (are strings immutable in Python?)

Strings are immutable in Python, but the OP is using lists (or as pmasiar pointed out that dictionaries could also be used) which are not immutable.

---

### Post by nanotube on 2008-03-05
and by the way... no reason to loop over characters in a line, when the following works:
```
>>> list("blabla")
['b', 'l', 'a', 'b', 'l', 'a']

```

so, you could do the following:
```
mylist = []
for line in open(sys.argv[1]):
    mylist.append(list(line))

```

or if you like list comprehensions (thanks wybiral for bringing these up), 
```
mylist = [list(line) for line in open(sys.argv[1])]
```

heh, once the answer to a question is down to a simple one-liner, you know it's solved. :)

---

### Post by Wybiral on 2008-03-06
> **nanotube said:**
> and by the way... no reason to loop over characters in a line, when the following works:
```
>>> list("blabla")
['b', 'l', 'a', 'b', 'l', 'a']

```

Good point! In fact, any time you need "[i for i in iterable]" it could easily be replaced with "list(iterable)". I always seem to forget that (especially when dealing with generators and the like).

---

### Post by pytheas22 on 2008-03-06
Thanks for the other replies too, which give me even better ideas on how to write good code.

I'm trying now to write a routine to test if the horizontal words on the board are in a wordlist file, represented by 'd'.  In principle, the routine should work by cycling through each square (board[p][q]) of each line on the board, and every time it finds a square with a letter in it, it adds that value to the string 's'.  When it determines that the next square on the line (board[p][q+1] does not have a letter in it (e.g. we are at the end of a word), it will check to see if string s is in wordlist d, and print output accordingly.  For the time being I'm treating single letters as words.

I think I'm close to getting it to work (but who knows), but I'm running into a few problems that I can't get past, although I imagine that they are simple issues.  First, I can't figure out how to append each new letter to s so that it forms a string, as opposed to an array--in other words, print s gives "['B', 'L', 'E', 'E', 'P']" when I want "BLEEP"

Second, it's not including the last square on the line--instead it's complaining about the list index being out of range--and I'm not sure why the value of board[p][q] is out of range when it gets to the last character of the line, as it looks to me like it should still be in range.

Third, as you can see from the code, I am trying to make this routine cycle through every line on the board, by increasing the value of p after getting to the end of the line, but this also is not working and I am not sure what's wrong with it.

If anyone has time to offer suggestions on what I need to do to get past these problems, I would really appreciate them.  I apologize because I know that I'm asking very basic stuff, but I've worked at this for several hours and still can't get past these issues, and as I said earlier, I have very little experience in programming, so I hope you'll all excuse the dumb questions.

Here is the code I have:
```

import sys
from itertools import izip
import string

#define files to open
dictfile = open('sowpods.txt','r')
startfile = open(sys.argv[1],'r')

#create dict from dictfile
d = []
for line in dictfile:
    line = line.strip('\n')
    d.append(line)

#create a dictionary pairing squares on the board
board = []
for line in startfile:
    board.append([x for x in line])

p = 0
q = 0
s = []
for p in range(16):
    for i in range(16):
        if board[p][q] != '.':
            s += board[p][q]
            if board[p][q + 1] == '.':
                print s
                if s in d:
                    print 'Word is in the dictionary!'
                else:
                    print 'Word is not in the dictionary!'
            q = q + 1
             
        else:
            print s
            q = q + 1
            s = []    
    s = []    
    p = p + 1
    print p
```

---

### Post by pytheas22 on 2008-03-06
Alright, after looking closely again, I realized that the out-of-range problem was caused because q was not being reset to 0 when the end of the line was reached.  So this solves problem #3--now it cycles through every line--and I no longer get an error about any keys being out of range; nonetheless, the routine is still apparently failing to look at the last square of every line, so problem #2 is still relevant.  I also still have the problem with not understanding how to make s a string.  My new code is below.

By the way, please don't hesitate to suggest ways to make the code better, beyond just making it work.  Learning to write as cleanly and efficiently as possible is important to me.

```
import sys
from itertools import izip
import string

#define files to open
dictfile = open('sowpods.txt','r')
startfile = open(sys.argv[1],'r')

#create dict from dictfile
d = []
for line in dictfile:
    line = line.strip('\n')
    d.append(line)

#create a dictionary pairing squares on the board
board = []
for line in startfile:
    board.append([x for x in line])

p = 0
q = 0
s = []
while p < 15:
    for i in range(15):
        if board[p][q] != '.':
            s += board[p][q]
            if board[p][q + 1] == '.':
                print s
                if s in d:
                    print 'Word is in the dictionary!'
                else:
                    print 'Word is not in the dictionary!'
            q = q + 1
             
        else:
            print s
            q = q + 1
            s = []    
    s = []    
    p = p + 1
    q = 0
    print p
```

---

### Post by Can+~ on 2008-03-06
> **pytheas22 said:**
> Thanks for the other replies too, which give me even better ideas on how to write good code.

I'm trying now to write a routine to test if the horizontal words on the board are in a wordlist file, represented by 'd'.  In principle, the routine should work by cycling through each square (board[p][q]) of each line on the board, and every time it finds a square with a letter in it, it adds that value to the string 's'.  When it determines that the next square on the line (board[p][q+1] does not have a letter in it (e.g. we are at the end of a word), it will check to see if string s is in wordlist d, and print output accordingly.  For the time being I'm treating single letters as words.

I think I'm close to getting it to work (but who knows), but I'm running into a few problems that I can't get past, although I imagine that they are simple issues.  First, I can't figure out how to append each new letter to s so that it forms a string, as opposed to an array--in other words, print s gives "['B', 'L', 'E', 'E', 'P']" when I want "BLEEP"

String -> List
[PHP]mylist = list(mystring)[/PHP]

List -> String
[PHP]import string
mystring = string.join(mylist, '')[/PHP]

Since you'r working a lot with strings and lists, you should probably have two tabs with this to pages open:
[http://docs.python.org/lib/string-methods.html](http://docs.python.org/lib/string-methods.html)
[http://docs.python.org/lib/typesseq-mutable.html](http://docs.python.org/lib/typesseq-mutable.html)

Also, if you want a quick reference of what is inside a certain library or instance of string/List use dir:
[PHP]print dir(string) #Prints the content of the string library[/PHP]

---

### Post by WW on 2008-03-06
It looks like s can be a string instead of a list.  Why not change each occurrence of **s = []** to **s = ''**?  The statement **s += board[p][q]** will still work--it will append the character to the end of the string.  Then **print s** works the way you want it to.

If you want to keep s as a list, then, as Can+~ suggests, you can use the string **join** function.

---

### Post by pytheas22 on 2008-03-06
Thanks to all for the responses.  I've finally written a script that works!  

I have however one small question: in order to get the routine that checks whether words on the scrabble board are in the dictionary or not to work, I want to append a '.' to the end of each line in the board configuration file, as well as a line of periods to the end of the file--this solves problem # 1 above--before cycling through the file.  In other words, I want to take the configuration file and make it look like this:
```

G..BLEEP......Q.
I..A........C.U.
BUNT........O.I.
E..E...J....RAX.
.UNDERDOG.NO.NO.
OP.....U.ZA...T.
.......SCAMSTER.
F......T......Y.
LADYLIKE........
AW....ADO.......
TA...ES.MITE..V.
F..........HAIR.
I...........I.O.
S..........VROW.
HEIR..........S.
...............
```

I've figured out a dirty way to do this by using the os.system function to call some bash commands, as you can see from the snippet below:
```

#append sentinel '.' to startfile
os.system("sed -i 's/$/./' start.conf") #dirty solution, plus need to figure out how to make sed take take an argument from the command-line
os.system("echo '...............' >> start.conf") #also pretty dirty

#define files to open
dictfile = open('sowpods.txt','r')
startfile = open(sys.argv[1],'r')
```

There are two problems with this:
1. I'm sure going to a sub-shell like this inefficient and that there's a better way to do it, which I would prefer as long as it's not too complicated (I tried playing around with 'write' but it seems more complicated than it needs to be for such a simple task)
2. if I leave things the way they are, then I need to figure out how to replace 'start.conf' in the bash commands with the first argument given when the python script is called, so that this script would work regardless of the name of the board configuration file.  In other words, ```
os.system("sed -i 's/$/./' start.conf")
```

should look more like
```

os.system("sed -i 's/$/./' [FIRST COMMAND-LINE ARGUMENT")
```

but I don't know if there's a way to do that using os.system.

Thanks in advance for any help in wrapping up this script, and thanks again for all of the help already provided.

---

### Post by nanotube on 2008-03-07
> **Can+~ said:**
> 
List -> String
[PHP]import string
mystring = string.join(mylist, '')[/PHP]


according to python style guides, this should be done as follows:
```
''.join(mylist)
```
since the "string" module is considered deprecated (and the docs claim it may be removed in python 3)
all the string module functions are methods of string objects.

---

### Post by mssever on 2008-03-07
> **Can+~ said:**
> List -> String
[php]import string
mystring = string.join(mylist, '')[/php]
Or ```
mystring = ''.join(mylist)
```No need to import string for this operation.
> **pytheas22 said:**
> Thanks to all for the responses.  I've finally written a script that works!  

I have however one small question: in order to get the routine that checks whether words on the scrabble board are in the dictionary or not to work, I want to append a '.' to the end of each line in the board configuration file, as well as a line of periods to the end of the file
You could do something like ```
for row in board:
    row.append('.')
board.append(list('.' * len(board[0])))
```I don't know Python too well, so I'm not positive that this exact code will work; if it doesn't, it probably isn't too far off.

However, you shouldn't have to add dots to the board. A better solution would be to adjust your search code so that it knows that the end of the list is also the end of any word, with or without a dot.
>  ```
os.system("sed -i 's/$/./' [FIRST COMMAND-LINE ARGUMENT")
```
Try ```
os.system("sed -i 's/$/./' %s" % sys.argv[0])
```I don't know whether the first command line argument is sys.argv[0] or sys.argv[1] in Python. Python makes extensive use of printf format strings such as this. It'd be good to learn printf well.

---

### Post by pmasiar on 2008-03-07
> **mssever said:**
> You could do something like ```
for row in board:
    row.append('.')
board.append(list('.' * len(board[0])))
```I don't know Python too well, so I'm not positive that this exact code will work; if it doesn't, it probably isn't too far off.


It certainly looks valid.

That's beauty of Python: There one obvious way to do it right. It just makes sense, even if you did not programmed in Python 6 months, is easy to jump back in. If you did not touch your Perl code for 6 months, it looks almost as alien as if written in Klingon! :-)

---

### Post by stevescripts on 2008-03-07
> **pmasiar said:**
> 

 ,,, If you did not touch your Perl code for 6 months, it looks almost as alien as if written in Klingon! :-)

Well said!  

Steve :lolflag:

---

### Post by slavik on 2008-03-07
> **pmasiar said:**
> It certainly looks valid.

That's beauty of Python: There one obvious way to do it right. It just makes sense, even if you did not programmed in Python 6 months, is easy to jump back in. If you did not touch your Perl code for 6 months, it looks almost as alien as if written in Klingon! :-)
I will have you know that I am fluent in Klingon ...

---

### Post by Can+~ on 2008-03-07
> **nanotube said:**
> according to python style guides, this should be done as follows:
```
''.join(mylist)
```
since the "string" module is considered deprecated (and the docs claim it may be removed in python 3)
all the string module functions are methods of string objects.

Crap, all this time looking at the documentation on strings, and I didn't notice the "DEPRECATED" on top. Silly me, that's what happens when you drag things from other language (started with ol' C)

---

### Post by pmasiar on 2008-03-07
> **slavik said:**
> I will have you know that I am fluent in Klingon ...

I am not surprised, I half-expected that: knowledge of Klingon is requirement to love Perl with the passion you do :-)

---

