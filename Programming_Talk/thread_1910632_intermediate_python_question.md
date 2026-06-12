---
title: "intermediate python question"
date: 2012-01-17
forum: Programming Talk
---

### Post by rajan on 2012-01-17
Hi,
I am struggling with what I think is a fairly intro-level programming concept that relates to a python code I'm writing. I want to write a code where I access a set of pre-existing arrays from either a command-line argument or a stdin-type input. A simplified example would be:

```

VOLUME=[1,1,1,1,1,1]
ENERGY=[2,2,2,2,2,2]

```

and at this point I would like to be able to do something like:

```

print sys.argv[2]

```

where sys.argv[2] = "VOLUME" --- This should then print the array 1,1,1,1,1,1.

I think this is called pass by reference or pass by value, but I tried to make heads from tails using google without success. 

Anyone have any clues, and I'm all for reading if you have suggestions. I just don't know where to start.

---

### Post by MadCow108 on 2012-01-17
I'm not sure understood the question, but I think a dictionary is what you are looking for
```
data = dict(
VOLUME=[1,1,1,1,1,1],
ENERGY=[2,2,2,2,2,2]
)

print data[sys.argv[2]]
```

---

### Post by CoffeeRain on 2012-01-17
Do you mean that if the argument is "VOLUME" print the array VOLUME? If so, this should work.

```

argument=sys.argv[2]
print eval(argument)

```

---

### Post by rajan on 2012-01-17
Hey MadCow,
 Thanks for the reply. My problem is a bit more complicated. I would like to create several arrays (~30) and reference them by name. From the example above, I would like to, from stdin, be able to access the entire array just by typing the name of the array that I have assigned in the python file. 

Is this possible?

---

### Post by rajan on 2012-01-17
> **CoffeeRain said:**
> Do you mean that if the argument is "VOLUME" print the array VOLUME? If so, this should work.

```

argument=sys.argv[2]
print eval(argument)

```

EVAL! 

That's just what I needed, thanks CoffeeRain

---

### Post by CoffeeRain on 2012-01-17
My example should work.

```

array_1=[1,1,1,1,1,1]
array_2=[2,2,2,2,2,2]
array_3=[3,3,3,3,3,3]
array_4=[4,4,4,4,4,4]

a=raw_input('What is the name of the array? ')
print eval(a)

```

---

### Post by CoffeeRain on 2012-01-17
Didn't see your second post. :)

---

### Post by simeon87 on 2012-01-17
> **rajan said:**
> EVAL! 

That's just what I needed, thanks CoffeeRain

Are you alone going to use the code? Or are you going to distribute it to others? You might want to reconsider eval (for sure) if you are making something for others. eval is pretty insecure, in particular when you're going to eval user input like that.

---

### Post by rajan on 2012-01-18
> **simeon87 said:**
> Are you alone going to use the code? ....


I will be using this code exclusively, mainly for data analysis. However, if you have an alternative, I'm always up for learning more python.

I found a few things by googling "eval python insecure" --- I think something

[like this]("http://stackoverflow.com/questions/661084/security-of-pythons-eval-on-untrusted-strings")

is what you're getting at?

---

### Post by Bachstelze on 2012-01-18
```
firas@dhcp-v056-094 ~ % cat test.py
#!/usr/bin/env python3

import sys
t = [int(x.strip()) for x in sys.argv[1].strip('[]').split(',')]
for i in t:
        print(i)
firas@dhcp-v056-094 ~ % ./test.py '[1, 2, 3, 4]'
1
2
3
4
```

Needs some error-checking but that's the idea.

---

### Post by simeon87 on 2012-01-19
> **rajan said:**
> I will be using this code exclusively, mainly for data analysis. However, if you have an alternative, I'm always up for learning more python.

I found a few things by googling "eval python insecure" --- I think something

[like this]("http://stackoverflow.com/questions/661084/security-of-pythons-eval-on-untrusted-strings")

is what you're getting at?

I try to avoid eval whenever I can. In your case, you know what the argument will be so you can lookup the variable somewhere instead of eval()-ing what you get.

---

### Post by MadCow108 on 2012-01-20
> **rajan said:**
> I will be using this code exclusively, mainly for data analysis. However, if you have an alternative, I'm always up for learning more python.

I found a few things by googling "eval python insecure" --- I think something

[like this]("http://stackoverflow.com/questions/661084/security-of-pythons-eval-on-untrusted-strings")

is what you're getting at?

