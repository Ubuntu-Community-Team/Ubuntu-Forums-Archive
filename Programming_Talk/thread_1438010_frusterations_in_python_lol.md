---
title: "frusterations in python lol"
date: 2010-03-24
forum: Programming Talk
---

### Post by XXMy_Little_ShinigamiXX on 2010-03-24
hi all im trying to pretty much get the same thing in the tutorial but without using their source code and trying my own first before doing theyres. i almost got it but a couple of things are really not wanting to cooperate lol. 
first off let me post the source right quick, its tic tac toe:

```

import time
import random
#-----------------
global TTT1
global TTT2
global TTT3
global Line
TTT1 = ['1', '2', '3']
TTT2 = ['4', '5', '6']
TTT3 = ['7', '8', '9']
Line = '--------------'   
#-------------------

def Main_Menu():
 print 'Play'
 print 'How to play'
 print 'Version'
 nothing = raw_input('')
 if nothing.capitalize() == 'Play':
     Start()
 elif nothing.capitalize() == 'How to play':
     How_To_Play()
 elif nothing.capitalize() == 'Version':
     print ''
     print 'Ver. 1.0'
     print ""
     Main_Menu()
 else:
     print ''
     print 'please enter an option from the menu above'
     print ''
     Main_Menu()


def Start():
 global Players_Choice
 Players_Choice = ''
 print 'please either choose X or O team'
 nothing = str(raw_input(''))
 if nothing not in 'X O'.split():
  Start()
 else:
  Players_Choice = nothing
  RANDOMSTART()
 
def RANDOMSTART():
 num = random.randint(1, 2)
 if num == 1: AIPLAY()     
 elif num == 2: Play()
      
def AIPLAY():
 global TTT1
 global TTT2
 global TTT3
 global Line
 global Players_Choice
 global AIChoice
 AIChoice = ''
 #---------#
 time.sleep(random.randint(1, 2))
 
 if Players_Choice == 'O':
  AIChoice = 'X'
 else: 
  AIChoice = 'O'
 
 if TTT2[1] in ['O', 'X']:
  pass
 else:
  del TTT2[1]
  TTT2.insert(1, AIChoice)
  Play()
 
 if TTT2[1] in ['O', 'X']:
  pass
 else:
  del TTT2[1]
  TTT2.insert(1, AIChoice)
  Play()
 
 if TTT1[1] in ['O', 'X']:
  pass
 else:
  del TTT1[1]
  TTT1.insert(1, AIChoice)
  Play()
 
 if TTT3[1] in ['O', 'X']:
  pass
 else:
  del TTT3[1]
  TTT3.insert(1, AIChoice)
  Play()
 
 if TTT2[0] in ['O', 'X']:
  pass
 else:
  del TTT2[0]
  TTT2.insert(0, AIChoice)
  Play()

 if TTT3[0] in ['O', 'X']:
  pass
 else:
  del TTT3[0]
  TTT3.insert(0, AIChoice)
  Play()
 
 if TTT1[0] in ['O', 'X']:
  pass
 else:
  del TTT1[0] 
  TTT1.insert(0, AIChoice)
  Play() 
 
 if TTT2[2] in ['O', 'X']:
  pass
 else:
  del TTT2[2]
  TTT2.insert(2, AIChoice)
  Play()
 
 if TTT1[2] in ['O', 'X']:
  pass
 else:
  del TTT1[2]
  TTT1.insert(2, AIChoice)
  Play()
  
 if TTT3[2] in ['O', 'X']:
  pass
 else:
  del TTT3[2]
  TTT3.insert(2, AIChoice)
  Play()
     
      
def Play(): 
 global TTT1
 global TTT2
 global TTT3
 global Line
 global AIChoice
 global Players_Choice 
#-----------|
 print TTT1
 print Line
 print TTT2
 print Line
 print TTT3     
# ----------| this is where the board is displayed after each run through
 ####if AIChoice in [TTT1[0] and TTT1[1] and TTT1[2]] or [TTT1[0] and TTT2[0] and TTT3[0]] or [TTT1[0] and TTT2[1] and TTT3[2]] or [TTT1[1] and TTT2[1] and TTT3[1]] or [TTT1[3] and TTT2[3] and TTT3[3]] or [TTT2[0] and TTT2[1] and TTT2[2]] or [TTT3[0] and TTT3[1] and TTT3[2]] or [TTT3[0] and TTT2[1] and TTT1[2]]:
 #### print 'the computer won'
 ####else: pass
#### for i in range(1, 10):
 #### choose = raw_input('please enter a choice for where you want to move 1-9: ')
  ####if choose in i:
   #####return choose
   #####break
  ####else:
   ####print 'please enter only 1-9'
 try:
  choose = int(choose)
 except ValueError:
  print ''
  print 'Please enter your Character', Players_Choice, 'into one of the numbers'
  print ""
  Play()
 # this is = to -1 to start the index at 0 when you push 1 for ex..
 ####for i in range(1, 10):
 #### while choose in range(i):
 if choose == 1 or choose == 2 or choose == 3:
  choose = choose - 1  
  del TTT1[choose]
  TTT1.insert(choose, Players_Choice)
 elif choose == 4 or choose == 5 or choose == 6:
  choose = choose - 4
  del TTT2[choose]
  TTT2.insert(choose, Players_Choice)
 elif choose == 7 or choose == 8 or choose == 9:
  choose = choose  - 7
  del TTT3[choose]
  TTT3.insert(choose, Players_Choice)
 else:
  print ''
  print 'please enter only numbers 1-9'
  print ''
  Play() 
  
 #if Players_Choice in [TTT1[0] and TTT1[1] and TTT1[2]]:
 # print 'you won!!!'
 #elif Players_Choice in [TTT1[0] and TTT2[0] and TTT3[0]]:
 # print 'you won!!!'  
 #elif Players_Choice in [TTT1[0] and TTT2[1] and TTT3[2]]:
 # print 'you won!!!'
 #elif Players_Choice in [TTT1[1] and TTT2[1] and TTT3[1]]:
 # print 'you won!!!'
 #elif Players_Choice in [TTT1[2] and TTT2[2] and TTT3[2]]:
  #print 'you won!!!' 
 #elif Players_Choice in [TTT2[0] and TTT2[1] and TTT2[2]]:
 # print 'you won!!!'
 #elif Players_Choice in [TTT3[0] and TTT3[1] and TTT3[2]]:
 # print 'you won!!!'
 #elif Players_Choice in [TTT3[0] and TTT2[1] and TTT1[2]]:
 # print 'you won'
 #else: 
 # pass
 AIPLAY()

def How_To_Play():
 global TTT1
 global TTT2
 global TTT3
 print TTT1
 print Line
 print TTT2
 print Line
 print TTT3
 print 'the numbers on the board will represent'
 print 'the number you will put in the keyboard'
 print 'once you have selected either the O or X team.'
 print 'whoever is the first to get three in a row wins.'
 Main_Menu()
  
  # The game starts here and calls the main menu function as defined above
print 'welcome to Tic-Tac-Toe'
print 'to get started press enter: '
nothing = raw_input('')
Main_Menu()

```the things marked with 4 of # are coding i am trying but is not working.  im trying to use things much more advanced than jsut if statements when i can. also you may have noticed this line:
```

 #if Players_Choice in [TTT1[0] and TTT1[1] and TTT1[2]]:
 # print 'you won!!!'
 #elif Players_Choice in [TTT1[0] and TTT2[0] and TTT3[0]]:
 # print 'you won!!!'  
 #elif Players_Choice in [TTT1[0] and TTT2[1] and TTT3[2]]:
 # print 'you won!!!'
 #elif Players_Choice in [TTT1[1] and TTT2[1] and TTT3[1]]:
 # print 'you won!!!'
 #elif Players_Choice in [TTT1[2] and TTT2[2] and TTT3[2]]:
  #print 'you won!!!' 
 #elif Players_Choice in [TTT2[0] and TTT2[1] and TTT2[2]]:
 # print 'you won!!!'
 #elif Players_Choice in [TTT3[0] and TTT3[1] and TTT3[2]]:
 # print 'you won!!!'
 #elif Players_Choice in [TTT3[0] and TTT2[1] and TTT1[2]]:
 # print 'you won'
 #else: 
 # pass

```is the exact same as saying this: but i liek this version better due to more efficiant:
```

 ####if AIChoice in [TTT1[0] and TTT1[1] and TTT1[2]] or [TTT1[0] and TTT2[0] and TTT3[0]] or [TTT1[0] and TTT2[1] and TTT3[2]] or [TTT1[1] and TTT2[1] and TTT3[1]] or [TTT1[3] and TTT2[3] and TTT3[3]] or [TTT2[0] and TTT2[1] and TTT2[2]] or [TTT3[0] and TTT3[1] and TTT3[2]] or [TTT3[0] and TTT2[1] and TTT1[2]]:

```problem is neither of them work properly, i switched to the first to make things easier to debug but to no avail, just frusteration. lol... i have spent hours trying to come to why this is messing up and i have nothing, the only thing i can tell you is what its doing: which btw those are the combonations to win: i suppose it has something to do with the 'and' and 'or' statements im using but im not sure. if you read from the first example its easier to follow. using those combonations they work yes, let me explain. if i had the following scenerio:

