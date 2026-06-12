---
title: "Python - command line question"
date: 2009-11-29
forum: Programming Talk
---

### Post by C++buntu on 2009-11-29
Hi everyone, 

I have a little problem, i want to run a program for a certain filename given as input in the command line, it doesn't work quite well so far and i don't know why. I can use the python-guru around here ;).

My program is the following:

```

import sys
from scitools.std import *

# Read the command line
def read_cml():
    try:
        cml = sys.argv[1]
    except IndexError:
        raise IndexError('No filename given. Program aborted.')
    if type(eval(sys.argv[1])) != str:
        raise ValueError('The filename must be a string, not "%s".' % sys.argv[1])
    return cml

# Read datafile      
def read_data(filename, display = False):
    infile = open(filename, 'r')
    celsius = []; density = []

    # 1st version
    for line in infile:
        if ((line[0] != '#') and (line[0] != '\n')):
            words = line.split()
            celsius.append(float(words[0]))
            density.append(float(words[1]))
            
    # 2nd version
    # for line in infile:
    #   if ((not line.startswith('#')) and (not line.startswith('\n'))):
    #       words = line.split()
    #       celsius.append(float(words[0]))
    #       density.append(float(words[1]))
    
    # 3th version
    # for line in infile:
    #   if ((not line.startswith('#')) and (not line.isspace())):
    #       words = line.split()
    #       celsius.append(float(words[0]))
    #       density.append(float(words[1]))   
     
    infile.close()
    celsius = array(celsius); density = array(density)

    if display == True:
        print '-'*15
        for c, d in zip(celsius, density):
            print '%g\t%g' % (c, d)
        print '-'*15

    plot(celsius, density, 'b-o', xlabel = 'Celsius [C]', ylabel = 'Density [kg/m^3]', title = '%s' % filename)

if __name__ == '__main__':
    try:
        filename = read_cml()
    except Exception, e:
        print e
        sys.exit(1)
        
    read_data(filename, True)

```

My file is formatted like this:

# Density of air at different temperatures, at 1 atm pressure
# Column 1: temperature in Celsius degrees
# Column 2: density in kg/m^3 

  0.0   999.8425
  4.0   999.9750
 15.0   999.1026
 20.0   998.2071
 25.0   997.0479
 37.0   993.3316
 50.0   988.04
100.0   958.3665
# Source: Wikipedia (keyword Density)

Now, when i run this in ipython, i got:

```

run read_density_data.py /home/cppbuntu/Desktop/Python/Source/files/density_of_water.dat
scitools.easyviz backend is gnuplot
invalid syntax (<string>, line 1)
/var/lib/python-support/python2.6/IPython/iplib.py:2672: DeprecationWarning: BaseException.message has been deprecated as of Python 2.6
  if status.message!=0 and not kw['exit_ignore']:
---------------------------------------------------------------------------
SystemExit                                Traceback (most recent call last)

/home/cppbuntu/Desktop/Python/Problems/Chapter 06/read_density_data.py in <module>()
     57     except Exception, e:
     58         print e
---> 59         sys.exit(1)
     60 
     61     read_data(filename, True)

SystemExit: 1
WARNING: Failure executing file: <read_density_data.py>

```

Any ideas? I've try to enter the filename as

/home/cppbuntu/Desktop/Python/Source/files/density_of_water.dat
'/home/cppbuntu/Desktop/Python/Source/files/density_of_water.dat'
and
"/home/cppbuntu/Desktop/Python/Source/files/density_of_water.dat"

but it doesn't work either :)

Thanks for the help.

---

### Post by snova on 2009-11-29
> **C++buntu said:**
> ```

# Read the command line
def read_cml():
    try:
        cml = sys.argv[1]
    except IndexError:
        raise IndexError('No filename given. Program aborted.')
    if type(eval(sys.argv[1])) != str:
        raise ValueError('The filename must be a string, not "%s".' % sys.argv[1])
    return cml

```

I don't have SciPy installed and cannot test the script properly, but this eval() magic is useless and probably the reason it isn't working. sys.argv is a list of strings already; there's nothing to be gained by doing this.

---

### Post by C++buntu on 2009-11-29
I'm doing this in case of somebody enter a number instead of a string...if i use eval, i can test if its a string or not...

---

### Post by C++buntu on 2009-11-29
and for the scipy part, you just need it in order to plot the graphic...the code that take care of the command line is supposed to work.

---

### Post by Can+~ on 2009-11-29
> **C++buntu said:**
> I'm doing this in case of somebody enter a number instead of a string...if i use eval, i can test if its a string or not...

You can use "[FONT="Courier New"]isdigit[/FONT]":

[PHP]>>> "Hello World".isdigit()
False
>>> "12345".isdigit()
True[/PHP]

(Anything passed as an argument is a string btw)

---

### Post by snova on 2009-11-29
> **C++buntu said:**
> I'm doing this in case of somebody enter a number instead of a string...if i use eval, i can test if its a string or not...

If I run this:

```
python ./yourscript.py density_of_water.dat
```

You're going to get this as sys.argv:

```
["./yourscript.py", "density_of_water.dat"]
```

Command line arguments are strings and there is not a thing that can be done to change this. Type checking is pointless (not to mention rather unpythonic) and evaluation is only going to frustrate someone who now has to manually pass quotes to the program. And then it's going to fail anyway because the filename itself also has to contain quotes now.

> Any ideas? I've try to enter the filename as

/home/cppbuntu/Desktop/Python/Source/files/density_of_water.dat
'/home/cppbuntu/Desktop/Python/Source/files/density_of_water.dat'
and
"/home/cppbuntu/Desktop/Python/Source/files/density_of_water.dat"

but it doesn't work either 

Thanks for the help.

Assuming you are passing these on the command line, all of these are completely equivalent. Programs are never passed anything other than strings; quotes here are processed by the shell.

"12345" is still a string (and an entirely valid filename).

---

### Post by ib.lundgren on 2009-11-29
You are forgetting to read in the lines in your for loop. 
```
for line in infile:
for line in infile.readlines()
```

Also when you are testing for a certain condition, say filename, make sure it is a filename and dont try and check if it is a number or not since that won't help you very much.

```
import os.path
print os.path.exists(sys.argv[1]) #True/False
```

It might also be useful during the reading of file to convert the "numbers" to actual numbers since they are stored as strings by default.
```
celsius = float(words[0])
density = float(words[1])
```

I have never used %g and quite frankly cant remember its use, i like floats =)
```
print "%15.1f%15.4f" % (c, d)
```

---

### Post by snova on 2009-11-29
> **ib.lundgren said:**
> You are forgetting to read in the lines in your for loop. 
```
for line in infile:
for line in infile.readlines()
```

No he isn't. Both of those will do the same thing, with the exception that yours will read the entire file in one go and convert it to a list. Granted these are small files, but it doesn't work well with larger ones. And, it's more code.

> Also when you are testing for a certain condition, say filename, make sure it is a filename and dont try and check if it is a number or not since that won't help you very much.

```
import os.path
print os.path.exists(sys.argv[1]) #True/False
```

This opens a race condition (the file might no longer be valid by the time you actually open it). It's better to just open the file and catch the exception should it fail.

[PHP]
    try:
        infile = open(sys.argv[1])
    except IOError as e:
        print e
        sys.exit(1)
[/PHP]

---

### Post by C++buntu on 2009-11-29
> **Can+~ said:**
> You can use "[FONT=Courier New]isdigit[/FONT]":

[php]>>> "Hello World".isdigit()
False
>>> "12345".isdigit()
True[/php](Anything passed as an argument is a string btw)

Oh, thanks for the tip! I will use that.

---

