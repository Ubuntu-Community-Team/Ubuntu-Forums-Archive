---
title: "Python basic game working in IDLE not terminal"
date: 2011-05-09
forum: Programming Talk
---

### Post by pafoo on 2011-05-09
Hello, I have been working on learning python. I am a sys admin who decided to stray from shell scripting. So I am following this begginers programming book and have run into a issue. I made a basic word guessing game and it runs fine in IDLE. But when I try to run it in the terminal it tells me that the module I am trying to run has no attribute named randrange. Here is my basic code.

#!/usr/bin/python

import random

print "\t\tHello, and welcome to Larry's number guessing game!!\n"
print "The way to play the guessing game is to guess a number from 1-100 in as few guesses as possible."
print "\n\t\tBy the way you only get 5 guesses!!\n\n"
begin = raw_input("Shall we begin? (yes/no) > ")

if begin == "no":
     print "That's ok, maybe next time"
elif begin == "yes":
     print "\nAlright, lets play!\n\n"

  
     guess = 0
     mnumber = (random.randrange(100) + 1)
     answer = ""
  
     while answer != mnumber:
    if (guess <= 5):
         answer = int(raw_input("Guess a number from 1-100 > "))
         guess += 1
     if answer > mnumber:
             print "That number is to high, guess again!!\n"
          elif answer < mnumber:
             print "That number is to low, guess again!!\n"
          elif answer == mnumber:
             print "\n\nThat's it!!! Great job!!!\n"
             print "You were able to get the answer in", guess,"guesses!"
          else:
             print "Im sorry that wasnt a valid number, please try again!"
    
    else:
     print "Sorry you lost!!!"
           break
else:
  print "Im sorry, please type 'yes' or 'no'"

raw_input("\n\nPress enter to exit")

---

### Post by ziekfiguur on 2011-05-09
I don't see why python wouldn't be able to find randrange(). Would you mind posting the code between [ CODE ][ /CODE ] tags so the formatting is preserved and we can test it?

---

### Post by DaithiF on 2011-05-09
Hi, works ok for me (after guessing on the indentation).

is the exact script you were trying to run?  My shot-in-the-dark guess would be that at some point in your version you had a variable called random that you assigned some value to ... this would have nuked your reference to the random module.

but as i said, the script you posted actually does work.

---

### Post by pafoo on 2011-05-09
Never tried that before, but hope this works

```


#!/usr/bin/python

import random

print "\t\tHello, and welcome to Larry's number guessing game!!\n"
print "The way to play the guessing game is to guess a number from 1-100 in as few guesses as possible."
print "\n\t\tBy the way you only get 5 guesses!!\n\n"
begin = raw_input("Shall we begin? (yes/no) > ")

if begin == "no":
  print "That's ok, maybe next time"
elif begin == "yes":
  print "\nAlright, lets play!\n\n"

  
  guess = 0
  mnumber = (random.randrange(100) + 1)
  answer = ""
  
  while answer != mnumber:
   if (guess <= 5):
    answer = int(raw_input("Guess a number from 1-100 > "))
    guess += 1
    if answer > mnumber:
      print "That number is to high, guess again!!\n"
    elif answer < mnumber:
      print "That number is to low, guess again!!\n"
    elif answer == mnumber:
      print "\n\nThat's it!!! Great job!!!\n"
      print "You were able to get the answer in", guess,"guesses!"
    else:
      print "Im sorry that wasnt a valid number, please try again!"
    
   else:
      print "Sorry you lost!!!"
      break
else:
  print "Im sorry, please type 'yes' or 'no'"

raw_input("\n\nPress enter to exit")


```

---

### Post by doas777 on 2011-05-09
if you are still having trouble with it, try this bangline:
```
#!/usr/bin/env python
```
that way it will use the system default interpreter. that would also explain why it works for others but not for you. just a thought.

---

### Post by DaithiF on 2011-05-09
err, hang on:
```

That's it!!! Great job!!!

You were able to get the answer in **6** guesses!


```

```

                Hello, and welcome to Larry's number guessing game!!

The way to play the guessing game is to guess a number from 1-100 in as few guesses as possible.

                By the way you only get **5** guesses!!

```
[off-by-one error]("http://en.wikipedia.org/wiki/Off_by_one") :)

---

### Post by ziekfiguur on 2011-05-09
It works fine for me as well, do you by any chance have a file called random.py or a folder called random in the folder from where you run the script? If so, that one gets loaded instead of the standard random module.

---

### Post by cgroza on 2011-05-09
I saw this before on the forum. Your filename is random.py.
When importing random, you are importing your own file, not the python module. 
Rename your file and it should work.

---

