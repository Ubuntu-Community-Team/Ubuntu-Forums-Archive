---
title: "Python Code - Random Number Generator"
date: 2010-11-27
forum: Programming Talk
---

### Post by banditkeef on 2010-11-27
Hey, i had a question. I have a week off of school until next semesters programming classes etc... so I've been playing around with python 2.5.2 idle 1.2.2 some more learning new stuff.

Came across a problem when making a dice rolling program. I can get 1 player vs computer to work but not 1 player vs 2 player. Also couldnt get my number generator to produce the right variation.... wants to produce 0's.

using - to hold my indents

#add libraries needed
import random

#main module
def main():
    -print 'Welcome to my gambling games program.'
    -print 'May the best man, or machine win.'
    -print

    -#initialize variables
    -endProgram = 'n'
    -continueGame = 'y'
    -selection = '0'
    -playerOne = 'NO NAME'
    -playerTwo = 'Computer'

    -#while loop to run program again
    -while endProgram == 'n':

        -#main selection menu
        -while selection != '3':
            --#initialize variables
            --winnerName = 'NO NAME'
            --p1numberOne = 0
            --p1numberTwo = 0
            --p1total = 0
            --p2numberOne = 0
            --p2numberTwo = 0
            --p2total = 0

            --#display menu
            --print 'Menu Selection'
            --print '1 - Roll the Dice (One Player)'
            --print '2 - Roll the Dice (Two Player)'
            --print '3 - Exit Game'
            
            --selection = raw_input('Enter your selection: ')
            --while selection < '1' or selection > '3':
                ---print 'Invalid input - try again.'
                ---selection = raw_input('Enter your selection: ')

            --if selection == '1':
                ---playerOne, playerTwo = inputNames(selection, playerOne, playerTwo)
                ---while continueGame == 'y': #loop to continue game
                    ----winnerName = rollDice(p1numberOne, p1numberTwo, p1total, p2numberOne, p2numberTwo, p2total, playerOne, playerTwo, winnerName)
                    ----displayInfo(playerOne, p1numberOne, p1numberTwo, playerTwo, p2numberOne, p2numberTwo, winnerName)
                    ----continueGame = raw_input('Do you want to continue the dice rolling game? (Enter n for no and y for yes): ')
            --elif selection == '2':
                ---playerOne, playerTwo = inputNames(selection, playerOne, playerTwo)
                ---while continueGame == 'y': #loop to continue game
                   ----winnerName = rollDice(p1numberOne, p1numberTwo, p1total, p2numberOne, p2numberTwo, p2total, playerOne, playerTwo, winnerName)
                    ----displayInfo(playerOne, p1numberOne, p1numberTwo, playerTwo, p2numberOne, p2numberTwo, winnerName)
                    ----continueGame = raw_input('Do you want to continue the dice rolling game? (Enter n for no and y for yes): ')
            --elif selection == '3':
                ---print 'Better luck next time.'
                ---print 'Now... get ya broke *** outta heer!'
                
    --endProgram = raw_input('Do you want to end the "Dice Rolling" program? (Enter n for no and y for yes): ')
    --if endProgram == 'n':
        ---print 'Glad to hear you got your balls back.'
        ---print 'Starting a new game.'
    --elif endProgram == 'y':
        ---print 'Ending the game... Peace up, A town down.'


#this function gets the players names
def inputNames(selection, playerOne, playerTwo):
    -if selection == '1':
        --playerOne = raw_input('Player One; Enter your name: ')
        --playerTwo = 'Computer'
    -elif selection == '2':
        --playerOne = raw_input('Player One; Enter your name: ')
        --playerTwo = raw_input('Player Two; Enter your name: ')
    -return playerOne, playerTwo

#this function will get the random values
def rollDice(p1numberOne, p1numberTwo, p1total, p2numberOne, p2numberTwo, p2total, playerOne, playerTwo, winnerName):
    -p1numberOne = random.randint(1, 6)
    -p1numberTwo = random.randint(1, 6)
    -p1total = p1numberOne + p1numberTwo

    -p2numberOne = random.randint(1, 6)
    -p2numberTwo = random.randint(1, 6)
    -p2total = p2numberOne + p2numberTwo
    
    -if p1total > p2total:
        --winnerName = playerOne
    -elif p1total < p2total:
        --winnerName = playerTwo
    -elif p1total == p2total:
        --winnerName = 'Tie'
    -return winnerName