X X X
-------
O O 6
-------
7, 8 O

because i got 3 in a row up top, it would print i won, so that portion of it works, however i dont know why its doing this but all i have to do to make it print that is move x to the top right, in other words square 3 first list index 2. all of those statements work the same, so every single end statement abotu the location of Players_Choice either X or O when put in even if you have no other peices on the board will tell you youve won.

so if i had this, and well say the game jsut started and i go first:  

1 2 X
------
4 5 6
------
7 8 9

as you can see no other pieces on the board, yet i win lol. no dont get me wrong, the code says i won too if i put X in all three squares up top, but why is it doing this?

on to my second issue, i am trying to make the input only = to int 1 - 9: 
i have tried so many different pieces of code its driving me bonkers. i even tried one involving the len() method, but that was only for strings i found out lol. dont get me wrong i can do it with a simple else statement, but i wanted something fancier lol. i feel like im always using if and else statements, ugh. lol its frusterating lol. so then i tried something liek these before adding that else in:

```

ex 1
for i in range(1, 10):
 while choose in range(i):
 return choose 
 break

ex2
if choose in '1, 2, 3, 4, 5, 6, 7, 8, 9' .split()
but of course the boolean value would return false when you tried to compare the two because youre comparing a list int to an int, not the same thing.:
also i tried 
while choose >= 1 and choose <= 9:
that didnt work either. 

```also quesiton 3 which is kind of off to the side, but how does this work? maybe i just dont understand. 

