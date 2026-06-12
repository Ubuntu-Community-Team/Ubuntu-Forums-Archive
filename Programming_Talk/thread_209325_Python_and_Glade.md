---
title: "Python and Glade"
date: 2006-07-05
forum: Programming Talk
---

### Post by frup on 2006-07-05
i've now come across a neat gui program called glade and have managed to build something crap but im proud of it :D
The tutorial i found this on gave me code to make a clickable button... but didnt explain any of the code (more focused on how to use glade)

does anyone know of any good glade + python tutorials for a n00b.. basically explaining how to add something to the program and where to put the code etc.. using glade i made an about dialog.. but this opens with the main window.. how do i hide this.. how do i link this to the help>about menu etc .. thanks :D

---

### Post by atoponce on 2006-07-05
[quote=frup]i've now come across a neat gui program called glade and have managed to build something crap but im proud of it :D
The tutorial i found this on gave me code to make a clickable button... but didnt explain any of the code (more focused on how to use glade)

does anyone know of any good glade + python tutorials for a n00b.. basically explaining how to add something to the program and where to put the code etc.. using glade i made an about dialog.. but this opens with the main window.. how do i hide this.. how do i link this to the help>about menu etc .. thanks :D[/quote]
I would love to learn more about Python and Glade.  I don't know much Python, but would really love to learn.  I have a few projects at work that I need to get started on, and I would love to do them with Python.  So if you find anything out, please, make sure that you post it here! :)

---

### Post by noob_Lance on 2006-07-05
can ya paste a link for us. i personally would like to see this and hopefully exapand on it. ^_^

thanks
~Lance

---