to evaluate data please use **ast.literal_eval** instead of eval (if available).
its a secure way to import data formatted in python container syntax.

---

### Post by lykwydchykyn on 2012-01-20
i'd just put my lists in a dictionary, with the key being the string literal I wanted to use to access them, e.g.:

```


data = { "VOLUME": [1,1,1,1,1,1], "ENERGY": [2,2,2,2,2,2] }

array_specified = sys.argv[2]

if array_specified in data.keys():
    print data[array_specified]

```

This way it's safe against malicious/accidental input.

Also, if it's not feasible to change the way the data is stored (i.e., they have to stay as independent variables), you can do something like this:
```

VOLUME = [1,1,1,1,1]
ENERGY = [2,2,2,2,2]

data = ["VOLUME":VOLUME, "ENERGY":ENERGY]

```

Which accomplishes the same thing.

---

### Post by Bachstelze on 2012-01-20
> **lykwydchykyn said:**
> i'd just put my lists in a dictionary, with the key being the string literal I wanted to use to access them, e.g.:

```


data = { "VOLUME": [1,1,1,1,1,1], "ENERGY": [2,2,2,2,2,2] }

array_specified = sys.argv[2]

if array_specified in data.keys():
    print data[array_specified]

```

This way it's safe against malicious/accidental input.

Also, if it's not feasible to change the way the data is stored (i.e., they have to stay as independent variables), you can do something like this:
```

VOLUME = [1,1,1,1,1]
ENERGY = [2,2,2,2,2]

data = ["VOLUME":VOLUME, "ENERGY":ENERGY]

```

Which accomplishes the same thing.

If I understand OP correctly, data is to be passed on standard input (or as an argument, which is the same thing: it is passed as text, it is not part of the code).

---

### Post by rajan on 2012-01-21
> **Bachstelze said:**
> If I understand OP correctly, data is to be passed on standard input (or as an argument, which is the same thing: it is passed as text, it is not part of the code).

This is correct. Here's the full code as I have it. It is used for parsing the log file from NAMD molecular dynamics output so that it can be used by either writing a file or manipulating the data in memory.

```
import os,sys,math

file1 = open(sys.argv[1],'r')
strin = file1.readlines()

TS = []
BOND = []
ANGLE = []
DIHED = []
IMPRP = []
ELECT = []
VDW = []
BOUNDARY = []
MISC = []
KINETIC = []
TOTAL = []
TEMP = []
POTENTIAL = []
TOTAL3 = []
TEMPAVG = []
PRESSURE = []
GPRESSURE = []
VOLUME = []
PRESSAVG = []
GPRESSAVG = []

for X in range(len(strin)):
    if strin[X][0:6] == 'ENERGY':
        str1 = strin[X].split()
        TS.append(str1[1]),BOND.append(str1[2]),ANGLE.append(str1[3]),DIHED.append(str1[4]),IMPRP.append(str1[5]),ELECT.append(str1[6]),VDW.append(str1[7]),BOUNDARY.append(str1[8]),MISC.append(str1[9]),KINETIC.append(str1[10]),TOTAL.append(str1[11]),TEMP.append(str1[12]),POTENTIAL.append(str1[13]),TOTAL3.append(str1[14]),TEMPAVG.append(str1[15]),PRESSURE.append(str1[16]),GPRESSURE.append(str1[17]),VOLUME.append(str1[18]),PRESSAVG.append(str1[19]),GPRESSAVG.append(str1[20])

newfile = sys.argv[1].split('.')

file2 = open(newfile[0]+'.dat2','w')

arr1 = eval(raw_input('\nWhich array?\n\n\n'))

for X in range(len(arr1)):
    #print arr1[X]
    file2.write('%7d %12.4f\n' % (int(TS[X]),float(arr1[X])))

file1.close()
file2.close()
```

The log file that this script will read is something of this sort, but about 14 MB worth:

```
ENERGY:      42       221.9634      1301.0058       112.1790         0.0000          -8500.8568    -24544.7663         0.0000         0.0000         0.0000         -31410.4750         0.0000    -31410.4750    -31410.4750         0.0000           -648.6436      -652.9078    681472.0000      -648.6436      -652.9078
```

In the future if I make this something I can place on a web server, the security will become more important. For now, however, I really appreciate all the tips.

---

### Post by lykwydchykyn on 2012-01-22
The basic principle still applies, though, that if you want to avoid eval (and you probably should), put your lists in a dictionary using string literal names as keys.  This keeps data as data, and protects the internals of your script from bad input.

That's just my opinion, anyway.

---

