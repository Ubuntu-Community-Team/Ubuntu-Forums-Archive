---
title: "[SOLVED] Python with tkinter: change state of checkbutton after it is created?"
date: 2007-06-03
forum: Programming Talk
---

### Post by tjansson on 2007-06-03
I am making a program with tkinter. I created a checkbutton which is initially enabled but depending on the state some other buttons I would like to change the state of the checkbutton to disabled. 

In the PDF about tkinter I can only see 5 methods for checkbutton. The only thing I though might do what I would like to is invoke(state=disabled) but that doesn't work. 

Just to give an example of the code where I would like to disable the button. It just for testing when i figured out how to disabled the button that will happen in another loop. 

```

		##Creates a checkbutton from the elements of list with sublist.
		##Element 0 = Name of the button
		##Element 1 = State of the button. Pressed or not pressed.
		##Element 2 = Description of the option.
		self.button_list1 = [ \
		["LPOT",   "t", "TRUE IF SPHERICAL HARMONIC EXPANSION IS USED"], \
		["LNCOL",  "t", "TRUE IF COLLOCATION IS NOT USED"], \
		["LFORM",  "f", "TRUE IF FORMAT IS INPUT"], \
		]
		self.cbvalues1 = {}
		for row, name in enumerate(self.button_list1):
			v = self.cbvalues1[name[0]] = StringVar() ## It is a string variable so, t or f can be store here
			self.cb = Checkbutton(frame, onvalue="t", offvalue="f", variable=v, state=DISABLED)
			label = Label(frame, text=name[0])
			label.grid(row=2+row, column=0, sticky=W)
			help = Label(frame, text=name[2])
			help.grid(row=2+row, column=2, sticky=W)
			self.cb.grid(row=2+row, column=1, sticky=W)
			if name[1] == "t":	##Sets the button state upon starting the program
				self.cb.select()			##read from the list button_state
			else: 
				self.cb.deselect()
				#self.cb.invoke(STATE=DISABLED)

```

---

### Post by WW on 2007-06-03
Use **configure()** to change the state. Here's a little demo program:

**disable_cb_test.py**
```

# disable_cb_test.py

from Tkinter import *

class App:

    def __init__(self, master):

        frame = Frame(master)
        frame.pack()

        self.button = Button(frame, text="QUIT", command=frame.quit)
        self.button.pack(side=LEFT)

        self.en = Button(frame, text="Enable", command=self.enable_cb)
        self.en.pack(side=LEFT)

        self.dis = Button(frame, text="Disable", command=self.disable_cb)
        self.dis.pack(side=LEFT)

        self.cb = Checkbutton(frame,text="Check")
        self.cb.pack(side=LEFT)

    def enable_cb(self):
        self.cb.configure(state='normal')

    def disable_cb(self):
        self.cb.configure(state='disabled')


root = Tk()
app = App(root)
root.mainloop()

```

---

### Post by tjansson on 2007-06-04
I love theese forums it is better than IRC channels. Thank you so much!! :D

It was exactly what I was looking for. Strange that it the configure method wasn't mentioned in the tkinter dokumentation.

---

### Post by tjansson on 2007-06-10
I would like the state of some checkbuttons to change when I select or deselect another checkbutton. 

This is my checkbutton class

```

		class NewCheckButton:
			def __init__(self, Ilabel, Iselected, Istate, Icommand, Idescrip):
				"""The state can be 'active' and 'disabled'"""
				# Making the varibles accesable to the object 
				self.varname    = Ilabel
				if Iselected == "select":
					self.selected  = "t"
				else:
					self.selected = "f"
				#self.row  		= Irow
				self.state      = Istate
				self.descrip    = Idescrip 
				
				#Creating Label and the help information
				if Icommand == "nocommand":
					self.cbbutton = Checkbutton(frame, onvalue="t", offvalue="f", selectcolor="blue", state=Istate)
				else:
					self.cbbutton = Checkbutton(frame, onvalue="t", offvalue="f", selectcolor="blue", state=Istate, command=Icommand)
				self.label = Label(frame, text=Ilabel)
				self.help = Label(frame, text=Idescrip)
				
				#Toggles if the button should be pressed down or not upon creation
				if Iselected == "select":
					self.cbbutton.select()
				else: 
					self.cbbutton.deselect()
				
				#Test button
				self.button1 = Button(frame, text="Enable", command=self.enable)
				self.button2 = Button(frame, text="Disable", command=self.disable)
				#self.button1.grid(row=Irow, column=3, sticky=W)
				#self.button2.grid(row=Irow, column=4, sticky=W)
				
				#Drawing the different widgets in the grid
				
			def draw(self, Irow):
				self.label.grid(      row=Irow, column=0, sticky=W)
				self.cbbutton.grid(row=Irow, column=1, sticky=W)
				self.help.grid(       row=Irow, column=3, sticky=E)
				
			def enable(self):
				self.cbbutton.configure(state='normal')
				self.cbbutton.update_idletasks()
				
			def disable(self):
				self.cbbutton.configure(state='disabled')
				self.cbbutton.update_idletasks()


```

Then I try to call one of the checkbuttons with a command option which should disable the other checkbutton nothing happens when I select or deselct the  LPOT checkbutton.
```

		self.LPOT   = NewCheckButton("Should spherical harmonic expansion be used?"  , "select", "active", "self.LFORM.disable", "")
		self.LNCOL  = NewCheckButton("Should collocation be used?" , "select",  "active", "nocommand", "")
		self.LFORM  = NewCheckButton("Are the coefficients formatted?",  "unselect", "active", "nocommand", "")


		self.LPOT.draw(2)
		self.LNCOL.draw(3)
		self.LFOPM.draw(4)

```

I hope I made myself clear - I feel confused now ... :D

---

### Post by tjansson on 2007-07-20
Found the solution in another thread - [http://ubuntuforums.org/showthread.php?t=498292](http://ubuntuforums.org/showthread.php?t=498292)

---

