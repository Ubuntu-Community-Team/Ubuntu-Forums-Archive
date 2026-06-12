---
title: "[SOLVED] Python with Tkinter, problems with grid placement"
date: 2007-05-11
forum: Programming Talk
---

### Post by tjansson on 2007-05-11
Dear all

I am trying to make a small wrapper program for textbased program and
it is going well but I have one problem. The placement of the widgets with grid is acting so strange. Eventhough I tried to place the button in a grid the ouput is totally different from what I designed.

I would have expected that the following made theese 3 buttons sit next to each other on a row
```

self.writetofileLabel.grid(row=0, column=0, sticky=W)
self.outputfileEntry.grid(row=0, column=1)
self.writetofileButton.grid(row=0, column=2)

```
but as can be seen in this picture they don't?

[IMG]http://tjansson.dyndns.dk/apache2-default/strange-grid.jpg[/IMG]

```

#!/usr/bin/python
"""\
Graphical interface for geocol12
Thomas R. N. Jansson
tjansson@fys.ku.dk
"""

#Load graphical tool kit
from Tkinter import *

import os
# clear console
# os.system('clear')


class App:
	
	def __init__(self, master):
		frame = Frame(master)
		frame.grid()
		
		#Write File
		self.writetofileLabel = Label(frame,text="Output filename:")
		self.outputfile = StringVar()
		self.outputfileEntry = Entry(master, state=NORMAL, text="Title", textvariable=self.outputfile)
		self.outputfileDefault = "default.inp"
		self.outputfileEntry.insert(0, self.outputfileDefault)
		self.writetofileButton = Button(frame, text="Write to file", command=self.write_to_file)
		self.writetofileLabel.grid(row=0, column=0, sticky=W)
		self.outputfileEntry.grid(row=0, column=1)
		self.writetofileButton.grid(row=0, column=2)
		
		#Option LPOT
		self.lpot= IntVar()
		self.lpotCheckbutton = Checkbutton(master, text="LPOT", variable=self.lpot)
		self.lpotCheckbuttonLabel = Label(frame,text="LPOT or not :")
		self.lpotCheckbuttonLabel.grid(row=1, column=0, sticky=W)
		self.lpotCheckbutton.grid(row=1, column=1)
		
		#Option LNCOL
		self.lncol = IntVar()
		self.lncolCheckbutton = Checkbutton(master, text="LNCOL", variable=self.lncol)
		self.lncolCheckbuttonLabel = Label(frame,text="LPOT or not :")
		self.lncolCheckbuttonLabel.grid(row=2, column=0, sticky=W)
		self.lncolCheckbutton.grid(row=2, column=1)
		
		#Input name of pot. coeff. set:
		self.runtitle = StringVar()
		self.runtitleEntry = Entry(master, state=NORMAL, text="Title", textvariable=self.runtitle)
		self.runtitleDefault = "Osu91a To Degree 10"
		self.runtitleEntry.insert(0, self.runtitleDefault)
		self.runtitleLabel = Label(frame,text="Name of Pot. Coeff. Set :")
		self.runtitleLabel.grid(row=3, column=0, sticky=W)
		self.runtitleEntry.grid(row=3, column=1)
		
		#QUIT
		self.button = Button(frame, text="QUIT", fg="red", command=frame.quit)
		self.button.grid(row=4, column=0, sticky=W)
		
		#Run geolcol12
		self.rungeolcolButton = Button(frame, text="Run geolcol12", command=self.run_geocol12)
		self.rungeolcolButton.grid(row=4, column=2, sticky=E)
		
		#self.refsys = IntVar()
		#self.refsysScale = Scale(master, from_=0, to=10, textvariable=self.refsys)
		#self.refsysScale.grid()		
		
	def write_to_file(self):
		#print self.outputfile.get()
		file = open(self.outputfile.get(), 'w')
		if file:
			print "open file"
			lncol = "f"
			print self.lncol.get()
			if self.lncol.get() == "0":
				lncol = "t"
			print lncol	
			wordlist = ["t\n", "f t f f f t f\n", self.outputfile.get(), "\n" ]
			file.writelines(wordlist)
			
			print self.outputfile.get()
			file.close
			print "close file"
		else:
			print "ERROR: writing to file"
		
	def run_geocol12(self):
		if os.path.isfile("cct/dgravsoft/geocol12"):
			write_to_file()
			os.popen("cct/dgravsoft/geocol12 <"+self.outputfile.get()+" &" )
		else:
			print "ERROR: cct/dgravsoft/geocol12 does not exist"
	
	
root = Tk()
app = App(root)
#root.geometry("640x100")
root.title('Graphical interface for geolcol12')
root.mainloop()                                                        

```

Kind regards
Thomas Jansson

---

