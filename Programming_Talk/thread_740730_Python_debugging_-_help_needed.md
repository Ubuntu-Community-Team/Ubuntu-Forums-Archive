---
title: "Python debugging - help needed"
date: 2008-03-31
forum: Programming Talk
---

### Post by louis_nichols on 2008-03-31
Hi all!

I develop in Python using Eclipse and Pydev and it is a pretty cool setup.

However, there is a small feature I would really like to use and I don't know how (or even if) I can do it.

I would like to insert blocks in my code which will only be executed (or not be executed) if in debug mode. I use various tricks to debug and sometimes I forget to comment them out when I release the application...

---

### Post by mssever on 2008-03-31
> **louis_nichols said:**
> Hi all!

I develop in Python using Eclipse and Pydev and it is a pretty cool setup.

However, there is a small feature I would really like to use and I don't know how (or even if) I can do it.

I would like to insert blocks in my code which will only be executed (or not be executed) if in debug mode. I use various tricks to debug and sometimes I forget to comment them out when I release the application...
Add a debug switch. Python might have one already. Otherwise, use a boolean debug variable to do sonething like ```
if debug:
    #do stuff
```Or, you can make yourself a little debug wrapper so you can do something like ```
debug('This is a debug message')
``` and let the wrapper decide what action to take.

---

### Post by louis_nichols on 2008-03-31
Hi and thanks for the response. I had already thought ot add a debug switch, but the trick is to make it... pydev aware. I mean, to make it execute or skip code based on whether Pydev is in debug mode or not.

---

### Post by louis_nichols on 2008-04-01
OK. I got it. The trick is the feature to set environment variables. I'm posting it here, in case someone will need it.

So I just went to ```
Run > Open run properties > Python run > New launch configuration
```
Here, I added 3 run configurations:

[LIST]
[*]**DEBUGGING **- for this one, I went under Environment and added the variable **debug** with value True
[*] **NORMAL RUN **- this is default. Simply runs the application normally
[*] **NORMAL RUN with output to console **- this is because for my application I redirected stdout and stderr to a text window, but having errors in Eclipse makes it easier, because the traceback has hyperlinks. For settings, this is identical to DEBUGGING (The reason I made it is below.)
[/LIST]

After this, I added these settings to Run and Debug Favourites. The entry DEBUGGING is under Debug and the other 2 under Run. This is done by clicking the arrow next to the buttons and selecting "Organize favourites"

Next, I added this code to the application:
```
import os, string
try:
    if string.lower(os.environ['Debug']) == "true":
        debug = True
    else:
        debug = False
except KeyError:
    debug = False
```

So now I can debug easier. I can add code to be executed only if in debug mode and not worry about forgetting it there. Also, I can still run the application with output to the Eclipse Console, which makes debugging easier when I encounter exceptions.

This setup is not really perfect, because I can't have any of the setups to be executed by default when I click Debug or Run. I always have to select them from the drop-down menu (I am not able to add keyboard shortcuts either.). But it does the job nicely. Of course, any suggestions for improvement are welcome. :)

---

