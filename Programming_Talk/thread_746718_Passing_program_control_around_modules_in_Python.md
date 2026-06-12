---
title: "Passing program control around modules in Python"
date: 2008-04-05
forum: Programming Talk
---

### Post by xelapond on 2008-04-05
Right now I am writing a program that has many modules.  The first(main) module calls another module(loginWindow), which displays a window and waits for user input. loginWindow is then supposed to then call a function from the first(main) module, and that function is the main program loop.  The problem is, when I import loginWindow into main and main into loginWindow I get the following errors:  If I do not import main into loginWindow then it works fine, but cannot call the function because main is not imported.
```
alex@Andromeda:~/Projects/IMAP Mail Notify$ python ./main.py
Traceback (most recent call last):
  File "./main.py", line 11, in <module>
    import loginWindow
  File "/home/alex/Projects/IMAP Mail Notify/loginWindow.py", line 10, in <module>
    import main
  File "/home/alex/Projects/IMAP Mail Notify/main.py", line 19, in <module>
    lw = loginWindow.loginWindow()
AttributeError: 'module' object has no attribute 'loginWindow'
```I have a loginWindow class in the second module which is instantiated and activated from the first module, if that makes any sense.

Thanks a ton, 

Alex

---

### Post by alexforcefive on 2008-04-05
Shouldn't you just be returning the values from loginWindow and then calling the function from main.py? so main looks like:
```

var1, var2 = loginwindow.loginwindow()
nextfunction(var1, var2)
```

and loginwindow looks like:

```

def loginwindow():
     *a bunch of stuff*
     return var1, var2

```

Sorry if that was really stupid, I just learned this like two days ago :)

---

### Post by xelapond on 2008-04-05
Thanks for the help, but that's not what I am trying to do.  I am using OOP, so it is creating an instance of loginWIndow in main.  loginWindow then calls main and passes values into it.

So main would look like:
```

import loginWindow
lw = loginWindow.loginWindow()
lw.show()

def main(var):
     *Do some stuff*
```

And loginWindow looks like:
```

import main

*Class declaration stuff*
    *Do some stuff*
     main.main(var)

```

This isn't working for some reason though, so i'm hoping someone can give me some pointers.

Thanks anyway, 

Alex

---

### Post by smartbei on 2008-04-06
Well, when you do 'import main' in the loginWindow module it actually runs the loginWndow commands again, ad infinitum.

There is a way to solve it - put the code that you want to run only once, when the module itself is run and not when it is included in side the following if block (Note that the '__main__' in the if itself has nothing to do with the filename):
```

if __name__ == "__main__":
    

```
That way, it won't call the loginWindow code over and over again.

Besides, that still looks like bad design to me. I would do something like:
```

---loginWindow.py---

class declaration...

---main.py---
import loginWindow

def main():
	lw = loginWindow.loginWindow()
	authenticated = lw.show()
	if authenticated:
		# code
	else:
		# code

if __name__ == "__main__":
	main()

```

---

### Post by xelapond on 2008-04-06
Thanks!  That fixed it!

So, when I import a modules does it automatically run any stray code that is not in a function, or other structure like that?

---

### Post by Wybiral on 2008-04-06
> **xelapond said:**
> Thanks!  That fixed it!

So, when I import a modules does it automatically run any stray code that is not in a function, or other structure like that?

Think about it this way: function and class declarations ARE code that generates the functions and classes when it's executed. Everything in the module is executed when the module is imported.

---

### Post by pmasiar on 2008-04-07
> **xelapond said:**
> So, when I import a modules does it automatically run any stray code that is not in a function, or other structure like that?

Yes.

As Wyb mentioned above, ALL code is executed. def statement binds name of the function with it's code block. So you can make advanced tricks and assign different code body to the same name if you want to. Function decorators do that.

---

