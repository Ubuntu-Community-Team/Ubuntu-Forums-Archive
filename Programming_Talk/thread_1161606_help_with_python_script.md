---
title: "help with python script"
date: 2009-05-16
forum: Programming Talk
---

### Post by The-ITu on 2009-05-16
here is the code:

[php]import os from Tkinter import *  def cls():     os.system(['clear', 'cls'][os.name=='nt'])  print 'This is a Tk button creater!' raw_input("press enter to continue") cls()  amountOfButtons = input("how many buttons do you want?  (max 10) >>> ") amountOfButtons = amountOfButtons + 1 tkTitle = raw_input('what would you like the title of the canvas to be? >>> ')  while amountOfButtons > 10:     print "that is an in correct value."     amountOfButtons = input("how many buttons do you want?  (max 10) >>> ")  command1, command2, command3, command4, command5, command6, command7, command8, command9, command10 = ' ', ' ', ' ', ' ', ' ', ' ', ' ', ' ', ' ', ' ' listOfComands = [command1, command2, command3, command4, command5, command6, command7, command8, command9, command10] text1, text2, text3, text4, text5, text6, text7, buton8, text9, text10 = ' ', ' ', ' ', ' ', ' ', ' ', ' ', ' ', ' ', ' ' listOfButtonComands = [text1, text2, text3, text4, text5, text6, text7, buton8, text9, text10]  for x in range (1, amountOfButtons):     rv = str(x)     listOfComands[x] = raw_input("what do you want button %s to to have writen on it? >>> " % rv)   for i in range (1, amountOfButtons):     rvi = str(i)     listOfButtonComands[i] = raw_input("what do you want button %s to return >>> " % rvi)   def pnt(num):     print listOfButtonComands[num]  canvasHeight = input("how high do you want your canvas? >>> ") canvasWidth = input("how wide do you want your canvas? >>> ")  cls()  raw_input("press enter to create!!")  cls()  root = Tk() root.title(tkTitle) canvas = Canvas(root, height=canvasHeight, width=canvasWidth) canvas.pack()  for g in range (1, amountOfButtons):     btn = Button(root, text = listOfButtonComands[g], command = pnt(g))     btn.pack()  raw_input()[/php]now the problem is in line 17 and 18 where im trying to make a list of empty variables but it tell me that they are not defined. how can i get past this?is

---

### Post by Xarver on 2009-05-17
Well, you could assign the variables before you use them.
It would look ugly, but you could assign all variables to the value None.
E.x. command1, command2, ... = None

---

### Post by Martin Witte on 2009-05-17
To create the desired commands list you can do this as well:
```
listOfCommands = []    
for x in range (0, amountOfButtons):
    listOfCommands.append(raw_input("what do you want button %s to to have writen on it? >>> " % x) )
# for debugging print content of listOfCommands
print listOfCommands

```
In this way you don't limit yourself to a maximum number of elements in the list, as the append method appends items to the list. Also note the correction in the way you make the prompt for raw_input.

About the Tkinter part of your code: you need to create a root widget, to which you add child windows, e.g.
```
root = Tk()

canvas = Canvas(root, height=canvasHeight, width=canvasWidth)
canvas.pack()

for g in range (0, amountOfButtons):
    btn = Button(root, text = listOfCommands[g], command = pnt(g))
    btn.pack()

```

see e.g [this link]("http://www.pythonware.com/library/tkinter/introduction/index.htm") for a Tkinter tutorial

---

### Post by The-ITu on 2009-05-17
> **Martin Witte said:**
> To create the desired commands list you can do this as well:
```
listOfCommands = []    
for x in range (0, amountOfButtons):
    listOfCommands.append(raw_input(&quot;what do you want button %s to to have writen on it? >>> &quot; % x) )
# for debugging print content of listOfCommands
print listOfCommands

```In this way you don't limit yourself to a maximum number of elements in the list, as the append method appends items to the list. Also note the correction in the way you make the prompt for raw_input.

About the Tkinter part of your code: you need to create a root widget, to which you add child windows, e.g.
```
root = Tk()

canvas = Canvas(root, height=canvasHeight, width=canvasWidth)
canvas.pack()

for g in range (0, amountOfButtons):
    btn = Button(root, text = listOfCommands[g], command = pnt(g))
    btn.pack()

```see e.g [this link]("http://www.pythonware.com/library/tkinter/introduction/index.htm") for a Tkinter tutorial

sorry for my late reply. i have updated this to the point where i dont get an error but it does not do what it is told to do. i have updated it on my original post.

---