```

def Start():
 global Players_Choice
 Players_Choice = ''
 print 'please either choose X or O team'
 nothing = str(raw_input(''))
 if nothing not in 'X O'.split():
  Start()
 else:
  Players_Choice = nothing
  RANDOMSTART()

```what i want to know is that line where it makes nothing into a string, and it is comparing it to see if that string is in a list. so from what im concluding a string is found in a list, a list is a colleciton of strings, integer or otherwise correct? because the statement i tried above when comparing if choose in made those int into a list value, im assuming it will alwyas return false because the int even though it is in the list isnt considered an int, but a string.... am i right? im not sure thats why i want to ask. also im still using 2.64 so im not sure if maybe that has sometihng to do with some of this working or not. i know it 
did in the last one, when snova helped me and told me i could make this dict value:

words = {
'dict1': 'something in here'.split(),
'dict2': 'something in here'.split()
}

i found out in 2.64 this code doesnt work but with one keyword, value list at a time. so if you were to do that you would have to say :

words = {
'dict1': 'somethign goes here'.split()
}

because i can only do 1 keyword, value pair. now his code was great and it works, but not in 2.64. sorry actually it works in 2.64 i just didnt even think of putting a comma in, i should have payed attention more. 
as always any input is appreciated :popcorn: thanks

