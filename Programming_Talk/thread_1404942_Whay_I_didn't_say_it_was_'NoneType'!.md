---
title: "Whay? I didn't say it was 'NoneType'!"
date: 2010-02-12
forum: Programming Talk
---

### Post by Ryland Taylor on 2010-02-12
Hi. I was making a text game in python. The game works just like hangman, but I used a guillotine that drops a little more each time, instead of adding a body part each time. So, anyways, here is the code (From "Invent your own computer games with python - 2nd edition"):
```
#Guillotine
#Play like hangman, but with a different theme

import random

GUILLOTINEPICS = ['''

 +---+
 |_|_|
 || ||
 | \||
 |  `|
 |   |
 |   |
 |   |
 |___|
 |-O-|
=======
||\_/||''','''

 +---+
 | | |
 |_|_|
 || ||
 | \||
 |  `|
 |   |
 |   |
 |___|
 |-O-|
=======
||\_/||''','''

 +---+
 | | |
 | | |
 |_-_|
 || ||
 | \||
 |  `|
 |   |
 |___|
 |-O-|
=======
||\_/||''','''

 +---+
 | | |
 | | |
 | | |
 |_|_|
 || ||
 | \||
 |  `|
 |___|
 |-O-|
=======
||\_/||''','''

 +---+
 | | |
 | | |
 | | |
 | | |
 |_|_|
 || ||
 | \||
 |__`|
 |-O-|
=======
||\_/||''','''

 +---+
 | | |
 | | |
 | | |
 | | |
 | | |
 |_|_|
 || ||
 |_\||
 |-O`|
=======
||\_/||''','''

 +---+
 | | |
 | | |
 | | |
 | | |
 | | |
 | | |
 |_|_|
 || ||
 |-\|| 
====`==
||\O/||''']

words = '''ant baboon badger bat bear beaver camel cat clam cobra cougar coyote 
crow deer dog donkey duck eagle ferret fox frog goat goose hawk lion lizard 
llama mole monkey moose mouse mule newt otter owl panda parrot pigeon python 
rabbit ram rat raven rhino salmon seal shark sheep skunk sloth snake spider 
stork swan tiger toad trout turkey turtle weasel whale wolf wombat 
zebra'''.split()

def getRandomWord(wordList):
    wordIndex = random.randint(0, len(wordList) - 1)
    
def displayBoard(GUILLOTINEPICS, missedLetters, correctLetters, secretWord):
    print(GUILLOTINEPICS[len(missedLetters)])
    print()

    print('Missed letters:', end = ' ')
    for letter in missedLetters:
        print(letter, end = ' ')
    print()

    blanks = '_' * len(secretWord)

    for i in range(len(secretWord)):
        if secretWord[i] in correctLetters:
            blanks = blanks[:i] + secretWord[i] + blanks[i + 1:]

    for letter in blanks:
        print(letter, end = ' ')
    print()

def getGuess(alreadyGuessed):
    while True:
        print('Guess a letter.')
        guess = input()
        guess = guess.lower()
        if len(guess) != 1:
            print('Please enter a single letter.')
        elif guess in alreadyGuessed:
            print('You have already guessed that letter. Choose again')
        elif guess not in 'abcdefghijklmnopqrstuvwxyz':
            print('That is not a letter. Please enter a letter.')
        else:
            return guess

def playAgain():
    print('Do you want to play again? (yes or no)')
    return input().lower().startswith('y')

print('G U I L L O T I N E')
missedLetters = ''
correctLetters = ''
secretWord = getRandomWord(words)
gameIsDone = False

while True:
    displayBoard(GUILLOTINEPICS, missedLetters, correctLetters, secretWord)
    
    guess = getGuess(missedLetters + correctLetters)
    if guess in secretWord:
        correctLetters = correctLetters + guess

        foundAllLetters = True
        for i in range(len(secretWord)):
            foundAllLetters = False
            break
        
        if foundAllLetters:
            print('Yes! The secret word is ' + secretWord + '!')
            gameIsDone = True
    else:
        missedLetters = missedLetters + guess

        if len(missedLetters) == len(GUILLOTINEPICS) -1:
            displayBoard(GUILLOTINEPICS, missedLetters, correctLetters, secretWord)
            print('You have run out of guesses!')
            print('You guessed ' + str(len(correctLetters)) + ''' correct 
letters. The secret word was''' + secretWord + '.')
            gameIsDone = True

    if gameIsDone:
        if playAgain():
            missedLetters = ''
            correctLetters = ''
            gameIsDone = False
            secretWord = getRandomWord(words)
        else:
            break
```
When I run this with python3, I get:
```
G U I L L O T I N E


 +---+
 |_|_|
 || ||
 | \||
 |  `|
 |   |
 |   |
 |   |
 |___|
 |-O-|
=======
||\_/||

Missed letters: 
Traceback (most recent call last):
  File "Guillotine.py", line 153, in <module>
    displayBoard(GUILLOTINEPICS, missedLetters, correctLetters, secretWord)
  File "Guillotine.py", line 118, in displayBoard
    blanks = '_' * len(secretWord)
TypeError: object of type 'NoneType' has no len()
```
I looked it up, and found [this page.]("http://www.daniweb.com/forums/thread105325.html#") So after looking at my code, i thought that this may be the problem
```
words = '''ant baboon badger bat bear beaver camel cat clam cobra cougar coyote 
crow deer dog donkey duck eagle ferret fox frog goat goose hawk lion lizard 
llama mole monkey moose mouse mule newt otter owl panda parrot pigeon python 
rabbit ram rat raven rhino salmon seal shark sheep skunk sloth snake spider 
stork swan tiger toad trout turkey turtle weasel whale wolf wombat 
zebra'''.split()
```
Is it the split method that makes it NoneType. How do I fix it?

---

### Post by wmcbrine on 2010-02-12
> **Ryland Taylor said:**
> ```
def getRandomWord(wordList):
    wordIndex = random.randint(0, len(wordList) - 1)
```You're missing something here. Hint: I think you want to **return** a **word**.

---

### Post by Ryland Taylor on 2010-02-12
Oh! Duh! Haha, thanks! It's always those little things that somehow slip past you!

---