### Post by frup on 2006-07-05
[http://www.learningpython.com/category/python/glade/](http://www.learningpython.com/category/python/glade/)

i did the building an application with pygtk glade tutorial... please keep in mind i came across python about 18 hours ago :D lol.

all i have managed to do extending on that tutorial is add images to the gui with glade and unfunctional things.. and googling only gives me glade documentation or really advanced tutorials... so basically when i add an input box or whatever i have no idea how to implement it to the program... when i add an about dialogue in glade... i have no idea how to link that to the about menu :S

also in the tutorial on that link.. clicking the button prints hello world in my IDE... how would i make this change what the label says or something like that?

Edit:```
def on_about1_activate(self, widget):
	print "About menu"
```
allows me to print this when the about menu is clicked.. i now have to work out how to load aboutdialogue1 :s lol

well i worked it out :D self.(glade xml stuff).get_widget( ) :D

---

### Post by Jayzilla on 2006-07-05
Many good ideas for beginner's projects can be found here: [http://www.daniweb.com/techtalkforums/thread32007.html](http://www.daniweb.com/techtalkforums/thread32007.html)

Fiddle around with them...you'll be surprised what you learn! :D

Good luck!

---

### Post by frup on 2006-07-05
Thanks, This is what i have and its not quite doing what i want with the file IO lol... ofcourse i have no idea what i am doing... basically before the file IO used a raw_input and now im trying to get input from the gui input field which is written when a button is pressed.. but i cant/dont know how to make it work.

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

class HellowWorldGTK:
	"""This is an Hello World GTK application"""

	def __init__(self):
		
		#Set the Glade file
		self.gladefile = "pyhelloworld.glade"  
	        self.wTree = gtk.glade.XML(self.gladefile) 
		
		#Create our dictionary and connect it
		dic = { "on_about1_activate" : self.on_about1_activate, "on_btnHelloWorld_clicked" : self.btnHelloWorld_clicked, 
            "on_entry1_insert_text" : self.on_entry1_insert_text,
			"on_MainWindow_destroy" : gtk.main_quit }
		self.wTree.signal_autoconnect(dic)
        
        def on_about1_activate(self, widget):
            print "open about later" 
            "Display the about dialog"
            about = self.wTree.get_widget("aboutdialog1")
            about.show ()
            
        def on_entry1_insert_text(self, widget):
        #No error messages but may not work... remember dictionary
            #Write a file
            out_file = open("test.txt","w")
            out = self.wTree.get_widget("entry1")
            out_file.write(out+"\n")
            out_file.close()

            #Read a file
            in_file = open("test.txt","r")
            text = in_file.read()
            in_file.close()

            print text,
        
        def btnHelloWorld_clicked(self, widget):
            print "Hello World!"
        #on_entry1_insert_text() #This doesnt work yet

if __name__ == "__main__":
     hwg = HellowWorldGTK()
     gtk.main()
```

---

### Post by xtacocorex on 2006-07-05
The PyGTK site is a good resource for programming with Python and GTK+.

It does take some thinking to figure out how to use the stuff with Glade, but it isn't bad.

Here is the link:
[http://www.pygtk.org/](http://www.pygtk.org/)

---

### Post by frup on 2006-07-05
i've already been through most of it but dont understand it yet :(

---

### Post by Note360 on 2006-07-05
WOW, you are moving fast through Python.

---

### Post by Note360 on 2006-07-05
Sorry, double post.

---

### Post by frup on 2006-07-05
probably too fast, im not taking much in.. with out the GUI its not too hard, basically similar concepts to PHP and javascript.. just have to find the built in functions... thats what im finding difficult.. i think i might stop trying to build a gui just yet... focus more on actually learning the language...

heres a script i made which was one of the ideas suggested on [http://www.daniweb.com/techtalkforums/thread32007.html](http://www.daniweb.com/techtalkforums/thread32007.html) ... im having a few problems with it i dont understand..  when alphanum[letter] is printed, each character is printed with a space between it.. i dont understand why this is happening or know how to fix it.. the commented out part of pwd[0]... prints it all together but that leaves a fixed length for the so called password..
```
import random

pwdlength = input("How long would you like your password? ")
alphanum = ("1","2","3","4","5","6","7","8","9","0","A","B","C","D","E","F","G","H","I","J","K","L","M","N","O","P","Q","R","S","T","U","V","W","X","Y","Z")
i = 0
while i < pwdlength:
    i = i+1
    letter = random.randint(0,35)
    print(alphanum[letter]),#can't we just print this! why the gaps with print aplhanum[letter],!
print 
#"\n\n",pwd[0]+pwd[1]+pwd[2]+pwd[3]+pwd[4]+pwd[5]

```

now if i convert it to JavaScript, it works fine :S i realise this is because in HTML you have force a line break, and in python loop automatically prints on a new line, a tutorial i did showed the  
```
    print(alphanum[letter]),
print 
```
method which makes it print on the same line, put it prints with a space between each char. :(  JS:
```
<script language="JavaScript">
var pwdlength = prompt("How long would you like your password? ","");
pwdlength = parseInt(pwdlength)
var alphanum = new Array("1","2","3","4","5","6","7","8","9","0","A","B","C","D","E","F","G","H","I","J","K","L","M","N","O","P","Q","R","S","T","U","V","W","X","Y","Z");
var i = 0;
while (i < pwdlength){
    i = i+1;
    var letter = Math.round(Math.random()*35);
    document.write(alphanum[letter]); 
}
</script>
```

---

### Post by Engnome on 2006-07-05
[QUOTE=frup]i've now come across a neat gui program called glade and have managed to build something crap but im proud of it :D
The tutorial i found this on gave me code to make a clickable button... but didnt explain any of the code (more focused on how to use glade)
[/QUOTE]

Do you have any knowledge of _coding_ a GUI? You should learn how to code a GUI from scratch without using programs such as glade. Once you can do some basic stuff figuring out how to link those GladeXML files will be easy. (besides the tutorials I've used when learning glade assumed some knowledge of _coding_ GUI)

---

### Post by frup on 2006-07-05
nope no knowledge... the most ive ever done is some stuff in java using the netbeans IDE which let me configure GUI through it.. i've already managed to do more than this in python but still am pretty lost..

---

### Post by dabear on 2006-07-05
[QUOTE=frup] having a few problems with it i dont understand..  when alphanum[letter] is printed, each character is printed with a space between it.. i dont understand why this is happening or know how to fix it.. the commented out part of pwd[0]... prints it all together but that leaves a fixed length for the so called password..
```
import random

pwdlength = input("How long would you like your password? ")
alphanum = ("1","2","3","4","5","6","7","8","9","0","A","B","C","D","E","F","G","H","I","J","K","L","M","N","O","P","Q","R","S","T","U","V","W","X","Y","Z")
i = 0
while i < pwdlength:
    i = i+1
    letter = random.randint(0,35)
    print(alphanum[letter]),#can't we just print this! why the gaps with print aplhanum[letter],!
print 
#"\n\n",pwd[0]+pwd[1]+pwd[2]+pwd[3]+pwd[4]+pwd[5]

```

[/QUOTE]
I must say, you are too influenced with php or something.
First of all, import string, and set aplhanum to something like string.digits + string.ascii_uppercase 

Second: the random module has the ability to pick a random element directly:  
```

r=random.Random()
print r.choice(yourlist)
```

Third: print's behaviour is to append a spache after each "parameter" it gets, this is for convenience only, because you almost every time want that space there to seperate items. If you want to do it otherwise, use pythons builtin "printf"-like control structure.
```

print '%s%s%d' % (var,var2, var3PrintedAsDigit)

```

And finally: if you have a string/list you want to print out some elements of, don't do
```

print  "\n\n",pwd[0]+pwd[1]+pwd[2]+pwd[3]+pwd[4]+pwd[5]


```

But rather
```

print  "\n\n",pwd[0:5]

```
(0 is starting point, 5 is how many you want).


If you have a list of passwds = ['pass1', 'pass2'] etc, you can concat them by using a function similar to implode() in php, the name of the method is "join", which is a method of a string, rather than a list.
so
```

<?php
echo implode(':', array('one', 'two', 'three'));
?>

```
is the same as this in python:

```

print ':'.join(['one', 'two', 'three'])

```

Hope that helped;)

---

### Post by frup on 2006-07-05
thankyou very much !!!! :D now i just have to work out exactly how those work :)

Theres no i++ in python is there? the tutorial i did on loops has i = i+1 which i think is stupid lol

this is what i have so far```

import random
import string

pwdlength = input("How long would you like your password? ")

alphanum = string.digits + string.ascii_uppercase
i = 0
while i < pwdlength:
    i = i+1
    letter = random.randint(0,35)
    pwd = []
    print alphanum[letter],#can't we just print this! why the gaps with print aplhanum[letter],! 
    pwd.append(alphanum[letter])
print  "\n\n",pwd[0:5] # This only prints out the last digit not 0:5 :S its out side the loop too. :S

```

EDIT and 49 minutes later its fixed :D lol stupid me was declaring the list in the loop, wiping it each instance lol 
```

import random
import string

pwdlength = input("How long would you like your password? ")
alphanum = string.digits + string.ascii_uppercase
i = 0
pwd = []
while i < pwdlength:
    i = i+1
    letter = random.randint(0,35)
    pwd.append(alphanum[letter])
print ''.join(pwd)

```

---

### Post by dabear on 2006-07-06
I would rather iterate over a range equal to the length of the password. It makes a shorter code.
You could either write this:
```

import random
import string

pwdlen = input("How long would you like your password? ")
alphanum = string.digits + string.ascii_uppercase

pwd = []
for i in xrange(pwdlen):
    pwd.append(random.choice(alphanum))
print ''.join(pwd)

raw_input()

```
or as a list-comprehension (I added a check for int value from the user)
```
import random
import string

pwdlen = raw_input('How long would you like your password? ')
alphanum = string.digits + string.ascii_uppercase

try:
    print ''.join([random.choice(alphanum) for i in xrange(pwdlen)])
except TypeError:
    print 'You did not type an integer! exiting.. bye bye.'
raw_input()

```

---

