---
title: "How to put numbers in a string in Python?"
date: 2009-07-18
forum: Programming Talk
---

### Post by Jimleko211 on 2009-07-18
I forgot how to spell the term, but I need to put in my numbers in with my strings in a print statement.  I'm probably explaining it wrong, but I don't know how else to explain it.

I'm working on a simple temperature converter, to practice functions, and I'm almost done.  However, in my main() function I get an error (I manually put in the main() to make it organized).

My code:
```

def toCelcius(temp):
    return (5/9)*(temp - 32)

def toFarenheit(temp):
    return (9/5)*temp+32

def main():
    print "Temperature converter"
    print
    temp = 0
    temp = input("Enter a temperature: ")
    choice = ' '
    choice = raw_input("Convert to Farenheit or Ceclius? (F/C): ")
    if choice == 'F':
        print temp + " C = " + toFarenheit(temp) + " F"
    elif choice == 'C':
        print temp + " F = " + toCelcius(temp) + " C"
    else:
        print "That was not a valid choice.  Please restart the program."

main()

```

Error:
```

File "temperature.py", line 44, in <module>
   main()
File "temperature.py", line 40, in main
   print temp +" F = " + toCelcius(temp) + " C"
TypeError: unsupported operand type(s) for +: 'int' and 'str'

```

That's with trying to convert 32 F to Celcius.

How do I fix my error?

---

### Post by Can+~ on 2009-07-18
Either (Explicit conversion to string):

[PHP]print str(number) + "string" + str(number2) + "string2"[/PHP]

Or (Comma values):

[PHP]print number, "string", number2, "string2"[/PHP]

Or (C-like):

[PHP]print "%d string %d string2" % (number, number2)[/PHP]

Or (C-like with a dictionary):

[PHP]print "%(key1)d string %(key2)d string2" % {"key1":number, "key2":number2}[/PHP]

[Or the format method]("http://docs.python.org/library/stdtypes.html#str.format")

---

### Post by Jimleko211 on 2009-07-18
> **Can+~ said:**
> Either (Explicit conversion to string):

[php]print str(number) + "string" + str(number2) + "string2"[/php]Or (Comma values):

[php]print number, "string", number2, "string2"[/php]Or (C-like):

[php]print "%d string %d string2" % (number, number2)[/php][Or the format method]("http://docs.python.org/library/stdtypes.html#str.format")

Thank you so much, that solved my problem!

---