EDIT----- comma added

---

### Post by lavinog on 2010-03-24
First, your code is hard to read.
Try and break it up into more functions such as your test for winning could be a function:
```

def check_for_win(TTT1,TTT2,TTT3):
 #if Players_Choice in [TTT1[0] and TTT1[1] and TTT1[2]]:
 # return True
 #elif Players_Choice in [TTT1[0] and TTT2[0] and TTT3[0]]:
 # return True
 #elif Players_Choice in [TTT1[0] and TTT2[1] and TTT3[2]]:
 # return True
 #elif Players_Choice in [TTT1[1] and TTT2[1] and TTT3[1]]:
 # return True
 #elif Players_Choice in [TTT1[2] and TTT2[2] and TTT3[2]]:
 # return True
 #elif Players_Choice in [TTT2[0] and TTT2[1] and TTT2[2]]:
 # return True
 #elif Players_Choice in [TTT3[0] and TTT3[1] and TTT3[2]]:
 # return True
 #elif Players_Choice in [TTT3[0] and TTT2[1] and TTT1[2]]:
 # return True
 #else: 
 # return False

```
This will help if you want to change the winning message without having to update a bunch of lines.

Also instead of using TTT1, TTT2, TTT3 you could just use a nested list:
```

TTT_Board = [ ['1', '2', '3'],
              ['4', '5', '6'],
              ['7', '8', '9'] ]


```

reference it with TTT_Board[row][col]

---

### Post by snova on 2010-03-24
> **XXMy_Little_ShinigamiXX said:**
> the things marked with 4 of # are coding i am trying but is not working.  im trying to use things much more advanced than jsut if statements when i can. also you may have noticed this line:
```

 #if Players_Choice in [TTT1[0] and TTT1[1] and TTT1[2]]:
 # print 'you won!!!'
 #elif Players_Choice in [TTT1[0] and TTT2[0] and TTT3[0]]:
 # print 'you won!!!'  
 #elif Players_Choice in [TTT1[0] and TTT2[1] and TTT3[2]]:
 # print 'you won!!!'
 #elif Players_Choice in [TTT1[1] and TTT2[1] and TTT3[1]]:
 # print 'you won!!!'
 #elif Players_Choice in [TTT1[2] and TTT2[2] and TTT3[2]]:
  #print 'you won!!!' 
 #elif Players_Choice in [TTT2[0] and TTT2[1] and TTT2[2]]:
 # print 'you won!!!'
 #elif Players_Choice in [TTT3[0] and TTT3[1] and TTT3[2]]:
 # print 'you won!!!'
 #elif Players_Choice in [TTT3[0] and TTT2[1] and TTT1[2]]:
 # print 'you won'
 #else: 
 # pass

```is the exact same as saying this: but i liek this version better due to more efficiant:
```

 ####if AIChoice in [TTT1[0] and TTT1[1] and TTT1[2]] or [TTT1[0] and TTT2[0] and TTT3[0]] or [TTT1[0] and TTT2[1] and TTT3[2]] or [TTT1[1] and TTT2[1] and TTT3[1]] or [TTT1[3] and TTT2[3] and TTT3[3]] or [TTT2[0] and TTT2[1] and TTT2[2]] or [TTT3[0] and TTT3[1] and TTT3[2]] or [TTT3[0] and TTT2[1] and TTT1[2]]:

```problem is neither of them work properly, i switched to the first to make things easier to debug but to no avail, just frusteration.

You *cannot* test multiple items like this. You must test each item for equality separately:

```

if Players_Choice == TTT1[0] and Players_Choice == TTT1[1] and Players_Choice == TTT1[2]:

```

Your existing code will test whether all of these three values are true, and then check whether Players_Choice is in [True] or [False], which is never correct.

