---
title: "couple of tough questions"
date: 2010-03-13
forum: Programming Talk
---

### Post by XXMy_Little_ShinigamiXX on 2010-03-13
hi, im once again designing my own version of hangman and refusing to use the totorial code as i believe you learn more that way, but ive ran into some issues.. let me post the code up right quick:

```

import random 
import string
#importing modules--------------------------

def Start(words): 
 return random.choice(words) as word  
 print word
 Board('self')

def Board(self):
 #for len(x) in word:
 #print '_' * x
 guess = str(raw_input('Please enter a letter to guess: '))
 if len(guess) != 1:
  print 'You may only enter 1 letter at a time: '
  guess = str(raw_input('Please enter a a single letter: '))
 elif guess in alreadyguessed:
  print 'you have already guessed that letter!'
  guess = str(raw_input('Please enter a letter to guess: '))
 elif guess.lower() not in string.ascii_lowercase:
  guess = str(raw_input('Please enter a valid letter: '))
 elif guess not in word:
  iteration.next()
 else:
  alreadyguessed.append(guess)
  Board('self')     

#global variables defined
global alreadyguessed
alreadyguessed = ['']
global iteration
iteration = iter(HANGMANPICS)
global word
#----------------------
#start of the game
#----------------------
print 'Welcome to hangman version 1.0'
print 'Please select the category of words to get started.'
print 'The choices are: Animals, Fruits,  and Japanese'
jump = raw_input()
if jump.capitalize() == 'Animals': Start('Animals')
elif jump.capitalize() == 'Fruits': Start('Fruits')
elif jump.capitalize() == 'Japanese': Start('Japanese')
#-----------------------

#our set of words
#-----------------
global Animals
global Fruits 
global Japanese
global HANGMANPICS
#-----------------
#our words being defined and split into lists
#----------------------------------------------------------------------------------------
Animals = 'dolphin zebra girrafe lion cat dog gizelle aardvark porpose eel'.split()
Fruits = 'watermelon banana apple orange mango rotten lettuce plum'.split()
Japanese = 'matsuri kyouto toukyou hanabi sora ichigo kesshin kokoro kirei'.split()
HANGMANPICS = '''just a long set of ascii art images'''

```#1
this is just what ive done so far, i have a couple of questions though, from the very top where the function start is im sure you can see im in a tight cookie lol. in the main module code it states when you select a category the function is going to be called with that category, and going to return a random word from whatever list that was. problem is i cant seem to assign it a value like word or something .. the only error it gives me is a syntax error when i try and use it like return x value 'as' key. how do i assign the value the word comes up with to a variable?
#2
also i want to be able to map out if someone guesses the correct letter in the word the first thing its going to do is add it to the list alreadyguessed, but i also want it to display the words and blanks, so i need to be able to map out whatever letter is correctly guessed to the word. like for example, lets say the word is 'Fish' and i guess the 'F': i want to be able to display 'F _ _ _' i think but im not sure but by chance can i use the mapping feature of python to do this?  maybe if i made it a set? like:
for x in set(word):
map(x)?
ugh im not even sure how to go about doing this, but im sure you get the idea of what i want to do. 
#3
this is kind of an odd question, because the program before this i did i did an imitation again of the tutorials program but did my own code, and added a few new features. in this one he/she battles, and finds restorative potions as well, its actually kinda neat lol.
heres the source code for this one:
```

import random
import time
from string import Template


def Main_Menu(self):
 global x
 x = str(raw_input('Enter your name here: '))
 time.sleep(1.0)
 temp = Template('Once upon a time there was a hero called $name whom searched from cave to cave.')
 print temp.safe_substitute(name=x)
 time.sleep(2.4)
 print 'The hero', x, 'was desperatly looking for the princess.'
 time.sleep(2.4)
 print 'and so', x,'\'s journey begins'
 time.sleep(1.0)
 print 'press enter to begin'
 skip = raw_input('')
 Start('self')
 
def Start(self): 
 battle = random.randint(1, 2)
 time.sleep(1.0)
 print 'Before you lies two caves to choose', x,
 time.sleep(1.0) 
 print 'which do you choose?'
 print 'if you choose the first cave, press 1, otherwise press 2'
 print 'choose wisely'
 choose = str(raw_input(''))
 choose = int(choose)
 while True:
  if choose == battle:
   Battle_Ground('self')
  elif random.randint(1, 2) != battle:
   Restore = random.randint(1, 5)
   HP = HP + Restore
   print 'You have found a restorative potion', x, 'restored', Restore, 'HPs'
   print x, '\'s current HP =', HP
   print ''
   break
 Start('self')  

def Battle_Ground(self):
 ENEMYATTACK = random.randint(1, 10)
 HP = HP - ENEMYATTACK
 ENEMYHP = 10 
 attack = 2
 print 'you are in battle now', x, 'so be sure make sure your HP doesnt drop below 0'
 print 'to attack', x, 'say attack'
 print 'to run', x, 'say run'
 print 'i feel like i must warn you though', x, 'if you run you might get eaten'
 print 'Your current HP = ', HP
 choose = str(raw_input('What do you want to do?: ')) 
 if choose.lower() == 'attack':
  while ENEMYHP != 0:
   ENEMYHP = ENEMYHP - attack
   HP = HP - ENEMYATTACK
   print 'you attack with', attack, 'damage', x, 'HP =', HP
   time.sleep(1.0)
   print 'the enemy attacks you with', ENEMYATTACK, 'damage', 'Enemy HP =', ENEMYHP
   time.sleep(1.0)
   if ENEMYHP == 0:
    break
  Start('self')          
 elif choose.lower() == 'run':
  c = random.randint(1, 10)
  if c == 3 or 4 or 5 or 6 or 7 or 8 or 9 or 10:
   print 'game over, you were eaten ', x
   Main_Menu('self')  
  elif c == 1 or 2:
   Start('self')


# start of the game
global HP
HP = 100
Main_Menu('self')


```this is the error its giving me is on this line:
 HP = HP - ENEMYATTACK
