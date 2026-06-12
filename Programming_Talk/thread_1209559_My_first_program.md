---
title: "My first program"
date: 2009-07-10
forum: Programming Talk
---

### Post by crownedzero on 2009-07-10
So I decided to attempt to learn how to code. This is the first thing I've written and I'm having some small difficulties with it. I had a smaller version of it running, but I decided to add more options.
```

#Temperature conversion

def Fahrenheit():
    while True:
        choice = raw_input('Convert Fahrenheit to "K"elvin or "C"elsius? ')
        if choice == 'quit' or 'Quit':
            print 'Returning to the previous menu'
            break
            temperature_converter()
        elif choice == 'K' or 'k':
            Fahrenheit_to_Kelvin()
        elif choice == 'C' or 'c':
            Fahrenheit_to_Kelvin()
        else:
            print 'Invalid selection, please try again. '
            
def Celsius():
    while True:
        choice = raw_input('Convert Celsius to "K"elvin or "F"ahrenheit? ')
        if choice == 'quit' or 'Quit':
            print 'Returning to the previous menu'
            break
            temperature_converter()
        elif choice == 'K' or 'k':
            Celsius_to_Kelvin()
        elif choice == 'F' or 'f':
            Celsius_to_Fahrenheit()
        else:
            print 'Invalid selection, please try again. '

def Kelvin():
    while True:
        choice = raw_input('Convert Kelvin to "F"ahrenheit or "C"elsius? ')
        if choice == 'quit' or 'Quit':
            print 'Returning to the previous menu'
            break
            temperature_converter()
        elif choice == 'F' or 'f':
            Kelvin_to_Fahrenheit()
        elif choice == 'C' or 'c':
            Kelvin_to_Celsius()
        else:
            print 'Invalid selection, please try again. '
            
def Fahrenheit_to_Kelvin():
    fahrenheit = int(raw_input('What temperature would you like converted? '))
    kelvin = (0.55555 *(fahrenheit -32) + 273)
    print fahrenheit, ' degrees Celsius converts to ', kelvin, 'degrees Kelvin'
    
def Fahrenheit_to_Celsius():
    fahrenheit = int(raw_input('What temperature would you like converted? '))
    celsius = .556 * (fahrenheit - 32)
    print fahrenheit, ' degrees Fahrenheit converts to ', celsius, 'degrees Celsius'      
    
def Celsius_to_Kelvin():
    celsius = int(raw_input('What temperature would you like converted? '))
    kelvin = celsius + 273
    print celsius, ' degrees Celsius converts to ', kelvin, 'degrees Kelvin'
    
def Celsius_to_Fahrenheit():
    celsius = int(raw_input('What temperature would you like converted? '))
    fahrenheit = (1.8 * temperature) + 32
    print celsius, ' degrees Celsius converts to ', fahrenheit, 'degrees Fahrenheit'      

def Kelvin_to_Fahrenheit():
    kelvin = int(raw_input('What temperature would you like converted? '))
    fahrenheit = ((temperature - 273) * 1.8) + 32
    print kelvin, ' degrees Kelvin converts to ', fahrenheit, 'degrees Fahrenheit'
    
def Kelvin_to_Celsius():
    kelvin = int(raw_input('What temperature would you like converted? '))
    celsius = temperature - 273
    print kelvin, ' degrees Kelvin converts to ', celsius, 'degrees Celsius'    
    
def temperature_conversion():
    while True:
        selection = raw_input('Would you like to convert from "F"ahrenheit, "C"elsius, or "K"elvin? \n"Quit" to exit or return to the previous menu: ')
        if selection == 'quit' or 'Quit':
            print 'Exiting'
            break
        elif selection == 'F' or 'f':
            Fahrenheit()
        elif selection == 'C' or 'c':
            Celsius()
        elif selection == 'K' or 'k':
            Kelvin()
        else:
            print 'Invalid selection, please try again'

temperature_conversion()

```
No matter what I put in at the prompt it exits. This is almost verbatim what my initial(working) code had. What am I missing? I know its something stupid that's staring right at me.

