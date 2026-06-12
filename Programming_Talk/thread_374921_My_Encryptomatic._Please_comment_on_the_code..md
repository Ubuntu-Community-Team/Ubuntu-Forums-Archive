---
title: "My Encryptomatic. Please comment on the code."
date: 2007-03-03
forum: Programming Talk
---

### Post by Darkness3477 on 2007-03-03
Well, i was working on this in Java, but after one persons praises about Python, I decided to try it out again. 

Anyway, I designed this in a matter of... an hour or more. Mostly 'cause I'm watching Richie Rich and I'm having to search on google every 10 seconds to find out how to do something...

Whilst I always thought Python was a reasonable language, and pretty easy to use(used it for some really trivial stuff). I didn't realise just how easy it was. I've got the code down to 44 lines, and I have some whitespace I could delete out, wheras my vb.net code was around 100 lines or so... but I think i could of possibly done that in a stuffed up way. I programed pretty much the exact program in vb.net, but it used a gui.

Anyway, don't laugh at the encryption method. I know it's nooby, but it'll do for now. I'm looking into using ROT13. Someone told me about it on these forums yesterday and I think I might use it.. Anyway. I'm posting this here for you guys to comment on ( if you feel like it, anyway) my coding skills (Which are cruddy, I know) and my program. And well, in the highly unlikely event, someone could leech off of this. 

```

#Coded by Maver

#I need to make some error checking and what not, just to clear things up a bit
#but I'm just too damn lazy. If you're going to use it
#make sure you follow the prompts and don't try to decrypt a file that doesn't
#exist.

def encrypt():
    print "Enter the file you wish to write to: "
    filelocal = raw_input("make sure it's a .txt: ")
    encrypt = raw_input("Enter the string you wish to encrypt: ")
    for char in encrypt:
        j = ord(char) * 3 + 3 / 2 + 1
        fileHandle = open ( filelocal, 'a' )
        fileHandle.write (str(j))
        fileHandle.write ("\n")
    fileHandle.close()

def decrypt():
    print "enter the encrypted file you wish"
    unencrypt = raw_input("to unencrypt ")
    plaintext = raw_input("What file do you want to save the plain/n too? ")
    fileHandle = open ( unencrypt, 'r' )

    fileList = fileHandle.readlines()

    for fileLine in fileList:
        fileHandle.close()
        i = 0
        length = len(fileList)
    fileHandle = open ( plaintext, 'a' )    
    while i < length:
        d =(int(fileList[i]) / 3 - 3 * 2 - 1 + 7)
        fileHandle.write (chr(d))
        i = i + 1


choice = input("1 for encryption, 2 for decryption: ")


if choice == 1:
    encrypt()

               
if choice == 2:
    decrypt()



```

---

### Post by dwblas on 2007-03-03
You are opening the "append to" file multiple times.  It should not be in the for loop.```

    fileHandle = open ( filelocal, 'a' )
    for char in encrypt:
        j = ord(char) * 3 + 3 / 2 + 1
        fileHandle.write (str(j))
        fileHandle.write ("\n")
    fileHandle.close()

```Also there are existing encryption programs for Python.  Pycrypt is one that I know of it you wish to see what has already done with it.

---

