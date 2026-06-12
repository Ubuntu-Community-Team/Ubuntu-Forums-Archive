---
title: "Python Help Please"
date: 2007-04-17
forum: Programming Talk
---

### Post by deathbyswiftwind on 2007-04-17
Okay here is my problem. Im writting a program ( a very simple one at that) which will output text for me to enter into text files so i can run them as scripts for forceclassing weapons on players in americas army. here is my source

```

# The intent of this program is to create forceclass scripts for americas army.
a = 0
b = 1000
c = 0
weapon = 0
weapons = []
TotalWeaponChoices = 0

num = input("Please enter how many different weapon classes you would like (1 - 21): ")

am = raw_input("Please enter an admin message if you want: ")

while TotalWeaponChoices != num:
    weapons.insert(c,raw_input("Please enter the weapons class: "))
    TotalWeaponChoices = TotalWeaponChoices + 1
    c = c + 1

print " "

while a != b:
    a = a +1
    print "admin forceclass", a , weapons[weapon]
    weapon = weapon + 1    

print "admin message", am    

```

It does want I want to some extent. It needs to class up to 1000. If the user enters he only wants 15 choices  it does this 

```

Please enter how many different weapon classes you would like (1 - 21): 15
Please enter an admin message if you want: jhfdjhfsd
Please enter the weapons class: a
Please enter the weapons class: b
Please enter the weapons class: c
Please enter the weapons class: d
Please enter the weapons class: e
Please enter the weapons class: f
Please enter the weapons class: g
Please enter the weapons class: h
Please enter the weapons class: i
Please enter the weapons class: j
Please enter the weapons class: k
Please enter the weapons class: l
Please enter the weapons class: m
Please enter the weapons class: n
Please enter the weapons class: o
 
admin forceclass 1 a
admin forceclass 2 b
admin forceclass 3 c
admin forceclass 4 d
admin forceclass 5 e
admin forceclass 6 f
admin forceclass 7 g
admin forceclass 8 h
admin forceclass 9 i
admin forceclass 10 j
admin forceclass 11 k
admin forceclass 12 l
admin forceclass 13 m
admin forceclass 14 n
admin forceclass 15 o
admin forceclass 16
Traceback (most recent call last):
  File "/home/rob/aaforceclasssscriptor.py", line 22, in <module>
    print "admin forceclass", a , weapons[weapon]
IndexError: list index out of range

```

Now please dont make fun of me Im a very big noob at programming and all I did was take a tutorial on python programming on the web. I think Im doing pretty good and I hope at least someone agrees.

Now I know I need to make something in the 

```


while a != b:
    a = a +1
    print "admin forceclass", a , weapons[weapon]
    weapon = weapon + 1 

```

part but I dont know what. I tried doing

```


while a != b:
    a = a +1
    print "admin forceclass", a , weapons[weapon]
    weapon = weapon + 1 
    if d == num:
    d == 0


```

But with no help. Once it reaches the user specified number it still crashes out.  PLEASE HELP!

---

### Post by WW on 2007-04-17
The problems is your second loop goes up to 1000, but you have only defined entries 0 to num-1 in the weapons array.  As soon as you try to print weapons[weapon] when weapon=num, you get an error.

The second loop should iterate as many times as there are weapons defined. You can fix your program by changing the line
```

while a != b:

```
to
```

while a != len(weapons):

```
or
```

while a != num:

```

---

### Post by deathbyswiftwind on 2007-04-17
Thanks you for your quick responce. One thing though. I need it to loop until it prints out to 1000. The game auto assigns players a number 1 to 1000. So when you look at playerlist it reads like 

jerk 1
dork 15
butthead 252
loser 52

and so forth.

Its dumb the way aa adds the player slot number to the player

Do you understand what I mean though? I know its confusing I just dont know how to word it right.

What I need it to do it
 Assign weapons to playerslots 1 to 1000

Once it goes through the weapons list I need it to loop back through the weapons list until it finally gets to player slot 1000

---

### Post by Buffalo Soldier on 2007-04-17
```
#!/usr/bin/env python
weapons = []
num = int(raw_input("Please enter how many different weapon classes you would like (1 - 21): "))

am = raw_input("Please enter an admin message if you want: ")

while len(weapons) < num:
    weapons.append(raw_input("Please enter the weapons class: "))

print

for x in range(1000):
    if x < len(weapons):
        print "admin forceclass", x + 1 , weapons[x]
    else:
        print "admin forceclass", x + 1 , "none"
    
print "admin message", am
```
That will continue printing out until forceclass 1000, Hope that's what you're looking for.

