---
title: "[Python] - Dealing with Files"
date: 2008-04-08
forum: Programming Talk
---

### Post by swatto on 2008-04-08
Hi all :)

Im currently reading Core Python Programming 2nd Ed.  Im on an exercise that requires me to open an existing text file within my python program for editing and then giving the option to save changes to the file or discard them.

Just wondering how I would go about doing this as I have tried google and various python tutorials but getting nowhere.

Cheers.

---

### Post by themusicwave on 2008-04-08
You need the File object.

Take a look at this documentation:
[http://docs.python.org/lib/bltin-file-objects.html]("http://docs.python.org/lib/bltin-file-objects.html")

it is fairly easy to read a file you just use:

file_ = open("pathtofile","r")
fileText = file_.read()
print fileText

---

### Post by ghostdog74 on 2008-04-08
you can open a file like this
```

for lines in open("file"):
  print lines

```
or like this is not too big
```

data=open("file").read()

```

---

### Post by swatto on 2008-04-08
Thanks for the replies - I know how to open a file and read it - but how do I open the file so that the text is displayed within the python program and the text that is displayed can be edited on-the-fly (or I may be making it too complicated for what the exercise is actually asking me to do ??).  I think the methods you have shown me read the file first and then print the output of the file within the python program.

---

### Post by themusicwave on 2008-04-08
What I would probably do is the following.

1) Read in the file and store it's contents(assuming it isn't enormous this shouldn't be an issue)
2)Close the file
3)Put the contents of the File into the GUI Widget like a TK Text widget.
4) Let the user do their thing.  As they make changes alter the text variable.
5) Have a save button/menu that writes the file back to the disk when they push it.

I think that would work fairly well and be a decent way of doing it.  As for specifics, it depends which GUI toolkit you are using.  If it's TK then take a look here:

[http://www.effbot.org/tkinterbook/]("http://www.effbot.org/tkinterbook/")

Specifically, look at the Text widget and scrollbar widget.  You would need to use them together to accomplish this task.

Hope that helps,

Jon

---

### Post by swatto on 2008-04-08
> **themusicwave said:**
> What I would probably do is the following.

1) Read in the file and store it's contents(assuming it isn't enormous this shouldn't be an issue)
2)Close the file
3)Put the contents of the File into the GUI Widget like a TK Text widget.
4) Let the user do their thing.  As they make changes alter the text variable.
5) Have a save button/menu that writes the file back to the disk when they push it.

I think that would work fairly well and be a decent way of doing it.  As for specifics, it depends which GUI toolkit you are using.  If it's TK then take a look here:

