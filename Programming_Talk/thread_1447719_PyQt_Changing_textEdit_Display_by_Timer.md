---
title: "PyQt Changing textEdit Display by Timer"
date: 2010-04-05
forum: Programming Talk
---

### Post by Greasyfingers on 2010-04-05
I'd appreciate some help. I'm not really a programmer; occasionally I manage to cobble some code together and make it do something useful - but please assume I'm a know-nothing.

I'm trying to make a simple GUI using PyQt, which will display the name of a random guitar chord (from a text file of chord names) in a window for a few seconds, and then display another chord name, and so on, until the window is closed. It's a rudimentary practise aid.

I've got the basis of it - mostly cribbed from examples on the web. Every time the window is opened a random chord name is diplayed, but I can't figure out how to make the chord name change every few seconds to a new one. I guess I need to loop a timer event somehow, but I need help with this.

Thanks.


Here's my code so far:

[php]
#!/usr/bin/python

# chorder.py

import sys, random
from PyQt4 import QtGui, QtCore

# Open the file of chord names
fileText = open('./chords', 'r')

# Setup an empty list to put the chord names into
chordList = []

# Run a loop that will extract each line of the file
# and continue untill it reaches the end of the file.
while 1:
	line = fileText.readline()
	chordName = line.rstrip()	# Strip whitespace from right of line
	if not line: break
	chordList.extend([chordName]) # Add each chord name to the list

fileText.close()

# Set the variable chordDisplay. This will be used  as an argument
# in the QTextEdit object and will change randomly at regular intervals
listLength = len(chordList)
n = random.randrange(0,listLength)	# Get a random number within range of list length
chordDisplay = chordList[n]	# Get a chord name, dependant upon the value of n
	
class MainWindow(QtGui.QMainWindow):
	def __init__(self):
		QtGui.QMainWindow.__init__(self)
		
		# Display chord name in a read-only QTextEdit widget.
		textEdit = QtGui.QTextEdit("<br><br><h1 style = font-family:Sans;color:red>\
		<center>" + chordDisplay + "</center></h1>")	# Text displayed in HTML format
		textEdit.setReadOnly(True)
		
		self.setCentralWidget(textEdit)	# Set position of QTextEdit widget in MainWindow
		self.setGeometry(290, 250, 500, 250)		# Set position and size of MainWindow
		self.setWindowTitle('Chorder')	# Set title of MainWindow
		self.setWindowIcon(QtGui.QIcon('./windIcon.svg'))	# Give MainWindow and icon

app = QtGui.QApplication(sys.argv)
main = MainWindow()
main.show()
sys.exit(app.exec_())
[/php]

---

### Post by ahmatti on 2010-04-06
You can do what you want quite easily with Qtimer: [http://www.riverbankcomputing.co.uk/static/Docs/PyQt4/html/qtimer.html](http://www.riverbankcomputing.co.uk/static/Docs/PyQt4/html/qtimer.html). Here is a quick example [http://www.rkblog.rk.edu.pl/w/p/qtimer-making-timers-pyqt4/](http://www.rkblog.rk.edu.pl/w/p/qtimer-making-timers-pyqt4/)

---

### Post by Greasyfingers on 2010-04-06
Thanks for that, ahmatti.

The example you linked to may be just what I need, but when I try to run it I get an error message 'ImportError: No module named timer'. Is it just a typo? I notice you called the module 'Qtimer'; I've tried renaming the moduel to various things, but can't get it to work.

What am I doing wrong?

BTW, I'm using Python 2.5 if that makes any difference.

---

### Post by oldfred on 2010-04-06
You cannot copy the example but have to download the entire example (at bottom of page) since it includes several files.

---

### Post by Greasyfingers on 2010-04-06
Got it. I understand how that was the wrong thing to do, now.

Thanks. I'll study that example and try to fathom out how to use it on mine.

---