> on to my second issue, i am trying to make the input only = to int 1 - 9: 
i have tried so many different pieces of code its driving me bonkers. i even tried one involving the len() method, but that was only for strings i found out lol. dont get me wrong i can do it with a simple else statement, but i wanted something fancier lol. i feel like im always using if and else statements, ugh. lol its frusterating lol. so then i tried something liek these before adding that else in:

```

ex 1
for i in range(1, 10):
 while choose in range(i):
 return choose 
 break

ex2
if choose in '1, 2, 3, 4, 5, 6, 7, 8, 9' .split()
but of course the boolean value would return false when you tried to compare the two because youre comparing a list int to an int, not the same thing.:
also i tried 
while choose >= 1 and choose <= 9:
that didnt work either. 

```

Wouldn't it make more sense to convert it to an integer, and then test its range?

[php]
try:
    choose = int(choose)
except ValueError:
    # User entered something other than an integer
    print "You must enter an integer."

# ...

if choose < 1 or choose > 9:
    # User entered something out of range.
    print "You must enter a number between 1 and 9."
[/php]

> also quesiton 3 which is kind of off to the side, but how does this work? maybe i just dont understand. 

```

def Start():
 global Players_Choice
 Players_Choice = ''
 print 'please either choose X or O team'
 nothing = str(raw_input(''))
 if nothing not in 'X O'.split():
  Start()
 else:
  Players_Choice = nothing
  RANDOMSTART()

```what i want to know is that line where it makes nothing into a string, and it is comparing it to see if that string is in a list. so from what im concluding a string is found in a list, a list is a colleciton of strings, integer or otherwise correct? because the statement i tried above when comparing if choose in made those int into a list value, im assuming it will alwyas return false because the int even though it is in the list isnt considered an int, but a string.... am i right? im not sure thats why i want to ask.

A list is a collection of objects, which might be integers, strings, or anything else. They do not all have to be of the same type, though they usually are. The above code should work.

```

>>> 1 in [1, 2, 3]
True
>>> 4 in [1, 2, 3]
False
>>> "hi" in [1, 2, 3]
False
>>> "hi in ["hi", "goodbye"]
True
>>> "hi" in [1, "hi", 22.5]
True

```

> also im still using 2.64 so im not sure if maybe that has sometihng to do with some of this working or not. i know it 
did in the last one, when snova helped me and told me i could make this dict value:

words = {
'dict1': 'something in here'.split()
'dict2': 'something in here'.split()
}

i found out in 2.64 this code doesnt work but with one keyword, value list at a time. so if you were to do that you would have to say :

words = {
'dict1': 'somethign goes here'.split()
}

because i can only do 1 keyword, value pair. now his code was great and it works, but not in 2.64. has anyone has any issues like this with 2.64? also i havent checked but if anyone knows off hand maybe if there is an upgrade to 2.64, maybe liek 2.7 or something lol.

I'm confused. There's nothing directly wrong with any of the above code (except a missing comma after the first split()).

---

### Post by lavinog on 2010-03-24
> **XXMy_Little_ShinigamiXX said:**
> also quesiton 3 which is kind of off to the side, but how does this work? maybe i just dont understand. 

```

def Start():
 global Players_Choice
 Players_Choice = ''
 print 'please either choose X or O team'
 nothing = str(raw_input(''))
 if nothing not in 'X O'.split():
  Start()
 else:
  Players_Choice = nothing
  RANDOMSTART()

```what i want to know is that line where it makes nothing into a string, and it is comparing it to see if that string is in a list. so from what im concluding a string is found in a list, a list is a colleciton of strings, integer or otherwise correct? because the statement i tried above when comparing if choose in made those int into a list value, im assuming it will alwyas return false because the int even though it is in the list isnt considered an int, but a string.... am i right? im not sure thats why i want to ask. also im still using 2.64 so im not sure if maybe that has sometihng to do with some of this working or not. i know it 


