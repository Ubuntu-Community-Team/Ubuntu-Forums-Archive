---
title: "shell script: timing how long a command(in ruby interpreter) takes to execute"
date: 2008-04-28
forum: Programming Talk
---

### Post by rbprogrammer on 2008-04-28
ok, so i want to create a shell script that will start a timer, execute a command, then look at the timer to see how much time has passed.  i would need this to be implemented with nanoseconds because some commands will take just a few nanoseconds to complete, while other will take seconds, maybe minutes to complete.

this is what i have for a script so far:
```

#!/bin/sh

#start timer

#execute some command
{
    echo "class Array"
    echo "  def common(a)"
    echo "    return self & a"
    echo "  end"
    echo "end"
    echo "class Fixnum"
    echo "  def relativeprime(k)"
    echo "    a = (1..self/2+1).to_a.delete_if { |x| self%x != 0 }"
    echo "    b = (1..k/2+1).to_a.delete_if { |x| k%x != 0 }"
    echo "    return a.common(b).length == 1"
    echo "  end"
    echo "end"
    echo "print 1.relativeprime(1000000)"                  #test this now
    echo "print '\n'"
    #echo "print 1.relativeprime(10000000)"                 #test this later
    #echo "print '\n'"
    #echo "print 1.relativeprime(10000000000000000000)"     #predict this time
    #echo "print '\n'"
} | ruby

#depending on implementation, stop timer


#look at timer to computer running time



```
now, how do i implement a timer? i was thinking of the "date" command with the nanosecond flag, but i dont know how to implement it so that it would print out accurate nanoseconds whether it took just a few nanoseconds or a few minutes.  obviously if the command took a few minutes i would have to convert the nanoseconds to minutes, but thats easy.

doing a simple google search: { [http://www.google.com/search?q=time+a+command+in+a+shell+script&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:official&client=firefox-a](http://www.google.com/search?q=time+a+command+in+a+shell+script&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:official&client=firefox-a) }
i got websites that basically say the same thing: { [http://www.cyberciti.biz/faq/shell-script-to-get-the-time-difference/](http://www.cyberciti.biz/faq/shell-script-to-get-the-time-difference/) }

but the nanosecond option doesnt seem to work the way i would expect.  executing the "1.relativeprime(1000000)" in ruby should take less than 1 second, but the next ruby command "1.relativeprime(10000000)" should take about 8 seconds, but i want an accurate number ( as best as possible ) to predict the running time of the last one.

any ideas?

---

### Post by CptPicard on 2008-04-28
No matter what you do, if you are going to be using a shell script and different processes for timer and your Ruby, you will not be able to get any kind of statistically meaningful nanosecond granularity results anyway... the Ruby interpreter will probably throw you off enough already.

---

### Post by ghostdog74 on 2008-04-28
you may want to try the time command for the whole script.
```

# time ruby ruby.script

```
or the benchmark module for ruby

---

### Post by mssever on 2008-04-28
From within Ruby, ```
require 'profile'
```

You'll get all the data you need. Just parse the output (or check the docs to find out how to customize it).

---

### Post by rbprogrammer on 2008-04-29
> **ghostdog74 said:**
> 
you may want to try the time command for the whole script.
```

# time ruby ruby.script

```
or the benchmark module for ruby

this was not in the script file, but it doesn't matter to me. this gave me the timing i needed for each of the test cases.

thanks ghostdog74

now all i have to do is figure out how to mark the thread as "solved" on the new forums.

---

