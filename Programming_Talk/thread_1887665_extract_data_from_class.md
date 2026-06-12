---
title: "extract data from class"
date: 2011-11-27
forum: Programming Talk
---

### Post by johnmay on 2011-11-27
I am converting a powershell script to python. 
```

import csv
class newvar:
    pass
def attempt(arg):  
        newvar.name = arg
        thelist.append(newvar)
        print newvar.name
        return 
thelist = []
i = 42
loc = 'infotest.csv'
latte = csv.reader(open(loc))
for info in latte:
        date = info[0]
        attempt (date)
        i -= 1
for s in thelist:
    print s.name

```The 7th line print is a debug line which tells me good so far. However, when I use the print s.name I just get the last value printed 42 times. Any suggestions greatly appreciated!

Thanks!

---

### Post by kostkon on 2011-11-27
actually, I think that the values are printed by the attempt function's
```
print newvar.name
```
and not the
```
for s in thelist:
    print s.name
```
anyway you need to specify that thelist is a global var (because you are trying to change its value [you don't need to do this if you are only reading its value]), otherwise thelist will be just a local var of the attempt function. Thus, try this:
```
thelist = []
def attempt(arg):  
        global thelist
        newvar.name = arg
        thelist.append(newvar)
        print newvar.name
        return 
```

---

### Post by johnmay on 2011-11-27
Kostkon, 
    Thanks for your suggestions, though I have not been able to successfully utilize them. I am not in complete agreement about the global setting because: 
```

thelist = []
def attempt(arg):  
        newvar = {'name' : arg };
        #thelist.append(newvar)
        #print newvar.name
    darth = newvar.values()
    thelist.append(darth)    
        return 

```

works to return the 'iterated' values in thelist, without naming it global. 
   As a matter of fact, I am able to use the dict method successfully, though I am not able to parse the results in an acceptable method, and I believe that using the class is the best method for achieving results I can work with. Thanks for your time and information!

---

### Post by johnmay on 2011-11-27
I figured it out:
 ```

def attempt(arg): 
          newvar.name = arg
          thelist.append(newvar.name)
          return

```Returns the value I 'expected' or wanted rather... 

Thanks for the inspiration Kostkon!

:guitar:

---