```

 if nothing not in 'X O'.split():

```
first nothing should be converted to upper to ensure the case matches, and you should also only use the first character (incase the user inputs multiple chars)
Since you are only wanting one character, you can just supply a string for the allowed characters:
```

if nothing[0].upper() not in 'XO'

```

you can always test these things in a python shell
```

>>> 'O' in 'XO'
True
>>> 'y' in 'XO'
False
>>> 

```

also I don't think your python version is an issue.

---

### Post by lavinog on 2010-03-24
To expand on what I mentioned earlier about the nested list and functions:
You could write 3 functions to break up each test for win:

[php]
def all_same(list_of_three):
 for c in 'XO':
  if list_of_three.count(c)==3:
   return c

def check_rows(ttt_board):
 for row in ttt_board:
  winner=all_same(row)
  if winner:
   return winner

def check_cols(ttt_board):
 for colnum in range(3):
  col=[]
  for rownum in range(3):
   col.append(ttt_board[rownum][colnum])
  
  winner=all_same(col)
  if winner:
   return winner

def check_diags(ttt_board):
 diag1=[]
 diag2=[]
  for i in range(3):
   diag1.append(ttt_board[i][i])
   diag2.append(ttt_board[i][-i])
  
  winner=all_same(diag1)
  if winner:
   return winner

  winner=all_same(diag2)
  if winner:
   return winner

def checkwin(ttt_board):
 w=check_rows(ttt_board):
 if w: return w

 w=check_cols(ttt_board):
 if w: return w

 w=check_diags(ttt_board):
 if w: return w
[/php]

---

### Post by schauerlich on 2010-03-24
Your code makes me sad.

---

### Post by XXMy_Little_ShinigamiXX on 2010-03-24
> **schauerlich said:**
> Your code makes me sad.

dude give me a friggin break ive only been doing this for a couple of months, its not like im some kind of prodigy chill.

---

### Post by wmcbrine on 2010-03-24
A minor point, but: "global" isn't really used the way you use it here. There's no reason to ever have a "global" statement at the top level, outside of a function (although it's harmless, I guess).

---

### Post by XXMy_Little_ShinigamiXX on 2010-03-24
> **snova said:**
> I'm confused. There's nothing directly wrong with any of the above code (except a missing comma after the first split()).

no your code is right but its not working with my version number. i looked at the code in the tutorial and it was doing the exact same thing you suggested, but they reccomend using ver 3, or else they said some of the code wont work.  so youre code works great, just not in my ver that i have is all.

---

### Post by lavinog on 2010-03-24
> **wmcbrine said:**
> A minor point, but: "global" isn't really used the way you use it here. There's no reason to ever have a "global" statement at the top level, outside of a function (although it's harmless, I guess).

You should also avoid using globals anyway...they lead to bad code.

---

### Post by XXMy_Little_ShinigamiXX on 2010-03-24
> **wmcbrine said:**
> A minor point, but: "global" isn't really used the way you use it here. There's no reason to ever have a "global" statement at the top level, outside of a function (although it's harmless, I guess).
oh, so basically i only need my global statements inside functions then? if thast the case do i still define them outside of functions and add the global statement inside the function? or do i do both inside the function?

---

### Post by lavinog on 2010-03-24
> **XXMy_Little_ShinigamiXX said:**
> no your code is right but its not working with my version number. i looked at the code in the tutorial and it was doing the exact same thing you suggested, but they reccomend using ver 3, or else they said some of the code wont work.  so youre code works great, just not in my ver that i have is all.

```

words = {
'dict1': 'something in here'.split(),
'dict2': 'something in here'.split()
}

```
This works in 2.6.4
you need the comma to separate the items

---

### Post by XXMy_Little_ShinigamiXX on 2010-03-24
> **lavinog said:**
> ```

words = {
'dict1': 'something in here'.split(),
'dict2': 'something in here'.split()
}

```This works in 2.6.4
you need the comma to separate the items
  
OHHH.. i bet i forgot the comma geez lol.. sorry
yeh i didnt even think of putting a comma down lol. sorry

---

