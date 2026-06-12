---
title: "Plython button box; how can I make the buttons launch executables?"
date: 2007-12-23
forum: Programming Talk
---

### Post by Romanus81 on 2007-12-23
So basically, this is what I am trying to do:
I installed MPD and MPC so that I can have a light and fast way to launch a looping music file at startup for background music. I also created executables that will clear the MPC play list and load a different song (so if I feel like jazz instead of classical, I can easily change them. The problem with this is that I now have 5 icons on my gnome panel, so I wanted to make a script that will display my options as buttons and allow me to choose one.
It was suggested to me that I use python and easygui. So far this is what I have:
```

from easygui import *
import sys

while 1:
	msg ="Hello! Would you like to change the background music?"
	title = "Hi there!"
	choices = ["Jazz", "classical", "radio", "amarok"]
	choice = indexbox(msg, title, choices)

```
I based it off of an example I found online:

```

from easygui import *
import sys

while 1:
	msgbox("Hello, world!")

	msg ="What is your favorite flavor?"
	title = "Ice Cream Survey"
	choices = ["Vanilla", "Chocolate", "Strawberry", "Rocky Road"]
	choice = choicebox(msg, title, choices)

	# note that we convert choice to string, in case
	# the user cancelled the choice, and we got None.
	msgbox("You chose: " + str(choice), "Survey Result")

	msg = "Do you want to continue?"
	title = "Please Confirm"
	if ccbox(msg, title):     # show a Continue/Cancel dialog
		pass  # user chose Continue
	else:
		sys.exit(0)           # user chose Cancel

```

---

### Post by urukrama on 2007-12-25
Why don't you use gmessage for this? It seems like a much easier solution.

---

### Post by samjh on 2007-12-25
Have you check this? [http://docs.python.org/lib/os-process.html](http://docs.python.org/lib/os-process.html)

There are all kinds of functions to run commands from within Python.

For example, if I wanted to execute the [FONT="Courier New"]ls[/FONT] command on the current directory in the current process, I can use:
```
os.execlp("ls")
```
All you've got to do is use one of those functions to run mdp when an appropriate button is pressed.

---