### Post by Wybiral on 2007-03-03
A few friendly suggestions on optimization (since you're just learning it doesn't matter, but since python is interpreted, it's usually good practice to optimize your code)

Use incrementation:
```

        i = i + 1

```
The above code should be replaced with:
```

        i += 1

```
Because the interpreter has to do less operations (thus it will be *slightly* faster)

Remove unnecessary conditions:
```

if choice == 1:
    encrypt()

if choice == 2:
    decrypt()

```
Should be replaced with:
```

if choice == 1:
    encrypt()

elif choice == 2:
    decrypt()

```
This is better because when choice is "1" it is a waste to check if it's "2" afterwards (because you know that it is already "1")

Avoid unnecessary function calls:
```

        fileHandle.write (str(j))
        fileHandle.write ("\n")

```
Should be replaced with:
```

        fileHandle.write (str(j) + "\n")

```
Because it only has to call the write function once.

Use the built in features:
```

    while i < length:
        d =(int(fileList[i]) / 3 - 3 * 2 - 1 + 7)
        fileHandle.write (chr(d))
        i = i + 1

```
Instead, use:
```

    for i in range(length):
        d =(int(fileList[i]) / 3 - 3 * 2 - 1 + 7)
        fileHandle.write (chr(d))

```
This is because it is always better to let the language do the work when you are using an interpreted language like python (because it's been optimized for that purpose)
In this case it also allows you to get rid of the "i = 0" a few lines above.

In fact, unless I'm seeing the indentations wrong, this loop:
```

    for fileLine in fileList:
        fileHandle.close()
        i = 0
        length = len(fileList)

```
Doesn't seem to do anything useful. You aren't changing the "fileHandle" the value of "i" or the value of "length" so having these inside the iteration is a waste of operations (and since "fileHandle" doesn't change, you're trying to close an already closed file!).

Of course, you don't need to worry about optimizing right now. But, you never want to waste any operations on unnecessary thing (especially since it's interpreted and you need all the speed you can get. That's why you should use the built-in "range()" instead of manual iteration, python was optimized for that)

But, other than optimization it looks fine. Good luck and enjoy python!

---

### Post by Darkness3477 on 2007-03-03
Dwblas: Yeah, I know that there are encryption programs made in Python and aware that I could incorporate a lot more into my program to make it quite a bit better, but this was just a project to bring together a few common programming things into one project and also to relearn a lot of Python that I have forgotton. Well, mostly I just forgot the very basic stuff which is all I new in the first place.

Also, thanks very much for pointing out the fact that I am opening the file multiple times. That'll be making the program quite a bit slower. But, considering I can't really measure how quick it's going at the moment (Soon as I enter the data in, it's done)... But still, best to get the hang of these things now.

Wybiral: Thank you very much for going through my code and providing a detailed analys of exactly where I can improve my code. That's the type of thing which I need. I *think* I can basically program. I just can't do it well. 

Also, I'm quite interested in how to optimize code for the best possible preformance. I find it very interesting how changing a line or two around can increase the speed. Of course I understand why sometime a line of code is slow compared to another (Comparing more things than you have too, doing more operations, etc).

So, thanks to both of you. I'll edit my code and fix it up after I've finished my pizza.

---

### Post by Wybiral on 2007-03-03
> **Darkness3477 said:**
> Dwblas: Yeah, I know that there are encryption programs made in Python and aware that I could incorporate a lot more into my program to make it quite a bit better, but this was just a project to bring together a few common programming things into one project and also to relearn a lot of Python that I have forgotton. Well, mostly I just forgot the very basic stuff which is all I new in the first place.

Also, thanks very much for pointing out the fact that I am opening the file multiple times. That'll be making the program quite a bit slower. But, considering I can't really measure how quick it's going at the moment (Soon as I enter the data in, it's done)... But still, best to get the hang of these things now.

Wybiral: Thank you very much for going through my code and providing a detailed analys of exactly where I can improve my code. That's the type of thing which I need. I *think* I can basically program. I just can't do it well. 

Also, I'm quite interested in how to optimize code for the best possible preformance. I find it very interesting how changing a line or two around can increase the speed. Of course I understand why sometime a line of code is slow compared to another (Comparing more things than you have too, doing more operations, etc).

So, thanks to both of you. I'll edit my code and fix it up after I've finished my pizza.

Some things are a little more complex than you'd probably like to hear...

For instance, why is "i += 1" faster than "i = i + 1" ?

Well...
The answer lies in how the python virtual machine processes that instruction. "i = i + 1" is actually preforming two operations.

First the virtual machine has to add "1" to "i" and then it moves that value into "i"

Using the increment operator "+=" the virtual machine only performs one operation, which is adding "1" to "i"

The "if" and "elif" thing really wouldn't affect the performance of that program, but imagine you had code that looked like this:
```

if a==1:
  # Do something
if a==2:
  # Do something else
if a==3:
  # Do something else

```
Imagine "a" did equal "1"... If you ran that set of conditions, it would check if "a" were "1", if so... It would do something. But, since nothing is telling the machine not to check if it is "2" or "3" it will!!! Naturally, WE know that it shouldn't, but the only way you can tell the machine NOT to check the other values is with "elif" (which means ELse IF)
```

if a==1:
  # Do something
elif a==2:
  # Do something else
elif a==3:
  # Do something else

```
That tells the machine that if "a" is "1" not to bother running the operations to check if it's "2" or "3"

This brings you to an even more interesting thing to keep in mind when you use "elif"...

Always check the condition that is MOST likely to occur first.

