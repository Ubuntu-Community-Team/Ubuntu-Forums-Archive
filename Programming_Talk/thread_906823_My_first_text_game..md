---
title: "My first text game."
date: 2008-08-31
forum: Programming Talk
---

### Post by dodle on 2008-08-31
Here is a little text game (very simple) that I have made.  I could use a little constructive criticism.  I'm sorry if the code is messy, I'm not very good with functions yet.  Functions were always a weak spot for me in mathematics, and I guess it is the same for me in programming.  You'll noticed that I defined some functions, but I never used them anywhere in the code.

Also at the end of the game the option is given to start over.  Is there a way to do this without importing.  Importing to restart doesn't seem like a good idea.```
instructions = "To move press one of the following keys + 'enter':\nn (north), \
s (south), e (east), w (west)\nTo see your status type 'stats'.\
\n\nThe purpose of this game is to find and defeat the dragon.\n\
There are three locations on the map that will give you enhanced stats\n\
but, there are also three locations that will deplete your hp."


# Stats

# Player's Initial Health
hp = 30

# Dragon's Health
dhp = 100

# Equipment
equip1 = "none" #sword
equip2 = "none" #shield
equip3 = "none" #armor'


def user_name():
    print name, surname

def user_name1():
    print name

def user_name2():
    print surname

name = raw_input("What is your first name?")
surname = raw_input("what is your last name?")

print
print 'Welcome', name, surname, 'to my game!'
print
print 'To see instructions type "inst"'
print
# Controls & Commands

x = 0
y = 0
n = "north"
s = "south"
e = "east"
w = "west"
spring = "none"

trap1 = "none"
trap2 = "none"
trap3 = "none"

# The Borders of the Map

while (x,y) != (-3,-1):
  if x > 10:
    x = x - 1
    print
    print "This is as far as you can go."
  if x < -10:
    x = x + 1
    print
    print "This is as far as you can go."
  if y > 10:
    y = y - 1
    print
    print "This is as far as you can go."
  if y < -10:
    y = y + 1
    print
    print "This is as far as you can go."

# Current Location
  print
  print "You are at", (x,y)
  
# Areas Where Equipment and Health Can Be Found


  if equip2 == "none" and (x,y) == (9,-9):
    equip2 = "shield"
    print
    print "You have acuired the shield!"

  if equip1 == "none" and (x,y) == (-1,-3):
    equip1 = "sword"
    print
    print "You have acuired the sword!"

  if spring == "none" and (x,y) == (10,8):
    spring = "entered"
    hp = hp + 30
    print
    print "You have entered the Holy Spring.\nYou have received +30 Health."

# Traps!


  if (x,y) == (-2,-1) and trap1 == "none":
    hp = hp - 5
    trap1 = "entered"
    print
    print "You have walked into a sand trap and lost 5 Health."
  
  if (x,y) == (-6,5) and trap2 == "none":
    hp = hp - 8
    trap2 = "entered"
    print
    print "you are attacked by wolves and barely escape with your life.\nYou lose 8 Health."
  
  if (x,y) == (-2,-7) and trap3 == "none":
    hp = hp - 10
    trap3 = "entered"
    print
    print "Your are stranded in the desert without food or water.\nYou lose 10 health."
    
# Begin Game
    
  answer = raw_input("Which direction would you like to go? \n:")
  if answer == "stats":
    print
    print "Health: ", hp, "\n" "Right Hand: ", equip1, "\n", "Left Hand: ", equip2
  if answer == "inst":
    print
    print instructions
  if answer == "n":
      y = y + 1
  if answer == "s":
      y = y - 1
  if answer == "e":
      x = x + 1
  if answer == "w":
      x = x - 1


# Response to invalid commands.
  elif answer != "n" and answer != "s" and answer != "e" and answer != "w" and answer != "stats" and answer != "inst":
      print
      print 'I don\'t understand "%s", try again.' % answer
      

# Final Battle



battle = "active"

print
print "You stand before the drawbridge of the castle, \nbefore the bridge a green dragon stands guard."
while battle == "active":
      print
      print "What will you do?"
      choice = raw_input('"r" for Run, "f" for Fight":')
      if choice == "stats":
          print
          print "Health: ", hp, "\n", "Right Hand: ", equip1, "\n", "Left Hand:", equip2
      if choice == "r":
          battle = "escaped"
      if choice == "f":
        if equip1 == "none":
            print
            print "You hit the dragon causing 4 damage."
            dhp = dhp - 4
        if equip1 == "sword":
            print
            print "you hit the dragon causing 10 damage!"
            dhp = dhp - 10
        if equip2 == "none":
            print
            print "The dragon attacks, causing you 7 damage."
            hp = hp - 7
            print "Your hp is ", hp, "\b."
        if equip2 == "shield":
            print
            print "The dragon attacks, only causing you 4 damage."
            hp = hp - 4
            print "Your Health is ", hp, "\b."
      if choice != "f" and "r" and "stats" and "inst":
          print
          print "You miss the dragon and hit yourself!"
          print "You lose 6 health."
          hp = hp - 6
          print "your hp is ", hp, "\b."
      if hp <= 0:
          battle = "lost"
      elif dhp <= 0:
          battle = "won"
          
