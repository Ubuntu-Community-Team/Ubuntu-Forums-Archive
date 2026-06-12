---
title: "noob python problem"
date: 2009-07-17
forum: Programming Talk
---

### Post by insanecrazy4 on 2009-07-17
so to improve myself to programming in python i have decided to take other peoples ideas and make my own solution. the temperature conversion script that i wrote works for many different temps. but it wont print out any answers and it doesnt handle negative integers. the code is not completed and can certanly be shortened but i want to figure out my problems before i make it better.

[PHP]#!/usr/local/bin/python
import math

temp1 = 0
conversion = 0
choice = ''

def kelvin_to_celsius(temp1):
	conversion = temp1 - 273.15
	print choice, '=' , conversion
def kelvin_to_Fahrenheit(temp1):
	conversion = (temp1 * 9/5 - 459.67)
	print choice, '=', conversion
def kelvin_to_Rankine(temp1):
	conversion = temp1 * 9/5
	print choice, '=', conversion
def kelvin_to_Delisle(temp1):
	conversion = (373.15 - temp1) * 3/2
	print choice, '=', conversion
def kelvin_to_Newton(temp1):
	conversion = (temp1 - 273.15) * 33/100
	print choice, '=', conversion
def kelvin_to_Reaumur(temp1):
	conversion = (temp1 - 273.15) * 4/5
	print choice, '=', conversion
def kelvin_to_Romer(temp1):
	conversion = (temp1 - 273.15) * 21/40 + 7.5
	print choice, '=', conversion
#celsius conversions not yet completed
def celsius_to_Fahrenheit(temp1):
	conversion = temp1 * 9/5 + 32
	print choice, '=', conversion
def celsius_to_Kelvin(temp1):
	conversion = temp1 + 273.15
	print choice, '=', conversion
def celsius_to_Rankine(temp1):
	conversion = (temp1 + 273.15) * 9/5
	print choice, '=', conversion
def celsius_to_Delisle(temp1):
	conversion = (100 - [temp1]) * 3/2
	print choice, '=', conversion
def celsius_to_Newton(temp1):
	conversion = temp1 * 33/100
	print choice, '=', conversion
def celsius_to_Reaumur(temp1):
	conversion = temp1 * 4/5
	print choice, '=', conversion
def celsius_to_Romer(temp1):
	conversion = temp1 * 21/40 + 7.5
	print choice, '=', conversion
#Rankine conversion not yet completed
def ranking_to_Celsius(temp1):
	conversion = (temp1 - 491.67) * 5/9
	print choice, '=', conversion
def ranking_to_Fahrenheit(temp1):
	conversion = temp1 - 459.67
	print choice, '=', conversion	
def ranking_to_kelvin(temp1):
	conversion = temp1 * 5/9
	print choice, '=', conversion
def ranking_to_Delisle(temp1):
	conversion = (671.67 - temp1) * 5/6
	print choice, '=', conversion
def ranking_to_Newton(temp1):
	conversion = (temp1 - 491.67) * 11/60
	print choice, '=', conversion
def ranking_to_Reaumur(temp1):
	conversion = (temp1 - 491.67) * 4/9
	print choice, '=', conversion
def ranking_to_Romer(temp1):
	conversion = (temp1 - 491.67) * 7/24 + 7.5
	print choice, '=', conversion
#delsile conversion not yet completed
def delsile_to_Celsius(temp1):
	conversion = 100 - temp1 * 2/3
	print choice, '=', conversion
def delsile_to_Fahrenheit(temp1):
	conversion = 212 - temp1 * 6/5
	print choice, '=', conversion
def delsile_to_Kelvin(temp1):
	conversion = 373.15 - temp1 * 2/3
	print choice, '=', conversion
def delsile_to_Rankine(temp1):
	conversion = 671.67 - temp1 * 6/5
	print choice, '=', conversion
def delsile_to_Newton(temp1):
	conversion = 33 - temp1 * 11/50
	print choice, '=', conversion
def delsile_to_Reaumur(temp1):
	conversion = 80 - temp1 * 8/15
	print choice, '=', conversion
def delsile_to_Romer(temp1):
	conversion = 60 - temp1 * 7/20
	print choice, '=', conversion