#this function displays the winner
def displayInfo(playerOne, p1numberOne, p1numberTwo, playerTwo, p2numberOne, p2numberTwo, winnerName):
    -print playerOne, p1numberOne
    -print playerOne, p1numberTwo
    -print
    -print playerTwo, p2numberOne
    -print playerTwo, p2numberTwo
    -print
    -print 'Congratulations! The winner is ',winnerName

#calls main
main()




>>> 
Welcome to my gambling games program.
May the best man, or machine win.

Menu Selection
1 - Roll the Dice (One Player)
2 - Roll the Dice (Two Player)
3 - Exit Game
Enter your selection: 1
Player One; Enter your name: John
John 0
John 0

Computer 0
Computer 0

Congratulations! The winner is  Computer
Do you want to continue the dice rolling game? (Enter n for no and y for yes): n
Menu Selection
1 - Roll the Dice (One Player)
2 - Roll the Dice (Two Player)
3 - Exit Game
Enter your selection: 2
Player One; Enter your name: john
Player Two; Enter your name: smith
Menu Selection
1 - Roll the Dice (One Player)
2 - Roll the Dice (Two Player)
3 - Exit Game
Enter your selection: 3
Better luck next time.
Now... get ya broke *** outta heer!
Do you want to end the "Dice Rolling" program? (Enter n for no and y for yes): y
Ending the game... Peace up, A town down.
>>>

---

### Post by debsankha on 2010-11-28
use random.randint(m,n) to generate integers between m and n.

---

### Post by spjackson on 2010-11-28
If you call displayInfo from rollDice you will see that you are getting sensible numbers, but the arguments that are passed in to rollDice are unchanged (i.e. revert to 0) once you return from rollDice.

You need to read up on pass by value, pass by reference and immutable objects in python.

---

### Post by TheWeakSleep on 2010-11-28
If you are going to post code, please use the ```
 or [php] tags, as it will make it much easier to read as well as preserving your indentation.

For instance, here is my attempt to solve your problem

[code]#!/usr/bin/env python
# A simple dice rolling program

import random

def main():
    while True:
        # May not be the prettiest way to make a prompt, but it works for me :p
        try:
            choice = int(raw_input('''What would you like to do?

[1] Roll the dice against a machine
[2] Roll the dice against a player
[3] Exit the game

>>>''' ))
            if choice == 1:
                playerOne = raw_input("What is your name? ")
                roll_the_dice(playerOne, 'Computer')
            elif choice == 2:
                playerOne = raw_input("Player One, what is your name? ")
                playerTwo = raw_input("Player Two, What is your name? ")
                roll_the_dice(playerOne, playerTwo)
            elif choice == 3:
                print "Goodbye!"
                break
        except:
            print "You must enter a number from the list\n."
    return 0

# This function 'rolls the dice' meaning it generates two random integers between 1 and 6 for each
# player. It computes the greater number and prints the winners
def roll_the_dice(playerOne, playerTwo):
    p1DiceOne = random.randint(1, 6)
    p1DiceTwo = random.randint(1, 6)
    p2DiceOne = random.randint(1, 6)
    p2DiceTwo = random.randint(1, 6)

    print "\n%s rolls a %i and a %i" % (playerOne, p1DiceOne, p1DiceTwo)
    print "%s rolls a %i and a %i\n" % (playerTwo, p2DiceOne, p2DiceTwo)

    if p1DiceOne + p1DiceTwo > p2DiceOne + p2DiceTwo:
        print "%s is the winner\n" % playerOne

    elif p2DiceOne + p2DiceTwo > p1DiceOne + p1DiceTwo:
        print "%s is the winner\n" % playerTwo

    else:
    print "It's a tie!\n"
    return 0

if __name__ == '__main__':
    main()

```

the [php] tags highlight syntax ;)

It's a good start though you could work on keeping your code more concise. (Mine may not be the best example :p )
For instance, you don't need to initialize the variables the way you are. You initialize 'selection' as '0' though later in your code you assign the same variable to raw_input.

I hope that you found this helpful, and that maybe my example will help, even if it's not the best example :p Most importantly have fun with python ;)

---

### Post by banditkeef on 2010-11-28
Yes, it was very helpful.

Thank you all for the input.

---