---

### Post by deathbyswiftwind on 2007-04-17
well thats closer except when it loops through instead of printing none I would like it to go back through the weapons list

so like if the user defines

[code]

weapons = [ 'r' , 'rpg' , 'rpk' , 'g' ]

it would then be like

admin forceclass 1 r
admin forceclass 2 rpg
admin forceclass 3 rpk
admin forceclass 4 g
admin forceclass 5 r
admin forceclass 6 rpg
admin forceclass 7 rpk
admin forceclass 8 g
admin forceclass 9 r
admin forceclass 10 rpg
admin forceclass 11 rpk
admin forceclass 12 g

all the way to 1000

---

### Post by Buffalo Soldier on 2007-04-17
```
weapons = []
num = int(raw_input("Please enter how many different weapon classes you would like (1 - 21): "))

am = raw_input("Please enter an admin message if you want: ")

while len(weapons) < num:
    weapons.append(raw_input("Please enter the weapons class: "))

print

[color=blue]for x in range(0, 1000, num):
    for y in range(num):
        if x + y < 1000:
            print "admin forceclass", x + y + 1,  weapons[y][/color]
    
print "admin message", am
```
Changes in blue. Not an elegant code. I'm sure someone here can show you a more "pythonic" code.

---

### Post by WW on 2007-04-18
A bit simpler:
```

weapons = []
num = int(raw_input("Please enter how many different weapon classes you would like (1 - 21): "))

am = raw_input("Please enter an admin message if you want: ")

while len(weapons) < num:
    weapons.append(raw_input("Please enter the weapons class: "))

print
[color=blue]
for x in range(1000):
    print "admin forceclass", x + 1,  weapons[x % num]
 [/color] 
print "admin message", am

```

---

### Post by deathbyswiftwind on 2007-04-18
Wow I was incredibly off :(

Thanks so much guys for all your help. One thing Im confused on though is what does the % symbol do in python?

I would also like to know something. Using if and maybe elif could I have made my while loop for the printing work? You know with something like

```

while a != b:
    a = a +1
    print "admin forceclass", a , weapons[weapon]
    if weapon != num:
        weapon = weapon + 1
    elif weapon == num
        weapon == 0

```

I will definatly be using the code I got from here but I am just still curious if there was ANYWAY i could have tinkered enough to end up getting it to work witht he way I was doing it

Also wondering is there a way to make it dump the  admin forceclass yada yada and admin message out to a text file? I know python can make,save,edit and what not.

---

### Post by Dancingwllamas on 2007-04-18
The % symbol is called Modulus. It returns the remainder of division (ie: 4%3 is 1, 5%3 is 2, etc).

---

### Post by deathbyswiftwind on 2007-04-22
Alright Im getting kinda frustrated (yet again) and would like some help. I am trying to make this program write to a text file. Ive been reading up on it but cant find an answer to my question. The problem is when I try to have it write using the 

print "admin message", x + 1 , weapons[x % num]
 
it tells me it has to be a string and not a tuple. So I get that part. But how do I make the output read as a string now? When it prints out its in perfect string forum I just dont know how to get it to write out.

---

### Post by rks_i1_13 on 2007-04-22
Hi, your method using if...elif is perfectly good except what i mentioned here using comments :-
```

elif weapon==num  #error, you forgot ':'
     weapon == 0  #error, you should use '='

```

and, btw if you want to write it into a file then do the following :-
```

aFile = open("filename.txt","w")
#your loop commands here :
     aFile.write("\n"+"admin forceclass"+str(a)+str(weapons[weapon]))

```

---

### Post by deathbyswiftwind on 2007-04-24
Sweet thanks alot man that worked! I had my buddy finish helping me.

```

#!/usr/bin/env python
print "Welcome to =JKL='s AA Froceclass Scipt Maker"
print
str3 = ".txt"
scrName = raw_input("Please choose your script name: ")
f=open(scrName +str3, 'w')
print
num = int(input("Please enter how many different weapon classes you would like (1 - 21): "))
weapons = []
print
am = raw_input("Please enter an admin message if you want: ")
print
while len(weapons) < num:
    weapons.append(raw_input("Please enter the weapons class: "))
for x in range(1000):
	x = x + 1
	prMSG = "admin forceclass " + str(x) + " " + weapons[x % num] + "\n"
	f.write(prMSG)
adMSG =  "admin message " + str(am)
f.write(adMSG)
f.close()

```

---

