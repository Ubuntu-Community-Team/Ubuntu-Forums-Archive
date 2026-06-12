---
title: "Python Problem"
date: 2007-02-12
forum: Programming Talk
---

### Post by jvc26 on 2007-02-12
Hi there, I'm just learning python at the minute and have been wondering a few things about python predefinitions. In the example:
```

#converts temperature to fahrenheit or celsius

def print_options():
    print "Options:"
    print " 'p' print options"
    print " 'c' convert from celsius"
    print " 'f' convert from fahrenheit"
    print " 'q' quit the program"

def celsius_to_fahrenheit(c_temp):
    return 9.0 / 5.0 * c_temp + 32

def fahrenheit_to_celsius(f_temp):
    return (f_temp - 32.0) * 5.0 / 9.0

choice = "p"
while choice != "q":
    if choice == "c":
        temp = input("Celsius temperature: ")
        print "Fahrenheit:", celsius_to_fahrenheit(temp)
    elif choice == "f":
        temp = input("Fahrenheit temperature: ")
        print "Celsius:", fahrenheit_to_celsius(temp)
    elif choice != "q":
        print_options()
    choice = raw_input("option: ")

```

What is the part in brackets here: def fahrenheit_to_celsius(f_temp) for? The first function, print_options() doesnt have anything between the () so what is the difference between the two?

I then wrote my own idea:
```

def print_options():
	print "Options:"
	print " 'p' Print Options"
	print " 's' Square area"
	print " 'r' Rectangle area"
	print " 'c' Circle Area"
	print " 'q' Quit"

def square_area(s_area):
	return side**2

def rectangle_area(r_area):
	return width * length

def circle_area(c_area):
	return 3.14 * radius**2

choice = "p"
while choice != "q":
	if choice == "s":
		print "Calculates the area of a square"
		side = input("Side length: ")
		area = 0
		print "Area", square_area(area)
	elif choice == "r":
		print "Calculates the area of a rectangle"
		width = input("Width: ")
		length = input("Length: ")
		area = 0
		print "Area", rectangle_area(area)
	elif choice == "c":
		print "Calculates the area of a circle"
		radius = input("Radius: ")
		area = 0
		print "Area", circle_area(area)
	elif choice != "q":
		print_options()
	choice = raw_input("Choice: ")

```
Using the above idea as an example. Are these three things correct:

1/ print "Area", rectangle_area(area) - calls the function rectangle_area() and returns the value of the calculation to variable area. If so what is the point of having rectangle_area(r_area)?

2/ Using another variable in this case, any of the other variables 'area' seems wasteful - could I just get away with using print "Area", circle_area(radius) as the value that variable previously held is no longer needed? Is this bad code as it is using a variable for something other than what it was used before? Or is this a better use of resources.

3/ Would it be better for the sake of the person using the program to end the last command with:
	choice = raw_input("Choice: ")
	print_options()
So as to refresh the list of options at the end of each run?

Sorry these may seem very basic questions, but am only learning and need some way of finding them out!
Thanks for your help,
Il

---

### Post by gradedcheese on 2007-02-12
> What is the part in brackets here: def fahrenheit_to_celsius(f_temp) for?

That's a parameter, named f_temp.  It's passed to the "fahrenheit_to_celsius" function (def means function).  A simple and silly example:

```

def add_nums( num1, num2 ):
   return num1 + num2

# call this function
print "1+2 is", add_nums( 1, 2 )
print "4+8 is", add_nums( 4, 8 )

```

that should clear it up, I think...

---

### Post by ssam on 2007-02-12
if you are a beginner you might want to read this [http://www.ibiblio.org/obp/thinkCSpy/](http://www.ibiblio.org/obp/thinkCSpy/)

---

### Post by jvc26 on 2007-02-12
Thanks guys thats made it a lot clearer,
Il

---

