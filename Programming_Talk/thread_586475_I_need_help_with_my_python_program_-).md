---
title: "I need help with my python program :-)"
date: 2007-10-22
forum: Programming Talk
---

### Post by Xavieran on 2007-10-22
HI everyone I am learning to program python and I am trying to write a program
to experiment with classes basically I want it to store information about cars.eg. (btw I don't know if these are the real stats) Toyota Echo- Style:Hatchback,Cylinders:4,Manufacturer:Toyota,Model:Echo
My class will store and then I have designed a function to print all the stats.Now I was going fine until I decided to let the user define his/her own cars and be able access their information.

When you run the program below my output was:

```
/usr/bin/python -u  "/home/xavieran/python/mycode/carsbetterwork.py"
Please type a name for the new car: Toyota Echo
What type of car is it: Hatchback
How many cylinders does it have: 4
Who manufactured the car: Toyota
What model is it: Echo
None
Traceback (most recent call last):
  File "/home/xavieran/python/mycode/carsbetterwork.py", line 21, in <module>
    print CarInfo(0)
  File "/home/xavieran/python/mycode/carsbetterwork.py", line 9, in CarInfo
    Garage={Name:Car(TypeOfCar,NoOfCylinders,Model,Manufacturer)}
NameError: global name 'TypeOfCar' is not defined
```

```
class Car:
	def __init__ (self,Style,Cylinders,Model,Make):
		self.TypeOfCar=Style
		self.NoOfCylinders=Cylinders
		self.Model=Model
		self.Manufacturer=Make
ToyotaEcho=Car('HatchBack',4,'Echo','Toyota')
def CarInfo(Car):
	Garage={Name:Car(TypeOfCar,NoOfCylinders,Model,Manufacturer)}
	return Garage
def NewCar():
	Name=raw_input('Please type a name for the new car: ')
	TypeOfCar=raw_input('What type of car is it: ')
	NoOfCylinders=int(raw_input('How many cylinders does it have: '))
	Manufacturer=raw_input('Who manufactured the car: ')
	Model=raw_input('What model is it: ')
	Garage={Name:Car(TypeOfCar,NoOfCylinders,Model,Manufacturer)}
	return
print NewCar()

print CarInfo(0)
```

Any help would be appreciated as well as suggestions on how to improve the program.

:) Thankyou :)

---

### Post by Wybiral on 2007-10-22
I think something like this is what you're going for:

```

class Car:
    def __init__ (self, Name, Style, Cylinders, Model, Make):
        self.Name = Name
        self.Style = Style
        self.Cylinders = Cylinders
        self.Model = Model
        self.Make = Make

    # Notice how 'info' is a member of 'Car'
    def info(self):
        out = 'Name: %s\n' % self.Name
        out += 'Style: %s\n' % self.Style
        out += 'Cylinders: %s\n' % self.Cylinders
        out += 'Make: %s\n' % self.Model
        out += 'Model: %s' % self.Make
        return out

# Uses input to create and return an instance of 'Car'
def NewCar():
    Name = raw_input('Please type a name for the new car: ')
    Style = raw_input('What type of car is it: ')
    Cylinders = int(raw_input('How many cylinders does it have: '))
    Model = raw_input('What model is it: ')
    Make = raw_input('Who manufactured the car: ')
    return Car(Name, Style, Cylinders, Model, Make)

# Instance of 'Car' created from user input
MyCar = NewCar()
print MyCar.info()

# Instance of 'Car' created manually
ToyotaEcho = Car('Toyota Echo', 'HatchBack', 4, 'Echo', 'Toyota')
print ToyotaEcho.info()

```

When you use 'Car()' as a function, you're calling the initializer and creating an instance of the class. Also, class members belong to the class, so you have to access them with "some_car.some_member" which is why the interpreter is complaining that "TypeOfCar" is not defined.

If you're going to create the "Garage" you wanted, you'll need a global dictionary/list. Just remember that any call you "Car" will create a NEW object.

Also, your "CarInfo" function was creating a map of the car name to a NEW car object. It should be a member of the class and use the members directly.

---

