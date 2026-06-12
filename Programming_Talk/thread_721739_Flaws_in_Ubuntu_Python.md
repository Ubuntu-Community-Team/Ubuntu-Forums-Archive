---
title: "Flaws in Ubuntu Python?"
date: 2008-03-11
forum: Programming Talk
---

### Post by Allus on 2008-03-11
Hello. I'm running this Python code on Ubuntu Gutsy:

This is from Mark Lutz's book Programming Python -- adder.py:
===================
import sys
sum = 0
while True:
     try:
          line = raw_input()
     except EOFError:
          break
     else:
          sum += int(line)
print sum
====================(the code is indented properly - it just doesn't show here.)

Okay, now I have this data file -- data.txt

123
000
999
042
===================

At the command line I type:

$ cat data.txt | python adder.py

This is supposed to give me 1164.  Instead I get this error:

Traceback (most recent call last):
  File "adder.py", line 9, in <module>
    sum += int(line) 
ValueError: invalid literal for int() with base 10: ''

Now I spent quite sometime trying to figure out what I did wrong. And finally went to a Python forum where I was told there was nothing wrong with the code. It worked for everyone else. Had to be me. 

Confused I went to my WinXp box. Sure thing. The code ran fine. That box is a dual boot with Kubuntu Feisty Fawn.  I tried the code there. Same error as on the Ubuntu Gutsy box.  I have one more computer that is a dual boot win98/Zenwalk    I tried it on Zenwalk.  The code ran fine -- just as on WinXp.

So, now I'm wondering if there is something wrong with the Python builds in Ubuntu/Kubuntu?  Or what else could this be?:confused:

---

### Post by dwblas on 2008-03-11
The error is here probably
sum += int(line)
try
sum += int(line.strip())     ## remove "\n"
if that doesn't work you'll have to print the ord() of each character in the offending line to see what is there that you obviously don't know about.  With anything like this, it is good to test for line.isdigit() and print a message if the string/line returns False.

The following means that you passed something that wasn't an integer in line 9.  Perhaps an EOF or an empty string?  In any case, if you test for "int-ness" first and print a message if it fails, the program will work as expected.
File "adder.py", line 9, in <module>
sum += int(line) 
ValueError: invalid literal for int() with base 10:

---

### Post by LaRoza on 2008-03-11
In the sticky, there is a guide for posting on the forum. It may help in future posts of code (and it will certainly help in reading it)

---

### Post by pmasiar on 2008-03-11
...if you add [code] tag :-)

---

### Post by WW on 2008-03-11
Your example, formatted like this:
```

import sys

sum = 0
while True:
    try:
        line = raw_input()
    except EOFError:
        break
    else:
        sum += int(line)
print sum

```
works for me (on Ubuntu 7.10, python 2.5.1).

---

### Post by bvmou on 2008-03-11
I think Lutz may be demonstrating things about strings and error handling.  Keep in mind that raw_input() [which will be deprecated in the next version of Python] always saves a string.  In this case your int(rawinputstring) takes that string and makes it back into an integer.  If your integer has a newline attached to it, you may get a formatting error in Linux.  The likeliest reason your Windows installation works better is that Python on Win32 is configured to handle newlines differently (newlines on Windows being a bit more complicated and unpredictable.)

In any case, this works for me:

```
import sys
sum = 0
while True:
	try:
		line = raw_input()
		sum += int(line)
	except EOFError:
		break

print sum
```

A better way, or one less likely to produce errors, might be:

```
data = open('data.txt')
data = data.readlines()
data = [int(item) for item in data]
sum = 0
for item in data:
	sum += item
print sum
```

int(item) works for me, and int(item[:-1]) will definitely work, ie, it will go from the zeroeth to the next-to-last character in a string, which will remove newlines if you know they are present.

---

### Post by Allus on 2008-03-11
> **WW said:**
> Your example, formatted like this:
```

import sys

sum = 0
while True:
    try:
        line = raw_input()
    except EOFError:
        break
    else:
        sum += int(line)
print sum

```
works for me (on Ubuntu 7.10, python 2.5.1).

First let me apologize to everyone for posting the code the way I did. In the future I'll use the PHP tags. 

WW, this really gets me.  That code is the exact way I run it on Ubuntu Gutsy and Kubuntu Feisty.  The same version.  But I get the aformentioned error.  

Now, in trying to take dwblas' advice and experimenting, I went back to my data file and altered it.  I removed the last return so that the cursor would be right at the end of the number 024 instead of at the begining of the line below it. This made it so the program worked. 

Is this something you did also?  

Either way, I have to wonder about the coincidence that this would happen on both the Ubuntu and Kubuntu systems, but not Windows or Zenwalk.

---

### Post by WW on 2008-03-11
An extra return character at the end of the file (or any blank lines in the file) will cause the error.  line will be an empty string, and then int generates the error.

For example
> 
>>> int('')
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
ValueError: invalid literal for int() with base 10: ''
>>> 


---

### Post by Allus on 2008-03-11
Well, thanks all for your replies.  Actually what Lutz was trying to achieve in this section of his book was redirection and piping.  This little predicatment of mine was just a distracting byproduct.  Interesting to hear that raw_input will be deprecated. 

