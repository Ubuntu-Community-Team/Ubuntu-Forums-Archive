---
title: "[Python] Exception Traceback Hook"
date: 2011-12-31
forum: Programming Talk
---

### Post by Pyro.699 on 2011-12-31
Basically what i am trying to do is when an exception is raised (from any thread that is currently running) i would like to catch that current exception and send important information from it to a remote server so that the problem could be tracked, fixed and then the program be updated. What would be the best way to obtain the most accurate information? I do know about over writing the sys.stderr but i would need to implement some kind of buffered reader because it doesn't send the entire traceback at once.

Any ideas?

Thanks
~Cody

---

### Post by chevloschelios on 2011-12-31
Hi, check this code.

```

try:
    #some code here
except Exception as e: 
    print "An error has occured"
    senderror(e)

```

---

### Post by Pyro.699 on 2011-12-31
> **chevloschelios said:**
> Hi, check this code.

```

try:
    #some code here
except Exception as e: 
    print "An error has occured"
    senderror(e)

```
That is slightly too obvious of a solution xD In program that spans thousands of line of code with over 100 files... having a single function that would have to be entered into EVERY try / except bracket would be much too tedious... plus you are forgetting the errors that are not covered in the try / except... This also does not cover multi threaded gui programs.

---

### Post by The Cog on 2011-12-31
This will take an exception and return a nice stack-trace string that you can mail to someone etc:```
# Format an exception wot we caught
def formatException(e):
    import sys
    from traceback import format_exception
    e = sys.exc_info()
    trace = format_exception(e[0], e[1], e[2])
    del e
    return "".join(trace)



```and use it like this:
```
try:
    something risky
catch Exception, ex:
    message = formatException(ex)
    # mail the exception to the boss

```

---

### Post by StephenF on 2012-01-01
> **The Cog said:**
> 
```
try:
    something risky
catch Exception, ex:
    message = formatException(ex)
    # mail the exception to the boss

```
Substitute 'something risky' with a call to main() or the main application loop and it will catch all uncaught exceptions.

---

### Post by Pyro.699 on 2012-01-02
Guys, all of these suggestions require me to have try / except clauses in a lot of areas...

My program "starts" this way:
[php]
def run():
    app = wx.PySimpleApp()
    frame = MyFrameClass(None, wx.ID_ANY)
    frame.Show()
    app.SetTopWindow(frame)
    app.MainLoop()
[/php]Now... if something inside the gui causes an execution error it does not trace back to this chunk of core NOR does it refer to ***run***.

I need something that is similar to overwriting the systderr but doesnt require that it get put through a buffered reader.

Thanks
~Cody

---
Example of an error caused in a separate thread:
[php]
Exception in thread Thread-1:
Traceback (most recent call last):
  File "/usr/local/lib/python2.7/threading.py", line 552, in __bootstrap_inner
    self.run()
  File "/home/path/to/my/file.py", line 39, in run
    int("fail")
ValueError: invalid literal for int() with base 10: 'fail'
[/php]

---