[http://www.effbot.org/tkinterbook/]("http://www.effbot.org/tkinterbook/")

Specifically, look at the Text widget and scrollbar widget.  You would need to use them together to accomplish this task.

Hope that helps,

Jon

Thanks - I don't know whether this is too advanced for me yet but ill have a go.  Just reading the text it does say that this exercise is alot more difficult and may require you use a GUI toolkit. :)

---

### Post by themusicwave on 2008-04-08
The only GUI Toolkit I have experience with for Python is Tkinter.  It was fairly simple to learn an that website I posted a link too was pretty helpful.

I also found this useful for learning TKinter and python [http://www.pythonware.com/library/tkinter/introduction/]("http://www.pythonware.com/library/tkinter/introduction/")

I think if you work at it a bit and read up on Tkinter you can definately handle the task.

If you get stuck just ask me or someone else for help.

---

### Post by swatto on 2008-04-09
Ive started work on seeing how far I get with this problem - here is where I am at the moment - im very new to python and programming in general and im stuck.  

```
#!/usr/bin/python

'Modify an Existing File(s) Contents'

from Tkinter import *

while True:
    fname = raw_input('Enter the filename you wish to modify: ')
    print

#attempt to open file for reading
    try: fobj = open(fname, 'r')
    except IOError, e:
         print "File Open Error:", e
         print
    else:
         break

#stores file contents in variable and closes the file object
data = fobj.read()
fobj.close()

#display contents to the screen
root = Tk()

textbox = Text(root)

textbox.insert(END, data)
textbox.pack()

root.mainloop()

```

I believe I now need to mess with the text widget to add scrollbars and two command buttons for the next part of the program and was wondering if somebody could help me get started as Im having trouble understanding the docs provided.

Thanks for any help :)

---

### Post by swatto on 2008-04-09
Ive managed to display the text widget with the file contents and create a quit button but this is as far as I can get as I get a bad file descriptor error when I call the function for the save changes.

[PHP]#!/usr/bin/python

'Modify an Existing File(s) Contents'

from Tkinter import *
import os

while True:
    fname = raw_input('Enter the filename you wish to modify: ')
    print

#attempt to open file for reading
    try: fobj = open(fname, 'r')
    except IOError, e:
         print "File Open Error:", e
         print
    else:
         break

#stores file contents in variable
data = fobj.read()

#function for saving changes to the file
def save(file):
    contents = textbox.get(1.0, END)
    fobj.write(contents)
    fobj.close()

#display contents to the screen
root = Tk()

textbox = Text(root)

textbox.insert(END, data)
quit = Button(root, text="QUIT", command=root.quit)
save_file = Button(root, text="SAVE CHANGES", command=save(fobj))
textbox.pack()
quit.pack()

root.mainloop()[/PHP]

---

### Post by themusicwave on 2008-04-09
I'll take a look.

In the future you could help us help you by using the php tags to arround your code.  That makes it easier to read and preserves the indents.  In Python the indents are rather important.

---

### Post by themusicwave on 2008-04-09
I modified your program a bit to get it working.  You were actually really close!  Check out my changes below.

[PHP]
from Tkinter import *
import os

#Reads in the input file name, makes sure it is valid
def getInputFileName():
    #Don't need a while loop, raw_input waits for input, use a loop to check for a good file name
    fname= ""
    while not os.path.exists(fname):
        fname = raw_input('Enter the filename you wish to modify: ')
        
    return fname

#reads in the save file name
def getSaveFileName():
    fname= ""
    while fname == "":
        fname = raw_input('Enter the filename you wish to save: ')
        
    return fname

#function for saving changes to the file
def save():
    
    fname = getSaveFileName()
    
    try:
        fobj = open(fname,"w")
        contents = textbox.get(1.0, END)
        fobj.write(contents)
        fobj.close()
    except IOError, e:
        print "File Open Error:", e
    

#attempt to open file for reading
try: 
    fobj = open(getInputFileName(), 'r')
except IOError, e:
    print "File Open Error:", e



#stores file contents in variable
data = fobj.read()
print data

#display contents to the screen
root = Tk()

textbox = Text(root)

textbox.insert(END, data)
quit = Button(root, text="QUIT", command=root.quit)
save_file = Button(root, text="SAVE CHANGES", command=save)
textbox.pack()
quit.pack(side=RIGHT)
save_file.pack(side=LEFT)

root.mainloop()
[/PHP]

Now for your next challenge, make an Entry widget to put the file name in and an open button to open the file path in the widget.

Also, add an Entry widget to enter the save path as well.

You're making a GUI app, so don't expect the user to look at the command line for prompts.

It was a pretty good start, I think you are getting the hang of it.

---

### Post by swatto on 2008-04-09
Got an update - I can't figure what is going wrong.  The save button doesn't work and the quit button replicates the file contents and writes the replication back to the file before quitting??

[PHP]#!/usr/bin/python

'Modify an Existing File(s) Contents'

from Tkinter import *
import os

while True:
    fname = raw_input('Enter the filename you wish to modify: ')
    print

#attempt to open file for reading
    try: fobj = open(fname, 'r+')
    except IOError, e:
         print "File Open Error:", e
         print
    else:
         break

#stores file contents in variable
data = fobj.read()


#function for saving changes to the file
def save(file,textbox):
    contents = textbox.get(1.0, END)
    fobj.write(contents)
    fobj.close


#display contents to the screen
root = Tk()

textbox = Text(root)

textbox.insert(END, data)
quit = Button(root, text="QUIT", command=root.quit)
save_file = Button(root, text="SAVE CHANGES", command=save(fobj, textbox))
textbox.pack()
quit.pack()
save_file.pack()

root.mainloop()[/PHP]

Ahh just read your reply - seems I posted near enough the same time as you - thankyou for doing that for me ill have a look and see if i can understand what you have modified.

---

### Post by swatto on 2008-04-10
Just looking through your code and I understand all of it - thankyou, I notice that it is alot cleaner than mine because of the functions so I am going to attempt to get used to using functions when writing code.  

I will have a go at the entry widgets challenge you have set me when I get back from work :).

One thing I noticed in the code - when the contents of the file is stored in the variable the program then prints the variable - why is that?

Cheers,

---

### Post by themusicwave on 2008-04-10
Functions do make things a lot neater and cleaner.  They also help because they compartmentalize things.  For example if the file isn't saving right you can reasonably assume the problem is in the save function.

As for the printing of the data, I left that in the code because you had it there.  You can remove it without any problems.

One more suggestion for you is to put all your functions at the top of your code and the main execution at the bottom.  Don't mix functions with main execution.

I think you can handle the entry widget, it isn't too difficult and like I said you were pretty close to getting it before.

Keep at it an you'll get it.  Let me know if you get stuck.

---

### Post by swatto on 2008-04-11
Just had a quick look last night to see if I could work out the first part of the challenge (to create a open entry widget instead of using terminal)

Analyzing the problem I think I have to:

[LIST=1]
[*]Make the program start up the GUI straight away - with a dialog box asking the user to enter a filename to open?
[*]Modify the getInputFileName() function to get the input from the entry widget instead
[*]Give the entry widget a command button that opens the text widget to display the file contents that were specified in the entry widget
[/LIST]

