---
title: "Running specific function in python script"
date: 2010-11-26
forum: Programming Talk
---

### Post by tw11 on 2010-11-26
Is it possible to run a specific function within a python script from the terminal. For example, if i have abc.py

```

def xyz(a):
   print "var a is "+a

```

is there a way to run python abc.py and specify the function xyz from within terminal (but not the python shell)?

Like: $ python abc.py -function xyz("HELLO")
var a is HELLO

except something that works obviously

Thanks!!

---

### Post by cgroza on 2010-11-26
You could cd to the script, open a python shell and: 
```
from abc import xyz

```
and then simply call the function.

---

### Post by Cheesehead on 2010-11-26
Use sys.argv:

From [http://docs.python.org/library/sys.html]("http://docs.python.org/library/sys.html")
sys.argv
The list of command line arguments passed to a Python script. argv[0] is the script name (it is operating system dependent whether this is a full pathname or not). If the command was executed using the -c command line option to the interpreter, argv[0] is set to the string '-c'. If no script name was passed to the Python interpreter, argv[0] is the empty string.


```
import sys
print (sys.argv)
for item in sys.argv:
  print (item)

Result:
$ python myscript.py -fred -joe -janet -spaz
['myscript.py', '-fred', '-joe', '-janet', '-spaz']
myscript.py
-fred
-joe         
-janet
-spaz
```


Use this by capturing the command line arguments within the Python script, and then passing the data to the correct function. Make sure to document so you remember how to maintain it later. Don't forget to check for bad input!


Example:```
import sys
"""Usage: $python myscript.py [-aeiou] [name] """

def main(string_of_flags, name):
   number_of_flags = len(string_of_flags)      # Figure out which flag was used
   result_list = []                                # If you have multiple flags, capture all the results
   for num in range(0,number_of_flags):
      flag = string_of_flags[num:(num+1)]
      if flag = 'a' :
         result_list.append(ring_the_doorbell(name))
      elif flag = 'e' :
         result_list.append(take_out_the_trash(name))
      elif.... # You get the idea
   final_result = reformat(result_list)            # Explain or convert results to something meaningful
print(final_result)



main(sys.argv[2], sys.argv[3])
```

---

### Post by smartbei on 2010-11-27
The python executable accepts the '-c' flag to indicate that you are passing it code. So if my file (test.py) is:
```

def test():
    print "AAA"

```

Then I could do:
```

$ python -c "execfile('test.py'); test()"
AAA

```

---

