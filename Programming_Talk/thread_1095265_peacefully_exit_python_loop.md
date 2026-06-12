---
title: "peacefully exit python loop"
date: 2009-03-13
forum: Programming Talk
---

### Post by hsjC on 2009-03-13
Hi all,

I have a python script that runs as an infinite loop. I wanna be able to gracefully exit this loop, maybe through something key combination like ctrl+d or escape. 

So far I can only end it with ctrl+c, and it shows error messages and such. 

The whole script is just like:

while (1):
    #do something
    #sys.exit(0) if condition met

---

### Post by Can+~ on 2009-03-13
[COLOR="#00AACC"][FONT="Courier New"]break[/FONT][/COLOR]

And a graceful way to do it would be to ask for the typical "quit" or "q".

---

### Post by hsjC on 2009-03-13
> **Can+~ said:**
> [COLOR="#00AACC"][FONT="Courier New"]break[/FONT][/COLOR]

And a graceful way to do it would be to ask for the typical "quit" or "q".

Ha, thanks for your reply first. :P

But my script is independent of the interpreter. So i run it from command prompt, not from the interactive python environment.

I know break can end the loop, but my question is more like, how can I add a constant-monitoring statement that checks for keyboard input, while the loop is running? I dont want to wait for user input within each iteration...

---

### Post by mcla0203 on 2009-03-13
> constant-monitoring statement that checks for keyboard input, while the loop is running? I dont want to wait for user input within each iteration

That sounds a lot like waiting for the user input within each iteration.  Why would this be undersiable?

---

### Post by Can+~ on 2009-03-13
You could allow the user to use Ctrl+C and add a KeyboardInterrupt exception.

And here is a similar post in Bytes.com:
[http://bytes.com/groups/python/19453-python-get-key-pressing](http://bytes.com/groups/python/19453-python-get-key-pressing)

---

### Post by imdano on 2009-03-13
You could just catch the KeyboardInterrupt exception raised when pressing ctrl+c [php]try:
    while 1:
        # do stuff
except KeyboardInterrupt:
    pass[/php]edit: too slow :(

---

### Post by hsjC on 2009-03-13
> **mcla0203 said:**
> That sounds a lot like waiting for the user input within each iteration.  Why would this be undersiable?

It does wait for user input, but I dont want this "waiting" to interrupt the flow of my while loop. Since it's doing stuff I need it to do. :D So I want it to happen parallel with my while loop.

---

### Post by hsjC on 2009-03-13
Thanks guys for all your input. Try-except works really well already.

Just wondering, how can I end the script with just an Escape?

Or, can I define my own key strokes as a new exception?

---

