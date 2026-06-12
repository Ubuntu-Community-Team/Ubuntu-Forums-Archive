---
title: "number game is making me nuts lol"
date: 2010-03-10
forum: Programming Talk
---

### Post by XXMy_Little_ShinigamiXX on 2010-03-10
```

import sys
from sys import quit
import random
from random import randint

def retry(x, y): 
 num1 = random.randint(x, y)
 b = int(raw_input('please enter a number: '))
 if b < num1: print 'too small'
 elif b > num1: print 'too high'
 elif b == num1: print 'yay'

print ('hello, and welcome to the numbers game \n'
      'please select the difficulty \n'
      'Easy, Medium, or Hard, or Insane or Shootme')
try:      
 select = str(raw_input(''))
 if select == 'Easy':
  x = random.randint(1, 10)
except select == 'Medium':
  x = random.randint(1, 20)
except select == 'Hard':
  x = random.randint(1, 50)
except select == 'insane':
  x = random.randint(1, 100)
except select == 'Shootme':
  x = random.randint(1, 1000)
 
print x
while True:
 y = int(raw_input('enter your guess: '))
 if y < x:
  print 'too small'
 elif y > x:
  print 'you guesed too high'  
 elif y == x:
 # print() optional incase you want a space
  print 'you guessed it right!', 'do you want to play again?'
  v = str(raw_input(''))
  if v == 'y': 
   print 'enter the number range for the random number: '
   c = int(raw_input(''))
   c2 = int(raw_input(''))
   retry(c, c2)
  elif v == 'n' or 'N': 
   sys.quit()

```ok so heres my code for this, but when i run the interpreter after selecting my difficulty it messes up. it tells me x is not defined when in fact it should be defined based on the difficulty i select.. it is telling me this in the line that says ;
print x:
this line comes after the x = random.randint() so there shouldnt be a problem.. it works when i select easy so i thikn somethings up with the try statement but i dont see what. *sigh can anyone help me with this? also the function i added in to keep retrying, well when it was successfully running in which all i did to change that is add a comment it kept giving me the same number on the retry. i understand that the variable has to be refreshed before it can give a new number: for example,
x = random.randint(1, 90) 
lets say the output was 25, well no matter how many times you type x its going to be 25. so i understand that concept but the function retry is being given new values everytime they are asked to enter them, this should fix it right?
:popcorn:

ok the first select option works ok now, i removed the try statement and Capitalized the I in insane mode lol. x wasnt being defined there because of that. but im still lost as to why x was not defined before on any other mode than easy. A try statement loops thorugh the default try and except statements until it finds a condition thats true right?

---

### Post by snova on 2010-03-10
Wow, this is some weird code.

> **XXMy_Little_ShinigamiXX said:**
> ```

import sys
from sys import quit
import random
from random import randint
```

This is unnecessary; either import the modules or import things from the module. As the rest of your code assumes the former, this should be changed to:

```

import random
import sys

```

Also, there is no **sys.quit()** function.

> ```
def retry(x, y): 
 num1 = random.randint(x, y)
 b = int(raw_input('please enter a number: '))
 if b < num1: print 'too small'
 elif b > num1: print 'too high'
 elif b == num1: print 'yay'
```

I'm not sure what this is supposed to do. Because every time this function is called it will generate a new random number, it's quite difficult to ever get the number right.

> ```

print ('hello, and welcome to the numbers game \n'
      'please select the difficulty \n'
      'Easy, Medium, or Hard, or Insane or Shootme')

```

I think this would be somewhat more idiomatic, but your choice:

```

print 'Hello, and welcome to the numbers game.'
print 'There are five difficulty levels: Easy, Medium, or Hard, or Insane and Shootme.'

```

(I moved the question to the next bit, as I think it looks a little nicer)

> ```

try:      
 select = str(raw_input(''))
 if select == 'Easy':
  x = random.randint(1, 10)
except select == 'Medium':
  x = random.randint(1, 20)
except select == 'Hard':
  x = random.randint(1, 50)
except select == 'insane':
  x = random.randint(1, 100)
except select == 'Shootme':
  x = random.randint(1, 1000)

```

try/except have no use here, they are for exception handling. I think you meant something more like this:

```

# I prefer prompting questions with raw_input(), as I think it looks a little nicer
# not to have an empty line.
select = raw_input('Please enter a difficulty level: ')
if select == 'Easy':
  x = random.randint(1, 10)
elif select == 'Medium':
  x = random.randint(1, 20)
elif select == 'Hard':
  x = random.randint(1, 50)
elif select == 'insane':
  x = random.randint(1, 100)
elif select == 'Shootme':
  x = random.randint(1, 1000)

```

Even better would be:

```

levels = {"Easy": 10, "Medium": 20, "Hard": 50, "Insane": 100, "Shootme": 1000}
select = raw_input("Please enter a difficulty level: ")
maximum = levels[select]
x = random.randint(1, maximum)

```

Something else to consider is that there is no error handling here; an invalid response will cause the program to throw an exception.

