---
title: "All class' variables deleted... Why?"
date: 2010-07-06
forum: Programming Talk
---

### Post by NoBugs! on 2010-07-06
Here is a short example of the problem...
A window is created with some arg/args passed to it.
The calling function later changes that variable and it gets garbage collected, that shouldn't effect the window's behavior, but the window's class no longer has access to any of its class' variables:
```
import gtk
import gc
class TestClass:
	def __init__(self,arg):
		self.window = gtk.Dialog()
		self.window.add_button(gtk.STOCK_CLOSE,gtk.RESPONSE_CLOSE)
		self.window.connect("response",self.exit)
		self.test = "this variable should stay"
		self.update(arg)
		
	def update(self,arg):
		#all variables are fine here:
		for i in arg:
			print i
		self.window.show_all()
	
	def exit(self,obj,obj2):
		print "exiting"
		#Here it is unable to access any of these class variables:
		print self.test
		print self.window
		self.window.destroy()

def main():
	gtk.main()
	return 0

if __name__ == "__main__":
	s = [gtk.gdk.pixbuf_new_from_file('/path to any picture file'),34,"hello"]
	TestClass(s)
	s = [34]
	gc.collect()
	main()

```
This gives an error:
Traceback (most recent call last):
  File "return.py", line 20, in exit
    print self.test
AttributeError: TestClass instance has no attribute 'test'

Line 20,21, and 22 will not work anymore.

---

### Post by dwhitney67 on 2010-07-06
When exit() is called, you probably do not have an instance of TestClass, and thus the reason the variables seem undefined.

I'm not familiar with pyGTK (sp?), but typically when one connects a callback routine to an event, the class instance is provided as a parameter to connect() (or whatever) so that the callback routine can receive this class instance.

------------------

EDIT:  I may be wrong on what is stated above; here's a Python example that uses connect()... [http://www.wellho.net/resources/ex.php4?item=y212/gtkfeedback.py](http://www.wellho.net/resources/ex.php4?item=y212/gtkfeedback.py)

---

### Post by StephenF on 2010-07-06
I guess callbacks from external libraries are difficult things to track but it's easily prevented by storing the instance of TestClass at the point of instantiation.

It will keep the garbage collector off your back.

---

### Post by NoBugs! on 2010-07-06
Perhaps it's a bug in Python's garbage collector? Or it's passing byref instead of byvalue?
How do you store instance of class at instantiation?

---

### Post by dwhitney67 on 2010-07-06
Try this:
```

...

class TestClass:
        ...

        def main(self):
                gtk.main()

if __name__ == "__main__":
        s = [gtk.gdk.pixbuf_new_from_file('/path to any picture file'),34,"hello"]
        base = TestClass(s)
        s = [34]
        gc.collect()
        base.main()        # Here, TestClass' main() method is called.

```
Note how I have made main() part of TestClass.

---

### Post by slooksterpsv on 2010-07-06
variable1 = TestClass(s)

Where variable1 is any name for the variable.

---

### Post by NoBugs! on 2010-07-06
variable = TestClass(s) worked! :)
I still can't see why the gc.collect deleted all the variables in the class, though...

---

### Post by slooksterpsv on 2010-07-06
> **NoBugs! said:**
> variable = TestClass(s) worked! :)
I still can't see why the gc.collect deleted all the variables in the class, though...

Cause it wasn't allocated to a variable so therefore it was like running a function, one time use, throw away after it executes. Without having a variable to store your data it figured it was no longer needed.

---