more particularly in depth is this:
  File "Dragon.py", line 45, in Battle_Ground
    HP = HP - ENEMYATTACK
UnboundLocalError: local variable 'HP' referenced before assignment

its telling me that HP is a local variable when in fact it is not! its defined global before the game starts, whats going on. i want to be able to keep HP at a constant number except for the restorative potions and enemy attacks. i think the = is making it a local reference but even if i remove that the HP stays at 100. it doesnt move. if i did it as a local variable then i would have to take and put it in the function as 100 but then everytime it reloaded the function it would run by that line of code again making it 100 again. is there any way of fixing this? 

#4
i believe i read somewhere in the tutorial though that global variables can only be altered outside functions. i believe this is what i read so if anyone wants me to make sure ill find it again. but whats this about?  only reason i ask is because im appending guess to alreadyguessed which is a global variable in the first code, so wouldnt that be some sort of exception?

any and all help is appreciated 
thanks :popcorn:

---

### Post by snova on 2010-03-13
> **XXMy_Little_ShinigamiXX said:**
> hi, im once again designing my own version of hangman and refusing to use the totorial code as i believe you learn more that way, but ive ran into some issues.. let me post the code up right quick:

```

import random 
import string
#importing modules--------------------------

def Start(words): 
 return random.choice(words) as word  
 print word
 Board('self')

def Board(self):
 #for len(x) in word:
 #print '_' * x
 guess = str(raw_input('Please enter a letter to guess: '))
 if len(guess) != 1:
  print 'You may only enter 1 letter at a time: '
  guess = str(raw_input('Please enter a a single letter: '))
 elif guess in alreadyguessed:
  print 'you have already guessed that letter!'
  guess = str(raw_input('Please enter a letter to guess: '))
 elif guess.lower() not in string.ascii_lowercase:
  guess = str(raw_input('Please enter a valid letter: '))
 elif guess not in word:
  iteration.next()
 else:
  alreadyguessed.append(guess)
  Board('self')
```

#1
this is just what ive done so far, i have a couple of questions though, from the very top where the function start is im sure you can see im in a tight cookie lol. in the main module code it states when you select a category the function is going to be called with that category, and going to return a random word from whatever list that was. problem is i cant seem to assign it a value like word or something .. the only error it gives me is a syntax error when i try and use it like return x value 'as' key. how do i assign the value the word comes up with to a variable?

I think you want something like this:

[PHP]
def Start(words):
    word = random.choice(words)
    Board(word)

def Board(word):
    pass # etc.
[/PHP]

A function can not change variables in the caller's scope in any case, and returning a variable along with a name is quite pointless.

Later on, you will have to pass the list of words explicitly:

[PHP]
#-----------------
#our words being defined and split into lists
#----------------------------------------------------------------------------------------
Animals = 'dolphin zebra girrafe lion cat dog gizelle aardvark porpose eel'.split()
Fruits = 'watermelon banana apple orange mango rotten lettuce plum'.split()
Japanese = 'matsuri kyouto toukyou hanabi sora ichigo kesshin kokoro kirei'.split()
#----------------------
#start of the game
#----------------------
print 'Welcome to hangman version 1.0'
print 'Please select the category of words to get started.'
print 'The choices are: Animals, Fruits,  and Japanese'
jump = raw_input()
if jump.capitalize() == 'Animals': Start(Animals)
elif jump.capitalize() == 'Fruits': Start(Fruits)
elif jump.capitalize() == 'Japanese': Start(Japanese)
[/PHP]

Or, to make it a bit shorter:

[PHP]
#-----------------
#our words being defined and split into lists
#----------------------------------------------------------------------------------------
Words = {
    "Animals": 'dolphin zebra girrafe lion cat dog gizelle aardvark porpose eel'.split(),
    "Fruits": 'watermelon banana apple orange mango rotten lettuce plum'.split(),
    "Japanese": 'matsuri kyouto toukyou hanabi sora ichigo kesshin kokoro kirei'.split()
    }
#----------------------
#start of the game
#----------------------
print 'Welcome to hangman version 1.0'
print 'Please select the category of words to get started.'
print 'The choices are: Animals, Fruits,  and Japanese'
jump = raw_input()
Start(Words[jump])
[/PHP]



> #2
also i want to be able to map out if someone guesses the correct letter in the word the first thing its going to do is add it to the list alreadyguessed, but i also want it to display the words and blanks, so i need to be able to map out whatever letter is correctly guessed to the word. like for example, lets say the word is 'Fish' and i guess the 'F': i want to be able to display 'F _ _ _' i think but im not sure but by chance can i use the mapping feature of python to do this?  maybe if i made it a set? like:
for x in set(word):
map(x)?
ugh im not even sure how to go about doing this, but im sure you get the idea of what i want to do.

**map** is not going to be of any help here. It is used to call a function on every item in a list and collect the return values, and is generally very important.

I think **Board**() needs to keep track of two lists here- the letters in the word, and the ones that have been revealed. The latter list will be populated with "_" initially.

[php]
letters = list(word) # "banana" will become ["b", "a", "n", "a", "n", "a"]
revealed = ["_"] * len(letters) # makes a list as long as letters is, by copying ["_"]
                                # ["_", "_", "_", "_", "_", "_"]
[/php]

Then, when the user enters a character, reveal all instances of it like this:

[PHP]
user_char = raw_input("Please select a character to guess: ")
for index, char in enumerate(letters):
    if char == user_char:
        revealed[index] = char
[/PHP]

**enumerate** is a function to iterate over both the index of the item and the item itself. So for "banana", it would produce (0, "b"), (1, "a"), (2, "n"), etc. Where the character is the correct one, copy it to **revealed** so that the user can see it when we print it out:

[PHP]print " ".join(revealed)[/PHP]

Supposing I typed in "a", **revealed** would become this:

```
["_", "a", "_", "a", "_", "a"]
```

So printing it would produce "_ a _ a _ a".

Now, as it is the loop will never end, so you need to keep track of how many characters have been revealed so far, and when it is equal to the length of the word, stop.

[php]
guessed = 0

# ...

if guessed == len(word):
    break
[/php]

The resulting game loop would look something like this:

[PHP]
def PlayHangman(word):
    guessed = 0
    letters = list(word)
    revealed = ["_"] * len(letters)
    while True:
        print " ".join(revealed)
        user_char = raw_input("Please select a character to guess: ")
        
        # loop over letters here; when one matches, increment guessed
        
        if guessed == len(word):
            print " ".join(revealed)
            print "You win!"
            break
[/PHP]

