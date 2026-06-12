---
title: "script sleep &quot;issue&quot;"
date: 2011-08-31
forum: Programming Talk
---

### Post by Drenriza on 2011-08-31
Hi all.

I have created a script, that at some point sleeps for (3h) 10800 seconds.
This is quite a long time, and the script docent show anywhere when the time is up. So i have tried to create a function as so.
```
#!/bin/bash

###Countdown Fields###
t1=$(($sleepDarling))
t2="1"
##########################################################################
###Countdown function###
countdown(){
while [ $t1 > 1 ];do
t3=$(($t1-t2))
sleep 1
(echo "time test ${t3}")
t1=$(($t3))
done
exit 0
}
```
My problem is that, after i had created above i thought "how do i apply a timer, when the script is sleeping"????

The main script works, that when it has executed a command it writes to a log file i have created. And at some point it writes a entry to the log file "Sleeping for ${userDefinedTime}" 3h. And it was here i wanted the timer to apply my function. But how do i apply my countdown to my log file, so it shows the dynamic countdown in the log file, without it gets humonges. Does it make sense?

Kind regards.

---

### Post by hakermania on 2011-08-31
I think it makes sense, you want your script to sleep and to run a function displaying time info, i mean info about how much time is left from the 3 hours?
As far as I know, this is called 'threading'.
For example, here's a script:
```

#!/bin/bash
countdown(){
sleep 1;
echo AA
sleep 1;
echo BB
}

countdown&
echo "GG"

```
If you run this script you will notice that it will output first of all 'GG', then 'AA' and then 'BB', because although the countdown function is run first, it is run with an &, which allows the program not to append to the function and run it concurrently with the following code. The function has also a 'sleep 1' at its beginning and so 'GG' is outputed first.

Can this solve your problem or I missed something?

---

### Post by Drenriza on 2011-08-31
Uhmmmm im not sure. "playing" with a few things at the moment to try and solve this.
Is it possible in my main script to execute a function in another script. But not sleep the main script. 

So it executes a function in another script and then just continue on as with any other command.
:D

---

### Post by hakermania on 2011-08-31
> **Drenriza said:**
> Uhmmmm im not sure. "playing" with a few things at the moment to try and solve this.
Is it possible in my main script to execute a function in another script. But not sleep the main script. 

So it executes a function in another script and then just continue on as with any other command.
:D
but in my solution it executes a function of itself, so why to execute a function from another script?
You could do something like:
```

#!/bin/bash
sleep_me(){
sleep 3h
}
calculate(){
mpla mpla
}
sleep_me&
calculate

```

---

### Post by Drenriza on 2011-08-31
> **hakermania said:**
> but in my solution it executes a function of itself, so why to execute a function from another script?
You could do something like:
```

#!/bin/bash
sleep_me(){
sleep 3h
}
calculate(){
mpla mpla
}
sleep_me&
calculate

```

I did not notice that :p sry.
So to understand you correctly. In your example (the main script of mine) you can execute a function but without sleeping the main script? So it just continues on as with any other command. But in reality the function is running in the background?

---

### Post by Arndt on 2011-08-31
> **Drenriza said:**
> Uhmmmm im not sure. "playing" with a few things at the moment to try and solve this.
Is it possible in my main script to execute a function in another script. But not sleep the main script. 

So it executes a function in another script and then just continue on as with any other command.
:D

You can write a function which works like sleep, but does it in portions, say divides the sleep period in 10, and has a loop which counts to 10 and says something between the sleeps.

---

### Post by Drenriza on 2011-08-31
> **Arndt said:**
> You can write a function which works like sleep, but does it in portions, say divides the sleep period in 10, and has a loop which counts to 10 and says something between the sleeps.

Yea thats not all bad. Didn't think of that.

But is it still possible from one script, to call a function in another script. But without sleeping the first script?

---

### Post by hakermania on 2011-08-31
> **Drenriza said:**
> I did not notice that :p sry.
So to understand you correctly. In your example (the main script of mine) you can execute a function but without sleeping the main script? So it just continues on as with any other command. But in reality the function is running in the background?

yes, you got me right

---

### Post by ofnuts on 2011-08-31
> **Drenriza said:**
> Yea thats not all bad. Didn't think of that.

But is it still possible from one script, to call a function in another script. But without sleeping the first script?You can't "call a function" in another script. You can invoke that script, either as synchronous, or as a background task. You can even start several processes, and continue when they are all finished:

```

for f in files_to_process
do
  some_subprocess_we_will_wait_on $f &
done

# now wait for all child processes
wait

# We can continue, knowing that all subprocesses are done
# Note that we don't get their return code this way...

```

If you want a bit more info on who is still running

```

# declare array of pids for child processes
set -a pids
for f in files_to_process
do
  some_subprocess_we_will_wait_on $f &
  # get pid of started child process and add it to our array of child process pids
  pids[${#pids
[*]}]=$!
done

# Now wait for each pid in turn, if the process is already terminated
# the wait returns immediately
for pid in ${pids
[*]}
do
  # wait is bash built-in
  wait $pid
  echo "Sensed end of $pid"
done

# We can continue, knowing that all subprocesses are done
# Note that we don't get their return code this way...


```

You can also "source" a script from another script ie: This adds the functions defined in the source script to those available to the code in the "sourcer". I use that to make a "library" of functions common to several scripts. Ie:

Sourced script:

```

# Sourced "library_script"
# Doesn't even need a #! or the executable flag
function foobar
{
  echo "foobar"
}
echo "Library loaded"

```

User script:
```

#! /bin/bash

. $(dirname $0)/library_script
foobar

```

---

### Post by Drenriza on 2011-08-31
Thanks all.

Going to play some more with it :p

---

### Post by Drenriza on 2011-08-31
quick question.
If i call a sourced script that contains

test(){
echo "something"
}
echo "something2"

then echo "something2" will be executed but echo "something" does not. Is it me who docent understand how it works? I don't get it :p can someone explain it to me.
the script i call was given 755 permissions.

Kind regards.

---

### Post by ofnuts on 2011-08-31
Your "echo "something"" is inside a function definition. It's not executed unless the function is explicitly called.

```

function testfunction
{
    echo "In test function"
}

echo "In main"
testfunction

```produces:
```

In main
In test function

```

---

