---
title: "Python: popen(), maybe I need to use something else?"
date: 2007-04-25
forum: Programming Talk
---

### Post by billyseth on 2007-04-25
Sorry about the vague subject but I am having trouble describing my needs here.
I am trying to get a python script(We will call it script A) to call another script(Script B), I need Script A to wait until Script B produces some output then process the output accordingly.
I am using popen() currently. I might just be using it incorrectly for what I need to do. Here is what is going on...

```
 def main():
        lircInput = os.popen("/usr/bin/ircat test")
        if lircInput == "left":
                left()
        else:
                right()

```

left() and right() both recall my main() function when they are done, is there anything you guys can think of?

Any help would be great. Thanks.

---

### Post by AdamG on 2007-04-25
You are soo close :)

The lircInput variable is just the file descriptor; you need to read the data from it.

```
lircData=lircInput.read()
if lircData == "left": 
    #etc etc

```

---

### Post by pmasiar on 2007-04-25
> **billyseth said:**
>  python script( script A) to call another script(Script B), I need Script A to wait until Script B produces some output then process the output accordingly.......

Is script B also a python program? Did you checked exec/execfile -- why they do not fit?

If Script A calls script B, A will wait until B is finished, so no tricks to synchronize is needed. Am I missing something?

Edit. I see i was looking at synchonization which is not a problem. Reading data from file - AdamG beat me to it.

---

### Post by billyseth on 2007-04-25
AdamG thank you for that, I would have ran into that problem once I overcome this one...

pmasiar you are on to something, script B should continue to run in the background, and give output. I need script A to read the output of script B, then process it, then wait for more output from script B.  Maybe I am not doing this in a very effective way. I am trying to get an easy interface between lirc and my script and the ircat command seems to be great, maybe not though

Thanks a lot

---

