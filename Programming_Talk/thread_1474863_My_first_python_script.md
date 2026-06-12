---
title: "My first python script :/"
date: 2010-05-06
forum: Programming Talk
---

### Post by makuab on 2010-05-06
I've attatched the script, it calculates runescape max hit (it was too big to paste it all)  i took all of the formulas from this page [http://runescape.wikia.com/wiki/Maximum_melee_hit](http://runescape.wikia.com/wiki/Maximum_melee_hit)  and this is a max hit calc by someone else, sadly the numbers dont match with the same settings [http://www.scape-xp.com/runescape-max-hit-calculator.html](http://www.scape-xp.com/runescape-max-hit-calculator.html)  and here is another [http://runehq.com/guide.php?type=calculator&id=0712](http://runehq.com/guide.php?type=calculator&id=0712)

---

### Post by hawaiian1der on 2010-05-06
It's all good, but I like capital letters at the beginning of my sentences :P Thats just me though.

---

### Post by makuab on 2010-05-06
> **hawaiian1der said:**
> It's all good, but I like capital letters at the beginning of my sentences :P Thats just me though.
I have a problem though.. D:

---

### Post by Tony Flury on 2010-05-06
It works - which has to be the first rule of any application, but you are not making best use of python and its abilities.

I have done a rewrite - attached - see how smaller it is ? if you look at your code - you have a very common theme - a load of prompts then a set of if statement, with calculations all of which are similar (apart from some constants).

So what i have done is write a simple function that takes a list of prompts and returns the constants, and all the main program does is use those constants in a single calculation.

```

def calcModifier( prompt, optionlist ):
    # each entry in the optionlist is a tuple -
    # entry 0 is the prompt, entry 1 is the constants to be used in the calculation 
    print 
    for entry in optionlist: print entry[0]
    print
    i = input( prompt )
    return optionlist[i][1]

#STRENGTH CALCULATOR BY MAKUA

strength = input("what is your strength level? ")
#dragon bax special

print
print ("press 1 for yes 2 for no")
print
bax = input("are you using the dragon battle axe special? ")
#dragon bax formula
if bax == 1:
	potbon = strength + 9 * .02
else:
	pass

#which strength potion?	
ops = [("Press 1 for normal", (.1, 3) ), ("Press 2 for super", (.15, 5)), ("Press 3 for extreme",(.22, 5)),("Press 4 for zamorak brew", (.12, 2)), ("Press 5 for none", (0,0))]
mod = calcModifier( "which strength potion will you use? ", ops)
potbon = strength * mod[0] + mod[1]

#which prayer?
ops = [(("Press 1 for burst of strength"), 1.05), (("Press 2 for superhuman strength"), 1.1), (("Press 3 for ultimate strength"), 1.15), (("Press 4 for chivalry"), 1.18), (("Press 5 for piety"), 1.23), (("Press 6 for none"), 1)]
praybon = calcModifier("which prayer will you use? ", ops)

# armour
ops = [("Press 1 for void melee armor", 1.2), ("Press 2 for black mask", 1.15), ("press 3 for salve amulet",1.15), ("press 4 for salve amulet (e)", 1.2), ("press 5 for none", 1)]
obon = calcModifier("other items? ", ops)

# style
ops = [("press 1 for aggressive",3), ("press 2 for controlled",1), ("press 3 for accurate/defensive",0)]
stylbon = calcModifier("which attack style? ", ops)

effectstr = strength + potbon * praybon * obon + stylbon
print
strbon = input("what is your strength bonus? ")
print
bdam = 13 + effectstr + strbon / 8 + effectstr * strbon / 64

print ("your max hit is"), bdam

```

---

### Post by makuab on 2010-05-06
> **Tony Flury said:**
> It works - which has to be the first rule of any application, but you are not making best use of python and its abilities.

I have done a rewrite - attached - see how smaller it is ? if you look at your code - you have a very common theme - a load of prompts then a set of if statement, with calculations all of which are similar (apart from some constants).

So what i have done is write a simple function that takes a list of prompts and returns the constants, and all the main program does is use those constants in a single calculation.

```

def calcModifier( prompt, optionlist ):
    # each entry in the optionlist is a tuple -
    # entry 0 is the prompt, entry 1 is the constants to be used in the calculation 
    print 
    for entry in optionlist: print entry[0]
    print
    i = input( prompt )
    return optionlist[i][1]

#STRENGTH CALCULATOR BY MAKUA

strength = input("what is your strength level? ")
#dragon bax special

print
print ("press 1 for yes 2 for no")
print
bax = input("are you using the dragon battle axe special? ")
#dragon bax formula
if bax == 1:
    potbon = strength + 9 * .02
else:
    pass

#which strength potion?    
ops = [("Press 1 for normal", (.1, 3) ), ("Press 2 for super", (.15, 5)), ("Press 3 for extreme",(.22, 5)),("Press 4 for zamorak brew", (.12, 2)), ("Press 5 for none", (0,0))]
mod = calcModifier( "which strength potion will you use? ", ops)
potbon = strength * mod[0] + mod[1]

#which prayer?
ops = [(("Press 1 for burst of strength"), 1.05), (("Press 2 for superhuman strength"), 1.1), (("Press 3 for ultimate strength"), 1.15), (("Press 4 for chivalry"), 1.18), (("Press 5 for piety"), 1.23), (("Press 6 for none"), 1)]
praybon = calcModifier("which prayer will you use? ", ops)

# armour
ops = [("Press 1 for void melee armor", 1.2), ("Press 2 for black mask", 1.15), ("press 3 for salve amulet",1.15), ("press 4 for salve amulet (e)", 1.2), ("press 5 for none", 1)]
obon = calcModifier("other items? ", ops)

# style
ops = [("press 1 for aggressive",3), ("press 2 for controlled",1), ("press 3 for accurate/defensive",0)]
stylbon = calcModifier("which attack style? ", ops)

effectstr = strength + potbon * praybon * obon + stylbon
print
strbon = input("what is your strength bonus? ")
print
bdam = 13 + effectstr + strbon / 8 + effectstr * strbon / 64

print ("your max hit is"), bdam

```

look at this and you'll know why i didnt :(
[http://ubuntuforums.org/showthread.php?t=1473065&page=2](http://ubuntuforums.org/showthread.php?t=1473065&page=2)


also i got an error with your script.

---

### Post by Tony Flury on 2010-05-06
I have been reading that other thread - and i thought you had got the hang of functions - the function is just a short hand - you could use the same list techniques without functions if you wanted, but you would have a lot of code that looks the same.

The error you got maybe due to the fact you are using python 3 

in which case :

```

replace 

for entry in optionlist: print entry[0]

with 

for entry in optionlist: print( entry[0] )

```

sorry - I am still using python 2.6 - which does not need the brackets on print.

---

### Post by makuab on 2010-05-06
> **Tony Flury said:**
> I have been reading that other thread - and i thought you had got the hang of functions - the function is just a short hand - you could use the same list techniques without functions if you wanted, but you would have a lot of code that looks the same.

The error you got maybe due to the fact you are using python 3 

in which case :

```

replace 

for entry in optionlist: print entry[0]

with 

for entry in optionlist: print( entry[0] )

```sorry - I am still using python 2.6 - which does not need the brackets on print.
lol i dont feel like i really understand them

---