#newton conversion not yet completed
def newton_to_Celsius(temp1):
	conversion = temp1 * 100/33
	print choice, '=', conversion
def newton_to_Fahrenheit(temp1):
	conversion = temp1 * 60/11 + 32
	print choice, '=', conversion
def newton_to_Kelvin(temp1):
	conversion = temp1 * 100/33 + 273.15
	print choice, '=', conversion
def newton_to_Rankine(temp1):
	conversion = temp1 * 60/11 + 491.67
	print choice, '=', conversion
def newton_to_Delisle(temp1):
	conversion = (33 - temp1) * 50/11
	print choice, '=', conversion	
def newton_to_Reaumur(temp1):
	conversion = temp1 * 80/33
	print choice, '=', conversion
def newton_to_Romer(temp1):
	conversion = temp1 * 35/22 + 7.5
	print choice, '=', conversion
#Reaumur conversion not yet completed
def reaumur_to_Celsius(temp1):
	conversion = temp1 * 5/4
	print choice, '=', conversion
def reaumur_to_Fahrenheit(temp1):
	conversion = temp1 * 9/4 + 32
	print choice, '=', conversion
def reaumur_to_Kelvin(temp1):
	conversion = temp1 * 5/4 + 273.15
	print choice, '=', conversion
def reaumur_to_Rankine(temp1):
	conversion = temp1 * 9/4 + 491.67
	print choice, '=', conversion
def reaumur_to_Delisle(temp1):
	conversion = (80 - temp1) * 15/8
	print choice, '=', conversion
def reaumur_to_Newton(temp1):
	conversion = temp1 * 33/80
	print choice, '=', conversion
def reaumur_to_Romer(temp1):
	conversion = temp1 * 21/32 + 7.5
	print choice, '=', conversion
#romer conversion not yet completed
def romer_to_Celsius(temp1): 	
	conversion = (temp1 - 7.5) * 40/21
	print choice, '=', conversion
def romer_to_Fahrenheit(temp1):
	conversion = (temp1 - 7.5) * 24/7 + 32
	print choice, '=', conversion
def romer_to_Kelvin(temp1):
	conversion = (temp1 - 7.5) * 40/21 + 273.15
	print choice, '=', conversion
def romer_to_Rankine(temp1):
	conversion = (temp1 - 7.5) * 24/7 + 491.67
	print choice, '=', conversion
def romer_to_Delisle(temp1):
	conversion = (60 - temp1) * 20/7
	print choice, '=', conversion
def romer_to_Newton(temp1):
	conversion = (temp1 - 7.5) * 22/35
	print choice, '=', conversion
def romer_to_Reaumur(temp1):
	conversion = (temp1 - 7.5) * 32/21
	print choice, '=', conversion
#Fahrenheit
def Fahrenheit_to_Celsius(temp1):
	conversion = (temp1 - 32) * 5/9
	print choice, '=', conversion
def Fahrenheit_to_Kelvin(temp1):
	conversion = (temp1 + 459.67) * 5/9
	print choice, '=', conversion
def Fahrenheit_to_Rankine(temp1):
	conversion = temp1 + 459.67
	print choice, '=', conversion
def Fahrenheit_to_Delisle(temp1):
	conversion = (212 - temp1) * 5/6
	print choice, '=', conversion
def Fahrenheit_to_Newton(temp1):
	conversion = (temp1 - 32) * 11/60
	print choice, '=', conversion
def Fahrenheit_to_Reaumur(temp1):
	conversion = (temp1 - 32) * 4/9
	print choice, '=', conversion
def Fahrenheit_to_Romer(temp1):
	conversion = (temp1 - 32) * 7/24 + 7.5
	print choice, '=', conversion
#prints out choices
print 'Temperature Conversion. Type in your selected temperature conversion acording to synta*.'
print 'Kelvin to (Celsius,Fahrenheit,Rankine,Delisle,Newton,Reaumur,Romer)'
print 'Celsius to (Kelvin,Fahrenheit,Rankine,Delisle,Newton,Reaumur,Romer)'
print 'Fahrenheit to (Kelvin,Celsius, Rankine,Delisle,Newton,Reaumur,Romer)'
print 'Rankine to (Kelvin,Celsius,Fahrenheit,Delisle,Newton,Reaumur,Romer)'
print 'Delisle to (Kelvin,Celsius,Fahrenheit,Rankine,Newton,Reaumur,Romer)'
print 'Newton to (Kelvin,Celsius,Fahrenheit,Delsile,Rankine,Reaumur,Romer)'
print 'Reaumur (Kelvin,Celsius,Fahrenheit,Delisle,Ranking,Newton,Romer)'
print 'Romer to (Kelvin,Celsius,Fahrenheit,Delisle,Ranking,Newton,Reaumur)'

