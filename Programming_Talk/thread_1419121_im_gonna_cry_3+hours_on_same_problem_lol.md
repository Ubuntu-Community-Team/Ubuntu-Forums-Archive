---
title: "im gonna cry 3+hours on same problem lol"
date: 2010-03-01
forum: Programming Talk
---

### Post by XXMy_Little_ShinigamiXX on 2010-03-01
so after i finished my password module i decided to take it for a test. so i added import password to my main module and drew up some lines, let me post;
```

inputs = str(raw_input(''))
while True:
 try:
  if inputs == 'option1':
   print 'option1 printed success'
  elif inputs == 'option2':
   print 'option2 print success'
  elif inputs == 'helpme':
   import helpme
   print helpme

```its basically a program that gives you a menu and you are to choose from the options with the raw_input function by typing in one of the following commands;
option1, option2, or helpme
extremely simple right?
ok.. i get no errors whatsoever until i atempt to lay down the while True: card, after i input that and try and run my program it says expected an indented block or an unexpected, either or. but it will give me no clue as to what the object is whatsoever, it will be something blank like this,

unexpected indent                       ^ 
or unexpected indent                                            ^
no files no nothing. 
just blank spaces, and i have been looking through my code for hours ready to rip my hair out and jump off the nearest platform i see lol. 
i have even went through and said;

with open('/python26/file.py', 'r') as d:
 d.readline(57) or 43 or whatever it is, and its always an object not an empty space.

that didnt help me, ive went through it LINE BY LINE and its always the same line that gets me into trouble, the while True: statement. i have been at this for hours upon hours and am tired as i have been up all night designing some submodules, etc.. so maybe im just not thinking straight. idk.. 

the exact code is this and before you say anythign corny its for my gf the love of my life lol. 

```

#import password #the password changed to a comment because i got tired of entering it lol
import helpme
import random
import sys
print """PRINCESS!!!!! **HUGS** hello beautiful :D 
if youve started using this great cause youre awesome like that!! :D
this is just here to remind you cupcake that all you need to do is 
type helpme for an avaliable list of commands you can do! :D
"""   ## this is another menu string

helpme = """
PRINCESS!!!! **HUGS**\n
this is a list of commands you can use anytime you want :D\n
type in poem to display the two castles, esspecially for princess jenjen :D\n
type in beautiful to hear all the reasons why i think youre beautiful :D \n
type in genius to hear all the reasons i know youre SUPER SMART!! :D\n
type in adorable to hear all the reasons i thinks youre SOO adorable :D\n
type in never to hear all the reasons why youre never alone :D\n
<3333333333333333333333333333333333333333333333333333333333333333333333\n
"""  # this is a giant string to print out at the menu

#this is where the value for inputs is defined
inputs = str(raw_input(''))
while True:
  try:
  inputs = str(raw_input(''))
  if inputs == 'beautiful':
   print 'you are beautiful'
  elif inputs == 'genius':
   print 'JEN IS SO SMART'
  elif inputs == 'helpme':
   from forjen import helpme
   print helpme
  elif inputs == 'adorable':
   print 'jen is adorable'
  elif inputs == 'never':
   print 'jen is so beautiful shes sure to never be alone'
  elif input == 'quit':
   sys.quit()


#the while true statement says that while input is being waited on
#it has a list of options you can choose to input for the value (inputs)

```of course the sentences etc.. i just threw in there for now, just to fill the blanks, the reason it was supposed to import random is because i am going to make it repeat the value of raw_input until 'quit' is typed. during that time in which im going to make a giant list of sentences like 'a likes b', 'a is doing something' and take and convert them to a string format. that way they are built into the module and i dont have to import, plus by doing that i can do random.choice(a) for example and even though its a string it will return a value of only one sentence inside that string, that is one value at a time in these '' anyway can someone please help me, is it an error listing? like maybe it is assuming somehting is missing a space but isnt? i see no flaws in my code that would cause an expected or unexpected indent. please help. :popcorn:

EDIT______________________________________
before i forget it was working to an extent at one point but i think thats when the elif statements were except, but i doubt it.  the only real thing that i could have think what caused this is i downloaded py2exe and converted the original .py file that had this data to an exe.
i read somewhere sometimes python changes little bits of data? like it shouldnt be that big a deal in things like this but obviously in jpegs and stuff yeh its a hug deal. could that be it?

well i just created a brand new txt file from scratch..still has the blank line problem. :( whats going on this is really aggravating me.

---

### Post by CptPicard on 2010-03-01
Why do you have a **try** without a corresponding **except**?

Why are you not indenting after the try?

Why is your indentation inconsistent, either two spaces or one?

---

