---
title: "I need some python help, please"
date: 2009-03-04
forum: Programming Talk
---

### Post by ramidavis on 2009-03-04
i have this in .py file:

```
import string as st
nar = []
 
nar.append([' '])
nar.append(['!','@','#','$','%','^','&','*','(',')'])
nar.append(['a','b','c'])
nar.append(['d','e','f'])
nar.append(['g','h','i'])
nar.append(['j','k','l'])
nar.append(['m','n','o'])
nar.append(['p','q','r','s'])
nar.append(['t','u','v'])
nar.append(['w','x','y','z'])
 
bigres = ""
while 1:
        inp = raw_input("")
        #print inp
        inp0 = int(inp[0])
        #print inp0
        inpc = st.count(inp,inp[0])
        inpcmod = inpc % len(nar[inp0])
        inpc = inpcmod -1
        #print inpc
        inpResult = nar[inp0][inpc]
        print bigres + " + " + inpResult
        bigres += inpResult
```

 and it gives me an error when i use it:
:~/Desktop$ ./a.py
./a.py: line 1: import: command not found
./a.py: line 2: nar: command not found
./a.py: line 4: syntax error near unexpected token `[' ']'
./a.py: line 4: `nar.append([' '])'


Any help??

I copy and pasted it from [*_[COLOR="Blue"]this[/COLOR]_*]("http://danfolkes.com/index.php/2008/08/11/python-cell-phone-number-pad-input/") site into a new file, named a.py, and allowed it to execute as program in 
right click > properties, then used terminal to execute. What am i missing here??:confused:

---

### Post by cyfur01 on 2009-03-04
The "./" directive is trying to execute the python file as a bash script. Thus you have two options:
1. Launch it as "python a.py" instead of "./a.py"
2. Add "#!/usr/bin/env python" to the start of the file so that bash will know that you want it to use the python interpreter to run the rest of the file. Then you can use "./a.py" to your heart's content. i.e.:
```

#!/usr/bin/env python
import string as st
nar = []
 
nar.append([' '])
nar.append(['!','@','#','$','%','^','&','*','(',')'])
nar.append(['a','b','c'])
nar.append(['d','e','f'])
nar.append(['g','h','i'])
nar.append(['j','k','l'])
nar.append(['m','n','o'])
nar.append(['p','q','r','s'])
nar.append(['t','u','v'])
nar.append(['w','x','y','z'])
 
bigres = ""
while 1:
        inp = raw_input("")
        #print inp
        inp0 = int(inp[0])
        #print inp0
        inpc = st.count(inp,inp[0])
        inpcmod = inpc % len(nar[inp0])
        inpc = inpcmod -1
        #print inpc
        inpResult = nar[inp0][inpc]
        print bigres + " + " + inpResult
        bigres += inpResult


```

---

### Post by Can+~ on 2009-03-04
Adding to what they said above, notice that this piece of code is terrible:

[LIST]
[*]Variable names are not clear. Nothing in the code is clear.
[*]The library "string" is deprecated, instead, strings now have their methods included.
[*]Since the sizes of the inside elements of the nar array are static, it should be more clever to use tuples ().
[*]The program doesn't catch errors when converting input to integers (# and *).
[/LIST]

---

### Post by sailthesea on 2009-03-04
Told you these guys would help you out
Try and explain what you want to do I still think its a good idea !

---

### Post by ramidavis on 2009-03-04
Well, i had this idea of 'texting style' input, (like cell phones use for text messages) but use it on computers. So, you could, if you wanted, just get one of those [[COLOR="Blue"]*_usb number pads_*[/COLOR]]("http://ecx.images-amazon.com/images/I/31%2BsAZrEa9L._SL500_AA280_.jpg"), and use that as your main keyboard. lol, strange idea i know, but, thats what i had in mind. This is a good start, but what i need now is way to run this, capture the input and output the result to some other program as text input for that program. Any way, just a crazy idea i had.

---

### Post by Can+~ on 2009-03-05
Aside from a programming exercise, I don't see how this can be useful for a computer user with a proper keyboard.

Btw, here's my version on python3. It doesn't add it to a string, but it simulated the cellphone keyboards, waiting for a time threshold to change the letter.

[PHP]
#!/usr/bin/python3
#using python3

import time

#Cellphone keyboard imitation
cell_keyboard = {
	"0" : (" "),
	"1" : ("!","@","#","$","%","^","&","*","(",")"),
	"2" : ("a","b","c","A","B","C"),
	"3" : ("d","e","f","D","E","F"),
	"4" : ("g","h","i","G","H","I"),
	"5" : ("j","k","l","J","K","K"),
	"6" : ("m","n","o","M","N","O"),
	"7" : ("p","q","r","s","P","Q","R","S"),
	"8" : ("t","u","v","T","U","V"),
	"9" : ("w","x","y","z","W","X","Y","Z"),
	"#" : (" "), #add something here
	"*" : (" ") 
}

THRESHOLD = 1.0 		# Constant: Seconds before resetting the keyboard
user_input = "" 		# Current user input
last_key = ["", 0] 		# Last key and repetitions.

print("Valid characters: 0-9 # * and q to quit")

while not user_input == "q":
	try:
		#Measure the time it takes to respond.
		response_time = time.time()
		user_input = input(">>")[0]
		response_time = time.time() - response_time
	except IndexError:
		user_input = ""
	
	#Check if it's valid
	if user_input in cell_keyboard:
		
		#If it matches the last key
		if user_input == last_key[0]:
			
			# And it was within threshold
			if response_time < THRESHOLD:
				last_key[1] += 1
			else:
				last_key[1] = 0
		else:
			# Assign the new key and 0 repetitions
			last_key[0] = user_input
			last_key[1] = 0
		
		#Now request the element on the keyboard.
		try:
			print(cell_keyboard[last_key[0]][last_key[1]])
		except IndexError:
			last_key[1] = 0
			print(cell_keyboard[last_key[0]][last_key[1]])
		
	else:
		print("Not a valid key.")
[/PHP]

It would probably be better with functions and classes, but I thought I had to stick to the "script" nature of the original one.

---

### Post by ramidavis on 2009-03-05
Nice! Yes, actually i just started python about a little while ago. Its my second language, c64 basic was my first. I just like 'mucking in the mud' so to speak. Write a few lines, see what happens, kill an hour or two... Thats what i love about the c64, and python. You can just cut loose and make something totally useless, and yet have fun and feel like you did something good. N o wonder they include python with the OLPC project. Great way to let kids explore and get thier feet wet. Maybe some day i'll pick up some java skills...

---

