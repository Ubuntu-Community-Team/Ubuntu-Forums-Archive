---
title: "Python help please"
date: 2012-09-16
forum: Programming Talk
---

### Post by EnexOD on 2012-09-16
I'm getting weird syntax's like
print ""
Syntax Error: invalid syntax

also getting

time.sleep(1)
Syntax Error: invalid syntax

elif skill==2:
Syntax Error: invalid syntax

```
#Another version of the "adventure game"
#September 14, 2012

import random, os, time, string
os.system("color 1C")  # green(2) text on white(F) background

#Warrior Class
wHP=random.randint(350,500)
wATT=random.randint(50,70)
wmagic=random.randint(5,15)
SDran=random.randint(2,4)
#Warrior Skills
BS=60
SS=65
SD=35 #Random number of slices (2-4)
ES=55

#Mage Class
mHP=random.randint(250,400)
mATT=random.randint(5,15)
mMAGIC=random.randint(65,90)
#Mage Skills
FP=55
P=70
WB=40
TS=65


#Monster Stats
xHP=random.randint(600,1000)
xATT=random.randint(30,50)


#while xHP>0:
cla=input("Choose a CLASS \n1.Mage \n2.Warrior \n:: ")
if cla==1:
	raw_input("")
	os.system("cls")
	print "You chose the Mage class, your stats are: \nHP="+str(mHP)+"\nATT="+str(mATT)+"\nMAGIC="+str(mMAGIC)
	raw_input("")
	os.system("cls")
     
while (xHP>0):
	skill=input("Select a skill \n1.Fire Punch \n2.Psychic \n3.Water Blast \n4.Thunder Slam \n:: ")     
	if skill==1:
		xHP -= (mMAGIC+FP)
		mMAGIC=random.randint(65,90)
		print ""
		print "You used Fire Punch, you did: "+str(mMAGIC+FP)+" magic damage."
		time.sleep(1)
		xHP=xHP-(mMAGIC+FP)
		print "The monsters hp is now: "+str(xHP-(mMAGIC+FP)
		time.sleep(1)
		print ""	 
	if skill==2:
		xHP -=(mMAGIC+P)
		mMAGIC=random.randint(65,90)
		print ("")
		print "You used Psychic, you did: "+str(mMAGIC+P)+" magic damage."
		#time.sleep(1)
		print "The monsters hp is now: "+str(xHP-(mMAGIC+P))
		#time.sleep(1)
		print ""
	if skill==3:
		xHP -= (mMAGIC+WB)
		mMAGIC=random.randint(65,90)
		print ""
		print "You used Water Blast, you did: "+str(mMAGIC+WB)+" magic damage."
		time.sleep(1)
		print "The monsters hp is now: "+str(xHP-(mMAGIC+WB))
		time.sleep(1)
		print ""
	if skill==4:
		xHP -= (mMAGIC+TS)
		mMAGIC=random.randint(65,90)
		print ""
		print "You used Thunder Slam, you did: "+str(mMAGIC+TS)+" magic damage."
		time.sleep(1)
		print "The monsters hp is now: "+str(xHP-(mMAGIC+TS))
		time.sleep(1)
		print ""
	if xHP>0:
		xATT=random.randint(30,50)
		mHP=(mHP-xATT)
		print "The monster attacked! He did: "+str(xATT)+" attack damage."
		print "Your hp is now "+str(mHP)+"."
		time.sleep(1)
		print ""
	
	if xHP<=0:
		print "You have successfully killed the monster, congratualations.."
		print time.sleep(2)
		print "Game over."
		print time.sleep(1)
		os.system("cls")
		print string.center("******************************",50)
		print string.center("******************************",50)
		print string.center("This game was created by Kevin Kim",50)
		print string.center("******************************",50)
		print string.center("******************************",50)
	
	if mHP<=0:
		print "The monster killed you....."
		print ".........."
		time.sleep(2)
		print "You have been slayed... Game over."
		break
          
if cla==2:
     raw_input("")
     os.system("cls")
     print "You chose the Warrior class, your stats are: \nHP="+str(wHP)+"\nATT="+str(wATT)+"\nMAGIC="+str(wMAGIC)
     raw_input("")
     os.system("cls")
     skill=input("Select a skill \n1.Body Slam \n2.Sword Strike \n3.Heal \n4.Earth Strike \n:: ")
	


```

---

### Post by Bachstelze on 2012-09-16
Use CODE tags, not QUOTE, as QUOTE does not preserve indentation.

---

### Post by EnexOD on 2012-09-16
There, fixed it 
thanks

---

### Post by micahpage on 2012-09-16
missing paren on line 52
```
str(xHP-(mMAGIC+FP)
```

---

### Post by EnexOD on 2012-09-16
Man... that one bracket fixed it.
thank you!!!

---

### Post by micahpage on 2012-09-16
np

normally if you get a syntax error, the reason for it is the line above the error you get.

---

### Post by EnexOD on 2012-09-16
okay, I'll keep that in mind.
new to python, trying to learn the basics of programming before I go to university

---

### Post by micahpage on 2012-09-16
you should also use elif for more than one if condition, if elif elif instead of if if if

use input() for python3.x and raw_input() for python2.x

you should also learn functions and classes as if you copy/paste a line it means you are doing something wrong.
for example:
this line is the same with a minor difference
```
print "The monsters hp is now: "+str(xHP-(mMAGIC+XX))
```
where XX is the only thing being changed

---

### Post by EnexOD on 2012-09-16
> **micahpage said:**
> you should also use elif for more than one if condition, if elif elif instead of if if if

yeah I usually do that but I was playing around with it during the syntax error. I was getting really frustrated because it said "elif skill==1: Syntax error"

---