---

### Post by Kinney on 2009-07-10
I haven't read through the whole thing but I noticed this in your main function.

if selection == 'quit' or 'Quit':

When you do this your saying if selection = 'quit' or true since 'Quit' is a non-zero value. It's not comparing selection to both.

Try changing it to:
if selection == 'quit' or selection == 'Quit':


Editing to give more options:
Also if you wanted to compare one variable to multiple strings you could do.
if selection in ['quit', 'Quit', 'QUIT']:

And you have this mistake in several spots it seems so you'll have to correct them all to make it work properly.

---

### Post by imdano on 2009-07-10
> **Kinney said:**
> I haven't read through the whole thing but I noticed this in your main function.

if selection == 'quit' or 'Quit':

When you do this your saying if selection = 'quit' or true since 'Quit' is a non-zero value. It's not comparing selection to both.

Try changing it to:
if selection == 'quit' or selection == 'Quit':


Editing to give more options:
Also if you wanted to compare one variable to multiple strings you could do.
if selection in ['quit', 'Quit', 'QUIT']:

And you have this mistake in several spots it seems so you'll have to correct them all to make it work properly.This is all true, but with the way he's using them it may make more sense to just do ```
if selection.lower() == 'quit':
```

---

### Post by crownedzero on 2009-07-10
I knew it was something to do with that, I just wasn't sure of how to go about having a list of selections. Works great now, thanks!

---

### Post by Kinney on 2009-07-10
> **imdano said:**
> This is all true, but with the way he's using them it may make more sense to just do ```
if selection.lower() == 'quit':
```
Good call. I hadn't thought of that.

I also wanted to point out that after fixing the selection statement the same mistake is made when comparing the letter values f, c, and k. And in addition he is making a call to selection outside of it's defined scope.

I'll let the OP attempt to correct though since he is learning.

---

### Post by crownedzero on 2009-07-10
> **imdano said:**
> This is all true, but with the way he's using them it may make more sense to just do ```
if selection.lower() == 'quit':
```

I actually did attempt this, but I left of the () so it returned an error.


```
Traceback (most recent call last):
  File "C:/Python26/test.py", line 16, in <module>
    temperature_converter()
  File "C:/Python26/test.py", line 4, in temperature_converter
    if choice.lower == 'quit':
AttributeError: 'builtin_function_or_method' object has no attribute 'lower'
```

---

### Post by crownedzero on 2009-07-10
> **Kinney said:**
> Good call. I hadn't thought of that.

I also wanted to point out that after fixing the selection statement the same mistake is made when comparing the letter values f, c, and k. And in addition he is making a call to selection outside of it's defined scope.

I'll let the OP attempt to correct though since he is learning.

^ Not sure what you mean. Here's the end result though. You can tell me if I fixed it or not.

```

#Temperature conversion

def Fahrenheit():
    while True:
        choice = raw_input('Convert Fahrenheit to "K"elvin or "C"elsius? ')
        if choice in ['QUIT', 'Quit', 'quit']:
            print 'Returning to the previous menu'
            break
            temperature_converter()
        elif choice in ['K','k']:
            Fahrenheit_to_Kelvin()
        elif choice in ['C','c']:
            Fahrenheit_to_Celsius()
        else:
            print 'Invalid selection, please try again. '
            
def Celsius():
    while True:
        choice = raw_input('Convert Celsius to "K"elvin or "F"ahrenheit? ')
        if choice in ['QUIT', 'Quit', 'quit']:
            print 'Returning to the previous menu'
            break
            temperature_converter()
        elif choice in ['K','k']:
            Celsius_to_Kelvin()
        elif choice == ['F','f']:
            Celsius_to_Fahrenheit()
        else:
            print 'Invalid selection, please try again. '

def Kelvin():
    while True:
        choice = raw_input('Convert Kelvin to "F"ahrenheit or "C"elsius? ')
        if choice in ['QUIT', 'Quit', 'quit']:
            print 'Returning to the previous menu'
            break
            temperature_converter()
        elif choice in ['F','f']:
            Kelvin_to_Fahrenheit()
        elif choice in ['C','c']:
            Kelvin_to_Celsius()
        else:
            print 'Invalid selection, please try again. '
            
