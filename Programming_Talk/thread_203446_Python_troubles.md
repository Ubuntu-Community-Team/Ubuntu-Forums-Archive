---
title: "Python troubles"
date: 2006-06-25
forum: Programming Talk
---

### Post by christhemonkey on 2006-06-25
Hi, im doing a [python course]("http://honors.montana.edu/~jjc/easytut/easytut/"), and i cant for the life of me get this program to function properly.

Im stuck on the exercise from the chapter on file in/out put, I have to refine a program from an earlier chapter (using dictionaries) to include the options to load and save to file.

When i try and load the saved file, i can never get it to load properly into the dictionary.

Attached is the current attempt.
(have removed the part where it attempts to load the inputed file into the dictionary as i cannot get the previous bit to work)

[The exercise]("http://honors.montana.edu/~jjc/easytut/easytut/node17.html#SECTION001710000000000000000")
[The original program.]("http://honors.montana.edu/~jjc/easytut/easytut/node13.html")


*It should be noted that i am doing this for fun and to learn, and am not trying to cheat on some exam or anything!:p *

Any help is of course appreciated in helping pointing out where i have gone wrong.

---

### Post by Revert on 2006-06-25
First off, it's going to need a while loop.  You're not always going to know how many lines there are, so you want it to run until it terminates.  You can either use the while 1: with the if and a break statement like they do in the example, or you could make it while len(whatever.readline) != 0:.  Either way, it's doing the same thing; I used the while 1 because it's what they used in the example.

Basically, you're going to want to...

while 1:
string = read a line

if the string's empty, it means you're at the end of the file, so break from the loop

otherwise, split the string

use the two portions of the split string as a key/value in the dictionary

Here's what I came up with:
[ATTACH]11744[/ATTACH]

---

### Post by digby on 2006-06-25
Revert is correct, but I wanted to add a little something that might help you out.  For (I believe) the last few versions of python, you don't really have to use the readline() function.  You can use a for loop and it will automatically treat each line as an element. For example in an exercise I just did, I was playing with a dictionary variable as well.  When I saved the file, I used this code:```
outFile = open('data.txt', 'w')
for x in dbase.keys():
    dbase[x].append(x)
    for y in dbase[x]:
       output = y
       output += ","
       outFile.write(output)
    
    outFile.write("\n")

outFile.close()
``` What this did was take my key and make it the last thing in the list that was associated with that key.  I then wrote that list to a file.  The next time the program was run, it imported from that file with this section:```
inFile = open("data.txt", "r")
    for line in inFile:
    if line == "": break
       dbase[line.split(',')[-2]] = line.split(',')[:-2]
```That part just reads every element in the file line by line.  When it gets to a blank line, it breaks the for loop.  The third line takes the second to last element in each line (remember, the new line marker is the last element) and makes it the key.  It then takes everything else in front of the key and makes it the list associated with that key.

Having a loop, as was stated above, is necessary because we rarely know how long a file is going to be in adavance, but you don't have to use a while loop to read it, and you also don't have to use the readline() function unless you just really want to.

There is another (very easy) way if all you are writing is a dictionary variable, and you don't care about any other program being able to read it.```
import shelve
dbase = shelve.open("data.shf")
``` Using the shelve module, any changes with an associate dictionary variable are automatically written to disk.  I know this goes against the spirit of what you are trying to learn, but it's something to keep in mind for future reference once you do understand file i/o.

---

### Post by christhemonkey on 2006-06-26
Thankyou both very much!


**digby**:
I shall bear that in mind.


I hope to join you all in able-to-code-python-land soon!

---

### Post by christhemonkey on 2006-06-27
Ok, i *finally* got this working!

Attached is my final copy of the program for the curious :)

Now onto how to deal with invalid user input......!


:D

---

### Post by deathbyswiftwind on 2006-06-28
Chris that is the one I am currently stuck on. Ive tried putting the try block where I believe it should go but it doesnt work. For anyone that is looking at this thats knows python please enlighten me. Ive been pondering this for 3 days now! here is the bottom part where the try block will need to go

```

phone_list = {}
menu_choice = 0
print_menu()
while menu_choice != 7:
#here is where i am putting try:
    menu_choice = input("Type in a number (1-7):")
    if menu_choice == 1:
        print_numbers(phone_list)
    elif menu_choice == 2:
        print "Add Name and Number"
        name = raw_input("Name:")
        phone = raw_input("Number:")
        add_number(phone_list,name,phone)
    elif menu_choice == 3:
        print "Remove Name and Number"
        name = raw_input("Name:")
        remove_number(phone_list,name)
    elif menu_choice == 4:
        print "Lookup Number"
        name = raw_input("Name:")
        print lookup_number(phone_list,name)
    elif menu_choice == 5:
        filename = raw_input("Filename to load:")
        load_numbers(phone_list,filename)
    elif menu_choice == 6:
        filename = raw_input("Filename to save:")
        save_numbers(phone_list,filename)
    elif menu_choice == 7:
        pass
    else:
        print_menu()
print "Goodbye"  
#here is where im putting valueError

```


and the code for the try block is

```

#this is the start of the try block for anyone who doesnt know
try:
#this is the end of the try block
except valueError
     print "That was not a valid choice"

