---
title: "My Distro Chooser [Python]"
date: 2007-07-31
forum: Programming Talk
---

### Post by Sayers on 2007-07-31
Please help me work on my code. 

```
print "Welcome to Distro Chooser 0.01"
print " "

##Here we set up the Distrubution Choices. Since we use numbers + / - to choose which is best the distros must be variables.
#ubuntu
ubuntu = 0
#gentoo
gentoo = 0
#debian
debian = 0

## Lets start the questions

##question 1
print "What do you use your computer for?"
print "Desktop [Non-Programming] (1)"
print "Desktop Programming (2)"
print "Server (3)"
print " "
qone = raw_input("Pick a number:")
if qone == 1: # Non-Desktop
	ubuntu += 5 #Makes a wonderfuly easy desktop
	gentoo += 1 #Gentoo is good but very hard to setup.
	debian += 3 #Easier to setup then Gentoo

if qone == 2:
	ubuntu += 2 #Ubuntu is good for programming. 
	gentoo += 4 #Gentoo lets you compile all the packages which is great for Developers
	debian += 3 #Debian is good for programming. 

if qone == 3:
	ubuntu += 1 # Ubuntu makes great servers for newbs, but most people who assemble servers know what they're doing.
	gentoo += 3 #Gentoo makes a decent server. Fast.
	debian += 5 #Debian is best known for it's server abbility
## Question 2
print " "
print "What is your knowledge of linux?"
print "Very Low / None (1)"
print "Medium (2)"
print "I know A LOT about linux (3)"
print " "
qtwo = input("Pick a number:")
if qtwo == 1:
	ubuntu += 5 #ubuntu is super easy!
	gentoo -= 3 #I subtract 3, Gentoo is impossible for a newbie.
	# I ignore debian, it isn't hard but it deffentily isn't easy.
if qtwo == 2:
	ubuntu += 3 # It's good for medium skill users but some will find it lacking the abbilityu to customize.
	gentoo += 2 # It is hard to use
	debian += 3 # easy to use easy to customize
if qtwo == 3:
	ubuntu += 1
	gentoo += 7 # any real hard-core linux user will love Gentoo
	debian += 4 # Very good. 
```

---

### Post by earobinson on 2007-07-31
> ubuntu += 2 #Ubuntu is good for programming. 
gentoo += 4 #Gentoo lets you compile all the packages which is great for Developers
debian += 3 #Debian is good for programming.  Im not sure about your comments here you can compile on ubuntu also? I know gentoo makes you compile a lot more but I dont see how that makes it better for devs

---

### Post by Sayers on 2007-07-31
Well I added that because you can customize the dev packages :)

---

### Post by tht00 on 2007-07-31
For programming practice, this looks useful.  As I learned to program, I mostly did exercises that were mostly useless in the real world.

As an actual 'distro chooser', there are a lot more things to consider as well as a lot more options to look at.  Just a heads up there.

---

### Post by Sayers on 2007-07-31
> **tht00 said:**
> For programming practice, this looks useful.  As I learned to program, I mostly did exercises that were mostly useless in the real world.

As an actual 'distro chooser', there are a lot more things to consider as well as a lot more options to look at.  Just a heads up there.

Well that's why it's open-source and I need help finishing :)

---

### Post by Sayers on 2007-07-31
> **tht00 said:**
> For programming practice, this looks useful.  As I learned to program, I mostly did exercises that were mostly useless in the real world.

As an actual 'distro chooser', there are a lot more things to consider as well as a lot more options to look at.  Just a heads up there.

Oh and, most things to program are already made :-) , it's called either redoing it better or going crazy :p

---

### Post by smartbei on 2007-07-31
I would recommend you structure the program differently, seeing as the way it currently is (while being very readable) is very long. Something like this:
```

print "Welcome to Distro Chooser 0.01"
distros=("ubuntu","gentoo","debian")
score=[0,0,0]
questions=["What do you use your computer for?\nDesktop Programming (2)\nServer (3)","What is your knowledge of linux?\nVery Low / None (1)\nMedium (2)\nI know A LOT about linux (3)"]
questions_effect=(((5,1,3),(2,4,3),(1,3,5)),((5,-3,0),(3,2,3),(1,7,4)))
for q in range(len(questions)):
	print questions[q]
	qres = int(raw_input("Pick a number: "))
	for s in range(len(distros)):
		score[s]+=questions_effect[q][qres-1][s]
for a in range(len(distros)):
	print distros[a],score[a]

```
Does the exact same thing but is much shorter...

Heh, now we are going to have a perl guy come in and do it in a single line :D.

---

### Post by Sayers on 2007-07-31
That looks like great code however, It is a little beyond my range of python at the moment.

---

### Post by smartbei on 2007-07-31
It just looks complicated - once you break it into pieces, it is very simple. 
```

print "Welcome to Distro Chooser 0.01"

## These are startup values - getting everything ready:
 # a tuple holding the names of the distros:
distros=("ubuntu","gentoo","debian")

# a list that holds the calculated score:
score=[0,0,0] 

#This is a tuple, holding a tuple for each question, with each of this holding a tuple for the effect of each number on each distro.
#                   (questions_effect)
#                  _________|_____________
#                 |                       |
#         (question 1)            (question 2)
#    ______|_______        ________|________
#   |      |       |      |        |        |
#(u,g,d) (u,g,d) (u,g,d) (u,g,d) (u,g,d) (u,g,d)
# (u,g,d) = the respective effects on (ubuntu, gentoo, debian)
questions_effect=(((5,1,3),(2,4,3),(1,3,5)),((5,-3,0),(3,2,3),(1,7,4)))

#the questions themselves - note that this is exactly what you wrote, except that instead of being on seperate print statements, the strings are put together into a single entry on a list - just for simplicity.
questions=["What do you use your computer for?\nDesktop Programming (2)\nServer (3)","What is your knowledge of linux?\nVery Low / None (1)\nMedium (2)\nI know A LOT about linux (3)"] 

#loops through the questions, asks each in turn and receives back user input.
for q in range(len(questions)):
	print questions[q]
	qres = int(raw_input("Pick a number: "))

	#loops through the correct effect on the distro's score based on the user's answer:
	for s in range(len(distros)):
		score[s]+=questions_effect[q][qres-1][s]

#prints it all out:
for a in range(len(distros)):
	print distros[a],score[a]

```

I hope that makes it clearer - sorry if I went too far, too fast.

---

### Post by pmasiar on 2007-07-31
> **Sayers said:**
> That looks like great code however, It is a little beyond my range of python at the moment.

[Virtues of good programmer](http://www.hhhh.org/wiml/virtues.html) are: Laziness, Impatience, and Hubris (all not in raw form, but properly seasoned).

smartbei was too lazy to write much code: he wrote data structure and code to interpret it instead. Impatience can be used to change it (just change data), Hubris is to think beginner can digest it :-)

---

### Post by smartbei on 2007-08-01
Haha, thanks for the implicit compliment :p.

---

### Post by engla on 2007-08-01
Python triple-quotes can also make that a bit more readable
```
questions=[
"""What do you use your computer for?
Desktop [Non-Programming] (1)
Desktop Programming (2)
Server (3)""",
"""What is your knowledge of linux?
Very Low / None (1)
Medium (2)
I know A LOT about linux (3)"""
]
```

---

