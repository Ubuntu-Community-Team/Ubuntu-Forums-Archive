---
title: "[SOLVED] Python- charming the snake.."
date: 2008-09-06
forum: Programming Talk
---

### Post by sp0nge on 2008-09-06
Hello, I am quite new to python and have been working to learn it independently for some time. It's been a journey but I've done well in my oppinion, but I need a little education that I can't seem to find on my own.

I have created a small encrypt/decrypt program. Nothing l337, but it's simple and helping me grasp the concepts of the language (my only previous experience is HTML really). 

When I run these commands in idle, it works. When I just try to run it on my machine, it HALF works (I can encode, but the decode prints and closes the window). This is the second version of this program I've made, the first works completely but I'm missing something here. 

Can someone tell me how to keep the program from closing after running the decode script, and perhaps continue looping through theMenu? 

```
import string

def getChoice(menu):
    print menu
    choice = int( raw_input("Select a choice(1-3): ") )
    return choice

def rot(string, ammount):
	return string [ammount:] + string[:ammount]

def main():
    theMenu = '''
    1) Encrypt
    2) Decrypt 
    3) Quit
    '''	
    choice = getChoice(theMenu)		
    while choice != 3:
    	if choice == 1:
        	tablefrom = string.ascii_lowercase
		tableto = rot(string.ascii_lowercase, 2)
		table_encode = string.maketrans(tablefrom, tableto)
		thestring = raw_input("Enter String:")
		encoded = thestring.translate(table_encode)
		print "Encoded string:", encoded
	elif choice == 2:
		tablefrom = string.ascii_lowercase
		tableto = rot(string.ascii_lowercase, 2)
		table_decode = string.maketrans(tableto, tablefrom)
		thestring = raw_input("Enter String:")
		encoded = thestring.translate(table_encode)
		print "Decoded string:", decoded
	else:
		print 'Invalid choice, try again!'
	choice = getChoice(theMenu)
if __name__ == "__main__":
    main()
```


Thanks for the help.

---

### Post by slavik on 2008-09-06
run it in a terminal, or add a sleep or something of the sort.

---

### Post by Martin Witte on 2008-09-06
when you save this ode in a file, and then run it from a command prompt you see:
martin@toshibap200:~$ python test.py

    1) Encrypt
    2) Decrypt 
    3) Quit
    
Select a choice(1-3): 2
Enter String:qwerty
Traceback (most recent call last):
  File "./test.py", line 38, in <module>
    main()
  File "./test.py", line 32, in main
    encoded = thestring.translate(table_encode)
UnboundLocalError: local variable 'table_encode' referenced before assignment
martin@toshibap200:~$ 

It looks like you copied the decode part from the encode part, and didnn't change all instances of encode ....

---

### Post by pmasiar on 2008-09-06
You start new terminal window for your program by double-clicking? When it finishes, closes.

If you run it in existing opened terminal, it will stay opened. 

Or before finishing main(), add line:
```
dummy=input_raw('All done - press any key finish')
```

---

### Post by sp0nge on 2008-09-06
Silly mistake, thanks for pointing that out. I'm super new to this and seem to be overlooking some small things. I fixed the problem with the encode, and it seemed to work a little more correctly. 

This time, the problem seems to be that the encode and decode portion was doing the same thing, so I changed it a bit and I'm still not quite sure why, but I'm not doing it correctly:


_____

I'm a blonde, not to mention out of my league at this point. Thanks for the help. It werkz! 

```
import string

def getChoice(menu):
	print menu
	choice = int( raw_input("Select a choice(1-3): ") )
	return choice

def rot(string, ammount):
	return string [ammount:] + string[:ammount]

def main():
	theMenu = '''
    	1) Encrypt
    	2) Decrypt 
    	3) Quit
    	'''	
    	choice = getChoice(theMenu)		
    	while choice != 3:
    		if choice == 1:
        		tablefrom = string.ascii_lowercase
			tableto = rot(string.ascii_lowercase, 2)
			table_encode = string.maketrans(tablefrom, tableto)
			thestring = raw_input("Enter String:")
			encoded = thestring.translate(table_encode)
			print "Encoded string:", encoded
		elif choice == 2:
			tablefrom = string.ascii_lowercase
			tableto = rot(string.ascii_lowercase, 2)
			table_decode = string.maketrans(tableto, tablefrom)
			thestring = raw_input("Enter String:")
			decoded = thestring.translate(table_decode)
			print "Decoded string:", decoded
		else:
			print 'Invalid choice, try again!'
		choice = getChoice(theMenu)
if __name__ == "__main__":
    main()
```

---