if battle == "escaped":
    print "Too bad you are chicken!"
    print
if battle == "lost":
    print "You have lost your life to the dragon.\nGame Over"
    print
if battle == "won":
    print "Congratulations!  You have slain the dragon and saved the Kingdom."
    print
    
rebt = "no"
while rebt == "no":
    GameOver = raw_input('Would you like to play again?\ny or n: ')
    if GameOver == "n":
      rebt = "yes"
    if GameOver == "y":
      import MyGameNoImport
print
      

```Attached is a little map, so that nobody gets too bored trying to find stuff.

Orange - starting point
Yellow - equipment
Blue - spring
Red - traps
Violet - target

---

### Post by mdawg414 on 2008-09-01
I like what I see so far dodle. This is a cool idea to start with because you can continue to develop it further and add interesting features. You should definitely look into using functions, it will make your life a LOT easier when you have to go back and modify the code.

Maybe in the next version you can experiment with a visual representation of the world rather than just printing the coordinates. Google a tutorial on how to clear the screen with python so the user's inputs don't scroll up the screen. And for restarting the game, my suggestion would be to set the health, location, and all of that back to the original values and continue running the program from there. Again, easy to do with some functions. Good job so far!

---

### Post by dodle on 2008-09-01
Thanks Mdawg, I appreciate your input.  I wanted to start working on a graphical version but figured I should get functions down first. This is actually my very first attempt at programming (other than 'Hello World').  I've never had any experience in C++, Java, or any other language.  If I get Python down, I might try another language.

---

### Post by Bachstelze on 2008-09-01
```
if choice != "f" and "r" and "stats" and "inst":
```

What were you expecting this to do? It's more than likely that it's not what it actually does.

---

### Post by Sinkingships7 on 2008-09-01
For things like damage statistics and whatnot, you could make it more real by adding random numbers into the mix. Say you have a dragon attacking, and you want him to be able to do some damage points no higher than 5, and no less than 2, you could do something like this:
[PHP]
damage = random.randrange(2, 5)
[/PHP]
Make sure you import the random library at the top before using random numbers.
[php]
import random
# OR
from random import randrange
[/php]

---

### Post by MONODA on 2008-09-01
Good job and congratulations I suggest looking into classes and using those to organize you game further. Here are a few good python references:
[http://www.livewires.org.uk/python/home](http://www.livewires.org.uk/python/home)
[http://diveintopython.org/](http://diveintopython.org/)
[http://www.python.org/doc/](http://www.python.org/doc/)

I highly recommend the first tutorial to any python and programming beginner, they were very helpful to me. The eventually teach you how to make a pacman and an astroids game :D
those will be very helpful to you and dont just follow one tutorial, go along several, that way you can learn the same things in a different way.

---

### Post by dodle on 2008-09-01
> **HymnToLife said:**
> ```
if choice != "f" and "r" and "stats" and "inst":
```

What were you expecting this to do? It's more than likely that it's not what it actually does.

That's for if a command is typed other than those four during battle, then the result is this:```
          print "You miss the dragon and hit yourself!"
          print "You lose 6 health."
          hp = hp - 6

```[QUOTE=Sinkingships7]For things like damage statistics and whatnot, you could make it more real by adding random numbers into the mix. Say you have a dragon attacking, and you want him to be able to do some damage points no higher than 5, and no less than 2, you could do something like this:
[PHP]damage = random.randrange(2, 5) [/PHP]
Make sure you import the random library at the top before using random numbers.

[PHP]import random
# OR
from random import randrange[/PHP][/QUOTE]Thanks Sinkingships7, I was wondering how I was going to do that.

---

### Post by lordhaworth on 2008-09-01
Id also recommend randomising the location of the items you can pick up. 

Also, if you eventually wanted to add a text-graphical aspect (i.e. a character for the player and characters for monsters/scenery etc?) for the boundaries of the game you could place some text characters (i.e. "] or [" at the locations where you display

> 
print "This is as far as you can go."


and make it so that if they try to move into the boundary nothing happens - i.e. make a wall. You could also implement this within the grid (or future sub grids to make mazes/caves etc). 

Things like this are great because you can always add more to them - but loooking very good so far!

---

### Post by Paul Miller on 2008-09-01
> **dodle said:**
> That's for if a command is typed other than those four during battle, then the result is this:```
          print "You miss the dragon and hit yourself!"
          print "You lose 6 health."
          hp = hp - 6

```

In that case, what you want is
```

if choice not in ["f", "r", "stats", "inst"]:

```

---

### Post by dodle on 2008-09-01
> **dodle said:**
> Also at the end of the game the option is given to start over.  Is there a way to do this without importing.  Importing to restart doesn't seem like a good idea.

This is causing an error in the game; It only allows playing through the game twice.  Is there a way to return to the top of the script without exiting the program?  

Thanks for the input everybody, I'm having a lot of fun with this.

---

### Post by lordhaworth on 2008-09-01
> 
Quote:
Originally Posted by dodle  
Also at the end of the game the option is given to start over. Is there a way to do this without importing. Importing to restart doesn't seem like a good idea. 

This is causing an error in the game; It only allows playing through the game twice. Is there a way to return to the top of the script without exiting the program? 

Thanks for the input everybody, I'm having a lot of fun with this. 


Couldn't you achieve this with a DO loop? It seems as though you specify all starting parameters at the beginning? Make the game loop until the users response triggers it not to continue anymore.

i.e. in pseudoish code example 

```

do while (continue == 1){
 # Stats

 # Player's Initial Health
 hp = 30

 # Dragon's Health
 dhp = 100

 # Equipment
 equip1 = "none" #sword
 equip2 = "none" #shield
 equip3 = "none" #armor'

...
...
...

while rebt == "no":
    GameOver = raw_input('Would you like to play again?\ny or n: ')
    if GameOver == "n":
      continue = 0:
    if GameOver == "y":

...
...
end do

```

EDIT (Excuse all errors!)

---

### Post by dodle on 2008-09-01
"do while" gives me an invalid syntax error.

---

### Post by pmasiar on 2008-09-01
> **MONODA said:**
> I suggest looking into classes and using those to organize you game further. Here are a few good python references:
[http://www.livewires.org.uk/python/home](http://www.livewires.org.uk/python/home)
[http://diveintopython.org/](http://diveintopython.org/)
[http://www.python.org/doc/](http://www.python.org/doc/)

I **DO NOT** recommend classes and OOP - you will get confused. Livewire intro is good, but "Dive into Python" is for experienced programmers learning Python as second language, not first.

See wiki in my sig for good Python intro for beginners, and more tasks to solve.

---

### Post by Bachstelze on 2008-09-01
> **dodle said:**
> This is causing an error in the game; It only allows playing through the game twice.  Is there a way to return to the top of the script without exiting the program?  

Thanks for the input everybody, I'm having a lot of fun with this.

If I were you, I'd use a while loop around your whole script (there is no do...while in Python). Example :

```
exit = False
while not exit :

    #all the game stuff here.

    print "Game over, do you want to play again? (y/n)"

    while True :
        a = raw_input()

        if a == "n" :
            exit = True

        if a in ["y", "n"] :
            break

```

---

### Post by signifer123 on 2008-09-01
Or you could have the Game in a method all to itself. 

```

def Game:
    #Game Code Here
    print "Play Again?(y/n)"
    u = raw_input()
    return u

#Start First Game
run = "y"
while run == "y":
     run=Game()

```

---

### Post by Bachstelze on 2008-09-01
> **signifer123 said:**
> Or you could have the Game in a method all to itself.

```

def Game:
    #Game Code Here
    print "Play Again?(y/n)"
    u = raw_input()
    if u == "y":
          Game()

#Start First Game
Game()

```

No, this would be very bad practice. Recursivity should not be used that way.

---

### Post by nvteighen on 2008-09-01
First, break out the game into pieces (functions) before getting yourself into Object Oriented Programming (aka OOP) using classes. I have to admit this is the task for such an approach, as it makes everything more intuitive (you have a "sword" object, a "player", a "dragon, etc. and you assign each one some propierties and actions...) but it's a bit harder concept to master and not absolutely necessary, so better let's use the second-best: procedural programming.

What you need is to recognize common patterns. For example, common actions that will be performed many times, like "moving around the map". But, of course, you just can't move from nowhere to no place (unless you're the Nowhere Man from The Beatles :)...) you need to know the starting position and the steps you want to move... So, let's create a function for that, that accepts a 'current_position' list in the form [x, y] and a 'steps' list [x, y] that will be performed:

[PHP]
def move(current_position, steps):
    current_position[0] += steps[0] # x += y is shorthand for x = x + y.
    current_position[1] += steps[1]
[/PHP]

Ok, this is a *very* rough way to do it. What's nice about that? That you just need to pass [1,1] into steps to have the player moving north-east, for example, or if I invented a magical potion that makes you faster, it'd allow you to "warp" 4 steps... etc... Anyway, you just use it this way:

[PHP]
player_pos = [0, 0] # player's initial position

# ...code...
# Oh, we have to move now southwards!
move(player_pos, [0, -1])

# Now, two spaces north, 21 east!
move(player_pos, [2, 21])
[/PHP]

Do you notice the huge amount of flexibility you gain just because of that simple function? Why? Because all moves around the map will be of the same type... and if you want to add a second player, the same function will work for him/her too!

Other common patterns, for example, changes in the player's health (either positive 'cure' or negative 'damage') could be modeled into a function you call each time it's necessary. Or "finding something"... everytime you find something you do the same: add the item to the player's "bag"... and so on.

If you do it that way, you'll be able to extend the game in a reasonably easy way.

EDIT: About restarting... if you apply this concepts I told you here, it will be quite easy.

---

