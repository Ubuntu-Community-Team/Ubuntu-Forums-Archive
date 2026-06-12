---
title: "python / glade help"
date: 2007-02-09
forum: Programming Talk
---

### Post by Choad on 2007-02-09
```

#!/usr/bin/env python

import sys

try:
	import gtk
	import gtk.glade
except:
	sys.exit(1)

class HelloWorldGUI:
	def __init__(self):
	        self.wTree = gtk.glade.XML("pyglade.glade", "HelloWorld")
	        
	dic = {"on_HelloWorld_destroy" : gtk.main_quit}
	
	self.wTree.signal_autoconnect(dic)
	
app = HelloWorldGUI()
gtk.main()

```

was following a tutorial and thats the code i ended up with. when i run it i get 

```

richard@richard-laptop:~$ cd Projects/pyglade/
richard@richard-laptop:~/Projects/pyglade$ ./MyPyGladeApp.py 
Traceback (most recent call last):
  File "./MyPyGladeApp.py", line 11, in ?
    class HelloWorldGUI:
  File "./MyPyGladeApp.py", line 17, in HelloWorldGUI
    self.wTree.signal_autoconnect(dic)
NameError: name 'self' is not defined
richard@richard-laptop:~/Projects/pyglade$ 
```

---

### Post by Choad on 2007-02-09
never mind. my bad. sorted it

---

### Post by Choad on 2007-02-09
> **Choad said:**
> never mind. my bad. sorted it
ok, so heres something

```

#!/usr/bin/env python

import sys

try:
 	import pygtk
  	pygtk.require("2.0")
except:
  	pass
try:
	import gtk
	import gtk.glade
except:
	sys.exit(1)

class HelloWorldGUI:
	def __init__(self):
	        self.wTree = gtk.glade.XML("pyglade.glade", "HelloWorld")
	        
		dic = {	"on_HelloWorld_destroy" 	: gtk.main_quit,
			"on_btnClickMe_clicked" 	: self.btnHelloWorldClick}
	
		self.wTree.signal_autoconnect(dic)
	
	def btnHelloWorldClick(self, widget):
		print "omg ponies"
**		self.wTree.get_widget("btnClickMe").Label = "pooo"**
		
if __name__ == "__main__":
	app = HelloWorldGUI()
	gtk.main()

```

why does that not work? im just guessing at how to do most things... how would i rename the label of the button when it's clicked?

---

### Post by Choad on 2007-02-10
bump

cmon! python/gtk is really popular, all i wanna know is how to refer to a widget

---

### Post by psychicdragon on 2007-02-10
To change the label of a button, you need to use the button's set_label method.

```
some_button.set_label("Hello!")
```

Take a look at the [PyGtk reference manual]("http://pygtk.org/docs/pygtk/index.html").

---

### Post by Choad on 2007-02-10
great odins raven! it works!

---

### Post by Choad on 2007-02-11
ok another question

```
#!/usr/bin/env python

import sys

try:
 	import pygtk
  	pygtk.require("2.0")
except:
  	pass
try:
	import gtk
	import gtk.glade
except:
	sys.exit(1)

class MoneyCalc:
	def __init__(self):
	        self.wTree = gtk.glade.XML("moneycalc.glade", "window1")
	        
		dic = {	"on_window1_destroy" 		: gtk.main_quit,
**			"on_btnCalculate_clicked"	: self.btnCalculateClicked**
			}
	
		self.wTree.signal_autoconnect(dic)
	
[B]	def btnCalculateClicked(self, widget):
		self.CalculateCoins(self.wTree.get_widget("spinMoney").get_value())	
	
	def CalculateCoins(total):
		x = total
		print x
		x -= 10
		print x[/B]
	
		

if __name__ == "__main__":
	app = MoneyCalc()
	gtk.main()
```

when i click the button, i get an error 

TypeError: CalculateCoins() takes exactly 1 argument (2 given)

whats up with this? i only *seem* to be giving it 1 argument

as you might be able to tell, im not that strong with python yet :p:

edit: ok, if i give it an argument before "total" then it works fine. what is the mystery argument that is being passed to the function?

---

### Post by psychicdragon on 2007-02-11
This is a Python thing; class methods must always have self as their first argument.

---

### Post by Choad on 2007-02-11
ok thats cool

now im trying to get an array to work. the page im lookin at says

bla = array([8])

but it gives me an error

 coins = array([8])
NameError: global name 'array' is not defined

thanks for all the help by the way. these forums rule!

---

### Post by psychicdragon on 2007-02-11
Dude, you should really read a Python tutorial. You're going about this the wrong way.

Python is a dynamically typed language, meaning that variables are the type that they seem to be. To make a list, just create a variable and treat it like a list.

```
my_list = ["Hello!", something, 2, 9.99999]
other_list = []
other_list.append(my_list)
```
etc.

---

### Post by Choad on 2007-02-11
hehe yeah i know i should. i always find actually trying to write a program is a much better way of learning a language tho.

anyway, thanks for that, works!

how do you concatenate a string and an int? i probably wont need any more help after this :D

---

### Post by psychicdragon on 2007-02-11
```

foo = "hello"
bar = 22

print foo + str(bar)

```

---

### Post by Choad on 2007-02-11
thanks again!

ok it all works, take a look

```

	def CalculateCoins(self, total):
		
		x = total
		
		coins = [2,1,0.5,0.2,0.1,0.05,0.02,0.01]
		
		for i in range(0,7):
			temp = 0
			while x >= coins[i]:
				temp += 1
				x -= coins[i]
			self.wTree.get_widget("entry" + str(i+1)).set_text(str(temp))

```

it takes the input "total" and works out the minimum number of coins needed to make up "total". it then tells you which coins you need by assigning each text entry "entry1" to "entry8" a value. (this is uk coins)

the only thing is, the last entry box never gets assigned.

also, for i in range(0,7) is a bit rubbish. cant i sumhow do for i in range(coins) or something? it doesnt seem to work if i change it tho

thanks again for the help

---

### Post by Choad on 2007-02-11
here is the project if you wanna have a look :)

also, it seems that it doesnt shut down cleanly. it always leaves a copy of python running in the task manager

---

### Post by psychicdragon on 2007-02-11
Two more tips for your project:

```
for coin in coins:
  # code goes her
```

Also, you need to attach gtk.main_quit() to the "delete-event" signal of your window for your program to exit cleanly.

---

### Post by Choad on 2007-02-11
for i in coins: doesnt count from 0 to 7 tho, it goes through the list. so i is 2, then 1, then 0.5

which is no good :)

also, i still cant get the last text entry to work :(

never mind. for i in range(8 ) works

for some wierd reason, it doesnt work if i set the value to 3 pence :(. i fear this could be due to rounding?

is there any way i can manually set the precision? or should i simply multiply by 100 to get rid of decimals?

*100 worked

its all good

---