> 
#3
this is kind of an odd question, because the program before this i did i did an imitation again of the tutorials program but did my own code, and added a few new features. in this one he/she battles, and finds restorative potions as well, its actually kinda neat lol.
heres the source code for this one:
```

import random
import time
from string import Template


def Main_Menu(self):
 global x
 x = str(raw_input('Enter your name here: '))
 time.sleep(1.0)
 temp = Template('Once upon a time there was a hero called $name whom searched from cave to cave.')
 print temp.safe_substitute(name=x)
 time.sleep(2.4)
 print 'The hero', x, 'was desperatly looking for the princess.'
 time.sleep(2.4)
 print 'and so', x,'\'s journey begins'
 time.sleep(1.0)
 print 'press enter to begin'
 skip = raw_input('')
 Start('self')
 
def Start(self): 
 battle = random.randint(1, 2)
 time.sleep(1.0)
 print 'Before you lies two caves to choose', x,
 time.sleep(1.0) 
 print 'which do you choose?'
 print 'if you choose the first cave, press 1, otherwise press 2'
 print 'choose wisely'
 choose = str(raw_input(''))
 choose = int(choose)
 while True:
  if choose == battle:
   Battle_Ground('self')
  elif random.randint(1, 2) != battle:
   Restore = random.randint(1, 5)
   HP = HP + Restore
   print 'You have found a restorative potion', x, 'restored', Restore, 'HPs'
   print x, '\'s current HP =', HP
   print ''
   break
 Start('self')  

def Battle_Ground(self):
 ENEMYATTACK = random.randint(1, 10)
 HP = HP - ENEMYATTACK
 ENEMYHP = 10 
 attack = 2
 print 'you are in battle now', x, 'so be sure make sure your HP doesnt drop below 0'
 print 'to attack', x, 'say attack'
 print 'to run', x, 'say run'
 print 'i feel like i must warn you though', x, 'if you run you might get eaten'
 print 'Your current HP = ', HP
 choose = str(raw_input('What do you want to do?: ')) 
 if choose.lower() == 'attack':
  while ENEMYHP != 0:
   ENEMYHP = ENEMYHP - attack
   HP = HP - ENEMYATTACK
   print 'you attack with', attack, 'damage', x, 'HP =', HP
   time.sleep(1.0)
   print 'the enemy attacks you with', ENEMYATTACK, 'damage', 'Enemy HP =', ENEMYHP
   time.sleep(1.0)
   if ENEMYHP == 0:
    break
  Start('self')          
 elif choose.lower() == 'run':
  c = random.randint(1, 10)
  if c == 3 or 4 or 5 or 6 or 7 or 8 or 9 or 10:
   print 'game over, you were eaten ', x
   Main_Menu('self')  
  elif c == 1 or 2:
   Start('self')


# start of the game
global HP
HP = 100
Main_Menu('self')


```this is the error its giving me is on this line:
 HP = HP - ENEMYATTACK
more particularly in depth is this:
  File "Dragon.py", line 45, in Battle_Ground
    HP = HP - ENEMYATTACK
UnboundLocalError: local variable 'HP' referenced before assignment

its telling me that HP is a local variable when in fact it is not! its defined global before the game starts, whats going on. i want to be able to keep HP at a constant number except for the restorative potions and enemy attacks. **i think the = is making it a local reference** but even if i remove that the HP stays at 100. it doesnt move. if i did it as a local variable then i would have to take and put it in the function as 100 but then everytime it reloaded the function it would run by that line of code again making it 100 again. is there any way of fixing this?

That is precisely the issue. Python wants to assign to a local variable, but to do so it must first find out what **HP** is... but it thinks you mean the local version, which doesn't exist yet. Add this statement to the top of **Battle_Ground**(), before **HP** is referenced:

[PHP]global HP[/PHP]

Among other things I have noticed here, "global HP" is entirely useless at a global scope, near the end. Also, the **self** parameters aren't being used for anything, so remove them.

Oh, and this is wrong:

[PHP]
 elif choose.lower() == 'run':
  c = random.randint(1, 10)
  if c == 3 or 4 or 5 or 6 or 7 or 8 or 9 or 10:
   print 'game over, you were eaten ', x
   Main_Menu('self')  
  elif c == 1 or 2:
   Start('self')
[/php]

Those if statements will not work correctly; try this instead:

[PHP]
 elif choose.lower() == 'run':
  c = random.randint(1, 10)
  if c in [3, 4, 5, 6, 7, 8, 9, 10]:
   print 'game over, you were eaten ', x
   Main_Menu('self')  
  elif c == 1 or c == 2:
   Start('self')
[/PHP]

> 
#4
i believe i read somewhere in the tutorial though that global variables can only be altered outside functions. i believe this is what i read so if anyone wants me to make sure ill find it again. but whats this about?  only reason i ask is because im appending guess to alreadyguessed which is a global variable in the first code, so wouldnt that be some sort of exception?

Ordinarily yes, you cannot, which is why we need the **global** statement in those functions (but it doesn't do anything at a global scope). You can access them, however, as long as you don't try to assign to them.

---