```

I keep wanting to put it right under the while statement and from the examples it gave that appears correct but then it still fails when anything but a number is entered. Please help

---

### Post by deathbyswiftwind on 2006-06-28
Chris,

  I tried your program just for shits and giggles since mine didnt come out very pretty and I encountered a weird problem. When I add a student and try to delete a student or add a grade for that student it says the student doesnt exist. Ive tried this many times and dont know whats causing it. Do you have the same problems?

---

### Post by christhemonkey on 2006-06-28
**deathbyswiftwind**:
I have that problem when i run the program on any machine other than the one i wrote it on.
Which is strange, as the add student bit was written by the tutorial person.

(and it works fine for me on my laptop)

Also, as for the try: block thing,

for starters, dont you need a : ofter "except ValueError"?

And, i think i did something like this when doing that section:
```
phone_list = {}
menu_choice = 0
print_menu()
while menu_choice != 7:
	try:
	    menu_choice = input("Type in a number (1-7):")
	    if menu_choice == 1:
	        print_numbers(phone_list)
	    elif menu_choice == 2:
	        print "Add Name and Number"
	        name = raw_input("Name:")
	        phone = raw_input("Number:")
	        add_number(phone_list,name,phone)
	    elif menu_choice == 3:
	        print "Remove Name and Number"
	        name = raw_input("Name:")
	        remove_number(phone_list,name)
	    elif menu_choice == 4:
	        print "Lookup Number"
	        name = raw_input("Name:")
	        print lookup_number(phone_list,name)
	    elif menu_choice == 5:
	        filename = raw_input("Filename to load:")
	        load_numbers(phone_list,filename)
	    elif menu_choice == 6:
	        filename = raw_input("Filename to save:")
	        save_numbers(phone_list,filename)
	    elif menu_choice == 7:
	        pass
	    else:
	        print_menu()
	except ValueError:
	        print "That is not a valid choice"
	print "Goodbye"  

```

Maybe that works, maybe it doesnt.
Cant find the one i did yesterday which did work.:s

---

### Post by deathbyswiftwind on 2006-06-28
I tried that and it still crashes out :confused:

---

### Post by digby on 2006-06-28
Post your whole program with the try block included... it could be an indent error... what error does it raise when it crashes?

---

### Post by deathbyswiftwind on 2006-06-28
Thank you so much for your help digby 

```

import string

true = 1
false = 0

def print_numbers(numbers):
    print "Telephone Numbers:"
    for x in numbers.keys():
        print "Name: ",x," \tNumber: ",numbers[x]
    print

def add_number(numbers,name,number):
    numbers[name] = number

def lookup_number(numbers,name):
    if numbers.has_key(name):
        return "The number is "+numbers[name]
    else:
        return name+" was not found"

def remove_number(numbers,name):
    if numbers.has_key(name):
        del numbers[name]
    else:
        print name," was not found"


def load_numbers(numbers,filename):
    in_file = open(filename,"r")
    while true:
        in_line = in_file.readline()
        if in_line == "":
            break
        in_line = in_line[:-1]
        [name,number] = string.split(in_line,",")
        numbers[name] = number
    in_file.close()

def save_numbers(numbers,filename):
    out_file = open(filename,"w")
    for x in numbers.keys():
        out_file.write(x+","+numbers[x]+"\n")
    out_file.close()
    

def print_menu():
    print '1. Print Phone Numbers'
    print '2. Add a Phone Number'
    print '3. Remove a Phone Number'
    print '4. Lookup a Phone Number'
    print '5. Load numbers'
    print '6. Save numbers'
    print '7. Quit'
    print
phone_list = {}
menu_choice = 0
print_menu()
while menu_choice != 7:
    try:
        menu_choice = input("Type in a number (1-7): ")
        if menu_choice == 1:
            print_numbers(phone_list)
        elif menu_choice == 2:
            print "Add Name and Number"
            name = raw_input("Name: ")
            phone = raw_input("Number: ")
            add_number(phone_list,name,phone)
        elif menu_choice == 3:
            print "Remove Name and Number"
            name = raw_input("Name: ")
            remove_number(phone_list,name)
        elif menu_choice == 4:
            print "Lookup Number"
            name = raw_input("Name: ")
            print lookup_number(phone_list,name)
        elif menu_choice == 5:
            filename = raw_input("Filename to load: ")
            load_numbers(phone_list,filename)
        elif menu_choice == 6:
            filename = raw_input("Filename to save: ")
            save_numbers(phone_list,filename)
        elif menu_choice == 7:
            pass
        else:
            print_menu()
    except Errorvalue:
        print "That was not a valid choice"
print "Goodbye"  


```

Everything runs fine its just if you enter any letter,symbol,etc instead of a number it still crashed out with an Errorvalue

---

### Post by digby on 2006-06-28
Ahh... you have this:```
except Errorvalue:
```And you need this:```
except NameError:
```If you look at the error generated when it crashes, it should say something like```
Traceback (most recent call last):
  File "/home/matt/project/temp.py", line 86, in ?
    except Errorvalue:
NameError: name 'Errorvalue' is not defined
``` The part before the ':' on the last line is the type of error being raised.  That's what you need to catch with your except statment.

'Errorvalue' is not (to the best of my knowledge) a valid python error type.  Thus, it doesn't know what to do with that and aborts.

---

### Post by deathbyswiftwind on 2006-06-28
wow now if i dont feel like a donkeys a$$  #-o  i guess i wasnt reading it close enough i just saw 

```

print "Type Control C or -1 to exit"
number = 1
while number != -1:
    try:
        number = int(raw_input("Enter a number: "))
        print "You entered: ",number
    except ValueError:
        print "That was not a number."

```

and thats what confused me

thanks for the help

---

### Post by digby on 2006-06-29
[quote=deathbyswiftwind]wow now if i dont feel like a donkeys a$$  #-o  i guess i wasnt reading it close enough 
thanks for the help[/quote]

Heh... I've made more obvious errors than that...  don't sweat it.  At the rate you're learning, I'll probably be asking you questions before too long.

---

