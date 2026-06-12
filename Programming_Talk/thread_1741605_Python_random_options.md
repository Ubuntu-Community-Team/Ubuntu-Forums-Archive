---
title: "Python: random options"
date: 2011-04-28
forum: Programming Talk
---

### Post by masque7 on 2011-04-28
I've written some Python code. 3 possible answers to simple sums are presented. Out of the 3 possible answers, sometimes 2 of them are the same. Sometimes even all 3 are the same. Example:

Question: 2+2
Answers: 
a. 1
b. 4
c. 4

```
import random
from pygame import *   # import all pygame functions

count = 0      # Sentry variables
score = 0

file1 = open('words.txt', 'r')      # Open text files
file2 = open('images.txt', 'r')

f1content = file1.readlines()      # Get content
f2content = file2.readlines()

init()               # Start PyGame
screen = display.set_mode((640, 480))   # Produces window
display.set_caption('Numeracy')   # Sets title

font = font.Font(None, 48) # Font object 'None' = system default, size 48

while count < 10: # Main loop, runs 10 times
   screen.fill(0)   # Fills screen with black

   # Random number for image shown
    # limited to number of entries in images.txt
   wordnum = random.randint(0, len(f2content)-1)

   # Randnum indicates the line of images.txt
   # corresponding to an image file
   mainpic = image.load(f2content[wordnum].rstrip('\n')) # Strip newline char

   # Draw images at top-center of screen
   screen.blit(mainpic, (255, 50))

   # Choose 3 random options
   options = [random.randint(0, len(f1content)-1),
      random.randint(0, len(f1content)-1),
      random.randint(0, len(f1content)-1)]

   # One of them the real answer
   options[random.randint(0, 2)] = wordnum

   # Draw the 3 possible answer words from f1content[] array
    #' True' for the second = anti-alias.
    # colours (red, green, blue) aka white
   text1 = font.render('(PRESS 1) = ' + f1content[options[0]].rstrip('\n'),
      True, (255, 255, 255))
   text2 = font.render('(PRESS 2) = ' + f1content[options[1]].rstrip('\n'),
      True, (255, 255, 255))
   text3 = font.render('(PRESS 3) = ' + f1content[options[2]].rstrip('\n'),
      True, (255, 255, 255))

   # Draw those words to the screen (horiz, vertical)
   screen.blit(text1, (30, 200))
   screen.blit(text2, (30, 300))
   screen.blit(text3, (30, 400))

   # Update everything
   display.update()

   done = False   # Sentry var for next loop

   # Wait for keyboard event. If key KEYUP, check if 1 key (K_1),
   # or 2, etc. When answer key, set to 'done' = True to exit loop
   while not done:
      for e in event.get():
         if e.type == KEYUP:
            if e.key == K_1:
               answer = 1
               done = True
            if e.key == K_2:
               answer = 2
               done = True
            if e.key == K_3:
               answer = 3
               done = True

   # Prints correct in green, increments to score
   if options[answer-1] == wordnum:
      resulttext = font.render('Correct!', True, (50, 255, 50))
      score += 1
   # Wrong - red text
   else:
      resulttext = font.render('Wrong!', True, (255, 50, 50))

   # Show the text
   screen.blit(resulttext, (450, 300))
   display.update()

   # Keypress before the next question
   while event.wait().type != KEYDOWN: pass

   count += 1

# Print the score when loop finished
print '\nYour score is:', score

```

How can I fix it so that each of the 3 answers are individual yet randomised options? I suppose this would contain a lot of comparing but the issue is that they aren't 3 separate varibles.

---

### Post by andrew1992 on 2011-04-28
A simple way would be to store the random items in a list if they are unique, and use a while loop until the list is of length 3 in your case.

```

my_list = []
while (len(my_list) < 3):
    number = get_random_number()
    if number not in my_list:
        my_list.append(number)

```

---

### Post by DaithiF on 2011-04-28
alas, if only the python random module contained a function to return a random sample of a certain size from a population, that would be pretty useful, huh?  But probably not worth checking the docs, because it hardly seems likely...

but wait ... whats this? [http://docs.python.org/library/random.html#random.sample](http://docs.python.org/library/random.html#random.sample)

```
options = random.sample(xrange(len(f1content)), 3)

```

---

### Post by andrew1992 on 2011-04-28
Haha nice. I too often default to re-inventing the wheel :)

---