> ```

print x
while True:
 y = int(raw_input('enter your guess: '))
 if y < x:
  print 'too small'
 elif y > x:
  print 'you guesed too high'  
 elif y == x:
 # print() optional incase you want a space
  print 'you guessed it right!', 'do you want to play again?'
  v = str(raw_input(''))
  if v == 'y': 
   print 'enter the number range for the random number: '
   c = int(raw_input(''))
   c2 = int(raw_input(''))
   retry(c, c2)
  elif v == 'n' or 'N': 
   sys.quit()

```

I think this code will mostly work. A somewhat simplified version (without the retry):

```

while True:
  y = int(raw_input("Enter your guess: "))
  if y < x:
    print "Too small"
  elif y > x:
    print "Too large"
  else:
    print "You guessed it right!"
    sys.exit()

```

If you want to add the retry feature, I would suggest moving the above loop (along with the difficulty/number selection code, so that it can be changed between games) into a function called play_game() or similar, replacing the exit() call with **return**. Then the main program would look similar to this:

```

while True:
  play_game()
  again = raw_input("Do you want to play again? ")
  if again != "y":
    break
  # anything other than "y" will restart the loop.

```

This has the advantage of not duplicating any code.

---

### Post by XXMy_Little_ShinigamiXX on 2010-03-10
```

import sys
import random

def retry(x, y): 
 num1 = random.randint(x, y)
 b = int(raw_input('please enter a number: '))
 if b < num1: print 'too small'
 elif b > num1: print 'too high'
 elif b == num1: print 'yay'
   
def play_game(play):
 print ('hello, and welcome to the numbers game \n'
      'please select the difficulty \n'
      'Easy, Medium, or Hard, or Insane or Shootme')
 levels = {'Easy': 10, 'Medium': 20, 'Hard': 50, 'Insane': 100, 'Shootme': 1000}
 select = raw_input('')
 maximum = levels[select]
 x = random.randint(1, maximum)
 while True:
  guess = int(raw_input('please enter your guess: '))
  if guess < x:
   print 'The number you guessed was too small!'
  elif guess > x:
   print 'The number you guessed was too large!'
  elif guess == x: 
   print 'correct! would you like to play again?'
   print ('NOTE: you have now beat the game so you\n'
          'may use your own Custom range settings by\n'
          'typing in Custom')
  redo = str(raw_input(''))
  if redo != 'y' or 'yes' or 'Yes' or 'Y' or 'Custom' or 'custom':
   break
  elif redo == 'Custom' or 'custom':
   print 'please enter the starting number for a range: '
   number1 = int(raw_input(''))
   print 'please enter the second number to finish the range: '
   number2 = int(raw_input(''))
   retry(number1, number2)
  else:
   return play_game('play')

play_game('play')

```ok thank yo uvery much for your help, i took you up on some of that code right quick and rewrote it basically. only problem is its refusing to run my while loop inside the funciton. i appreciate your help very much, as im a noob and my playing with functions is limited. i didnt understand in the tutorials why it was putting a function inside of another function, but i think i undertsand it a little better now. thank you. no chance you can tell me why my while loop isnt working? LOL :popcorn:

---

### Post by bgs100 on 2010-03-10
The reason is here:

> ```
  if redo != 'y' or 'yes' or 'Yes' or 'Y' or 'Custom' or 'custom':
   break

```

First it evaluates "redo != 'y'", which if someone said 'y', will be False. But then you have an "or" after that, and because the first part was False, it will try the next part. It considers 'yes' true, so it breaks.

I think you're trying to do:
```
  if redo not in ['y', 'yes', 'Yes', 'Y', 'Custom', 'custom']:
   break

```

You have a similar problem on the next part:
> ```
  elif redo == 'Custom' or 'custom':

```

If the person doesn't type 'Custom' (or 'custom'), the part below the elif will still be executed.

Again, you need either:
```
  elif redo in ['Custom', 'custom']:

```

Or better yet:
```
  elif redo.lower() == 'custom'
```

redo.lower() returns redo, but with all of the letters in lowercase.

You could do this:
```

  redo = raw_input('').lower() # redo is the input lowercased
  if redo not in ['y', 'yes', 'custom']:
   break
  elif redo == 'custom':
   print 'please enter the starting number for a range: '
   number1 = int(raw_input(''))
   print 'please enter the second number to finish the range: '
   number2 = int(raw_input(''))
   retry(number1, number2)
  else:
   return play_game('play')

```

However, another problem is that that whole part will be ran regardless of whether the person won. You need to increase the indent level to keep it in the "elif guess == x: ", so you need to add a space before each of those lines.

---