def Fahrenheit_to_Kelvin():
    fahrenheit = int(raw_input('What temperature would you like converted? '))
    kelvin = (0.55555 *(fahrenheit -32) + 273)
    print fahrenheit, ' degrees Fahrenheit converts to ', kelvin, 'degrees Kelvin'
    
def Fahrenheit_to_Celsius():
    fahrenheit = int(raw_input('What temperature would you like converted? '))
    celsius = .556 * (fahrenheit - 32)
    print fahrenheit, ' degrees Fahrenheit converts to ', celsius, 'degrees Celsius'      
    
def Celsius_to_Kelvin():
    celsius = int(raw_input('What temperature would you like converted? '))
    kelvin = celsius + 273
    print celsius, ' degrees Celsius converts to ', kelvin, 'degrees Kelvin'
    
def Celsius_to_Fahrenheit():
    celsius = int(raw_input('What temperature would you like converted? '))
    fahrenheit = (1.8 * temperature) + 32
    print celsius, ' degrees Celsius converts to ', fahrenheit, 'degrees Fahrenheit'      

def Kelvin_to_Fahrenheit():
    kelvin = int(raw_input('What temperature would you like converted? '))
    fahrenheit = ((temperature - 273) * 1.8) + 32
    print kelvin, ' degrees Kelvin converts to ', fahrenheit, 'degrees Fahrenheit'
    
def Kelvin_to_Celsius():
    kelvin = int(raw_input('What temperature would you like converted? '))
    celsius = temperature - 273
    print kelvin, ' degrees Kelvin converts to ', celsius, 'degrees Celsius'    
    
def temperature_conversion():
    while True:
        **selection = raw_input('Would you like to convert from "F"ahrenheit, "C"elsius, or "K"elvin? \n"Quit" to exit or return to the previous menu: ')
        if selection in ['Quit', 'quit', 'QUIT']:
            print 'Exiting'
            break
        elif selection in ['F', 'f']:
            Fahrenheit()
        elif selection in ['C', 'c']:
            Celsius()
        elif selection in ['K', 'k']:
            Kelvin()
        else:
            print 'Invalid selection, please try again'

temperature_conversion()

```

Silly question while I'm at it. I **the selection line I'm referring too, but it actually runs of the screen even maximized. If I wanted to continue it on another line(just in the code) for aestethics how's that one work?

---

### Post by Can+~ on 2009-07-10
> **crownedzero said:**
> Silly question while I'm at it. I **the selection line I'm referring too, but it actually runs of the screen even maximized. If I wanted to continue it on another line(just in the code) for aestethics how's that one work?

[PHP]print '''This is written in
multiple lines, and also
spans multiple lines on the output'''

print 'When this is printed \
it will all be in a single  \
line. Have fun.'[/PHP]

You can achieve the same effect with either **'** or **"**.

---

### Post by Kinney on 2009-07-10
> **crownedzero said:**
> ^ Not sure what you mean. 

Nevermind. I must have read your code wrong earlier.

---

### Post by lavinog on 2009-07-10
You might want to look into removing all of the prompts and let the user just enter in values such as **104.5F K** (converts 104.5 F to Kelvin)
If the user leaves the value blank assume they want to exit (they can restart the program otherwise or you can use an exit prompt)

You can also make your functions reusable:
```

def Fahrenheit_to_Kelvin( temp_f ):
    temp_c = Fahrenheit_to_Celsius( temp_f )
    temp_k = Celsius_to_Kelvin( temp_c )
    return temp_k
    
def Fahrenheit_to_Celsius( temp_f ):
    temp_c = .556 * (temp_f - 32)
    return temp_c
    
def Celsius_to_Kelvin( temp_c ):
    temp_k = temp_c + 273
    return temp_k

def example():
    fahrenheit=104.5
    kelvin = Fahrenheit_to_Kelvin( fahrenheit )
    print fahrenheit, ' degrees Fahrenheit converts to ', kelvin, 'degrees
    