Hmm not quite sure though :confused:

---

### Post by themusicwave on 2008-04-11
That could work I think.

Here is what I would do to accomplish the task.

1) Like you said the program starts off with the GUI and loads it right away.  The Text widget is blank, with nothing in it at all.

2) The user types the file they want to open in an Entry widget at the top of the screen and presses an Open button.  

3) The open button checks that the file exists.  If it does it sends the file name to a function to read the contents of the file into a variable.  It then displays this variables contents in the Text widget.

You could have save work in a very similar way.

To modify the getInputFile function, I would probably rename it to openFile or something more descriptive like that.  Make it so that when open is pushed it calls that function.  It should then look at the Entry widget to get the path to the file.  Then open that path and put it's contents in the Text widget.

Let me know how it goes as always ask if you get stuck.

---

### Post by swatto on 2008-04-11
> **themusicwave said:**
> That could work I think.

Here is what I would do to accomplish the task.

1) Like you said the program starts off with the GUI and loads it right away.  The Text widget is blank, with nothing in it at all.

2) The user types the file they want to open in an Entry widget at the top of the screen and presses an Open button.  

3) The open button checks that the file exists.  If it does it sends the file name to a function to read the contents of the file into a variable.  It then displays this variables contents in the Text widget.

You could have save work in a very similar way.

To modify the getInputFile function, I would probably rename it to openFile or something more descriptive like that.  Make it so that when open is pushed it calls that function.  It should then look at the Entry widget to get the path to the file.  Then open that path and put it's contents in the Text widget.

Let me know how it goes as always ask if you get stuck.

They were similar to the steps I had in mind so good to know Im thinking logically :) - thankyou for your extended help on this I really appreciate it.  Im going to have to read up alot more on Tkinter though I think as I am having trouble finding out how to display a window when a button is clicked and also how to structure the GUI code so that the appearance of the program is how I want it.

---

### Post by themusicwave on 2008-04-11
> **swatto said:**
> They were similar to the steps I had in mind so good to know Im thinking logically :) - thankyou for your extended help on this I really appreciate it.  Im going to have to read up alot more on Tkinter though I think as I am having trouble finding out how to display a window when a button is clicked and also how to structure the GUI code so that the appearance of the program is how I want it.

Reading up is always a good idea.

As for makign the GUI look the way you want, I suggest looking into the Grid Manager.

Instead of using Item.pack() you use item.grid(row=,column=)

This way you end up with GUIs that are layout as a table, this can make things much easier. Check this out:
[http://www.effbot.org/tkinterbook/grid.htm]("http://www.effbot.org/tkinterbook/grid.htm")

I don't mind helping out, so ask away.

---

### Post by swatto on 2008-04-16
The thread about function scope was kinda related to this themusicwave :)

Im still trying to figure out how to modify the function so that it can access the GUI elements outside of the function in order to put the file contents in the text widget.  I was reading a little about lambda but not sure if thats what I need :confused:

---

### Post by themusicwave on 2008-04-16
That's what I figured in the other thread.

Well for this application there are 2 ways to do achieve this, one is easier than the other.  The easy one is also typically considered bad programming.

1) Use Global Variables for the widgets and/or their contents to do this you need the Global keyword.

Example:

[PHP]
text = "Hello I am some global text"

#Set the value of global text to the value of newText
def setText(newText):
    
    #tell python you want text to refer to the global var, not a local
    global text

    text = newText

print "Text Before Call:", text

setText("Set text changed my text!")
print "Text after call:", text
[/PHP]


Like I said this way is easy, but it also is considered weaker programming style and a bad habit in general.  

The other option would require you to learn a bit of Object Orient Programming or OOP.  This is where you define a Class with methods(functions) and attributes(variables) associated with it.  It works somewhat similar to the global variable except inside of the variables being available to the whole program they are only available to the functions of their own class.

Example:

[PHP]
#define a class
class TestClass:

    #Constructer this runs when a new object of this class is made
    def __init__(self):
        self.text = "Text from the constructor!"

    #When called this function sets the class attribuet text to the value of nexText
    def setText(self,newText):
        self.text = newText


#Main Execution
if __name__ == "__main__":

    #declare a new object of type TestClass, this calls the __init__ function
    tc = TestClass()

    #print tc's text attribute
    print tc.text

    #set tc's text attribute to something new

    tc.setText("I chnaged the text!")

    #print the new text attribute
    print tc.text
[/PHP]

This one is a bit more advanced of a topic, and it may be covered later in your book.

I would recommend trying it with approach 1 first using the global variable.  That way you only need to learn the TKinter concepts themselves.  Then we can turn it into a class pretty easily.  Trying to tackle TKinter and OOP all at once might be a bit too much.

Give it a shot using the globals, let me know how it goes.

---