#mass load of if statements. if reading this please dont forget to bring some coffee and a confy chair.

choice = raw_input('What is your choice:')
temp1 = raw_input('and your temp you need converted:')
if choice == 'kelvin to celsius':
	kelvin_to_celsius()
if choice == 'kelvin to Fahrenheit': 
	kelvin_to_fahrenheit()
if choice == 'kelvin to Rankine' :
	kelvin_to_rankine()
if choice == 'kelvin to Delisle':
	kelvin_to_delisle()
if choice == 'kelvin to Newton':
	kelvin_to_newton()
if choice == 'kelvin to Reaumur': 
	kelvin_to_reaumur()
if choice == 'kelvin to Romer' :
	kelvin_to_romer()
choice = raw_input('press enter to exit')[/PHP]

---

### Post by BluShift on 2009-07-17
I really wish I could help but I am at about the same level as you are... I have no idea :confused:

---

### Post by Can+~ on 2009-07-17
1. So your functions are all defined as 

[PHP]def something_to_other(temp1):[/PHP]

But in the calling, you're not passing anything:

[PHP]if choice == 'kelvin to Rankine' :
    kelvin_to_rankine() [/PHP]

When you should... (repeat this for every function call)

[PHP]if choice == 'kelvin to Rankine' :
    kelvin_to_rankine(temp1) [/PHP]

2. You're receiving a **string**, but on the moment of adding/substracting/multiplying, you need a **number**, in this case, a floating point:

[PHP]temp1 = float(raw_input('and your temp you need converted:'))[/PHP]

3. This is the third time I see a python temperature conversion program, what's going on?

I posted a similar code here:
-[The whole thread]("http://ubuntuforums.org/showthread.php?t=1209559")
-[My response]("http://ubuntuforums.org/showpost.php?p=7595821&postcount=16")

---

### Post by insanecrazy4 on 2009-07-17
> **Can+~ said:**
> 1. So your functions are all defined as 

[PHP]def something_to_other(temp1):[/PHP]

But in the calling, you're not passing anything:

[PHP]if choice == 'kelvin to Rankine' :
    kelvin_to_rankine() [/PHP]

When you should... (repeat this for every function call)

[PHP]if choice == 'kelvin to Rankine' :
    kelvin_to_rankine(temp1) [/PHP]

2. You're receiving a **string**, but on the moment of adding/substracting/multiplying, you need a **number**, in this case, a floating point:

[PHP]temp1 = float(raw_input('and your temp you need converted:'))[/PHP]

3. This is the third time I see a python temperature conversion program, what's going on?

I posted a similar code here:
-[The whole thread]("http://ubuntuforums.org/showthread.php?t=1209559")
-[My response]("http://ubuntuforums.org/showpost.php?p=7595821&postcount=16")

ty for your help i got it working. the reason why im making a temp conversion program is for learning purposes just as i saw you guys making them.

---

### Post by smartbei on 2009-07-18
Hmmm... While good for learning basic syntax and getting familiar with the program, creating a universal converter in this way is really just a lot of copy-pasting. I suggest getting a subset of this working (say, only temperature, and only Fahrenheit-Celsius-Kelvin) and then moving on to your next project. This way you will learn a lot more (since you won't be copying and pasting tons of function declarations and if...else blocks).

---

### Post by The Cog on 2009-07-18
As a warning - some functions, such as this one:
```
def Fahrenheit_to_Celsius(temp1):
    conversion = (temp1 - 32) * 5/9
```
will return inaccurate (integer) values if called with an intger value for temp1. You should make sure that all your arithmetic is done using floating point arithmetic, which can be done by converting the incoming value to a float, either explicitly:
```
    conversion = (float(temp1) - 32) * 5/9
```
or using a mathematical operation that converts it to a float:
```
    conversion = (temp1 - 32.0) * 5/9
```

---