```

if CONDITION_A:
    # Do something
elif CONDITION_B:
    # Do something

```
If it's more probable for "CONDITION_B" to be true than "CONDITION_A" you are potentially wasting an operation by checking "CONDITION_A" first! Always check the most probable condition first.

As far as the "write" function goes... I'm willing to bet it takes more operations to send the parameters to the function and preform the function than it takes to concatenate (combine) two strings. So, instead of calling the function twice, concatenate the strings and call the function once.

About using "range()" over your own iterator... If you absolutely HAVE to use your own because of the structure of the program, then do it... But if you can, it is always better to let the language do its thing. Python's virtual machine is probably highly optimized for using "range()" with "for" so take advantage of their optimization because python is compiled, which means it's way of doing things is probably going to be faster than your way (since yours is being interpreted).

As a final note... These optimizations don't mean much in an average program where there's plenty of CPU to waste... But why not make it as fast as possible??? Also, you WILL notice the difference between non-optimized code and optimized code when you use lots of tight loops. If a set of operations is being called thousands of times, the speed decrease is accumulative. Calling one single non-optimized operation isn't going to make a difference, but when you throw it in a loop that iterates thousands of times... It will build up to be a huge difference.

A lot of people might say... "Write now, optimize later" and that makes sense to an extent... Don't make your code so optimized that it's unreadable and hard to manage! But also don't take that statement for granted and write crappy code when you have the option of making it more efficient.

But like I said... These are just tips for when you get better, you probably don't need to worry about them until you start writing serious programs that require more speed.

Once again... Always have fun! I love python, it's a great language (python, C, and C++ are some of my favorite hobbies)

---

### Post by pragmatine on 2007-03-04
Don't try to roll your own encryption algorithm - use a standard, STRONG, one such as Twofish [http://www.schneier.com/twofish.html](http://www.schneier.com/twofish.html)

---

