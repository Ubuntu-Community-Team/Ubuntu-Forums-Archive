---
title: "python error"
date: 2011-07-29
forum: Programming Talk
---

### Post by rpmp on 2011-07-29
ok here the problem im learning python programing and im having an error in terminal sayng that error line 40 unexpected indent.  here the code

Code:
```
#this is a guessing game
#im also gonna explain it to you doc with these comments that are blue 

#only imports we will use are , random, those are the imports
import random

#this will tell the computer how many times u guessed doc
guessestaken = 0

#every print means what the computer says doc and input it what ur sayng
print("Eeh whats up doc? tell me your name doc" )
myname = input()

#this doc will the numbers u can try to guess but only one is right
number = random.randint(1, 20)
print("Well" + myname + "im a thinking of a number between 1 and 20")

#okay doc this says ur chances
while guessestaken < 6:
    print("take a guess doc")

#this says the guess u said
    guess = input()
    guess = int(guess)

#this says how many gueses u taken
guessestaken = guessestaken + 1

if guess < number:
        print("your guess is wrong doc")

if guess > number: 
        print("no doc still wrong")

if guess == number:
        break 

if guess == number:
    guessestaken = str(guessestaken)
        print("good job" + myname + "u guessed it in" + guessestaken + "guesses")

if guess != number:
    number = str(number)
        print("no doc that ain it")
```

---

### Post by Bachstelze on 2011-07-29
Please edit your message and wrap CODE tags around your code. Right now we can't see the indentation at all, so we obviously can't help you with your indentation problem.

---

### Post by rpmp on 2011-07-29
how exactcly do u do that? cause i  dont know.

wait i did it.

---

### Post by Arndt on 2011-07-29
> **rpmp said:**
> how exactcly do u do that? cause i  dont know.

wait i did it.

Obviously not.

You use the word CODE in brackets, or select the whole thing and press the # symbol at the tool bar at the top.

---

### Post by rpmp on 2011-07-29
what do u mean? i dont know how to do this

---

### Post by Arndt on 2011-07-29
> **rpmp said:**
> what do u mean? i dont know how to do this

If you reply to this post with the Quote button, you will see how the CODE tags are used in the little example below.

```
// this is code
a = b

```

---

### Post by oldfred on 2011-07-29
To edit with code tags easily after posting you have to use the advanced button and then you get the full menu in the edit panel at the top. On the right side of edit panel is #. If you highlight with mouse the code, then click #, it will put code tags before & after the highlighted area. You may have to repaste your code as it may have already lost the spacing.

I found in python if copying code from another place, I would often mess up the spacing. I often have to back space to previous line. Sometime error is not even on line shown but another above it.

I use Geany, but had to turn off tabs to use spaces automatically in three places. One is normal edit, one was saved files & the third was under projects.

---

### Post by Arndt on 2011-07-29
> **oldfred said:**
> To edit with code tags easily after posting you have to use the advanced button and then you get the full menu in the edit panel at the top. On the right side of edit panel is #. 


Where is that advanced button? It always looks like that for me.

---

### Post by Arndt on 2011-07-29
> **Arndt said:**
> Where is that advanced button? It always looks like that for me.

I see now that there is a choice in the user profile to show that tool bar or not. I don't remember if I turned that on, or it was like that from the start. But I still don't see an advanced button when I'm using the basic mode.

---

### Post by rpmp on 2011-07-29
ok finally did it thanks

---

### Post by oldfred on 2011-07-29
Remove the indents on lines 40 & 44, they need to be at same indent as line above.
I had to change line 36 to pass to get it to run, but the input is wrong & I have never used that so I do not know that answer.

---

### Post by rpmp on 2011-07-29
fixed line 40 and 44 but dont know wat u mean by fix line 36 it says break outside loop wat does it mean?

---

### Post by oldfred on 2011-07-29
I do not know what the complaint about break is. But you have the same logic statement twice in a row. So I just changed break to pass. Then program runs but not correctly.

---

### Post by Bachstelze on 2011-07-30
> **rpmp said:**
> it says break outside loop wat does it mean?

It means just that: you have a break outside a loop. This makes zero sense. break must be in a for or while loop, here you have it after an if.

---

### Post by rpmp on 2011-07-30
> **oldfred said:**
> I do not know what the complaint about break is. But you have the same logic statement twice in a row. So I just changed break to pass. Then program runs but not correctly.


how u changed the break?

---

### Post by Arndt on 2011-07-30
> **rpmp said:**
> how u changed the break?

Look at this part of your code. The last line is clearly meant to be included in the while loop, but it has the wrong indentation. As far as python is concerned, this is a syntactically valid program (apart from the "break" later), but the while loop ends with the statement "guess = int(guess)". The "break" which comes later is not inside the while loop, and that makes python complain about it. All you have to do is fix the indentation from the guessestaken line onward.

Things like these may be easier to catch if you also indent the comments, but that's a question of style.

```
#okay doc this says ur chances
while guessestaken < 6:
    print("take a guess doc")

#this says the guess u said
    guess = input()
    guess = int(guess)

#this says how many gueses u taken
guessestaken = guessestaken + 1
```

---

