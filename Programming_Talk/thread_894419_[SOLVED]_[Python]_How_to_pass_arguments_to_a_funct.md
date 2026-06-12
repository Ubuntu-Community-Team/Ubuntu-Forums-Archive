---
title: "[SOLVED] [Python] How to pass arguments to a function and have a default argument??"
date: 2008-08-19
forum: Programming Talk
---

### Post by rlameiro on 2008-08-19
Hi everyone, I am stuck in a mater here...

I have this little function to call a tk info box
[PHP]def errormsg():
	"""This is the function that calls a Graphic error message box
	USAGE : errormsg("title", "text")
	"""
	err_msg = tkMessageBox.showerror("ERROR", "Command unsucsessful. \n Check if hardware is connected or \n check the serial port used.") [/PHP]

What I want to do is use the errormsg("test", "test") to show up this text in the message box, or to use errormsg() to show up the default info. for what I searched I understand that I need to define the arguments, but if I define the arguments I cannot use the function like this errormsg() isn't it?
I hope anyone here can help me with this, I've searched for this on the documentation and in the internet and didn't find the answer. maybe I used bad words on the search.

---

### Post by rlameiro on 2008-08-19
I found this way of doing things. Is this the correct way? 

[PHP]def errormsg(title = "ERROR", text = "Command unsucsessful. \n Check if hardware is connected or \n check the serial port used." ):
    """This is the function that calls a Graphic error message box
    USAGE : errormsg("title", "text")
    """
    err_msg = tkMessageBox.showerror(title, text)[/PHP]

---

### Post by LaRoza on 2008-08-19
That is the correct way to have default argument values.

```

>>> def function(arg1,arg2="World"):
...     print arg1 + " " + arg2
... 
>>> function("Hello")
Hello World
>>> function("Disney")
Disney World
>>> 

```

---

### Post by dwhitney67 on 2008-08-19
> **rlameiro said:**
> I found this way of doing things. Is this the correct way? 

[PHP]def errormsg(title = "ERROR", text = "Command unsucsessful. \n Check if hardware is connected or \n check the serial port used." ):
    """This is the function that calls a Graphic error message box
    USAGE : errormsg("title", "text")
    """
    err_msg = tkMessageBox.showerror(title, text)[/PHP]

I would recommend that you clean up the clutter in your function declaration, so that it is easier to read.  Something like:
[PHP]#!/usr/bin/python

import sys

GENERIC_SEVERITY = "Critical:"
GENERIC_ERR_MSG  = "Command Unsuccessful"


def displayError( severity=GENERIC_SEVERITY, msg=GENERIC_ERR_MSG ):
        print severity,msg

##
## Main Program
##
displayError()
displayError( "Warning:", "Pants on fire!" )[/PHP]

---