All the examples offered give me the same results:  If I put a return character behind the last input item I get the error.  If I leave the cursor right behind the last data item, (Instead of on a new line), the program works.

Now, I understand that Windows attaches \r\n and linux just \n  but that really does not explain what is going on here.

I have access to a BackTrack 3.0 Operating System and tried the scripts on there. The scripts work fine with the last newline character.  So, the scripts work on Windows, zenwalk and backtrack  but not Ubuntu or Kubuntu.

Both Zenwalk and Backtrack are slackware distros of linux.  So the issue seems to be with Debian/Gnu and not linux per se.

---

### Post by WW on 2008-03-11
> **Allus said:**
> 
All the examples offered give me the same results:  If I put a return character behind the last input item I get the error.  If I leave the cursor right behind the last data item, (Instead of on a new line), the program works.

This might depend on which editor you use.  For both of the cases (cursor right behind the last character or on a new line), try the command **hexdump -c file**.  For example,
> 
$ cat data.txt
123
000
999
042
$ hexdump -c data.txt
0000000   1   2   3  \n   0   0   0  \n   9   9   9  \n   0   4   2  \n
0000010
$ 


---

### Post by dwblas on 2008-03-11
> All the examples offered give me the same results: If I put a return character behind the last input item I get the error. If I leave the cursor right behind the last data item, (Instead of on a new line), the program works.That's because the last record in the file is empty and Python is doing this correctly.  It should tell you If you send something and it doesn't know what to do.  Try this modification with a print statement added.  It should make it obvious that the last line is empty and is causing the problem.  You have a problem because you are using a file with an empty string not because you are using Ubuntu.  The other people who tested this code were not piping a file into the program as input.  As a clue for future use, if you are the only one having the problem, then it is not the OS, computer, or phase of the moon.  It is you.  You can only solve a problem if you can define what the problem is.```
import sys

sum = 0
while True:
    try:
        line = raw_input()
    except EOFError:
        break
    else:
        print "adding", line, "to sum"
        sum += int(line)
print sum
```

---

### Post by pmasiar on 2008-03-12
> **Allus said:**
> Interesting to hear that raw_input will be deprecated. 

raw_input() will become input() in Py3K, and you can make equivalent of today's input by eval(input()) in Py3K. 

BTW it was a fight to keep input(), Guido wanted to drop it and to place all I/O functions into io module, but arguments for beginners persuaded him to keep input() in core buildin functions :-)

---

### Post by Allus on 2008-03-12
> **WW said:**
> This might depend on which editor you use.  For both of the cases (cursor right behind the last character or on a new line), try the command **hexdump -c file**.  For example,

WW:  Well, I was using gedit on Ubuntu, Kate on Kubuntu, Kwrite on backtrack and geany on zenwalk.  So, I downloaded geany on the Ubuntu system and recreated the data.txt file.  You are right.  The program worked despite the last character being a return character.  So the editor plays a factor here.  I would not have thought of that because I thought programs like Kate and especially gedit would be okay for these files.  I guess Ill have to play around with the hexdump on different editors. Thanks.

dwblass:  Yes, I did something similar to your suggestion last night, that's how I caught on that an extra character was being processed. I was wondering why I was the only one having this problem, but i never suspected the phase of the moon would have anything to do with it.

pmasiar:  Thanks for the info.  Using eval() I hear can be dangerous.  I'll have to gain more knowledge of that before I use it.

---

### Post by Allus on 2008-03-12
Yeppers.  In geany:

allus@Bardot:~/pyc$ cat data.txt
123
000
999
042
allus@Bardot:~/pyc$ hexdump -c data.txt
0000000   1   2   3  \n   0   0   0  \n   9   9   9  \n   0   4   2  \n
0000010

And in gedit:

allus@Bardot:~/pyc$ cat data.txt
123
000
999
042

allus@Bardot:~/pyc$ hexdump -c data.txt
0000000   1   2   3  \n   0   0   0  \n   9   9   9  \n   0   4   2  \n
0000010  \n                                                            
0000011
allus@Bardot:~/pyc$ 

I guess I could have also seen this just in the way the gedit file created an extra line in the cat output.

Thanks again.

---

### Post by pmasiar on 2008-03-12
> **Allus said:**
> pmasiar:  Thanks for the info.  Using eval() I hear can be dangerous.  I'll have to gain more knowledge of that before I use it.

Yes, but current input() does eval for you :-) raw_input() does not.

---

### Post by Allus on 2008-03-12
> **pmasiar said:**
> Yes, but current input() does eval for you :-) raw_input() does not.

So, could you just use sys.stdin.read()   ?

---

### Post by pmasiar on 2008-03-12
> **Allus said:**
> So, could you just use sys.stdin.read()   ?

to do what? Either one has it's use:

- if you need input string as-is, use raw_input()
- if you ie want to convert numbers to values, or if you defined string constants you want interpreted, or any other eval tricks - use input(). 

Either one gives you prompt, sys.stdin.read() IMHO does not.

Do whatever makes sense, I just mentioned that if someone is afraid of eval(), input() does eval() "behind the scenes" with the same results. Safer is to use raw_input(), and check it for sanity/validity before evaluating, but YMMV.

---