### Post by XXMy_Little_ShinigamiXX on 2010-03-10
```

import sys
import random

def retry(x, y): 
 num1 = random.randint(x, y)
 b = int(raw_input('please enter a number: '))
 if b < num1: print 'too small'
 elif b > num1: print 'too high'
 elif b == num1: print 'yay'
   
def play_game(play):
 print ('hello, and welcome to the numbers game \n'
      'please select the difficulty \n'
      'Easy, Medium, or Hard, or Insane or Shootme')
 levels = {'Easy': 10, 'Medium': 20, 'Hard': 50, 'Insane': 100, 'Shootme': 1000}
 select = raw_input('')
 maximum = levels[select]
 x = random.randint(1, maximum)
 while True:
  guess = int(raw_input('please enter your guess: '))
  if guess < x:
   print 'The number you guessed was too small!'
  elif guess > x:
   print 'The number you guessed was too large!'
  elif guess == x: 
   print 'correct! would you like to play again?'
   print ('NOTE: you have now beat the game so you\n'
          'may use your own Custom range settings by\n'
          'typing in Custom')
   break
 redo = str(raw_input(''))
 if redo.lower() == 'y' or 'yes': 
  return play_game('play')
 # old text if redo != 'y' or 'yes' or 'Yes' or 'Y' or 'Custom' or 'custom':
 # pass
 elif redo.lower() == 'custom':
  print 'please enter the starting number for a range: '
  number1 = int(raw_input(''))
  print 'please enter the second number to finish the range: '
  number2 = int(raw_input(''))
  retry(number1, number2)
 #old text elif redo == 'y' or 'yes' or 'Yes' or 'Y':
  

play_game('play')

```ok so i took a second look at it after a few hours away from the screen;
btw the above code is the updated lol;
right to the point where the break was is where i revised for the most part. the issue i was having was that the if statement that was before != 'y' etc.. was still indented to be part of the while loop. that was supposed to be a seperate function outside the loop lol. after indenting everything back and putting the break in the right place everything jsut kinda felll into place, except the custom game settings, its gonna take me a bit to work those out to lol. any help is always appreciated :popcorn: btw thank you very much for that redo.lower() explanation i saw that in a tutorial and i was thinking what in the world is this good for lol. but now i know :) if i just put this line of code:
x = raw_input('')
if x.lower() == 'yes': etc..
so basiclaly no matter how it is entered via, Yes, YES, YeS, yeS, etc.. its going to return it to the orginal state of yes and therefore by adding the value of yes to x. thank you very much :popcorn: sorry for the long and drug out code but i cant allow the tutorial to make a better code then me LOL. 

PS.. the play_game('play') code at the bottom was just to kick the game off when the interpreter started. lol

---

### Post by XXMy_Little_ShinigamiXX on 2010-03-10
WALLLA!!!!!!!!!! lol

```

import sys
import random
import pprint # this is a just incase i decide to add something else later

def retry(x, y): 
 num1 = random.randint(x, y)
 while True:
  b = int(raw_input('please enter your guess: '))
  if b < num1: 
   print 'The number you guessed was too small!'
  elif b > num1: 
   print 'The number you guessed was too large!'
  elif b == num1: 
   break
 print ('correct! would you like to play normal mode or \n'
          'continue with custom mode? for custom mode again\n'
          'type in custom and for normal mode type in normal')
 option1 = str(raw_input('')) 
 if option1.lower() == 'custom':
  print 'please enter the starting number for a range: '
  number1 = int(raw_input(''))
  print 'please enter the second number to finish the range: '
  number2 = int(raw_input(''))
  retry(number1, number2)
 elif option1.lower() == 'normal': return play_game('play')
   
def play_game(play):
 print ('hello, and welcome to the numbers game \n'
      'please select the difficulty \n'
      'Easy, Medium, or Hard, or Insane or Shootme')
 levels = {'Easy': 10, 'Medium': 20, 'Hard': 50, 'Insane': 100, 'Shootme': 1000}
 select = raw_input('')
 maximum = levels[select]
 x = random.randint(1, maximum)
 while True:
  guess = int(raw_input('please enter your guess: '))
  if guess < x:
   print 'The number you guessed was too small!'
  elif guess > x:
   print 'The number you guessed was too large!'
  elif guess == x: 
   print 'correct! would you like to play again?'
   print ('NOTE: you have now beat the game so you\n'
          'may use your own Custom range settings by\n'
          'typing in Custom')
   break
 redo = str(raw_input(''))
 if redo.lower() == 'custom':
  print 'please enter the starting number for a range: '
  number1 = int(raw_input(''))
  print 'please enter the second number to finish the range: '
  number2 = int(raw_input(''))
  retry(number1, number2)
 elif redo.lower() == 'y' or 'yes': 
  return play_game('play')
 # old text if redo != 'y' or 'yes' or 'Yes' or 'Y' or 'Custom' or 'custom':
 # pass

 #old text elif redo == 'y' or 'yes' or 'Yes' or 'Y':
  

play_game('play')

```

ok this should have everything fixed as far as the basics go. i havent added error handling as this isnt something i really plan on using a lot in other modules. nor have i added the input.capitalize() to the other input when choosing the difficulty level, but you may if you want to .. lol i think im done with this project though so gates are shut lol. thanks guys :popcorn:

---

