---
title: "Simplifying a bash script"
date: 2018-11-21
forum: Programming Talk
---

### Post by saurian2 on 2018-11-21
Hello everyone,

I have a customized bash script to build some stuffs which it looks something like this:

```
#!/bin/bash

#Do some stuffs
#...

STATUS=$?
if [ $STATUS -eq 0 ]; then
    #Do stuffs 1
    #...
    STATUS=$?
    if [ $STATUS -eq 0 ]; then
        #Do stuffs 2
        #...
        STATUS=$?
        if [ $STATUS -eq 0 ]; then
            #...
        else echo "Random message for building stuffs 3"
        fi
    else echo "Random message for building stuffs 2"
    fi
else echo "Random message for building stuffs 1"
fi
```

Is there a way to simplify my script. I'm thinking about using some kind of FOR so I won't have to repeat writing that IF-ELSE-FI clause lots of time. I'm pretty new in bash but if you can give me some hints or links I'm a pretty fast learner. The biggest problem is the fact that there are different line codes for each IF-ELSE branch (even though the logic is basically the same for each branch).

Thanks in advance!

---

### Post by TheFu on 2018-11-22
Use functions.

Google "ABSG bash" to find the Advanced Bash Scripting Guide" docs.

I have a general rule about bash/sh/ksh scripting.  When it becomes longer than 1 page, then it is time to switch to a more powerful language like python/ruby/perl.  I have 1 exception to that rule - program installations scripts.  Sometimes using only Bourne Shell is desired/mandatory for support across the most Unix-like platforms.

One last hint is to create a cleanup function that gets called to remove any temporary files made during processing and to capture any signals (like the different kill signals) so if the script dies for any reason, you don't leave crap behind.

---

### Post by saurian2 on 2018-12-03
@TheFu: That was it. This script is used for building a Java project using both ant and maven. Things are pretty complicated with building some modules with maven and others with ant. I normally had a really long script where I was building each module and simple displaying an error message like "Module X failed to build" if something wasn't built (a module failing would mean that all the next modules will fail). Now I created a function for each module and in a **for** I was able to put all the logic of my script.

Thanks!

---

### Post by TheFu on 2018-12-03
Usually for software build projects it is best to use build tools, not scripts.  Everyone starts out with a little build script, but as projects become more and more complex, the time to build grows.  Some projects I've worked on took over 4 hrs to build and that was using lots of parallel compile servers, but linking was only possible on 1 machine after all the compiles finished.  By reducing compilation to only those files where dependencies had changed, we were able to reduce the build time about 3/4.  Nothing could make linking faster, but that's life.

Automatic dependency tools should be pretty good these days.  We had them nailed in the mid-1990s.  Take advantage of those, if you can.

---

### Post by saurian2 on 2018-12-04
I agree but this is not my choice. When I got on this project things were this way and I tried for a simpler way to build everything (without using Jenkins). At a certain point this should be fixed.

---