### Post by cwaldbieser on 2007-05-12
> **tjansson said:**
> Dear all

I am trying to make a small wrapper program for textbased program and
it is going well but I have one problem. The placement of the widgets with grid is acting so strange. Eventhough I tried to place the button in a grid the ouput is totally different from what I designed.

I would have expected that the following made theese 3 buttons sit next to each other on a row
```

self.writetofileLabel.grid(row=0, column=0, sticky=W)
self.outputfileEntry.grid(row=0, column=1)
self.writetofileButton.grid(row=0, column=2)

```
but as can be seen in this picture they don't?

[IMG]http://tjansson.dyndns.dk/apache2-default/strange-grid.jpg[/IMG]

```

#!/usr/bin/python
"""\
Graphical interface for geocol12
Thomas R. N. Jansson
tjansson@fys.ku.dk
"""

#Load graphical tool kit
from Tkinter import *

import os
# clear console
# os.system('clear')


class App:
	
	def __init__(self, master):
		frame = Frame(master)
		frame.grid()
		
		#Write File
		self.writetofileLabel = Label(frame,text="Output filename:")
		self.outputfile = StringVar()
		self.outputfileEntry = Entry(master, state=NORMAL, text="Title", textvariable=self.outputfile)
		self.outputfileDefault = "default.inp"
		self.outputfileEntry.insert(0, self.outputfileDefault)
		self.writetofileButton = Button(frame, text="Write to file", command=self.write_to_file)
		self.writetofileLabel.grid(row=0, column=0, sticky=W)
		self.outputfileEntry.grid(row=0, column=1)
		self.writetofileButton.grid(row=0, column=2)
		
		#Option LPOT
		self.lpot= IntVar()
		self.lpotCheckbutton = Checkbutton(master, text="LPOT", variable=self.lpot)
		self.lpotCheckbuttonLabel = Label(frame,text="LPOT or not :")
		self.lpotCheckbuttonLabel.grid(row=1, column=0, sticky=W)
		self.lpotCheckbutton.grid(row=1, column=1)
		
		#Option LNCOL
		self.lncol = IntVar()
		self.lncolCheckbutton = Checkbutton(master, text="LNCOL", variable=self.lncol)
		self.lncolCheckbuttonLabel = Label(frame,text="LPOT or not :")
		self.lncolCheckbuttonLabel.grid(row=2, column=0, sticky=W)
		self.lncolCheckbutton.grid(row=2, column=1)
		
		#Input name of pot. coeff. set:
		self.runtitle = StringVar()
		self.runtitleEntry = Entry(master, state=NORMAL, text="Title", textvariable=self.runtitle)
		self.runtitleDefault = "Osu91a To Degree 10"
		self.runtitleEntry.insert(0, self.runtitleDefault)
		self.runtitleLabel = Label(frame,text="Name of Pot. Coeff. Set :")
		self.runtitleLabel.grid(row=3, column=0, sticky=W)
		self.runtitleEntry.grid(row=3, column=1)
		
		#QUIT
		self.button = Button(frame, text="QUIT", fg="red", command=frame.quit)
		self.button.grid(row=4, column=0, sticky=W)
		
		#Run geolcol12
		self.rungeolcolButton = Button(frame, text="Run geolcol12", command=self.run_geocol12)
		self.rungeolcolButton.grid(row=4, column=2, sticky=E)
		
		#self.refsys = IntVar()
		#self.refsysScale = Scale(master, from_=0, to=10, textvariable=self.refsys)
		#self.refsysScale.grid()		
		
	def write_to_file(self):
		#print self.outputfile.get()
		file = open(self.outputfile.get(), 'w')
		if file:
			print "open file"
			lncol = "f"
			print self.lncol.get()
			if self.lncol.get() == "0":
				lncol = "t"
			print lncol	
			wordlist = ["t\n", "f t f f f t f\n", self.outputfile.get(), "\n" ]
			file.writelines(wordlist)
			
			print self.outputfile.get()
			file.close
			print "close file"
		else:
			print "ERROR: writing to file"
		
	def run_geocol12(self):
		if os.path.isfile("cct/dgravsoft/geocol12"):
			write_to_file()
			os.popen("cct/dgravsoft/geocol12 <"+self.outputfile.get()+" &" )
		else:
			print "ERROR: cct/dgravsoft/geocol12 does not exist"
	
	
root = Tk()
app = App(root)
#root.geometry("640x100")
root.title('Graphical interface for geolcol12')
root.mainloop()                                                        

```

Kind regards
Thomas Jansson

It looks like "self.outputfileEntry" has a parent of "master" while the other two have "frame" as their parent.  With different parents, they won't end up in the same grid.

---

### Post by tjansson on 2007-05-12
Thank you so much!! Spend so much time on this. :D

---