example()

```

The code above can also be reduced further, but might reduce readability:
```

def Fahrenheit_to_Kelvin( temp_f ): return Celsius_to_Kelvin( Fahrenheit_to_Celsius( temp_f ) )

def Fahrenheit_to_Celsius( temp_f ): return .556 * (temp_f - 32)
    
def Celsius_to_Kelvin( temp_c ): return temp_c + 273


```

---

### Post by lavinog on 2009-07-10
Also I noticed that in function Celsius_to_Fahrenheit() and the ones following, reference a variable 'temperature' that doesn't exist.

---

### Post by Can+~ on 2009-07-10
> **lavinog said:**
> The code above can also be reduced further, but might reduce readability:
```

def Fahrenheit_to_Kelvin( temp_f ): return Celsius_to_Kelvin( Fahrenheit_to_Celsius( temp_f ) )

def Fahrenheit_to_Celsius( temp_f ): return .556 * (temp_f - 32)
    
def Celsius_to_Kelvin( temp_c ): return temp_c + 273


```

Lambda!

[PHP]CtK = lambda temp_c: temp_c + 273
FtC = lambda temp_f: (temp_f - 32)*0.556
FtK = lambda temp_f: CtK(FtC(temp_f))[/PHP]

---

### Post by lavinog on 2009-07-10
> **Can+~ said:**
> Lambda!

[PHP]CtK = lambda temp_c: temp_c + 273
FtC = lambda temp_f: (temp_f - 32)*0.556
FtK = lambda temp_f: CtK(FtC(temp_f))[/PHP]

I am still new at this stuff.
I know about Lambda, but don't understand the advantage to it. Is it more optimized than a function?


I finished writing my version using the input method I was describing:
[php]

def F_to_K( temp_f ): return C_to_K( F_to_C( temp_f ) )

def F_to_C( temp_f ): return .556 * (temp_f - 32)
    
def C_to_K( temp_c ): return temp_c + 273

def C_to_F( temp_c ): return ( 1.8 * temp_c ) + 32

def K_to_C( temp_k ): return temp_k - 273

def K_to_F( temp_k ): return C_to_F( K_to_C( temp_K ) )

def convert_temp(temp_str):

    valid_units=['F','C','K']

    
    for i in range(-1,-len(temp_str),-1):
        conv_to = temp_str[i].upper()
        if conv_to in valid_units :
            valid_units.remove(conv_to)
            break
    else:return-5

    for i in range(i,-len(temp_str),-1):
        conv_from = temp_str[i].upper()
        if conv_from in valid_units :
            break
    else:return -5

    try:
        temp_value = float(temp_str[:i])
    except:
        return -6

    if conv_from == 'F':
        if conv_to == 'C':temp_converted = F_to_C( temp_value )
        if conv_to == 'K':temp_converted = F_to_K( temp_value )

    if conv_from == 'C':
        if conv_to == 'F':temp_converted = C_to_F( temp_value )
        if conv_to == 'K':temp_converted = C_to_K( temp_value )

    if conv_from == 'K':
        if conv_to == 'F':temp_converted = K_to_F( temp_value )
        if conv_to == 'C':temp_converted = K_to_C( temp_value )

    outstr = 'Result: ' + str(temp_value) + conv_from + ' = ' + str( temp_converted ) + conv_to
    print( outstr )
    print( "\n\n\n" )
    

    
def main():
    prompt_str='''Enter temperature and conversion codes like so:
###.#{F,C,K} {F,C,K}          ex: 104.4F C
To exit press enter on blank line.

'''
    while True:
        temp_str=raw_input(prompt_str)
        if len( temp_str ) == 0: break
        retflag = convert_temp(temp_str)

        if retflag == -5:
            print('Input does not match format')
            
        if retflag == -6:
            print('Value Error')
        

main()
[/php]

This lets you just enter in a value like 39.234cf to convert c to f

---

### Post by lavinog on 2009-07-10
Ok used lambda instead, added some comments, and changed the conversion for kelvin to be 273.15 instead of 273
[php]
def convert_temp(temp_str):
    
    valid_units=['F','C','K']

    # Find what we are converting to
    for i in range(-1,-len(temp_str),-1):
        conv_to = temp_str[i].upper()
        if conv_to in valid_units :
            # remove this unit to prevent converting to the same unit
            valid_units.remove(conv_to)
            break
    # return a error number if no value found (I randomly picked -5)
    else : return -5 
    
    # Find what we are converting from
    for i in range(i,-len(temp_str),-1):
        conv_from = temp_str[i].upper()
        if conv_from in valid_units :
            break
    # return error again due to bad input format
    else:return -5

    try:    # using try incase string cannot be converted to float
        temp_value = float(temp_str[:i])
    except:
        return -6 # return a different error number

    # using lambda instead of functions as recomended by Can+~
    F_to_K = lambda temp_f: C_to_K( F_to_C( temp_f ) )
    F_to_C = lambda temp_f: .556 * (temp_f - 32)
    C_to_K = lambda temp_c: temp_c + 273.15
    C_to_F = lambda temp_c: ( 1.8 * temp_c ) + 32
    K_to_C = lambda temp_k: temp_k - 273.15
    K_to_F = lambda temp_k: C_to_F( K_to_C( temp_K ) )

    if conv_from == 'F':
        if conv_to == 'C':temp_converted = F_to_C( temp_value )
        if conv_to == 'K':temp_converted = F_to_K( temp_value )

    if conv_from == 'C':
        if conv_to == 'F':temp_converted = C_to_F( temp_value )
        if conv_to == 'K':temp_converted = C_to_K( temp_value )

    if conv_from == 'K':
        if conv_to == 'F':temp_converted = K_to_F( temp_value )
        if conv_to == 'C':temp_converted = K_to_C( temp_value )

    outstr = 'Result: ' + str(temp_value) + conv_from + ' = ' + str( temp_converted ) + conv_to
    print( outstr )
    print( "\n\n\n" )
    
    
def main():
    prompt_str='''Enter temperature and conversion codes like so:
###.#{F,C,K} {F,C,K}          ex: 104.4F C
To exit press enter on blank line.

'''
    while True:
        temp_str=raw_input(prompt_str)
        if len( temp_str ) == 0: break
        retflag = convert_temp(temp_str)

        #check for errors
        if retflag == -5:
            print('Input does not match format')
            
        if retflag == -6:
            print('Value Error')
        

main()

[/php]

---

### Post by Can+~ on 2009-07-10
> **lavinog said:**
> Ok used lambda instead, added some comments, and changed the conversion for kelvin to be 273.15 instead of 273
[php]
def convert_temp(temp_str):
    
    valid_units=['F','C','K']

    # Find what we are converting to
    for i in range(-1,-len(temp_str),-1):
        conv_to = temp_str[i].upper()
        if conv_to in valid_units :
            # remove this unit to prevent converting to the same unit
            valid_units.remove(conv_to)
            break
    # return a error number if no value found (I randomly picked -5)
    else : return -5 
    
    # Find what we are converting from
    for i in range(i,-len(temp_str),-1):
        conv_from = temp_str[i].upper()
        if conv_from in valid_units :
            break
    # return error again due to bad input format
    else:return -5

    try:    # using try incase string cannot be converted to float
        temp_value = float(temp_str[:i])
    except:
        return -6 # return a different error number

    # using lambda instead of functions as recomended by Can+~
    F_to_K = lambda temp_f: C_to_K( F_to_C( temp_f ) )
    F_to_C = lambda temp_f: .556 * (temp_f - 32)
    C_to_K = lambda temp_c: temp_c + 273.15
    C_to_F = lambda temp_c: ( 1.8 * temp_c ) + 32
    K_to_C = lambda temp_k: temp_k - 273.15
    K_to_F = lambda temp_k: C_to_F( K_to_C( temp_K ) )

    if conv_from == 'F':
        if conv_to == 'C':temp_converted = F_to_C( temp_value )
        if conv_to == 'K':temp_converted = F_to_K( temp_value )

    if conv_from == 'C':
        if conv_to == 'F':temp_converted = C_to_F( temp_value )
        if conv_to == 'K':temp_converted = C_to_K( temp_value )

    if conv_from == 'K':
        if conv_to == 'F':temp_converted = K_to_F( temp_value )
        if conv_to == 'C':temp_converted = K_to_C( temp_value )

    outstr = 'Result: ' + str(temp_value) + conv_from + ' = ' + str( temp_converted ) + conv_to
    print( outstr )
    print( "\n\n\n" )
    
    
def main():
    prompt_str='''Enter temperature and conversion codes like so:
###.#{F,C,K} {F,C,K}          ex: 104.4F C
To exit press enter on blank line.

'''
    while True:
        temp_str=raw_input(prompt_str)
        if len( temp_str ) == 0: break
        retflag = convert_temp(temp_str)

        #check for errors
        if retflag == -5:
            print('Input does not match format')
            
        if retflag == -6:
            print('Value Error')
        

main()

[/php]

You shouldn't use return values to denote errors, that's why Python has Exception Handling.

---

### Post by Can+~ on 2009-07-10
Here's my take on the problem:

[PHP]#!/usr/bin/python
# coding: utf-8

# Dictionary with conversions
conversions = {
	"FK": lambda t: 0.556*(t - 32) + 273.15,
	"FC": lambda t: 0.556*(t - 32),
	"CK": lambda t: t + 273.15,
	"CF": lambda t: t*1.8 + 32,
	"KF": lambda t: (t-273.15)*1.8 + 32,
	"KC": lambda t: t - 273.15
}

def showsyntax():
	return "Syntax should be <value>º<C|K|F> to º<C|K|F>. Leave input blank to quit"

def parse(command):
	try:
		command = command.split("to")
		
		# Get the value and convert it to float
		value = float(command[0].split("º")[0])
		
		# Get the conversion units
		convfrom = command[0].split("º")[1].strip().upper()
		convto = command[1].strip("º \n").upper()
		
		# Stick them together and ask the dictionary.
		return conversions[convfrom+convto](value)
	except ValueError:
		print "Numeric value expected."
		print showsyntax()
	except IndexError:
		print "Parameters missing."
		print showsyntax()
	except KeyError:
		return value
	
def main():
	print "Unit converter 1.0.0"
	print showsyntax()
	
	while True:
		command = raw_input(">>").strip(" \n")
		
		if command != "":
			print parse(command)	
		else:
			break	

main()[/PHP]

First: I know someone will shout "REGULAR EXPRESSIOOOOOOOOOOOOOOONS" (read with slow-motion voice) but I limited myself to string methods for the sake of readability.

Now, the code works as following: Asks for input, breaks it down into three parts, value, convfrom and convto, and sends it to a dictionary with lambda functions on it.

The "core" of the whole code is on the first dictionary which maps each function to a corresponding string. For example, without any code and that dictionary, we could still use it:

[PHP]>>> conversions = \
... {
...     "FK": lambda t: 0.556*(t - 32) + 273.15,
...     "FC": lambda t: 0.556*(t - 32),
...     "CK": lambda t: t + 273.15,
...     "CF": lambda t: t*1.8 + 32,
...     "KF": lambda t: (t-273.15)*1.8 + 32,
...     "KC": lambda t: t - 273.15
... }
>>> conversions["CK"](300)
573.14999999999998[/PHP]

Why is that? Dictionaries are one of the key (pun intended) things that python has, it allows to do a x -> y relation, for example:

[PHP]>>> colorfruit = {"apple":"red", "orange":"orange", "grape":"purple"}
>>> colorfruit["apple"]
'red'[/PHP]

Now, in the code I posted I mapped to a lambda function (you can also do it with normal functions btw), meaning that doing:

```
conversions["CK"](300)
```

is the same as doing:

```
(lambda t: t + 273.15)(300)
```

which is plain addition:

```
300 + 273.15
```

This is one the many "tricks" you can do on python. As for the Exception Handling, [read the other post]("http://ubuntuforums.org/showthread.php?t=1209701") in which we discussed the same subject.

---

### Post by JordyD on 2009-07-10
It's better than my first (larger) python program. I commented like there was no tomorrow. Take this for example:
```
file.close()
# Close the file
```

---

### Post by Mirge on 2009-07-10
> **JordyD said:**
> It's better than my first (larger) python program. I commented like there was no tomorrow. Take this for example:
```
file.close()
# Close the file
```

It's good to establish a habit of commenting early on :). That may be slightly excessive though :).

---

### Post by JordyD on 2009-07-10
> **Mirge said:**
> It's good to establish a habit of commenting early on :). That may be slightly excessive though :).

Well, see, it's so bad in those files that they're almost unreadable.

That was not the worst case, by the way.

After reading that file again, I was convinced of the idea of "self documenting code". I like those multiline comments you can put after your functions.

[PHP]def pew(shipID = 0):
    """
    Shoot a missile at the ship with shipID
    """[/PHP]

Of course I would never name a function "pew", but it allowed me to show when a multiline like that would be helpful.

---

### Post by lavinog on 2009-07-10
> **Can+~ said:**
> 
[PHP]>>> conversions = \
... {
...     "FK": lambda t: 0.556*(t - 32) + 273.15,
...     "FC": lambda t: 0.556*(t - 32),
...     "CK": lambda t: t + 273.15,
...     "CF": lambda t: t*1.8 + 32,
...     "KF": lambda t: (t-273.15)*1.8 + 32,
...     "KC": lambda t: t - 273.15
... }
>>> conversions["CK"](300)
573.14999999999998[/PHP]

Very informative, thank you for the info.

I was just thinking about user interaction.
Depending on the purpose of the program, If I was a using this program repeatedly, It might be benificial to allow the user to only enter a temp with the current unit and have the program output the other two conversions
ex:
```