### Post by Darkness3477 on 2007-03-04
Well, I was learning Java because we're soon to be using it in School and I like to be ontop of things. Especially since i'm the top in my class right now (I'm the only one who's actually programmed, meaning I can fly through the easy stuff we're currently doing). I'm also interested in making some simple games, and one that I can have on a website would be just... the Bee's knees. 

But yeah, Python's pretty nice to use. So, perhaps I'll just make a simple game using Python (when I've gone through the basics and increase my skills in programming) which is partly why I'm interested in fast, correct, code. Whilst the games I make might not be as CPU intensive as (Whatever the current cool game is) I'm assuming it'll still be pretty heavy.

Anyway, thanks. I'm gonna go search for a programming challenge to attempt, as I just don't know what I to code right now. I tried a Palindrome one last night. I got it to work with a simple string, but it doesn't ignore whitespace, punctuation or capital letters... It works with numbers, and if the number entered isn'it a palindrome, it prints the next one. I found the challenge on here somewhere. It was pretty easy to do, actually. Although it's pretty slow. I enterd a number with around 30 digits and it crashed. Might be because it's out of range of the integer, or I programmed it to be very slow. either way it was pretty fun to do.

pragmatine: I used my own simple because this was a learning excercise. It helped me learn how to use lists, read/write to a file and a few other things. I learn things far better by putting them into what I think is a real world application. Me learning about those things seperately would be fine, but as I've now put them altogether i feel that I have learned more than what I would have done any other way. 

It's not like i'm going to use this program for anything important. If i was going to use it for anything, it would be just to hide certain things from my parents. But, of course, they don't care what I use the computer for and don't know how to user Ubuntu. My mothers computing knowledge extends to her asking me to log in, open up OpenOffice and leaving her to type something up. Sometimes, she can even open it up for herself! Lol.

---

### Post by Wybiral on 2007-03-04
> **Darkness3477 said:**
> Well, I was learning Java because we're soon to be using it in School and I like to be ontop of things. Especially since i'm the top in my class right now (I'm the only one who's actually programmed, meaning I can fly through the easy stuff we're currently doing). I'm also interested in making some simple games, and one that I can have on a website would be just... the Bee's knees. 

But yeah, Python's pretty nice to use. So, perhaps I'll just make a simple game using Python (when I've gone through the basics and increase my skills in programming) which is partly why I'm interested in fast, correct, code. Whilst the games I make might not be as CPU intensive as (Whatever the current cool game is) I'm assuming it'll still be pretty heavy.

Anyway, thanks. I'm gonna go search for a programming challenge to attempt, as I just don't know what I to code right now. I tried a Palindrome one last night. I got it to work with a simple string, but it doesn't ignore whitespace, punctuation or capital letters... It works with numbers, and if the number entered isn'it a palindrome, it prints the next one. I found the challenge on here somewhere. It was pretty easy to do, actually. Although it's pretty slow. I enterd a number with around 30 digits and it crashed. Might be because it's out of range of the integer, or I programmed it to be very slow. either way it was pretty fun to do.

pragmatine: I used my own simple because this was a learning excercise. It helped me learn how to use lists, read/write to a file and a few other things. I learn things far better by putting them into what I think is a real world application. Me learning about those things seperately would be fine, but as I've now put them altogether i feel that I have learned more than what I would have done any other way. 

It's not like i'm going to use this program for anything important. If i was going to use it for anything, it would be just to hide certain things from my parents. But, of course, they don't care what I use the computer for and don't know how to user Ubuntu. My mothers computing knowledge extends to her asking me to log in, open up OpenOffice and leaving her to type something up. Sometimes, she can even open it up for herself! Lol.

lol, you should try the Da Vince algorithm... Just turn everything backwards. It's easy to do, and it makes executables non-executable... Text files look like Jargon and it's really easy to reverse.

All you need is a stack or list that you can read for backwards. Plus, the same algorithm that encrypts it, decrypts it, lol!

---

### Post by Darkness3477 on 2007-03-04
Would it be something like...
```
plaintext = raw_input("Please enter a string to encrypt :")
encrypted = plaintext[::-1]
....write code to file...
```

That's what I used to check if my string was a Palindrome (And numbers)... Although, if the numbers weren't a Palindrome, I printed the next one instead of writing out false. I should go edit my code so it allows for spacing and all that.... so Ere would be a Palindrome (capital letter makes it not a palindrome in my program)

---

### Post by dwblas on 2007-03-04
> I'm also interested in making some simple gamesPython has game creation sites and helps  When you are ready to try, Google will find them.

---

### Post by Darkness3477 on 2007-03-05
Yeah, I know Python is pretty easy to create games when using Pygame.. However, "pretty easy" is pretty darn hard for me right now.

 I tried making a dot move around when using the curser keys and I couldn't even get that right. Perhaps because the tutorials I was using weren't very good... I dunno. Maybe I'm just missing something. Anyway, after I've firgured out how to move my little dot around the screenI think I might leave game programming there for awhile and continue with it after I've gathered a little more knowledge.

---

### Post by Tuna-Fish on 2007-03-05
Just a little hint towards making that encryptomatic a lot more useful:
raw_input() reads from standard input, print() writes to standard output. When coding for linux,  before implementing file handling, always remember that you can redirect pretty much anything in to a standard input, and you can redirect standard output to pretty much anything.

So, turn that file into a runnable script by adding the line ```
#! /usr/bin/python
``` and giving it execute rights. Then instead of reading from/printing to a file, just use raw_input() and print(), and stop the loop when raw_input() gets EOF. 

Thus, you can use the program by:
```
1. normally, interactively.
./program.py
#enter text to be encrypted
#encrypted text appears on screen.
#to quit, give EOF (ctrl-d)

2. with source and destination files
<source_file ./program.py > destination_file
#you can of course, choose to omit either: to get original functionality, don't give a source but give destination.
3. as a part of a pipe
ls|./program.py|some_other_command
#would encrypt a directory listing and feed it to something else.

```

The reason unix cmd-line is so powerful isn't because it's components are powerful, but because of the near-unlimited ways they can be combined. Unless you have a really pressing reason not to, always follow the two most important tenets of unix:
1. Do one thing and do it well
2. Play well with others (accept non-interactive redirected standard input, make sure your standard output is useful, ie has nothing but the data)

---

### Post by Tuna-Fish on 2007-03-05
Just to give a finished example:
```

#! /usr/bin/python
###################
# a wonderful encryptomatic
def f():
	#the actual encryption
while True:
	try:
		a = raw_input()
		print(f(a))
	except EOFError:
		break

```

That's all the file handling a properly coded unix filter needs, in 6 lines!

---

### Post by Darkness3477 on 2007-03-05
Hey, thanks for the example. I'll look into it and fix it up when I've finished my english homework.

---

