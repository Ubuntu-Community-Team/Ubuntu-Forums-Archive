---
title: "Logic error in Python3 number guessing game"
date: 2010-04-20
forum: Programming Talk
---

### Post by MCVenom on 2010-04-20
Hey guys. I'm trying to make a simple game script where the player and 'computer' face off to guess the randomly picked number first. The problem is, at the end when the player is asked if he/she wants to keep playing, the game always restarts no matter what was entered ("", "No", "python", etc. will return as if "Yes" was entered). Here's the code:

```
#!/usr/bin/env python3.1

# Number Guess Versus Mode
# Player and Computer face off to guess the number first
# Computer has some limited AI, so beware!

# Copyright 2010, John King -- for questions, concerns, bugs, or ideas
# on how to improve the code, email me at kingj.developer@gmail.com

# ========================GPL NOTICE==================================
# This program is free software: you can redistribute it and/or modify
# it under the terms of the GNU General Public License as published by
# the Free Software Foundation, either version 3 of the License, or
# (at your option) any later version.
#
# This program is distributed in the hope that it will be useful,
# but WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
# GNU General Public License for more details.
#
# You should have received a copy of the GNU General Public License
# along with this program.  If not, see <http://www.gnu.org/licenses/>.
# =====================================================================

# Please don't let the copyright and GPL notices fool you -- I'm not vain enough to believe
# they're necessary for such a simple program;
# I just like being able to tell people I've written copyrighted and/or GPL'ed software xD

#=======================PROGRAM START================================

import random # Import the random module so we can make our random numbers
game_loop = True # Allows the player to keep playing new games as long as they wish.

while game_loop == True:
        i = "Prompt" # Allows us to determine if the player wants to keep playing.

        print("\tWelcome to Number Guess Vs. Computer! (Better name TBA),")
        print("Simply guess the number before the computer does.")

        target_number = random.randint(1,100) # Pick the random number
        max_ai = 100 # Set our beginning AI bounds for the computer
        min_ai = 1
        guessed_number = 0 # Initialize our guessed number variable

        while guessed_number != target_number: # While no one has guessed the number correctly
                guessed_number = input("\nPlease guess a number. ") # Have the player guess the number.

                if guessed_number == "": # This loop fixes an issue which causes the program to crash if nothing is entered 
                        guessed_number = 0 # Ideally, this loop should also check for non-numeric values and deal with them too
                        continue # But I don't know how to do that yet -_-;

                guessed_number = int(guessed_number) # Makes sure the guessed_number variable is set as an integer type

                if guessed_number == target_number: # If the player guesses the number right
                        print("\nYou have won!") # Congratulate him/her,
                        break # Then end the game
                elif guessed_number > target_number: # If the guessed number is too high
                        print("Your number is too high.") # Tell the player
                        max_ai = guessed_number # And have the computer take note of this for it's artificial intelligence bounds
                elif guessed_number < target_number: # If the guessed number is too low
                        print("Your number is too low.") # Tell the player
                        min_ai = guessed_number #  And have the computer take note of this for it's artificial intelligence bounds 

                guessed_number = random.randint(min_ai, max_ai) # Have the computer guess the number, ruling out numbers already shown to be too low or too high

                if guessed_number == target_number:
                        print("\nThe computer has guessed the correct number,", str(target_number) + ", and has won!")
                        break
                elif guessed_number > target_number:
                        print("The computer's guessed number was too high.")
                        max_ai = guessed_number
                elif guessed_number < target_number:
                        print("The computer's guessed number was too low.")
                        min_ai = guessed_number

                # print("Artificial Intelligence bounds:", str(min_ai) + ",", str(max_ai)) # Prints what the computer has figured as the bounds that the target number is in.
                # ^This line was used to test the program's AI
    
        while i == "Prompt":
                keep_playing = input("\nWould you like to play another game? ")
                print("\n")
                
                if keep_playing == "Yes" or "Y" or "y" or "yes" or "YES":
                        i = "Restart"
                elif keep_playing == "No" or "N" or "n" or "no" or "NO":
                        i = "Stop"
                        game_loop = False
                else:
                        print("I'm sorry, I didn't quite understand you, could you repeat that?")
                        print("(P.S.: Try 'Yes' or 'No')")
            
input("\n\nPress the enter key to exit.")    
```

Any ideas? Thanks in advance.

---

### Post by Tony Flury on 2010-04-20
You can't do comparisons the way you are trying to do them 

```

if a == "a" or "b" or "c" :

```
will always succeed - as each string "b", "c" will always be true.

what you need is something like this
```

if a == "a" or a == "b" or a == "c":

```
or even better 
```

if a in ["a", "b", "c"] :

```

---

### Post by MCVenom on 2010-04-20
> **Tony Flury said:**
> You can't do comparisons the way you are trying to do them 

```

if a == "a" or "b" or "c" :

```
will always succeed - as each string "b", "c" will always be true.

what you need is something like this
```

if a == "a" or a == "b" or a == "c":

```
or even better 
```

if a in ["a", "b", "c"] :

```
Thanks for the help, the script works fine now :D

---