>>>0c 
32 F      273.15 K

```

---

### Post by Can+~ on 2009-07-10
> **lavinog said:**
> Very informative, thank you for the info.

I was just thinking about user interaction.
Depending on the purpose of the program, If I was a using this program repeatedly, It might be benificial to allow the user to only enter a temp with the current unit and have the program output the other two conversions
ex:
```

>>>0c 
32 F      273.15 K

```

Here's another task:

Try to make it work with command line arguments, such as:

python conversion.py 23C F

---

### Post by nvteighen on 2009-07-11
> **Can+~ said:**
> Here's my take on the problem:

[PHP]#!/usr/bin/python
# coding: utf-8

# Dictionary with conversions
conversions = {
	"FK": lambda t: 0.556*(t - 32) + 273.15,
	"FC": lambda t: 0.556*(t - 32),
	"CK": lambda t: t + 273.15,
	"CF": lambda t: t*1.8 + 32,
	"KF": lambda t: (t-273.15)*1.8 + 32,
	"KC": lambda t: t - 273.15
}

# [...]
[/PHP]


That's almost Lisp... it just lacks using symbols instead of strings :p Nice code!

I'd had used such an approach in Lisp, but never in Python... In Python, I would have used a generic linear function (something that calculates ax + b) and then a dictionary of a and b factors for each transformation... I'll take notes on what you did for future projects ;)

---

### Post by Can+~ on 2009-07-11
> **nvteighen said:**
> That's almost Lisp... it just lacks using symbols instead of strings :p Nice code!

I'd had used such an approach in Lisp, but never in Python... In Python, I would have used a generic linear function (something that calculates ax + b) and then a dictionary of a and b factors for each transformation... I'll take notes on what you did for future projects ;)

Yeah, I've been learning Scheme; some of the functional paradigm actually got into me and affected my coding on other languages.

---

### Post by nvteighen on 2009-07-11
> **Can+~ said:**
> Yeah, I've been learning Scheme; some of the functional paradigm actually got into me and affected my coding on other languages.
So it happened to me... you'll quickly see the benefits :)

---

