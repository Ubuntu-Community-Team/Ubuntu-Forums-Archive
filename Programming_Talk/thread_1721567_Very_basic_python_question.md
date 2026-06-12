---
title: "Very basic python question"
date: 2011-04-04
forum: Programming Talk
---

### Post by antagonist388 on 2011-04-04
My question is this: I know ord(x) returns an integer value, but what's the function that turns that integer back into a string?

---

### Post by sisco311 on 2011-04-04
Hi and welcome to the forums!

In python2 **chr** and **unichr**. in python3 **chr**.

See:
[http://docs.python.org/library/functions.html](http://docs.python.org/library/functions.html)
[http://docs.python.org/release/3.0.1/library/functions.html](http://docs.python.org/release/3.0.1/library/functions.html)

---

### Post by antagonist388 on 2011-04-04
awesome, thank you.

Another question:
How can I turn a locally defined variable into a globally defined variable?

---

### Post by cgroza on 2011-04-04
You assign it to a already global variable.
Global variables generally considered a bad idea, as there is almost aways a better way in Object Orientated Programming.

---

### Post by llanitedave on 2011-04-05
> **antagonist388 said:**
> awesome, thank you.

Another question:
How can I turn a locally defined variable into a globally defined variable?

As cgroza has pointed out, you probably don't want to do that.  If there is a variable that you need to use throughout your application, one approach is to define a class that contains the variable, create an instance of that class, and pass the instance to the functions that need it.

---

### Post by Chimes on 2011-04-05
example:

```

def addthree(some_number):
  some_number = some_number +3
  return some_number

class calculator:
  def __init__(self):
    self.var=0

  def add_num(self, num):
     self.var = self.var+num
     return self.var

  def set_num(self, num):
     self.var = num
     return self.var

def main():
  a=0
  print(a)
  a = addthree(a)
  print(a)
  b = addthree(a)
  addthree(a)
  print(a)

  calc = calculator()
  meow = calc.add_num(3)
  print(meow)
  meow = calc.set_num(5)
  print(meow)
  calc.var = 10
  meow = calc.add_num(2)
  print(meow)
  calc.memvar = list()
  calc.memvar.append(meow)
  calc.memvar.append(addthree(calc.memvar[0])
  print(calc.memvar[1])

if __name__=='__main__':
  main()

```

this should get you started on variable storage. :)

Please, please, do not give your variables the meaningless names i gave them here. If i ever read a program that uses "memvar" as a variable name seriously,  i will go crazy. :P

---

### Post by simeon87 on 2011-04-05
I don't agree with the advice that global variables are a bad idea. Python is not OOP but it's multi-paradigm, you can have variables outside your classes. Not everything is an object so if you have a global variable then there's no need to wrap it in an object and keep passing it around. As long as you have one place to access the information (i.e., no duplication) you can still have a well organized project.

---

### Post by cgroza on 2011-04-05
> **simeon87 said:**
> I don't agree with the advice that global variables are a bad idea. Python is not OOP but it's multi-paradigm, you can have variables outside your classes. Not everything is an object so if you have a global variable then there's no need to wrap it in an object and keep passing it around. As long as you have one place to access the information (i.e., no duplication) you can still have a well organized project.
They bring allot of risks, and if used in a somewhat medium to big project, they become terrible to debug.

---

### Post by simeon87 on 2011-04-05
> **cgroza said:**
> They bring allot of risks, and if used in a somewhat medium to big project, they become terrible to debug.

I would also argue against it in projects at companies or with a group of people but in personal projects it may just be fine.

---

### Post by llanitedave on 2011-04-05
> **simeon87 said:**
> I would also argue against it in projects at companies or with a group of people but in personal projects it may just be fine.

Yes.  It's not a "never, never do" thing, otherwise it would have been a mistake to allow it in the language.  It's just something that should be done sparingly, cautiously, and always for a good reason.

---

### Post by nvteighen on 2011-04-06
Global variables aren't evil; they're usually misused, which isn't the same.

For example, in a language like C, the C Standard Library uses a global variable (int errno) to provide more information on errors than what a single return code may provide. The usual case is: a function returns a pointer, but it may fail for different reasons. So, when the function fails, it returns a NULL pointer, and sets errno to some specified value depending on what happened. Remember, C doesn't support multiple return values and passing a pointer to some variable just to make it hold the error code seems quite convoluted.

But, I've seen (and written) lots of OOP code in which some data member ends up being a "de facto" global variable inside the class's namespace. Ok, it's not really a global variable, in the sense that it isn't accessible at all points of execution, but if the class namespace is big enough, such a variable may also trigger the "obfuscating" effect (specially when debugging) if used incorrectly, exactly like a "really global" variable.

---