### Post by pmasiar on 2007-10-22
As a beginner, you don't have to bother about classes and OOP until you need it. Python lets you code in plain old procedural style with no problems.

See pythonchallenge website and wiki in my sig for training tasks.

---

### Post by ghostdog74 on 2007-10-22
> **Wybiral said:**
> 
...
    # Notice how 'info' is a member of 'Car'
    def info(self):
        out = 'Name: %s\n' % self.Name
        out += 'Style: %s\n' % self.Style
        out += 'Cylinders: %s\n' % self.Cylinders
        out += 'Make: %s\n' % self.Model
        out += 'Model: %s' % self.Make
        return out
...


```

out = """
Name: %s
Style: %s
Cylinders: %s
Make: %s
Model: %s """ % (self.Name...blah...)

```

---

### Post by Wybiral on 2007-10-22
> **ghostdog74 said:**
> ```

out = """
Name: %s
Style: %s
Cylinders: %s
Make: %s
Model: %s """ % (self.Name...blah...)

```

You could do that. It's a preference thing. I don't like my lines to go out too far (like the format parameter would have).

---

### Post by Xavieran on 2007-10-22
Thanks heaps!:)
 I've reformatted my original CarInfo Function using Wybiral's format string and it now actually does something useful I've added a while loop and exception management (Essential for when you misspell things) .
How can I make my NewCar Function actually save the cars information into something that CarInfo can read and would it be possible to write the cars information into a text file on my system.

Current Code:
```
class Car:
	def __init__ (self,Name,Style,Cylinders,Model,Make):
		self.Name=Name
		self.TypeOfCar=Style
		self.NoOfCylinders=Cylinders
		self.Model=Model
		self.Manufacturer=Make
		
	def CarInfo(self):
		output='%s\n'%(self.Name)
		output+='Type of car: %s\n'%(self.TypeOfCar)
		output+='Cylinders: %d\n'%(self.NoOfCylinders)
		output+='Model: %s\n'%(self.Model)
		output+='Manufacturer: %s\n'%(self.Manufacturer)
		return output
	
def NewCar():
	RealName=input('Please type a name for the new car with no spaces: ')
	Name=raw_input('Please type a name for the new car: ')
	TypeOfCar=raw_input('What type of car is it: ')
	NoOfCylinders=int(raw_input('How many cylinders does it have: '))
	Manufacturer=raw_input('Who manufactured the car: ')
	Model=raw_input('What model is it: ')
	RealName=(Name,TypeOfCar,NoOfCylinders,Manufacturer,Model)
	return RealName

ToyotaEcho=Car('Toyota Echo','HatchBack',4,'Echo','Toyota')
FordGt=Car('Ford Gt','Sports car',8,'Gt','Ford')
Garage=[ToyotaEcho.Name,FordGt.Name]


i=0
while i==0:
	try:
		print 'Current Cars: ',Garage[0:]
		print Car.CarInfo(input('Type the name of the car you wish to view :'))
	except NameError:
		print 'That car is not in the database.' 
```

Thanks for your help;)

---

### Post by Wybiral on 2007-10-22
> **Xavieran said:**
> How can I make my NewCar Function actually save the cars information into something that CarInfo can read and would it be possible to write the cars information into a text file on my system.

If it's a member of the class, then you don't pass the cars to it, the car already has it so you can call it with "mycar.CarInfo()" (like in the example I posted).

Yes, you can write it to a file. Look up the functions "open()" and "write()".

I agree with pmasiar, OOP is something you want to learn after you master some of the simpler concepts of programming.

EDIT:

Also, good naming conventions are a must. You're using a multiple names for the same types of objects in your program, you should use a clear and standard convention when labeling things (stick with "TypeOfCar" or "Style", but don't use both to represent the same thing). And, four space tabs are preferred in the Python community over actual tabs (it's a rule in a lot of standards). Spacing between operators is another common standard that will make your code more readable to others.

---

### Post by ghostdog74 on 2007-10-22
> **Wybiral said:**
> You could do that. It's a preference thing. I don't like my lines to go out too far (like the format parameter would have).
string concats like this are fairly slow, as strings are immutable.
[Here]("http://www.skymind.com/~ocrow/python_string/") and [here.]("http://wiki.python.org/moin/PythonSpeed/PerformanceTips#head-bcf69f4e2cacc9683c2f9a1f401e891cac50506f")
However, this  might not be true for newer versions of Python.

---

### Post by Wybiral on 2007-10-22
> **ghostdog74 said:**
> string concats like this are fairly slow, as strings are immutable.
[Here]("http://www.skymind.com/~ocrow/python_string/") and [here.]("http://wiki.python.org/moin/PythonSpeed/PerformanceTips#head-bcf69f4e2cacc9683c2f9a1f401e891cac50506f")
However, this  might not be true for newer versions of Python.

Naturally, but an application like this is in no hurry to shave any CPU, so as it is, it's just preference. A one line formated string would be the fastest, but IMO it's harder to read (and I'm not fond of multi-line quotes).

But, you do have a point... And sometimes you need to squeeze that CPU power out, but usually not (unless it's a 3d game or server-code bottleneck). In most cases, readability should be the main goal.

---

### Post by pmasiar on 2007-10-22
> **Wybiral said:**
> 
        out += 'Style: %s\n' % self.Style


re-allocating strings is wasteful. Better is to add partial output to list of strings, and join when ready:

```

out = []
out.append('Style: %s' % self.Style)
...
return '\n'.join(out)

```

---

### Post by Xavieran on 2007-10-22
Thanks for your help guys! I researched the open() and write() functions and have now hacked the program into something useful.Now it can save cars data into the file called Car.
> **pmasiar said:**
> As a beginner, you don't have to bother about classes and OOP until you need it. Python lets you code in plain old procedural style with no problems.
I understand what you mean.I was just making this program to experiment with classes and stuff like that.

Thanks for your suggestions for improvements. 
Any new ideas are still welcome.

I've added comments.(is this the correct way to do them?)

The new code:
```
class Car:
	'''A Car class'''
	def __init__ (self,Name,Style,Cylinders,Model,Make):
		self.Name=Name
		self.Car=Style
		self.Cylinders=Cylinders
		self.Model=Model
		self.Make=Make
#Uses string formatting to concatenate and then print to screen	
	def info(self):
		'''Give information on a Car object and write it to a file'''
		output = [self.Name]
		output.append('Type of car: %s' % self.Car)
		output.append('Cylinders: %s' % self.Cylinders)
		output.append('Model: %s' % self.Model)
		output.append('Manufacturer: %s' % self.Make)
		output.append('\n')
		print '\n'.join(output)
#		Garage=open('/home/xavieran/Car','a')
#		return Garage.write('\n'.join(output))
def NewCar():
	'''Writes a new car to the Car file'''
#First asks the user for info about the car...
	Name=raw_input('Please type a name for the new car: ')
	Type=raw_input('What type of car is it: ')
	Cylinders=int(raw_input('How many cylinders does it have: '))
	Make=raw_input('Who manufactured the car: ')
	Model=raw_input('What model is it: ')
#Then concatenates all that info into a single string...
	output = [Name]
	output.append('Type of car: %s' % Type)
	output.append('Cylinders: %s' % Cylinders)
	output.append('Model: %s' % Model)
	output.append('Manufacturer: %s' % Make)
	output.append('\n')
#and finally prints it to the screen and writes to the Car file
	print '\n'.join(output)
	Garage=open('/home/xavieran/Car','a')
	return Garage.write('\n'.join(output))
# Define some Car objects and make a list to hold them
ToyotaEcho=Car('Toyota Echo','HatchBack',4,'Echo','Toyota')
FordGt=Car('Ford Gt','Sports car',8,'Gt','Ford')
Cars=[ToyotaEcho.Name,FordGt.Name]
#A loop to print a Car objects info.Can access the NewCar() function
i=0
while i==0:
	try:
		print 'Current Cars: ',Cars
		print Car.info(input('Type the name of the car you wish to view :'))
	except NameError:NewCar()		
```
Xavieran

---

