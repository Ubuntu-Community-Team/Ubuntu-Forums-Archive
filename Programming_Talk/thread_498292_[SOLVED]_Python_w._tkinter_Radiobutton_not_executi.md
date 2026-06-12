---
title: "[SOLVED] Python w. tkinter: Radiobutton not executing command when pressed?"
date: 2007-07-11
forum: Programming Talk
---

### Post by tjansson on 2007-07-11
I am writing a program in Python using tkinter and I have created a new radiobutton class called NewRadiobutton. But for some reason I can't make the buttons execute a command when pressing them down. 

Here is the class
```

		class NewRadioButton:
			## Creating the class for checkbuttons
			def enable(self):
				self.on.configure( state='normal', selectcolor="green")
				self.off.configure(state='normal', selectcolor="red")
				self.on.update_idletasks()
				self.off.update_idletasks()
				print "Trykkede enable"
				
			def disable(self):
				self.on.configure( state='disabled', selectcolor="grey")
				self.off.configure(state='disabled', selectcolor="grey")
				self.on.update_idletasks()
				self.off.update_idletasks()
				print "Trykke disable"

			def draw(self, Irow):
				self.label.grid( row=Irow, column=0, sticky=W)
				self.on.grid(    row=Irow, column=1, sticky=W)
				self.off.grid(   row=Irow, column=2, sticky=W)
				self.help.grid(  row=Irow, column=3, sticky=E)

			def __init__(self, Ilabel, Iselected, IcommandYES, IcommandNO, Idescrip):
				self.varname    = Ilabel
				self.state      = StringVar()
				self.descrip    = Idescrip
				
				#Creating Label and the help information
				if IcommandYES == "nocommand":
					self.on  = Radiobutton(frame, text="Yes", value="t", selectcolor="green", indicatoron=0, variable=self.state, state="normal" )
					self.off = Radiobutton(frame, text="No",  value="f", selectcolor="red"  , indicatoron=0, variable=self.state, state="normal" )
				else:
					self.on  = Radiobutton(frame, text="Yes", value="t", selectcolor="green", indicatoron=0, variable=self.state, command=IcommandYES, state="normal")
					self.off = Radiobutton(frame, text="No",  value="f", selectcolor="red"  , indicatoron=0, variable=self.state, command=IcommandNO, state="normal" )

				self.label = Label(frame, text=Ilabel)
				self.help = Label(frame, text=Idescrip)
				
				#Toggles if the button should be pressed down or not upon creation
				if Iselected == "select":
					self.on.select()
					self.selected  = "t"
				else:
					self.off.select()
					self.selected = "f"

```

When I create new buttons using the class it looks like this:
```

		self.LPOT   = NewRadioButton("Should spherical harmonic expansion be used?", 				"select",   "self.LFORM.enable'", "self.LFORM.disable", "")

```
However when pressing these buttons nothing happen?

If I make a testbutton there is no problems:
```

		self.button1 = Button(frame, text="Enable", command=self.LFORM.enable)
		self.button1.grid(row=maxrow+14, column=3, sticky=W)
		self.button2 = Button(frame, text="Disable", command=self.LFORM.disable)
		self.button2.grid(row=maxrow+15, column=3, sticky=W)

```

So my question is:
**Why doesn't my NewRadioButtons executes the command I feed them with?**

---

### Post by tjansson on 2007-07-11
The strange thing is that if exchange the command to "exit" it works and the program exit. So why can't execute the command I am feeding it. It doesn't work either when writing command="print 'Button pressed'" - why is that ?

---

### Post by LaRoza on 2007-07-11
> **tjansson said:**
> The strange thing is that if exchange the command to "exit" it works and the program exit. So why can't execute the command I am feeding it. It doesn't work either when writing command="print 'Button pressed'" - why is that ?

I use Python, and just recently used Tkinter. I experienced a similar problem.

Here is what I determined to be the problem.

The command associated with the widget, a button, was executed as soon as the function was called, not when it was pressed.

I fixed it by making the creation of the GUI outside a function.

I do not know what this works, but here is the code for it:

```

###########################################################
#PyTree1.1, WILL HAVE A GUI.
#GUI WRITTEN,WORK ON STYLE, AND BINDING IT TO getPath
###########################################################
#14 JUNE 2007 
###MADE BUTTON FUNCTIONAL
####NEED TO FUSE GUI WITH CLI VERSION
#15 JUNE 2007
###CHANGED MIND ABOUT GUI, INSTEAD OF DRAWING OBJECTS, MAKE AN XML FILE, EASIER TO USE AND EASIER TO SAVE
#05 JULY 2007
###MADE CLI VERSION, NOW RESUME WORK ON GUI VERSION
#10 JULY 2007
###MADE GUI VERSION, NOW ADDING ERROR CHECKING AND FILE CHECKING
import Tkinter
import os
############################################################
#CREATES THE FILE WITH ITS HEADING AND STYLE AND DTD

def createFile(thePath,saveAs):
    heading ="<?xml version=\"1.0\"?>\n<?xml-stylesheet type=\"text/css\" href=\"FileML/FileML.css\"?>\n<!DOCTYPE tree SYSTEM \"FileML/FileML.dtd\">\n\n<tree>\n\n<filePath>\n" + thePath + "\n</filePath>\n\n"
    saveAs += ".xml"
    saved = open(saveAs,'a')
    saved.write(heading)
    saved.close()
    drawTree(thePath,saveAs)

#DRAWS THE TREE
def drawTree(pathIs,saveIs):
    tree = os.walk(pathIs)
    saved = open(saveIs,'a')
    for directory in tree:
        printDirectoryC(directory,saveIs)
    saved.write("\n</tree>")
#PRINT CONTENTS
def printDirectoryC(direct,save):
    saved = open(save,'a')
    saved.write("<directory>\n<directoryName>")
    saved.write(direct[0])
    saved.write("</directoryName>")
    for file in direct[2]:
       saved.write("<fileName>" + file + "</fileName>")
    saved.write("</directory>\n\n")
#PREVENTS INVALID XML
def eraseFile(fileToErase):
    fileToErase += ".xml"
    open(fileToErase,'w')
#GET USER INPUT, THIS IS THE FIRST FUNCTION
def getPath():
    #path = raw_input("What is the path: ")
    #save = raw_input("Save As: ")
    pathed = path.get()
    saved = save.get()
    if os.path.isdir(pathed) == 1 and os.path.isfile(saved + ".xml") == 0:
            eraseFile(saved)
            createFile(pathed,saved)
    else:
        print "No such path or file exists"

#######################################################################
root = Tkinter.Tk()
root.title("PyTree1.1")

path = Tkinter.Entry(root,width=50)
path.pack(side=Tkinter.TOP)

save = Tkinter.Entry(root,width=20)
save.pack(side=Tkinter.LEFT)

action = Tkinter.Button(root,width=20,text="Tree",command=getPath)
action.pack(side=Tkinter.RIGHT)

close = Tkinter.Button(root,width=10,text="Close",command=root.quit)
close.pack(side=Tkinter.BOTTOM)

root.mainloop()

```

Note: the variables associated with the widgets are global.

---

### Post by tjansson on 2007-07-11
Thanks for the answer I think that is related as well but somewhat different.

I found out I could make use exec() or eval() to evaluate the sting with the command which is "self.LPOT.disable", but now I ran in to some serious scope problems. When I try to execute the command "self.LPOT.disable" from within the class NewRadioButton it off course fails since there is no NewRadioButton.LPOT obejct. So I need it to execute "self.LPOT.disable" as if it was outside the class but right now I am rather confused.

---

### Post by cwaldbieser on 2007-07-14
> **tjansson said:**
> 
When I create new buttons using the class it looks like this:
```

		self.LPOT   = NewRadioButton("Should spherical harmonic expansion be used?", 				"select",   "self.LFORM.enable'", "self.LFORM.disable", "")

```
However when pressing these buttons nothing happen?


You are passing in strings instead of callback functions.  Just pass in the functions:
```

self.LPOT = NewRadioButton("Should spherical harmonic expansion be used?", "select", self.LFORM.enable, self.LFORM.disable, "")

```

---

### Post by tjansson on 2007-07-20
Thanks  alot - that was so simple and yet solved my problems! :D

---

